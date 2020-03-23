---
title: 다중 사용자 기능 자습서 - 5. 공유 환경에 Azure Spatial Anchors 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031683"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="af337-105">5. 공유 환경에 Azure Spatial Anchors 통합</span><span class="sxs-lookup"><span data-stu-id="af337-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="af337-106">이 단원에서는 ASA(Azure Spatial Anchors)를 공유 환경에 통합하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="af337-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="af337-107">ASA를 사용하면 모든 참가자가 동일한 실제 위치에서 개체를 볼 수 있도록 물리적 환경에서 가상 환경을 고정하는 경우 공동 배치된 여러 개의 디바이스에서 공통 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af337-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="af337-108">목표</span><span class="sxs-lookup"><span data-stu-id="af337-108">Objectives</span></span>

* <span data-ttu-id="af337-109">다중 디바이스 맞춤을 위해 공유 환경에 ASA 통합</span><span class="sxs-lookup"><span data-stu-id="af337-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="af337-110">ASA가 로컬 공유 환경의 컨텍스트에서 작동하는 방법에 대한 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="af337-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="af337-111">지침</span><span class="sxs-lookup"><span data-stu-id="af337-111">Instructions</span></span>

1. <span data-ttu-id="af337-112">MixedRealityPlayspace 부모 개체 아래에서 TableAnchor 프리팹을 선택하고 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="af337-114">[프로젝트] 보기에서 Assets->Resources->Prefabs로 차례로 이동하고, TableAnchor 프리팹을 SharedPlayground 개체 위로 끌어서 자식 항목으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af337-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="af337-115">MixedRealityPlayspace 부모 개체, TableAnchor 개체, Buttons 개체를 차례로 펼칩니다.</span><span class="sxs-lookup"><span data-stu-id="af337-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="af337-117">이제 [계층 구조]에서 ShareAzureAnchorButton을 선택하고, 주의를 [검사기] 패널로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="af337-118">아래 이미지에 표시된 드롭다운 메뉴까지 아래로 스크롤하고, AnchorModuleScript를 선택하고, ShareAnchorNetwork()를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="af337-120">GetAzureAnchorButton(4단계 참조)을 선택하고, 주의를 [검사기] 패널로 다시 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="af337-121">아래 이미지에 표시된 드롭다운 메뉴까지 아래로 스크롤하고, AnchorModuleScript를 선택하고, GetSharedAnchorNetwork()를 클릭하고, 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="af337-123">4단계를 반복하여 StartAzureSession () 함수를 StartAzureSessionButton에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="af337-124">4단계를 반복하여 CreateAzureAnchor () 함수를 CreateAzureAnchorButton에 연결하고, TableAnchor 개체가 함수의 '게임 개체' 매개 변수 필드에 할당되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="af337-125">[Azure 리소스에 장면 연결](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) 지침에 따라 Azure Spatial Anchors 서비스 자격 증명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="af337-126">공유 모듈을 테스트하려면 "Azure ASA 세션 시작" 단추를 클릭하여 Azure Spatial Anchors 세션을 시작한 다음, "Azure 앵커 만들기" 단추를 클릭하여 Azure 앵커를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af337-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="af337-127">Azure 앵커가 만들어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="af337-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="af337-128">Azure 앵커가 만들어지면 "Azure 앵커 공유" 단추를 클릭하여 HoloLens에서 만든 Azure 앵커를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="af337-129">다른 HoloLens에서 공유 Azure 앵커를 받으려면 "Azure ASA 세션 시작"을 클릭하여 현재 ASA 세션을 시작하고 이 세션에 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="af337-130">다른 HoloLens에서 공유 Azure 앵커를 가져오려면 "Azure 앵커 가져오기" 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="af337-131">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="af337-131">Congratulations</span></span>

<span data-ttu-id="af337-132">이 단원에서는 Azure의 강력한 새 Spatial Anchors를 통합하여 공동 배치된 디바이스를 공유 환경에 맞추는 방법에 대해 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="af337-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="af337-133">이제 공유 모듈도 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="af337-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="af337-134">새 Photon 계정을 설정하고, Photon과 PUN을 새 Unity 애플리케이션에 통합하고, 아바타와 공유 개체를 구성하고, 마지막으로 ASA를 사용하여 여러 참가자를 맞추는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="af337-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
