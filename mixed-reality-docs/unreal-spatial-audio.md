---
title: Unreal의 공간 오디오
description: Unreal 엔진용 공간 오디오 플러그 인에 대한 개요입니다.
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 스트리밍, 원격, 혼합 현실, 개발, 시작, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 특징, 홀로그램, 게임 개발
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446814"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="8794d-104">Unreal의 공간 오디오</span><span class="sxs-lookup"><span data-stu-id="8794d-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="8794d-105">개요</span><span class="sxs-lookup"><span data-stu-id="8794d-105">Overview</span></span>

<span data-ttu-id="8794d-106">시각과 달리 인간은 360도 서라운드 사운드로 들을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="8794d-107">공간 음향은 인간의 청력이 작동하는 방식을 에뮬레이트하여 세계 좌표 공간에서의 소리 위치를 식별하는 데 필요한 신호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="8794d-108">공간 음향을 혼합 현실 애플리케이션에 추가하면 사용자가 경험하는 몰입도가 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="8794d-109">고품질 공간 음향 처리는 복잡하므로 HoloLens 2에는 이러한 소리 개체를 처리하기 위한 전용 하드웨어가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="8794d-110">이 하드웨어 처리 지원에 액세스하려면 먼저 **MicrosoftSpatialSound** 플러그 인을 Unreal 프로젝트에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="8794d-111">이 문서에서는 해당 플러그 인을 설치하고 구성하는 과정을 안내하고, Unreal 엔진에서 공간 음향을 사용하는 데 필요한 더 자세한 리소스를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span> 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="8794d-112">MicrosoftSpatialSound 플러그 인 설치</span><span class="sxs-lookup"><span data-stu-id="8794d-112">Installing the Microsoft Spatial Sound plugin</span></span> 

<span data-ttu-id="8794d-113">공간 음향을 프로젝트에 추가하는 첫 번째 단계는 MicrosoftSpatialSound 플러그 인을 설치하는 것이며, 이 플러그 인은 다음을 수행하여 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span> 

1. <span data-ttu-id="8794d-114">**편집 > 플러그 인**을 차례로 클릭하고, 검색 상자에서 **MicrosoftSpatialSound**를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span> 
2. <span data-ttu-id="8794d-115">**MicrosoftSpatialSound** 플러그 인에서 **사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span> 
3. <span data-ttu-id="8794d-116">플러그 인 페이지에서 **지금 다시 시작**을 선택하여 Unreal 편집기를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span> 

