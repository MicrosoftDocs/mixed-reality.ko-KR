### <a name="getting-unity-ready-for-development"></a><span data-ttu-id="bd5b3-101">Unity를 개발할 준비 하는 중</span><span class="sxs-lookup"><span data-stu-id="bd5b3-101">Getting Unity ready for development</span></span> 


<span data-ttu-id="bd5b3-102">이 자습서에서는 Mixed Reality Toolkit 가져오기, 빌드 설정 구성, 장면 준비를 포함 하 여 응용 프로그램 개발을 위해 Unity를 준비 하 고 구성 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-102">In this tutorial, we learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="bd5b3-103">목표로</span><span class="sxs-lookup"><span data-stu-id="bd5b3-103">Objectives:</span></span>

- <span data-ttu-id="bd5b3-104">응용 프로그램 개발을 위한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="bd5b3-104">Configure Unity for application development</span></span>

- <span data-ttu-id="bd5b3-105">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="bd5b3-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="bd5b3-106">프로젝트 장면 준비</span><span class="sxs-lookup"><span data-stu-id="bd5b3-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="bd5b3-107">지침</span><span class="sxs-lookup"><span data-stu-id="bd5b3-107">Instructions</span></span>

1. <span data-ttu-id="bd5b3-108">여기를 클릭 하 여 Mixed Reality Toolkit unity 패키지를 다운로드 하 고 저장 [합니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="bd5b3-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="bd5b3-109">Unity에서 자산 메뉴를 클릭 하 고 패키지 가져오기를 선택한 다음 사용자 지정 패키지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="bd5b3-111">1 단계에서 제공한 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="bd5b3-112">Unity에 가져오기 팝업 창이 표시 되 면 가져오기 단추를 클릭 하 여 가져오기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="bd5b3-113">MRTK를 가져오는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="bd5b3-115">참고: 다운로드 된 패키지는 파일을 저장 한 로컬 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="bd5b3-116">위의 이미지는 패키지를 찾을 위치를 표시 된다 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="bd5b3-117">새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-117">Create a new scene.</span></span> <span data-ttu-id="bd5b3-118">이 작업은 파일을 클릭 하 고 새 장면을 선택 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-118">This can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="bd5b3-119">장면을 HLSharedProjectMain로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="bd5b3-120">참고: 아래 이미지와 비슷한 팝업을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="bd5b3-121">지금은 아니요를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="bd5b3-123">Mixed Reality Toolkit에서 장면에 추가 및 구성을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="bd5b3-125">완료 되 면 프로필을 사용자 지정할 수 있는 새 구성 파일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="bd5b3-126">복사 및 사용자 지정을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-126">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="bd5b3-130">아래로 스크롤하여 진단 창을 숨기려면 진단 시스템 사용을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-130">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="bd5b3-131">응용 프로그램 개발 중에 진단 창을 사용 하도록 설정 하 여 성능을 모니터링 하 고 프로덕션 또는 응용 프로그램 데모 중에 사용 하지 않도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-131">We recommend keeping the diagnostics window enabled during application development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="bd5b3-133">Ctrl + shift + B를 누르거나 파일 > 빌드 설정으로 이동 하 여 빌드 설정을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="bd5b3-134">프로그램은 현재 PC, Mac 및 Linux 독립 실행형 플랫폼 아래에 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="bd5b3-135">HoloLens 2 개발의 경우 플랫폼을 유니버설 Windows 플랫폼로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="bd5b3-136">선택한 후 플랫폼 전환을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-136">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="bd5b3-138">완료 되 면 열려 있는 장면 추가 라는 상자를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="bd5b3-139">이제 검사기 패널로 이동 하 여 지원 되는 가상 현실 오른쪽에 있는 확인란이 선택 되어 있는지 확인 합니다 (아래 이미지에 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="bd5b3-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="bd5b3-140">또한 아래 그림에 표시 된 것 처럼 장면/HLSharedProjectMain 옆의 확인란도 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="bd5b3-142">검사기 패널의 게시 설정 섹션에서 기능으로 스크롤하고 다음 확인란이 표시 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="bd5b3-144">여기에서 다운로드할 수 있는 SharingAssetCollection 이라는 사용자 지정 패키지를 가져옵니다 [.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="bd5b3-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="bd5b3-146">프로젝트 패널에서 Prefabs 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-146">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="bd5b3-147">다음 몇 단계에서 장면에 몇 가지 prefabs 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-147">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="bd5b3-148">Prefabs 폴더에서 prefab, 디버그 창을 클릭 하 여 계층으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-148">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="bd5b3-149">완료 되 면 파일을 클릭 한 다음 저장을 클릭 하거나 ctrl + S를 눌러 프로젝트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-149">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="bd5b3-151">참고: Prefab를 클릭 하면 TMP Essentials에 대 한 정보를 요청 하는 팝업이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-151">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="bd5b3-152">필요에 따라 TMP Essentials 가져오기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-152">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="bd5b3-153">이 팝업이 표시 되 면 계층 구조에서 prefab을 삭제 하 고 텍스트 관련 오류 발생을 방지 하기 위해 계층으로 다시 끌어 야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-153">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="bd5b3-155">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-155">Congratulations</span></span>

<span data-ttu-id="bd5b3-156">이제 Unity 프로젝트를 Photon 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-156">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="bd5b3-157">향후 자습서에서는이 장면 및 Unity 프로젝트를 전체 공유 환경에 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd5b3-157">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="bd5b3-158">[다음 자습서: 여러 사용자 연결](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="bd5b3-158">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

