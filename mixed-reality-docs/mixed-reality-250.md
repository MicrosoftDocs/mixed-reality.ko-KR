---
title: MR 250-HoloLens 및 몰입 형 헤드셋 공유
description: Unity에서 Visual Studio, HoloLens, 및 Windows Mixed Reality 헤드셋을 사용 하 여 홀로그램 혼합된 현실 장치 간에 공유 하는 자세한 연습을 코딩이 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, 컨트롤러, 공유, 네트워킹, 장치 간 xbox 컨트롤러 mixedrealitytoolkit-unity 몰입 형, 동작
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598045"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR 250을 공유 합니다. HoloLens 및 몰입 형 헤드셋

유니버설 Windows 플랫폼 (UWP)의 유연성을 사용 하 여 여러 장치에 걸쳐 있는 응용 프로그램을 만들려면 쉽습니다. 이러한 유연성을 통해 각 장치의 장점을 활용 하는 환경을 만들 수 있습니다. 이 자습서에서는 HoloLens와 Windows Mixed Reality 몰입 형 헤드셋에서 실행 되는 기본 공유 경험을 설명 합니다. 이 콘텐츠는 미국 워싱턴주 시애틀에서에서 Microsoft Build 2017 컨퍼런스에서 처음 배달 되었습니다.

**이 자습서를 수행합니다.**

* UNET를 사용 하 여 네트워크를 설정 합니다.
* 혼합된 현실 장치의 홀로그램을 공유 합니다.
* 혼합된 현실 장치에 따라 사용 중인 응용 프로그램의 다른 보기를 설정 합니다.
* 여기서 HoloLens 사용자 가이드 몇 가지 간단한 퍼즐을 통해 몰입 형 헤드셋 사용자 경험을 공유를 만듭니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 250을 공유 합니다. HoloLens 및 몰입 형 헤드셋</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 설치 된 Windows 10 PC를 [필요한 개발 도구](install-the-tools.md) 하 고 [Windows Mixed Reality 몰입 형 헤드셋을 지원 하도록 구성](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)합니다.
* PC와 함께 작동 하는 Xbox 컨트롤러입니다.
* 하나 이상의 HoloLens 장치 및 몰입 형 헤드셋 하나입니다.
* 검색에 대 한 UDP 브로드캐스트를 허용 하는 네트워크입니다.

### <a name="project-files"></a>프로젝트 파일

* 다운로드 합니다 [파일](https://github.com/Microsoft/MixedReality250/archive/master.zip) 프로젝트에서 필요 합니다. 파일 위치를 기억 하기 쉬운을 추출 합니다.
* 이 프로젝트에 필요 합니다 [권장 되는 버전의 Unity Windows Mixed Reality 지원과](install-the-tools.md)합니다.

>[!NOTE]
>을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/MixedReality250)합니다.

## <a name="chapter-1---holo-world"></a>1 장-Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>목표

개발 환경이 간단한 프로젝트를 사용 하 여 준비가 되었는지 확인 합니다.

### <a name="what-we-will-build"></a>우리는 빌드

HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋을 홀로그램을 보여 주는 응용 프로그램입니다.

### <a name="steps"></a>단계
* Unity를 엽니다.
    * 선택 **열려**합니다.
    * 프로젝트 파일의 압축을 푼로 이동 합니다.
    * **폴더 선택**을 클릭합니다.
    * *Unity 프로젝트를 처음으로 처리 하는 데에 대 한 약간 소요 됩니다.*
* 혼합 현실 Unity에서 활성화 되어 있는지 확인 합니다.
    * 빌드 설정 대화 상자를 엽니다 (**컨트롤 + Shift + B** 또는 **파일 > 빌드 설정...** ).
    * 선택 **유니버설 Windows 플랫폼** 클릭 **플랫폼 전환**합니다.
    * 선택 **편집 > 플레이어 설정**합니다.
    * 에 **검사기** 오른쪽의 패널에서 확장 **xr 하이 설정을**합니다.
    * 확인 합니다 **지원 되는 가상 현실** 상자입니다.
    * *Windows Mixed Reality 가상 현실 SDK 이어야 합니다.*
* 장면을 만듭니다.
    * 에 **계층 구조** 마우스 오른쪽 단추로 클릭 **주 카메라** 선택 **삭제**합니다.
    * **HoloToolkit > 입력 > Prefabs** 끕니다 **MixedRealityCameraParent** 하는 **계층**합니다.
