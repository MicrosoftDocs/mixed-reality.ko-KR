---
title: Unity의 음성 입력
description: Unity는 Windows Mixed Reality 응용 프로그램에 음성 입력을 추가 하는 세 가지 방법을 제공 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 음성 입력, KeywordRecognizer, GrammarRecognizer, 마이크, 받아쓰기, 음성
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548687"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="b6b56-104">Unity의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="b6b56-104">Voice input in Unity</span></span>

<span data-ttu-id="b6b56-105">Unity는 Unity 응용 프로그램에 [음성 입력](voice-input.md) 을 추가 하는 세 가지 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="b6b56-106">KeywordRecognizer (두 가지 유형의 PhraseRecognizers 중 하나)를 사용 하 여 앱에 수신 대기할 문자열 명령의 배열을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="b6b56-107">GrammarRecognizer (다른 유형의 PhraseRecognizer)를 사용 하면 수신 대기할 특정 문법을 정의 하는 SRGS 파일이 앱에 제공 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="b6b56-108">DictationRecognizer를 사용 하 여 앱은 모든 단어를 수신 대기 하 고 사용자에 게 음성의 메모 또는 다른 표시를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="b6b56-109">받아쓰기 또는 문구 인식을 한 번에 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="b6b56-110">즉, GrammarRecognizer 또는 KeywordRecognizer가 활성 상태 이면 DictationRecognizer은 활성 상태가 될 수 없으며 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="b6b56-111">음성 기능 사용</span><span class="sxs-lookup"><span data-stu-id="b6b56-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="b6b56-112">음성 입력을 활용 하려면 앱에 대해 **마이크** 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="b6b56-113">Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="b6b56-114">"Windows 스토어" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="b6b56-115">"게시 설정 > 기능" 섹션에서 **마이크** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="b6b56-116">문구 인식</span><span class="sxs-lookup"><span data-stu-id="b6b56-116">Phrase Recognition</span></span>

<span data-ttu-id="b6b56-117">앱이 사용자가 말하는 특정 문구를 수신 대기 하도록 하려면 다음 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="b6b56-118">KeywordRecognizer 또는 GrammarRecognizer를 사용 하 여 수신할 구를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="b6b56-119">OnPhraseRecognized 이벤트를 처리 하 고 인식 된 구에 해당 하는 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="b6b56-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="b6b56-120">KeywordRecognizer</span></span>

<span data-ttu-id="b6b56-121">**공간** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="b6b56-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="b6b56-122">**종류** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="b6b56-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="b6b56-123">몇 가지 using 문을 사용 하 여 몇 가지 키 입력을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="b6b56-124">그런 다음 클래스에 몇 개의 필드를 추가 하 여 인식기 및 키워드 > 동작 사전을 저장 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="b6b56-125">이제 키워드를 사전에 추가 합니다 (예: Start () 메서드 내부).</span><span class="sxs-lookup"><span data-stu-id="b6b56-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="b6b56-126">이 예에서는 "activate" 키워드를 추가 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="b6b56-127">키워드 인식기를 만들고 인식 하려는 항목을 알려 주세요.</span><span class="sxs-lookup"><span data-stu-id="b6b56-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="b6b56-128">이제 OnPhraseRecognized 이벤트에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="b6b56-129">예제 처리기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-129">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="b6b56-130">마지막으로 인식을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="b6b56-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="b6b56-131">GrammarRecognizer</span></span>

