---
title: MR Learning ASA 모듈 2 HoloLens에 Azure 공간 앵커
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327098"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="2f972-104">Photon (수정 나 잘못 된 경우)</span><span class="sxs-lookup"><span data-stu-id="2f972-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="2f972-105">이 단원에서는</span><span class="sxs-lookup"><span data-stu-id="2f972-105">In this lesson,</span></span> 

<span data-ttu-id="2f972-106">목표:</span><span class="sxs-lookup"><span data-stu-id="2f972-106">Objectives:</span></span>

* <span data-ttu-id="2f972-107">에 대해 알아봅니다 ___ 하는 방법</span><span class="sxs-lookup"><span data-stu-id="2f972-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="2f972-108">에 대해 알아봅니다 ___ 하는 방법</span><span class="sxs-lookup"><span data-stu-id="2f972-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="2f972-109">지침</span><span class="sxs-lookup"><span data-stu-id="2f972-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="2f972-110">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="2f972-110">Setting Up Photon</span></span>

1. <span data-ttu-id="2f972-111">설정 된 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정.</span><span class="sxs-lookup"><span data-stu-id="2f972-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="2f972-112">이 전자 메일 imputing 및 몇 가지 확인 단계를 거치지 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="2f972-114">등록 하면 Sdk 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="2f972-115">해당 페이지에 있는 경우 "서버" 클릭 하 고 "자체 호스트 합니다." 라는 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="2f972-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="2f972-116">아래로 스크롤한 다음 하 고 "server" 두 번째 이미지 아래에 표시 된 대로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="2f972-119">"추가 정보입니다." 레이블이 지정 된을 표시할 입력란에 일으키는</span><span class="sxs-lookup"><span data-stu-id="2f972-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="2f972-120">계속 해 서 읽어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-120">Go ahead and read it.</span></span> <span data-ttu-id="2f972-121">완료 되 면 다운로드 하는 것 "downloadSDK" 옆에 있는 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="2f972-123">다운로드가 완료 되 면 폴더를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="2f972-124">SDK 폴더를 표시 합니다. 파일 탐색기 열리면 SDK 폴더를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="2f972-125">다음 단계 '서버입니다.' 라는 새 폴더를 만들고 windows c: 드라이브를 이동 하는 것</span><span class="sxs-lookup"><span data-stu-id="2f972-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="2f972-127">이제 폴더를 열고 앞에서 복사한 SDK 폴더에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="2f972-129">완료 되 면 SDK 폴더를 열고 "배포" 다음 "bin_Win64 가"로 이동 하 고 "photon 컨트롤입니다."를 두 번 클릭</span><span class="sxs-lookup"><span data-stu-id="2f972-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="2f972-131">참고: 대부분의 프로그램 정보 (아래 이미지에 표시) 하는 대로 IP 주소에 대 한 질문이 나 다른 비슷한 질문이 있으면 도구 모음에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="2f972-133">서버를 설정 및 시작 했으므로 Photon 웹 사이트로 다시 이동 하 고 (아래 이미지에서는 boxed) 프로필 아이콘을 클릭 하 고 "응용 프로그램입니다."를 선택</span><span class="sxs-lookup"><span data-stu-id="2f972-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="2f972-135">"새 앱 만들기" 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="2f972-137">"Photon 형식입니다." 아래에 있는 드롭다운 메뉴에서 "Photon 실행" 선택</span><span class="sxs-lookup"><span data-stu-id="2f972-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="2f972-138">다음 (것을 기억해) 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="2f972-139">이 예에서는 이라는 "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="2f972-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="2f972-140">완료 되 면 "만들기"를 클릭</span><span class="sxs-lookup"><span data-stu-id="2f972-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="2f972-142">작업이 완료 되 면 응용 프로그램 페이지로 돌아가서 아래 그림과 같은 결과가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="2f972-143">앱 ID를 클릭 하 고 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="2f972-144">붙여넣기가 쉽게 액세스할 수 있는 곳입니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="2f972-146">새 unity 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-146">Create a new unity project.</span></span> <span data-ttu-id="2f972-147">Unity 허브를 열고 "new." 클릭</span><span class="sxs-lookup"><span data-stu-id="2f972-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="2f972-148">이름을 "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="2f972-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="2f972-149">클릭 한 다음 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-149">Then click create.</span></span> 

   > <span data-ttu-id="2f972-150">참고: 이 로드 하려면 최대 2 분 컴퓨터 속도에 따라를 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="2f972-152">참고: "위치" 옵션을 변경 하 여 컴퓨터에서 프로젝트를 저장할 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="2f972-153">기억 하 고 쉽게 액세스 하는 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="2f972-154">프로젝트 로드 되 면 클릭 "자산 저장소"입니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="2f972-155">그런 다음 아래 그림과에서 같이 검색 상자에 "예제"를 입력 하 고 "Photon 예제 2 무료" 자산을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="2f972-157">다운로드 및 가져오기!</span><span class="sxs-lookup"><span data-stu-id="2f972-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="2f972-159">**Unity 프로젝트 설정**</span><span class="sxs-lookup"><span data-stu-id="2f972-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="2f972-160">클릭 하 여 Unity의 Photon을 설정 하는 데 필요한 새 자산을 다운로드 [여기 있습니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="2f972-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="2f972-161">Unity에서 자산 메뉴 및 가져오기 자산을 "클릭"자산에 사용자 지정 합니다."</span><span class="sxs-lookup"><span data-stu-id="2f972-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="2f972-163">1 단계에서 제공 된 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="2f972-164">가져오기 단추에 표시 되 면 Unity 되 면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="2f972-166">참고: 찾을 있는 됩니다 패키지를 다운로드 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="2f972-167">위의 이미지에서 패키지를 찾을 수 있습니다 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="2f972-168">새 장면을 만드는 (컨트롤을 사용 하 여 / 명령 + 수 N 또는 "file"을 클릭 하 고 "새 장면을."를 선택 하 여).</span><span class="sxs-lookup"><span data-stu-id="2f972-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="2f972-169">장면 "HLSharedProjectMain."로 저장</span><span class="sxs-lookup"><span data-stu-id="2f972-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="2f972-170">참고: 아래 이미지와 비슷한 팝업이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="2f972-171">이제 클릭 "아니요"입니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="2f972-173">"혼합 현실 Toolkit" 클릭 "장면에 추가 및 구성"에서</span><span class="sxs-lookup"><span data-stu-id="2f972-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="2f972-175">완료 되 면 새 구성 파일을 나타납니다 프로필에 맞게 선택할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="2f972-176">"복사 및 사용자 지정 합니다."를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="2f972-178">아래로 스크롤하여 "진단 시스템을 사용 합니다." 선택을 취소합니다</span><span class="sxs-lookup"><span data-stu-id="2f972-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="2f972-179">이 쉽게이 프로젝트를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="2f972-181">빌드 설정 (control + shift + B)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="2f972-182">프로그램 "PC, Mac 및 Linux 독립 실행형" 플랫폼에서 현재 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="2f972-183">이 프로젝트에 플랫폼 "유니버설 windows 플랫폼입니다."으로 설정</span><span class="sxs-lookup"><span data-stu-id="2f972-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="2f972-184">선택 하 고 "플랫폼 전환 합니다." 클릭</span><span class="sxs-lookup"><span data-stu-id="2f972-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="2f972-186">완료 되 면 "open 장면을 추가 합니다." 라는 상자를 클릭</span><span class="sxs-lookup"><span data-stu-id="2f972-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="2f972-187">이제 검사기 패널로 이동 하 고 (아래 이미지에 표시 된)으로 "지원 되는 가상 reality"의 오른쪽에 확인란을 했는지 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="2f972-189">참고: 또한 "장면/HLSharedProjectMain" 옆의 확인란도 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="2f972-190">아래 검사기 패널에서 "게시 설정" "기능"까지 아래로 스크롤하여 다음 확인란만 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="2f972-191">인터넷 클라이언트</span><span class="sxs-lookup"><span data-stu-id="2f972-191">internet client</span></span>
- <span data-ttu-id="2f972-192">인터넷 클라이언트 서버</span><span class="sxs-lookup"><span data-stu-id="2f972-192">internet client server</span></span>
- <span data-ttu-id="2f972-193">개인 네트워크 클라이언트 서버</span><span class="sxs-lookup"><span data-stu-id="2f972-193">private network client server</span></span>
- <span data-ttu-id="2f972-194">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="2f972-194">camera/webcam</span></span>
- <span data-ttu-id="2f972-195">마이크</span><span class="sxs-lookup"><span data-stu-id="2f972-195">microphone</span></span>

21. <span data-ttu-id="2f972-196">12 단계와 마찬가지로 다음 단계는 "2 단원" [여기]. 다운로드할 수 있습니다를 호출 하는 다른 사용자 지정 패키지를 가져올 것 [lesson2.unitypackage 링크 위치] 해당 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="2f972-198">이제 프로젝트 패널에서 이동 "prefabs" 폴더에 다음 몇 단계에서 구현 장면에 몇 가지 prefabs 하므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="2f972-199">"Prefabs" 폴더에서 클릭 하 고 prefab, "DebugWindow" 계층으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="2f972-200">완료 되 면 프로젝트를 저장 합니다 (클릭 파일을 다음 저장 또는 컨트롤 + S)</span><span class="sxs-lookup"><span data-stu-id="2f972-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="2f972-202">참고: 클릭 하면 prefab, TMP Essentials에 대 한 요청을 표시 하는 팝업을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="2f972-203">필요한 경우는 "가져오기 TMP Essentials"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="2f972-205">**여러 사용자를 연결합니다.**</span><span class="sxs-lookup"><span data-stu-id="2f972-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="2f972-206">프로젝트 패널에서 "prefabs" 폴더에 22 단계와 같이 다음 단계에서 끌어서 놓기 "NetworkLobby" prefab 계층에는입니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="2f972-208">자식 prefab, "NetworkRoom." 표시 "NetworkLobby," 부모 prefab을 열어야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="2f972-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="2f972-209">검사기 패널로 이동 하 고 "구성 요소를 추가 합니다."를 클릭 후 선택</span><span class="sxs-lookup"><span data-stu-id="2f972-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="2f972-210">"PhotonView"를 검색 하 고 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="2f972-212">계층 구조 (계층 및 "empty" 선택에서 마우스 오른쪽 단추로 클릭)에서 새 빈 게임 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="2f972-213">위치를 x로 설정 해야 = 0, y = 0, z = 0 및 "PhotonUser." 개체 이름</span><span class="sxs-lookup"><span data-stu-id="2f972-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="2f972-215">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="2f972-215">Congratulations</span></span>



