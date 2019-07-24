---
title: 홈에서 3D 모델 배치 사용
description: Windows Mixed Reality 홈에서 웹 사이트 또는 응용 프로그램의 3D 모델을 준비 하는 방법
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, 모델, 홈, 장소, 세계, 모델링, 혼합 현실 홈, 웹, 앱
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829727"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="9e12a-104">혼합 현실 홈에서 3D 모델 배치 사용</span><span class="sxs-lookup"><span data-stu-id="9e12a-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="9e12a-105">이 기능은 [Windows 10 4 월 2018 업데이트](release-notes-april-2018.md)의 일부로 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="9e12a-106">이전 버전의 Windows는이 기능과 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="9e12a-107">[Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 은 사용자가 응용 프로그램을 시작 하기 전에 수행 하는 시작 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="9e12a-108">일부 시나리오에서는 2D 앱 (예: Holograms 앱)을 사용 하 여 3D 모델을 혼합 현실 홈으로 직접 배치 하거나 전체 3D에서 추가 검사를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="9e12a-109">*모델 추가 프로토콜* 을 사용 하 여 웹 사이트 또는 응용 프로그램의 3d 모델을 Windows Mixed Reality 홈으로 직접 보낼 수 있습니다. 여기서 [3d 앱](3d-app-launcher-design-guidance.md)시작, 2d 앱 및 holograms와 같은 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="9e12a-110">예를 들어 공간을 디자인 하기 위해 3D 가구의 카탈로그를 표시 하는 응용 프로그램을 개발 하는 경우 *모델 추가 프로토콜* 을 사용 하 여 사용자가 카탈로그에서 이러한 3d 가구 모델을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="9e12a-111">전 세계에 배치 되 면 사용자는 집에서 다른 holograms 마찬가지로 이러한 3D 모델을 이동 하 고 크기를 조정 하 고 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="9e12a-112">이 문서에서는 사용자가 응용 프로그램 또는 웹에서 3D 개체를 사용 하 여 세계를 데코레이팅하는 데 사용할 수 있도록 하기 위해 *모델 추가 프로토콜* 을 구현 하는 방법에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="9e12a-113">장치 지원</span><span class="sxs-lookup"><span data-stu-id="9e12a-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9e12a-114"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="9e12a-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="9e12a-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9e12a-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9e12a-116"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="9e12a-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9e12a-117">모델 프로토콜 추가</span><span class="sxs-lookup"><span data-stu-id="9e12a-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="9e12a-118">✔️</span><span class="sxs-lookup"><span data-stu-id="9e12a-118">✔️</span></span></td>
        <td><span data-ttu-id="9e12a-119">✔️</span><span class="sxs-lookup"><span data-stu-id="9e12a-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="9e12a-120">개요</span><span class="sxs-lookup"><span data-stu-id="9e12a-120">Overview</span></span>

<span data-ttu-id="9e12a-121">Windows Mixed Reality 홈에서 3D 모델 배치를 사용 하도록 설정 하는 두 가지 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="9e12a-122">[3d 모델이 Windows Mixed Reality 홈과 호환 되는지 확인](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="9e12a-123">응용 프로그램 또는 웹 페이지에서 *모델 추가 프로토콜* 을 구현 합니다 (이 문서).</span><span class="sxs-lookup"><span data-stu-id="9e12a-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="9e12a-124">*모델 추가 프로토콜* 구현</span><span class="sxs-lookup"><span data-stu-id="9e12a-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="9e12a-125">[호환 되는 3d 모델이](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)있으면 웹 페이지나 응용 프로그램에서 다음 URI를 활성화 하 여 *모델 추가 프로토콜* 을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="9e12a-126">URI가 원격 리소스를 가리키는 경우 자동으로 다운로드 되 고 홈에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="9e12a-127">로컬 리소스는 홈에 배치 되기 전에 혼합 현실 홈의 앱 데이터 폴더에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="9e12a-128">사용자가 단추를 숨기 거 나 가능 하면 사용 하지 않도록 설정 하 여이 기능을 지원 하지 않는 이전 버전의 Windows를 실행 중일 수 있는 시나리오를 고려 하 여 환경을 설계 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="9e12a-129">유니버설 Windows 플랫폼 앱에서 *모델 추가 프로토콜* 호출:</span><span class="sxs-lookup"><span data-stu-id="9e12a-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="9e12a-130">웹 페이지에서 *모델 추가 프로토콜* 호출:</span><span class="sxs-lookup"><span data-stu-id="9e12a-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="9e12a-131">모던 (VR) 헤드셋 고려 사항</span><span class="sxs-lookup"><span data-stu-id="9e12a-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="9e12a-132">모던 (VR) 헤드셋의 경우 혼합 현실 포털은 *모델 추가 프로토콜*을 호출 하기 전에 실행 되 고 있지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="9e12a-133">이 경우 *모델 추가 프로토콜이* 혼합 현실 포털을 시작 하 고 혼합 현실 홈에서 도착 한 후 헤드셋에서 볼 수 있는 위치에 개체를 직접 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="9e12a-134">혼합 현실 포털이 이미 실행 되 고 있는 바탕 화면에서 *모델 추가 프로토콜* 을 호출 하는 경우 헤드셋이 "활성" 상태 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="9e12a-135">그렇지 않으면 배치가 성공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e12a-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="9e12a-136">참조</span><span class="sxs-lookup"><span data-stu-id="9e12a-136">See also</span></span>

* [<span data-ttu-id="9e12a-137">Windows Mixed Reality 홈에서 사용할 3D 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="9e12a-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="9e12a-138">Windows Mixed Reality 홈 탐색</span><span class="sxs-lookup"><span data-stu-id="9e12a-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
