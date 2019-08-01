---
title: Unity 개발 개요
description: Unity에서 혼합 현실 앱 빌드를 시작 합니다.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, 포팅, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서
ms.openlocfilehash: b1384e886a2b4d0b3ed9f8008fca6af6ad4b78d5
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701789"
---
# <a name="unity-development-overview"></a><span data-ttu-id="ef968-104">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="ef968-104">Unity development overview</span></span>

<span data-ttu-id="ef968-105">[혼합 현실 앱](app-views.md) 을 빌드하기 위한 가장 빠른 경로는 [Unity](http://aka.ms/HoloLensUnity)를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](http://aka.ms/HoloLensUnity).</span></span> <span data-ttu-id="ef968-106">[Unity 자습서](https://unity3d.com/learn/tutorials)를 탐색 하는 데 시간이 소요 되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-106">We recommend that you take time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="ef968-107">자산이 필요한 경우 Unity는 포괄적인 [자산 저장소](https://www.assetstore.unity3d.com/)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="ef968-108">Unity를 기본적으로 이해 하 고 나면 [자습서](tutorials.md) 를 방문 하 여 unity를 사용한 혼합 현실 개발의 세부 사항을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="ef968-109">Unity [혼합 현실 포럼](http://forum.unity3d.com/forums/hololens.102/) 을 방문 하 여 unity에서 혼합 현실 앱을 빌드하는 커뮤니티의 나머지 부분과 함께 실행 될 수 있는 문제에 대 한 해결 방법을 찾아보세요.</span><span class="sxs-lookup"><span data-stu-id="ef968-109">Be sure to visit the [Unity Mixed Reality forums](http://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>

<span data-ttu-id="ef968-110">Unity를 사용 하 여 혼합 현실 앱 빌드를 시작 하려면 먼저 [도구를 설치](install-the-tools.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="ef968-111">혼합 현실 도구 키트를 사용 하는 새 Unity 프로젝트</span><span class="sxs-lookup"><span data-stu-id="ef968-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="ef968-112">Unity에서 개발 하는 가장 쉬운 방법은 Mixed Reality Toolkit의 도움을 주는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-112">The easiest way to develop in Unity is with the help of Mixed Reality Toolkit.</span></span> <span data-ttu-id="ef968-113">Project를 자동으로 설치 하 고 개발을 가속화 하는 혼합 현실 기능 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-113">It will help you setup with project automatically, and provide a set of mixed reality features to accelerate your development.</span></span> <span data-ttu-id="ef968-114">자세히 알아보고 시작 하려면 [Mixed Reality Toolkit v2](mrtk-getting-started.md) 를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef968-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="ef968-115">Windows Mixed Reality로 기존 Unity 앱 포팅</span><span class="sxs-lookup"><span data-stu-id="ef968-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="ef968-116">Windows Mixed Reality로 이식 하는 기존 Unity 프로젝트를 사용 하는 경우 [unity 포팅 가이드](porting-guides.md) 에 따라 시작 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef968-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="ef968-117">Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="ef968-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="ef968-118">Mixed Reality Toolkit를 가져오지 않고 새 Unity 프로젝트를 만들려는 경우에는 Windows Mixed Reality에 대해 수동으로 변경 해야 하는 몇 가지 Unity 설정 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-118">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="ef968-119">이러한 항목은 프로젝트별 및 장면의 두 범주로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-119">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="ef968-120">[Windows Mixed Reality에 대해 새 Unity 프로젝트를 구성](Configure-Unity-Project.md) 하는 단계별 가이드는 여기를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef968-120">See here for step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="ef968-121">혼합 현실 기능 및 입력 추가</span><span class="sxs-lookup"><span data-stu-id="ef968-121">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="ef968-122">프로젝트를 사용 하 여 MRTK v 2를 설정 하거나 위에서 설명한 대로 프로젝트를 구성한 후에는 표준 Unity 게임 개체 (예: 카메라)가 자동으로 작동 하 **고, 카메라**위치가 사용자가 전 세계를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-122">Once you've setup MRTK V2 with your project, or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="ef968-123">[공간 단계](coordinate-systems.md#spatial-coordinate-systems), [제스처, 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md) 또는 [음성 입력과](voice-input-in-unity.md) 같은 Windows 혼합 현실 기능에 대 한 지원을 추가 하면 Unity에 직접 빌드된 api를 사용 하 여 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-123">Adding support for Windows Mixed Reality features, such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="ef968-124">먼저, 해당 환경에서 대상으로 할 수 있는 [환경 규모](coordinate-systems.md) 를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-124">First, review the [experience scales](coordinate-systems.md) that your applicatioin can target:</span></span>
* <span data-ttu-id="ef968-125">**방향** 또는 **대규모 환경을**구축 하려는 경우 Unity의 추적 공간 형식을 [고정](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-125">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="ef968-126">대규모 또는 **공간 규모의 환경을**구축 하려는 경우 Unity의 추적 공간 유형이 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)로 설정 되었는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-126">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="ef968-127">사용자가 5 미터를 초과 하 여 로밍할 수 있도록 HoloLens에서 **세계 규모** 의 경험을 구축 하려는 경우 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 구성 요소를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-127">If you're looking to build a **world-scale** experience on HoloLens that lets users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="ef968-128">혼합 현실 응용 프로그램의 모든 핵심 구성 요소는 다른 Unity Api와 일치 하는 방식으로 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-128">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="ef968-129">혼합 현실 도구 키트를 통해 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-129">They are also available through the Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="ef968-130">카메라</span><span class="sxs-lookup"><span data-stu-id="ef968-130">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="ef968-131">좌표계</span><span class="sxs-lookup"><span data-stu-id="ef968-131">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="ef968-132">응시</span><span class="sxs-lookup"><span data-stu-id="ef968-132">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="ef968-133">제스처 및 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="ef968-133">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="ef968-134">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="ef968-134">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="ef968-135">지속성</span><span class="sxs-lookup"><span data-stu-id="ef968-135">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="ef968-136">공간 음향</span><span class="sxs-lookup"><span data-stu-id="ef968-136">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="ef968-137">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="ef968-137">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="ef968-138">많은 혼합 현실 응용 프로그램에서 Unity 앱에도 노출 되는 다른 주요 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-138">There are other key features that many mixed reality applications will want to use that are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="ef968-139">공유 환경</span><span class="sxs-lookup"><span data-stu-id="ef968-139">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="ef968-140">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="ef968-140">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="ef968-141">포커스 지점</span><span class="sxs-lookup"><span data-stu-id="ef968-141">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="ef968-142">추적 손실</span><span class="sxs-lookup"><span data-stu-id="ef968-142">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="ef968-143">키보드</span><span class="sxs-lookup"><span data-stu-id="ef968-143">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="ef968-144">실제 또는 시뮬레이션 된 장치에서 Unity 프로젝트 실행</span><span class="sxs-lookup"><span data-stu-id="ef968-144">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="ef968-145">Holographic Unity 프로젝트를 테스트할 준비가 되 면 다음 단계는 [Unity Visual Studio 솔루션을 내보내고 빌드하](exporting-and-building-a-unity-visual-studio-solution.md)는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-145">Once you've got your holographic Unity project ready for testing, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="ef968-146">이 VS 솔루션을 사용 하면 실제 또는 시뮬레이션 된 장치를 사용 하 여 다음 세 가지 방법 중 하나로 응용 프로그램을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-146">With that VS solution in hand, you can then run your application in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="ef968-147">실제 HoloLens 또는 Windows Mixed Reality 모던 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="ef968-147">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="ef968-148">HoloLens 에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="ef968-148">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="ef968-149">Windows Mixed Reality 몰입 형 헤드셋 시뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="ef968-149">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="ef968-150">Unity 설명서</span><span class="sxs-lookup"><span data-stu-id="ef968-150">Unity documentation</span></span>

<span data-ttu-id="ef968-151">Docs.microsoft.com에서 사용할 수 있는이 설명서 외에 Unity는 Unity 편집기와 함께 Windows Mixed Reality 기능에 대 한 설명서를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-151">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="ef968-152">Unity 제공 설명서에는 두 개의 개별 섹션이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-152">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="ef968-153">**Unity 스크립팅 참조**</span><span class="sxs-lookup"><span data-stu-id="ef968-153">**Unity scripting reference**</span></span>
    * <span data-ttu-id="ef968-154">설명서의이 섹션에는 Unity에서 제공 하는 스크립팅 API에 대 한 세부 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-154">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="ef968-155">Unity 편집기에서 **도움말 > 스크립팅 참조** 를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-155">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="ef968-156">**Unity 수동**</span><span class="sxs-lookup"><span data-stu-id="ef968-156">**Unity manual**</span></span>
    * <span data-ttu-id="ef968-157">이 설명서는 기본에서 고급 기술로 Unity를 사용 하는 방법을 배우는 데 도움이 되도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-157">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="ef968-158">**Help > Manual** 를 통해 Unity 편집기에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef968-158">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="ef968-159">참조</span><span class="sxs-lookup"><span data-stu-id="ef968-159">See also</span></span>
* [<span data-ttu-id="ef968-160">Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="ef968-160">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="ef968-161">MR 기본 100: Unity 시작</span><span class="sxs-lookup"><span data-stu-id="ef968-161">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="ef968-162">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="ef968-162">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ef968-163">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="ef968-163">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="ef968-164">Unity Visual Studio 솔루션 내보내기 및 빌드</span><span class="sxs-lookup"><span data-stu-id="ef968-164">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="ef968-165">HoloLens용 Unity 앱에서 Windows 네임스페이스 사용</span><span class="sxs-lookup"><span data-stu-id="ef968-165">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="ef968-166">Unity 및 Visual Studio 사용 모범 사례</span><span class="sxs-lookup"><span data-stu-id="ef968-166">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="ef968-167">Unity 플레이 모드</span><span class="sxs-lookup"><span data-stu-id="ef968-167">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="ef968-168">포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="ef968-168">Porting guides</span></span>](porting-guides.md)
