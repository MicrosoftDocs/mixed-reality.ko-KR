---
title: MR 입력 211-제스처
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 제스처 개념에 대 한 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 제스처
ms.openlocfilehash: 694f51f1b56588e100d6d2676a8194d7e9936133
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559881"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-input-211-gesture"></a>MR 입력 211: 제스처

[제스처](gestures.md) 사용자 의도를 작업으로 설정 합니다. 제스처를 사용 하면 사용자가 holograms와 상호 작용할 수 있습니다. 이 과정에서는 사용자의 손을 추적 하 고, 사용자 입력에 응답 하 고, 직접 상태 및 위치에 따라 사용자에 게 피드백을 제공 하는 방법을 알아봅니다.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

[MR 기본 101](holograms-101.md)에서는 간단한 공기 탭 제스처를 사용 하 여 holograms와 상호 작용 했습니다. 이제는 공중 탭 제스처를 벗어나 이동 하 여 다음에 대 한 새로운 개념을 살펴보겠습니다.

* 사용자의 손을 추적 하 고 사용자에 게 피드백을 제공 하는 경우를 감지 합니다.
* 탐색 제스처를 사용 하 여 holograms를 회전 합니다.
* 사용자의 손을 볼 때 사용자 의견을 제공 하세요.
* 조작 이벤트를 사용 하 여 사용자가 손을 holograms 이동할 수 있도록 합니다.

이 과정에서는 [MR 입력 210](holograms-210.md)에서 빌드된 Unity 프로젝트 **모델 탐색기**를 다시 방문 합니다. Astronaut 친구는 이러한 새 제스처 개념을 탐색 하는 데 도움이 됩니다.

>[!IMPORTANT]
>아래 각 장에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다. 단계별 지침은 정확 하 고 최신 상태 이지만 최신의 비디오에서 스크립트 및 시각적 개체를 볼 수 있습니다. Posterity에 대 한 비디오는 포함 되어 있지만 적용 되는 개념은 그대로 유지 됩니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 211: 제스처</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.
* 몇 가지 C# 기본적인 프로그래밍 기능.
* [MR 기본 101](holograms-101.md)를 완료 해야 합니다.
* [MR 입력 210](holograms-210.md)을 완료 해야 합니다.
* [개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)있습니다.

### <a name="errata-and-notes"></a>정오표 및 참고 사항

* 코드에서 중단점을 적중 하려면 Visual Studio의 도구-> 옵션-> 디버깅에서 "내 코드만 사용"을 사용 하지 않도록 설정 (*선택 취소*) 해야 합니다.

## <a name="chapter-0---unity-setup"></a>0 장-Unity 설치

### <a name="instructions"></a>지침

1. Unity를 시작합니다.
2. **열기**를 선택 합니다.
3. 이전에 보관 하지 않은 **제스처** 폴더로 이동 합니다.
4. **모델 탐색기** **시작**/폴더를 찾아 선택 합니다.
5. **폴더 선택** 단추를 클릭 합니다.
6. **프로젝트** 패널에서 **장면** 폴더를 확장 합니다.
7. **모델 탐색기** 장면을 두 번 클릭 하 여 Unity에서 로드 합니다.

### <a name="building"></a>빌드

1. Unity에서 **파일 > 빌드 설정**을 선택 합니다.
2. 백그라운드에서 장면 **/모델 탐색기** 가 **백그라운드**에서 표시 되지 않는 경우 **열린 장면 추가** 를 클릭 하 여 장면을 추가 합니다.
3. 특별히 HoloLens를 개발 하는 경우 **대상 장치** 를 **hololens**로 설정 합니다. 그렇지 않으면 **모든 장치**에 그대로 둡니다.
4. **빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).
5. **빌드**를 클릭합니다.
6. "App" 이라는 **새 폴더** 를 만듭니다.
7. 단일 **앱** 폴더를 클릭 합니다.
8. **폴더 선택** 을 클릭 하면 Unity에서 Visual Studio 용 프로젝트 빌드를 시작 합니다.

Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.

1. **앱** 폴더를 엽니다.
2. **모델 탐색기 Visual Studio 솔루션**을 엽니다.

HoloLens에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.
2. 로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터**를 선택 합니다.
3. **HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다. **선택**을 클릭합니다. 장치 IP 주소를 모르는 경우 **네트워크 & 인터넷 > 고급 옵션 > 설정**을 참조 하세요.
4. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다. 처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device-hololens)으로 연결 해야 합니다.
5. 앱이 배포 되 면 **선택 제스처로** **fitbox** 를 해제 합니다.

