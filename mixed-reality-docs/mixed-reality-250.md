---
title: MR 공유 250-HoloLens 및 모던 헤드셋
description: Unity, Visual Studio, HoloLens 및 Windows Mixed Reality 헤드셋을 사용 하 여이 코딩 연습을 수행 하 여 혼합 현실 장치 간 holograms 공유에 대 한 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 이동 컨트롤러, 공유, xbox 컨트롤러, 네트워킹, 장치 간
ms.openlocfilehash: c8d341f75424887ca1b0994c8a4d16a0bded671e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437867"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. HoloLens 2에 대 한 [새로운 일련의 자습서](mrlearning-base.md) 가 게시 되었습니다.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR 공유 250: HoloLens 및 모던 헤드셋

UWP (유니버설 Windows 플랫폼)를 사용 하면 여러 장치에 걸쳐 있는 응용 프로그램을 쉽게 만들 수 있습니다. 이러한 유연성을 통해 각 장치의 장점을 활용 하는 환경을 만들 수 있습니다. 이 자습서에서는 HoloLens 및 Windows Mixed Reality 몰입 형 헤드셋에서 실행 되는 기본 공유 환경을 소개 합니다. 이 콘텐츠는 원래 시애틀, WA의 Microsoft Build 2017 회의에서 제공 되었습니다.

**이 자습서에서는 다음을 수행 합니다.**

* UNET를 사용 하 여 네트워크를 설정 합니다.
* 혼합 현실 장치에서 holograms을 공유 합니다.
* 사용 되는 혼합 현실 장치에 따라 응용 프로그램의 다른 보기를 설정 합니다.
* HoloLens 사용자가 간단한 퍼즐을 통해 몰입 형 헤드셋 사용자를 안내 하는 공유 환경을 만듭니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 공유 250: HoloLens 및 모던 헤드셋</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 확인 사항

### <a name="prerequisites"></a>필수 구성 요소

* [필요한 개발 도구가](install-the-tools.md) 포함 된 WINDOWS 10 PC 이며 [windows Mixed Reality 모던 헤드셋을 지원 하도록 구성 되어](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)있습니다.
* PC에서 작동 하는 Xbox 컨트롤러
* 하나 이상의 HoloLens 장치 및 하나의 몰입 형 헤드셋.
* UDP 브로드캐스트 검색을 허용 하는 네트워크입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/MixedReality250/archive/master.zip) 을 다운로드 합니다. 쉽게 기억할 수 있는 위치에 파일을 추출 합니다.
* 이 프로젝트를 사용 하려면 [Windows Mixed Reality를 지 원하는 권장 버전의 Unity](install-the-tools.md)가 필요 합니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/MixedReality250)있습니다.

## <a name="chapter-1---holo-world"></a>1 장-Holo 세계

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>목표

개발 환경에서 간단한 프로젝트를 사용할 준비가 되었는지 확인 합니다.

### <a name="what-we-will-build"></a>빌드할 내용

HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에서 홀로그램을 표시 하는 응용 프로그램입니다.

### <a name="steps"></a>단계

* Unity를 엽니다.
    * **열기**를 선택 합니다.
    * 프로젝트 파일의 압축을 푼 위치로 이동 합니다.
    * **폴더 선택**을 클릭합니다.
    * *Unity가 처음으로 프로젝트를 처리 하는 데는 약간의 시간이 걸립니다.*
* 혼합 현실이 Unity에서 사용 되는지 확인 합니다.
    * 빌드 설정 대화 상자를 엽니다 (**컨트롤 + Shift + B** 또는 **파일 > 빌드 설정**...).
    * **유니버설 Windows 플랫폼** 선택한 후 **플랫폼 전환**을 클릭 합니다.
    * **편집 > 플레이어 설정**을 선택 합니다.
    * 오른쪽의 **검사기** 패널에서 **XR 설정**을 확장 합니다.
    * **가상 현실 지원 됨** 확인란을 선택 합니다.
    * *Windows Mixed Reality는 가상 현실 SDK 여야 합니다.*
* 장면을 만듭니다.
    * **계층** 에서 마우스 오른쪽 단추를 클릭 하 고 **삭제** **를 선택 합니다** .
    * **HoloToolkit > 입력 > Prefabs** 에서 **계층**으로 **MixedRealityCameraParent** 를 끌어옵니다.
