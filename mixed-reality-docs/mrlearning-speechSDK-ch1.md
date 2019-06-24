# <a name="speech-sdk-learning-module"></a><span data-ttu-id="cdb0e-101">Speech SDK 학습 모듈</span><span class="sxs-lookup"><span data-stu-id="cdb0e-101">Speech SDK Learning Module</span></span>

<span data-ttu-id="cdb0e-102">이 자습서에서는 Azure Cognitive Services 음성 SDK는 HoloLens 2를 사용 하 여 사용을 탐색 하는 혼합 현실 응용 프로그램을 만들게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-102">In this tutorial you will create a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="cdb0e-103">이 자습서 시리즈를 사용 하 여 완료 되 면 장치의 마이크를 사용 하 여 실시간으로 텍스트를 음성 기록, 사용자 음성을 다른 언어로 번역 및 Speech SDK를 사용 하 여 음성 명령을 인식 하도록 의도 기능을 활용 하는 일을 할 수는 인공 지능 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-103">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

<span data-ttu-id="cdb0e-104">목표:</span><span class="sxs-lookup"><span data-stu-id="cdb0e-104">Objectives:</span></span>

- <span data-ttu-id="cdb0e-105">HoloLens 2 응용 프로그램에 Azure Speech SDK를 통합 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-105">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="cdb0e-106">음성 명령을 사용 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="cdb0e-106">Learn how to use voice commands</span></span>
- <span data-ttu-id="cdb0e-107">음성-텍스트 기능을 사용 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="cdb0e-107">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="cdb0e-108">지침</span><span class="sxs-lookup"><span data-stu-id="cdb0e-108">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="cdb0e-109">시작하기</span><span class="sxs-lookup"><span data-stu-id="cdb0e-109">Getting Started</span></span>

1. <span data-ttu-id="cdb0e-110">Unity를 시작 하 고 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-110">Start Unity and create a new project.</span></span> <span data-ttu-id="cdb0e-111">프로젝트 이름을 "Speech SDK 학습 모듈입니다."를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-111">Enter the project name “Speech SDK Learning Module.”</span></span> <span data-ttu-id="cdb0e-112">프로젝트를 저장 하는 위치에 대 한 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-112">Choose a location for where to save your project.</span></span> <span data-ttu-id="cdb0e-113">"프로젝트 만들기." 클릭</span><span class="sxs-lookup"><span data-stu-id="cdb0e-113">Then click "Create Project."</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="cdb0e-115">참고: 위의 이미지에 표시 된 대로 템플릿에 "3D에서"로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-115">Note: Ensure that the template is set to "3D," as shown in the image above.</span></span>

