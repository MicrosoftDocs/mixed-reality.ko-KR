---
title: Unity에서 찾을 수 있는 카메라
description: HoloLens Unity에서 찾을 수 있는 카메라 사용 합니다.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 사진, 비디오, hololens, 카메라, unity, 찾을 수 있는
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601770"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="bdb5d-104">Unity에서 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="bdb5d-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="bdb5d-105">사진 비디오 카메라에 대 한 기능을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="bdb5d-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="bdb5d-106">"웹캠" 기능을 사용 하는 앱에 대 한 선언 해야 합니다 [카메라](locatable-camera.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="bdb5d-107">Unity 편집기에서 "> 프로젝트 설정 > Player 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="bdb5d-108">"Windows Store" 탭을 클릭</span><span class="sxs-lookup"><span data-stu-id="bdb5d-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="bdb5d-109">"게시 설정 > 기능" 섹션을 확인 합니다 **웹캠** 하 고 **마이크** 기능</span><span class="sxs-lookup"><span data-stu-id="bdb5d-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="bdb5d-110">단일 작업을 한 번에 카메라를 사용 하 여 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="bdb5d-111">(사진, 비디오 또는 없음) 모드에서 카메라를 현재 결정할 UnityEngine.XR.WSA.WebCam.Mode를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="bdb5d-112">사진 캡처</span><span class="sxs-lookup"><span data-stu-id="bdb5d-112">Photo Capture</span></span>

<span data-ttu-id="bdb5d-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="bdb5d-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="bdb5d-114">**형식:** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="bdb5d-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="bdb5d-115">합니다 *PhotoCapture* 유형을 사진 사진 비디오 카메라를 사용 하 여 계속 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="bdb5d-116">사용 하 여 일반적인 패턴 *PhotoCapture* 사진을 촬영 하는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="bdb5d-117">만들기는 *PhotoCapture* 개체</span><span class="sxs-lookup"><span data-stu-id="bdb5d-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="bdb5d-118">만들기는 *CameraParameters* 원하는 설정 사용 하 여 개체</span><span class="sxs-lookup"><span data-stu-id="bdb5d-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="bdb5d-119">시작을 통해 사진 모드 *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="bdb5d-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="bdb5d-120">원하는 찍기</span><span class="sxs-lookup"><span data-stu-id="bdb5d-120">Take the desired photo</span></span>
    * <span data-ttu-id="bdb5d-121">(선택 사항) 해당 그림이 상호 작용</span><span class="sxs-lookup"><span data-stu-id="bdb5d-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="bdb5d-122">사진 모드를 중지 하 고 리소스 정리</span><span class="sxs-lookup"><span data-stu-id="bdb5d-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="bdb5d-123">일반적인 설정 PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="bdb5d-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="bdb5d-124">같은 위의 처음 3 단계 먼저 모든 세 가지 용도로</span><span class="sxs-lookup"><span data-stu-id="bdb5d-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="bdb5d-125">만드는 것으로 시작 된 *PhotoCapture* 개체</span><span class="sxs-lookup"><span data-stu-id="bdb5d-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="bdb5d-126">다음은 개체를 저장, 매개 변수를 설정 하 고 사진 모드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="bdb5d-127">마지막으로도 사용 하 여 여기에 제시 된 코드 정리 동일한</span><span class="sxs-lookup"><span data-stu-id="bdb5d-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="bdb5d-128">이러한 단계 후 캡처하는 사진 유형을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="bdb5d-129">파일에 사진을 캡처합니다</span><span class="sxs-lookup"><span data-stu-id="bdb5d-129">Capture a Photo to a File</span></span>

<span data-ttu-id="bdb5d-130">가장 간단한 작업이 파일에 직접 사진을 캡처하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="bdb5d-131">JPG 또는 PNG 사진을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="bdb5d-132">사진 모드를 성공적으로 시작 하는 경우 이제 사진을 촬영 하 고 디스크에 저장</span><span class="sxs-lookup"><span data-stu-id="bdb5d-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="bdb5d-133">디스크에 사진을 캡처한 후 사진 모드를 종료 하 고이 개체 정리</span><span class="sxs-lookup"><span data-stu-id="bdb5d-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="bdb5d-134">캡처는 Texture2D에 사진</span><span class="sxs-lookup"><span data-stu-id="bdb5d-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="bdb5d-135">Texture2D 데이터를 캡처할 때 프로세스를 디스크에 캡처하기 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="bdb5d-136">위 프로세스 설정을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-136">We will follow the set up process above.</span></span>