* 장면에 Holograms 추가
    * **AppPrefabs** 에서 **Skybox** 를 **장면 뷰로**끕니다.
    * **AppPrefabs** 에서 **관리자** 를 **계층**으로 끕니다.
    * **AppPrefabs** 를 계층 **으로 끕니다** .
* 저장 및 빌드
    * 저장 ( **컨트롤 + S** 또는 **파일 > 장면 저장**)
    * 새 장면 이므로 이름을로 해야 합니다. 이름은 중요 하지 않지만 SharedMixedReality를 사용 합니다.
* Visual Studio로 내보내기
    * 빌드 메뉴 열기 (**컨트롤 + Shift + B** 또는 **파일 > 빌드 설정**)
    * **열려 있는 장면 추가를 클릭 합니다.**
    * **Unity C# 프로젝트** 확인
    * **빌드**를 클릭합니다.
    * 표시 되는 파일 탐색기 창에서 **App**이라는 새 폴더를 만듭니다.
    * 단일 **앱** 폴더를 클릭 합니다.
    * **폴더 선택을 누릅니다.**
    * **빌드가 완료 될 때까지 대기**
    * 표시 되는 파일 탐색기 창에서 **응용 프로그램** 폴더로 이동 합니다.
    * SharedMixedReality를 두 번 클릭 하 여 Visual Studio를 시작 **합니다.**
* Visual Studio에서 빌드
    * 맨 위 도구 모음을 사용 하 여 대상을 **릴리스** 및 **x 86**으로 변경 합니다.
    * **로컬 컴퓨터** 옆의 화살표를 클릭 하 고 HoloLens에 배포할 **장치** 를 선택 합니다.
    * **장치** 옆에 있는 화살표를 클릭 하 고 혼합 현실 헤드셋에 대해 배포할 **로컬 컴퓨터** 를 선택 합니다.
    * **디버그->** 를 클릭 하 여 디버깅 또는 **컨트롤 + F5** 키를 눌러 응용 프로그램을 시작 합니다.

### <a name="digging-into-the-code"></a>코드 살펴보기

프로젝트 패널에서 **Assets\HoloToolkit\Input\Scripts\Utilities** 으로 이동 하 고 **MixedRealityCameraManager.cs** 를 두 번 클릭 하 여 엽니다.

**개요:** MixedRealityCameraManager.cs는 장치에 따라 품질 수준 및 배경 설정을 조정 하는 간단한 스크립트입니다. 여기서 핵심은 HolographicSettings는 장치가 HoloLens (IsDisplayOpaque false) 또는 몰입 형 헤드셋 (IsDisplayOpaque이 true를 반환) 인지 여부를 스크립트에서 검색할 수 있도록 하는 것입니다.

### <a name="enjoy-your-progress"></a>진행 상황을 경험해 보세요.

이 시점에서 응용 프로그램은 홀로그램만 렌더링 합니다. 나중에 홀로그램에 대 한 상호 작용을 추가할 예정입니다. 두 장치 모두 홀로그램을 동일 하 게 렌더링 합니다. 몰입 형 헤드셋은 파란 하늘 및 구름 배경도 렌더링 합니다.

## <a name="chapter-2---interaction"></a>2 장-상호 작용

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>목표

Windows Mixed Reality 응용 프로그램의 입력을 처리 하는 방법을 보여 줍니다.

### <a name="what-we-will-build"></a>빌드할 내용

1 챕터의 응용 프로그램을 기반으로 하는 기능을 추가 하 여 사용자가 홀로그램을 선택 하 여 HoloLens의 실제 세계 표면 또는 모던 헤드셋의 가상 테이블에 저장할 수 있습니다.

**입력 리프레셔:** HoloLens에서 선택 제스처는 **공중 탭**입니다. 모던 헤드셋에서 Xbox 컨트롤러의 **A** 단추를 사용 합니다. 자세한 내용은 [상호 작용 모델 개요](interaction-fundamentals.md)를 확인 하세요.

### <a name="steps"></a>단계

* 입력 관리자 추가
    * **HoloToolkit > 입력 > Prefabs** **Inputmanager** 를 **계층 구조** 에 **관리자**의 자식으로 끌어 놓습니다.
    * **HoloToolkit > 입력 > Prefabs > 커서** **계층**으로 **커서** 를 끕니다.
* 공간 매핑 추가
    * **HoloToolkit > SpatialMapping > Prefabs** **SpatialMapping** 를 **Hierarchy**로 끌어 놓습니다.
