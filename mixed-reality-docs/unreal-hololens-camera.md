---
title: Unreal의 HoloLens 카메라
description: Unreal에서 HoloLens 카메라 사용 가이드
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 카메라, 세 번째 카메라, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840122"
---
# <a name="hololens-camera-in-unreal"></a>Unreal의 HoloLens 카메라

## <a name="third-camera-mixed-reality-capture"></a>세 번째 혼합 현실 캡처

세 번째 카메라 MRC(Mixed Reality Capture)는 아이 텍스처 관점이 아닌 HoloLens 바이저의 카메라 관점에서 혼합 현실 캡처를 렌더링하는 데 사용할 수 있습니다.  이를 통해 MRC 영상에서 실제 세계와 홀로그램의 매핑이 개선됩니다. 

세 번째 카메라 MRC 사용을 선택하려면 원하는 비디오 크기로 SetEnabledMixedRealityCamera 및 ResizeMixedRealityCamera를 호출합니다. 

![세 번째 카메라](images/unreal-camera-3rd.PNG)

그런 다음 HoloLens 디바이스 포털에서 MRC 비디오를 녹화합니다. 

## <a name="pv-camera"></a>PV 카메라

런타임 시 게임에서 웹캠 텍스처를 검색할 수도 있습니다.  HoloLens에서 웹캠 텍스처를 가져오려면 먼저 프로젝트 설정> 플랫폼> HoloLens> 기능의 Unreal 에디터에서 "웹캠" 기능이 선택되어 있는지 확인합니다. 

StartCameraCapture 함수를 사용하여 런타임 시 웹캠 사용을 선택합니다.  StopCameraCapture 함수를 사용하여 캡처를 중지합니다. 

![Camera 시작 중지](images/unreal-camera-startstop.PNG)

카메라 이미지를 렌더링하려면 먼저 프로젝트의 재질을 기반으로 하는 동적 재질 인스턴스를 만듭니다.  이 경우 PVCamMat 이라는 재질을 기반으로 합니다.  이를 Material Instance Dynamic Object Reference 유형의 변수에 설정합니다.  그런 다음 장면에서 카메라 피드를 이 새로운 동적 재질 인스턴스에 렌더링할 개체의 재질을 설정하고 카메라 이미지를 재료에 바인딩하는 데 사용할 타이머를 시작합니다. 

![카메라 렌더링](images/unreal-camera-render.PNG)

이 타이머에 대한 새로운 기능을 만들고(이 경우 MaterialTimer), GetARCameraImage를 호출하여 웹캠에서 텍스처를 가져옵니다.  이 텍스처가 유효한 경우 셰이더의 텍스처 파라미터를 이 이미지에 설정합니다.  그렇지 않으면 재질 타이머를 다시 시작합니다. 

![카메라 텍스처](images/unreal-camera-texture.PNG)

카메라 이미지를 올바르게 표시하려면 재질에 SetTextureParameterValue의 이름과 일치하는 매개 변수가 색상 항목에 바인딩되어 있어야 합니다. 

![카메라 텍스처](images/unreal-camera-material.PNG)

## <a name="see-also"></a>참고 항목
* [위치를 찾을 수 있는 카메라](locatable-camera.md)
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
