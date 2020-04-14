---
title: DirectX의 음성 입력
description: Windows Mixed Reality 용 DirectX 앱에서 음성 명령과 작은 구와 문장 인식을 구현 하는 방법에 대해 설명 합니다.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 연습, 음성 명령, 구, 인식, 음성, directx, 플랫폼, cortana, windows mixed 현실
ms.openlocfilehash: 2837a0fc42e8fdebb2e1facee118d20b5668cd43
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277971"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="3d1b4-104">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="3d1b4-104">Voice input in DirectX</span></span>

<span data-ttu-id="3d1b4-105">이 문서에서는 Windows Mixed Reality 용 DirectX 앱에서 [음성 명령과](voice-input.md) 작은 문구 및 문장 인식 기능을 구현 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-105">This article explains how to implement [voice commands](voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="3d1b4-106">이 문서의 코드 조각에서는 C++ [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되는 C + 17-so-far working 규격 C++/winrt가 아닌/cx를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-106">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="3d1b4-107">개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-107">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="3d1b4-108">연속 음성 인식을 위해 SpeechRecognizer 사용</span><span class="sxs-lookup"><span data-stu-id="3d1b4-108">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="3d1b4-109">이 섹션에서는 연속 음성 인식을 사용 하 여 앱에서 음성 명령을 사용 하도록 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-109">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="3d1b4-110">이 연습에서는 [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) 샘플의 코드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-110">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="3d1b4-111">샘플을 실행 하는 경우 등록 된 색 명령 중 하나의 이름을 말하기 회전 큐브의 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="3d1b4-112">먼저 새 *Windows:: Media:: SpeechRecognition:: SpeechRecognizer* 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-112">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="3d1b4-113">From *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="3d1b4-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="3d1b4-114">인식기에서 수신 대기할 음성 명령 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-114">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="3d1b4-115">여기서는 홀로그램의 색을 변경 하는 명령 집합을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="3d1b4-116">편의를 위해 나중에 명령에 사용할 데이터도 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-116">For convenience, we also create the data that we'll use for the commands later.</span></span>

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

<span data-ttu-id="3d1b4-117">사전에 없을 수 있는 윗주 단어를 사용 하 여 명령을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-117">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="3d1b4-118">음성 인식기에 대 한 제약 조건 목록에 명령 목록을 로드 하려면 [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-118">To load the commands list into the list of constraints for the speech recognizer use a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

