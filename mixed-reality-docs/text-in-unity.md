---
title: Unity의 텍스트
description: Unity에 텍스트를 표시 하기 위해 사용할 수 있는 텍스트 구성 요소에는 UI 텍스트와 3D 텍스트 메시의 두 가지 유형이 있습니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 컨트롤, 글꼴, 입력 체계, ui, ux
ms.openlocfilehash: 739dee36ffcbaa92fad705d1b0e58506801c9a4d
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701907"
---
# <a name="text-in-unity"></a><span data-ttu-id="237ce-104">Unity의 텍스트</span><span class="sxs-lookup"><span data-stu-id="237ce-104">Text in Unity</span></span>

<span data-ttu-id="237ce-105">텍스트는 holographic apps에서 가장 중요 한 구성 요소 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="237ce-106">Unity에 텍스트를 표시 하기 위해 사용할 수 있는 텍스트 구성 요소에는 UI 텍스트, 3D 텍스트 메시 및 텍스트 메시 Pro의 세 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="237ce-107">기본적으로 UI 텍스트와 3D 텍스트 메시는 흐리게 표시 되 고 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-107">By default UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="237ce-108">HoloLens에서 크기를 관리할 수 있는 선명한 고품질 텍스트를 얻으려면 몇 가지 변수를 조정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="237ce-109">UI 텍스트 및 3D 텍스트 메시 구성 요소를 사용할 때 크기 조정 요소를 적용 하 여 적절 한 차원을 얻으려면 렌더링 품질을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="237ce-110">![선명 하 고 멋진 텍스트를 얻는 방법](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="237ce-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="237ce-111">*Unity의 흐린 기본 텍스트*</span><span class="sxs-lookup"><span data-stu-id="237ce-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a><span data-ttu-id="237ce-112">Unity의 3D 텍스트 (텍스트 메시) 및 UI 텍스트 작업</span><span class="sxs-lookup"><span data-stu-id="237ce-112">Working with Unity's 3D Text (Text Mesh) and UI Text</span></span>

