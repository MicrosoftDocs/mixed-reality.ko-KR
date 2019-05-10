---
title: 응시 및 유지
description: 응시 및 지속 입력된 모델 개요
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: 혼합 현실을 응시, 유지, 상호 작용 디자인
ms.openlocfilehash: d99180b6eb278eb6d7bf322c01a1c7cceb7fad1f
ms.sourcegitcommit: a4a53e6772805d89a47588857e3e8fb1fd8d9710
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469060"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="8daf4-104">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="8daf4-104">Gaze and dwell</span></span>

<span data-ttu-id="8daf4-105">실습, 도구 및 파트를 사용 하 여 꽉 찼을 때 tedious 어렵거나 제스처 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="8daf4-106">음성 명령, 제스처 같은 과도 하 게 큰 조건 예를 들어 상황에 맞게 신뢰할 수 있는 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="8daf4-107">또한 컨트롤 컴퓨터에 음성을 사용 하 여 기본 상호 작용을 아직 아니지만 확실히 steam를 확보 됩니다!</span><span class="sxs-lookup"><span data-stu-id="8daf4-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="8daf4-108">응시 지속 작업 헤드업 HoloLens에 핸 즈 프리 가장 친숙 하 고 마스터 간편한 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="8daf4-109">또한 게이즈 유지는 100% 신뢰할 수 있는 운영 환경에서 노이즈가 간섭 또는 대기 제약 조건과 관계입니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="8daf4-110">목표</span><span class="sxs-lookup"><span data-stu-id="8daf4-110">Goals</span></span>

<span data-ttu-id="8daf4-111">음성 사용 하지 않고 전체 핸 즈 프리 상호 작용 하는 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-111">Provide a mechanism for full hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="8daf4-112">디자인 원칙</span><span class="sxs-lookup"><span data-stu-id="8daf4-112">Design principles</span></span>

1. <span data-ttu-id="8daf4-113">응시 무기 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="8daf4-114">응시 직관적인 상호 작용에 대 한 시각적 피드백 하는데 너무 많은 피드백 간주를 유도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="8daf4-115">피드백을 어떤 해당 대상으로 하는, 의도 대 한 자동 선택 되지 않습니다 하지만 알고 사용자 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="8daf4-116">텍스트를 읽으려면 선택 하기 전에 정보를 흡수 하는 사용자 공간을 제공 하는 추가 고려 사항이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="8daf4-117">금발 속도 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="8daf4-118">지속 채우기는 탐색에 미치는 영향에 따라 다른 타이머를 가질 수 있습니다-자주 사용 되는 함수 일반적으로에서 이익을 채우기 시간을 단축 동안 더 파생적 함수 채우기 시간이 더에서 이점을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="8daf4-119">채우기 색의 애니메이션 곡선 느낌 채우기 시간 단축을 영향을 주게 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="8daf4-120">고려 사항 fast/중간/느린 사용자 결정을 사용 하도록 설정 하려면 취해야 속도 재정의 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="8daf4-121">Yo-yo 효과를 no-no의 예를 들어합니다</span><span class="sxs-lookup"><span data-stu-id="8daf4-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="8daf4-122">Yo-yo 효과 (라고도 "밤에는 Roxbury")은 특정 배치의 콘텐츠와 게이즈 기반 컨트롤에서 나타날 수 있습니다 하는 불편 패턴.</span><span class="sxs-lookup"><span data-stu-id="8daf4-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="8daf4-123">예를 들어,를 목록 탐색 창 맨 아래에 채우기 단추를 사용 하 여 자세히 다루지는, 결과 조회, 지속 등 살펴보면 아래로-확인 루프를 유도 합니다. 이 결과 패턴 편리 하 게 되었으며 탐색 컨트롤 작은 백-및-명시 해야 하는 중앙된 위치에 배치 하 여 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="8daf4-124">해당 효과 기준으로 지속 단추의 배치가 편안 하 게 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="8daf4-125">UI 패턴</span><span class="sxs-lookup"><span data-stu-id="8daf4-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="8daf4-126">높은 빈도 단추</span><span class="sxs-lookup"><span data-stu-id="8daf4-126">High frequency buttons</span></span>
    
