---
title: DirectX의 음성 입력
description: Windows Mixed Reality 용 DirectX 앱에서 음성 명령과 작은 구와 문장 인식을 구현 하는 방법에 대해 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 연습, 음성 명령, 구, 인식, 음성, directx, 플랫폼, cortana, windows mixed 현실
ms.openlocfilehash: 0dcfaae13f763c9b8a06910f11558d2fd8e00276
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641081"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="f3f99-104">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="f3f99-104">Voice input in DirectX</span></span>

<span data-ttu-id="f3f99-105">이 항목에서는 Windows Mixed Reality 용 DirectX 앱에서 [음성 명령과](voice-input.md)작은 구와 문장 인식을 구현 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="f3f99-106">이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="f3f99-107">개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="f3f99-108">음성 명령을 연속 해 서 인식 하기 위해 SpeechRecognizer 사용</span><span class="sxs-lookup"><span data-stu-id="f3f99-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="f3f99-109">이 섹션에서는 연속 음성 인식을 사용 하 여 앱에서 음성 명령을 사용 하도록 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="f3f99-110">이 연습에서는 [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) 샘플의 코드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-110">This walkthrough uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="f3f99-111">샘플을 실행 하는 경우 등록 된 색 명령 중 하나의 이름을 말하기 회전 큐브의 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="f3f99-112">먼저 새 **Windows:: Media:: SpeechRecognition:: SpeechRecognizer** 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="f3f99-113">From *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="f3f99-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="f3f99-114">인식기에서 수신 대기할 음성 명령 목록을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="f3f99-115">여기서는 홀로그램의 색을 변경 하는 명령 집합을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="f3f99-116">편의를 위해 나중에 명령에 사용할 데이터도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="f3f99-117">사전에 없을 수 있는 음성 단어를 사용 하 여 명령을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="f3f99-118">명령 목록이 음성 인식기에 대 한 제약 조건 목록에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="f3f99-119">[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) 개체를 사용 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="f3f99-120">음성 인식기의 [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)에서 [resultgenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="f3f99-121">이 이벤트는 명령 중 하나가 인식 될 때 앱에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="f3f99-122">**Onresultgenerated** 이벤트 처리기는 [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) 인스턴스에서 이벤트 데이터를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="f3f99-123">신뢰가 정의한 임계값 보다 크면 앱에서 이벤트가 발생 한 것을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="f3f99-124">후속 업데이트 루프에서 사용할 수 있도록 이벤트 데이터를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="f3f99-125">*HolographicVoiceInputSampleMain*에서:</span><span class="sxs-lookup"><span data-stu-id="f3f99-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="f3f99-126">그러나 응용 프로그램 시나리오에 적용 되는 데이터를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="f3f99-127">예제 코드에서는 사용자의 명령에 따라 회전 하는 홀로그램 큐브의 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="f3f99-128">*HolographicVoiceInputSampleMain:: Update*에서:</span><span class="sxs-lookup"><span data-stu-id="f3f99-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="f3f99-129">음성 구와 문장의 원 샷 인식에 받아쓰기 사용</span><span class="sxs-lookup"><span data-stu-id="f3f99-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="f3f99-130">사용자가 말하는 문구 또는 문장을 수신 하도록 음성 인식기를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="f3f99-131">이 경우 음성 인식기에 게 필요한 입력 유형을 알려 주는 SpeechRecognitionTopicConstraint 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="f3f99-132">앱 워크플로는 다음과 같은 유형의 사용 사례에 대해 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="f3f99-133">앱은 SpeechRecognizer을 만들고, UI 프롬프트를 제공 하 고, 즉시 음성으로 명령을 수신 하기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="f3f99-134">사용자가 구 또는 문장을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="f3f99-135">사용자 음성이 인식 되 고 결과가 앱으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="f3f99-136">이 시점에서 앱은 인식이 발생 했음을 나타내는 UI 프롬프트를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="f3f99-137">응답 하려는 신뢰 수준 및 음성 인식 결과의 신뢰 수준에 따라 앱에서 결과를 처리 하 고 적절 하 게 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="f3f99-138">이 섹션에서는 SpeechRecognizer를 만들고, 제약 조건을 컴파일하고, 음성 입력을 수신 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="f3f99-139">다음 코드는 토픽 제약 조건을 컴파일합니다 .이 경우 웹 검색에 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="f3f99-140">컴파일이 성공 하면 음성 인식을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="f3f99-141">그런 다음 결과가 앱으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-141">The result is then returned to the app.</span></span> <span data-ttu-id="f3f99-142">결과를 충분히 확신 하는 경우 명령을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="f3f99-143">이 코드 예제에서는 보통 신뢰도를 사용 하 여 결과를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="f3f99-144">음성 인식을 사용할 때마다 사용자가 시스템 개인 정보 설정에서 마이크를 해제 했음을 나타내는 예외를 감시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="f3f99-145">이는 초기화 중 또는 인식 중에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="f3f99-146">**참고:** 음성 인식을 최적화 하는 데 사용할 수 있는 미리 정의 된 몇 가지 [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="f3f99-147">받아쓰기를 최적화 하려면 받아쓰기 시나리오를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="f3f99-148">음성을 사용 하 여 웹 검색을 수행 하는 경우 다음과 같이 웹 특정 시나리오 제약 조건을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="f3f99-149">폼 제약 조건을 사용 하 여 양식을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="f3f99-150">이 경우 양식 작성을 위해 최적화 된 고유한 문법을 적용 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="f3f99-151">SRGS 형식을 사용 하 여 고유한 문법을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="f3f99-152">연속 자유 음성 받아쓰기 사용</span><span class="sxs-lookup"><span data-stu-id="f3f99-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="f3f99-153">여기에서 연속 받아쓰기 시나리오에 대 한 Windows 10 UWP 음성 코드 샘플을 참조 하세요 [.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="f3f99-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="f3f99-154">품질 저하 처리</span><span class="sxs-lookup"><span data-stu-id="f3f99-154">Handle degradation in quality</span></span>

<span data-ttu-id="f3f99-155">환경에서의 조건으로 인해 음성 인식이 작동 하지 않는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="f3f99-156">예를 들어 대화방에 잡음이 있거나 사용자가 너무 많은 볼륨을 말할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="f3f99-157">음성 인식 API는 품질 저하를 일으킨 조건에 대해 가능한 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="f3f99-158">이 정보는 WinRT 이벤트를 사용 하 여 앱으로 푸시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="f3f99-159">다음은이 이벤트를 구독 하는 방법의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="f3f99-160">코드 샘플에서는 디버그 콘솔에 조건 정보를 기록 하도록 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="f3f99-161">앱은 UI, 음성 합성 등을 통해 사용자에 게 피드백을 제공 하거나, 일시적 품질 감소에 의해 음성이 중단 될 때 다르게 동작 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="f3f99-162">Ref 클래스를 사용 하 여 DirectX 앱을 만들지 않는 경우 음성 인식기를 해제 하거나 다시 만들기 전에 이벤트에서 구독을 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="f3f99-163">HolographicSpeechPromptSample에는 인식을 중지 하 고 다음과 같은 이벤트를 구독 취소 하는 루틴이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="f3f99-164">음성 합성을 사용 하 여 가청 음성 프롬프트 제공</span><span class="sxs-lookup"><span data-stu-id="f3f99-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="f3f99-165">Holographic speech 샘플은 음성 합성을 사용 하 여 사용자에 게 가청 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="f3f99-166">이 항목에서는 합성 된 음성 샘플을 만들고 HRTF 오디오 Api를 사용 하 여 다시 재생 하는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="f3f99-167">구 입력을 요청할 때 사용자 고유의 음성 프롬프트를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="f3f99-168">이는 연속 인식 시나리오에 대해 음성 명령을 음성으로 지정할 수 있는 경우에도 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="f3f99-169">음성 신시사이저를 사용 하 여이 작업을 수행 하는 방법의 예는 다음과 같습니다. 미리 녹음 된 음성 클립, 시각적 UI 또는 표시 되는 항목에 대 한 기타 표시기를 사용할 수도 있습니다. 예를 들어, 프롬프트가 동적이 지 않은 시나리오를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="f3f99-170">먼저 SpeechSynthesizer 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="f3f99-171">또한 합성 될 텍스트를 포함 하는 문자열이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="f3f99-172">음성은 SynthesizeTextToStreamAsync를 사용 하 여 비동기적으로 합성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="f3f99-173">여기서는 비동기 작업을 시작 하 여 음성을 합성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="f3f99-174">음성 합성은 바이트 스트림으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="f3f99-175">해당 바이트 스트림을 사용 하 여 XAudio2 음성을 초기화할 수 있습니다. holographic 코드 샘플의 경우 HRTF 오디오 효과로 다시 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="f3f99-176">음성 인식과 마찬가지로 음성 합성은 문제가 발생 하는 경우 예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f99-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f3f99-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3f99-177">See also</span></span>
* [<span data-ttu-id="f3f99-178">음성 앱 디자인</span><span class="sxs-lookup"><span data-stu-id="f3f99-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="f3f99-179">SpeechRecognitionAndSynthesis 샘플</span><span class="sxs-lookup"><span data-stu-id="f3f99-179">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
