---
title: MR 입력 210-응시
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 응시 개념에 대 한 자세한 내용을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 응시
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434686"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. HoloLens 2에 대 한 [새로운 일련의 자습서](mrlearning-base.md) 가 게시 되었습니다.

# <a name="mr-input-210-gaze"></a>MR 입력 210: 응시

[응시](gaze-and-commit.md) 는 첫 번째 입력 형태 이며 사용자의 의도 및 인식을 표시 합니다. MR 입력 210 (즉, 프로젝트 탐색기)은 Windows Mixed Reality의 응시 관련 개념을 자세히 설명 합니다. 앱이 사용자의 응시에 대해 알고 있는 기능을 최대한 활용 하 여 커서 및 holograms에 상황별 인식을 추가할 예정입니다.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

여기에는 응시 개념을 배우는 데 도움이 되는 친숙 한 astronaut 있습니다. [MR 기본 101](holograms-101.md)에는 방금 응시 한 간단한 커서가 있었습니다. 지금은 간단한 커서를 넘어 단계를 이동 하 고 있습니다.

* 커서와 holograms를 설정 하는 중입니다. 사용자가 찾고 있는 위치에 따라 또는 사용자가 찾고 *있지 않은* 위치에 따라 변경 됩니다. 이렇게 하면 컨텍스트를 인식 합니다.
* 사용자에 게 대상에 대 한 추가 컨텍스트를 제공 하는 커서 및 holograms에 피드백을 추가 합니다. 이 피드백은 오디오 및 시각적 개체 일 수 있습니다.
* 사용자가 더 작은 대상에 도달 하는 데 도움이 되는 기술 대상을 보여 드리겠습니다.
* 방향 표시기를 사용 하 여 holograms에 사용자의 주의를 그리는 방법을 보여 드리겠습니다.
* 전 세계에서 이동할 때 사용자와 holograms 하는 기술을 가르쳐 드리겠습니다.

>[!IMPORTANT]
>아래 각 장에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다. 단계별 지침은 정확 하 고 최신 상태 이지만 최신의 비디오에서 스크립트 및 시각적 개체를 볼 수 있습니다. Posterity에 대 한 비디오는 포함 되어 있지만 적용 되는 개념은 그대로 유지 됩니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 210: 응시</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 확인 사항

### <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.
* 몇 가지 C# 기본적인 프로그래밍 기능.
* [MR 기본 101](holograms-101.md)를 완료 해야 합니다.
* [개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)있습니다.

### <a name="errata-and-notes"></a>정오표 및 참고 사항

* Visual Studio에서 코드의 중단점을 적중 하려면 도구-> 옵션-> 디버깅에서 "내 코드만"을 사용 하지 않도록 설정 (선택 취소) 해야 합니다.

## <a name="chapter-1---unity-setup"></a>1 장-Unity 설치

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>목표

* HoloLens 개발을 위해 Unity를 최적화합니다.
* 자산을 가져오고 장면을 설정합니다.
* HoloLens에서 astronaut를 확인 합니다.

### <a name="instructions"></a>지침

1. Unity를 시작합니다.
2. **새 프로젝트**를 선택 합니다.
3. 프로젝트 이름을 **Modelexplorer**로 합니다.
4. 이전에 보관 하지 않은 **응시** 폴더로 위치를 입력 합니다.
5. 프로젝트가 **3D**로 설정되어 있는지 확인합니다.
6. **Create Project**를 클릭합니다.

### <a name="unity-settings-for-hololens"></a>HoloLens 용 Unity 설정

내보내려는 앱이 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다고 Unity에 알려야 합니다. HoloLens를 가상 현실 장치로 추가 하 여이 작업을 수행 합니다.

1. **편집 > 프로젝트 설정 > 플레이어**로 이동 합니다.
2. 플레이어 설정에 대 한 **검사기 패널** 에서 **Windows 스토어** 아이콘을 선택 합니다.
3. **XR 설정** 그룹을 확장 합니다.
4. **렌더링** 섹션에서 **가상 현실 지원 됨** 확인란을 선택 하 여 새 **가상 현실 sdk** 목록을 추가 합니다.
5. **Windows Mixed Reality** 가 목록에 나타나는지 확인 합니다. 그렇지 않은 경우 목록 맨 아래에 있는 **+** 단추를 선택 하 고 **Windows Holographic**를 선택 합니다.

다음으로, scripting 백 엔드를 .NET으로 설정 해야 합니다.

1. **편집 > 프로젝트 설정 > 플레이어** 로 이동 합니다 (이전 단계에서이 작업을 계속 진행할 수 있음).
2. 플레이어 설정에 대 한 **검사기 패널** 에서 **Windows 스토어** 아이콘을 선택 합니다.
3. **기타 설정** 구성 섹션에서 **Scripting 백 엔드가** **.net** 으로 설정 되어 있는지 확인 합니다.

