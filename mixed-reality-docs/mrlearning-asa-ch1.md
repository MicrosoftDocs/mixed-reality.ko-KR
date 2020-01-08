---
title: Azure 공간 앵커 자습서-1. Azure 공간 앵커 시작
description: 혼합 현실 애플리케이션에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334455"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure 공간 앵커 시작

## <a name="overview"></a>개요

HoloLens 2 자습서의 두 번째 시리즈를 시작 합니다. 이 세 부분으로 구성 된 자습서 시리즈에서는 Azure 공간 앵커의 기본 사항을 알아봅니다.

이 첫 번째 자습서에서는 azure [공간 앵커](mrlearning-asa-ch1.md)를 시작 하 고, azure 세션을 시작 및 중지 하 고, 단일 장치에서 azure 앵커를 만들고, 업로드 하 고, 다운로드 하는 데 필요한 여러 단계를 살펴봅니다.

두 번째 자습서 인 [Azure 공간 앵커 저장, 검색 및 공유](mrlearning-asa-ch2.md)에서 앵커 정보를 HoloLens 2의 저장소에 저장 하 고 다중 장치 앵커 맞춤을 위해이 앵커 정보를 다른 장치에 공유 하는 방법에 대해 알아봅니다.

세 번째 자습서에서는 [Azure 공간 고정 피드백을 표시](mrlearning-asa-ch3.md)하는 방법에 대해 사용자에 게 Azure 공간 앵커를 사용할 때 앵커 이벤트 및 상태에 대 한 피드백을 제공 하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* HoloLens 2 용 Azure 공간 앵커를 사용 하 여 개발 하는 기본 사항 알아보기
* 공간 앵커 만들기, 업로드 및 다운로드

## <a name="prerequisites"></a>전제 조건

>[!TIP]
>초보자를 위한 [자습서](mrlearning-base.md) 시리즈를 아직 완료 하지 않은 경우 해당 자습서를 먼저 완료 하는 것이 좋습니다.

