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
# <a name="voice-input-in-unity"></a>Unity의 음성 입력

Unity는 Unity 응용 프로그램에 [음성 입력](voice-input.md) 을 추가 하는 세 가지 방법을 제공 합니다.

KeywordRecognizer (두 가지 유형의 PhraseRecognizers 중 하나)를 사용 하 여 앱에 수신 대기할 문자열 명령의 배열을 제공할 수 있습니다. GrammarRecognizer (다른 유형의 PhraseRecognizer)를 사용 하면 수신 대기할 특정 문법을 정의 하는 SRGS 파일이 앱에 제공 될 수 있습니다. DictationRecognizer를 사용 하 여 앱은 모든 단어를 수신 대기 하 고 사용자에 게 음성의 메모 또는 다른 표시를 제공할 수 있습니다.

>[!NOTE]
>받아쓰기 또는 문구 인식을 한 번에 처리할 수 있습니다. 즉, GrammarRecognizer 또는 KeywordRecognizer가 활성 상태 이면 DictationRecognizer은 활성 상태가 될 수 없으며 그 반대의 경우도 마찬가지입니다.

## <a name="enabling-the-capability-for-voice"></a>음성 기능 사용

음성 입력을 활용 하려면 앱에 대해 **마이크** 기능을 선언 해야 합니다.
1. Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.
2. "Windows 스토어" 탭을 클릭 합니다.
3. "게시 설정 > 기능" 섹션에서 **마이크** 기능을 확인 합니다.

## <a name="phrase-recognition"></a>문구 인식

앱이 사용자가 말하는 특정 문구를 수신 대기 하도록 하려면 다음 작업을 수행 해야 합니다.
1. KeywordRecognizer 또는 GrammarRecognizer를 사용 하 여 수신할 구를 지정 합니다.
2. OnPhraseRecognized 이벤트를 처리 하 고 인식 된 구에 해당 하는 작업을 수행 합니다.

### <a name="keywordrecognizer"></a>KeywordRecognizer

**공간** *UnityEngine. Windows. Speech*<br>
**종류** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

몇 가지 using 문을 사용 하 여 몇 가지 키 입력을 저장 해야 합니다.

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

그런 다음 클래스에 몇 개의 필드를 추가 하 여 인식기 및 키워드 > 동작 사전을 저장 해 보겠습니다.

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

이제 키워드를 사전에 추가 합니다 (예: Start () 메서드 내부). 이 예에서는 "activate" 키워드를 추가 하 고 있습니다.

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

키워드 인식기를 만들고 인식 하려는 항목을 알려 주세요.

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

이제 OnPhraseRecognized 이벤트에 등록 합니다.

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

예제 처리기는 다음과 같습니다.

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

마지막으로 인식을 시작 합니다.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**공간** *UnityEngine. Windows. Speech*<br>
**형식**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

GrammarRecognizer는 SRGS를 사용 하 여 인식 문법을 지정 하는 경우에 사용 됩니다. 이는 앱에 몇 개의 키워드 이상이 있거나 더 복잡 한 구를 인식 하거나 명령 집합을 쉽게 설정 하 고 해제 하려는 경우에 유용할 수 있습니다. 참조 파일 형식 정보에 대해 [SRGS XML을 사용 하 여 문법을 만듭니다](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) .