* 홀로그램 장면에 추가
    * **AppPrefabs** 끕니다 **Skybox** 하는 **장면 보기로**합니다.
    * **AppPrefabs** 끕니다 **관리자** 하는 **계층**합니다.
    * **AppPrefabs** 끕니다 **섬** 하는 **계층**합니다.
* 저장 및 작성
    * 저장 (하거나 **컨트롤 + S** 하거나 **파일 > 저장 장면**)
    * 새 장면을 이므로 이름을 지정 해야 합니다. 이름은 중요 하지 않지만 SharedMixedReality 사용 합니다.
* Visual Studio로 내보내기
    * 빌드 메뉴를 열고 (**컨트롤 + Shift + B** 하거나 **파일 > 빌드 설정**)
    * 클릭 **열기 장면을 추가 합니다.**
    * 확인할 **Unity C# 프로젝트**
    * **빌드**를 클릭합니다.
    * 표시 되는 파일 탐색기 창에서 라는 새 폴더를 만듭니다 **앱**합니다.
    * 한 번 클릭 합니다 **앱** 폴더입니다.
    * 키를 눌러 **폴더를 선택 합니다.**
    * **빌드가 완료 될 때까지 기다리는**
    * 표시 되는 파일 탐색기 창에서 이동 합니다 **앱** 폴더입니다.
    * 두 번 클릭 **SharedMixedReality.sln** Visual Studio를 시작 하려면
* Visual Studio에서 빌드
    * 대상에 맨 위의 도구 모음을 사용 하 여 변경할 **릴리스** 하 고 **x86**합니다.
    * 다음 화살표를 클릭 **로컬 컴퓨터** 선택한 **장치** HoloLens에 배포 하려면
    * 다음 화살표를 클릭 **장치** 선택한 **로컬 컴퓨터** 혼합된 현실 헤드셋에 대 한 배포 합니다.
    * 클릭 **디버그-> 디버깅 하지 않고 시작** 하거나 **컨트롤 + F5** 응용 프로그램을 시작 합니다.

### <a name="digging-into-the-code"></a>코드 살펴보기

프로젝트 패널에서로 이동 **Assets\HoloToolkit\Input\Scripts\Utilities** 를 두 번 클릭 **MixedRealityCameraManager.cs** 하 여 엽니다.

**개요:** MixedRealityCameraManager.cs는 장치에 따라 품질 수준 및 배경색 설정을 조정 하는 간단한 스크립트입니다. 키 HolographicSettings.IsDisplayOpaque 장치는 HoloLens 인지 여부를 검색 하는 스크립트를 허용 하는 다음과 같습니다 (IsDisplayOpaque false 반환) 또는 몰입 형 헤드셋 (IsDisplayOpaque true 반환).

### <a name="enjoy-your-progress"></a>진행 상황을 이용할 수 있습니다

이 시점에서 응용 프로그램을 홀로그램을 렌더링 됩니다. 나중에 상호 작용을 홀로그램을 추가 합니다. 장치와 동일 하 게 렌더링 된 홀로그램 합니다. 몰입 형 헤드셋 파란색 하늘 및 클라우드 배경이 렌더링도 됩니다.

## <a name="chapter-2---interaction"></a>2 장-상호 작용

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>목표

Windows Mixed Reality 응용 프로그램에 대 한 입력을 처리 하는 방법을 보여 줍니다.

### <a name="what-we-will-build"></a>우리는 빌드

1 장에서 응용 프로그램을 토대로 사용자를 홀로그램 승차 및 HoloLens에는 실제 화면 또는 몰입 형 헤드셋 가상 테이블에 배치할 수 있도록 하는 기능을 추가 합니다.

**입력된 세부 정보:** 선택 제스처에 HoloLens 합니다 **어 탭**합니다. 몰입 형 헤드셋에서 사용 합니다 **는** Xbox 컨트롤러에 단추입니다. 입력에 대 한 자세한 내용은 [여기서 시작](gestures.md)합니다.

### <a name="steps"></a>단계
* 입력 관리자 추가
    * **HoloToolkit > 입력 > Prefabs** 끕니다 **InputManager** 하 **계층** 자식인 **관리자**합니다.
    * **HoloToolkit > 입력 > Prefabs > 커서** 끕니다 **커서** 하 **계층**합니다.