* 올바른 [도구로](install-the-tools.md) 구성 된 WINDOWS 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 C# 기본 프로그래밍 기능
* [개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode) HoloLens 2 장치
* [빠른 시작: Azure 공간 앵커를 사용 하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서의 [공간 앵커 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료 합니다.

>[!IMPORTANT]
>이 자습서 시리즈에는 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> 이 필요 하며 권장 버전은 unity 2019.1.14입니다. 이렇게 하면 위에 연결 된 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항이 나 권장 사항이 대체 됩니다.

## <a name="creating-the-unity-project"></a>Unity 프로젝트 만들기

이 섹션에서는 새 Unity 프로젝트를 만들고 Windows Mixed Reality에 대해 구성 합니다.

1. Unity 프로젝트를 만들고 적절 한 이름 (예: _Azure 공간 앵커 자습서_)을 지정 합니다.

2. Windows Mixed Reality의 Unity 프로젝트를 구성 합니다.

    >[!TIP]
    >Unity 프로젝트를 만들고 Windows Mixed Reality에 맞게 구성 하는 방법에 대 한 미리 알림은 [시작 자습서](mrlearning-base.md) 시리즈의 일부인 [프로젝트 및 첫 번째 응용 프로그램 초기화](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) 자습서의 [새 Unity 프로젝트 만들기](mrlearning-base-ch1.md#create-new-unity-project) 및 [windows mixed reality 용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) 섹션을 참조할 수 있습니다.

## <a name="adding-inbuilt-unity-packages"></a>기본 제공 Unity 패키지 추가

이 섹션에서는 프로젝트에서 사용 하는 도구 키트와 Sdk에 필요한 기본 제공 Unity 자산 및 패키지를 추가 합니다.

1. TMP 필수 리소스를 가져옵니다.

    >[!NOTE]
    >혼합 현실 도구 키트에 필요한이 패키지를 추가 하 고 있습니다.

    Unity 메뉴에서 **Window** > **TEXTMESHPRO** > **Import TMP 필수 리소스**를 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-2-1.1.png)

    Unity 패키지 가져오기 팝업 창에서 먼저 **모두** 단추를 클릭 하 여 모든 자산을 선택 했는지 확인 한 다음 **가져오기** 단추를 클릭 하 여 자산을 가져옵니다.

    ![mrlearning](images/mrlearning-asa-ch1-2-1.2.png)

2. AR를 설치 합니다.

    >[!NOTE]
    >Azure 공간 앵커 SDK에 필요한이 패키지를 추가 하 고 있습니다.

    Unity 메뉴에서 **창** > **패키지 관리자**를 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-2-2.1.png)

    패키지 관리자 창에서 **AR Foundation** 을 선택 하 고 **설치** 단추를 클릭 하 여 패키지를 설치 합니다.

    >[!IMPORTANT]
    >AR 패키지를 목록에 표시 하기 전에 몇 초 정도 걸릴 수 있습니다.

    ![mrlearning](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

이 섹션에서는 모든 자습서 자산을 다운로드 하 고 가져옵니다.

1. 자산을 다운로드 합니다.

    * [AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (버전 2.0.0)
    * [MixedReality. 2.1.0. unitypackage.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [MRTK. HoloLens2.2.1.0.1. unitypackage를 시작 합니다.](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [MRTK. HoloLens2 AzureSpatialAnchors. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. 자산을 가져옵니다.

    Unity 메뉴에서 **자산** > **가져오기 패키지** > **사용자 지정 패키지**...를 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-3-2.1.png)

    패키지 가져오기 ... 팝업 창에서 **AzureSpatialAnchors** 를 선택 하 고 **열기** 단추를 클릭 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-3-2.2.png)

    Unity 패키지 가져오기 팝업 창에서 먼저 **모두** 단추를 클릭 하 여 모든 자산을 선택 했는지 확인 한 다음 **가져오기** 단추를 클릭 하 여 자산을 가져옵니다.

    ![mrlearning](images/mrlearning-asa-ch1-3-2.3.png)

    이러한 단계를 반복 하 여 나머지 자산 패키지를 가져옵니다. 완료 되 면 Unity 프로젝트의 **자산** 폴더에 이러한 하위 폴더가 포함 되어야 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a>장면 만들기 및 준비

이 섹션에서는 혼합 현실 도구 키트와 일부 자습서 prefabs를 추가 하 여 장면을 만들고 준비 합니다.

1. 새 장면을 만듭니다.

    Unity 메뉴에서 **파일** > **새 장면**을 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-1.1.png)

    Unity 메뉴에서 **파일** > 다른 **이름으로 저장**...을 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-1.2.png)

    장면 저장 팝업 창에서 프로젝트의 **배경** 폴더로 이동 하 고, 장면에 적절 한 이름 (예: _ASATutorialScene_)을 지정 하 고, **저장** 단추를 클릭 하 여 장면을 저장 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    >프로젝트의 자산 폴더 내에 있는 한 언제 든 지 장면을 저장할 수 있습니다. 그러나 프로젝트를 계속 구성 하려면 일반적으로 프로젝트의 배경 폴더에 저장 하는 것이 좋습니다.

2. Mixed Reality Toolkit을 추가 합니다.

    Unity 메뉴에서 **Mixed Reality Toolkit** > **장면에 추가 및 구성**...을 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-2.1.png)

    MixedRealityToolkitConfigurationProfile 선택 팝업 창에서 **DefaultHoloLens2ConfigurationProfile** 를 클릭 하 여 장면의 MRTK 구성 프로필로 설정 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-2.2.png)

    Unity 메뉴에서 **파일** > **저장** 을 선택 하 여 장면을 저장 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    >바로 가기 키 CTRL + S (macOS에서 command + S)를 사용 하 여이 자습서를 진행 하면서 장면을 빠르게 저장할 수 있습니다.

