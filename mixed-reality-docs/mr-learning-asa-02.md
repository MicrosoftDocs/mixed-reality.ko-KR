---
title: Azure Spatial Anchors 자습서 - 2. Azure Spatial Anchors 시작
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d117839e51e586f4b905a20510fffc670d34cd4e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376495"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Azure Spatial Anchors 시작

## <a name="overview"></a>개요

이 자습서에서는 Azure Spatial Anchors 세션을 시작 및 중지하고 단일 디바이스에서 Azure Spatial Anchors를 생성, 업로드 및 다운로드하는 데 필요한 여러 단계를 살펴봅니다.

## <a name="objectives"></a>목표

* HoloLens 2용 Azure Spatial Anchors를 사용하여 개발하는 방법에 대한 기본 사항 알아보기
* 공간 앵커를 만들고 Azure에서 가져오는 방법 알아보기

## <a name="creating-and-preparing-the-unity-project"></a>Unity 프로젝트 만들기 및 준비

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

이를 위해 먼저 [프로젝트 초기화 및 첫 번째 애플리케이션 배포](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정
1. [빌드 플랫폼 전환](mr-learning-base-02.md#configuring-the-unity-project)
1. [TextMeshPro 필수 리소스 가져오기](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [Unity 프로젝트 구성](mr-learning-base-02.md#configuring-the-unity-project)
1. [장면 만들기 및 구성](mr-learning-base-02.md#creating-and-configuring-the-scene) 및 장면에 적절한 이름(예: *AzureSpatialAnchors*) 지정

그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 다음을 수행합니다.

1. **MRTK 구성 프로필**을 **DefaultHoloLens2ConfigurationProfile**로 변경
1. **공간 인식 메시 표시 옵션**을 **폐색**으로 변경

## <a name="installing-inbuilt-unity-packages"></a>기본 제공 Unity 패키지 설치

Unity 메뉴에서 **창** > **패키지 관리자**를 차례로 선택하여 패키지 관리자 창을 연 다음, **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Azure Spatial Anchors SDK에 필요하므로 AR Foundation 패키지를 설치합니다. 이 패키지는 다음 섹션에서 가져옵니다.

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)(버전 2.2.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법은 [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 지침을 참조하세요.

## <a name="preparing-the-scene"></a>장면 준비

이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.

프로젝트 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 이동한 후 다음과 같은 프리팹을 클릭하고 Hierarchy(계층 구조) 창으로 끌어서 장면에 추가합니다.

* **ButtonParent** 프리팹
* **DebugWindow** 프리팹
* **Instructions** 프리팹
* **ParentAnchor** 프리팹

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> 장면에 큰 아이콘(예: 방해가 되는 큰 틀의 'T' 아이콘)이 표시되는 경우 위 이미지와 같이 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 숨길 수 있습니다.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>장면을 작동하도록 단추 구성

이 섹션에서는 스크립트를 장면에 추가하여 로컬 앵커와 Azure Spatial Anchors가 앱에서 동작하는 방식에 대한 기본 사항을 보여 주는 일련의 단추 이벤트를 만듭니다.

Hierarchy(계층 구조) 창에서 **ButtonParent** 개체를 펼쳐서 **StartAzureSession**라는 첫 번째 자식 개체를 선택하고 Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.

* **ParentAnchor** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **StartAzureSession ()** 을 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

Hierarchy(계층 구조) 창에서 **StopAzureSession**이라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.

* **ParentAnchor** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **StopAzureSession ()** 을 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

Hierarchy(계층 구조) 창에서 **CreateAzureAnchor**라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.

* **ParentAnchor** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **CreateAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정
* **ParentAnchor** 개체를 빈 **None (Game Object)** 필드에 할당하여 CreateAzureAnchor () 함수의 인수로 만들기

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

Hierarchy(계층 구조) 창에서 **RemoveLocalAnchor**라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.

* **ParentAnchor** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **RemoveLocalAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정
* **ParentAnchor** 개체를 빈 **None (Game Object)** 필드에 할당하여 RemoveLocalAnchor () 함수의 인수로 만들기

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

Hierarchy(계층 구조) 창에서 **FindAzureAnchor**라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.

* **ParentAnchor** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **FindAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

Hierarchy(계층 구조) 창에서 **DeleteAzureAnchor**라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.

* **ParentAnchor** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **DeleteAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Azure 리소스에 장면 연결

Hierarchy(계층 구조) 창에서 **ParentAnchor** 개체를 선택하고, Inspector(인스펙터) 창에서 **Spatial Anchor Manager(스크립트)** 구성 요소를 찾습니다. 이 자습서 시리즈에서 [필수 구성 요소](mr-learning-asa-01.md#prerequisites)의 일부로 생성된 Azure Spatial Anchors 계정의 자격 증명을 사용하여 **Credentials** 섹션을 구성합니다.

* **Spatial Anchors Account ID** 필드에 Azure Spatial Anchors 계정의 **계정 ID**를 붙여넣습니다.
* **Spatial Anchors Account Key** 필드에 Azure Spatial Anchors 계정의 기본 또는 보조 **액세스 키**를 붙여넣습니다.

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Azure Spatial Anchors의 기본 동작 사용해 보기

Azure Spatial Anchors는 Unity에서 실행할 수 없으므로 Azure Spatial Anchors 기능을 테스트하려면 프로젝트를 빌드하고 디바이스에 앱을 배포해야 합니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.

앱이 디바이스에서 실행되는 경우 Azure Spatial Anchor 자습서 지침 패널에 표시되는 화면의 지시를 따릅니다.

1. 큐브를 다른 위치로 이동
1. Azure 세션 시작
1. Azure 앵커 만들기(큐브의 위치에 앵커 만들기)
1. Azure 세션 중지
1. 로컬 앵커 제거(사용자가 큐브를 이동할 수 있도록 허용)
1. 큐브를 다른 곳으로 이동
1. Azure 세션 시작
1. Azure 앵커 찾기(큐브를 3단계의 위치에 배치)
1. Azure 앵커 삭제
1. Azure 세션 중지

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Azure Spatial Anchors는 인터넷을 사용하여 앵커 데이터를 저장하고 로드하므로 디바이스가 인터넷에 연결되어 있어야 합니다.

## <a name="anchoring-an-experience"></a>환경 고정

이전 섹션에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다. 큐브를 사용하여 연결된 앵커가 있는 부모 게임 개체를 표현하고 시각화했습니다. 이 섹션에서는 전체 환경을 ParentAnchor 개체의 자식 항목으로 배치하여 이 환경을 고정시키는 방법에 대해 알아봅니다.

Hierarchy(계층 구조) 창에서 **ParentAnchor** 개체를 선택하고, Inspector(인스펙터) 창에서 **Transform** 구성 요소를 다음과 같이 구성합니다.

* **X 배율**을 1.1로 변경
* **Z 배율**을 1.1로 변경

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

프로젝트 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** 폴더로 이동한 다음, **RoverExplorer_Complete** 프래팹을 클릭하여 Hierarchy(계층 구조) 창으로 끌어서 장면에 추가합니다.

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

Hierarchy(계층 구조) 창에 RoverModule_Complete 개체가 아직 선택되어 있으면 **ParentAnchor** 개체로 끌어서 ParentAnchor 개체의 자식으로 만듭니다.

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

이제 프로젝트를 다시 빌드하고 디바이스에 앱을 배포하는 경우, 크기 조정된 큐브를 이동하여 전체 Rover Explorer 환경을 재배치할 수 있습니다.

> [!TIP]
> 위치 변경 개체(예: 이 자습서에 사용된 큐브) 사용, 환경 주위의 경계 상자를 해제/설정하는 단추 사용, 위치 및 회전 gizmos 사용 등을 포함하여 환경 위치 변경을 위한 다양한 사용자 환경 흐름이 있습니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다. 이 자습서에는 Azure Spatial Anchors 세션을 시작 및 중지하는 데 필요한 다양한 단계를 살펴볼 수 있는 몇 가지 단추를 제공했습니다. 이를 통해 단일 디바이스에서 Azure Spatial Anchors를 생성, 업로드 및 다운로드할 수도 있습니다.

다음 자습서에서는 앱이 다시 시작된 후에도 검색을 위해 Azure 앵커 ID를 HoloLens 2에 저장하는 방법 및 여러 디바이스 간에 앵커 ID를 전송하여 공간 맞춤을 구현하는 방법에 대해 알아봅니다.

[다음 자습서: 3. Azure Spatial Anchors 저장, 검색 및 공유](mr-learning-asa-03.md)
