---
title: Windows Mixed Reality 용 SteamVR 응용 프로그램 업데이트
description: Windows Mixed Reality 헤드셋의 호환성을 최대화 하기 위해 SteamVR 응용 프로그램을 업데이트 하는 최선의 방법입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, 호환성
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548665"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a><span data-ttu-id="1444f-104">Windows Mixed Reality 용 SteamVR 응용 프로그램 업데이트</span><span class="sxs-lookup"><span data-stu-id="1444f-104">Updating your SteamVR application for Windows Mixed Reality</span></span>

<span data-ttu-id="1444f-105">개발자가 Windows Mixed Reality 헤드셋에서 실행할 SteamVR 환경을 테스트 하 고 최적화 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="1444f-106">이 설명서는 개발자가 Windows Mixed Reality에서 뛰어난 환경을 실행 하기 위해 수행할 수 있는 일반적인 개선 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="1444f-107">초기 설치 지침</span><span class="sxs-lookup"><span data-stu-id="1444f-107">Initial setup instructions</span></span>

<span data-ttu-id="1444f-108">Windows Mixed Reality에서 게임 또는 앱 테스트를 시작 하려면 먼저 [시작 가이드](http://aka.ms/WindowsMixedRealitySteamVR) 를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="1444f-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](http://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="1444f-109">컨트롤러 모델</span><span class="sxs-lookup"><span data-stu-id="1444f-109">Controller Models</span></span>
1. <span data-ttu-id="1444f-110">앱이 컨트롤러 모델을 렌더링 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="1444f-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="1444f-111">[Windows Mixed Reality 동작 컨트롤러 모델](motion-controllers.md#rendering-the-motion-controller-model) 사용</span><span class="sxs-lookup"><span data-stu-id="1444f-111">Use the [Windows Mixed Reality motion controller models](motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="1444f-112">IVRRenderModel:: GetComponentState를 사용 하 여 구성 요소 부분에 대 한 로컬 변환을 가져옵니다 (예:</span><span class="sxs-lookup"><span data-stu-id="1444f-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="1444f-113">포인터 포즈)</span><span class="sxs-lookup"><span data-stu-id="1444f-113">Pointer pose)</span></span>
2. <span data-ttu-id="1444f-114">활용 이라는 개념이 있는 환경은 입력 Api에서 컨트롤러를 구별 하기 위해 힌트를 가져와야 합니다 [(Unity 예제)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) .</span><span class="sxs-lookup"><span data-stu-id="1444f-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="1444f-115">컨트롤</span><span class="sxs-lookup"><span data-stu-id="1444f-115">Controls</span></span>