모던 헤드셋에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64**로 변경 합니다.
2. 배포 대상이 **로컬 컴퓨터**로 설정 되었는지 확인 합니다.
3. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.
4. 앱이 배포 되 면 동작 컨트롤러에서 트리거를 당겨 **Fitbox** 를 해제 합니다.

>[!NOTE]
>Visual Studio 오류 패널에 몇 가지 빨간색 오류가 표시 될 수 있습니다. 무시 해도 됩니다. 출력 패널로 전환 하 여 실제 빌드 진행률을 확인 합니다. 출력 패널에 오류가 발생 하면 문제를 해결 해야 합니다 (대부분 스크립트에서 실수로 인해 발생 하는 경우).

## <a name="chapter-1---hand-detected-feedback"></a>1 장 검색 된 피드백

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>목표

* 직접 추적 이벤트를 구독 합니다.
* 커서 피드백을 사용 하 여 손을 추적할 때 사용자를 표시 합니다.

>[!NOTE]
>HoloLens 2에서 손이 표시 될 때마다 손 모양 (손가락을 가리키는 경우가 아님)이 발생 합니다.

### <a name="instructions"></a>지침

* **계층** 패널에서 **inputmanager** 개체를 확장 합니다.
* **GesturesInput** 개체를 찾고 선택 합니다.

**InteractionInputSource.cs** 스크립트는 다음 단계를 수행 합니다.

1. InteractionSourceDetected 및 InteractionSourceLost 이벤트를 구독 합니다.
2. 수동 검색 상태를 설정 합니다.
3. InteractionSourceDetected 및 InteractionSourceLost 이벤트의 구독을 취소 합니다.

다음으로, 사용자의 작업에 따라 사용자 의견을 표시 하는 커서를 [MR 입력 210](holograms-210.md) 에서 하나로 업그레이드 합니다.

1. **계층** 패널에서 **커서** 개체를 선택 하 고 삭제 합니다.
2. **프로젝트** 패널에서 **CursorWithFeedback** 를 검색 하 여 **계층** 패널로 끌어 옵니다.
3. **계층** 패널 **에서 inputmanager** 를 클릭 한 다음 **계층 구조** 에서 **CursorWithFeedback** 개체를 다음의 맨 아래에 있는 Inputmanager의 **simplesinglepointerselector**필드로 끕니다. **검사기**.
4. **계층**에서 **CursorWithFeedback** 를 클릭 합니다.
5. **검사기** 패널에서 **개체 커서** 스크립트의 **커서 상태 데이터** 를 확장 합니다.

**커서 상태 데이터** 는 다음과 같이 작동 합니다.

* 모든 **관찰** 상태는 검색 된 손이 없고 사용자가 간단히 살펴보는 것을 의미 합니다.
* 모든 **상호 작용** 상태는 손 또는 컨트롤러가 검색 됨을 의미 합니다.
* **가리키기** 상태는 사용자가 홀로그램을 보고 있음을 의미 합니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 **파일 > 빌드 설정을** 사용 하 여 응용 프로그램을 다시 빌드합니다.
* **앱** 폴더를 엽니다.
* 아직 열려 있지 않은 경우 **Modelexplorer Visual Studio 솔루션**을 엽니다.
  * 설정 하는 동안 Visual Studio에서이 프로젝트를 이미 빌드/배포한 경우 해당 인스턴스를 열고 메시지가 표시 되 면 다시 로드를 클릭할 수 있습니다.
* Visual Studio에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.
* 응용 프로그램을 HoloLens에 배포한 후에는 공기 탭 제스처를 사용 하 여 fitbox를 해제 합니다.
* 손을 보기로 이동 하 고 인덱스 손가락을 하늘으로 가리켜 손으로 추적을 시작 합니다.
* 왼쪽, 오른쪽, 위쪽 및 아래쪽으로 이동 합니다.
* 손 모양 검색 후 보기가 손실 될 때 커서가 어떻게 변경 되는지 봅니다.
* 모던 헤드셋을 사용할 경우 컨트롤러를 연결 하 고 연결을 끊어야 합니다. 연결 된 컨트롤러는 항상 "사용할 수 있음" 이므로이 피드백은 몰입 형 장치에서 그다지 흥미로운 점이 됩니다.

