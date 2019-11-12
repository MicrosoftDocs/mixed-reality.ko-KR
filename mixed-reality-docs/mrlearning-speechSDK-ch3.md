---
title: Azure Speech Services 자습서-3. Azure Cognitive Services speech translation 구성 요소 추가
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913204"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="5f2cd-105">3. Azure Cognitive Services speech translation 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="5f2cd-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="5f2cd-106">이 자습서에서는 프로젝트의 Azure Cognitive Services Speech Translation 구성 요소에 대해 알아보고 세 가지 언어로 번역 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="5f2cd-107">지침</span><span class="sxs-lookup"><span data-stu-id="5f2cd-107">Instructions</span></span>

1. <span data-ttu-id="5f2cd-108">계층에서 Lunarcom_Base 개체를 선택 하 고 검사기 패널에서 구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="5f2cd-109">Lunarcom 변환 인식기를 검색 하 고 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="5f2cd-111">오프 라인 모드 시뮬레이터를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="5f2cd-113">이동 하기 전에 음성 SDK 변환기를 테스트 하기 전에 위의 그림에 나와 있는 것 처럼 오프 라인 모드 시뮬레이터를 사용 하지 않도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-113">Before moving on, ensure the offline mode simulator is disabled, as shown in the image above, before testing the Speech-SDK translator.</span></span> <span data-ttu-id="5f2cd-114">변환 하려면 인터넷에 연결 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="5f2cd-115">Lunarcom 변환 인식기에서 드롭다운을 클릭 하 고 번역 하려는 언어를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="5f2cd-117">이제 응용 프로그램을 실행 하 고 위성 단추를 클릭 하 여 변환기를 테스트 하 고 말하기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="5f2cd-118">인식을 중지 하려면 위성 단추를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="5f2cd-119">다음은 장면이 표시 되는 모양의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="5f2cd-120">"대상 언어" 드롭다운 (위의 이미지 참조)에서 언어를 자유롭게 변경 하 여 다른 언어로 번역을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="5f2cd-121">다음은 장면이 표시 되는 모양의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="5f2cd-123">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-123">Congratulations</span></span>

<span data-ttu-id="5f2cd-124">이제 프로젝트는 말하는 단어를 여러 언어로 번역할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-124">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="5f2cd-125">자유롭게 언어를 사용 하 고 번역의 정확도를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f2cd-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="5f2cd-126">다음 자습서: 4. 의도 및 자연어 이해 설정</span><span class="sxs-lookup"><span data-stu-id="5f2cd-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
