---
title: 1. 시작
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서 시리즈 1/6부
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 39e4e7218341dcc69eacf01f43b5e0721e76031b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720379"
---
# <a name="1-getting-started"></a><span data-ttu-id="74049-104">1. 시작</span><span class="sxs-lookup"><span data-stu-id="74049-104">1. Getting started</span></span>

<span data-ttu-id="74049-105">여기서는 혼합 현실을 처음 사용하거나 익숙한 사용자 모두를 위해 [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) 및 [Unreal Engine](https://www.unrealengine.com/en-US/)을 시작하는 출발점을 제시합니다.</span><span class="sxs-lookup"><span data-stu-id="74049-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="74049-106">이 자습서 시리즈에서는 [Unreal용 Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unreal)의 일부인 [UX Tools 플러그 인](https://github.com/microsoft/MixedReality-UXTools-Unreal)을 사용하여 대화형 체스 앱을 빌드하는 방법을 단계별로 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="74049-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="74049-107">플러그 인은 코드, 청사진 및 예제를 통해 프로젝트에 일반 UX 기능을 추가하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74049-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![뷰포트에서 장면 종료](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="74049-109">시리즈를 마치면 다음에 대한 실습 경험을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74049-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="74049-110">새 프로젝트 시작</span><span class="sxs-lookup"><span data-stu-id="74049-110">Starting a new project</span></span>
* <span data-ttu-id="74049-111">혼합 현실 설정</span><span class="sxs-lookup"><span data-stu-id="74049-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="74049-112">사용자 입력 작업</span><span class="sxs-lookup"><span data-stu-id="74049-112">Working with user input</span></span>
* <span data-ttu-id="74049-113">단추 추가</span><span class="sxs-lookup"><span data-stu-id="74049-113">Adding buttons</span></span>
* <span data-ttu-id="74049-114">에뮬레이터 또는 디바이스에서 재생</span><span class="sxs-lookup"><span data-stu-id="74049-114">Playing on an emulator or device</span></span>

<span data-ttu-id="74049-115">궁금한 점은 [Unreal 개발 개요](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="74049-115">If you have any questions, check out our [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74049-116">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="74049-116">Prerequisites</span></span>
<span data-ttu-id="74049-117">진행하기 전에 다음 요구 사항에 부합하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="74049-117">Make sure you've met the following requirements before jumping in:</span></span>
* <span data-ttu-id="74049-118">Windows 10 1809 이상</span><span class="sxs-lookup"><span data-stu-id="74049-118">Windows 10 1809 or later</span></span>
* <span data-ttu-id="74049-119">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="74049-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="74049-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 이상</span><span class="sxs-lookup"><span data-stu-id="74049-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="74049-121">[개발용으로 구성된](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 디바이스 또는 에뮬레이터</span><span class="sxs-lookup"><span data-stu-id="74049-121">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="74049-122">Visual Studio 2019(아래 워크로드 포함)</span><span class="sxs-lookup"><span data-stu-id="74049-122">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="74049-123">Visual Studio 2019 설치</span><span class="sxs-lookup"><span data-stu-id="74049-123">Installing Visual Studio 2019</span></span>
<span data-ttu-id="74049-124">마지막 단계는 다음과 같이 Visual Studio를 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="74049-124">The last step is to setup Visual Studio as follows:</span></span>
1. <span data-ttu-id="74049-125">최신 버전의 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="74049-125">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="74049-126">다음 [워크로드](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="74049-126">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span></span>
    * <span data-ttu-id="74049-127">C++를 사용한 데스크톱 개발</span><span class="sxs-lookup"><span data-stu-id="74049-127">Desktop development with C++</span></span>
    * <span data-ttu-id="74049-128">.NET 데스크톱 개발</span><span class="sxs-lookup"><span data-stu-id="74049-128">.NET desktop development</span></span>
    * <span data-ttu-id="74049-129">유니버설 Windows 플랫폼 개발</span><span class="sxs-lookup"><span data-stu-id="74049-129">Universal Windows Platform development</span></span>

3. <span data-ttu-id="74049-130">다음 [구성 요소](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="74049-130">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span></span>
    * <span data-ttu-id="74049-131">컴파일러, 빌드 도구 및 런타임 > MSVC v142 - VS 2019 C++ ARM64 빌드 도구(최신 버전)</span><span class="sxs-lookup"><span data-stu-id="74049-131">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="74049-132">간단하죠.</span><span class="sxs-lookup"><span data-stu-id="74049-132">That's it!</span></span> <span data-ttu-id="74049-133">이제 체스 앱 프로젝트를 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="74049-133">You're all set to move on to starting the chess app project.</span></span>

[<span data-ttu-id="74049-134">다음 섹션: 2. 프로젝트 및 첫 번째 애플리케이션 초기화</span><span class="sxs-lookup"><span data-stu-id="74049-134">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)