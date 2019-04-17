---
title: Unity 및 Visual Studio를 사용 하 여 작업에 대 한 모범 사례
description: 팁과 요령을 Unity 및 Visual Studio를 사용 하 여 혼합된 현실 응용 프로그램을 만드는 워크플로 간소화 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: visual studio, HoloLens, 몰입 형 헤드셋을 unity 배포
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604105"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="667e4-104">Unity 및 Visual Studio를 사용 하 여 작업에 대 한 모범 사례</span><span class="sxs-lookup"><span data-stu-id="667e4-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="667e4-105">Unity를 사용한 혼합된 현실 응용 프로그램을 만드는 개발자를 위한 Unity 및 Visual Studio는 몰입 형 헤드셋 및/또는 HoloLens에 배포 되는 응용 프로그램 패키지를 만들 수 사이 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-105">A developer creating a mixed reality application with Unity will need to switch between Unity and Visual Studio to build the application package that is deployed to HoloLens and/or an immersive headset.</span></span> <span data-ttu-id="667e4-106">기본적으로 Visual Studio의 두 인스턴스는 필요한 (Unity 스크립트를 수정 하려면 1) 및 디버그 장치를 배포 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-106">By default two instances of Visual Studio are required (one to modify Unity scripts and one to deploy to the device and debug).</span></span> <span data-ttu-id="667e4-107">단일 Visual Studio 인스턴스를 사용 하 여 개발 있으며 Unity 프로젝트 내보내기 빈도가 감소 디버깅 환경을 개선 하는 다음 절차입니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-107">The following procedure allows development using single Visual Studio instance, reduces the frequency of exporting Unity projects, and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="667e4-108">반복 시간 개선</span><span class="sxs-lookup"><span data-stu-id="667e4-108">Improving iteration time</span></span>

<span data-ttu-id="667e4-109">Unity 및 Visual Studio를 사용 하 여 작업 하는 경우 일반적인 워크플로 문제는 여러 windows의 Visual Studio 열기 및 지속적으로 반복 하는 Visual Studio와 Unity 간에 전환 해야 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-109">A common workflow problem when working with Unity and Visual Studio is having multiple windows of Visual Studio open and the need to constantly switch between Visual Studio and Unity to iterate.</span></span>
1. <span data-ttu-id="667e4-110">**Unity** -장면을 수정 하 고 Visual Studio 솔루션 내보내기</span><span class="sxs-lookup"><span data-stu-id="667e4-110">**Unity** - for modifying the scene and exporting a Visual Studio solution</span></span>
2. <span data-ttu-id="667e4-111">**Visual Studio (1)** -스크립트를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-111">**Visual Studio (1)** - for modifying scripts</span></span>
3. <span data-ttu-id="667e4-112">**Visual Studio (2)** -빌드하고 Unity 배포 내보낸 장치에 Visual Studio 솔루션</span><span class="sxs-lookup"><span data-stu-id="667e4-112">**Visual Studio (2)** - for building and deploying the Unity exported Visual Studio solution to the device</span></span>

<span data-ttu-id="667e4-113">다행히 Visual Studio의 단일 인스턴스를 간소화 하 고 Unity에서 내보내기를 자주 수행에서 줄일 수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-113">Luckily, there's a way to streamline to a single instance of Visual Studio and cut down on frequent exports from Unity.</span></span>

<span data-ttu-id="667e4-114">때 [Unity에서 프로젝트를 내보내는](exporting-and-building-a-unity-visual-studio-solution.md)를 확인 합니다 **Unity C# 프로젝트** "파일 > 빌드 설정" 메뉴에서 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-114">When [exporting your project from Unity](exporting-and-building-a-unity-visual-studio-solution.md), check the **Unity C# Projects** checkbox in the "File > Build Settings" menu.</span></span> <span data-ttu-id="667e4-115">이제 Unity에서 내보낸 프로젝트에 프로젝트의 모든 C# 스크립트 및 몇 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-115">Now, the project you export from Unity includes all of your project's C# scripts and has several benefits:</span></span>
* <span data-ttu-id="667e4-116">스크립트를 작성 하 고 프로젝트를 빌드/배포에 대 한 Visual Studio의 동일한 인스턴스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-116">Use the same instance of Visual Studio for writing scripts and building/deploying your project</span></span>
* <span data-ttu-id="667e4-117">장면에는 Unity 편집기에서 변경 된 경우에 Unity에서 내보내기 스크립트의 내용을 변경할 수 있습니다 Visual Studio에서 다시 내보내지 않고 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-117">Export from Unity only when the scene is changed in the Unity Editor; changing the contents of scripts can be done in Visual Studio without re-exporting.</span></span>