* 가상 Playspace 추가
    * **계층 구조** 에서 **MixedRealityCameraParent** 선택 **경계** 를 확장 합니다.
    * **검사기** 패널에서 **경계** 사용 확인란을 선택 합니다.
    * **AppPrefabs** 에서 **VRRoom** 을 **계층**으로 끌어옵니다.
* WorldAnchorManager 추가
    * **계층**에서 **관리자**를 선택 합니다.
    * **검사기**에서 **구성 요소 추가**를 클릭 합니다.
    * **세계 앵커 관리자**를 입력 합니다.
    * **세계 앵커 관리자** 를 선택 하 여 추가 합니다.
* 섬에 TapToPlace 추가
    * **계층**에서 **아일랜드**를 확장 합니다.
    * **MixedRealityLand**를 선택 합니다.
    * **검사기**에서 **구성 요소 추가**를 클릭 합니다.
    * **누릅니다를 입력 하** 고 선택 합니다.
    * **부모를 탭**하 여 확인 합니다.
    * **배치 오프셋** 을 **(0, 0.1, 0)** 로 설정 합니다.
* 이전 처럼 저장 및 빌드

### <a name="digging-into-the-code"></a>코드 살펴보기

**스크립트 1-GamepadInput.cs**

프로젝트 패널에서 **Assets\HoloToolkit\Input\Scripts\InputSources** 으로 이동 하 고 **GamepadInput.cs** 를 두 번 클릭 하 여 엽니다. 프로젝트 패널의 동일한 경로에서 **InteractionSourceInputSource.cs**를 두 번 클릭 합니다.

두 스크립트 모두 BaseInputSource 공통 기본 클래스를 포함 합니다.

BaseInputSource는 스크립트가 이벤트를 트리거할 수 있도록 하는 InputManager에 대 한 참조를 유지 합니다. 이 경우 InputClicked 이벤트는 관련 됩니다. 이는 스크립트 2, TapToPlace에 대 한 정보를 기억해 야 합니다. GamePadInput의 경우에는 누를 컨트롤러의 단추를 폴링하고, InputClicked 이벤트를 발생 시킵니다. InteractionSourceInputSource의 경우 TappedEvent에 대 한 응답으로 InputClicked 이벤트를 발생 시킵니다.

**스크립트 2-TapToPlace.cs**

프로젝트 패널에서 **Assets\HoloToolkit\SpatialMapping\Scripts** 으로 이동 하 고 **TapToPlace.cs** 를 두 번 클릭 하 여 엽니다.

Holographic 응용 프로그램을 만들 때 대부분의 개발자는 Holograms를 제스처 입력으로 이동 하는 것이 가장 좋습니다. 따라서이 스크립트를 철저히 설명 해 수행자. 이 자습서에서는 몇 가지 사항을 강조 표시 해야 합니다.

먼저 TapToPlace는 IInputClickHandler를 구현 합니다. IInputClickHandler는 GamePadInput.cs 또는 InteractionSourceInputSource.cs에 의해 발생 한 InputClicked 이벤트를 처리 하는 함수를 노출 합니다. OnInputClicked은 TapToPlace를 사용 하는 개체가 포커스에 있는 동안 BaseInputSource에서 클릭을 감지 하면 호출 됩니다. HoloLens를 클릭 하거나 Xbox 컨트롤러의 A 단추를 누르면 이벤트가 트리거됩니다.

Second는 업데이트에서 화면을 검토 하 고 있는지 확인 하기 위해 실행 되는 코드입니다. 여기에는 게임 개체를 테이블 처럼 화면에 놓을 수 있습니다. 모던 헤드셋은 실제 표면의 개념을 포함 하지 않으므로 테이블 위쪽 (Vroom > TableThingy > Cube)을 나타내는 개체는 SpatialMapping 물리학 계층으로 표시 되어 있으므로 업데이트에서 광선 캐스트가 가상 테이블 위쪽과 충돌 합니다.

### <a name="enjoy-your-progress"></a>진행 상황을 경험해 보세요.

이번에는 아일랜드를 선택 하 여 이동할 수 있습니다. HoloLens에서 아일랜드를 실제 표면으로 이동할 수 있습니다. 몰입 형 헤드셋에서 추가 된 가상 테이블로 아일랜드를 이동할 수 있습니다.

