---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327464"
---
# <a name="setting-up-photon"></a><span data-ttu-id="03e05-104">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="03e05-104">Setting Up Photon</span></span>

<span data-ttu-id="03e05-105">이 단원에서는에서는 Unity 프로젝트로 Photon Unity 네트워킹 (예제)를 가져와서 공유 환경을 만들기 위한 준비 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="03e05-106">Photon 몇 가지 네트워킹 옵션 혼합 현실 개발자에 게 사용할 수 있는 공유 환경을 만들 수 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="03e05-107">에서는 Photon 계정을 만들려면 Photon을 가져오고 선택적 로컬 서버를 만드는 방법 설명</span><span class="sxs-lookup"><span data-stu-id="03e05-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="03e05-108">목표:</span><span class="sxs-lookup"><span data-stu-id="03e05-108">Objectives:</span></span>

* <span data-ttu-id="03e05-109">Photon 계정을 만드는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="03e05-110">찾기 및 Photon Unity 네트워킹을 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="03e05-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="03e05-111">로컬 Photon 서버 설정</span><span class="sxs-lookup"><span data-stu-id="03e05-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="03e05-112">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="03e05-112">Setting Up Photon</span></span>

1. <span data-ttu-id="03e05-113">설정 된 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정.</span><span class="sxs-lookup"><span data-stu-id="03e05-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="03e05-114">Photon 등록 페이지를 클릭 하 여 이동할 [이 링크](https://dashboard.photonengine.com/en-US/Account/SignUp)합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="03e05-115">계정을 만들려면 등록 페이지의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="03e05-117">등록 하면 Sdk 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="03e05-118">해당 페이지에 있는 경우 "서버" 클릭 하 고 "자체 호스트 합니다." 라는 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="03e05-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="03e05-119">아래로 스크롤한 다음 하 고 "server" 두 번째 이미지 아래에 표시 된 대로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="03e05-122">"추가 정보입니다." 레이블이 지정 된을 표시할 입력란에 일으키는</span><span class="sxs-lookup"><span data-stu-id="03e05-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="03e05-123">계속 해 서 읽어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-123">Go ahead and read it.</span></span> <span data-ttu-id="03e05-124">완료 되 면 다운로드 하는 것 "downloadSDK" 옆에 있는 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="03e05-126">다운로드가 완료 되 면 폴더를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="03e05-127">SDK 폴더를 표시 합니다. 파일 탐색기 열리면 SDK 폴더를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="03e05-128">다음 단계 '서버입니다.' 라는 새 폴더를 만들고 windows c: 드라이브를 이동 하는 것</span><span class="sxs-lookup"><span data-stu-id="03e05-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="03e05-130">이제 폴더를 열고 앞에서 복사한 SDK 폴더에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="03e05-132">완료 되 면 SDK 폴더를 열고 "배포" 다음 "bin_Win64 가"로 이동 하 고 "photon 컨트롤입니다."를 두 번 클릭</span><span class="sxs-lookup"><span data-stu-id="03e05-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="03e05-134">참고: 대부분의 프로그램 정보 (아래 이미지에 표시) 하는 대로 IP 주소에 대 한 질문이 나 다른 비슷한 질문이 있으면 도구 모음에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="03e05-136">서버를 설정 및 시작 했으므로 Photon 웹 사이트로 다시 이동 하 고 여전히 등록 되어 있는지 확인 (또는 다시에 로그인 하지 않은 경우) (아래 이미지의 오른쪽 위 모서리의 boxed) 프로필 아이콘을 클릭 하 고 "응용 프로그램입니다."를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="03e05-138">"새 앱 만들기" 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="03e05-140">"Photon 형식입니다." 아래에 있는 드롭다운 메뉴에서 "Photon 예제"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="03e05-141">그런 다음 이름을,이 예에서 "HoloLensPhotonProject." 라는 것</span><span class="sxs-lookup"><span data-stu-id="03e05-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="03e05-142">완료 되 면 "만들기" 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="03e05-144">작업이 완료 되 면 응용 프로그램 페이지로 돌아가서 아래 그림과 같은 결과가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="03e05-145">앱 ID를 클릭 하 고 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="03e05-146">붙여넣기가 쉽게 액세스할 수 있는 곳입니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="03e05-148">새 unity 프로젝트를 만들고 이름을 "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="03e05-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="03e05-149">새 Unity 프로젝트를 만드는 방법에 대 한 자세한 내용은를 참조 하십시오 [자료 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="03e05-150">아래 이미지에 표시 된 대로 "자산 저장소" 탭의 프로젝트 로드 되 면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="03e05-151">그런 다음 아래 이미지에서 강조 표시 하 고 검색 상자에 "예제"를 입력 하 고 검색 결과에서 "Photon 예제 2 무료" 자산을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="03e05-153">다운로드 하 고 있는 "다운로드" 및 "가져오기" 단추를 눌러이 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="03e05-155">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-155">Congratulations</span></span>

<span data-ttu-id="03e05-156">성공적으로 Photon 계정을 만들지, 로컬 Photon 서버를 설정 했으며 Unity에 예제를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="03e05-157">다음 단계는 프로젝트를 설정 하 고 여러 사용자가 작업을 볼 수 있도록 한 다음 다른 사용자와 연결을 허용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="03e05-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="03e05-158">[다음 단원: Sharing(Photon) 단원 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="03e05-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

