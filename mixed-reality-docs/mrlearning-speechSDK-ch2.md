---
title: Azure Speech Services 자습서 - 2. 로컬 음성-텍스트 변환을 위한 오프라인 모드 추가
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Speech SDK를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031616"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a><span data-ttu-id="102b1-105">2. 음성 인식을 사용하여 명령 실행</span><span class="sxs-lookup"><span data-stu-id="102b1-105">2. Using speech recognition to execute commands</span></span>

<span data-ttu-id="102b1-106">이 자습서에서는 Azure 음성 인식을 통해 사용자가 정의하는 단어 또는 구에 따라 작업을 수행할 수 있는 명령을 실행하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-106">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="102b1-107">목표</span><span class="sxs-lookup"><span data-stu-id="102b1-107">Objectives</span></span>

* <span data-ttu-id="102b1-108">Azure 음성 인식을 사용하여 명령을 실행하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="102b1-108">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="102b1-109">지침</span><span class="sxs-lookup"><span data-stu-id="102b1-109">Instructions</span></span>

<span data-ttu-id="102b1-110">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 실행 단어 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="102b1-111">**실행 단어** 필드에서 적절한 구를 입력합니다(예: _터미널 활성화_).</span><span class="sxs-lookup"><span data-stu-id="102b1-111">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="102b1-112">**해제 단어** 필드에서 적절한 구(예: _터미널 해제_)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-112">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="102b1-114">Lunarcom 실행 단어 인식기(스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-114">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="102b1-115">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-115">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="102b1-116">이전 자습서에서와 같이 이제 게임 모드로 들어가면 터미널 패널을 기본적으로 사용하도록 설정되어 있지만, **터미널 해제**라는 해제 단어를 말하여 터미널 패널을 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-116">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="102b1-118">그리고 **터미널 활성화**라는 실행 단어를 말하여 터미널 패널을 다시 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-118">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="102b1-120">애플리케이션에서 Azure에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-120">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="102b1-121">Azure에 자주 연결할 수 없는 것으로 예상되는 경우 [음성 명령 사용](mrlearning-base-ch5.md#enabling-voice-commands) 지침에 따라 MRTK를 사용하여 음성 명령을 구현할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-121">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Enabling Voice Commands](mrlearning-base-ch5.md#enabling-voice-commands) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="102b1-122">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-122">Congratulations</span></span>

<span data-ttu-id="102b1-123">Azure에서 구동하는 음성 명령을 구현했습니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-123">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="102b1-124">디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-124">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="102b1-125">다음 자습서에서는 Azure 음성 번역을 사용하여 음성을 번역하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="102b1-125">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

[<span data-ttu-id="102b1-126">다음 자습서: 3. Azure Cognitive Services 음성 번역 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="102b1-126">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
