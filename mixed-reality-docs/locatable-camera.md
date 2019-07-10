---
title: 찾을 수 있는 카메라
description: HoloLens 전면 카메라, 작동 방법 및 프로필에 대 한 일반 정보 및 해결 방법을 개발자에 게 제공 합니다.
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: 카메라, hololens, 색 카메라, 연결, hololens 2, 컴퓨터 비전, fiducial cv 앞, 표식, qr 코드, qr, 사진, 비디오
ms.openlocfilehash: b80e201723f8f499a6d35008b9d308f93b925b1c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694534"
---
# <a name="locatable-camera"></a>찾을 수 있는 카메라

HoloLens 앞면의 사용자에 게 확인 하려면 앱을 사용 하도록 설정 하는 장치는 탑재 된 세계 지향 카메라를 포함 합니다. 스마트폰, 노트북 또는 데스크톱에서 색 카메라에 대 한 것 처럼 개발자가에 대 한 액세스 및 카메라 컨트롤입니다. 동일한 유니버설 windows [미디어 캡처](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) windows media foundation HoloLens 작업할 모바일 및 데스크톱에서 작동 하는 Api입니다. Unity [이러한 windows Api도 래핑](locatable-camera-in-unity.md) 일반 사진 및 비디오 (홀로그램 없이 또는)에서 카메라의 위치 및 큐브 뷰를 찾기 등의 작업에 대 한 HoloLens에서 카메라의 단순한 사용을 추상화 하는 장면입니다.

## <a name="device-camera-information"></a>장치 카메라 정보

### <a name="hololens-first-generation"></a>HoloLens (초기)

* 흰색 자동 분산, 자동 노출 및 전체 이미지 처리 파이프라인을 사용 하 여 고정된 포커스 (PV) 사진/비디오 카메라입니다.
* 카메라 활성화 될 때마다 전 세계 연결 흰색 개인 LED 켜 집니다.
* 카메라 30, 24, 20, 15 및 5 fps (모든 모드 16 9 가로 세로 비율을은) 다음과 같은 모드를 지원 합니다.:

  |  비디오  |  Preview  |  여전히  |  가로 뷰 필드 (H-FOV) |  제안 된 사용 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (비디오 안정화를 통해 기본 모드) | 
  |  해당 사항 없음 |  해당 사항 없음 |  2048x1152 |  67deg |  가장 높은 해상도 여전히 이미지 | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  비디오 안정화 전에 오버 스캔 (패딩) 확인 | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  오버 스캔을 사용 하 여 큰 FOV 비디오 모드 | 
  |  896x504 |  896x504 |  896x504 |  48deg |  전원 부족 이미지에 대 한 낮은 해상도 모드 처리 작업 | 

### <a name="hololens-2"></a>HoloLens 2

* 흰색 자동 분산, 자동 노출 및 전체 이미지 처리 파이프라인을 사용 하 여 자동 포커스 (PV) 사진/비디오 카메라입니다.
* 전 세계 연결 흰색 개인 LED 카메라 활성화 될 때마다 켜 집니다.
* HoloLens 2 다른 카메라 프로필을 지원합니다. 설명 하는 방법 [검색 하 고 카메라 기능을 선택](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles).
* 카메라 다음 프로필과 (모든 비디오 모드 16 9 가로 세로 비율을은)는 해상도 지원 합니다.:
  
  | 프로필                                         | 비디오     | Preview   | 여전히     | 프레임 속도 | 가로 뷰 필드 (H-FOV) | 제안 된 사용                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | 레거시, 0 BalancedVideoAndPhoto 100             | 2272x1278 | 2272x1278 |           | 15,30       | 64.69                            | 고품질 비디오 기록                |
  | 레거시, 0 BalancedVideoAndPhoto 100             | 896x504   | 896x504   |           | 15,30       | 64.69                            | 고품질 사진 캡처에 대 한 스트림 미리 보기 |
  | 레거시, 0 BalancedVideoAndPhoto 100             |           |           | 3904x2196 |             | 64.69                            | 고품질 사진 캡처                  |
  | BalancedVideoAndPhoto,120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64.69                            | 긴 기간 시나리오                     |
  | BalancedVideoAndPhoto,120                       | 1504x846  | 1504x846  |           | 15,30       | 64.69                            | 긴 기간 시나리오                     |
  | 비디오 회의 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100 BalancedVideoAndPhoto 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100 BalancedVideoAndPhoto 120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100 BalancedVideoAndPhoto 120 | 1128x636  |           |           | 15,30       | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100 BalancedVideoAndPhoto 120 | 960 x 540   |           |           | 15,30       | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100 BalancedVideoAndPhoto 120 | 760x428   |           |           | 15,30       | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100 BalancedVideoAndPhoto 120 | 640x360   |           |           | 15,30       | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100 BalancedVideoAndPhoto 120 | 500x282   |           |           | 15,30       | 64.69                            | 비디오 회의 긴 기간 시나리오 |
  | 비디오 회의 100 BalancedVideoAndPhoto 120 | 424x240   |           |           | 15,30       | 64.69                            | 비디오 회의 긴 기간 시나리오 |

