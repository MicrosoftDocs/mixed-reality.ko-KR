---
title: 과정이 카메라
description: HoloLens front camera 카메라, 작동 방식 및 개발자가 사용할 수 있는 프로필 및 해상도에 대 한 일반 정보입니다.
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: 카메라, hololens, 컬러 카메라, 전면, hololens 2, cv, 컴퓨터 비전, fiducial, 표식, qr 코드, qr, 사진, 비디오
ms.openlocfilehash: b80e201723f8f499a6d35008b9d308f93b925b1c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694534"
---
# <a name="locatable-camera"></a>과정이 카메라

HoloLens에는 앱이 사용자에 게 표시 되는 내용을 볼 수 있도록 장치 앞에 탑재 된 전 세계 카메라가 포함 되어 있습니다. 개발자는 스마트폰, 노트북 또는 데스크톱에서 색 카메라를 사용할 때와 마찬가지로 카메라에 액세스 하 고 해당 카메라를 제어할 수 있습니다. 모바일 및 데스크톱에서 작동 하는 동일한 유니버설 windows [미디어 캡처](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) 및 windows Media foundation Api는 HoloLens에서 작업 합니다. 또한 Unity는 일반적인 사진과 비디오 (holograms 유무에 관계 없이)를 사용 하 고 카메라의 위치와 장면의 원근감을 찾는 등의 작업을 위해 HoloLens에서 카메라의 간단한 사용을 추상화 하도록 [이러한 Windows api를 래핑 했습니다](locatable-camera-in-unity.md) .

## <a name="device-camera-information"></a>장치 카메라 정보

### <a name="hololens-first-generation"></a>HoloLens (첫 번째 생성)

* 자동 흰색 잔액, 자동 노출 및 전체 이미지 처리 파이프라인이 있는 PV (focus photo/video) 카메라
* 카메라가 활성화 될 때마다 전 세계의 개인 개인 정보 취급 LED가 켜 집니다.
* 카메라는 30, 24, 20, 15, 5fps의 다음 모드 (모든 모드에서 16:9 가로 세로 비율)를 지원 합니다.

  |  비디오  |  미리 보기  |  실패할  |  뷰의 가로 필드 (H-FOV) |  권장 사용법 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (비디오 안정화를 사용 하는 기본 모드) | 
  |  해당 사항 없음 |  해당 사항 없음 |  2048x1152 |  67deg |  가장 높은 해상도의 이미지 | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  비디오 안정화 전 Overscan (패딩) 해상도 | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Overscan를 사용 하는 넓은 FOV 비디오 모드 | 
  |  896x504 |  896x504 |  896x504 |  48deg |  이미지 처리 작업에 대 한 낮은 전원/저해상도 모드 | 

### <a name="hololens-2"></a>HoloLens 2

* 자동 흰색 잔액, 자동 노출 및 전체 이미지 처리 파이프라인이 있는 PV (자동 포커스 사진/비디오) 카메라
* 카메라가 활성화 될 때마다 전 세계의 개인 개인 정보 취급 LED가 켜 집니다.
* HoloLens 2는 다른 카메라 프로필을 지원 합니다. [카메라 기능을 검색 하 고 선택](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles)하는 방법을 알아봅니다.
* 카메라는 다음 프로필 및 해상도를 지원 합니다 (모든 비디오 모드는 16:9 가로 세로 비율).
  
  | 프로필                                         | 비디오     | 미리 보기   | 실패할     | 프레임 속도 | 뷰의 가로 필드 (H-FOV) | 권장 사용법                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | 레거시, 0 BalancedVideoAndPhoto, 100             | 2272x1278 | 2272x1278 |           | 15, 30       | 64.69                            | 고품질 비디오 녹화                |
  | 레거시, 0 BalancedVideoAndPhoto, 100             | 896x504   | 896x504   |           | 15, 30       | 64.69                            | 고품질 사진 캡처에 대 한 미리 보기 스트림 |
  | 레거시, 0 BalancedVideoAndPhoto, 100             |           |           | 3904x2196 |             | 64.69                            | 고품질 사진 캡처                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30       | 64.69                            | 긴 기간 시나리오                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15, 30       | 64.69                            | 긴 기간 시나리오                     |
  | 비디오 회의, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30, 60    | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100                           | 1504x846  | 1504x846  |           | 5, 15, 30, 60  | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100 BalancedVideoAndPhoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15, 30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100 BalancedVideoAndPhoto, 120 | 1280x720  | 1280x720  | 1280x720  | 15, 30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100 BalancedVideoAndPhoto, 120 | 1128x636  |           |           | 15, 30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100 BalancedVideoAndPhoto, 120 | 960 x 540   |           |           | 15, 30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15, 30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100 BalancedVideoAndPhoto, 120 | 640x360   |           |           | 15, 30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15, 30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15, 30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |

