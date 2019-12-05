---
title: Azure 공간 앵커 자습서-1. Azure 공간 앵커 시작
description: 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: b615f1135f5d2947f8f718e080ef45a3c1fcc576
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830843"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="19789-105">1. Azure 공간 앵커 시작</span><span class="sxs-lookup"><span data-stu-id="19789-105">1. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="19789-106">HoloLens 2 자습서의 두 번째 모듈을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-106">Welcome to the second module of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="19789-107">시작 하기 전에 모든 [필수 구성 요소](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) 를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-107">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="19789-108">첫 번째 [기본 모듈](mrlearning-base.md) 을 아직 완료 하지 않은 경우 해당 모듈을 먼저 완료 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-108">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="19789-109">새 Unity 프로젝트에서 시작 하는 경우 [기본 모듈](mrlearning-base.md)의 새 프로젝트 만들기 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="19789-109">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="19789-110">목표</span><span class="sxs-lookup"><span data-stu-id="19789-110">Objectives</span></span>

* <span data-ttu-id="19789-111">HoloLens 2를 사용 하 여 Azure 공간 앵커로 개발 하는 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="19789-111">Learn the fundamentals of developing with Azure Spatial Anchors with HoloLens 2</span></span>

* <span data-ttu-id="19789-112">공간 앵커 만들기, 업로드 및 다운로드</span><span class="sxs-lookup"><span data-stu-id="19789-112">Create, upload, and download spatial anchors</span></span>

