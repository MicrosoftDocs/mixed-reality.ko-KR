---
title: 5. 단추 추가 및 체스 말 위치 초기화
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 자습서의 5부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 77fe2b59db970a2ac4b531d69efec6794478f7d5
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519995"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="678d7-104">5. 단추 추가 및 체스 말 위치 초기화</span><span class="sxs-lookup"><span data-stu-id="678d7-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="678d7-105">이 섹션에서는 계속해서 Mixed Reality Toolkit UX Tools 플러그 인의 기능을 시연하고 체스 앱의 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-105">This section continues demonstrating the capabilities of the Mixed Reality Toolkit UX Tools plugin and building out the features of your chess app.</span></span> <span data-ttu-id="678d7-106">새 기능을 만들고 현재 레벨에서 청사진으로 행위자의 참조를 가져오는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-106">You’ll create a new function and learn how to get references to Actors from your Level into a Blueprint.</span></span>

## <a name="objectives"></a><span data-ttu-id="678d7-107">목표</span><span class="sxs-lookup"><span data-stu-id="678d7-107">Objectives</span></span>

* <span data-ttu-id="678d7-108">프로젝트에 단추 추가</span><span class="sxs-lookup"><span data-stu-id="678d7-108">Add a button to your project</span></span>
* <span data-ttu-id="678d7-109">체스 말을 원래 위치로 보내는 새 "위치 초기화" 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="678d7-109">Create a new “Reset Location” function that sends a piece back to its original location</span></span>
* <span data-ttu-id="678d7-110">단추를 누르면 새로 만든 함수를 트리거하도록 단추 연결</span><span class="sxs-lookup"><span data-stu-id="678d7-110">Hook the button up to trigger the newly created function when pressed</span></span>

## <a name="create-a-function-to-reset-location"></a><span data-ttu-id="678d7-111">위치를 초기화하는 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="678d7-111">Create a function to reset location</span></span>

1.  <span data-ttu-id="678d7-112">**WhiteKing**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-112">Open **WhiteKing**.</span></span> <span data-ttu-id="678d7-113">**내 청사진** 패널에서 **함수** 섹션 옆에 있는 "+" 단추를 클릭하여 새 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-113">In the **My Blueprint** panel, click the “+” button next to the **Functions** section to create a new function.</span></span> <span data-ttu-id="678d7-114">이 함수 이름을 "위치 초기화"로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-114">Name this function “Reset Location”.</span></span> 

2.  <span data-ttu-id="678d7-115">새로 만든 **위치 초기화** 청사진에서 실행 핀을 청사진 그리드의 아무 위치로 끌어다 놓고 **SetActorRelativeTransform** 노드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-115">In your newly created **Reset Location** Blueprint, drag the execution pin and release anywhere on the Blueprint grid to call a **SetActorRelativeTransform** node.</span></span> <span data-ttu-id="678d7-116">이 함수는 부모를 기준으로 행위자의 변환(위치, 회전 및 배율)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="678d7-117">이 함수를 사용하여 보드에서 킹의 위치를 초기화할 것이며, 보드가 원래 위치에서 이동되었더라도 상관 없습니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-117">We’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> <span data-ttu-id="678d7-118">위치가 X =-26, Y = 4, Z = 0인 **변환 만들기** 노드를 만들고, 새 상대 변환 입력에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-118">Create a **Make Transform** node with Location X = -26, Y = 4, Z = 0, and connect it to the New Relative Transform input.</span></span> 

![위치 초기화 함수](images/unreal-uxt/5-function.PNG)

3.  <span data-ttu-id="678d7-120">**WhiteKing**을 컴파일하고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-120">Compile and Save **WhiteKing**.</span></span> <span data-ttu-id="678d7-121">주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-121">Return to the Main window.</span></span> 

## <a name="add-a-button"></a><span data-ttu-id="678d7-122">단추 추가</span><span class="sxs-lookup"><span data-stu-id="678d7-122">Add a button</span></span>

1.  <span data-ttu-id="678d7-123">**Blueprints** 폴더에서 SimpleButton을 서브클래스로 분류하는 새 청사진을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-123">In your **Blueprints** folder, create a new Blueprint that subclasses SimpleButton.</span></span> <span data-ttu-id="678d7-124">SimpleButton은 UX Tools 플러그 인의 일부로 제공되는 3D 단추 청사진 행위자입니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-124">SimpleButton is a 3D button Blueprint Actor that is provided as part of the UX Tools plugin.</span></span> <span data-ttu-id="678d7-125">이 단추의 이름을 "ResetButton"으로 지정하고 두 번 클릭하여 청사진을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-125">Name this button “ResetButton” and double click to open the Blueprint.</span></span> 

![SimpleButton의 새 청사진을 서브클래스로 분류](images/unreal-uxt/5-subclass.PNG)

