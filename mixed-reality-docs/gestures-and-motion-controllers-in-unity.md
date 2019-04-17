---
title: 제스처와 Unity의 동작 컨트롤러
description: 두 가지 키에 응시 Unity, 손 제스처 및 동작 컨트롤러에 대해 작업을 수행 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 제스처 동작 컨트롤러, unity, 게이즈를 입력
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597655"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>제스처와 Unity의 동작 컨트롤러

두 가지 주요 작업을 수행할 사용자 [Unity에서 gaze](gaze-in-unity.md), [제스처를 전달](gestures.md) 하 고 [컨트롤러 동작](motion-controllers.md). Unity에서 동일한 Api를 통해 공간 입력의 두 원본에 대 한 데이터를 액세스 합니다.

Windows Mixed Reality를 일반적인에 대 한 공간 입력된 데이터에 액세스 하는 두 가지를 제공 하는 unity *Input.GetButton/Input.GetAxis* 여러 Unity xr 하이 Sdk에서 사용할 수 있는 Api 및 *InteractionManager / GestureRecognizer* 공간을 사용할 수 있는 입력된 데이터의 전체 집합을 노출 하는 Windows Mixed Reality로 특정 API.

## <a name="unity-buttonaxis-mapping-table"></a>Unity 단추/축 매핑 테이블

아래 표에 단추 및 축 Id를 통해 Windows Mixed Reality 동작 컨트롤러에 대 한 Unity의 입력 관리자에서 지원 됩니다 합니다 *Input.GetButton/GetAxis* Api에는 "Windows MR 별" 열 속성을 참조 하는 동안 으로 사용할 수는 *InteractionSourceState* 형식입니다. 이러한 각 Api는 아래 섹션에서 자세히 설명 되어 있습니다.

Windows Mixed Reality에 대 한 단추/축 ID 매핑을는 일반적으로 Oculus 단추/축 Id와 일치합니다.

Windows Mixed Reality에 대 한 단추/축 ID 매핑이 OpenVR의 매핑을 두 가지 방식에서에서 다릅니다.
1. 매핑을 스틱 및 터치 패드를 사용 하 여 컨트롤러를 지원 하기 위해 스틱 구별 된 터치 패드 Id를 사용 합니다.
2. 매핑을 A, X 단추를 해당 물리적 ABXY 단추에 사용할 수 있는 메뉴 단추에 대 한 Id를 오버 로드 하지 않습니다.

<table>
<tr>
<th rowspan="2">입력 </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">일반적인 Unity Api</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a><br />(XR.WSA.Input)</th>
</tr><tr>
<th> 왼쪽 위 </th><th> 오른쪽 위</th>
</tr><tr>
<td> 누른 선택 트리거 </td><td> Axis 9 = 1.0 </td><td> Axis 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> 트리거 아날로그 값 선택 </td><td> 축 9 </td><td> Axis 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 누른 부분적으로 트리거를 선택 </td><td> 단추 14 <i>(gamepad 호환성)</i> </td><td> 단추 15 <i>(gamepad 호환성)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> 메뉴 단추 누름 </td><td> 단추 6 * </td><td> 단추 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 그립 단추 누름 </td><td> 축 11 = 1.0 (아날로그 값 없음)<br />단추 4 <i>(gamepad 호환성)</i> </td><td> 축 12 = 1.0 (아날로그 값 없음)<br />단추 5 <i>(gamepad 호환성)</i> </td><td> 잡았습니다.</td>
</tr><tr>
<td> 엄지 스틱 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </td><td> 축 1 </td><td> 축 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> 엄지 스틱 Y <i>(위쪽:-1.0, 아래: 1.0)</i> </td><td> 축 2 </td><td> 축 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> 엄지 스틱 누름 </td><td> 단추 8 </td><td> 단추 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 터치 패드 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </td><td> 축 17 * </td><td> Axis 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> 터치 패드 Y <i>(위쪽:-1.0, 아래: 1.0)</i> </td><td> 축 18 * </td><td> 축 20 * </td><td> touchpadPosition.y</td>
</tr><tr>
<td> 작업 패드 </td><td> 단추 18 * </td><td> 단추 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 터치 패드 누름 </td><td> 단추 16 * </td><td> 단추 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 그립 포즈 또는 포인터 자세 </td><td colspan="2"> <i>그립</i> 만 초래 합니다. <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> 전달 <i>그립</i> 하거나 <i>포인터</i> 인수로: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 상태를 추적합니다. </td><td colspan="2"> <i>위치 정확성과 소스 손실 위험 MR 관련 API를 통해 에서만 사용할 수 있습니다</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>이러한 단추/축 Id 매핑에 Oculus 터치 및 OpenVR 게임 패드에서 사용 하는 충돌로 인해 OpenVR에 대 한 Unity를 사용 하는 Id에서 다릅니다.

