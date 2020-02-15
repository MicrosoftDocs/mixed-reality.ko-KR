---
title: Azure 공간 앵커 자습서-3. Azure 공간 고정 피드백 표시
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: f4f609a71b05a52e8761e282763a540b42e9f7f5
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250706"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="56a32-105">3. Azure 공간 고정 피드백 표시</span><span class="sxs-lookup"><span data-stu-id="56a32-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="56a32-106">이 자습서에서는 사용자에 게 Azure 공간 앵커 (GLOBAL.ASA)를 사용할 때 앵커 검색, 이벤트 및 상태에 대 한 피드백을 제공 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="56a32-107">목표</span><span class="sxs-lookup"><span data-stu-id="56a32-107">Objectives</span></span>

* <span data-ttu-id="56a32-108">현재 GLOBAL.ASA 세션에 대 한 중요 한 정보를 표시 하는 UI 패널을 설정 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="56a32-109">사용자가 사용자에 게 사용할 수 있도록 하는 사용자 의견 요소 이해 및 탐색</span><span class="sxs-lookup"><span data-stu-id="56a32-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="56a32-110">사용자 의견 피드백 설정 UI 패널</span><span class="sxs-lookup"><span data-stu-id="56a32-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="56a32-111">계층 창에서 **textcontent** 개체 > **지침** 을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체** \*\* > 선택 하 여 TextMeshPro\*\* Text 개체를 명령 > Textcontent 개체의 자식으로 만들고 **사용자 의견**등의 적절 한 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-기본](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="56a32-113">장면에서 작업을 더 쉽게 수행 하려면 개체 왼쪽의 눈 모양 아이콘을 클릭 하 여 ParentAnchor 개체의 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 여부</a> 를 꺼짐으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="56a32-114">이렇게 하면 게임 내 표시를 변경 하지 않고 장면 창에서 개체를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="56a32-115">**사용자 의견** 개체를 선택한 상태에서 검사기 창의 위치와 크기를 변경 하 여 명령 텍스트 아래에 깔끔하게 배치 되도록 합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="56a32-116">Rect Transform **Pos Y** 를-0.24로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="56a32-117">Rect 변환 **너비** 를 0.555으로 변경</span><span class="sxs-lookup"><span data-stu-id="56a32-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="56a32-118">Rect 변환 **높이** 를 0.1으로 변경</span><span class="sxs-lookup"><span data-stu-id="56a32-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="56a32-119">그런 다음 텍스트를 텍스트 영역 내에 깔끔하게 맞추기 위해 글꼴 속성을 선택 합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="56a32-120">텍스트 메시 Pro (스크립트) **글꼴 스타일** 을 굵게 변경</span><span class="sxs-lookup"><span data-stu-id="56a32-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="56a32-121">텍스트 메시 Pro (스크립트) **글꼴 크기** 를 0.17으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="56a32-122">텍스트 메시 Pro (스크립트) **맞춤** 을 가운데 및 중간으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-기본](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="56a32-124">**사용자 의견** 개체를 선택한 상태에서 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 피드백 개체에 **앵커 피드백 스크립트 (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-기본](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="56a32-126">**사용자** 의견 개체를 **앵커 피드백 스크립트 (스크립트)** 구성 요소의 **피드백 텍스트** 필드에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-126">Assign the **Feedback** object to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-기본](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="56a32-128">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-128">Congratulations</span></span>

<span data-ttu-id="56a32-129">이 자습서에서는 사용자에 게 실시간 피드백을 제공 하기 위해 Azure 공간 고정 환경의 현재 상태를 표시 하는 UI 패널을 만드는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="56a32-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
