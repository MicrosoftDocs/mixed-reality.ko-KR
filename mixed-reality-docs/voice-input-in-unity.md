---
title: Unity에서 음성 입력
description: Unity는 Windows Mixed Reality 응용 프로그램에 음성 입력을 추가 하려면 세 가지 방법으로 노출 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 음성 입력, KeywordRecognizer, GrammarRecognizer, 마이크, 받아쓰기, 음성
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604817"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="4b95e-104">Unity에서 음성 입력</span><span class="sxs-lookup"><span data-stu-id="4b95e-104">Voice input in Unity</span></span>

<span data-ttu-id="4b95e-105">Unity를 추가 하는 세 가지 방법 노출 [입력 음성](voice-input.md) Unity 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="4b95e-106">(두 가지 유형의 PhraseRecognizers 중 하나) KeywordRecognizer를 사용 하 여 앱에 대 한 수신 대기 하는 문자열 명령 배열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="4b95e-107">GrammarRecognizer (다른 유형의 PhraseRecognizer)를 사용 하 여 앱에 대 한 수신 대기 하도록 특정 문법 정의 SRGS 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="4b95e-108">DictationRecognizer를 사용 하 여 앱 단어에 대 한 수신 대기 하 고 메모 또는 해당 음성의 다른 디스플레이 사용 하 여 사용자를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="4b95e-109">받아쓰기 또는 구 인식 한 번에 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="4b95e-110">즉, GrammarRecognizer 또는 KeywordRecognizer 활성 상태인 경우를 DictationRecognizer 일 수 없습니다 active 그 반대로 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="4b95e-111">음성에 대 한 기능을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="4b95e-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="4b95e-112">합니다 **마이크** 음성 입력을 활용 하 여 앱에 대 한 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="4b95e-113">Unity 편집기에서 "> 프로젝트 설정 > Player 편집"로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="4b95e-114">"Windows Store" 탭을 클릭</span><span class="sxs-lookup"><span data-stu-id="4b95e-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="4b95e-115">"게시 설정 > 기능" 섹션을 확인 합니다 **마이크** 기능</span><span class="sxs-lookup"><span data-stu-id="4b95e-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="4b95e-116">Phrase Recognition</span><span class="sxs-lookup"><span data-stu-id="4b95e-116">Phrase Recognition</span></span>

<span data-ttu-id="4b95e-117">특정 수신 하도록 앱을 사용 하도록 설정 하려면 재생 된 어구 사용자가 다음 동작을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="4b95e-118">KeywordRecognizer 또는 GrammarRecognizer 사용에 대 한 수신 대기 하는 문구를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="4b95e-119">OnPhraseRecognized 이벤트를 처리 하 고 해당 구가 인식 하는 작업을 수행</span><span class="sxs-lookup"><span data-stu-id="4b95e-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="4b95e-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="4b95e-120">KeywordRecognizer</span></span>

<span data-ttu-id="4b95e-121">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="4b95e-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="4b95e-122">**형식:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="4b95e-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="4b95e-123">몇 가지 해야 문을 사용 하 여 몇 가지 키 입력을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="4b95e-124">다음 키워드 및 인식기를 저장 하는 클래스에 몇 가지 필드 사전 작업->를 추가 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="4b95e-125">이제 키워드 (예: start () 메서드) 내에서 사전에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="4b95e-126">이 예제에서 "활성화" 키워드를 추가 하는 것:</span><span class="sxs-lookup"><span data-stu-id="4b95e-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="4b95e-127">키워드 인식기 만들고 인식 하도록 원하는 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="4b95e-128">이제 OnPhraseRecognized 이벤트 등록</span><span class="sxs-lookup"><span data-stu-id="4b95e-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="4b95e-129">예제에서는 처리기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-129">An example handler is:</span></span>

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

<span data-ttu-id="4b95e-130">마지막으로 인식 시작!</span><span class="sxs-lookup"><span data-stu-id="4b95e-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="4b95e-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="4b95e-131">GrammarRecognizer</span></span>