## <a name="chapter-2---navigation"></a>2 장-탐색

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>목표

* 탐색 제스처 이벤트를 사용 하 여 astronaut를 회전 합니다.

### <a name="instructions"></a>지침

앱에서 탐색 제스처를 사용 하려면 탐색 제스처가 발생할 때 **GestureAction.cs** 를 편집 하 여 개체를 회전 합니다. 또한 탐색을 사용할 수 있을 때 표시할 피드백을 커서에 추가 합니다.

1. **계층** 패널에서 **CursorWithFeedback**를 확장 합니다.
2. **Holograms** 폴더에서 **ScrollFeedback** 자산을 찾습니다.
3. **ScrollFeedback** Prefab를 **계층**의 **CursorWithFeedback** GameObject에 끌어다 놓습니다.
4. **CursorWithFeedback**을 클릭 합니다.
5. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
6. 메뉴의 검색 상자에 **CursorFeedback**을 입력 합니다. 검색 결과를 선택 합니다.
7. **ScrollFeedback** 개체를 **계층** 의 **커서 피드백** 구성 요소에있는 **검색 된 게임 개체의 스크롤** 속성으로 끌어 놓습니다.
8. **계층** 패널에서 **AstroMan** 개체를 선택 합니다.
9. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
10. 메뉴에서 검색 상자 **제스처 동작**을 입력 합니다. 검색 결과를 선택 합니다.

다음으로, Visual Studio에서 **GestureAction.cs** 을 엽니다. 연습 2. c 코딩에서 스크립트를 편집 하 여 다음을 수행 합니다.

1. 탐색 제스처가 수행 될 때마다 **AstroMan 개체를 회전** 합니다.
2. **RotationFactor** 를 계산 하 여 개체에 적용 되는 회전의 양을 제어 합니다.
3. 사용자가 왼쪽 또는 오른쪽으로 이동 하면 y 축 주위로 **개체를 회전** 합니다.

스크립트에서 예제 2(sp2)를 완료 하거나 코드를 아래의 완료 된 솔루션으로 바꿉니다.

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

다른 탐색 이벤트는 이미 일부 정보로 채워져 있음을 알 수 있습니다. GameObject를 도구 키트의 InputSystem's stack에 푸시하여, 회전이 시작 된 후 사용자가 Astronaut에 포커스를 유지할 필요가 없습니다. 마찬가지로 제스처가 완료 되 면 GameObject를 스택에서 팝 합니다.

### <a name="build-and-deploy"></a>빌드 및 배포

1. Unity에서 응용 프로그램을 다시 빌드한 다음, Visual Studio에서 빌드 및 배포 하 여 HoloLens에서 실행 합니다.
2. Astronaut을 응시 하 고 두 개의 화살표가 커서 양쪽에 표시 되어야 합니다. 이 새 시각적 개체는 astronaut을 회전할 수 있음을 나타냅니다.
3. HoloLens가 손을 추적 하기 시작 하도록 준비 된 위치 (하늘을 가리키고 있는 인덱스 손가락)에 손을 배치 합니다.
4. Astronaut를 회전 하려면 인덱스 손가락을 왼쪽 이나 오른쪽으로 이동 하 여 NavigationX 제스처를 트리거합니다.

## <a name="chapter-3---hand-guidance"></a>3 장 지침

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>목표

* 수동 **가이드 점수** 를 사용 하 여 수동 추적이 손실 되는 경우를 예측할 수 있습니다.
* **커서에 대 한 피드백** 을 제공 하 여 사용자가 카메라의 보기 가장자리에 가까이 있는 경우를 표시 합니다.

### <a name="instructions"></a>지침

1. **계층** 패널에서 **CursorWithFeedback** 개체를 선택 합니다.
2. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
3. 메뉴에서 검색 상자 **손 모양 지침**을 입력 합니다. 검색 결과를 선택 합니다.
4. **프로젝트** 패널 **Holograms** 폴더에서 **HandGuidanceFeedback** 자산을 찾습니다.
5. **HandGuidanceFeedback** 자산을 **검사기** 패널의 **손 지침 표시기** 속성으로 끌어다 놓습니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 응용 프로그램을 다시 빌드한 다음, Visual Studio에서 빌드 및 배포 하 여 HoloLens에서 앱을 경험해 보세요.
* 손으로 보기를 전환 하 고 인덱스 손가락을 발생 시켜 추적 하세요.
* 탐색 제스처로 astronaut 회전을 시작 합니다 (인덱스 손가락 및 엄지 단추를 함께 사용).
* 왼쪽, 오른쪽, 위쪽 및 아래쪽으로 이동 합니다.
* 제스처 프레임의 가장자리가 가까이 있으면 커서 옆에 화살표를 표시 하 여 손 추적이 손실 된다는 경고를 표시 합니다. 화살표는 추적 손실을 방지 하기 위해 손을 이동할 방향을 나타냅니다.