<span data-ttu-id="1444f-116">컨트롤 레이아웃을 디자인 하거나 조정할 때 다음의 예약 된 명령 집합을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="1444f-117">**왼쪽 및 오른쪽 아날로그 엄지 스틱** 을 클릭 하면 **스트림 대시보드에**예약 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>
2. <span data-ttu-id="1444f-118">**Windows 단추** 는 항상 Windows Mixed Reality 홈으로 사용자를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="1444f-119">가능 하면 [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior와 일치 하는 thumb 스틱 기반 teleportation로 기본값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-119">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="1444f-120">도구 설명 및 UI</span><span class="sxs-lookup"><span data-stu-id="1444f-120">Tooltips and UI</span></span>

<span data-ttu-id="1444f-121">많은 VR 게임은 게임 또는 앱에 대 한 가장 중요 한 명령을 사용자에 게 알려 주는 동작 컨트롤러 도구 설명 및 오버레이를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-121">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="1444f-122">Windows Mixed reality의 응용 프로그램을 튜닝할 때 도구 설명이 Windows 컨트롤러 모델에 매핑되는지 확인 하는 환경에서이 부분을 검토 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-122">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="1444f-123">또한 사용자 환경에 컨트롤러 이미지를 표시 하는 점이 있는 경우 Windows Mixed Reality 동작 컨트롤러를 사용 하 여 업데이트 된 이미지를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="1444f-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="1444f-124">Haptics</span></span>

<span data-ttu-id="1444f-125">[Windows 10 4 월 2018 업데이트](release-notes-april-2018.md)부터 Windows Mixed Reality의 SteamVR 환경에 대 한 haptics가 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-125">Beginning with the [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="1444f-126">SteamVR app 또는 game에 이미 haptics에 대 한 지원이 포함 된 경우 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)에서 추가 작업 없이 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](motion-controllers.md).</span></span>

<span data-ttu-id="1444f-127">Windows Mixed Reality 동작 컨트롤러는 다른 SteamVR 동작 컨트롤러에서 발견 된 선형 작동기와는 달리 표준 haptics 모터를 사용 하 여 예상 되는 사용자 환경이 약간 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="1444f-128">따라서 Windows Mixed Reality 동작 컨트롤러를 사용 하 여 haptics 디자인을 테스트 하 고 조정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-128">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="1444f-129">예를 들어 Windows Mixed Reality 동작 컨트롤러에서 짧은 햅 펄스 (5-10 밀리초)가 더 눈에 띄지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-129">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="1444f-130">더 눈에 띄는 펄스를 생성 하려면 더 긴 "클릭" (40-70 밀리초)을 사용 하 여 모터를 다시 전원 꺼짐으로 설정 하기 전에 표시 하는 시간을 더 많이 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-130">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="1444f-131">Windows Mixed Reality 시작 메뉴에서 SteamVR apps 시작</span><span class="sxs-lookup"><span data-stu-id="1444f-131">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="1444f-132">스트림를 통해 배포 되는 VR 환경의 경우 [SteamVR Beta에 대 한 Windows Mixed reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 를 최신 [windows 참가자](https://insider.windows.com) RS5 항공편과 함께 업데이트 하 여 이제 SteamVR 제목이 "모든 앱"의 windows mixed Reality 시작 메뉴에 표시 됩니다. 자동으로 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-132">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="1444f-133">이러한 소프트웨어 버전을 설치 하면 고객이 헤드셋을 제거 하지 않고 Windows Mixed Reality 홈에서 직접 SteamVR 타이틀을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-133">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="1444f-134">Windows Mixed Reality 로고</span><span class="sxs-lookup"><span data-stu-id="1444f-134">Windows Mixed Reality logo</span></span>

<span data-ttu-id="1444f-135">제목에 대해 Windows Mixed Reality 지원을 표시 하려면 앱 방문 페이지에서 "스토어 페이지 편집" 링크로 이동 하 고 "기본 정보" 탭을 클릭 한 다음 "가상 현실"로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-135">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="1444f-136">"Windows Mixed Reality 숨기기"를 선택 취소 한 다음 저장소에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-136">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="1444f-137">버그 및 피드백</span><span class="sxs-lookup"><span data-stu-id="1444f-137">Bugs and feedback</span></span>

<span data-ttu-id="1444f-138">사용자 의견은 Windows Mixed Reality SteamVR 환경을 개선 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-138">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="1444f-139">[Windows 피드백 허브](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)를 통해 모든 피드백 및 버그를 제출 하세요.</span><span class="sxs-lookup"><span data-stu-id="1444f-139">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="1444f-140">[SteamVR 피드백을 최대한 활용 하는 방법에 대 한](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)몇 가지 팁은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-140">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="1444f-141">공유에 대 한 질문이 나 의견이 있는 경우 [스트림 포럼](http://steamcommunity.com/app/719950/discussions/)에서 연락할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1444f-141">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="1444f-142">Faq 및 문제 해결</span><span class="sxs-lookup"><span data-stu-id="1444f-142">FAQs and troubleshooting</span></span>

<span data-ttu-id="1444f-143">경험을 설정 하거나 재생 하는 일반적인 문제를 실행 하는 경우 [최신 문제 해결 단계를 확인](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)하세요.</span><span class="sxs-lookup"><span data-stu-id="1444f-143">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="1444f-144">참조</span><span class="sxs-lookup"><span data-stu-id="1444f-144">See also</span></span>
* [<span data-ttu-id="1444f-145">도구 설치</span><span class="sxs-lookup"><span data-stu-id="1444f-145">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="1444f-146">헤드셋 및 동작 컨트롤러 드라이버 기록</span><span class="sxs-lookup"><span data-stu-id="1444f-146">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="1444f-147">Windows Mixed Reality 최소 PC 하드웨어 호환성 지침</span><span class="sxs-lookup"><span data-stu-id="1444f-147">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
