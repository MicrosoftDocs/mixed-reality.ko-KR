---
title: 사례 연구-빌드 HoloSketch, 공간 레이아웃 및 HoloLens에 앱을 스케치 UX
description: HoloSketch는 장치의 공간 레이아웃 및 UX holographic 환경을 구축 하는 데는 HoloLens에 대 한 도구를 스케치 합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, 스케치, 앱
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600135"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="2a9eb-104">사례 연구-빌드 HoloSketch, 공간 레이아웃 및 HoloLens에 앱을 스케치 UX</span><span class="sxs-lookup"><span data-stu-id="2a9eb-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="2a9eb-105">HoloSketch는 장치의 공간 레이아웃 및 UX holographic 환경을 구축 하는 데는 HoloLens에 대 한 도구를 스케치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="2a9eb-106">HoloSketch 페어링된 Bluetooth 키보드 및 마우스와 제스처 및 음성 명령을 사용 하 여 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="2a9eb-107">HoloSketch의 목적은 신속 하 게 시각화 및 반복에 대 한 간단한 UX 레이아웃 도구를 제공 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="2a9eb-108">![HoloSketch: 공간 레이아웃 및 UX HoloLens에 앱을 스케치 합니다.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="2a9eb-109">*HoloSketch: 공간 레이아웃 및 HoloLens에 앱을 스케치 UX*</span><span class="sxs-lookup"><span data-stu-id="2a9eb-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="2a9eb-110">![신속 하 게 시각화 및 반복에 대 한 간단한 UX 레이아웃 도구입니다.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="2a9eb-111">*신속 하 게 시각화 및 반복에 대 한 간단한 UX 레이아웃 도구*</span><span class="sxs-lookup"><span data-stu-id="2a9eb-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="2a9eb-112">기능</span><span class="sxs-lookup"><span data-stu-id="2a9eb-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="2a9eb-113">빠른 연구 및 프로토타입 확장에 대 한 기본 형식</span><span class="sxs-lookup"><span data-stu-id="2a9eb-113">Primitives for quick studies and scale-prototyping</span></span>

![기본 셰이프를 사용 하 여](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="2a9eb-115">빠른 결집할 연구 및 프로토타입 확장에 대 한 기본 셰이프를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="2a9eb-116">OneDrive 통해 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="2a9eb-116">Import objects through OneDrive</span></span>

![개체 가져오기](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="2a9eb-118">PNG/JPG 이미지 또는 3D FBX 개체 가져오기 (Unity에서 패키징 필요) OneDrive 통해 혼합된 현실 공간으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="2a9eb-119">개체를 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-119">Manipulate objects</span></span>

![개체를 조작합니다.](images/manipulate-objects-640px.jpg)

<span data-ttu-id="2a9eb-121">친숙 한 3D 개체 인터페이스를 사용 하 여 개체 (이동/회전/배율)를 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="2a9eb-122">Bluetooth, 마우스/키보드, 제스처 및 음성 명령</span><span class="sxs-lookup"><span data-stu-id="2a9eb-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![Bluetooth를 지원합니다.](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="2a9eb-124">HoloSketch는 Bluetooth 마우스/키보드, 제스처 및 음성 명령을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="2a9eb-125">배경</span><span class="sxs-lookup"><span data-stu-id="2a9eb-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="2a9eb-126">발생 하는 장치에서 디자인의 중요성</span><span class="sxs-lookup"><span data-stu-id="2a9eb-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="2a9eb-127">HoloLens에 대 한 무언가 설계 하는 경우 장치에서 디자인을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="2a9eb-128">혼합된 현실 앱 디자인의 가장 큰 과제 중 하나는 확장성, 위치 및 깊이의 의미를 일반적인 2D 스케치 특히 통과 하기 어렵다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="2a9eb-129">2D의 비용 기반 통신</span><span class="sxs-lookup"><span data-stu-id="2a9eb-129">Cost of 2D based communication</span></span>

<span data-ttu-id="2a9eb-130">UX 흐름과 다른 사람에 게는 시나리오와 효과적으로 통신 하려면 디자이너 Illustrator, Photoshop 및 PowerPoint와 같은 기존 2D 도구를 사용 하 여 자산을 만드는 시간이 많이 소비 끝날 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="2a9eb-131">이러한 2D 디자인으로 변환 하기 위해 추가적인 작업이 필요한 경우가 많습니다 3D 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="2a9eb-132">몇 가지 아이디어는 3D로 2D에서이 변환에서 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="2a9eb-133">복잡 한 배포 프로세스</span><span class="sxs-lookup"><span data-stu-id="2a9eb-133">Complex deployment process</span></span>

<span data-ttu-id="2a9eb-134">혼합된 현실에 새 캔버스 이므로 기본적으로 디자인 반복 및 시행 착오 많은 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="2a9eb-135">Unity 및 Visual Studio와 같은 도구를 사용 하 여 모르는 디자이너에 대 한 쉽습니다 하지 HoloLens에 함께 무언가 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="2a9eb-136">일반적으로 장치에서 2D/3D 아트 워크를 보려면 아래 프로세스를 진행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="2a9eb-137">이것은 신속 하 게 아이디어와 시나리오에서 반복 하는 디자이너에 대 한 큰 장애물입니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="2a9eb-138">![복잡 한 배포 프로세스](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="2a9eb-139">*배포 프로세스*</span><span class="sxs-lookup"><span data-stu-id="2a9eb-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="2a9eb-140">HoloSketch 사용 하 여 간소화 된 프로세스</span><span class="sxs-lookup"><span data-stu-id="2a9eb-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="2a9eb-141">HoloSketch를 사용 하 여 개발 도구 및 포털 쌍 장치를 통하지 않고이 프로세스를 단순화 하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="2a9eb-142">OneDrive를 사용 하 여, 사용자는 HoloLens에 2D/3D 자산을 쉽게 배치 수 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="2a9eb-143">![HoloSketch 사용 하 여 간소화 된 프로세스](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="2a9eb-144">*HoloSketch 사용 하 여 간소화 된 프로세스*</span><span class="sxs-lookup"><span data-stu-id="2a9eb-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="2a9eb-145">3 차원 디자인 사고 및 솔루션을 장려</span><span class="sxs-lookup"><span data-stu-id="2a9eb-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="2a9eb-146">이 도구는 디자이너 수 있도록 솔루션을 진정으로 3 차원 공간에서 탐색 및 2D에 빠지지 않았는지 라고 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="2a9eb-147">백그라운드 Hololens의 경우 실제 이므로 해당 UI에 대 한 3D 배경이 만들기에 대 한 생각 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="2a9eb-148">HoloSketch는 디자이너가 Hololens에서 3D 디자인을 쉽게 탐색할 수 있는 방법을 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="2a9eb-149">시작</span><span class="sxs-lookup"><span data-stu-id="2a9eb-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="2a9eb-150">HoloSketch 2D 이미지 (JPG/PNG)을 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="2a9eb-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="2a9eb-151">' 문서/HoloSketch ' OneDrive 폴더에 JPG/PNG 이미지를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="2a9eb-152">HoloSketch에서 OneDrive 메뉴에서 선택 하 고 환경에서 이미지를 배치 하는 일을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="2a9eb-153">![2D 이미지 가져오기](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="2a9eb-154">*이미지 및 OneDrive 통해 3D 개체 가져오기*</span><span class="sxs-lookup"><span data-stu-id="2a9eb-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="2a9eb-155">HoloSketch 3D 개체를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="2a9eb-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="2a9eb-156">OneDrive 폴더에 업로드 하기 전에 Unity 자산 묶음으로 3D 개체를 패키지 하려면 다음 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="2a9eb-157">이 프로세스를 사용 하 여 Microsoft 그림판 3D, Maya 및 배급사 4d 등 3D 소프트웨어에서 FBX/OBJ 파일을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="2a9eb-158">현재 버전 5.4.5f1 Unity 사용 하 여 자산 번들 만들기가 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="2a9eb-159">다운로드 하 고 Unity 프로젝트를 엽니다 ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="2a9eb-160">이 Unity 프로젝트 번들 자산 생성을 위한 스크립트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="2a9eb-161">새 GameObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="2a9eb-162">내용에 따라 GameObject 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="2a9eb-163">검사기 창에서 ' 구성 요소 추가 '를 클릭 하 고 ' 상자 Collider'를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![검사기 창에서 ' 구성 요소 추가 '를 클릭 하 고 ' 상자 Collider' 추가](images/holosketch-10a-assetbundles-1000px.png)
   
   ![검사기 창에서 ' 구성 요소 추가 '를 클릭 하 고 ' 상자 Collider' # 2를 추가 합니다.](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="2a9eb-166">프로젝트 패널에 끌어와 3D FBX 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="2a9eb-167">계층 패널에 개체를 끌어 **아래에 새 GameObject**합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![아래에 새 GameObject 계층 패널에 개체를 끌어 놓습니다.](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="2a9eb-169">개체는 일치 하지 않는 경우에 collider 차원을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="2a9eb-170">얼굴 개체를 회전 **z 축**합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-170">Rotate the object to face **Z-axis**.</span></span>

   ![개체는 일치 하지 않는 경우 collider 크기를 조정 합니다.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="2a9eb-172">계층 구조 창에서 [프로젝트] 패널에 개체를 끌어서 **prefab 있도록**입니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="2a9eb-173">[관리자] 패널의 아래쪽에 드롭다운, 만들기 및 새 고유 이름을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="2a9eb-174">아래 예제에서는 추가 하 고 'brownchair' AssetBundle 이름에 대 한 할당을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![[관리자] 패널의 아래쪽에 드롭다운을 클릭 하 고 새 고유 이름을 할당 합니다.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="2a9eb-176">모델 개체에 대 한 축소판 이미지를 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="2a9eb-177">![프로젝트 패널에 이미지를 끌어서 개체에 사용 된 이름을 할당 합니다.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="2a9eb-178">Unity 프로젝트의 '자산' 폴더 아래에 있는 'Assetbundles' 라는 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="2a9eb-179">[자산] 메뉴에서 파일을 생성 하려면 ' AssetBundles 빌드 '를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="2a9eb-180">![[자산] 메뉴에서 파일을 생성 하려면 ' AssetBundles 빌드 '를 선택 합니다.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="2a9eb-181">**OneDrive에서 /Files/Documents/HoloSketch 폴더에 생성된 된 파일을 업로드 합니다.**</span><span class="sxs-lookup"><span data-stu-id="2a9eb-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="2a9eb-182">Asset_unique_name 파일만을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="2a9eb-183">매니페스트 파일 또는 AssetBundles 파일을 업로드할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="2a9eb-184">![파일/문서/HoloSketch에 파일 추가/폴더](images/holosketch-onedriveupload-1000px.png)
![HoloSketch의 OneDrive 메뉴에 추가 된 3D 개체를 보면](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="2a9eb-185">개체를 조작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="2a9eb-185">How to manipulate the objects</span></span>

<span data-ttu-id="2a9eb-186">HoloSketch 3D 소프트웨어에서 널리 사용 되는 기존 인터페이스를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="2a9eb-187">이동을 사용 지정, 회전, 제스처 및 마우스를 사용 하 여 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="2a9eb-188">음성 또는 키보드를 사용 하 여 서로 다른 모드 간에 빠르게 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="2a9eb-189">개체 조작 모드</span><span class="sxs-lookup"><span data-stu-id="2a9eb-189">Object manipulation modes</span></span>

<span data-ttu-id="2a9eb-190">![개체를 조작 하는 방법](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="2a9eb-191">*개체를 조작 하는 방법*</span><span class="sxs-lookup"><span data-stu-id="2a9eb-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="2a9eb-192">상황별 및 도구 벨트 메뉴</span><span class="sxs-lookup"><span data-stu-id="2a9eb-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="2a9eb-193">**상황에 맞는 메뉴를 사용 하 여**</span><span class="sxs-lookup"><span data-stu-id="2a9eb-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="2a9eb-194">상황에 맞는 메뉴를 열려면 double 어 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="2a9eb-195">메뉴 항목:</span><span class="sxs-lookup"><span data-stu-id="2a9eb-195">Menu items:</span></span>
* <span data-ttu-id="2a9eb-196">**레이아웃 화면:** 3D 그리드 시스템 레이아웃을 수행할 수 있는 여러 개체 이며 그룹으로 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="2a9eb-197">개체를 추가할 레이아웃 화면의 double 어-탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="2a9eb-198">**기본 형식:** 큐브, 구, 실린더 및 콘을 연구 결집할 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="2a9eb-199">**OneDrive:** 개체를 가져오려면 OneDrive 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="2a9eb-200">**도움말:** 도움말 화면을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="2a9eb-201">![상황에 맞는 메뉴](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="2a9eb-202">*상황에 맞는 메뉴*</span><span class="sxs-lookup"><span data-stu-id="2a9eb-202">*Contextual menu*</span></span>

<span data-ttu-id="2a9eb-203">**도구 벨트 메뉴를 사용 하 여**</span><span class="sxs-lookup"><span data-stu-id="2a9eb-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="2a9eb-204">이동, 회전, 크기 조정, 저장 및 로드 장면 도구 벨트 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="2a9eb-205">키보드, 제스처 및 음성 명령을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="2a9eb-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="2a9eb-206">![키보드, 제스처 및 음성 명령](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2a9eb-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="2a9eb-207">*키보드, 제스처 및 음성 명령*</span><span class="sxs-lookup"><span data-stu-id="2a9eb-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="2a9eb-208">앱 다운로드</span><span class="sxs-lookup"><span data-stu-id="2a9eb-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="2a9eb-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">다운로드 하 고 HoloSketch 앱을 무료로 Microsoft Store 설치</a>
</span><span class="sxs-lookup"><span data-stu-id="2a9eb-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="2a9eb-210">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="2a9eb-210">Known issues</span></span>
* <span data-ttu-id="2a9eb-211">사용 하 여 자산 번들 만들기는 현재 **Unity 버전 5.4.5f1 합니다.**</span><span class="sxs-lookup"><span data-stu-id="2a9eb-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="2a9eb-212">OneDrive의 데이터 양에 따라 앱 OneDrive 콘텐츠를 로드 하는 동안 중지 된 것 처럼 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="2a9eb-213">현재, 저장 및 로드 기능은 기본 개체 지원</span><span class="sxs-lookup"><span data-stu-id="2a9eb-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="2a9eb-214">메뉴 텍스트, 사운드, 비디오 및 사진 상황에 맞는 메뉴에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="2a9eb-215">Play 단추 메뉴의 도구 벨트 조작 gizmo를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="2a9eb-216">프로그램 스케치를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-216">Sharing your sketches</span></span>

<span data-ttu-id="2a9eb-217">HoloLens의 비디오 기록을 기능을 사용 하면 하면 ' Hey Cortana 시작/중지 기록 '.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="2a9eb-218">볼륨 위쪽/아래쪽에 스케치 사진을 찍은 함께 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2a9eb-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="2a9eb-219">저자 소개</span><span class="sxs-lookup"><span data-stu-id="2a9eb-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="2a9eb-220"><b>했어요 Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="2a9eb-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="2a9eb-221">UX 디자이너 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="2a9eb-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="2a9eb-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="2a9eb-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="2a9eb-223">개발자 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="2a9eb-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