SRGS 문법이 있고 [Streamingassets 폴더](http://docs.unity3d.com/Manual/StreamingAssets.html)의 프로젝트에 있습니다.

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

GrammarRecognizer을 만들고 SRGS 파일에 대 한 경로를 전달 합니다.

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

이제 OnPhraseRecognized 이벤트에 등록 합니다.

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

적절 하 게 처리할 수 있는 SRGS 문법에 지정 된 정보를 포함 하는 콜백이 제공 됩니다. 대부분의 중요 한 정보는 semanticMeanings 배열에서 제공 됩니다.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

마지막으로 인식을 시작 합니다.

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>받아쓰기

**공간** *UnityEngine. Windows. Speech*<br>
**형식**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

DictationRecognizer를 사용 하 여 사용자의 음성을 텍스트로 변환 합니다. DictationRecognizer는 [받아쓰기](voice-input.md#dictation) 기능을 노출 하 고, 가설 및 구가 완료 된 이벤트에 대 한 등록 및 수신 대기를 지원 하므로, 나중에 말할 때 사용자에 게 피드백을 제공할 수 있습니다. Start () 및 Stop () 메서드는 각각 받아쓰기 인식을 사용 하거나 사용 하지 않도록 설정 합니다. 인식기를 사용 하 여 작업을 완료 한 후에는 Dispose () 메서드를 사용 하 여 사용 하는 리소스를 해제 해야 합니다. 이러한 리소스는 가비지 수집 중에 해제 되지 않은 경우 추가 성능 비용으로 자동으로 해제 됩니다.

받아쓰기를 시작 하는 데 필요한 몇 가지 단계만 있습니다.
1. 새 DictationRecognizer 만들기
2. 받아쓰기 이벤트 처리
3. DictationRecognizer 시작

### <a name="enabling-the-capability-for-dictation"></a>받아쓰기 기능 사용

받아쓰기를 활용 하기 위해 앱에 대해 위에서 언급 한 "마이크" 기능과 함께 "인터넷 클라이언트" 기능을 선언 해야 합니다.
1. Unity 편집기에서 "> 프로젝트 설정 > 플레이어 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.
2. "Windows 스토어" 탭을 클릭 합니다.
3. "게시 설정 > 기능" 섹션에서 **Internetclient** 기능을 확인 합니다.

### <a name="dictationrecognizer"></a>DictationRecognizer

다음과 같이 DictationRecognizer를 만듭니다.

```
dictationRecognizer = new DictationRecognizer();
```

받아쓰기 동작을 구현 하기 위해 구독 하 고 처리할 수 있는 받아쓰기 이벤트는 네 가지가 있습니다.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

이 이벤트는 일반적으로 문장의 끝에 사용자가 일시 중지 한 후에 발생 합니다. 여기에는 전체 인식 된 문자열이 반환 됩니다.

먼저 DictationResult 이벤트를 구독 합니다.

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

그런 다음 DictationResult 콜백을 처리 합니다.

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

이 이벤트는 사용자가 통신 하는 동안 지속적으로 발생 합니다. 인식기는 수신 대기 하는 동안 지금까지 수신 하는 내용에 대 한 텍스트를 제공 합니다.

먼저 DictationHypothesis 이벤트를 구독 합니다.

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

그런 다음 DictationHypothesis 콜백을 처리 합니다.

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

이 이벤트는 인식기가 중지 될 때 발생 합니다. 중지 ()를 호출할 때 발생 하는 시간 초과 또는 다른 오류가 발생 했는지 여부입니다.

먼저 DictationComplete 이벤트를 구독 합니다.

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

그런 다음 DictationComplete 콜백을 처리 합니다.

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

이 이벤트는 오류가 발생할 때 발생 합니다.

먼저 DictationError 이벤트를 구독 합니다.

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

그런 다음 DictationError 콜백을 처리 합니다.

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

관심이 있는 받아쓰기 이벤트를 구독 하 고 처리 한 후에는 받아쓰기 인식기를 시작 하 여 이벤트 수신을 시작 합니다.

```
dictationRecognizer.Start();
```

DictationRecognizer을 더 이상 유지 하지 않으려면 이벤트를 구독 취소 하 고 DictationRecognizer를 삭제 해야 합니다.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**팁**
* Start () 및 Stop () 메서드는 각각 받아쓰기 인식을 사용 하거나 사용 하지 않도록 설정 합니다.
* 인식기를 사용 하 여 작업을 완료 한 후에는 Dispose () 메서드를 사용 하 여 해당 리소스를 해제 해야 합니다. 이러한 리소스는 가비지 수집 중에 해제 되지 않은 경우 추가 성능 비용으로 자동으로 해제 됩니다.
* 시간 제한은 설정 된 시간 후에 발생 합니다. DictationComplete 이벤트에서 이러한 시간 제한을 확인할 수 있습니다. 다음 두 가지 제한 시간을 인식 합니다.
   1. 인식기가 시작 되 고 처음 5 초 동안 오디오가 들리지 않으면 시간이 초과 됩니다.
   2. 인식기가 결과를 제공 했지만 20 초 동안 침묵 소음을 받은 경우 시간이 초과 됩니다.

## <a name="using-both-phrase-recognition-and-dictation"></a>구 인식과 받아쓰기 모두 사용

앱에서 구 인식과 받아쓰기를 모두 사용 하려는 경우에는 다른 항목을 시작 하기 전에 하나를 완전히 종료 해야 합니다. 여러 KeywordRecognizers를 실행 하는 경우 다음을 사용 하 여 한 번에 모두 종료할 수 있습니다.

```
PhraseRecognitionSystem.Shutdown();
```

모든 인식기를 이전 상태로 복원 하기 위해 DictationRecognizer가 중지 된 후 다음을 호출할 수 있습니다.

```
PhraseRecognitionSystem.Restart();
```

KeywordRecognizer를 시작할 수도 있습니다. 그러면 PhraseRecognitionSystem도 다시 시작 됩니다.

## <a name="using-the-microphone-helper"></a>마이크 도우미 사용

GitHub의 Mixed Reality 도구 키트에는 시스템에 사용할 수 있는 마이크가 있는 경우 개발자에 게 힌트에 대 한 마이크 도우미 클래스가 포함 되어 있습니다. 한 가지 용도는 응용 프로그램에서 음성 상호 작용 힌트를 표시 하기 전에 시스템에 마이크가 있는지 확인 하는 것입니다.

마이크 도우미 스크립트는 [입력/스크립트/유틸리티 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)에서 찾을 수 있습니다. GitHub 리포지토리에는 도우미를 사용 하는 방법을 보여 주는 [작은 샘플](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) 도 포함 되어 있습니다.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Mixed Reality Toolkit의 음성 입력
이 장면에서 음성 입력의 예제를 찾을 수 있습니다.

- [HoloToolkit-Examples/Input/장면이/SpeechInputSource](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