>[!NOTE]
>활용할 수 있습니다 [혼합 현실 캡처](mixed-reality-capture.md) 홀로그램 및 비디오 안정화를 포함 하는 앱의 사진 또는 비디오를 수행 합니다.
>
>개발자는 고객 콘텐츠를 캡처할 때 최적의 상태로 표시 되도록 하려는 경우 앱을 만들 때 고려해 야 하는 고려 사항이 있습니다. 또한 (를 사용자 지정) 응용 프로그램 내에서 직접에서 혼합된 현실 캡처. 자세히 알아보세요 [현실 캡처 개발자를 위한 혼합](mixed-reality-capture-for-developers.md)합니다.

## <a name="locating-the-device-camera-in-the-world"></a>전 세계에서 장치 카메라를 찾기

HoloLens 사진 및 비디오를 사용 하는 경우 캡처된 프레임을 카메라의 렌즈 모델 뿐만 아니라 전 세계에서 카메라의 위치를 포함 합니다. 이 보강 된 이미징 시나리오에 대 한 실제 환경에서 카메라의 위치에 대 한 이유를 응용 프로그램 수 있습니다. 개발자가 즐겨 찾는 이미지 처리 또는 사용자 지정 컴퓨터 비전 라이브러리를 사용 하 여 고유한 시나리오를 롤백하지 창의적으로 수 있습니다.

HoloLens 설명서의 다른 위치에서 "카메라"는 "가상 게임 카메라" (으로 렌더링 하면 프러스텀 앱)를 참조할 수 있습니다. 그렇지 않으면 표시 된 경우가 아니면이 페이지에서 "카메라"은 실제 RGB 색 카메라를 가리킵니다.

세부 정보를 사용 하 여이 페이지 덮개를 [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference) 그러나도 Api 끌어오기 카메라 내장 함수를 사용 하 여 위치 클래스 [Media Foundation 특성](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)합니다. 참조 하십시오 합니다 [tracking 샘플 Holographic 얼굴](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) 자세한 내용은 합니다.

### <a name="images-with-coordinate-systems"></a>좌표계를 사용 하 여 이미지

