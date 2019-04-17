---
title: Holographic Remoting 플레이어
description: Holographic 원격 플레이어는 PC 앱과 게임 Holographic 원격 지에 연결 하는 도우미 앱. Holographic 원격 PC에서의 Microsoft HoloLens holographic 콘텐츠를 스트리밍합니다 실시간으로 Wi-fi 연결을 사용 합니다.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605002"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="1a46d-105">Holographic Remoting 플레이어</span><span class="sxs-lookup"><span data-stu-id="1a46d-105">Holographic Remoting Player</span></span>

<span data-ttu-id="1a46d-106">Holographic 원격 플레이어는 PC 앱과 게임 Holographic 원격 지에 연결 하는 도우미 앱.</span><span class="sxs-lookup"><span data-stu-id="1a46d-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="1a46d-107">Holographic 원격 PC에서의 Microsoft HoloLens holographic 콘텐츠를 스트리밍합니다 실시간으로 Wi-fi 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="1a46d-108">Holographic 원격 플레이어 Holographic 원격을 지원 하도록 특별히 설계 된 PC 앱만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="1a46d-109">HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-109">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="1a46d-110">Holographic 원격 플레이어에 게 연결</span><span class="sxs-lookup"><span data-stu-id="1a46d-110">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="1a46d-111">Holographic 원격 플레이어에 게 연결 하는 앱의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-111">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="1a46d-112">다음과 같이 원격 플레이어의 주 화면에서 볼 수 있는 HoloLens 장치, IP 주소를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-112">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![Holographic Remoting 플레이어](images/holographicremotingplayer.png)

<span data-ttu-id="1a46d-114">주 화면에 표시 될 때마다 연결 앱 있는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-114">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="1a46d-115">Holographic 원격 연결이 보면 **암호화 되지 않은**합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-115">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="1a46d-116">항상 신뢰할 수 있는 보안 Wi-fi 연결을 통해 Holographic Remoting을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-116">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="1a46d-117">품질 및 성능</span><span class="sxs-lookup"><span data-stu-id="1a46d-117">Quality and Performance</span></span>

<span data-ttu-id="1a46d-118">품질 및 성능을 경험의 세 가지 요인에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-118">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="1a46d-119">**실행 중인 홀로그램 환경** -고해상도 또는 매우 자세한 콘텐츠를 렌더링 하는 앱은 더 빠른 PC 또는 무선 연결을 더 빠르게 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-119">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="1a46d-120">**PC의 하드웨어** -PC를 실행 하 고 초당 60 프레임으로 holographic 환경을 인코딩할 수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-120">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="1a46d-121">그래픽 카드에 대 한 일반적으로 GeForce GTX 970 또는 AMD Radeon R9 290 더 나은 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-121">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="1a46d-122">마찬가지로 특정 환경을 높거나 낮은 엔드 카드가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-122">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="1a46d-123">**Wi-fi 연결** -holographic 환경을 Wi-fi를 통해 스트리밍됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-123">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="1a46d-124">품질을 최대화 하기 위해 낮은 정체를 사용 하 여 고속 네트워크를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-124">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="1a46d-125">이더넷 케이블을 통해 연결 된 PC를 사용 하 여, Wi-fi, 대신 향상 될 수 있습니다 품질입니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-125">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="1a46d-126">진단</span><span class="sxs-lookup"><span data-stu-id="1a46d-126">Diagnostics</span></span>

<span data-ttu-id="1a46d-127">연결의 품질을 측정 하려면 예를 들어 **"진단 사용"** Holographic 원격 플레이어의 주 화면에 있는 동안에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-127">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="1a46d-128">진단 설정 되 면 앱은 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-128">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="1a46d-129">**FPS** -렌더링 된 프레임의 평균 원격 플레이어 받고 초당 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-129">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="1a46d-130">60 FPS 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-130">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="1a46d-131">**대기 시간** -프레임은 HoloLens로 PC에서 하는 데 걸리는 평균 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-131">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="1a46d-132">낮을수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-132">The lower the better.</span></span> <span data-ttu-id="1a46d-133">이 Wi-fi 네트워크에 따라 크게 좌우 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-133">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="1a46d-134">메인 화면에서 말하면 **"진단 사용 안 함"** 진단을 해제 하려면.</span><span class="sxs-lookup"><span data-stu-id="1a46d-134">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="1a46d-135">PC 시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1a46d-135">PC System Requirements</span></span>
* <span data-ttu-id="1a46d-136">PC **해야** Windows 10 1 주년 업데이트 실행 중 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-136">Your PC **must** be running the Windows 10 Anniversary Update.</span></span>
* <span data-ttu-id="1a46d-137">GeForce GTX 970 또는 AMD Radeon R9 290 더 나은 그래픽 카드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-137">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="1a46d-138">PC를 통해 무선 홉 수를 줄이기 위해 이더넷 네트워크에 연결 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1a46d-138">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a46d-139">관련 항목</span><span class="sxs-lookup"><span data-stu-id="1a46d-139">See Also</span></span>
* [<span data-ttu-id="1a46d-140">Holographic 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="1a46d-140">Holographic remoting software license terms</span></span>](microsoft-holographic-remoting-software-license-terms.md)
* [<span data-ttu-id="1a46d-141">Microsoft 개인정보취급방침</span><span class="sxs-lookup"><span data-stu-id="1a46d-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