2. <span data-ttu-id="cdb0e-116">다운로드 합니다 [혼합 현실 Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity 패키지를 PC의 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-116">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package and save it to a folder on your PC.</span></span> <span data-ttu-id="cdb0e-117">Unity 프로젝트에 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-117">Import the package into your Unity project.</span></span> <span data-ttu-id="cdb0e-118">이 작업을 수행 하는 방법에 대 한 자세한 내용은 참조 하십시오 [기본 모듈입니다. 1 단원](mrlearning-base-ch1.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-118">For detailed instructions on how to do this, please see [base module lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="cdb0e-119">다운로드 하 여 Azure를 가져와야 [Speech SDK](https://aka.ms/csspeech/unitypackage) Unity 자산 패키지에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-119">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for Unity asset package.</span></span> <span data-ttu-id="cdb0e-120">"자산을" 선택 "패키지 가져오기," 다음 "사용자 지정 패키지 있습니다."를 선택를 클릭 하 여 Speech SDK 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="cdb0e-120">Import the Speech SDK package by clicking on "assets," selecting "import package," then selecting "custom package."</span></span> <span data-ttu-id="cdb0e-121">이전에 다운로드 한 Speech SDK 패키지를 검색 하 여 가져오기 프로세스를 시작 하려면 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-121">Find the Speech SDK package downloaded earlier and open it to begin the importing process.</span></span> 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="cdb0e-123">다음 팝업 창에서 "가져오기" Speech SDK 패키지 가져오기를 시작 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-123">In the next pop-up window, click “Import” to begin importing the Speech SDK package.</span></span> <span data-ttu-id="cdb0e-124">아래 이미지에 나와 있는 것 처럼 모든 항목을 확인을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-124">Ensure all items are checked, as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. <span data-ttu-id="cdb0e-126">다운로드 합니다 [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) 자산 패키지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-126">Download the [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) asset package.</span></span> <span data-ttu-id="cdb0e-127">Lunarcom 자산 패키지는 실제로 Azure의 Speech SDK 사용을 보여 주기 위해 자산 및이 단원 시리즈에 대 한 개발 하는 스크립트 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-127">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="cdb0e-128">음성 명령을 터미널은 궁극적으로 개발 음력 모듈 어셈블리 환경과 상호 연결 되는 것은 [자료 모듈 자습서입니다.](mrlearning-base-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="cdb0e-128">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>
6. <span data-ttu-id="cdb0e-129">혼합 현실 Toolkit 및 Speech SDK를 가져오는 데 비슷한 단계를 수행 하 여 Unity 프로젝트에 Lunarcom 자산 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-129">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="cdb0e-130">혼합된 현실 도구 키트 (MRTK)를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-130">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="cdb0e-131">이 작업을 수행 하 여 창의 위쪽에서 "혼합 현실 Toolkit" 패널에서 클릭 한 다음 "장면 및 구성에 추가 합니다."를 선택</span><span class="sxs-lookup"><span data-stu-id="cdb0e-131">To do this, click on the "Mixed Reality Toolkit" panel in the top of your window, and then select "Add to Scene and Configure."</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. <span data-ttu-id="cdb0e-133">장면은 이제 몇 가지 새 항목에는 MRTK에서 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-133">Your scene will now have several new items in it from the MRTK.</span></span> <span data-ttu-id="cdb0e-134">"File"을 클릭 하 여 다른 이름으로 장면 저장 "다른 이름으로 저장"을 "SpeechScene" 장면 이름을 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-134">Save your scene under a different name by clicking on "file," then "save as" and name your scene “SpeechScene”.</span></span> 

   > <span data-ttu-id="cdb0e-135">참고: MRTK 프로젝트에 추가한 후 "실행" 모드로 전환 되지 않는 장면에 있는 재생 단추를 누르기를 Unity를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-135">Note: If you press the play button on your scene after you add the MRTK to your project, and it doesn't enter the "play" mode, you may need to restart Unity.</span></span> 

9. <span data-ttu-id="cdb0e-136">계층에서 선택한 "MixedRealityToolkit" 개체를 사용 하 여 검사기 패널에서 "복사 및 사용자 지정"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-136">With the “MixedRealityToolkit" object selected in your hierarchy, click "copy and customize" in the inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="cdb0e-138">또한 (계층에서 선택한 "MixedRealityToolkit" 개체)와 검사기 창에서 "사용 진단 System."는 오른쪽에 있는 확인란의 선택을 취소 하 여 진단 시스템 해제</span><span class="sxs-lookup"><span data-stu-id="cdb0e-138">Also in the inspector panel (with the “MixedRealityToolkit" object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of "Enable Diagnostics System."</span></span>

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. <span data-ttu-id="cdb0e-140">프로젝트 패널에서 "Lunarcom" 폴더를 확장 하 고 "Lunarcom_Base" prefab 계층으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-140">In the project panel, expand the "Lunarcom" folder and drag the "Lunarcom_Base" prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. <span data-ttu-id="cdb0e-142">계층의 "Lunarcom_Base" 개체를 선택 하 고 위치 x로 설정 되어 있는지 확인 합니다. = 0, y = 0 및 z = 0, x로 회전 뿐만 아니라 = 0, y = 0 및 z = 0.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-142">Select the "Lunarcom_Base" object in your hierarchy and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="cdb0e-143">눈금이 줄어 설정 x 0.008, = y 0.008, 및 z = = 0.01 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-143">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. <span data-ttu-id="cdb0e-145">"구성 요소 추가" 클릭 합니다. 검색 하 고 "LunarcomController."를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-145">Click "add component" and search for and select “LunarcomController.”</span></span> <span data-ttu-id="cdb0e-146">이 스크립트는 6 단계에서에서 가져온 Lunarcom 자산 팩에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-146">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. <span data-ttu-id="cdb0e-148">앱에서 Azure Cognitive Services에 연결 하려면 입력할 "구독 키" 라고도 "API 키" Speech Service에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-148">To connect our app to Azure Cognitive Services, you must enter a "subscription key" also known as an "API Key" for the Speech Service.</span></span> <span data-ttu-id="cdb0e-149">지침을 따르세요 [이 링크](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) 무료 구독 키를 확보 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-149">Follow the instructions at [this link](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="cdb0e-150">구독 키를 가져온 후 입력 [관리자] 패널에 있는 "LunarcomController" 구성 "음성 서비스 API 키" 필드에 아래 그림과에서 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-150">Once you obtain the subscription key, enter it into the “Speech Service API Key” field of the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>

15. <span data-ttu-id="cdb0e-151">등록할 때 "LunarcomController" 구성 요소 검사기 패널에서 "음성 서비스 지역" 필드에 구독 키에 대 한 선택한 영역을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-151">Enter the Region that you chose when you signed up for the subscription key into the “Speech Service Region” field of the "LunarcomController" component in the inspector panel.</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. <span data-ttu-id="cdb0e-153">계층의 왼쪽에 있는 화살표를 클릭 하 여 "Lunarcom_Base" 개체를 차례로 확장 한 후 아래 그림과에서 같이 "터미널" 해당 자식 개체에 대해 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-153">In your hierarchy, expand the "Lunarcom_Base" object by clicking the arrow to the left of it, then do the same for its child object, "Terminal" as shown in the image below.</span></span>

17. <span data-ttu-id="cdb0e-154">"Lunarcom_Base"를 선택한 상태에서 누르고 아래 이미지에 표시 된 대로 검사기 창에서 "Lunarcom" 계층 구조에서에서 텍스트를 "출력 텍스트" 슬롯 "LunarcomController" 구성 요소를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-154">While "Lunarcom_Base" is selected, click and drag “Lunarcom Text” from the hierarchy to the "Output Text" slot in the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>
18. <span data-ttu-id="cdb0e-155">이제 "터미널" 슬롯에 "Light 컨트롤러 연결" 슬롯 "Light 연결" 개체 "터미널" 개체를 사용 하 여 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-155">Now do the same thing with the "Terminal" object into the "terminal" slot and the "Connection Light" object to the "Connection Light Controller" slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. <span data-ttu-id="cdb0e-157">[관리자] 패널에서 "LunarcomController" 스크립트 "Lunarcom 단추" 섹션 옆의 화살표를 클릭 하 고 3으로 크기를 변경 또는 Return 키를 눌러 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-157">Click the arrow next to the "Lunarcom Buttons" section of the "LunarcomController" script in the inspector panel and change the size to 3 and press the Enter or Return key on your keyboard.</span></span> <span data-ttu-id="cdb0e-158">이렇게 하면 세 개의 새로운 "Element" 필드 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-158">This will cause three new "Element" fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. <span data-ttu-id="cdb0e-160">계층에서 옆에 있는 화살표를 클릭 하 여 "Lunarcom 단추"를 확장 하 고 "LunarcomController" 구성 요소에서 각각의 요소 0, 1 및 2 참조로 Mic, 위성, 및 Rocket gameobject를 끌어 위와 동일한 프로세스를 사용 하 여 검사기 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-160">Expand the "Lunarcom Buttons" by clicking the arrow next to it in your hierarchy and, using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references respectively in the "LunarcomController" component in the inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. <span data-ttu-id="cdb0e-162">계층에서 "Lunarcom_Base" 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-162">Select the "Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="cdb0e-163">검사기 창에서 "추가 구성 요소"를 클릭 합니다. 검색 하 고 "LunarcomWakeWordRecognizer."를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-163">Click “Add Component” in the inspector panel and search for and select “LunarcomWakeWordRecognizer.”</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. <span data-ttu-id="cdb0e-165">"Wake 단어" 슬롯에서 "Activate 터미널." 입력</span><span class="sxs-lookup"><span data-stu-id="cdb0e-165">In the "Wake Word" slot, type in "Activate Terminal."</span></span> <span data-ttu-id="cdb0e-166">또한 "해제 단어" 슬롯에서 "해제 터미널." 입력</span><span class="sxs-lookup"><span data-stu-id="cdb0e-166">Also, in the "Dismiss Word" slot, type in "Dismiss Terminal."</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a><span data-ttu-id="cdb0e-168">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-168">Congratulations</span></span>

<span data-ttu-id="cdb0e-169">Azure에서 구동 응용 프로그램에서 음성 인식 기능을 설정한!</span><span class="sxs-lookup"><span data-stu-id="cdb0e-169">You've set up voice recognition in your application, powered by Azure!</span></span> <span data-ttu-id="cdb0e-170">모든 기능이 제대로 작동 하도록 응용 프로그램을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-170">Run the application to ensure all functions are working properly.</span></span> <span data-ttu-id="cdb0e-171">절전 모드 해제 마디 22, "활성화 터미널." 단계에서 입력 시작</span><span class="sxs-lookup"><span data-stu-id="cdb0e-171">Start with saying the wake word you typed in step 22, "Activate Terminal."</span></span> <span data-ttu-id="cdb0e-172">그런 다음 음성 인식 시작 말하기를 시작 하는 마이크 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-172">Then, select the microphone button to start voice recognition and begin speaking.</span></span> <span data-ttu-id="cdb0e-173">당신은 말하면서 터미널에서 감정과 단어가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-173">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="cdb0e-174">음성 인식 하지 않도록 마이크 단추를 두 번 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-174">Press the microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="cdb0e-175">"해제 터미널" Lunarcom 터미널을 숨기려면 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-175">Say "Dismiss Terminal" to hide the Lunarcom terminal.</span></span> <span data-ttu-id="cdb0e-176">다음 단원에서는 Azure의 speech SDK HoloLens 2가 오프 라인으로 인해 사용할 수 없는 위치 하는 상황에 대 한 장치 기반 음성 인식을 사용 하 여 동적으로 전환 하는 방법을 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cdb0e-176">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition, for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="cdb0e-177">다음 단원: Speech SDK 단원 2</span><span class="sxs-lookup"><span data-stu-id="cdb0e-177">Next Lesson: Speech SDK Lesson 2</span></span>](mrlearning-speechSDK-ch2.md)

