---
title: Azure Spatial Anchors 자습서 - 1. Azure Spatial Anchors 시작
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 385b302f3a2b9ad80527387353746947d91e3aa3
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216304"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure Spatial Anchors 시작

## <a name="overview"></a>개요

HoloLens 2 자습서의 두 번째 시리즈를 시작합니다. 4부로 구성된 이 자습서 시리즈에서는 Azure Spatial Anchors의 기본 사항에 대해 알아봅니다.

첫 번째 자습서인 이 [Azure Spatial Anchors 시작](mrlearning-asa-ch1.md)에서는 Azure 세션을 시작 및 중지하고 단일 디바이스에서 Azure 앵커를 생성, 업로드 및 다운로드하는 데 필요한 여러 단계를 살펴봅니다.

두 번째 자습서인 [Azure Spatial Anchors 저장, 검색 및 공유](mrlearning-asa-ch2.md)에서는 앵커 정보를 HoloLens 2의 스토리지에 저장하여 여러 앱 세션에서 Azure Spatial Anchors를 저장하는 방법 및 이 앵커 정보를 다른 디바이스와 공유하여 다중 디바이스 앵커 맞춤을 수행하는 방법을 알아봅니다.

세 번째 자습서인 [Azure Spatial Anchor 피드백 표시](mrlearning-asa-ch3.md)에서는 Azure Spatial Anchors를 사용할 때 앵커 이벤트 및 상태에 대한 피드백을 사용자에게 제공하는 방법을 알아봅니다.

네 번째 자습서인 [Android 및 iOS용 Azure Spatial Anchors](mrlearning-asa-ch4.md)에서는 Android 및 iOS 디바이스에 프로젝트를 빌드하고 배포하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* HoloLens 2용 Azure Spatial Anchors를 사용하여 개발하는 방법에 대한 기본 사항 알아보기
* Spatial Anchors 만들기, 업로드 및 다운로드

## <a name="prerequisites"></a>필수 구성 요소

