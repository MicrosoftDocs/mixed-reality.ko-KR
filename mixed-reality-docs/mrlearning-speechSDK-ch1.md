---
title: Azure Speech Services 자습서-1. 음성 인식 및 기록을 통합 하 고 사용
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 4baef90f8e00e5da1063c708ae24d2057e0dc227
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438377"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="1bdee-105">1. 음성 인식 및 기록을 통합 하 고 사용</span><span class="sxs-lookup"><span data-stu-id="1bdee-105">1. Integrating and using speech recognition and transcription</span></span>

<span data-ttu-id="1bdee-106">이 자습서에서는 HoloLens 2와 함께 Azure Cognitive Services Speech SDK를 사용 하는 방법을 탐색 하는 혼합 현실 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-106">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="1bdee-107">이 자습서 시리즈를 마치면 장치의 마이크를 사용 하 여 음성 텍스트를 실시간으로 높여줄, 음성을 다른 언어로 번역 하 고, 음성 SDK의 의도 기능을 활용 하 여 음성 명령을 이해 하는 데 사용할 수 있습니다. 인공 지능.</span><span class="sxs-lookup"><span data-stu-id="1bdee-107">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="1bdee-108">목표</span><span class="sxs-lookup"><span data-stu-id="1bdee-108">Objectives</span></span>

- <span data-ttu-id="1bdee-109">Azure Speech SDK를 HoloLens 2 응용 프로그램에 통합 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-109">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="1bdee-110">음성 명령을 사용 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="1bdee-110">Learn how to use voice commands</span></span>
- <span data-ttu-id="1bdee-111">음성 텍스트 기능 사용 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="1bdee-111">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="1bdee-112">지침</span><span class="sxs-lookup"><span data-stu-id="1bdee-112">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="1bdee-113">시작</span><span class="sxs-lookup"><span data-stu-id="1bdee-113">Getting Started</span></span>