## <a name="chapter-3---sharing"></a>3 장-공유

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>목표

네트워크가 올바르게 구성 되었는지 확인 하 고 장치 간에 공간 앵커가 공유 되는 방법을 자세히 설명 합니다.

### <a name="what-we-will-build"></a>빌드할 내용

프로젝트를 여럿이 아닌 프로젝트로 변환 합니다. 세션을 호스트 하거나 조인 하는 데 UI와 논리를 추가 합니다. HoloLens 사용자는 해당 헤드에 대 한 클라우드가 포함 된 세션에서 서로를 볼 수 있으며, 몰입 형 헤드셋 사용자는 앵커 위치 근처의 클라우드를 가집니다. 모던 헤드셋의 사용자는 장면의 원점을 기준으로 HoloLens 사용자를 확인 합니다. HoloLens 사용자는 모두 같은 장소에서 아일랜드의 홀로그램을 보게 됩니다. 이 장 중에는 몰입 형 헤드셋의 사용자가 섬에 있지 않고, HoloLens와 매우 유사 하 게 작동 합니다.

### <a name="steps"></a>단계

* 섬 및 VRRoom 제거
    * **계층** 에서 분리를 마우스 오른쪽 **단추로 클릭 하** 고 **삭제** 를 선택 합니다.
    * **계층** 에서 **VRRoom** 를 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 합니다.
* Usland 추가
    * **AppPrefabs** 에서 **Usland** 를 **계층**으로 끌어옵니다.
* **AppPrefabs** 에서 다음의 각을 **계층**으로 끌어옵니다.
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 이전 처럼 저장 및 빌드

### <a name="digging-into-the-code"></a>코드 살펴보기

프로젝트 패널에서 **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** 으로 이동 하 고 **UnetAnchorManager.cs**를 두 번 클릭 합니다. 한 HoloLens에서 다른 HoloLens와 추적 정보를 공유 하는 기능 (두 장치 모두 동일한 공간을 공유할 수 있음)이 거의 마법입니다. 두 명 이상의 사용자가 동일한 디지털 데이터를 사용 하 여 공동 작업할 수 있는 경우 혼합 현실의 성능이 유지 됩니다.

이 스크립트에서 몇 가지 사항을 확인 해야 합니다.

시작 함수에서 **Isdisplayopaque**검사를 확인 합니다. 이 경우 앵커가 설정 된 것으로 가정 합니다. 이는 몰입 형 헤드셋이 앵커를 가져오거나 내보내는 방법을 노출 하지 않기 때문입니다. 그러나 HoloLens에서 실행 하는 경우이 스크립트는 장치 간의 앵커 공유를 구현 합니다. 세션을 시작 하는 장치는 내보내기를 위한 앵커를 만듭니다. 세션을 조인 하는 장치는 세션을 시작한 장치에서 앵커를 요청 합니다.

**내보내려면**

사용자가 세션을 만들 때 NetworkDiscoveryWithAnchors는 UNETAnchorManagers CreateAnchor 함수를 호출 합니다. CreateAnchor 흐름을 살펴보겠습니다.

먼저 몇 가지 정리 작업을 수행 하 여 이전 앵커에 대해 수집 했을 수 있는 모든 데이터를 정리 합니다. 그런 다음 로드할 캐시 된 앵커가 있는지 확인 합니다. 고정 데이터는 5 ~ 20mb의 경향이 있으므로 캐시 된 앵커를 다시 사용 하면 네트워크를 통해 전송 해야 하는 데이터의 양이 절약 됩니다. 나중에이 작업을 수행 하는 방법을 살펴보겠습니다. 앵커를 다시 사용 하는 경우에도 앵커가 없는 새 클라이언트 조인을 위해 앵커 데이터를 준비 해야 합니다.

앵커 데이터를 준비 하는 경우 WorldAnchorTransferBatch 클래스는 다른 장치나 응용 프로그램에 보내기 위한 앵커 데이터를 준비 하는 기능과 앵커 데이터를 가져오는 기능을 제공 합니다. 내보내기 경로를 사용할 예정 이므로 WorldAnchorTransferBatch에 앵커를 추가 하 고 ExportAsync 함수를 호출 합니다. 그러면 ExportAsync는 내보내기에 대 한 데이터를 생성할 때 WriteBuffer 콜백을 호출 합니다. 모든 데이터를 내보낸 후 ExportComplete가 호출 됩니다. WriteBuffer에서 내보내기 위해 보관 하는 목록에 데이터 청크를 추가 합니다. ExportComplete에서 목록을 배열로 변환 합니다. 또한 AnchorName 변수는 설정 된 경우 앵커를 요청 하는 다른 장치를 트리거합니다.

