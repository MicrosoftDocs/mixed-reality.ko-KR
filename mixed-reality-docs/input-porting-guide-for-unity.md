---
title: Unity 용 입력 포팅 가이드
description: Unity에서 Windows Mixed Reality의 입력을 처리 하는 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 입력, unity, 포팅
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515491"
---
# <a name="input-porting-guide-for-unity"></a>Unity 용 입력 포팅 가이드

Unity의 일반 입력의 두 방법 중 하나를 사용 하 여 입력 논리를 Windows Mixed Reality로 이식할 수 있습니다. 여러 플랫폼에 걸쳐 있는 GetButton/Getbutton Api 또는 Windows 별 XR. WSA. 동작 컨트롤러 및 HoloLens 바늘에 대해 구체적으로 다양 한 데이터를 제공 하는 입력 Api

## <a name="general-inputgetbuttongetaxis-apis"></a>일반 입력. GetButton/Getbutton Api

Unity는 현재 일반 입력을 사용 합니다. GetButton/Input. Getbutton Api를 사용 하 여 [Oculus sdk](https://docs.unity3d.com/Manual/OculusControllers.html) 및 [openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)의 입력을 노출 합니다. 앱이 입력에 이러한 Api를 이미 사용 하 고 있는 경우 Windows Mixed Reality에서 동작 컨트롤러를 지원 하기에 가장 쉬운 경로입니다. 입력 관리자에서 단추와 축을 다시 매핑해야 합니다.

자세한 내용은 [unity 단추/축 매핑 표](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 및 [일반적인 unity api 개요](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)를 참조 하세요.

## <a name="windows-specific-xrwsainput-apis"></a>Windows 관련 XR. WSA. 입력 Api

앱에서 각 플랫폼에 대 한 사용자 지정 입력 논리를 이미 빌드하는 경우 **XR** 네임 스페이스에서 Windows 관련 공간 입력 api를 사용 하도록 선택할 수 있습니다. 이렇게 하면 위치 정확도 나 원본 종류와 같은 추가 정보에 액세스할 수 있으므로 HoloLens와 컨트롤러를 따로 지시할 수 있습니다.

자세한 내용은 [UnityEngine. XR api 개요](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)를 참조 하세요.

## <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 및 포인팅 포즈

Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 하며, 각 컨트롤러의 디자인이 사용자의 손 위치와 앱에서 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다. controller.

이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스에 대해 조사할 수 있는 두 가지 종류의 포즈가 있습니다.

* HoloLens에서 감지 된 손바닥의 위치 또는 이동 컨트롤러를 보유 하는 야자수의 위치를 나타내는 **그립 포즈**입니다.
    * 모던 헤드셋에서는이 포즈를 사용 하 여 사용자 **의 손을** 나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다.
    * **그립 위치**: 중심 컨트롤러를 자연스럽 게 사용할 때 왼쪽 또는 오른쪽으로 조정 하 여 그립 내에서 위치를 가운데에 맞춥니다.
    * **그립 방향의 오른쪽 축입니다**. 손을 완전히 열어 평평한 5 손가락 포즈를 형성 하는 경우 야자나무 (왼쪽 야자나무에서 전방, 오른쪽 팜)에 있는 광선
    * **그립 방향의 앞 축**: 컨트롤러를 보유 하 고 있는 것 처럼 부분적으로 닫는 경우 엄지 단추가 아닌 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.
    * **그립 방향의 위쪽 축입니다**. 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.
    * Unity의 교차 공급 업체 입력 API (XR)를 통해 그립 포즈에 액세스할 수 있습니다 **[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) 또는 Windows 특정 API (**sourcestate/Rotation**, 그립 포즈 요청)를 통해
* 앞에 있는 컨트롤러의 팁을 나타내는 **포인터가 포즈**입니다.
    * 이 포즈는 컨트롤러 모델 자체를 렌더링할 때 **UI를 가리킬** 때 raycast에 가장 잘 사용 됩니다.
    * 현재 포인터 포즈는 Windows 관련 API (**Sourcestate/Rotation**, 포인터 포즈 요청)를 통해서만 사용할 수 있습니다.

이러한 포즈 좌표는 모두 Unity 세계 좌표로 표현 됩니다.

## <a name="see-also"></a>참조
* [모션 컨트롤러](motion-controllers.md)
* [Unity의 제스처 및 모션 컨트롤러](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 추적](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [포팅 가이드](porting-guides.md)