각 이미지 프레임 (여부를 사진 또는 비디오) 포함을 [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 카메라 캡처를 사용 하 여 액세스할 수 있는 시점에 루트로 합니다 [coordinatesystem입니다](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) 프로그램의속성[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)합니다. 각 프레임에 있는 카메라 렌즈 모델에 대 한 설명을 포함 하는 또한 합니다 [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 속성입니다. 함께 이러한 변환을 정의할 각 픽셀에 대 한 광선을 그린 photons 픽셀 생성 되는 경로 나타내는 3D 공간에서. 이러한 표면이 다른 좌표 시스템을 프레임의 좌표계에서 변환의 확보 하 여 앱의 다른 콘텐츠에 관련 될 수 있습니다 (예:는 [고정 참조 프레임](coordinate-systems.md#stationary-frame-of-reference)). 요약 하면, 각 이미지 프레임 다음을 제공 합니다.
* 픽셀 (형식의 데이터를 RGB/NV12/JPEG/등)
* A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 캡처의 위치에서
* A [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 카메라의 렌즈 모드를 포함 하는 클래스

### <a name="camera-to-application-specified-coordinate-system"></a>응용 프로그램에서 지정한 좌표계에 카메라

'CameraIntrinsics' 및 'CameraCoordinateSystem'에서 응용 프로그램/세계 좌표 시스템을 이동 하려면 다음이 필요 합니다.

[Unity에서 찾을 수 있는 카메라](locatable-camera-in-unity.md): (따라서 CameraCoordinateSystem 변환에 걱정할 필요가 없습니다)에 자동으로 CameraToWorldMatrix PhotoCaptureFrame 클래스에 의해 제공 됩니다.

[DirectX에서 찾을 수 있는 카메라](locatable-camera-in-directx.md): 카메라의 좌표계 및 사용자 고유의 응용 프로그램 coordinate system(s) 간의 변환에 대 한 쿼리를 매우 간단한 방법을 보여 줍니다.

### <a name="distortion-error"></a>왜곡 오류

HoloLens에서 비디오 및 여전히 이미지 스트림을 시스템의 이미지 처리 파이프라인의 왜곡 전에 아닌 프레임 (미리 보기 스트림은 원래 왜곡 된 프레임을 포함 하는 데 사용) 응용 프로그램에 제공 됩니다. CameraIntrinsics만는 가능 하기 때문에 응용 프로그램 이미지 프레임 나타내는 완벽 한 pinhole 카메라 가정해 야를 undistortion 이미지 프로세서에서 작동 하는 단 수 여전히에서 그대로 오류가 최대 10 개의 픽셀 HoloLens (초기) CameraIntrinsics 프레임 메타 데이터에 사용할 때 여러 사용 사례, 예를 들어, 실제 포스터/표식, 홀로그램 맞추려는 및 표시 하는 경우이 오류는 중요 하지는 < 10px 오프셋 (약 홀로그램 2 미터 떨어진 위치에 대 한 11 mm)이이 왜곡 오류가 발생할 수 있습니다. 

## <a name="locatable-camera-usage-scenarios"></a>찾을 수 있는 카메라 사용 시나리오

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>캡처된 전 세계에서 사진 또는 비디오 표시

장치 카메라 프레임 이미지를 만든 경우 장치가 정확 하 게 위치를 표시할 수 있는 "카메라를 World" transform을 함께 제공 됩니다. 예를 들어 작은 holographic 아이콘 (CameraToWorld.MultiplyPoint(Vector3.zero)) 및도 그리기는 카메라 직면 하 고 있던 (CameraToWorld.MultiplyVector(Vector3.forward)) 방향의 작은 화살표는이 위치에 배치할 수 있습니다.

### <a name="tag--pattern--poster--object-tracking"></a>태그 / 패턴 / 포스터 / 추적 개체

많은 혼합된 현실 응용 프로그램 공간에서 추적 지점을 만들려면 인식할 수 있는 이미지 또는 시각적 패턴을 사용 합니다. 기준으로 개체를 가리키거나 알려진된 위치를 만들 다음 렌더링에 사용 됩니다. HoloLens 사용 fiducials (예: QR 코드를 사용 하 여 TV 모니터)를 사용 하 여 태그가 지정 된 실제 개체를 찾기, 홀로그램 fiducials를 위에 놓으면 및 태블릿을 통해 HoloLens와 통신 하는 설치 된 같은 비 HoloLens 장치를 사용 하 여 시각적으로 페어링 포함 됩니다. -Fi 합니다.

시각적 패턴을 인식 하 고 그런 다음 응용 프로그램 세계 좌표 공간에서 해당 개체를 배치, 하는 몇 가지 해야 합니다.
1. 이미지 패턴 인식 도구 키트, QR 코드, AR 태그, 얼굴 찾기, 원 추적기, OCR 등입니다.
2. 런타임 시 이미지 프레임을 수집 하 고 인식 계층에 전달
3. 환경 위치 또는 가능성이 world 광선에 다시 이미지 위치로 unproject 합니다. 참조 항목
4. 이러한 환경 위치 가상 모델 위치

몇 가지 중요 한 이미지 처리 링크:
* [OpenCV](http://opencv.org/)
* [QR 태그](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

장기 실행 이미지 인식 알고리즘을 사용 하 여 처리 하는 경우에 특히 대화형 응용 프로그램 프레임 속도 유지 하는 것은 중요 하며, 합니다. 이러한 이유로 다음 패턴을 흔히 사용:
1. 카메라 개체를 관리 하는 주 스레드:
2. 주 스레드: 요청 새 프레임 (비동기)
3. 새 프레임 스레드 추적 전달할 주 스레드:
4. 추적 스레드: 처리 요점을 수집 하는 이미지
5. 주 스레드: 이동 가상 모델에 맞게 찾을 요점
6. 2 단계에서 주 스레드: 반복

일부 이미지 표식 시스템만 단일 픽셀 위치를 제공 (다른 모든 변환을 제공이 섹션에서는 필요 하지 않을 경우), 가능한 위치는 빛 동등 합니다. 단일 3d 위치에 연결할 수 있습니다 다음 여러 광선을 활용 하 고 대략적인 교차점에서 최종 결과 찾습니다. 이렇게 하려면를 해야 합니다.
1. 카메라 이미지가 여러 개 수집 이동 하는 루프를 가져오기
2. 관련 된 기능이 지점과 해당 world 광선 찾기
3. 여러 world 광선을 사용 하 여 각 기능을 사전에 있는 경우 해당 광선의 교집합에 대 한 해결 하기 위해 다음 코드를 사용할 수 있습니다.

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

두 개 이상에 해당 하는 추적 된 태그의 위치를 지정 하는 사용자가 현재 시나리오에 맞게 modelled 장면을 배치할 수 있습니다. 무게를 가정할 수 없습니다, 하는 경우 다음 해야 세 태그가 위치 합니다. 사용 하 여 대부분의 경우 여기서 흰색 구 실시간은 단순한 색 구성표를 추적 태그 위치 및 파란색 구 모델링할 태그 위치를 나타내며이 시각적으로 맞춤 품질을 평가할 수 있습니다. 모든 응용 프로그램에서 다음 설정을 가정합니다.
* 두 개 이상에 해당 하는 모델링할 태그의 위치
* 하나는 장면에서 태그의 부모인 ' 보정 공간'
* 카메라 기능 식별자
* (것은 부모 공간을 자체 modelled 표식이 없습니다 이동할 신중 하 게 다른 연결을 기준으로 하는 위치 이므로) 실시간 태그를 사용 하 여 modelled 태그에 맞게 보정 공간을 이동 하는 동작입니다.

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

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>추적 또는 식별 태그가 지정 된 고정 또는 이동 실제 개체/얼굴 Led 또는 다른 인식기 라이브러리를 사용 하 여

예를 들면 다음과 같습니다.
* Led 사용 하 여 산업 로봇 (또는 느린 이동에 대 한 QR 코드 개체)
* 식별 및 단체 실에 개체를 인식 합니다.
* 식별 하 고 (예: 위치 holographic 대화 상대 카드 얼굴을 통해) 대화방 참가자를 인식 합니다.

## <a name="see-also"></a>참조
* [DirectX의 위치를 찾을 수 있는 카메라](locatable-camera-in-directx.md)
* [Unity의 위치를 찾을 수 있는 카메라](locatable-camera-in-unity.md)
* [혼합 현실 캡처](mixed-reality-capture.md)
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
* [미디어 캡처 소개](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Holographic 얼굴 추적 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
