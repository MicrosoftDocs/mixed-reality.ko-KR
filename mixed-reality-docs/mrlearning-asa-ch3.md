---
title: MR Learning ASA 모듈 HoloLens 2 Azure 공간 앵커
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326888"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="153b7-104">Azure 공간 앵커 피드백 표시</span><span class="sxs-lookup"><span data-stu-id="153b7-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="153b7-105">이 단원에서는 Azure 공간 앵커를 사용 하는 경우 앵커 검색, 이벤트 및 상태에 대 한 피드백을 사용 하 여 사용자에 게 제공 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="153b7-106">목표:</span><span class="sxs-lookup"><span data-stu-id="153b7-106">Objectives:</span></span>

* <span data-ttu-id="153b7-107">현재 ASA 세션에 대 한 중요 한 정보를 표시 하는 UI 패널을 설정 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="153b7-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="153b7-108">이해 및 탐색 ASA SDK를 사용할 수 있도록 사용자에 게 피드백 요소</span><span class="sxs-lookup"><span data-stu-id="153b7-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="153b7-109">지침</span><span class="sxs-lookup"><span data-stu-id="153b7-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="153b7-110">ASA 피드백 UI 패널 설정</span><span class="sxs-lookup"><span data-stu-id="153b7-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="153b7-111">이 단원에서는 "SaveAnchorToDisk"를 사용 하지 및 "ShareAnchor" 단추 하므로 두 단추를 선택 하 고 이러한 단추를 숨기려면 (아래와 같이) [관리자] 패널에 확인란을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="153b7-113">다음으로 명령 패널을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-113">Next, create the instruction panel.</span></span> <span data-ttu-id="153b7-114">"지침" 단추를 마우스 오른쪽 단추로 클릭 하 여 시작, "3D 개체" 및 "textmeshpro-텍스트 선택 합니다." 위로</span><span class="sxs-lookup"><span data-stu-id="153b7-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="153b7-116">규모 및 장면의 지침을 사용 하 여 일치 시킬 수 있도록 텍스트의 위치를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="153b7-117">또한 모든 텍스트의 맞춤을 가운데 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="153b7-118">그런 다음 아래 이미지에서에 표시 된 대로 텍스트 편집기에서 샘플 텍스트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="153b7-120">TextMeshPro 개체의 이름을 "FeedbackPanel."로 변경</span><span class="sxs-lookup"><span data-stu-id="153b7-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="153b7-122">프로젝트 패널에서 "자산"를 선택 합니다. 마우스 오른쪽 단추로 클릭 하 고 "탐색기에 표시 합니다." 선택</span><span class="sxs-lookup"><span data-stu-id="153b7-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="153b7-124">이제 클릭 [여기](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) 파일을 다운로드 하는 데 필요한 다음에서 몇 가지 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="153b7-125">탐색기가 열리면 "ASAmodulesAssets" 폴더 assets 폴더를 선택 하 고 앵커 피드백 스크립트와 앵커 모듈 스크립트 파일을 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="153b7-127">참고: 덮어쓰기를 선택 했는지 이전 덮어쓸지 아니면 이전 유지 하려는 경우 묻는 팝업이 표시 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="153b7-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="153b7-128">이제 Assets 폴더를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-128">Now return to the Assets folder.</span></span> <span data-ttu-id="153b7-129">그런 다음 "AzureSpatialAnchorsPlugin" 폴더 examples 폴더 및 scripts 폴더에 이동 하 고 Azure 공간 앵커 데모 래퍼를 해당 폴더로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="153b7-131">파일을 업로드 했으므로 ASA_feedback 계층 구조에서 "feedbackpanel" 텍스트 선택 되어 있는지 확인 한 "구성 요소 추가"를 클릭 하 고 앵커 피드백 스크립트에 대 한 검색 하 고 표시 되 면 선택 하 여 추가 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="153b7-133">아래 그림에 표시 된 대로 "feedbackPanel" 텍스트 개체를 ASA_Feedback 계층에서 아래 스크립트를 빈 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="153b7-135">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-135">Congratulations</span></span>

<span data-ttu-id="153b7-136">이 단원에서는 실시간 피드백을 사용 하 여 사용자를 제공 하는 데 Azure 공간 앵커 환경의 현재 상태를 표시 하려면 UI 패널을 만드는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="153b7-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


