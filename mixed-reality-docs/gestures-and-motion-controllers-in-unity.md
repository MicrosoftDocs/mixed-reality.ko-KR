---
title: Unity의 제스처 및 동작 컨트롤러
description: Unity에서 작업을 수행 하는 데는 두 가지 주요 방법, 즉 핸드 제스처와 동작 컨트롤러가 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 제스처, 동작 컨트롤러, unity, 응시, 입력
ms.openlocfilehash: a7ca5a895015ba0458f0f64f1422612e797f5067
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435230"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Unity의 제스처 및 동작 컨트롤러

HoloLens의 [손으로](gaze-and-commit.md#composite-gestures) 는 [Unity](gaze-in-unity.md)에서 작업을 수행 하는 두 가지 주요 방법, 그리고 HOLOLENS 및 몰입 형 HMD의 [동작 컨트롤러](motion-controllers.md) 를 사용할 수 있습니다. Unity에서 동일한 Api를 통해 두 공간 입력 원본에 대 한 데이터에 액세스할 수 있습니다.

Unity는 Windows Mixed Reality의 공간 입력 데이터에 액세스 하는 두 가지 기본 방법인 공통 *입력. GetButton/input. Getbutton* api는 여러 Unity XR sdk에서 작동 하 고, *InteractionManager/GestureRecognizer* api는와 관련이 있습니다. 사용 가능한 공간 입력 데이터의 전체 집합을 노출 하는 Windows 혼합 현실입니다.

## <a name="unity-buttonaxis-mapping-table"></a>Unity 단추/축 매핑 테이블

아래 표의 단추 및 축 Id는 *입력. GetButton/Getbutton* api를 통해 Unity의 Windows Mixed Reality 동작 컨트롤러에서 지원 됩니다. 반면 "Windows MR" 열은에서 사용할 수 있는 속성을 참조 합니다. *InteractionSourceState* 유형입니다. 이러한 각 Api에 대해서는 아래 섹션에서 자세히 설명 합니다.

Windows Mixed Reality의 단추/축 ID 매핑은 일반적으로 Oculus 단추/축 Id와 일치 합니다.

Windows Mixed Reality의 단추/축 ID 매핑은 다음 두 가지 방법으로 OpenVR 매핑과 다릅니다.
1. 이 매핑은 thumbsticks와 터치 패드를 모두 사용 하는 컨트롤러를 지원 하기 위해 엄지 스틱과는 다른 터치 패드 Id를 사용 합니다.
2. 매핑은 메뉴 단추의 A 및 X 단추 Id를 오버 로드 하지 않고 실제 ABXY 단추에 사용할 수 있도록 합니다.

<table>
<tr>
<th rowspan="2">입력 </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity Api</a><br />(입력. GetButton/Getbutton) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 특정 입력 API</a><br />XR. WSA. 입력</th>
</tr><tr>
<th> 왼쪽 </th><th> 오른쪽</th>
</tr><tr>
<td> 트리거를 선택 합니다. </td><td> 축 9 = 1.0 </td><td> 축 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> 아날로그 값 트리거를 선택 합니다. </td><td> 축 9 </td><td> 축 10 </td><td> Select보도 금액</td>
</tr><tr>
<td> 부분적으로 누른 트리거 선택 </td><td> 단추 14 <i>(게임  호환)</i></td><td> 단추 15 <i>(게임 패드 호환성)</i> </td><td> Select보도 횟수 &gt; 0.0</td>
</tr><tr>
<td> 메뉴 단추 누름 </td><td> 단추 6 * </td><td> 단추 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 그립 단추 누름 </td><td> 축 11 = 1.0 (아날로그 값 없음)<br />단추 4 <i>(게임 패드 호환성)</i> </td><td> 축 12 = 1.0 (아날로그 값 없음)<br />단추 5 <i>(게임 패드 호환성)</i> </td><td> grasped</td>
</tr><tr>
<td> 엄지 스틱 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </td><td> 축 1 </td><td> 축 4 </td><td> thumbstickPosition</td>
</tr><tr>
<td> 엄지 스틱 Y <i>(위쪽:-1.0, 아래쪽: 1.0)</i> </td><td> 축 2 </td><td> 축 5 </td><td> thumbstickPosition</td>
</tr><tr>
<td> 엄지 스틱 누름 </td><td> 단추 8 </td><td> 단추 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 터치 패드 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </td><td> 축 17 * </td><td> 축 19 * </td><td> touchpadPosition</td>
</tr><tr>
<td> 터치 패드 Y <i>(위쪽:-1.0, 아래쪽: 1.0)</i> </td><td> 축 18 * </td><td> 축 20 * </td><td> touchpadPosition</td>
</tr><tr>
<td> 터치 패드 작업 </td><td> 단추 18 * </td><td> 단추 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 터치 패드 누름 </td><td> 단추 16 * </td><td> 단추 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 그립 포즈 또는 포인터 포즈 </td><td colspan="2"> <i>그립</i> 포즈만: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking. GetLocalRotation</a></td><td> 전달 <i>그립</i> 또는 <i>포인터</i> 를 인수로 전달 합니다. sourcestate TryGetPosition<br />sourceState<br /></td>
</tr><tr>
<td> 상태 추적 </td><td colspan="2"> <i>위치 정확도 및 원본 손실 위험은 MR 특정 API를 통해서만 사용할 수 있습니다</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState. positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>이러한 단추/축 Id는 gamepads, Oculus Touch 및 OpenVR에서 사용 하는 매핑의 충돌로 인해 Unity에서 OpenVR에 사용 하는 Id와 다릅니다.

## <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 및 포인팅 포즈

Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 하며, 각 컨트롤러의 디자인이 사용자의 손 위치와 앱에서 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다. controller.

이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스, **그립 포즈** 및 **포인터 포즈**에 대해 조사할 수 있는 두 가지 종류의 포즈를 확인할 수 있습니다. 그립 포즈 및 포인터 포즈 좌표는 모두 전역 Unity 세계 좌표의 모든 Unity Api에 의해 표현 됩니다.

### <a name="grip-pose"></a>그립 포즈

**그립 포즈** 는 HoloLens에서 감지한 손바닥의 위치 또는 동작 컨트롤러를 보유 하는 야자나무를 나타냅니다.

몰입 형 헤드셋에서 그립 포즈는 사용자 **의 손을** 만들거나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다. 동작 컨트롤러에 대해 Windows에서 제공 하는 **렌더링할 모델** 은 동작 컨트롤러를 시각화할 때에도 그립 포즈를 사용 합니다.

그립 포즈는 구체적으로 다음과 같이 정의 됩니다.
* **그립 위치**: 컨트롤러를 자연스럽 게 유지 하는 경우 왼쪽 또는 오른쪽으로 조정 하 여 그립 내 위치를 가운데에 맞춥니다. Windows Mixed Reality 동작 컨트롤러에서이 위치는 일반적으로 보통 클릭 단추와 맞춥니다.
* **그립 방향 오른쪽 축**: 손 모양 5 손가락 포즈를 형성 하는 손을 완전히 열 때 palm (왼쪽 야자나무에서 오른쪽으로 뒤로)의 광선을 만듭니다.
* **그립 방향 전방 축: 핸들**을 부분적으로 (컨트롤러를 보유 하는 것 처럼) 닫는 경우 비 엄지 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.
* **그립 방향 up 축**: 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.

Unity의 교차 공급 업체 입력 API (XR)를 통해 그립 포즈에 액세스할 수 있습니다 *[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) 또는 WINDOWS MR 특정 API (*sourcestate/Rotation*, **그립** 노드에 대 한 포즈 데이터 요청)를 통해

### <a name="pointer-pose"></a>포인터 포즈

**포인터 포즈** 는 컨트롤러의 팁을 나타냅니다.

시스템 제공 포인터 포즈는 **컨트롤러 모델 자체를 렌더링**하는 경우 raycast에 가장 잘 사용 됩니다. 컨트롤러 대신 다른 가상 개체 (예: 가상 사용자)를 렌더링 하는 경우 앱 정의 된 포 모델의 배럴을 따라 이동 하는 광선과 같이 해당 가상 개체에 가장 자연 스러운 광선을 가리켜야 합니다. 사용자는 가상 개체를 볼 수 있고 실제 컨트롤러는 볼 수 없으므로 가상 개체를 가리키면 앱을 사용 하는 것이 더 자연스럽 게 될 수 있습니다.

현재 포인터 포즈는 *InteractionSourceNode* 를 인수로 전달 하는 Windows MR 특정 API 인 *TryGetPosition/Rotation*을 통해서만 Unity에서 사용할 수 있습니다.

## <a name="controller-tracking-state"></a>컨트롤러 추적 상태

헤드셋 처럼 Windows Mixed Reality 동작 컨트롤러를 사용 하려면 외부 추적 센서를 설정 하지 않아도 됩니다. 대신, 컨트롤러는 헤드셋 자체의 센서에 의해 추적 됩니다.

사용자가 컨트롤러를 헤드셋의 뷰 필드에서 밖으로 이동 하는 경우 대부분의 경우 Windows는 컨트롤러 위치를 계속 유추 하 고 앱에 제공 합니다. 컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다.

이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다. 컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다.

이를 위한 가장 좋은 방법은 직접 시도해 보는 것입니다. 다양 한 추적 상태에서 동작 컨트롤러와 함께 작동 하는 몰입 형 콘텐츠 예제를 통해이 비디오를 확인 하세요.

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>명시적 추적 상태에 대 한 추론

추적 상태에 따라 위치를 다르게 처리 하려는 앱은 더 나아가 컨트롤러의 상태에 대 한 속성 (예: *SourceLossRisk* 및 *positionaccuracy*)을 검사할 수 있습니다.

<table>
<tr>
<th> 상태 추적 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>높은 정확도</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>높은 정확도 (손실 위험)</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>대략적인 정확도</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: orange"> 대략 일치 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>위치  없음</b></td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: orange"> 대략 일치 </td><td style="background-color: orange"> false</td>
</tr>
</table>

이러한 동작 컨트롤러 추적 상태는 다음과 같이 정의 됩니다.
* **높은 정확도:** 동작 컨트롤러는 헤드셋의 보기 필드 내에 있지만 일반적으로 시각적 추적에 따라 정확도가 높은 위치를 제공 합니다. 일시적으로 보기의 필드를 벗어나거나 헤드셋 센서에서 일시적으로 가려진 이동 컨트롤러 (예: 사용자)는 컨트롤러의 관성 추적을 기반으로 짧은 시간 동안 계속 해 서 정확도가 높은 포즈를 반환 합니다. 자체.
* **높은 정확도 (손실 위험):** 사용자가 이동 컨트롤러를 헤드셋의 보기 필드 가장자리를 지나서 이동할 때 헤드셋은 곧 컨트롤러의 위치를 시각적으로 추적할 수 없습니다. 앱은 **SourceLossRisk** reach 1.0을 확인 하 여 컨트롤러가이 FOV 경계에 도달한 경우를 인식 합니다. 이 시점에서 앱은 매우 높은 품질의 동작을 안정적으로 스트리밍하는 데 필요한 컨트롤러 제스처를 일시 중지 하도록 선택할 수 있습니다.
* **대략적인 정확도:** 컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다. 이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다. 컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다. 입력 요구 사항이 많은 앱은 사용자에 게 오프 스크린 대상에 대 한 hitbox을 제공 하는 등의 방법으로 **positionaccuracy** 속성을 검사 하 여 정확도가 **높은** **정확도부터 정확도까지** 이러한 삭제를 합리적으로 선택할 수 있습니다. 이 시간 동안.
* **위치 없음:** 컨트롤러는 오랜 시간 동안 정확한 정확도로 작동할 수 있지만 때때로 본문 잠금 위치가 중요 하지 않은 것을 시스템에서 인식 하는 경우도 있습니다. 예를 들어 방금 설정 된 컨트롤러가 시각적으로 관찰 되지 않았거나 사용자가 다른 사용자가 선택 하는 컨트롤러를 배치할 수 있습니다. 이러한 시간에 시스템은 앱에 어떤 위치도 제공 하지 않으며 *TryGetPosition* 는 false를 반환 합니다.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Common Unity Api (입력. GetButton/Getbutton)

**네임 스페이스:** *unityengine*, *unityengine. XR*<br>
**형식**: *Input*, *XR. InputTracking*

Unity는 현재 일반 입력을 사용 *합니다. GetButton/Input. Getbutton* api를 사용 하면 핸드 및 동작 컨트롤러를 포함 하 여 [oculus Sdk](https://docs.unity3d.com/Manual/OculusControllers.html), [Openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html) 및 Windows Mixed Reality의 입력을 노출할 수 있습니다. 앱이 입력에 이러한 Api를 사용 하는 경우 Windows Mixed Reality를 비롯 하 여 여러 XR Sdk에서 동작 컨트롤러를 쉽게 지원할 수 있습니다.

### <a name="getting-a-logical-buttons-pressed-state"></a>논리적 단추의 누름 상태 가져오기

일반 Unity 입력 Api를 사용 하려면 일반적으로 [Unity 입력 관리자](https://docs.unity3d.com/Manual/ConventionalGameInput.html)에서 단추와 축을 논리적 이름에 연결 하 여 단추 또는 축 id를 각 이름에 바인딩하는 것으로 시작 합니다. 그런 다음 해당 논리적 단추/축 이름을 참조 하는 코드를 작성할 수 있습니다.

예를 들어 왼쪽 동작 컨트롤러의 트리거 단추를 전송 작업에 매핑하려면 **> 프로젝트 설정 편집** 으로 이동 하 여 Unity 내에서 입력 > 하 고 축 아래에서 제출 섹션의 속성을 확장 합니다. **식이 양의 단추나** **Alt 긍정 단추** 속성을 다음과 같이 **조이스틱 단추 14**로 변경 합니다.

![Unity의 InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

그런 다음 스크립트는 입력을 사용 하 여 전송 작업을 확인할 수 있습니다 *. GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
**축**에서 **크기** 속성을 변경 하 여 논리적 단추를 더 추가할 수 있습니다.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>물리적 단추의 누름 상태를 직접 가져오기

*입력. GetKey*를 사용 하 여 정규화 된 이름으로 수동으로 단추에 액세스할 수도 있습니다.

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>직접 또는 동작 컨트롤러의 포즈 가져오기

XR를 사용 하 여 컨트롤러의 위치 및 회전에 액세스할 수 있습니다 *. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

이는 컨트롤러의 그립 포즈 (사용자가 컨트롤러를 보유 하는 위치)를 나타내며 사용자의 손을 사용 하거나 컨트롤러 자체의 모델을 렌더링 하는 데 유용 합니다.

이 그립 포즈와 포인터 포즈 (컨트롤러의 팁) 간의 관계는 컨트롤러 마다 다를 수 있습니다. 이제 컨트롤러의 포인터 포즈에 액세스 하는 것은 아래 섹션에 설명 된 MR 특정 입력 API를 통해서만 가능 합니다.

## <a name="windows-specific-apis-xrwsainput"></a>Windows 관련 Api (XR. WSA. 입력

**네임 스페이스:** *unityengine. XR*<br>
**유형**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Windows Mixed Reality 입력 (HoloLens 용) 및 동작 컨트롤러에 대 한 자세한 정보를 보려면 *Unityengine. XR* 네임 스페이스에서 windows 관련 공간 입력 api를 사용 하도록 선택할 수 있습니다. 이를 통해 위치 정확도 나 소스 종류와 같은 추가 정보에 액세스할 수 있으므로 실습 및 컨트롤러를 구분할 수 있습니다.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>직접 및 동작 컨트롤러의 상태 폴링

*GetCurrentReading* 메서드를 사용 하 여 각 상호 작용 소스 (직접 또는 동작 컨트롤러)에 대해이 프레임의 상태를 폴링할 수 있습니다.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

가져오는 각 *InteractionSourceState* 는 현재 시점에서 상호 작용 소스를 나타냅니다. *InteractionSourceState* 는 다음과 같은 정보를 노출 합니다.
* 어떤 [종류의 누름](motion-controllers.md) 이 발생 합니까 (선택/메뉴/-/터치 패드/엄지 스틱)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 터치 패드 및/또는 엄지 스틱 XY 좌표 및 작업 된 상태와 같은 동작 컨트롤러에 해당 하는 기타 데이터

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* InteractionSourceKind는 원본이 나 동작 컨트롤러 인지 여부를 알 수 있습니다.

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>앞으로 예측 된 렌더링 동작에 대 한 폴링

* 손이 나 컨트롤러에서 상호 작용 원본 데이터를 폴링하는 경우이 프레임의 photons 사용자의 눈에 도달 하 게 되는 순간에 대해 앞으로 예측 하는 포즈를 얻을 수 있습니다.  이러한 앞으로 예측 된 포즈는 컨트롤러를 **렌더링** 하거나 각 프레임을 보유 한 개체를 렌더링 하는 데 가장 적합 합니다.  컨트롤러를 사용 하 여 지정 된 보도 또는 릴리스를 대상으로 하는 경우 아래에 설명 된 기록 이벤트 Api를 사용 하는 경우 가장 정확 합니다.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 이 현재 프레임에 대해 앞으로 예측 한 헤드 포즈를 얻을 수도 있습니다.  원본 포즈와 마찬가지로,이 기능은 커서를 **렌더링** 하는 데 유용 합니다. 단, 아래에 설명 된 기록 이벤트 api를 사용 하는 경우에는 지정 된 누름 또는 릴리스를 대상으로 하는 것이 가장 정확 합니다.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>상호 작용 소스 이벤트 처리

정확한 기록 포즈 데이터에서 발생 하는 입력 이벤트를 처리 하기 위해 폴링 대신 상호 작용 소스 이벤트를 처리할 수 있습니다.

상호 작용 소스 이벤트를 처리 하려면:
* *InteractionManager* 입력 이벤트에 등록 합니다. 관심이 있는 각 상호 작용 이벤트 형식에 대해 구독 해야 합니다.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* 이벤트를 처리 합니다. 상호 작용 이벤트를 구독 한 후에는 해당 하는 경우 콜백을 받게 됩니다. *Sourcepressed* 예제에서는 소스가 검색 된 후와 릴리스 또는 손실 되기 전에이 상태가 됩니다.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>이벤트 처리를 중지 하는 방법

이벤트에 더 이상 관심이 없거나 이벤트를 구독 하는 개체를 삭제 하려는 경우에는 이벤트 처리를 중지 해야 합니다. 이벤트 처리를 중지 하려면 이벤트의 구독을 취소 합니다.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>상호 작용 소스 이벤트 목록

사용할 수 있는 상호 작용 소스 이벤트는 다음과 같습니다.
* *InteractionSourceDetected* (원본이 활성화 됩니다.)
* *InteractionSourceLost* (비활성 상태가 됨)
* *InteractionSourcePressed* (누르기, 단추 누르기 또는 "Select" 재생)
* *InteractionSourceReleased* (탭의 끝, 단추 해제 또는 "Select" 재생 끝)
* *InteractionSourceUpdated* (다른 상태를 이동 하거나 변경 하지 않음)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>기록 대상 이벤트는 누름 또는 릴리스와 가장 정확 하 게 일치 합니다.

앞에서 설명한 폴링 Api는 앱을 앞으로 예측 하는 포즈를 제공 합니다.  이러한 예측 된 포즈는 컨트롤러 또는 가상 핸드헬드 개체를 렌더링 하는 데 가장 적합 하지만 다음 두 가지 주요 이유로 이후 포즈는 대상 지정에 적합 하지 않습니다.
* 사용자가 컨트롤러의 단추를 누르면 시스템이 press를 받기 전에 Bluetooth를 통해 무선 대기 시간이 20ms 될 수 있습니다.
* 그런 다음 앞으로 예측 하는 포즈를 사용 하는 경우 현재 프레임의 photons가 사용자의 눈에 도달 하는 시간을 대상으로 하는 20ms 예측의 또 다른 10 개를 적용할 수 있습니다.

즉, 폴링을 통해 사용자의 헤드 및 손을 사용 하는 경우에는 사용자의 헤드를 30-40ms로 나타내는 소스 포즈 또는 헤드가 발생 합니다.  HoloLens 손으로 입력 한 경우 무선 전송 지연이 발생 하지 않지만, 누르기를 검색 하는 데 비슷한 처리 지연이 발생 합니다.

직접 또는 컨트롤러에 대 한 사용자의 원래 의도에 따라 정확 하 게 대상으로 지정 하려면 해당 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 입력 이벤트에서 기록 원본 포즈 또는 head 포즈를 사용 해야 합니다.

사용자의 헤드 또는 해당 컨트롤러에서 기록 포즈 데이터를 사용 하 여 보도를 대상으로 지정할 수 있습니다.
* 사용자가 [gazing](gaze-and-commit.md) 된 항목을 확인 하기 위해 **대상 지정** 에 사용할 수 있는 제스처 또는 컨트롤러를 누를 때 발생 하는 시점의 헤드입니다.

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* 이동 컨트롤러를 사용 하 여 사용자가 컨트롤러를 가리킨 **항목을 확인 하는** 데 사용 될 수 있는 시점에 발생 하는 소스입니다.  이는 누름이 발생 한 컨트롤러의 상태가 됩니다.  컨트롤러 자체를 렌더링 하는 경우에는 핸들 포즈 대신 포인터 포즈를 요청 하 여 사용자가 렌더링 된 컨트롤러의 자연 스러운 팁을 고려 하는 대상 광선을 만들 수 있습니다.

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>이벤트 처리기 예

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>상위 수준 복합 제스처 Api (GestureRecognizer)

**네임 스페이스:** *unityengine. XR*<br>
**유형**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

앱은 공간 입력 원본, 탭, 유지, 조작 및 탐색 제스처에 대 한 상위 수준 복합 제스처를 인식할 수도 있습니다. GestureRecognizer를 사용 하 여 [직접](gaze-and-commit.md#composite-gestures) 및 [동작 컨트롤러](motion-controllers.md) 에서 이러한 복합 제스처를 인식할 수 있습니다.

GestureRecognizer의 각 제스처 이벤트는 입력에 대 한 SourceKind와 이벤트 시점의 대상 헤드 광선을 제공 합니다. 일부 이벤트는 추가 컨텍스트별 정보를 제공 합니다.

제스처 인식기를 사용 하 여 제스처를 캡처하는 데 필요한 몇 가지 단계만 있습니다.
1. 새 제스처 인식기 만들기
2. 감시할 제스처 지정
3. 이러한 제스처에 대 한 이벤트 구독
4. 제스처 캡처 시작

### <a name="create-a-new-gesture-recognizer"></a>새 제스처 인식기 만들기

*GestureRecognizer*를 사용 하려면 *GestureRecognizer*를 만들어야 합니다.

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>감시할 제스처 지정

*SetRecognizableGestures ()* 를 통해 관심 있는 제스처를 지정 합니다.

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>이러한 제스처에 대 한 이벤트 구독

관심이 있는 제스처에 대 한 이벤트를 구독 합니다.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>탐색 및 조작 제스처는 *GestureRecognizer*의 인스턴스에서 함께 사용할 수 없습니다.

### <a name="start-capturing-gestures"></a>제스처 캡처 시작

기본적으로 *GestureRecognizer* 는 *Startcapturinggestures ()* 를 호출할 때까지 입력을 모니터링 하지 않습니다. *Stopcapturinggestures ()* 가 처리 된 프레임 보다 먼저 입력이 수행 되 면 *Stopcap의 ing제스처 ()* 가 호출 된 후에 제스처 이벤트가 생성 될 수 있습니다. *GestureRecognizer* 는 제스처가 실제로 발생 한 previou 프레임 중에 설정 되었는지 여부를 기억할 것 이므로이 프레임의 응시 대상에 따라 제스처 모니터링을 시작 및 중지 하는 것은 안정적입니다.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>제스처 캡처 중지

제스처 인식을 중지 하려면:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>제스처 인식기 제거

*GestureRecognizer* 개체를 삭제 하기 전에 구독 이벤트의 구독을 취소 해야 합니다.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Unity에서 동작 컨트롤러 모델 렌더링

![동작 컨트롤러 모델 및 teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*동작 컨트롤러 모델 및 teleportation*

응용 프로그램에서 사용자가 보유 하 고 있는 실제 컨트롤러와 일치 하는 동작 컨트롤러를 렌더링 하려면 [혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity/)에서 **motioncontroller prefab** 를 사용할 수 있습니다.  이 prefab는 시스템의 설치 된 동작 컨트롤러 드라이버에서 런타임에 올바른 인 글 Tf 모델을 동적으로 로드 합니다.  편집기에서 수동으로 가져오는 대신 이러한 모델을 동적으로 로드 하는 것이 중요 합니다. 따라서 앱은 사용자에 게 있을 수 있는 현재 및 미래의 모든 컨트롤러에 대해 물리적으로 정확한 3D 모델을 표시 합니다.

1. [시작](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 지침에 따라 Mixed Reality Toolkit를 다운로드 하 여 Unity 프로젝트에 추가 합니다.
2. 시작 단계의 일부로 카메라를 *MixedRealityCameraParent* prefab로 대체 한 경우에는 계속 진행 하는 것이 좋습니다.  이 prefab에는 동작 컨트롤러 렌더링이 포함 됩니다.  그렇지 않으면 프로젝트 창에서 장면에 asset */HoloToolkit/Input/Prefabs/MotionControllers. prefab* 를 추가 합니다.  사용자가 장면 내에서 teleports 때 카메라를 이동 하는 데 사용 하는 모든 부모 개체의 자식으로 해당 prefab을 추가 하 여 컨트롤러를 사용자와 함께 사용할 수 있습니다.  앱에 teleporting 포함 되지 않은 경우 장면의 루트에 prefab를 추가 합니다.

## <a name="throwing-objects"></a>개체 throw

가상 현실에서 개체를 throw 하는 것은 어려운 문제 이며, 처음에는 보일 수 있습니다. 대부분의 물리적 기반 상호 작용의 경우와 마찬가지로 게임에서 throw 되는 것이 예기치 않은 방식으로 작동 하는 경우에는 즉시 명확 하 고 집중 교육 중단 됩니다. 실제로 올바른 throw 동작을 나타내는 방법에 대해 자세히 살펴보고, 플랫폼 업데이트를 통해 사용할 수 있는 몇 가지 지침을 제공 하 여 사용자와 공유 하 고 싶습니다.

[여기](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)에서 throw를 구현 하는 방법에 대 한 예제를 찾을 수 있습니다. 이 샘플은 다음 네 가지 지침을 따릅니다.
* **위치 대신 컨트롤러의 *속도* 를 사용**합니다. 11 월 Windows 업데이트에서는 [' ' 근사치 ' ' 위치 추적 상태](motion-controllers.md#controller-tracking-state)에 있는 경우 동작이 변경 되었습니다. 이 상태에서 컨트롤러에 대 한 속도 정보는 정확도가 높은 것으로 예상 되는 경우에도 계속 보고 됩니다 .이는 일반적으로 높은 정확도를 유지 합니다.
* **컨트롤러의 *각도 속도* 를 통합**합니다. 이 논리는 위에 링크 된 패키지 내에서 `GetThrownObjectVelAngVel` 정적 메서드의 `throwing.cs` 파일에 모두 포함 됩니다.
   1. 각도 속도가 conserved throw 된 개체는 throw 되는 순간와 동일한 각도의 속도를 유지 해야 합니다 `objectAngularVelocity = throwingControllerAngularVelocity;`.
   2. Throw 된 개체의 질량 중심은 그립 포즈의 원점에 있지 않을 수 있으므로 사용자 참조 프레임의 컨트롤러와 다른 속도를 가질 가능성이 높습니다. 이러한 방식으로 제공 되는 개체 속도의 부분은 컨트롤러 원본 주위에서 throw 된 개체의 질량 중심의 순간 탄젠트 속도입니다. 이 탄젠트 속도는 컨트롤러 원본 및 throw 된 개체의 질량 중심 사이의 거리를 나타내는 벡터와 컨트롤러의 각도 속도 간 곱입니다.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. 따라서 throw 된 개체의 총 속도는 컨트롤러의 속도와 이러한 탄젠트 속도의 합입니다. `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **속도를 적용 하는 *시간* 에 대 한 주의를**기울여야 합니다. 단추를 누르면 해당 이벤트가 Bluetooth를 통해 운영 체제에 20ms 최대의 시간이 걸릴 수 있습니다. 즉, 컨트롤러 상태 변경을 누른 상태에서 누르지 않음 또는 그 반대로 폴링할 때 발생 하는 컨트롤러의 정보는 실제로 이러한 변화에 대 한 것입니다. 또한 폴링 API에 의해 표시 되는 컨트롤러는 프레임이 표시 될 때 발생할 수 있는 포즈를 반영 하 여 향후 20ms 될 수 있는 것으로 예상 됩니다. 이는 보류 중인 개체를 *렌더링* 하는 데 유용 하지만 사용자가 throw를 릴리스한 순간의 궤적을 계산할 때 개체를 *대상으로 지정* 하는 데 시간이 복합어. 다행히 11 월 업데이트를 사용 하는 경우 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 와 같은 Unity 이벤트가 전송 되 면이 상태에는 단추가 실제로 눌러져 있거나 해제 되었을 때의 기록 포즈 데이터가 반환 됩니다.  을 throw 하는 동안 가장 정확한 컨트롤러 렌더링과 컨트롤러를 대상으로 하려면 적절 한 폴링 및 이벤트를 올바르게 사용 해야 합니다.
   * 각 프레임을 렌더링 하는 **컨트롤러** 의 경우 응용 프로그램은 현재 프레임의 photon 시간에 대해 앞으로 예측 되는 컨트롤러에서 컨트롤러의 *GameObject* 위치를 지정 해야 합니다.  Unity 폴링 Api (예: XR)에서이 데이터를 가져옵니다 *[. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 또는 *[XR. WSA. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .
   * Press 또는 릴리스부터 **컨트롤러를 대상** 으로 하는 경우 앱은 해당 누르기 또는 릴리스 이벤트에 대 한 기록 컨트롤러의 포즈를 기준으로 궤적을 ray로 계산 해야 합니다.  *[InteractionManager InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 와 같은 Unity 이벤트 api에서이 데이터를 가져옵니다.
* **그립 포즈를 사용**합니다. 각도 속도와 속도는 포인터가 아닌 그립 포즈를 기준으로 보고 됩니다.

Throw는 향후 Windows 업데이트를 사용 하 여 계속 개선 되며 여기에서 자세한 정보를 찾을 수 있습니다.

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>MRTK v2의 제스처 및 동작 컨트롤러

입력 관리자에서 제스처 및 동작 컨트롤러에 액세스할 수 있습니다. 
* [MRTK v2의 제스처](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [MRTK v2의 동작 컨트롤러](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>자습서와 함께 수행

보다 자세한 사용자 지정 예제가 포함 된 단계별 자습서는 혼합 현실 아카데미에서 제공 됩니다.

- [MR 입력 211: 제스처](holograms-211.md)
- [MR 입력 213: 동작 컨트롤러](mixed-reality-213.md)

[![MR 입력 213-동작 컨트롤러](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 입력 213-동작 컨트롤러*

## <a name="see-also"></a>참고 항목

* [헤드 게이즈 및 커밋](gaze-and-commit.md)
* [모션 컨트롤러](motion-controllers.md)


