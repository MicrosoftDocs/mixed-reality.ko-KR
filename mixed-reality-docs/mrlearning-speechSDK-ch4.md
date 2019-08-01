---
title: Azure Speech Services 자습서-4. 의도 및 자연어 이해 설정
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 5ca2df56eee3ae41d97de4e8b1e88a39d4d36718
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701945"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="34ba3-105">4. 의도 및 자연어 이해 설정</span><span class="sxs-lookup"><span data-stu-id="34ba3-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="34ba3-106">이 단원에서는 Azure Speech Service의 의도 기능을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="34ba3-107">의도 기능을 사용 하면 사용자가 특정 음성 명령을 사용 하지 않아도 되 고 시스템에서 해당 의도를 인식할 수 있는 AI 지원 음성 명령으로 응용 프로그램을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="34ba3-108">이 단원에서는 Azure LUIS 포털을 설정 하 고, 의도/엔터티/길이 발언를 설정 하 고, 의도 리소스를 게시 하 고, Unity 앱을 의도 리소스에 연결 하 고, 첫 번째 의도 API 호출을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="34ba3-109">목표</span><span class="sxs-lookup"><span data-stu-id="34ba3-109">Objectives</span></span>

- <span data-ttu-id="34ba3-110">응용 프로그램에서 의도 및 자연어 이해를 설정 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="34ba3-111">Azure의 LUIS 포털을 설정 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="34ba3-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="34ba3-112">Azure에서 의도, 엔터티 및 길이 발언를 설정 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="34ba3-113">지침</span><span class="sxs-lookup"><span data-stu-id="34ba3-113">Instructions</span></span>
1. <span data-ttu-id="34ba3-114">컴퓨터에서 받아쓰기를 사용 하도록 허용 합니다. 이렇게 하려면 Windows 설정으로 이동 하 여 "개인 정보"를 선택 하 고 "speech"를 선택한 다음 "& 음성"을 선택 하 여 음성 서비스를 켜고 제안 사항을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="34ba3-118">[Azure Portal](https://portal.azure.com/)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="34ba3-119">로그인 하면 리소스 만들기를 클릭 하 고 "Language Understanding"를 검색 한 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="34ba3-121">만들기 단추를 선택 하 여이 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-121">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="34ba3-122">프로젝트 이름을 "Speech_SDK_Learning_Module"로 표시 하 고 "종 량 제"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-122">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="34ba3-125">지역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-125">Select your Region.</span></span>  <span data-ttu-id="34ba3-126">이 자습서에서는 "미국 서 부"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-126">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="34ba3-127">그런 다음 가격 책정 계층에 대해 "F0"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-127">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="34ba3-128">이제 "만들기" (왼쪽 아래 모서리에 있음)를 클릭 하 여 리소스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-128">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="34ba3-129">참고: "만들기"를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업은 1 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-129">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="34ba3-130">리소스가 만들어지면 포털에 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-130">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="34ba3-131">이 알림을 클릭 하 고 "리소스로 이동"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-131">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="34ba3-132">"LUIS API" 서비스의 "빠른 시작" 페이지에서 첫 번째 단계로 이동 하 고 "키"를 선택한 다음 "키"를 클릭 합니다 (아래 이미지에 표시 된 파란색 하이퍼링크 "키"를 클릭 하 여이를 수행할 수도 있음).</span><span class="sxs-lookup"><span data-stu-id="34ba3-132">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="34ba3-133">그러면 "키" 서비스가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-133">This will reveal your service, "Keys."</span></span> <span data-ttu-id="34ba3-134">앱에서 나중에 사용할 수 있도록 키 중 하나의 복사본을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-134">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="34ba3-136">섹션 2b의 "빠른 시작" 페이지로 돌아가서 LUIS 응용 프로그램 내에서 새 서비스를 만드는 데 사용할 웹 페이지로 리디렉션되는 "Language Understanding Portal" (위의 그림에 표시 됨)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-136">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="34ba3-137">참고: "Language Understanding 포털"에 도달 하면 Azure Portal와 동일한 자격 증명을 사용 하 여 로그인 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-137">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="34ba3-138">LUIS를 처음 사용 하는 경우 시작 페이지의 아래쪽으로 스크롤하여 "LUIS 만들기" 앱 단추를 찾아 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-138">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="34ba3-139">로그인 한 후 내 앱 (현재 해당 섹션에 있지 않은 경우)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-139">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="34ba3-140">그런 다음 새 앱 만들기를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-140">You can then click on Create new app.</span></span> <span data-ttu-id="34ba3-141">새 앱의 이름을 "Speech SDK Learning Module"으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-141">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="34ba3-142">설명 필드에 "Speech SDK Learning Module"을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-142">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="34ba3-143">그런 다음 "완료"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-143">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="34ba3-146">두고 앱이 영어와 다른 언어를 파악 해야 하는 경우 "Culture"를 적절 한 언어로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-146">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="34ba3-147">오른쪽 위에 있는 "빌드"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-147">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="34ba3-148">왼쪽의 앱 자산에서 "의도"를 선택한 다음 "새 의도 만들기"를 클릭 하 고 이름을 "보도 ..."로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-148">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="34ba3-150">참고: Lunarcom 앱이 이름으로 참조 하기 때문에이 자습서에 사용 된 의도 및 엔터티 이름을 사용 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-150">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="34ba3-151">참고: 이제 "보도" 및 "None"의 두 가지 의도를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-151">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="34ba3-152">왼쪽의 앱 자산에서 "엔터티"를 선택 하 고 "새 엔터티 만들기"를 클릭 하 고 "Action"으로 이름을로 설정 하 고 엔터티 형식을 "Simple"로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-152">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="34ba3-154">"새 엔터티 만들기"를 다시 클릭 하 고 이름을 "대상"으로 한 다음 엔터티 형식을 "Simple"로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-154">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="34ba3-156">왼쪽의 앱 자산에서 "의도"를 선택 하 고 10 단계에서 만든 "보도" 의도를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="34ba3-158">오른쪽에 있는 "보기 옵션" 드롭다운을 클릭 하 고 "엔터티 값 표시"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-158">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="34ba3-160">"예제 입력 ..."을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-160">Click on the “Enter an example…”</span></span> <span data-ttu-id="34ba3-161">상자로.</span><span class="sxs-lookup"><span data-stu-id="34ba3-161">textbox.</span></span> <span data-ttu-id="34ba3-162">그런 다음 길이 발언을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-162">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="34ba3-164">오른쪽의 "보기 옵션" 드롭다운을 클릭 하 고 "엔터티 이름 표시"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-164">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="34ba3-166">각각의 10 길이 발언는 다음 위치에 1이 있는 엔터티 레이블을 포함 해야 합니다. 자주 단어를 클릭 하 고 팝업에서 "레이블 제거" 및 2를 선택 합니다. 레이블을 지정 해야 하는 단어를 클릭 하 고 팝업에서 적절 한 레이블을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="34ba3-168">이제 모델을 게시 하려면 오른쪽 위에 있는 "학습"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="34ba3-169">그런 다음 처리가 완료 되 면 오른쪽 위에 있는 "테스트"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="34ba3-171">텍스트 상자에 "시작 단추를 선택 하십시오."를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-171">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="34ba3-172">참고: 길이 발언에서 작업으로 "선택"을 추가 하지 않았지만 "검사"를 클릭 하면 모델은 동작 엔터티로 "select"를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-172">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="34ba3-174">이제 오른쪽 위에 있는 "게시"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-174">Now, click "publish" in the top right.</span></span> <span data-ttu-id="34ba3-175">드롭다운에 "Production"가 표시 되는지 확인 하 고 팝업 에서도 "게시"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-175">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="34ba3-177">게시 된 후에는 페이지 맨 위에 녹색 막대가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-177">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="34ba3-178">녹색 막대를 클릭 하 여 "관리" 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-178">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="34ba3-180">왼쪽에 있는 "응용 프로그램 설정"의 "키 및 끝점"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-180">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="34ba3-181">그런 다음 "게시"를 "프로덕션"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="34ba3-182">자신의 이름과 일치 하도록 표준 시간대를 설정 하 고 상자를 선택 하 여 예측 된 의도 점수를 모두 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="34ba3-183">마지막으로 "리소스 할당"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-183">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="34ba3-185">첫 번째 드롭다운에서 테 넌 트를 선택 하 고 구독 이름 드롭다운에서 "종 량 제"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-185">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="34ba3-186">LUIS 리소스 이름 아래에서 1-5 단계에서 앞서 만든 리소스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="34ba3-187">그런 다음 "리소스 할당"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-187">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="34ba3-189">참고: 다음 섹션에서 쉽게 액세스할 수 있도록 방금 할당 한 리소스와 연결 된 끝점 URL을 복사 하 여 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-189">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="34ba3-190">참고: 테 넌 트 이름에 대해이 응용 프로그램에 대해 만든 회사 또는 프로필을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-190">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="34ba3-191">이제 Unity에서 새 앱을 열고 계층 구조에서 Lunarcom_Base 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="34ba3-192">검사기 패널에서 "구성 요소 추가"를 클릭 하 고 "LunarcomIntentRecognizer"를 검색 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="34ba3-194">검사기 패널에서 "LunarcomIntentRecognizer"의 Luis 끝점 필드에 22 단계에서 저장 한 끝점 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="34ba3-196">참고: 검사기 패널의 "LunarcomOfflineRecognizer" 구성 요소에서 "SimulateOfflineMode"에 대해 "사용 안 함"이 선택 되어 있는지 확인 합니다. 그렇지 않으면 프로그램 테스트가 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-196">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="34ba3-197">Unity 편집기에서 재생 단추를 누르고 로켓 단추를 클릭 하 여 의도 인식을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-197">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="34ba3-198">"로켓 시작 단추를 선택 하십시오." 라는 구를 Utter.</span><span class="sxs-lookup"><span data-stu-id="34ba3-198">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="34ba3-199">참고: 앱에서 원하는 함수를 인식 하 고 로켓 단추를 활성화 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-199">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="34ba3-201">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-201">Congratulations</span></span>

<span data-ttu-id="34ba3-202">이 단원에서는 AI 지원 음성 명령을 추가 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-202">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="34ba3-203">이제 프로그램에서 정확한 음성 명령을 utter 하지 않아도 사용자의 의도를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34ba3-203">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

