---
title: 사례 연구-HoloSketch, 공간 레이아웃 및 HoloLens 용 UX 스케치 앱 빌드
description: HoloSketch는 holographic 환경을 빌드하는 데 도움이 되는 장치 상의 공간 레이아웃 및 UX 스케치 도구입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, 스케치, 앱
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524404"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="bf67f-104">사례 연구-HoloSketch, 공간 레이아웃 및 HoloLens 용 UX 스케치 앱 빌드</span><span class="sxs-lookup"><span data-stu-id="bf67f-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="bf67f-105">HoloSketch는 holographic 환경을 빌드하는 데 도움이 되는 장치 상의 공간 레이아웃 및 UX 스케치 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="bf67f-106">HoloSketch는 쌍을 이루는 Bluetooth 키보드 및 마우스 뿐만 아니라 제스처 및 음성 명령에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="bf67f-107">HoloSketch의 목적은 신속한 시각화 및 반복을 위한 간단한 UX 레이아웃 도구를 제공 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="bf67f-108">![HoloSketch: HoloLens 용 공간 레이아웃 및 UX 스케치 앱입니다.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="bf67f-109">*HoloSketch: HoloLens 용 공간 레이아웃 및 UX 스케치 앱*</span><span class="sxs-lookup"><span data-stu-id="bf67f-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="bf67f-110">![빠른 시각화 및 반복을 위한 간단한 UX 레이아웃 도구입니다.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="bf67f-111">*빠른 시각화 및 반복을 위한 간단한 UX 레이아웃 도구입니다.*</span><span class="sxs-lookup"><span data-stu-id="bf67f-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="bf67f-112">기능</span><span class="sxs-lookup"><span data-stu-id="bf67f-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="bf67f-113">빠른 연구 및 규모 프로토타입 작성을 위한 기본 형식</span><span class="sxs-lookup"><span data-stu-id="bf67f-113">Primitives for quick studies and scale-prototyping</span></span>

![기본 도형 사용](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="bf67f-115">빠른 massing 연구 및 확장 프로토타입 작성을 위해 기본 셰이프를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="bf67f-116">OneDrive를 통해 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="bf67f-116">Import objects through OneDrive</span></span>

![개체 가져오기](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="bf67f-118">OneDrive를 통해 혼합 된 현실 공간으로 PNG/JPG 이미지 또는 3D FBX 개체 (Unity에서 패키징 필요)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="bf67f-119">개체 조작</span><span class="sxs-lookup"><span data-stu-id="bf67f-119">Manipulate objects</span></span>

![개체 조작](images/manipulate-objects-640px.jpg)

<span data-ttu-id="bf67f-121">익숙한 3D 개체 인터페이스를 사용 하 여 개체 (이동/회전/배율)를 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="bf67f-122">Bluetooth, 마우스/키보드, 제스처 및 음성 명령</span><span class="sxs-lookup"><span data-stu-id="bf67f-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![Bluetooth 지원](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="bf67f-124">HoloSketch는 Bluetooth 마우스/키보드, 제스처 및 음성 명령을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="bf67f-125">배경</span><span class="sxs-lookup"><span data-stu-id="bf67f-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="bf67f-126">장치에서 디자인이 발생 하는 중요성</span><span class="sxs-lookup"><span data-stu-id="bf67f-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="bf67f-127">HoloLens를 설계할 때 장치에서 디자인을 경험 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="bf67f-128">혼합 현실 앱 디자인에서 가장 큰 문제 중 하나는 특히 기존 2D 스케치를 통해 규모, 위치 및 깊이를 이해 하기 어려운 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="bf67f-129">2D 기반 통신 비용</span><span class="sxs-lookup"><span data-stu-id="bf67f-129">Cost of 2D based communication</span></span>

<span data-ttu-id="bf67f-130">UX 흐름과 시나리오를 다른 사용자에 게 효과적으로 전달 하기 위해 디자이너는 Illustrator, Photoshop 및 PowerPoint와 같은 기존 2D 도구를 사용 하 여 자산을 만드는 데 많은 시간이 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="bf67f-131">이러한 2D 디자인은 종종 3D로 변환 하는 데 추가 작업이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="bf67f-132">일부 아이디어는 2D에서 3D로의 변환에서 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="bf67f-133">복잡 한 배포 프로세스</span><span class="sxs-lookup"><span data-stu-id="bf67f-133">Complex deployment process</span></span>

<span data-ttu-id="bf67f-134">혼합 현실는 미국에 대 한 새로운 캔버스 이므로 특성에 따라 다양 한 디자인 반복과 평가판 및 오류가 수반 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="bf67f-135">Unity 및 Visual Studio와 같은 도구를 잘 모르는 디자이너의 경우 HoloLens에 추가 하는 것은 쉽지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="bf67f-136">일반적으로 장치에서 2D/3D 아트 워크를 확인 하려면 아래 프로세스를 진행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="bf67f-137">이는 아이디어 및 시나리오를 신속 하 게 반복 하는 디자이너에 게 큰 장벽 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="bf67f-138">![복잡 한 배포 프로세스](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="bf67f-139">*배포 프로세스*</span><span class="sxs-lookup"><span data-stu-id="bf67f-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="bf67f-140">HoloSketch를 사용한 간소화 된 프로세스</span><span class="sxs-lookup"><span data-stu-id="bf67f-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="bf67f-141">HoloSketch를 사용 하 여 개발 도구 및 장치 포털 페어링을 포함 하지 않고이 프로세스를 간소화 하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="bf67f-142">OneDrive를 사용 하 여 사용자는 2D/3D 자산을 HoloLens에 쉽게 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="bf67f-143">![HoloSketch를 사용한 간소화 된 프로세스](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="bf67f-144">*HoloSketch를 사용한 간소화 된 프로세스*</span><span class="sxs-lookup"><span data-stu-id="bf67f-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="bf67f-145">3 차원 디자인 고려 및 솔루션을 장려 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="bf67f-146">이 도구를 통해 디자이너는 진정한 3 차원 공간에서 솔루션을 탐색 하 고 2D로는 중단 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="bf67f-147">Hololens의 경우 배경이 실제 세계 이기 때문에 UI에 대 한 3D 배경을 만드는 방법에 대해 생각해 서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="bf67f-148">HoloSketch은 디자이너에서 Hololens의 3D 디자인을 쉽게 탐색 하는 방법을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="bf67f-149">시작</span><span class="sxs-lookup"><span data-stu-id="bf67f-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="bf67f-150">2D 이미지 (JPG/PNG)를 HoloSketch로 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="bf67f-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="bf67f-151">' Documents/HoloSketch ' OneDrive 폴더에 JPG/PNG 이미지를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="bf67f-152">HoloSketch의 OneDrive 메뉴에서 이미지를 선택 하 고 환경에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="bf67f-153">![2D 이미지 가져오기](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf67f-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="bf67f-154">*OneDrive를 통해 이미지 및 3D 개체 가져오기*</span><span class="sxs-lookup"><span data-stu-id="bf67f-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="bf67f-155">HoloSketch에 3D 개체를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="bf67f-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="bf67f-156">OneDrive 폴더에 업로드 하기 전에 다음 단계에 따라 3D 개체를 Unity 자산 번들로 패키지 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf67f-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="bf67f-157">이 프로세스를 사용 하 여 Maya, 시네마 4D 및 Microsoft Paint 3D와 같은 3D 소프트웨어에서 FBX/OBJ 파일을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="bf67f-158">현재 asset 번들 만들기는 Unity 버전 5.4.5 f1에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="bf67f-159">Unity 프로젝트 [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)를 다운로드 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="bf67f-160">이 Unity 프로젝트에는 번들 자산 생성에 대 한 스크립트가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="bf67f-161">새 GameObject을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="bf67f-162">내용에 따라 GameObject의 이름을로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="bf67f-163">검사기 패널에서 ' 구성 요소 추가 '를 클릭 하 고 ' Box Collider '를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![검사기 패널에서 ' 구성 요소 추가 '를 클릭 하 고 ' Box Collider '를 추가 합니다.](images/holosketch-10a-assetbundles-1000px.png)
   
   ![검사기 패널에서 ' 구성 요소 추가 '를 클릭 하 고 ' Box Collider '를 추가 #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="bf67f-166">3D FBX 파일을 프로젝트 패널로 끌어 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="bf67f-167">개체를 **새 GameObject**의 계층 패널로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![새 GameObject의 계층 패널로 개체를 끌어 옵니다.](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="bf67f-169">개체와 일치 하지 않는 경우 collider dimension을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="bf67f-170">개체를 **Z 축**표면으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-170">Rotate the object to face **Z-axis**.</span></span>

   ![개체와 일치 하지 않는 경우에는 collider dimension을 조정 합니다.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="bf67f-172">계층 패널에서 프로젝트 패널로 개체를 끌어 **prefab**.</span><span class="sxs-lookup"><span data-stu-id="bf67f-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="bf67f-173">검사기 패널의 아래쪽에서 드롭다운을 클릭 하 고 새 고유 이름을 만들고 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="bf67f-174">아래 예제에서는 AssetBundle 이름에 대해 ' brownchair '을 추가 하 고 할당 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![검사기 패널의 아래쪽에서 드롭다운을 클릭 하 고 새 고유 이름을 할당 합니다.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="bf67f-176">모델 개체에 대 한 미리 보기 이미지를 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="bf67f-177">![이미지를 프로젝트 패널로 끌고 개체에 사용 되는 이름을 할당 합니다.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="bf67f-178">Unity 프로젝트의 ' Asset ' 폴더 아래에 ' Assetbundles ' 이라는 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="bf67f-179">자산 메뉴에서 ' AssetBundles 빌드 '를 선택 하 여 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="bf67f-180">![자산 메뉴에서 ' AssetBundles 빌드 '를 선택 하 여 파일을 생성 합니다.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="bf67f-181">**생성 된 파일을 OneDrive의/Files/Documents/HoloSketch 폴더에 업로드 합니다.**</span><span class="sxs-lookup"><span data-stu-id="bf67f-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="bf67f-182">Asset_unique_name 파일만 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="bf67f-183">매니페스트 파일이 나 AssetBundles 파일을 업로드할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="bf67f-184">![파일/문서/HoloSketch/폴더](images/holosketch-onedriveupload-1000px.png)
![에 파일 추가 HoloSketch의 OneDrive 메뉴에 3d 개체가 추가 된 것을 볼 수 있습니다.](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf67f-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="bf67f-185">개체를 조작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="bf67f-185">How to manipulate the objects</span></span>

<span data-ttu-id="bf67f-186">HoloSketch는 3D 소프트웨어에서 널리 사용 되는 기존 인터페이스를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="bf67f-187">제스처와 마우스를 사용 하 여 개체를 이동, 회전, 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="bf67f-188">음성 또는 키보드를 사용 하 여 여러 모드 간을 빠르게 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="bf67f-189">개체 조작 모드</span><span class="sxs-lookup"><span data-stu-id="bf67f-189">Object manipulation modes</span></span>

<span data-ttu-id="bf67f-190">![개체를 조작 하는 방법](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="bf67f-191">*개체를 조작 하는 방법*</span><span class="sxs-lookup"><span data-stu-id="bf67f-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="bf67f-192">상황별 및 도구 벨트 메뉴</span><span class="sxs-lookup"><span data-stu-id="bf67f-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="bf67f-193">**상황에 맞는 메뉴 사용**</span><span class="sxs-lookup"><span data-stu-id="bf67f-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="bf67f-194">두 번 탭 하 여 상황에 맞는 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="bf67f-195">메뉴 항목:</span><span class="sxs-lookup"><span data-stu-id="bf67f-195">Menu items:</span></span>
* <span data-ttu-id="bf67f-196">**레이아웃 화면:** 이는 여러 개체를 레이아웃 하 고 그룹으로 관리할 수 있는 3D 그리드 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="bf67f-197">레이아웃 화면에서 두 번 탭 하 여 개체를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="bf67f-198">**기본형** Massing 연구에는 큐브, 구, 실린더 및 원추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="bf67f-199">**OneDrive:** OneDrive 메뉴를 열어 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="bf67f-200">**도움말:** 도움말 화면을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="bf67f-201">![상황에 맞는 메뉴](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="bf67f-202">*상황에 맞는 메뉴*</span><span class="sxs-lookup"><span data-stu-id="bf67f-202">*Contextual menu*</span></span>

<span data-ttu-id="bf67f-203">**도구 벨트 메뉴 사용**</span><span class="sxs-lookup"><span data-stu-id="bf67f-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="bf67f-204">이동, 회전, 크기 조정, 저장 및 로드 장면을 도구 벨트 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="bf67f-205">키보드, 제스처 및 음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="bf67f-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="bf67f-206">![키보드, 제스처 및 음성 명령](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bf67f-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="bf67f-207">*키보드, 제스처 및 음성 명령*</span><span class="sxs-lookup"><span data-stu-id="bf67f-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="bf67f-208">앱 다운로드</span><span class="sxs-lookup"><span data-stu-id="bf67f-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="bf67f-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Microsoft Store에서 무료로 HoloSketch 앱 다운로드 및 설치</a>
</span><span class="sxs-lookup"><span data-stu-id="bf67f-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="bf67f-210">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="bf67f-210">Known issues</span></span>
* <span data-ttu-id="bf67f-211">현재 자산 번들 만들기는 **Unity 버전 5.4.5 f1** 에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="bf67f-212">OneDrive의 데이터 양에 따라 OneDrive 콘텐츠를 로드 하는 동안 앱이 중지 된 것 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="bf67f-213">현재 저장 및 로드 기능은 기본 개체만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="bf67f-214">상황에 맞는 메뉴에서 텍스트, 소리, 비디오 및 사진 메뉴를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="bf67f-215">도구 벨트 메뉴의 재생 단추를 클릭 하면 조작 gizmo 그리려면 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="bf67f-216">스케치 공유</span><span class="sxs-lookup"><span data-stu-id="bf67f-216">Sharing your sketches</span></span>

<span data-ttu-id="bf67f-217">' 안녕하세요 Cortana, 녹화 시작/중지 ' 라고 말하여 HoloLens의 비디오 녹화 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="bf67f-218">볼륨 위쪽/아래쪽 키를 함께 사용 하 여 스케치를 그림으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf67f-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="bf67f-219">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="bf67f-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="bf67f-220"><b>동 Yoon 공원</b></span><span class="sxs-lookup"><span data-stu-id="bf67f-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="bf67f-221">UX 디자이너@Microsoft</span><span class="sxs-lookup"><span data-stu-id="bf67f-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="bf67f-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="bf67f-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="bf67f-223">개발@Microsoft</span><span class="sxs-lookup"><span data-stu-id="bf67f-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
