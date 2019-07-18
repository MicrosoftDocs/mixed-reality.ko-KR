---
title: HoloLens 용 MR 학습 공유 모듈 2
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293622"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="ee254-104">Azure 공간 앵커 및 공유 환경</span><span class="sxs-lookup"><span data-stu-id="ee254-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="ee254-105">이 단원에서는 Azure 공간 앵커 (GLOBAL.ASA)를 공유 환경에 통합 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="ee254-106">모든 참가자가 동일한 물리적 위치에 있는 개체를 볼 수 있도록 실제 환경에서 가상 환경을 고정 하는 경우에는 여러 개의 공동 배치 된 장치에서 일반적인 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="ee254-107">이 단원을 계속 진행 하기 전에, Azure 계정 및 리소스를 만들고, Azure 계정 및 리소스를 만들고, Azure를 공유 환경에 통합 하기 전에 필요한 다른 기본 빌딩 블록을 설명 하는 GLOBAL.ASA 학습 모듈을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="ee254-108">목표로</span><span class="sxs-lookup"><span data-stu-id="ee254-108">Objectives:</span></span>

- <span data-ttu-id="ee254-109">다기능를 다중 장치 맞춤을 위한 공유 환경에 통합 하세요.</span><span class="sxs-lookup"><span data-stu-id="ee254-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="ee254-110">로컬 공유 환경의 컨텍스트에서가 작동 하는 방식에 대 한 기본 사항을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="ee254-111">지침</span><span class="sxs-lookup"><span data-stu-id="ee254-111">Instructions</span></span>

1. <span data-ttu-id="ee254-112">이전 단원 (컨트롤 + S)의 프로젝트를 저장 하 고 다시 필요할 때 더 쉽게 찾을 수 있도록 이름을 "HLSharedProjectMainPart5"로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="ee254-113">MixedRealityPlayspace 부모 개체 아래에서 TableAnchor prefab를 선택 하 고 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="ee254-115">프로젝트 뷰에서 자산-> 리소스-> Prefabs로 이동 하 고 SharedPlayground 개체의 맨 위에 TableAnchor를 끌어 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-115">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="ee254-116">MixedRealityPlayspace 부모 개체인 TableAnchor 개체를 확장 하 고 Buttons 개체도 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="ee254-118">이제 계층에서 ShareAzureAnchorButton를 선택 하 고 Inaspector 패널로 주목를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="ee254-119">아래 이미지에 표시 된 드롭다운 메뉴로 스크롤하고 AnchorModuleScript를 선택 하 고 ShareAnchorNetework ()를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="ee254-121">GetAzureAnchorButton (4 단계 참조)를 선택 하 고 주목를 검사기 패널로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="ee254-122">아래 이미지에 표시 된 드롭다운 메뉴로 스크롤하고 AnchorModuleScript를 선택 하 고 GetSharedAnchorNetwork ()를 클릭 한 다음 저장을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="ee254-124">공유 모듈을 테스트 하려면 azure 공간 앵커 세션을 시작 하 고 "Azure 앵커 만들기" 단추를 클릭 하 여 azure 앵커를 만들고 azure 앵커를 만들 때까지 대기 하는 "Azure GLOBAL.ASA 세션 시작" 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-124">To test the sharing module, click on the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button and wait for sometime for the azure anchor to get created.</span></span> <span data-ttu-id="ee254-125">Azure 앵커를 만든 후 "Azure 앵커 공유" 단추를 클릭 하 여 HoloLens에서 만든 azure 앵커를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-125">Once the azure anchor is created then click on the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="ee254-126">다른 HoloLens에서 공유 azure 앵커를 수신 하려면 "Azure GLOBAL.ASA 세션 시작"을 클릭 하 여 시작 하 고 현재 GLOBAL.ASA 세션을 확인 한 다음 "Azure 앵커 가져오기" 단추를 클릭 하 여 다른 HoloLens에서 공유 azure 앵커를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-126">To recieve the shared azure anchor in another HoloLens, click on the "Start Azure ASA Session" to start and get in to the current ASA session and click on "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="ee254-127">참고: 개별 단추에 대 한 해당 작업의 모든 세부 정보가 디버그 창에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-127">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ee254-128">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-128">Congratulations</span></span>

<span data-ttu-id="ee254-129">이 단원에서는 Azure의 강력한 새 공간 앵커를 통합 하 여 공유 환경에서 공동 배치 된 장치를 맞추는 방법에 대해 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="ee254-130">이 단원에서는 공유 모듈도 마무리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="ee254-131">새 Photon 계정을 설정 하 고, Photon 및 THIS를 새 Unity 응용 프로그램에 통합 하 고, 아바타 및 공유 개체를 구성 하 고, 마지막으로,를 사용 하 여 여러 참가자를 정렬 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="ee254-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