## <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 포인팅 포즈 비교

Windows Mixed Reality 다양 한 폼 팩터 동작 컨트롤러에서는, 각 컨트롤러의 디자인을 사용 하 여 렌더링할 때 가리키는 사용 해야 다른 사용자의 직접 위치 사이의 "전달" 방향 해당 앱의 자연 관계를 컨트롤러입니다.

이러한 컨트롤러를 더 잘 나타내기 위해 두 가지 종류의 포즈 각 상호 작용 원본에 대해 조사할 수 있습니다는 **그립 자세** 하며 **포인터 자세**합니다. 그립 자세 및 포인터 포즈 좌표 두 전역 Unity 영역 좌표에서 모든 Unity Api가 표시 됩니다.

### <a name="grip-pose"></a>그립 자세

합니다 **그립 포즈** 는 HoloLens 감지한 손 모양 손바닥 또는 동작 컨트롤러 보유 palm의 위치를 나타냅니다.

몰입 형 헤드셋 그립 포즈 가장 사용 렌더링 **사용자의 직접** 또는 **사용자의 직접에 보관 된 개체**검 또는 총 등입니다. 그립 자세는으로 동작 컨트롤러를 시각화 하는 경우에 사용 됩니다 합니다 **렌더링 가능한 모델** 제공 동작에 대 한 Windows에서 컨트롤러는 원본 및 회전 중심으로 그립 포즈를 사용 합니다.

그립 자세는 특히 다음과 같이 정의 됩니다.
* 합니다 **위치를 잡고**: 물론 컨트롤러를 보유 하는 경우 팜 중심 왼쪽 또는 오른쪽 가운데 그립 내의 위치를 조정 합니다. Windows Mixed Reality 동작 컨트롤러에서이 위치는 일반적으로 감각을 단추를 사용 하 여 맞춥니다.
* 합니다 **방향을 올바른 축 잡고**: 완전히 플랫 5 손가락 자세를 직접 열면 광선과 표준 프로그램 palm에서 (왼쪽된 palm, palm 오른쪽에서 이전 버전과에서 앞으로)
* 합니다 **방향을 정방향 축 잡고**: 부분적으로 (처럼 컨트롤러 보유) 직접을 닫을 때, 광선을 가리키는 "forward" 튜브를 통해 비 엄지 손가락으로 구성 합니다.
* 합니다 **축 위쪽 방향 잡고**: 오른쪽 정방향 정의 사용 권한에 포함 된 최대 축.

그립 자세 하거나 Unity의 공급 업체 간 입력 API 통해 액세스할 수 있습니다 (*[xr 하이 있습니다. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)합니다. GetLocalPosition/Rotation*) 또는 Windows MR 관련 API를 통해 (*sourceState.sourcePose.TryGetPosition/Rotation*, 요청에 대 한 데이터를 초래 합니다 **그립** 노드).

### <a name="pointer-pose"></a>포인터 자세

합니다 **포인터 포즈** 앞으로 가리키는 컨트롤러의 끝을 나타냅니다.

시스템 제공 포인터 자세는 raycast 했으면 **컨트롤러 모델 자체 렌더링**합니다. 일부 가상 건, 같은 컨트롤러 대신 다른 가상 개체를 렌더링 하는 경우 총 앱 정의 모델의 barrel 함께 전송 되는 ray 같은 가상 개체에 대 한 가장 자연 스러운 광선을 사용 하 여 가리켜야 합니다. 사용자가 가상 개체와 실제 컨트롤러 하지에서 볼 수 있으므로 가상 개체를 사용 하 여 가리키는 가능성이 됩니다 앱을 사용 하는 더 자연 스러운.

현재 포인터 자세는 Unity는 Windows MR 관련 API 통해서만 사용할 수 있습니다 *sourceState.sourcePose.TryGetPosition/Rotation*전달 *InteractionSourceNode.Pointer* 으로 인수입니다.

## <a name="controller-tracking-state"></a>컨트롤러 상태를 추적

헤드셋와 같은 Windows Mixed Reality 동작 컨트롤러 설정이 필요 하지 않습니다 외부 추적 센서입니다. 대신, 컨트롤러 자체 헤드셋의 센서에서 추적 됩니다.

