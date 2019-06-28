---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416124"
---
# <a name="setting-up-photon"></a><span data-ttu-id="a622b-104">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="a622b-104">Setting Up Photon</span></span>

<span data-ttu-id="a622b-105">이 단원에서는에서는 Unity 프로젝트로 Photon Unity 네트워킹 (예제)를 가져와서 공유 환경을 만들기 위한 준비 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="a622b-106">Photon 몇 가지 네트워킹 옵션 혼합 현실 개발자에 게 사용할 수 있는 공유 환경을 만들 수 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="a622b-107">에서는 Photon 계정을 만들려면 Photon을 가져오고 선택적 로컬 서버를 만드는 방법 설명</span><span class="sxs-lookup"><span data-stu-id="a622b-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="a622b-108">목표:</span><span class="sxs-lookup"><span data-stu-id="a622b-108">Objectives:</span></span>

* <span data-ttu-id="a622b-109">Photon 계정을 만드는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="a622b-110">찾기 및 Photon Unity 네트워킹을 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="a622b-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="a622b-111">로컬 Photon 서버 설정</span><span class="sxs-lookup"><span data-stu-id="a622b-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="a622b-112">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="a622b-112">Setting Up Photon</span></span>

1. <span data-ttu-id="a622b-113">설정 된 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정.</span><span class="sxs-lookup"><span data-stu-id="a622b-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="a622b-114">Photon 등록 페이지를 클릭 하 여 이동할 [이 링크](https://dashboard.photonengine.com/en-US/Account/SignUp)합니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="a622b-115">계정을 만들려면 등록 페이지의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="a622b-118">"새 앱 만들기" 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="a622b-120">"Photon 형식입니다." 아래에 있는 드롭다운 메뉴에서 "Photon 예제"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="a622b-121">그런 다음 이름을,이 예에서 "HoloLensPhotonProject." 라는 것</span><span class="sxs-lookup"><span data-stu-id="a622b-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="a622b-122">완료 되 면 "만들기" 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="a622b-124">작업이 완료 되 면 응용 프로그램 페이지로 돌아가서 아래 그림과 같은 결과가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="a622b-125">앱 ID를 클릭 하 고 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="a622b-126">붙여넣기가 쉽게 액세스할 수 있는 곳입니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="a622b-128">새 unity 프로젝트를 만들고 이름을 "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="a622b-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="a622b-129">새 Unity 프로젝트를 만드는 방법에 대 한 자세한 내용은를 참조 하십시오 [자료 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="a622b-130">아래 이미지에 표시 된 대로 "자산 저장소" 탭의 프로젝트 로드 되 면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="a622b-131">그런 다음 아래 이미지에서 강조 표시 하 고 검색 상자에 "예제"를 입력 하 고 검색 결과에서 "Photon 예제 2-무료" 자산을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="a622b-133">다운로드 하 고 있는 "다운로드" 및 "가져오기" 단추를 눌러이 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="a622b-135">Photon 가져오기 프로세스가 완료 되 면 예제 마법사가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="a622b-136">4 단계에서 응용 프로그램 ID (해야 하는 클립보드에)를 수행 하 고 AppID 상자에 붙여넣습니다. "설치 프로젝트" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="a622b-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="a622b-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="a622b-138">AppID를 성공적으로 추가한 후 "Photon"->"PhotonUnityNetworking"로 이동-> "리소스"-자산에 "PhotonServerSettings" > 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="a622b-139">"이름 서버 사용" 옵션을 선택 하 고 "당사" 또는 photon 서비스 지역이 고정된 지역 설정.</span><span class="sxs-lookup"><span data-stu-id="a622b-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a622b-141">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-141">Congratulations</span></span>

<span data-ttu-id="a622b-142">성공적으로 Photon 계정을 만들지, 로컬 Photon 서버를 설정 했으며 Unity에 예제를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="a622b-143">다음 단계는 프로젝트를 설정 하 고 여러 사용자가 작업을 볼 수 있도록 한 다음 다른 사용자와 연결을 허용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a622b-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="a622b-144">[다음 단원: Sharing(Photon) 단원 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="a622b-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

