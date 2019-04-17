---
title: 사용자 지정 홈 환경 추가
description: 제공 하는 Windows Mixed Reality 홈 환경 외에도 만들고 고유한를 사용 하 여 실험할 수 있습니다.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 홈, 사용자 지정 환경, 위치, cliff 집, skyloft, 사용자 만들기
ms.openlocfilehash: ef140efd88aa0d3329ae2aa7e5b202c3bfe77c0a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597520"
---
# <a name="add-custom-home-environments"></a><span data-ttu-id="22d08-104">사용자 지정 홈 환경 추가</span><span class="sxs-lookup"><span data-stu-id="22d08-104">Add custom home environments</span></span>

>[!NOTE]
><span data-ttu-id="22d08-105">이 실험적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-105">This is an experimental feature.</span></span> <span data-ttu-id="22d08-106">체험해 보세요를 즐겁게 하며 모든 항목이 예상 대로 제대로 작동 하지 않더라도 놀라지 마세요.</span><span class="sxs-lookup"><span data-stu-id="22d08-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="22d08-107">이 기능과 되므로 사용에 대 한 관심의 실행 가능성을 평가 하는 것에 알려주세요 환경을 (및 발견 한 모든 버그)에 [개발자 포럼](https://forums.hololens.com/categories/custom-home-environments)합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="22d08-108">로 시작 합니다 [Windows 10 2018 년 4 월 업데이트](#release-notes-april-2018.md),으로 사용할 사용자 지정 환경 위치 선택 (시작 메뉴)를 추가할 수 있는 실험적인 기능을 활성화 했습니다는 [Windows Mixed Reality 홈](#navigating-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="22d08-108">Starting with the [Windows 10 April 2018 update](#release-notes-april-2018.md), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](#navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="22d08-109">Windows Mixed Reality Cliff 집 고 Skyloft 집으로 선택할 수 있는 두 가지 기본 환경에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, that you can choose as your home.</span></span> <span data-ttu-id="22d08-110">사용자 지정 환경 만들기를 사용 하면 사용자 고유의 만들기를 사용 하 여 해당 목록을 확장 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-110">Creating custom environments allows you to expand that list with your own creations.</span></span> <span data-ttu-id="22d08-111">진행 중인이 사용할 수 있는 초기 상태 평가 창작자, 개발자의 관심 분야의 종류를 만들고 다른 제작 도구를 사용 하 여 작동 방식을 이해를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22d08-111">We are making this available in an early state to evaluate interest from creators and developers, see what kinds of worlds you create, and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="22d08-112">해당 텔레포트 보면 사용자 지정 환경을 사용 하는 경우 앱과 상호 작용 하 고 홀로그램 배치 Skyloft 고 Cliff 집에서와 마찬가지로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-112">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="22d08-113">소설 환경에서 웹 사이트를 탐색 하거나 홀로그램 혁신적인 도시를 채울 수 있습니다-가능성은 무한!</span><span class="sxs-lookup"><span data-stu-id="22d08-113">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="22d08-114">장치 지원</span><span class="sxs-lookup"><span data-stu-id="22d08-114">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="22d08-115">기능</span><span class="sxs-lookup"><span data-stu-id="22d08-115">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="22d08-116"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="22d08-116"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="22d08-117"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="22d08-117"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="22d08-118">사용자 지정 홈 환경</span><span class="sxs-lookup"><span data-stu-id="22d08-118">Custom home environments</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="22d08-119">✔️</span><span class="sxs-lookup"><span data-stu-id="22d08-119">✔️</span></span></td>
</tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="22d08-120">샘플 환경을 시도</span><span class="sxs-lookup"><span data-stu-id="22d08-120">Trying a sample environment</span></span>

<span data-ttu-id="22d08-121">사용자 지정 홈 환경의 창조적 가능성 중 일부를 보여 주는 샘플 환경을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-121">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="22d08-122">작업을 수행 하려면 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-122">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="22d08-123">[예제 판타지 섬 환경 다운로드](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (링크가 자동 압축 풀기 실행 파일을 가리키는).</span><span class="sxs-lookup"><span data-stu-id="22d08-123">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="22d08-124">![소설을 섬 샘플 환경](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="22d08-124">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="22d08-125">*소설을 섬 샘플 환경*</span><span class="sxs-lookup"><span data-stu-id="22d08-125">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="22d08-126">실행 합니다 **Fantasy_Island.exe** 방금 다운로드 한 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-126">Run the **Fantasy_Island.exe** file you just downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="22d08-127">(다음과 같은)는 웹에서 다운로드.exe 파일을 실행 하려고 하면 "Windows PC를 보호 하는 데 사용" 팝업을 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-127">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="22d08-128">Fantasy_Island.exe이이 팝업에서를 실행 하려면 **자세한 내용은** 차례로 **실행**합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-128">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="22d08-129">이 보안 설정은 있으므로 신뢰 하지 않을 파일을 다운로드 하는 것을 방지 하기 것만이 옵션 선택 하십시오이 파일의 원본을 신뢰 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="22d08-129">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="22d08-130">오픈 **파일 탐색기** 주소 표시줄에 다음을 붙여 넣는 방법으로 환경 폴더로 이동 하 고: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-130">Open **File Explorer** and navigate to the environments folder by pasting the following in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="22d08-131">이 폴더에 다운로드 한 샘플 환경을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-131">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="22d08-132">다시 시작 **혼합 현실 포털**합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-132">Restart **Mixed Reality Portal**.</span></span> <span data-ttu-id="22d08-133">이 위치 선택에서 환경 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-133">This will refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="22d08-134">헤드셋에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-134">Put on your headset.</span></span> <span data-ttu-id="22d08-135">집에서 했으면 엽니다는 **시작 메뉴** 컨트롤러 단추는 Windows를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="22d08-136">선택 된 **자릿수** 홈 환경을 선택에 대 한 고정 된 앱 목록 위의 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="22d08-137">위치 목록에서 다운로드 한 판타지 섬 환경을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-137">You will find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="22d08-138">선택 **판타지 섬** 새 사용자 지정 홈 환경 입력!</span><span class="sxs-lookup"><span data-stu-id="22d08-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="22d08-139">사용자 고유의 사용자 지정 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="22d08-139">Creating your own custom environment</span></span>

<span data-ttu-id="22d08-140">이 샘플 환경을 사용 하는 것 외에도 소프트웨어를 편집 하면 즐겨 찾는 3D를 사용 하 여 사용자 고유의 사용자 지정 환경을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="22d08-141">모델링 지침</span><span class="sxs-lookup"><span data-stu-id="22d08-141">Modeling guidelines</span></span>

<span data-ttu-id="22d08-142">환경을 모델링 하는 경우 다음 권장 사항에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-142">When modeling your environment, keep the following recommendations in mind.</span></span> <span data-ttu-id="22d08-143">이렇게 하면 올바른 방향 believably 규모 환경에서 사용자 생성을 확인 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-143">This will help ensure the user spawns in the correct orientation in a believably-sized world:</span></span>

1. <span data-ttu-id="22d08-144">사용자는 원점을 원하는 생성 위치 0,0,0 따라서 가운데에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-144">Users will spawn at 0,0,0 so center your desired spawn location around the origin.</span></span>
2. <span data-ttu-id="22d08-145">작업 단위는 전 세계 규모의 자산을 작성할 수 있습니다 있도록 미터제로 설정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-145">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="22d08-146">최대 축 "Y"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-146">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="22d08-147">자산 양의 Z 축 방향으로 "forward" 발생 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-147">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="22d08-148">모든 메시를 결합할 필요는 없지만 리소스가 제한 된 장치를 대상으로 하는 경우 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-148">All meshes do not need to be combined, but it is recommended if you are targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="22d08-149">환경 내보내기</span><span class="sxs-lookup"><span data-stu-id="22d08-149">Exporting your environment</span></span>

<span data-ttu-id="22d08-150">Windows Mixed Reality 환경에 대 한 자산 배달 형식으로 이진 glTF (.glb)에 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-150">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="22d08-151">glTF는 사용료를 지불 Khronos 그룹에 의해 유지 관리 하는 3D 자산 배달에 대 한 무료 개방형 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-151">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="22d08-152">Windows 앱 및 환경에서 형식에 대 한 Microsoft의 지원 됩니다 glTF 업계 상호 운용 가능한 3D 콘텐츠에 대 한 표준으로 발전 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-152">As glTF evolves as an industry standard for interoperable 3D content, so will Microsoft’s support for the format across Windows apps and experiences.</span></span>

<span data-ttu-id="22d08-153">사용자 지정 홈 환경으로 사용할 자산을 내보내는 첫 번째 단계는 glTF 2.0 모델을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-153">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="22d08-154">GlTF 작업 그룹은 유지 관리를 [지원 되는 내보내기 도구 목록과 변환기](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) glTF 2.0 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-154">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="22d08-155">시작 하려면이 페이지에 나열 된 프로그램 중 하나를 사용 하 여 만들고 glTF 2.0 모델 내보내기 또는 지원 되는 변환기 중 하나를 사용 하 여 기존 모델을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-155">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="22d08-156">또한 체크 아웃 [유용한 기사의](https://www.khronos.org/blog/art-pipeline-for-gltf) Blender와 3DS glTF 모델 내보내기에 대 한 최신 워크플로 간략하게 제공 하는 직접 Max입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-156">Additionally, check out [this helpful article](https://www.khronos.org/blog/art-pipeline-for-gltf) which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="22d08-157">환경 제한</span><span class="sxs-lookup"><span data-stu-id="22d08-157">Environment limits</span></span>

<span data-ttu-id="22d08-158">모든 환경에는 < 256 mb 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-158">All environments must be < 256 mbs.</span></span> <span data-ttu-id="22d08-159">256 mb 보다 큰 환경 로드 하 고 사용자와 관련 된 기본 skybox를 사용 하 여 빈 세계는 대체 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-159">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="22d08-160">모델을 만들 때이 파일 크기 제한을 염두에서 하세요 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-160">Please keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="22d08-161">또한 아래 설명 된 대로 WindowsMRAssetConverter를 사용 하 여 사용자 환경 최적화 하려는 경우 최적화 프로그램이 더 큰 파일 크기를 갖지만 더 빠르게 로드 하는 질감을 만듭니다 질감 크기를 증가 인식 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-161">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="22d08-162">사용자 환경 최적화</span><span class="sxs-lookup"><span data-stu-id="22d08-162">Optimizing your environment</span></span>

<span data-ttu-id="22d08-163">Windows Mixed Reality를 다양 한 환경의 부하 시간을 크게 줄일 수 있는 선택적 최적화를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-163">Windows Mixed Reality supports a number of optional optimizations that will significantly reduce the load time of your environments.</span></span> <span data-ttu-id="22d08-164">이 경우에 따라은 로드 하는 동안 시간 초과 많은 질감을 사용 하 여 환경에 특히 중요 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-164">This can be especially important for environments with many textures, as they will sometimes time out while loading.</span></span> <span data-ttu-id="22d08-165">그러나 적거나 저해상도 질감을 사용 하 여 소규모 환경의 않습니다 항상 필요한, 일반적으로 모든 자산에 대해이 단계가 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-165">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="22d08-166">이 과정을 더 쉽게 만들었습니다 합니다 [Windows 혼합 현실 자산 변환기 (GitHub에서 사용 가능)](https://github.com/Microsoft/glTF-Toolkit/releases) 프로그램 최적화를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-166">To make this process easier, we have created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to perform your optimizations.</span></span> <span data-ttu-id="22d08-167">이 도구는 추가 질감 압축, 압축 및 아래쪽 크기 조정 확인을 수행 하 여 모든 표준 2.0 glTF 또는.glb을 최적화 하기 위해 Microsoft glTF 도구 키트에서 사용할 수 있는 유틸리티 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-167">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or .glb by performing an additional texture packing, compression and resolution down-scaling.</span></span> 

<span data-ttu-id="22d08-168">변환기는 현재 다양 한 최적화가 정확한 동작을 조정 하는 플래그를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-168">The converter currently supports a number of flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="22d08-169">최상의 결과 위해 다음 플래그를 사용 하 여 실행을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-169">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="22d08-170">플래그</span><span class="sxs-lookup"><span data-stu-id="22d08-170">Flag</span></span>|<span data-ttu-id="22d08-171">권장된 값</span><span class="sxs-lookup"><span data-stu-id="22d08-171">Recommended Value(s)</span></span>|<span data-ttu-id="22d08-172">설명</span><span class="sxs-lookup"><span data-stu-id="22d08-172">Description</span></span>
---|---|---
<span data-ttu-id="22d08-173">-max-texture-size</span><span class="sxs-lookup"><span data-stu-id="22d08-173">-max-texture-size</span></span>|<span data-ttu-id="22d08-174">1024 또는 2048</span><span class="sxs-lookup"><span data-stu-id="22d08-174">1024 or 2048</span></span>| <span data-ttu-id="22d08-175">질감의 품질을 개선 하기 위해이 조정, 기본값은 512 x 512입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-175">Tweak this to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="22d08-176">더 큰 값을 환경 파일 크기를 크게 영향을 참고 따라서 염두 256mb 제한</span><span class="sxs-lookup"><span data-stu-id="22d08-176">Note that a larger value will significantly impact the file size of the environment so keep the 256 mb limit in mind</span></span>
<span data-ttu-id="22d08-177">-최소 버전</span><span class="sxs-lookup"><span data-stu-id="22d08-177">-min-version</span></span>|<span data-ttu-id="22d08-178">1803</span><span class="sxs-lookup"><span data-stu-id="22d08-178">1803</span></span>|<span data-ttu-id="22d08-179">사용자 지정 환경 버전의 windows 에서만 지원 됩니다 > 1803 =.</span><span class="sxs-lookup"><span data-stu-id="22d08-179">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="22d08-180">이 플래그는 이전 버전의 질감을 제거 하 고 최종 자산의 파일 크기를 줄이기</span><span class="sxs-lookup"><span data-stu-id="22d08-180">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="22d08-181">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-181">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="22d08-182">테스트 환경</span><span class="sxs-lookup"><span data-stu-id="22d08-182">Testing your environment</span></span>

<span data-ttu-id="22d08-183">최종.glb 환경을 만든 후 헤드셋에서 테스트할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-183">Once you have your final .glb environment you're ready to test it out in the headset.</span></span> <span data-ttu-id="22d08-184">2 단계에서 시작 합니다 ["샘플 환경을 동안"](#trying-a-sample-environment) 홈 혼합된 현실으로 사용자 지정 환경을 사용 하는 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-184">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="feedback"></a><span data-ttu-id="22d08-185">사용자 의견</span><span class="sxs-lookup"><span data-stu-id="22d08-185">Feedback</span></span>

<span data-ttu-id="22d08-186">이 실험적 기능을 평가 하는 것을 하는 동안 사용자 지정 환경에서 발생할 수 있는 버그를 사용 하는 방법을 학습에 관심이 및 원하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-186">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may encounter, and how you like the feature.</span></span> <span data-ttu-id="22d08-187">만들기 및 사용자 지정 홈 환경에서 사용에 대 한 모든 의견을 [개발자 포럼](https://forums.hololens.com/categories/custom-home-environments)합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-187">Please share any and all feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="22d08-188">문제 해결 및 팁</span><span class="sxs-lookup"><span data-stu-id="22d08-188">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="22d08-189">환경의 이름을 변경 하려면 어떻게 해야 합니까?</span><span class="sxs-lookup"><span data-stu-id="22d08-189">How do I change the name of the environment?</span></span>

<span data-ttu-id="22d08-190">환경 폴더에 파일 이름은 위치 선택에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-190">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="22d08-191">환경의 이름을 변경 하려면 단순히 환경 이름 바꾸기 파일 이름, 다시 시작 후 혼합 현실 포털 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-191">To change the name of your environment simply rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="22d08-192">위치 선택 내에서 사용자 지정 환경을 어떻게 제거 합니까?</span><span class="sxs-lookup"><span data-stu-id="22d08-192">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="22d08-193">사용자 지정 환경을 제거 하려면 PC의 환경 폴더를 엽니다 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 환경을 삭제 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-193">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="22d08-194">혼합 현실 포털을 다시 시작 하면이 환경 위치 선택에서 더 이상 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-194">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="22d08-195">내 즐겨 찾는 사용자 지정 환경 기본값으로 하는 방법</span><span class="sxs-lookup"><span data-stu-id="22d08-195">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="22d08-196">현재 기본 환경을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-196">You can't currently change the default environment.</span></span> <span data-ttu-id="22d08-197">혼합 현실 포털을 다시 시작할 때마다 Cliff 집 환경에 반환 되는 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-197">Each time you restart Mixed Reality Portal, you will be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="22d08-198">빈 공간에 생성 하나요</span><span class="sxs-lookup"><span data-stu-id="22d08-198">I spawn into a blank space</span></span>

<span data-ttu-id="22d08-199">Windows Mixed Reality [256mb를 초과 하는 환경을 지원 하지 않습니다](#environment-limits)합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-199">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="22d08-200">Environment이이 제한을 초과 하는 경우 모델이 없는 빈 하늘 상자에서 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-200">When an environment exceeds this limit, you will land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="22d08-201">내 환경에 로드 하는 데 시간이 오래 걸리는</span><span class="sxs-lookup"><span data-stu-id="22d08-201">It takes a long time to load my environment</span></span>

<span data-ttu-id="22d08-202">선택적 최적화를 더 빠르게 로드 되도록 환경에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-202">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="22d08-203">참조 ["환경의 최적화"](#optimizing-your-environment) 세부 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-203">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="22d08-204">내 환경의 규모 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-204">The scale of my environment is incorrect</span></span>

<span data-ttu-id="22d08-205">Windows Mixed Reality 환경을 로드할 때 glTF 단위 1 미터를 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-205">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="22d08-206">환경을 로드는 예기치 않은 확장을 다시 확인 되도록에 내보내기 하는 경우 1 미터 규모로 모델링 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-206">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1 meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="22d08-207">내 환경에서 생성 위치가 잘못 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-207">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="22d08-208">기본 생성 위치는 환경의 0,0,0에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-208">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="22d08-209">해당 현재 불가능 환경의 원하는 생성 시점에 배치 하 여 원본과 내보내 생성 시점을 수정 해야 하므로이 위치를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-209">Its not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the desired spawn point.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="22d08-210">오디오 환경의 올바른 보인다는 것</span><span class="sxs-lookup"><span data-stu-id="22d08-210">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="22d08-211">사용자 지정 환경을 만들면 사용자가 만든 실제 공간 일치 하지 않는 소음 렌더링 시뮬레이션을 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-211">When you create your custom environment, it will be using an acoustics rendering simulation that does not match the physical space you have created.</span></span> <span data-ttu-id="22d08-212">Sound 잘못 된 방향에서 가져올 수 있습니다 및 들리지만 muffled 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d08-212">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="22d08-213">참조</span><span class="sxs-lookup"><span data-stu-id="22d08-213">See also</span></span>
* [<span data-ttu-id="22d08-214">실제로 홈 혼합 Windows 탐색</span><span class="sxs-lookup"><span data-stu-id="22d08-214">Navigating the Windows Mixed Reality Home</span></span>](#navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="22d08-215">Windows 혼합 현실 자산 변환기 (github)</span><span class="sxs-lookup"><span data-stu-id="22d08-215">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)

