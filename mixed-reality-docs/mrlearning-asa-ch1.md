---
title: MR Learning ASA 모듈 HoloLens 2 Azure 공간 앵커
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415273"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a><span data-ttu-id="47d62-104">HoloLens 2 Azure 공간 앵커를 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="47d62-104">Getting started with Azure Spatial Anchors on HoloLens 2</span></span>

<span data-ttu-id="47d62-105">HoloLens 2 자습서의 두 번째 모듈을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-105">Welcome to the second module of the HoloLens 2 Tutorial.</span></span> <span data-ttu-id="47d62-106">시작 하기 전에 해야 하는 모든의 합니다 [필수 구성 요소](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="47d62-107">첫 번째 완료 하지 않은 경우 [기본 모듈입니다.](mrlearning-base.md) 아직 것이 좋습니다 해당 모듈을 먼저 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-107">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="47d62-108">새 Unity 프로젝트에서 시작 하는 경우의 새 프로젝트 만들기 단계를 수행 합니다 [기본 모듈입니다.](mrlearning-base.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-108">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="47d62-109">목표</span><span class="sxs-lookup"><span data-stu-id="47d62-109">Objectives</span></span>

* <span data-ttu-id="47d62-110">HoloLens 2를 사용 하 여 Azure 공간 앵커를 사용 하 여 개발 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="47d62-110">Learn the fundamentals of developing with Azure Spatial Anchors with the HoloLens 2</span></span>

* <span data-ttu-id="47d62-111">만들기, 업로드 및 다운로드 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="47d62-111">Create, Upload, and Download Spatial Anchors</span></span>

  

## <a name="instructions"></a><span data-ttu-id="47d62-112">지침</span><span class="sxs-lookup"><span data-stu-id="47d62-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="47d62-113">다운로드 및 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="47d62-113">Downloading and importing assets</span></span>
<span data-ttu-id="47d62-114">시작 하기 전에 다운로드 하 고 다음 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-114">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="47d62-115">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="47d62-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="47d62-116">자산 팩 MR 자료 모듈</span><span class="sxs-lookup"><span data-stu-id="47d62-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[<span data-ttu-id="47d62-117">자산 팩 ASA 모듈</span><span class="sxs-lookup"><span data-stu-id="47d62-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[<span data-ttu-id="47d62-118">혼합 현실 도구 키트</span><span class="sxs-lookup"><span data-stu-id="47d62-118">Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> <span data-ttu-id="47d62-119">참고: Azure 공간 앵커, MR 자료 모듈 자산 팩에 대 한 지침이 6 단계 및 3-특정 지침은 4 단계 혼합 현실 도구 키트 (MRKT)에서 가져오는 방법에 대 한 지침이 5 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47d62-119">Note: See Step 5 for specific instructions on how to import Azure Spatial Anchors, Step 6 for specific instructions on the MR Base module Asset Pack, and steps 3 through 4 for specific instructions on the Mixed Reality Toolkit (MRKT).</span></span>

1. <span data-ttu-id="47d62-120">프로젝트에서 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-120">Create a new scene in your project.</span></span> <span data-ttu-id="47d62-121">장면 폴더를 마우스 오른쪽 단추로 클릭 하 고 "만들기", 다음 장면을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-121">Right click your Scene folder, click "Create," then Scene.</span></span> <span data-ttu-id="47d62-122">새 장면을 ASALearningmodule 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-122">Name the new scene ASALearningmodule.</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="47d62-124">몇 가지 미리 정의 된 항목을 새 장면을 함께 표시를 보려는 ASALearningmodule를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-124">Double click ASALearningmodule to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="47d62-125">혼합된 현실 개발용 장면을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="47d62-127">참고: 포함 된 팝업이 표시 됩니다, 그리고 "혼합된 현실 도구 키트에 대 한 파일을 선택 해야 합니다."</span><span class="sxs-lookup"><span data-stu-id="47d62-127">Note: You will see a pop-up that says, "You must choose a file for the Mixed Reality Toolkit."</span></span> <span data-ttu-id="47d62-128">확인을 클릭 하면 4 단계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-128">Clicking Ok brings you to Step 4.</span></span>

4. <span data-ttu-id="47d62-129">선택 된 MRTK에 대 한 파일을 선택 DefaultMixedRealityToolkitConfigurationProfile 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

   > <span data-ttu-id="47d62-130">참고: 사용자 고유의 구성 프로필에 있는 경우 자유롭게을 대신 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="47d62-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="47d62-132">이제 장면 혼합된 현실 용 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="47d62-133">장면 저장 합니다 (컨트롤을 사용 하 여이 작업을 수행할 명령을 + S 또는 파일을 클릭 한 다음 클릭 / 저장 시).</span><span class="sxs-lookup"><span data-stu-id="47d62-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="47d62-134">가져오기의 [Azure 공간 앵커](https://github.com/azure/azure-spatial-anchors-samples/releases)합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="47d62-135">공간 앵커를 사용 하려면이 자산을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="47d62-136">위에 있는 링크를 클릭 하 고 AzureSpatialAnchors.unitypackage 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-136">Click on the link above and right click on AzureSpatialAnchors.unitypackage.</span></span> <span data-ttu-id="47d62-137">다른 이름으로 대상 저장 클릭 하 고 컴퓨터에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-137">Click on Save Target As and save it to your computer.</span></span> 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   <span data-ttu-id="47d62-139">저장 한 후 Unity로 다시 자산 클릭, 패키지 가져오기로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-139">After it's saved, go back into Unity, click Assets, go down to Import Package.</span></span> <span data-ttu-id="47d62-140">사용자 지정 패키지를 클릭 하는 중... 컴퓨터 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-140">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="47d62-141">경우는 수행, Azure 공간 앵커 패키지를 저장 하는 위치를 찾아 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-141">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="47d62-142">열기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-142">Then click Open.</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   <span data-ttu-id="47d62-144">팝업 표시 providingg 도구 / 설정 및 가져오기에 라는 목록이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-144">A pop-up appears, providingg a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="47d62-145">선택 ***모든*** 사용할 수 있는 옵션의 가져오기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-145">Select ***all*** of the options available, then click Import.</span></span>

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > <span data-ttu-id="47d62-147">참고: 환자 일 걸립니다 잠시 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-147">Note: Be patient, it will take a few minutes to import.</span></span> 

   6. <span data-ttu-id="47d62-148">가져오기 [MR 자료 모듈 자산 팩](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) 다음입니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-148">Import [MR Base module Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) next.</span></span> <span data-ttu-id="47d62-149">훨씬 단계 5와 같이 위의 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-149">Much like Step 5, click the link above.</span></span> <span data-ttu-id="47d62-150">그런 다음 BasemoduleAssetsV1 1.unitypackag 마우스 오른쪽 단추로 클릭으로 대상 저장을 클릭 하 고 컴퓨터에 저장.</span><span class="sxs-lookup"><span data-stu-id="47d62-150">Then right click BasemoduleAssetsV1 1.unitypackag, and click Save Target As, and save it to your computer.</span></span>

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > <span data-ttu-id="47d62-152">팁:  쉽게 찾고 액세스할 수 있도록 동일한 폴더에 이러한 모든 자산을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-152">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="47d62-153">간단 하 고 구성 된 모든 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-153">It keeps everything nice and organized.</span></span>

   <span data-ttu-id="47d62-154">5 단계와 마찬가지로 Unity를 뒤로 이동, 자산을 클릭 하 고 패키지 가져오기 마우스로 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-154">Just like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="47d62-155">사용자 지정 패키지를 클릭 하는 중... 컴퓨터 파일은 다시 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-155">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="47d62-156">기본 모듈 자산 팩을 저장 위치를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-156">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="47d62-157">선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-157">and select it.</span></span> <span data-ttu-id="47d62-158">열기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-158">Click Open.</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > <span data-ttu-id="47d62-160">참고: 나중에이 모듈에에서 필요한 자세한 자산 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-160">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="47d62-161">이 시점에서 언급 된 모든 자산을 가져오려면 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-161">Follow these steps to import any assets mentioned from this point on.</span></span> 
                                                                                                                                                                                                                    
7. <span data-ttu-id="47d62-162">동일한 접근 방식을 사용 하 여 이전 패키지를 가져올 때 ASA 모듈 ack를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-162">Import the ASA module ack using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="47d62-163">장면 구성</span><span class="sxs-lookup"><span data-stu-id="47d62-163">Configuring your scene</span></span>

<span data-ttu-id="47d62-164">이 섹션에서는 prefabs 및 스크립트를 만드는 일련의 로컬 앵커와 Azure 공간 앵커 응용 프로그램에서 작동 하는 방법의 기본 개념을 보여 주는 단추 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-164">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

7. <span data-ttu-id="47d62-165">자산 폴더 아래의 프로젝트 탭에서 ASAmoduleAssets 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-165">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="47d62-166">선택 하면 두 prefabs 표시 됩니다. ButtonParent 및 ParentAnchor 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-166">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. <span data-ttu-id="47d62-168">두 prefabs 장면 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-168">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. <span data-ttu-id="47d62-170">두 번 클릭 하 여 선택 부모 앵커입니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-170">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="47d62-171">장면 전체를 보려면 보기를 조정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-171">You might need to adjust your view to see the entire scene.</span></span> <span data-ttu-id="47d62-172">필요에 따라 장면을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-172">Adjust your scene as needed.</span></span>

    <span data-ttu-id="47d62-173">ParentAnchor prefab 숙지 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-173">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="47d62-174">현재 게임 라는 개체 ParentAnchor, 데모용으로 색이 지정 된 큐브입니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-174">Currently, the game object named, ParentAnchor, is a colored cube for demonstration purposes.</span></span> <span data-ttu-id="47d62-175">결국 우리 ', ll 큐브를 숨기고는 ParentAnchor의 자식으로 콘텐츠를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-175">Eventually, we',ll hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="47d62-176">이 prefab AzureSpatialAnchorsDemoWrapper.cs 스크립트 (ASA SDK 포함) 및 ParentAnchor 개체에이 모듈의 일부로 포함 된 ASAmoduleScript.cs 스크립트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-176">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK), and the ASAmoduleScript.cs script, included as part of this module to the ParentAnchor object.</span></span> 

10. <span data-ttu-id="47d62-177">단추를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-177">Configure buttons.</span></span> <span data-ttu-id="47d62-178">ParentAnchor prefab 여러 레이블이 지정 된 단추 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-178">Under the ParentAnchor prefab, notice several labeled buttons.</span></span> <span data-ttu-id="47d62-179">이러한 단추는 MRTK PressableButton prefabs에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-179">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="47d62-180">Pressable 단추를 만드는 방법에 자세히 알아보려면 합니다 [기본 모듈입니다.](mrlearning-base-ch2.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-180">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="47d62-181">각 단추에 대 한 키를 누르거나 아래 목록에 따라 단추를 선택 하는 경우 트리거되는 이벤트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-181">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="47d62-182">StartAzureSession, 라는 단추 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-182">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47d62-183">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StartAzureSession() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-183">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="47d62-187">단추 이름으로, StopAzureSession 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-187">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47d62-188">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StopAzureSession() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-188">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="47d62-189">CreateAnchor, 라는 단추 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-189">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47d62-190">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 CreateAzureAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-190">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="47d62-191">이벤트 트리거 시작 확인에 대 한 앵커 라는 단추에 대 한 단추 Presse에서 새 이벤트 만들기"와 클릭 이벤트 트리거.</span><span class="sxs-lookup"><span data-stu-id="47d62-191">For the Button named, Start Looking For Anchor, create a new event under the Button Presse" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47d62-192">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 FindAzureAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-192">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="47d62-193">DeleteAzureAnchor, 라는 단추 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-193">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47d62-194">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 DeleteAzureAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-194">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="47d62-195">라는 로컬 앵커 삭제 단추의 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-195">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47d62-196">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 RemoveLocalAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-196">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="47d62-197">빌드 및 기본 응용 프로그램을 보여 줍니다</span><span class="sxs-lookup"><span data-stu-id="47d62-197">Build and demonstrate Base Application</span></span>

<span data-ttu-id="47d62-198">장면을 Azure 공간 앵커의 기본 사항을 설명 하기 위해 구성 했으므로 작성 하 고 Azure 공간 앵커의 기본 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-198">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="47d62-199">이전 섹션의 Build Settings 창을 닫은 경우 File>Build Settings로 이동하여 Build Settings 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-199">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="47d62-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="47d62-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="47d62-201">열기 백그라운드에서 추가 단추를 클릭 하 여 시도 하려는 장면이 빌드 목록에 자동으로 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-201">Ensure the scene you want to try is in the Scenes in Build list by clicking on the Add Open Scenes button.</span></span>

3. <span data-ttu-id="47d62-202">Build 단추를 눌러 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-202">Press the Build button to begin the build process.</span></span>
    <span data-ttu-id="47d62-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="47d62-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="47d62-204">애플리케이션의 새 폴더를 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-204">Create and name a new folder for your application.</span></span> <span data-ttu-id="47d62-205">아래 이미지에서 앱 이름 가진 폴더가 응용 프로그램을 포함 하기 위해 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-205">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="47d62-206">새로 만든된 폴더에 빌드를 시작 폴더 선택를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-206">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="47d62-207">Unity의 빌드가 완료 된 후 빌드 설정을 닫아도"창입니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-207">After the build has completed, you may close the Build Setting" window in Unity.</span></span> 
    <span data-ttu-id="47d62-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="47d62-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="47d62-209">참고: 빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-209">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="47d62-210">"Error: CS0246 = "XX"를 찾을 수 없는 tyoe 또는 네임 스페이스 이름 (사용 하는 누락 된 지시문 또는 어셈블리 참조가?).</span><span class="sxs-lookup"><span data-stu-id="47d62-210">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="47d62-211">설치 해야 할 수도 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="47d62-211">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="47d62-212">빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-212">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="47d62-213">두 번 the"MixedRealityBase.sln 솔루션 또는 해당 이름을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-213">Double click on the“MixedRealityBase.sln solution or the corresponding name.</span></span> <span data-ttu-id="47d62-214">Visual Studio에서 솔루션 파일을 열려면 프로젝트에 대 한 대체 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-214">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="47d62-215">참고: (즉, 앱 폴더, 빌드 폴더 내에서.sln 파일을 사용 하 여 혼동 하면 안 되는 폴더 외부 이름이 비슷한.sln 파일 때문에 이전 단계에서 명명 규칙을 따르는 경우 새로 만든된 폴더를 열어야 합니다.입니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-215">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > <span data-ttu-id="47d62-217">참고: 새 구성 요소를 설치를 묻는 메시지가 나타나면 Visual Studio 잠시 모든 필수 구성 요소가 설치 되어 있는지 확인 하려면에서 구체적 ["Tools 설치" 페이지](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="47d62-217">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="47d62-218">USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-218">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="47d62-219">이러한 단원 지침 HoloLens 2 장치를 사용 하 여 테스트를 배포할 수 있다고 가정에서 수도 있습니다를 배포 하는 [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md) 를 만들도록 선택할는 [테스트용 로드 앱 패키지](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="47d62-219">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="47d62-220">디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-220">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="47d62-221">이번에 처음으로 HoloLens 2에 배포하는 경우리면 Visual Studio에서 pin 사용하여 HoloLens 2에 연결하도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-221">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="47d62-222">따릅니다 [이러한 지침](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) 개발자 모드를 사용 하도록 설정 하거나 Visual Studio를 쌍으로 연결 해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="47d62-222">Follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="47d62-223">릴리스 구성 및 "RM" 아키텍처를 선택 하 여 HoloLens 2에 구성에 대 한 Visual Studio를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-223">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration and the “RM” architecture.</span></span>
    <span data-ttu-id="47d62-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="47d62-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
   
9. <span data-ttu-id="47d62-225">마지막 단계는 디버그를 선택 하 여 장치를 빌드할 수 > 디버깅 하지 않고 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-225">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="47d62-226">디버깅 하지 않고 시작을 선택 하면 응용 프로그램을 Visual Studio에 표시 되는 성공적인 빌드 다음 디버깅 정보에 따라 장치에 즉시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build ithout Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="47d62-227">따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="47d62-228">빌드를 선택할 수 있습니다 > 응용 프로그램을 자동으로 시작 하지 않고 장치에 배포할 솔루션을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-228">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
    <span data-ttu-id="47d62-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="47d62-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
    
<span data-ttu-id="47d62-230">10. 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-230">10.Follow the instructions.</span></span> <span data-ttu-id="47d62-231">응용 프로그램은 장치에서 실행 하는 경우에 따라는 화면의 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-231">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="47d62-232">아래 단계에 해당 되는 장면 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-232">Press the Scene buttons corresponding to the Steps below.</span></span>
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="47d62-233">공간 앵커 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-233">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="47d62-234">큐브를 다른 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-234">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="47d62-235">큐브의 위치의 Azure 공간 앵커를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-235">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="47d62-236">Azure 공간 앵커 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-236">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="47d62-237">큐브에 큐브를 이동할 수 있도록 로컬 앵커를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-237">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    6. <span data-ttu-id="47d62-238">큐브의 다른 위치를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-238">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="47d62-239">Azure 공간 앵커 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-239">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="47d62-240">Azure 공간 aachors를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-240">Find Azure Spatial aachors.</span></span> 
    
    <span data-ttu-id="47d62-241">e 되돌아가야 원래 위치로 있습니다 넣습니다 앵커를 만들 때).</span><span class="sxs-lookup"><span data-stu-id="47d62-241">e You should go back to the original place you put it when you created the anchor).</span></span>
    9. <span data-ttu-id="47d62-242">Azure 공간 앵커를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-242">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="47d62-243">Azure 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-243">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="47d62-244">환경을 고정</span><span class="sxs-lookup"><span data-stu-id="47d62-244">Anchoring an experience</span></span>

<span data-ttu-id="47d62-245">이전 섹션에서는 Azure 공간 앵커의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-245">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="47d62-246">큐브를 나타내는 연결 된 앵커를 사용 하 여 부모 게임 개체를 시각화 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-246">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="47d62-247">이 섹션에서는 ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-247">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="47d62-248">예를 들어 음력 모듈 중 생성 된 어셈블리 데모 응용 프로그램을 사용 했습니다 [기본 모듈 6 단원](mrlearning-base-ch6.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-248">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="47d62-249">음력 모듈 어셈블리 전체 prefab을 검색 하 고 끌어온 사용자 계층 구조의 AnchorParent gameobject 자식인 아래 이미지에 표시 된 대로 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-249">Search for the Lunar Module Assembly Complete prefab, and drag it into your heirarchy as a child of the AnchorParent gameobject as shown in the image below.</span></span>

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="47d62-251">모듈 어셈블리 위치에는 아래 이미지 에서처럼 큐브에 노출 됩니다 있도록 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-251">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="47d62-252">응용 프로그램에서 사용자가 큐브를 이동 하 여 전체 환경 위치 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-252">In the application, users may reposition the entire experience by moving the cube.</span></span> 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > <span data-ttu-id="47d62-254">참고: 다양 한 경험을 둘러싸는 경계 상자를 설정/해제, 위치 및 회전 gizmo 사용 재배치 개체 (예: 큐브가이 단계에서 사용)를 사용 하는 단추 사용을 비롯 하 여 환경을 위치에 대 한 사용자 경험 흐름 및 기타 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-254">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="47d62-255">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-255">Congratulations</span></span>
<span data-ttu-id="47d62-256">이 단원에서는 Azure 공간 앵커의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-256">In this lesson, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="47d62-257">이 esson 수 있는 여러 단추를 사용 하 여 시작 하 고 Azure 세션을 중지 하 고 만들기, 업로드 및 단일 장치에서 azure 앵커를 다운로드 하는 데 필요한 다양 한 단계를 살펴보면 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-257">This esson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="47d62-258">다음 단원에서는 응용 프로그램 다시 시작 된 후에, 검색에 대 한 여 HoloLens 2 Azure 앵커 Id를 저장 하는 방법을 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="47d62-258">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="47d62-259">시리즈도 배웁니다 공간 맞춤 하 고 다중 사용자 세션 (곧 모듈을 공유 하는 일환으로 제공 합니다.)를 공유 하는 방법에 대 한 알아봅니다를 여러 장치 간에 앵커 Id를 전송 하는 방법</span><span class="sxs-lookup"><span data-stu-id="47d62-259">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions (forthcoming as part of sharing module.)</span></span>

[<span data-ttu-id="47d62-260">다음 단원: ASA 단원 2</span><span class="sxs-lookup"><span data-stu-id="47d62-260">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)

