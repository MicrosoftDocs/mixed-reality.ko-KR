---
title: 공간 메시 시각화
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 혼합 현실, HoloLens, UI 컨트롤, 상호 작용, UI, ux, UX 디자인, 공간 UI, 공간 상호 작용, 3D UI, 3D UX
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346136"
---
# <a name="spatial-mesh"></a><span data-ttu-id="a6c86-103">공간 메시</span><span class="sxs-lookup"><span data-stu-id="a6c86-103">Spatial mesh</span></span>

![공간 메시](images/UX/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="a6c86-105">공간 메시 시각화를 통해 사용자는 장치가 물리적 환경을 인식 하 고 이해 하는 방법을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="a6c86-106">공간 컨텍스트를 제공 하는 것 외에도 적절 한 공간 메시 시각화를 통해 매력적인 및 마법 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="a6c86-107">디자인 지침</span><span class="sxs-lookup"><span data-stu-id="a6c86-107">Design guideline</span></span>
<span data-ttu-id="a6c86-108">사용자가 콘텐츠를 집중적으로 사용 하 고 상호 작용할 수 있도록 하는 것이 중요 하기 때문에 백그라운드에서 공간 메시를 지속적으로 반복적으로 시각화 하는 작업은 혼란을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="a6c86-109">초기 실행에서 한 번만 또는 사용자가 공간을 대상으로 하 여 환경 메시를 볼 수 있는 명확한 의도를 표시 하는 경우에만 환경을 시각화 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="a6c86-110">HoloLens 셸에서이 동작을 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a6c86-111">Unity 용 MRTK (Mixed Reality Toolkit)의 공간 메시 시각화</span><span class="sxs-lookup"><span data-stu-id="a6c86-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="a6c86-112">MRTK는 공간 메시 시각화에 대 한 여러 자료를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="a6c86-113">**MRTK_Wireframe, MRTK_Wireframe**: 기본 정적 공간 메시 재질: 애니메이션 없이 메시 윤곽선을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="a6c86-114">이 자료는 전체 공간 메시 기 하 도형을 표시 하기 때문에 디버깅 목적으로 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="a6c86-115">그러나 프로덕션 환경에서는 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="a6c86-116">**MRTK_SurfaceReconstruction.** 대만:이 자료는 공간 메시에 애니메이션 된 펄스 효과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-116">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="a6c86-117">이 자료를 사용 하 여 특정 경험 또는 사용자의 공중 탭 입력에서 환경을 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c86-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="a6c86-118">예제는 **PulseShaderExamples** 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6c86-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="a6c86-119">자세한 내용은 [Mrtk-공간 인식](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 및 [Mrtk-펄스 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6c86-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="a6c86-120">참조</span><span class="sxs-lookup"><span data-stu-id="a6c86-120">See also</span></span>

* [<span data-ttu-id="a6c86-121">커서</span><span class="sxs-lookup"><span data-stu-id="a6c86-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a6c86-122">손 광선</span><span class="sxs-lookup"><span data-stu-id="a6c86-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a6c86-123">Button</span><span class="sxs-lookup"><span data-stu-id="a6c86-123">Button</span></span>](button.md)
* [<span data-ttu-id="a6c86-124">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="a6c86-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a6c86-125">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="a6c86-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a6c86-126">조작</span><span class="sxs-lookup"><span data-stu-id="a6c86-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a6c86-127">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="a6c86-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a6c86-128">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="a6c86-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a6c86-129">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="a6c86-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a6c86-130">음성 명령</span><span class="sxs-lookup"><span data-stu-id="a6c86-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a6c86-131">키보드</span><span class="sxs-lookup"><span data-stu-id="a6c86-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a6c86-132">Tooltip</span><span class="sxs-lookup"><span data-stu-id="a6c86-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a6c86-133">슬레이트</span><span class="sxs-lookup"><span data-stu-id="a6c86-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="a6c86-134">슬라이더</span><span class="sxs-lookup"><span data-stu-id="a6c86-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="a6c86-135">셰이더</span><span class="sxs-lookup"><span data-stu-id="a6c86-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="a6c86-136">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="a6c86-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a6c86-137">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="a6c86-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a6c86-138">표면 자성</span><span class="sxs-lookup"><span data-stu-id="a6c86-138">Surface magnetism</span></span>](surface-magnetism.md)
