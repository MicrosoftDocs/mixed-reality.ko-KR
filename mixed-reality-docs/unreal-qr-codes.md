---
title: Unreal의 QR 코드
description: Unreal에서 QR 코드 사용 가이드
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, qr 코드
ms.openlocfilehash: 90a51227ae455389168fb3262e83f34b64a7bfb5
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428742"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="93c5a-104">Unreal의 QR 코드</span><span class="sxs-lookup"><span data-stu-id="93c5a-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="93c5a-105">개요</span><span class="sxs-lookup"><span data-stu-id="93c5a-105">Overview</span></span>

<span data-ttu-id="93c5a-106">HoloLens 2는 웹캠을 사용하여 세계 공간에서 QR 코드를 볼 수 있습니다. 즉, 각 코드의 실세계 위치에서 좌표계를 사용하여 스스로를 홀로그램으로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="93c5a-107">HoloLens 2는 단일 QR 코드 외에도, 공유 경험을 만들기 위해 여러 디바이스에서 동일한 위치에 홀로그램을 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="93c5a-108">애플리케이션에 QR 코드를 추가하기 위한 모범 사례를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="93c5a-109">자동 영역</span><span class="sxs-lookup"><span data-stu-id="93c5a-109">Quiet zones</span></span>
- <span data-ttu-id="93c5a-110">조명 및 배경</span><span class="sxs-lookup"><span data-stu-id="93c5a-110">Lighting and backdrop</span></span>
- <span data-ttu-id="93c5a-111">크기, 거리 및 각도 위치</span><span class="sxs-lookup"><span data-stu-id="93c5a-111">Size, distance, and angular position</span></span>

<span data-ttu-id="93c5a-112">QR 코드가 앱에 배치될 때 [환경 고려 사항](environment-considerations-for-hololens.md)에 특히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="93c5a-113">이러한 각각의 토픽에 대한 자세한 정보와 필요한 NuGet 패키지를 다운로드하는 방법에 대한 지침은 주 [QR 코드 추적](qr-code-tracking.md) 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="93c5a-114">QR 검색 사용</span><span class="sxs-lookup"><span data-stu-id="93c5a-114">Enabling QR detection</span></span>
<span data-ttu-id="93c5a-115">HoloLens 2는 웹캠을 사용하여 QR 코드를 확인해야 하므로 프로젝트 설정에서 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="93c5a-116">**편집 > 프로젝트 설정**을 열고 **플랫폼** 섹션까지 아래로 스크롤한 다음, **HoloLens**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="93c5a-117">**기능** 섹션을 확장하고 **웹캠**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="93c5a-118">또한 [ARSessionConfig 자산](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)을 추가하여 QR 코드 추적을 옵트인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="93c5a-119">추적 이미지 설정</span><span class="sxs-lookup"><span data-stu-id="93c5a-119">Setting up a tracked image</span></span>

<span data-ttu-id="93c5a-120">QR 코드는 Unreal의 AR 추적 기하 도형 시스템을 통해 추적 이미지로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-120">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="93c5a-121">이 작업을 수행하려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-121">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="93c5a-122">청사진을 만들고 **ARTrackableNotify** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-122">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![QR AR 추적 가능 알림](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="93c5a-124">**ARTrackableNotify**를 선택하고 **세부 정보** 패널에서 **이벤트** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-124">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![QR 이벤트](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="93c5a-126">**추적 기하 도형 추가** 옆의 **+** 를 클릭하여 이벤트 그래프에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-126">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="93c5a-127">[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 구성 요소 API에서 이벤트의 전체 목록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-127">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![QR 렌더링 예제](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="93c5a-129">추적 이미지 사용</span><span class="sxs-lookup"><span data-stu-id="93c5a-129">Using a tracked image</span></span>
<span data-ttu-id="93c5a-130">다음 이미지의 이벤트 그래프는 QR 코드의 가운데에 점을 렌더링하고 그 데이터를 출력하는 데 사용되는 **OnUpdateTrackedImage** 이벤트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-130">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![QR 렌더링 예제](images/unreal-qr-render.PNG)

<span data-ttu-id="93c5a-132">다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-132">Here's waht's going on:</span></span>
1. <span data-ttu-id="93c5a-133">먼저 추적 이미지를 **ARTrackedQRCode**에 캐스트하여 현재 업데이트된 이미지가 QR 코드인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="93c5a-134">인코딩된 데이터는 **QRCode** 변수에서 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="93c5a-135">**GetLocalToWorldTransform** 위치에서 QR 코드의 왼쪽 위를, **GetEstimateSize**로 크기를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="93c5a-136">코드에서 [QR 코드 좌표계를 가져올 수](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-136">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="93c5a-137">고유 ID 찾기</span><span class="sxs-lookup"><span data-stu-id="93c5a-137">Finding the unique ID</span></span>
<span data-ttu-id="93c5a-138">모든 QR 코드에는 다음을 통해 찾을 수 있는 고유한 guid ID가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="93c5a-139">**As ARTracked QRCode** 핀을 끌어서 놓고 검색하여 **고유 ID 가져오기**</span><span class="sxs-lookup"><span data-stu-id="93c5a-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR Guid](images/unreal-qr-guid.PNG)

<span data-ttu-id="93c5a-141">QR 코드를 사용하기 위해서는 뒤에서 많은 작업이 필요하므로 이것이 전부는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="93c5a-141">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="93c5a-142">내부 작업을 더 상세히 설명하는 다음 링크를 확인해 보세요.</span><span class="sxs-lookup"><span data-stu-id="93c5a-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="93c5a-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93c5a-143">See also</span></span>
* [<span data-ttu-id="93c5a-144">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="93c5a-144">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="93c5a-145">홀로그램</span><span class="sxs-lookup"><span data-stu-id="93c5a-145">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="93c5a-146">좌표계</span><span class="sxs-lookup"><span data-stu-id="93c5a-146">Coordinate systems</span></span>](coordinate-systems.md)