3. 자습서 prefabs를 추가 합니다.

    프로젝트 패널에서 **자산** > **mrtk로 이동 합니다. AzureSpatialAnchors** > **Prefabs** 폴더입니다. CTRL 단추 (macOS에서 명령)를 누른 상태에서 **Buttonparent**, **Debugwindow**및 **parentanchor** 를 클릭 하 여 세 개의 prefabs를 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-3.1.png)

    세 개의 prefabs를 선택한 상태에서 계층 패널로 끌어 장면에 추가 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-3.2.png)

    장면의 개체에 초점을 맞추기 위해 ParentAnchor 개체를 두 번 클릭 한 다음 약간 축소할 수 있습니다.

    ![mrlearning](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    >장면에서 많은 아이콘이 표시 되는 경우, 예를 들어, 크게 프레임을 벗어난 아이콘이 표시 되는 경우 Gizmo 그리려면을 off 위치로 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">전환</a> 하 여 숨길 수 있습니다.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>장면을 작동 하도록 단추 구성

이 섹션에서는 prefabs 및 스크립트를 장면에 추가 하 여 로컬 앵커와 Azure 공간 앵커가 응용 프로그램에서 작동 하는 방식에 대 한 기본 사항을 보여 주는 일련의 단추를 만듭니다.

1. Pressable Button Holo Lens 2 (스크립트) 구성 요소를 구성 합니다.

    계층 패널에서 **Buttonparent** 개체를 확장 하 고 **StartAzureSession**라는 첫 번째 자식 개체를 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-5-1.1.png)

    검사기 패널에서 **Pressable Button Holo Lens 2 (스크립트)** 구성 요소로 스크롤하고 **+** 아이콘을 클릭 하 여 **단추 누름 ()** 이벤트에 새 이벤트 수신기를 추가 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-5-1.2.png)

    계층 패널에서 StartAzureSession 개체를 선택한 상태에서 계층 패널의 **Parentanchor** 개체를 클릭 하 고이 단추를 클릭 하 여 parentanchor 개체가 단추 누름 이벤트를 수신 하도록 합니다 .이 필드를 방금 추가한 이벤트 수신기의 빈 **없음 (개체)** 필드로 끕니다.

    ![mrlearning](images/mrlearning-asa-ch1-5-1.3.png)

    동일한 이벤트 수신기의 **함수 없음** 드롭다운을 클릭 한 다음 **AnchorModuleScript** > **StartAzureSession ()** 를 선택 하 여이 단추에서 단추 누름 이벤트가 발생 했을 때 트리거되는 작업으로 StartAzureSession () 함수를 설정 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-5-1.4.png)

2. Interactable (스크립트) 구성 요소를 구성 합니다.

    계층 패널에서 StartAzureSession 개체를 선택 하 고, 검사기 패널에서 **Interactable (스크립트)** 구성 요소로 스크롤하고, **OnClick ()** 이벤트에 대해 위의 1 단계와 동일한 프로세스를 반복 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-5-2.1.png)

3. 나머지 단추 구성

    나머지 각 단추에 대해 위의 1 단계와 2 단계에 설명 된 프로세스를 완료 하 여 다음과 같은 단추 누름 () 및 OnClick () 이벤트에 함수를 할당 합니다.

    * **Stopazuresession** 개체에 대해 **stopazuresession ()** 함수를 할당 합니다.
    * **Createanchor** 개체의 경우 **createazureanchor ()** 함수를 할당 하 고 **Parentanchor** 를 빈 **None (Game object)** 필드로 끌어 옵니다.
    * Anchor 개체를 **검색** 하려면 **FindAzureAnchor ()** 함수를 할당 합니다.
    * **Delete Azure anchor** 개체의 경우 **deleteazureanchor ()** 함수를 할당 합니다.
    * **Delete Local anchor** 개체의 경우 **removelocalanchor ()** 함수를 할당 하 고 **parentanchor** 를 빈 **없음 (게임 개체)** 필드로 끌어 옵니다.

4. Azure 리소스에 장면 연결

    계층 패널에서 **Parentanchor** 개체를 선택 하 고 검사기 패널에서 **공간 앵커 관리자 (스크립트)** 구성 요소로 스크롤합니다.

    그런 다음 **자격 증명** 섹션에서 공간 앵커 계정 Id 및 키를 해당 **공간** 앵커 계정 Id 및 **공간 앵커 계정 키** 필드에 붙여넣습니다.

    >[!NOTE]
    >이 자습서의 [필수 구성 요소](mrlearning-asa-ch1.md#prerequisites)에 따라 공간 앵커 계정 Id 및 키를 만들었습니다.

    ![mrlearning](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    >장면을 저장 했는지 확인 합니다.

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Azure 공간 앵커의 기본 동작 시도

이제 Azure 공간 앵커의 기본 사항을 보여 주기 위해 장면을 구성 했으므로 Azure 공간 앵커 어떠한 체험을 경험할 수 있도록 앱을 배포할 시간입니다.

1. 필요한 추가 기능을 추가 합니다.

    Unity 메뉴에서 **편집** > **프로젝트 설정 ...** 을 선택 하 여 플레이어 설정 패널을 엽니다.

    ![mrlearning](images/mrlearning-asa-ch1-6-1.1.png)

    플레이어 설정 패널에서 **플레이어** , **게시 설정**을 차례로 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-6-1.2.png)

    **게시 설정**에서 **기능** 섹션까지 아래로 스크롤하고 자습서의 시작 부분에서 프로젝트를 만들 때 사용 하도록 설정 된 **SpatialPerception**이 사용 하도록 설정 되어 있는지 두 번 확인 합니다. 그런 다음 **Internetclient**, **internetclientserver**, **PrivateNetworkClientServer**, **removablestorage**, **웹캠**및 **마이크** 기능을 사용 하도록 설정 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-6-1.3.png)

