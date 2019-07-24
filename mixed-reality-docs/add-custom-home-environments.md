---
title: 사용자 지정 홈 환경 추가
description: Microsoft에서 제공 하는 Windows Mixed Reality 홈 환경 외에도 사용자 고유의을 만들고 사용 하 여 시험해 볼 수 있습니다.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, 가상 현실, VR, MR, 홈, 사용자 지정 환경, 장소, 절벽 집, skyloft, 사용자, 만들기
ms.openlocfilehash: d0cdb878f1994cb5f898f06b98d74dee3dd4fdf1
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024533"
---
# <a name="add-custom-home-environments"></a><span data-ttu-id="55b8c-104">사용자 지정 홈 환경 추가</span><span class="sxs-lookup"><span data-stu-id="55b8c-104">Add custom home environments</span></span>

>[!NOTE]
><span data-ttu-id="55b8c-105">이는 실험적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-105">This is an experimental feature.</span></span> <span data-ttu-id="55b8c-106">시도 하 고 재미 있게 해 주지만, 모든 것이 예상 대로 작동 하지 않을 경우에는 걱정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="55b8c-107">이 기능의 실행 가능성을 평가 하 고 사용 하는 데 관심이 있기 때문에 [개발자 포럼](https://forums.hololens.com/categories/custom-home-environments)에서 사용자 환경 및 발견 한 버그를 알려 주세요.</span><span class="sxs-lookup"><span data-stu-id="55b8c-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="55b8c-108">[Windows 10 4 월 2018 업데이트](#release-notes-april-2018.md)부터 [windows Mixed Reality 홈](#navigating-the-windows-mixed-reality-home.md)으로 사용할 수 있는 사용자 지정 환경을 시작 메뉴의 위치 선택기에 추가할 수 있는 실험적 기능을 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-108">Starting with the [Windows 10 April 2018 update](#release-notes-april-2018.md), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](#navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="55b8c-109">Windows Mixed Reality에는 집으로 선택할 수 있는 두 가지 기본 환경인 절벽 집과 Skyloft가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, that you can choose as your home.</span></span> <span data-ttu-id="55b8c-110">사용자 지정 환경을 만들면 직접 만든 목록을 사용 하 여 해당 목록을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-110">Creating custom environments allows you to expand that list with your own creations.</span></span> <span data-ttu-id="55b8c-111">작성자와 개발자의 관심을 평가 하는 초기 상태로이 기능을 사용할 수 있도록 하 고, 어떤 종류의 사용자를 만드는 지 확인 하 고, 다양 한 제작 도구를 사용 하는 방법을 이해 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-111">We are making this available in an early state to evaluate interest from creators and developers, see what kinds of worlds you create, and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="55b8c-112">사용자 지정 환경을 사용 하는 경우 teleporting, 앱과의 상호 작용 및 holograms 배치는 절벽 집 및 Skyloft에서와 같이 작동 하는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-112">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="55b8c-113">판타지에서 웹을 찾아보거나 holograms를 사용 하 여 futuristic 도시를 채울 수 있습니다. 가능성은 무한 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-113">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="55b8c-114">장치 지원</span><span class="sxs-lookup"><span data-stu-id="55b8c-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="55b8c-115"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="55b8c-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="55b8c-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="55b8c-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="55b8c-117"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="55b8c-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="55b8c-118">사용자 지정 홈 환경</span><span class="sxs-lookup"><span data-stu-id="55b8c-118">Custom home environments</span></span></td>
        <td><span data-ttu-id="55b8c-119">❌</span><span class="sxs-lookup"><span data-stu-id="55b8c-119">❌</span></span></td>
        <td><span data-ttu-id="55b8c-120">✔️</span><span class="sxs-lookup"><span data-stu-id="55b8c-120">✔️</span></span></td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="55b8c-121">샘플 환경 시도</span><span class="sxs-lookup"><span data-stu-id="55b8c-121">Trying a sample environment</span></span>

<span data-ttu-id="55b8c-122">사용자 지정 홈 환경의 독창적인 기능 중 일부를 보여 주는 샘플 환경을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-122">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="55b8c-123">다음 단계를 수행 하 여 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="55b8c-123">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="55b8c-124">[샘플 판타지 섬 환경 다운로드](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) 자동 압축 풀기 실행 파일에 대 한 링크를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-124">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="55b8c-125">![판타지 섬 샘플 환경](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="55b8c-125">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="55b8c-126">*판타지 섬 샘플 환경*</span><span class="sxs-lookup"><span data-stu-id="55b8c-126">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="55b8c-127">방금 다운로드 한 **Fantasy_Island** 파일을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-127">Run the **Fantasy_Island.exe** file you just downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="55b8c-128">웹에서 다운로드 한 .exe 파일을 실행 하려고 할 때 (예:) "Windows 보호 된 PC" 팝업이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-128">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="55b8c-129">이 팝업에서 Fantasy_Island를 실행 하려면 **추가 정보** 를 선택 하 고 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-129">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="55b8c-130">이 보안 설정은 신뢰 하지 않을 수 있는 파일을 다운로드 하는 것을 방지 하기 위한 것 이므로 파일 원본을 신뢰 하는 경우에만이 옵션을 선택 하십시오.</span><span class="sxs-lookup"><span data-stu-id="55b8c-130">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="55b8c-131">**파일 탐색기** 를 열고 주소 표시줄 `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`에 다음을 붙여넣어 환경 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-131">Open **File Explorer** and navigate to the environments folder by pasting the following in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="55b8c-132">다운로드 한 샘플 환경을이 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-132">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="55b8c-133">**혼합 현실 포털**을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-133">Restart **Mixed Reality Portal**.</span></span> <span data-ttu-id="55b8c-134">그러면 위치 선택기에서 환경 목록이 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-134">This will refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="55b8c-135">헤드셋에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-135">Put on your headset.</span></span> <span data-ttu-id="55b8c-136">홈에 있으면 컨트롤러의 Windows 단추를 사용 하 여 **시작 메뉴** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-136">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="55b8c-137">고정 된 앱 목록 위의 **장소** 아이콘을 선택 하 여 홈 환경을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-137">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="55b8c-138">위치 목록에서 다운로드 한 판타지 섬 환경을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-138">You will find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="55b8c-139">새 사용자 지정 홈 환경을 입력 하려면 **판타지 섬** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-139">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="55b8c-140">사용자 고유의 사용자 지정 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="55b8c-140">Creating your own custom environment</span></span>

<span data-ttu-id="55b8c-141">샘플 환경을 사용 하는 것 외에도 즐겨 사용 하는 3D 편집 소프트웨어를 사용 하 여 사용자 지정 환경을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-141">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="55b8c-142">모델링 지침</span><span class="sxs-lookup"><span data-stu-id="55b8c-142">Modeling guidelines</span></span>

<span data-ttu-id="55b8c-143">환경을 모델링할 때 다음 권장 사항을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-143">When modeling your environment, keep the following recommendations in mind.</span></span> <span data-ttu-id="55b8c-144">이렇게 하면 사용자가 believably 크기의 세계에서 올바른 방향으로 생성 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-144">This will help ensure the user spawns in the correct orientation in a believably-sized world:</span></span>

1. <span data-ttu-id="55b8c-145">사용자는 0, 0, 0을 생성 하므로 원본 주위에서 원하는 생성 위치를 중앙에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-145">Users will spawn at 0,0,0 so center your desired spawn location around the origin.</span></span>
2. <span data-ttu-id="55b8c-146">자산을 전 세계 규모로 제작할 수 있도록 작업 단위를 미터로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-146">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="55b8c-147">위쪽 축을 "Y"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-147">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="55b8c-148">자산은 양의 Z 축에 "전달" 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-148">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="55b8c-149">모든 메시를 결합할 필요는 없지만 리소스가 제한 된 장치를 대상으로 하는 경우에는 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-149">All meshes do not need to be combined, but it is recommended if you are targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="55b8c-150">환경 내보내기</span><span class="sxs-lookup"><span data-stu-id="55b8c-150">Exporting your environment</span></span>

<span data-ttu-id="55b8c-151">Windows Mixed Reality는 환경에 대 한 자산 배달 형식으로 이진 글 Tf (.bb)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-151">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="55b8c-152">글 Tf는 Khronos 그룹에서 유지 관리 되는 3D 자산 배달에 대 한 무료 무료 오픈 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-152">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="55b8c-153">인 글 Tf는 상호 운용할 수 있는 3D 콘텐츠에 대 한 업계 표준으로 진화 하므로 Microsoft는 Windows 앱과 환경에서 형식을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-153">As glTF evolves as an industry standard for interoperable 3D content, so will Microsoft’s support for the format across Windows apps and experiences.</span></span>

<span data-ttu-id="55b8c-154">사용자 지정 홈 환경으로 사용할 자산을 내보내는 첫 번째 단계는 글 2.0 모델을 생성 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-154">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="55b8c-155">내보내기 Tf 작업 그룹은 [지원 되는 및 변환기의 목록을](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) 유지 관리 하 여 글 2.0 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-155">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="55b8c-156">시작 하려면이 페이지에 나열 된 프로그램 중 하나를 사용 하 여 글 2.0 모델을 만들거나 내보내거나 지원 되는 변환기 중 하나를 사용 하 여 기존 모델을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-156">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="55b8c-157">또한 Blender 및 3DS Max에서 직접 인 글 록 모델을 내보내기 위한 art 워크플로의 개요를 제공 하는 [이 유용한 문서](https://www.khronos.org/blog/art-pipeline-for-gltf) 를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="55b8c-157">Additionally, check out [this helpful article](https://www.khronos.org/blog/art-pipeline-for-gltf) which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="55b8c-158">환경 제한</span><span class="sxs-lookup"><span data-stu-id="55b8c-158">Environment limits</span></span>

<span data-ttu-id="55b8c-159">모든 환경은 256 < 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-159">All environments must be < 256 mbs.</span></span> <span data-ttu-id="55b8c-160">256 mb 보다 큰 환경은 로드 되지 않고 사용자를 둘러싼 기본 skybox을 사용 하 여 빈 환경으로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-160">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="55b8c-161">모델을 만들 때이 파일 크기 제한을 염두에 두세요.</span><span class="sxs-lookup"><span data-stu-id="55b8c-161">Please keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="55b8c-162">또한 아래에 설명 된 대로 WindowsMRAssetConverter를 사용 하 여 환경을 최적화 하려는 경우 최적화 프로그램에서 더 큰 파일 크기의 질감을 만들지만 더 빠르게 로드 하므로 텍스처 크기가 cognizant 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-162">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="55b8c-163">환경 최적화</span><span class="sxs-lookup"><span data-stu-id="55b8c-163">Optimizing your environment</span></span>

<span data-ttu-id="55b8c-164">Windows Mixed Reality는 환경의 로드 시간을 크게 줄일 수 있는 다양 한 선택적 최적화를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-164">Windows Mixed Reality supports a number of optional optimizations that will significantly reduce the load time of your environments.</span></span> <span data-ttu-id="55b8c-165">이러한 기능은 많은 질감이 있는 환경에서 로드 하는 동안 시간이 초과 되는 경우에 특히 중요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-165">This can be especially important for environments with many textures, as they will sometimes time out while loading.</span></span> <span data-ttu-id="55b8c-166">일반적으로 모든 자산에 대해이 단계를 수행 하는 것이 좋지만 거의 또는 저해상도 질감이 있는 소규모 환경에서는 항상 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-166">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="55b8c-167">이 프로세스를 더 쉽게 수행 하기 위해 최적화를 수행 하기 위해 [Windows Mixed Reality 자산 변환기 (GitHub에서 사용 가능)](https://github.com/Microsoft/glTF-Toolkit/releases) 를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-167">To make this process easier, we have created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to perform your optimizations.</span></span> <span data-ttu-id="55b8c-168">이 도구는 Microsoft 글 Tf 도구 키트에서 제공 되는 일련의 유틸리티를 사용 하 여 추가 텍스처 압축, 압축 및 해상도 축소를 수행 하 여 표준 2.0 글 Tf 또는. 글 2를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-168">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or .glb by performing an additional texture packing, compression and resolution down-scaling.</span></span> 

<span data-ttu-id="55b8c-169">변환기는 현재 최적화의 정확한 동작을 조정 하기 위해 여러 플래그를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-169">The converter currently supports a number of flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="55b8c-170">최상의 결과를 위해 다음 플래그를 사용 하 여를 실행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-170">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="55b8c-171">플래그</span><span class="sxs-lookup"><span data-stu-id="55b8c-171">Flag</span></span>|<span data-ttu-id="55b8c-172">권장 값</span><span class="sxs-lookup"><span data-stu-id="55b8c-172">Recommended Value(s)</span></span>|<span data-ttu-id="55b8c-173">설명</span><span class="sxs-lookup"><span data-stu-id="55b8c-173">Description</span></span>
---|---|---
<span data-ttu-id="55b8c-174">-최대 질감-크기</span><span class="sxs-lookup"><span data-stu-id="55b8c-174">-max-texture-size</span></span>|<span data-ttu-id="55b8c-175">1024 또는 2048</span><span class="sxs-lookup"><span data-stu-id="55b8c-175">1024 or 2048</span></span>| <span data-ttu-id="55b8c-176">이를 조정 하 여 질감의 품질을 향상 시킵니다. 기본값은 512x512입니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-176">Tweak this to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="55b8c-177">값이 클수록 환경의 파일 크기에 크게 영향을 주므로 256 mb 제한을 염두에 두십시오.</span><span class="sxs-lookup"><span data-stu-id="55b8c-177">Note that a larger value will significantly impact the file size of the environment so keep the 256 mb limit in mind</span></span>
<span data-ttu-id="55b8c-178">-최소 버전</span><span class="sxs-lookup"><span data-stu-id="55b8c-178">-min-version</span></span>|<span data-ttu-id="55b8c-179">1803</span><span class="sxs-lookup"><span data-stu-id="55b8c-179">1803</span></span>|<span data-ttu-id="55b8c-180">사용자 지정 환경은 windows > = 1803 버전 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-180">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="55b8c-181">이 플래그는 이전 버전의 질감을 제거 하 고 최종 자산의 파일 크기를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-181">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="55b8c-182">이는 아래와 같이 함수의 반환값을 데이터 프레임으로 바로 변환하는 데 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-182">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="55b8c-183">환경 테스트</span><span class="sxs-lookup"><span data-stu-id="55b8c-183">Testing your environment</span></span>

<span data-ttu-id="55b8c-184">최종 .bb 환경을 준비 하 고 나면 헤드셋에서 테스트할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-184">Once you have your final .glb environment you're ready to test it out in the headset.</span></span> <span data-ttu-id="55b8c-185">["샘플 환경 시도"](#trying-a-sample-environment) 섹션의 2 단계에서 시작 하 여 사용자 지정 환경을 혼합 현실 홈으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-185">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="feedback"></a><span data-ttu-id="55b8c-186">사용자 의견</span><span class="sxs-lookup"><span data-stu-id="55b8c-186">Feedback</span></span>

<span data-ttu-id="55b8c-187">이 실험적 기능을 평가 하는 동안 사용자 지정 환경을 사용 하는 방법, 발생할 수 있는 버그 및 기능을 원하는 방법을 배우는 데 관심이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-187">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may encounter, and how you like the feature.</span></span> <span data-ttu-id="55b8c-188">[개발자 포럼](https://forums.hololens.com/categories/custom-home-environments)에서 사용자 지정 홈 환경을 만들고 사용 하기 위한 모든 피드백을 공유 해 주세요.</span><span class="sxs-lookup"><span data-stu-id="55b8c-188">Please share any and all feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="55b8c-189">문제 해결 및 팁</span><span class="sxs-lookup"><span data-stu-id="55b8c-189">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="55b8c-190">환경 이름을 변경 어떻게 할까요??</span><span class="sxs-lookup"><span data-stu-id="55b8c-190">How do I change the name of the environment?</span></span>

<span data-ttu-id="55b8c-191">환경 폴더의 파일 이름은 위치 선택에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-191">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="55b8c-192">환경 이름을 변경 하려면 환경 파일 이름 이름을 바꾸고 Mixed Reality 포털을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-192">To change the name of your environment simply rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="55b8c-193">내 위치 선택기에서 사용자 지정 환경을 제거할 어떻게 할까요? 있나요?</span><span class="sxs-lookup"><span data-stu-id="55b8c-193">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="55b8c-194">사용자 지정 환경을 제거 하려면 PC에서 환경 폴더 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`)를 열고 환경을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-194">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="55b8c-195">Mixed Reality 포털을 다시 시작한 후에는이 환경이 더 이상 장소 선택기에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-195">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="55b8c-196">즐겨 사용 하는 사용자 지정 환경에 기본값 어떻게 할까요??</span><span class="sxs-lookup"><span data-stu-id="55b8c-196">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="55b8c-197">현재 기본 환경을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-197">You can't currently change the default environment.</span></span> <span data-ttu-id="55b8c-198">Mixed Reality 포털을 다시 시작할 때마다 절벽 집 환경으로 돌아옵니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-198">Each time you restart Mixed Reality Portal, you will be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="55b8c-199">빈 공간을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-199">I spawn into a blank space</span></span>

<span data-ttu-id="55b8c-200">Windows Mixed Reality [는 256 mb를 초과 하는 환경을 지원 하지 않습니다](#environment-limits).</span><span class="sxs-lookup"><span data-stu-id="55b8c-200">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="55b8c-201">환경에서이 한도를 초과 하면 모델 없이 빈 하늘 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-201">When an environment exceeds this limit, you will land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="55b8c-202">환경을 로드 하는 데 시간이 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-202">It takes a long time to load my environment</span></span>

<span data-ttu-id="55b8c-203">환경에 선택적 최적화를 추가 하 여 부하를 더 빠르게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-203">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="55b8c-204">자세한 내용은 ["환경 최적화"](#optimizing-your-environment) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="55b8c-204">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="55b8c-205">내 환경의 소수 자릿수가 잘못 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-205">The scale of my environment is incorrect</span></span>

<span data-ttu-id="55b8c-206">Windows Mixed Reality는 환경을 로드 하는 경우 글 Tf 단위를 1 미터로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-206">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="55b8c-207">환경에서 예기치 않은 규모를 로드 하는 경우 내보내기를 다시 확인 하 여 1 미터 단위로 모델링 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-207">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1 meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="55b8c-208">내 환경의 생성 위치가 잘못 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-208">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="55b8c-209">기본 생성 위치는 환경에서 0, 0, 0에 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-209">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="55b8c-210">현재이 위치를 사용자 지정할 수 없으므로 원하는 생성 지점에 배치 된 원본을 사용 하 여 환경을 내보내 생성 지점을 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-210">Its not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the desired spawn point.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="55b8c-211">오디오는 환경에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-211">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="55b8c-212">사용자 지정 환경을 만들 때 만든 실제 공간과 일치 하지 않는 acoustics 렌더링 시뮬레이션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-212">When you create your custom environment, it will be using an acoustics rendering simulation that does not match the physical space you have created.</span></span> <span data-ttu-id="55b8c-213">소리는 잘못 된 방향에서 제공 될 수 있으며 소리가 muffled 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b8c-213">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="55b8c-214">참조</span><span class="sxs-lookup"><span data-stu-id="55b8c-214">See also</span></span>
* [<span data-ttu-id="55b8c-215">Windows Mixed Reality 자산 변환기 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="55b8c-215">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)