<span data-ttu-id="237ce-113">Unity는 장면에 추가 된 모든 새 요소를 1 개의 Unity 단위 또는 100% 변형 배율로 가정 합니다 .이 크기는 HoloLens에서 약 1 미터로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="237ce-114">글꼴의 경우 3D TextMesh의 경계 상자는 기본적으로 높이의 약 1 미터에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="237ce-115">![Unity에서 글꼴 작업](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="237ce-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="237ce-116">*기본 Unity 3D 텍스트 (텍스트 메시)는 1 측정기 인 1 개의 Unity 단위를 차지 합니다.*</span><span class="sxs-lookup"><span data-stu-id="237ce-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="237ce-117">대부분의 비주얼 디자이너는 요소를 사용 하 여 실제 세계의 글꼴 크기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="237ce-118">1 미터에 약 2835 (2, 834.645666399962) 점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="237ce-119">1 미터에 대 한 시점 시스템 변환과 Unity의 기본 텍스트 메시 글꼴 크기 13을 기반으로 하는 간단한 수학 2835 13은 0.0046 (0.004586111116)와 동일 하 게 시작할 수 있는 좋은 표준 배율을 제공 합니다 (일부는 0.005로 반올림).</span><span class="sxs-lookup"><span data-stu-id="237ce-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="237ce-120">텍스트 개체 또는 컨테이너를 이러한 값으로 크기를 조정 하면 디자인 프로그램에서 글꼴 크기를 1:1으로 변환할 수 있을 뿐만 아니라 사용자 환경 전체에서 일관성을 유지할 수 있도록 표준도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="237ce-121">![다른 글꼴 크기를 사용 하는 Unity 3D 텍스트 메시](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="237ce-121">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="237ce-122">*Unity 3D 텍스트 및 UI 텍스트에 대 한 값 크기 조정*</span><span class="sxs-lookup"><span data-stu-id="237ce-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<br>

<span data-ttu-id="237ce-123">![다른 글꼴 크기를 사용 하는 Unity 3D 텍스트 메시](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="237ce-123">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="237ce-124">*최적화 된 값이 있는 Unity 3D 텍스트 메시*</span><span class="sxs-lookup"><span data-stu-id="237ce-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="237ce-125">장면에 UI 또는 canvas 기반 텍스트 요소를 추가 하는 경우 차이가 크기는 더 커집니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="237ce-126">두 크기의 차이점은 약 1000% 이며,이는 UI 기반 텍스트 구성 요소에 대 한 배율 인수를 0.00046 (정확 하 게 0.0004586111116) 또는 0.0005 (반올림 된 값)로 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="237ce-127">![단위 값 마다 다른 동적 픽셀이 있는 Unity UI 텍스트](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="237ce-127">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="237ce-128">*최적화 된 값이 있는 Unity UI 텍스트*</span><span class="sxs-lookup"><span data-stu-id="237ce-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="237ce-129">글꼴의 기본값은 해당 글꼴의 질감 크기 또는 해당 글꼴을 Unity로 가져온 방법의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="237ce-130">이러한 테스트는 Unity의 기본 Arial 글꼴 및 가져온 다른 글꼴을 기반으로 수행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="237ce-131">텍스트 메시 Pro 작업</span><span class="sxs-lookup"><span data-stu-id="237ce-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="237ce-132">Unity의 텍스트 메시 Pro를 사용 하 여 텍스트 렌더링 품질을 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="237ce-133">이는 [사인 된 거리 필드 (.sdf)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 기법을 사용 하는 거리에 관계 없이 선명한 텍스트 윤곽선을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-133">It supports crisp text outlines regardless of the distance using the [Signed Distance Field (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="237ce-134">3D 텍스트 메시 및 UI 텍스트에 대해 위에서 사용한 것과 동일한 계산 방법을 사용 하 여 기존 입력 점에 사용할 적절 한 크기 조정 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find the proper scaling values to use with conventional typographic points.</span></span> <span data-ttu-id="237ce-135">크기가 36 인 기본 3D 텍스트 메시 Pro 글꼴의 경계 크기는 2.5 Unity 단위 (2.5 m) 이므로 크기 조정 값 0.005을 사용 하 여 포인트 크기를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-135">Since the default 3D Text Mesh Pro font with the size of 36 has a bounding size of 2.5 Unity units (2.5m), we can use scaling value 0.005 to get the point size.</span></span> <span data-ttu-id="237ce-136">UI 메뉴 아래의 텍스트 메시 Pro는 기본 경계 크기인 25 개 Unity 단위 (25m)를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-136">The Text Mesh Pro under the UI menu has the default bounding size of 25 Unity units (25m).</span></span> <span data-ttu-id="237ce-137">크기 조정 값에 대해 0.0005을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="237ce-138">![다른 글꼴 크기를 사용 하는 Unity 3D 텍스트 메시](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="237ce-138">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="237ce-139">*Unity 3D 텍스트 및 UI 텍스트에 대 한 값 크기 조정*</span><span class="sxs-lookup"><span data-stu-id="237ce-139">*Scaling values for the Unity 3D Text and UI Text*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="237ce-140">권장 텍스트 크기</span><span class="sxs-lookup"><span data-stu-id="237ce-140">Recommended text size</span></span>
<span data-ttu-id="237ce-141">짐작할 수 있듯이, PC 또는 태블릿 장치에서 사용 하는 형식 크기 (일반적으로 12 – 32pt 사이)는 2 미터 거리에서 매우 작게 보입니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="237ce-142">각 글꼴의 특성에 따라 달라 지지만 일반적으로 권장 되는 최소 보기 각도와 가독성을 위한 글꼴 높이는 사용자 연구 연구를 기반으로 하는 0.35 °-0.4 °/12.21-13.97mm을 중심으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="237ce-143">위에서 소개한 배율 인수를 사용 하는 약 35-40pt입니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-143">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="237ce-144">0\.45 m (45cm)에서 거의 상호 작용 하는 경우 읽을 수 있는 최소 글꼴의 보기 각도와 높이는 0.4 °-0.5 °/3.14 – 3.9 mm입니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-144">For the near interaction at 0.45m (45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="237ce-145">위에서 소개한 크기 조정 인수를 사용 하 여 약 9-12pt입니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="237ce-146">![*근거리 및 원거리 상호 작용 범위 콘텐츠 (근거리 및 원거리* 상호 작용 범위)](images/typography-distance-1000px.jpg)
</span><span class="sxs-lookup"><span data-stu-id="237ce-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="237ce-147">읽을 때 최소 글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="237ce-147">The minimum legible font size</span></span>
| <span data-ttu-id="237ce-148">거리</span><span class="sxs-lookup"><span data-stu-id="237ce-148">Distance</span></span> | <span data-ttu-id="237ce-149">시야각</span><span class="sxs-lookup"><span data-stu-id="237ce-149">Viewing angle</span></span> | <span data-ttu-id="237ce-150">텍스트 높이</span><span class="sxs-lookup"><span data-stu-id="237ce-150">Text height</span></span> | <span data-ttu-id="237ce-151">글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="237ce-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="237ce-152">45cm (직접 조작 거리)</span><span class="sxs-lookup"><span data-stu-id="237ce-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="237ce-153">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="237ce-153">0.4°-0.5°</span></span> | <span data-ttu-id="237ce-154">3.14 – 3.9 mm</span><span class="sxs-lookup"><span data-stu-id="237ce-154">3.14–3.9mm</span></span> | <span data-ttu-id="237ce-155">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="237ce-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="237ce-156">2m</span><span class="sxs-lookup"><span data-stu-id="237ce-156">2m</span></span> | <span data-ttu-id="237ce-157">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="237ce-157">0.35°-0.4°</span></span> | <span data-ttu-id="237ce-158">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="237ce-158">12.21–13.97mm</span></span> | <span data-ttu-id="237ce-159">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="237ce-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="237ce-160">편안 하 게 읽을 때의 글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="237ce-160">The comfortably legible font size</span></span>
| <span data-ttu-id="237ce-161">거리</span><span class="sxs-lookup"><span data-stu-id="237ce-161">Distance</span></span> | <span data-ttu-id="237ce-162">시야각</span><span class="sxs-lookup"><span data-stu-id="237ce-162">Viewing angle</span></span> | <span data-ttu-id="237ce-163">텍스트 높이</span><span class="sxs-lookup"><span data-stu-id="237ce-163">Text height</span></span> | <span data-ttu-id="237ce-164">글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="237ce-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="237ce-165">45cm (직접 조작 거리)</span><span class="sxs-lookup"><span data-stu-id="237ce-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="237ce-166">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="237ce-166">0.65°-0.8°</span></span> | <span data-ttu-id="237ce-167">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="237ce-167">5.1-6.3mm</span></span> | <span data-ttu-id="237ce-168">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="237ce-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="237ce-169">2m</span><span class="sxs-lookup"><span data-stu-id="237ce-169">2m</span></span> | <span data-ttu-id="237ce-170">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="237ce-170">0.6°-0.75°</span></span> | <span data-ttu-id="237ce-171">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="237ce-171">20.9-26.2mm</span></span> | <span data-ttu-id="237ce-172">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="237ce-172">59.4-74.2pt</span></span> |

<span data-ttu-id="237ce-173">맑은 고딕 (Windows의 기본 글꼴)은 대부분의 경우 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="237ce-174">그러나 밝은 수직선을 진동 하 고 가독성을 저하 시킬 수 있으므로 작은 크기로 밝은 색 또는 반투명 글꼴 패밀리를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="237ce-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="237ce-175">스트로크 두께가 충분 한 최신 글꼴이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="237ce-176">예를 들어 Helvetica 및 Arial은 멋진 하 고 일반 또는 굵게 가중치를 사용 하 여 HoloLens에서 매우 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>


<span data-ttu-id="237ce-177">![각도](images/Text_In_Unity_ViewingAngle.jpg)
보기*거리, 각도 및 텍스트 높이* 보기</span><span class="sxs-lookup"><span data-stu-id="237ce-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="237ce-178">적절 한 차원의 선명한 텍스트 렌더링 품질</span><span class="sxs-lookup"><span data-stu-id="237ce-178">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="237ce-179">이러한 크기 조정 요소에 따라 [UI 텍스트 및 3D 텍스트 메시를 사용 하 여 텍스트 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-179">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="237ce-180">개발자는 이러한 prefabs를 사용 하 여 선명한 텍스트와 일관 된 글꼴 크기를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-180">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="237ce-181">![적절 한 차원의 선명한 텍스트 렌더링 품질](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="237ce-181">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="237ce-182">*적절 한 차원의 선명한 텍스트 렌더링 품질*</span><span class="sxs-lookup"><span data-stu-id="237ce-182">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="237ce-183">폐색가 지원 되는 셰이더</span><span class="sxs-lookup"><span data-stu-id="237ce-183">Shader with occlusion support</span></span>

<span data-ttu-id="237ce-184">Unity의 기본 글꼴 재질은 폐색를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-184">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="237ce-185">이로 인해 기본적으로 개체 뒤에 텍스트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-185">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="237ce-186">[폐색를 지 원하는 간단한 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)를 포함 했습니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-186">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="237ce-187">아래 이미지는 기본 글꼴 재질 (왼쪽) 및 적절 한 폐색 (오른쪽) 텍스트가 포함 된 텍스트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="237ce-187">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="237ce-188">![폐색가 지원 되는 셰이더](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="237ce-188">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="237ce-189">*폐색가 지원 되는 셰이더*</span><span class="sxs-lookup"><span data-stu-id="237ce-189">*Shader with occlusion support*</span></span>


## <a name="see-also"></a><span data-ttu-id="237ce-190">참조</span><span class="sxs-lookup"><span data-stu-id="237ce-190">See also</span></span>
* [<span data-ttu-id="237ce-191">MRTK의 텍스트 Prefab</span><span class="sxs-lookup"><span data-stu-id="237ce-191">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="237ce-192">입력 체계</span><span class="sxs-lookup"><span data-stu-id="237ce-192">Typography</span></span>](typography.md)

 