<span data-ttu-id="3d1b4-119">음성 인식기의 [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)에서 [resultgenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-119">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="3d1b4-120">이 이벤트는 명령 중 하나가 인식 될 때 앱에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-120">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="3d1b4-121">*Onresultgenerated* 이벤트 처리기는 [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) 인스턴스에서 이벤트 데이터를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-121">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="3d1b4-122">신뢰가 정의한 임계값 보다 크면 앱에서 이벤트가 발생 한 것을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-122">If the confidence is greater than the threshold that you defined, your app should note that the event happened.</span></span> <span data-ttu-id="3d1b4-123">후속 업데이트 루프에서 사용할 수 있도록 이벤트 데이터를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-123">Save the event data so that you can use it in a subsequent update loop.</span></span>

<span data-ttu-id="3d1b4-124">*HolographicVoiceInputSampleMain*에서:</span><span class="sxs-lookup"><span data-stu-id="3d1b4-124">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

<span data-ttu-id="3d1b4-125">예제 코드에서는 사용자의 명령에 따라 회전 하는 홀로그램 큐브의 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-125">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="3d1b4-126">*HolographicVoiceInputSampleMain:: Update*에서:</span><span class="sxs-lookup"><span data-stu-id="3d1b4-126">From *HolographicVoiceInputSampleMain::Update*:</span></span>

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a><span data-ttu-id="3d1b4-127">"원 샷" 인식 사용</span><span class="sxs-lookup"><span data-stu-id="3d1b4-127">Use "one-shot" recognition</span></span>

<span data-ttu-id="3d1b4-128">사용자가 말하는 구 또는 문장을 수신 하도록 음성 인식기를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-128">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="3d1b4-129">이 경우 음성 인식기에 게 필요한 입력 유형을 알려 주는 *SpeechRecognitionTopicConstraint* 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-129">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="3d1b4-130">이 시나리오에 대 한 앱 워크플로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-130">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="3d1b4-131">앱은 SpeechRecognizer을 만들고, UI 프롬프트를 제공 하 고, 음성 명령 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-131">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="3d1b4-132">사용자가 구 또는 문장을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-132">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="3d1b4-133">사용자의 음성이 인식 되 고 결과가 앱으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-133">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="3d1b4-134">이 시점에서 앱은 인식이 발생 했음을 나타내는 UI 프롬프트를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-134">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="3d1b4-135">응답 하려는 신뢰 수준 및 음성 인식 결과의 신뢰 수준에 따라 앱에서 결과를 처리 하 고 적절 하 게 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-135">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="3d1b4-136">이 섹션에서는 SpeechRecognizer를 만들고, 제약 조건을 컴파일하고, 음성 입력을 수신 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-136">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="3d1b4-137">다음 코드는 토픽 제약 조건을 컴파일합니다 .이 경우 웹 검색에 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-137">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="3d1b4-138">컴파일이 성공 하면 음성 인식을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-138">If compilation succeeds, we can proceed with speech recognition.</span></span>

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

<span data-ttu-id="3d1b4-139">그런 다음 결과가 앱으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-139">The result is then returned to the app.</span></span> <span data-ttu-id="3d1b4-140">결과를 충분히 확신 하는 경우 명령을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-140">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="3d1b4-141">이 코드 예제에서는 보통 신뢰도를 사용 하 여 결과를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-141">This code example processes results with at least medium confidence.</span></span>

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

<span data-ttu-id="3d1b4-142">음성 인식을 사용할 때마다 사용자가 시스템 개인 정보 설정에서 마이크를 해제 했음을 나타낼 수 있는 예외를 조사 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-142">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="3d1b4-143">이는 초기화 또는 인식 중에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-143">This can happen during initialization or recognition.</span></span>

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> <span data-ttu-id="3d1b4-144">음성 인식을 최적화 하는 데 사용할 수 있는 미리 정의 된 몇 가지 [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-144">There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="3d1b4-145">받아쓰기를 최적화 하려면 받아쓰기 시나리오를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-145">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="3d1b4-146">음성 웹 검색의 경우 다음과 같은 웹 관련 시나리오 제약 조건을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-146">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="3d1b4-147">폼 제약 조건을 사용 하 여 양식을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-147">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="3d1b4-148">이 경우 폼을 채우도록 최적화 된 고유한 문법을 적용 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-148">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="3d1b4-149">SRGS 형식으로 고유한 문법을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-149">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="3d1b4-150">연속 인식 사용</span><span class="sxs-lookup"><span data-stu-id="3d1b4-150">Use continuous recognition</span></span>

<span data-ttu-id="3d1b4-151">연속 받아쓰기 시나리오의 경우 [Windows 10 UWP 음성 코드 샘플](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-151">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="3d1b4-152">품질 저하 처리</span><span class="sxs-lookup"><span data-stu-id="3d1b4-152">Handle quality degradation</span></span>

<span data-ttu-id="3d1b4-153">환경 조건은 음성 인식을 방해 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-153">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="3d1b4-154">예를 들어 대화방에 잡음이 있거나 사용자가 너무 loudly 말할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-154">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="3d1b4-155">음성 인식 API는 가능한 경우 품질 저하를 일으킨 조건에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-155">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="3d1b4-156">이 정보는 WinRT 이벤트를 통해 앱에 푸시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-156">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="3d1b4-157">다음 예제에서는이 이벤트를 구독 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-157">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="3d1b4-158">이 코드 샘플에서는 조건 정보를 디버그 콘솔에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-158">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="3d1b4-159">앱은 UI, 음성 합성 및 다른 방법을 통해 사용자에 게 피드백을 제공 하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-159">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="3d1b4-160">또는 일시적인 품질 감소에 의해 음성이 중단 될 때 다르게 동작 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-160">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

<span data-ttu-id="3d1b4-161">Ref 클래스를 사용 하 여 DirectX 앱을 만들지 않는 경우 음성 인식기를 해제 하거나 다시 만들기 전에 이벤트에서 구독을 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-161">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="3d1b4-162">HolographicSpeechPromptSample에는 인식을 중지 하 고 이벤트를 구독 취소 하는 루틴이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-162">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="3d1b4-163">음성 합성을 사용 하 여 가청 프롬프트 제공</span><span class="sxs-lookup"><span data-stu-id="3d1b4-163">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="3d1b4-164">Holographic speech 샘플은 음성 합성을 사용 하 여 사용자에 게 가청 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-164">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="3d1b4-165">이 섹션에서는 합성 된 음성 샘플을 만든 다음 HRTF 오디오 Api를 통해 다시 재생 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-165">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="3d1b4-166">구 입력을 요청할 때 사용자 고유의 음성 프롬프트를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-166">You should provide your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="3d1b4-167">또한 프롬프트는 연속 인식 시나리오에서 음성 명령을 음성으로 사용할 수 있는 경우를 표시 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-167">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="3d1b4-168">다음 예제에서는 음성 신시사이저를 사용 하 여이 작업을 수행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-168">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="3d1b4-169">미리 녹음 된 음성 클립, 시각적 UI 또는 표시 되는 항목에 대 한 다른 표시기를 사용할 수도 있습니다. 예를 들어, 프롬프트가 동적이 지 않은 시나리오를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-169">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="3d1b4-170">먼저 SpeechSynthesizer 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-170">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="3d1b4-171">또한 합성할 텍스트를 포함 하는 문자열이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-171">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="3d1b4-172">음성은 SynthesizeTextToStreamAsync을 통해 비동기적으로 합성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-172">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="3d1b4-173">여기서는 음성을 합성 하는 비동기 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-173">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="3d1b4-174">음성 합성은 바이트 스트림으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="3d1b4-175">해당 바이트 스트림을 사용 하 여 XAudio2 음성을 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-175">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="3d1b4-176">Holographic 코드 샘플의 경우 HRTF 오디오 효과로 다시 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-176">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

<span data-ttu-id="3d1b4-177">음성 인식과 마찬가지로 음성 합성은 문제가 발생 한 경우 예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1b4-177">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a><span data-ttu-id="3d1b4-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d1b4-178">See also</span></span>
* [<span data-ttu-id="3d1b4-179">음성 앱 디자인</span><span class="sxs-lookup"><span data-stu-id="3d1b4-179">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="3d1b4-180">SpeechRecognitionAndSynthesis 샘플</span><span class="sxs-lookup"><span data-stu-id="3d1b4-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
