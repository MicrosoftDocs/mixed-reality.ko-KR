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
# <a name="voice-input-in-unity"></a>Unity에서 음성 입력

Unity를 추가 하는 세 가지 방법 노출 [입력 음성](voice-input.md) Unity 응용 프로그램입니다.

(두 가지 유형의 PhraseRecognizers 중 하나) KeywordRecognizer를 사용 하 여 앱에 대 한 수신 대기 하는 문자열 명령 배열을 지정할 수 있습니다. GrammarRecognizer (다른 유형의 PhraseRecognizer)를 사용 하 여 앱에 대 한 수신 대기 하도록 특정 문법 정의 SRGS 파일을 지정할 수 있습니다. DictationRecognizer를 사용 하 여 앱 단어에 대 한 수신 대기 하 고 메모 또는 해당 음성의 다른 디스플레이 사용 하 여 사용자를 제공할 수 있습니다.

>[!NOTE]
>받아쓰기 또는 구 인식 한 번에 처리할 수 있습니다. 즉, GrammarRecognizer 또는 KeywordRecognizer 활성 상태인 경우를 DictationRecognizer 일 수 없습니다 active 그 반대로 가능 합니다.

## <a name="enabling-the-capability-for-voice"></a>음성에 대 한 기능을 사용 하도록 설정

합니다 **마이크** 음성 입력을 활용 하 여 앱에 대 한 기능을 선언 해야 합니다.
1. Unity 편집기에서 "> 프로젝트 설정 > Player 편집"로 이동 하 여 플레이어 설정으로 이동 합니다.
2. "Windows Store" 탭을 클릭
3. "게시 설정 > 기능" 섹션을 확인 합니다 **마이크** 기능

## <a name="phrase-recognition"></a>Phrase Recognition

특정 수신 하도록 앱을 사용 하도록 설정 하려면 재생 된 어구 사용자가 다음 동작을 수행 해야 합니다.
1. KeywordRecognizer 또는 GrammarRecognizer 사용에 대 한 수신 대기 하는 문구를 지정 합니다.
2. OnPhraseRecognized 이벤트를 처리 하 고 해당 구가 인식 하는 작업을 수행

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**형식:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

몇 가지 해야 문을 사용 하 여 몇 가지 키 입력을 저장 합니다.

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

다음 키워드 및 인식기를 저장 하는 클래스에 몇 가지 필드 사전 작업->를 추가 해 보겠습니다.

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

이제 키워드 (예: start () 메서드) 내에서 사전에 추가 합니다. 이 예제에서 "활성화" 키워드를 추가 하는 것:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

키워드 인식기 만들고 인식 하도록 원하는 알려줍니다.

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

이제 OnPhraseRecognized 이벤트 등록

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

예제에서는 처리기는 다음과 같습니다.

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

마지막으로 인식 시작!

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**형식**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

GrammarRecognizer SRGS를 사용 하 여 인식 문법을 지정 하는 경우에 사용 됩니다. 더 복잡 한 구 인식 하도록 하려는 경우 앱에는 몇 개 키워드 또는 쉽게 설정 및 명령 집합 해제 하려는 경우에 유용할 수 있습니다. 참조 [SRGS XML을 사용 하는 문법을 만드는](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) 파일 형식 정보입니다.

