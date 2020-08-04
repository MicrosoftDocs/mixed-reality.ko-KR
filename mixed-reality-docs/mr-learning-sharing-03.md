---
title: 다중 사용자 기능 자습서 - 3. 여러 사용자 연결
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376395"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="7abc6-105">3. 여러 사용자 연결</span><span class="sxs-lookup"><span data-stu-id="7abc6-105">3. Connecting multiple users</span></span>

<span data-ttu-id="7abc6-106">이 자습서에서는 라이브 공유 환경의 일부로 여러 사용자를 연결하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="7abc6-107">자습서를 마치면 여러 디바이스에서 앱을 실행하여 각 사용자가 다른 사용자의 아바타가 움직이는 것을 실시간으로 보게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-107">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="7abc6-108">목표</span><span class="sxs-lookup"><span data-stu-id="7abc6-108">Objectives</span></span>

* <span data-ttu-id="7abc6-109">공유 환경에서 여러 사용자를 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="7abc6-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="7abc6-110">장면 준비</span><span class="sxs-lookup"><span data-stu-id="7abc6-110">Preparing the scene</span></span>

<span data-ttu-id="7abc6-111">이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="7abc6-112">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** 폴더로 이동한 다음, 다음과 같은 프리팹을 클릭하고 Hierarchy 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="7abc6-113">**NetworkLobby** 프리팹</span><span class="sxs-lookup"><span data-stu-id="7abc6-113">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="7abc6-114">**SharedPlayground** 프리팹</span><span class="sxs-lookup"><span data-stu-id="7abc6-114">**SharedPlayground** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="7abc6-116">Project 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 이동한 다음, 다음과 같은 프리팹을 클릭하고 Hierarchy 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="7abc6-117">**DebugWindow** 프리팹</span><span class="sxs-lookup"><span data-stu-id="7abc6-117">**DebugWindow** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="7abc6-119">사용자 프리팹 만들기</span><span class="sxs-lookup"><span data-stu-id="7abc6-119">Creating the user prefab</span></span>

<span data-ttu-id="7abc6-120">이 섹션에서는 공유 환경의 사용자를 나타내는 데 사용할 프리팹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-120">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="7abc6-121">1. 사용자 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="7abc6-121">1. Create and configure the user</span></span>

<span data-ttu-id="7abc6-122">Hierarchy 창에서 빈 영역을 마우스 오른쪽 단추로 클릭하고 **Create Empty**를 선택하여 빈 개체를 장면에 추가하고 개체의 이름을 **PhotonUser**로 지정하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-122">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="7abc6-123">변환 **위치**는 X = 0, Y = 0, Z = 0으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-123">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="7abc6-125">Hierarchy 창에서 **PhotonUser** 개체를 선택한 다음, Inspector 창에서 **구성 요소 추가** 단추를 사용하여 **Photon User (Script)** 구성 요소를 PhotonUser 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-125">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="7abc6-127">Inspector 창에서 **Add Component** 단추를 사용하여 **Generic Net Sync (Script)** 구성 요소를 PhotonUser 개체에 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-127">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="7abc6-128">**Is User** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-128">Check the **Is User** checkbox</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="7abc6-130">Inspector 창에서 **Add Component** 단추를 사용하여 **Photon View (Script)** 구성 요소를 PhotonUser 개체에 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-130">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="7abc6-131">**Observed Components** 필드에 **Generic Net Sync(Script)** 구성 요소를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-131">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="7abc6-133">2. 아바타 만들기</span><span class="sxs-lookup"><span data-stu-id="7abc6-133">2. Create the avatar</span></span>

<span data-ttu-id="7abc6-134">Project 창에서 **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** 폴더로 이동하여 MRTK 자료를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-134">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="7abc6-135">그런 다음, Hierarchy 창에서 **PhotonUser** 개체를 마우스 오른쪽 단추로 클릭하고 **3D Object** > **Sphere**를 선택하여 PhotonUser 개체의 자식으로 구형 개체를 만들어서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-135">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="7abc6-136">변환 **Position**은 X = 0, Y = 0, Z = 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-136">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="7abc6-137">변환 **Scale**을 적절한 크기(예: X = 0.15, Y = 0.15, Z = 0.15)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-137">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="7abc6-138">MeshRenderer > Materials > **Element 0** 필드에 **MRTK_Standard_White** 자료를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-138">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="7abc6-140">3. 프리팹 만들기</span><span class="sxs-lookup"><span data-stu-id="7abc6-140">3. Create the prefab</span></span>

<span data-ttu-id="7abc6-141">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-141">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="7abc6-143">Resources 폴더를 선택한 상태에서 **PhotonUser** 개체를 Hierarchy 창에서 **Resources** 폴더로 **클릭하고 끌어서** PhotonUser 개체를 프리펩으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-143">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="7abc6-145">Hierarchy 창에서 **PhotonUser** 개체를 마우스 오른쪽 단추로 클릭하고 **Delete**를 선택하여 장면에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-145">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="7abc6-147">사용자 프리팹을 인스턴스화하도록 PUN 구성</span><span class="sxs-lookup"><span data-stu-id="7abc6-147">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="7abc6-148">이 섹션에서는 이전 섹션에서 만든 PhotonUser 프리펩을 사용하도록 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-148">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="7abc6-149">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-149">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="7abc6-150">Hierarchy 창에서 **NetworkLobby** 개체를 펼쳐서 **NetworkRoom** 자식 개체를 선택한 다음, Inspector 창에서 **Photon Room (Script)** 구성 요소를 찾아서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-150">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="7abc6-151">**Photon User Prefab** 필드에 Resources 폴더의 **PhotonUser** 프리팹을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-151">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="7abc6-153">여러 사용자 환경 체험</span><span class="sxs-lookup"><span data-stu-id="7abc6-153">Trying the experience with multiple users</span></span>

<span data-ttu-id="7abc6-154">Unity 프로젝트를 빌드하고 HoloLens에 배포했으면 Unity로 돌아가서 HoloLens에서 앱이 실행되는 동안 게임 모드로 들어갑니다. 머리(HoloLens)를 움직이면 HoloLens 사용자 아바타가 움직이는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-154">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="7abc6-156">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7abc6-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="7abc6-157">앱에서 Photon에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-157">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7abc6-158">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-158">Congratulations</span></span>

<span data-ttu-id="7abc6-159">여러 사용자가 동일한 환경에 연결하여 서로의 움직임을 볼 수 있도록 프로젝트를 구성하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-159">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="7abc6-160">다음 자습서에서는 개체의 움직임도 여러 디바이스에서 공유되도록 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="7abc6-160">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

[<span data-ttu-id="7abc6-161">다음 자습서: 4. 여러 사용자와 개체 이동 공유</span><span class="sxs-lookup"><span data-stu-id="7abc6-161">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
