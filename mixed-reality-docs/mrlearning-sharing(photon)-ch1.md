---
title: 다중 사용자 기능 자습서 - 1. Photon Unity 네트워킹 설정
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610814"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Photon Unity 네트워킹 설정

## <a name="overview"></a>개요

이 자습서에서는 PUN(Photon Unity Networking)을 사용하여 공유 환경을 만들기 위해 준비하는 방법을 알아봅니다. Photon은 Mixed Reality 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다. Photon PUN 애플리케이션을 만들고 Photon PUN 자산을 Unity 프로젝트로 가져오고 Unity 프로젝트를 Photon PUN 애플리케이션에 연결하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* Photon PUN 애플리케이션을 만드는 방법 알아보기
* Photon PUN 자산을 찾아서 가져오는 방법 알아보기
* Unity 프로젝트를 Photon PUN 애플리케이션에 연결하는 방법 알아보기

## <a name="prerequisites"></a>필수 구성 요소

>[!TIP]
>[시작 자습서](mrlearning-base.md) 및 [Azure Spatial Anchors 자습서](mrlearning-asa-ch1.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.

* 올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 기본 C# 프로그래밍 기능
* [개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* [Spatial Anchors 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션([빠른 시작: Azure Spatial Anchors를 사용하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서)을 완료합니다.

> [!IMPORTANT]
> 이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.

## <a name="creating-and-preparing-the-unity-project"></a>Unity 프로젝트 만들기 및 준비

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mrlearning-base-ch1.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [새 Unity 프로젝트 만들기](mrlearning-base-ch1.md#create-new-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정

2. [Windows Mixed Reality용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [TextMesh Pro Essential Resources 가져오기](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Mixed Reality Toolkit용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Unity 장면에 Mixed Reality Toolkit 추가](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 및 장면에 적절한 이름(예: *MultiUserCapabilities*) 지정

그런 다음, [Mixed Reality Toolkit 프로필을 구성하는 방법(공간 인식 표시 옵션 변경)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경하고, 공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.

> [!CAUTION]
> 위에 연결된 [Mixed Reality Toolkit용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) 지침에서 설명한 대로 Unity용 MSBuild를 사용하지 않도록 설정하는 것이 좋습니다.

## <a name="configuring-the-capabilities"></a>기능 구성

Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 연 다음, **플레이어** >  **게시 설정** 섹션을 차례로 찾습니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다. 그런 다음, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** 기능을 사용하도록 설정합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a>기본 제공 Unity 패키지 추가
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

이 섹션에서는 다음 섹션에서 가져올 Azure Spatial Anchors SDK에 필요하므로 Unity의 기본 제공 AR Foundation 패키지를 설치합니다.

Unity 메뉴에서 **Window** > **패키지 관리자**를 차례로 선택합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> AR Foundation 패키지가 목록에 표시되는 데 몇 초 정도 걸릴 수 있습니다.

패키지 관리자 창에서 **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)(버전 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.

자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> MultiUserCapabilities 자습서 자산 패키지를 가져오면 유형 또는 네임스페이스가 누락되었음을 나타내는 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 오류가 Console 창에 보입니다. 이것은 예상한 오류이며, 다음 섹션에서 Photon 자산을 가져오면 해결됩니다.

## <a name="importing-the-photon-assets"></a>Photon 자산 가져오기

이 섹션에서는 Unity의 Asset Store에서 PUN(Photon Unity Network) 자산을 가져옵니다.

Unity 메뉴에서 **Window** > **Asset Store**를 선택하여 Asset Store 창을 열고 Exit Games에서 **PUN 2 - FREE**를 검색하여 선택한 다음, **Download** 단추를 클릭하여 자산 패키지를 Unity 계정에 다운로드합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

다운로드가 완료되면 **Import** 단추를 클릭하여 Import Unity Package 창을 엽니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

Unity에서 Import(가져오기) 프로세스가 완료되면 Pun Wizard 창이 PUN Setup 메뉴가 로드된 상태로 나타납니다. 지금은 이 창을 무시하거나 닫으면 됩니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a>Photon 설정

이 섹션에서는 Photon 계정이 없으면 만들고 새 PUN 애플리케이션을 만듭니다.

Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">대시보드</a>로 이동하여 로그인하고(사용할 계정이 있는 경우) 그렇지 않으면 **Create One** 링크를 클릭하여 지침에 따라 새 계정을 등록합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

로그인되면 **Create a New App** 단추를 클릭합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

Create a New Application(새 애플리케이션 만들기) 페이지에서 다음 값을 입력합니다.

* Photon Type에는 Photon PUN을 선택합니다.
* 이름에는 적절한 이름(예: _MRTK Tutorials_)을 입력합니다.
* 설명에는 적절한 설명(선택 사항)을 입력합니다.
* URL 필드는 비워둡니다.

**Create** 단추를 클릭하여 새 애플리케이션을 만듭니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

Photon에서 만들기 프로세스가 완료되면 새 PUN 애플리케이션이 대시보드에 나타납니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Unity 프로젝트를 PUN 애플리케이션에 연결

이 섹션에서는 Unity 프로젝트를 이전 섹션에서 만든 PUN 애플리케이션에 연결합니다.

Photon 대시보드에서 **App ID** 필드를 클릭하고 앱 ID 필드를 표시하여 클립보드에 복사합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

Unity 메뉴에서 **Window** > **Photon Unity Networking** > **PUN Wizard**를 선택하여 Pun Wizard 창을 열고 **Setup Project** 창을 클릭하여 PUN Setup 메뉴를 열어서 다음과 같이 구성합니다.

* **AppId or Email** 필드에 이전 단계에서 복사한 PUN App ID를 붙여넣습니다.

그런 다음, **Setup Project** 단추를 클릭하여 App ID를 적용합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

Unity에서 PUN 설정 프로세스가 완료되면 PUN Setup 메뉴에 **Done!** 이라는 메시지가 표시되고 Project 창에 **PhotonServerSettings** 자산이 자동으로 선택되고 해당 속성이 Inspector 창에 표시됩니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a>축하합니다.

Photon PUN 애플리케이션을 만들어서 Unity 프로젝트에 연결하는 데 성공했습니다. 다음 단계에서는 여러 사용자가 서로 볼 수 있도록 다른 사용자와 연결을 허용할 수 있습니다.

[다음 자습서: 2. 여러 사용자 연결](mrlearning-sharing(photon)-ch2.md)
