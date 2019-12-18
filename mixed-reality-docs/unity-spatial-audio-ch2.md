---
title: 공간 오디오 자습서-2. Spatializing button 상호 작용 소리
description: 프로젝트에 단추를 추가 하 고 단추 상호 작용 소리를 spatialize.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오
ms.openlocfilehash: bd70e3bc88ee39b2c6257089ac3a2b93dfae0ad1
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182780"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="3d991-105">Spatializing button 상호 작용 소리</span><span class="sxs-lookup"><span data-stu-id="3d991-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="3d991-106">목표</span><span class="sxs-lookup"><span data-stu-id="3d991-106">Objectives</span></span>
<span data-ttu-id="3d991-107">HoloLens 2 자습서의 공간 오디오 모듈의이 두 번째 장에서는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="3d991-108">단추 추가</span><span class="sxs-lookup"><span data-stu-id="3d991-108">Add a button</span></span>
* <span data-ttu-id="3d991-109">단추 클릭 소리 Spatialize</span><span class="sxs-lookup"><span data-stu-id="3d991-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="3d991-110">단추 추가</span><span class="sxs-lookup"><span data-stu-id="3d991-110">Add a button</span></span>
<span data-ttu-id="3d991-111">**프로젝트** 창에서 **자산** 을 선택 하 고 검색 표시줄에 "PressableButtonHoloLens2"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![자산에서 prefab 단추](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="3d991-113">Prefab 단추는 흰색 아이콘이 아니라 파란색 아이콘으로 표시 되는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="3d991-114">**PressableButtonHoloLens2** 라는 Prefab을 **계층** 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="3d991-115">새 단추의 **검사기** 창에서 **위치** 속성을 (0,-0.4, 2)로 설정 하 여 응용 프로그램이 시작 될 때 사용자 앞에 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="3d991-116">단추의 **변환** 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-116">The **Transform** component of the button will look like this:</span></span>

![단추 변형](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="3d991-118">Spatialize 단추 피드백</span><span class="sxs-lookup"><span data-stu-id="3d991-118">Spatialize button feedback</span></span>
<span data-ttu-id="3d991-119">이 단계에서는 단추에 대 한 오디오 피드백을 spatialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="3d991-120">관련 디자인 제안 사항은 [공간 음향 디자인](spatial-sound-design.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3d991-120">For related design suggestions, see [spatial sound design](spatial-sound-design.md).</span></span> 

<span data-ttu-id="3d991-121">오디오 **믹서** 창에서는 오디오 **원본** 구성 요소에서 오디오 재생을 위해 **믹서 그룹**이라는 대상을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="3d991-122">**창 > 오디오-> 오디오 믹서** 를 사용 하 여 메뉴 모음에서 **오디오 믹서** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="3d991-123">**Mixers**옆의 ' + '를 클릭 하 여 **믹서** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="3d991-124">새 믹서에는 **Master**라는 기본 **그룹이** 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="3d991-125">이제 **믹서** 창이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-125">Your **Mixer** pane will now look like this:</span></span>

![첫 번째 믹서가 있는 믹서 패널](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="3d991-127">[5 장](unity-spatial-audio-ch5.md)에서 반향를 사용 하도록 설정할 때까지 믹서의 볼륨 미터는 Microsoft Spatializer을 통해 재생 된 소리에 대 한 활동을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="3d991-128">**계층** 창에서 **PressableButtonHoloLens2** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="3d991-129">**검사기** 창에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="3d991-130">**오디오 원본** 구성 요소 찾기</span><span class="sxs-lookup"><span data-stu-id="3d991-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="3d991-131">**출력** 속성의 경우 선택기를 클릭 하 고 믹서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="3d991-132">**Spatialize** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="3d991-133">**공간 Blend** 슬라이더를 3d (1)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="3d991-134">2019 이전의 Unity 버전에서 ' Spatialize ' 확인란은 **오디오 소스**에 대 한 **검사기** 창의 아래쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="3d991-135">이러한 변경 후 **PressableButtonHoloLens2** 의 **오디오 원본** 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![오디오 원본 단추](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="3d991-137">**Spatialize** 확인란을 선택 하지 않고 **공간 Blend** 를 1 (3d)로 이동 하는 경우 Unity는 **Microsoft spatializer** with hrtfs 대신 패닝 spatializer를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="3d991-138">볼륨 곡선 조정</span><span class="sxs-lookup"><span data-stu-id="3d991-138">Adjust the Volume curve</span></span>
<span data-ttu-id="3d991-139">기본적으로 Unity는 수신기에서 더 멀리 경우 spatialized 소리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="3d991-140">이 감쇠가 상호 작용 피드백 소리에 적용 되 면 인터페이스를 사용 하기가 더 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="3d991-141">이 감쇠를 사용 하지 않도록 설정 하려면 **볼륨** 곡선을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="3d991-142">**PressableButtonHoloLens2**에 대 한 **검사기** 창의 **오디오 원본** 구성 요소에는 **3d 소리 설정**이라는 섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="3d991-143">해당 섹션에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-143">In that section:</span></span>
1. <span data-ttu-id="3d991-144">**Volume Rolloff** 속성을 Linear로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="3d991-145">Y 축의 ' 0 '에서 ' 1 '까지 **볼륨** 곡선 (빨간색 곡선)의 끝점을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="3d991-146">**볼륨** 곡선의 모양을 평면으로 조정 하려면 흰색 곡선 셰이프 컨트롤을 X 축에 평행으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="3d991-147">이러한 변경 후에는 **PressableButtonHoloLens2** **오디오 원본** 속성의 **3d 사운드 설정** 섹션이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![3D 소리 설정 단추](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a><span data-ttu-id="3d991-149">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3d991-149">Next steps</span></span>

<span data-ttu-id="3d991-150">HoloLens 2 또는 Unity 편집기에서 앱을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="3d991-150">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="3d991-151">앱에서 단추를 터치 하 고 spatialized 단추 상호 작용 소리를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-151">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="3d991-152">Unity 편집기에서 테스트 하는 경우 스페이스바를 눌러 스크롤 휠을 눌러 직접 시뮬레이션을 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d991-152">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="3d991-153">자세한 내용은 [Mrtk 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3d991-153">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

<span data-ttu-id="3d991-154">[3 장으로](unity-spatial-audio-ch3.md) 이동 하 여 앱에 비디오를 추가 하 고 비디오에서 오디오를 spatialize.</span><span class="sxs-lookup"><span data-stu-id="3d991-154">Continue to [Chapter 3](unity-spatial-audio-ch3.md) to add a video to your app, and spatialize the audio from the video.</span></span>

