---
title: Azure 클라우드 자습서 - 1. HoloLens 2용 Azure Cloud Services
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다양한 Azure 서비스를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Azure, Mixed Reality, Unity, 자습서, HoloLens, HoloLens 2, Azure Blob Storage, Azure Table Storage, Azure Spatial Anchors, Azure Bot Framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306003"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. HoloLens 2용 Azure Cloud Services

## <a name="overview"></a>개요

**Azure 클라우드** 서비스를 **HoloLens 2** 애플리케이션에 가져오는 데 초점을 맞춘 이 자습서 시리즈를 시작합니다. 5부로 구성된 이 자습서 시리즈에서는 여러 **Azure 클라우드** 서비스를 **HoloLens 2**용 **Unity** 프로젝트에 통합하는 방법에 대해 알아봅니다. 연속된 각 챕터에서 새로운 **Azure 클라우드** 서비스를 추가하여 애플리케이션 기능 및 사용자 환경을 확장하는 한편, 각 **Azure 클라우드** 서비스의 기본 사항을 학습합니다.

> [!NOTE]
> 이 자습서 시리즈는 **HoloLens 2**에 집중하지만 Unity의 플랫폼 간 특성으로 인해 대부분의 학습 내용이 데스크톱 및 스마트폰 애플리케이션에도 적용됩니다.

첫 번째 [HoloLens 2용 Azure Cloud Services 소개](mr-learning-azure-01.md) 자습서에서는 먼저 애플리케이션의 목표를 설명하고, 각 Azure 클라우드 서비스를 간략하게 소개한 다음, Unity 프로젝트를 설정합니다.

두 번째 [Azure Storage 통합](mr-learning-azure-02.md) 자습서에서는 Azure Storage를 데모 애플리케이션의 지속성 솔루션으로 통합하고, Blob Storage와 Table Storage 간의 차이점을 알아보고, 필요한 프로젝트 리소스를 준비하며, 장면을 설정하고, 데이터 읽기, 업데이트 및 삭제 작업을 확인합니다.

세 번째 [Azure Custom Vision 통합](mr-learning-azure-03.md) 자습서를 계속 진행하면 Azure Custom Vision을 사용하여 HoloLens 2 애플리케이션에서 이미지를 학습하고 검색합니다. 이 챕터는 사용자 고유의 Azure Custom Vision 리소스를 설정하고 장면 구성 요소를 준비하며, 애플리케이션 내에서 사용자 고유의 이미지를 학습하고 검색하는 작업을 시작합니다.

다음으로, 네 번째 [Azure Spatial Anchors 통합](mr-learning-azure-04.md) 자습서에서 Azure Spatial Anchors 서비스를 검색하여 위치를 저장하여 찾고, 핵심 개념을 학습하며, 필요한 리소스를 준비하고, 애플리케이션의 새 기능을 사용합니다.

다섯 번째 [LUIS와 Azure Bot Service 통합](mr-learning-azure-05.md) 자습서를 통해 새로운 사용자 상호 작용 방법인 자연어를 애플리케이션에 제공하여 마무리합니다! 이 기능은 LUIS(Language Understanding)에서 Azure Bot Framework를 사용하여 실현됩니다. 이 마지막 챕터에서는 Azure Bot Service의 기본 사항을 설명하고, 프로세스의 속도를 향상시키기 위해 Bot Framework 작성기를 제로 코드 솔루션으로 사용합니다. 봇이 만들어지면 이를 장면에 통합하고 HoloLens 2 애플리케이션의 마지막 단계에서 실행합니다.

## <a name="application-goals"></a>애플리케이션 목표

이 자습서 시리즈에서는 이미지에서 개체를 감지하고 해당 공간 위치를 찾을 수 있는 **HoloLens 2** 애플리케이션을 빌드합니다. 도메인 언어를 설정하려면 이제 **추적된 개체**에서 이러한 엔터티를 호출합니다.
사용자는 컴퓨터 비전 및/또는 공간 위치를 통해 이미지 세트를 연결하거나 둘 모두를 연결하는 **추적된 개체**를 만들 수 있습니다. 모든 데이터가 클라우드에 유지되어야 합니다. 또한 애플리케이션의 일부 측면은 필요에 따라 봇을 통해 지원되는 자연어로 제어됩니다.

