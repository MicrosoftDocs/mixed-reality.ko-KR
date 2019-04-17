---
title: Spectator 보기
description: 외부 장치에서 홀로그램 혼합된 현실 환경 비디오 녹화 또는 외장 디스플레이에서 혼합된 현실 경험을 보여 주는 수단으로 시각화 합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: IPad, iPhone, iOS spectator 보기 OpenCV, 카메라, ARKit, HoloLens, 혼합 현실, MixedRealityToolkit, 데모, 레코드
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602270"
---
# <a name="spectator-view-for-hololens"></a><span data-ttu-id="79375-104">HoloLens spectator 보기</span><span class="sxs-lookup"><span data-stu-id="79375-104">Spectator View for HoloLens</span></span>

![표식](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a><span data-ttu-id="79375-106">현재 리팩터링</span><span class="sxs-lookup"><span data-stu-id="79375-106">Current Refactor</span></span>

> [!NOTE]
><span data-ttu-id="79375-107">HoloLens spectator 보기 적극적으로 리팩터링하려 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-107">Spectator View for HoloLens is being actively refactored.</span></span> <span data-ttu-id="79375-108">이 작업은 미리 보기 통합 및 Pro 코드 베이스 되며 HoloLens 2 지원을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-108">This work is intended to consolidate the Preview and Pro codebases and extend support to HoloLens 2.</span></span> 

<span data-ttu-id="79375-109">현재 보려는 Spectator 보기 리팩터링 상태의 MixedRealityToolkit와 MixedRealityToolkit Unity 리포지토리에서 ' 기능/spectatorView ' 분기를 확인:</span><span class="sxs-lookup"><span data-stu-id="79375-109">To view the current state of the Spectator View refactor see 'feature/spectatorView' branches in both the MixedRealityToolkit and MixedRealityToolkit-Unity repos:</span></span>

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

<span data-ttu-id="79375-110">및</span><span class="sxs-lookup"><span data-stu-id="79375-110">and</span></span>

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a><span data-ttu-id="79375-111">개요</span><span class="sxs-lookup"><span data-stu-id="79375-111">Overview</span></span>

<span data-ttu-id="79375-112">HoloLens, 착용 하는 경우에서는 것을 잊어버릴 경우가 있는 사용자 수 일어날 수 없는 없는 것.</span><span class="sxs-lookup"><span data-stu-id="79375-112">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="79375-113">Spectator 보기를 통해 다른 사람에 게는 2D 화면의 해당 환경에서 보게 HoloLens 사용자.</span><span class="sxs-lookup"><span data-stu-id="79375-113">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="79375-114">Spectator 보기 (미리 보기)는 홀로그램 HD, Spectator 보기 Pro를 위한 것 홀로그램 전문가 품질 기록 하는 동안 기록에 빠르고 경제적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-114">Spectator View (Preview) is fast and affordable approach to recording holograms in HD, while Spectator View Pro is intended for professional quality recording of holograms.</span></span>

<span data-ttu-id="79375-115">다음 표에서 옵션 및 해당 기능을 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79375-115">The following table shows both options and their capabilities.</span></span> <span data-ttu-id="79375-116">비디오 녹화 요구에 가장 잘 맞는 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-116">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="79375-117">Spectator 보기 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="79375-117">Spectator View (Preview)</span></span> |              <span data-ttu-id="79375-118">Spectator 보려면 Pro</span><span class="sxs-lookup"><span data-stu-id="79375-118">Spectator View Pro</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="79375-119">HD 품질</span><span class="sxs-lookup"><span data-stu-id="79375-119">HD quality</span></span>                         |         <span data-ttu-id="79375-120">Full HD</span><span class="sxs-lookup"><span data-stu-id="79375-120">Full HD</span></span>         |        <span data-ttu-id="79375-121">(따라 DSLR) filming 전문가 품질</span><span class="sxs-lookup"><span data-stu-id="79375-121">Professional quality filming (as determined by DSLR)</span></span>      |
| <span data-ttu-id="79375-122">쉽게 카메라 이동</span><span class="sxs-lookup"><span data-stu-id="79375-122">Easy camera movement</span></span>                      |            <span data-ttu-id="79375-123">✔</span><span class="sxs-lookup"><span data-stu-id="79375-123">✔</span></span>            |                                             |
| <span data-ttu-id="79375-124">3 인칭 보기</span><span class="sxs-lookup"><span data-stu-id="79375-124">Third-person view</span></span>                    |            <span data-ttu-id="79375-125">✔</span><span class="sxs-lookup"><span data-stu-id="79375-125">✔</span></span>            |                      <span data-ttu-id="79375-126">✔</span><span class="sxs-lookup"><span data-stu-id="79375-126">✔</span></span>                      |
| <span data-ttu-id="79375-127">화면에 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-127">Can be streamed to screens</span></span>           |            <span data-ttu-id="79375-128">✔</span><span class="sxs-lookup"><span data-stu-id="79375-128">✔</span></span>            |                      <span data-ttu-id="79375-129">✔</span><span class="sxs-lookup"><span data-stu-id="79375-129">✔</span></span>                      |
| <span data-ttu-id="79375-130">이식 가능</span><span class="sxs-lookup"><span data-stu-id="79375-130">Portable</span></span>                             |            <span data-ttu-id="79375-131">✔</span><span class="sxs-lookup"><span data-stu-id="79375-131">✔</span></span>            |                                             |
| <span data-ttu-id="79375-132">무선</span><span class="sxs-lookup"><span data-stu-id="79375-132">Wireless</span></span>                             |            <span data-ttu-id="79375-133">✔</span><span class="sxs-lookup"><span data-stu-id="79375-133">✔</span></span>            |                                             |
| <span data-ttu-id="79375-134">추가 필수 하드웨어</span><span class="sxs-lookup"><span data-stu-id="79375-134">Additional required hardware</span></span>         |     <span data-ttu-id="79375-135">iPhone (또는 iPad)</span><span class="sxs-lookup"><span data-stu-id="79375-135">iPhone (or iPad)</span></span>    | <span data-ttu-id="79375-136">HoloLens + Rig + 삼각대 + DSLR + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="79375-136">HoloLens + Rig + Tripod + DSLR + PC + Unity</span></span> |
| <span data-ttu-id="79375-137">하드웨어 투자</span><span class="sxs-lookup"><span data-stu-id="79375-137">Hardware investment</span></span>                  |           <span data-ttu-id="79375-138">낮음</span><span class="sxs-lookup"><span data-stu-id="79375-138">Low</span></span>           |                     <span data-ttu-id="79375-139">높음</span><span class="sxs-lookup"><span data-stu-id="79375-139">High</span></span>                    |
| <span data-ttu-id="79375-140">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="79375-140">Cross-platform</span></span>                       |           <span data-ttu-id="79375-141">iOS</span><span class="sxs-lookup"><span data-stu-id="79375-141">iOS</span></span>           |                                             |
| <span data-ttu-id="79375-142">뷰어 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-142">Viewer can interact</span></span>                  |            <span data-ttu-id="79375-143">✔</span><span class="sxs-lookup"><span data-stu-id="79375-143">✔</span></span>            |                                             |
| <span data-ttu-id="79375-144">네트워킹 필요 (UNET 스크립팅)</span><span class="sxs-lookup"><span data-stu-id="79375-144">Networking required (UNET scripting)</span></span> |            <span data-ttu-id="79375-145">✔</span><span class="sxs-lookup"><span data-stu-id="79375-145">✔</span></span>            |                      <span data-ttu-id="79375-146">✔</span><span class="sxs-lookup"><span data-stu-id="79375-146">✔</span></span>                      |
| <span data-ttu-id="79375-147">런타임 설치 기간</span><span class="sxs-lookup"><span data-stu-id="79375-147">Runtime setup duration</span></span>               |         <span data-ttu-id="79375-148">인스턴트</span><span class="sxs-lookup"><span data-stu-id="79375-148">Instant</span></span>         |                     <span data-ttu-id="79375-149">슬로우</span><span class="sxs-lookup"><span data-stu-id="79375-149">Slow</span></span>                    |

## <a name="spectator-view-preview"></a><span data-ttu-id="79375-150">Spectator 보기 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="79375-150">Spectator View (Preview)</span></span>

![표식](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a><span data-ttu-id="79375-152">사용 사례</span><span class="sxs-lookup"><span data-stu-id="79375-152">Use cases</span></span>

- <span data-ttu-id="79375-153">HD에서 filming 홀로그램: Spectator 보기 (미리 보기)를 사용 하는 iPhone을 사용 하 여 혼합된 현실 경험을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-153">Filming holograms in HD: Using Spectator View (Preview), you can record a mixed reality experience using an iPhone.</span></span> <span data-ttu-id="79375-154">Full HD에서 기록 하 고 홀로그램 및 그림자에 앤티앨리어싱을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-154">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="79375-155">홀로그램 비디오를 캡처하는 비용 효율적이 고 빠른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-155">It is a cost-effective and quick way to capture video of holograms.</span></span>
- <span data-ttu-id="79375-156">라이브 데모: Stream 라이브 혼합된 현실 iPhone 또는 iPad를 지연 없는에서 직접 Apple TV에 환경을!</span><span class="sxs-lookup"><span data-stu-id="79375-156">Live demos: Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
- <span data-ttu-id="79375-157">게스트를 사용 하 여 환경을 공유 합니다. HoloLens가 아닌 사용자가 휴대폰 또는 태블릿에서 직접 홀로그램 환경 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-157">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

### <a name="current-features"></a><span data-ttu-id="79375-158">현재 기능</span><span class="sxs-lookup"><span data-stu-id="79375-158">Current features</span></span>

- <span data-ttu-id="79375-159">휴대폰을 세션에 추가 하는 것에 대 한 자동 검색을 네트워크입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-159">Network auto-discovery for adding phones to the session.</span></span>
- <span data-ttu-id="79375-160">사용자가 올바른 세션에 추가 되므로 자동 세션 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-160">Automatic session handling, so users are added to the correct session.</span></span>
- <span data-ttu-id="79375-161">공간 홀로그램, 홀로그램 정확히 동일한 위치에서 모든 사용자가 표시 되도록 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-161">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
- <span data-ttu-id="79375-162">iOS (ARKit 사용 가능 장치)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-162">iOS support (ARKit-enabled devices).</span></span>
- <span data-ttu-id="79375-163">여러 iOS 게스트입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-163">Multiple iOS guests.</span></span>
- <span data-ttu-id="79375-164">비디오 + 홀로그램 + 앰비언트 사운드 + 홀로그램 소리를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-164">Recording of video + holograms + ambient sound + hologram sound.</span></span>
- <span data-ttu-id="79375-165">비디오를 저장,를 전자 메일로 보내거나 다른 지원 앱과 공유할 수 있도록 시트를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-165">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>


>[!NOTE] 
><span data-ttu-id="79375-166">Spectator 보기 Pro 버전 코드를 사용 하 여 Spectator 보기 (미리 보기) 코드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-166">The Spectator View (Preview) code cannot be used with the Spectator View Pro version code.</span></span> <span data-ttu-id="79375-167">홀로그램의 비디오 기록을 필요한 경우 새 프로젝트에서 구현 하는 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-167">We recommend to implement it in new projects where video recording of holograms is required.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a><span data-ttu-id="79375-168">라이선스</span><span class="sxs-lookup"><span data-stu-id="79375-168">Licenses</span></span>

- [<span data-ttu-id="79375-169">OpenCV-(3 절 BSD 라이선스)</span><span class="sxs-lookup"><span data-stu-id="79375-169">OpenCV - (3-clause BSD License)</span></span>](https://opencv.org/license.html)
- [<span data-ttu-id="79375-170">Unity ARKit-(MIT 라이선스)</span><span class="sxs-lookup"><span data-stu-id="79375-170">Unity ARKit - (MIT License)</span></span>](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a><span data-ttu-id="79375-171">Spectator 보기 (미리 보기)를 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="79375-171">How to set up Spectator View (Preview)</span></span>

### <a name="requirements"></a><span data-ttu-id="79375-172">요구 사항</span><span class="sxs-lookup"><span data-stu-id="79375-172">Requirements</span></span>

- <span data-ttu-id="79375-173">[Spectator 보기 플러그 인 및 필요한 OpenCV 이진 파일](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) -아래 Spectator 보기 기본 플러그 인을 빌드하는 방법에 대 한 세부 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-173">[Spectator View plugin and required OpenCV binaries](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) - Details on how to build the Spectator View Native Plugin can be found below.</span></span> <span data-ttu-id="79375-174">생성 된 이진 파일에서 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-174">From the generated binaries you will need:</span></span>

    - <span data-ttu-id="79375-175">opencv_aruco343.dll</span><span class="sxs-lookup"><span data-stu-id="79375-175">opencv_aruco343.dll</span></span>
    - <span data-ttu-id="79375-176">opencv_calib3d343.dll</span><span class="sxs-lookup"><span data-stu-id="79375-176">opencv_calib3d343.dll</span></span>
    - <span data-ttu-id="79375-177">opencv_core343.dll</span><span class="sxs-lookup"><span data-stu-id="79375-177">opencv_core343.dll</span></span>
    - <span data-ttu-id="79375-178">opencv_features2d343.dll</span><span class="sxs-lookup"><span data-stu-id="79375-178">opencv_features2d343.dll</span></span>
    - <span data-ttu-id="79375-179">opencv_flann343.dll</span><span class="sxs-lookup"><span data-stu-id="79375-179">opencv_flann343.dll</span></span>
    - <span data-ttu-id="79375-180">opencv_imgproc343.dll</span><span class="sxs-lookup"><span data-stu-id="79375-180">opencv_imgproc343.dll</span></span>

    - <span data-ttu-id="79375-181">zlib1.dll</span><span class="sxs-lookup"><span data-stu-id="79375-181">zlib1.dll</span></span>
    - <span data-ttu-id="79375-182">SpectatorViewPlugin.dll</span><span class="sxs-lookup"><span data-stu-id="79375-182">SpectatorViewPlugin.dll</span></span>
- <span data-ttu-id="79375-183">Spectator 뷰는 해당 네트워크 검색 및 공간 동기화에 대 한 Unity 네트워킹 (UNET)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-183">Spectator View uses Unity Networking (UNET) for its network discovery and spatial syncing.</span></span> <span data-ttu-id="79375-184">즉 장치 간에 동기화를 적용 하는 동안 모든 상호 작용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-184">This means all interactivity during the application needs to be synced between the devices.</span></span>
- <span data-ttu-id="79375-185">Unity 2017.2.1p2 이상</span><span class="sxs-lookup"><span data-stu-id="79375-185">Unity 2017.2.1p2 or later</span></span>
- <span data-ttu-id="79375-186">하드웨어</span><span class="sxs-lookup"><span data-stu-id="79375-186">Hardware</span></span>
    - <span data-ttu-id="79375-187">HoloLens</span><span class="sxs-lookup"><span data-stu-id="79375-187">A HoloLens</span></span>
    - <span data-ttu-id="79375-188">Windows 10을 실행 하는 Windows PC</span><span class="sxs-lookup"><span data-stu-id="79375-188">Windows PC running Windows 10</span></span>
    - <span data-ttu-id="79375-189">ARKit 호환 장치 (iPhone 6s부터 / iPad Pro 2016부터 / iPad 2017 이상)-iOS 11 실행 이상</span><span class="sxs-lookup"><span data-stu-id="79375-189">ARKit compatible device (iPhone 6s onwards / iPad Pro 2016 onwards / iPad 2017 onwards) - running iOS 11 or above</span></span>
    - <span data-ttu-id="79375-190">부터 xcode 9.2 사용 하 여 Mac</span><span class="sxs-lookup"><span data-stu-id="79375-190">Mac with xcode 9.2 onwards</span></span>
- <span data-ttu-id="79375-191">Apple 개발자 계정, 평가판 또는 [유료](https://developer.apple.com/)</span><span class="sxs-lookup"><span data-stu-id="79375-191">Apple developer account, free or [paid](https://developer.apple.com/)</span></span>
- <span data-ttu-id="79375-192">Microsoft Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="79375-192">Microsoft Visual Studio 2017</span></span>

### <a name="building-the-spectator-view-native-plugin"></a><span data-ttu-id="79375-193">Spectator 보기 기본 플러그 인 작성</span><span class="sxs-lookup"><span data-stu-id="79375-193">Building the Spectator View native plugin</span></span>

<span data-ttu-id="79375-194">필요한 파일을 생성 하려면 다음이 단계를 수행 합니다. https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md</span><span class="sxs-lookup"><span data-stu-id="79375-194">To generate the required files, follow these steps: https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md</span></span>

### <a name="project-setup"></a><span data-ttu-id="79375-195">프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="79375-195">Project setup</span></span>

1. <span data-ttu-id="79375-196">장면 준비, 전 세계 루트 gameobject 아래에 포함 된 장면 내 모든 보이는 gameobject를 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-196">Prepare your scene, ensuring all visable gameobjects within your scene are contained under a world root gameobject.</span></span>

    ![전 세계 루트](images/SpecViewPhoneWorldRoot2.PNG)

2. <span data-ttu-id="79375-198">SpectatorView prefab 추가 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) 장면에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-198">Add the SpectatorView prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) into your scene.</span></span>
3. <span data-ttu-id="79375-199">SpectatorViewNetworking prefab 추가 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) 장면에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-199">Add the SpectatorViewNetworking prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) into your scene.</span></span>
4. <span data-ttu-id="79375-200">SpectatorViewNetworking gameobject를 선택 하 고 SpectatorViewNetworkingManager 구성 요소에는 몇 가지 항목을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-200">Select the SpectatorViewNetworking gameobject and on the SpectatorViewNetworkingManager component, there's a few things you can link up.</span></span> <span data-ttu-id="79375-201">왼쪽에 그대로 유지 하는 경우 필요한 스크립트 런타임 시이 구성 요소 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-201">If left untouched this component will search for necessary scripts at runtime.</span></span>
    - <span data-ttu-id="79375-202">Marker Detection HoloLens -> SpectatorView/Hololens/MarkerDetection</span><span class="sxs-lookup"><span data-stu-id="79375-202">Marker Detection HoloLens -> SpectatorView/Hololens/MarkerDetection</span></span>
    - <span data-ttu-id="79375-203">표식을 생성 3D SpectatorView/IPhone/SyncMarker/3DMarker-></span><span class="sxs-lookup"><span data-stu-id="79375-203">Marker Generation 3D -> SpectatorView/IPhone/SyncMarker/3DMarker</span></span>

    ![SpectatorView 네트워크 검색](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a><span data-ttu-id="79375-205">앱 네트워킹</span><span class="sxs-lookup"><span data-stu-id="79375-205">Networking your app</span></span>

- <span data-ttu-id="79375-206">Spectator UNET를 사용 하 여 해당 네트워킹에 대 한 뷰와 사용자를 위해 모든 호스트 클라이언트 연결을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-206">Spectator View uses UNET for its networking and manages all host-client connections for you.</span></span>
- <span data-ttu-id="79375-207">앱 특정 데이터를 동기화 하 고 예를 들어 SyncVars NetworkTransform, NetworkBehavior를 사용 하 여 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-207">Any app specific data has to be synced and implemented by you, using e.g. SyncVars, NetworkTransform, NetworkBehavior.</span></span>
- <span data-ttu-id="79375-208">Unity 네트워킹에 대 한 자세한 내용은 참조 하십시오 [멀티 플레이 게임 및 네트워킹](https://docs.unity3d.com/Manual/UNet.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-208">For more information on Unity Networking please visit [Multiplayer and Networking](https://docs.unity3d.com/Manual/UNet.html).</span></span> <span data-ttu-id="79375-209">(참고: UNet는 더 이상 사용 되지 않습니다. 이 문제를 해결 Spectator 보기 코드 베이스의 현재 리팩터링)</span><span class="sxs-lookup"><span data-stu-id="79375-209">(Note: UNet has been deprecated; the current refactor of the Spectator View codebase will address this issue)</span></span>

### <a name="building-for-each-platform-hololens-or-ios"></a><span data-ttu-id="79375-210">각 플랫폼 (HoloLens 또는 iOS)</span><span class="sxs-lookup"><span data-stu-id="79375-210">Building for each platform (HoloLens or iOS)</span></span>

- <span data-ttu-id="79375-211">IOS 용으로 빌드하 하는 경우 이것은 아직이 플랫폼과 호환 MRTK의 GLTF 구성 요소를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-211">When building for iOS, ensure you remove the GLTF component of MRTK as this is not yet compatible with this platform.</span></span>
- <span data-ttu-id="79375-212">SpectatorView prefab의 최상위 수준에 ' 플랫폼 Switcher' 라는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-212">At the top level of the SpectatorView prefab there is a component called 'Platform Switcher'.</span></span> <span data-ttu-id="79375-213">에 대 한 빌드 하려는 플랫폼을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-213">Select the platform you want to build for.</span></span>
    - <span data-ttu-id="79375-214">'Hololens'를 선택 하는 경우 iPhone gameobject 비활성화 될 SpectatorView prefab의 아래에 있는 모든 gameobject 및 'Hololens' 활성화에서 모든 gameobject 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-214">If selecting 'Hololens' you should see all gameobjects beneath the iPhone gameobject in the SpectatorView prefab become inactive and all the gameobjects under 'Hololens' become active.</span></span>
    - <span data-ttu-id="79375-215">플랫폼에 따라 선택 하 여는 HoloToolkit 되 잠시 걸릴 수 있습니다이 프로젝트에서 추가 또는 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-215">This can take a little while as depending on the platform you choose the HoloToolkit is being added or removed from the project.</span></span>

    ![플랫폼 전환기](images/SpecViewPhoneSwitcher.PNG)

- <span data-ttu-id="79375-217">Unity 사용 하 여 확인할 수 없는 문제로 인해 같은 Unity 편집기 인스턴스 (간의 닫지 Unity 빌드 안 함)를 사용 하 여 응용 프로그램의 모든 버전을 빌드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-217">Ensure you build all versions of the application using the same Unity editor instance (do not close Unity between builds) due to an unresolved issue with Unity.</span></span>

### <a name="running-your-app"></a><span data-ttu-id="79375-218">앱 실행</span><span class="sxs-lookup"><span data-stu-id="79375-218">Running your app</span></span>

<span data-ttu-id="79375-219">작성 하 고 응용 프로그램 및 HoloLens iPhone에서의 버전을 배포 후에 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-219">Once you have built and deployed a version of you application on iPhone and on HoloLens, you should be able to connect them.</span></span>

1. <span data-ttu-id="79375-220">장치와 같은 Wi-fi 네트워크에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-220">Ensure that both devices are on the same Wi-Fi network.</span></span>
2. <span data-ttu-id="79375-221">순서에 관계 없이 두 장치에서 응용 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-221">Start the application on the both devices, in no specific order.</span></span> <span data-ttu-id="79375-222">IPhone에서 응용 프로그램을 시작 하는 프로세스를 켜고 사진을 찍을 시작 HoloLens 카메라를 트리거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-222">The process of starting the application on the iPhone should trigger the HoloLens camera to turn on and begin taking pictures.</span></span>
3. <span data-ttu-id="79375-223">IPhone 앱이 시작 되는 즉시 바닥 나 테이블과 같은 표면에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-223">As soon as iPhone app starts, it will look for surfaces like floors or tables.</span></span> <span data-ttu-id="79375-224">화면 발견 되 면 아래와 유사한 표식을 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-224">When surfaces are found, you should see a marker similar to the one below.</span></span> <span data-ttu-id="79375-225">이 마커는 HoloLens를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79375-225">Show this marker to the HoloLens.</span></span>

    ![표식](images/SpecViewPhoneMarker.PNG)

4. <span data-ttu-id="79375-227">표식에 감지 되 면 여는 HoloLens 사라져야 및 두 장치를 연결 하 고이 공간적으로 동기화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-227">Once the marker has been detected by the HoloLens it should disappear and both devices should be connected and spatially synced.</span></span>

### <a name="recording-video"></a><span data-ttu-id="79375-228">비디오 녹화</span><span class="sxs-lookup"><span data-stu-id="79375-228">Recording video</span></span>

1. <span data-ttu-id="79375-229">를 캡처하고 iPhone에서 비디오를 저장 하려면 페이지를 누르고 화면 1 초입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-229">To capture and save a video from the iPhone, tap and hold the screen for 1 second.</span></span> <span data-ttu-id="79375-230">[기록] 메뉴를 열립니다.</span><span class="sxs-lookup"><span data-stu-id="79375-230">This will open the recording menu.</span></span>
2. <span data-ttu-id="79375-231">빨간색 record 단추를 탭, 화면 녹화를 시작 하기 전에 카운트다운이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-231">Tap the red record button, this will start a countdown before beginning to record the screen.</span></span>
3. <span data-ttu-id="79375-232">기록 탭 완료 화면 다른 1 초 동안 보관을 중지 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="79375-232">To finish recording tap and hold the screen for another 1 second, then tap the stop button.</span></span>
4. <span data-ttu-id="79375-233">미리 보기 단추 (파란색 단추)가 나타나지 녹화 한 비디오 로드 되 면 기록 된 비디오를 시청 하려면 탭 하세요.</span><span class="sxs-lookup"><span data-stu-id="79375-233">Once the recorded video loads, a Preview button (blue button) will appear, tap to watch the recorded video.</span></span>
5. <span data-ttu-id="79375-234">카메라 앨범에 저장 하는 선택한 공유 시트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="79375-234">Open the Share sheet and select Save to camera roll.</span></span>

### <a name="example-scene"></a><span data-ttu-id="79375-235">예제 장면</span><span class="sxs-lookup"><span data-stu-id="79375-235">Example scene</span></span>

<span data-ttu-id="79375-236">예제 장면에서 찾을 수 있습니다 [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)</span><span class="sxs-lookup"><span data-stu-id="79375-236">An example scene can be found in [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="79375-237">문제 해결</span><span class="sxs-lookup"><span data-stu-id="79375-237">Troubleshooting</span></span>

<span data-ttu-id="79375-238">**Unity 편집기에는 HoloLens 장치에 의해 호스트 되는 세션에 연결 되지 않는**</span><span class="sxs-lookup"><span data-stu-id="79375-238">**The Unity Editor won't connect to a session hosted by a HoloLens device**</span></span>

- <span data-ttu-id="79375-239">Windows 방화벽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-239">This could be the Windows Firewall.</span></span>
- <span data-ttu-id="79375-240">Windows 방화벽 옵션으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-240">Go to Windows Firewall options.</span></span>
- <span data-ttu-id="79375-241">앱 또는 Windows 방화벽을 통해 기능을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-241">Allow an app or feature through Windows Firewall.</span></span>
- <span data-ttu-id="79375-242">인스턴스에 대 한 모든 목록 틱에서 Unity 편집기의 도메인, 사설 및 공용입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-242">For all instances of Unity Editor in the list tick, Domain, Private and Public.</span></span>
- <span data-ttu-id="79375-243">그런 다음 Windows 방화벽 옵션을 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-243">Then go back to Windows Firewall options.</span></span>
- <span data-ttu-id="79375-244">고급 설정을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-244">Click Advanced settings.</span></span>
- <span data-ttu-id="79375-245">인바운드 규칙을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-245">Click Inbound Rules.</span></span>
- <span data-ttu-id="79375-246">모든 인스턴스가 Unity 편집기의 녹색 틱이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-246">All instances of Unity Editor should have a green tick.</span></span>
- <span data-ttu-id="79375-247">Unity 편집기의 모든 인스턴스에 대 한 녹색 틱이 없는 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-247">For any instances of Unity Editor that don't have a green tick:</span></span>
    - <span data-ttu-id="79375-248">두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-248">Double click it.</span></span>
    - <span data-ttu-id="79375-249">작업 대화 상자에서 연결 허용을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-249">In the action dialog select Allow the connection.</span></span>
    - <span data-ttu-id="79375-250">확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-250">Click OK.</span></span>
    - <span data-ttu-id="79375-251">Unity 편집기를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-251">Restart the Unity Editor.</span></span>

<span data-ttu-id="79375-252">**런타임 시 iPhone 화면에는 "찾기 Floor..."이 표시 됩니다. 하지만 AR 마커를 표시 하지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="79375-252">**At runtime the iPhone screen says "Locating Floor..." but does not display an AR marker.**</span></span>

- <span data-ttu-id="79375-253">IPhone 가로 화면을 가리키는 바닥 이나 테이블 iPhone 카메라를 사용해 서 원하는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-253">The iPhone is looking for a horizontal surface so try pointing the iPhone camera towards the floor or a table.</span></span> <span data-ttu-id="79375-254">이 화면을 HoloLens와 공간적으로 동기화 하는 데 필요한 찾을 ARKit 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-254">This will help ARKit find surfaces necessary to spatially sync with HoloLens.</span></span>

<span data-ttu-id="79375-255">**HoloLens 카메라 본체가 켜지 지 않는다 자동으로 iPhone 하려고 할 때 조인 합니다.**</span><span class="sxs-lookup"><span data-stu-id="79375-255">**HoloLens camera does not turn on automatically when iPhone tries to join.**</span></span>

- <span data-ttu-id="79375-256">HoloLens와 iPhone 같은 Wi-fi 네트워크에서 실행 되 고 있는지 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="79375-256">Make sure both HoloLens and iPhone are running on the same Wi-Fi network.</span></span>

<span data-ttu-id="79375-257">**Spectator 보기 응용 프로그램에 모바일 장치를 시작할 때 다른 Spectator 보기 앱을 실행 하는 다른 hololens 자신의 카메라 설정**</span><span class="sxs-lookup"><span data-stu-id="79375-257">**When launching an Spectator View application on a mobile device, other hololens running other Spectator View apps turn on their camera**</span></span>

- <span data-ttu-id="79375-258">Goto NewDeviceDiscovery 구성 요소 및 두 개의 고유 값에 브로드캐스트 키와 브로드캐스트 포트를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-258">Goto the NewDeviceDiscovery component and change the both the Broadcast Key and Broadcast port to two unique values.</span></span>
- <span data-ttu-id="79375-259">SpectatorViewDiscovery 이동한 다른 고유한 숫자 집합 키 브로드캐스트 및 브로드캐스트 포트를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-259">Go to SpectatorViewDiscovery and change the Broadcast Key and Broadcast port to another set of unique numbers.</span></span>

<span data-ttu-id="79375-260">**HoloLens mac Unity 편집기를 사용 하 여 연결 되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="79375-260">**The HoloLens won't connect with the mac Unity Editor.**</span></span>

- <span data-ttu-id="79375-261">Unity 버전에 연결할 수 있는 알려진된 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-261">This is a known issue which could be linked to the Unity version.</span></span> <span data-ttu-id="79375-262">여전히 건물 iPhone 작동 하 고 정상적으로 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-262">Building to the iPhone should still work and connect as normal.</span></span>

<span data-ttu-id="79375-263">**HoloLens 카메라가 설정 하지만 마커를 검색할 수 없는 합니다.**</span><span class="sxs-lookup"><span data-stu-id="79375-263">**The HoloLens camera turns on but is not able to scan the marker.**</span></span>

- <span data-ttu-id="79375-264">같은 Unity 편집기 인스턴스 (간의 닫지 Unity 빌드 안 함)를 사용 하 여 응용 프로그램의 모든 버전을 빌드하는 것을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-264">Ensure that you build all versions of the application using the same Unity Editor instance (do not close Unity between builds).</span></span> <span data-ttu-id="79375-265">Unity 사용 하 여 알 수 없는 문제 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-265">This is due to an unknown issue with Unity.</span></span>

## <a name="spectator-view-pro"></a><span data-ttu-id="79375-266">Spectator 보려면 Pro</span><span class="sxs-lookup"><span data-stu-id="79375-266">Spectator View Pro</span></span>

![Spectator 뷰 설정](images/spectatorview-300px.png)

<span data-ttu-id="79375-268">Spectator 보기 Pro를 사용 하 여 이러한 네 가지 구성 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-268">Using Spectator View Pro involves these four components:</span></span>
1. <span data-ttu-id="79375-269">기반으로 하는 spectator 보기 위해 특별히 빌드된 앱 [혼합된 현실 환경 공유할](shared-experiences-in-mixed-reality.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-269">An app built specifically to enable spectator view, which is based on [shared experiences in mixed reality](shared-experiences-in-mixed-reality.md).</span></span>
2. <span data-ttu-id="79375-270">사용자가 앱을 사용 하 여 HoloLens 착용입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-270">A user wearing HoloLens using the app.</span></span>
3. <span data-ttu-id="79375-271">Spectator 보기 카메라 rig 3 인칭 관점 비디오를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-271">A spectator view camera rig providing a third-person perspective video.</span></span>
4. <span data-ttu-id="79375-272">Spectator 보기 비디오를 공유할 앱 및 합치기를 홀로그램을 실행 하는 데스크톱 PC.</span><span class="sxs-lookup"><span data-stu-id="79375-272">A desktop PC running the shared experience app and compositing the holograms into a spectator view video.</span></span>

![Spectator 보기 Pro 설정](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a><span data-ttu-id="79375-274">사용 사례</span><span class="sxs-lookup"><span data-stu-id="79375-274">Use cases</span></span>

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


<span data-ttu-id="79375-275">*여전히 이미지, 비디오 클립을 또는 라이브 데모를 보려면이 든 상관 없이 프로그램 holographic 만들기 공유 spectator 보기를 사용할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="79375-275">*Spectator view can be used for sharing your holographic creations, whether they're a still image, a video clip, or a live demonstration.*</span></span>


<span data-ttu-id="79375-276">이 기술은 잘 작동 하는 세 가지 주요 시나리오는</span><span class="sxs-lookup"><span data-stu-id="79375-276">There are three key scenarios that work well with this technology:</span></span>

<span data-ttu-id="79375-277">**1. 사진 캡처**</span><span class="sxs-lookup"><span data-stu-id="79375-277">**1. Photo capture**</span></span><br>
<span data-ttu-id="79375-278">이 기술을 사용 하 여 홀로그램의 고해상도 이미지를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-278">Using this technology, you can capture high resolution images of your holograms.</span></span> <span data-ttu-id="79375-279">이벤트를 마케팅 콘텐츠를 소개, 잠재적 클라이언트에 게 보내거나도 Windows 스토어에 응용 프로그램을 제출 이러한 이미지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-279">These images can be used to showcase content at marketing events, send to your potential clients, or even submit your application to the Windows Store.</span></span> <span data-ttu-id="79375-280">이러한 이미지를 캡처하는 데 사용할 것인지는 사진 카메라를 결정 하, 따라서 품질 DSLR 카메라가 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-280">You get to decide which photo camera you would like to use to capture these images, as such you may prefer a quality DSLR camera.</span></span>


<span data-ttu-id="79375-281">![Spectator 보기 Pro 사진 캡처 예제](images/fall-350px.jpg)</span><span class="sxs-lookup"><span data-stu-id="79375-281">![Spectator View Pro photo capture example](images/fall-350px.jpg)</span></span><br>
<span data-ttu-id="79375-282">*사진 캡처 예제-바닥에 표시 되 게 밑바닥 이루어져 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="79375-282">*Photo capture example - making it appear the floor is made of lava.*</span></span>


<span data-ttu-id="79375-283">**2. 비디오 캡처**</span><span class="sxs-lookup"><span data-stu-id="79375-283">**2. Video capture**</span></span><br>
<span data-ttu-id="79375-284">비디오는 최적의 스토리 holographic 앱 경험 많은 사용자와 공유 하기 위한 메커니즘을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-284">Videos are the best story telling mechanism for sharing a holographic app experience with many people.</span></span> <span data-ttu-id="79375-285">Spectator 보기에는 카메라, lens 고 프레이밍 가장 짝패가 앱 소개 하고자 하는 방법을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-285">Spectator view lets you choose the camera, lens, and framing that best suits how you want to showcase your app.</span></span> <span data-ttu-id="79375-286">배치 하면 사용할 수 있는 비디오 하드웨어를 기반으로 비디오 품질을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-286">It puts you in control of the video quality based on the video hardware you have available.</span></span>

<span data-ttu-id="79375-287">![Spectator 보기 Pro 비디오 캡처 예제](images/spectatorviewvideo.gif)</span><span class="sxs-lookup"><span data-stu-id="79375-287">![Spectator View Pro video capture example](images/spectatorviewvideo.gif)</span></span><br>
<span data-ttu-id="79375-288">*비디오 캡처 예제-혼합된 현실 공동 작업을 기록 합니다.*</span><span class="sxs-lookup"><span data-stu-id="79375-288">*Video capture example - recording a mixed reality collaboration experience.*</span></span>


<span data-ttu-id="79375-289">**3. 라이브 데모**</span><span class="sxs-lookup"><span data-stu-id="79375-289">**3. Live demonstrations**</span></span><br>
<span data-ttu-id="79375-290">카메라 위치 안정적인 / 제어 된 유지 spectator 보기는 라이브 데모에 대 한 기본 설정된 방법.</span><span class="sxs-lookup"><span data-stu-id="79375-290">Spectator view is a preferred approach for live demonstrations as the camera position remains steady or controlled.</span></span> <span data-ttu-id="79375-291">고품질 비디오 카메라를 사용할 수 있으므로 큰 화면을 위한 고품질 이미지를 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-291">Because you can use a high-quality video camera, you can also produce high-quality images meant for a big screen.</span></span> <span data-ttu-id="79375-292">해당 설정에 대 한 줄에서 대기 하는 즉시 참가자 개까지 화면에 라이브 데모를 스트리밍에 대 한 적절 한 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-292">This is also appropriate for streaming live demos on a screen, possibly to eager participants waiting in line for their turn.</span></span>

### <a name="comparing-video-capture-techniques"></a><span data-ttu-id="79375-293">비디오 캡처 기술 비교</span><span class="sxs-lookup"><span data-stu-id="79375-293">Comparing video capture techniques</span></span>

<span data-ttu-id="79375-294">[혼합 현실 캡처](mixed-reality-capture.md) (MRC) 비디오 조합으로 구성 된 첫 번째 사용자-의-관점에서 표시 하는 HoloLens 사용자가 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-294">[Mixed reality capture](mixed-reality-capture.md) (MRC) provides a video composite of what the HoloLens user is seeing from a first person point-of-view.</span></span> <span data-ttu-id="79375-295">Spectator 보기 홀로그램 및 HoloLens 장치 착용 사용자 환경을 보려면 비디오 관찰자 허용 3 인칭 관점에서 비디오를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-295">Spectator view produces a video from a third-person perspective, allowing the video observer to see the environment with holograms and the user wearing a HoloLens device.</span></span> <span data-ttu-id="79375-296">카메라의 선택 했으므로 더 높은 해상도 및 MRC 이미지에 사용 되는 기본 제공 HoloLens 카메라 보다 더 나은 품질 이미지 spectator 보기도 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-296">Because you have a choice of camera, spectator views can also produce higher resolution and better quality images than the built-in HoloLens camera used for MRC images.</span></span> <span data-ttu-id="79375-297">이러한 이유로 spectator 보기는 더 적합 마케팅 비디오, Windows 스토어에서 앱 이미지 또는 대상에 대 한 실시간 보기를 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-297">For this reason, spectator view is better suited for app images in the Windows Store, marketing videos, or for projecting a live view for an audience.</span></span>

<span data-ttu-id="79375-298">![Microsoft 기조 프레젠테이션에서 사용 하는 전문 카메라 보기 Pro spectator](images/spectator-view-professional-red-camera-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="79375-298">![Spectator View Pro professional camera used in Microsoft keynote presentations](images/spectator-view-professional-red-camera-300px.jpg)</span></span><br>
<span data-ttu-id="79375-299">*Microsoft 기조 프레젠테이션에서 사용 하는 전문 카메라 보기 Pro spectator*</span><span class="sxs-lookup"><span data-stu-id="79375-299">*Spectator View Pro professional camera used in Microsoft keynote presentations*</span></span>


<span data-ttu-id="79375-300">Spectator 보기를 표시 하는 Microsoft HoloLens 환경을 대상 그룹을 처음부터 제품 2015 년 1 월에에서 발표 했을 때 필수적인 부분을 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-300">Spectator view has been an essential piece of how Microsoft HoloLens has presented experiences to audiences since the very beginning when the product was announced in January 2015.</span></span> <span data-ttu-id="79375-301">사용 되는 전문 설정을 많이 요구 하는 비용이 많이 드는 가격 태그를 절감 했습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-301">The professional setup used had high demands and an expensive price tag to go with it.</span></span> <span data-ttu-id="79375-302">예를 들어, 카메라 genlock 신호를 사용 하 여 추적 시스템 HoloLens를 사용 하 여 조정 하는 정확한 시간을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-302">For example, the camera uses a genlock signal to ensure precise timing that coordinates with the HoloLens tracking system.</span></span> <span data-ttu-id="79375-303">이 설치에서 spectator 보기 카메라를 이동할 수 있었습니다 홀로그램 HoloLens에서 직접 경험을 표시 하는 사용자의 환경에 맞게 안정적인 하면서.</span><span class="sxs-lookup"><span data-stu-id="79375-303">In this setup, moving the spectator view camera was possible while keeping holograms stable to match the experience of someone who is seeing the experience directly in HoloLens.</span></span>

<span data-ttu-id="79375-304">Spectator 보기의 오픈 소스 버전 trades 카메라 rig를 전체 설치의 비용을 크게 낮추기 위해 이동 기능을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-304">The open-source version of spectator view trades off the ability to move the camera rig in order to dramatically lower the cost of the overall setup.</span></span> <span data-ttu-id="79375-305">이 프로젝트는 HoloLens에 엄격 하 게 탑재 하는 외부 카메라를 사용 하 여 고화질 사진을 찍고 holographic Unity 프로젝트의 비디오.</span><span class="sxs-lookup"><span data-stu-id="79375-305">This project uses an external camera rigidly mounted to a HoloLens to take high-definition pictures and video of your holographic Unity project.</span></span> <span data-ttu-id="79375-306">**라이브 데모 중 카메라는 고정된 된 위치에 유지 되어야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="79375-306">**During live demonstrations, the camera should remain in a fixed position.**</span></span> <span data-ttu-id="79375-307">카메라 이동 홀로그램 지터 또는 드리프트 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-307">Movement of the camera can lead to hologram jitter or drift.</span></span> <span data-ttu-id="79375-308">비디오 프레임의 타이밍 및 렌더링을 PC에 제공 될 수 있습니다 정확 하 게 동기화 되지 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-308">This is because the timing of the video frame and the rendering of holograms on the PC may not be precisely synchronized.</span></span> <span data-ttu-id="79375-309">따라서 카메라를 계속 유지 또는 이동 제한 보이는 하는 사람을 HoloLens에 가까운 결과 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-309">Therefore, keeping the camera steady or limiting movement will produce a result close to what the person wearing a HoloLens can see.</span></span>

<span data-ttu-id="79375-310">앱 spectator 보기에 대 한 준비를 위해 작성 해야는 [경험을 공유](holograms-240.md) 앱 HoloLens 뿐만 아니라 Unity 편집기의 바탕 화면에서 앱이 실행 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-310">To make your app ready for spectator view, you'll need to build a [shared experience](holograms-240.md) app and ensure the app can run on both HoloLens as well as desktop in the Unity editor.</span></span> <span data-ttu-id="79375-311">데스크톱 버전의 앱에 추가 구성 요소를 렌더링된 홀로그램을 사용 하 여 비디오 피드 하는 복합 기본 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-311">The desktop version of the app will have additional components built in that composite the video feed with the rendered holograms.</span></span>

## <a name="how-to-set-up-spectator-view-pro"></a><span data-ttu-id="79375-312">Spectator 보기 Pro 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="79375-312">How to set up Spectator View Pro</span></span> 

### <a name="requirements"></a><span data-ttu-id="79375-313">요구 사항</span><span class="sxs-lookup"><span data-stu-id="79375-313">Requirements</span></span>

![Spectator 보기 Pro Rig](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a><span data-ttu-id="79375-315">하드웨어 구입 목록</span><span class="sxs-lookup"><span data-stu-id="79375-315">Hardware shopping list</span></span>

<span data-ttu-id="79375-316">아래 권장 되는 하드웨어 목록을 이지만 너무 호환 다른 단위를 사용 하 여 실험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-316">Below is a recommended list of hardware, but you can experiment with other compatible units too.</span></span> 

|<span data-ttu-id="79375-317">하드웨어 구성 요소</span><span class="sxs-lookup"><span data-stu-id="79375-317">Hardware component</span></span>                                                                     |<span data-ttu-id="79375-318">권장</span><span class="sxs-lookup"><span data-stu-id="79375-318">Recommendation</span></span>               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|<span data-ttu-id="79375-319">HoloLens 에뮬레이터를 사용 하 여 holographic 개발에 대해 작동 하는 PC 구성</span><span class="sxs-lookup"><span data-stu-id="79375-319">A PC configuration that works for holographic development with the HoloLens emulator</span></span>  |                              | 
|<span data-ttu-id="79375-320">Out HDMI 또는 사진 캡처 SDK 사용 하 여 카메라</span><span class="sxs-lookup"><span data-stu-id="79375-320">Camera with HDMI out or photo capture SDK</span></span>                                             | <span data-ttu-id="79375-321">사진 및 비디오 캡처에 대 한 테스트를 거쳤습니다 합니다 [율이 EOS 5d 표시 III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) 카메라입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-321">For photo and video capture, we have tested the [Canon EOS 5D Mark III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) camera.</span></span> <span data-ttu-id="79375-322">라이브 데모에 대 한 테스트를 거쳤습니다 합니다 [Blackmagic 디자인 프로덕션 카메라 4k](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k)합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-322">For live demonstrations, we have tested the [Blackmagic Design Production Camera 4K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k).</span></span><br><br><span data-ttu-id="79375-323">단, 모든 카메라 HDMI (예: GoPro) out을 사용 하 여 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-323">Note, any camera with HDMI out (e.g. GoPro) should work.</span></span> <span data-ttu-id="79375-324">다양 한 비디오를 사용 합니다 [율이 EF 14 mm f/2.8 L II USM 매우 광범위 각도 고정 렌즈](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), 요구 사항을 충족 하는 카메라 렌즈를 선택 해야 하지만 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-324">Many of our videos use the [Canon EF 14mm f/2.8L II USM Ultra-Wide Angle Fixed Lens](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), but you should choose a camera lens that meets your needs.</span></span> | 
|<span data-ttu-id="79375-325">카드 색 프레임 카메라 rig를 보정 복합 장면 미리 보기를 활용 하려면 PC에 대 한 캡처</span><span class="sxs-lookup"><span data-stu-id="79375-325">Capture card for your PC to get color frames from your camera to calibrate your rig and preview your composite scene</span></span> |  <span data-ttu-id="79375-326">테스트를 거쳤습니다 합니다 [Blackmagic 디자인 강도 Pro 4k 캡처 카드](https://www.amazon.com/dp/B00U3QNP7Q)합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-326">We have tested the [Blackmagic Design Intensity Pro 4K capture card](https://www.amazon.com/dp/B00U3QNP7Q).</span></span> | 
|<span data-ttu-id="79375-327">케이블</span><span class="sxs-lookup"><span data-stu-id="79375-327">Cables</span></span>                                                                                 |  <span data-ttu-id="79375-328">[미니 HDMI를 HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) 카메라 캡처 카드에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-328">[HDMI to Mini HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) for attaching your camera to your capture card.</span></span> <span data-ttu-id="79375-329">카메라에 맞는 HDMI 폼 팩터를 구매를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-329">Ensure you purchase an HDMI form factor that fits your camera.</span></span> <span data-ttu-id="79375-330">(GoPro를 통해 예를 들어 출력 [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)</span><span class="sxs-lookup"><span data-stu-id="79375-330">(GoPro, for instance, outputs over [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)</span></span><br><br><span data-ttu-id="79375-331">[HDMI 케이블](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) 복합 preview 모니터 또는 텔레비전에 피드를 보기 위한</span><span class="sxs-lookup"><span data-stu-id="79375-331">[HDMI cable](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) for viewing the composite feed on a preview monitor or television</span></span> | 
|<span data-ttu-id="79375-332">Aluminum 대괄호에 HoloLens 카메라에 연결할 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="79375-332">Machined aluminum bracket to connect your HoloLens to the camera.</span></span> | [<span data-ttu-id="79375-333">Aluminum 대괄호</span><span class="sxs-lookup"><span data-stu-id="79375-333">Aluminum bracket</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|<span data-ttu-id="79375-334">3D는 카메라 hotshoe에 HoloLens 탑재를 연결 하는 어댑터를 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-334">3D printed adapter to connect the HoloLens mount to the camera hotshoe.</span></span>| [<span data-ttu-id="79375-335">3D 인쇄 어댑터</span><span class="sxs-lookup"><span data-stu-id="79375-335">3D printed adapter</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|<span data-ttu-id="79375-336">Hotshoe fastener hotshoe 어댑터를 탑재 하려면</span><span class="sxs-lookup"><span data-stu-id="79375-336">Hotshoe fastener to mount the hotshoe adapter</span></span>                                       |  [<span data-ttu-id="79375-337">Hotshoe Fastener</span><span class="sxs-lookup"><span data-stu-id="79375-337">Hotshoe Fastener</span></span>](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|<span data-ttu-id="79375-338">선별 된 너트, bolt 및 도구</span><span class="sxs-lookup"><span data-stu-id="79375-338">Assorted nuts, bolts, and tools</span></span>                                                |  [<span data-ttu-id="79375-339">1/4-20 "너트</span><span class="sxs-lookup"><span data-stu-id="79375-339">1/4-20" Nuts</span></span>](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[<span data-ttu-id="79375-340">1/4-20 "x 3/4" Bolt</span><span class="sxs-lookup"><span data-stu-id="79375-340">1/4-20" x 3/4" Bolts</span></span>](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[<span data-ttu-id="79375-341">7 월 16 너트 드라이버</span><span class="sxs-lookup"><span data-stu-id="79375-341">7/16 Nut Driver</span></span>](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[<span data-ttu-id="79375-342">T15 Torx</span><span class="sxs-lookup"><span data-stu-id="79375-342">T15 Torx</span></span>](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[<span data-ttu-id="79375-343">T7 Torx</span><span class="sxs-lookup"><span data-stu-id="79375-343">T7 Torx</span></span>](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a><span data-ttu-id="79375-344">소프트웨어 구성 요소</span><span class="sxs-lookup"><span data-stu-id="79375-344">Software components</span></span>

1. <span data-ttu-id="79375-345">소프트웨어를 다운로드 합니다 [spectator 보려면 GitHub 프로젝트](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-345">Software downloaded from the [GitHub project for spectator view](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView).</span></span>
2. <span data-ttu-id="79375-346">[Blackmagic Capture Card SDK](https://www.blackmagicdesign.com/support).\\</span><span class="sxs-lookup"><span data-stu-id="79375-346">[Blackmagic Capture Card SDK](https://www.blackmagicdesign.com/support).\\</span></span>
 <span data-ttu-id="79375-347">데스크톱 비디오 개발자 SDK "최신 다운로드"를에서 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-347">Search for Desktop Video Developer SDK in "Latest Downloads".</span></span>
3. <span data-ttu-id="79375-348">[Blackmagic 데스크톱 비디오 런타임](https://www.blackmagicdesign.com/support). \\</span><span class="sxs-lookup"><span data-stu-id="79375-348">[Blackmagic Desktop Video Runtime](https://www.blackmagicdesign.com/support).\\</span></span>
 <span data-ttu-id="79375-349">데스크톱 비디오 소프트웨어 업데이트 "최신 버전 다운로드"에 대 한 검색 합니다. \\</span><span class="sxs-lookup"><span data-stu-id="79375-349">Search for Desktop Video Software Update in "Latest Downloads".\\</span></span>
 <span data-ttu-id="79375-350">SDK 버전을 버전 번호가 일치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-350">Ensure the version number matches the SDK version.</span></span>
4. <span data-ttu-id="79375-351">[OpenCV 3.1](https://opencv.org/releases.html) 보정 또는 Blackmagic 캡처 카드 없이 비디오 캡처에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-351">[OpenCV 3.1](https://opencv.org/releases.html) For calibration or video capture without the Blackmagic capture card.</span></span>
5. <span data-ttu-id="79375-352">[SDK 율이](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (선택 사항). \\</span><span class="sxs-lookup"><span data-stu-id="79375-352">[Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (Optional).\\</span></span>
 <span data-ttu-id="79375-353">율이 카메라를 사용 하는 경우 율이 SDK에 대 한 액세스 권한이 더 높은 해상도 이미지를 사용자 PC에 카메라가 tether 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-353">If you are using a Canon camera and have access to the Canon SDK, you can tether your camera to your PC to take higher resolution images.</span></span>
6. <span data-ttu-id="79375-354">Holographic 응용 프로그램 개발에 대 한 unity. \\</span><span class="sxs-lookup"><span data-stu-id="79375-354">Unity for your holographic app development.\\</span></span>
 <span data-ttu-id="79375-355">OSS 프로젝트에서 지원 되는 버전을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-355">Supported version can be found in the OSS project.</span></span>
7. <span data-ttu-id="79375-356">최신 업데이트가 포함 된 visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="79375-356">Visual Studio 2015 with latest updates.</span></span>

### <a name="building-your-own-spectator-view-pro-camera"></a><span data-ttu-id="79375-357">사용자 고유의 Spectator 보기 Pro 카메라 구축</span><span class="sxs-lookup"><span data-stu-id="79375-357">Building your own Spectator View Pro camera</span></span>

<span data-ttu-id="79375-358">**공지 및 고 지 사항:** 수정할 때는 HoloLens 하드웨어 (등 "spectator 보기" 프로그램 HoloLens 설정에 국한 되지 않음) 기본 안전 주의 사항은 항상 관찰 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-358">**NOTICE & DISCLAIMER:** When making modifications to your HoloLens hardware (including, but not limited to, setting up your HoloLens for "spectator view") basic safety precautions should always be observed.</span></span> <span data-ttu-id="79375-359">수정 하기 전에 모든 지침 및 설명서를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-359">Read all instructions and manuals before making any modifications.</span></span> <span data-ttu-id="79375-360">것이 모든 지침 및 지시에 따라 도구를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-360">It is your responsibility to follow all instructions and use tools as directed.</span></span> <span data-ttu-id="79375-361">구매 하였거나 라이선스에 HoloLens 제한적된 보증 또는 보증도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-361">You may have purchased or licensed your HoloLens with a limited warranty or no warranty.</span></span> <span data-ttu-id="79375-362">해당을 참조 하세요 [HoloLens 사용권 계약 또는 사용 약관 및 판매](https://www.microsoft.com/hololens/support/warranty) 보증 옵션을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-362">Please read your applicable [HoloLens License Agreement or Terms of Use and Sale](https://www.microsoft.com/hololens/support/warranty) to understand your warranty options.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a><span data-ttu-id="79375-363">Rig 어셈블리</span><span class="sxs-lookup"><span data-stu-id="79375-363">Rig Assembly</span></span>

<span data-ttu-id="79375-364">![HoloLens 및 DSLR 카메라를 사용 하 여 어셈블된 Spectator 보기 Pro rig를 지원 합니다.](images/assembly.gif)</span><span class="sxs-lookup"><span data-stu-id="79375-364">![Assembled Spectator View Pro rig with HoloLens and DSLR camera.](images/assembly.gif)</span></span><br>
<span data-ttu-id="79375-365">*HoloLens 및 DSLR 카메라를 사용 하 여 어셈블된 Spectator 보기 Pro rig*</span><span class="sxs-lookup"><span data-stu-id="79375-365">*Assembled Spectator View Pro rig with HoloLens and DSLR camera*</span></span>


* <span data-ttu-id="79375-366">headband는 HoloLens에서 제거할 T7 스크루 드라이버를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-366">Use a T7 screwdriver to remove the headband from the HoloLens.</span></span> <span data-ttu-id="79375-367">나사에 완화 되 면 다른 쪽에서 클립을 사용 하 여 해당 포크 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-367">Once the screws are loose, poke them out with a paperclip from the other side.</span></span>
* <span data-ttu-id="79375-368">내부에 나사 한도 제거 작은 머리 스크루 드라이버를 사용 하 여 HoloLens 하이퍼바이저 앞입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-368">Remove the screw cap on the inside front of the HoloLens visor with a small flat head screwdriver.</span></span>
* <span data-ttu-id="79375-369">T15 스크루 드라이버를 사용 하 여 작은 torx bolt는 사용자를 제거해 HoloLens 대괄호를 제거할 및 후크 모양의 첨부 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-369">Use a T15 screwdriver to remove the small torx bolts from the HoloLens bracket to remove the U and Hook-shaped attachments.</span></span>
* <span data-ttu-id="79375-370">앞면 대괄호의 돌출을 사용 하 여는 하이퍼바이저의 안쪽에 노출 된 구멍에 맞춰 정렬 된 대괄호에는 HoloLens를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-370">Place the HoloLens on the bracket, lining up the exposed hole on the inside of the visor with the extrusion on the front of the bracket.</span></span> <span data-ttu-id="79375-371">HoloLens' 무기 거래 대괄호의 맨 아래에 핀으로 위치에 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-371">The HoloLens' arms should be kept in place by the pins on the bottom of the bracket.</span></span>
* <span data-ttu-id="79375-372">다시 연결 하는 및를 대괄호로 HoloLens 보안 후크 모양의 첨부 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-372">Reattach the U and Hook-shaped attachments to secure the HoloLens to the bracket.</span></span>
* <span data-ttu-id="79375-373">카메라의 hotshoe를 hotshoe fastener를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-373">Attach the hotshoe fastener to the hotshoe of your camera.</span></span>
* <span data-ttu-id="79375-374">Hotshoe fastener에 탑재 어댑터를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-374">Attach the mount adapter to the hotshoe fastener.</span></span>
* <span data-ttu-id="79375-375">좁은 쪽은 앞으로 연결 되므로 어댑터와 동시에 카메라의 렌즈를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-375">Rotate the adapter so the narrow side is facing forward and parallel to the camera's lens.</span></span>
* <span data-ttu-id="79375-376">7 월 16 너트 드라이버를 사용 하 여 1/4"너트를 사용 하 여 현재 위치에서 어댑터를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-376">Secure the adapter in place with a 1/4" nut using the 7/16 nut driver.</span></span>
* <span data-ttu-id="79375-377">HoloLens' 하이퍼바이저 전면의와 최대한 가까이 카메라의 렌즈의 맨 앞으로 이므로 어댑터에 대 한 괄호를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-377">Position the bracket against the adapter so the front of the HoloLens' visor is as close as possible to the front of the camera's lens.</span></span>
* <span data-ttu-id="79375-378">7 월 16 너트 드라이버를 사용 하 여 4 1/4"nuts and bolt를 사용 하 여는 괄호를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-378">Attach the bracket with 4 1/4" nuts and bolts using the 7/16 nut driver.</span></span>

#### <a name="pc-setup"></a><span data-ttu-id="79375-379">PC 설정</span><span class="sxs-lookup"><span data-stu-id="79375-379">PC Setup</span></span>
* <span data-ttu-id="79375-380">소프트웨어 구성 요소 섹션에서 소프트웨어를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-380">Install the software from the software components section.</span></span>
* <span data-ttu-id="79375-381">마더보드에 열기 PCIe 슬롯에 캡처 카드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-381">Add the capture card to an open PCIe slot on your motherboard.</span></span>
* <span data-ttu-id="79375-382">카메라에서 외부 HDMI 슬롯에는 HDMI 케이블 (HDMI에서) 해당 캡처 카드.</span><span class="sxs-lookup"><span data-stu-id="79375-382">Plug an HDMI cable from your camera to the outer HDMI slot (HDMI-In) on the capture card.</span></span>
* <span data-ttu-id="79375-383">선택적인 미리 보기 모니터로 캡처 카드 center HDMI 슬롯 (HDMI 스케일 아웃)에서 HDMI 케이블을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-383">Plug an HDMI cable from the center HDMI slot (HDMI-Out) on the capture card to an optional preview monitor.</span></span>

#### <a name="camera-setup"></a><span data-ttu-id="79375-384">카메라 설정</span><span class="sxs-lookup"><span data-stu-id="79375-384">Camera Setup</span></span>
* <span data-ttu-id="79375-385">3: 4 사진 확인 전체 해상도 1920x1080 보다는 자른를 출력 하므로 카메라 비디오 모드로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-385">Change your camera to Video Mode so it outputs at the full 1920x1080 resolution rather than a cropped 3:4 photo resolution.</span></span>
* <span data-ttu-id="79375-386">카메라 HDMI 설정을 찾아서 사용 하도록 설정 **미러링** 하거나 **듀얼 모니터**합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-386">Find your camera's HDMI settings and enable **Mirroring** or **Dual Monitor**.</span></span>
* <span data-ttu-id="79375-387">1080 p 출력 해상도 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-387">Set the output resolution to 1080P.</span></span>
* <span data-ttu-id="79375-388">해제 **화면에서 보기 Live 표시** 하므로 모든 화면 오버레이 피드 복합에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-388">Turn off **Live View On Screen Display** so any screen overlays do not appear in the composite feed.</span></span>
* <span data-ttu-id="79375-389">카메라를 켜려면 **Live 보기**합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-389">Turn on your camera's **Live View**.</span></span>
* <span data-ttu-id="79375-390">사용 하는 경우는 **율이 SDK** flash 단위 사용, 사용 하지 않도록 설정 하려는 **LV 자동 해결**합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-390">If using the **Canon SDK** and would like to use a flash unit, disable **Silent LV Shoot**.</span></span>
* <span data-ttu-id="79375-391">외부 HDMI 슬롯에는 HDMI 케이블 카메라에서 (HDMI에서) 해당 캡처 카드.</span><span class="sxs-lookup"><span data-stu-id="79375-391">Plug an HDMI cable from the camera to the outer HDMI slot (HDMI-In) on the capture card.</span></span>

#### <a name="calibration"></a><span data-ttu-id="79375-392">보정</span><span class="sxs-lookup"><span data-stu-id="79375-392">Calibration</span></span>

<span data-ttu-id="79375-393">Spectator 보기 rig를 설정한 후에 HoloLens에 카메라의 위치 및 회전 오프셋을 얻기 위해 조정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-393">After setting up your spectator view rig, you must calibrate in order to get the position and rotation offset of your camera to your HoloLens.</span></span>
* <span data-ttu-id="79375-394">Calibration\Calibration.sln 아래 보정 Visual Studio 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="79375-394">Open the Calibration Visual Studio solution under Calibration\Calibration.sln.</span></span>
* <span data-ttu-id="79375-395">이 솔루션에서는 타사 파티 원본의 inc 위치에 대 한 매크로 만드는 파일 dependencies.props를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-395">In this solution, you will find the file dependencies.props which creates macros for the inc locations of the 3rd party sources.</span></span>
* <span data-ttu-id="79375-396">이 파일을 업데이트할 위치를 사용 하 여 설치한 OpenCV 3.1, Blackmagic SDK 및 율이 SDK (있는 경우)</span><span class="sxs-lookup"><span data-stu-id="79375-396">Update this file with the location you installed OpenCV 3.1, the Blackmagic SDK, and the Canon SDK (if applicable)</span></span>

<span data-ttu-id="79375-397">![Visual Studio에서 종속성 위치 스냅숏](images/dependencies-600px.png)</span><span class="sxs-lookup"><span data-stu-id="79375-397">![Dependency locations snapshot in Visual Studio](images/dependencies-600px.png)</span></span><br>
<span data-ttu-id="79375-398">*Visual Studio에서 종속성 위치 스냅숏*</span><span class="sxs-lookup"><span data-stu-id="79375-398">*Dependency locations snapshot in Visual Studio*</span></span>


* <span data-ttu-id="79375-399">보정 패턴 Calibration\CalibrationPatterns\2_66_grid_FULL.png 플랫, 엄격한 화면에 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-399">Print out the calibration pattern Calibration\CalibrationPatterns\2_66_grid_FULL.png on a flat, rigid surface.</span></span>
* <span data-ttu-id="79375-400">PC에 USB를 통해 여 HoloLens를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-400">Plug your HoloLens into your PC over USB.</span></span>
* <span data-ttu-id="79375-401">전처리기 정의 업데이트할 **HOLOLENS_USER** 하 고 **HOLOLENS_PW** 에서 **stdafx.h** HoloLens' 장치 포털 자격 증명을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-401">Update the preprocessor definitions **HOLOLENS_USER** and **HOLOLENS_PW** in **stdafx.h** with your HoloLens' device portal credentials.</span></span>
* <span data-ttu-id="79375-402">HDMI 통해 카메라 캡처 카드에 연결 하 고 전원을 켭니다.</span><span class="sxs-lookup"><span data-stu-id="79375-402">Attach your camera to your capture card over HDMI and turn it on.</span></span>
* <span data-ttu-id="79375-403">보정 솔루션을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-403">Run the Calibration solution.</span></span>
* <span data-ttu-id="79375-404">다음과 같은 뷰 주변 체크 무늬 패턴을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-404">Move the checkerboard pattern around the view like this:</span></span>

<span data-ttu-id="79375-405">![보정 Spectator 보기 Pro rig](images/calibration.gif)</span><span class="sxs-lookup"><span data-stu-id="79375-405">![Calibrating the Spectator View Pro rig](images/calibration.gif)</span></span><br>
<span data-ttu-id="79375-406">*보정 Spectator 보기 Pro rig*</span><span class="sxs-lookup"><span data-stu-id="79375-406">*Calibrating the Spectator View Pro rig*</span></span>


* <span data-ttu-id="79375-407">그림은 바둑판 표시 되 면 자동으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-407">A picture will automatically be taken when a checkerboard is in view.</span></span> <span data-ttu-id="79375-408">다음 포즈로 진행 하기 전에 HoloLens의 하이퍼바이저에 흰색 광원을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-408">Look for the white light on the HoloLens' visor before advancing to the next pose.</span></span>
* <span data-ttu-id="79375-409">완료 되 면 키를 눌러 **Enter** 보정 앱 만들려면 포커스에는 **CalibrationData.txt** 파일.</span><span class="sxs-lookup"><span data-stu-id="79375-409">When finished, press **Enter** with the Calibration app in focus to create a **CalibrationData.txt** file.</span></span>
* <span data-ttu-id="79375-410">이 파일에 저장 됩니다 **Documents\CalibrationFiles\CalibrationData.txt**</span><span class="sxs-lookup"><span data-stu-id="79375-410">This file will be saved to **Documents\CalibrationFiles\CalibrationData.txt**</span></span>
* <span data-ttu-id="79375-411">보정 데이터를 정확 하 게이 파일을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-411">Inspect this file to see if your calibration data is accurate:</span></span>
   * <span data-ttu-id="79375-412">**DSLR RMS** 0에 가까워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-412">**DSLR RMS** should be close to 0.</span></span>
   * <span data-ttu-id="79375-413">**HoloLens RMS** 0에 가까워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-413">**HoloLens RMS** should be close to 0.</span></span>
   * <span data-ttu-id="79375-414">**스테레오 RMS** 수 20-50, 이것은 허용 때문에 두 카메라 간에 보기의 필드는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-414">**Stereo RMS** may be 20-50, this is acceptable since the field of view between the two cameras may be different.</span></span>
   * <span data-ttu-id="79375-415">**번역** 연결 된 카메라의 렌즈를 HoloLens' 카메라의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-415">**Translation** is the distance from the HoloLens' camera to the attached camera's lens.</span></span> <span data-ttu-id="79375-416">미터입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-416">This is in meters.</span></span>
   * <span data-ttu-id="79375-417">**회전** identity에 가까워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-417">**Rotation** should be close to identity.</span></span>
   * <span data-ttu-id="79375-418">**DSLR_fov** y 값이 세로 보기의 필드 필터의 초점 모든 카메라 본문 자르기 요소를 예상 가까워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-418">**DSLR_fov** y value should be close to the vertical field of view expected from your lens' focal length and any camera body crop factor.</span></span>
* <span data-ttu-id="79375-419">이해 하기 표시 되지 않으면 위의 값 중 하나를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-419">If any of the above values do not appear to make sense, recalibrate.</span></span>
* <span data-ttu-id="79375-420">이 파일을 복사 합니다 **자산** Unity 프로젝트의 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-420">Copy this file to the **Assets** directory in your Unity project.</span></span>

### <a name="compositor"></a><span data-ttu-id="79375-421">Compositor</span><span class="sxs-lookup"><span data-stu-id="79375-421">Compositor</span></span>

<span data-ttu-id="79375-422">작성자는 Unity 편집기의 창으로 실행 되는 Unity 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-422">The compositor is a Unity extension that runs as a window in the Unity editor.</span></span> <span data-ttu-id="79375-423">이 작업이 가능 하도록 Compositor Visual Studio 솔루션을 먼저 빌드해야 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-423">To enable this, the Compositor Visual Studio solution first needs to be built.</span></span>
* <span data-ttu-id="79375-424">Compositor\Compositor.sln 아래 Compositor Visual Studio 솔루션을 엽니다</span><span class="sxs-lookup"><span data-stu-id="79375-424">Open the Compositor Visual Studio solution under Compositor\Compositor.sln</span></span>
* <span data-ttu-id="79375-425">위의 보정 솔루션에서 동일한 조건을 사용 하 여 dependencies.props를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-425">Update dependencies.props with the same criteria from the Calibration solution above.</span></span> <span data-ttu-id="79375-426">보정 단계를 수행 하는 경우이 파일은 이미 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-426">If you followed the calibration steps, this file will already have been updated.</span></span>
* <span data-ttu-id="79375-427">릴리스 및 Unity 버전의 아키텍처와 일치 하는 아키텍처 전체 솔루션을 빌드하십시오.</span><span class="sxs-lookup"><span data-stu-id="79375-427">Build the entire solution as Release and the architecture that matches your Unity version's architecture.</span></span> <span data-ttu-id="79375-428">확실 하지 않은의 경우 x86 및 x64)를 빌드하십시오.</span><span class="sxs-lookup"><span data-stu-id="79375-428">If in doubt, build both x86 and x64.</span></span>
* <span data-ttu-id="79375-429">X64에 대 한 솔루션을 빌드한 경우 또한 프로젝트를 빌드합니다 SpatialPerceptionHelper x86 있으므로 HoloLens에서을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-429">If you built the solution for x64, also build the SpatialPerceptionHelper project as x86 since it will run on the HoloLens.</span></span>
* <span data-ttu-id="79375-430">응용 프로그램이 실행 되는 경우에 Unity를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-430">Close Unity if it is running your application.</span></span> <span data-ttu-id="79375-431">Unity는 Dll은 런타임에 변경 되는 경우 다시 시작할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-431">Unity needs to be relaunched if DLLs are changed at runtime.</span></span>
* <span data-ttu-id="79375-432">Unity 프로젝트에이 솔루션에서 빌드한 Dll에 복사할 Compositor\CopyDLL.cmd를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-432">Run Compositor\CopyDLL.cmd to copy the DLLs built from this solution to your Unity project.</span></span> <span data-ttu-id="79375-433">이 스크립트는 포함 된 샘플 프로젝트에 Dll을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-433">This script will copy the DLLs to the included sample project.</span></span> <span data-ttu-id="79375-434">설정 된 사용자 고유의 프로젝트를 만든 후 CopyDLL 있습니다도 복사할 프로젝트의 자산 디렉터리를 가리키는 명령줄 인수를 사용 하 여 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-434">Once you have your own project set up, you can run CopyDLL with a command line argument pointing to your project's Assets directory to copy there as well.</span></span>
* <span data-ttu-id="79375-435">샘플 Unity 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-435">Launch the sample Unity app.</span></span>

### <a name="unity-app"></a><span data-ttu-id="79375-436">Unity 앱</span><span class="sxs-lookup"><span data-stu-id="79375-436">Unity app</span></span>

<span data-ttu-id="79375-437">Compositor는 Unity 편집기의 창으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-437">The compositor runs as a window in the Unity Editor.</span></span> <span data-ttu-id="79375-438">포함 된 샘플 프로젝트에 모든 설정 되 면 Dll이 복사 됩니다 compositor spectator 보기를 사용 하 여 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-438">The included sample project has everything set up to work with spectator view once the compositor DLLs are copied.</span></span>

<span data-ttu-id="79375-439">Spectator view 필요으로 실행 되도록 응용 프로그램을 [경험을 공유](holograms-240.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-439">Spectator view requires the application to be run as a [shared experience](holograms-240.md).</span></span> <span data-ttu-id="79375-440">이 HoloLens에서 발생 하는 응용 프로그램 상태 변경 네트워크를 통해 너무 Unity에서 실행 되는 앱을 업데이트 해야 한다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-440">This means that any application state changes that happen on the HoloLens need to be networked to update the app running in Unity too.</span></span>

<span data-ttu-id="79375-441">새 Unity 프로젝트에서 시작 하며, 경우에 일부 설치 프로세스를 먼저 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-441">If starting from a new Unity project, you will need to do some setup first:</span></span>
* <span data-ttu-id="79375-442">복사본 **자산/추가 기능/HolographicCameraRig** 프로젝트에 샘플 프로젝트에서.</span><span class="sxs-lookup"><span data-stu-id="79375-442">Copy **Assets/Addons/HolographicCameraRig** from the sample project to your project.</span></span>
* <span data-ttu-id="79375-443">프로젝트에 최신 MixedRealityToolkit 추가 포함 **공유**, **csc.rsp**, **gmcs.rsp**, 및 **smcs.rsp**합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-443">Add the latest MixedRealityToolkit to your project, including **Sharing**, **csc.rsp**, **gmcs.rsp**, and **smcs.rsp**.</span></span>
* <span data-ttu-id="79375-444">추가 프로그램 **CalibrationData.txt** 자산 디렉터리에 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="79375-444">Add your **CalibrationData.txt** file to your Assets directory.</span></span>

![Unity 자산 디렉터리 스냅숏](images/files-400px.png)

* <span data-ttu-id="79375-446">추가 된 **HolographicCameraRig\Prefabs\SpectatorViewManager** 장면 prefab 및 필드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-446">Add the **HolographicCameraRig\Prefabs\SpectatorViewManager** prefab to your scene and fill in the fields:</span></span>
   * <span data-ttu-id="79375-447">**HolographicCameraManager** HolographicCameraRig prefab 디렉터리에서 HolographicCameraManager prefab으로 채워져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-447">**HolographicCameraManager** should be populated with the HolographicCameraManager prefab from the HolographicCameraRig prefab directory.</span></span>
   * <span data-ttu-id="79375-448">**앵커** HolographicCameraRig prefab 디렉터리에서 앵커 prefab으로 채워져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-448">**Anchor** should be populated with the Anchor prefab from the HolographicCameraRig prefab directory.</span></span>
   * <span data-ttu-id="79375-449">**공유** 는 MixedRealityToolkit에서 공유 prefab으로 채워져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-449">**Sharing** should be populated with the Sharing prefab from the MixedRealityToolkit.</span></span>
   * <span data-ttu-id="79375-450">참고: 이러한 prefabs 이미 있는 경우 프로젝트 계층 구조에서 기존 prefabs이이 부분은 대신 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79375-450">Note: If any of these prefabs already exist in your project hierarchy, the existing prefabs will be used instead of these ones.</span></span>
   * <span data-ttu-id="79375-451">**Spectator 보기 IP** spectator 보기 rig에 연결 하 여 HoloLens의 IP 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-451">**Spectator View IP** should be the IP of your HoloLens attached to your spectator view rig.</span></span>
   * <span data-ttu-id="79375-452">**공유 서비스 IP** MixedRealityToolkit SharingService를 실행 하는 PC의 IP 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-452">**Sharing Service IP** should be the IP of the PC running the MixedRealityToolkit SharingService.</span></span>
   * <span data-ttu-id="79375-453">선택 사항: 여러 PC에 연결 된 rig를 보고 하는 여러 spectator 있으면의 **로컬 컴퓨터 IP** spectator 보기 rig와 통신 하는 PC를 사용 하 여 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-453">Optional: If you have multiple spectator view rigs attached to multiple PC's, **Local Computer IP** should be set with the PC the spectator view rig will communicate with.</span></span>

![Unity에서 spectator 보기 관리자 속성](images/spectatorviewmanager-500px.png)

* <span data-ttu-id="79375-455">시작 된 MixedRealityToolkit **공유 서비스**</span><span class="sxs-lookup"><span data-stu-id="79375-455">Start the MixedRealityToolkit **Sharing Service**</span></span>
* <span data-ttu-id="79375-456">빌드하고 spectator 보기 rig에 연결 하는 HoloLens에 D3D UWP 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-456">Build and deploy the app as a D3D UWP to the HoloLens attached to the spectator view rig.</span></span>
* <span data-ttu-id="79375-457">환경에서 다른 HoloLens 장치에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-457">Deploy the app to any other HoloLens devices in the experience.</span></span>
* <span data-ttu-id="79375-458">확인 합니다 **백그라운드에서 실행** 확인란 **플레이어 설정/편집/프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-458">Check the **Run In Background** checkbox under **edit/project settings/player**.</span></span>

![Unity의 배경 설정에서 실행](images/run-in-bg-400px.png)
* <span data-ttu-id="79375-460">Compositor 창의 시작 **Spectator 보기/작성자**</span><span class="sxs-lookup"><span data-stu-id="79375-460">Launch the compositor window under **Spectator View/Compositor**</span></span>

![Unity의 spectator 뷰에 대 한 작성자 보기](images/compositor-500px.png)

* <span data-ttu-id="79375-462">이 창에서는 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79375-462">This window allows you to:</span></span>
   * <span data-ttu-id="79375-463">비디오 녹화 시작</span><span class="sxs-lookup"><span data-stu-id="79375-463">Start recording video</span></span>
   * <span data-ttu-id="79375-464">사진 가져오기</span><span class="sxs-lookup"><span data-stu-id="79375-464">Take a picture</span></span>
   * <span data-ttu-id="79375-465">홀로그램 불투명도 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-465">Change hologram opacity</span></span>
   * <span data-ttu-id="79375-466">(조정 하는 캡처 카드 대기 시간에 대 한 계정에 색 타임 스탬프) 프레임 오프셋 변경</span><span class="sxs-lookup"><span data-stu-id="79375-466">Change the frame offset (which adjusts the color timestamp to account for capture card latency)</span></span>
   * <span data-ttu-id="79375-467">캡처에 저장 된 디렉터리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="79375-467">Open the directory the captures are saved to</span></span>
   * <span data-ttu-id="79375-468">(프로젝트에의 한 SpatialMappingManager 있으면) spectator 보기 카메라에서 공간 매핑 데이터를 요청</span><span class="sxs-lookup"><span data-stu-id="79375-468">Request spatial mapping data from the spectator view camera (if a SpatialMappingManager exists in your project)</span></span>
   * <span data-ttu-id="79375-469">장면의 복합 뷰 뿐만 아니라 색, 홀로그램, 및 알파 채널을 개별적으로 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-469">Visualize the scene's composite view as well as color, holograms, and alpha channel individually.</span></span>
   * <span data-ttu-id="79375-470">카메라를 켭니다.</span><span class="sxs-lookup"><span data-stu-id="79375-470">Turn your camera on.</span></span>
   * <span data-ttu-id="79375-471">Unity에서 play 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="79375-471">Press play in Unity.</span></span>
   * <span data-ttu-id="79375-472">카메라를 이동할 때 있는 피드 카메라 색을 기준으로 실제 환경에서 Unity에서 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79375-472">When the camera is moved, holograms in Unity should be where they are in the real world relative to your camera color feed.</span></span>

## <a name="see-also"></a><span data-ttu-id="79375-473">참조</span><span class="sxs-lookup"><span data-stu-id="79375-473">See also</span></span>

* [<span data-ttu-id="79375-474">혼합된 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="79375-474">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="79375-475">개발자를 위한 실제로 캡처 혼합</span><span class="sxs-lookup"><span data-stu-id="79375-475">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="79375-476">혼합된 현실 환경 공유했습니다</span><span class="sxs-lookup"><span data-stu-id="79375-476">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* [<span data-ttu-id="79375-477">GitHub에서 보기 (미리 보기) 코드 spectator</span><span class="sxs-lookup"><span data-stu-id="79375-477">Spectator View (Preview) code on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [<span data-ttu-id="79375-478">Spectator GitHub에서 네이티브 코드 보기 (미리 보기)</span><span class="sxs-lookup"><span data-stu-id="79375-478">Spectator View (Preview) native code on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [<span data-ttu-id="79375-479">GitHub에서 보기 Pro 코드 spectator</span><span class="sxs-lookup"><span data-stu-id="79375-479">Spectator View Pro code on GitHub</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