SRGS 문법에 있고 프로젝트에서 되 면을 [StreamingAssets 폴더](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

GrammarRecognizer 만들고 SRGS 파일 경로 전달 합니다.

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

이제 OnPhraseRecognized 이벤트 등록

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

적절 하 게 처리할 수 있는 프로그램 SRGS 문법에 지정 된 정보를 포함 하는 콜백을 받을 수 있습니다. 대부분의 중요 한 정보 semanticMeanings 배열에서 제공 됩니다.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

마지막으로 인식 시작!

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>받아쓰기

**Namespace:** *UnityEngine.Windows.Speech*<br>
**형식**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

사용자의 음성을 텍스트로 변환 하는 DictationRecognizer를 사용 합니다. DictationRecognizer 노출 [받아쓰기](voice-input.md#dictation) 말하는 동안 피드백 모두 사용자 지정할 수 있는 기능 및 지원 등록 하 고 가설 및 구 수신 완료 이벤트 및 나중에 있습니다. Start () 및 stop () 메서드는 각각 사용 하도록 설정 하 고 인식 받아쓰기를 비활성화 합니다. 인식기를 사용 하 여 완료 되 면 dispose () 메서드를 사용 하 여 사용 되는 리소스를 해제 하려면 폐기 되어야 합니다. 이 리소스를 해제 이러한 자동으로 추가 성능 비용 가비지 수집 중 이전에 해제 되지 않은 경우.

받아쓰기를 사용 하 여 시작 하는 데 필요한 몇 가지 단계만 가지
1. 새 DictationRecognizer 만들기
2. 받아쓰기 이벤트 처리
3. DictationRecognizer 시작

### <a name="enabling-the-capability-for-dictation"></a>받아쓰기 기능을 사용 하도록 설정

위에서 언급 한 "마이크" 기능 외에 "인터넷 클라이언트" 기능을 받아쓰기를 활용 하 여 앱에 대해 선언 되어야 합니다.
1. Unity 편집기에서 "> 프로젝트 설정 > Player 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.
2. "Windows Store" 탭을 클릭
3. "게시 설정 > 기능" 섹션을 확인 합니다 **InternetClient** 기능

### <a name="dictationrecognizer"></a>DictationRecognizer

만들기는 DictationRecognizer 다음과 같이 합니다.

```
dictationRecognizer = new DictationRecognizer();
```

구독할 수 있고 받아쓰기 동작을 구현 하려는 경우에 처리 하는 4 개의 받아쓰기 이벤트가 있습니다.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

이 이벤트가 사용자 일시 중지, 일반적으로 문장의 끝입니다. 전체 인식 문자열이 여기 반환 됩니다.

먼저 DictationResult 이벤트를 구독 합니다.

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

DictationResult 콜백을 처리 합니다.

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

이 이벤트는 사용자와 통신 하는 동안에 지속적으로 발생 합니다. 이것이 무엇 인지의 텍스트를 제공 인식기에서 수신 대기 하는 대로 지금 들립니다.

먼저 DictationHypothesis 이벤트를 구독 합니다.

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

DictationHypothesis 콜백을 처리 합니다.

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Stop () 호출에서 발생 하는 시간 제한 또는 일부 다른 오류로 못하게에서 인식기 중지 되 면이 이벤트가 발생 합니다.

먼저 DictationComplete 이벤트를 구독 합니다.

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

DictationComplete 콜백을 처리 합니다.

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

DictationError 콜백을 처리 합니다.

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

구독 하 고 관심 있는 받아쓰기 이벤트를 처리 했으면, 이벤트를 수신 하려면 받아쓰기 인식기를 시작 합니다.

```
dictationRecognizer.Start();
```

에서 더 이상 주변 DictationRecognizer 유지 하려는 경우 이벤트에서 구독을 취소 하 고는 DictationRecognizer를 삭제 해야 합니다.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**팁**
* Start () 및 stop () 메서드는 각각 사용 하도록 설정 하 고 인식 받아쓰기를 비활성화 합니다.
* 인식기를 사용 하 여 완료 되 면 dispose () 메서드를 사용 하 여 사용 되는 리소스를 해제 하려면 삭제 되어야 합니다. 이 리소스를 해제 이러한 자동으로 추가 성능 비용 가비지 수집 중 이전에 해제 되지 않은 경우.
* 시간 제한 설정된 기간 후 발생합니다. 이러한 시간 제한 DictationComplete 이벤트에서 확인할 수 있습니다. 알아야 할 두 가지 시간 제한을 가지가 있습니다.
   1. 인식기 시작 되 고 모든 오디오 첫 번째 5 초 동안 듣지 못합니다, 시간 초과 됩니다.
   2. 인식기에 결과 지정 하지만 다음 20 초 동안 대기를 시도해볼 경우 시간 초과 됩니다.

## <a name="using-both-phrase-recognition-and-dictation"></a>구 인식과 받아쓰기를 사용 하 여

구 인식과 받아쓰기 앱에서 사용 하려는 경우에 완전히 종료 하나 다른 시작 하기 전에 해야 합니다. 여러 KeywordRecognizers 실행 중인 경우 종료할 수 있습니다 이러한 모두 한 번에 사용 하 여:

```
PhraseRecognitionSystem.Shutdown();
```

DictationRecognizer 중지 되 면 모든 인식기를 이전 상태로 복원 하려면 다음을 호출할 수 있습니다.

```
PhraseRecognitionSystem.Restart();
```

PhraseRecognitionSystem을도 다시 시작을 KeywordRecognizer를 시작할 수도 있습니다.

## <a name="using-the-microphone-helper"></a>마이크 도우미 사용

GitHub에서 혼합 현실 도구 키트는 시스템에서 마이크를 사용할 수 없는 경우 개발자가 암시 하는 마이크 도우미 클래스를 포함 합니다. 에 대 한 한 가지 용도 하나 응용 프로그램에 모든 음성 상호 작용 힌트를 표시 하기 전에 시스템에서 마이크 있는지 확인 하고자 것입니다.

마이크 도우미 스크립트에서 찾을 수 있습니다 합니다 [Utilities/스크립트 입력/폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)합니다. GitHub 리포지토리에 포함 되어는 [작은 샘플](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) 도우미를 사용 하는 방법을 설명 합니다.

## <a name="voice-input-in-mixed-reality-toolkit"></a>혼합 현실 도구 키트의 음성 입력
이 장면에서 음성 입력의 예제를 찾을 수 있습니다.

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