## <a name="chapter-4---manipulation"></a>4 장-조작

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>목표

* 조작 이벤트를 사용 하 여 astronaut를 손으로 이동 합니다.
* 조작을 사용할 수 있는 경우 사용자에 게 알릴 수 있도록 커서에 대 한 피드백을 제공 합니다.

### <a name="instructions"></a>지침

GestureManager.cs 및 AstronautManager.cs를 사용 하면 다음을 수행할 수 있습니다.

1. 음성 키워드 "**Move Astronaut**"를 사용 하 여 **조작** 제스처를 사용 하도록 설정 하 고 "**Rotate Astronaut**"를 사용 하지 않도록 설정 합니다.
2. **조작 제스처 인식기**에 대 한 응답으로 전환 합니다.

이제 시작하겠습니다.

1. **계층** 패널에서 비어 있는 새 GameObject을 만듭니다. 이름을 "**AstronautManager**"로 합니다.
2. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
3. 메뉴의 검색 상자에 **Astronaut Manager**를 입력 합니다. 검색 결과를 선택 합니다.
4. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
5. 메뉴의 검색 상자에 **음성 입력 원본**을 입력 합니다. 검색 결과를 선택 합니다.

이제 astronaut의 상호 작용 상태를 제어 하는 데 필요한 음성 명령을 추가 합니다.

1. **검사기**에서 **키워드** 섹션을 확장 합니다.
2. 오른쪽의 **+** 를 클릭 하 여 새 키워드를 추가 합니다.
3. 키워드를 **Move Astronaut**로 입력 합니다. 원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.
4. 오른쪽의 **+** 를 클릭 하 여 새 키워드를 추가 합니다.
5. **Astronaut 회전**으로 키워드를 입력 합니다. 원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.
6. 해당 처리기 코드는 **GestureAction.cs**의 **ISpeechHandler OnSpeechKeywordRecognized** 처리기에서 찾을 수 있습니다.

![4 장의 음성 입력 소스를 설정 하는 방법](images/holograms211-speech.png)

다음으로 커서에서 조작 피드백을 설정 합니다.

1. **프로젝트** 패널 **Holograms** 폴더에서 **pathingfeedback** 자산을 찾습니다.
2. **Pathingfeedback** Prefab을 **계층**의 **CursorWithFeedback** 개체로 끌어서 놓습니다.
3. **계층** 패널에서 **CursorWithFeedback**를 클릭 합니다.
4. **Inspector**의 **커서 피드백** 구성 요소에서 **Pathing 검색 된 게임 개체** 속성에 **pathingfeedback** 개체를 끌어서 놓습니다.

이제 **GestureAction.cs** 에 코드를 추가 하 여 다음을 사용 하도록 설정 해야 합니다.

1. **IManipulationHandler** 함수에 코드를 추가 합니다 .이 함수는 **조작** 제스처가 검색 될 때 astronaut를 이동 합니다.
2. **이동 벡터** 를 계산 하 여 astronaut 위치에 따라 이동 해야 하는 위치를 결정 합니다.
3. Astronaut를 새 위치로 **이동** 합니다.

**GestureAction.cs**에서 연습 4-5를 완료 하거나 아래에서 완성 된 솔루션을 사용 합니다.

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

* Unity에서 다시 빌드한 다음, Visual Studio에서 빌드 및 배포 하 여 HoloLens에서 앱을 실행 합니다.
* HoloLens 앞으로 손을 이동 하 고 추적할 수 있도록 인덱스 손가락을 올립니다.
* Astronaut 위에 커서를 올려 둡니다.
* Astronaut를 조작 제스처로 이동 하려면 ' Move Astronaut '를 표시 합니다.
* 이제 프로그램에서 조작 이벤트에 응답 하는 것을 나타내기 위해 커서 주위에 네 개의 화살표가 표시 됩니다.
* 인덱스 손가락을 엄지 단추 아래로 낮추고 pinched을 함께 유지 합니다.
* 손을 움직이면 astronaut도 이동 합니다 (이는 조작).
* Astronaut 조작을 중지 하도록 인덱스 손가락을 올립니다.
* 참고: 손을 이동 하기 전에 ' Move Astronaut '가 표시 되지 않으면 탐색 제스처가 대신 사용 됩니다.
* Rotatable 상태로 돌아가려면 ' Astronaut 회전 ' 이라고 합니다.