<span data-ttu-id="bdb5d-137">*OnPhotoModeStarted*를 메모리에 프레임을 캡처합니다 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="bdb5d-138">다음 질감에 결과 적용 하 고 일반적인 위의 코드 정리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="bdb5d-139">원시 바이트를 사용 하 여 사진 및 상호 작용을 캡처</span><span class="sxs-lookup"><span data-stu-id="bdb5d-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="bdb5d-140">메모리 내의 원시 바이트를 조작할 프레임을 따르 설정 단계 위와 동일 및 *OnPhotoModeStarted* 사진을 캡처하는 Texture2D와 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="bdb5d-141">차이점은 *OnCapturedPhotoToMemory* 에서는 수 원시 바이트를 가져오기 하 고 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="bdb5d-142">이 예제에서는 만듭니다는 *목록<Color>*  추가 될 수 있는 처리 또는 통해 질감을 적용할 *SetPixels()*</span><span class="sxs-lookup"><span data-stu-id="bdb5d-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="bdb5d-143">비디오 캡처</span><span class="sxs-lookup"><span data-stu-id="bdb5d-143">Video Capture</span></span>

<span data-ttu-id="bdb5d-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="bdb5d-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="bdb5d-145">**형식:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="bdb5d-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="bdb5d-146">*VideoCapture* 기능이 매우 비슷한 *PhotoCapture*합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="bdb5d-147">두 개의 차이가 프레임 당 두 번째 (FPS) 값을 지정 해야 하 고. mp4 파일로 디스크에 직접 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="bdb5d-148">사용 하는 단계 *VideoCapture* 는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="bdb5d-149">만들기는 *VideoCapture* 개체</span><span class="sxs-lookup"><span data-stu-id="bdb5d-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="bdb5d-150">만들기는 *CameraParameters* 원하는 설정 사용 하 여 개체</span><span class="sxs-lookup"><span data-stu-id="bdb5d-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="bdb5d-151">비디오 모드를 통해 시작 *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="bdb5d-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="bdb5d-152">비디오 녹화 시작</span><span class="sxs-lookup"><span data-stu-id="bdb5d-152">Start recording video</span></span>
5. <span data-ttu-id="bdb5d-153">비디오 녹화 중지</span><span class="sxs-lookup"><span data-stu-id="bdb5d-153">Stop recording video</span></span>
6. <span data-ttu-id="bdb5d-154">비디오 모드를 중지 하 고 리소스 정리</span><span class="sxs-lookup"><span data-stu-id="bdb5d-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="bdb5d-155">만드는 것으로 시작 우리의 *VideoCapture* 개체 *VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="bdb5d-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="bdb5d-156">에서는 다음을 설정 기록 및 시작에 사용 하려는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="bdb5d-157">녹음/녹화 시작 되 면 예정</span><span class="sxs-lookup"><span data-stu-id="bdb5d-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="bdb5d-158">기록 시작 된 후 중지를 사용 하도록 설정 하려면 UI 또는 동작을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="bdb5d-159">여기에서는 로그인</span><span class="sxs-lookup"><span data-stu-id="bdb5d-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="bdb5d-160">나중에 기록을 중지 하려고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="bdb5d-161">이 타이머 또는 사용자 입력을 예를 들어에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="bdb5d-162">녹음/녹화를 중지 되 고 나면 비디오 모드를 중지 하 고 리소스를 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="bdb5d-163">문제 해결</span><span class="sxs-lookup"><span data-stu-id="bdb5d-163">Troubleshooting</span></span>
* <span data-ttu-id="bdb5d-164">사용할 수 없는 해결 방법</span><span class="sxs-lookup"><span data-stu-id="bdb5d-164">No resolutions are available</span></span>
    * <span data-ttu-id="bdb5d-165">확인 합니다 **웹캠** 기능 프로젝트에 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb5d-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdb5d-166">관련 항목</span><span class="sxs-lookup"><span data-stu-id="bdb5d-166">See Also</span></span>
* [<span data-ttu-id="bdb5d-167">찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="bdb5d-167">Locatable camera</span></span>](locatable-camera.md)
