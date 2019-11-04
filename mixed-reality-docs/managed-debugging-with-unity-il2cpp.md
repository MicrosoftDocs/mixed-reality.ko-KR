---
title: Unity를 사용 하 여 관리 되는 디버깅 IL2CPP
description: 이 문서에서는 Unity IL2CPP UWP 프로젝트에서 관리 되는 디버거를 실행 하는 방법을 설명 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, 디버깅, il2cpp
ms.openlocfilehash: fd09c3ca1bd410c56e46eb8e8815742f87482d08
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439634"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="b8218-104">Unity를 사용 하 여 관리 되는 디버깅 IL2CPP</span><span class="sxs-lookup"><span data-stu-id="b8218-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="b8218-105">다음 단계를 수행 하 여 관리 되는 디버거를 Unity IL2CPP UWP 빌드에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="b8218-106">이 가이드는 원래 HoloLens 및 HoloLens 2 용으로 개발 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="b8218-107">[멀티 캐스트](https://en.wikipedia.org/wiki/Multicast)를 지 원하는 네트워크에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="b8218-108">UWP 게시 설정 기능의 Unity에서 **Internetclientserver** 및 **PrivateNetworkClientServer** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![UWP 게시 설정 기능](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="b8218-110">Unity UWP 빌드 설정 구성:</span><span class="sxs-lookup"><span data-stu-id="b8218-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="b8218-111">개발 빌드</span><span class="sxs-lookup"><span data-stu-id="b8218-111">Development Build</span></span>
    - <span data-ttu-id="b8218-112">스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="b8218-112">Script Debugging</span></span>
    - <span data-ttu-id="b8218-113">관리 되는 디버거 대기 (옵션)</span><span class="sxs-lookup"><span data-stu-id="b8218-113">Wait for Managed Debugger (optional)</span></span>

    ![UWP 빌드 설정](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="b8218-115">Unity에서 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-115">Build in Unity.</span></span>
1. <span data-ttu-id="b8218-116">Visual Studio 솔루션에서 장치에 빌드 및 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="b8218-117">**디버그** 또는 **릴리스** 구성을 사용 하 여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="b8218-118">**마스터** 구성은 Unity 프로파일러를 사용 하지 않도록 설정 하 고 최적의 디버깅을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="b8218-119">필요한 경우 솔루션에서 appxmanifest.xml의 기능 목록에 있는 **인터넷 (클라이언트 & 서버)** 및 **개인 네트워크 (클라이언트 & 서버)** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="b8218-120">장치에서 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-120">Start the app on your device.</span></span> <span data-ttu-id="b8218-121">장치가 PC와 동일한 네트워크에 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="b8218-122">장치가 USB를 통해 PC에 연결 **되지** 않았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="b8218-123">C# 스크립트를 보고 편집할 수 있는 Unity에서 스크립트를 두 번 클릭 하면 생성 된 Visual Studio 솔루션으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-123">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="b8218-124">디버그 > Unity 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-124">Debug -> Attach Unity Debugger.</span></span>

    ![Unity 디버거 연결](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="b8218-126">목록에서 장치를 선택 하 고 "확인"을 클릭 하 여 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8218-126">Select your device in the list and click "OK" to attach.</span></span>

    ![장치 목록](images/il2cpp-debugging-machines.png)
