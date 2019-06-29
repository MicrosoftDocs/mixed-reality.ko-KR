---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465208"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="d8108-104">Azure 공간 앵커 및 공유 환경이</span><span class="sxs-lookup"><span data-stu-id="d8108-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="d8108-105">이 단원에서는 공유 경험에 공간 앵커 ASA (Azure)를 통합 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="d8108-106">ASA에는 여러 배치 장치를 공통 참조 인 경우 모든 참가자가 동일한 물리적 위치에서 개체를 볼 수 있도록 해당 실제 환경 앵커 가상 환경을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="d8108-107">이 단원에서는 진행 하기 전에 ASA 기본 사항, Azure 계정 및 리소스 만들기 및 공유 경험에 ASA 통합 수 전에 필요 없는 다른 기본 빌딩 블록 다룰 ASA 학습 모듈을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="d8108-108">목표:</span><span class="sxs-lookup"><span data-stu-id="d8108-108">Objectives:</span></span>

- <span data-ttu-id="d8108-109">ASA multi-device 맞춤에 대 한 공유 환경으로 통합</span><span class="sxs-lookup"><span data-stu-id="d8108-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="d8108-110">ASA 로컬 공유 환경의 컨텍스트에서 작동 하는 방법의 기본 사항 배우기</span><span class="sxs-lookup"><span data-stu-id="d8108-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="d8108-111">지침</span><span class="sxs-lookup"><span data-stu-id="d8108-111">Instructions</span></span>

1. <span data-ttu-id="d8108-112">이전 단원 (control + S)에서 프로젝트를 저장 하 고 쉽게 필요할 때 다시 찾을 수 있도록 "HLSharedProjectMainPart5.unity" 이름을 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="d8108-113">MixedRealityPlayspace 부모 개체 아래에 있는 TableAnchor prefab을 선택 하 여 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="d8108-115">자산 이동 리소스-> 프로젝트 뷰에서 자식 있도록 SharedPlayground 개체 위에 TableAnchor prefab을 끌어서 Prefabs,-> 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-115">In the Project view go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="d8108-116">MixedRealityPlayspace 부모 개체, TableAnchor 개체를 확장 하 고도 단추 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="d8108-118">이제 계층의 ShareAzureAnchorButton를 선택 하 고 주의가 Inaspector 패널로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="d8108-119">아래 이미지에 표시 된 드롭다운 메뉴를 스크롤하십시오 AnchorModuleScript를 선택 하 고 ShareAnchorNetework()를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="d8108-121">GetAzureAnchorButton 선택 (4 단계 참조) 하 고 [관리자] 패널에 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="d8108-122">아래 이미지에 표시 된 드롭다운 메뉴를 스크롤합니다 선택 AnchorModuleScript, 및 GetSharedAnchorNetwork()를 클릭 하 고 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="d8108-124">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-124">Congratulations</span></span>

<span data-ttu-id="d8108-125">이 단원에서는 Azure의 강력한 새 공간 앵커 공유 환경에서 공동 배치 장치에 맞게 통합 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-125">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="d8108-126">이 단원에는 공유 모듈으로 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-126">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="d8108-127">아바타 및 공유 개체를 구성 하 고 마지막 ASA를 사용 하 여 여러 참가자를 맞추는 새 Photon 계정 설정, Photon 및 예제를 새 Unity 응용 프로그램을 통합 하는 방법을 알게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d8108-127">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

