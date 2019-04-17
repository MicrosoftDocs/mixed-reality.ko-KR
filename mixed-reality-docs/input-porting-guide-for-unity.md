---
title: 포팅 가이드 Unity에 대 한 입력
description: Windows Mixed Reality Unity에 대 한 입력을 처리 하는 방법에 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 입력, unity, 이식
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602790"
---
# <a name="input-porting-guide-for-unity"></a>포팅 가이드 Unity에 대 한 입력

Windows Mixed Reality 여러 플랫폼에 걸쳐 있는 Unity의 일반 Input.GetButton/GetAxis Api 또는 Windows 관련 XR 두 가지 방법 중 하나를 사용 하기 위한 입력된 논리를 이식할 수 있습니다. WSA입니다. 입력된 Api에 맞게 다양 한 데이터를 제공 하는 컨트롤러 동작 및 HoloLens 전달 합니다.

## <a name="general-inputgetbuttongetaxis-apis"></a>일반 Input.GetButton/GetAxis Api

Unity에 대 한 입력을 노출 하는 일반 Input.GetButton/Input.GetAxis Api를 현재 사용 [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 하 고 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)합니다. 앱을 이미 사용 중인 이러한 Api 입력에 대 한 경우 Windows Mixed Reality에서 동작 컨트롤러를 지원 하기 위한 가장 쉬운 경로입니다: 단추 및 축 입력 관리자를 다시 매핑할 하기만 합니다.

자세한 내용은 참조 하세요. 합니다 [Unity 단추/축 매핑 테이블](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 하며 [일반적인 Unity Api 개요](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)합니다.

## <a name="windows-specific-xrwsainput-apis"></a>Windows-specific XR.WSA.Input APIs

앱에는 이미 각 플랫폼에 대 한 사용자 지정 입력된 논리 빌드를 하는 경우 아래에서 Windows 특정 공간 입력된 Api를 사용 하도록 선택할 수 있습니다 합니다 **UnityEngine.XR.WSA.Input** 네임 스페이스입니다. 이 기능을 사용 하면 위치 정확도 같은 추가 정보 또는 실습 및 컨트롤러 떨어져 HoloLens에 알릴 수 있도록 원본 유형, 액세스할 수 있습니다.

자세한 내용은 참조는 [UnityEngine.XR.WSA.Input Api 개요](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)합니다.

## <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 포인팅 포즈 비교

Windows Mixed Reality 다양 한 폼 팩터 동작 컨트롤러에서는, 각 컨트롤러의 디자인을 사용 하 여 렌더링할 때 가리키는 사용 해야 다른 사용자의 직접 위치 사이의 "전달" 방향 해당 앱의 자연 관계를 컨트롤러입니다.

잘 표현 하기 위해 이러한 컨트롤러, 두 가지 종류의 포즈 각 상호 작용 원본에 대해 조사할 수 있습니다.

* 합니다 **그립 포즈**, HoloLens, 감지한 손 모양 손바닥 또는 동작 컨트롤러를 보유 하는 손 안에서 가능 위치를 나타내는입니다.
    * 몰입 형 헤드셋이이 포즈 가장 사용 렌더링 **사용자의 직접** 또는 **사용자의 직접에 보관 된 개체**검 또는 총 등입니다.
    * 합니다 **위치를 잡고**: 물론 컨트롤러를 보유 하는 경우 팜 중심 왼쪽 또는 오른쪽 가운데 그립 내의 위치를 조정 합니다.
    * 합니다 **방향을 올바른 축 잡고**: 완전히 플랫 5 손가락 자세를 직접 열면 광선과 표준 프로그램 palm에서 (왼쪽된 palm, palm 오른쪽에서 이전 버전과에서 앞으로)
    * 합니다 **방향을 정방향 축 잡고**: 부분적으로 (처럼 컨트롤러 보유) 직접을 닫을 때, 광선을 가리키는 "forward" 튜브를 통해 비 엄지 손가락으로 구성 합니다.
    * 합니다 **축 위쪽 방향 잡고**: 오른쪽 정방향 정의 사용 권한에 포함 된 최대 축.
    * 그립 자세 하거나 Unity의 공급 업체 간 입력 API 통해 액세스할 수 있습니다 (**[xr 하이 있습니다. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)합니다. GetLocalPosition/Rotation**) 또는 Windows 관련 API를 통해 (**sourceState.sourcePose.TryGetPosition/Rotation**, 그립 포즈를 요청).
* 합니다 **포인터 포즈**, 앞으로 가리키는 컨트롤러의 끝을 나타내는입니다.
    * 이 포즈 raycast에 가장 적합 하면 **UI를 가리키는** 컨트롤러 모델 자체를 렌더링 하는 경우.
    * 현재 포인터 자세는 Windows 전용 API를 통해서만 사용할 수 있습니다 (**sourceState.sourcePose.TryGetPosition/Rotation**, 포인터 포즈를 요청).

이러한 자세 좌표 모든 Unity 영역 좌표에서 표시 됩니다.

## <a name="see-also"></a>참조
* [컨트롤러 동작](motion-controllers.md)
* [제스처와 Unity의 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [포팅 가이드](porting-guides.md)
