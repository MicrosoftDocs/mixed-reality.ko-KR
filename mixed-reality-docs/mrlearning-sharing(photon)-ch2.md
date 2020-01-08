---
title: 다중 사용자 기능 자습서-2. Unity를 개발할 준비 하는 중
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 6840bcc583fe3e42dcaa6f42e71098f4dbe76f4c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334318"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="f340c-105">2. Unity를 개발할 준비 하는 중</span><span class="sxs-lookup"><span data-stu-id="f340c-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="f340c-106">이 자습서에서는 혼합 현실 도구 키트 가져오기, 빌드 설정 구성 및 장면 준비를 포함 하 여 응용 프로그램 개발을 위해 Unity를 준비 하 고 구성 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="f340c-107">목표</span><span class="sxs-lookup"><span data-stu-id="f340c-107">Objectives</span></span>

* <span data-ttu-id="f340c-108">응용 프로그램 개발을 위한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="f340c-108">Configure Unity for application development</span></span>
* <span data-ttu-id="f340c-109">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="f340c-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="f340c-110">프로젝트 장면 준비</span><span class="sxs-lookup"><span data-stu-id="f340c-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="f340c-111">지침</span><span class="sxs-lookup"><span data-stu-id="f340c-111">Instructions</span></span>

1. <span data-ttu-id="f340c-112">여기를 클릭 하 여 Mixed Reality Toolkit Foundation unity 패키지를 다운로드 하 고 저장 합니다 [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="f340c-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="f340c-113">Unity에서 자산 메뉴를 클릭 하 고 패키지 가져오기를 선택한 다음 사용자 지정 패키지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="f340c-115">1 단계에서 제공한 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="f340c-116">Unity에 가져오기 팝업 창이 표시 되 면 가져오기 단추를 클릭 하 여 MRTK 가져오기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="f340c-117">이 작업은 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="f340c-119">다운로드 된 패키지는 해당 파일을 저장 한 로컬 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="f340c-120">위의 이미지는 패키지를 찾을 위치를 표시 된다 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="f340c-121">새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-121">Create a new scene.</span></span> <span data-ttu-id="f340c-122">파일을 클릭 하 고 새 장면을 선택 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="f340c-123">HLSharedProjectMain로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="f340c-124">아래 이미지와 비슷한 팝업이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="f340c-125">지금은 아니요를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-125">For now, click No.</span></span>
    <span data-ttu-id="f340c-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f340c-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="f340c-127">Mixed Reality Toolkit에서 장면에 추가 및 구성을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="f340c-129">완료 되 면 프로필을 사용자 지정할 수 있는 새 구성 파일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="f340c-131">계층에서 혼합-현실 도구 키트 (MRTK)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="f340c-132">검사기 패널에서 Mixed Reality Toolkit 스크립트를 찾아 아래 그림에 표시 된 것 처럼 "& 사용자 지정 복사" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="f340c-133">이 작업 뒤에 pop가 나타나고 팝업 메뉴에서 복제 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="f340c-136">아래로 스크롤하여 진단 창을 숨기려면 진단 시스템 사용을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="f340c-137">응용 프로그램을 개발 하는 동안 진단 창을 사용 하도록 설정 하 여 성능을 모니터링 한 다음 프로덕션 또는 응용 프로그램 데모 중에 사용 하지 않도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="f340c-139">Ctrl + shift + B를 누르거나 파일 > 빌드 설정으로 이동 하 여 빌드 설정을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="f340c-140">프로그램은 현재 PC, Mac 및 Linux 독립 실행형 플랫폼 아래에 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="f340c-141">HoloLens 2 개발의 경우 플랫폼을 유니버설 Windows 플랫폼로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="f340c-142">선택한 후 플랫폼 전환을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="f340c-144">완료 되 면 열려 있는 장면 추가 라는 상자를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="f340c-145">이제 검사기 패널로 이동 하 여 지원 되는 가상 현실 오른쪽에 있는 확인란이 선택 되어 있는지 확인 합니다 (아래 이미지에 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="f340c-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="f340c-146">또한 아래 이미지에 나와 있는 것 처럼 장면/HLSharedProjectMain 옆의 확인란도 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="f340c-148">검사기 패널의 게시 설정 섹션에서 기능으로 스크롤하고 다음 확인란이 표시 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="f340c-150">표시 된 사용자 지정 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="f340c-151">a.</span><span class="sxs-lookup"><span data-stu-id="f340c-151">a.</span></span> [<span data-ttu-id="f340c-152">HoloLens2을 시작 했습니다. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="f340c-152">Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    <span data-ttu-id="f340c-153">b.</span><span class="sxs-lookup"><span data-stu-id="f340c-153">b.</span></span> [<span data-ttu-id="f340c-154">HoloLens2.2.1.0.0. unitypackage (영문)</span><span class="sxs-lookup"><span data-stu-id="f340c-154">Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    ><span data-ttu-id="f340c-155">[시작 자습서](mrlearning-base-ch1.md)를 완료 한 경우에도 HoloLens2 이라는 unity 패키지를 컴퓨터에 저장 했을 수 있습니다. _2.1.0.0. unitypackage_ 는 컴퓨터에 저장 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-155">If you have completed the [Getting started tutorials](mrlearning-base-ch1.md), you might still have the Unity package named _Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage_ stored on your computer.</span></span> <span data-ttu-id="f340c-156">그렇다면 위의 단계에 나열 된 자산 다운로드를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-156">If so, you can skip downloading the asset listed in step a above.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="f340c-158">프로젝트 패널에서 Prefabs 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-158">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="f340c-159">다음 단계에서는 장면에 몇 가지 prefabs을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-159">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="f340c-160">Prefabs 폴더에서 prefab, 디버그 창을 클릭 하 여 계층으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-160">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="f340c-161">완료 되 면 파일을 클릭 한 다음 저장을 클릭 하거나 ctrl + S를 눌러 프로젝트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-161">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="f340c-163">Prefab를 클릭 하면 TMP Essentials에 대 한 정보를 요청 하는 팝업이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-163">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="f340c-164">필요에 따라 TMP Essentials 가져오기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-164">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="f340c-165">이 팝업이 표시 되 면 계층 구조에서 prefab을 삭제 하 고 텍스트 관련 오류 발생을 방지 하기 위해 계층으로 다시 끌어 야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-165">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="f340c-167">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-167">Congratulations</span></span>

<span data-ttu-id="f340c-168">이제 Unity 프로젝트를 Photon 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-168">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="f340c-169">향후 자습서에서는이 장면 및 Unity 프로젝트를 전체 공유 환경에 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="f340c-169">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="f340c-170">[다음 자습서: 3. 여러 사용자 연결](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="f340c-170">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
