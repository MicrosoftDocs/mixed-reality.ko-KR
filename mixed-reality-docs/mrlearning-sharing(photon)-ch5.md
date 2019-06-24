---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326453"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="e3850-104">Azure 공간 앵커 및 공유 환경이</span><span class="sxs-lookup"><span data-stu-id="e3850-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="e3850-105">이 단원에서는 공유 경험에 공간 앵커 ASA (Azure)를 통합 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="e3850-106">ASA에 대 한 일반적인 이해를 누른 경우 모든 참가자가 동일한 물리적 위치에서 개체를 볼 수 있도록 해당 실제 환경과 가상 고정 하려면 환경에 여러 배치 장치를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="e3850-107">이 단원에서는 진행 하기 전에 ASA 기본 사항, Azure 계정 및 리소스 만들기 및 공유 경험에 ASA 통합 수 전에 필요 없는 다른 기본 빌딩 블록 다룰 ASA 학습 모듈을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="e3850-108">목표:</span><span class="sxs-lookup"><span data-stu-id="e3850-108">Objectives:</span></span>

- <span data-ttu-id="e3850-109">ASA multi-device 맞춤에 대 한 공유 환경으로 통합</span><span class="sxs-lookup"><span data-stu-id="e3850-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="e3850-110">ASA 로컬 공유 환경의 컨텍스트에서 작동 하는 방법의 기본 사항 배우기</span><span class="sxs-lookup"><span data-stu-id="e3850-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="e3850-111">지침</span><span class="sxs-lookup"><span data-stu-id="e3850-111">Instructions</span></span>

1. <span data-ttu-id="e3850-112">이전 단원 (control + S)에서 프로젝트를 저장 하 고 쉽게 필요할 때 다시 찾을 수 있도록 "HLSharedProjectMainPart5.unity" 이름을 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="e3850-113">"MixedRealityPlayspace" 부모 개체 아래에 있는 TableAnchor prefab을 선택 하 여 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. <span data-ttu-id="e3850-115">이전 단원 중 일부와 마찬가지로 얻을 수 있는 새 사용자 지정 패키지를 가져올 [여기 있습니다.](placeholderlink)</span><span class="sxs-lookup"><span data-stu-id="e3850-115">Just like some of the previous lessons, import a new custom package that you can get [here.](placeholderlink)</span></span>

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. <span data-ttu-id="e3850-117">을 가져온 후 프로젝트 패널에서 "prefabs" 폴더에서 새로 업데이트 된 테이블 앵커 (이전 단계에서 가져온 unity 패키지)에서 가져올 놓습니다 부모 개체 "MixedRealityPlayspace."</span><span class="sxs-lookup"><span data-stu-id="e3850-117">Once it's imported, grab the newly updated table anchor (from the unity package imported in the previous step) from the "prefabs" folder in the project panel and drop it into the parent object "MixedRealityPlayspace."</span></span>

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. <span data-ttu-id="e3850-119">"MixedRealityPlayspace" 부모 개체를 "TableAnchor" 개체를 확장 하 고 "단추" 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-119">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. <span data-ttu-id="e3850-121">이제 계층의 "ShareAzureAnchorButton"를 선택 하 고 주의가 검사기 패널로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-121">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="e3850-122">아래 이미지에 표시 된 드롭다운 메뉴를 스크롤하십시오 "AnchorModuleScript"를 선택 하 고 "ShareAnchorNetework()." 클릭</span><span class="sxs-lookup"><span data-stu-id="e3850-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. <span data-ttu-id="e3850-124">6 단계와 마찬가지로 "GetAzureAnchorButton"를 선택 하 고 [관리자] 패널에 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-124">Much like step 6, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="e3850-125">아래 이미지에 표시 된 드롭다운 메뉴를 스크롤하십시오 "AnchorModuleScript"를 선택 하 고 "GetSharedAnchorNetwork()." 클릭</span><span class="sxs-lookup"><span data-stu-id="e3850-125">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="e3850-126">다음 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-126">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="e3850-128">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-128">Congratulations</span></span>

<span data-ttu-id="e3850-129">이 단원에서는 Azure의 강력한 새 공간 앵커 공유 환경에서 공동 배치 장치에 맞게 통합 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="e3850-130">이 단원에는 공유 모듈으로 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="e3850-131">아바타 및 공유 개체를 구성 하 고 마지막 ASA를 사용 하 여 여러 참가자를 맞추는 새 Photon 계정 설정, Photon 및 예제를 새 Unity 응용 프로그램을 통합 하는 방법을 알게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e3850-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

