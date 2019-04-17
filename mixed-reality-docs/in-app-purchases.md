---
title: 앱에서 바로 구매
description: 앱에서 바로 구매 혼합된 현실 앱에서 지원 되지만 몇 가지 작업을 설정 하는 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 앱 내 구매, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602880"
---
# <a name="in-app-purchases"></a><span data-ttu-id="33019-104">앱에서 바로 구매</span><span class="sxs-lookup"><span data-stu-id="33019-104">In-app purchases</span></span>

<span data-ttu-id="33019-105">앱에서 바로 구매 HoloLens에 지 이지만 일부 작업을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33019-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="33019-106">앱에서 구매를 활용 하기 위해 기능을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33019-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="33019-107">XAML을 만들 [2D 보기](app-views.md) 슬레이트를 표시 하려면</span><span class="sxs-lookup"><span data-stu-id="33019-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="33019-108">몰입 형 보기 상태로 유지 하는 배치를 활성화 하려면 전환</span><span class="sxs-lookup"><span data-stu-id="33019-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="33019-109">API 호출: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="33019-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="33019-110">이 API는 인 앱 구매 이름, 설명 및 가격을 보여 주는 주식 Windows OS 팝업을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="33019-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="33019-111">사용자는 구매 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33019-111">The user can then choose purchase options.</span></span> <span data-ttu-id="33019-112">앱 다시 전환할 수 있는 UI를 제공 해야 합니다는 작업이 완료 되 면 해당 [몰입 형 뷰](app-views.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="33019-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="33019-113">Windows Mixed Reality 몰입 형 헤드셋 데스크톱 기반을 대상으로 하는 앱에 대 한 필요가 직접 RequestProductPurchaseAsync API를 호출 하기 전에 XAML 보기로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="33019-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