<span data-ttu-id="b6b56-132">**공간** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="b6b56-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="b6b56-133">**형식**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="b6b56-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="b6b56-134">GrammarRecognizer는 SRGS를 사용 하 여 인식 문법을 지정 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="b6b56-135">이는 앱에 몇 개의 키워드 이상이 있거나 더 복잡 한 구를 인식 하거나 명령 집합을 쉽게 설정 하 고 해제 하려는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="b6b56-136">참조 파일 형식 정보에 대해 [SRGS XML을 사용 하 여 문법을 만듭니다](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) .</span><span class="sxs-lookup"><span data-stu-id="b6b56-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="b6b56-137">SRGS 문법이 있고 [Streamingassets 폴더](http://docs.unity3d.com/Manual/StreamingAssets.html)의 프로젝트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="b6b56-138">GrammarRecognizer을 만들고 SRGS 파일에 대 한 경로를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="b6b56-139">이제 OnPhraseRecognized 이벤트에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="b6b56-140">적절 하 게 처리할 수 있는 SRGS 문법에 지정 된 정보를 포함 하는 콜백이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="b6b56-141">대부분의 중요 한 정보는 semanticMeanings 배열에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="b6b56-142">마지막으로 인식을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="b6b56-143">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="b6b56-143">Dictation</span></span>