* <span data-ttu-id="8daf4-127">다음/뒤로 단추</span><span class="sxs-lookup"><span data-stu-id="8daf4-127">Next/Back buttons</span></span>
  * <span data-ttu-id="8daf4-128">짧은 지연 사전 채우기 (부동 깜박임 버퍼)</span><span class="sxs-lookup"><span data-stu-id="8daf4-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="8daf4-129">큰 단추는 쉽게 게이즈를 사용 하 여 적중 수</span><span class="sxs-lookup"><span data-stu-id="8daf4-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="8daf4-130">눈 높이에서 이러한 상호 작용 하도록 않게 부담 데 유용한</span><span class="sxs-lookup"><span data-stu-id="8daf4-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="8daf4-131">지속 지역 (뒤로)을 사용 하 여 쉽게 비활성 아이콘 보다 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-131">Dwell region can be larger than inactive icon to make it easier to use (Back)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="8daf4-132">낮은 빈도 단추</span><span class="sxs-lookup"><span data-stu-id="8daf4-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="8daf4-133">설정 메뉴를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-133">Activate settings menu</span></span>
  * <span data-ttu-id="8daf4-134">더 이상 사전 채우기 확인 (부동 깜박임 버퍼)을 지연</span><span class="sxs-lookup"><span data-stu-id="8daf4-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="8daf4-135">자주 커서 경로 모니터로 이러한 단추를 유지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="8daf4-136">확인 (즉, 검색 흐름, 대화 상자)</span><span class="sxs-lookup"><span data-stu-id="8daf4-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="8daf4-137">주 단추 강조 표시 선택 영역이 표시</span><span class="sxs-lookup"><span data-stu-id="8daf4-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="8daf4-138">강조 표시 선택 영역이으로 동시 지속 대상 표시</span><span class="sxs-lookup"><span data-stu-id="8daf4-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="8daf4-139">사용 하 여 인터페이스를 간단 하 게 유지 하는 아이콘을 둘러싸는 대상 유지</span><span class="sxs-lookup"><span data-stu-id="8daf4-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="8daf4-140">중요 한 결정을 강조 표시를 활성화 하지 있도록 중역이 시간에 대 한 지속 대상 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="8daf4-141">설정/해제 단추</span><span class="sxs-lookup"><span data-stu-id="8daf4-141">Toggle buttons</span></span>

* <span data-ttu-id="8daf4-142">Pin</span><span class="sxs-lookup"><span data-stu-id="8daf4-142">Pin</span></span>
  * <span data-ttu-id="8daf4-143">활성/비활성 지우기 시각적 상태</span><span class="sxs-lookup"><span data-stu-id="8daf4-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="8daf4-144">방사형 채우기 지 원하는 포커스 및 자연 스러운 진행 상태를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="8daf4-145">개별 설정</span><span class="sxs-lookup"><span data-stu-id="8daf4-145">Individual settings</span></span>
  * <span data-ttu-id="8daf4-146">활성/비활성 선택을 취소 상태</span><span class="sxs-lookup"><span data-stu-id="8daf4-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="8daf4-147">대상 모두 왼쪽된 주변 아이콘에 자세히 설명 하지</span><span class="sxs-lookup"><span data-stu-id="8daf4-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="8daf4-148">지속을 대상으로 선택 활성을 강조 하는 경우에 표시</span><span class="sxs-lookup"><span data-stu-id="8daf4-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="8daf4-149">"슬라이더에서" 부분에 대해 고민 설정/해제에 대 한 오른쪽</span><span class="sxs-lookup"><span data-stu-id="8daf4-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="8daf4-150">목록 보기</span><span class="sxs-lookup"><span data-stu-id="8daf4-150">List views</span></span>

* <span data-ttu-id="8daf4-151">검색 목록 보기-가이드 파일을 엽니다</span><span class="sxs-lookup"><span data-stu-id="8daf4-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="8daf4-152">커서 강조 표시 행에서 아무 곳 이나 행에서 하지만 유지를 시작 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="8daf4-153">지속 대상 왼쪽에 표시 되는 커서에서 행이 강조 표시 하는 경우</span><span class="sxs-lookup"><span data-stu-id="8daf4-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="8daf4-154">모든 목록 보기에는 텍스트의 왼쪽에서 원 항상 대상 유지</span><span class="sxs-lookup"><span data-stu-id="8daf4-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="8daf4-155">모든 대상의 반복적인 UI를 방지 하려면 한 번에 대해 자세히 설명 하지 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="8daf4-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="8daf4-156">UX 경험을 설정 하려면 동일한 패턴을 다시 사용</span><span class="sxs-lookup"><span data-stu-id="8daf4-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="8daf4-157">목록 보기-작업/단계 지침에서의 계층 구조를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="8daf4-158">대상 텍스트의 왼쪽에서 원 항상 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="8daf4-159">지속 유도성 축소/확장</span><span class="sxs-lookup"><span data-stu-id="8daf4-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="8daf4-160">검색 목록 보기-모드 선택</span><span class="sxs-lookup"><span data-stu-id="8daf4-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="8daf4-161">위에 설정 된 패턴에 따라</span><span class="sxs-lookup"><span data-stu-id="8daf4-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="8daf4-162">상황에 맞는 단추</span><span class="sxs-lookup"><span data-stu-id="8daf4-162">Contextual buttons</span></span>

* <span data-ttu-id="8daf4-163">표시/숨기기 3D-표시를 3d에서 홀로그램 거의 테더 따라</span><span class="sxs-lookup"><span data-stu-id="8daf4-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="8daf4-164">활성/비활성 지우기 시각적 상태</span><span class="sxs-lookup"><span data-stu-id="8daf4-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="8daf4-165">피벗</span><span class="sxs-lookup"><span data-stu-id="8daf4-165">Pivots</span></span>

