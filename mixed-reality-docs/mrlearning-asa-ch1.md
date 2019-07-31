---
title: HoloLens 학습을 위한 Azure 공간 앵커 (HoloLens) 2
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 9f830bc4ead35fd308108051617c61c65d98d451
ms.sourcegitcommit: c0d5c19b756b8e6ff95ea26a4d8d2b3a53878c2e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671963"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="0d093-104">1. Azure 공간 앵커 시작</span><span class="sxs-lookup"><span data-stu-id="0d093-104">1. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="0d093-105">HoloLens 2 자습서의 두 번째 모듈을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-105">Welcome to the second module of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="0d093-106">시작 하기 전에 모든 [필수 구성 요소](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="0d093-107">첫 번째 [기본 모듈](mrlearning-base.md) 을 아직 완료 하지 않은 경우 해당 모듈을 먼저 완료 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-107">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="0d093-108">새 Unity 프로젝트에서 시작 하는 경우 [기본 모듈](mrlearning-base.md)의 새 프로젝트 만들기 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-108">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="0d093-109">목표</span><span class="sxs-lookup"><span data-stu-id="0d093-109">Objectives</span></span>

* <span data-ttu-id="0d093-110">HoloLens 2를 사용 하 여 Azure 공간 앵커로 개발 하는 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="0d093-110">Learn the fundamentals of developing with Azure Spatial Anchors with HoloLens 2</span></span>

* <span data-ttu-id="0d093-111">공간 앵커 만들기, 업로드 및 다운로드</span><span class="sxs-lookup"><span data-stu-id="0d093-111">Create, upload, and download spatial anchors</span></span>

## <a name="instructions"></a><span data-ttu-id="0d093-112">지침</span><span class="sxs-lookup"><span data-stu-id="0d093-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="0d093-113">자산 다운로드 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="0d093-113">Downloading and importing assets</span></span>
<span data-ttu-id="0d093-114">시작 하기 전에 다음 자산을 다운로드 하 여 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="0d093-114">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="0d093-115">Azure 공간 앵커 v 1.1.0</span><span class="sxs-lookup"><span data-stu-id="0d093-115">Azure Spatial Anchors v1.1.0</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[<span data-ttu-id="0d093-116">MR 기본 모듈 자산 팩 v 1.2</span><span class="sxs-lookup"><span data-stu-id="0d093-116">MR Base module Asset Pack v1.2</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/1.2/BaseModuleAssets-1.2.unitypackage)

[<span data-ttu-id="0d093-117">GLOBAL.ASA 모듈 Asset Pack v1.0</span><span class="sxs-lookup"><span data-stu-id="0d093-117">ASA module Asset Pack v1.0</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/v1/ASAModuleAssets_1.unitypackage)

[<span data-ttu-id="0d093-118">Mixed Reality Toolkit 2.0.0 RC1</span><span class="sxs-lookup"><span data-stu-id="0d093-118">Mixed Reality Toolkit 2.0.0RC1</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)

> <span data-ttu-id="0d093-119">참고: Azure 공간 앵커를 가져오는 방법에 대 한 구체적인 지침은 5 단계를 참조 하 고, MR 기본 모듈 자산 팩의 특정 지침에 대해서는 6 단계를 참조 하 고, Mixed Reality 도구 키트 (MRKT)에 대 한 특정 지침은 3 ~ 4 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d093-119">Note: See Step 5 for specific instructions on how to import Azure Spatial Anchors, Step 6 for specific instructions on the MR Base module Asset Pack, and steps 3 through 4 for specific instructions on the Mixed Reality Toolkit (MRKT).</span></span>

1. <span data-ttu-id="0d093-120">프로젝트에 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-120">Create a new scene in your project.</span></span> <span data-ttu-id="0d093-121">장면 폴더를 마우스 오른쪽 단추로 클릭 하 고 만들기, 장면을 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-121">Right click your Scene folder, click Create, then Scene.</span></span> <span data-ttu-id="0d093-122">새 장면 이름을 ASALearningmodule로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-122">Name the new scene ASALearningmodule.</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="0d093-124">ASALearningmodule를 두 번 클릭 하 여 미리 정의 된 항목이 새 장면에 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-124">Double click ASALearningmodule to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="0d093-125">혼합 현실 개발을 위한 장면을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="0d093-127">참고: 혼합 된 현실 도구 키트에 대 한 파일을 선택 해야 한다는 팝업이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-127">Note: You will see a pop-up that says, You must choose a file for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="0d093-128">확인을 클릭 하면 4 단계로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-128">Clicking Ok brings you to Step 4.</span></span>

4. <span data-ttu-id="0d093-129">MRTK에 대 한 파일을 선택 하는 경우 DefaultMixedRealityToolkitConfigurationProfile를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

> <span data-ttu-id="0d093-130">참고: 사용자 고유의 구성 프로필이 있는 경우이를 대신 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d093-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="0d093-132">이제는 혼합 현실에 대해 장면이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="0d093-133">장면을 저장 해야 합니다 (ctrl/command + S를 사용 하 여이 작업을 수행 하거나 파일을 클릭 한 다음 저장을 클릭).</span><span class="sxs-lookup"><span data-stu-id="0d093-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="0d093-134">[Azure 공간 앵커](https://github.com/azure/azure-spatial-anchors-samples/releases)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="0d093-135">공간 앵커를 사용 하려면이 자산을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="0d093-136">위의 링크를 클릭 하 고 AzureSpatialAnchors. unitypackage를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-136">Click on the link above and right click on AzureSpatialAnchors.unitypackage.</span></span> <span data-ttu-id="0d093-137">다른 이름으로 대상 저장을 클릭 하 고 컴퓨터에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-137">Click on Save Target As and save it to your computer.</span></span> 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

<span data-ttu-id="0d093-139">저장 된 후 Unity로 돌아가서 자산을 클릭 하 고 패키지 가져오기로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-139">After it's saved, go back into Unity, click Assets, go down to Import Package.</span></span> <span data-ttu-id="0d093-140">그런 다음 사용자 지정 패키지 ...를 클릭 합니다. 컴퓨터 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-140">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="0d093-141">이렇게 하면 Azure 공간 앵커 패키지를 저장 한 위치를 찾아서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-141">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="0d093-142">그런 다음 열기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-142">Then click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

<span data-ttu-id="0d093-144">팝업이 표시 되 고 도구 및 설정 목록이 providingg 가져올 항목을 묻는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-144">A pop-up appears, providingg a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="0d093-145">사용할 수 있는 옵션을 ***모두*** 선택 하 고 가져오기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-145">Select ***all*** of the options available, then click Import.</span></span>

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> <span data-ttu-id="0d093-147">참고: 잠시 기다려 주세요. 가져오는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-147">Note: Be patient, it will take a few minutes to import.</span></span> 

6. <span data-ttu-id="0d093-148">가져오기 [MR 기본 모듈 자산 팩]https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) 다음.</span><span class="sxs-lookup"><span data-stu-id="0d093-148">Import [MR Base module Asset Pack]https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) next.</span></span> <span data-ttu-id="0d093-149">5 단계와 마찬가지로 위의 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-149">Much like Step 5, click the link above.</span></span> <span data-ttu-id="0d093-150">그런 다음 BasemoduleAssetsV1 1. i g ag를 마우스 오른쪽 단추로 클릭 하 고 다른 이름으로 대상 저장을 클릭 하 여 컴퓨터에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-150">Then right click BasemoduleAssetsV1 1.unitypackag, and click Save Target As, and save it to your computer.</span></span>

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> <span data-ttu-id="0d093-152">팁:  이러한 모든 자산을 찾고 쉽게 액세스할 수 있도록 동일한 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-152">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="0d093-153">모든 것을 잘 구성 된 상태로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-153">It keeps everything nice and organized.</span></span>

