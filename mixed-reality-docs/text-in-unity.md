---
title: Unity에서 텍스트
description: Unity에서 텍스트를 표시 하는 두 가지 유형의 텍스트 구성 요소를 사용할 수 있습니다-UI 텍스트 및 텍스트를 3D 메시입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 컨트롤, ux, ui, 입력 체계, 글꼴
ms.openlocfilehash: 7d40db2e0571e835e28e444c7921e1a086800936
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829969"
---
# <a name="text-in-unity"></a><span data-ttu-id="a44ed-104">Unity에서 텍스트</span><span class="sxs-lookup"><span data-stu-id="a44ed-104">Text in Unity</span></span>

<span data-ttu-id="a44ed-105">텍스트 holographic 앱의 가장 중요 한 구성 요소 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="a44ed-106">Unity에서 텍스트를 표시 하는 세 가지 유형의 텍스트 구성 요소를 사용할 수 있습니다-UI 텍스트, 텍스트 3D 메시 및 텍스트 메시 Pro입니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="a44ed-107">기본적으로 UI 텍스트 및 텍스트를 3D 메시 흐리게 표시 되며 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-107">By default UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="a44ed-108">선명 하 고 고품질 텍스트 HoloLens에 크기를 관리할 수 있는 몇 가지 변수를 조정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="a44ed-109">UI 텍스트 및 3D 메시 텍스트 구성 요소를 사용 하는 경우 적절 한 크기를 가져오려면 배율 인수를 적용 하 여 더 나은 렌더링 품질을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="a44ed-110">![선명 하 게 하 고 뛰어난 텍스트를 가져오는 방법](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="a44ed-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="a44ed-111">*Unity에서 흐리게 표시 기본 텍스트*</span><span class="sxs-lookup"><span data-stu-id="a44ed-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a><span data-ttu-id="a44ed-112">Unity의 3D 텍스트 (텍스트 메시) 및 UI 텍스트 작업</span><span class="sxs-lookup"><span data-stu-id="a44ed-112">Working with Unity's 3D Text(Text Mesh) and UI Text</span></span>