>[!NOTE]
>고객은 [혼합 현실 캡처](mixed-reality-capture.md) 를 활용 하 여 holograms 및 비디오 안정화를 포함 하는 앱의 비디오 또는 사진을 찍을 수 있습니다.
>
>개발자는 응용 프로그램을 만들 때 고객이 콘텐츠를 캡처할 때 최대한 적절 하 게 보이도록 하려는 경우 고려해 야 할 사항이 있습니다. 앱 내에서 직접 혼합 현실 캡처를 사용 하도록 설정 (및 사용자 지정) 할 수도 있습니다. [개발자를 위한 혼합 현실 캡처에서](mixed-reality-capture-for-developers.md)자세히 알아보세요.

## <a name="locating-the-device-camera-in-the-world"></a>전 세계에서 장치 카메라 찾기

HoloLens에서 사진과 비디오를 사용 하는 경우 캡처된 프레임에는 카메라의 렌즈 모델 뿐만 아니라 전 세계의 카메라 위치가 포함 됩니다. 이를 통해 응용 프로그램은 확대 된 이미징 시나리오에 대 한 실제 환경에서 카메라의 위치를 지정할 수 있습니다. 개발자는 선호 하는 이미지 처리 또는 사용자 지정 컴퓨터 비전 라이브러리를 사용 하 여 자신의 시나리오를 창의적 수 있습니다.

HoloLens 설명서의 다른 곳에서 "카메라"는 "가상 게임 카메라" (앱에서 렌더링 하는 것과 같은)를 참조할 수 있습니다. 달리 지정 되지 않은 경우이 페이지의 "카메라"는 실제 RGB 색 카메라를 참조 합니다.

이 페이지에 대 한 세부 정보는 [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference) 클래스를 사용 하지만 [미디어 파운데이션 특성](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)을 사용 하 여 카메라 내장 함수 및 위치를 끌어오는 api도 있습니다. 자세한 내용은 [Holographic face 추적 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) 을 참조 하세요.

### <a name="images-with-coordinate-systems"></a>좌표계가 있는 이미지

