---
title: Unity에서 손실 추적
description: Unity 앱 내에서 손실 추적을 처리 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity를 손실 추적, 손실 이미지를 추적 합니다.
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602770"
---
# <a name="tracking-loss-in-unity"></a>Unity에서 손실 추적

장치를 찾을 수 없는 자체 세계에서 하는 경우 앱 "손실 추적"을 경험 했습니다. 기본적으로 Unity update 루프를 일시 중지 하 고 시작 화면 이미지를 사용자에 게 표시 됩니다. 추적 다시 설정 됨, 시작 이미지 사라지고 update 루프를 계속 합니다.

대신 사용자 설정을 옵트아웃 하 여 수동으로이 전환을 처리할 수 있습니다. 모든 콘텐츠는 아무런 조치를 처리 하는 경우 손실을 추적 하는 동안 잠금을 본문 될 것 같습니다.

## <a name="default-handling"></a>기본 처리 합니다.

기본적으로 앱 뿐만 아니라 모든 메시지 및 이벤트의 update 루프는 손실 추적의 기간 동안 중지 됩니다. 동시에 이미지를 사용자에 게 표시 됩니다. 편집으로 이동 하 여이 이미지를 사용자 지정할 수 있습니다-> 설정-선수, 시작 이미지를 클릭 하 고 손실 Holographic 추적 이미지 설정 >.

## <a name="manual-handling"></a>수동 처리

추적 손실을 수동으로 처리 하려면로 이동 해야 **편집할** > **프로젝트 설정** > **플레이어**  >   **유니버설 Windows 플랫폼 설정 탭** > **시작 이미지** > **Windows Holographic** "에서 추적 손실 일시 중지 및 이미지 표시를 선택 취소 ". 그런 다음 아래 지정 된 Api를 사용 하 여 변경 내용 추적을 처리 해야 합니다.

**Namespace:** *UnityEngine.XR.WSA*<br>
**형식:** *WorldManager*

* 추적 손실/얻은 검색할 이벤트를 노출 하는 전역 관리자 (*WorldManager.OnPositionalLocatorStateChanged*) 및 현재 상태를 쿼리 하는 속성 (*WorldManager.state*)
* 추적 상태가 활성 상태인 경우 카메라 사용자 변환도 가상 세계에서 변환할 표시 되지 않습니다. 즉, 개체는 모든 물리적 위치에 해당 더 이상 모든 본문 잠긴 나타납니다.

각 프레임 또는 핸들 state 속성에 대 한 폴링 해야 하거나 사용자 고유의에 변경 내용 추적을 처리 하는 경우는 *OnPositionalLocatorStateChanged* 이벤트입니다.

### <a name="polling"></a>폴링

가장 중요 한 상태가 *PositionalLocatorState.Active* 추적 완벽 하 게 작동 됨을 의미 합니다. 다른 상태로 주 카메라 회전 델타만 발생 합니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>OnPositionalLocatorStateChanged 이벤트 처리

구독할 수 또는 고 더 편리 하 게 *OnPositionalLocatorStateChanged* 의 변화를 처리 하려면:

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>참조
* [DirectX의 손실 추적 처리](coordinate-systems-in-directx.md#handling-tracking-loss)
