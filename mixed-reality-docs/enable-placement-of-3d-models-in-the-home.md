---
title: 집에서 3D 모델의 배치를 사용 하도록 설정
description: Windows Mixed Reality 홈에 웹 사이트 또는 응용 프로그램에서 3D 모델을 배치 하는 방법
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, 모델, 홈에서 위치, 위치, 세계, 모델링, 혼합된 현실 홈, 웹, 앱
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605022"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="d64fc-104">홈 혼합된 현실에서 3D 모델의 배치를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="d64fc-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="d64fc-105">일부로 추가 된이 기능을 [Windows 10 2018 년 4 월 업데이트](release-notes-april-2018.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="d64fc-106">이전 버전 Windows의이 기능을 사용 하 여 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="d64fc-107">합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 출발점 응용 프로그램을 시작 하기 전에 사용자가 이동 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="d64fc-108">일부 시나리오에서는 2D 앱 (예: 홀로그램 앱) 장식을 또는 전체 3d에서 추가로 조사에 대 한 3D 모델 혼합된 현실 홈에 직접 배치할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="d64fc-109">합니다 *모델 프로토콜을 추가* 계속 유지 되며 여기서 같은 웹 사이트 또는 집 Windows Mixed Reality로 직접 응용 프로그램에서 3D 모델을 보낼 수 있습니다 [3D 앱 시작 관리자](3d-app-launcher-design-guidance.md), 2D 앱 및 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="d64fc-110">예를 들어, 응용 프로그램 카탈로그의 공간을 디자인 하기 위한 3D 가구를 표시 하는 개발 하는 경우 사용할 수는 *모델 프로토콜 추가* 카탈로그에서 해당 가구 3D 모델에 적용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="d64fc-111">사용자가 이동, 전 세계에 배치 되 면 크기 조정 및 집에서 다른 홀로그램 마찬가지로 이러한 3D 모델을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="d64fc-112">이 문서에서는 구현 하는 개요를 제공 합니다 *모델 프로토콜을 추가* 앱 또는 웹에서 3D 개체를 사용 하 여 세계를 데코 레이트 할 수 있도록 시작할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="d64fc-113">장치 지원</span><span class="sxs-lookup"><span data-stu-id="d64fc-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d64fc-114">기능</span><span class="sxs-lookup"><span data-stu-id="d64fc-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="d64fc-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d64fc-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d64fc-116"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="d64fc-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d64fc-117">모델 프로토콜 추가</span><span class="sxs-lookup"><span data-stu-id="d64fc-117">Add model protocol</span></span></td><td style="text-align: center;"> <span data-ttu-id="d64fc-118">✔️</span><span class="sxs-lookup"><span data-stu-id="d64fc-118">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d64fc-119">✔️</span><span class="sxs-lookup"><span data-stu-id="d64fc-119">✔️</span></span></td>
</tr>
</table>

## <a name="overview"></a><span data-ttu-id="d64fc-120">개요</span><span class="sxs-lookup"><span data-stu-id="d64fc-120">Overview</span></span>

<span data-ttu-id="d64fc-121">Windows Mixed Reality 홈에서 3D 모델의 배치를 사용 하도록 설정 하는 방법은 2 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="d64fc-122">[3D 모델 홈 Windows Mixed Reality와 호환 되는지 확인](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="d64fc-123">구현 된 *모델 프로토콜 추가* 응용 프로그램 또는 웹 페이지 (이 문서)에서.</span><span class="sxs-lookup"><span data-stu-id="d64fc-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="d64fc-124">구현 된 *모델 프로토콜 추가*</span><span class="sxs-lookup"><span data-stu-id="d64fc-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="d64fc-125">했으면를 [호환 3D 모델](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)를 구현할 수 있습니다 합니다 *모델 프로토콜을 추가* 웹 페이지 또는 응용 프로그램에서 다음 URI를 활성화 하 여:</span><span class="sxs-lookup"><span data-stu-id="d64fc-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="d64fc-126">URI 원격 리소스를 가리키는 경우 다음이 자동으로 다운로드 되 고 홈에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="d64fc-127">집에서 추가 되기 전에 로컬 리소스의 혼합된 현실 홈 앱 데이터 폴더에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="d64fc-128">사용자 수 실행 될 있는 이전 버전의 Windows 단추를 숨기 거 나 가능 하면 사용 하 여이 기능을 지원 하지 않는 시나리오에 대 한 계정에 환경을 디자인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="d64fc-129">호출 된 *모델 프로토콜 추가* 유니버설 Windows 플랫폼 앱에서:</span><span class="sxs-lookup"><span data-stu-id="d64fc-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="d64fc-130">호출 된 *모델 프로토콜 추가* 웹 페이지에서:</span><span class="sxs-lookup"><span data-stu-id="d64fc-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="d64fc-131">몰입 형 (VR) 헤드셋에 대 한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="d64fc-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="d64fc-132">몰입 형 (VR) 헤드셋, 혼합 현실 포털 없는 호출 하기 전에 실행 중 이어야 합니다 *모델 프로토콜 추가*합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="d64fc-133">이 경우에 *모델 프로토콜 추가* 혼합 현실 포털을 시작 하 고 개체 직접 여기서 헤드셋은 홈 혼합된 현실에서 열리면 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="d64fc-134">호출할 때 합니다 *모델 프로토콜 추가* 이미 실행 하는 혼합 현실 포털을 사용 하 여 데스크톱에서 헤드셋 "절전 모드 해제" 인지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="d64fc-135">그렇지 않은 경우 배치에 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d64fc-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="d64fc-136">참조</span><span class="sxs-lookup"><span data-stu-id="d64fc-136">See also</span></span>

* [<span data-ttu-id="d64fc-137">Windows Mixed Reality 집에서 사용할 3D 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="d64fc-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="d64fc-138">Windows Mixed Reality 홈 탐색</span><span class="sxs-lookup"><span data-stu-id="d64fc-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