<span data-ttu-id="b6b56-144">**공간** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="b6b56-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="b6b56-145">**형식**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="b6b56-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="b6b56-146">DictationRecognizer를 사용 하 여 사용자의 음성을 텍스트로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="b6b56-147">DictationRecognizer는 [받아쓰기](voice-input.md#dictation) 기능을 노출 하 고, 가설 및 구가 완료 된 이벤트에 대 한 등록 및 수신 대기를 지원 하므로, 나중에 말할 때 사용자에 게 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="b6b56-148">Start () 및 Stop () 메서드는 각각 받아쓰기 인식을 사용 하거나 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="b6b56-149">인식기를 사용 하 여 작업을 완료 한 후에는 Dispose () 메서드를 사용 하 여 사용 하는 리소스를 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="b6b56-150">이러한 리소스는 가비지 수집 중에 해제 되지 않은 경우 추가 성능 비용으로 자동으로 해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="b6b56-151">받아쓰기를 시작 하는 데 필요한 몇 가지 단계만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="b6b56-152">새 DictationRecognizer 만들기</span><span class="sxs-lookup"><span data-stu-id="b6b56-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="b6b56-153">받아쓰기 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="b6b56-153">Handle Dictation events</span></span>
3. <span data-ttu-id="b6b56-154">DictationRecognizer 시작</span><span class="sxs-lookup"><span data-stu-id="b6b56-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="b6b56-155">받아쓰기 기능 사용</span><span class="sxs-lookup"><span data-stu-id="b6b56-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="b6b56-156">받아쓰기를 활용 하기 위해 앱에 대해 위에서 언급 한 "마이크" 기능과 함께 "인터넷 클라이언트" 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="b6b56-157">Unity 편집기에서 "> 프로젝트 설정 > 플레이어 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="b6b56-158">"Windows 스토어" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="b6b56-159">"게시 설정 > 기능" 섹션에서 **Internetclient** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="b6b56-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="b6b56-160">DictationRecognizer</span></span>

<span data-ttu-id="b6b56-161">다음과 같이 DictationRecognizer를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="b6b56-162">받아쓰기 동작을 구현 하기 위해 구독 하 고 처리할 수 있는 받아쓰기 이벤트는 네 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="b6b56-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="b6b56-163">DictationResult</span></span>
2. <span data-ttu-id="b6b56-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="b6b56-164">DictationComplete</span></span>
3. <span data-ttu-id="b6b56-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="b6b56-165">DictationHypothesis</span></span>
4. <span data-ttu-id="b6b56-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="b6b56-166">DictationError</span></span>

<span data-ttu-id="b6b56-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="b6b56-167">**DictationResult**</span></span>

<span data-ttu-id="b6b56-168">이 이벤트는 일반적으로 문장의 끝에 사용자가 일시 중지 한 후에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="b6b56-169">여기에는 전체 인식 된 문자열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="b6b56-170">먼저 DictationResult 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="b6b56-171">그런 다음 DictationResult 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="b6b56-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="b6b56-172">**DictationHypothesis**</span></span>

<span data-ttu-id="b6b56-173">이 이벤트는 사용자가 통신 하는 동안 지속적으로 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="b6b56-174">인식기는 수신 대기 하는 동안 지금까지 수신 하는 내용에 대 한 텍스트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="b6b56-175">먼저 DictationHypothesis 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="b6b56-176">그런 다음 DictationHypothesis 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="b6b56-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="b6b56-177">**DictationComplete**</span></span>

<span data-ttu-id="b6b56-178">이 이벤트는 인식기가 중지 될 때 발생 합니다. 중지 ()를 호출할 때 발생 하는 시간 초과 또는 다른 오류가 발생 했는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="b6b56-179">먼저 DictationComplete 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="b6b56-180">그런 다음 DictationComplete 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="b6b56-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="b6b56-181">**DictationError**</span></span>

<span data-ttu-id="b6b56-182">이 이벤트는 오류가 발생할 때 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="b6b56-183">먼저 DictationError 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="b6b56-184">그런 다음 DictationError 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="b6b56-185">관심이 있는 받아쓰기 이벤트를 구독 하 고 처리 한 후에는 받아쓰기 인식기를 시작 하 여 이벤트 수신을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="b6b56-186">DictationRecognizer을 더 이상 유지 하지 않으려면 이벤트를 구독 취소 하 고 DictationRecognizer를 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="b6b56-187">**팁**</span><span class="sxs-lookup"><span data-stu-id="b6b56-187">**Tips**</span></span>
* <span data-ttu-id="b6b56-188">Start () 및 Stop () 메서드는 각각 받아쓰기 인식을 사용 하거나 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="b6b56-189">인식기를 사용 하 여 작업을 완료 한 후에는 Dispose () 메서드를 사용 하 여 해당 리소스를 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="b6b56-190">이러한 리소스는 가비지 수집 중에 해제 되지 않은 경우 추가 성능 비용으로 자동으로 해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="b6b56-191">시간 제한은 설정 된 시간 후에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="b6b56-192">DictationComplete 이벤트에서 이러한 시간 제한을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="b6b56-193">다음 두 가지 제한 시간을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="b6b56-194">인식기가 시작 되 고 처음 5 초 동안 오디오가 들리지 않으면 시간이 초과 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="b6b56-195">인식기가 결과를 제공 했지만 20 초 동안 침묵 소음을 받은 경우 시간이 초과 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="b6b56-196">구 인식과 받아쓰기 모두 사용</span><span class="sxs-lookup"><span data-stu-id="b6b56-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="b6b56-197">앱에서 구 인식과 받아쓰기를 모두 사용 하려는 경우에는 다른 항목을 시작 하기 전에 하나를 완전히 종료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="b6b56-198">여러 KeywordRecognizers를 실행 하는 경우 다음을 사용 하 여 한 번에 모두 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="b6b56-199">모든 인식기를 이전 상태로 복원 하기 위해 DictationRecognizer가 중지 된 후 다음을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="b6b56-200">KeywordRecognizer를 시작할 수도 있습니다. 그러면 PhraseRecognitionSystem도 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="b6b56-201">마이크 도우미 사용</span><span class="sxs-lookup"><span data-stu-id="b6b56-201">Using the microphone helper</span></span>

<span data-ttu-id="b6b56-202">GitHub의 Mixed Reality 도구 키트에는 시스템에 사용할 수 있는 마이크가 있는 경우 개발자에 게 힌트에 대 한 마이크 도우미 클래스가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="b6b56-203">한 가지 용도는 응용 프로그램에서 음성 상호 작용 힌트를 표시 하기 전에 시스템에 마이크가 있는지 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="b6b56-204">마이크 도우미 스크립트는 [입력/스크립트/유틸리티 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="b6b56-205">GitHub 리포지토리에는 도우미를 사용 하는 방법을 보여 주는 [작은 샘플](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) 도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="b6b56-206">Mixed Reality Toolkit의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="b6b56-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="b6b56-207">이 장면에서 음성 입력의 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6b56-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="b6b56-208">HoloToolkit-Examples/Input/장면이/SpeechInputSource</span><span class="sxs-lookup"><span data-stu-id="b6b56-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