<span data-ttu-id="0d093-154">5 단계와 마찬가지로 Unity로 돌아가서 자산을 클릭 하 고 가져오기 패키지를 마우스로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-154">Just like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="0d093-155">사용자 지정 패키지 ...를 클릭 합니다. 컴퓨터 파일이 다시 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-155">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="0d093-156">기본 모듈 자산 팩을 저장 한 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-156">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="0d093-157">선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-157">and select it.</span></span> <span data-ttu-id="0d093-158">열기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-158">Click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> <span data-ttu-id="0d093-160">참고: 이 모듈의 뒷부분에 더 많은 자산이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-160">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="0d093-161">이 시점에서 언급 된 자산을 가져오려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-161">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="0d093-162">이전 패키지를 가져오는 것과 동일한 방법을 사용 하 여 [global.asa 모듈 팩](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1) 을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-162">Import the [ASA module pack](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1) using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="0d093-163">장면 구성</span><span class="sxs-lookup"><span data-stu-id="0d093-163">Configuring your scene</span></span>

<span data-ttu-id="0d093-164">이 섹션에서는 prefabs 및 스크립트를 장면에 추가 하 여 로컬 앵커와 Azure 공간 앵커가 응용 프로그램에서 작동 하는 방식에 대 한 기본 사항을 보여 주는 일련의 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-164">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