* <span data-ttu-id="8daf4-166">최근/All 가이드 목록</span><span class="sxs-lookup"><span data-stu-id="8daf4-166">Recent/All guides list</span></span>
  * <span data-ttu-id="8daf4-167">탭이 활성 상태로 유지 되는 UI 유도성 채우기</span><span class="sxs-lookup"><span data-stu-id="8daf4-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="8daf4-168">간단한 단어 피벗에 대 한 하기로 했습니다 지속 대상 패턴 생략</span><span class="sxs-lookup"><span data-stu-id="8daf4-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="8daf4-169">간단한 인터페이스를 다른 2 원 대상과 더 광범위 한 UI를 통해 선호 하는 것</span><span class="sxs-lookup"><span data-stu-id="8daf4-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="8daf4-170">여기서는 단어는 지연 채우기 전에 충분 한 쾌적은 아주 짧은</span><span class="sxs-lookup"><span data-stu-id="8daf4-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="8daf4-171">UX 지침 및 모범 사례</span><span class="sxs-lookup"><span data-stu-id="8daf4-171">UX guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="8daf4-172">대상 크기</span><span class="sxs-lookup"><span data-stu-id="8daf4-172">Target sizes</span></span>

  * <span data-ttu-id="8daf4-173">Pin 아이콘 최소 크기: unity에서 30 Mru (2 분 @ 30 cm) 세계 좌표 공간에서 6 cm</span><span class="sxs-lookup"><span data-stu-id="8daf4-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="8daf4-174">대상 "자석" 또는 "고정" 전혀?</span><span class="sxs-lookup"><span data-stu-id="8daf4-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="8daf4-175">(커서 다듬기 gaze 즉)</span><span class="sxs-lookup"><span data-stu-id="8daf4-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="8daf4-176">애니메이션</span><span class="sxs-lookup"><span data-stu-id="8daf4-176">Animation</span></span>

  * <span data-ttu-id="8daf4-177">지속 visual 트리거.5sec 하기 전의 지연</span><span class="sxs-lookup"><span data-stu-id="8daf4-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="8daf4-178">지속 visual 1.2 초 기간</span><span class="sxs-lookup"><span data-stu-id="8daf4-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="8daf4-179">애니메이션에서 곡선?</span><span class="sxs-lookup"><span data-stu-id="8daf4-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="8daf4-180">시각적 피드백</span><span class="sxs-lookup"><span data-stu-id="8daf4-180">Visual feedback</span></span>

  * <span data-ttu-id="8daf4-181">커서 시작 위치를 응시 방사형 채우기</span><span class="sxs-lookup"><span data-stu-id="8daf4-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="8daf4-182">단추의 센터에서 항상 방사형 채우기입니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-182">Always radial fill from center of button.</span></span> <span data-ttu-id="8daf4-183">일관 된 응답 다른 단추는 다른 모든 방향으로 보다 덜 혼동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="8daf4-184">이 규칙은 방향 상호 작용 (예를 들어, nav 위쪽/아래쪽/왼쪽/오른쪽, 등)에 있지만 손상 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="8daf4-185">예를 들어 가이드는 다음/이전에 남겨진다는에서 예외가 오른쪽 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-185">For example, Guides makes an exception on Next/Back being left right fills.</span></span>
    * <span data-ttu-id="8daf4-186">(해제 설정/해제) 하는 경우 외부에서 방사형 채우기를 반전 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="8daf4-187">단추를 하나 누르는의 역 느낌은 유지 하기 위해 유용한 visual 패턴.</span><span class="sxs-lookup"><span data-stu-id="8daf4-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="8daf4-188">점진적 공개</span><span class="sxs-lookup"><span data-stu-id="8daf4-188">Progressive disclosure</span></span>

 * <span data-ttu-id="8daf4-189">점진적 공개 지속 대상 (예: 목록 컨트롤)에서 강조 표시에 였음을 의미합니다</span><span class="sxs-lookup"><span data-stu-id="8daf4-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="8daf4-190">텍스트에서 아무 곳 이나 응시에 스포트라이트를 사용 하 여 텍스트 모음 강조 표시</span><span class="sxs-lookup"><span data-stu-id="8daf4-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="8daf4-191">응시 채우기 대상에는 나타나지만 항상 왼쪽에서 강조 표시 되는 목록 항목에 대해서만</span><span class="sxs-lookup"><span data-stu-id="8daf4-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="8daf4-192">반복적인 누적된 원 모양으로 인해 항상 모든 지속 대상이 되지 않도록 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8daf4-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="8daf4-193">참조</span><span class="sxs-lookup"><span data-stu-id="8daf4-193">See also</span></span>
* [<span data-ttu-id="8daf4-194">직접 조작</span><span class="sxs-lookup"><span data-stu-id="8daf4-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8daf4-195">지점 및 커밋</span><span class="sxs-lookup"><span data-stu-id="8daf4-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="8daf4-196">상호 작용 기본 사항</span><span class="sxs-lookup"><span data-stu-id="8daf4-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="8daf4-197">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="8daf4-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8daf4-198">응시 및 음성</span><span class="sxs-lookup"><span data-stu-id="8daf4-198">Gaze and voice</span></span>](voice-design.md)
