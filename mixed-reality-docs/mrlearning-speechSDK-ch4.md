## <a name="lesson-4"></a><span data-ttu-id="79fbd-101">4 단원</span><span class="sxs-lookup"><span data-stu-id="79fbd-101">Lesson 4</span></span>

<span data-ttu-id="79fbd-102">4 장에서 음성 서비스 내재 된 기능을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="79fbd-103">Azure LUIS 포털 설정, 우리의 의도/엔터티/길이 발언을 설치, 의도 리소스를 게시, Unity 앱 의도 리소스를 연결 하 고 첫 번째 의도 API 호출을 확인.</span><span class="sxs-lookup"><span data-stu-id="79fbd-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="79fbd-104">이 작업을 수행, Windows 설정으로 이동 하 고, "개인 정보 보호," 다음 "음성 변환," 마지막 "잉크 입력 및 입력"을 선택 하 고 음성 서비스 및 입력 제안을 설정에 받아쓰기를 사용 하도록 설정 하려면 컴퓨터를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="79fbd-108">참고: Mac/Macbook에서이 작업을 수행 하는 방법에 대 한 자세한 내용은 [여기](linkgoeshere)합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="79fbd-109">에 로그인 합니다 [Azure Portal](https://portal.azure.com/)합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="79fbd-110">일단 로그인 하면 리소스를 만들고 "언어 이해"에 대 한 검색 클릭 하 고 enter 키를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="79fbd-112">이 서비스의 인스턴스를 만들려고 하 고 만들기 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="79fbd-113">프로젝트 "Speech_SDK_Learning_Module" 이름과 "종 량 제."를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="79fbd-116">지역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-116">Select your Region.</span></span>  <span data-ttu-id="79fbd-117">이 자습서에서는 (미국) 미국 서 부 "."를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="79fbd-118">가격 책정 계층에 대 한 "F0"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="79fbd-119">이제 리소스를 만들려면 (왼쪽된 아래 모서리에 있음) "만들기"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="79fbd-120">참고: 클릭할 "만들기"를 만들려는 서비스에 대 한 대기 해야 면 몇 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="79fbd-121">리소스가 만들어지면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="79fbd-122">이 알림을 클릭 하 고 "리소스로 이동 합니다." 선택</span><span class="sxs-lookup"><span data-stu-id="79fbd-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="79fbd-123">"LUIS API" 서비스의 "빠른 시작" 페이지에서 첫 번째 단계로 이동한 "키를" 가져오기 "키" (이렇게 할 수 또한 파란색 하이퍼링크를 클릭 하 여 "키" 아래 그림과에서 같이)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="79fbd-124">서비스에 "키입니다." 표시 되며</span><span class="sxs-lookup"><span data-stu-id="79fbd-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="79fbd-125">앱에서 나중에 사용할 수 있도록 키 중 하나의 복사본을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="79fbd-127">섹션 2b 아래 "빠른 시작" 페이지에서 포털에서 클릭 "언어 이해" (위의 그림에 표시) LUIS 응용 프로그램 내에서 새 서비스를 만드는 데 사용할 수 있는 웹 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="79fbd-128">참고: "언어 이해 포털"에 도달 하면 없는 경우 이미 Azure portal로 동일한 자격 증명에 로그인 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="79fbd-129">LUIS를 사용 하 여 처음 이면를 찾고 앱 "LUIS 만들기" 단추를 클릭할 시작 페이지의 맨 아래로 스크롤하여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="79fbd-130">일단 로그인 하면 (없는 경우 해당 섹션에서 현재) 내 앱을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="79fbd-131">그런 다음 새 앱 만들기를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-131">You can then click on Create new app.</span></span> <span data-ttu-id="79fbd-132">새 앱 이름 지정 "Speech SDK 학습 모듈입니다."</span><span class="sxs-lookup"><span data-stu-id="79fbd-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="79fbd-133">설명 필드에 "Speech SDK 학습 모듈"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="79fbd-134">"완료"를 클릭</span><span class="sxs-lookup"><span data-stu-id="79fbd-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="79fbd-137">참고: 앱 영어가 아닌 언어를 이해할 수 할 경우 적절 한 언어 "Culture"으로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="79fbd-138">오른쪽 상단에 있는 "빌드"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="79fbd-139">왼쪽의 앱 자산에서 선택 "인 텐트" 다음 "새 의도 만들기"를 클릭 하 고 이름을 "PressButton."</span><span class="sxs-lookup"><span data-stu-id="79fbd-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="79fbd-141">참고: 이름별 의도 및 Lunarcom 앱 참조할 하 하기 때문에이 자습서에서 사용 하는 엔터티의 이름을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="79fbd-142">다른 프로젝트를 선택 하 든 간에 명명 규칙 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="79fbd-143">참고: 이제 2 의도-"PressButton" 및 "None"입니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="79fbd-144">왼쪽의 앱 자산에서 선택 "엔터티" 및 "새 엔터티 만들기"를 클릭 합니다. "Action" 라는 이름을 지정 하 고 "간단 합니다."으로 엔터티 형식을 유지합니다</span><span class="sxs-lookup"><span data-stu-id="79fbd-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="79fbd-146">"새 엔터티 만들기"를 다시 클릭 하 고 "대상" 이름을 "단순"으로 엔터티 형식에도 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="79fbd-148">"의도"를 선택 합니다. 왼쪽의 앱 자산에서 10 단계에서 만든 "PressButton" 의도에서 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="79fbd-150">보기 옵션"드롭다운 목록에서 오른쪽 클릭 하 고"엔터티 값을 보여 줍니다."선택</span><span class="sxs-lookup"><span data-stu-id="79fbd-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="79fbd-152">"입력 예제..." 클릭</span><span class="sxs-lookup"><span data-stu-id="79fbd-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="79fbd-153">텍스트 상자에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-153">textbox.</span></span> <span data-ttu-id="79fbd-154">그런 다음 다음 길이 발언을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="79fbd-156">보기 옵션"드롭다운 목록에서 오른쪽 클릭 하 고"엔터티 이름을 표시 합니다."선택</span><span class="sxs-lookup"><span data-stu-id="79fbd-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="79fbd-158">10의 각 되도록 길이 발언 1만 다음 엔터티 레이블 다음 위치에 있어야 합니다.) 태그로 되는 단어를 "레이블 제거" 및 2 선택 팝업에서 클릭 합니다.) 레이블을 지정 해야 하는 단어를 적절 한 레이블을 선택 팝업에서를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="79fbd-160">이제 모델을 게시 하려면 오른쪽 위에 있는 "학습"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="79fbd-161">그런 다음 처리를 마친 후 오른쪽 위에 있는 "테스트"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="79fbd-163">텍스트 상자에 "[시작] 단추 선택"을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="79fbd-164">참고:에서는 추가 하지 않은 "select" 동작으로 우리의 길이 발언-에서 하지만 "검사"를 클릭 하면 모델 "select"로 인식 작업 엔터티.</span><span class="sxs-lookup"><span data-stu-id="79fbd-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="79fbd-166">이제 오른쪽 위에 있는 "게시"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="79fbd-167">드롭다운에 "Production" 라는 확인 하 고 "게시"도 팝업에 클릭.</span><span class="sxs-lookup"><span data-stu-id="79fbd-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="79fbd-169">게시 한 후 페이지의 맨 위에 있는 녹색 막대가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="79fbd-170">녹색 막대 "Manage" 페이지로 이동 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="79fbd-172">왼쪽에 "" 응용 프로그램 설정 "에서" 키 및 끝점을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="79fbd-173">그런 다음 드롭다운 게시 하려면 ""프로덕션."로</span><span class="sxs-lookup"><span data-stu-id="79fbd-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="79fbd-174">일치 하지 않는, 표준 시간대를 설정 하 고 확인란을 선택 하는 모든 예측된 의도 점수가 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="79fbd-175">마지막으로, "할당 리소스입니다." 클릭</span><span class="sxs-lookup"><span data-stu-id="79fbd-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="79fbd-177">첫 번째 드롭다운 목록에서 테 넌 트를 선택 하 고 "종 량 제" 구독 이름 드롭다운 목록에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="79fbd-178">LUIS 리소스 이름에서 위의 1 ~ 5 단계에서 만든 리소스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="79fbd-179">그런 다음 "할당 리소스입니다." 클릭</span><span class="sxs-lookup"><span data-stu-id="79fbd-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="79fbd-181">참고: 복사 하 고만 할당 된 다음 섹션에 쉽게 액세스할 수 있도록 리소스와 연결 된 끝점 URL을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="79fbd-182">참고: 테 넌 트 이름에 대 한 프로그램 corporation 또는이 응용 프로그램에 대해 만든 프로필을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="79fbd-183">이제 Unity에서 새 앱을 열고 하 고 계층 구조에서 Lunarcom_Base 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="79fbd-184">검사기 창에서 "추가 구성 요소"를 클릭 합니다. 검색 하 고 "LunarcomIntentRecognizer."를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="79fbd-186">검사기 창에서 "LunarcomIntentRecognizer"의 Luis 끝점 필드에서 22 단계에서 저장 되는 끝점 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="79fbd-188">참고: 검사기 창에서 "LunarcomOfflineRecognizer" 구성 요소에는 "SimulateOfflineMode"이 고 그렇지에 대 한 "사용 안 함"을 선택, 테스트 프로그램은 작동 하지 않습니다 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="79fbd-189">Unity 편집기의 재생 단추를 눌러 한 의도 인식 시작 로켓 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="79fbd-190">"Rocket [시작] 단추를 선택 합니다." 라는 문구를 장모님</span><span class="sxs-lookup"><span data-stu-id="79fbd-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="79fbd-191">참고: 원하는 함수를 인식 하 고 rocket 단추를 활성화 하는 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="79fbd-193">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-193">Congratulations</span></span>

<span data-ttu-id="79fbd-194">공식적으로 음성 SDK는 프로그램에서 음성 명령을 추가 하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="79fbd-195">이제 프로그램이 모든 종류의 변형 음성 명령을 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fbd-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="79fbd-196">테스트 하 고 재미 있는 것!</span><span class="sxs-lookup"><span data-stu-id="79fbd-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="79fbd-197">다음 단원: Speech SDK 단원 5</span><span class="sxs-lookup"><span data-stu-id="79fbd-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)