8. <span data-ttu-id="0d093-165">프로젝트 탭의 자산 폴더 아래에서 ASAmoduleAssets을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-165">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="0d093-166">선택 하면 두 개의 prefabs 표시 됩니다. ButtonParent 및 ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="0d093-166">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. <span data-ttu-id="0d093-168">두 prefabs를 장면으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-168">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. <span data-ttu-id="0d093-170">부모 앵커를 두 번 클릭 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-170">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="0d093-171">전체 장면을 보려면 보기를 조정 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-171">You might need to adjust your view to see the entire scene.</span></span> <span data-ttu-id="0d093-172">필요에 따라 장면을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-172">Adjust your scene as needed.</span></span>

<span data-ttu-id="0d093-173">ParentAnchor prefab에 익숙해져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-173">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="0d093-174">현재, ParentAnchor 라는 게임 개체는 데모용으로 색칠 된 큐브입니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-174">Currently, the game object named, ParentAnchor, is a colored cube for demonstration purposes.</span></span> <span data-ttu-id="0d093-175">결국 큐브를 숨기고 콘텐츠를 ParentAnchor의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-175">Eventually, we',ll hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="0d093-176">이 prefab에는 AzureSpatialAnchorsDemoWrapper.cs 스크립트 (GLOBAL.ASA SDK에 포함) 및이 모듈의 일부로 ParentAnchor 개체에 포함 된 ASAmoduleScript.cs 스크립트가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-176">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK), and the ASAmoduleScript.cs script, included as part of this module to the ParentAnchor object.</span></span> 

11. <span data-ttu-id="0d093-177">단추를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-177">Configure buttons.</span></span> <span data-ttu-id="0d093-178">ButtonParent prefab에서 레이블이 지정 된 여러 단추를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-178">Under the ButtonParent prefab, notice several labeled buttons.</span></span> <span data-ttu-id="0d093-179">이러한 단추는 MRTK의 보도 Sablebutton prefabs에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-179">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="0d093-180">[기본 모듈](mrlearning-base-ch2.md)에서 Pressable 단추를 만드는 방법에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="0d093-180">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="0d093-181">각 단추에 대해 사용자가 아래 목록에 따라 단추를 누르거나 선택할 때 트리거되는 이벤트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-181">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="0d093-182">StartAzureSession 라는 단추에 대해 단추 누름 이벤트 트리거 뿐만 아니라 클릭 시 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-182">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="0d093-183">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StartAzureSession () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-183">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="0d093-187">단추 이름 StopAzureSession에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-187">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="0d093-188">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StopAzureSession () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-188">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="0d093-189">CreateAnchor 라는 단추에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-189">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="0d093-190">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 CreateAzureAnchor () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-190">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="0d093-191">이라는 단추의 경우 앵커를 검색 하기 시작 하 고, "이벤트 트리거" 및 [클릭 시 이벤트 트리거] 아래에 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-191">For the Button named, Start Looking For Anchor, create a new event under the Button Presse" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="0d093-192">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 FindAzureAnchor () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-192">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="0d093-193">DeleteAzureAnchor 라는 단추에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-193">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="0d093-194">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 DeleteAzureAnchor () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-194">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="0d093-195">이라는 단추의 경우 로컬 앵커를 삭제 하 고 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-195">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="0d093-196">ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 RemoveLocalAnchor () 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-196">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="0d093-197">기본 응용 프로그램 빌드 및 시연</span><span class="sxs-lookup"><span data-stu-id="0d093-197">Build and demonstrate Base Application</span></span>

