---
title: Azure Spatial Anchors 자습서 - 1. 소개
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: f273c573d40b1e65e325bd31b5dd9e14c1ee66ec
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376555"
---
# <a name="1-introduction"></a><span data-ttu-id="c1d59-105">1. 소개</span><span class="sxs-lookup"><span data-stu-id="c1d59-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="c1d59-106">개요</span><span class="sxs-lookup"><span data-stu-id="c1d59-106">Overview</span></span>

<span data-ttu-id="c1d59-107">Azure Spatial Anchors 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="c1d59-108">이 자습서 시리즈를 통해 <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a>(ASA)의 기본 사항과 실제 환경에서 완벽하게 혼합된 현실 경험을 고정하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="c1d59-109">Android 및 iOS에 프로젝트를 배포하는 방법에 대해서도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="c1d59-110">이 시리즈의 자습서:</span><span class="sxs-lookup"><span data-stu-id="c1d59-110">Tutorials in this series:</span></span>

1. [<span data-ttu-id="c1d59-111">소개</span><span class="sxs-lookup"><span data-stu-id="c1d59-111">Introduction</span></span>](mr-learning-asa-01.md)
2. [<span data-ttu-id="c1d59-112">Azure Spatial Anchors 시작</span><span class="sxs-lookup"><span data-stu-id="c1d59-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="c1d59-113">Azure Spatial Anchors 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="c1d59-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="c1d59-114">Azure Spatial Anchor 피드백 표시</span><span class="sxs-lookup"><span data-stu-id="c1d59-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="c1d59-115">Android 및 iOS용 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c1d59-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="c1d59-116">목표</span><span class="sxs-lookup"><span data-stu-id="c1d59-116">Objectives</span></span>

* <span data-ttu-id="c1d59-117">공간 앵커를 만들고 Azure에서 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c1d59-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="c1d59-118">앱 세션 간에 공간 맞춤을 달성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c1d59-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="c1d59-119">여러 디바이스 간의 공간 맞춤을 구현하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c1d59-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="c1d59-120">Android 및 iOS에 대한 프로젝트를 준비, 빌드 및 배포하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c1d59-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1d59-121">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c1d59-121">Prerequisites</span></span>

* <span data-ttu-id="c1d59-122">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="c1d59-122">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="c1d59-123">Windows 10 SDK(10.0.18362.0 이상 버전)</span><span class="sxs-lookup"><span data-stu-id="c1d59-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="c1d59-124">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="c1d59-124">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="c1d59-125">Unity 2019.3.15가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="c1d59-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="c1d59-126">다음 자습서의 [Spatial Anchors 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료했습니다. [빠른 시작: Azure Spatial Anchors를 사용하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서)을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="c1d59-127">[시작 자습서](mr-learning-base-01.md) 시리즈 또는 Unity 및 MRTK를 사용하는 몇 가지 기본 사전 경험을 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="c1d59-128">Azure Spatial Anchors 계정을 만드는 [Azure Spatial Anchors 자습서](mr-learning-asa-01.md) 시리즈 또는 이전 환경을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-128">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or previous experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="c1d59-129">Android 및 HoloLens에 배포하려는 경우</span><span class="sxs-lookup"><span data-stu-id="c1d59-129">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="c1d59-130">Windows 또는 macOS 컴퓨터에 USB 연결을 사용하는 <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">개발자 사용</a> 및 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 지원 가능</a> Android 디바이스</span><span class="sxs-lookup"><span data-stu-id="c1d59-130">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="c1d59-131">Unity 2019.3.15가 설치되고 Android 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="c1d59-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="c1d59-132">iOS 및 HoloLens에 배포하려는 경우</span><span class="sxs-lookup"><span data-stu-id="c1d59-132">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="c1d59-133">최신 버전의 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 및 <a href="https://cocoapods.org" target="_blank">CocoaPods</a>가 설치된 macOS 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="c1d59-133">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="c1d59-134">macOS 컴퓨터에 USB로 연결된 <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 호환</a> iOS 디바이스</span><span class="sxs-lookup"><span data-stu-id="c1d59-134">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="c1d59-135">Unity 2019.3.15가 설치되고 iOS 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="c1d59-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="c1d59-136">이 자습서 시리즈에 추천되는 Mixed Reality Toolkit 버전은 MRTK 2.4.0입니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-136">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="c1d59-137">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.3.15입니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-137">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="c1d59-138">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="c1d59-138">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="c1d59-139">다음 자습서: 2. Azure Spatial Anchors를 사용하여 시작</span><span class="sxs-lookup"><span data-stu-id="c1d59-139">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
