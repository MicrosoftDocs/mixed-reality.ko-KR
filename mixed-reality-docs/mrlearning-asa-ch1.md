---
title: MR Learning ASA 모듈 HoloLens 2 Azure 공간 앵커
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326893"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a><span data-ttu-id="12353-104">HoloLens 2의 Azure 공간 앵커를 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="12353-104">Getting Started with Azure Spatial Anchors on HoloLens 2</span></span>

<span data-ttu-id="12353-105">HoloLens 2 자습서의 두 번째 모듈을 시작 합니다!</span><span class="sxs-lookup"><span data-stu-id="12353-105">Welcome to the second module of the HoloLens 2 Tutorial!</span></span> <span data-ttu-id="12353-106">시작 하기 전에 해야 하는 모든의 합니다 [필수 구성 요소](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12353-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="12353-107">첫 번째 완료 하지 않은 경우 [기본 모듈입니다.](mrlearning-base.md) 아직 좋습니다를 먼저 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-107">If you have not completed the first, [base module](mrlearning-base.md) yet, we highly recommend that you complete that first.</span></span> <span data-ttu-id="12353-108">새 unity 프로젝트에서 시작 하는 경우의 새 프로젝트 만들기 단계를 수행 합니다 [기본 모듈입니다.](mrlearning-base.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-108">If you are starting from a new unity project, follow the new project creation steps in the [base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="12353-109">목표</span><span class="sxs-lookup"><span data-stu-id="12353-109">Objectives</span></span>

* <span data-ttu-id="12353-110">HoloLens 2를 사용 하 여 Azure 공간 앵커를 사용 하 여 개발 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="12353-110">Learn the fundamentals of developing with Azure Spatial Anchors with the HoloLens 2</span></span>

* <span data-ttu-id="12353-111">만들기, 업로드 및 다운로드 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="12353-111">Create, Upload, and Download Spatial Anchors</span></span>

  

## <a name="instructions"></a><span data-ttu-id="12353-112">지침</span><span class="sxs-lookup"><span data-stu-id="12353-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="12353-113">다운로드 및 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="12353-113">Downloading and Importing Assets</span></span>
<span data-ttu-id="12353-114">시작 하기 전에 다운로드 하 고 다음 자산을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-114">Before beginning, you must download and import the following assets:</span></span>

[<span data-ttu-id="12353-115">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="12353-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="12353-116">자산 팩 MR 자료 모듈</span><span class="sxs-lookup"><span data-stu-id="12353-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[<span data-ttu-id="12353-117">자산 팩 ASA 모듈</span><span class="sxs-lookup"><span data-stu-id="12353-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[<span data-ttu-id="12353-118">혼합 현실 도구 키트</span><span class="sxs-lookup"><span data-stu-id="12353-118">Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> <span data-ttu-id="12353-119">참고: Azure 공간 앵커, MR 자료 모듈 자산 팩에 대 한 자세한 지침은 6 단계 및 혼합 현실 도구 키트에 대 한 자세한 지침은 3-4 단계를 가져오는 방법에 대 한 자세한 지침은 5 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12353-119">Note: see step 5 for specific instructions on how to import the Azure Spatial Anchors, step 6 for specific instructions on the MR Base module Asset Pack, and steps 3-4 for specific instructions on the Mixed Reality Toolkit.</span></span>

1. <span data-ttu-id="12353-120">프로젝트에서 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12353-120">create a new scene in your project.</span></span> <span data-ttu-id="12353-121">장면 폴더를 마우스 오른쪽 단추로 클릭 하 고 "," 다음 장면 만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-121">Right click your scene folder, click "create," then scene.</span></span> <span data-ttu-id="12353-122">이름을 새 장면을 "ASALearningmodule."</span><span class="sxs-lookup"><span data-stu-id="12353-122">Name the new scene "ASALearningmodule."</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="12353-124">두 번 클릭 "ASALearningmodule" 새 장면을 함께 미리 정의 된 일부 항목이 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-124">Double click "ASALearningmodule" to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="12353-125">혼합된 현실 개발용 장면을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="12353-127">참고: 포함 된 팝업이 표시 됩니다, 그리고 "혼합된 현실 도구 키트에 대 한 파일을 선택 해야 합니다."</span><span class="sxs-lookup"><span data-stu-id="12353-127">Note: You will see a pop-up that says, "you must choose a file for the Mixed Reality Toolkit."</span></span> <span data-ttu-id="12353-128">"확인"는 다음 4 단계로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12353-128">Clicking "ok" will bring you to step 4.</span></span>

4. <span data-ttu-id="12353-129">혼합 현실 도구 키트에 대 한 파일을 선택 하는 경우 선택, "DefaultMixedRealityToolkitConfigurationProfile."</span><span class="sxs-lookup"><span data-stu-id="12353-129">When choosing a file for the Mixed Reality Toolkit, select, "DefaultMixedRealityToolkitConfigurationProfile."</span></span>

   > <span data-ttu-id="12353-130">참고: 사용자 고유의 구성 프로필 자유롭게 사용 하는 대신에 있으면 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-130">Note: If you have your own configuration profile feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="12353-132">이제 장면 혼합된 현실 용 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12353-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="12353-133">장면 저장 합니다 (컨트롤을 사용 하 여이 작업을 수행할 / 명령 + S, 또는 파일을 클릭 한 다음 후 클릭에 저장).</span><span class="sxs-lookup"><span data-stu-id="12353-133">Make sure you save your scene (do this with either control/command+S, or click on file, then click on save).</span></span> 

5. <span data-ttu-id="12353-134">가져오기의 [Azure 공간 앵커](https://github.com/azure/azure-spatial-anchors-samples/releases)합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="12353-135">공간 앵커를 사용 하려면이 자산을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="12353-136">따라서 위에 있는 링크를 클릭 하 고 마우스 오른쪽 단추로 클릭 "AzureSpatialAnchors.unitypackage."</span><span class="sxs-lookup"><span data-stu-id="12353-136">So, click on the link above and right click on "AzureSpatialAnchors.unitypackage."</span></span> <span data-ttu-id="12353-137">컴퓨터에 클릭 "다른 이름으로 대상"에 저장 하 고 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-137">Click on "save target as" and save it to your computer.</span></span> 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   <span data-ttu-id="12353-139">그런 다음 저장 된 후, unity로 다시 돌아가서, 클릭 "자산을" "패키지 가져오기," 아래로 이동 "사용자 지정 패키지..." 클릭 컴퓨터 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="12353-139">Then, after it's saved, go back into unity, click "assets," go down to "import package," then click "custom package..." Your computer files will open up.</span></span> <span data-ttu-id="12353-140">한 번은 수행, Azure 공간 앵커 패키지를 저장 하는 위치를 찾아 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-140">Once they do, find where you saved the Azure Spatial Anchors package and select it.</span></span> <span data-ttu-id="12353-141">"열기"를 클릭 합니다</span><span class="sxs-lookup"><span data-stu-id="12353-141">Then click "open."</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   <span data-ttu-id="12353-143">이제 팝업 도구 및 설정, 가져오기 내용을 라는 목록이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12353-143">Now there will be a popup giving a list of tools and settings, asking you what to import.</span></span> <span data-ttu-id="12353-144">선택 ***모든*** 사용할 수 있는 옵션 가져오기를 클릭 합니다 "."</span><span class="sxs-lookup"><span data-stu-id="12353-144">Select ***all*** of the options available, then click "import."</span></span>

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > <span data-ttu-id="12353-146">참고:이 가져오려면 몇 분 정도 걸립니다 정도가 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12353-146">note: it will take a few minutes to import, so please be patient.</span></span> 

   6. <span data-ttu-id="12353-147">가져오기 [MR 자료 모듈 자산 팩](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) 다음입니다.</span><span class="sxs-lookup"><span data-stu-id="12353-147">Import [MR Base module Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) next.</span></span> <span data-ttu-id="12353-148">5 단계와 마찬가지로 위의 링크를 클릭, 한 다음 마우스 오른쪽 단추로 클릭 "BasemoduleAssetsV1 1.unitypackage" 컴퓨터에 "다른 이름으로 대상"에 저장 하 고 저장을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-148">Much like step 5, click the link above, then right click "BasemoduleAssetsV1 1.unitypackage" and click "save target as" and save it to your computer.</span></span>

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > <span data-ttu-id="12353-150">팁:  쉽게 찾고 액세스할 수 있도록 동일한 폴더에 이러한 모든 자산을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-150">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="12353-151">간단 하 고 구성 된 모든 보존 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12353-151">It will keep everything nice and organized!</span></span>

   <span data-ttu-id="12353-152">Unity로 다시 이동 5 단계와 마찬가지로 "자산", "패키지 가져오기"를 마우스로 클릭 한 다음 "사용자 지정 패키지..." 선택 및 기본 모듈 자산 팩을 저장 위치를 이동 하므로 컴퓨터 파일을 다시 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12353-152">Just like step 5, go back in to unity, click "assets," hover over "import package" then click "custom package..." Your computer files should appear again, so go to where you stored the Base module Asset Pack and select it.</span></span> <span data-ttu-id="12353-153">"열기"를 클릭 합니다</span><span class="sxs-lookup"><span data-stu-id="12353-153">Then click "open."</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > <span data-ttu-id="12353-155">참고: 나중에이 모듈에에서 필요한 자세한 자산 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-155">Note: there may be more assets needed later in this module.</span></span> <span data-ttu-id="12353-156">이 시점에서 언급 된 모든 자산을 가져오려면 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-156">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="12353-157">ASA 모듈을 동일한 접근 방식을 사용 하 여 이전 패키지를 가져올 때 팩을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12353-157">Import the ASA module Pack using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="12353-158">장면 구성</span><span class="sxs-lookup"><span data-stu-id="12353-158">Configuring your scene</span></span>

<span data-ttu-id="12353-159">이 섹션에서는 추가 될 예정 prefabs 및 스크립트를 만드는 일련의 로컬 앵커와 Azure 공간 앵커 응용 프로그램에서 작동 하는 방법의 기본 개념을 보여 주는 단추 장면에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-159">In this section, we will be adding prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

7. <span data-ttu-id="12353-160">"프로젝트" 탭 "자산" 폴더 아래에서 "ASAmoduleAssets." 클릭</span><span class="sxs-lookup"><span data-stu-id="12353-160">In the "project" tab, underneath the "assets" folder, click on "ASAmoduleAssets."</span></span> <span data-ttu-id="12353-161">한 번 선택한 2 prefabs, "ButtonParent" 및 "ParentAnchor."를 보면</span><span class="sxs-lookup"><span data-stu-id="12353-161">Once selected you will see 2 prefabs, "ButtonParent" and "ParentAnchor."</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. <span data-ttu-id="12353-163">장면에 모두를 prefabs를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="12353-163">Drag both of the prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. <span data-ttu-id="12353-165">두 번 클릭 하 여 선택 부모 앵커입니다.</span><span class="sxs-lookup"><span data-stu-id="12353-165">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="12353-166">장면 전체를 참조 하십시오. 필요에 따라 장면을 조정 하므로을 보기를 조정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-166">You may need to adjust your view to see the entire scene, so adjust your scene as needed.</span></span>

    <span data-ttu-id="12353-167">ParentAnchor prefab 숙지 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-167">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="12353-168">현재 "ParentAnchor" 이라는 게임 개체는 데모용으로 색이 지정 된 큐브.</span><span class="sxs-lookup"><span data-stu-id="12353-168">Currently, the game object named "ParentAnchor" is a colored cube, for demonstration purposes.</span></span> <span data-ttu-id="12353-169">결국 큐브 숨기기 하 고는 ParentAnchor의 자식으로 콘텐츠를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-169">Eventually, we will hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="12353-170">이 prefab AzureSpatialAnchorsDemoWrapper.cs 스크립트 (ASA SDK 포함) 및 ParentAnchor 개체 ASAmoduleScript.cs 스크립트 (이 모듈의 일부로 포함)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-170">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK) and the ASAmoduleScript.cs script (included as part of this module) to the ParentAnchor object.</span></span> 

10. <span data-ttu-id="12353-171">단추를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-171">Configure Buttons.</span></span> <span data-ttu-id="12353-172">ParentAnchor prefab 아래 여러 개의 레이블이 지정 된 단추를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-172">Under the ParentAnchor prefab, you will notice several labeled buttons.</span></span> <span data-ttu-id="12353-173">이러한 단추는 MRTK PressableButton prefabs에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="12353-173">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="12353-174">Pressable 단추를 만드는 방법에 자세히 알아보려면 합니다 [기본 모듈입니다.](mrlearning-base-ch2.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-174">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="12353-175">각 단추에 대 한 키를 누르거나 아래 목록에 따라 단추를 선택 하는 경우 트리거되는 이벤트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-175">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="12353-176">"StartAzureSession" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12353-176">For the Button named "StartAzureSession", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="12353-177">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StartAzureSession() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-177">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="12353-181">"StopAzureSession" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12353-181">For the Button named "StopAzureSession", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="12353-182">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StopAzureSession() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-182">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="12353-183">"CreateAnchor" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12353-183">For the Button named "CreateAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="12353-184">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 CreateAzureAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-184">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="12353-185">"시작 확인에 대 한 앵커" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12353-185">For the Button named "Start Looking For Anchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="12353-186">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 FindAzureAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-186">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="12353-187">"DeleteAzureAnchor" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12353-187">For the Button named "DeleteAzureAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="12353-188">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 DeleteAzureAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-188">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="12353-189">지정 된 "로컬 앵커 삭제" 단추 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12353-189">For the Button named "Delete Local Anchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="12353-190">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 RemoveLocalAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-190">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="12353-191">빌드 및 기본 응용 프로그램을 보여 줍니다</span><span class="sxs-lookup"><span data-stu-id="12353-191">Build and Demonstrate Base Application</span></span>

<span data-ttu-id="12353-192">장면을 Azure 공간 앵커의 기본 사항을 설명 하기 위해 구성 했으므로 작성 하 고 Azure 공간 앵커의 기본 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="12353-192">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="12353-193">이전 섹션의 Build Settings 창을 닫은 경우 File>Build Settings로 이동하여 Build Settings 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12353-193">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="12353-194">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="12353-194">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="12353-195">“Add Open Scenes” 단추를 클릭하여 사용하려는 장면이 "Scenes in Build" 목록에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-195">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="12353-196">Build 단추를 눌러 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-196">Press the Build button to begin the build process.</span></span>
    <span data-ttu-id="12353-197">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="12353-197">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="12353-198">애플리케이션의 새 폴더를 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-198">Create and name a new folder for your application.</span></span> <span data-ttu-id="12353-199">아래 이미지에서는 애플리케이션을 포함할 폴더가 이름 "App"을 사용하여 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-199">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="12353-200">“Select Folder”를 클릭하여 새로 만든 폴더로 빌드를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-200">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="12353-201">빌드가 완료된 후에 Unity에서 "Build Settings" 창을 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-201">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 
    <span data-ttu-id="12353-202">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="12353-202">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="12353-203">참고: 빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-203">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="12353-204">"Error: CS0246 = "XX"를 찾을 수 없는 tyoe 또는 네임 스페이스 이름 (사용 하는 누락 된 지시문 또는 어셈블리 참조가?) "를 설치 해야 할 수 있습니다 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="12353-204">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="12353-205">빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12353-205">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="12353-206">"MixedRealityBase.sln" 솔루션(또는 프로젝트에 다른 이름을 사용한 경우 해당 이름)을 두 번 클릭하여 Visual Studio에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12353-206">Double click on the “MixedRealityBase.sln” solution (or the corresponding name, if you used an alternative name for your project) to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="12353-207">참고: 새로 만든 폴더(즉, 이전 단계의 명명 규칙을 따르는 경우 "App" 폴더)를 열어야 합니다. 이 폴더 밖에 비슷한 이름의 .sln 파일이 있으므로 build 폴더 내의 .sln 파일과 혼동하지 않도록 주의합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-207">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > <span data-ttu-id="12353-209">참고: 새 구성 요소를 설치를 묻는 메시지가 나타나면 visual studio 잠시 모든 필수 구성 요소가 설치 되어 있는지 확인 하려면에서 구체적 ["Tools 설치" 페이지](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="12353-209">Note: If visual studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="12353-210">USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-210">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="12353-211">이러한 단원 지침 HoloLens 2 장치를 사용 하 여 테스트를 배포할 수 있다고 가정에서 수도 있습니다를 배포 하는 [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md) 를 만들도록 선택할는 [테스트용 로드 앱 패키지](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="12353-211">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="12353-212">디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-212">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="12353-213">이번에 처음으로 HoloLens 2에 배포하는 경우리면 Visual Studio에서 pin 사용하여 HoloLens 2에 연결하도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-213">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="12353-214">개발자 모드를 사용하도록 설정하거나 Visual Studio와 페어링해야 하는 경우 [다음 지침](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="12353-214">Please follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="12353-215">"Release" 구성과 "ARM" 아키텍처를 선택하여 HoloLens 2로 빌드하기 위해 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-215">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>
    <span data-ttu-id="12353-216">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="12353-216">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
    
9. <span data-ttu-id="12353-217">마지막 단계는 디버그를 선택 하 여 장치를 빌드할 수 > 디버깅 하지 않고 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-217">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="12353-218">"디버깅하지 않고 시작"을 선택하면 빌드 성공 시 애플리케이션이 디바이스에서 즉시 시작되지만, Visual Studio에 디버깅 정보가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-218">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="12353-219">따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-219">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="12353-220">빌드>솔루션 배포를 선택하여 디바이스로 배포할 때 애플리케이션이 자동으로 시작되지 않도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-220">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
    <span data-ttu-id="12353-221">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="12353-221">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
    
10. <span data-ttu-id="12353-222">응용 프로그램이 장치에서 실행 중이면 따르세요를 화면에 나타나는 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="12353-222">When the application is running on your device, please follow the on-screen instructions.</span></span> <span data-ttu-id="12353-223">아래 단계에 해당 되는 장면 단추를 누르십시오.</span><span class="sxs-lookup"><span data-stu-id="12353-223">Please press the scene buttons corresponding to the Steps below.</span></span>
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="12353-225">Azure 공간 앵커 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-225">Start the Azure spatial anchors session.</span></span>
    
    2. <span data-ttu-id="12353-226">큐브를 다른 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-226">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="12353-227">큐브의 위치의 Azure 공간 앵커를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-227">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="12353-228">Azure 공간 앵커 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-228">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="12353-229">큐브에 큐브를 이동할 수 있도록 로컬 앵커를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-229">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    6. <span data-ttu-id="12353-230">큐브의 다른 위치를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-230">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="12353-231">Azure 공간 앵커 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-231">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="12353-232">Azure 공간 앵커를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-232">Find Azure spatial anchors.</span></span>
    <span data-ttu-id="12353-233">(큐브는 원래 위치로 다시 이동 해야 하는 이제 배치 앵커를 만들 때).</span><span class="sxs-lookup"><span data-stu-id="12353-233">(now cube should go back to the original place you put it when you created the anchor).</span></span>
    9. <span data-ttu-id="12353-234">Azure 공간 앵커를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-234">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="12353-235">Azure 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-235">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="12353-236">환경을 고정</span><span class="sxs-lookup"><span data-stu-id="12353-236">Anchoring an experience</span></span>

<span data-ttu-id="12353-237">이전 섹션에서는 Azure 공간 앵커의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-237">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="12353-238">큐브를 나타내는 연결 된 앵커를 사용 하 여 부모 게임 개체를 시각화 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-238">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="12353-239">이 섹션에서는 있습니다 wiill ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="12353-239">In this section, you wiill learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="12353-240">이 예제에서는 중 생성 된 음력 모듈 어셈블리 데모 앱 사용 [기본 모듈 6 단원](mrlearning-base-ch6.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-240">For this example, we will use the Lunar module Assembly demo app that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="12353-241">음력 모듈 어셈블리 전체 prefab 검색 하 고 끌어온 사용자 계층 구조의 AnchorParent gameobject 자식인 아래 이미지에 표시 된 대로 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="12353-241">Search for the Lunar module Assembly Complete prefab and drag it into your heirarchy as a child of the AnchorParent gameobject, as shown in the image below.</span></span>

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="12353-243">아래 이미지 에서처럼 모듈 어셈블리 환경을 큐브에 노출 계속 하는 방식으로 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-243">Position the module assembly experience in such a way that the cube is still exposed, as shown in the image below.</span></span> <span data-ttu-id="12353-244">응용 프로그램에서 사용자가 큐브를 이동 하 여 전체 환경 위치 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-244">In the application, users may reposition the entire experience by moving the cube.</span></span> 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > <span data-ttu-id="12353-246">참고: 다양 한 경험을 둘러싸는 경계 상자를 설정/해제, 위치 및 회전 gizmo 사용 재배치 개체 (예: 큐브가이 단계에서 사용)를 사용 하는 단추 사용을 비롯 하 여 환경을 위치에 대 한 사용자 경험 흐름 및 기타 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="12353-246">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="12353-247">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-247">Congratulations</span></span>
<span data-ttu-id="12353-248">이 단원에서는 Azure 공간 앵커의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-248">In this Lesson, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="12353-249">이 단원에서는 시작 하 고 Azure 세션을 중지 하는 데 필요한 다양 한 단계를 탐색 및 만들기, 업로드 및 단일 장치에서 azure 앵커를 다운로드할 수 있도록 하는 여러 단추를 사용 하 여 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="12353-249">This Lesson provided you with several buttons allowing you to explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="12353-250">다음 단원에서는 응용 프로그램 다시 시작 된 후에, 검색에 대 한 여 HoloLens 2 Azure 앵커 Id를 저장 하는 방법을 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="12353-250">In the next Lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="12353-251">시리즈 중 공간 맞춤을 위해 여러 장치 간에 앵커 Id를 전송 하는 방법을 알아볼을 최종적으로 세션 (곧 모듈을 공유 하는 일환으로 제공 합니다.)를 공유 하는 다중 사용자에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="12353-251">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and eventually learn about multi-user shared sessions (forthcoming as part of sharing module.)</span></span>

[<span data-ttu-id="12353-252">다음 단원: ASA 단원 2</span><span class="sxs-lookup"><span data-stu-id="12353-252">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)

