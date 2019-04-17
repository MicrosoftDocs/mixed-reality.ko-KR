---
title: MR 입력 211-제스처
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 제스처 개념의 세부 정보를 알아보려면이 코딩 연습을 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, academy, 자습서, 제스처
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603385"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-input-211-gesture"></a>MR 입력 211: 제스처

[제스처](gestures.md) 사용자 의도 작업으로 변환 합니다. 제스처를 사용 하 여 사용자 홀로그램 상호 작용할 수 있습니다. 이 과정에서는 사용자의 손에 추적, 사용자 입력에 응답 하는 방법을 알아보겠습니다 및 사용자에 게 피드백 상태 및 위치 가까이 기반 합니다.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

[MR 기본 사항 101](holograms-101.md), 우리의 홀로그램와 상호 작용 하는 간단한 어 탭 제스처를 사용 했습니다. 이제 어 탭 제스처를 넘어 이동 하 고 새로운 개념을 탐색 드리겠습니다.

* 사용자의 직접 추적 중인 경우를 감지 및 사용자에 게 피드백을 제공 합니다.
* 우리의 홀로그램을 회전 하려면 탐색 제스처를 사용 합니다.
* 사용자의 직접 보기에서 이동 하려고 할 때 피드백을 제공 합니다.
* 조작 이벤트를 사용 하 여 홀로그램 알아내기란을 사용 하 여 이동할 수 있도록 합니다.

이 과정에서 Unity 프로젝트를 다시 방문할 예정 **모델 탐색기**, 구축한입니다 [MR 입력 210](holograms-210.md)합니다. 우리의 고상한 friend가 이러한 새 제스처 개념의 탐색 지원 하도록 합니다.

>[!IMPORTANT]
>각 아래 단원에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다. 단계별 지침을 정확 하 고 현재는, 스크립트 및 만료 된 해당 동영상의 시각적 개체를 볼 수 있습니다. 비디오는 두세요 포함 상태를 유지 및 개념 설명 하기 때문에 계속 적용 합니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 211: 제스처</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.
* 기본적인 C# 기능을 프로그래밍 합니다.
* 완료 해야 [MR 기본 사항 101](holograms-101.md)합니다.
* 완료 해야 [MR 입력 210](holograms-210.md)합니다.
* HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.

### <a name="project-files"></a>프로젝트 파일

* 다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) 프로젝트에서 필요 합니다. Unity 2017.2 이상이 필요합니다.
* 취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.

>[!NOTE]
>을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)합니다.

### <a name="errata-and-notes"></a>오류 및 정보

* 사용 하지 않도록 설정할 필요 "내 코드만 사용" (*unchecked*)-> 도구 아래에서 Visual Studio에서 코드에서 중단점을 적중 하려면-> 디버깅 옵션입니다.

## <a name="chapter-0---unity-setup"></a>장 0-Unity 설치

### <a name="instructions"></a>지침