<span data-ttu-id="0d093-198">이제 Azure 공간 앵커의 기본 사항을 보여 주기 위해 장면을 구성 했으므로 Azure 공간 앵커의 기본 동작을 작성 하 고 시연 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-198">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="0d093-199">이전 섹션의 Build Settings 창을 닫은 경우 File>Build Settings로 이동하여 Build Settings 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-199">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
<span data-ttu-id="0d093-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="0d093-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="0d093-201">열려 있는 장면 추가 단추를 클릭 하 여 시도 하려는 장면이 빌드 목록의 장면에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-201">Ensure the scene you want to try is in the Scenes in Build list by clicking on the Add Open Scenes button.</span></span>

3. <span data-ttu-id="0d093-202">Build 단추를 눌러 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-202">Press the Build button to begin the build process.</span></span>
<span data-ttu-id="0d093-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="0d093-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="0d093-204">애플리케이션의 새 폴더를 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-204">Create and name a new folder for your application.</span></span> <span data-ttu-id="0d093-205">아래 이미지에서 응용 프로그램을 포함 하기 위해 이름이 앱 인 폴더를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-205">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="0d093-206">폴더 선택을 클릭 하 여 새로 만든 폴더로 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-206">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="0d093-207">빌드가 완료 되 면 Unity에서 빌드 설정 "창을 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-207">After the build has completed, you may close the Build Setting" window in Unity.</span></span> 
<span data-ttu-id="0d093-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="0d093-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="0d093-209">참고: 빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-209">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="0d093-210">"Error: CS0246 = password 또는 네임 스페이스 이름 "XX"을 (를) 찾을 수 없습니다. using 지시문 또는 어셈블리 참조가 있는지 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d093-210">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="0d093-211">[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 를 설치 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-211">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="0d093-212">빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-212">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="0d093-213">"MixedRealityBase 솔루션 또는 해당 이름을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-213">Double click on the“MixedRealityBase.sln solution or the corresponding name.</span></span> <span data-ttu-id="0d093-214">프로젝트에 대체 이름을 사용 하 여 Visual Studio에서 솔루션 파일을 연 경우</span><span class="sxs-lookup"><span data-stu-id="0d093-214">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="0d093-215">참고: 빌드 폴더 내에 있는 .sln 파일과 혼동 하지 않도록 해당 폴더 외부에 비슷한 이름의 .sln 파일이 있기 때문에 새로 만든 폴더 (즉, 이전 단계의 명명 규칙에 따라 응용 프로그램 폴더)를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-215">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="0d093-217">참고: Visual Studio에서 새 구성 요소를 설치 하도록 요청 하는 경우 잠시 시간을 내 서 모든 필수 구성 요소가 ["도구 설치" 페이지](install-the-tools.md) 에 특정 한 대로 설치 되었는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d093-217">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="0d093-218">USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-218">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="0d093-219">이 단원 지침에서는 HoloLens 2 장치를 사용 하 여 테스트를 배포할 것으로 가정 하지만 [hololens 2 에뮬레이터](using-the-hololens-emulator.md) 에 배포 하거나 [테스트용 로드에 대 한 앱 패키지](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>) 를 만들도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-219">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="0d093-220">디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-220">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="0d093-221">이번에 처음으로 HoloLens 2에 배포하는 경우리면 Visual Studio에서 pin 사용하여 HoloLens 2에 연결하도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-221">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="0d093-222">개발자 모드를 사용 하도록 설정 하거나 Visual Studio와 쌍을 설정 해야 하는 경우 [다음 지침](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) 을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="0d093-222">Follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="0d093-223">RM 아키텍처 뿐만 아니라 릴리스 구성을 선택 하 여 HoloLens 2를 빌드하기 위해 Visual Studio를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-223">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration as well as the RM architecture.</span></span>
<span data-ttu-id="0d093-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="0d093-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
   
9. <span data-ttu-id="0d093-225">마지막 단계는 디버그 > 디버깅 하지 않고 시작을 선택 하 여 장치를 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-225">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="0d093-226">디버깅 하지 않고 시작을 선택 하면 Visual Studio에 표시 되는 디버깅 정보가 성공적으로 생성 될 때 응용 프로그램이 장치에서 즉시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build ithout Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="0d093-227">따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="0d093-228">또한 응용 프로그램을 자동으로 시작 하지 않고도 빌드 > 솔루션 배포를 선택 하 여 장치에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-228">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
<span data-ttu-id="0d093-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="0d093-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
   
