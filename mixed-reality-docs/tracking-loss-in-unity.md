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
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="9f42c-104">Unity에서 손실 추적</span><span class="sxs-lookup"><span data-stu-id="9f42c-104">Tracking loss in Unity</span></span>

<span data-ttu-id="9f42c-105">장치를 찾을 수 없는 자체 세계에서 하는 경우 앱 "손실 추적"을 경험 했습니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="9f42c-106">기본적으로 Unity update 루프를 일시 중지 하 고 시작 화면 이미지를 사용자에 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="9f42c-107">추적 다시 설정 됨, 시작 이미지 사라지고 update 루프를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="9f42c-108">대신 사용자 설정을 옵트아웃 하 여 수동으로이 전환을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="9f42c-109">모든 콘텐츠는 아무런 조치를 처리 하는 경우 손실을 추적 하는 동안 잠금을 본문 될 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="9f42c-110">기본 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-110">Default Handling</span></span>

<span data-ttu-id="9f42c-111">기본적으로 앱 뿐만 아니라 모든 메시지 및 이벤트의 update 루프는 손실 추적의 기간 동안 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="9f42c-112">동시에 이미지를 사용자에 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="9f42c-113">편집으로 이동 하 여이 이미지를 사용자 지정할 수 있습니다-> 설정-선수, 시작 이미지를 클릭 하 고 손실 Holographic 추적 이미지 설정 >.</span><span class="sxs-lookup"><span data-stu-id="9f42c-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="9f42c-114">수동 처리</span><span class="sxs-lookup"><span data-stu-id="9f42c-114">Manual Handling</span></span>

<span data-ttu-id="9f42c-115">추적 손실을 수동으로 처리 하려면로 이동 해야 **편집할** > **프로젝트 설정** > **플레이어**  >   **유니버설 Windows 플랫폼 설정 탭** > **시작 이미지** > **Windows Holographic** "에서 추적 손실 일시 중지 및 이미지 표시를 선택 취소 ".</span><span class="sxs-lookup"><span data-stu-id="9f42c-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="9f42c-116">그런 다음 아래 지정 된 Api를 사용 하 여 변경 내용 추적을 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="9f42c-117">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="9f42c-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="9f42c-118">**형식:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="9f42c-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="9f42c-119">추적 손실/얻은 검색할 이벤트를 노출 하는 전역 관리자 (*WorldManager.OnPositionalLocatorStateChanged*) 및 현재 상태를 쿼리 하는 속성 (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="9f42c-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="9f42c-120">추적 상태가 활성 상태인 경우 카메라 사용자 변환도 가상 세계에서 변환할 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="9f42c-121">즉, 개체는 모든 물리적 위치에 해당 더 이상 모든 본문 잠긴 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="9f42c-122">각 프레임 또는 핸들 state 속성에 대 한 폴링 해야 하거나 사용자 고유의에 변경 내용 추적을 처리 하는 경우는 *OnPositionalLocatorStateChanged* 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="9f42c-123">폴링</span><span class="sxs-lookup"><span data-stu-id="9f42c-123">Polling</span></span>

<span data-ttu-id="9f42c-124">가장 중요 한 상태가 *PositionalLocatorState.Active* 추적 완벽 하 게 작동 됨을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="9f42c-125">다른 상태로 주 카메라 회전 델타만 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="9f42c-126">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f42c-126">For example:</span></span>

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="9f42c-127">OnPositionalLocatorStateChanged 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="9f42c-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="9f42c-128">구독할 수 또는 고 더 편리 하 게 *OnPositionalLocatorStateChanged* 의 변화를 처리 하려면:</span><span class="sxs-lookup"><span data-stu-id="9f42c-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9f42c-129">참조</span><span class="sxs-lookup"><span data-stu-id="9f42c-129">See also</span></span>
* [<span data-ttu-id="9f42c-130">DirectX의 손실 추적 처리</span><span class="sxs-lookup"><span data-stu-id="9f42c-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
