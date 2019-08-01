---
title: 다중 사용자 기능 자습서-1. Photon Unity 네트워킹 설정
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: acb6966ace81180e95e6a0fe447d350572f7c0dd
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701966"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="f4354-105">1. Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="f4354-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="f4354-106">이 자습서에서는 THIS (Photon Unity 네트워킹)를 Unity 프로젝트로 가져와 공유 환경을 만들 준비를 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-106">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="f4354-107">Photon는 혼합 현실 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="f4354-108">Photon 계정을 만들고, Photon를 가져오고, 선택적 로컬 서버를 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-108">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="f4354-109">목표</span><span class="sxs-lookup"><span data-stu-id="f4354-109">Objectives</span></span>

* <span data-ttu-id="f4354-110">Photon 계정을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="f4354-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="f4354-111">Photon Unity 네트워킹을 찾고 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="f4354-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="f4354-112">로컬 Photon 서버 설정</span><span class="sxs-lookup"><span data-stu-id="f4354-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="f4354-113">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="f4354-113">Setting up Photon</span></span>

1. <span data-ttu-id="f4354-114">[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-114">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="f4354-115">[이 링크](https://dashboard.photonengine.com/en-US/Account/SignUp)를 클릭 하 여 Photon 등록 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="f4354-116">등록 페이지의 지침에 따라 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="f4354-119">새 앱 만들기 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="f4354-121">드롭다운 메뉴의 Photon 형식에서 Photon THIS을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="f4354-122">그런 다음 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-122">Then give it a name.</span></span> <span data-ttu-id="f4354-123">이 예제에서는 HoloLensPhotonProject 라는 이름을 지정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="f4354-124">완료 되 면 만들기 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="f4354-126">작업이 완료 되 면 응용 프로그램 페이지로 돌아가 아래 그림과 유사한 내용이 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-126">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="f4354-127">응용 프로그램 ID를 클릭 하 고 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-127">Click on the application ID and copy it.</span></span> <span data-ttu-id="f4354-128">쉽게 액세스할 수 있는 위치에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="f4354-130">새 unity 프로젝트를 만들고 이름을 HLSharingProject로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="f4354-131">새 Unity 프로젝트를 만드는 방법에 대 한 지침은 [기본 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f4354-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="f4354-132">프로젝트가 로드 되 면 아래 그림에 표시 된 것 처럼 자산 저장소 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-132">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="f4354-133">그런 다음 아래 이미지에 강조 표시 된 검색 상자에 THIS를 입력 하 고 검색 결과에서 Photon THIS 2-FREE "자산을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="f4354-135">다운로드 및 가져오기 단추를 눌러이 자산을 다운로드 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="f4354-137">Photon 가져오기 프로세스가 완료 되 면 This 마법사가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="f4354-138">4 단계에서 응용 프로그램 ID (클립보드에 있어야 함)를 가져와 AppID 상자에 붙여넣은 다음 프로젝트 설치 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-138">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="f4354-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f4354-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="f4354-140">AppID를 성공적으로 추가한 후 Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings (자산)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="f4354-141">이름 서버 사용 옵션을 선택 하 고 고정 지역을 US 또는 photon 서비스 지역으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="f4354-143">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-143">Congratulations</span></span>

<span data-ttu-id="f4354-144">Photon 계정을 성공적으로 만들고, 로컬 Photon 서버를 설정 하 고, THIS를 Unity로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="f4354-145">다음 단계는 여러 사용자가 작업을 볼 수 있도록 프로젝트를 설정 하 고 다른 사용자와의 연결을 허용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f4354-145">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="f4354-146">[다음 자습서: 2. Unity 개발 준비](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="f4354-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