사용자가 헤드셋의 필드의 보기 컨트롤러를 이동 하면 대부분의 경우에서 Windows 계속 컨트롤러 위치를 유추 하 고 앱을 제공 합니다. 경우 컨트롤러 근사치 정확도 위치로 컨트롤러의 위치는 삭제 하는 충분 한 시간에 대 한 추적 visual 끊어졌습니다.

이 시점에서 시스템 얼굴이 움직일, 여전히 해당 내부 방향 센서를 사용 하 여 컨트롤러의 true 방향을 노출 하는 동안 사용자의 위치를 추적 하는 사용자에 게 컨트롤러 본문 잠금을 됩니다. 컨트롤러를 사용 하 고 UI 요소를 활성화 하는 많은 앱은 사용자 알아채지 않으면 서의 대략적인 정확도 정상적으로 작동할 수 있습니다.

이 대해 가장 좋은 방법은 직접 시도해 볼 경우 컨트롤러 동작을 사용 하 여 추적의 다양 한 상태에서 작동 하는 몰입 감이 뛰어난 콘텐츠 예제를 사용 하 여이 비디오를 확인해 보십시오.

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>상태를 명시적으로 추적 하는 방법에 대 한 추론

위치 추적 상태에 따라 다르게 처리 하려는 앱 수 더 나아가 같은 컨트롤러의 상태에 대 한 속성을 검사할 *SourceLossRisk* 하 고 *PositionAccuracy*:

<table>
<tr>
<th> 상태를 추적합니다. </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>높은 정확도</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>높은 정확도 (손실의 위험이)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>대략적인 정확도</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 대략 일치 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>위치가 없습니다</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 대략 일치 </td><td style="background-color: orange"> false</td>
</tr>
</table>

이러한 동작 컨트롤러 추적 상태는 다음과 같이 정의 됩니다.
* **높은 정확도 경우:** 동작 컨트롤러 헤드셋의 뷰 필드 내에 있는 동안 정확도 높은 위치, visual 추적에 따라 일반적으로 제공 됩니다. 참고는 컨트롤러를 이동 하는 일시적으로 보기의 필드를 벗어나거나 헤드셋 센서에서 일시적으로 가려지는지 (예: 사용자의 반면) 기반 컨트롤러의 관성 추적으로 짧은 시간에 대 한 정확도 높은 포즈 반환할 계속 자체입니다.
* **높은 정확도 (손실의 위험이):** 사용자 헤드셋의 뷰 필드의 가장자리를 넘어 동작 컨트롤러를 움직이면 헤드셋 곧 없게 됩니다 컨트롤러의 위치를 시각적으로 추적할 수 있습니다. 앱 경우 컨트롤러에 도달이 FOV 경계 확인 하 여 알고 합니다 **SourceLossRisk** 1.0에 도달 합니다. 이 시점에서 앱 꾸준하게 매우 고품질 발생 해야 하는 컨트롤러 제스처를 일시 중지 하도록 선택할 수 있습니다.
* **대략적인 정확도:** 경우 컨트롤러 근사치 정확도 위치로 컨트롤러의 위치는 삭제 하는 충분 한 시간에 대 한 추적 visual 끊어졌습니다. 이 시점에서 시스템 얼굴이 움직일, 여전히 해당 내부 방향 센서를 사용 하 여 컨트롤러의 true 방향을 노출 하는 동안 사용자의 위치를 추적 하는 사용자에 게 컨트롤러 본문 잠금을 됩니다. 컨트롤러를 사용 하 고 UI 요소를 활성화 하는 많은 앱 사용자 알아채지 않으면 서 일반 while로 대략적인 정확도 작동할 수 있습니다. 라우터로도 충분 입력된 요구 사항이 있는 앱에서이 삭제 감지 하도록 선택할 수 있습니다 **높은** 정확도 **근사치** 검사 하 여 정확도 **PositionAccuracy** 속성에 대 한 사용자에 게 더 넓은 hitbox 오프 스크린 대상에서이 시간 동안 예입니다.
* **위치가 없습니다.** 컨트롤러는 오랜 시간 동안 대략적인 정확도에서 작동할 수 있습니다, 있지만 때로는 시스템 임을 알고 있습니다 본문 잠긴 위치도 하지 의미 있는 지금은. 예를 들어 방금 설정 하는 컨트롤러 수 하지 관찰 한 시각적으로 또는 사용자가 다음 다른 사용자가 선택 하는 컨트롤러 작성 될 수 있습니다. 시스템에서 해당 시간에 앱에 그 위치를 제공 하지 것입니다 하 고 *TryGetPosition* false를 반환 합니다.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>일반적인 Unity Api (Input.GetButton/GetAxis)

