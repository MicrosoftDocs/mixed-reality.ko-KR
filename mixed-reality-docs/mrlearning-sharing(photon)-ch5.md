---
title: 다중 사용자 기능 자습서-5. 공유 환경에 Azure 공간 앵커 통합
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553811"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="23012-105">5. Azure 공간 앵커를 공유 환경에 통합</span><span class="sxs-lookup"><span data-stu-id="23012-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="23012-106">이 단원에서는 Azure 공간 앵커 (GLOBAL.ASA)를 공유 환경에 통합 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="23012-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="23012-107">모든 참가자가 동일한 물리적 위치에 있는 개체를 볼 수 있도록 실제 환경에서 가상 환경을 고정 하는 경우에는 여러 개의 공동 배치 된 장치에서 일반적인 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23012-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="23012-108">목표</span><span class="sxs-lookup"><span data-stu-id="23012-108">Objectives</span></span>

* <span data-ttu-id="23012-109">다기능를 다중 장치 맞춤을 위한 공유 환경에 통합 하세요.</span><span class="sxs-lookup"><span data-stu-id="23012-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="23012-110">로컬 공유 환경의 컨텍스트에서가 작동 하는 방식에 대 한 기본 사항을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="23012-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="23012-111">지침</span><span class="sxs-lookup"><span data-stu-id="23012-111">Instructions</span></span>

1. <span data-ttu-id="23012-112">MixedRealityPlayspace 부모 개체 아래에서 TableAnchor prefab를 선택 하 고 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="23012-114">프로젝트 뷰에서 자산-> 리소스-> Prefabs로 이동 하 고 SharedPlayground 개체의 맨 위에 TableAnchor를 끌어 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23012-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="23012-115">MixedRealityPlayspace 부모 개체인 TableAnchor 개체를 확장 하 고 Buttons 개체도 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="23012-117">이제 계층 구조에서 ShareAzureAnchorButton을 선택 하 고 주목를 검사기 패널로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="23012-118">아래 이미지에 표시 된 드롭다운 메뉴로 스크롤하고 AnchorModuleScript를 선택 하 고 ShareAnchorNetwork ()를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="23012-120">GetAzureAnchorButton (4 단계 참조)를 선택 하 고 주목를 검사기 패널로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="23012-121">아래 이미지에 표시 된 드롭다운 메뉴로 스크롤하고 AnchorModuleScript를 선택 하 고 GetSharedAnchorNetwork ()를 클릭 한 다음 저장을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="23012-123">4 단계를 반복 하 여 StartAzureSession () 함수를 StartAzureSessionButton에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="23012-124">4 단계를 반복 하 여 CreateAzureAnchor () 함수를 CreateAzureAnchorButton에 연결 하 고 TableAnchor 개체가 함수의 매개 변수 ' 게임 개체 ' 필드에 할당 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="23012-125">Azure [리소스에 장면 연결](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) 지침에 따라 Azure 공간 앵커 서비스 자격 증명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="23012-126">공유 모듈을 테스트 하려면 azure 공간 앵커 세션을 시작 하는 "Azure 만들기 세션 시작" 단추를 클릭 한 다음 "Azure 앵커 만들기" 단추를 클릭 하 여 azure 앵커를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23012-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="23012-127">Azure 앵커가 생성 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="23012-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="23012-128">Azure 앵커를 만든 후 "Azure 앵커 공유" 단추를 클릭 하 여 HoloLens에서 만든 azure 앵커를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="23012-129">다른 HoloLens에서 공유 azure 앵커를 수신 하려면 "Azure GLOBAL.ASA 세션 시작"을 클릭 하 여 현재 GLOBAL.ASA 세션을 시작 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="23012-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="23012-130">"Azure 앵커 가져오기" 단추를 클릭 하 여 다른 HoloLens에서 공유 azure 앵커를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="23012-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="23012-131">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="23012-131">Congratulations</span></span>

<span data-ttu-id="23012-132">이 단원에서는 Azure의 강력한 새 공간 앵커를 통합 하 여 공유 환경에서 공동 배치 된 장치를 맞추는 방법에 대해 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="23012-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="23012-133">이렇게 하면 공유 모듈도 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23012-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="23012-134">새 Photon 계정을 설정 하 고, Photon 및 THIS를 새 Unity 응용 프로그램에 통합 하 고, 아바타 및 공유 개체를 구성 하 고, 마지막으로,를 사용 하 여 여러 참가자를 정렬 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="23012-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
