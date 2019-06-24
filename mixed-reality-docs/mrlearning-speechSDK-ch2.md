## <a name="lesson-2"></a><span data-ttu-id="0c5d7-101">2 단원</span><span class="sxs-lookup"><span data-stu-id="0c5d7-101">Lesson 2</span></span>

<span data-ttu-id="0c5d7-102">단원 2에서는 Azure 서비스에 연결할 수 없는 경우는 로컬 음성-텍스트 번역을 수행할 수 있도록 하는 오프 라인 모드를 추가할 예정 *시뮬레이션* 연결이 끊어진된 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-102">In Lesson 2, we will add an Offline mode that will allow us to perform local speech-to-text translation when we are unable to connect to the Azure service and we will *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="0c5d7-103">계층 구조에서 "Lunarcom_Base" 개체를 선택 하 고 검사기 패널에서 "추가 구성 요소"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-103">Select the "Lunarcom_Base" object in the hierarchy and click “Add Component” in the inspector panel.</span></span> <span data-ttu-id="0c5d7-104">검색 하 고 "Lunarcom 오프 라인 인식"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-104">Search for and select the "Lunarcom Offline Recognition."</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. <span data-ttu-id="0c5d7-106">"LunarcomOfflineRecognizer"에서 드롭다운을 클릭 하 고 "사용"을 선택 합니다.를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-106">Click the dropdown in the “LunarcomOfflineRecognizer” and select “Enabled.”</span></span> <span data-ttu-id="0c5d7-107">이 연결 되지 않은 사용자 처럼 동작 프로젝트를 프로그램 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-107">This will program the project to act like the user doesn't have connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="0c5d7-109">이제 키를 눌러 Unity 편집기에서 재생 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-109">Now, press play on the Unity Editor and test it.</span></span> <span data-ttu-id="0c5d7-110">장면에서 왼쪽 아래에서 마이크를 누르고 말하기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-110">Press the microphone in the bottom left hand corner in the scene and begin speaking.</span></span> 

> <span data-ttu-id="0c5d7-111">참고: 비활성화 된 단어 절전 모드 해제 기능을 오프 라인 했으므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-111">note: because we’re offline, the Wake Word functionality has been disabled.</span></span> <span data-ttu-id="0c5d7-112">음성 인식 하 게 하려면 때마다 마이크를 물리적으로 클릭 해야 하는, 하는 동안 오프 라인입니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-112">So, you will have to physically click the microphone every time you wish to have your speech recognized while offline.</span></span> 

<span data-ttu-id="0c5d7-113">다음은 장면 다음과 같을 수 있습니다의 예:</span><span class="sxs-lookup"><span data-stu-id="0c5d7-113">Below is an example of what your scene could look like:</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="0c5d7-115">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="0c5d7-115">Congratulations</span></span>

<span data-ttu-id="0c5d7-116">오프 라인 모드를 사용 하도록 설정한 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="0c5d7-116">The offline mode has been enabled!</span></span> <span data-ttu-id="0c5d7-117">이제 면 인터넷의 모든 형태에서 계속 작업할 수 있습니다 Speech SDK를 사용 하 여 프로젝트!</span><span class="sxs-lookup"><span data-stu-id="0c5d7-117">Now when you're away from any form of internet, you can still work on your project with Speech-SDK!</span></span> 

[<span data-ttu-id="0c5d7-118">다음 단원: SpeechSDK 단원 3</span><span class="sxs-lookup"><span data-stu-id="0c5d7-118">Next Lesson: SpeechSDK Lesson 3</span></span>](link placeholder)