### <a name="features"></a>기능

* 데이터 및 이미지에 대한 기본 관리
* 이미지 학습 및 검색
* 공간 위치 및 지침 저장
* 자연어를 통해 일부 기능을 사용하는 봇 도우미

## <a name="azure-cloud-services"></a>Azure 클라우드 서비스

애플리케이션에 필요한 기능을 해결하려면 다음과 같은 **Azure 클라우드** 서비스를 사용합니다.

### <a name="azure-storage"></a>Azure Storage

[Azure Storage](https://azure.microsoft.com/services/storage/)는 지속성 솔루션에 사용됩니다. 이를 통해 데이터를 테이블에 저장하고 이미지와 같은 큰 이진 파일을 업로드할 수 있습니다.

### <a name="azure-custom-vision"></a>Azure Custom Vision

[Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)([Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)의 일부)을 사용하면 이미지 세트인 *추적된 개체*에 연결하고, 이 세트에서 기계 학습 모델을 학습시키고, *추적된 개체*를 감지할 수 있습니다.

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

*추적된 개체* 위치를 저장하고 이를 찾기 위한 단계별 지침을 제공하려면 [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/)를 사용합니다.

### <a name="azure-bot-service"></a>Azure Bot Service

이 애플리케이션은 주로 기존 UI를 기반으로 하므로 [Azure Bot Service](https://azure.microsoft.com/services/bot-service/)를 사용하여 일부 프로필을 추가하고 새로운 상호 작용 방법으로 작동합니다.

## <a name="prerequisites"></a>필수 구성 요소

>[!TIP]
>[시작 자습서](mr-learning-base-01.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.

* 올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 기본 C# 프로그래밍 기능
* [개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* 연결된 웹캠(Unity 편집기에서 테스트하려는 경우)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>(Unity 2019.3.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가됨)

> [!CAUTION]
> 이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.3.X입니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.

## <a name="creating-and-preparing-the-unity-project"></a>Unity 프로젝트 만들기 및 준비

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름 지정(예: *Azure Cloud Tutorials*)
2. [빌드 플랫폼 전환](mr-learning-base-02.md#configuring-the-unity-project)
3. [TextMeshPro 필수 리소스 가져오기](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Unity 프로젝트 구성](mr-learning-base-02.md#configuring-the-unity-project)
6. [장면 만들기 및 구성](mr-learning-base-02.md#creating-and-configuring-the-scene) 및 적절한 장면 이름 지정(예: *AzureCloudServices*)

그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경하고, 공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.

## <a name="installing-inbuilt-unity-packages"></a>기본 제공 Unity 패키지 설치

Unity 메뉴에서 **창** > **패키지 관리자**를 차례로 선택하여 [패키지 관리자] 창을 연 다음, **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Azure Spatial Anchors SDK에 필요하므로 AR Foundation 패키지를 설치합니다. 이 패키지는 다음 섹션에서 가져옵니다.

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.

* [Unity용 Azure 스토리지](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [Azure Spatial Anchors](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [MRTK.Tutorials.AzureCloudServices](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.

자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>장면 만들기 및 준비
<!-- TODO: Consider renaming to 'Preparing the scene' -->

이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** 폴더로 차례로 이동합니다. Ctrl 단추를 누른 채 **SceneController**, **RootMenu** 및 **DataManager**를 클릭하여 세 개의 프리팹을 선택합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController(프리팹)** 에는 **SceneController(스크립트)** 및 **UnityDispatcher(스크립트)** 라는 두 개의 스크립트가 포함되어 있습니다. **SceneController** 스크립트 구성 요소는 여러 UX 함수를 포함하고 있고 사진 캡처 기능을 용이하게 하며, **UnityDispatcher**는 Unity 주 스레드에서 작업을 실행할 수 있는 도우미 클래스입니다.

**RootMenu(프리팹)** 는 다양한 작은 스크립트 구성 요소를 통해 서로 연결되는 모든 UI 창을 보유하고 애플리케이션의 일반 UX 흐름을 제어하는 기본 UI 프리팹입니다.

**DataManager(프리팹)** 는 Azure 스토리지와의 통신을 담당하며 다음 자습서에서 자세히 설명합니다.

이제 세 개의 프리팹을 선택한 채 [계층 구조] 창으로 끌어 장면에 추가합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

장면의 개체에 초점을 맞추기 위해 **RootMenu** 개체를 두 번 클릭한 다음, 약간씩 다시 축소할 수 있습니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> 장면에서 큰 아이콘(예: 틀이 있는 매력적인 큰 'T' 아이콘)이 표시되는 경우 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 이러한 아이콘을 숨길 수 있습니다.

## <a name="configuring-the-scene"></a>장면 구성

이 섹션에서는 *SceneManager*, *DataManager* 및 *RootMenu*를 모두 연결하여 다음 [Azure Storage 통합](mr-learning-azure-01.md) 자습서에서 사용할 수 있도록 작업 장면을 준비합니다.

### <a name="connect-the-objects"></a>개체 연결

[계층 구조] 창에서 **DataManager** 개체를 선택합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

[검사기] 창에서 **DataManager(스크립트)** 구성 요소를 찾습니다. 그러면 **On Data Manager Ready ()** 이벤트에 빈 슬롯이 표시됩니다. 이제 [계층 구조] 창에서 **SceneController** 개체를 **On Data Manager Ready ()** 이벤트로 끕니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

이벤트의 드롭다운 메뉴가 활성화되었음을 알 수 있습니다. 드롭다운 메뉴를 클릭하고, **SceneController**로 이동하고, 하위 메뉴에서 **Init ()** 옵션을 선택합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

[계층 구조] 창에서 **SceneController** 개체를 선택합니다. 그러면 [검사기]에서 **SceneController**(스크립트) 구성 요소를 찾을 수 있습니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

채워지지 않은 몇 가지 필드가 있습니다. 이를 변경해 보겠습니다. **DataManager** 개체를 [계층 구조]에서 *데이터 관리자* 필드로 이동하고, **RootMenu** GameObject를 [계층 구조]에서 *주 메뉴* 필드로 이동합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

이제 장면이 다음 자습서에서 사용할 수 있도록 준비되었습니다. 프로젝트에 저장하는 것을 잊지 마세요.

## <a name="prepare-project-build-pipeline"></a>프로젝트 빌드 파이프라인 준비

프로젝트는 아직 콘텐츠로 채워야 하지만 **HoloLens 2**에 맞게 빌드할 수 있도록 몇 가지 항목을 준비해야 합니다.

### <a name="1-add-additional-required-capabilities"></a>1. 필요한 추가 기능 추가

Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

[프로젝트 설정] 창에서 **플레이어**, **게시 설정**을 차례로 선택합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다. 그런 다음, **InternetClientServer**, **PrivateNetworkClientServer** 및 **Webcam** 기능을 사용하도록 설정합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. HoloLens 2에 앱 배포

이 자습서 시리즈에서 사용할 일부 기능은 Unity 편집기 내에서 실행할 수 없습니다. 즉, 애플리케이션을 HoloLens 2 디바이스에 배포하는 방법을 잘 알고 있어야 합니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법을 미리 알아보려면 [시작 자습서 - 디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. HoloLens 2에서 앱 실행 및 앱 내 지침 수행

> [!CAUTION]
> 모든 Azure 서비스에서 인터넷을 사용하므로 디바이스가 인터넷에 연결되어 있는지 확인하세요.

애플리케이션이 디바이스에서 실행되는 경우 다음과 같은 요청된 기능에 대한 액세스를 허용합니다.

* 마이크
* 카메라

*채팅 봇* 및 *Custom Vision*과 같은 서비스가 제대로 작동하려면 이러한 기능이 필요합니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 자습서 시리즈를 소개하고, 구현할 기능 및 **Azure 클라우드** 서비스를 연결하여 *HoloLens 2* 애플리케이션을 실행하는 방법을 알아보았습니다. 필요한 구성 요소를 프로젝트에 추가하고, 이 자습서 시리즈에서 사용할 장면을 준비했습니다.

다음 단원에서는 데이터와 이미지를 저장하기 위한 클라우드 기반 지속성 솔루션으로 Azure 스토리지를 사용합니다.

[다음 자습서: 2. Azure Storage 통합](mr-learning-azure-02.md)