>[!TIP]
>[시작 자습서](mrlearning-base.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.

* 올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 기본 C# 프로그래밍 기능
* [개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens(1세대) 또는 HoloLens 2 디바이스
* Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* [HoloLens 빠른 시작](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서의 [Spatial Anchors 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료합니다.

Android에 배포하려는 경우
* Windows 또는 macOS 컴퓨터에 USB 연결을 사용하는 <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">개발자 사용</a> 및 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 지원 가능</a> Android 디바이스
* Unity 2019.2.X가 설치되고 Android 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

iOS에 배포하려는 경우
* 최신 버전의 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 및 <a href="https://cocoapods.org" target="_blank">CocoaPods</a>가 설치된 macOS 컴퓨터
* macOS 컴퓨터에 USB로 연결된 <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 호환</a> iOS 디바이스
* Unity 2019.2.X가 설치되고 iOS 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!IMPORTANT]
> 이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.

## <a name="creating-the-unity-project"></a>Unity 프로젝트 만들기
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mrlearning-base-ch1.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [새 Unity 프로젝트 만들기](mrlearning-base-ch1.md#create-new-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정

2. [Windows Mixed Reality용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [TextMesh Pro Essential Resources 가져오기](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Mixed Reality Toolkit용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Unity 장면에 Mixed Reality Toolkit 추가](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 및 장면에 적절한 이름(예: *AzureSpatialAnchors*) 지정

그런 다음, [Mixed Reality Toolkit 프로필을 구성하는 방법(공간 인식 표시 옵션 변경)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경하고, 공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.

> [!CAUTION]
> 위에 연결된 [Mixed Reality Toolkit용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) 지침에서 설명한 대로 Unity용 MSBuild를 사용하지 않도록 설정하는 것이 좋습니다.

## <a name="adding-inbuilt-unity-packages"></a>기본 제공 Unity 패키지 추가
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

이 섹션에서는 다음 섹션에서 가져올 Azure Spatial Anchors SDK에 필요하므로 Unity의 기본 제공 AR Foundation 패키지를 설치합니다.

Unity 메뉴에서 **Window** > **패키지 관리자**를 차례로 선택합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> AR Foundation 패키지가 목록에 표시되는 데 몇 초 정도 걸릴 수 있습니다.

패키지 관리자 창에서 **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)(버전 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.

자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>장면 만들기 및 준비
<!-- TODO: Consider renaming to 'Preparing the scene' -->

이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 차례로 이동합니다. CTRL 단추를 누른 상태에서 **ButtonParent**, **DebugWindow**, **Instructions** 및 **ParentAnchor**를 클릭하여 4개의 프리팹을 선택합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

4개의 프리팹을 선택한 상태에서 [계층 구조] 창으로 끌어서 장면에 추가합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

장면의 개체에 초점을 맞추기 위해 ParentAnchor 개체를 두 번 클릭한 다음, 약간씩 다시 축소할 수 있습니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> 장면에서 큰 아이콘(예: 틀이 있는 매력적인 큰 'T' 아이콘)이 표시되는 경우 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 이러한 아이콘을 숨길 수 있습니다.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>장면을 작동하도록 단추 구성

이 섹션에서는 스크립트를 장면에 추가하여 로컬 앵커와 Azure Spatial Anchors가 애플리케이션에서 동작하는 방법에 대한 기본 사항을 보여 주는 일련의 단추 이벤트를 만듭니다.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. 누름 가능한 단추 HoloLens 2(스크립트) 구성 요소 구성

[계층 구조] 창에서 **ButtonParent** 개체를 펼치고, **StartAzureSession**이라는 첫 번째 자식 개체를 선택합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

[검사기] 창에서 **누름 가능한 단추 HoloLens 2(스크립트)** 구성 요소를 찾고, **+** 아이콘을 클릭하여 새 이벤트 수신기를 **Button Pressed ()** 이벤트에 추가합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

[계층 구조] 창에서 StartAzureSession 개체를 선택한 상태에서 [계층 구조] 창의 **ParentAnchor** 개체를 클릭하여 방금 추가한 이벤트 수신기의 빈 **없음(개체)** 필드로 끌어서 ParentAnchor 개체에서 이 단추의 단추 누름 이벤트를 수신 대기하도록 설정합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

동일한 이벤트 수신기의 **함수 없음** 드롭다운을 클릭한 다음, **AnchorModuleScript** > **StartAzureSession ()** 을 차례로 선택하여 StartAzureSession () 함수를 이 단추의 단추 누름 이벤트가 실행될 때 트리거되는 작업으로 설정합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. Interactable(스크립트) 구성 요소 구성

[계층 구조] 창에서 StartAzureSession 개체를 선택한 채로 [검사기] 창에서 **Interactable(스크립트)** 구성 요소를 찾고, **OnClick ()** 이벤트에 대해 위의 1단계와 동일한 프로세스를 반복합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. 나머지 단추 구성

나머지 각 단추에 대해 위의 1단계 및 2단계에서 설명한 프로세스를 완료하여 함수를 **Button Pressed ()** 및 **OnClick ()** 이벤트 모두에 할당합니다.

* **StopAzureSession** 개체에 대해 AnchorModuleScript > **StopAzureSession ()** 함수를 할당합니다.
* **CreateAzureAnchor** 개체에 대해 AnchorModuleScript > **CreateAzureAnchor ()** 함수를 할당합니다.
  * 그런 다음, **ParentAnchor**를 빈 **없음(게임 개체)** 필드로 다시 끕니다.
* **RemoveLocalAnchor** 개체에 대해 AnchorModuleScript > **RemoveLocalAnchor ()** 함수를 할당합니다.
  * 그런 다음, **ParentAnchor**를 빈 **없음(게임 개체)** 필드로 다시 끕니다.
* **FindAzureAnchor** 개체에 대해 AnchorModuleScript > **FindAzureAnchor ()** 함수를 할당합니다.
* **DeleteAzureAnchor** 개체에 대해 AnchorModuleScript > **DeleteAzureAnchor ()** 함수를 할당합니다.

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. Azure 리소스에 장면 연결

[계층 구조] 창에서 **ParentAnchor** 개체를 선택하고, [검사기] 창에서 **공간 앵커 관리자(스크립트)** 구성 요소까지 아래로 스크롤합니다.

그런 다음, **자격 증명** 섹션에서 이 자습서에 있는 [필수 구성 요소](mrlearning-asa-ch1.md#prerequisites)의 일부로 만든 Spatial Anchors 계정 ID 및 키를 해당 **Spatial Anchors 계정 ID** 및 **Spatial Anchors 계정 키** 필드에 붙여넣습니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Azure Spatial Anchors의 기본 동작 사용해 보기

이제 장면에서 Azure Spatial Anchors의 기본 사항을 보여 주도록 구성되었으므로 Azure Spatial Anchors를 직접 경험할 수 있도록 앱을 배포할 시간입니다.

### <a name="1-add-additional-required-capabilities"></a>1. 필요한 추가 기능 추가

Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 엽니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

[플레이어 설정] 창에서 **플레이어**, **게시 설정**을 차례로 선택합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다. 그런 다음, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** 및 **Webcam** 기능을 사용하도록 설정합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. HoloLens 2에 앱 배포

Azure Spatial Anchors는 Unity에서 실행할 수 없으므로 Azure Spatial Anchors 기능을 테스트하려면 프로젝트를 디바이스에 배포해야 합니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법을 미리 알아보려면 [디바이스에 애플리케이션 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침을 참조할 수 있습니다.

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. HoloLens 2에서 앱 실행 및 앱 내 지침 수행

> [!CAUTION]
> Azure Spatial Anchors는 인터넷을 사용하여 앵커 데이터를 저장하고 로드하므로 디바이스가 인터넷에 연결되어 있는지 확인합니다.

애플리케이션이 디바이스에서 실행되는 경우 Azure Spatial Anchor 자습서 지침 패널에 표시되는 화면상의 지침을 따릅니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>환경 고정

이전 섹션에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다. 큐브를 사용하여 연결된 앵커가 있는 부모 게임 개체를 표현하고 시각화했습니다. 이 섹션에서는 전체 환경을 ParentAnchor 개체의 자식 항목으로 배치하여 이 환경을 고정시키는 방법에 대해 알아봅니다.

### <a name="1-add-the-rocket-launcher-experience"></a>1. 로켓 발사대 환경 추가

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** 폴더로 차례로 이동하고, **RocketLauncher_Complete** 프리팹을 선택합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

RocketLauncher_Complete 프리팹을 선택한 채로 [계층 구조] 창의 **ParentAnchor** 개체 위로 끌어서 ParentAnchor 개체의 자식 항목으로 만듭니다.

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. 로켓 발사대 환경의 위치 변경

**RocketLauncher_Complete** 개체를 적절한 크기 조정 및 방향으로 위치 지정, 회전 및 크기 조정하고, **ParentAnchor** 개체가 계속 공개되도록 합니다. 예를 들어 다음과 같습니다.

* 변환 **위치** X = 0, Y = 0, Z = 3.75
* 변환 **회전** X = 0, Y = 90, Z = 0
* 변환 **크기 조정** X = 10, Y = 10, Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

애플리케이션에서 사용자는 큐브를 이동하여 전체 로켓 발사대 환경의 위치를 변경할 수 있습니다.

> [!TIP]
> 위치 변경 개체 사용, 환경 주위의 경계 상자를 해제/설정하는 단추 사용, 위치 및 회전 gizmos 사용 등을 포함하여 위치 변경 환경에 대한 다양한 사용자 환경 흐름이 있습니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다. 여기서는 Azure Spatial Anchors 세션을 시작 및 중지하고 단일 디바이스에서 Azure Spatial Anchors를 생성, 업로드 및 다운로드하는 데 필요한 다양한 단계를 살펴볼 수 있는 몇 가지 단추를 제공했습니다.

다음 단원에서는 애플리케이션이 다시 시작된 후에도 검색을 위해 Azure 앵커 ID를 HoloLens 2에 저장하는 방법 및 여러 디바이스 간에 앵커 ID를 전송하여 공간 맞춤을 구현하는 방법에 대해 알아봅니다.

[다음 단원: 2. Azure Spatial Anchors 저장, 검색 및 공유](mrlearning-asa-ch2.md)
