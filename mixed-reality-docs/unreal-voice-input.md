---
title: 음성 입력
description: HoloLens 2 및 Unreal engine에서 음성 입력 설정 및 사용에 대 한 자습서
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, HoloLens 2, 음성, 음성 입력, 음성 인식, 혼합 현실, 개발, 기능, 설명서, 가이드, holograms, 게임 개발
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330635"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="9d888-104">Unreal의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="9d888-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="9d888-105">개요</span><span class="sxs-lookup"><span data-stu-id="9d888-105">Overview</span></span>
<span data-ttu-id="9d888-106">음성 입력을 사용 하면 핸드 제스처를 사용할 필요 없이 홀로그램과 상호 작용할 수 있으며 HoloLens (첫 번째 Gen) 및 HoloLens 2에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-106">Voice input allows you to interact with a hologram without having to use hand gestures and is supported on HoloLens (1st Gen) and HoloLens 2.</span></span> <span data-ttu-id="9d888-107">다른 모든 유니버설 Windows 앱의 음성을 지 원하는 동일한 엔진에 의해 제공 되며 혼합 현실에서 상호 작용 하는 방식에 자연 스러운 느낌을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-107">It's powered by the same engine that supports speech in all other Universal Windows Apps and can add a natural feeling to the way you interact in mixed reality.</span></span> 

<span data-ttu-id="9d888-108">지원 되는 음성 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-108">Supported voice features include:</span></span>
- <span data-ttu-id="9d888-109">[Select 명령](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span><span class="sxs-lookup"><span data-stu-id="9d888-109">The [Select command](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span></span>
- [<span data-ttu-id="9d888-110">안녕하세요. Cortana</span><span class="sxs-lookup"><span data-stu-id="9d888-110">Hey, Cortana</span></span>](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- <span data-ttu-id="9d888-111">단추 및 레이블 상호 작용에 대 한 자세한 내용은 "참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d888-111">"See it, say it" for button and label interaction</span></span>
- <span data-ttu-id="9d888-112">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="9d888-112">Dictation</span></span>

<span data-ttu-id="9d888-113">자세한 내용은 기본 [음성 입력](voice-input.md) 설명서를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d888-113">For more information, check out the main [Voice Input](voice-input.md) documentation.</span></span>

## <a name="enabling-speech-recognition"></a><span data-ttu-id="9d888-114">음성 인식 사용</span><span class="sxs-lookup"><span data-stu-id="9d888-114">Enabling Speech Recognition</span></span>

<span data-ttu-id="9d888-115">HoloLens에서 음성 인식을 사용 하도록 설정 하려면:</span><span class="sxs-lookup"><span data-stu-id="9d888-115">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="9d888-116">**프로젝트 설정 > 플랫폼 > HoloLens > 기능** 을 선택 하 고 **마이크**를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-116">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="9d888-117">음성 recogniztion 사용 설정에서 음성 **정보 > 음성** 으로 설정 > **영어**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-117">Enabled speech recogniztion in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="9d888-118">음성 인식은 항상 **설정** 앱에서 구성 된 Windows 표시 언어로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-118">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="9d888-119">또한 최상의 서비스 품질을 위해 **온라인 음성 인식을** 사용 하도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-119">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Windows 음성 인식 설정](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="9d888-121">응용 프로그램에서 마이크를 사용 하도록 설정 하려는 경우 먼저 ask를 시작 하면 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-121">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="9d888-122">**예** 를 선택 하면 앱에서 음성 입력이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-122">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="9d888-123">음성 입력에는 특별 한 Windows Mixed Reality Api가 필요 하지 않습니다. 기존 Unreal Engine 4 [입력](https://docs.unrealengine.com/Gameplay/Input/index.html) 매핑 API를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-123">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="9d888-124">음성 매핑 추가</span><span class="sxs-lookup"><span data-stu-id="9d888-124">Adding Speech Mappings</span></span>
<span data-ttu-id="9d888-125">음성 입력을 사용 하는 경우 음성 작업을 작업에 연결 하는 것은 중요 한 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-125">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="9d888-126">이러한 매핑은 사용자가 말할 수 있는 음성 키워드에 대해 앱을 모니터링 한 다음 연결 된 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-126">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="9d888-127">다음과 같은 방법으로 음성 매핑을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-127">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="9d888-128">**편집 > 프로젝트 설정**을 선택 하 고 **엔진** 섹션으로 스크롤한 다음 **입력**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-128">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="9d888-129">점프 명령에 대 한 새 음성 매핑을 추가 하려면:</span><span class="sxs-lookup"><span data-stu-id="9d888-129">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="9d888-130">**+** **배열 요소** 옆의 아이콘을 클릭 하 고 다음 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-130">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="9d888-131">**작업 이름** 에 대 한 **jumpWord**</span><span class="sxs-lookup"><span data-stu-id="9d888-131">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="9d888-132">**Speech 키워드** 에 대 한 **점프**</span><span class="sxs-lookup"><span data-stu-id="9d888-132">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="9d888-133">모든 영어 단어 또는 짧은 문장을 키워드로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-133">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![UE4 엔진 입력 설정은](images/unreal/engine-input.png)

<span data-ttu-id="9d888-135">음성 매핑은 작업 또는 축 매핑과 같은 입력 구성 요소나 이벤트 그래프의 청사진 노드로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-135">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="9d888-136">예를 들어, 단어를 음성으로 연결 하는 경우에 따라 두 개의 다른 로그를 출력 하도록 점프 명령을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-136">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="9d888-137">청사진을 두 번 클릭 하 여 **이벤트 그래프**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-137">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="9d888-138">**마우스 오른쪽 단추를 클릭** 하 고 음성 매핑의 **작업 이름** (이 경우 **jumpWord**)을 검색 한 다음 **enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-138">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="9d888-139">그러면 **입력 동작** 노드가 그래프에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-139">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="9d888-140">아래 이미지에 나와 있는 것 처럼 **누름** 핀을 끌어 **문자열 노드에 인쇄** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-140">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="9d888-141">**릴리스된** pin은 비워 둘 수 있으며, 음성 매핑에 대해서는 아무 것도 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-141">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![음성에 대 한 간단한 작업](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="9d888-143">앱을 재생 하 고 콘솔을 통해 로그를 **출력 하는 단어를** 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-143">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="9d888-144">모든 설정에 따라 HoloLens 앱에 음성 입력을 추가 하기 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-144">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="9d888-145">음성 및 상호 작용에 대 한 자세한 내용은 아래 링크에서 찾을 수 있으며 사용자를 위해 만드는 환경에 대해 생각해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d888-145">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d888-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d888-146">See also</span></span>
* [<span data-ttu-id="9d888-147">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="9d888-147">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="9d888-148">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="9d888-148">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="9d888-149">MR 입력 212: 음성</span><span class="sxs-lookup"><span data-stu-id="9d888-149">MR Input 212: Voice</span></span>](holograms-212.md)