* 공간 매핑 추가
    * **HoloToolkit > SpatialMapping > Prefabs** 끕니다 **SpatialMapping** 하 **계층**합니다.
* 가상 Playspace 추가
    * **계층 구조** 확장 **MixedRealityCameraParent** 선택 **경계**
    * **검사기** 패널을 사용 하도록 설정 하려면 확인란 **경계**
    * **AppPrefabs** 끕니다 **VRRoom** 하 **계층**합니다.
* WorldAnchorManager 추가
    * **계층 구조**를 선택 **관리자**합니다.
    * **검사기**, 클릭 **구성 요소 추가**합니다.
    * 형식 **World 앵커 Manager**합니다.
    * 선택 **World 앵커 Manager** 추가 합니다.
* 아일랜드에 TapToPlace 추가
    * **계층 구조**를 확장 하 고 **섬**합니다.
    * 선택 **MixedRealityLand**합니다.
    * **검사기**, 클릭 **구성 요소 추가**합니다.
    * 형식 **위치에 탭** 선택 합니다.
    * 확인할 **탭에 부모 놓기**합니다.
    * 설정할 **배치 오프셋** 하 **(0, 0.1, 0)** 합니다.
* 저장 하 고 이전 처럼 빌드

### <a name="digging-into-the-code"></a>코드 살펴보기

**1-GamepadInput.cs 스크립트**

프로젝트 패널에서로 이동 **Assets\HoloToolkit\Input\Scripts\InputSources** 를 두 번 클릭 **GamepadInput.cs** 하 여 엽니다. 프로젝트 패널의 동일한 경로에서 두 번 클릭할 수도 **InteractionSourceInputSource.cs**합니다.

두 스크립트 BaseInputSource 공통 기본 클래스에 있는 참고 합니다.

BaseInputSource는 InputManager 이벤트를 트리거하는 스크립트를 허용 하는에 대 한 참조를 유지 합니다. 이 경우 InputClicked 이벤트 관련이 있습니다. 이 스크립트 2 TapToPlace 때 기억해 야 할 중요 한 됩니다. GamePadInput의 경우 누르는 컨트롤러에는 단추에 대해 폴링한 다음 InputClicked 이벤트를 발생 시킵니다. InteractionSourceInputSource의 경우는 TappedEvent에 대 한 응답에서 InputClicked 이벤트를 발생 했습니다.

**2-TapToPlace.cs 스크립트**

프로젝트 패널에서로 이동 **Assets\HoloToolkit\SpatialMapping\Scripts** 를 두 번 클릭 **TapToPlace.cs** 하 여 엽니다.

대부분의 개발자 Holographic 응용 프로그램을 만들 때 구현 하려면 먼저 제스처 입력을 사용 하 여 홀로그램으로 이동 합니다. 따라서이 스크립트를 철저 하 게 의견 endeavored 했습니다 했습니다. 몇 가지 사항은이 자습서에 대 한 강조 표시 하는 것입니다.

첫째, 참고 TapToPlace IInputClickHandler를 구현 하도록 합니다. IInputClickHandler는 GamePadInput.cs 또는 InteractionSourceInputSource.cs 발생 하는 InputClicked 이벤트를 처리 하는 함수를 노출 합니다. OnInputClicked는 BaseInputSource TapToPlace 사용 하 여 개체에 포커스가 있을 때 클릭을 검색 하는 경우 호출 됩니다. HoloLens에 airtapping 또는 Xbox 컨트롤러에는 단추를 누르면 이벤트를 트리거합니다.

둘째 코드 참조 테이블과 같은 화면에서 게임 개체를 배치할 수 있도록 화면을 현재 검토 중 경우 업데이트에서 실행 됩니다. 몰입 형 헤드셋 없는 실제 표면의 개념 이므로 테이블 위쪽을 나타내는 개체 (Vroom > TableThingy > 큐브) 업데이트에서 캐스팅 광선 가상 테이블 맨와 충돌 하므로 SpatialMapping 물리학 계층으로 표시 되었습니다.

### <a name="enjoy-your-progress"></a>진행 상황을 이용할 수 있습니다

이 시간 이동는 아일랜드를 선택할 수 있습니다. HoloLens에 실제 화면에는 아일랜드를 이동할 수 있습니다. 몰입 형 헤드셋에 추가한 가상 테이블에는 아일랜드를 이동할 수 있습니다.

