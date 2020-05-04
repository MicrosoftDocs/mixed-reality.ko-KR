---
title: Unreal 개발 개요
description: Unreal에서 혼합 현실 앱 빌드를 시작합니다.
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 베타, 스트리밍, 원격, 혼합 현실, 개발, 시작, 새 프로젝트, 에뮬레이터, 설명서
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491175"
---
# <a name="unreal-development-overview"></a><span data-ttu-id="27246-104">Unreal 개발 개요</span><span class="sxs-lookup"><span data-stu-id="27246-104">Unreal development overview</span></span>

<span data-ttu-id="27246-105">Unreal Engine 4에 대한 혼합 현실 지원은 현재 베타 버전입니다!</span><span class="sxs-lookup"><span data-stu-id="27246-105">Mixed reality support for Unreal Engine 4 is now in beta!</span></span> <span data-ttu-id="27246-106">Unreal 개발을 처음 접하는 경우 <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Unreal Engine 4 시작</a> 페이지를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="27246-106">If you're new to Unreal development, <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Getting Started with Unreal Engine 4</a> is a great page to explore.</span></span> <span data-ttu-id="27246-107">자산이 필요한 경우 Unreal에는 포괄적인 <a href="https://www.unrealengine.com/marketplace//store" target="_blank">마켓플레이스</a>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27246-107">If you need assets, Unreal has a comprehensive <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>.</span></span> 

<span data-ttu-id="27246-108">Unreal Engine 4에 대해 기본적으로 이해한 경우 Unreal Engine 설명서 사이트의 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens Development</a> 페이지를 방문하여 HoloLens에서 앱을 빌드하고 실행하는 방법에 대해 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27246-108">Once you've built a basic understanding of Unreal Engine 4, you can visit the <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens Development</a> page on the Unreal Engine documentation site to learn how to build and run your apps on HoloLens.</span></span> <span data-ttu-id="27246-109">Unreal에서 혼합 현실 앱을 빌드하는 커뮤니티에 참여하려면 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality 포럼</a>을 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="27246-109">Be sure to visit the <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality forums</a> to engage with the community who build mixed reality apps in Unreal.</span></span> <span data-ttu-id="27246-110">여기는 발생할 수 있는 문제에 대한 해결 방법을 찾는 데 적합한 장소입니다.</span><span class="sxs-lookup"><span data-stu-id="27246-110">It's a great place to find solutions to problems you might run into.</span></span>

## <a name="installing-the-prerequisites"></a><span data-ttu-id="27246-111">필수 구성 요소 설치</span><span class="sxs-lookup"><span data-stu-id="27246-111">Installing the prerequisites</span></span>

<span data-ttu-id="27246-112">Unreal에서 HoloLens 2 앱 빌드를 시작하려면 [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md) 또는 HoloLens 헤드셋이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="27246-112">To get started with building a HoloLens 2 app in Unreal, you'll need the [HoloLens 2 Emulator](using-the-hololens-emulator.md) or a HoloLens headset.</span></span> <span data-ttu-id="27246-113">또한 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">Unreal용 HoloLens 2 필수 구성 요소</a>에 나열된 워크로드와 구성 요소를 사용하여 최신 버전의 Visual Studio를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27246-113">You'll also need to install the latest version of Visual Studio with the workloads and components listed in <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">HoloLens 2 Prerequisites for Unreal</a>.</span></span>

## <a name="building-and-running-your-unreal-app"></a><span data-ttu-id="27246-114">Unreal 앱 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="27246-114">Building and running your Unreal app</span></span>

<span data-ttu-id="27246-115">먼저 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">HoloLens 2용 앱을 패키지합니다</a>.</span><span class="sxs-lookup"><span data-stu-id="27246-115">First, <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">package your app for HoloLens 2</a>.</span></span> <span data-ttu-id="27246-116">다음으로 패키지를 배포할 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27246-116">Next, choose where you want to deploy your package:</span></span>
* <span data-ttu-id="27246-117"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">HoloLens 2 에뮬레이터에 배포</a></span><span class="sxs-lookup"><span data-stu-id="27246-117"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">Deploy to the HoloLens 2 Emulator</a></span></span>
* <span data-ttu-id="27246-118"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">HoloLens 2 헤드셋에 배포</a></span><span class="sxs-lookup"><span data-stu-id="27246-118"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">Deploy to a HoloLens 2 Headset</a></span></span>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a><span data-ttu-id="27246-119">홀로그램 원격 플레이어를 통해 앱을 헤드셋으로 스트리밍</span><span class="sxs-lookup"><span data-stu-id="27246-119">Streaming your app to a headset via the Holographic Remoting Player</span></span>

<span data-ttu-id="27246-120">앱을 데스크톱에서 HoloLens 헤드셋의 홀로그램 원격 플레이어 앱으로 스트림하면 두 가지 주요 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27246-120">Streaming your app from your desktop to the Holographic Remoting Player app on a HoloLens headset has two main advantages:</span></span> 
* <span data-ttu-id="27246-121">개발 속도를 높이므로 변경할 때마다 앱을 다시 패키지하고 업로드할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27246-121">Speeds up development, so there's no need to repackage and upload your app each time you make a change</span></span>
* <span data-ttu-id="27246-122">데스크톱의 기능을 활용하므로 헤드셋에서 사용할 수 있는 컴퓨터의 제한 없이 데스크톱 GPU에서 허용하는 만큼 많은 다각형을 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27246-122">Leverages the power of your desktop, so you can render as many polygons as your desktop GPU allows, without being limited by the computer available on the headset</span></span>

<span data-ttu-id="27246-123">스트리밍을 시작하려면 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 스트리밍 빠른 시작</a>[]()을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="27246-123">To get started with streaming, check out the <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 Streaming Quick Start</a>[]().</span></span>

## <a name="see-also"></a><span data-ttu-id="27246-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27246-124">See also</span></span>
* <span data-ttu-id="27246-125"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">모바일 디바이스에 대한 Unreal 성능 지침</a></span><span class="sxs-lookup"><span data-stu-id="27246-125"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a></span></span>
