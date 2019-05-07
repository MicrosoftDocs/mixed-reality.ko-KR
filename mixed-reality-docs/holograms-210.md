---
title: MR 210-응시 입력
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 게이즈 개념의 자세한 연습을 코딩이 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit mixedrealitytoolkit-unity academy, 자습서, 응시
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993553"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-input-210-gaze"></a>MR 입력 210: 응시

[Gaze](gaze.md) 입력의 첫 번째 형태 이며 사용자의 의도 및 인식 표시 됩니다. MR 입력 210 (즉, 프로젝트 탐색기)는 Windows Mixed Reality 게이즈 관련 개념에 자세히입니다. 추가할 컨텍스트 인식 커서 및 홀로그램, 사용자의 게이즈 알고 앱 활용 하 합니다.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

필요가 친숙 한 고상한 여기 게이즈 개념을 배울 수 있습니다. [MR 기본 사항 101](holograms-101.md), 방금 사용자 게이즈를 준수 하는 단순 커서를 했습니다. 지금 단순 커서 능가 하는 단계로 이동 합니다.

* 만들어진다는 것 커서 및 우리의 홀로그램 게이즈 인식: 둘 다 있는 사용자가 보는-사용자가에 따라 변경 됩니다 *되지* 확인 합니다. 따라서 해당 컨텍스트를 인식 합니다.
* 커서 및 홀로그램 대상으로 지정 되는 것에 더 많은 컨텍스트를 사용자에 게 피드백을 추가 하겠습니다. 이 피드백은 오디오 visual 수 있습니다.
* 보여드리겠습니다 타기 팅 방법 보다 작은 대상에 도달 하는 데 도움이 됩니다.
* 프로그램 홀로그램 방향 표시기를 사용 하 여 사용자의 주의 그리는 방법을 살펴보겠습니다.
* 사용자 환경에서 이동 그녀에 따라 사용자를 사용 하 여 프로그램 홀로그램 수행할 방법 설명 하겠습니다.

>[!IMPORTANT]
>각 아래 단원에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다. 단계별 지침을 정확 하 고 현재는, 스크립트 및 만료 된 해당 동영상의 시각적 개체를 볼 수 있습니다. 비디오는 두세요 포함 상태를 유지 및 개념 설명 하기 때문에 계속 적용 합니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 210: 응시</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.
* 기본적인 C# 기능을 프로그래밍 합니다.
* 완료 해야 [MR 기본 사항 101](holograms-101.md)합니다.
* HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.

### <a name="project-files"></a>프로젝트 파일

* 다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) 프로젝트에서 필요 합니다. Unity 2017.2 이상이 필요합니다.
* 취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.

>[!NOTE]
>을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)합니다.

### <a name="errata-and-notes"></a>오류 및 정보

* Visual Studio에서 "내 코드만" 해야 사용 안 함 (선택 안 함된) 도구-> 옵션-> 디버깅 코드에서 중단점을 적중 하려면.

## <a name="chapter-1---unity-setup"></a>1 장-Unity 설치

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>목표

* HoloLens 개발에 대 한 Unity를 최적화 합니다.
* 자산을 가져오고 장면 설정 합니다.
* 에 HoloLens를 고상한을 봅니다.

### <a name="instructions"></a>지침

1. Unity를 시작 합니다.
2. 선택 **새 프로젝트**합니다.
3. 프로젝트 이름을 **ModelExplorer**합니다.
4. 위치를 입력 합니다 **Gaze** 폴더 되지 않은 보관 된 이전에 있습니다.
5. 프로젝트 설정 되어 있는지 확인 **3D**합니다.
6. 클릭 **프로젝트를 만들**합니다.

### <a name="unity-settings-for-hololens"></a>HoloLens에 대 한 unity 설정

Unity 내보내기 하려는 앱을 만들어야 알 수 있도록 해야는 [몰입 형 뷰](app-views.md) 2D 보기 대신 합니다. 가상 현실 장치로 HoloLens 추가 여는 작업을 수행 합니다.