<span data-ttu-id="667e4-118">사용 하 여 **Unity C# 프로젝트** 설정에 각 프로그램의 인스턴스가 하나만 열 수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-118">With **Unity C# Projects** enabled, only one instance of each program need be opened:</span></span>
1. <span data-ttu-id="667e4-119">**Unity** -장면을 수정 하 고 Visual Studio 솔루션 내보내기</span><span class="sxs-lookup"><span data-stu-id="667e4-119">**Unity** - for modifying the scene and exporting a Visual Studio solution</span></span>
2. <span data-ttu-id="667e4-120">**Visual Studio** -빌드 및 배포 Unity 장치에 Visual Studio 솔루션을 내보낸 다음 스크립트를 수정 하기 위한</span><span class="sxs-lookup"><span data-stu-id="667e4-120">**Visual Studio** - for modifying scripts then building and deploying the Unity exported Visual Studio solution to the device</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="667e4-121">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="667e4-121">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="667e4-122">다운로드 [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)</span><span class="sxs-lookup"><span data-stu-id="667e4-122">Download [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)</span></span>

<span data-ttu-id="667e4-123">**Visual Studio Tools for Unity의 이점**</span><span class="sxs-lookup"><span data-stu-id="667e4-123">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="667e4-124">변수와 복잡 한 식을 평가 하는 중단점을 배치 하 여 Visual Studio에서 Unity 편집기에서 play 모드를 디버그 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-124">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="667e4-125">Unity 프로젝트 탐색기를 사용 하 여 Unity를 표시 하는 것과 동일한 계층을 사용 하 여 스크립트를 찾으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-125">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="667e4-126">직접 Visual Studio 내의 Unity 콘솔을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-126">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="667e4-127">마법사를 사용 하 여 신속 하 게 만들거나 스크립트로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-127">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="667e4-128">표시 C# 쉽게 조정에 대 한 변수 클래스</span><span class="sxs-lookup"><span data-stu-id="667e4-128">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="667e4-129">클래스 변수를 노출 하는 방법은 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-129">There are two ways to expose class variables.</span></span> <span data-ttu-id="667e4-130">이렇게 하려면 개인 변수를 [SerializeField] 특성을 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-130">The recommended way to do so is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="667e4-131">따라서 편집기에서 액세스할 수 있지만 하지 프로그래밍 방식으로 노출 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-131">This allows them to be accessed from the editor but not programatically exposed.</span></span>  <span data-ttu-id="667e4-132">확인 하려면 다른 옵션은 C# 편집기 UI에서에서이 노출 하려면 클래스 변수를 public입니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-132">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="667e4-133">두 가지 방법을 모두 사용 하면 편집기에서 재생 하는 동안 변수를 쉽게 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-133">Both approaches make it possible to easily tweak variables while playing in-editor.</span></span> <span data-ttu-id="667e4-134">이 상호 작용 정비공 속성을 조정 하는 데 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-134">This is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="667e4-135">Windows SDK 또는 Unity 업그레이드 후 UWP Visual Studio 솔루션을 다시 생성</span><span class="sxs-lookup"><span data-stu-id="667e4-135">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="667e4-136">새 Windows SDK 또는 Unity 엔진을 업그레이드 한 후 UWP Visual Studio 솔루션을 소스 제어에 체크 인 날짜 지 남 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-136">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="667e4-137">Unity에서 새 UWP 솔루션을 빌드하고 다음 체크 인 된 솔루션으로 모든 차이점을 병합 하 여 업그레이드 후 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-137">You can resolve this after the upgrade by building a new UWP solution from Unity, then merging any differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="667e4-138">변경 내용이 쉽게 비교에 대 한 텍스트 형식으로 자산 사용</span><span class="sxs-lookup"><span data-stu-id="667e4-138">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="667e4-139">자산을 텍스트 형식으로 저장 쉽게 Visual Studio에서 콘텐츠 변경 내용이 차이 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-139">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="667e4-140">변경 하 여 "> 프로젝트 설정 > 편집기 편집"이을 사용할 수 있습니다 **Asset Serialization** 모드 **Force Text**합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-140">You can enable this in "Edit > Project Settings > Editor" by changing **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="667e4-141">그러나 텍스트 자산 파일 변경 내용을 병합 하는 것은 오류가 발생 하기 쉬운 및 권장 되는 것이 좋습니다 소스 제어 시스템에서 이진 단독 체크 아웃을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="667e4-141">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control system.</span></span>
