<span data-ttu-id="a466c-101">**Unity 개발을 위한 준비**</span><span class="sxs-lookup"><span data-stu-id="a466c-101">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="a466c-102">이 단원에서는 준비, 혼합 현실 도구 키트를 가져오기 하 고, 빌드 설정을 구성 하 고,이 장면 준비를 포함 하 여 앱 개발을 위해 Unity를 구성 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-102">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="a466c-103">목표:</span><span class="sxs-lookup"><span data-stu-id="a466c-103">Objectives:</span></span>

- <span data-ttu-id="a466c-104">앱 개발에 대 한 Unity를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-104">Configure Unity for app development</span></span>

- <span data-ttu-id="a466c-105">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="a466c-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="a466c-106">프로젝트 장면 준비</span><span class="sxs-lookup"><span data-stu-id="a466c-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="a466c-107">지침</span><span class="sxs-lookup"><span data-stu-id="a466c-107">Instructions</span></span>

1. <span data-ttu-id="a466c-108">다운로드 하 고 클릭 하 여 혼합 현실 Toolkit unity 패키지를 저장 [여기 있습니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="a466c-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="a466c-109">Unity에서 자산 메뉴 및 "패키지 가져오기," 선택 클릭 "사용자 지정 패키지입니다."</span><span class="sxs-lookup"><span data-stu-id="a466c-109">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="a466c-111">1 단계에서 제공 된 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="a466c-112">Unity에서 가져오기 팝업 창이 표시 되 면 가져오기를 시작 하려면 [가져오기] 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-112">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="a466c-113">가져오기는 MRTK 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="a466c-115">참고: 파일을 저장 한 로컬 폴더에 다운로드 한 패키지가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-115">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="a466c-116">위의 이미지에서 패키지를 찾을 수 있습니다 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="a466c-117">(이 가능 "file"을 클릭 하 고 "새 장면을"를 선택 하 여) 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-117">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="a466c-118">장면 "HLSharedProjectMain."로 저장</span><span class="sxs-lookup"><span data-stu-id="a466c-118">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="a466c-119">참고: 아래 이미지와 비슷하게 보이는 팝업을 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-119">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="a466c-120">이제 클릭 "아니요"</span><span class="sxs-lookup"><span data-stu-id="a466c-120">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="a466c-122">"혼합 현실 Toolkit" 클릭 "장면에 추가 및 구성"에서</span><span class="sxs-lookup"><span data-stu-id="a466c-122">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="a466c-124">완료 되 면 새 구성 파일을 나타납니다 프로필에 맞게 선택할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-124">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="a466c-125">"복사 및 사용자 지정 합니다."를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-125">Click "copy and customize."</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="a466c-129">아래로 스크롤하여 "사용" 진단 시스템 진단 창을 숨기려면 싶다면의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-129">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="a466c-130">진단 창이 성능을 모니터링 하려면 앱 개발 동안 사용 하도록 설정 하 고 프로덕션 또는 응용 프로그램 데모 중 해제 상태로 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-130">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="a466c-132">컨트롤 + shift + B를 눌러 또는 파일로 이동 하 여 빌드 설정 > 빌드 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-132">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="a466c-133">프로그램 "PC, Mac 및 Linux 독립 실행형" 플랫폼에서 현재 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-133">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="a466c-134">HoloLens 2 개발을 위한 플랫폼 "유니버설 Windows 플랫폼"으로 설정</span><span class="sxs-lookup"><span data-stu-id="a466c-134">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="a466c-135">선택 하 고 "플랫폼 전환 합니다." 클릭</span><span class="sxs-lookup"><span data-stu-id="a466c-135">Select it and click "switch platform."</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="a466c-137">완료 되 면 "open 장면을 추가 합니다." 라는 상자를 클릭</span><span class="sxs-lookup"><span data-stu-id="a466c-137">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="a466c-138">이제 검사기 패널로 이동 하 고 (아래 이미지에 표시 된)으로 "지원 되는 가상 reality"의 오른쪽에 확인란을 했는지 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-138">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="a466c-139">또한 아래 이미지에 표시 된 대로 "장면/HLSharedProjectMain" 옆의 확인란 선택도 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-139">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="a466c-141">검사기 패널 스크롤합니다 "기능" 섹션에서 "게시 설정" 하 고 다음 확인란 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-141">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="a466c-143">다운로드할 수 있는 "SharingAssetCollection" 라는 사용자 지정 패키지를 가져올 [여기.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="a466c-143">Import the custom package called "SharingAssetCollection" which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="a466c-144">이제 프로젝트 패널에서 이동 "prefabs" 폴더에 다음 몇 단계에서 구현 장면에 몇 가지 prefabs 하므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-144">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="a466c-145">"Prefabs" 폴더에서 클릭 하 고 prefab, "DebugWindow" 계층으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-145">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="a466c-146">완료 되 면 프로젝트를 저장 합니다 (파일을 저장 한 다음 클릭 또는 컨트롤 + S를 눌러)</span><span class="sxs-lookup"><span data-stu-id="a466c-146">Once finished, save the project (click file, then save, or press control+S)</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="a466c-148">참고: 클릭 하면 prefab, TMP Essentials에 대 한 요청을 표시 하는 팝업을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-148">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="a466c-149">필요한 경우는 "가져오기 TMP Essentials"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-149">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="a466c-150">이 팝업이 나타나면 해야를 prefab 계층 구조에서 삭제를 다시 잠재적인 텍스트 관련 오류를 방지 하려면 계층으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-150">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="a466c-152">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-152">Congratulations</span></span>

<span data-ttu-id="a466c-153">Unity 프로젝트 Photon 준비가 완료 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="a466c-153">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="a466c-154">앞 단원에서는이 장면 및 전체 공유 경험을 위해 Unity 프로젝트에 빌드 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a466c-154">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="a466c-155">[다음 단원: Sharing(Photon) 단원 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="a466c-155">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