1. 로 이동 **편집 > 프로젝트 설정 > 플레이어**합니다.
2. 에 **검사기 패널** 플레이어 설정에 대 한 선택 합니다 **Windows 스토어** 아이콘입니다.
3. 확장 된 **xr 하이 설정을** 그룹입니다.
4. 에 **렌더링** 섹션을 **가상 현실 지원** 새 추가 하려면이 확인란을 **가상 현실 Sdk** 목록.
5. 확인 **Windows Mixed Reality** 목록에 나타납니다. 그렇지 않은 경우 선택 합니다 **+** 목록의 맨 아래에 있는 단추를 선택 **Windows Holographic**합니다.

다음으로.net 스크립팅 백 엔드를 설정 해야 합니다.

1. 로 이동 **편집 > 프로젝트 설정 > 플레이어** (될 수 있습니다이 이전 단계에서).
2. 에 **검사기 패널** 플레이어 설정에 대 한 선택 합니다 **Windows 스토어** 아이콘입니다.
3. 에 **기타 설정** 구성 섹션, 했는지 **스크립팅 백 엔드** 로 설정 된 **.NET**

마지막으로, HoloLens에 빠른 성능을 달성 하기 위해 우리의 품질 설정을 업데이트 됩니다.

1. 로 이동 **편집 > 프로젝트 설정 > 품질**합니다.
2. 아래쪽 화살표를 클릭 합니다 **기본** Windows 스토어 아이콘 아래에 있는 행입니다.
3. 선택 **매우 낮은** 에 대 한 **Windows 스토어 앱**합니다.

### <a name="import-project-assets"></a>프로젝트 자산 가져오기

1. 마우스 오른쪽 단추로 클릭 합니다 **자산** 폴더에는 **프로젝트** 패널입니다.
2. 클릭할 **패키지를 가져올 > 사용자 지정 패키지**합니다.
3. 다운로드 한 프로젝트 파일을 이동 하 고 클릭 **ModelExplorer.unitypackage**합니다.
4. **열기**를 클릭합니다.
5. 패키지를 로드 한 후 클릭 합니다 **가져오기** 단추입니다.

### <a name="setup-the-scene"></a>장면 설치

1. 계층 구조에서 삭제 합니다 **주 카메라**합니다.
2. 에 **HoloToolkit** 폴더를 열고 합니다 **입력** 폴더를 엽니다를 **Prefabs** 폴더.
3. 끌어서 놓기 합니다 **MixedRealityCameraParent** 에서 prefab 합니다 **Prefabs** 폴더를 **계층**합니다.
4. 마우스 오른쪽 단추로 클릭 합니다 **Directional Light** 계층 및 선택 **삭제**합니다.
5. 에 **홀로그램** 폴더를 끌어서의 루트에 다음 자산을 삭제 합니다 **계층**:
    * **AstroMan**
    * **광원**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. 시작 **재생 모드** ▶ 고상한을 볼 수 있습니다.
7. 클릭 **재생 모드** 를 다시 ▶ **중지**합니다.
8. 에 **홀로그램** 폴더를 찾을 **Fitbox** 자산의 루트에 놓습니다 합니다 **계층**.
9. 선택 된 **Fitbox** 에 **계층** 패널.
10. 끌어서를 **AstroMan** 컬렉션에서는 **계층** 에 **홀로그램 컬렉션** 에서 Fitbox 속성을 **검사기** 패널.

### <a name="save-the-project"></a>프로젝트를 저장 합니다.

1. 새 장면을 저장 합니다. **파일 >으로 장면 저장**합니다.
2. 클릭 **새 폴더** 는 폴더의 이름을 **장면**합니다.
3. 파일 이름을 "**ModelExplorer**"에 저장 된 **장면** 폴더입니다.

### <a name="build-the-project"></a>프로젝트 빌드

