---
title: Unity 개발 개요
description: Unity에서 혼합 현실 앱 빌드를 시작합니다.
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, 포팅, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서
ms.openlocfilehash: e0fe775f5fe891416145d91e52a5a801e049c568
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81433419"
---
# <a name="unity-development-overview"></a><span data-ttu-id="351e5-104">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="351e5-104">Unity development overview</span></span>

<span data-ttu-id="351e5-105">[혼합 현실 앱](app-views.md)을 빌드하는 가장 빠른 경로는 [Unity](https://unity.com)를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](https://unity.com).</span></span> <span data-ttu-id="351e5-106">잠시 시간을 내어 [Unity 자습서](https://unity3d.com/learn/tutorials)를 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-106">We recommend that you take time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="351e5-107">자산이 필요한 경우 Unity에는 포괄적인 [Asset Store](https://www.assetstore.unity3d.com/)(자산 저장소)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="351e5-108">Unity를 기본적으로 이해한 경우 [자습서](tutorials.md)를 참조하여 Unity에서 혼합 현실을 개발하는 방법에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="351e5-109">[Unity Mixed Reality 포럼](https://forum.unity3d.com/forums/hololens.102/)을 방문하여 Unity에서 혼합 현실 앱을 빌드하는 나머지 커뮤니티와 교류하고 발생할 수 있는 문제에 대한 해결 방법을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-109">Be sure to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>

<span data-ttu-id="351e5-110">Unity를 사용하여 혼합 현실 앱 빌드를 시작하려면 먼저 [도구를 설치](install-the-tools.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="351e5-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="351e5-111">Mixed Reality Toolkit를 사용하는 새 Unity 프로젝트</span><span class="sxs-lookup"><span data-stu-id="351e5-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="351e5-112">Unity에서 개발하는 가장 쉬운 방법은 Mixed Reality Toolkit를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-112">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="351e5-113">이를 통해 프로젝트를 자동으로 설정하고, 개발을 가속화하는 혼합 현실 기능 세트를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-113">This will help you setup with the project automatically, and provide a set of mixed reality features to accelerate your development.</span></span> <span data-ttu-id="351e5-114">자세한 내용을 알아보고 시작하려면 [Mixed Reality Toolkit v2](mrtk-getting-started.md)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="351e5-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="351e5-115">기존 Unity 앱을 Windows Mixed Reality에 포팅</span><span class="sxs-lookup"><span data-stu-id="351e5-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="351e5-116">Windows Mixed Reality에 포팅할 기존 Unity 프로젝트가 있는 경우 [Unity 포팅 가이드](porting-guides.md)에 따라 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="351e5-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="351e5-117">Windows Mixed Reality용 새 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="351e5-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="351e5-118">Mixed Reality Toolkit를 가져오지 않고 새 Unity 프로젝트를 만들려면 Windows Mixed Reality에 대해 수동으로 변경해야 하는 작은 Unity 설정 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-118">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="351e5-119">이러한 설정은 두 가지 범주, 즉 프로젝트별 및 장면별 범주로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-119">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="351e5-120">단계별 가이드는 [Windows Mixed Reality용 새 Unity 프로젝트 구성](Configure-Unity-Project.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="351e5-120">See here for a step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="351e5-121">혼합 현실 기능 및 입력 추가</span><span class="sxs-lookup"><span data-stu-id="351e5-121">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="351e5-122">프로젝트를 사용하여 MRTK V2를 설정하거나 위에서 설명한 대로 프로젝트가 구성되면, 표준 Unity 게임 개체(예: 카메라)가 **착석 규모 환경**을 위해 즉시 켜지며 현실 세계에서 사용자의 머리 움직임에 따라 카메라의 위치가 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-122">Once you've setup MRTK V2 with your project or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="351e5-123">Windows Mixed Reality 기능에 대한 지원(예: [공간 스테이지](coordinate-systems.md#spatial-coordinate-systems), [제스처, 모션 컨트롤러](gestures-and-motion-controllers-in-unity.md) 또는 [음성 입력](voice-input-in-unity.md))은 Unity에 직접 빌드된 API를 사용하여 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-123">Adding support for Windows Mixed Reality features, such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="351e5-124">먼저 애플리케이션에서 대상으로 지정할 수 있는 [환경 규모](coordinate-systems.md)를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-124">First, review the [experience scales](coordinate-systems.md) that your application can target:</span></span>
* <span data-ttu-id="351e5-125">**방향 전용** 또는 **착석 규모 환경**을 빌드하려면 Unity의 추적 공간 형식을 [고정](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-125">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="351e5-126">**기립 규모** 또는 **실내 규모 환경**을 빌드하려면 Unity의 추적 공간 형식을 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-126">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="351e5-127">사용자가 5m 이상 배회할 수 있는 **세계 규모** 환경을 HoloLens에 빌드하려면 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 구성 요소를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-127">If you're looking to build a **world-scale** experience on HoloLens that lets users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="351e5-128">혼합 현실 애플리케이션의 모든 핵심 구성 요소는 다른 Unity API와 일치하는 방식으로 공개됩니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-128">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="351e5-129">이러한 구성 요소는 Mixed Reality Toolkit를 통해서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-129">They are also available through the Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="351e5-130">카메라</span><span class="sxs-lookup"><span data-stu-id="351e5-130">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="351e5-131">좌표계</span><span class="sxs-lookup"><span data-stu-id="351e5-131">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="351e5-132">응시</span><span class="sxs-lookup"><span data-stu-id="351e5-132">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="351e5-133">제스처 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="351e5-133">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="351e5-134">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="351e5-134">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="351e5-135">지속성</span><span class="sxs-lookup"><span data-stu-id="351e5-135">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="351e5-136">공간 음향</span><span class="sxs-lookup"><span data-stu-id="351e5-136">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="351e5-137">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="351e5-137">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="351e5-138">Unity 앱에도 공개되고 많은 혼합 현실 애플리케이션에서 사용하도록 하려는 다른 주요 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-138">There are other key features that many mixed reality applications will want to use that are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="351e5-139">공유 환경</span><span class="sxs-lookup"><span data-stu-id="351e5-139">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="351e5-140">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="351e5-140">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="351e5-141">포커스 지점</span><span class="sxs-lookup"><span data-stu-id="351e5-141">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="351e5-142">추적 손실</span><span class="sxs-lookup"><span data-stu-id="351e5-142">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="351e5-143">키보드</span><span class="sxs-lookup"><span data-stu-id="351e5-143">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="351e5-144">실제 디바이스 또는 시뮬레이션된 디바이스에서 Unity 프로젝트 실행</span><span class="sxs-lookup"><span data-stu-id="351e5-144">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="351e5-145">홀로그램 Unity 프로젝트를 테스트할 준비가 되면 다음 단계로 [Unity Visual Studio 솔루션을 내보내고 빌드](exporting-and-building-a-unity-visual-studio-solution.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-145">Once you've got your holographic Unity project ready for testing, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="351e5-146">이 VS 솔루션을 사용하면 실제 디바이스 또는 시뮬레이션된 디바이스를 사용하여 다음 세 가지 방법 중 하나에서 애플리케이션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-146">With that VS solution in hand, you can then run your application in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="351e5-147">실제 HoloLens 또는 Windows Mixed Reality 몰입형 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="351e5-147">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="351e5-148">HoloLens 에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="351e5-148">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="351e5-149">Windows Mixed Reality 몰입형 헤드셋 시뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="351e5-149">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="351e5-150">Unity 설명서</span><span class="sxs-lookup"><span data-stu-id="351e5-150">Unity documentation</span></span>

<span data-ttu-id="351e5-151">Unity는 docs.microsoft.com에서 사용할 수 있는 이 설명서 외에도 Windows Mixed Reality 기능에 대한 설명서를 Unity 편집기와 함께 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-151">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="351e5-152">Unity에서 제공하는 설명서에는 다음과 같은 두 개의 개별 섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-152">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="351e5-153">**Unity 스크립팅 참조**</span><span class="sxs-lookup"><span data-stu-id="351e5-153">**Unity scripting reference**</span></span>
    * <span data-ttu-id="351e5-154">설명서의 이 섹션에는 Unity에서 제공하는 스크립팅 API에 대한 세부 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-154">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="351e5-155">Unity 편집기에서 **도움말 > 스크립팅 참조**를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-155">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="351e5-156">**Unity 설명서**</span><span class="sxs-lookup"><span data-stu-id="351e5-156">**Unity manual**</span></span>
    * <span data-ttu-id="351e5-157">이 설명서는 기본 기술에서 고급 기술에 이르기까지 Unity를 사용하는 방법을 익히는 데 도움이 되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-157">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="351e5-158">Unity 편집기에서 **도움말 > 설명서**를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="351e5-158">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="351e5-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="351e5-159">See also</span></span>
* [<span data-ttu-id="351e5-160">Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="351e5-160">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="351e5-161">MR 기본 100: Unity 시작</span><span class="sxs-lookup"><span data-stu-id="351e5-161">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="351e5-162">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="351e5-162">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="351e5-163">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="351e5-163">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="351e5-164">Unity Visual Studio 솔루션 내보내기 및 빌드</span><span class="sxs-lookup"><span data-stu-id="351e5-164">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="351e5-165">HoloLens용 Unity 앱에서 Windows 네임스페이스 사용</span><span class="sxs-lookup"><span data-stu-id="351e5-165">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="351e5-166">Unity 및 Visual Studio 사용 모범 사례</span><span class="sxs-lookup"><span data-stu-id="351e5-166">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="351e5-167">Unity 플레이 모드</span><span class="sxs-lookup"><span data-stu-id="351e5-167">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="351e5-168">포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="351e5-168">Porting guides</span></span>](porting-guides.md)
