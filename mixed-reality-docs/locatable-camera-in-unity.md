---
title: Unity의 과정이 카메라
description: Unity의 HoloLens 과정이 카메라 사용입니다.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 사진, 비디오, hololens, 카메라, unity, 과정이
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515443"
---
# <a name="locatable-camera-in-unity"></a>Unity의 과정이 카메라

## <a name="enabling-the-capability-for-photo-video-camera"></a>사진 비디오 카메라 기능 사용

[카메라](locatable-camera.md)를 사용 하려면 앱에 대해 "웹캠" 기능을 선언 해야 합니다.
1. Unity 편집기에서 "> 프로젝트 설정 > 플레이어 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.
2. "Windows 스토어" 탭을 클릭 합니다.
3. "게시 설정 > 기능" 섹션에서 **웹캠** 및 **마이크** 기능을 확인 합니다.

카메라에서는 한 번에 하나의 작업만 수행할 수 있습니다. 카메라의 현재 모드 (사진, 비디오 또는 없음)를 확인 하려면 UnityEngine. XR을 확인할 수 있습니다.

## <a name="photo-capture"></a>사진 캡처

**공간** *UnityEngine. XR*<br>
**입력할** *사진 캡처*

사진 *캡처* 유형을 사용 하면 사진 비디오 카메라와 사진을 계속 사용할 수 있습니다. 사진 *캡처* 를 사용 하 여 사진을 촬영 하는 일반적인 패턴은 다음과 같습니다.
1. *사진 캡처* 개체 만들기
2. 원하는 설정을 사용 하 여 *CameraParameters* 개체를 만듭니다.
3. *Startphoto Modeasync* 를 통해 사진 모드 시작
4. 원하는 사진 가져오기
    * 필드 해당 사진과 상호 작용
5. 사진 모드 중지 및 리소스 정리

### <a name="common-set-up-for-photocapture"></a>사진 캡처에 대 한 일반적인 설정

세 가지 용도 모두에서 위의 동일한 첫 3 단계부터 시작 합니다.

먼저 *사진 캡처* 개체를 만듭니다.

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

다음으로 개체를 저장 하 고, 매개 변수를 설정 하 고, 사진 모드를 시작 합니다.

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

끝으로 여기에 제공 된 동일한 정리 코드를 사용 합니다.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

이러한 단계를 수행 하 고 나면 캡처할 사진 유형을 선택할 수 있습니다.

### <a name="capture-a-photo-to-a-file"></a>파일에 사진 캡처

가장 간단한 작업은 파일에 직접 사진을 캡처하는 것입니다. 사진은 JPG 또는 PNG로 저장할 수 있습니다.

사진 모드를 성공적으로 시작 하는 경우 이제 사진을 사용 하 고 디스크에 저장 합니다.

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

사진을 디스크로 캡처한 후 사진 모드를 종료 하 고 개체를 정리 합니다.

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a>Texture2D에 사진 캡처

Texture2D으로 데이터를 캡처할 때 프로세스는 디스크에 캡처하는 것과 매우 비슷합니다.

위의 설정 프로세스를 따릅니다.

*Onsale Modestarted*에서 메모리에 프레임을 캡처합니다.

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

그런 다음 결과를 질감에 적용 하 고 위의 일반적인 정리 코드를 사용 합니다.

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>사진 캡처 및 원시 바이트 조작

메모리 프레임에 있는 원시 바이트와 상호 작용 하려면 Texture2D에 대 한 사진 캡처 *에서와 같이* 위와 동일한 설정 단계를 수행 합니다. 차이점은 원시 바이트를 가져와 상호 작용할 수 있는 *OnCapturedPhotoToMemory* 입니다.

이 예제에서는 *setpixels ()* 을 통해 텍스처에 추가로 처리 하거나 적용할 수 있는 *목록을<Color>*  만듭니다.

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a>비디오 캡처

**공간** *UnityEngine. XR*<br>
**입력할** *VideoCapture*

*VideoCapture* 은 *사진 캡처와*매우 유사 하 게 작동 합니다. 두 가지 차이점은 FPS (초당 프레임 수) 값을 지정 해야 하 고, mp4 파일로는 디스크에 직접 저장 하는 것입니다. *VideoCapture* 를 사용 하는 단계는 다음과 같습니다.
1. *VideoCapture* 개체 만들기
2. 원하는 설정을 사용 하 여 *CameraParameters* 개체를 만듭니다.
3. *Startvideomodeasync* 를 통해 비디오 모드 시작
4. 비디오 녹화 시작
5. 비디오 녹화 중지
6. 비디오 모드 중지 및 리소스 정리

먼저 *VideoCapture* 개체 *VideoCapture m_VideoCapture = null* 을 만듭니다.

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

그런 다음 기록 하 고 시작 하는 데 사용할 매개 변수를 설정 합니다.

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

시작 되 면 기록을 시작 합니다.

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

기록이 시작 된 후에는 중지할 수 있도록 UI 나 동작을 업데이트할 수 있습니다. 다음 로그만

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

이후 시점에서 기록을 중지할 것입니다. 이는 예를 들어 타이머 또는 사용자 입력에서 발생할 수 있습니다.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

기록이 중지 된 후에는 비디오 모드를 중지 하 고 리소스를 정리 합니다.

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a>문제 해결
* 사용 가능한 해결 방법이 없습니다.
    * **웹캠** 기능이 프로젝트에 지정 되어 있는지 확인 합니다.

## <a name="see-also"></a>관련 항목
* [위치를 찾을 수 있는 카메라](locatable-camera.md)
