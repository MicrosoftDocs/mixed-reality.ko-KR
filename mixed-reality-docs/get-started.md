---
title: 시작
description: 이 가이드에는 혼합된 현실 개발을 사용 하 여 즉시 가동 및 실행 하는 가장 빠른 방법은 간략하게 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 시작, 기초, HoloLens, 몰입 형 헤드셋, ar, vr, unity, visual studio, 빠른 시작 하는 방법
ms.openlocfilehash: 92fbc6eee227da571ff36401f84cf81a093062d7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601345"
---
# <a name="get-started"></a><span data-ttu-id="e82d1-104">시작</span><span class="sxs-lookup"><span data-stu-id="e82d1-104">Get started</span></span>

<span data-ttu-id="e82d1-105">혼합된 현실 개발을 시작 합니다!</span><span class="sxs-lookup"><span data-stu-id="e82d1-105">Welcome to the world of mixed reality development!</span></span> <span data-ttu-id="e82d1-106">MR 접하는 경우이 가이드는 시작 하려면 허브 및 최대한 빨리 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-106">If you're new to MR, this guide will be your hub to get up and running as quickly as possible.</span></span> <span data-ttu-id="e82d1-107">개발에 대 한 사용자 PC의 집합을 시작, 장치, 준비 및 MR 개발 프로세스를 신속 하 게 하는 도구를 설치 하 게 도울 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-107">We'll help you get your PC set up for development, get your device(s) ready, and install tools that will speed up the MR development process.</span></span> 

## <a name="intro-to-mixed-reality"></a><span data-ttu-id="e82d1-108">혼합된 현실에 대 한 소개</span><span class="sxs-lookup"><span data-stu-id="e82d1-108">Intro to mixed reality</span></span>

<span data-ttu-id="e82d1-109">"Mixed reality"가 뭐 냐고요 및 연결 증강된 현실 (AR) 하는 방법에 대 한 몇 가지 질문을 해야 하 고 가상 현실 (VR).</span><span class="sxs-lookup"><span data-stu-id="e82d1-109">You may have some questions about what we mean by "mixed reality" and how it relates to augmented reality (AR) and virtual reality (VR).</span></span> <span data-ttu-id="e82d1-110">즉, 혼합된 현실은 확대 된 현실에서 모든 항목을 다루는 스펙트럼 이므로 디지털 세계와 실제 세계의 혼합 현실 세계에 거의 완전히 인 가상 현실에 실제 세계에서 디지털 콘텐츠 위치 디지털 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-110">In short, mixed reality is the blending of the physical world with the digital world, so it's a spectrum that covers everything from augmented reality, where digital content is placed in the real world, to virtual reality, where your real world is almost entirely replaced by the digital.</span></span> 

<span data-ttu-id="e82d1-111">![HoloLens 및 몰입 형 (VR) 헤드셋을 지 원하는 혼합된 현실 앱의 예제](images/mr-island.png)</span><span class="sxs-lookup"><span data-stu-id="e82d1-111">![Example of a mixed reality app that supports both HoloLens and immersive (VR) headsets](images/mr-island.png)</span></span><br>
<span data-ttu-id="e82d1-112">*HoloLens 및 몰입 형 (VR) 헤드셋 혼합된 현실 앱 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="e82d1-112">*Mixed reality apps can support both HoloLens and immersive (VR) headsets*</span></span>