1. Unity를 시작 합니다.
2. 선택 **열려**합니다.
3. 로 이동 합니다 **제스처** 폴더 되지 않은 보관 된 이전에 있습니다.
4. 찾기 및 선택 합니다 **터**/**모델 탐색기** 폴더입니다.
5. 클릭 합니다 **폴더 선택** 단추입니다.
6. 에 **프로젝트** 패널을 확장 합니다 **장면** 폴더.
7. 두 번 클릭 **ModelExplorer** 장면 Unity에 로드 합니다.

### <a name="building"></a>빌드

1. Unity에서 선택 **파일 > 빌드 설정**합니다.
2. 하는 경우 **장면/ModelExplorer** 에 나열 되지 **Scenes In Build**, 클릭 **열기 장면 추가** 장면에 추가할 합니다.
3. HoloLens에 대 한 구체적으로 개발 하는 경우 설정 **대상 장치** 하 **HoloLens**합니다. 그렇지 않으면 켜져 **모든 장치**합니다.
4. 확인 **빌드 형식** 로 설정 된 **D3D** 하 고 **SDK** 로 설정 되어 **가장 최근에 설치 된** (16299 또는 최신 SDK는 이어야 함).
5. **빌드**를 클릭합니다.
6. 만들기는 **새 폴더** 이름을 "App"입니다.
7. 한 번 클릭 합니다 **앱** 폴더입니다.
8. 키를 눌러 **폴더 선택** Unity for Visual Studio 프로젝트를 빌드하기 시작 됩니다.

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

>[!NOTE]
>Visual Studio 오류 패널에서 빨간색 일부 오류를 확인할 수 있습니다. 무시 해도 됩니다. 스위치를 실제 보려면 출력 패널에 빌드 진행률입니다. 출력 패널에는 오류 (가장 일반적으로 스크립트를이 잘못 되어 발생)을 수정 해야 해야 합니다.

## <a name="chapter-1---hand-detected-feedback"></a>1 장-직접 사용자 의견 검색

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>목표

* 추적 이벤트를 전달 하는 데 구독 합니다.
* 손 모양 추적 되는 경우 사용자가 표시할 커서 피드백을 사용 합니다.

### <a name="instructions"></a>지침

* 에 **계층** 패널을 확장 합니다 **InputManager** 개체입니다.
* 찾아 선택 합니다 **GesturesInput** 개체입니다.

합니다 **InteractionInputSource.cs** 스크립트는 두이 단계를 수행 합니다.

1. InteractionSourceDetected 및 InteractionSourceLost 이벤트를 구독합니다.
2. HandDetected 상태를 설정합니다.
3. InteractionSourceDetected 및 InteractionSourceLost 이벤트에서이 구독을 취소 합니다.

에서는 커서에서 업그레이드에서는 어 [MR 입력 210](holograms-210.md) 사용자 작업에 따라 피드백을 보여 주는 하나로 합니다.

1. 에 **계층 구조** 패널에서 합니다 **커서** 개체를 삭제 합니다.
2. 에 **프로젝트** 패널에서 검색할 **CursorWithFeedback** 으로 끌어 놓습니다 합니다 **계층** 패널입니다.
3. 클릭할 **InputManager** 에 **계층** 패널 다음 끌어를 **CursorWithFeedback** 에서 개체를 **계층** 에 InputManager의 **SimpleSinglePointerSelector**의 **커서** 맨 아래에 필드를 **검사기**합니다.
4. 클릭 합니다 **CursorWithFeedback** 에 **계층**합니다.
5. 에 **검사기** 패널에서 확장 **커서 상태 데이터** 에 **개체 커서** 스크립트입니다.

합니다 **커서 상태 데이터** 이 처럼 작동 합니다.

* 모든 **관찰** 상태 없습니다 직접 검색 하 고 사용자는 단순히 확인 하는 것을 의미 합니다.
* 모든 **상호 작용** 상태는 직접 또는 컨트롤러 검색 되는 것을 의미 합니다.
* 모든 **호버** 상태를 홀로그램에서 사용자가 보는 것을 의미 합니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity를 사용 하 여 **파일 > 빌드 설정** 응용 프로그램을 다시 작성 해야 합니다.
* 엽니다는 **앱** 폴더입니다.
* 열려 있지 않으면 엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.
  * (이미 빌드된/을 배포한 경우 Visual Studio에서이 프로젝트를 설정 하는 동안 다음 수 VS의 해당 인스턴스를 열고 ' 모두 다시 로드 ' 메시지가 표시 되 면 클릭).
* Visual Studio에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.
* 응용 프로그램을 HoloLens를 배포한 후에 어 탭 제스처를 사용 하 여 fitbox를 해제 합니다.
* 보기로 직접 이동 하 고 직접 추적을 시작 하려면 하늘을 집게 손가락을 가리킵니다.
* 왼쪽으로 직접 이동, 오른쪽, 위쪽 및 아래쪽 합니다.
* 직접 검색 되어 다음 보기에서 손실 된 경우 커서가 어떻게 변경 하는지 시청 하세요.
* 몰입 형 헤드셋을 사용 하는 경우에 연결 및 컨트롤러를 분리 하는 것이 해야 합니다. 연결 된 컨트롤러를 "제공 가능한"은 항상이 피드백 몰입 형 장치에서 덜 관심 있는 수 있습니다.

## <a name="chapter-2---navigation"></a>2 장-탐색

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>목표

* 고상한을 회전 하려면 탐색 제스처 이벤트를 사용 합니다.

### <a name="instructions"></a>지침

앱에서 탐색 제스처를 사용 하려면 하겠습니다 편집 **GestureAction.cs** 탐색 제스처 발생 하는 경우 개체를 회전 합니다. 또한 피드백 탐색 사용할 때 표시할 커서를 추가 하겠습니다.

1. 에 **계층 구조** 패널에서 확장 **CursorWithFeedback**합니다.
2. 에 **홀로그램** 폴더를 찾기는 **ScrollFeedback** 자산입니다.
3. 끌어서 놓기는 **ScrollFeedback** 으로 prefab 합니다 **CursorWithFeedback** GameObject를 **계층**.
4. 클릭할 **CursorWithFeedback**합니다.
5. 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
6. 메뉴에서 검색 상자에 입력 **CursorFeedback**합니다. 검색 결과 선택 합니다.
7. 끌어서 놓기 합니다 **ScrollFeedback** 에서 개체를 **계층** 에 **게임 개체를 검색 하는 스크롤** 속성에는 **커서 피드백**구성 요소를 **검사기**합니다.
8. 에 **계층** 패널을 선택 합니다 **AstroMan** 개체.
9. 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
10. 메뉴에서 검색 상자에 입력 **제스처 작업**합니다. 검색 결과 선택 합니다.

다음으로 열기 **GestureAction.cs** Visual Studio에서. 코딩 2.c 실행, 다음을 수행 하는 스크립트를 편집 합니다.

1. **회전 된 AstroMan** 탐색 제스처가 수행 될 때마다 개체입니다.
2. 계산 합니다 **rotationFactor** 개체에 적용 되는 회전의 양을 제어할 수 있습니다.
3. **개체를 회전** y 축 왼쪽 또는 오른쪽 속속들이 이동할 때.

전체 코딩 연습 2.c 스크립트 또는 코드 완료 된 솔루션 아래 코드로 바꿉니다.

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

다른 탐색 이벤트를 몇 가지 정보를 사용 하 여 이미 입력 된 것을 알 수 있습니다. 도구 키트의 끌어다 GameObject를 푸시 했습니다 InputSystem의 모달 스택, 회전 시작 되 면는 고상한에 초점을 유지 하기 위해 사용자 포함 되지 않도록 합니다. 마찬가지로, 제스처 완료 되 면 스택에서 GameObject를 팝 했습니다.

### <a name="build-and-deploy"></a>빌드 및 배포

1. Unity에서 응용 프로그램을 다시 빌드 및는 HoloLens에서 실행 하려면 Visual Studio에서 배포 합니다.
2. 커서의 어느 쪽에 두 개의 화살표가 나타납니다 고상한을 응시 합니다. 이 새로운 시각적 개체는 고상한 회전할 수 있는지를 나타냅니다.
3. 준비 위치 (집게 손가락 하늘 향함)에 직접 배치는 HoloLens 직접 추적 시작 됩니다.
4. 고상한을 회전 하려면 집게 손가락의 축소 위치로 줄이고 왼쪽 또는 오른쪽 NavigationX 제스처를 트리거할으로 직접 이동 합니다.

## <a name="chapter-3---hand-guidance"></a>3 장-직접 지침

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>목표

* 사용 하 여 **지침 점수를 전달** 직접 추적 손실 됩니다 예측할 수 있도록 합니다.
* 제공 **커서에 대 한 피드백** 사용자의 직접 보기의 카메라의 가장자리를가 하는 경우를 표시 합니다.

### <a name="instructions"></a>지침

1. 에 **계층** 패널을 선택 합니다 **CursorWithFeedback** 개체.
2. 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
3. 메뉴에서 검색 상자에 입력 **손 지침**합니다. 검색 결과 선택 합니다.
4. 에 **프로젝트** 패널 **홀로그램** 폴더를 찾기는 **HandGuidanceFeedback** 자산입니다.
5. 끌어서 놓기는 **HandGuidanceFeedback** 자산에는 **손 지침 표시기** 속성에는 **검사기** 패널입니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 응용 프로그램을 다시 빌드 및 HoloLens에 앱을 Visual Studio에서 배포 합니다.
* 직접 뷰로 가져올 하 고 추적 하려면 집게 손가락을 발생 시킵니다.
* 탐색 제스처와 고상한 회전을 시작 (집게 손가락 및 함께 엄지 단추).
* 맨 왼쪽, 오른쪽, 위쪽 및 아래쪽 직접을 이동 합니다.
* 손 제스처 프레임의 가장자리 만료일이 화살표 옆에 표시 되어야 하는 대로 해당 직접 추적 경고 메시지를 커서 손실 됩니다. 화살표는 직접 추적 손실 되지 않도록 하기 위해 이동할 방향을 나타냅니다.

## <a name="chapter-4---manipulation"></a>4 장-조작

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>목표

* 손으로 고상한 이동할 조작 이벤트를 사용 합니다.
* 사용자 조작에 사용할 수 있습니다 시기를 알 수 있도록 커서에서 피드백을 제공 합니다.

### <a name="instructions"></a>지침

GestureManager.cs 및 AstronautManager.cs 수 있도록 다음 작업을 수행 합니다.

1. 음성 키워드를 사용 하 여 "**이동 고상한**" 사용할 수 있도록 **조작** 제스처 및 "**회전 고상한**" 비활성화 합니다.
2. 응답으로 전환 합니다 **조작 제스처 인식기**합니다.

그럼 시작해 보겠습니다.

1. 에 **계층** 패널에서 새로운 빈 GameObject를 만듭니다. Name it "**AstronautManager**".
2. 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
3. 메뉴에서 검색 상자에 입력 **고상한 Manager**합니다. 검색 결과 선택 합니다.
4. 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
5. 메뉴에서 검색 상자에 입력 **음성 입력 원본**합니다. 검색 결과 선택 합니다.

이제는 고상한의 상호 작용 상태를 제어 하는 데 필요한 음성 명령을 추가 합니다.

1. 확장 된 **키워드** 섹션을 **검사기**합니다.
2. 클릭 합니다 **+** 새로운 키워드를 추가 하려면 오른쪽에 있습니다.
3. As 키워드를 입력 **고상한 이동**합니다. 원하는 경우 키 바로 가기를 추가 해도 됩니다.
4. 클릭 합니다 **+** 새로운 키워드를 추가 하려면 오른쪽에 있습니다.
5. As 키워드를 입력 **고상한 회전**합니다. 원하는 경우 키 바로 가기를 추가 해도 됩니다.
6. 해당 처리기 코드를 찾을 수 있습니다 **GestureAction.cs**를 **ISpeechHandler.OnSpeechKeywordRecognized** 처리기입니다.

![4 장 음성 입력 원본을 설정 하는 방법](images/holograms211-speech.png)

다음으로 조작 피드백 커서에서 설정 됩니다.

1. 에 **프로젝트** 패널 **홀로그램** 폴더를 찾기는 **PathingFeedback** 자산입니다.
2. 끌어서 놓기는 **PathingFeedback** 으로 prefab 합니다 **CursorWithFeedback** 개체를 **계층**합니다.
3. 에 **계층 구조** 패널에서 클릭 **CursorWithFeedback**합니다.
4. 끌어서 놓기 합니다 **PathingFeedback** 에서 개체를 **계층** 에 **게임 개체를 검색 하는 경로 지정** 속성에는 **커서 피드백**구성 요소를 **검사기**합니다.

이제 코드를 추가 해야 **GestureAction.cs** 다음을 사용 하도록 설정 하려면:

1. 코드를 추가 합니다 **IManipulationHandler.OnManipulationUpdated** 고상한을 이동 하는 함수를 때를 **조작** 제스처가 감지 되 합니다.
2. 계산 된 **이동 벡터** 위치는 고상한 설정할지 결정할 기반 가까이 위치 합니다.
3. **이동** 의 새 위치로 고상한 합니다.

4.a 연습 완료 코딩 **GestureAction.cs**, 하거나 아래 완료 된 솔루션을 사용 하 여:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서를 다시 빌드하십시오 빌드 및 HoloLens에 앱을 실행 하려면 Visual Studio에서 배포 합니다.
* HoloLens 앞에 손을 이동 하 고 추적할 수 있도록 집게 손가락을 발생 시킵니다.
* 고상한 위에 커서를 집중 합니다.
* 조작 제스처를 사용 하 여 고상한 이동할 ' 고상한 이동 '을 가정해 보겠습니다.
* 4 방향 화살표는 프로그램이 지금 응답할 조작 이벤트를 나타내기 위해 커서 주위에 표시 됩니다.
* 엄지 손가락 아래로 집게 손가락을 절감 하 고 함께 키거나 유지 하세요.
* 직접 주위를 이동 하면는 고상한도 이동 됩니다 (이것이 조작) 합니다.
* 집게 손가락을 고상한 조작 중지를 발생 시킵니다.
* 참고: 고상한 이동 ' 직접 이동 하기 전에 라고 하면, 한 탐색 제스처를 대신 사용 됩니다.
* 회전식 상태로 돌아갈 ' 고상한 회전 ' 가정해 보겠습니다.

## <a name="chapter-5---model-expansion"></a>5 장-모델 확장

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>목표

* 여러 고상한 모델을 확장 하 고, 더 작은 부분을 사용자가 상호 작용할 수 있습니다.
* 개별적으로 탐색 및 조작 제스처를 사용 하 여 각 부분을 이동 합니다.

### <a name="instructions"></a>지침

이 섹션에서는에서는 다음 작업을 수행 합니다.

1. 새 키워드를 추가 합니다. "**확장 모델**" 고상한 모델을 확장 합니다.
2. 새 키워드를 추가 합니다. "**재설정 모델**" 원래 형태로 모델을 반환 하 합니다.

이전 장에서 음성 입력 원본에 자세한 두 키워드를 추가 하 여이 작업을 수행 합니다. 또한 인식 이벤트를 처리 하는 또 다른 방법은 보여 드립니다.

1. 다시 클릭할 **AstronautManager** 에 **검사기** 확장를 **키워드** 섹션를 **검사기**.
2. 클릭 합니다 **+** 새로운 키워드를 추가 하려면 오른쪽에 있습니다.
3. As 키워드를 입력 **모델을 확장**합니다. 원하는 경우 키 바로 가기를 추가 해도 됩니다.
4. 클릭 합니다 **+** 새로운 키워드를 추가 하려면 오른쪽에 있습니다.
5. As 키워드를 입력 **모델을 다시 설정**합니다. 원하는 경우 키 바로 가기를 추가 해도 됩니다.
6. 에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.
7. 메뉴에서 검색 상자에 입력 **음성 입력 처리기**합니다. 검색 결과 선택 합니다.
8. 확인할 **전역 수신기는**초점을 맞춰 보겠습니다에서는 GameObject 관계 없이 작동 하도록 이러한 명령을 것 이므로, 합니다.
9. 클릭 합니다 **+** 단추를 선택 **확장 모델** 키워드 드롭다운 목록에서.
10. 클릭 합니다 **+** 응답으로 끌어서를 **AstronautManager** 에서 **계층** 에 **없음 (개체)** 필드입니다.
11. 이제 클릭 합니다 **No 함수** 드롭다운 **AstronautManager**, 다음 **ExpandModelCommand**합니다.
12. 음성 입력 처리기를 클릭 **+** 단추를 선택 **재설정 모델** 키워드 드롭다운 목록에서.
13. 클릭 합니다 **+** 응답으로 끌어서를 **AstronautManager** 에서 **계층** 에 **없음 (개체)** 필드입니다.
14. 이제 클릭 합니다 **No 함수** 드롭다운 **AstronautManager**, 다음 **ResetModelCommand**합니다.

![5 장에 대 한 음성 입력 소스를 설정 하 고 처리기 방법](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>빌드 및 배포

* 시도해 보세요. 빌드하고 HoloLens에 앱을 배포 합니다.
* 예를 들어 **확장 모델** 확장된 고상한 모델을 봅니다.
* 사용 하 여 **탐색** 개별 고상한 세트를 회전 합니다.
* 예를 들어 **이동 고상한** 사용 하 여 **조작** 고상한 세트의 개별 항목을 이동 합니다.
* 예를 들어 **회전 고상한** 조각을 다시 회전 합니다.
* 예를 들어 **재설정 모델** 는 고상한 원래 형태로 돌아갑니다.

## <a name="the-end"></a>끝

축하합니다. 이제 완료 **MR 입력 211: 제스처**합니다.

* 검색 및 추적, 탐색 및 조작 이벤트를 전달 하는 데 응답 하는 방법을 알고 있습니다.
* 탐색 및 조작 제스처 간의 차이점을 이해 합니다.
* 손 모양 손실 되려고 할 때, 손 모양 검색 되 고 개체가 다른 상호 작용 (탐색 및 조작)를 지원 하는 경우에 대 한 시각적 피드백을 제공 하는 커서를 변경 하는 방법을 알고 있습니다.
