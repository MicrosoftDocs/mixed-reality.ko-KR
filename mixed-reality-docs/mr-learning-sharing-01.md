---
title: 다중 사용자 기능 자습서 - 1. 소개
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: eff600ba6388732ab9aa200ce41494cac1dddf35
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306800"
---
# <a name="1-introduction"></a><span data-ttu-id="be33d-105">1. 소개</span><span class="sxs-lookup"><span data-stu-id="be33d-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="be33d-106">개요</span><span class="sxs-lookup"><span data-stu-id="be33d-106">Overview</span></span>

<span data-ttu-id="be33d-107">다중 사용자 기능 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-107">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="be33d-108">이 자습서 시리즈를 통해 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity 네트워킹</a>(PUN)을 사용하여 다중 사용자 환경을 구축하는 기본 사항을 배우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-108">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="be33d-109">PUN은 혼합 현실 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-109">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="be33d-110">이 시리즈의 자습서:</span><span class="sxs-lookup"><span data-stu-id="be33d-110">Tutorials in this series:</span></span>

* [<span data-ttu-id="be33d-111">Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="be33d-111">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="be33d-112">여러 사용자 연결</span><span class="sxs-lookup"><span data-stu-id="be33d-112">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="be33d-113">여러 사용자와 개체 움직임 공유</span><span class="sxs-lookup"><span data-stu-id="be33d-113">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="be33d-114">공유 환경에 Azure Spatial Anchors 통합</span><span class="sxs-lookup"><span data-stu-id="be33d-114">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="be33d-115">목표</span><span class="sxs-lookup"><span data-stu-id="be33d-115">Objectives</span></span>

* <span data-ttu-id="be33d-116">PUN 앱을 만들고 Unity 프로젝트를 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="be33d-116">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="be33d-117">공유 환경에서 여러 사용자를 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="be33d-117">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="be33d-118">개체 이동을 다른 사용자와 공유하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="be33d-118">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="be33d-119">여러 디바이스 간의 공간 맞춤을 구현하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="be33d-119">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be33d-120">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="be33d-120">Prerequisites</span></span>

* <span data-ttu-id="be33d-121">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="be33d-121">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="be33d-122">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="be33d-122">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="be33d-123">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="be33d-123">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="be33d-124">Unity 2019.3.15가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="be33d-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="be33d-125">다음 자습서의 [Spatial Anchors 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료했습니다. [빠른 시작: Azure Spatial Anchors를 사용하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서)을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-125">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="be33d-126">[시작 자습서](mr-learning-base-01.md) 시리즈 또는 Unity 및 MRTK를 사용하는 몇 가지 기본 사전 경험을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-126">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="be33d-127">Azure Spatial Anchors 계정을 만드는 [Azure Spatial Anchors 자습서](mr-learning-asa-01.md) 시리즈 또는 이전 환경을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-127">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="be33d-128">Android 및 HoloLens에 배포하려는 경우</span><span class="sxs-lookup"><span data-stu-id="be33d-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="be33d-129">Windows 또는 macOS 컴퓨터에 USB 연결을 사용하는 <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">개발자 사용</a> 및 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 지원 가능</a> Android 디바이스</span><span class="sxs-lookup"><span data-stu-id="be33d-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="be33d-130">Unity 2019.3.15가 설치되고 Android 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="be33d-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="be33d-131">iOS 및 HoloLens에 배포하려는 경우</span><span class="sxs-lookup"><span data-stu-id="be33d-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="be33d-132">최신 버전의 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 및 <a href="https://cocoapods.org" target="_blank">CocoaPods</a>가 설치된 macOS 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="be33d-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="be33d-133">macOS 컴퓨터에 USB로 연결된 <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 호환</a> iOS 디바이스</span><span class="sxs-lookup"><span data-stu-id="be33d-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="be33d-134">Unity 2019.3.15가 설치되고 iOS 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="be33d-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="be33d-135">이 자습서 시리즈에 추천되는 Mixed Reality Toolkit 버전은 MRTK 2.4.0입니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="be33d-136">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.3.15입니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="be33d-137">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="be33d-138">다음 자습서: 2. Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="be33d-138">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