마지막으로, HoloLens에서 빠른 성능을 얻기 위해 품질 설정을 업데이트 합니다.

1. **편집 > 프로젝트 설정 > 품질**로 이동 합니다.
2. Windows 스토어 아이콘 아래의 **기본** 행에 있는 아래쪽 화살표를 클릭 합니다.
3. **Windows 스토어 앱**에 대해 **매우 낮음** 을 선택 합니다.

### <a name="import-project-assets"></a>프로젝트 자산 가져오기

1. **프로젝트** 패널에서 **자산** 폴더를 마우스 오른쪽 단추로 클릭 합니다.
2. **패키지 가져오기 > 사용자 지정 패키지**를 클릭 합니다.
3. 다운로드 한 프로젝트 파일로 이동 하 고 **unitypackage**를 클릭 합니다.
4. **열기**를 클릭합니다.
5. 패키지가 로드 되 면 **가져오기** 단추를 클릭 합니다.

### <a name="setup-the-scene"></a>장면 설정

1. 계층에서 **주 카메라**를 삭제 합니다.
2. **HoloToolkit** 폴더에서 **입력** 폴더를 열고 **Prefabs** 폴더를 엽니다.
3. **MixedRealityCameraParent** Prefab를 **Prefabs** 폴더에서 **계층**으로 끌어 놓습니다.
4. 계층에서 **방향 광원** 을 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.
5. **Holograms** 폴더에서 다음 자산을 **계층**의 루트에 끌어 놓습니다.
    * **AstroMan**
    * **조명을**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. **재생 모드** 를 시작 하 ▶ astronaut를 봅니다.
7. **재생 모드** ▶ 다시 클릭 하 여 **중지**합니다.
8. **Holograms** 폴더에서 **fitbox** 자산을 찾아 **계층**의 루트로 끌어옵니다.
9. **계층** 패널에서 **fitbox** 를 선택 합니다.
10. **계층** 에서 **AstroMan** 컬렉션을 **검사기** 패널의 fitbox에 있는 **홀로그램 컬렉션** 속성으로 끌어 옵니다.

### <a name="save-the-project"></a>프로젝트를 저장 합니다.

1. 새 장면: 파일을 저장 하 **> 장면을 저장**합니다.
2. **새 폴더** 를 클릭 하 고 폴더 이름을 **장면**으로 합니다.
3. 파일 이름을 "**Modelexplorer**"로 하 고 해당 파일을 **백그라운드** 폴더에 저장 합니다.

### <a name="build-the-project"></a>프로젝트 빌드

1. Unity에서 **파일 > 빌드 설정**을 선택 합니다.
2. 열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.
3. **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.
4. 특별히 HoloLens를 개발 하는 경우 **대상 장치** 를 **hololens**로 설정 합니다. 그렇지 않으면 **모든 장치**에 그대로 둡니다.
5. **빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).
6. **빌드**를 클릭합니다.
7. "App" 이라는 **새 폴더** 를 만듭니다.
8. 단일 **앱** 폴더를 클릭 합니다.
9. **폴더 선택**을 누릅니다.

Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.

1. **앱** 폴더를 엽니다.
2. **모델 탐색기 Visual Studio 솔루션**을 엽니다.

HoloLens에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.
2. 로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터**를 선택 합니다.
3. **HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다. **선택**을 클릭 합니다. 장치 IP 주소를 모르는 경우 **네트워크 & 인터넷 > 고급 옵션 > 설정**을 참조 하세요.
4. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다. 처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.
5. 앱이 배포 되 면 **선택 제스처로** **fitbox** 를 해제 합니다.

모던 헤드셋에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64**로 변경 합니다.
2. 배포 대상이 **로컬 컴퓨터**로 설정 되었는지 확인 합니다.
3. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.
4. 앱이 배포 되 면 동작 컨트롤러에서 트리거를 당겨 **Fitbox** 를 해제 합니다.

## <a name="chapter-2---cursor-and-target-feedback"></a>2 장-커서 및 대상 피드백

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>목표

* 커서 비주얼 디자인 및 동작입니다.
* 응시 기반 커서 피드백입니다.
* 응시 기반 홀로그램 피드백입니다.

다음은 몇 가지 커서 디자인 원칙에 대 한 작업의 기반입니다.

* 커서는 항상 표시 됩니다.
* 커서를 너무 작거나 크게 표시 하지 않습니다.
* 방해 하지 않는지 콘텐츠를 방지 합니다.

### <a name="instructions"></a>지침