## <a name="chapter-5---model-expansion"></a>5 장-모델 확장

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>목표

* Astronaut 모델을 사용자가 상호 작용할 수 있는 여러 개의 작은 조각으로 확장 합니다.
* 탐색 및 조작 제스처를 사용 하 여 각 부분을 개별적으로 이동 합니다.

### <a name="instructions"></a>지침

이 섹션에서는 다음 작업을 수행 합니다.

1. 새 "**모델 확장**" 키워드를 추가 하 여 astronaut 모델을 확장 합니다.
2. 새 키워드 "**모델 다시 설정**"을 추가 하 여 모델을 원래 형식으로 반환 합니다.

이전 장의 음성 입력 소스에 두 개 이상의 키워드를 추가 하 여이 작업을 수행 합니다. 또한 인식 이벤트를 처리 하는 또 다른 방법을 보여 드리겠습니다.

1. **검사기** 에서 **AstronautManager** 를 클릭 하 고 **검사기**에서 **키워드** 섹션을 확장 합니다.
2. 오른쪽의 **+** 를 클릭 하 여 새 키워드를 추가 합니다.
3. 키워드를 **확장 모델**로 입력 합니다. 원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.
4. 오른쪽의 **+** 를 클릭 하 여 새 키워드를 추가 합니다.
5. 키워드를 **모델 다시 설정**으로 입력 합니다. 원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.
6. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
7. 메뉴의 검색 상자에 **음성 입력 처리기**를 입력 합니다. 검색 결과를 선택 합니다.
8. 이 명령은 GameObject에 관계 없이 작동 하기 때문에 **전역 수신기**를 선택 합니다.
9. 단추를 **+** 클릭 하 고 키워드 드롭다운에서 **모델 확장** 을 선택 합니다.
10. 응답 아래를 클릭 하 고 계층의 **AstronautManager** 을 **None (Object)** 필드로 끕니다. **+**
11. 이제 **함수 없음** 드롭다운을 클릭 하 고 **AstronautManager**, **ExpandModelCommand**를 차례로 선택 합니다.
12. 음성 입력 처리기의 **+** 단추를 클릭 하 고 키워드 드롭다운에서 **모델 다시 설정** 을 선택 합니다.
13. 응답 아래를 클릭 하 고 계층의 **AstronautManager** 을 **None (Object)** 필드로 끕니다. **+**
14. 이제 **함수 없음** 드롭다운을 클릭 하 고 **AstronautManager**, **resetmodelcommand**를 차례로 선택 합니다.

![5 장의 음성 입력 소스 및 처리기를 설정 하는 방법](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>빌드 및 배포

* 시도해 보세요. 앱을 빌드하고 HoloLens에 배포 합니다.
* **모델을 확장** 하 여 확장 된 astronaut 모델을 표시 한다고 가정 합니다.
* **탐색** 을 사용 하 여 astronaut 짝패의 개별 부분을 회전 합니다.
* **Astronaut를 이동한** 다음 **조작** 을 사용 하 여 Astronaut 짝패의 개별 부분을 이동 합니다.
* **Astronaut를 회전** 하 여 조각을 다시 회전 한다고 가정 합니다.
* **모델을 다시 설정** 하 여 원래 형식으로 astronaut를 반환 한다고 가정 합니다.

## <a name="the-end"></a>끝

축하합니다. 이제 MR 입력 211 **을 완료 했습니다. 제스처**.

* 직접 추적, 탐색 및 조작 이벤트를 검색 하 고 대응 하는 방법을 알고 있습니다.
* 탐색 제스처와 조작 제스처의 차이점을 이해 하 고 있습니다.
* 커서를 변경 하 여 손을 감지 했을 때, 손을 잃어 버릴 때, 개체가 서로 다른 상호 작용을 지 원하는 경우 (탐색 vs 조작)에 대 한 시각적 피드백을 제공 하도록 커서를 변경 하는 방법을 알고 있습니다.
