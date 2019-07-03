---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523294"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="99555-104">Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="99555-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="99555-105">이 자습서에서는 Unity 프로젝트로 Photon Unity 네트워킹 (예제)를 가져와서 공유 환경을 만들기 위한 준비 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="99555-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="99555-106">Photon 몇 가지 네트워킹 옵션 혼합 현실 개발자에 게 사용할 수 있는 공유 환경을 만들 수 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="99555-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="99555-107">에서는 Photon 계정을 만들려면 Photon을 가져오고 선택적 로컬 서버를 만드는 방법 설명</span><span class="sxs-lookup"><span data-stu-id="99555-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="99555-108">목표:</span><span class="sxs-lookup"><span data-stu-id="99555-108">Objectives:</span></span>

* <span data-ttu-id="99555-109">Photon 계정을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="99555-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="99555-110">찾기 및 Photon Unity 네트워킹을 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="99555-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="99555-111">로컬 Photon 서버 설정</span><span class="sxs-lookup"><span data-stu-id="99555-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="99555-112">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="99555-112">Setting up Photon</span></span>

1. <span data-ttu-id="99555-113">설정 된 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정.</span><span class="sxs-lookup"><span data-stu-id="99555-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="99555-114">Photon 등록 페이지를 클릭 하 여 이동할 [이 링크](https://dashboard.photonengine.com/en-US/Account/SignUp)합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="99555-115">계정을 만들려면 등록 페이지의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="99555-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="99555-118">새 앱 단추 만들기를 클릭 하 여 응용 프로그램 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="99555-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="99555-120">Photon 예제 Photon 형식 아래에서 드롭다운 메뉴에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="99555-121">그런 다음 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-121">Then give it a name.</span></span> <span data-ttu-id="99555-122">이 예에서는 라는 HoloLensPhotonProject 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="99555-123">완료 되 면 만들기 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="99555-125">작업이 완료 되 면 응용 프로그램 페이지로 돌아가서 아래 그림과 같은 결과가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99555-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="99555-126">응용 프로그램 ID를 클릭 하 고 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="99555-127">붙여넣기가 쉽게 액세스할 수 있는 곳입니다.</span><span class="sxs-lookup"><span data-stu-id="99555-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="99555-129">새 unity 프로젝트를 만들고 HLSharingProject 라는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="99555-130">새 Unity 프로젝트를 만드는 방법에 대 한 자세한 내용은를 참조 하십시오 [자료 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="99555-131">아래 이미지에 나와 있는 것 처럼 자산 저장소 탭의 프로젝트 로드 되 면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="99555-132">검색 결과에서 그런 다음 아래 이미지에서 강조 표시 하 고 검색 상자에 예제를 입력 한 Photon 예제 2-빈도 선택"자산입니다.</span><span class="sxs-lookup"><span data-stu-id="99555-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="99555-134">다운로드 하 고 다운로드 및 가져오기 단추를 눌러이 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="99555-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="99555-136">Photon 가져오기 프로세스가 완료 되 면 예제 마법사가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="99555-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="99555-137">4 단계에서 응용 프로그램 ID (해야 하는 클립보드에)를 수행 하 고 AppID 상자에 붙여넣습니다. 설치 프로젝트 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="99555-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="99555-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="99555-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="99555-139">Photon AppID를 성공적으로 추가한 후 이동할 PhotonUnityNetworking->-> 리소스에는 자산에 PhotonServerSettings-> 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="99555-140">옵션을 사용 하 여 이름 서버를 선택 하 고 우리에 게 고정 된 지역 또는 yourPphoton 서비스 지역 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="99555-142">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="99555-142">Congratulations</span></span>

<span data-ttu-id="99555-143">성공적으로 Photon 계정을 만들지, 로컬 Photon 서버를 설정 했으며 Unity에 예제를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="99555-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="99555-144">다음 단계는 프로젝트를 설정 하 고 여러 사용자가 작업을 볼 수 있도록 한 다음 다른 사용자와 연결을 허용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="99555-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="99555-145">[다음 자습서의 경우: Unity 개발을 위한 준비](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="99555-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

