---
title: Azure Spatial Anchors 자습서 - 5. Android 및 iOS용 Azure Spatial Anchors
description: 이 과정을 완료하면 Mixed Reality Toolkit 및 Azure Spatial Anchors가 포함된 Unity 프로젝트를 Android 및 iOS에 배포하는 방법을 알아볼 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens, Android, iOS
ms.localizationpriority: high
ms.openlocfilehash: 8c63204948b3e4aa3d25e5b2ca948798726f0838
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376545"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Android 및 iOS용 Azure Spatial Anchors

이 자습서에서는 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인을 사용하여 Android 및 iOS 디바이스에 프로젝트를 빌드하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* Unity AR Foundation 및 ARCore XR 플러그 인을 사용하여 Android 디바이스에 프로젝트를 빌드하는 방법에 대해 알아봅니다.
* Unity AR Foundation 및 ARKit XR 플러그 인을 사용하여 iOS 디바이스에 프로젝트를 빌드하는 방법에 대해 알아봅니다.

## <a name="installing-inbuilt-unity-packages"></a>기본 제공 Unity 패키지 설치

이 섹션에서는 다음과 같은 기본 제공 패키지를 업그레이드하고 설치합니다.

* AR Foundation 3.1.3
* Legacy Input Helpers 2.1.4
* Android 지원을 위한 ARCore XR 플러그 인 3.1.3
* iOS 지원을 위한 ARKit XR 플러그 인 3.1.3

> [!CAUTION]
> 모든 버전이 MRTK와 호환되는 것은 아니며 특정 버전만 함께 작동하므로 위에 나열된 정확한 버전을 설치해야 합니다.

Unity 메뉴에서 **창** > **패키지 관리자**를 차례로 선택하여 [패키지 관리자] 창을 연 다음, **AR Foundation** > **3.1.3**을 선택하고 **3.1.3으로 업데이트** 단추를 클릭하여 패키지를 업데이트합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

필요에 따라 동일한 프로세스를 수행하여 나머지 패키지를 가져옵니다.

> [!NOTE]
> Android용으로 이 프로젝트를 개발하는 경우 ARKit XR 플러그 인 패키지를 설치할 필요가 없습니다. 마찬가지로 iOS용으로 이 프로젝트를 개발하는 경우 ARCore XR 플러그 인을 설치할 필요가 없습니다.

## <a name="configure-mrtk-for-ar-foundation-camera"></a>AR Foundation Camera에 대한 MRTK 구성

