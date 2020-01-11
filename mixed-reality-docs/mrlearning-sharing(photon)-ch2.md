---
title: 다중 사용자 기능 자습서-2. Unity를 개발할 준비 하는 중
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 6abf4fa8fc87afc7007d6f7c76becfbd88ed7a12
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901512"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="751b4-105">2. Unity를 개발할 준비 하는 중</span><span class="sxs-lookup"><span data-stu-id="751b4-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="751b4-106">이 자습서에서는 혼합 현실 도구 키트 가져오기, 빌드 설정 구성 및 장면 준비를 포함 하 여 응용 프로그램 개발을 위해 Unity를 준비 하 고 구성 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="751b4-107">목표</span><span class="sxs-lookup"><span data-stu-id="751b4-107">Objectives</span></span>

* <span data-ttu-id="751b4-108">응용 프로그램 개발을 위한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="751b4-108">Configure Unity for application development</span></span>
* <span data-ttu-id="751b4-109">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="751b4-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="751b4-110">프로젝트 장면 준비</span><span class="sxs-lookup"><span data-stu-id="751b4-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="751b4-111">지침</span><span class="sxs-lookup"><span data-stu-id="751b4-111">Instructions</span></span>

1. <span data-ttu-id="751b4-112">여기를 클릭 하 여 Mixed Reality Toolkit Foundation unity 패키지를 다운로드 하 고 저장 합니다 [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="751b4-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="751b4-113">Unity에서 자산 메뉴를 클릭 하 고 패키지 가져오기를 선택한 다음 사용자 지정 패키지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="751b4-115">1 단계에서 제공한 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="751b4-116">Unity에 가져오기 팝업 창이 표시 되 면 가져오기 단추를 클릭 하 여 MRTK 가져오기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="751b4-117">이 작업은 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="751b4-119">다운로드 된 패키지는 해당 파일을 저장 한 로컬 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="751b4-120">위의 이미지는 패키지를 찾을 위치를 표시 된다 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="751b4-121">새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-121">Create a new scene.</span></span> <span data-ttu-id="751b4-122">파일을 클릭 하 고 새 장면을 선택 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="751b4-123">HLSharedProjectMain로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="751b4-124">아래 이미지와 비슷한 팝업이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="751b4-125">지금은 아니요를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-125">For now, click No.</span></span>
    <span data-ttu-id="751b4-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="751b4-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="751b4-127">Mixed Reality Toolkit에서 장면에 추가 및 구성을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="751b4-129">완료 되 면 프로필을 사용자 지정할 수 있는 새 구성 파일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="751b4-131">계층에서 혼합-현실 도구 키트 (MRTK)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="751b4-132">검사기 패널에서 Mixed Reality Toolkit 스크립트를 찾아 아래 그림에 표시 된 것 처럼 "& 사용자 지정 복사" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="751b4-133">이 작업 뒤에 pop가 나타나고 팝업 메뉴에서 복제 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="751b4-136">아래로 스크롤하여 진단 창을 숨기려면 진단 시스템 사용을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="751b4-137">응용 프로그램을 개발 하는 동안 진단 창을 사용 하도록 설정 하 여 성능을 모니터링 한 다음 프로덕션 또는 응용 프로그램 데모 중에 사용 하지 않도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="751b4-139">Ctrl + shift + B를 누르거나 파일 > 빌드 설정으로 이동 하 여 빌드 설정을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="751b4-140">프로그램은 현재 PC, Mac 및 Linux 독립 실행형 플랫폼 아래에 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="751b4-141">HoloLens 2 개발의 경우 플랫폼을 유니버설 Windows 플랫폼로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="751b4-142">선택한 후 플랫폼 전환을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="751b4-144">완료 되 면 열려 있는 장면 추가 라는 상자를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="751b4-145">이제 검사기 패널로 이동 하 여 지원 되는 가상 현실 오른쪽에 있는 확인란이 선택 되어 있는지 확인 합니다 (아래 이미지에 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="751b4-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="751b4-146">또한 아래 이미지에 나와 있는 것 처럼 장면/HLSharedProjectMain 옆의 확인란도 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="751b4-148">검사기 패널의 게시 설정 섹션에서 기능으로 스크롤하고 다음 확인란이 표시 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="751b4-150">표시 된 사용자 지정 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="751b4-151">a.</span><span class="sxs-lookup"><span data-stu-id="751b4-151">a.</span></span> <span data-ttu-id="751b4-152">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (버전 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="751b4-152">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>

    <span data-ttu-id="751b4-153">b.</span><span class="sxs-lookup"><span data-stu-id="751b4-153">b.</span></span> [<span data-ttu-id="751b4-154">MRTK. HoloLens2.2.1.0.1. unitypackage를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)

    <span data-ttu-id="751b4-155">c.</span><span class="sxs-lookup"><span data-stu-id="751b4-155">c.</span></span> [<span data-ttu-id="751b4-156">MRTK. HoloLens2 AzureSpatialAnchors. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="751b4-156">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

    <span data-ttu-id="751b4-157">d.</span><span class="sxs-lookup"><span data-stu-id="751b4-157">d.</span></span> [<span data-ttu-id="751b4-158">MRTK. HoloLens2.2.1.0.1. unitypackage를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="751b4-159">Azure 공간 앵커에 대 한 Unity 프로젝트를 구성 하는 방법에 대 한 미리 알림은 azure 공간 [앵커](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) 자습서 시리즈의 일부인 [azure 공간 앵커 시작](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) 자습서를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="751b4-161">프로젝트 패널에서 Prefabs 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-161">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="751b4-162">다음 단계에서는 장면에 몇 가지 prefabs을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-162">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="751b4-163">Prefabs 폴더에서 prefab, 디버그 창을 클릭 하 여 계층으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-163">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="751b4-164">완료 되 면 파일을 클릭 한 다음 저장을 클릭 하거나 ctrl + S를 눌러 프로젝트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-164">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="751b4-166">Prefab를 클릭 하면 TMP Essentials에 대 한 정보를 요청 하는 팝업이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-166">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="751b4-167">필요에 따라 TMP Essentials 가져오기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-167">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="751b4-168">이 팝업이 표시 되 면 계층 구조에서 prefab을 삭제 하 고 텍스트 관련 오류 발생을 방지 하기 위해 계층으로 다시 끌어 야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-168">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="751b4-170">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-170">Congratulations</span></span>

<span data-ttu-id="751b4-171">이제 Unity 프로젝트를 Photon 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-171">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="751b4-172">향후 자습서에서는이 장면 및 Unity 프로젝트를 전체 공유 환경에 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="751b4-172">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="751b4-173">[다음 자습서: 3. 여러 사용자 연결](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="751b4-173">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
