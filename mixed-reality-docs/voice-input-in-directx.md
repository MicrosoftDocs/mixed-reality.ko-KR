---
title: DirectX의 음성 입력
description: Windows Mixed Reality DirectX 앱에서 음성 명령 및 작은 구 및 문장 인식을 구현 하는 방법을 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 연습, 음성 명령, 구, 인식, 음성, directx, 플랫폼, cortana, windows 혼합된 현실
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605102"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="7988a-104">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="7988a-104">Voice input in DirectX</span></span>

<span data-ttu-id="7988a-105">이 항목에서는 구현 하는 방법에 설명 [음성 명령](voice-input.md), 및 Windows Mixed Reality에 대 한 DirectX 앱에서 작은 구 및 문장 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="7988a-106">이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="7988a-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="7988a-107">개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="7988a-108">연속 음성 명령 인식 하는 데는 SpeechRecognizer</span><span class="sxs-lookup"><span data-stu-id="7988a-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="7988a-109">이 섹션에서는 앱에 음성 명령을 사용할 수 있도록 연속 음성 인식 기능을 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="7988a-110">이 연습에서는 코드를 사용 합니다 [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="7988a-111">샘플을 실행할 때 이름 회전 큐브의 색을 변경 하려면 등록 된 색 명령 중 하나를 말하십시오.</span><span class="sxs-lookup"><span data-stu-id="7988a-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="7988a-112">먼저 새를 만듭니다 **Windows::Media::SpeechRecognition::SpeechRecognizer** 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="7988a-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="7988a-113">*HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="7988a-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="7988a-114">인식기가 수신 대기에 대 한 음성 명령의 목록을 만드는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="7988a-115">여기서는 홀로그램의 색을 변경 하는 명령 집합을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="7988a-116">또한 편의 위해 데이터를 사용 하 여 명령에 대 한 나중에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="7988a-117">사전에 없을 수도 있는 음성 단어를 사용 하 여 명령은 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="7988a-118">명령 목록은 음성 인식기에 대 한 제약 조건 목록에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="7988a-119">사용 하 여 이렇게를 [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="7988a-120">구독 합니다 [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) 음성 인식기의 이벤트 [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="7988a-121">이 이벤트에 명령 중 하나에서 인식 하는 경우 앱을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="7988a-122">프로그램 **OnResultGenerated** 이벤트 처리기에서 이벤트 데이터를 수신 된 [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="7988a-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="7988a-123">신뢰도 정의한 임계값을 초과 하는 경우 이벤트가 발생 한 앱 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="7988a-124">만들 수 있도록 이벤트 데이터를 저장 합니다. 후속 업데이트 루프에서 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="7988a-125">From *HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="7988a-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="7988a-126">확인 앱 시나리오에 적용할 수 있지만 데이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="7988a-127">이 예제 코드에서는 사용자의 명령에 따라 회전 홀로그램 큐브의 색을 변경 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="7988a-128">From *HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="7988a-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="7988a-129">음성 구 및 문장 원 샷 인식 받아쓰기 사용</span><span class="sxs-lookup"><span data-stu-id="7988a-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="7988a-130">구 또는 문장 사용자가 음성에 대 한 수신 대기 하도록 음성 인식기를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="7988a-131">이 경우에는 예상 되는 입력 형식을 음성 인식기에 알려주는 SpeechRecognitionTopicConstraint 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="7988a-132">앱 워크플로 이러한 유형의 사용 사례에 대 한 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="7988a-133">SpeechRecognizer 만들고 UI 프롬프트를 제공 즉시 읽을 명령에 대 한 수신 대기를 시작 하는 앱.</span><span class="sxs-lookup"><span data-stu-id="7988a-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="7988a-134">사용자는 구 또는 문장 말합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="7988a-135">사용자의 음성 인식을 수행 하 고 앱으로 결과 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="7988a-136">이 시점에서 응용 프로그램 인식 되었음을 나타내는에서는 UI 프롬프트를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="7988a-137">에 응답 하려면 신뢰도 수준 및 음성 인식 결과의 신뢰도 수준에 따라 앱 결과 처리 하 고 적절 하 게 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="7988a-138">이 섹션에는 SpeechRecognizer 만들고 제약 조건의 컴파일 음성 입력에 대 한 수신 대기 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="7988a-139">다음 코드는이 예에서 웹 검색을 위해 최적화 된 항목 제약 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="7988a-140">컴파일 성공 하면 음성 인식 기능을 사용 하 여 진행 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="7988a-141">결과 앱에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-141">The result is then returned to the app.</span></span> <span data-ttu-id="7988a-142">우리는 결과에 확신 하는 경우 명령을 처리할 수 있습니다 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="7988a-143">이 코드 예제에서는 보통 이상 신뢰도 사용 하 여 결과 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="7988a-144">음성 인식 기능을 사용할 때마다 사용자가 시스템 개인 정보 설정에서 마이크를 해제 나타낼 수 있는 예외 않도록 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="7988a-145">인식 하는 동안 또는 초기화 하는 동안 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="7988a-146">**참고:** 미리 정의 된 몇 가지 [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) 음성 인식 기능을 최적화 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="7988a-147">받아쓰기 최적화 하려는 경우 받아쓰기 시나리오를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="7988a-148">음성을 사용 하 여 웹 검색을 수행 하려면, 하는 경우 다음과 같은 웹 관련 시나리오 제약 조건을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="7988a-149">양식을 채울 수 형식 제약 조건을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="7988a-150">이 경우 양식 입력에 최적화 된 고유한 문법 적용할 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="7988a-151">SRGS 형식을 사용 하 여 사용자 고유의 문법을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="7988a-152">Continuous, 자유 형식 음성 받아쓰기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="7988a-153">연속 받아쓰기 시나리오에 대 한 Windows 10 UWP 음성 코드 샘플을 참조 [여기 있습니다.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="7988a-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="7988a-154">품질 저하를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-154">Handle degradation in quality</span></span>

<span data-ttu-id="7988a-155">환경에서 조건을 작업에서 음성 인식을 방해 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="7988a-156">예를 들어 대화방 너무 노이즈가 발생할 수 있습니다 또는 사용자가 너무 대용량 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="7988a-157">음성 인식 API를 돕고 가능한 경우 품질에서 저하 시킨 된 조건에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="7988a-158">이 정보는 WinRT 이벤트를 사용 하 여 앱에 푸시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="7988a-159">이 이벤트를 구독 하는 방법의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="7988a-160">코드 샘플에서는 디버그 콘솔에 조건 정보를 쓸 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="7988a-161">앱 UI, 음성 합성 및 등을 통해 사용자에 게 피드백을 제공 하거나 음성 품질에서 임시 감소에 의해 중단 될 경우 다르게 동작 하도록 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="7988a-162">DirectX 앱을 만드는 ref 클래스를 사용 하지 않는 경우 해야 구독을 취소 하면 이벤트에서 해제 또는 사용자 음성 인식기를 다시 만들기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="7988a-163">HolographicSpeechPromptSample 인식, 중지 및 이벤트 구독 취소 하는 루틴에 다음과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="7988a-164">사용 하 여 음성 합성 청각적 음성 안내를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="7988a-165">Holographic 음성 샘플 음성 합성을 사용 하 여 사용자에 게 청각적 지침 제공.</span><span class="sxs-lookup"><span data-stu-id="7988a-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="7988a-166">이 항목에서는 합성된 음성 샘플을 만들고 HRTF 오디오 Api를 사용 하 여 다시 재생 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="7988a-167">구 입력을 요청 하는 경우 고유한 음성 프롬프트를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="7988a-168">이 수에 유용 나타내는 수 읽을 음성 명령, 연속 인식 시나리오의 경우.</span><span class="sxs-lookup"><span data-stu-id="7988a-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="7988a-169">다음은 음성 신시사이저;를 사용 하 여 그렇게 하는 방법의 예 또한 미리 녹음 된 음성 클립, 시각적 UI 또는 다른 표시기의 예를 들어 프롬프트 동적 하지 않은 시나리오에서 말할 내용을 사용할 수는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="7988a-170">먼저 SpeechSynthesizer 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="7988a-171">합성 될 텍스트를 사용 하 여 문자열도 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="7988a-172">음성은 SynthesizeTextToStreamAsync를 사용 하 여 비동기적으로 합성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="7988a-173">여기에서 시작 된 음성 합성을 비동기 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="7988a-174">음성 합성을 바이트 스트림으로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="7988a-175">초기화 하는 바이트 스트림;를 사용 하 여는 XAudio2 음성 holographic 코드 샘플에 대 한에서는 재생할 HRTF 오디오 효과로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7988a-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="7988a-176">으로 음성 인식 음성 합성 예외가 throw 됩니다 문제가 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="7988a-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7988a-177">참조</span><span class="sxs-lookup"><span data-stu-id="7988a-177">See also</span></span>
* [<span data-ttu-id="7988a-178">음성 앱 디자인</span><span class="sxs-lookup"><span data-stu-id="7988a-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="7988a-179">DirectX의 공간 소리</span><span class="sxs-lookup"><span data-stu-id="7988a-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="7988a-180">SpeechRecognitionAndSynthesis 샘플</span><span class="sxs-lookup"><span data-stu-id="7988a-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
