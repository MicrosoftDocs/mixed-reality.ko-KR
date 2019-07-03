# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="76c29-101">Unity 개발을 위한 준비</span><span class="sxs-lookup"><span data-stu-id="76c29-101">Getting Unity ready for development</span></span> 

<span data-ttu-id="76c29-102">이 자습서에서는 준비 하 고 응용 프로그램 개발, 혼합 현실 도구 키트 가져오기, 빌드 설정을 구성 하 고이 장면 준비를 포함 하 여 Unity를 구성 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-102">In this tutorial, we learn how to prepare and configure Unity for applicaiton development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="76c29-103">목표:</span><span class="sxs-lookup"><span data-stu-id="76c29-103">Objectives:</span></span>

- <span data-ttu-id="76c29-104">응용 프로그램 개발에 대 한 Unity를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-104">Configure Unity for applicaiton development</span></span>

- <span data-ttu-id="76c29-105">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="76c29-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="76c29-106">프로젝트 장면 준비</span><span class="sxs-lookup"><span data-stu-id="76c29-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="76c29-107">지침</span><span class="sxs-lookup"><span data-stu-id="76c29-107">Instructions</span></span>

1. <span data-ttu-id="76c29-108">다운로드 하 고 클릭 하 여 혼합 현실 Toolkit unity 패키지를 저장 [여기 있습니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="76c29-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="76c29-109">Unity에서 패키지 가져오기 자산 메뉴를 클릭 하 고 선택한 사용자 지정 패키지에 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="76c29-111">1 단계에서 제공 된 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="76c29-112">Unity에서 가져오기 팝업 창이 표시 되 면 가져오기를 시작 하려면 [가져오기] 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="76c29-113">가져오기는 MRTK 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="76c29-115">참고: 다운로드 한 패키지 파일을 저장 한 로컬 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="76c29-116">위의 이미지에서 패키지를 찾을 수 있습니다 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="76c29-117">새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-117">Create a new scene.</span></span> <span data-ttu-id="76c29-118">이 수 하면 파일을 클릭 하 고 새 장면을 선택 하 여 ").</span><span class="sxs-lookup"><span data-stu-id="76c29-118">Tthis can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="76c29-119">장면 HLSharedProjectMain로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="76c29-120">참고: 아래 이미지와 비슷하게 보이는 팝업을 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="76c29-121">이제 클릭 아니요.</span><span class="sxs-lookup"><span data-stu-id="76c29-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="76c29-123">혼합 현실 도구 키트에서 장면 및 구성에 추가 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="76c29-125">완료 되 면 새 구성 파일을 표시, 프로필을 사용자 지정할 수 있는 옵션이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="76c29-126">복사를 클릭 하 고 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-126">Click Copy and Customize.</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="76c29-130">아래로 스크롤하여 진단 창 숨기려는 경우 Siagnostics 사용 시스템의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-130">Scroll down and uncheck Enable Siagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="76c29-131">진단 창이 성능을 모니터링 하려면 응용 프로그램 개발 중 사용 하도록 설정 하 고 프로덕션 또는 응용 프로그램 데모 중 해제 상태로 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-131">We recommend keeping the diagnostics window enabled during applicaiton development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="76c29-133">열린 컨트롤 + shift + B를 누르거나 파일을 이동 하 여 빌드 설정-> 빌드 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="76c29-134">프로그램이 독립 실행형 PC, Mac 및 Linux 플랫폼에서 현재 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="76c29-135">HoloLens 2 개발에 대 한 유니버설 Windows 플랫폼으로 플랫폼을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="76c29-136">선택 하 고 플랫폼 전환을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-136">Select it and click Switch Platform.</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="76c29-138">완료 되 면 상자를 열고 백그라운드에서 추가 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="76c29-139">이제 검사기 패널로 이동 하 고 가상 현실 지원 (아래 이미지에 표시 됨)는 오른쪽에 있는 확인란이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="76c29-140">또한 아래 이미지에 표시 된 대로 장면을/HLSharedProjectMain 옆의 확인란도 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="76c29-142">검사기 창에서 게시 설정 섹션에서 기능을 스크롤하고 다음 확인란 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="76c29-144">다운로드할 수 있는 SharingAssetCollection 라는 사용자 지정 패키지를 가져올 [여기.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="76c29-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="76c29-145">프로젝트 패널에서 Prefabs 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-145">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="76c29-146">다음 몇 단계에서 몇 가지 prefabs 장면에 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-146">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="76c29-147">Prefabs 폴더에서 클릭 하 고 계층 안으로 DebugWindow prefab을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-147">In the Prefabs folder, click and drag the prefab, DebugWindow into the hierarchy.</span></span> <span data-ttu-id="76c29-148">완료 되 면 clckin 파일에서 프로젝트를 저장 한 다음 저장 하거나 컨트롤 + S를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-148">Once finished, save the project by clckin File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="76c29-150">참고: 클릭 하면 prefab, TMP Essentials에 대 한 요청을 표시 하는 팝업을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-150">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="76c29-151">필요에 따라 가져오기 TMP Essentials를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-151">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="76c29-152">이 팝업이 나타나면 해야를 prefab 계층 구조에서 삭제를 다시 잠재적인 텍스트 관련 오류를 방지 하려면 계층으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-152">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="76c29-154">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-154">Congratulations</span></span>

<span data-ttu-id="76c29-155">Unity 프로젝트 Photon 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-155">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="76c29-156">향후 자습서에서는이 장면 및 전체 공유 경험을 위해 Unity 프로젝트에 빌드 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="76c29-156">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="76c29-157">[다음 자습서의 경우: 여러 사용자를 연결합니다.](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="76c29-157">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