1. **HoloToolkit\Input\Prefabs** 폴더에서 **inputmanager** 자산을 찾습니다.
2. **Inputmanager** 를 **계층 구조**에 끌어다 놓습니다.
3. **HoloToolkit\Input\Prefabs** 폴더에서 **커서** 자산을 찾습니다.
4. **커서** 를 **계층**으로 끌어다 놓습니다.
5. **계층**에서 **inputmanager** 개체를 선택 합니다.
6. **계층** 의 **커서** 개체를 **검사기**의 맨 아래에 있는 Inputmanager의 **simplesinglepointerselector**필드로 끕니다.

![간단한 단일 포인터 선택기 설정](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>빌드 및 배포

1. **빌드 설정 > 파일**에서 응용 프로그램을 다시 빌드합니다.
2. **앱 폴더**를 엽니다.
3. **모델 탐색기 Visual Studio 솔루션**을 엽니다.
4. **디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.
5. 커서를 그리는 방법 및 홀로그램을 터치 하는 경우 모양이 어떻게 변경 되는지 관찰 합니다.

### <a name="instructions"></a>지침

1. **계층** 패널에서 **AstroMan**->**GEO_G**->**Back_Center** 개체를 확장 합니다.
2. **Interactible.cs** 를 두 번 클릭 하 여 Visual Studio에서 엽니다.
3. **Interactible.cs**의 **OnFocusEnter ()** 및 **OnFocusExit ()** 콜백에서 줄의 주석 처리를 제거 합니다. 이는 포커스 (응시 또는 컨트롤러 포인팅)가 특정 GameObject의 collider를 입력 하 고 종료 하는 경우 Mixed Reality Toolkit의 InputManager에서 호출 됩니다.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>`EnableKeyword`와 `DisableKeyword`를 사용 합니다. Toolkit의 표준 셰이더를 사용 하 여 자신의 앱에서 이러한 기능을 활용 하려면 [스크립트를 통해 자료에 액세스 하기 위한 Unity 지침](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)을 따라야 합니다. 이 경우 Resources 폴더에 필요한 [강조 표시 된 자료의 세 가지 변형이](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) 이미 포함 되어 있습니다 (이름에 강조 표시 된 세 가지 자료 참조).

### <a name="build-and-deploy"></a>빌드 및 배포

1. 이전과 마찬가지로 프로젝트를 빌드하고 HoloLens에 배포 합니다.
2. 응시가 개체를 목표로 하 고 있지 않을 때 발생 하는 상황을 관찰 합니다.

## <a name="chapter-3---targeting-techniques"></a>3 장-대상 지정 기술

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>목표

* Holograms을 더 쉽게 대상으로 지정 합니다.
* 안정화 자연 헤드 이동.

### <a name="instructions"></a>지침

1. **계층** 패널에서 **inputmanager** 개체를 선택 합니다.
2. **검사기** 패널에서 **응시 안정기** 스크립트를 찾습니다. 원하는 경우 클릭 하 여 Visual Studio에서 엽니다.
    * 이 스크립트는 Raycast 데이터의 샘플을 반복 하 고 사용자가 전체 자릿수를 대상으로 하는 응시를 안정화 하는 데 도움이 됩니다.
3. **검사기**에서 **저장 된 안정성 샘플** 값을 편집할 수 있습니다. 이 값은 안정기가 안정화 값을 계산 하기 위해 반복 하는 샘플 수를 나타냅니다.

## <a name="chapter-4---directional-indicator"></a>4 장 방향 표시기

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>목표

* 커서에 방향 표시기를 추가 하 여 holograms를 찾을 수 있습니다.

### <a name="instructions"></a>지침

**DirectionIndicator.cs** 파일을 사용할 예정입니다.

1. 사용자가 holograms에 gazing 되지 않은 경우 방향 표시기를 표시 합니다.
2. 사용자가 holograms에 gazing 경우 방향 표시기를 숨깁니다.
3. Holograms를 가리키도록 방향 표시기를 업데이트 합니다.

그럼 시작해 보겠습니다.

1. **계층** 패널에서 **AstroMan** 개체를 클릭 하 고 **화살표를 클릭** 하 여 확장 합니다.
2. **계층** 패널의 **AstroMan**아래에서 **DirectionalIndicator** 개체를 선택 합니다.
3. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
4. 메뉴에서 검색 상자 **방향 표시기**를 입력 합니다. 검색 결과를 선택 합니다.
5. **계층** 패널에서 **커서** 개체를 **검사기**의 **cursor** 속성으로 끌어 놓습니다.
6. **프로젝트** 패널의 **Holograms** 폴더에서 **DirectionalIndicator** 자산을 **검사기**의 **방향 표시기** 속성으로 끌어다 놓습니다.
7. 앱을 빌드 및 배포 합니다.
8. 방향 표시기 개체를 사용 하 여 astronaut를 찾는 방법을 시청 하세요.

## <a name="chapter-5---billboarding"></a>5 장-Billboarding

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>목표

* Billboarding를 사용 하 여 holograms 항상 사용자를 중심으로 합니다.

**Billboard.cs** 파일을 사용 하 여 사용자가 항상 연결 되도록 GameObject 지향을 유지 합니다.

1. **계층** 패널에서 **AstroMan** 개체를 선택 합니다.
2. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
3. 메뉴에서 검색 상자 **빌보드**를 입력 합니다. 검색 결과를 선택 합니다.
4. **Inspector** 에서 **피벗 축** 을 **Y**로 설정 합니다.
5. 시도해 보세요. 이전 처럼 앱을 빌드하고 배포 합니다.
6. 관점을 변경 하는 방법에 관계 없이 빌보드 개체가 어떻게 되는지 확인 합니다.
7. 지금은 **AstroMan** 에서 스크립트를 삭제 합니다.

## <a name="chapter-6---tag-along"></a>6 장-태그 동반

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>목표

* 태그를 사용 하 여 holograms에 대 한 의견을 보내 주시기 바랍니다.

이 문제를 해결 하는 동안 다음과 같은 설계 제약 조건을 따릅니다.

* 콘텐츠는 항상 한 눈에 볼 수 있습니다.
* 콘텐츠는 그렇지 않습니다.
* 헤드 잠금 콘텐츠는 불편 합니다.

여기에 사용 된 솔루션은 "태그 동반" 방식을 사용 하는 것입니다.

태그 동반 개체는 사용자의 보기를 완전히 유지 하지 않습니다. 태그는 고무 밴드에 의해 사용자의 헤드에 연결 된 개체로 생각할 수 있습니다. 사용자가 이동 하면 완전히 종료 하지 않고 뷰의 가장자리를 향해 이동 하 여 콘텐츠를 쉽게 한눈에 볼 수 있습니다. 사용자가 태그를 따라 개체를 gazes 하는 경우에는 더 자세히 볼 수 있습니다.

**SimpleTagalong.cs** 파일을 사용할 예정입니다.

1. 태그 동반 개체가 카메라 범위 내에 있는지 여부를 확인 합니다.
2. 뷰 내에 없는 경우 태그를 뷰에 부분적으로 배치 합니다.
3. 그렇지 않으면 사용자의 기본 거리를 따라 태그를 배치 합니다.

이렇게 하려면 먼저 **TagalongAction**를 호출 하도록 **Interactible.cs** 스크립트를 변경 해야 합니다.

1. 코딩 연습 6. a (주석 처리 줄 84 ~ 87)를 완료 하 여 **Interactible.cs** 를 편집 합니다.

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

**Interactible.cs** 와 쌍을 이루는 **InteractibleAction.cs** 스크립트는 holograms을 탭 할 때 사용자 지정 작업을 수행 합니다. 이 경우 태그에 대해 구체적으로 사용 합니다.

* **Scripts** 폴더에서 **TagalongAction.cs** 자산을 클릭 하 여 Visual Studio에서 엽니다.
* 코딩 연습을 완료 하거나 다음과 같이 변경 합니다.
  * **계층**의 맨 위에 있는 검색 표시줄에 **ChestButton_Center** 를 입력 하 고 결과를 선택 합니다.
  * **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
  * 메뉴에서 검색 상자 **Tagalong 작업**을 입력 합니다. 검색 결과를 선택 합니다.
  * **Holograms** 폴더에서 **Tagalong** 자산을 찾습니다.
  * **계층**에서 **ChestButton_Center** 개체를 선택 합니다. **TagAlong** 개체를 **프로젝트** 패널에서 **Inspector** **개체의 TagAlong** 속성에 끌어서 놓습니다.
  * **Inspector** 에서 **Tagalong Action** 개체를 **Interactible** 스크립트의 **Interactible action** 필드로 끕니다.
* **TagalongAction** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.

![Interactible 설정](images/holograms210-interactible.png)

다음을 추가 해야 합니다.

* TagalongAction 스크립트 (InteractibleAction에서 상속 됨)의 PerformAction 함수에 기능을 추가 합니다.
* Billboarding을 gazed 개체에 추가 하 고 피벗 축을 XY로 설정 합니다.
* 그런 다음 개체에 간단한 태그를 추가 합니다.

**TagalongAction.cs**의 솔루션은 다음과 같습니다.

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* 시도해 보세요. 앱을 빌드 및 배포 합니다.
* 콘텐츠가 응시 지점의 중심을 따라가는 지를 확인 합니다.
