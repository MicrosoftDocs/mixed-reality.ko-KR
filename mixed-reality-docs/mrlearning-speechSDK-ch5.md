---
title: MR Learning SpeechSDK 모듈-음성 인식 및 기록
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: fc65dccfcbc181af0c0b321374c721797e120e5d
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460333"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="3eae4-104">Speech SDK 학습 모듈-음성 명령을 사용 하 여 로켓 시작 관리자 제어</span><span class="sxs-lookup"><span data-stu-id="3eae4-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="3eae4-105">이 단원에서는 Azure Speech Service의 의도 기능을 사용 하 여 음성의 의도를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="3eae4-106">검색 된 음성을 음성 명령으로 사용 하 여 로켓 시작 관리자를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="3eae4-107">이 단원에서는 로켓 시작 기 자산을 가져오고 검색 된 의도 음성 명령을 미리 정의 된 제어 단추에 인터페이스 하 여 로켓을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span> 

## <a name="objectives"></a><span data-ttu-id="3eae4-108">목표</span><span class="sxs-lookup"><span data-stu-id="3eae4-108">Objectives</span></span>

- <span data-ttu-id="3eae4-109">음성 의도를 음성 명령으로 연결 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="3eae4-110">음성 의도 음성 명령을 로켓 컨트롤 입력 명령으로 사용 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="3eae4-111">지침</span><span class="sxs-lookup"><span data-stu-id="3eae4-111">Instructions</span></span>
1. <span data-ttu-id="3eae4-112">이 자습서에서는 "BaseModule" 자산을 사용 하 여 로켓 시작 관리자를 음성 명령과 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="3eae4-113">이를 위해 프로젝트에 자산을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="3eae4-114">이 링크 (링크 첨부)를 사용 하 여 "로켓 시작 관리자" 자산을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-114">You can download the "Rocket Launcher" asset using this link (Attach the link).</span></span> 

2. <span data-ttu-id="3eae4-115">자산을 가져오려면 자산-> 가져오기 패키지-> 사용자 지정 패키지-> 다운로드 한 파일로 이동 하 여 가져오기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="3eae4-117">"로켓 시작 관리자" 자산을 가져온 후 "로켓 시작 관리자" 폴더 > Prefabs-> "로켓 Launcher_Complete"를 선택 하 고 기존 장면 계층 구조에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-117">After importing the "Rocket Launcher" asset, navigate inside the "Rocket Launcher" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="3eae4-119">이제 이전 단원에서 작업 한 LUIS 프로젝트와 "로켓 시작 관리자"를 통합 해야 합니다 (lesson4에 대 한 링크).</span><span class="sxs-lookup"><span data-stu-id="3eae4-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson (link for lesson4).</span></span> <span data-ttu-id="3eae4-120">이렇게 하려면 계층에서 "로켓 Launcher_Complete" prefab를 확장 하 고 "LaunchRoundButton", "ResetRoundButton" 및 "배치 힌트" 단추를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="3eae4-122">"LaunchRoundButton"를 선택 하 고 검사기 패널에서 "Interactable"로 이동 하 고 이벤트 "OnClick ()" 아래에서 "LunarModule" prefab를 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="3eae4-123">그런 다음 함수 드롭다운을 선택 하 고 "LunarModule"를 선택한 다음 "StartThruster ()" 함수로 이동 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="3eae4-126">"ResetRoundButton"를 선택 하 고 검사기 패널에서 "Interactable"로 이동 하 고 이벤트 "OnClick ()" 아래에서 "LunarModule" prefab를 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="3eae4-127">그런 다음 함수 드롭다운을 선택 하 고 "LunarModule"를 선택한 다음 "resetModule ()" 함수로 이동 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="3eae4-129">"배치 힌트"를 선택 하 고, 검사기 패널에서 "Interactable"로 이동 하 고 이벤트 "OnClick ()" 아래에서 "LunarModule" prefab를 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="3eae4-130">그런 다음 함수 드롭다운을 선택 하 고 "LunarModule"를 선택한 다음 "TogglePlacementHints" 함수로 이동 하 여 ToggleGameOBjects ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  <span data-ttu-id="3eae4-132">그런 다음, 계층에서 Lunarcom_Completed prefab를 선택 하 고 검사기에서 "Lunarcom 의도 인식기" 스크립트로 이동한 다음 "LaunchRoundButton", "ResetRoundButton" 및 "배치 힌트" 단추를 해당 위치에 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="3eae4-134">Unity 편집기에서 재생 단추를 누르고 "로켓" 단추를 클릭 하 고 "로켓" 단추를 클릭 하 고, "utter" 단추를 클릭 하 고, "rest 단추를 누릅니다.", "rest 단추를 누릅니다." 또는 다른 구를 클릭 하 여 로켓 시작 관리자에 대 한 시작, 다시 설정 또는 힌트 요청을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="3eae4-138">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-138">Congratulations</span></span>

<span data-ttu-id="3eae4-139">이 단원에서는 AI 지원 음성 명령을 음성 명령에 연결 하 여 입력 방법으로 사용 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="3eae4-140">이제 프로그램에서 음성 명령으로 스피커 의도를 사용 하 여 로켓 시작 관리자에 대 한 입력을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eae4-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>

