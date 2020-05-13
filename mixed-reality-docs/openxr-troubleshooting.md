---
title: OpenXR 문제 해결
description: OpenXR 응용 프로그램의 문제를 해결 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 문제 해결
ms.openlocfilehash: 269982596ed6162d9c2f1ec999a446bcecd6ba2a
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228008"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="7e352-104">OpenXR 문제 해결</span><span class="sxs-lookup"><span data-stu-id="7e352-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="7e352-105">Windows Mixed Reality OpenXR 런타임을 사용 하 여 OpenXR 앱을 개발할 때 발생 하는 몇 가지 문제 해결 팁은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="7e352-106"><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>에 대 한 다른 질문이 있는 경우 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 포럼</a> 또는 <a href="https://khr.io/slack" target="_blank">여유 시간 #openxr 채널</a>을 방문 하세요.</span><span class="sxs-lookup"><span data-stu-id="7e352-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="7e352-107">현재 Windows Mixed Reality OpenXR 런타임에 x86 앱과 관련 하 여 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="7e352-108">현재 x64 용 데스크톱 OpenXR 앱을 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="7e352-109">Windows Mixed Reality를 시작 하지 않는 OpenXR 앱</span><span class="sxs-lookup"><span data-stu-id="7e352-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="7e352-110">OpenXR 앱을 실행할 때 Windows Mixed Reality를 시작 하지 않는 경우 Windows Mixed Reality OpenXR 런타임이 활성 런타임으로 설정 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="7e352-111">[OpenXR For Windows Mixed Reality 헤드셋 시작](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 을 참조 하 여 런타임을 활성 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-111">Be sure to follow the instructions above for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="7e352-112">[Windows Mixed Reality OpenXR 개발자 도구](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) 를 실행 하 여 시스템의 Windows Mixed Reality OpenXR 런타임 상태에 대 한 추가 문제 해결 도움말을 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-112">You can also run the [Windows Mixed Reality OpenXR Developer Tools](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a><span data-ttu-id="7e352-113">혼합 현실 포털에서 "OpenXR 설정" 메뉴 항목을 표시 하지 않음</span><span class="sxs-lookup"><span data-stu-id="7e352-113">Mixed Reality Portal not showing "Set up OpenXR" menu item</span></span>

<span data-ttu-id="7e352-114">Windows 10 10 월 2018 업데이트 (1809) 이상을 실행 하 고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-114">Be sure you are running at least the Windows 10 October 2018 Update (1809).</span></span>  <span data-ttu-id="7e352-115">이전 버전의 Windows 10을 사용 하는 경우 [windows 10 업데이트 도우미](https://www.microsoft.com//software-download/windows10)를 사용 하 여 1903 (5 월 2019 업데이트)로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-115">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update (1903) using the [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10).</span></span>

<span data-ttu-id="7e352-116">이전 버전의 Mixed Reality 포털 앱이 있는 경우 "OpenXR 설정" 메뉴 항목을 사용 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-116">The "Set up OpenXR" menu item may not be available if you have an older version of the Mixed Reality Portal app.</span></span>  <span data-ttu-id="7e352-117">[혼합 현실 포털 앱 업데이트](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) 를 확인 하 여 최신 버전이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-117">Check for a [Mixed Reality Portal app update](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) to ensure you have the latest version.</span></span>

<span data-ttu-id="7e352-118">Windows Mixed Reality OpenXR 런타임이 이미 설치 되어 있고 활성 상태인 경우에는 "OpenXR 설정" 메뉴 항목이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-118">Note that the "Set up OpenXR" menu item will not show up if the Windows Mixed Reality OpenXR Runtime is already installed and active.</span></span>  <span data-ttu-id="7e352-119">[Windows Mixed Reality OpenXR 개발자 도구](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) 를 설치 하 여 시스템에서 OpenXR 런타임의 현재 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e352-119">You can install the [Windows Mixed Reality OpenXR Developer Tools](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) to determine the current status of the OpenXR runtime on your system.</span></span>