일부 경우에는 앵커가 내보내지 않고 다시 시도 하는 데이터를 적게 만들게 됩니다. 여기서는 CreateAnchor만 다시 호출 합니다.

내보내기 경로의 마지막 함수는 AnchorFoundRemotely입니다. 다른 장치에서 앵커를 찾으면 해당 장치는 호스트에 지시 하 고,이는 앵커가 "좋은 앵커" 이며 캐시 될 수 있는 신호로 사용 됩니다.

**내보내고**

HoloLens가 세션에 참여 하는 경우 앵커를 가져와야 합니다. UNETAnchorManager의 업데이트 함수에서 AnchorName가 폴링합니다. 앵커 이름이 변경 되 면 가져오기 프로세스가 시작 됩니다. 먼저 로컬 앵커 저장소에서 지정 된 이름의 앵커를 로드 하려고 합니다. 이미 있는 경우 데이터를 다시 다운로드 하지 않고 사용할 수 있습니다. 아직 없는 경우 다운로드를 시작 하는 WaitForAnchor를 호출 합니다.

다운로드가 완료 되 면 NetworkTransmitter_dataReadyEvent가 호출 됩니다. 이렇게 하면 다운로드 한 데이터를 사용 하 여 ImportAsync를 호출 하도록 업데이트 루프가 신호를 받습니다. 가져오기 프로세스가 완료 되 면 ImportAsync에서 ImportComplete를 호출 합니다. 가져오기를 완료 하면 앵커가 로컬 플레이어 저장소에 저장 됩니다. PlayerController.cs는 실제로 AnchorFoundRemotely에 대 한 호출을 수행 하 여 호스트에 올바른 앵커가 설정 되었음을 알립니다.

### <a name="enjoy-your-progress"></a>진행 상황을 경험해 보세요.

이번에는 HoloLens를 사용 하는 사용자가 UI의 **시작 세션** 단추를 사용 하 여 세션을 호스팅합니다. HoloLens 또는 몰입 형 헤드셋의 다른 사용자가 세션을 선택한 다음 UI의 **세션 참가** 단추를 선택 합니다. HoloLens 장치를 사용 하는 여러 사용자가 있는 경우 해당 헤드에 대 한 빨간색 클라우드가 있습니다. 또한 헤드셋은 HoloLens 장치와 동일한 세계 좌표 공간을 찾으려고 시도 하지 않기 때문에 각 모던 헤드셋에는 파란색 클라우드가 있지만 파란색 클라우드가 헤드셋 위에 있지 않습니다.

프로젝트의이 지점은 포함 된 공유 응용 프로그램입니다. 매우 많은 작업을 수행 하지 않으며 기준선으로 작동할 수 있습니다. 다음 장에서는 사람들이 즐길 수 있는 환경을 구축 하기 시작 합니다. 공유 환경 디자인에 대 한 추가 지침을 보려면 여기로 이동 하세요.

## <a name="chapter-4---immersion-and-teleporting"></a>4 장-집중 교육 및 teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>목표

각 유형의 혼합 현실 장치에 대 한 환경을 제공 합니다.

### <a name="what-we-will-build"></a>빌드할 내용

응용 프로그램을 업데이트 하 여 응용 프로그램을 업데이트 하 여 사용자에 게 몰입 형 헤드셋 사용자를 배치 합니다. HoloLens 사용자는 계속 해 서 아일랜드의 눈에 볼 수 있습니다. 각 장치 유형의 사용자는 전 세계에 표시 되는 다른 사용자를 볼 수 있습니다. 예를 들어 몰입 형 헤드셋 사용자는 아일랜드의 다른 경로에 대 한 다른 아바타을 볼 수 있으며,이는 HoloLens 위의 자이언트 사용자를 고립 된 클라우드로 볼 수 있습니다. 모던 헤드셋 사용자는 HoloLens 사용자가 아일랜드를 보고 있는 경우 HoloLens 사용자의 응시 광선의 커서만 볼 수 있습니다. HoloLens 사용자는 각 몰입 형 헤드셋 사용자를 나타내는 아바타에 게 아바타를 보게 됩니다.

