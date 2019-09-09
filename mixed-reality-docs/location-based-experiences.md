---
title: Windows Mixed Reality를 사용 하는 위치 기반 엔터테인먼트
description: Unity에서 기본 Holographic 네이티브 개체에 대 한 액세스를 가져옵니다.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: 혼합 현실, vr, lbe, 위치
ms.openlocfilehash: e23d17ff2b07c636c98a9f19a5dd20f4dc558bf7
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69983401"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="34e5d-104">Windows Mixed Reality를 사용 하는 위치 기반 엔터테인먼트</span><span class="sxs-lookup"><span data-stu-id="34e5d-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="34e5d-105">지난 몇 년 동안에는 위치 기반 엔터테인먼트 범주에서 놀라운 규모의 성장과 혁신을 담당자 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-105">In the last couple of years, we have witnessed an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="34e5d-106">테마 파킹 및 theatres 같은 전통적인 장소는 기존 탑승 및 설치에 대 한 무료 환경을 제공 하는 몰입 형 다중 플레이어 환경을 제공 하기 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-106">Traditional venues like theme parks and theatres have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="34e5d-107">새로운 operators 및 장소는 대량의에 대 한 매력적인 가격으로 고유한 다중 sensorial 멀티 플레이어 환경을 제공 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="34e5d-108">이러한 모든 환경은 혼합 현실에서 가능한 작업을 위해 봉투를 푸시하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="34e5d-109">이 문서는 위치 기반 엔터테인먼트 범주에서 Windows Mixed Reality를 시작 하기 위한 가이드입니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="34e5d-110">아래 지침은 학습, 제품 디자인 또는 기타 사용 사례와 같은 엔터테인먼트 이상의 위치 기반 환경에 추가로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design or other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="34e5d-111">엔지니어링 FAQ</span><span class="sxs-lookup"><span data-stu-id="34e5d-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="34e5d-112">하드웨어</span><span class="sxs-lookup"><span data-stu-id="34e5d-112">Hardware</span></span>

<span data-ttu-id="34e5d-113">**대답 설치 프로그램에서 사용할 수 있는 Microsoft 및 파트너의 하드웨어는 무엇 인가요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="34e5d-114">A: Microsoft와 해당 OEM 파트너는 요구 사항에 따라 선택할 수 있는 강력한 장치 포트폴리오를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="34e5d-115">고객에 게 제공 하는 환경에 가상 현실 헤드셋이 필요한 경우 HP, Samsung 및 Acer의 다음 시장 헤드셋 헤드셋은 매우 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-115">If the experiences you’re providing to your customers require virtual reality headsets, the following in-market headsets from HP, Samsung and Acer are a great fit.</span></span> <span data-ttu-id="34e5d-116">각 헤드셋에는 고유한 차별화 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="34e5d-117">아래에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-117">More details on each below.</span></span>