이 섹션에서는 모바일 디바이스에 배포하기 위해 MRTK를 구성하는 방법을 알아봅니다.

Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택합니다. 그런 다음, Inspector(인스펙터) 창에서 **Camera** 탭을 선택하고 카메라 프로필을 복제한 다음, 적절한 이름(예: **AzureSpatialAnchors_ARCameraProfile**)을 지정합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> MRTK 프로필을 복제하는 방법은 [Mixed Reality Toolkit 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.

Inspector(인스펙터) 창에서 **Camera** 탭을 선택한 상태로 **Camera Setting Providers**(카메라 설정 공급자)를 펼쳐서 **+ Add Camera Setting Provider**(카메라 설정 공급자 추가) 단추를 클릭한 다음, 새로 추가한 **New data provider 1**(새 데이터 공급자 1)을 펼칩니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

**유형** 드롭다운을 사용하여 유형을 **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**로 변경합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택한 상태로, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 다음 구성 요소를 추가합니다.

* AR 앵커 관리자(스크립트)
* DisableDiagnosticsSystem(스크립트)

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> AR 참조 지점 관리자(스크립트) 구성 요소를 추가하면 AR 세션 원본(스크립트) 구성 요소가 AR 참조 지점 관리자(스크립트) 구성 요소에 필요하기 때문에 자동으로 추가됩니다.

## <a name="building-your-application-to-your-android-device"></a>Android 디바이스에 애플리케이션 빌드

이 섹션에서는 프로젝트를 구성하고 빌드하여 Android 디바이스에 배포하는 방법을 알아봅니다.

Unity 메뉴에서 **파일** > **빌드 설정...** 을 선택하여 빌드 설정 창을 연 다음, 플랫폼을 Android로 전환합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> 빌드 플랫폼을 전환하는 방법은 [빌드 플랫폼 전환](mr-learning-base-02.md#switching-the-build-platform) 지침을 참조하세요.

빌드 설정 창을 닫습니다.

Unity 메뉴에서 **Mixed Reality Toolkit** > **유틸리티** > **Unity 프로젝트 구성**을 선택하여 **MRTK 프로젝트 구성기** 창을 열고 모든 옵션이 선택되어 있는지 확인한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 플레이어 설정 창을 연 다음, **플레이어** >  **기타 설정** 섹션을 찾아서 **Vulkan**을 선택하고 **"-"** 기호를 클릭하여 제거합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

플레이어 설정 창을 닫고 빌드 설정 창을 다시 엽니다.

빌드 설정 창에서 **Add Open Scenes**(열려 있는 장면 추가) 단추를 클릭하여 현재 장면을 **Scenes In Build**(빌드의 장면) 목록에 추가합니다. 그런 다음, USB 케이블을 사용하여 Android 디바이스를 컴퓨터에 연결하고 **Run Device**(디바이스 실행) 드롭다운 목록에서 선택합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Run Device(디바이스 실행) 드롭다운 목록에 디바이스가 보이지 않으면 드롭다운 목록 옆에 있는 새로 고침 단추를 눌러야 할 수도 있습니다.

빌드 설정 창에서 **빌드 및 실행** 단추를 클릭하여 Build Android(Android 빌드) 창을 엽니다.

빌드를 저장할 적당한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택한 다음, apk에 적절한 이름(예: _MRTKTutorials-AzureSpatialAnchors_)을 지정하고 **저장** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
Android SDK, NDK 및 JDK 모듈과 관련된 Unity 콘솔 창에 오류가 발생하면 Unity Hub를 열고 Android 빌드 지원 모듈과 관련된 Android 빌드 지원 모듈을 설치해야 합니다.

빌드 프로세스가 완료되면 앱이 Android 디바이스에 자동으로 로드됩니다.

## <a name="building-your-application-to-your-ios-device"></a>iOS 디바이스에 애플리케이션 빌드

이 섹션에서는 프로젝트를 구성하고 빌드하여 iOS 디바이스에 배포하는 방법을 알아봅니다.

Unity 메뉴에서 **파일** > **빌드 설정...** 을 선택하여 빌드 설정 창을 열고 플랫폼을 iOS로 전환합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> 빌드 플랫폼을 전환하는 방법은 [빌드 플랫폼 전환](mr-learning-base-02.md#switching-the-build-platform) 지침을 참조하세요.

빌드 설정 창을 닫습니다.

Unity 메뉴에서 **Mixed Reality Toolkit** > **유틸리티** > **Unity 프로젝트 구성**을 선택하여 **MRTK 프로젝트 구성기** 창을 열고 모든 옵션이 선택되어 있는지 확인한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 선택하여 플레이어 설정 창을 연 다음, **플레이어** >  **기타 설정** 섹션을 찾아서 **Strip Engine Code**(엔진 코드 스트립) 확인란 선택을 취소하여 사용하지 않도록 설정합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

플레이어 설정 창을 닫고 **빌드** 설정 창을 다시 엽니다.

빌드 설정 창에서 **Add Open Scenes**(열려 있는 장면 추가) 단추를 클릭하여 현재 장면을 **Scenes In Build**(빌드의 장면) 목록에 추가합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

빌드 설정 창에서 **빌드** 단추를 클릭하여 Build iOS(iOS 빌드) 창을 엽니다.

Xcode 프로젝트를 저장할 적당한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어서 적절한 이름(예: _MRTKTutorials-AzureSpatialAnchors_)을 지정한 다음, **폴더 선택** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

빌드 프로세스가 완료되면 [Xcode 프로젝트 내보내기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) 지침에 따라 Xcode 프로젝트를 iOS 디바이스에 배포하는 방법을 알아봅니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인을 사용하여 Android 및 iOS 디바이스에 프로젝트를 빌드하는 방법을 알아보았습니다.