<span data-ttu-id="e82d1-113">Windows Mixed Reality MR 스펙트럼을 처리할 수 있는 도구 집합을 단일 개발 플랫폼으로 만든 및 현재 동일한 스펙트럼을 포괄 하는 두 개의 장치 유형을 지원: [Microsoft HoloLens](https://www.microsoft.com/hololens), 전 세계의 첫 번째 독립적인된 holographic 헤드셋, 및 [Windows Mixed Reality 몰입 형 헤드셋 및 동작 컨트롤러](https://www.microsoft.com/windows/windows-mixed-reality), 강력한 가상 현실 환경에 대 한 PC에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-113">We created Windows Mixed Reality as a single development platform and set of tools that can cover the MR spectrum, and we currently support two device types that cover the same spectrum: [Microsoft HoloLens](https://www.microsoft.com/hololens), the world's first self-contained holographic headset, and [Windows Mixed Reality immersive headsets and motion controllers](https://www.microsoft.com/windows/windows-mixed-reality), which connect to a PC for powerful virtual reality experiences.</span></span> <span data-ttu-id="e82d1-114">이 내용을 확인할 수 있습니다 [혼합 현실?] (문서를 보다 정확 하 게 응답 하려는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-114">You can check out our What is [mixed reality?]( article for a more thorough answer if you're interested.</span></span>

## <a name="choose-your-development-path"></a><span data-ttu-id="e82d1-115">배포 경로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-115">Choose your development path</span></span>

<span data-ttu-id="e82d1-116">혼합된 현실 앱을 개발 하는 가장 쉬운 방법은 사용 하 여 [Unity](https://unity3d.com), 게임 개발에 대 한 자주 사용 되는 미들웨어를 강력 하 고 인기 있는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-116">The easiest way to develop a mixed reality app is using [Unity](https://unity3d.com), a powerful and popular middleware tool often used for game development.</span></span> <span data-ttu-id="e82d1-117">사용자 지정 엔진을 사용 하려는 경우 수도 있습니다 [DirectX에 대 한 빌드](directx-development-overview.md), 하지만 대부분의 MR 개발자가 게임 및 앱에 대 한 Unity를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-117">If you want to use a custom engine, you can also [build against DirectX](directx-development-overview.md), but most MR developers use Unity for their games and apps.</span></span> <span data-ttu-id="e82d1-118">Unity를 사용 하 여 HoloLens, (VR) 헤드셋 몰입 형, 또는 둘 다를 대상으로 하는 혼합된 현실 앱을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-118">With Unity you'll be able to create a mixed reality app that targets HoloLens, immersive (VR) headsets, or both!</span></span>

## <a name="prepare-your-pc-and-devices-for-development"></a><span data-ttu-id="e82d1-119">PC 및 장치 개발을 위한 준비</span><span class="sxs-lookup"><span data-stu-id="e82d1-119">Prepare your PC and devices for development</span></span>

<span data-ttu-id="e82d1-120">HoloLens, (VR) 헤드셋 몰입 형, 또는 둘 다를 대상으로 하는 혼합된 현실 앱을 빌드하는 지 여부를 일반적인 도구와 Api 집합을 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-120">Whether you're building a mixed reality app that targets HoloLens, immersive (VR) headsets, or both, you'll be using a common set of tools and APIs.</span></span> <span data-ttu-id="e82d1-121">또한 PC 개발을 충분히 강력한 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-121">You'll also want to make sure your PC is powerful enough for the development you'll be doing.</span></span> 

>[!NOTE]
><span data-ttu-id="e82d1-122">권장 되는 개발 PC 사양에서 지원 되는 버전의 각 소프트웨어 도구 및 관련 설정 또는 구성에서 각각에 대 한 정보를 찾을 수 있습니다 합니다 [도구를 설치](install-the-tools.md) 문서.</span><span class="sxs-lookup"><span data-stu-id="e82d1-122">You can find our recommendations on development PC specs, supported versions of each software tool, and relevant settings or configuration notes for each in the [Install the tools](install-the-tools.md) article.</span></span> <span data-ttu-id="e82d1-123">아래 도구를 설치 하기 전에 해당 문서를 검토 하세요.</span><span class="sxs-lookup"><span data-stu-id="e82d1-123">Please review that article before installing the tools below.</span></span>

<span data-ttu-id="e82d1-124">설치 하는 도구:</span><span class="sxs-lookup"><span data-stu-id="e82d1-124">Tools to install:</span></span>
* [<span data-ttu-id="e82d1-125">Unity</span><span class="sxs-lookup"><span data-stu-id="e82d1-125">Unity</span></span>](https://store.unity.com/download)
* [<span data-ttu-id="e82d1-126">Visual Studio (windows 10 SDK)</span><span class="sxs-lookup"><span data-stu-id="e82d1-126">Visual Studio (with Windows 10 SDK)</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="e82d1-127">Unity 용 혼합된 현실 도구 키트</span><span class="sxs-lookup"><span data-stu-id="e82d1-127">Mixed Reality Toolkit for Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

<span data-ttu-id="e82d1-128">또한 하려는 [대상 장치의 개발자 모드로 설정 하 고 대상 장치에 앱을 배포 하기 위한 Visual Studio 구성](using-visual-studio.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-128">You'll also want to [put your target device into Developer mode and configure Visual Studio for deploying apps to the target device](using-visual-studio.md).</span></span>

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e82d1-129">혼합 현실 용 도구 키트에 Unity에 대 한 메모</span><span class="sxs-lookup"><span data-stu-id="e82d1-129">A note about the Mixed Reality Toolkit for Unity</span></span>

![Unity에 대 한 MRTK](images/mrtkandunity.png)<br>

<span data-ttu-id="e82d1-131">***YOYO이 구체화 후 왜 MRTK UNITY 정말 대단한 있고 모든 멋진 내부:) 모든 사람에 게***</span><span class="sxs-lookup"><span data-stu-id="e82d1-131">***YOYO PLEASE FLESH THIS OUT AND TELL EVERYONE WHY MRTK-UNITY IS SO AMAZING AND ALL THE COOL THINGS IT HAS INSIDE :)***</span></span>

<span data-ttu-id="e82d1-132">혼합 현실 도구 키트는 스크립트 컬렉션 구성 요소를 하며 Microsoft HoloLens 및 Windows Mixed Reality 헤드셋을 대상으로 하는 응용 프로그램의 개발을 가속화 하세요.</span><span class="sxs-lookup"><span data-stu-id="e82d1-132">The Mixed Reality Toolkit is a collection of scripts and components intended to accelerate development of applications targeting Microsoft HoloLens and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="e82d1-133">프로젝트는 장벽이 혼합된 현실 응용 프로그램을 만들고 우리가 증가 함에 따라 커뮤니티에 다시 기여에 항목을 줄이는 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-133">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span>

## <a name="start-your-first-mr-project"></a><span data-ttu-id="e82d1-134">첫 번째 MR 프로젝트 시작</span><span class="sxs-lookup"><span data-stu-id="e82d1-134">Start your first MR project</span></span>

<span data-ttu-id="e82d1-135">이제는 PC와 장치 설정 되 면 Unity에서 첫 번째 혼합된 현실 프로젝트를 만들 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-135">Now that your PC and device(s) are set up, you're ready to create your first mixed reality project in Unity.</span></span> <span data-ttu-id="e82d1-136">첫 번째 MR academy 과정을 따르려면 [MR 기본 사항 100: Unity를 사용 하 여 시작](holograms-100.md), 혼합된 현실 헤드셋에서 실행 되 고 큐브 엔드에서 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-136">Follow along with our first MR academy course, [MR Basics 100: Getting started with Unity](holograms-100.md), and by the end you'll have a cube up and running in a mixed reality headset.</span></span>

<span data-ttu-id="e82d1-137">![혼합된 현실 Unity 프로젝트의 큐브 스크린 샷](images/mr-cube.PNG)</span><span class="sxs-lookup"><span data-stu-id="e82d1-137">![Screenshot of a cube in a mixed reality Unity project](images/mr-cube.PNG)</span></span><br>
<span data-ttu-id="e82d1-138">*첫 번째 혼합된 현실 프로젝트에 Unity-hello world!*</span><span class="sxs-lookup"><span data-stu-id="e82d1-138">*Your first mixed reality project in Unity - hello world!*</span></span>

## <a name="learn-more-and-get-help"></a><span data-ttu-id="e82d1-139">자세히 알아보고 도움말을 보려면</span><span class="sxs-lookup"><span data-stu-id="e82d1-139">Learn more and get help</span></span>

<span data-ttu-id="e82d1-140">첫 번째 MR 프로젝트를 성공적으로 만든 했으므로 자세한 아마도 배고픈 완료 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="e82d1-140">Now that you've successfully created your first MR project, you're probably hungry for more!</span></span> <span data-ttu-id="e82d1-141">해야 하는 데 도움이 되는 일부 리소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-141">Here are some resources that should help:</span></span>
* <span data-ttu-id="e82d1-142">[혼합 현실 개발자 설명서](mixed-reality.md) -아직 여기 이지만 등 많은 기술 문서, 디자인 지침, 샘플 프로젝트 및 사례 연구를 포함 하 여 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-142">[Mixed reality developer documentation](mixed-reality.md) - you're already here, but there's so much more to check out, including technical documentation, design guidance, sample projects, and case studies.</span></span>
* <span data-ttu-id="e82d1-143">[혼합된 현실 academy](academy.md) -핵심 MR 구성 요소를 구현 하는 데 프로젝트 설정에서 모든 내용을 다루는 자습서를 따라, MR 앱에 클라우드 서비스에 Azure를 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-143">[Mixed reality academy](academy.md) - follow along with tutorials covering everything from setting up projects, to implementing core MR building blocks, to integrating Azure cloud services into your MR app.</span></span>
* <span data-ttu-id="e82d1-144">[Unity에 알아봅니다](https://unity3d.com/learn) -Unity의 웹 사이트가 학습 과정의 모든 단계에서 작성자에 대 한 자습서, 프로젝트 및 라이브 교육 세션 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-144">[Learn Unity](https://unity3d.com/learn) - Unity's website offers tutorials, projects, and live training sessions for creators at every stage of learning.</span></span>

<span data-ttu-id="e82d1-145">또한 이러한 유용한 커뮤니티 리소스에서 도움말을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-145">You can also get help from these great community resources:</span></span>
* <span data-ttu-id="e82d1-146">[혼합 현실을 개발자 포럼](https://forums.hololens.com/) -요청 및 질문에 답변으로 Microsoft에서 직접 MR 개발 뉴스 읽기 혼합된 현실 개발자를 위한 공식 포럼입니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-146">[Mixed reality developer forums](https://forums.hololens.com/) - the official forum for mixed reality developers to ask and answer questions, as well as read MR development news straight from Microsoft.</span></span>
* <span data-ttu-id="e82d1-147">[HoloDevelopers Slack 채널](https://holodevelopersslack.azurewebsites.net/) -가장 강력 하 고 략이 외부 혼합 현실 관련 개발자 채널은 여기에 개발자 지식 및 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-147">[HoloDevelopers Slack channel](https://holodevelopersslack.azurewebsites.net/) - the most robust and resourceful external mixed reality-specific developer channel; the devs here are knowledgeable and helpful.</span></span>
* <span data-ttu-id="e82d1-148">[Unity 포럼](https://forum.unity3d.com/) -Unity의 공식 포럼입니다.</span><span class="sxs-lookup"><span data-stu-id="e82d1-148">[Unity forums](https://forum.unity3d.com/) - Unity's official forums.</span></span>