1. Unity에서 선택 **파일 > 빌드 설정**합니다.
2. 클릭 **열기 장면 추가** 장면에 추가 합니다.
3. 선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 클릭 **플랫폼 전환**합니다.
4. HoloLens에 대 한 구체적으로 개발 하는 경우 설정 **대상 장치** 하 **HoloLens**합니다. 그렇지 않으면 켜져 **모든 장치**합니다.
5. 확인 **빌드 형식** 로 설정 된 **D3D** 하 고 **SDK** 로 설정 되어 **가장 최근에 설치 된** (16299 또는 최신 SDK는 이어야 함).
6. **빌드**를 클릭합니다.
7. 만들기는 **새 폴더** 이름을 "App"입니다.
8. 한 번 클릭 합니다 **앱** 폴더입니다.
9. 키를 눌러 **폴더 선택**합니다.

Unity 완료 되 면 파일 탐색기 창이 나타납니다.

1. 엽니다는 **앱** 폴더입니다.
2. 엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.

HoloLens 배포 하는 경우:

1. 에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x86**합니다.
2. 드롭다운 로컬 컴퓨터 단추 옆의 화살표를 클릭 하 고 선택 **원격 컴퓨터**합니다.
3. 입력 **HoloLens 장치 IP 주소** 인증 모드를 설정 하 고 **유니버설 (암호화 되지 않은 프로토콜)** 합니다. 클릭 **선택**합니다. 장치 IP 주소를 모르는 경우 찾는 위치 **설정 > 네트워크 및 인터넷 > 고급 옵션**합니다.
4. 맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다. 처음으로 장치에 배포할 경우 해야 [Visual Studio를 사용 하 여 쌍](using-visual-studio.md#pairing-your-device-hololens)합니다.
5. 앱에 배포 하는 경우 해제 합니다 **Fitbox** 사용 하 여를 **제스처 선택**.

경우는 몰입 형 헤드셋에 배포 합니다.

1. 에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x64**합니다.
2. 배포 대상 설정 되어 있는지 확인 **로컬 컴퓨터**합니다.
3. 맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.
4. 앱에 배포 하는 경우 해제 합니다 **Fitbox** 동작 컨트롤러에서 트리거를 풀링 하 여 합니다.

## <a name="chapter-2---cursor-and-target-feedback"></a>2 장-커서 및 대상 피드백

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>목표

* 커서 시각적 디자인 및 동작 합니다.
* 피드백 커서 게이즈 기반입니다.
* 홀로그램 게이즈 기반 피드백입니다.

기준 작업 몇 가지 커서 디자인 원칙 즉 하겠습니다.

* 커서가 항상 존재 합니다.
* 너무 작은 또는 큰 커서를 허용 하지 마십시오.
* 콘텐츠를 방해 하지 않습니다.

### <a name="instructions"></a>지침

1. 에 **HoloToolkit\Input\Prefabs** 폴더를 찾기는 **InputManager** 자산입니다.
2. 끌어서 놓기 합니다 **InputManager** 에 **계층**합니다.
3. 에 **HoloToolkit\Input\Prefabs** 폴더를 찾기는 **커서** 자산입니다.
4. 끌어서 놓기 합니다 **커서** 에 **계층**합니다.
5. 선택 된 **InputManager** 개체를 **계층**합니다.
6. 끌어서 합니다 **커서** 에서 개체를 **계층** InputManager의에 **SimpleSinglePointerSelector**의 **커서** 필드에 아래쪽의 **검사기**합니다.

![간단한 단일 포인터 선택기 설정](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>빌드 및 배포

1. 앱을 다시 빌드해야 **파일 > 빌드 설정**합니다.
2. 엽니다는 **앱 폴더**합니다.
3. 엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.
4. 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.
5. 커서를 그리는 방법 및를 홀로그램 접촉 되어 해당 하는 경우 모양을 변경 하는 방법을 확인 합니다.

### <a name="instructions"></a>지침

1. 에 **계층** 패널을 확장 합니다 **AstroMan**->**GEO_G**->**Back_Center** 개체입니다.
2. 두 번 클릭 **Interactible.cs** Visual Studio에서 엽니다.
3. 줄의 주석도 제거 합니다 **IFocusable.OnFocusEnter()** 하 고 **IFocusable.OnFocusExit()** 콜백을 **Interactible.cs**합니다. 이러한 값은 포커스 (하거나 게이즈 컨트롤러 가리켜) 하 고 특정 GameObject collider를 끝낼 때 혼합 현실 도구 키트의 InputManager에 의해 호출 됩니다.

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
>사용 하 여 `EnableKeyword` 고 `DisableKeyword` 위에 있습니다. 확인 하기 위해 도구 키트의 표준 셰이더를 사용 하 여 사용자 고유의 앱에서 이러한 사용, 수행 해야 합니다 [스크립트를 통해 자료에 액세스 하기 위해 Unity 지침](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)합니다. 이미 포함 되어이 예에서 합니다 [강조 표시 된 자료의 세 가지 변형 된](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) 리소스 폴더 (이름에 강조 표시를 사용 하 여 세 가지 자료 검색)에 필요 합니다.

### <a name="build-and-deploy"></a>빌드 및 배포

1. 이전과 마찬가지로 프로젝트를 빌드하고 HoloLens에 배포 합니다.
2. 개체는 게이즈는 대상으로 하는 경우 어떻게 되는지 관찰 하 고 있지 않은 경우.

## <a name="chapter-3---targeting-techniques"></a>3 장-기술을 대상으로

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>목표

* 대상 홀로그램 쉽게 확인 합니다.
* 자연 스러운 헤드 이동 안정화 합니다.

### <a name="instructions"></a>지침

1. 에 **계층** 패널을 선택 합니다 **InputManager** 개체.
2. 에 **검사기** 패널에서 찾을 합니다 **Gaze 안정기** 스크립트입니다. 확인 하려는 경우 클릭 하 여 Visual Studio에서 엽니다.
    * 이 스크립트는 Raycast 데이터 샘플을 반복 하 고 전체 자릿수를 대상으로 하는 사용자의 게이즈를 안정화 하는 데 도움이 됩니다.
3. 에 **검사기**, 편집할 수 있습니다 합니다 **안정성 샘플 저장** 값입니다. 이 값은 안정기에 반복이 안정화 되 값을 계산 하는 샘플 수를 나타냅니다.

## <a name="chapter-4---directional-indicator"></a>4 장-방향 표시기

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>목표

* 홀로그램을 찾기 위해 커서에서 방향 표시기를 추가 합니다.

### <a name="instructions"></a>지침

사용 하려고 합니다 **DirectionIndicator.cs** 될 파일:

1. 사용자가를 홀로그램에서 gazing 되지 경우 방향 표시기를 표시 합니다.
2. 사용자가를 홀로그램에서 gazing 경우 방향 표시기를 숨깁니다.
3. 방향 표시기를 홀로그램을 가리키도록 업데이트 합니다.

그럼 시작해 보겠습니다.

1. 클릭 합니다 **AstroMan** 개체를 **계층** 패널 및 **화살표를 클릭** 하 여 확장 합니다.
2. 에 **계층** 패널을 선택 합니다 **DirectionalIndicator** 개체 아래 **AstroMan**.
3. 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
4. 메뉴에서 검색 상자에 입력 **방향 표시기**합니다. 검색 결과 선택 합니다.
5. 에 **계층** 패널을 끌어서 놓아를 **커서** 개체를 **커서** 속성에는 **검사기**.
6. 에 **프로젝트** 패널의 **홀로그램** 폴더, 끌어서 놓기를 **DirectionalIndicator** 자산에는 **방향 표시기**의 속성을 **검사기**합니다.
7. 앱 빌드 및 배포 합니다.
8. 방향 표시기 개체는 고상한을 찾을 수 있습니다 어떻게 시청 하세요.

## <a name="chapter-5---billboarding"></a>5 장-빌보드

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>목표

* 빌보드를 사용 하 여 홀로그램 항상 사용자 쪽에 직면 합니다.

사용 합니다 **Billboard.cs** 를 항상 사용자 향하도록 같은 지향 GameObject를 유지 하는 파일입니다.

1. 에 **계층** 패널을 선택 합니다 **AstroMan** 개체.
2. 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
3. 메뉴에서 검색 상자에 입력 **빌보드**합니다. 검색 결과 선택 합니다.
4. 에 **검사기** 설정 합니다 **피벗 축** 에 **Y**합니다.
5. 시도해 보세요. 빌드 및 배포 하기 전에 해당 응용 프로그램.
6. 어떻게 빌보드 개체 얼굴 관점을 변경 하는 방법에 관계 없이 참조 하세요.
7. 스크립트를 삭제 합니다 **AstroMan** 지금은 합니다.

## <a name="chapter-6---tag-along"></a>6 장-Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>목표

* Tag-Along 전시실 팔 로우 하 여 홀로그램을 사용 하 여 합니다.

이 문제에 작업을에서는 다음 디자인 제약 조건으로 안내 됩니다.

* 콘텐츠 항상 있어야 한눈에 제거 합니다.
* 콘텐츠 방식에서 아니어야 합니다.
* 콘텐츠 헤드 잠금 편리 하 게 아닙니다.

여기에 솔루션 "tag-along" 접근 방식을 사용 하는 것입니다.

Tag-along 개체를 완전히 사용자 보기를 유지합니다. 생각할 수 있습니다는 개체와 tag-along 고무 밴드에서 사용자의 머리글에 연결 합니다. 사용자가이 완전히 종료 하지 않고 보기의 모서리 쪽으로 이동 하 여 콘텐츠를 쉽게 보기 내에서 유지 됩니다. 사용자 gazes 향해 tag-along 개체, 경우 있어 자세히 보기로 합니다.

사용 하려고 합니다 **SimpleTagalong.cs** 될 파일:

1. 카메라 범위 내에서 Tag-Along 개체 인지 확인 합니다.
2. 그렇지 않은 경우 하면 보기 프러스텀 내 하면 보기 프러스텀 부분적으로 내에 Tag-Along를 배치 합니다.
3. 이 고, 그렇지 사용자 로부터 Tag-Along 기본 거리를 배치 합니다.

이렇게 하려면 먼저 변경 해야 합니다 **Interactible.cs** 스크립트를 호출 하는 **TagalongAction**합니다.

1. 편집할 **Interactible.cs** 코딩을 완료 하 여 6.a (주석 처리 제거 줄 84를 87)를 실행 합니다.

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

합니다 **InteractibleAction.cs** 스크립트를 사용 하 여 쌍을 이루는 **Interactible.cs** 홀로그램에서 탭 사용자 지정 작업을 수행 합니다. 이 경우 tag-along 맞게 하나를 사용 하겠습니다.

* 에 **스크립트** 폴더를 클릭 **TagalongAction.cs** 자산을 Visual Studio에서 엽니다.
* 코딩 연습을 완료 하거나이 변경:
  * 맨 위에 있는 합니다 **계층**, 검색 표시줄 유형에 **ChestButton_Center** 결과 선택 하 고 합니다.
  * 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
  * 메뉴에서 검색 상자에 입력 **태그가 있는 작업**합니다. 검색 결과 선택 합니다.
  * **홀로그램** 폴더 찾기 합니다 **태그가 있는** 자산입니다.
  * 선택 된 **ChestButton_Center** 개체를 **계층**합니다. 끌어서 놓기는 **태그가 있는** 에서 개체를 **프로젝트** 패널에 **검사기** 에 **개체에 태그가 있는** 속성입니다.
  * 끌어서 합니다 **태그가 있는 작업** 에서 개체를 **검사기** 에 **Interactible 작업** 필드에 **Interactible** 스크립트입니다.
* 두 번 클릭 합니다 **TagalongAction** 스크립트 Visual Studio에서 엽니다.

![Interactible 설정](images/holograms210-interactible.png)

다음을 추가 해야 합니다.

* PerformAction 함수 TagalongAction 스크립트 (InteractibleAction에서 상속)에 기능을 추가 합니다.
* 빌보드 gazed 시 개체에 추가한 피벗 축의 XY로 설정 합니다.
* 개체에 간단한 Tag-Along를 추가 합니다.

솔루션을 다음과 같습니다 **TagalongAction.cs**:

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

* 시도해 보세요. 앱 빌드 및 배포 합니다.
* 콘텐츠 게이즈 지점의 중앙을 따라가는 방법을 시청 하지만 지속적으로 하지 않고 차단 합니다.
