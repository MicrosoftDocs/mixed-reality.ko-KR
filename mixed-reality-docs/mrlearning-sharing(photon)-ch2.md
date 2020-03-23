---
title: 다중 사용자 기능 자습서 - 2. Unity 개발 준비
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031236"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="d75c8-105">2. Unity 개발 준비</span><span class="sxs-lookup"><span data-stu-id="d75c8-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="d75c8-106">이 자습서에서는 애플리케이션을 개발하기 위해 Mixed Reality Toolkit 가져오기, 빌드 설정 구성 및 장면 준비를 포함하여 Unity를 준비하고 구성하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="d75c8-107">목표</span><span class="sxs-lookup"><span data-stu-id="d75c8-107">Objectives</span></span>

* <span data-ttu-id="d75c8-108">애플리케이션 개발을 위한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="d75c8-108">Configure Unity for application development</span></span>
* <span data-ttu-id="d75c8-109">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="d75c8-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="d75c8-110">프로젝트 장면 준비</span><span class="sxs-lookup"><span data-stu-id="d75c8-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="d75c8-111">지침</span><span class="sxs-lookup"><span data-stu-id="d75c8-111">Instructions</span></span>

1. <span data-ttu-id="d75c8-112">[여기](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)를 클릭하여 Mixed Reality Toolkit Foundation Unity 패키지를 다운로드하고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="d75c8-113">Unity에서 [자산] 메뉴를 클릭하고, [패키지 가져오기]를 선택한 다음, [사용자 지정 패키지]를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="d75c8-115">1단계에 제공된 링크에서 방금 다운로드한 Unity 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="d75c8-116">Unity에 가져오기 팝업 창이 표시되면 [가져오기] 단추를 클릭하여 MRTK 가져오기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="d75c8-117">이 경우 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="d75c8-119">다운로드한 패키지는 해당 파일을 저장한 로컬 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="d75c8-120">위의 이미지에서는 패키지를 찾을 수 있는 위치를 보여 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="d75c8-121">패키지를 가져오면 MRTK Project Configurator(MRTK 프로젝트 구성기) 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d75c8-122">그렇지 않으면 Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > Unity 프로젝트 구성을 차례로 선택하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="d75c8-123">MRTK 프로젝트 구성기 창에서 [구성 수정] 섹션을 펼치고, [Unity용 MSBuild 사용] 확인란의 선택을 취소하고, 다른 모든 옵션이 선택되었는지 확인한 다음, [적용] 단추를 클릭하여 해당 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="d75c8-125">Unity용 MSBuild는 사용할 SDK 중 일부만 지원할 수 있으며, 사용하도록 설정된 후에 이를 사용하지 않도록 설정하는 것이 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="d75c8-126">따라서 Unity용 MSBuild를 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="d75c8-127">새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-127">Create a new scene.</span></span> <span data-ttu-id="d75c8-128">이 작업은 [파일]을 클릭하고 [새 장면]을 선택하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="d75c8-129">HLSharedProjectMain으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="d75c8-130">Mixed Reality Toolkit 아래에서 [장면에 추가] 및 [구성]을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="d75c8-132">이 작업이 완료되면 계층 구조에서 MRTK(Mixed Reality Toolkit)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="d75c8-133">[검사기] 패널에서 MRTK 구성 프로필을 DefaultHoloLens2ConfigurationProfile로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="d75c8-135">계층 구조에서 MRTK(Mixed Reality Toolkit)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="d75c8-136">아래 그림과 같이 [검사기] 패널에서 Mixed Reality Toolkit 스크립트를 찾아서 "복사 및 사용자 지정" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="d75c8-137">이후 팝업이 표시되며, 이 팝업 메뉴에서 복제 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="d75c8-140">진단 창을 숨기려면 아래로 스크롤하여 [진단 시스템 사용]의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="d75c8-141">애플리케이션 개발 중에 진단 창을 사용하도록 설정한 상태를 유지하여 성능을 모니터링한 다음, 프로덕션 또는 애플리케이션 데모 중에 이를 사용하지 않도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="d75c8-143">Control+Shift+B를 누르거나 파일->빌드 설정으로 차례로 이동하여 빌드 설정을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="d75c8-144">이 프로그램은 현재 PC, Mac 및 Linux 독립 실행형 플랫폼 아래에 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="d75c8-145">HoloLens 2 개발의 경우 플랫폼을 유니버설 Windows 플랫폼으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="d75c8-146">이를 선택하고 [플랫폼 전환]을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="d75c8-148">완료되면 [열려 있는 장면 추가] 상자를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="d75c8-149">이제 [검사기] 패널로 이동하여 아래 이미지와 같이[지원되는 가상 현실] 오른쪽의 확인란이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="d75c8-150">또한 아래 이미지와 같이 [장면/HLSharedProjectMain] 옆의 확인란도 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="d75c8-152">[검사기] 창의 [게시 설정] 섹션 아래에서 [기능]까지 아래로 스크롤하고, 다음 확인란이 표시되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="d75c8-154">나열된 사용자 지정 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="d75c8-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)(버전 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="d75c8-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="d75c8-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d75c8-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="d75c8-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d75c8-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="d75c8-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d75c8-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="d75c8-159">Azure Spatial Anchors용 Unity 프로젝트를 구성하는 방법을 미리 알아보려면 [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) 자습서 시리즈의 일부인 [Azure Spatial Anchors 시작](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) 자습서를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="d75c8-160">[프로젝트] 패널에서 Prefabs 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="d75c8-161">다음 단계에서는 몇 가지 프리팹을 장면에 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="d75c8-162">Prefabs 폴더에서 [디버그 창] 프리팹을 클릭하여 [계층 구조]로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="d75c8-163">완료되면 [파일]. [저장]을 차례로 클릭하거나 Control+S를 눌러 프로젝트를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="d75c8-165">프리팹을 클릭하면 TMP Essentials에 대한 정보를 요구하는 팝업이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="d75c8-166">필요에 따라 [TMP Essentials 가져오기]를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="d75c8-167">이 팝업이 표시되면 잠재적인 텍스트 관련 오류를 방지하기 위해 계층 구조에서 프리팹을 삭제하고 계층 구조로 다시 끌어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d75c8-169">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-169">Congratulations</span></span>

<span data-ttu-id="d75c8-170">이제 Photon에서 Unity 프로젝트를 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="d75c8-171">다음 자습서에서는 이 장면과 Unity 프로젝트를 기반으로 하여 전체 공유 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c8-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="d75c8-172">[다음 자습서: 3. 여러 사용자 연결](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="d75c8-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