<span data-ttu-id="4b95e-132">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="4b95e-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="4b95e-133">**형식**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="4b95e-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="4b95e-134">GrammarRecognizer SRGS를 사용 하 여 인식 문법을 지정 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="4b95e-135">더 복잡 한 구 인식 하도록 하려는 경우 앱에는 몇 개 키워드 또는 쉽게 설정 및 명령 집합 해제 하려는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="4b95e-136">참조 [SRGS XML을 사용 하는 문법을 만드는](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) 파일 형식 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="4b95e-137">SRGS 문법에 있고 프로젝트에서 되 면을 [StreamingAssets 폴더](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="4b95e-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="4b95e-138">GrammarRecognizer 만들고 SRGS 파일 경로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="4b95e-139">이제 OnPhraseRecognized 이벤트 등록</span><span class="sxs-lookup"><span data-stu-id="4b95e-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="4b95e-140">적절 하 게 처리할 수 있는 프로그램 SRGS 문법에 지정 된 정보를 포함 하는 콜백을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="4b95e-141">대부분의 중요 한 정보 semanticMeanings 배열에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="4b95e-142">마지막으로 인식 시작!</span><span class="sxs-lookup"><span data-stu-id="4b95e-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="4b95e-143">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="4b95e-143">Dictation</span></span>

<span data-ttu-id="4b95e-144">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="4b95e-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="4b95e-145">**형식**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="4b95e-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="4b95e-146">사용자의 음성을 텍스트로 변환 하는 DictationRecognizer를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="4b95e-147">DictationRecognizer 노출 [받아쓰기](voice-input.md#dictation) 말하는 동안 피드백 모두 사용자 지정할 수 있는 기능 및 지원 등록 하 고 가설 및 구 수신 완료 이벤트 및 나중에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="4b95e-148">Start () 및 stop () 메서드는 각각 사용 하도록 설정 하 고 인식 받아쓰기를 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="4b95e-149">인식기를 사용 하 여 완료 되 면 dispose () 메서드를 사용 하 여 사용 되는 리소스를 해제 하려면 폐기 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="4b95e-150">이 리소스를 해제 이러한 자동으로 추가 성능 비용 가비지 수집 중 이전에 해제 되지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="4b95e-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="4b95e-151">받아쓰기를 사용 하 여 시작 하는 데 필요한 몇 가지 단계만 가지</span><span class="sxs-lookup"><span data-stu-id="4b95e-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="4b95e-152">새 DictationRecognizer 만들기</span><span class="sxs-lookup"><span data-stu-id="4b95e-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="4b95e-153">받아쓰기 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="4b95e-153">Handle Dictation events</span></span>
3. <span data-ttu-id="4b95e-154">DictationRecognizer 시작</span><span class="sxs-lookup"><span data-stu-id="4b95e-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="4b95e-155">받아쓰기 기능을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="4b95e-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="4b95e-156">위에서 언급 한 "마이크" 기능 외에 "인터넷 클라이언트" 기능을 받아쓰기를 활용 하 여 앱에 대해 선언 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="4b95e-157">Unity 편집기에서 "> 프로젝트 설정 > Player 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="4b95e-158">"Windows Store" 탭을 클릭</span><span class="sxs-lookup"><span data-stu-id="4b95e-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="4b95e-159">"게시 설정 > 기능" 섹션을 확인 합니다 **InternetClient** 기능</span><span class="sxs-lookup"><span data-stu-id="4b95e-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="4b95e-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="4b95e-160">DictationRecognizer</span></span>

<span data-ttu-id="4b95e-161">만들기는 DictationRecognizer 다음과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="4b95e-162">구독할 수 있고 받아쓰기 동작을 구현 하려는 경우에 처리 하는 4 개의 받아쓰기 이벤트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="4b95e-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="4b95e-163">DictationResult</span></span>
2. <span data-ttu-id="4b95e-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="4b95e-164">DictationComplete</span></span>
3. <span data-ttu-id="4b95e-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="4b95e-165">DictationHypothesis</span></span>
4. <span data-ttu-id="4b95e-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="4b95e-166">DictationError</span></span>

<span data-ttu-id="4b95e-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="4b95e-167">**DictationResult**</span></span>

<span data-ttu-id="4b95e-168">이 이벤트가 사용자 일시 중지, 일반적으로 문장의 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="4b95e-169">전체 인식 문자열이 여기 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="4b95e-170">먼저 DictationResult 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="4b95e-171">DictationResult 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="4b95e-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="4b95e-172">**DictationHypothesis**</span></span>

<span data-ttu-id="4b95e-173">이 이벤트는 사용자와 통신 하는 동안에 지속적으로 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="4b95e-174">이것이 무엇 인지의 텍스트를 제공 인식기에서 수신 대기 하는 대로 지금 들립니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="4b95e-175">먼저 DictationHypothesis 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="4b95e-176">DictationHypothesis 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="4b95e-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="4b95e-177">**DictationComplete**</span></span>

<span data-ttu-id="4b95e-178">Stop () 호출에서 발생 하는 시간 제한 또는 일부 다른 오류로 못하게에서 인식기 중지 되 면이 이벤트가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="4b95e-179">먼저 DictationComplete 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="4b95e-180">DictationComplete 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="4b95e-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="4b95e-181">**DictationError**</span></span>

<span data-ttu-id="4b95e-182">이 이벤트는 오류가 발생할 때 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="4b95e-183">먼저 DictationError 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="4b95e-184">DictationError 콜백을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="4b95e-185">구독 하 고 관심 있는 받아쓰기 이벤트를 처리 했으면, 이벤트를 수신 하려면 받아쓰기 인식기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="4b95e-186">에서 더 이상 주변 DictationRecognizer 유지 하려는 경우 이벤트에서 구독을 취소 하 고는 DictationRecognizer를 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="4b95e-187">**팁**</span><span class="sxs-lookup"><span data-stu-id="4b95e-187">**Tips**</span></span>
* <span data-ttu-id="4b95e-188">Start () 및 stop () 메서드는 각각 사용 하도록 설정 하 고 인식 받아쓰기를 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="4b95e-189">인식기를 사용 하 여 완료 되 면 dispose () 메서드를 사용 하 여 사용 되는 리소스를 해제 하려면 삭제 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="4b95e-190">이 리소스를 해제 이러한 자동으로 추가 성능 비용 가비지 수집 중 이전에 해제 되지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="4b95e-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="4b95e-191">시간 제한 설정된 기간 후 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="4b95e-192">이러한 시간 제한 DictationComplete 이벤트에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="4b95e-193">알아야 할 두 가지 시간 제한을 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="4b95e-194">인식기 시작 되 고 모든 오디오 첫 번째 5 초 동안 듣지 못합니다, 시간 초과 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="4b95e-195">인식기에 결과 지정 하지만 다음 20 초 동안 대기를 시도해볼 경우 시간 초과 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="4b95e-196">구 인식과 받아쓰기를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="4b95e-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="4b95e-197">구 인식과 받아쓰기 앱에서 사용 하려는 경우에 완전히 종료 하나 다른 시작 하기 전에 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="4b95e-198">여러 KeywordRecognizers 실행 중인 경우 종료할 수 있습니다 이러한 모두 한 번에 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="4b95e-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="4b95e-199">DictationRecognizer 중지 되 면 모든 인식기를 이전 상태로 복원 하려면 다음을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="4b95e-200">PhraseRecognitionSystem을도 다시 시작을 KeywordRecognizer를 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="4b95e-201">마이크 도우미 사용</span><span class="sxs-lookup"><span data-stu-id="4b95e-201">Using the microphone helper</span></span>

<span data-ttu-id="4b95e-202">GitHub에서 혼합 현실 도구 키트는 시스템에서 마이크를 사용할 수 없는 경우 개발자가 암시 하는 마이크 도우미 클래스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="4b95e-203">에 대 한 한 가지 용도 하나 응용 프로그램에 모든 음성 상호 작용 힌트를 표시 하기 전에 시스템에서 마이크 있는지 확인 하고자 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="4b95e-204">마이크 도우미 스크립트에서 찾을 수 있습니다 합니다 [Utilities/스크립트 입력/폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="4b95e-205">GitHub 리포지토리에 포함 되어는 [작은 샘플](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) 도우미를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="4b95e-206">혼합 현실 도구 키트의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="4b95e-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="4b95e-207">이 장면에서 음성 입력의 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b95e-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="4b95e-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span><span class="sxs-lookup"><span data-stu-id="4b95e-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