## <a name="chapter-3---sharing"></a>3 장-공유

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>목표

네트워크가 올바르게 구성 되었는지 확인 하 고 세부 정보 공간 앵커 장치 간에 공유 되는 방법입니다.

### <a name="what-we-will-build"></a>우리는 빌드

멀티 플레이 프로젝트에 프로젝트를 변환 합니다. UI 및 논리 호스트나 조인 세션에 추가 합니다. HoloLens 사용자를 머리를 통해 클라우드를 사용 하 여 세션에서 서로으로 표시 되 고 몰입 형 헤드셋 사용자가 앵커 인 가까이 있는 클라우드. 몰입 형 헤드셋에 HoloLens 사용자 장면의 원점 기준으로 표시 됩니다. HoloLens 사용자에는 동일한 위치에서 아일랜드의 홀로그램을 표시 됩니다. 몰입 형 헤드셋 사용자가이 장 중의 섬에 되지 것입니다 하지만 됩니다 매우 비슷하게 작동 HoloLens는 아일랜드의 새 뷰를 사용 하 여 키 이며

### <a name="steps"></a>단계
* 제거 섬 및 VRRoom
    * **계층 구조** 마우스 오른쪽 단추로 클릭 **섬** 선택 **삭제**
    * **계층 구조** 마우스 오른쪽 단추로 클릭 **VRRoom** 선택 **삭제**
* Usland 추가
    * **AppPrefabs** 끕니다 **Usland** 하 **계층**합니다.
* **AppPrefabs** 각 다음을 끌어 **계층**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 저장 하 고 이전 처럼 빌드

### <a name="digging-into-the-code"></a>코드 살펴보기

프로젝트 패널에서로 이동 **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** 를 두 번 클릭 **UnetAnchorManager.cs**합니다. 하나의 HoloLens 장치 모두 동일한 공간을 공유할 수 있도록 다른 HoloLens를 사용 하 여 추적 정보를 공유에 대 한 기능은 마법 거의입니다. 두 개의 혼합된 현실 활용 살아있는 또는 더 많은 사람들이 동일한 디지털 데이터를 사용 하 여 공동 작업할 수 있습니다.

이 스크립트에서 지적 하는 몇 가지 사항은 다음과 같습니다.

시작 함수에 대 한 검사를 알 수 있듯이 **IsDisplayOpaque**합니다. 이 경우 앵커 설정 되어 있는지 가정 합니다. 즉, 몰입 형 헤드셋 가져오기 또는 내보내기 앵커 하는 방법을 제공 하지 않습니다. 그러나는 HoloLens에서 실행 하는,이 스크립트를 장치 간에 공유 앵커 구현 합니다. 세션을 시작 하는 장치는 내보내기에 대 한 앵커를 만듭니다. 세션에 참가 하는 장치는 해당 세션을 시작 하는 장치에서 앵커를 요청 합니다.

**내보내기:**

사용자 세션을 만들 때 NetworkDiscoveryWithAnchors UNETAnchorManagers CreateAnchor 함수를 호출 합니다. 보겠습니다 CreateAnchor 흐름을 따릅니다.

이전 앵커에 대 한 수집 수 데이터를 정리 하면, 몇 가지 정리 작업을 수행 하 여 시작 합니다. 그런 다음 부하에 캐시 된 앵커 인지 확인 합니다. 앵커 데이터 5-20 MB, 네트워크를 통해 전송 해야 하는 데이터의 양에 따라 저장할 수 캐시 된 앵커를 다시 사용 하므로 사이 여야 하는 경향이 있습니다. 잠시 후 작동 방식을 살펴보겠습니다. 앵커를 다시 사용 되는 경우에 데이터를 준비 하는 새 클라이언트를 조인 하는 경우 없는 앵커 앵커를 가져올 해야 합니다.

앵커 데이터 준비의 말하자면 WorldAnchorTransferBatch 클래스는 앵커 데이터를 가져오는 다른 장치 또는 응용 프로그램 및 기능을 보내기에 대 한 앵커 데이터를 준비 하는 기능을 제공 합니다. 내보내기 경로에 되므로 우리의 앵커를 WorldAnchorTransferBatch에 추가 하 고 ExportAsync 함수를 호출 합니다. ExportAsync는 WriteBuffer 콜백을 호출 다음 내보내기에 대 한 데이터를 생성 합니다. 모든 데이터를 내보낸 경우 ExportComplete 호출 됩니다. WriteBuffer에서는 추가 데이터의 청크 목록 내보내기에 대 한 유지 합니다. ExportComplete에서 배열에 목록을 변환합니다. AnchorName 변수의 설정 됩니다, 다른 장치를 트리거하는 사용 하지 않더라도 앵커를 요청 하려면.