> [!NOTE]
> <span data-ttu-id="8794d-117">아직 설치하지 않은 경우 Unreal 자습서 시리즈의 **[프로젝트 초기화](unreal-uxt-ch2.md)** 섹션에 있는 지침에 따라 **Microsoft Windows Mixed Reality** 및 **HoloLens** 플러그 인을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Unreal 공간 오디오 플러그 인](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="8794d-119">편집기가 다시 시작되면 프로젝트가 모두 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="8794d-120">HoloLens 2 플랫폼용 공간화 플러그 인 설정</span><span class="sxs-lookup"><span data-stu-id="8794d-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="8794d-121">공간화 플러그 인은 플랫폼별로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="8794d-122">다음을 수행하여 HoloLens 2용 MicrosoftSpatialSound 플러그 인을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="8794d-123">**편집 > 프로젝트 설정**을 차례로 선택하고, **플랫폼**으로 스크롤하여 **HoloLens**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-123">Selecting **Edit > Project Settings**, scrolling to **Platforms** and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="8794d-124">**오디오** 속성을 펼치고, **공간화 플러그 인** 필드를 **MicrosoftSpatialSound**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![HoloLens 플랫폼용 공간화 플러그 인](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="8794d-126">데스크톱 PC의 Unreal 편집기에서 애플리케이션을 미리 보려면 **Windows** 플랫폼에 대해 위의 단계를 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Windows 플랫폼용 공간화 플러그 인](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="8794d-128">워크스테이션에서 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="8794d-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="8794d-129">데스크톱 버전의 Windows에서는 기본적으로 공간 오디오를 사용하지 않도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="8794d-130">다음을 수행하여 이를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-130">You can enable it by:</span></span>
* <span data-ttu-id="8794d-131">작업 표시줄에서 마우스 오른쪽 단추로 **볼륨** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-131">Right-clicking on the **volume** icon in the task bar.</span></span> 
    + <span data-ttu-id="8794d-132">HoloLens 2에서 듣는 콘텐츠를 가장 잘 표현하려면 **공간 음향 -> 헤드폰용 Windows Sonic**을 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![공간화 플러그 인](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="8794d-134">이 설정은 Unreal 편집기에서 프로젝트를 테스트하려는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="8794d-135">감쇠 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="8794d-135">Creating Attenuation objects</span></span>
<span data-ttu-id="8794d-136">필요한 플러그 인이 설치되고 구성되면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="8794d-137">**행위자 배치** 창에서 **주변 소리** 행위자를 검색하여 **장면** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![주변 소리 행위자 추가](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="8794d-139">**주변 소리** 행위자를 장면에서 시각적 요소의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span> 
    * <span data-ttu-id="8794d-140">주변 소리 행위자는 기본적으로 시각적 표현을 제공하지 않으므로 장면의 위치에서 소리만 들을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="8794d-141">시각적 요소에 연결하면 다른 자산처럼 행위자를 보고 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="8794d-142">마우스 오른쪽 단추로 **콘텐츠 브라우저**를 클릭하고, **고급 자산 만들기 -> 소리 -> 소리 감쇠**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![소리 감쇠 자산 만들기](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="8794d-144">**콘텐츠 브라우저** 창에서 마우스 오른쪽 단추로 **소리 감쇠** 자산을 클릭하고, **편집** 옵션을 선택하여 속성 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="8794d-145">**공간화 메서드**를 **Binaural(입체 음향)** 로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-145">Switch the **Spatialization Method** to **Binaural**.</span></span>

![공간화 메서드 설정](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="8794d-147">**주변 소리** 행위자를 선택하고, **세부 정보** 패널에서 **감쇠** 섹션까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span> 
    * <span data-ttu-id="8794d-148">**감쇠 설정** 속성을 만든 **소리 감쇠** 자산으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![감쇠 설정](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="8794d-150">사용할 SoundAsset 파일을 지정하도록 주변 소리 행위자의 **소리** 속성을 업데이트하여 주변 소리 행위자에 연결하려는 **소리 자산**을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![소리 자산 설정](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> <span data-ttu-id="8794d-152">MicrosoftSpatialSound 플러그 인을 사용하여 공간화하려면 SoundAsset 파일이 모노여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="8794d-153">아래 스크린샷과 같이 콘텐츠 브라우저 창에서 마우스로 자산 위를 가리키면 소리 파일의 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![새 소리 감쇠 자산](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="8794d-155">이러한 모든 설정이 구성되면 HoloLens 2의 전용 하드웨어 오프로드 지원을 사용하여 주변 소리를 공간화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="8794d-156">공간화 개체 구성</span><span class="sxs-lookup"><span data-stu-id="8794d-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="8794d-157">공간 오디오를 사용한다는 것은 가상 환경에서 소리가 작동하는 방식을 관리해야 한다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="8794d-158">주요 초점은 사용자가 가까이 있을 때는 더 크게 표시되고, 멀리 있을 때는 더 조용하게 표시되는 소리 개체를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="8794d-159">이를 소리 감쇠라고 하며, 소리가 고정된 지점에 있는 것처럼 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="8794d-160">모든 감쇠 개체에는 다음에 대한 수정 가능한 설정이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="8794d-161">거리</span><span class="sxs-lookup"><span data-stu-id="8794d-161">Distance</span></span>
* <span data-ttu-id="8794d-162">공간화</span><span class="sxs-lookup"><span data-stu-id="8794d-162">Spatialization</span></span>
* <span data-ttu-id="8794d-163">공기 흡수</span><span class="sxs-lookup"><span data-stu-id="8794d-163">Air Absorption</span></span>
* <span data-ttu-id="8794d-164">수신기 포커스</span><span class="sxs-lookup"><span data-stu-id="8794d-164">Listener Focus</span></span>
* <span data-ttu-id="8794d-165">반향 보내기</span><span class="sxs-lookup"><span data-stu-id="8794d-165">Reverb Send</span></span>
* <span data-ttu-id="8794d-166">폐색</span><span class="sxs-lookup"><span data-stu-id="8794d-166">Occlusion</span></span>

<span data-ttu-id="8794d-167">[Unreal의 소리 감쇠](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)에는 이러한 각 항목에 대한 세부 정보와 구현이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8794d-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>


## <a name="see-also"></a><span data-ttu-id="8794d-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8794d-168">See also</span></span>
* [<span data-ttu-id="8794d-169">공간 음향</span><span class="sxs-lookup"><span data-stu-id="8794d-169">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="8794d-170">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="8794d-170">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="8794d-171">MR 공간 220: 공간 음향</span><span class="sxs-lookup"><span data-stu-id="8794d-171">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)