<span data-ttu-id="a44ed-113">Unity 장면에 추가 된 모든 새 요소 1 Unity 단위로 크기 또는 1m HoloLens에 100% 변환 확장으로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="a44ed-114">글꼴의 경우 3D TextMesh 경계 상자 높이 대 한 1 미터에는 기본적으로 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="a44ed-115">![Unity의 글꼴 사용](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="a44ed-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="a44ed-116">*기본 Unity 3D 텍스트 (텍스트 메시) 차지 1 미터는 Unity 단위 1 개*</span><span class="sxs-lookup"><span data-stu-id="a44ed-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="a44ed-117">대부분의 비주얼 디자이너 점을 사용 하 여 실제 환경에서 글꼴 크기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="a44ed-118">약 2835 (2,834.645666399962)는 1 미터에는 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="a44ed-119">13 2835 equals 0.0046 (정확 하 게 0.004586111116)로 나눈 값의 간단한 수학 지점 시스템 변환할 1m 및 13 Unity의 기본 텍스트 메시 글꼴 크기에 따라 적절 한 표준 확장을 시작 하려면 제공 (일부 할 0.005로 반올림)입니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="a44ed-120">텍스트 개체 또는 이러한 값에는 컨테이너를 크기 조정을 허용 하지 않습니다만 글꼴 1:1 변환 디자인 프로그램에서 크기를 지정 하지만 사용자 환경 전체에서 일관성을 유지할 수 있도록 표준 제공.</span><span class="sxs-lookup"><span data-stu-id="a44ed-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="a44ed-121">![Unity 3D 텍스트 메시 다른 글꼴 크기를 사용 하 여](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="a44ed-121">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="a44ed-122">*Unity 3D 텍스트 및 UI 텍스트에 대 한 크기 조정 값*</span><span class="sxs-lookup"><span data-stu-id="a44ed-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<span data-ttu-id="a44ed-123">![Unity 3D 텍스트 메시 다른 글꼴 크기를 사용 하 여](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="a44ed-123">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="a44ed-124">*Unity 3D 텍스트 메시 최적화 된 값을 사용 하 여*</span><span class="sxs-lookup"><span data-stu-id="a44ed-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="a44ed-125">장면에 UI 또는 캔버스 기반된 텍스트 요소를 추가할 때 크기과 차이로 인해가 여전히 큽니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="a44ed-126">두 가지 크기의 차이 약 1000 %0.00046 (정확 하 게 0.0004586111116)에 기반 하는 UI 텍스트 구성 요소에 대 한 배율 인수를 전달 해 또는 0.0005 반올림된 한 값에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="a44ed-127">![다른 동적 픽셀 단위 값 수를 사용 하 여 unity UI 텍스트](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="a44ed-127">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="a44ed-128">*최적화 된 값을 사용 하 여 unity UI 텍스트*</span><span class="sxs-lookup"><span data-stu-id="a44ed-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="a44ed-129">글꼴의 기본 값을 해당 글꼴 또는 글꼴 Unity로 가져온 방법의 질감 크기에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="a44ed-130">이러한 테스트는 가져온된 다른 글꼴을 하나 뿐 아니라 Unity에서 기본 Arial 글꼴에 따라 수행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="a44ed-131">텍스트를 사용 하 여 작업에는 Pro 메시</span><span class="sxs-lookup"><span data-stu-id="a44ed-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="a44ed-132">Unity의 텍스트 메시 Pro를 사용 하 여 텍스트 렌더링 품질을 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="a44ed-133">사용 하 여 거리에 관계 없이 선명한 텍스트 윤곽선을 지원 합니다 [SDF (서명 거리 필드)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 기법입니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-133">It supports crisp text outline regardless of the distance using the [SDF(Signed Distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="a44ed-134">에 사용 되는 위에 텍스트를 3D 메시 및 UI 텍스트 동일한 계산 방법을 사용 기존 인쇄 지점을 사용 하려면 적절 한 크기 조정 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find proper scaling values to use conventional typographic Point.</span></span> <span data-ttu-id="a44ed-135">36 크기를 사용 하 여 기본 3D 텍스트 메시 Pro 글꼴 2.5 Unity Unit(2.5m)의 경계를 보여주고, 있으므로 포인트 크기를 사용 하려면 크기 조정 값 0.005를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-135">Since the default 3D Text Mesh Pro font with the size 36 shows the bounding of 2.5 Unity Unit(2.5m), we can use scaling value 0.005 to use the Point size.</span></span> <span data-ttu-id="a44ed-136">기본 크기의 25 Unity Unit(25m) 경계는 텍스트 메시 Pro UI 메뉴 아래에</span><span class="sxs-lookup"><span data-stu-id="a44ed-136">The Text Mesh Pro under UI menu has the default bounding size of 25 Unity Unit(25m).</span></span> <span data-ttu-id="a44ed-137">제공이 0.0005 크기 조정 값에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="a44ed-138">![Unity 3D 텍스트 메시 다른 글꼴 크기를 사용 하 여](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="a44ed-138">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="a44ed-139">*Unity 3D 텍스트 및 UI 텍스트에 대 한 크기 조정 값*</span><span class="sxs-lookup"><span data-stu-id="a44ed-139">*Scaling values for the Unity 3D Text and UI Text*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="a44ed-140">권장 되는 텍스트 크기</span><span class="sxs-lookup"><span data-stu-id="a44ed-140">Recommended text size</span></span>
<span data-ttu-id="a44ed-141">예상할 수 있듯이 PC 또는 태블릿 장치 (일반적으로 12 – 32pt) 사이 사용 하는 형식 크기 2 미터 거리 만큼 떨어진 좁습니다 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="a44ed-142">각 글꼴의 특성에 다르지만 0.35°-0.4°/12.21-13.97mm 사용자 연구 조사의에 따라 권장 되는 보기 각도 및 읽기 쉽도록 코멘트가 글꼴 높이 최소는 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="a44ed-143">위에 소개 된 배율 인수를 사용 하 여 35 40pt는.</span><span class="sxs-lookup"><span data-stu-id="a44ed-143">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="a44ed-144">거의 상호 작용 0.45m(45cm)에 최소 읽을 수 글꼴 각도 높이 0.4 °-0.5 ° / 3.14 – 3.9 mm 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-144">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="a44ed-145">위에 소개 된 배율 인수를 사용 하 여 9 12pt는.</span><span class="sxs-lookup"><span data-stu-id="a44ed-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="a44ed-146">![가까운과 먼 상호 작용 범위](images/typography-distance-1000px.jpg)
*근처에서 콘텐츠와 먼 상호 작용 범위*</span><span class="sxs-lookup"><span data-stu-id="a44ed-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="a44ed-147">읽을 수 있는 최소 글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="a44ed-147">The minimum legible font size</span></span>
| <span data-ttu-id="a44ed-148">거리</span><span class="sxs-lookup"><span data-stu-id="a44ed-148">Distance</span></span> | <span data-ttu-id="a44ed-149">각도</span><span class="sxs-lookup"><span data-stu-id="a44ed-149">Viewing angle</span></span> | <span data-ttu-id="a44ed-150">텍스트 높이</span><span class="sxs-lookup"><span data-stu-id="a44ed-150">Text height</span></span> | <span data-ttu-id="a44ed-151">글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="a44ed-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="a44ed-152">45 cm (직접 조작 거리)</span><span class="sxs-lookup"><span data-stu-id="a44ed-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="a44ed-153">0.4°-0.5°</span><span class="sxs-lookup"><span data-stu-id="a44ed-153">0.4°-0.5°</span></span> | <span data-ttu-id="a44ed-154">3.14–3.9mm</span><span class="sxs-lookup"><span data-stu-id="a44ed-154">3.14–3.9mm</span></span> | <span data-ttu-id="a44ed-155">8.9–11.13pt</span><span class="sxs-lookup"><span data-stu-id="a44ed-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="a44ed-156">2m</span><span class="sxs-lookup"><span data-stu-id="a44ed-156">2m</span></span> | <span data-ttu-id="a44ed-157">0.35°-0.4°</span><span class="sxs-lookup"><span data-stu-id="a44ed-157">0.35°-0.4°</span></span> | <span data-ttu-id="a44ed-158">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="a44ed-158">12.21–13.97mm</span></span> | <span data-ttu-id="a44ed-159">34.63-39.58pt</span><span class="sxs-lookup"><span data-stu-id="a44ed-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="a44ed-160">편안 하 게 읽을 수 글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="a44ed-160">The comfortably legible font size</span></span>
| <span data-ttu-id="a44ed-161">거리</span><span class="sxs-lookup"><span data-stu-id="a44ed-161">Distance</span></span> | <span data-ttu-id="a44ed-162">각도</span><span class="sxs-lookup"><span data-stu-id="a44ed-162">Viewing angle</span></span> | <span data-ttu-id="a44ed-163">텍스트 높이</span><span class="sxs-lookup"><span data-stu-id="a44ed-163">Text height</span></span> | <span data-ttu-id="a44ed-164">글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="a44ed-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="a44ed-165">45 cm (직접 조작 거리)</span><span class="sxs-lookup"><span data-stu-id="a44ed-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="a44ed-166">0.65°-0.8°</span><span class="sxs-lookup"><span data-stu-id="a44ed-166">0.65°-0.8°</span></span> | <span data-ttu-id="a44ed-167">5.1-6.3mm</span><span class="sxs-lookup"><span data-stu-id="a44ed-167">5.1-6.3mm</span></span> | <span data-ttu-id="a44ed-168">14.47-17.8pt</span><span class="sxs-lookup"><span data-stu-id="a44ed-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="a44ed-169">2m</span><span class="sxs-lookup"><span data-stu-id="a44ed-169">2m</span></span> | <span data-ttu-id="a44ed-170">0.6°-0.75°</span><span class="sxs-lookup"><span data-stu-id="a44ed-170">0.6°-0.75°</span></span> | <span data-ttu-id="a44ed-171">20.9-26.2mm</span><span class="sxs-lookup"><span data-stu-id="a44ed-171">20.9-26.2mm</span></span> | <span data-ttu-id="a44ed-172">59.4-74.2pt</span><span class="sxs-lookup"><span data-stu-id="a44ed-172">59.4-74.2pt</span></span> |

<span data-ttu-id="a44ed-173">Segoe UI (Windows에 대 한 기본 글꼴) 대부분의 경우 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="a44ed-174">그러나 씬 세로 스트로크는 진동 이므로 가독성을 저하 시킵니다 작은 크기로 light 또는 semi 밝은 글꼴 패밀리를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="a44ed-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="a44ed-175">충분 한 스트로크 두께 사용 하 여 최신 글꼴 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="a44ed-176">예를 들어, Helvetica Arial 멋진 확인 및 일반 또는 굵게 표시 된 가중치를 사용 하 여 HoloLens에 매우 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>


<span data-ttu-id="a44ed-177">![시야각](images/Text_In_Unity_ViewingAngle.jpg)
*거리, 각도 및 텍스트 높이 보기*</span><span class="sxs-lookup"><span data-stu-id="a44ed-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="a44ed-178">적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한</span><span class="sxs-lookup"><span data-stu-id="a44ed-178">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="a44ed-179">이 배율은 따라 만들었습니다 [UI 텍스트 및 텍스트를 3D 메시를 사용 하 여 텍스트 prefabs](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-179">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="a44ed-180">개발자는 정확한 텍스트와 일관 된 글꼴 크기를 가져오려면 이러한 prefabs를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-180">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="a44ed-181">![적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="a44ed-181">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="a44ed-182">*적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한*</span><span class="sxs-lookup"><span data-stu-id="a44ed-182">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="a44ed-183">폐색 지원과 셰이더</span><span class="sxs-lookup"><span data-stu-id="a44ed-183">Shader with occlusion support</span></span>

<span data-ttu-id="a44ed-184">Unity의 기본 글꼴 재질 폐색을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-184">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="a44ed-185">이 때문에 기본적으로 텍스트 개체 뒤에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-185">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="a44ed-186">간단한 포함 되어 있습니다 [셰이더를 폐색 지](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-186">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="a44ed-187">아래 이미지는 기본 글꼴 재질 (왼쪽)를 사용 하 여 텍스트 및 적절 한 폐색 (오른쪽)를 사용 하 여 텍스트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a44ed-187">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="a44ed-188">![폐색 지원과 셰이더](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="a44ed-188">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="a44ed-189">*폐색 지원과 셰이더*</span><span class="sxs-lookup"><span data-stu-id="a44ed-189">*Shader with occlusion support*</span></span>


## <a name="see-also"></a><span data-ttu-id="a44ed-190">참조</span><span class="sxs-lookup"><span data-stu-id="a44ed-190">See also</span></span>
* [<span data-ttu-id="a44ed-191">텍스트 Prefab은 MRTK에서</span><span class="sxs-lookup"><span data-stu-id="a44ed-191">Text Prefab in the MRTK</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="a44ed-192">입력 체계</span><span class="sxs-lookup"><span data-stu-id="a44ed-192">Typography</span></span>](typography.md)

 