10. <span data-ttu-id="0d093-230">지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-230">Follow the instructions.</span></span> <span data-ttu-id="0d093-231">응용 프로그램이 장치에서 실행 되는 경우 화면의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-231">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="0d093-232">아래 단계에 해당 하는 장면 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-232">Press the Scene buttons corresponding to the Steps below.</span></span>

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="0d093-234">공간 앵커 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-234">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="0d093-235">큐브를 다른 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-235">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="0d093-236">큐브의 위치에 Azure 공간 앵커를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-236">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="0d093-237">Azure 공간 앵커 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-237">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="0d093-238">큐브의 로컬 앵커를 제거 하 여 사용자가 큐브를 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-238">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    
    6. <span data-ttu-id="0d093-239">큐브를 다른 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-239">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="0d093-240">Azure 공간 앵커 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-240">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="0d093-241">Azure 공간 앵커를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-241">Find Azure Spatial Anchors.</span></span> 
    <span data-ttu-id="0d093-242">앵커를 만들 때 원래 위치로 다시 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-242">You should go back to the original place you put it when you created the anchor.</span></span>
    
    9. <span data-ttu-id="0d093-243">Azure 공간 앵커를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-243">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="0d093-244">Azure 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-244">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="0d093-245">환경 고정</span><span class="sxs-lookup"><span data-stu-id="0d093-245">Anchoring an experience</span></span>

<span data-ttu-id="0d093-246">이전 섹션에서는 Azure 공간 앵커의 기본 사항을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-246">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="0d093-247">큐브를 사용 하 여 연결 된 앵커를 사용 하 여 부모 게임 개체를 나타내고 시각화 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-247">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="0d093-248">이 섹션에서는 ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-248">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="0d093-249">이 예에서는 [기본 모듈 단원 6](mrlearning-base-ch6.md)에서 만든 음력 모듈 어셈블리 데모 응용 프로그램을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-249">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="0d093-250">다음 그림에 표시 된 것 처럼, 음력 모듈 어셈블리 전체 prefab을 검색 하 여 계층 구조에 AnchorParent gameobject의 자식으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-250">Search for the Lunar Module Assembly Complete prefab, and drag it into your heirarchy as a child of the AnchorParent gameobject as shown in the image below.</span></span>

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="0d093-252">아래 이미지에 표시 된 것 처럼 큐브가 계속 노출 되도록 모듈 어셈블리 환경을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-252">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="0d093-253">응용 프로그램에서 사용자는 큐브를 이동 하 여 전체 환경을 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-253">In the application, users may reposition the entire experience by moving the cube.</span></span> 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> <span data-ttu-id="0d093-255">참고: 환경을 둘러싸는 경계 상자를 설정/해제 하는 단추를 사용 하 고,이 단계에서 사용 되는 큐브와 같은 위치 조정 개체를 사용 하 고, 위치 및 회전 gizmo 그리려면을 사용 하는 등의 다양 한 사용자 환경 흐름을 사용 하 여 환경 위치를 조정 합니다. 및 기타.</span><span class="sxs-lookup"><span data-stu-id="0d093-255">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="0d093-256">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-256">Congratulations</span></span>
<span data-ttu-id="0d093-257">이 자습서에서는 Azure 공간 앵커의 기본 사항을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-257">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="0d093-258">이 esson에서는 Azure 세션을 시작 및 중지 하 고 단일 장치에서 azure 앵커를 만들고, 업로드 하 고, 다운로드 하는 데 필요한 다양 한 단계를 살펴볼 수 있는 몇 가지 단추를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-258">This esson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="0d093-259">다음 단원에서는 응용 프로그램을 다시 시작한 후에도 검색을 위해 HoloLens 2에 Azure 앵커 Id를 저장 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-259">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="0d093-260">시리즈를 사용 하는 동안에는 여러 장치 간에 앵커 Id를 전송 하 여 공간 맞춤을 수행 하는 방법과 공유 자습서의 일부로 서 사용자가 사용할 수 있는 다중 사용자 공유 세션에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0d093-260">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions, forthcoming as part of Sharing tutorial.</span></span>

[<span data-ttu-id="0d093-261">다음 단원: 2. Azure Spatial Anchors 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="0d093-261">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

