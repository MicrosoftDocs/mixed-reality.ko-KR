---
title: DirectX의 공간 앵커를 공유합니다.
description: 공간 앵커를 공유 하 여 두 개의 HoloLens 장치를 동기화 하는 방법에 설명 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 동기화, 공간 앵커, 전송, 멀티 플레이 게임, 보기, 시나리오, 연습, 샘플 코드, Azure, Azure 공간 앵커 ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605062"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="c55be-104">DirectX의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="c55be-104">Shared experiences in DirectX</span></span>

<span data-ttu-id="c55be-105">공유 경험을 여러 사용자가 자신의 HoloLens, iOS 또는 Android 장치를 사용 하 여 전체적으로 확인 하 고 있는 공간에서 고정된 소수점에 배치 되는 동일한 홀로그램 상호 작용 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="c55be-106">이 공간 앵커 공유를 통해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="c55be-107">Azure 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="c55be-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="c55be-108">사용할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 앵커를 만들 내구성이 있는 클라우드 기반 공간에 앱 여러 HoloLens, iOS 및 Android 장치에서 찾을 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c55be-109">일반적인 공간 앵커를 여러 장치를 공유 각 사용자는 동일한 실제 위치에 해당 앵커에 상대적인 렌더링 된 콘텐츠를 볼 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="c55be-110">따라서 실시간 공유 환경.</span><span class="sxs-lookup"><span data-stu-id="c55be-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="c55be-111">사용할 수도 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> HoloLens, iOS 및 Android 장치에서 비동기 홀로그램 지 속성에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c55be-112">견고한 클라우드 공간 앵커를 공유 하 여 여러 장치 관찰할 수 있습니다 동일한 지속형된 홀로그램 시간이 지남에 따라 해당 장치를 동시에 함께 있는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="c55be-113">5 분을 사용해으로 시작 하려면 HoloLens 앱에서 공유 환경을 구축 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">공간 앵커 HoloLens Azure 빠른 시작</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-113">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="c55be-114">Azure 공간 앵커를 사용 하 여 실행을 했으면 할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens에 앵커를 찾아서 만들</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="c55be-115">연습에 사용할 수 있는 <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 및 iOS</a> 도 모든 장치에서 동일한 앵커를 공유할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-115">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="c55be-116">로컬 앵커 전송</span><span class="sxs-lookup"><span data-stu-id="c55be-116">Local anchor transfers</span></span>

<span data-ttu-id="c55be-117">Azure 공간 앵커를 사용할 수 없습니다 상황에서 [로컬 앵커 전송](local-anchor-transfers-in-directx.md) 두 번째 HoloLens 장치에서 가져올 앵커를 내보내려면 하나 HoloLens 장치를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-117">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="c55be-118">이 방법은 Azure 공간 앵커 보다 덜 강력 앵커 회수를 제공 하 고이 접근 방식에서 iOS 및 Android 장치를 지원 하지 않는 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="c55be-118">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="c55be-119">참조</span><span class="sxs-lookup"><span data-stu-id="c55be-119">See also</span></span>
* [<span data-ttu-id="c55be-120">혼합된 현실 환경 공유했습니다</span><span class="sxs-lookup"><span data-stu-id="c55be-120">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="c55be-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a></span><span class="sxs-lookup"><span data-stu-id="c55be-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="c55be-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure 공간 앵커 HoloLens 용 SDK</a></span><span class="sxs-lookup"><span data-stu-id="c55be-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>