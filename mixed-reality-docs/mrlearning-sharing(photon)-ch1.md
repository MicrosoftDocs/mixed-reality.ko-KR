---
title: 다중 사용자 기능 자습서-1. Photon Unity 네트워킹 설정
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: d879144c7097d8b3873618f986b9f169e8553fa8
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553821"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="5d2c8-105">1. Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="5d2c8-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="5d2c8-106">개요</span><span class="sxs-lookup"><span data-stu-id="5d2c8-106">Overview</span></span>

<span data-ttu-id="5d2c8-107">이 자습서에서는 THIS (Photon Unity 네트워킹)를 Unity 프로젝트로 가져와 공유 환경을 만들기 위해 준비 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="5d2c8-108">Photon는 혼합 현실 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="5d2c8-109">Photon 계정을 만들고, Photon를 가져오고, 선택적 로컬 서버를 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="5d2c8-110">목표</span><span class="sxs-lookup"><span data-stu-id="5d2c8-110">Objectives</span></span>

* <span data-ttu-id="5d2c8-111">Photon 계정을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="5d2c8-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="5d2c8-112">Photon Unity 네트워킹을 찾고 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="5d2c8-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="5d2c8-113">로컬 Photon 서버 설정</span><span class="sxs-lookup"><span data-stu-id="5d2c8-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d2c8-114">필수 조건</span><span class="sxs-lookup"><span data-stu-id="5d2c8-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="5d2c8-115">[시작 자습서](mrlearning-base.md) 및 [Azure 공간 앵커로 시작 된 자습서](mrlearning-asa-ch1.md) 자습서 시리즈를 아직 완료 하지 않은 경우 해당 자습서를 먼저 완료 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="5d2c8-116">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="5d2c8-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="5d2c8-117">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="5d2c8-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="5d2c8-118">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="5d2c8-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="5d2c8-119">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="5d2c8-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="5d2c8-120">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="5d2c8-121">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="5d2c8-122">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="5d2c8-122">Setting up Photon</span></span>

1. <span data-ttu-id="5d2c8-123">[Photon](https://dashboard.photonengine.com//Account/SignUp) 계정을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="5d2c8-124">[이 링크](https://dashboard.photonengine.com//Account/SignUp)를 클릭 하 여 Photon 등록 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="5d2c8-125">등록 페이지의 지침에 따라 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="5d2c8-128">새 앱 만들기 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="5d2c8-130">드롭다운 메뉴의 Photon 형식에서 Photon THIS을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="5d2c8-131">그런 다음 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-131">Then give it a name.</span></span> <span data-ttu-id="5d2c8-132">이 예제에서는 HoloLensPhotonProject 라는 이름을 지정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="5d2c8-133">완료 되 면 만들기 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="5d2c8-135">응용 프로그램 페이지로 돌아가 아래 그림과 유사한 내용이 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="5d2c8-136">응용 프로그램 ID를 클릭 하 고 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-136">Click the application ID and copy it.</span></span> <span data-ttu-id="5d2c8-137">쉽게 액세스할 수 있는 위치에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="5d2c8-139">새 unity 프로젝트를 만들고 이름을 HLSharingProject로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="5d2c8-140">새 Unity 프로젝트를 만드는 방법에 대 한 지침은 [기본 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="5d2c8-141">프로젝트가 로드 되 면 아래 그림에 표시 된 것 처럼 자산 저장소 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="5d2c8-142">그런 다음 아래 이미지에 강조 표시 된 검색 상자에 THIS를 입력 하 고 검색 결과에서 Photon THIS 2-FREE "자산을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="5d2c8-144">다운로드 및 가져오기 단추를 눌러이 자산을 다운로드 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="5d2c8-146">Photon 가져오기 프로세스가 완료 되 면 This 마법사가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="5d2c8-147">4 단계에서 응용 프로그램 ID (클립보드에 있어야 함)를 사용 하 여 AppID 상자에 붙여넣은 다음 프로젝트 설치 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="5d2c8-149">AppID를 성공적으로 추가한 후 Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings (자산)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="5d2c8-150">이름 서버 사용 옵션을 선택 하 고 고정 지역을 US 또는 photon 서비스 지역으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="5d2c8-152">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-152">Congratulations</span></span>

<span data-ttu-id="5d2c8-153">Photon 계정을 성공적으로 만들고, 로컬 Photon 서버를 설정 하 고, THIS를 Unity로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="5d2c8-154">다음 단계는 여러 사용자가 작업을 볼 수 있도록 프로젝트를 설정 하 고 다른 사용자와의 연결을 허용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5d2c8-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="5d2c8-155">[다음 자습서: 2. Unity를 개발할 준비 하는 중](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="5d2c8-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
