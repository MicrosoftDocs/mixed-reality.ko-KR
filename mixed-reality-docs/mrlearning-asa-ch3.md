---
title: Azure 공간 앵커 자습서-3. Azure 공간 고정 피드백 표시
description: 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 9f57cb9874aade2d6b19d0c061fd83eb04b9ef11
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914378"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="a1128-105">3. Azure 공간 고정 피드백 표시</span><span class="sxs-lookup"><span data-stu-id="a1128-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="a1128-106">이 단원에서는 Azure 공간 앵커를 사용할 때 앵커 검색, 이벤트 및 상태에 대 한 피드백을 사용자에 게 제공 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="a1128-107">목표</span><span class="sxs-lookup"><span data-stu-id="a1128-107">Objectives</span></span>

* <span data-ttu-id="a1128-108">현재 GLOBAL.ASA 세션에 대 한 중요 한 정보를 표시 하는 UI 패널을 설정 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="a1128-109">사용자가 사용자에 게 사용할 수 있도록 하는 사용자 의견 요소 이해 및 탐색</span><span class="sxs-lookup"><span data-stu-id="a1128-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="a1128-110">지침</span><span class="sxs-lookup"><span data-stu-id="a1128-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="a1128-111">사용자 의견 피드백 설정 UI 패널</span><span class="sxs-lookup"><span data-stu-id="a1128-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="a1128-112">이 단원에서는 "SaveAnchorToDisk" 및 "ShareAnchor" 단추를 사용 하지 않으므로 두 단추를 모두 선택 하 고 아래와 같이 검사기 패널에서 확인란의 선택을 취소 하 여 이러한 단추를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="a1128-114">명령 패널을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-114">Create the instruction panel.</span></span> <span data-ttu-id="a1128-115">"명령" 단추를 마우스 오른쪽 단추로 클릭 하 고 "3D 개체"를 마우스로 가리킨 다음 "textmeshpro"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="a1128-117">장면의 지침과 일치 하도록 텍스트의 크기와 위치를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="a1128-118">또한 모든 텍스트의 맞춤이 가운데 맞춤 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="a1128-119">그런 다음 아래 이미지에 나와 있는 것 처럼 텍스트 편집기에서 샘플 텍스트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="a1128-121">TextMeshPro 개체의 이름을 "FeedbackPanel"로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="a1128-123">ASA_feedback 계층 구조에서 "feedbackpanel" 텍스트를 선택 했는지 확인 하 고 "구성 요소 추가"를 클릭 한 다음, 표시 되 면이를 검색 하 고 선택 하 여 앵커 피드백 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-123">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="a1128-125">아래 그림에 표시 된 것 처럼 ASA_Feedback 계층 구조에서 스크립트 아래의 빈 슬롯으로 "feedbackPanel" 텍스트 개체를 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-125">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a1128-127">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-127">Congratulations</span></span>

<span data-ttu-id="a1128-128">이 단원에서는 사용자에 게 실시간 피드백을 제공 하기 위해 Azure 공간 고정 환경의 현재 상태를 표시 하는 UI 패널을 만드는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="a1128-128">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