2. HoloLens 2에 앱을 배포 합니다.

    >[!TIP]
    >Unity 프로젝트를 빌드하고 HoloLens 2에 배포 하는 방법에 대 한 미리 알림은 [시작 자습서](mrlearning-base.md) 시리즈의 일부인 [프로젝트 및 첫 번째 응용 프로그램 초기화](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) 자습서의 [장치에 응용 프로그램 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 섹션을 참조할 수 있습니다.

3. 앱을 실행 하 고 앱의 지침을 따릅니다.

    >[!CAUTION]
    >Azure 공간 앵커는 인터넷을 사용 하 여 고정 데이터를 저장 하 고 로드 하므로 장치가 인터넷에 연결 되어 있는지 확인 합니다.

    응용 프로그램이 장치에서 실행 되는 경우 **Azure 공간 고정 모듈 명령** 패널에 표시 된 화면의 지시를 따릅니다.

    ![mrlearning](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a>환경 고정

이전 섹션에서는 Azure 공간 앵커의 기본 사항을 배웠습니다. 큐브를 사용 하 여 연결 된 앵커를 사용 하 여 부모 게임 개체를 나타내고 시각화 했습니다. 이 섹션에서는 ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법에 대해 설명 합니다.

1. 로켓 시작 관리자 환경을 추가 합니다.

    프로젝트 패널에서 **자산** > **mrtk로 이동 합니다. 자습서. GetPrefabs** 가 시작 > 폴더를 선택 하 고 **로켓 Launcher_Complete** prefab를 선택 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-7-1.1.png)

    로켓 Launcher_Complete prefab를 선택한 상태에서 계층 패널의 **parentanchor** 개체 위쪽으로 끌어 parentanchor 개체의 자식으로 만듭니다.

    ![mrlearning](images/mrlearning-asa-ch1-7-1.2.png)

2. 로켓 시작 관리자 환경의 위치를 변경 합니다.

    **Parentanchor** (cube)가 계속 노출 되도록 모듈 **로켓 Launcher_Complete** 개체를 이동 합니다.

    ![mrlearning](images/mrlearning-asa-ch1-7-2.1.png)

    응용 프로그램에서 사용자는 이제 큐브를 이동 하 여 전체 로켓 시작 관리자 환경을 재배치할 수 있습니다.

    >[!TIP]
    >위치 조정 개체 (예:이 자습서에서 사용 되는 큐브) 사용, 환경 주위에 있는 경계 상자를 전환 하는 단추 사용, 위치 및 회전 사용 등의 다양 한 사용자 환경 흐름이 있습니다. gizmo 그리려면.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure 공간 앵커의 기본 사항을 배웠습니다. 이 단원에서는 Azure 세션을 시작 및 중지 하 고 단일 장치에서 azure 앵커를 만들고 업로드 하 고 다운로드 하는 데 필요한 여러 단계를 살펴볼 수 있는 몇 가지 단추를 제공 했습니다.

다음 단원에서는 응용 프로그램을 다시 시작한 후에도 검색을 위해 HoloLens 2에 Azure 앵커 Id를 저장 하는 방법과 여러 장치 간에 앵커 Id를 전송 하 여 공간 맞춤을 구현 하는 방법을 배웁니다.

[다음 단원: 2. Azure 공간 앵커 저장, 검색 및 공유](mrlearning-asa-ch2.md)