<span data-ttu-id="34e5d-118">HP 반향: [세부 정보](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="34e5d-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="34e5d-119">Samsung Odyssey +: [세부 정보](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="34e5d-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="34e5d-120">Acer: [세부 정보](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="34e5d-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="34e5d-121">사용자의 위치가 혼합 또는 확대 된 현실에서 전문적으로 진행 되는 헤드셋을 사용 해야 하는 경우 Microsoft HoloLens 2를 사용할 수 있습니다 (이제 사전에 관심을 볼 수 있음).</span><span class="sxs-lookup"><span data-stu-id="34e5d-121">If your location specializes in mixed or augmented reality experiences requiring the use of a see-through headset, you can procure the Microsoft HoloLens 2 (now open for pre-order interest).</span></span>  

<span data-ttu-id="34e5d-122">HoloLens 2: [사전 순서 관심](https://www.microsoft.com/en-us/hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="34e5d-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com/en-us/hololens/buy)</span></span>

<span data-ttu-id="34e5d-123">고급 컴퓨터 비전, 음성 및 본문 추적이 필요한 환경을 실험 하는 경우 Azure Kinect 진한 a를 요구에 맞게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-123">If you’re experimenting with experiences that require advanced computer vision, speech and body tracking, you may find the Azure Kinect DK a fit for your needs.</span></span>  

<span data-ttu-id="34e5d-124">Azure Kinect: [세부 정보](https://azure.microsoft.com/en-us/services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="34e5d-124">Azure Kinect: [Details](https://azure.microsoft.com/en-us/services/kinect-dk/)</span></span>

<span data-ttu-id="34e5d-125">**대답 내 PC 테더 링 된 VR 환경을 실행 하는 데 사용할 수 있는 백팩 Pc의 포트폴리오는 무엇 인가요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="34e5d-126">PC 테더 링 된 VR 환경에서 Oem은 해당 요구에 맞게 작성 된 백팩 Pc를 놀라운 방식으로 선택할 것을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="34e5d-127">HP는 전 세계의 가장 강력한 wearable PC 인 HP VR 백팩 G2를 출시 했습니다. 이제 무료 로밍 환경에 최적화 되어 있으며, 이제 RTX 2080 GPU를 사용 하 여 30% 더 강력한 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="34e5d-128">세부 정보</span><span class="sxs-lookup"><span data-stu-id="34e5d-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="34e5d-129">설정</span><span class="sxs-lookup"><span data-stu-id="34e5d-129">Setup</span></span>

<span data-ttu-id="34e5d-130">**대답 보다 쉽게 설치를 구성 하 고 LBE에 대 한 혼합 현실 포털을 사용자 지정 하려면 어떻게 해야 하나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="34e5d-131">이 기능을 사용 하려면 버전이 2000.19061.1011.0 이상 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="34e5d-132">키오스크 또는 사용자 지정 환경에 앱을 배포 하기 위해 일반적으로 앱을 통해 사용할 수 있는 것 보다 혼합 현실 포털의 사용자 지정이 더 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="34e5d-133">혼합 현실 포털의 최신 7 월 업데이트에서는 구성 파일을 통해 다음 작업을 수행할 수 있는 몇 가지 고급 설정을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-133">The latest July update of Mixed Reality Portal supports several advanced settings that can be via a configuration file to do the following:</span></span>  

<span data-ttu-id="34e5d-134">실패 한 시스템 검사 허용 – 일반적으로 설치 프로세스는 설치를 완료 하기 전에 PC에서 Windows Mixed Reality와의 호환성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="34e5d-135">호환성 문제가 있는 경우이를 무시 하면 Windows Mixed Reality를 실행 하려고 할 때 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-135">Bypassing this may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="34e5d-136">장치 도우미 앱 건너뛰기 – DCA는 제조업체에서 제공 하는 헤드셋 특정 설치 단계를 제공 하 고 헤드셋의 펌웨어를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="34e5d-137">방 설정 건너뛰기 – 대화방 경계를 만들라는 메시지를 표시 하는 대신, 헤드셋을 장착/고정 모드로 직접 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-137">Skip room setup – instead of being prompted to create a room boundary, you can proceed directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="34e5d-138">스토어에서 앱 설치 건너뛰기-일반 설치는 3D 뷰어 및 Edge 360 뷰어 추가 기능을 비롯 한 여러 스토어 앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="34e5d-139">이렇게 하면 이러한 앱의 설치를 건너뛸 수 있지만 장치 기능이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="34e5d-140">전체 화면에 미리 보기 표시 – 혼합 현실 포털은 헤드셋을 사용 하는 동안 데스크톱 PC의 전체 화면에 헤드셋 미리 보기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="34e5d-141">왼쪽 패널에 대해 새로 숨기기 – 혼합 현실 포털을 시작할 때 새 패널이 확장 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-141">Hide New for you side panel – this prevent the New for you panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="34e5d-142">구성 방법:</span><span class="sxs-lookup"><span data-stu-id="34e5d-142">How to configure:</span></span>  

<span data-ttu-id="34e5d-143">이러한 구성 중 하나를 설정 하려면 _$env: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_  디렉터리 아래에 _userconfig_ 이라는 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="34e5d-144">대부분의 사용자에 게는 _C:\Users\<username > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_  처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-144">For most users this will look like _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="34e5d-145">JSON 파일에는 설정 하려는 위의 설정에 대해 "true"로 설정 된 아래 내용이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="34e5d-146">**대답 Playspace를 구성 하는 방법에 대 한 지침이 있나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="34e5d-147">A: Playspace 구성은 소비자 설정 환경에서 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="34e5d-148">대화방 설정 프로세스를 사용 하 여 대화방 경계를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="34e5d-149">방 경계 구성에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34e5d-149">More details on configuring room boundaries can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="34e5d-150">위의 문서에 설명 된 대로 최대 합리적인 단일 좌표 playspace는 5mx5m 주위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="34e5d-151">더 큰 영역을 사용 하려는 경우 Windows Holographic API 스택에서 공간 앵커 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-151">If you want to have a larger area you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="34e5d-152">이 API를 사용 하려면 생성 하는 환경에서 사용자 지정 엔지니어링이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-152">Using this API will require custom engineering in the experiences you are producing.</span></span>  

<span data-ttu-id="34e5d-153">다른 공간 크기에 대 한 콘텐츠를 최적화 하는 방법에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34e5d-153">More details on how to optimize your content for different space sizes can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="34e5d-154">**대답 공간이 너무 크고 경계를 사용 하 여 제공 된 환경을 설정 하려고 할 때 오류가 발생 합니다. 내 대량 로밍 환경 작업을 설정 하려면 어떻게 해야 하나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to setup my large free-roam experience work?**</span></span>

<span data-ttu-id="34e5d-155">A: ~ 18x18ft 보다 큰 공간을 설정 하려면 시스템에서 제공 하는 경계 환경을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-155">A: To setup a larger space than ~18x18ft you won’t be able to use the boundary experience provided by the system.</span></span>  <span data-ttu-id="34e5d-156">경계 시스템은 단일 고정 좌표 "앵커"를 활용 합니다 .이는 사용자가 중앙 단계 앵커에서 멀리 떨어져 있을 때 불안정 해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-156">The boundary systems relies on leveraging a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="34e5d-157">대신 경계를 표시 하거나 스테이지 범위 또는 playspace를 구성 하지 않는 "장착 됨" 모드를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-157">Instead, you can setup “seated” mode, which will not display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="34e5d-158">그런 다음 실제 경계 영역을 참조 하도록 앱 내에서 여러 공간 앵커를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-158">Then, you’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="34e5d-159">응용 프로그램 개발자는 사용자가 실제 환경에서 충돌 하지 않도록 필요한 보호 기능을 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="34e5d-160">이러한 작업은 환경 내에서 디지털 벽 이거나 사용자 지정 된 게임 경계 시각적 개체 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="34e5d-161">WMR를 사용 하 여 대화방 경계를 설정 하는 방법에 대 한 지침은 [여기](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-161">Guidance on setting up the room boundary with WMR can be found [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="34e5d-162">**대답 Playspace의 원점은 어디에 있나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="34e5d-163">A: 플레이 공간의 원점은 실내 설정 환경에 따라 결정 되며, 설치 중에 가운데 단추를 누를 때 특히 HMD 위치가 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="34e5d-164">다중 플레이어 설정</span><span class="sxs-lookup"><span data-stu-id="34e5d-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="34e5d-165">**대답 내 장소에서 다중 플레이어 환경을 배포 합니다. Windows Mixed Reality에서 지원 되나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="34e5d-166">A: 혼합 현실 공간 데이터 패키지 작성 도구는 한 PC에서 다른 PC로 공간 데이터를 이식할 수 있도록 하 여 동일한 공간에서 여러 플레이어를 지역화할 수 있는 베타 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-166">A: The Mixed Reality Spatial Data Packager tool is a beta feature that allows localizing multiple players in the same space by enabling porting of the spatial data from one PC to another.</span></span> <span data-ttu-id="34e5d-167">도구에 [액세스 하 여이 도구](mixedrealityspatialdatapackager.md)에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-167">You can access the tool and learn more about it [here](mixedrealityspatialdatapackager.md).</span></span>

### <a name="tracking"></a><span data-ttu-id="34e5d-168">추적</span><span class="sxs-lookup"><span data-stu-id="34e5d-168">TRACKING</span></span>

<span data-ttu-id="34e5d-169">Q: Windows Mixed Reality 헤드셋의 추적 기술은 어떻게 작동 하나요?</span><span class="sxs-lookup"><span data-stu-id="34e5d-169">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="34e5d-170">혼합 현실에서는 HoloLens와 동일한 추적 기술을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-170">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="34e5d-171">내부 추적 시스템에 대 한 자세한 내용을 보려면 [여기](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system)에서 설명서를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="34e5d-171">To learn more about the inside-out tracking system, check out the documentation [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="34e5d-172">상위 수준 공간 매핑 시스템의 작동 방식에 대 한 설명을 보려면 [여기](spatial-mapping-design.md)에서 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34e5d-172">For a description of how the higher-level spatial mapping system works you can read our description [here](spatial-mapping-design.md).</span></span>

<span data-ttu-id="34e5d-173">**대답 안정적인 추적 볼륨을 얻기 위한 모범 사례가 있나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-173">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="34e5d-174">성공 여부를 추적 하기 위한 환경을 최대한 구성 하기 위해이 [게시물](environment-considerations-for-hololens.md)의 모범 사례를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-174">To best configure the environment for tracking success, you can read best practices in this [post](environment-considerations-for-hololens.md).</span></span>

<span data-ttu-id="34e5d-175">**대답 웨어하우스 규모 공간 또는 최적화에 대 한 추적을 포함 하는 특정 미묘한 차이이 있나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-175">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="34e5d-176">A: 다음은 보다 안정적인 추적 볼륨을 가져오는 데 도움이 될 수 있는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-176">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="34e5d-177">여러 위치에서 겹치는 공간에 다양 한 기능을 제공 하면 추적 시스템에서 고정 잠금을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-177">Providing a variety of features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="34e5d-178">실선 윤곽선 스타일 선을 사용 하는 대신 임의 페인트 splatters 및 해칭을 생각해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="34e5d-178">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="34e5d-179">가능 하면 영역의 동적 조명 범위를 최소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-179">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="34e5d-180">혼합 현실 HMDs의 추적 카메라는 HDR가 아니고 다른 조명을 처리 하기 위해 AGC (자동 게인)와 AEC (자동 노출)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-180">The tracking cameras on our Mixed Reality HMDs are not HDR and have AGC (auto gain) and AEC (auto exposure) going in order to deal with different lighting.</span></span> <span data-ttu-id="34e5d-181">Surface 광원, 패턴 및 대비 분포에 따라, AGC 또는 AEC 중 하나는 "색"과 반대 될 수 있는 기능을 씻어 볼 수 있는 거의 모든 흰색 또는 블랙 실에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-181">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a pretty much all white or black room which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="34e5d-182">밝은 일광 절약 시간제를 사용 하 여 외부 창 앞에서 내부 사진을 가져오는 경우 외부에서 세부 정보를 볼 수 있도록 노출을 조정 하면 내부에 있는 모든 항목이 노출 되지 않으며 검정색이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-182">If you are trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="34e5d-183">또는 내부에 대해 설정 된 경우에는 외부의 모든 항목을 overexposed 하 고 모두 흰색으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-183">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="34e5d-184">추적 카메라의 AEC/AGC를 혼동 하는 경우 추적 카메라를 원인 수 있는 경우에도 공간 (오버 헤드)에 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-184">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="34e5d-185">평평 하 고 확산 되는 조명.</span><span class="sxs-lookup"><span data-stu-id="34e5d-185">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="34e5d-186">혼합 현실 클라우드 서비스 및 AZURE</span><span class="sxs-lookup"><span data-stu-id="34e5d-186">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="34e5d-187">**대답 비즈니스 규모를 어떻게 지원 Microsoft Azure 있나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-187">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="34e5d-188">A: Azure를 기반으로 하는 온사이트 및 원격 관리를 사용 하면 비즈니스에서 데이터를 기반으로 하 고 운영 비용을 절감 하며 기존 및 새 위치에서 배포를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-188">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="34e5d-189">Azure Storage, Azure Functions, App Service, Azure 네트워킹 및 IOT Hub와 같은 azure 클라우드 서비스는 다음과 같은 사용 사례를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-189">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="34e5d-190">원격 장치 배포 & 관리</span><span class="sxs-lookup"><span data-stu-id="34e5d-190">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="34e5d-191">실시간 온사이트 분석</span><span class="sxs-lookup"><span data-stu-id="34e5d-191">Real Time Onsite Analytics</span></span> 

<span data-ttu-id="34e5d-192">지능적으로 조정 가능한 LBE 게임</span><span class="sxs-lookup"><span data-stu-id="34e5d-192">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="34e5d-193">LBE 콘텐츠 스트리밍 및 배포</span><span class="sxs-lookup"><span data-stu-id="34e5d-193">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="34e5d-194">LBE 플레이어 기본 설정 열 지도</span><span class="sxs-lookup"><span data-stu-id="34e5d-194">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="34e5d-195">LBE 예약 및 예약 시스템</span><span class="sxs-lookup"><span data-stu-id="34e5d-195">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="34e5d-196">**대답 대량 공간에 배포할 공간 MMOG를 개발 합니다. 내 콘텐츠 및 개체 지 속성을 관리 하는 데 도움이 되는 모든 서비스**</span><span class="sxs-lookup"><span data-stu-id="34e5d-196">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="34e5d-197">A: Azure 공간 앵커는 HoloLens, iOS 및 Android 장치에서 여러 사용자가 공간적으로 사용할 수 있는 혼합 현실 환경을 사용할 수 있도록 하는 새로운 혼합 현실 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-197">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS and Android devices.</span></span> <span data-ttu-id="34e5d-198">[여기](https://azure.microsoft.com/en-us/services/spatial-anchors/)에서 Azure 공간 앵커에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-198">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com/en-us/services/spatial-anchors/).</span></span>

<span data-ttu-id="34e5d-199">**대답. Microsoft는 다양 한 플레이어 환경을 전문적으로 활용 하 고 있으며 콘텐츠 및 프런트 엔드 개발에 대 한 개발 시간에 집중 하고자 합니다. 백 엔드 개발을 부트스트랩 하거나 오프 로드 하는 데 도움이 되는 제품이 있나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-199">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="34e5d-200">A: Azure PlayFab은 라이브 게임을 위한 완벽 한 백 엔드 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-200">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="34e5d-201">[여기](https://playfab.com/)에서 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-201">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="34e5d-202">기타</span><span class="sxs-lookup"><span data-stu-id="34e5d-202">Misc</span></span>

<span data-ttu-id="34e5d-203">**대답 SteamVR를 사용 하 여 내 환경을 배포 합니다. Windows Mixed Reality가 SteamVR에서 작동 하나요?**</span><span class="sxs-lookup"><span data-stu-id="34e5d-203">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="34e5d-204">A: SteamVR에 대 한 windows Mixed Reality를 사용 하면 사용자가 Windows Mixed Reality 모던 헤드셋에서 SteamVR 환경을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-204">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="34e5d-205">WMR with SteamVR에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34e5d-205">Learn more about SteamVR with WMR [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="34e5d-206">지원 및 커뮤니티</span><span class="sxs-lookup"><span data-stu-id="34e5d-206">Support and community</span></span>  

<span data-ttu-id="34e5d-207">다음은 팀의 실무 전문가와 관련 된 몇 가지 유용한 리소스입니다. 문제 해결 지원을 받고 광범위 한 mixed reality 개발자 커뮤니티에 기여 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-207">Below are a few helpful resources to engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="34e5d-208">공개적으로 릴리스된 기능에 문제가 발생 하는 경우 피드백 허브를 사용 하 여 버그를 작성 하세요. 자세한 내용은이 [페이지](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34e5d-208">If you run into issues with any publicly released features, please file a bug using Feedback Hub.For guidance, please refer to this [page](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="34e5d-209">WMR에 대 한 추가 문제 해결 도움말을 보려면 [지원 요청](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)을 제출 하 여 고객 지원 팀에 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="34e5d-209">For additional troubleshooting help with WMR please get in touch with our customer support team by filing a [support request](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).</span></span>

<span data-ttu-id="34e5d-210">HoloDevelopers 여유 시간 채널에 참여 하 여 팀의 혼합 현실 및 실무 전문가를 대상으로 하는 개발자에 게 참여 하세요. [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="34e5d-210">Join our HoloDevelopers Slack channel to engage with the developers working on mixed reality and subject matter experts from the team: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="34e5d-211">Twitter Microsoft의 혼합 현실 개발자 관계 팀에 따라 뉴스, 이벤트 및 업데이트를 따르세요.@MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="34e5d-211">Twitter: Follow our Mixed Reality Developer Relations team for news, events and updates @MxdRealityDev</span></span> 

<span data-ttu-id="34e5d-212">샌프란시스코와 관련 하 여 발생 하는 경우 항상 Microsoft Reactor에서 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-212">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="34e5d-213">이벤트 일정은 [여기](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e5d-213">You can see our calendar of events [here](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco).</span></span>