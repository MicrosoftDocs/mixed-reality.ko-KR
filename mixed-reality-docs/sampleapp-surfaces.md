---
title: 화면
description: 표면은 Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱입니다. 시각적 개체, 오디오 및 완전히 구분 되는 tactile 하루아침를 만드는 방법을 살펴봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, mrtk, 디자인, 샘플 앱, 컨트롤
ms.openlocfilehash: fb6948ceda2a059323d23d72d6d3245a3a9896ee
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240464"
---
# <a name="surfaces"></a><span data-ttu-id="aef17-105">화면</span><span class="sxs-lookup"><span data-stu-id="aef17-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="aef17-106">이 문서에서는 혼합 현실 앱 개발에 대 한 학습 정보 및 제안을 공유 하는 위치를 [혼합 현실 디자인 랩에서](https://github.com/Microsoft/MRDesignLabs_Unity)만든 예비 샘플에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="aef17-107">디자인 관련 문서와 코드는 새로운 검색을 수행할 때 개선 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="aef17-108">[표면은](https://github.com/microsoft/MRDL_Unity_Surfaces) Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="aef17-109">시각적 개체, 오디오 및 완전히 구분 되는 tactile 하루아침를 만드는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![화면](images/MRDL_Surfaces_1.jpg)

## <a name="about-the-app"></a><span data-ttu-id="aef17-111">앱 정보</span><span class="sxs-lookup"><span data-stu-id="aef17-111">About the app</span></span>
<span data-ttu-id="aef17-112">표면은 MRTK (Mixed Reality Toolkit)의 입력 시스템 및 구성 요소를 사용 하 여 HoloLens 2에 대 한 앱 환경을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-112">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="aef17-113">이 프로젝트에서는의 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-113">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="aef17-114">MRTK의 [입력 시스템](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), 특히 직접/조인트 추적을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-114">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="aef17-115">고성능 그래픽에는 MRTK의 [표준 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-115">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="aef17-116">이 프로젝트의 구성 요소를 사용 하 여 사용자 고유의 혼합 현실 앱 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-116">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="aef17-117">MR 개발 일 2020-MR 표면 앱에서 학습</span><span class="sxs-lookup"><span data-stu-id="aef17-117">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="aef17-118">MR 표면 앱에서 학습</span><span class="sxs-lookup"><span data-stu-id="aef17-118">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="aef17-119">Lars Simkins, MRDL surface 앱 뒤의 선임 디자이너는 앱의 디자인 스토리와 기술 주요 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef17-119">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="aef17-120">GitHub의 프로젝트 리포지토리</span><span class="sxs-lookup"><span data-stu-id="aef17-120">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="aef17-121">HoloLens 2의 Microsoft Store에서 앱 다운로드</span><span class="sxs-lookup"><span data-stu-id="aef17-121">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="aef17-122">(앱은 HoloLens 2 에서만 사용할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="aef17-122">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="aef17-123">저자 정보</span><span class="sxs-lookup"><span data-stu-id="aef17-123">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="aef17-124"><b>동 Yoon 공원</b></span><span class="sxs-lookup"><span data-stu-id="aef17-124"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="aef17-125">UX 디자이너@Microsoft</span><span class="sxs-lookup"><span data-stu-id="aef17-125">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="aef17-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aef17-126">See also</span></span>

* [<span data-ttu-id="aef17-127">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="aef17-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="aef17-128">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="aef17-128">Object collection</span></span>](object-collection.md)