각 이미지 프레임 (사진 또는 비디오)에는 [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)의 [CoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) 속성을 사용 하 여 액세스할 수 있는 캡처 시점에 카메라에서 [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 를 포함 합니다. 또한 각 프레임에는 [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 속성에서 찾을 수 있는 카메라 렌즈 모델에 대 한 설명이 포함 되어 있습니다. 이러한 변환은 함께 각 픽셀에 대해 픽셀을 생성 한 photons에서 가져온 경로를 나타내는 3D 공간의 광선을 정의 합니다. 이러한 광선은 프레임의 좌표계에서 다른 좌표계 (예: [고정 참조 프레임](coordinate-systems.md#stationary-frame-of-reference))로 변환을 가져와서 앱의 다른 콘텐츠와 관련 될 수 있습니다. 요약 하자면, 각 이미지 프레임은 다음을 제공 합니다.
* 픽셀 데이터 (RGB/NV12/JPEG/등 형식)
* 캡처 위치의 [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)
* 카메라의 렌즈 모드가 포함 된 [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 클래스입니다.

### <a name="camera-to-application-specified-coordinate-system"></a>응용 프로그램에서 지정한 좌표계로 카메라

' CameraIntrinsics ' 및 ' CameraCoordinateSystem '에서 응용 프로그램/지역 좌표계로 이동 하려면 다음이 필요 합니다.

[Unity의 과정이 카메라](locatable-camera-in-unity.md): CameraToWorldMatrix는 PhotoCaptureFrame 클래스에서 자동으로 제공 되므로 CameraCoordinateSystem 변환에 대해 걱정할 필요가 없습니다.

[DirectX의 과정이 카메라](locatable-camera-in-directx.md): 카메라의 좌표계와 사용자 고유의 응용 프로그램 좌표계 간에 변환을 쿼리 하는 매우 간단한 방법을 보여 줍니다.

### <a name="distortion-error"></a>왜곡 오류

HoloLens에서 비디오와 스틸 이미지 스트림은 응용 프로그램에서 프레임을 사용할 수 있게 되기 전에 시스템의 이미지 처리 파이프라인에서 undistorted 됩니다 (미리 보기 스트림은 원래 왜곡 된 프레임을 포함 함). CameraIntrinsics만 사용할 수 있기 때문에 응용 프로그램에서 이미지 프레임은 완벽 한 pinhole 카메라를 나타낸다고 가정 해야 하지만 이미지 프로세서의 왜곡 함수는 HoloLens에서 최대 10 픽셀의 오류를 발생 시킬 수 있습니다 (첫 번째 생성). 프레임 메타 데이터에서 CameraIntrinsics를 사용 하는 경우 많은 사용 사례에서이 오류는 중요 하지 않지만, 예를 들어 실제 세계의 포스터/표식에 holograms를 맞추는 경우 10px 오프셋 (holograms에 약 11mm이 배치 됨)이 발생 하는 것을 < 알 수 있습니다. 

## <a name="locatable-camera-usage-scenarios"></a>과정이 카메라 사용 시나리오

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>캡처된 전 세계에 사진 또는 비디오 표시

장치 카메라 프레임에는 이미지를 찍은 시간을 정확히 표시 하는 데 사용할 수 있는 "전 세계 카메라" 변환이 포함 되어 있습니다. 예를 들어이 위치 (MultiplyPoint (Vector3))에 작은 holographic 아이콘을 배치 하 고 카메라가 연결 된 방향으로 약간의 화살표 (CameraToWorld (MultiplyVector))를 그릴 수 있습니다.

### <a name="tag--pattern--poster--object-tracking"></a>태그/패턴/포스터/개체 추적

많은 혼합 현실 응용 프로그램에서는 인식할 수 있는 이미지 또는 시각적 패턴을 사용 하 여 공간에 추적 가능 점을 만듭니다. 그런 다음이 요소를 기준으로 개체를 렌더링 하거나 알려진 위치를 만드는 데 사용 됩니다. HoloLens를 사용 하는 경우 fiducials로 태그가 지정 된 실제 세계 개체 (예: QR 코드를 사용 하는 TV 모니터)를 찾고, holograms를 fiducials에 배치 하 고,를 통해 HoloLens와 통신 하도록 설정 된 태블릿과 같은 비 HoloLens 장치와 시각적으로 연결 하는 것이 포함 됩니다. Wi-fi.

시각적 패턴을 인식 한 다음이 개체를 응용 프로그램의 세계 공간에 놓으려면 다음과 같은 몇 가지 작업을 수행 해야 합니다.
1. QR 코드, AR 태그, 얼굴 찾기, 원 추적기, OCR 등의 이미지 패턴 인식 도구 키트입니다.
2. 런타임에 이미지 프레임을 수집 하 여 인식 계층으로 전달 합니다.
3. 이미지 위치를 세계 위치 또는 세계 광선으로 다시 프로젝션 합니다. 참조 항목
4. 이러한 세계 위치에 가상 모델 배치

몇 가지 중요 한 이미지 처리 링크:
* [OpenCV](http://opencv.org/)
* [QR 태그](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

특히 장기 실행 이미지 인식 알고리즘을 처리할 때는 대화형 응용 프로그램 프레임 률을 유지 하는 것이 중요 합니다. 이러한 이유로 일반적으로 다음과 같은 패턴을 사용 합니다.
1. 주 스레드: 카메라 개체를 관리 합니다.
2. 주 스레드: 새 프레임 (비동기)을 요청 합니다.
3. 주 스레드: 추적 스레드에 새 프레임 전달
4. 추적 스레드: 키 요소를 수집 하는 이미지를 처리 합니다.
5. 주 스레드: 찾은 키 지점과 일치 하도록 가상 모델을 이동 합니다.
6. 주 스레드: 2 단계에서 반복

일부 이미지 표식 시스템은 단일 픽셀 위치만 제공 합니다 .이 경우 다른 항목은이 섹션이 필요 하지 않은 전체 변환을 제공 하며,이는 가능한 위치의 광선과 동일 합니다. 단일 3d 위치로 이동 하려면 여러 광선을 활용 하 여 대략적인 교차를 기준으로 최종 결과를 찾을 수 있습니다. 이렇게 하려면 다음을 수행 해야 합니다.
1. 여러 카메라 이미지를 수집 하는 루프 가져오기
2. 연결 된 기능 지점과 해당 세계 광선 찾기
3. 여러 가지 세계 광선을 포함 하는 기능 사전이 있는 경우 다음 코드를 사용 하 여 이러한 광선의 교차를 해결할 수 있습니다.

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

두 개 이상의 추적 된 태그 위치가 지정 된 경우 사용자의 현재 시나리오에 맞게 모델링할 장면을 배치할 수 있습니다. 중력을 가정할 수 없는 경우 세 가지 태그 위치가 필요 합니다. 대부분의 경우 흰색은 실시간 추적 된 태그 위치를 나타내고 파란색 구는 모델링할 태그 위치를 나타내는 간단한 색 구성표를 사용 합니다 .이를 통해 사용자는 맞춤 품질을 시각적으로 평가할 수 있습니다. 모든 응용 프로그램에서 다음 설정을 가정 합니다.
* 모델링할 태그 위치 둘 이상
* 장면에 있는 하나의 ' 보정 공간 '은 태그의 부모입니다.
* 카메라 기능 식별자
* 모델링할 태그를 실시간 태그와 맞추기 위해 보정 공간을 이동 하는 동작입니다. 모델링할 표식 자체가 아닌 부모 공간은 이동 하는 것이 좋습니다.

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Led 또는 다른 인식기 라이브러리를 사용 하 여 태그가 지정 된 고정 또는 실제 개체/얼굴 이동 추적 또는 식별

예를 들면 다음과 같습니다.
* Led가 있는 산업 로봇 (또는 느린 개체 이동에 대 한 QR 코드)
* 대화방의 개체 식별 및 인식
* 대화방에서 사람 식별 및 인식 (예: 얼굴에 holographic 연락처 카드 넣기)

## <a name="see-also"></a>참조
* [DirectX의 위치를 찾을 수 있는 카메라](locatable-camera-in-directx.md)
* [Unity의 위치를 찾을 수 있는 카메라](locatable-camera-in-unity.md)
* [혼합 현실 캡처](mixed-reality-capture.md)
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
* [미디어 캡처 소개](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Holographic face 추적 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
