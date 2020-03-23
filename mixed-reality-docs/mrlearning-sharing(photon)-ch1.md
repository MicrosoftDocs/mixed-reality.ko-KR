---
title: 다중 사용자 기능 자습서 - 1. Photon Unity 네트워킹 설정
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031336"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="9ffc9-105">1. Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="9ffc9-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="9ffc9-106">개요</span><span class="sxs-lookup"><span data-stu-id="9ffc9-106">Overview</span></span>

<span data-ttu-id="9ffc9-107">이 자습서에서는 PUN(Photon Unity 네트워킹)을 Unity 프로젝트로 가져와서 공유 환경을 만들기 위해 준비하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="9ffc9-108">Photon은 Mixed Reality 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="9ffc9-109">Photon 계정을 만들고, Photon을 가져오고, 필요에 따라 로컬 서버를 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="9ffc9-110">목표</span><span class="sxs-lookup"><span data-stu-id="9ffc9-110">Objectives</span></span>

* <span data-ttu-id="9ffc9-111">Photon 계정을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="9ffc9-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="9ffc9-112">Photon Unity 네트워킹을 찾고 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="9ffc9-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="9ffc9-113">로컬 Photon 서버 설정</span><span class="sxs-lookup"><span data-stu-id="9ffc9-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ffc9-114">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="9ffc9-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="9ffc9-115">[시작 자습서](mrlearning-base.md) 및 [Azure Spatial Anchors 시작 자습서](mrlearning-asa-ch1.md) 시리즈를 아직 시작하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="9ffc9-116">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="9ffc9-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9ffc9-117">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="9ffc9-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9ffc9-118">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="9ffc9-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="9ffc9-119">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="9ffc9-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="9ffc9-120">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="9ffc9-121">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="9ffc9-122">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="9ffc9-122">Setting up Photon</span></span>

1. <span data-ttu-id="9ffc9-123">[Photon](https://dashboard.photonengine.com//Account/SignUp) 계정을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="9ffc9-124">[이 링크](https://dashboard.photonengine.com//Account/SignUp)를 클릭하여 Photon 가입 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="9ffc9-125">가입 페이지의 지침에 따라 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="9ffc9-128">[새 앱 만들기] 단추를 클릭하여 애플리케이션 ID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="9ffc9-130">[Photon 유형] 아래의 드롭다운 메뉴에서 Photon PUN을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="9ffc9-131">그런 다음, 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-131">Then give it a name.</span></span> <span data-ttu-id="9ffc9-132">이 예에서는 HoloLensPhotonProject라는 이름을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="9ffc9-133">완료되면 [만들기] 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="9ffc9-135">애플리케이션 페이지로 돌아가면 아래 그림과 비슷하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="9ffc9-136">애플리케이션 ID를 클릭하여 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-136">Click the application ID and copy it.</span></span> <span data-ttu-id="9ffc9-137">이를 쉽게 액세스할 수 있는 위치에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="9ffc9-139">새 Unity 프로젝트를 만들고, HLSharingProject라는 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="9ffc9-140">새 Unity 프로젝트를 만드는 방법에 대한 지침은 [기본 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="9ffc9-141">프로젝트가 로드되면 아래 이미지와 같이 [자산 저장소] 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="9ffc9-142">그런 다음, 아래 이미지에서 강조 표시된 검색 상자에서 PUN을 입력하고, 검색 결과에서 "Photon PUN 2 - FREE" 자산을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="9ffc9-144">[다운로드] 및 [가져오기] 단추를 눌러 이 자산을 다운로드하고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="9ffc9-146">Photon에서 가져오기 프로세스가 완료되면 Pun 마법사가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="9ffc9-147">4단계에서 애플리케이션 ID(클립보드에 있음)를 가져와서 AppID 상자에 붙여넣고 [프로젝트 설정] 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="9ffc9-149">AppID가 성공적으로 추가되면 Assets에서 Photon->PhotonUnityNetworking->Resources->PhotonServerSettings으로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="9ffc9-150">[이름 서버 사용] 옵션을 선택하고, 고정 지역을 미국 또는 Photon 서비스 지역으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="9ffc9-152">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-152">Congratulations</span></span>

<span data-ttu-id="9ffc9-153">Photon 계정을 성공적으로 만들고, 로컬 Photon 서버를 설정하고, PUN을 Unity로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="9ffc9-154">다음 단계는 여러 사용자가 작업을 볼 수 있도록 프로젝트를 설정하고 다른 사용자와의 연결을 허용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9ffc9-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="9ffc9-155">[다음 자습서: 2. Unity 개발 준비](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="9ffc9-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