## <a name="instructions"></a><span data-ttu-id="19789-113">지침</span><span class="sxs-lookup"><span data-stu-id="19789-113">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="19789-114">자산 다운로드 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="19789-114">Downloading and importing assets</span></span>
<span data-ttu-id="19789-115">시작 하기 전에 다음 자산을 다운로드 하 여 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="19789-115">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="19789-116">Azure 공간 앵커 v 1.1.0</span><span class="sxs-lookup"><span data-stu-id="19789-116">Azure Spatial Anchors v1.1.0</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[<span data-ttu-id="19789-117">HoloLens2을 시작 했습니다. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="19789-117">Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[<span data-ttu-id="19789-118">HoloLens2. AzureSpatialAnchor 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="19789-118">Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[<span data-ttu-id="19789-119">Mixed Reality Toolkit Foundation 패키지 2.1.0</span><span class="sxs-lookup"><span data-stu-id="19789-119">Mixed Reality Toolkit  Foundation Package 2.1.0</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. <span data-ttu-id="19789-120">프로젝트에 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19789-120">Create a new scene in your project.</span></span> <span data-ttu-id="19789-121">장면 폴더를 마우스 오른쪽 단추로 클릭 하 고 만들기, 장면을 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-121">Right-click your Scene folder, click Create, then Scene.</span></span> <span data-ttu-id="19789-122">새 장면의 이름을 "ASALearningModule"로 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-122">Name the new scene as "ASALearningModule".</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="19789-124">"ASALearningmodule" 장면을 두 번 클릭 하 여 미리 정의 된 항목이 새 장면에 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-124">Double-click "ASALearningmodule" scene to see some pre-defined items to appear along with the new scene.</span></span> 
3. <span data-ttu-id="19789-125">혼합 현실 개발을 위한 장면을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="19789-127">참고: [Mixed Reality Toolkit에 대 한 프로필](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)을 선택 하는 팝업 대화 상자가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-127">Note: You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="19789-128">*DefaultHoloLens2ConfigurationProfile* 라는 프로필을 두 번 클릭 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-128">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

4. <span data-ttu-id="19789-129">MRTK에 대 한 파일을 선택 하는 경우 DefaultMixedRealityToolkitConfigurationProfile를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-129">When choosing a file for the MRTK, select DefaultMixedRealityToolkitConfigurationProfile.</span></span>

> <span data-ttu-id="19789-130">참고: 사용자 고유의 구성 프로필이 있는 경우 대신 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="19789-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="19789-132">이제는 혼합 현실에 대해 장면이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19789-132">The scene is now configured for mixed reality.</span></span> <span data-ttu-id="19789-133">장면을 저장 해야 합니다 .이 작업은 제어/명령 + S를 사용 하거나 파일을 클릭 한 다음 저장을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-133">Make sure you save your scene (do this with either control/command+S or click on file, followed by Save).</span></span> 

5. <span data-ttu-id="19789-134">1 단계에서 다운로드 한 [Azure 공간 앵커 v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="19789-134">Import the [Azure Spatial Anchors v1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity package that we downloaded in step 1.</span></span> <span data-ttu-id="19789-135">이렇게 하려면 자산을 클릭 하 고, 패키지 가져오기로 이동한 다음, 사용자 지정 패키지 ...를 클릭 합니다. 컴퓨터 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="19789-135">For that, click Assets, go down to Import Package and then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="19789-136">이렇게 하면 Azure 공간 앵커 패키지를 저장 한 위치를 찾아서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-136">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="19789-137">그런 다음 열기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-137">Then click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

<span data-ttu-id="19789-139">도구 및 설정 목록을 제공 하 고 가져올 항목을 요청 하는 팝업이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="19789-139">A pop-up appears, providing a list of tools and settings and asking you what to import.</span></span> <span data-ttu-id="19789-140">사용할 수 있는 옵션을 ***모두*** 선택 하 고 가져오기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-140">Select ***all*** of the options available, then click Import.</span></span>

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> <span data-ttu-id="19789-142">참고: 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-142">Note: Be patient, it will take a few minutes to import.</span></span> 

6. <span data-ttu-id="19789-143">HoloLens2를 가져옵니다. [2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) Next를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-143">Import [Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) next.</span></span> <span data-ttu-id="19789-144">5 단계와 마찬가지로 Unity로 돌아가서 자산을 클릭 하 고 가져오기 패키지를 마우스로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="19789-144">Much like Step 5, go back into Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="19789-145">사용자 지정 패키지 ...를 클릭 합니다. 컴퓨터 파일이 다시 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19789-145">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="19789-146">기본 모듈 자산 팩을 저장 한 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-146">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="19789-147">선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-147">and select it.</span></span> <span data-ttu-id="19789-148">열기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-148">Click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> <span data-ttu-id="19789-150">참고:이 모듈의 뒷부분에 더 많은 자산이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-150">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="19789-151">이 시점에서 언급 된 자산을 가져오려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-151">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="19789-152">이전 패키지를 가져오는 것과 동일한 단계를 사용 하 여 [global.asa 모듈 팩 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="19789-152">Import the [ASA module pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage), using the same steps as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="19789-153">장면 구성</span><span class="sxs-lookup"><span data-stu-id="19789-153">Configuring your scene</span></span>

<span data-ttu-id="19789-154">이 섹션에서는 prefabs 및 스크립트를 장면에 추가 하 여 로컬 앵커와 Azure 공간 앵커가 응용 프로그램에서 작동 하는 방식에 대 한 기본 사항을 보여 주는 일련의 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19789-154">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

8. <span data-ttu-id="19789-155">프로젝트 탭의 자산 폴더 아래에서 ASAmoduleAssets을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-155">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="19789-156">이 항목을 선택 하면 두 prefabs: ButtonParent 및 ParentAnchor가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19789-156">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. <span data-ttu-id="19789-158">두 prefabs를 장면으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-158">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

<span data-ttu-id="19789-160">참고: ButtonParent를 장면에 추가 하면 TMP 자산을 가져올지 묻는 팝업이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19789-160">Note: After adding the ButtonParent into the scene, a pop-up will appear asking you to import TMP assets.</span></span> <span data-ttu-id="19789-161">"TMP Essentials"를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="19789-161">Import the "TMP Essentials".</span></span> <span data-ttu-id="19789-162">그러면 장면에 많은 글꼴 텍스트가 표시 되 면 ButtonParent 개체를 삭제 하 고 ASAmoduleAssets 폴더에서 다시 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-162">After this, If you see any large font text in the scene, delete the ButtonParent object and add it again from the ASAmoduleAssets folder.</span></span>

<span data-ttu-id="19789-163">참고: HoloLens에서 디버그 로그를 확인 하려는 경우 ASAModuleAssets 폴더에서 DebugWindow prefab를 장면으로 끌어서 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-163">Note: If you want to check the debug logs in the HoloLens, you can drag and drop the DebugWindow prefab from ASAModuleAssets folder into the scene.</span></span> <span data-ttu-id="19789-164">DebugWindow inspector 패널에서 DebugWindowMessaging 스크립트를 연결 하 고 디버그 창 사용 옵션을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-164">Attach the DebugWindowMessaging script in the DebugWindow inspector panel and enable the Debug Window Enabled option.</span></span> <span data-ttu-id="19789-165">그런 다음 DebugWindow prefab를 Debugwindow empty 필드로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-165">After that, drag  and drop the DebugWindow prefab into the DebugText empty field.</span></span> <span data-ttu-id="19789-166">적절 한 경우에는 DebugWindow 위치를 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-166">You can also adjust the DebugWindow position wherever appropriate for you.</span></span>

10. <span data-ttu-id="19789-167">장면을 확대 하려면 계층의 부모 앵커를 두 번 클릭 하 고 보기를 조정 하 여 필요에 따라 전체 장면을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-167">In order to zoom in to the scene, double-click the parent anchor in the hierarchy and adjust your view to see the entire scene as needed.</span></span> <span data-ttu-id="19789-168">현재 ParentAnchor는 데모용 으로만 사용 되는 색이 지정 된 큐브입니다.</span><span class="sxs-lookup"><span data-stu-id="19789-168">Currently, ParentAnchor is a colored cube used only for demonstration purposes.</span></span> <span data-ttu-id="19789-169">결국 큐브를 숨기고 콘텐츠를 ParentAnchor의 자식으로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-169">Eventually, we will hide the cube and place our content as a child of the ParentAnchor.</span></span> 

11. <span data-ttu-id="19789-170">이제 장면을 작동 하기 위한 단추를 구성 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-170">Now let's configure the buttons for operating the scene.</span></span> <span data-ttu-id="19789-171">이를 위해 ButtonParent prefab를 확장 하면 MRTK의 기능 prefabs에서 생성 되는 레이블이 지정 된 단추가 몇 개 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19789-171">For that, expand the ButtonParent prefab and you'll notice several labeled buttons, which are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="19789-172">[기본 모듈](mrlearning-base-ch2.md)에서 보도를 만드는 방법에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="19789-172">Learn more about how to create PressableButton from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="19789-173">이러한 단추가 작동 하려면 사용자가 개별 단추를 누르거나 선택할 때 트리거되는 이벤트를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-173">For these buttons to operate, you need to add an event which will be triggered when the user presses or selects the individual buttons.</span></span> 

- <span data-ttu-id="19789-174">StartAzureSession 라는 단추에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19789-174">For the Button named StartAzureSession, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="19789-175">다음 스크린샷에 표시 된 것 처럼 ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StartAzureSession () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-175">Drag the ParentAnchor object into the empty field and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component as shown in the below screenshot.</span></span>
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="19789-179">StopAzureSession 이라는 단추에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19789-179">For the Button named StopAzureSession, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="19789-180">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StopAzureSession () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-180">Drag the ParentAnchor object into the empty field and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="19789-181">CreateAnchor 라는 단추에 대해 단추 누름 이벤트 트리거 뿐만 아니라 Click Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19789-181">For the Button named CreateAnchor, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="19789-182">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 CreateAzureAnchor () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-182">Drag the ParentAnchor object into the empty field and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>  <span data-ttu-id="19789-183">**이후에 ParentAnchor를 다시 다음 빈 "게임 개체" 필드로 끌어 옵니다.**</span><span class="sxs-lookup"><span data-stu-id="19789-183">**After this, drag the ParentAnchor again into the next empty "Game Object" field.**</span></span>

- <span data-ttu-id="19789-184">앵커를 찾는 시작 단추에 대해 Click Click 이벤트 트리거와 함께 단추 누름 이라는 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19789-184">For the Button named Start Looking For Anchor, create a new event under the Button Press" event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="19789-185">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 FindAzureAnchor () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-185">Drag the ParentAnchor object into the empty field and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="19789-186">DeleteAzureAnchor 라는 단추에 대해 단추 누름 이벤트 트리거 뿐만 아니라 Click Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19789-186">For the Button named DeleteAzureAnchor, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="19789-187">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 DeleteAzureAnchor () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-187">Drag the ParentAnchor object into the empty field and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>  

- <span data-ttu-id="19789-188">로컬 앵커 삭제 단추에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19789-188">For the Button named Delete Local Anchor, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="19789-189">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 RemoveLocalAnchor () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-189">Drag the ParentAnchor object into the empty field and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span> <span data-ttu-id="19789-190">**이후에 ParentAnchor 개체를 다시 다음 빈 "게임 개체" 필드로 끌어 옵니다.**</span><span class="sxs-lookup"><span data-stu-id="19789-190">**After this, drag the ParentAnchor object again into the next empty "Game Object" field.**</span></span>

12. <span data-ttu-id="19789-191">Azure 공간 앵커를 설정 하려면 자산 폴더의 AzureSpatialAnchorsPlugin 폴더로 이동 하 고 예제-> 리소스-> AzureSpatialAnchorsDemoConfig 파일로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-191">To set up Azure spatial anchors, go to the AzureSpatialAnchorsPlugin folder in the assets folder and navigate to Examples -> Resources->AzureSpatialAnchorsDemoConfig file.</span></span> <span data-ttu-id="19789-192">검사기 패널에서 이전에 만든 Azure 계정 ID 및 계정 키를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-192">In the inspector panel, add the Azure Account ID and Account Key that you created earlier.</span></span> <span data-ttu-id="19789-193">만든 적이 없거나 아직 없는 경우 [필수 구성 요소](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="19789-193">If you haven't created them or don't have the them, please follow the [Prerequisites](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span></span> 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="19789-195">기본 응용 프로그램 빌드 및 시연</span><span class="sxs-lookup"><span data-stu-id="19789-195">Build and demonstrate Base Application</span></span>

<span data-ttu-id="19789-196">이제 Azure 공간 앵커의 기본 사항을 보여 주기 위해 장면을 구성 했으므로 Azure 공간 앵커의 기본 동작을 작성 하 고 시연 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19789-196">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="19789-197">파일 > 빌드 설정으로 이동 하 여 빌드 설정 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="19789-197">Open the build settings window again, by going to File>Build Settings.</span></span>
    <span data-ttu-id="19789-198">![mrlearning-ch1-3-1 단계](images/mrlearning-asa-ch1-3-step1.jpg)</span><span class="sxs-lookup"><span data-stu-id="19789-198">![mrlearning-asa-ch1-3-step1](images/mrlearning-asa-ch1-3-step1.jpg)</span></span>
2. <span data-ttu-id="19789-199">열려 있는 장면 추가 단추를 클릭 하 여 시도 하려는 장면이 빌드 목록의 장면에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-199">Ensure the scene you want to try is in the Scenes in the build list, by clicking on the Add Open Scenes button.</span></span>
3. <span data-ttu-id="19789-200">플랫폼이 유니버설 Windows 플랫폼로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-200">Verify the Platform is set to the Universal Windows Platform.</span></span> <span data-ttu-id="19789-201">그렇지 않은 경우 동일한로 설정 하세요.</span><span class="sxs-lookup"><span data-stu-id="19789-201">If not, please set it to the same.</span></span>
4. <span data-ttu-id="19789-202">플레이어 설정 단추를 누르고 게시 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-202">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="19789-203">기능 아래에서 인터넷, 인터넷 클라이언트 서버, 개인 네트워크 클라이언트 서버, 이동식 저장소, 웹캠, 마이크 및 공간 인식을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-203">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Removable Storage, Webcam, Microphone and Spatial Perception.</span></span>
5. <span data-ttu-id="19789-204">동일한 플레이어 설정에서 XR 설정으로 이동 하 고에서 지원 되는 가상 현실를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-204">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>
6. <span data-ttu-id="19789-205">Build 단추를 눌러 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-205">Press the Build button to begin the build process.</span></span>
   <span data-ttu-id="19789-206">![mrlearning-ch1-3-6 단계](images/mrlearning-asa-ch1-3-step6.jpg)</span><span class="sxs-lookup"><span data-stu-id="19789-206">![mrlearning-asa-ch1-3-step6](images/mrlearning-asa-ch1-3-step6.jpg)</span></span>
7. <span data-ttu-id="19789-207">애플리케이션의 새 폴더를 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-207">Create and name a new folder for your application.</span></span> <span data-ttu-id="19789-208">아래 이미지에서 응용 프로그램을 포함 하기 위해 이름이 앱 인 폴더를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-208">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="19789-209">폴더 선택을 클릭 하 여 새로 만든 폴더로 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-209">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="19789-210">빌드가 완료 되 면 Unity에서 빌드 설정 "창을 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-210">After the build has completed, you may close the Build Setting" window in Unity.</span></span>

    ![mrlearning-ch1-3-step7](images/mrlearning-asa-ch1-3-step7.jpg)

    > <span data-ttu-id="19789-212">참고: 빌드가 실패 하는 경우 다시 빌드를 시도 하거나 Unity를 다시 시작 하 고 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-212">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="19789-213">"Error: CS0246 =" XX "형식 또는 네임 스페이스 이름을 찾을 수 없습니다. (using 지시문 또는 어셈블리 참조가 있는지 여부)와 같은 오류가 표시 되는 경우 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) 를 설치 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-213">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?), you might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span> 


8. <span data-ttu-id="19789-214">빌드가 성공적으로 수행 된 후에도 아래와 같이 몇 가지 오류가 발생할 수 있습니다. 그러나 빌드가 성공한 경우이를 무시 하 고 다음 단계를 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-214">Even after a successful build, you might get some errors as shown below, but if the build is successful you can ignore them and proceed with next steps.</span></span>

    ![mrlearning-ch1-3-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. <span data-ttu-id="19789-216">빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="19789-216">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="19789-217">프로젝트에 대 한 대체 이름을 사용 하 여 Visual Studio에서 솔루션 파일을 여는 경우 "MixedRealityBase" 솔루션이 나 해당 이름을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-217">Double-click on the“MixedRealityBase.sln" solution or the corresponding name, if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

    > <span data-ttu-id="19789-218">참고: 앞의 단계에서 명명 규칙을 준수 하는 경우 새로 만든 폴더 (즉, 응용 프로그램 폴더)를 열어야 합니다 .이 폴더에는 빌드 폴더 내에 있는 .sln 파일과 혼동 하지 않는 유사한 이름의 .sln 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-218">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps, as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span>

    ![mrlearning-ch1-3-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > <span data-ttu-id="19789-220">참고: Visual Studio에서 새 구성 요소를 설치 하도록 요청 하는 경우 모든 필수 구성 요소를 ["도구 설치" 페이지](install-the-tools.md) 에 특정 한 대로 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-220">Note: If Visual Studio asks to install new components, ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span>


9. <span data-ttu-id="19789-221">USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-221">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="19789-222">이 단원 지침에서는 HoloLens 2 장치를 사용 하 여 테스트를 배포할 것으로 가정 하지만 [hololens 2 에뮬레이터](using-the-hololens-emulator.md) 에 배포 하거나 [테스트용 로드에 대 한 앱 패키지](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) 를 만들도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-222">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

10. <span data-ttu-id="19789-223">장치를 빌드하기 전에 개발자 모드에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-223">Before building to your device, ensure that it is in Developer Mode.</span></span> <span data-ttu-id="19789-224">HoloLens 2에 처음으로 배포 하는 경우 Visual Studio는 HoloLens 2를 PIN과 페어링 하도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-224">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a PIN.</span></span> <span data-ttu-id="19789-225">개발자 모드를 사용 하도록 설정 하거나 Visual Studio와 쌍을 설정 해야 하는 경우 [다음 지침](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) 을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="19789-225">Follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

11. <span data-ttu-id="19789-226">ARM 아키텍처 뿐만 아니라 릴리스 구성을 선택 하 여 HoloLens 2를 빌드하기 위해 Visual Studio를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-226">Configure Visual Studio for building to your HoloLens 2, by selecting the Release configuration as well as the ARM architecture.</span></span>

    ![mrlearning-ch1-3-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. <span data-ttu-id="19789-228">마지막 단계는 디버그>디버깅하지 않고 시작을 선택하여 디바이스로 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="19789-228">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="19789-229">디버깅 하지 않고 시작을 선택 하면 Visual Studio에 디버깅 정보가 표시 되지 않고 빌드에 성공 했을 때 응용 프로그램이 장치에서 즉시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19789-229">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="19789-230">따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-230">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="19789-231">또한 응용 프로그램을 자동으로 시작 하지 않고도 빌드 > 솔루션 배포를 선택 하 여 장치에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-231">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![mrlearning-ch1-3-step12](images/mrlearning-asa-ch1-3-step12.jpg)

><span data-ttu-id="19789-233">참고: Azure 공간 앵커는 인터넷을 사용 하 여 앵커 데이터를 저장 하 고 로드 하므로, 사용자의 컴퓨터를 테스트 하기 전에 장치가 인터넷에 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-233">Note: The Azure spatial anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet before testing the ASA app.</span></span>

13. <span data-ttu-id="19789-234">지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="19789-234">Follow the instructions.</span></span> 
    <span data-ttu-id="19789-235">응용 프로그램이 장치에서 실행 되는 경우 화면의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="19789-235">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="19789-236">아래 단계에 해당 하는 장면 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="19789-236">Press the Scene buttons corresponding to the Steps below.</span></span> <span data-ttu-id="19789-237">이전 단계에서 설명한 대로 디버그 창을 추가한 경우 개별 단추 누르기에 대 한 피드백 및 Azure 공간 앵커와 관련 된 개별 작업의 진행 상황을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-237">If you added the debug window as mentioned in the previous steps, you can see the feedback for individual button press and the progress of individual operations related to Azure spatial anchors.</span></span>

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="19789-239">공간 앵커 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-239">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="19789-240">큐브를 다른 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-240">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="19789-241">큐브의 위치에 Azure 공간 앵커를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-241">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="19789-242">Azure 공간 앵커 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-242">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="19789-243">큐브의 로컬 앵커를 제거 하 여 사용자가 큐브를 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-243">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    
    6. <span data-ttu-id="19789-244">큐브를 다른 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-244">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="19789-245">Azure 공간 앵커 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-245">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="19789-246">Azure 공간 앵커를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-246">Find Azure Spatial Anchors.</span></span> 
    <span data-ttu-id="19789-247">앵커를 만들 때 원래 위치로 다시 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-247">You should go back to the original place you put it when you created the anchor.</span></span>
    
    9. <span data-ttu-id="19789-248">Azure 공간 앵커를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-248">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="19789-249">Azure 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-249">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="19789-250">환경 고정</span><span class="sxs-lookup"><span data-stu-id="19789-250">Anchoring an experience</span></span>

<span data-ttu-id="19789-251">이전 섹션에서는 Azure 공간 앵커의 기본 사항을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-251">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="19789-252">큐브를 사용 하 여 연결 된 앵커를 사용 하 여 부모 게임 개체를 나타내고 시각화 했습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-252">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="19789-253">이 섹션에서는 ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19789-253">In this section, you'll learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="19789-254">이 예에서는 [기본 모듈 단원 6](mrlearning-base-ch6.md)에서 만든 음력 모듈 어셈블리 데모 응용 프로그램을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-254">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="19789-255">"로켓 시작 관리자 완료" prefab을 검색 하 여 계층 구조에 개체의 자식으로 끌어 놓습니다 (아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="19789-255">Search for the "Rocket Launcher Complete" prefab and drag it into your hierarchy as a child of the object (see the image below).</span></span>

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="19789-257">아래 이미지에 표시 된 것 처럼 큐브가 계속 노출 되도록 모듈 어셈블리 환경을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-257">Position the module assembly experience so that the cube is still exposed, as shown in the image below.</span></span> <span data-ttu-id="19789-258">응용 프로그램에서 사용자는 큐브를 이동 하 여 전체 환경을 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-258">In the application, users may reposition the entire experience by moving the cube.</span></span> 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> <span data-ttu-id="19789-260">참고: 환경을 둘러싸는 경계 상자를 설정/해제 하는 단추를 사용 하 고,이 단계에서 사용 되는 큐브와 같이 위치 조정 개체를 사용 하 고, 위치 및 회전을 사용 하는 등 환경에 대 한 다양 한 사용자 환경 흐름을 제공 합니다. gizmo 그리려면.</span><span class="sxs-lookup"><span data-stu-id="19789-260">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="19789-261">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="19789-261">Congratulations</span></span>
<span data-ttu-id="19789-262">이 자습서에서는 Azure 공간 앵커의 기본 사항을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-262">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="19789-263">이 단원에서는 Azure 세션을 시작 및 중지 하 고 단일 장치에서 azure 앵커를 만들고 업로드 하 고 다운로드 하는 데 필요한 여러 단계를 살펴볼 수 있는 몇 가지 단추를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="19789-263">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span> <span data-ttu-id="19789-264">다음 단원에서는 응용 프로그램을 다시 시작한 후에도 검색을 위해 HoloLens 2에 Azure 앵커 Id를 저장 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19789-264">In the next lesson, you'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="19789-265">시리즈를 사용 하는 동안 여러 장치 간에 앵커 Id를 전송 하 여 공간 맞춤을 수행 하 고, 공유 자습서의 일부로 서, 다중 사용자 공유 세션에 대해 알아보는 방법도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19789-265">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment and learn about multi-user shared sessions, forthcoming as part of the Sharing tutorial.</span></span>

[<span data-ttu-id="19789-266">다음 단원: 2. Azure 공간 앵커 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="19789-266">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