1. <span data-ttu-id="1bdee-114">Unity를 시작 하 고 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-114">Start Unity, and create a new project.</span></span> <span data-ttu-id="1bdee-115">프로젝트 이름 Speech SDK 학습 모듈을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-115">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="1bdee-116">프로젝트를 저장할 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-116">Choose a location for where to save your project.</span></span> <span data-ttu-id="1bdee-117">그런 다음 프로젝트 만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-117">Then click Create Project.</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="1bdee-119">참고: 위의 이미지에 표시 된 것 처럼 템플릿이 3D로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-119">Note: Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="1bdee-120">[Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity 패키지를 다운로드 하 고 PC의 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-120">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package, and save it to a folder on your PC.</span></span> <span data-ttu-id="1bdee-121">패키지를 Unity 프로젝트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-121">Import the package into your Unity project.</span></span> <span data-ttu-id="1bdee-122">이 작업을 수행 하는 방법에 대 한 자세한 지침은 [기본 모듈 단원 1](mrlearning-base-ch1.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1bdee-122">For detailed instructions on how to do this, please see [Base Module Lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="1bdee-123">Unity 자산 패키지용 Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage) 를 다운로드 하 여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-123">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="1bdee-124">자산을 클릭 하 고 패키지 가져오기를 선택한 다음 사용자 지정 패키지를 선택 하 여 음성 SDK 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-124">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="1bdee-125">이전에 다운로드 한 음성 SDK 패키지를 찾아서 열어서 가져오기 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-125">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span> 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="1bdee-128">다음 팝업 창에서 가져오기를 클릭 하 여 음성 SDK 패키지 가져오기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-128">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="1bdee-129">아래 이미지에 표시 된 것 처럼 모든 항목이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-129">Ensure all items are checked as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. <span data-ttu-id="1bdee-131">[이 링크](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)를 클릭 하 여 Lunarcom 패키지와 함께 음성 SDK 모듈 자산 팩을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-131">Download the Speech SDK Module asset pack, also know as Lunarcom package by clicking on [this link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span></span> <span data-ttu-id="1bdee-132">Lunarcom asset 패키지는 Azure의 Speech SDK의 실용적인 사용을 보여 주기 위해이 단원 시리즈를 위해 개발 된 자산 및 스크립트 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-132">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="1bdee-133">궁극적으로는 [기본 모듈 자습서](mrlearning-base-ch6.md) 에서 개발한 음력 모듈 어셈블리 환경과 상호 작용 하는 음성 명령 터미널입니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-133">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>

6. <span data-ttu-id="1bdee-134">Mixed Reality Toolkit 및 Speech SDK를 가져오는 것과 비슷한 단계를 수행 하 여 Lunarcom asset 패키지를 Unity 프로젝트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-134">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="1bdee-135">MRTK (Mixed Reality Toolkit)를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-135">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="1bdee-136">이렇게 하려면 창의 위쪽에 있는 혼합 현실 도구 키트 패널을 클릭 한 다음 장면에 추가 및 구성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-136">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. <span data-ttu-id="1bdee-140">이제 장면에 MRTK의 여러 새 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-140">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="1bdee-141">"파일"을 클릭 하 고 [다른 이름으로 저장]을 클릭 한 후 장면 이름을 SpeechScene로 설정 하 여 장면을 다른 이름으로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-141">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span> 

> <span data-ttu-id="1bdee-142">참고: 프로젝트에 MRTK를 추가 하 고 재생 모드로 들어가지 않는 경우 장면에서 Play를 누르면 Unity를 다시 시작 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-142">Note: If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span> 

9. <span data-ttu-id="1bdee-143">계층에서 MixedRealityToolkit 개체를 선택한 상태에서 검사기 패널의 복사 및 사용자 지정을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-143">With the MixedRealityToolkit object selected in your hierarchy, click Copy and Customize in the Inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="1bdee-145">또한 검사기 패널 (계층에서 MixedRealityToolkit 개체가 선택 된 상태)에서 진단 시스템 사용 오른쪽에 있는 상자를 선택 취소 하 여 진단 시스템을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-145">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. <span data-ttu-id="1bdee-147">음성 명령을 사용 하려면 새로 만든 MRTK 프로필을 선택 하 여 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-147">To enable voice commands, select the newly created MRTK profile to customize.</span></span> <span data-ttu-id="1bdee-148">이 자습서에서는 음성 인식 및 기록을 위해 입력 음성 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-148">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="1bdee-149">음성 설정을 변경할 수 있도록 입력 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-149">Lets clone the input profile to make changes to speech settings.</span></span>

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. <span data-ttu-id="1bdee-152">입력 프로필을 복제 한 후 음성 명령으로 이동 하 여 음성 명령을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-152">Once the input profile is cloned, go to speech commands and clone the speech commands.</span></span>

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. <span data-ttu-id="1bdee-155">이제 음성 명령에서 "일반 설정"으로 이동 하 고 "시작 동작"을 "수동 시작"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-155">Now under speech commands, go to "General Settings" and set "Start Behavior" to "Manual Start"</span></span>

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. <span data-ttu-id="1bdee-157">프로젝트 패널에서 Lunarcom 폴더를 확장 하 고 Lunarcom_Base prefab를 계층 구조로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-157">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. <span data-ttu-id="1bdee-159">계층에서 Lunarcom_Base 개체를 선택 하 고 위치가 x = 0, y = 0 및 z = 0으로 설정 되어 있고 x = 0, y = 0 및 z = 0으로 설정 된 회전을 설정 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-159">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="1bdee-160">크기를 읽기 x = 0.008, y = 0.008 및 z = 0.01로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-160">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="1bdee-162">구성 요소 추가를 클릭 하 고 LunarcomController를 검색 한 다음 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-162">Click Add Component, and search for and select LunarcomController.</span></span> <span data-ttu-id="1bdee-163">이 스크립트는 6 단계에서 가져온 Lunarcom asset pack에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-163">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="1bdee-165">응용 프로그램을 Azure Cognitive Services에 연결 하려면 음성 서비스에 대 한 구독 키 (API 키 라고도 함)를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-165">To connect our applicaiton to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="1bdee-166">[여기](https://docs.microsoft.com//azure/cognitive-services/speech-service/get-started) 의 지침에 따라 무료 구독 키를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-166">Follow the instructions at [here](https://docs.microsoft.com//azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="1bdee-167">구독 키를 가져온 후 아래 이미지에 나와 있는 것 처럼 검사기 패널에서 LunarcomController 구성 요소의 Speech Service API 키 필드에 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-167">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

18. <span data-ttu-id="1bdee-168">구독 키에 등록할 때 선택한 지역을 검사기 패널의 LunarcomController 구성 요소에 있는 음성 서비스 지역 필드에 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-168">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="1bdee-169">예를 들어 "westus"의 지역 "미국 서 부" 형식에 대해</span><span class="sxs-lookup"><span data-stu-id="1bdee-169">For example, for the region "West US" type in "westus"</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="1bdee-171">계층에서 왼쪽에 있는 화살표를 클릭 하 여 Lunarcom_Base 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-171">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="1bdee-172">그런 다음 아래 그림에 표시 된 것 처럼 자식 개체 "터미널"에 대해 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-172">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="1bdee-173">Lunarcom_Base가 선택 된 상태에서 아래 이미지에 표시 된 것 처럼 Lunarcom 텍스트를 클릭 하 여 계층에서 검사기 패널의 LunarcomController 구성 요소에 있는 출력 텍스트 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-173">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

21. <span data-ttu-id="1bdee-174">터미널 개체와 연결 라이트 컨트롤러 슬롯에 대 한 연결 조명 개체를 사용 하 여 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-174">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="1bdee-176">검사기 패널에서 LunarcomController 스크립트의 Lunarcom Buttons 섹션 옆에 있는 화살표를 클릭 하 고 크기를 3으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-176">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="1bdee-177">Enter 키를 누르거나를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-177">Press Enter or Return.</span></span> <span data-ttu-id="1bdee-178">이렇게 하면 세 개의 새 요소 필드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-178">This causes three new Element fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="1bdee-180">계층 구조에서 옆에 있는 화살표를 클릭 하 고 위와 동일한 프로세스를 사용 하 여 Lunarcom 단추를 확장 하 고, gameobject의 LunarcomController 구성 요소에서 Mic, 위성 및 로켓을 각각 0, 1 및 2 참조 요소로 끌어 옵니다. 검사기 패널.</span><span class="sxs-lookup"><span data-stu-id="1bdee-180">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="1bdee-182">계층에서 Lunarcom_Base "개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-182">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="1bdee-183">검사기 패널에서 구성 요소 추가를 클릭 하 고 LunarcomWakeWordRecognizer를 검색 한 다음 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-183">Click Add Component in the inspector panel, and search for and select LunarcomWakeWordRecognizer.</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="1bdee-185">절전 모드 해제 단어 슬롯에서 터미널 활성화를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-185">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="1bdee-186">Word 슬롯 해제에서 터미널 해제를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-186">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="1bdee-188">디바이스로 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="1bdee-188">Build your application to your device</span></span>

1. <span data-ttu-id="1bdee-189">파일 > 빌드 설정으로 이동 하 여 빌드 설정 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-189">Open the build settings window again by going to File>Build Settings.</span></span>

![1 단원 Chapter5 1 단계](images/Lesson1Chapter5Step1.JPG)

2. <span data-ttu-id="1bdee-191">“Add Open Scenes” 단추를 클릭하여 사용하려는 장면이 "Scenes in Build" 목록에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-191">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>
3. <span data-ttu-id="1bdee-192">플레이어 설정 단추를 누르고 게시 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-192">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="1bdee-193">기능 아래에서 인터넷, 인터넷 클라이언트 서버, 개인 네트워크 클라이언트 서버, 마이크 및 공간 인식을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-193">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Microphone and Spatial Perception.</span></span>
4. <span data-ttu-id="1bdee-194">동일한 플레이어 설정에서 XR 설정으로 이동 하 고에서 지원 되는 가상 현실를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-194">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>
5. <span data-ttu-id="1bdee-195">Build 단추를 눌러 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-195">Press the Build button to begin the build process.</span></span>

![1 단원 Chapter5 3 단계](images/Lesson1Chapter5Step3.JPG)

6. <span data-ttu-id="1bdee-197">애플리케이션의 새 폴더를 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-197">Create and name a new folder for your application.</span></span> <span data-ttu-id="1bdee-198">아래 이미지에서는 애플리케이션을 포함할 폴더가 이름 "App"을 사용하여 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-198">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="1bdee-199">“Select Folder”를 클릭하여 새로 만든 폴더로 빌드를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-199">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="1bdee-200">빌드가 완료된 후에 Unity에서 "Build Settings" 창을 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-200">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 

![1 단원 Chapter5 4 단계](images/Lesson1Chapter5Step4.JPG)

> <span data-ttu-id="1bdee-202">참고: 빌드가 실패 하는 경우 다시 빌드를 시도 하거나 Unity를 다시 시작 하 고 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-202">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="1bdee-203">"Error: CS0246 = using 지시문 또는 어셈블리 참조가 있는지 확인 하십시오."와 같은 오류가 표시 되는 경우 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) 를 설치 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-203">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span>

7. <span data-ttu-id="1bdee-204">빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-204">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="1bdee-205">".Sln" 솔루션 파일을 두 번 클릭 하 여 Visual Studio에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-205">Double click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

> <span data-ttu-id="1bdee-206">참고: 새로 만든 폴더 (이전 단계에서 명명 규칙을 준수 하는 경우 "App" 폴더)를 열어야 합니다 .이 폴더에는 빌드 폴더 내에 있는 .sln 파일과 혼동 하지 않는 유사 하 게 이름이 지정 된 .sln 파일이 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-206">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="1bdee-208">참고: Visual Studio에서 새 구성 요소를 설치 하도록 요청 하는 경우 잠시 시간을 두고 ["도구 설치" 페이지](install-the-tools.md) 에 지정 된 대로 모든 필수 구성 요소를 설치 했는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="1bdee-208">Note: If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

8. <span data-ttu-id="1bdee-209">USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-209">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="1bdee-210">이러한 단원 지침에서는 사용자가 HoloLens 2 디바이스를 사용하여 테스트를 배포한다고 가정하지만, [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 [테스트용으로 로드할 앱 패키지](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)를 만들도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-210">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>
9. <span data-ttu-id="1bdee-211">디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-211">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="1bdee-212">이번에 처음으로 HoloLens 2에 배포하는 경우리면 Visual Studio에서 pin 사용하여 HoloLens 2에 연결하도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-212">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="1bdee-213">개발자 모드를 사용하도록 설정하거나 Visual Studio와 페어링해야 하는 경우 [다음 지침](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="1bdee-213">Please follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

10. <span data-ttu-id="1bdee-214">"Release" 구성과 "ARM" 아키텍처를 선택하여 HoloLens 2로 빌드하기 위해 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-214">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

![1 단원 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

11. <span data-ttu-id="1bdee-216">마지막 단계는 디버그>디버깅하지 않고 시작을 선택하여 디바이스로 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-216">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="1bdee-217">"디버깅하지 않고 시작"을 선택하면 빌드 성공 시 애플리케이션이 디바이스에서 즉시 시작되지만, Visual Studio에 디버깅 정보가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-217">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="1bdee-218">따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-218">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="1bdee-219">빌드>솔루션 배포를 선택하여 디바이스로 배포할 때 애플리케이션이 자동으로 시작되지 않도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-219">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

![1 단원 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a><span data-ttu-id="1bdee-221">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-221">Congratulations</span></span>

<span data-ttu-id="1bdee-222">Azure에서 제공 하는 응용 프로그램에서 음성 인식을 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-222">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="1bdee-223">응용 프로그램을 실행 하 여 모든 기능과 기능이 제대로 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-223">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="1bdee-224">22 단계에서 입력 한 절전 모드 해제 단어를 말한 후 터미널을 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-224">Start with saying the wake word you typed in Step 22, Activate Terminal.</span></span> <span data-ttu-id="1bdee-225">마이크 단추를 선택 하 여 음성 인식을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-225">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="1bdee-226">말하기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-226">Begin speaking.</span></span> <span data-ttu-id="1bdee-227">말할 때 터미널에 transcribed 단어가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-227">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="1bdee-228">음성 인식을 중지 하려면 마이크 단추를 두 번 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-228">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="1bdee-229">터미널을 해제 하 여 Lunarcom 터미널을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-229">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="1bdee-230">다음 단원에서는 장치 지원 음성 인식을 사용 하도록 동적으로 전환 하는 방법에 대해 설명 합니다 .이는 HoloLens 2가 오프 라인 상태 이기 때문에 Azure의 speech SDK를 사용할 수 없는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="1bdee-230">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="1bdee-231">다음 자습서: 2. 로컬 음성-텍스트 번역을 위한 오프 라인 모드 추가</span><span class="sxs-lookup"><span data-stu-id="1bdee-231">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)