**Namespace:** *UnityEngine*, *UnityEngine.XR*<br>
**형식**: *Input*, *XR.InputTracking*

현재 사용 하 여 일반적인 unity *Input.GetButton/Input.GetAxis* 에 대 한 입력을 노출 하는 Api [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)를 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 및 Windows Mixed Reality 포함 실습 및 동작 컨트롤러입니다. 입력에 대 한 이러한 Api를 사용 하는 앱을 하는 경우 Windows Mixed Reality를 비롯 한 여러 xr 하이 Sdk에서 동작 컨트롤러 쉽게 지원할 수 있습니다.

### <a name="getting-a-logical-buttons-pressed-state"></a>논리 단추의 누름된 상태 가져오기

일반 Unity 입력 Api를 사용 하려면 일반적으로 먼저 단추 및 축의 논리적 이름으로 마무리 합니다 [Unity 입력 관리자](https://docs.unity3d.com/Manual/ConventionalGameInput.html), 각 이름에는 단추 또는 축 Id 바인딩. 그런 다음 해당 논리 단추/축 이름을 참조 하는 코드를 작성할 수 있습니다.

예를 들어 왼쪽된 동작 컨트롤러의 트리거 단추 전송 작업에 매핑할로 이동 **편집 > 프로젝트 설정 > 입력** Unity 내에서 축 제출 섹션의 속성을 확장 합니다. 변경 된 **양의 단추** 또는 **Alt 양의 단추** 읽을 속성 **조이스틱 단추 14**, 다음과 같은:

![Unity's InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

스크립트에 다음 사용 하 여 전송 작업에 대 한 확인해 *Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
변경 하 여 더 많은 논리 단추를 추가할 수 있습니다 합니다 **크기** 아래에서 속성 **축**합니다.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>직접 물리적 단추 누름된 상태 가져오기

해당 정규화 하 여 단추를 수동으로 액세스할 수도 있습니다 사용 하 여 이름을 *Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>손 모양 받거나 동작 컨트롤러 자세

위치 및 컨트롤러의 회전을 액세스할 수 있습니다 사용 하 여 *xr 하이 있습니다. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

참고가 컨트롤러의 그립 포즈 (사용자 보유 컨트롤러)에 검 또는 총 사용자의 직접 또는 컨트롤러 자체의 모델을 렌더링 하는 데 유용 합니다.

컨트롤러에서이 그립 포즈 포인터 포즈 (컨트롤러의 팁을 가리키는 위치)와 관계 다는 참고 합니다. 이 시점에서 컨트롤러의 포인터 포즈 액세스 가능성이 MR 관련 입력 아래 섹션에 설명 된 API 통해 있습니다.

## <a name="windows-specific-apis-xrwsainput"></a>Windows 관련 Api (xr 하이 있습니다. WSA입니다. 입력)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**형식**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

(HoloLens)에 대 한 Windows Mixed Reality 직접 입력 하 고 동작 컨트롤러에 대 한 자세한 정보를 가져오려면 아래 Windows 관련 공간 입력된 Api를 사용 하도록 선택할 수 있습니다 합니다 *UnityEngine.XR.WSA.Input* 네임 스페이스입니다. 이 기능을 사용 하면 위치 정확도 같은 추가 정보 또는 실습 및 컨트롤러 간격을 알 수 있도록 원본 유형, 액세스할 수 있습니다.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>실습 및 동작 컨트롤러의 상태에 대 한 폴링

이 프레임 상태 사용 하 여 각 상호 작용 (직접 또는 동영상 컨트롤러) 원본에 대해 폴링하면 합니다 *GetCurrentReading* 메서드.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

각 *InteractionSourceState* 얻게 백 현재 시점에서 상호 작용 원본을 나타냅니다. 합니다 *InteractionSourceState* 와 같은 정보를 노출 합니다.
* [누름 유형의](motion-controllers.md) (선택/메뉴/한결/터치 패드/엄지 스틱) 발생 하는

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 다른 데이터 컨트롤러 동작, 이러한는 터치 패드 및/또는 엄지 스틱의 XY 좌표 및 관련 작업된 상태

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* 원본 손 모양 또는 동작 컨트롤러 인지 알아야 InteractionSourceKind

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>정방향 예측 렌더링 동작에 대 한 폴링

* 실습 및 컨트롤러의 상호 작용 원본 데이터에 대 한 폴링 얻게 발생 시점은이 프레임 photons 사용자의 눈에 도달 하면에 대 한 정방향 예측 발생 됩니다.  이러한 정방향 예측 발생에 가장 적합 **렌더링** 컨트롤러 또는 보유 한 각 프레임 개체입니다.  지정 된 키를 눌러 대상으로 하거나 컨트롤러를 사용 하 여 릴리스 하는 경우 기록 이벤트 아래에서 설명 하는 Api를 사용 하는 경우 가장 정확 하 게 됩니다.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 또한 현재이 프레임에 대 한 정방향 예측 머리 포즈를 가져올 수 있습니다.  그대로 원본 자세를 사용 하 여이 대 한 유용한 **렌더링** 커서에 지정 된 키를 눌러 또는 릴리스 기록 이벤트 아래에서 설명 하는 Api를 사용 하는 경우 가장 정확 하 게 됩니다.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>원본 이벤트를 상호 작용 하는 처리

입력된 이벤트를 정확 하 게 기록 포즈 데이터를 사용 하 여 즉시 처리를 폴링하는 대신 소스 이벤트를 상호 작용을 처리할 수 있습니다.

이벤트를 처리 하려면 상호 작용 원본:
* 등록 된 *InteractionManager* 입력된 이벤트입니다. 관심 있는 상호 작용 이벤트의 각 형식에 대해 구독 해야 합니다.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* 이벤트를 처리 합니다. 상호 작용 이벤트에 가입한 후에 해당 하는 경우 콜백을 받을 수 있습니다. 에 *SourcePressed* 예제에서는 이러한 될 수 있으며 원본 감지 된 후 해제 되거나 손실 되기 전에 합니다.

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

더 이상에 관심이 이벤트 또는 이벤트에 등록 된 개체를 제거 하는 경우의 이벤트 처리를 중지 해야 합니다. 이벤트 처리를 중지 하려면 이벤트에서 취소 합니다.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>원본 이벤트를 상호 작용의 목록

사용 가능한 상호 작용 원본 이벤트 다음과 같습니다.
* *InteractionSourceDetected* (원본 활성화)
* *InteractionSourceLost* (비활성 됨)
* *InteractionSourcePressed* (탭, 단추 누름 또는 "Select" 마냥 마음이 들 뜹니다)
* *InteractionSourceReleased* (탭, 단추를 놓았음을, 또는 "Select" 마냥 마음이 들 뜹니다 끝의 끝)
* *InteractionSourceUpdated* (이동 또는 그렇지 않은 경우 일부 상태 변경)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>키를 눌러 또는 릴리스 가장 정확 하 게 일치 하는 기록 대상 발생에 대 한 이벤트

앞에서 설명한 폴링 Api 앱 포즈 정방향 예측을 제공 합니다.  이러한 예측된 포즈 컨트롤러나 가상 핸드헬드 개체 렌더링에 가장 적합 한 중일에 향후 발생은 두 가지 주요 이유를 대상으로 적합 하지 않습니다.
* 컨트롤러에서 단추를 누를 때 있을 수 있습니다 무선 대기 시간이 약 20ms Bluetooth를 통한 시스템 눌러를 받기 전에 합니다.
* 다음 사용 중인 경우 정방향 예측 포즈를 가지는 정방향 예측의 다른 10 20ms 적용할 현재 프레임의 photons 사용자의 눈에 도달 하면 시간을 대상으로 합니다.

즉, 폴링 하면 원본 자세 하거나 헤드 즉 30 40ms 정방향 여기서 사용자의 헤드 및 실습 실제로 된 키를 눌러 또는 릴리스 발생 했을 때 다시에서 발생할 합니다.  HoloLens 직접 입력에 대 한 지연 시간 없이 무선 전송 중일 있습니다 눌러 검색할 유사한 처리 지연이 됩니다.

직접 또는 컨트롤러 press에서 사용자의 원래 의도에 따라 대상을 정확 하 게 사용 해야는 머리 포즈를 기록 원본 포즈 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 입력된 이벤트입니다.

눌러 대상 또는 사용자의 헤드 또는 해당 컨트롤러의 기록 포즈 데이터로 릴리스 수 있습니다.:
* 에 사용할 수 있는 시점에 제스처 또는 컨트롤러 누르면 머리 포즈 발생 **대상** 사용자가 무엇을 확인 하려면 [gazing](gaze.md) 에서:

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

* 에 사용할 수 있는 시점에 동작 컨트롤러를 누르면 원본 포즈 발생 **대상** 어떤 사용자가 가리키는에서 컨트롤러를 확인 하려면.  눌러 발생 하는 컨트롤러의 상태가 됩니다.  컨트롤러 자체를 렌더링 하는 경우에 어떤 사용자가는 것이 좋습니다 컨트롤러를 렌더링 하는 자연 스러운 끝에서 대상 광선의 문제를 해결 하는 그립 자세 하지 않고 포인터 자세를 요청할 수 있습니다.

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

### <a name="event-handlers-example"></a>이벤트 처리기 예제

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>높은 수준의 복합 제스처 (GestureRecognizer) Api

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**형식**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

앱 공간 입력된 소스를 누르기, 보류, 조작 및 탐색 제스처에 대 한 높은 수준의 복합 제스처를 인식할 수도 있습니다. 둘 사이에서 이러한 복합 제스처를 인식할 수 있습니다 [바늘](gestures.md) 하 고 [컨트롤러 동작](motion-controllers.md) 는 GestureRecognizer를 사용 하 여 합니다.

각 제스처 이벤트에는 GestureRecognizer 타기 팅 헤드 광선 뿐만 아니라 입력에 대 한 이벤트 시는 SourceKind를 제공합니다. 일부 이벤트는 특정 추가 컨텍스트 정보를 제공합니다.

제스처 인식기를 사용 하 여 제스처를 캡처하는 데 필요한 몇 가지 단계만 가지
1. 새 제스처 인식기를 만들려면
2. 조사 하는 제스처를 지정 합니다.
3. 이러한 제스처에 대 한 이벤트 구독
4. 제스처를 캡처하기 시작

### <a name="create-a-new-gesture-recognizer"></a>새 제스처 인식기를 만들려면

사용 하는 *GestureRecognizer*을 만들어야 합니다를 *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>조사 하는 제스처를 지정 합니다.

제스처는 관심을 통해 지정 *SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>이러한 제스처에 대 한 이벤트 구독

관심이 있다면 제스처에 대 한 이벤트를 구독 합니다.

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
>탐색 및 조작 제스처 인스턴스에서 상호 배타적인를 *GestureRecognizer*합니다.

### <a name="start-capturing-gestures"></a>제스처를 캡처하기 시작

기본적으로 *GestureRecognizer* 까지 입력을 모니터링 하지 않습니다 *StartCapturingGestures()* 라고 합니다. 후 제스처 이벤트를 발생할 수 있기 *StopCapturingGestures()* 입력 프레임 하기 전에 수행 된 경우 호출 됩니다. 여기서 *StopCapturingGestures()* 처리 되었습니다. 합니다 *GestureRecognizer* 여부를 때 또는 해제 하는 제스처 실제로 발생 한 previou 프레임 따라서 시작 하려면 신뢰할 수 있는 것 및 대상 지정이 프레임 응시에 따라 중지 제스처 모니터링에 저장 됩니다.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>제스처를 캡처를 중지합니다

제스처 인식을 중지 합니다.

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>제스처 인식기를 제거합니다.

제거 하기 전에 이벤트 구독된에서 구독을 취소 하는 *GestureRecognizer* 개체입니다.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Unity의 동작 컨트롤러 모델 렌더링

![동작 컨트롤러 모델 및 텔레포트](images/motioncontrollertest-teleport-1000px.png)<br>
*동작 컨트롤러 모델 및 텔레포트*

렌더링 되는 실제 컨트롤러 보유 하 고 다양 한 단추를 누를 때 표현 하는 사용자가 일치 하는 앱에서 동작 컨트롤러를 사용할 수 있습니다 합니다 **MotionController prefab** 에 [혼합 현실 도구 키트 ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  이 prefab 시스템의 설치 동작 컨트롤러 드라이버에서 런타임 시 올바른 glTF 모델을 동적으로 로드합니다.  이러한 모델을 동적으로 로드 해야 것이 아니라 가져와 수동으로 편집기에서 앱 표시 되도록 모든 현재 및 미래의 컨트롤러에 대 한 3D 모델을 물리적으로 정확 하 게 사용자가 있을 수 있습니다.

1. 수행 합니다 [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 혼합 현실 도구 키트를 다운로드 하 여 Unity 프로젝트에 추가 하는 지침입니다.
2. 사용 하 여 카메라를 대체 하는 경우는 *MixedRealityCameraParent* prefab 준비가 시작 단계 중 일부로!  해당 prefab 컨트롤러 렌더링 동작을 포함합니다.  추가 고, 그렇지 *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* 프로젝트 창에서 장면에 있습니다.  부모 개체의 자식으로 prefab 사용 하는 경우 카메라를 이동 하려면 추가 하는 것이 좋습니다 장면 내 사용자 텔레포트 시킵니다 컨트롤러 사용자와 함께 제공 되도록 합니다.  앱에 텔레포트과 관련이 없는 prefab 장면의 루트에 추가 하면 됩니다.

## <a name="throwing-objects"></a>개체를 throw합니다.

어려운 문제는 가상 현실에서 개체를 throw 되 고 처음 보입니다. 실제로 가장 기반된 조작, 예기치 않은 방식으로 게임 역할에서 throw 할 때와 마찬가지로 갈피 이며 집중 교육을 중단 합니다. 고려할 어느 정도의 시간이 필요 throwing 실제로 올바른 동작을 나타내며를 공유 하고자 하는 우리의 플랫폼에 대 한 업데이트를 통해 사용 하도록 설정 하는 몇 가지 지침, 개발 하는 방법에 대 한 긴밀 하 게 투자 있어야 했습니다.

throw를 구현 하려면 권장 방법의 예제를 찾을 수 있습니다 [여기](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)합니다. 이 샘플이 네 가지 지침을 따릅니다.
* **컨트롤러를 사용할 *속도* 위치 대신**합니다. Windows 11 월 업데이트에서 변경 된 동작을 도입 했습니다 때 합니다 [위치 추적 상태를 ' 근사치'](motion-controllers.md#controller-tracking-state)합니다. 이 상태에서는 컨트롤러에 대 한 속도 정보는 종종 위치 높은 정확도 유지 하는 보다 더 높은 정확도 것으로 보고 됩니다 계속 됩니다.
* **통합 된 *각도 속도* 컨트롤러의**합니다. 이 논리에 포함 된 모든 합니다 `throwing.cs` 파일을 `GetThrownObjectVelAngVel` 위에 링크 된 패키지 내에서 정적 메서드:
   1. 각도 속도 절약 됩니다으로 throw 된 개체를 throw 하는 시점에 있었던 것과 동일한 angular 개발 속도 유지 해야 합니다. `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 으로 throw 된 개체의 대용량의 중심 그립 포즈의 원점에 가능성이 된 다양 한 속도 컨트롤러의 사용자의 참조 프레임에서에서 가능성이 있습니다. 이러한 방식으로 제공 하는 개체의 개발 속도의 부분은 컨트롤러 원점에서 throw 된 개체의 대용량의 중심의 즉각적인 탄젠트 속도입니다. 탄젠트 속도가이 컨트롤러 원점에서 throw 된 개체의 대용량의 중심 사이의 거리를 나타내는 벡터를 사용 하 여 컨트롤러의 angular 개발 속도의 교차곱을 보여 줍니다.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. Throw 된 개체의 총 속도 따라서 컨트롤러의 개발 속도 및이 탄젠트 속도의 합입니다. `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **주의를 기울여야 합니다 *시간* 속도는 적용**합니다. 단추를 누를 때 운영 체제에 Bluetooth를 통해 버블 업 이벤트에 대 한 최대 20ms 걸릴 수 있습니다. 즉,에서 컨트롤러 상태 변경에 대 한 폴링 누르지 하기 위해 누르는 경우 그 반대의 경우이 사용 하 여 얻을 수 있는 컨트롤러 포즈 정보 되는 사전 상태에서이 변경 됩니다. 또한이 폴링 API에서 제공 되는 컨트롤러 포즈 자세한 다음 20ms를 나중에 될 수 있는 프레임을 표시할 때 가능성이 포즈를 반영 하기 위해 앞으로 예측 됩니다. 좋은 점 *렌더링* 개체를 보유 하지만 시간 문제에 대 한 않았을 *대상으로 하* 개체 잠시 궤적 계산 사용자 출시가 throw 합니다. 다행 스럽게도 때 Unity 이벤트 11 월 업데이트를 사용 하 여 *InteractionSourcePressed* 또는 *InteractionSourceReleased* , 전송 상태 기록 포즈 데이터가 포함 됩니다 때 백 단추 실제로 누름 이거나 출시 되었습니다.  가장 정확한 컨트롤러 렌더링 및 throw 하는 동안 대상으로 컨트롤러를 얻으려면 올바르게 사용 해야 폴링 및 이벤트를 적절 하 게 합니다.
   * 에 대 한 **컨트롤러 렌더링** 각 프레임을 앱에 컨트롤러의 배치 해야 *GameObject* 정방향 예측 컨트롤러에서 현재 프레임의 photon 시간 위한 포즈 합니다.  Unity와 같은 폴링 Api에서에서이 데이터를 가져올 *[xr 하이 있습니다. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 하거나  *[xr 하이 있습니다. WSA입니다. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* 합니다.
   * 에 대 한 **컨트롤러를 대상으로 하** 누르거나 릴리스 시 앱 raycast 해야 하 고 해당 키를 눌러 또는 릴리스 이벤트에 대 한 기록 컨트롤러 포즈 기반 궤적을 계산 합니다.  같은 Unity 이벤트 Api에서에서이 데이터를 가져올  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 합니다.
* **그립 자세를 사용 하 여**입니다. 각도 속도 및 개발 속도 포인터 자세 하지 그립 자세를 기준으로 보고 됩니다.

향후 Windows 업데이트로 향상 계속를 throw 하 고 여기에서 자세한 내용을 보려면 예상할 수 있습니다.

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>혼합 현실 도구 키트를 사용 하 여 개발 가속화

두 예제에서는 장면 InputManager 및 Unity에서 MotionController에 대 한 가지가 있습니다. 이러한 작업을 통해 MRTK의 InputManager를 사용 하 여 동작 컨트롤러 단추에서 이벤트를 처리 하는 데이터에 액세스 하는 방법을 알아볼 수 있습니다.

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [기술 세부 정보 추가 정보 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![MRTK의 예에서는 내부에서를 입력 합니다.](images/MRTK_ExampleScene_Input.png)<br>
*MRTK의 예에서는 내부에서를 입력 합니다.*

### <a name="automatic-scene-setup"></a>장면 자동 설치

가져올 때 [MRTK Unity 패키지를 릴리스](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) 에서 프로젝트를 복제 또는 합니다 [GitHub 리포지토리](https://github.com/Microsoft/MixedRealityToolkit-Unity), Unity에서 새 메뉴 ' 혼합 현실 Toolkit'를 찾을 것입니다. '구성' 메뉴 아래에서 적용 혼합 현실 장면 [설정] 메뉴를 표시 됩니다. 기본 카메라를 제거 하 고 기본 구성 요소 추가 클릭 하면 [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)하십시오 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), 및 [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)합니다.

![장면 설치용 MRTK 메뉴](images/MRTK_Input_Menu.png)<br>
*장면 설치용 MRTK 메뉴*

![MRTK 자동 장면 설치](images/MRTK_HowTo_Input1.png)<br>
*MRTK 자동 장면 설치*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefab

프로젝트 패널에서 수동으로 추가할 수 있습니다. Prefabs로 이러한 구성 요소를 찾을 수 있습니다. 검색 하는 경우 **MixedRealityCamera**, 두 개의 다른 카메라 prefabs 참조 할 수 있습니다. 차이점은 **MixedRealityCamera** 전용인 카메라 prefab 반면 **MixedRealityCameraParent** 텔레포트, 동작 등 몰입 형 헤드셋에 대 한 추가 구성 요소를 포함 합니다. 컨트롤러를 경계입니다.

![MRTK에서 카메라 prefabs](images/MRTK_HowTo_Input2.png)<br>
*MRTK에서 카메라 prefabs*

**MixedRealtyCamera** HoloLens 및 몰입 형 헤드셋을 모두 지원 합니다. 장치 유형을 검색 하 고 플래그 지우기 등 Skybox 속성 최적화 합니다. 다음 사용자 지정 커서 동작 컨트롤러 모델 같은 사용자 지정 하는 Floor 유용한 속성 중 일부를 찾을 수 있습니다.

![커서 및 Floor 동작 컨트롤러에 대 한 속성](images/MRTK_HowTo_Input3.png)<br>
*커서 및 Floor 동작 컨트롤러에 대 한 속성*

## <a name="follow-along-with-tutorials"></a>자습서를 따라

혼합 현실 아카데미에서 사용할 수 있는 자세한 사용자 지정 예제를 사용한 단계별 자습서 같습니다.

- [MR 입력 211: 제스처](holograms-211.md)
- [MR 입력 213: 컨트롤러 동작](mixed-reality-213.md)

[![MR 입력 213-컨트롤러 동작](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 입력 213-컨트롤러 동작*

## <a name="see-also"></a>참조

* [제스처](gestures.md)
* [컨트롤러 동작](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [InteractionInputSource.cs MixedRealityToolkit Unity에서](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
