---
title: 다중 사용자 기능 자습서 - 4. 여러 사용자와 개체 움직임 공유
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cd8f0cb8888e7225566acc8c4b26aced3e4d977e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306254"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="8a83a-105">4. 여러 사용자와 개체 움직임 공유</span><span class="sxs-lookup"><span data-stu-id="8a83a-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="8a83a-106">이 자습서에서는 공유 환경의 모든 참가자가 협업하고 서로의 상호 작용을 볼 수 있도록 개체의 움직임을 공유하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="8a83a-107">목표</span><span class="sxs-lookup"><span data-stu-id="8a83a-107">Objectives</span></span>

* <span data-ttu-id="8a83a-108">개체의 움직임을 공유하도록 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="8a83a-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="8a83a-109">기본 다중 사용자 협업 앱을 빌드하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="8a83a-109">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="8a83a-110">장면 준비</span><span class="sxs-lookup"><span data-stu-id="8a83a-110">Preparing the scene</span></span>

<span data-ttu-id="8a83a-111">이 섹션에서는 자습서 프리팹을 추가하여 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="8a83a-112">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** 폴더로 이동하여 **TableAnchor** 프리팹을 Hierarchy 창의 **SharedPlayground** 개체로 끌어와서 SharedPlayground 개체의 자식으로 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="8a83a-114">개체를 인스턴스화하도록 PUN 구성</span><span class="sxs-lookup"><span data-stu-id="8a83a-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="8a83a-115">이 섹션에서는 [시작 자습서](mr-learning-base-01.md)에서 만든 Rover 탐색기 환경을 사용하도록 프로젝트를 구성하고 인스턴스화할 위치를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-115">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="8a83a-116">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="8a83a-117">Hierarchy 창에서 **NetworkLobby** 개체를 펼쳐서 **NetworkRoom** 자식 개체를 선택한 다음, Inspector 창에서 **Photon Room (Script)** 구성 요소를 찾아서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="8a83a-118">**Rover 탐색기 프리팹** 필드에 대해 리소스 폴더에서 **RoverExplorer_Complete_Variant** 프리팹을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-118">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="8a83a-120">**NetworkRoom** 자식 개체가 선택된 상태로 Hierarchy 창에서 **TableAnchor** 개체를 펼친 다음, Inspector 창에서 **Photon Room (Script)** 구성 요소를 찾아서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="8a83a-121">**Rocket 탐색기 위치** 필드에 대해 Hierarchy 창에서 TableAnchor > **Table** 자식 개체를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-121">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="8a83a-123">공유 개체 움직임 환경 체험</span><span class="sxs-lookup"><span data-stu-id="8a83a-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="8a83a-124">Unity 프로젝트를 빌드하고 HoloLens에 배포했으면 Unity로 돌아가서 HoloLens에서 앱이 실행되는 동안 재생 단추를 눌러 게임 모드로 들어갑니다. HoloLens에서 개체를 움직이면 Unity에서 개체가 움직이는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="8a83a-126">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-126">Congratulations</span></span>

<span data-ttu-id="8a83a-127">다른 사용자가 개체를 움직일 때 개체가 움직이는 것을 볼 수 있도록 개체 이동을 동기화하도록 프로젝트를 성공적으로 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-127">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="8a83a-128">다음 자습서에서는 실제 환경에 맞게 환경을 조정하는 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-128">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="8a83a-129">이렇게 하면 사용자가 실제 위치에서 서로 볼 수 있으므로 개체는 모든 사용자에 대해 동일한 물리적 위치와 회전에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a83a-129">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

[<span data-ttu-id="8a83a-130">다음 자습서: 5. 공유 환경에 Azure Spatial Anchors 통합</span><span class="sxs-lookup"><span data-stu-id="8a83a-130">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)
