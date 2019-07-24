---
title: 앱에서 바로 구매
description: 앱 내 구매는 혼합 현실 앱에서 지원 되지만 몇 가지 작업을 설정 해야 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 앱에서 바로 구매, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515296"
---
# <a name="in-app-purchases"></a><span data-ttu-id="7fda7-104">앱에서 바로 구매</span><span class="sxs-lookup"><span data-stu-id="7fda7-104">In-app purchases</span></span>

<span data-ttu-id="7fda7-105">앱 내 구매는 HoloLens에서 지원 되지만 몇 가지 작업을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fda7-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="7fda7-106">앱 구매 기능에서을 활용 하려면 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fda7-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="7fda7-107">슬레이트로 표시할 XAML [2d 뷰](app-views.md) 만들기</span><span class="sxs-lookup"><span data-stu-id="7fda7-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="7fda7-108">이로 전환 하 여 배치를 활성화 하면 몰입 형 보기가 남습니다.</span><span class="sxs-lookup"><span data-stu-id="7fda7-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="7fda7-109">API: wait [Currentapp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fda7-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="7fda7-110">이 API는 앱 내 구매 이름, 설명 및 가격을 표시 하는 stock Windows OS 팝업을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fda7-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="7fda7-111">그러면 사용자가 구매 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fda7-111">The user can then choose purchase options.</span></span> <span data-ttu-id="7fda7-112">작업이 완료 되 면 앱은 사용자가 [몰입 형 보기로](app-views.md)다시 전환할 수 있도록 UI를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fda7-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="7fda7-113">데스크톱 기반 Windows Mixed Reality 모던 헤드셋을 대상으로 하는 앱의 경우 RequestProductPurchaseAsync API를 호출 하기 전에 XAML 뷰로 수동으로 전환할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fda7-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