앵커 않습니다 내보내거나 만들어집니다. 따라서 거의 데이터는 일부 경우에 다시 시도 합니다. 여기에서는 방금 CreateAnchor 다시 호출합니다.

내보내기 경로에 마지막 기능은 AnchorFoundRemotely 사용 하는 것입니다. 다른 장치에서 앵커를 찾으면 해당 장치에는 호스트에 알려 고 호스트 앵커 "좋은 앵커"는 신호로 사용 됩니다 캐시 될 수 있습니다.

**가져오기:**

HoloLens 세션에 들어오면 앵커를 가져올 해야 합니다. UNETAnchorManager의 업데이트 함수에는 AnchorName은 사용 하는 간격으로 폴링됩니다. 앵커 이름이 변경 되 면 가져오기 프로세스가 시작 됩니다. 먼저 로컬 앵커 저장소에서 지정 된 이름의 앵커를 로드 하려고 합니다. 를 이미 보유 하 고 데이터를 다시 다운로드 하지 않고 사용할 수 있습니다. 에서는 인증서가 없는 경우 WaitForAnchor 다운로드를 시작 하는 호출 했습니다.

다운로드가 완료 되 면 NetworkTransmitter_dataReadyEvent 라고 합니다. 이 업데이트 루프를 ImportAsync 다운로드 한 데이터를 사용 하 여 호출을 신호로 알립니다. 가져오기 프로세스가 완료 되 면 ImportAsync ImportComplete를 호출 합니다. 가져오기에 성공한 경우 앵커 플레이어 로컬 저장소에 저장 됩니다. 에서는 PlayerController.cs 실제로 호출 하 AnchorFoundRemotely 좋은 앵커를 설정한 경우 알고 있어야 하는 호스트 수 있도록 합니다.

### <a name="enjoy-your-progress"></a>진행 상황을 이용할 수 있습니다

이 이번에는 HoloLens 사용 하 여 사용자를 호스팅할 사용 하 여 세션을 **세션을 시작** 는 UI의 단추입니다. 다른 사용자에 게 모두 HoloLens 또는 몰입 형 헤드셋에서 세션 선택한 다음 선택 합니다 **세션에 참가** 는 UI의 단추입니다. HoloLens 장치를 사용 하 여 여러 사람이 경우 겨누는 위에 빨간색 클라우드를 갖습니다. 각 몰입 형 헤드셋에 대 한 파란색 클라우드 됩니다 있지만 파란색 클라우드는 헤드셋 HoloLens 장치 같은 세계 좌표 공간을 찾으려고 시도 하지 않는 대로 헤드셋, 위의 되지 않습니다.

이 프로젝트에 점이 포함 된 공유 응용 프로그램; 매우 많은 작업을 수행 하지 않습니다 하 고 기준으로 작동할 수 있습니다. 다음 장에서 이용 하려면 사용자 환경에서 빌드 시작 합니다. 공유 환경 디자인 지침 얻기위해를 여기로 이동 합니다.

## <a name="chapter-4---immersion-and-teleporting"></a>4 장-집중 교육 및 텔레포트

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>목표

각 유형의 혼합된 현실 장치 환경을 제공 합니다.

### <a name="what-we-will-build"></a>우리는 빌드

몰입 형 뷰를 사용 하 여 섬에 몰입 형 헤드셋 사용자를 추가할 응용 프로그램을 업데이트 됩니다. HoloLens 사용자는 여전히 섬 부 감 뷰를 갖습니다. 전 세계에 나타나는 각 장치 유형의 사용자가 다른 사용자가 볼 수 있습니다. 예를 들어 몰입 형 헤드셋 사용자의 섬에 다른 경로 상의 다른 아바타를 볼 수 있습니다 및 HoloLens 사용자 위에 섬 거 대 한 클라우드로 표시 됩니다. 몰입 형 헤드셋 사용자 섬에 HoloLens 사용자가 보는 경우에 HoloLens 사용자 게이즈 광선의 커서를 표시 됩니다. HoloLens 사용자는 각 몰입 형 헤드셋 사용자를 나타내는 섬에 아바타를 표시 됩니다.