2.  <span data-ttu-id="678d7-127">**구성 요소** 패널에서 **PressableButton(상속됨)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-127">In the **Components** panel, click on **PressableButton (Inherited)**.</span></span> <span data-ttu-id="678d7-128">[세부 정보] 패널에서 **이벤트** 섹션이 보일 때까지 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-128">In the Details panel, scroll until you see the **Events** section.</span></span> <span data-ttu-id="678d7-129">**단추를 누를 때** 옆에 있는 녹색 더하기 단추를 클릭합니다. 그러면 **단추를 누를 때** 이벤트가 이벤트 그래프에 추가되고, 단추를 누르면 이 이벤트가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-129">Click the green plus button next to **On Button Pressed**- this will add an **On Button Pressed** event to the Event Graph, which will be called when the button is pressed.</span></span> <span data-ttu-id="678d7-130">여기서 WhiteKing의 위치 초기화 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-130">From here, we’ll want to call our WhiteKing’s Reset Location function.</span></span> <span data-ttu-id="678d7-131">호출하려면 먼저 레벨에서 WhiteKing 행위자에 대한 참조를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-131">To do this, we’ll first need to get a reference to the WhiteKing Actor in our Level.</span></span> 

3.  <span data-ttu-id="678d7-132">**내 청사진** 패널에서 **변수** 섹션을 찾은 다음, **+** 단추를 클릭하여 새 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-132">In the **My Blueprint** panel, find the **Variables** section and click the **+** button to add a new variable.</span></span> <span data-ttu-id="678d7-133">이 변수의 이름을 "WhiteKing"으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-133">Name this variable “WhiteKing”.</span></span> <span data-ttu-id="678d7-134">[세부 정보] 패널에서 **변수 유형** 옆에 있는 드롭다운을 선택하고, "WhiteKing"을 검색하고, **개체 참조**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-134">In the Details panel, select the dropdown next to **Variable Type**, search for “WhiteKing”, and select the **Object Reference**.</span></span> <span data-ttu-id="678d7-135">마지막으로 **편집 가능한 인스턴스** 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-135">Finally, check the box next to **Instance Editable**.</span></span> <span data-ttu-id="678d7-136">이렇게 하면 기본 레벨에서 변수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-136">This will allow the variable to be set from the Main Level.</span></span> 

![변수 만들기](images/unreal-uxt/5-var.PNG)

4.  <span data-ttu-id="678d7-138">**내 청사진 > 변수**에 있는 WhiteKing 변수를 초기화 단추 이벤트 그래프로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-138">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph.</span></span> <span data-ttu-id="678d7-139">**WhiteKing 가져오기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-139">Choose **Get WhiteKing**.</span></span> 

5.  <span data-ttu-id="678d7-140">WhiteKing 출력 핀을 새 노드로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-140">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="678d7-141">**위치 초기화** 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-141">Select the **Reset Location** function.</span></span> <span data-ttu-id="678d7-142">마지막으로 **단추를 누를 때**의 나가는 실행 핀을 **위치 초기화**의 들어오는 실행 핀으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-142">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="678d7-143">ResetButton 청사진을 **컴파일**하고 **저장**한 다음, 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-143">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![단추를 누를 때 위치 초기화 함수 호출](images/unreal-uxt/5-callresetloc.PNG)

6.  <span data-ttu-id="678d7-145">**ResetButton**을 뷰포트로 끌어다 놓고 위치를 X = 50, Y =-25, Z = 10으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-145">Drag **ResetButton** into the viewport and set its location to X = 50, Y = -25, Z = 10.</span></span> <span data-ttu-id="678d7-146">**기본값**에서 WhiteKing 변수의 값을 **WhiteKing**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-146">Under **Default**, set the value of the WhiteKing variable to **WhiteKing**.</span></span>

![변수 설정](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="678d7-148">이제 잡을 수 있는 체스 말과 보드뿐 아니라 누르면 체스 말의 위치를 초기화하는 완전한 기능을 갖춘 단추를 사용하는 혼합 현실 앱이 생겼습니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-148">You now have a mixed reality app with a grabbable chess piece and board, as well as a fully functioning button that will reset the piece’s location when pressed.</span></span> <span data-ttu-id="678d7-149">이 시점까지 완료된 앱은 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="678d7-149">The completed app up to this point can be found on [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span></span> <span data-ttu-id="678d7-150">사용자가 단추를 누를 때 보드 전체를 초기화하도록, 이 자습서의 범위를 넘어서 나머지 체스 말을 자유롭게 설정해 보세요.</span><span class="sxs-lookup"><span data-stu-id="678d7-150">Feel free to go beyond this tutorial and set up the remainder of the chess pieces, so that the entire board is reset when the user presses the button.</span></span>

![뷰포트에서 장면 종료](images/unreal-uxt/5-endscene.PNG)

[<span data-ttu-id="678d7-152">다음 섹션: 6. 패키징 후 디바이스 또는 에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="678d7-152">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