**몰입 형 장치에 대 한 업데이트 된 입력:**

* Xbox 컨트롤러의 왼쪽 범퍼 및 오른쪽 범퍼 단추가 플레이어를 회전 합니다.
* Xbox 컨트롤러에서 Y 단추를 누르고 있으면 [텔레포트](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 커서를 사용할 수 있습니다. Y 단추를 놓을 때 커서에 회전 화살표 표시기가 있으면 커서의 위치로 teleported 됩니다.

### <a name="steps"></a>단계

* MixedRealityCameraParent에 MixedRealityTeleport 추가
    * **계층**에서 **usland**를 선택 합니다.
    * **Inspector**에서 **수준 제어**를 사용 하도록 설정 합니다.
    * **계층**에서 **MixedRealityCameraParent**를 선택 합니다.
    * **검사기**에서 **구성 요소 추가**를 클릭 합니다.
    * **혼합 현실 텔레포트** 를 입력 하 고 선택 합니다.

### <a name="digging-into-the-code"></a>코드 살펴보기

모던 헤드셋 사용자는 케이블로 Pc에 테더 링 된 케이블을 사용 하는 것 보다 더 큽니다. 보정 하려면 사용자의 동작과 별개로 카메라를 이동 하는 기능이 필요 합니다. 혼합 현실 응용 프로그램을 디자인 하는 방법에 대 한 자세한 내용은 [편안 함 페이지](comfort.md) 를 참조 하세요 (특히 자체 동작 및 locomotion).

이 프로세스를 설명 하기 위해 두 개의 용어를 정의 하는 것이 유용 합니다. 먼저 **dolly** 는 사용자와 별개로 카메라를 이동 하는 개체입니다. **Dolly** 의 자식 게임 개체가 **기본 카메라가**됩니다. 기본 카메라는 사용자의 머리에 연결 됩니다.

프로젝트 패널에서 **Assets\AppPrefabs\Support\Scripts\GameLogic** 으로 이동 하 고 **MixedRealityTeleport.cs**를 두 번 클릭 합니다.

MixedRealityTeleport에는 두 개의 작업이 있습니다. 먼저 범퍼를 사용 하 여 회전을 처리 합니다. 업데이트 함수에서 왼쪽 범퍼와 RightBumper의 ' ButtonUp '을 폴링합니다. GetButtonUp은 첫 번째 프레임에서 단추가 중단 된 후에만 true를 반환 합니다. 단추 중 하나가 발생 한 경우 사용자가 회전 해야 한다는 것을 알 수 있습니다.

회전할 때 ' 페이드 컨트롤 ' 이라는 간단한 스크립트를 사용 하 여 페이드 아웃 하 고 페이드 아웃 합니다. 이 작업을 수행 하면 사용자가 discomfort으로 이어질 수 있는 자연스럽 게 이동 하는 것을 방지할 수 있습니다. 페이드 인 및 출력 효과는 매우 간단 합니다. **주 카메라**앞에 검은색으로 4 개의 줄이 있습니다. 페이드 아웃 하면 알파 값을 0에서 1로 전환 합니다. 이를 통해 쿼드의 검정색 픽셀은 점차적으로 렌더링 되 고 보이지 않게 됩니다. 다시 페이드 인 되 면 알파 값을 0으로 다시 전환 합니다.

회전을 계산할 때 **dolly** 를 회전 하지만 **기본 카메라**를 중심으로 회전을 계산 하는 것을 확인 합니다. 이는 **기본 카메라가** 0, 0, 0, 0, 0, dolly에 대 한 회전이 사용자의 관점에서 벗어나 표시 되기 때문에 중요 합니다. 실제로 카메라 위치를 중심으로 회전 하지 않는 경우 사용자는 회전 하는 대신 **dolly** 를 중심으로 이동 하 게 됩니다.

MixedRealityTeleport에 대 한 두 번째 작업은 **dolly**이동을 처리 하는 것입니다. 이 작업은 SetWorldPosition에서 수행 됩니다. SetWorldPosition는 원하는 세계 위치를 사용 하 여 사용자가 inhabit 하는 위치를 사용 합니다. 해당 오프셋이 각 프레임에 추가 되기 때문에 **기본 카메라**의 로컬 위치를 뺀 위치에 **dolly** 를 배치 해야 합니다.

두 번째 스크립트는 SetWorldPosition를 호출 합니다. 해당 스크립트를 살펴보겠습니다. 프로젝트 패널에서 **Assets\AppPrefabs\Support\Scripts\GameLogic** 으로 이동 하 고 **TeleportScript.cs**를 두 번 클릭 합니다.

이 스크립트는 MixedRealityTeleport 보다 약간 더 복잡 합니다. 스크립트에서 보관할 Xbox 컨트롤러의 Y 단추가 있는지 확인 하 고 있습니다. 단추를 누르고 있으면 텔레포트 커서가 렌더링 되 고 스크립트는 사용자의 응시 위치에서 광선을 캐스팅 합니다. 이 광선이 가리키는 서피스와 충돌 하는 경우 표면이로 텔레포트 하는 데 적합 한 표면으로 간주 되며, 텔레포트 커서의 애니메이션이 사용 됩니다. 광선이 더 이상 가리키는 표면과 충돌 하지 않으면 커서의 애니메이션이 사용 하지 않도록 설정 됩니다. Y 단추가 해제 되 고 광선의 계산 된 점이 유효한 위치인 경우 스크립트는 광선이 교차 된 위치를 사용 하 여 SetWorldPosition를 호출 합니다.

### <a name="enjoy-your-progress"></a>진행 상황을 경험해 보세요.

이번에는 친구를 찾아야 합니다.

다시 한 번 HoloLens를 사용 하는 사용자는 세션을 호스팅합니다. 다른 사용자가 세션에 참여 합니다. 응용 프로그램은 처음 3 명의 사용자에 게 아일랜드의 세 경로 중 하나에 있는 몰입 형 헤드셋에서 조인 하 게 됩니다. 이 섹션에서는 아일랜드를 자유롭게 살펴보세요.

유의 사항:

1. 클라우드에서 얼굴을 볼 수 있습니다. 그러면 사용 사용자가 HoloLens 사용자가 보고 있는 방향을 볼 수 있습니다.
2. 섬에 있는 아바타는 necks를 회전 합니다. 사용자가 수행 하는 작업을 따르지 않는 것은 아닙니다 (해당 정보는 없음). 하지만 좋은 경험을 위해 노력 하 고 있습니다.
3. HoloLens 사용자가 아일랜드를 살펴보면 사용 사용자가 자신의 커서를 볼 수 있습니다.
4. HoloLens 사용자를 나타내는 클라우드는 그림자를 캐스트 합니다.

## <a name="chapter-5---finale"></a>5 장-Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>목표

두 장치 유형 간에 공동 작업 대화형 환경을 만듭니다.

### <a name="what-we-will-build"></a>빌드할 내용

4 장을 기반으로 하는 몰입 형 헤드셋의 사용자가 아일랜드의 퍼즐 근처에 있으면 HoloLens 사용자는 퍼즐에 대 한 단서를 포함 하는 도구 설명을 얻게 됩니다. 모든 몰입 형 헤드셋 사용자가 퍼즐를 지 나 로켓 방에 있는 "ready pad"로 이동 하면 로켓이 시작 됩니다.

### <a name="steps"></a>단계

* **계층**에서 **usland**를 선택 합니다.
* **검사기**의 **수준 제어**에서 **공동 작업 사용**을 선택 합니다.

### <a name="digging-into-the-code"></a>코드 살펴보기

이제 LevelControl.cs을 살펴보겠습니다. 이 스크립트는 게임 논리의 핵심 이며 게임 상태를 유지 관리 합니다. UNET를 사용 하는 멀티 플레이 게임 이기 때문에,이 자습서를 수정 하는 데 충분 한 수준으로 데이터가 흐르는 방식을 이해 해야 합니다. UNET의 전체 개요는 Unity 설명서를 참조 하세요.

프로젝트 패널에서 **Assets\AppPrefabs\Support\Scripts\GameLogic** 으로 이동 하 고 **LevelControl.cs**를 두 번 클릭 합니다.

몰입 형 헤드셋이 로켓 출시를 위해 준비 된 것을 어떻게 알 수 있는지를 알려주세요. 부울의 세 경로에 해당 하는 부울 목록에 세 개의 중 하나를 설정 하 여 로켓 출시 준비를 전달 합니다. 경로에 할당 된 사용자가 로켓 방 내부의 갈색 패드 위에 있는 경우 경로의 bool이 설정 됩니다. 이제 세부 정보를 확인 합니다.

Update () 함수에서 시작 됩니다. ' 참고 자료 ' 함수가 있음을 확인 합니다. 이를 개발에 사용 하 여 로켓 launch 및 reset 시퀀스를 테스트 했습니다. 다중 사용자 환경에서는 작동 하지 않습니다. 체득 때 다음 정보를 사용할 수 있습니다. 참고 자료 해야 하는지 확인 한 후에는 로컬 플레이어가 사용 인지 확인 합니다. 목표를 달성 하는 방법에 초점을 맞춰야 합니다. If (사용) 검사 내에서 **EnableCollaboration** bool 뒤에 checkgoal 숨기기에 대 한 호출이 있습니다. 이는이 챕터에 대 한 단계를 완료 하는 동안 선택한 확인란에 해당 합니다. EnableCollaboration 내부에서 CheckGoal () 호출을 볼 수 있습니다.

CheckGoal는 몇 가지 수학을 통해 pad에 더 있는지 또는 더 적은지를 확인 합니다. 이 경우 "목표에 도달 했습니다." 라는 로그를 디버그 하 고 ' SendAtGoalMessage () '를 호출 합니다. SendAtGoalMessage에서 playerController를 호출 합니다. 잠시 시간을 절약 하기 위해 코드는 다음과 같습니다.

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

SendAtGoalMessage는 SetGoalIndex를 호출 하는 Cmdis Dat목표가 호출 되며 LevelControl.cs로 돌아갑니다. 언뜻 보기에는 이상한 현상이 보입니다. 플레이어 컨트롤러를 통해 이상한 라우팅이 아닌 SetGoalIndex를 호출 하지 않는 이유는 무엇 인가요? 그 이유는 데이터가 동기화 된 상태로 유지 하기 위해에서 사용 하는 데이터 모델을 준수 한다는 것입니다. 수법 및 스 싱을 방지 하려면 각 개체에 동기화 된 변수를 변경할 수 있는 권한이 있는 사용자가 있어야 합니다. 또한 호스트 (세션을 시작한 사용자)만 데이터를 직접 변경할 수 있습니다. 호스트가 아니지만 권한이 있는 사용자는 변수를 변경 하는 호스트에 ' 명령 '을 보내야 합니다. 기본적으로 호스트에는 사용자를 나타내기 위해 생성 된 개체를 제외한 모든 개체에 대 한 권한이 있습니다. 이 경우이 개체는 playercontroller 스크립트를 포함 합니다. 개체에 대 한 권한을 요청 하 고 변경 작업을 수행 하는 방법이 있지만 플레이어 컨트롤러에 자체 권한이 있으며 플레이어 컨트롤러를 통해 명령을 라우팅하는 방법을 활용 하도록 선택 합니다.

또 다른 방법으로, 우리는 목표를 발견 했을 때 플레이어가 호스트에 알려야 하 고 호스트는 다른 사람에 게 알립니다.

LevelControl.cs에서 SetGoalIndex를 살펴보세요. 여기서는 syclist (AtGoal)의 값을 설정 합니다. 이 작업을 수행 하는 동안 호스트의 컨텍스트에 있습니다. 명령과 마찬가지로 RPC는 호스트가 발급할 수 있는 작업으로, 모든 클라이언트에서 일부 코드를 실행 하도록 합니다. 여기서는 ' RpcCheckAllGoals '을 호출 합니다. 각 클라이언트는 세 개의 AtGoals 모두 설정 되었는지 확인 하 고, 그렇다면 로켓를 시작 합니다.

### <a name="enjoy-your-progress"></a>진행 상황을 경험해 보세요.

이전 장을 기반으로 하 여 세션을 시작 하겠습니다. 지금은 몰입 형 헤드셋의 사용자가 경로에서 "도어"로 이동 하면 HoloLens 사용자만 볼 수 있는 도구 설명이 표시 됩니다. HoloLens 사용자는 몰입 형 헤드셋의 사용자에 게이 단서를 전달 하는 일을 담당 합니다. 각 아바타가 화산 내에서 해당 하는 갈색 패드를 단계별로 실행 하면 로켓이 공간에 시작 됩니다. 장면을 다시 설정 하기 위해 60 초 후에 다시 설정 됩니다.

## <a name="see-also"></a>참고 항목

* [MR 입력 213: 동작 컨트롤러](mixed-reality-213.md)