**몰입 형 장치에 대 한 업데이트 된 입력:**
* Xbox 컨트롤러에서 범퍼 및 범퍼 오른쪽 단추를 왼쪽된 회전 플레이어
* 하면 Xbox 컨트롤러에서 Y 단추를 보유 하는 [텔레포트](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 커서입니다. 에 있는 경우 커서 회전 화살표 표시기 Y 단추를 놓을 때 커서의 위치를 여기저기 수 있습니다.

### <a name="steps"></a>단계
* MixedRealityCameraParent MixedRealityTeleport 추가
    * **계층 구조**를 선택 **Usland**합니다.
    * **검사기**를 사용 하도록 설정 **수준 제어**입니다.
    * **계층 구조**를 선택 **MixedRealityCameraParent**합니다.
    * **검사기**, 클릭 **구성 요소 추가**합니다.
    * 형식 **혼합 현실 텔레포트** 선택 합니다.

### <a name="digging-into-the-code"></a>코드 살펴보기

케이블을 사용 하 여 Pc에 테더 링 된 몰입 형 헤드셋 사용자는 이지만 섬 케이블 깁니다 보다 큽니다. 를 보완 하는 사용자의 동작 독립적으로 카메라를 이동할 수를 해야 합니다. 참조 하십시오 합니다 [편안 하 게 페이지](comfort.md) (특히 자체 동작 및 locomotion) 혼합된 현실 응용 프로그램을 디자인 하는 방법에 대 한 자세한 내용은 합니다.

이 프로세스를 설명 하기 위해 두 용어를 정의 하는 것이 유용할 됩니다. 먼저 **dolly** 카메라를 이동 하지 독립적으로 사용자에서는 개체 여야 합니다. 자식 게임 개체를 **dolly** 됩니다 합니다 **주 카메라**합니다. 주 카메라는 사용자의 헤드에 연결 됩니다.

프로젝트 패널에서로 이동 **Assets\AppPrefabs\Support\Scripts\GameLogic** 를 두 번 클릭 **MixedRealityTeleport.cs**합니다.

MixedRealityTeleport는 두 가지 작업이 있습니다. 먼저 범퍼를 사용 하 여 회전을 처리 합니다. 업데이트 함수에서 LeftBumper RightBumper에 'ButtonUp'에 대해 폴링합니다. GetButtonUp만 true를 반환 단추가 다운 된 후 첫 번째 프레임에 있습니다. 단추 중 하나에서 발생 하는 경우 알 수는 사용자가 회전 해야 합니다.

에서는 회전 하는 경우 페이드 수행 하 고 '제어 페이드' 라고 하는 간단한 스크립트를 사용 하 여 페이드 인 합니다. 사용자 뜨거움을 일으킬 수 있는 비 자연 이동 보지 못하도록 방지 하기 위해 이렇게 합니다. 시작 및 종료 효과 누르는 페이드는 매우 간단 합니다. 앞의 첫 줄을 black 쿼드 있다고 합니다 **주 카메라**합니다. 페이드아웃 알파 값을 0에서 1 전환 했습니다. 점진적으로 렌더링 하 고 뒤에 아무 것도 모호 하 게 쿼드의 검정 픽셀이 그러면 합니다. 다시 페이딩 알파 값 0으로 다시 전환 했습니다.

회전 각도 계산 하는 경우 회전 된 것을 확인 하세요 **dolly** 회전 각도 계산 하지만 합니다 **주 카메라**. 이것이 멀리 만큼 이나 중요 합니다 **주 카메라** 됩니다 0,0,0에서 정확도 dolly 중심의 회전은 사용자의 관점에서 합니다. 사실, 카메라 위치 주변 회전 하지 않습니다 하는 경우 사용자에서 이동 대 호 합니다 **dolly** 회전 하는 대신 합니다.

MixedRealityTeleport에 대 한 두 번째 작업을 처리 하는 이동 합니다 **dolly**합니다. SetWorldPosition에서 수행 됩니다. SetWorldPosition 원하는 세계 좌표 위치, 사용자가 이러한 산재 percieve 있는 위치를 사용 합니다. 넣어야 우리의 **dolly** 의 로컬 위치에서 뺀 값에 해당 위치에는 **주 카메라**처럼 각 프레임 해당 오프셋 추가 됩니다.

두 번째 스크립트 SetWorldPosition를 호출합니다. 해당 스크립트를 살펴보겠습니다. 프로젝트 패널에서로 이동 **Assets\AppPrefabs\Support\Scripts\GameLogic** 를 두 번 클릭 **TeleportScript.cs**합니다.

이 스크립트는 MixedRealityTeleport 보다 약간 더 복잡 합니다. 스크립트를 Xbox 컨트롤러에서 Y 단추를 누르고를 확인 합니다. 커서는 텔레포트 아래로 렌더링 됩니다 단추 유지 되는 동안에 스크립트를 사용자의 게이즈 위치 광선을 그린 캐스팅 합니다. 해당 광선 보다는 화면을 사용 하 여 충돌 하는 경우, 텔레포트 좋은 화면 화면으로 간주 됩니다 및 텔레포트 커서에서 애니메이션을 사용할 위쪽을 가리키는 합니다. 광선을 더 많거나 적은 포인팅 화면을 충돌 하지 않도록, 애니메이션 커서에서 비활성화 됩니다. Y 단추를 놓을 때 광선의 계산 된 점은 올바른 위치를 스크립트 SetWorldPosition 광선과 교차 하는 위치를 사용 하 여 호출 합니다.

### <a name="enjoy-your-progress"></a>진행 상황을 이용할 수 있습니다

이 이번 친구를 찾아 해야 합니다.

이번에 HoloLens 사용 하 여 사용자 세션을 호스팅합니다. 다른 사용자가 세션에 연결 됩니다. 응용 프로그램에는 처음 세 사용자의 섬에 세 가지 경로 중 하나는 몰입 형 헤드셋에서 참여를 배치 합니다. 이 단원의 섬 살펴보시기 바랍니다.

에 세부 정보:
1. HoloLens 사용자를 찾을 방향을 참조 immersed 사용자 도움이 되는 클라우드의 얼굴 볼 수 있습니다.
2. 섬에 아바타 necks 회전 하는 경우 사용자가 현재 수행 중인 따릅니까 없습니다 (해당 정보가 있는 없는) 실제 실제로 이지만 유용한 환경에 대해 수행 하 합니다.
3. HoloLens 사용자는 아일랜드를 살펴보면 immersed 사용자가 커서를 볼 수 있습니다.
4. HoloLens 사용자를 대표 하는 클라우드 그림자를 캐스팅 합니다.

## <a name="chapter-5---finale"></a>5 장-알아내기란

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>목표

두 장치 유형 간에 대화형는 공동 작업 환경을 만듭니다.

### <a name="what-we-will-build"></a>우리는 빌드

을 기반으로 구축 4 장을 가져오면는 몰입 형 헤드셋을 사용 하 여 사용자 a 근처의 섬에는 HoloLens 사용자 퍼즐을 알아내는 단서를 사용 하 여 도구 설명을 받게 됩니다. 해당 퍼즐 지난 및 "준비 패드"에 rocket 방에 가져오려면 몰입 형 헤드셋 사용자의 모든 면을 rocket 시작 됩니다.

### <a name="steps"></a>단계
* **계층 구조**를 선택 **Usland**합니다.
* **검사기**의 **수준 제어**, 확인 **공동 작업을 사용 하도록 설정**합니다.

### <a name="digging-into-the-code"></a>코드 살펴보기

알려주세요 LevelControl.cs을 살펴보겠습니다. 이 스크립트의 게임 논리의 핵심 이며 게임 상태를 유지 관리 합니다. UNET를 사용 하 여 멀티 플레이 게임 이므로 데이터가 흐르는 방식, 적어도 충분히이 자습서를 수정 하려면 이해 해야 합니다. UNET의 자세한 개요를 Unity의 설명서를 참조 하세요.

프로젝트 패널에서로 이동 **Assets\AppPrefabs\Support\Scripts\GameLogic** 를 두 번 클릭 **LevelControl.cs**합니다.

알려주세요는 몰입 형 헤드셋 rocket 출시를 위해 준비 되었는지 어떻게을 나타냅니다. Rocket 시작 준비 값일의 섬에 세 가지 경로에 해당 하는 목록에서 세 가지 값일 중 하나를 설정 하 여 전달 됩니다. 패스의 bool rocket 룸 내부의 갈색 패드를 기반으로 경로에 할당 된 사용자가 설정 됩니다. 이제 세부 정보를 확인 합니다.

Update () 함수에서 시작 하겠습니다. '참고' 함수는를 기록 됩니다. 에서는 하는 데 사용이 개발에서 rocket 시작 테스트 시퀀스를 다시 설정 합니다. 다중 사용자 환경에서 작동 하지 않습니다. 다행히 다음과 같은 정보를 화하고 시간을 기준으로 작동 하는지 만들 수 있습니다. 에서는 참고 해야 하는 경우를 확인, 후 로컬 플레이어 사용 되는 경우 참조 확인 합니다. 어떻게 찾을 수 있는지 목표에 집중 하려고 합니다. If 내부 (사용)는 CheckGoal 뒤 숨기기에 대 한 호출을 확인 합니다 **EnableCollaboration** bool. 이 장의 단계를 완료 하는 동안 선택한 확인란에 해당 합니다. EnableCollaboration 내부 CheckGoal()에 대 한 호출을 표시 됩니다.

CheckGoal 우리는 더 많거나 적은 패드에 고정 몇 가지 계산을 수행 합니다. 우리는 우리 Debug.Log "목표에서 Arrived" 하 고 'SendAtGoalMessage()' 호출 합니다. SendAtGoalMessage playerController.SendAtGoal 호출합니다. 일부 시간 절약을 위해 코드는 다음과 같습니다.

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

SendAtGoalMessage CmdSendAtGoal, LevelControl.cs 년대에서 되는 호출 levelState.SetGoalIndex 호출 하는 note 합니다. 얼핏 보기에 이상한 것 같습니다. 호출 하지 않는 이유만이 아닌 SetGoalIndex 플레이어 컨트롤러를 통해 라우팅 이상한? 이유는 UNET 데이터 동기화를 사용 하 여 데이터 모델을 준수 하는 것입니다. 수법을 행 및 쓰 래 싱을 방지 하려면 UNET 각 개체의 동기화 된 변수를 변경할 권한이 사용자에 있어야 합니다. 또한 호스트 (세션을 시작 하는 사용자)만 데이터를 직접 변경할 수 있습니다. 호스트 되지 않으며, 권한이 있는 사용자는 'command' 변수를 변경 하는 호스트에 전송 해야 합니다. 기본적으로 호스트는 사용자를 나타내는 생성 된 개체를 제외 하 고 모든 개체에 대해 권한을 갖습니다. 이 경우가이 개체는 playercontroller 스크립트를 포함 합니다. 개체에 대 한 권한을 요청 하 고 변경 내용을 확인 하는 방법을 이지만 플레이어 컨트롤러 플레이어 컨트롤러를 통해 자체 인증 기관과 경로 명령에 팩트를 활용 하 여 선택 합니다.

다시 말해 목표에서 직접 찾았습니다 플레이어 호스트에 지시 해야 하 고 호스트 다른 모든 사람에 게 합니다.

LevelControl.cs 살펴보겠습니다 SetGoalIndex 년대. 여기서는 synclist (AtGoal)에서 값의 값을 설정 했습니다. 이 작업을 수행 하는 동안 호스트의 컨텍스트에 있는 것을 기억 합니다. 명령에는 마찬가지로 RPC 호스트에서 실행할 수 있는 것으로 인해 일부 코드를 실행 하는 모든 클라이언트. 여기 'RpcCheckAllGoals' 라고합니다. 개별적으로 각 클라이언트 모든 세 AtGoals 설정 된 경우 확인를 그렇다면 rocket를 시작 합니다.

### <a name="enjoy-your-progress"></a>진행 상황을 이용할 수 있습니다

이전 장에서 토대로 하기 전에 세션을 시작 합니다. 사용자가 해당 경로에 "도어"를 몰입 형 헤드셋 get으로이 이번 도구 설명이 HoloLens 사용자만 볼 수 있는지 표시 됩니다. HoloLens 사용자는 몰입 형 헤드셋에서 사용자에 게이 단서를 통신 하는 일을 담당 합니다. rocket 화산의 안에 해당 해당 갈색 패드에 각 아바타가 단계별 면 공간에 시작 됩니다. 이 작업을 다시 수행할 수 있도록 장면 60 초 후 다시 설정 됩니다.

## <a name="see-also"></a>참조
* [MR 입력 213: 컨트롤러 동작](mixed-reality-213.md)
