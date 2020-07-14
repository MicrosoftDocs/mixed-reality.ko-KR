---
title: Azure Speech Services 자습서 - 4. 의도 및 자연어 이해 설정
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Speech SDK를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 8cebe1fb203aeed9a262a2e9f482993b4775e0a6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303664"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="8cd7d-105">4. 의도 및 자연어 이해 설정</span><span class="sxs-lookup"><span data-stu-id="8cd7d-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="8cd7d-106">이 자습서에서는 Azure Speech Service의 의도 인식에 대해 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-106">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="8cd7d-107">의도 인식 기능을 사용하면 애플리케이션에서 AI 지원 음성 명령을 갖출 수 있습니다. 여기서는 사용자가 비특정 음성 명령을 말할 수 있으며, 시스템에서 해당 의도를 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-107">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="8cd7d-108">목표</span><span class="sxs-lookup"><span data-stu-id="8cd7d-108">Objectives</span></span>

* <span data-ttu-id="8cd7d-109">LUIS 포털에서 의도, 엔터티 및 발화를 설정하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-109">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="8cd7d-110">애플리케이션에서 의도와 자연어 이해를 구현하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-110">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="8cd7d-111">장면 준비</span><span class="sxs-lookup"><span data-stu-id="8cd7d-111">Preparing the scene</span></span>

<span data-ttu-id="8cd7d-112">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 의도 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-112">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="8cd7d-114">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** 폴더로 차례로 이동하고, **RocketLauncher_Complete** 프리팹을 [계층 구조] 창으로 끌어 카메라 앞의 적절한 위치에 배치합니다. 예를 들어 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="8cd7d-115">변환 **위치** X = 0, Y = -0.4, Z = 1</span><span class="sxs-lookup"><span data-stu-id="8cd7d-115">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="8cd7d-116">변환 **회전** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="8cd7d-116">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="8cd7d-118">[계층 구조] 창에서 **Lunarcom** 개체를 다시 선택한 다음, **RocketLauncher_Complete** > **Button** 개체를 차례로 펼치고, 각 **Buttons** 개체의 자식 개체를 해당 **Lunar 발사 시스템 단추** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-118">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="8cd7d-120">Azure Language Understanding 리소스 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-120">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="8cd7d-121">이 섹션에서는 다음 섹션에서 만들 LUIS(Language Understanding Intelligent Service) 앱에 대한 Azure 예측 리소스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-121">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="8cd7d-122"><a href="https://portal.azure.com" target="_blank">Azure</a>에 로그인하고, **리소스 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-122">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="8cd7d-123">그런 다음, **Language Understanding**을 검색하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-123">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="8cd7d-125">**만들기** 단추를 클릭하여 이 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-125">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="8cd7d-127">[만들기] 페이지에서 **예측** 옵션을 클릭하고 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-127">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="8cd7d-128">평가판 구독을 사용하는 경우 **구독**에 대해 **평가판**을 선택하고, 그렇지 않으면 다른 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-128">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="8cd7d-129">**리소스 그룹**에 대해 **새로 만들기** 링크를 클릭하고, 적절한 이름(예: *MRKT-Tutorials*)을 입력한 다음, **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-129">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click the **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="8cd7d-131">이 문서를 작성하는 시점부터 다음 섹션에서 LUIS(Language Understanding Intelligent Service)를 만들 때 LUIS 내에서 작성 평가판 키가 자동으로 생성되므로 작성 리소스를 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-131">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="8cd7d-132">다른 적합한 리소스 그룹이 Azure 계정에 이미 있는 경우(예: [Azure Spatial Anchors](mr-learning-asa-01.md) 자습서를 완료한 경우), 새 리소스 그룹을 만드는 대신 이 리소스 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-132">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mr-learning-asa-01.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="8cd7d-133">[만들기] 페이지에 있는 상태에서 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-133">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="8cd7d-134">**이름**에 대해 서비스에 적절한 이름을 입력합니다(예: *MRTK-Tutorial-AzureSpeechServices*).</span><span class="sxs-lookup"><span data-stu-id="8cd7d-134">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="8cd7d-135">**예측 위치**에 대해 앱 사용자의 실제 위치와 가까운 위치(예: *(미국) 미국 서부*)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-135">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="8cd7d-136">**예측 가격 책정 계층**에 대해 이 자습서에서는 **F0(초당 5개 호출, 월당 10,000개 호출)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-136">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="8cd7d-138">다음으로, **검토 + 만들기** 탭으로 이동하고, 세부 정보를 검토한 다음, 페이지 아래쪽에 있는 **만들기** 단추를 클릭하여 리소스 및 새 리소스 그룹(새로 만들도록 구성한 경우)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-138">Next, go to the **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="8cd7d-140">[만들기] 단추를 클릭하면 서비스가 만들어질 때까지 기다려야 하며, 이 경우 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-140">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="8cd7d-141">리소스 만들기 프로세스가 완료되면 **배포가 완료됨**이라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-141">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="8cd7d-143">LUIS(Language Understanding Intelligent Service) 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-143">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="8cd7d-144">이 섹션에서는 LUIS 앱을 만들고, 예측 모델을 구성 및 학습시키고, 이전 단계에서 만든 Azure 예측 리소스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-144">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="8cd7d-145">특히 사용자가 작업을 수행해야 한다고 말하면 앱에서 사용자가 참조하는 단추에 따라 장면의 빨간색 단추 세 개 중 하나에서 Interactable.OnClick() 이벤트를 트리거하는 의도를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-145">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="8cd7d-146">예를 들어 사용자가 **go ahead and launch the rocket(계속 진행하여 로켓 발사)** 이라고 말하면 앱에서 **go ahead**가 일부 **작업**을 수행해야 함을 의미하고 **대상**에 대한 Interactable.OnClick() 이벤트가 **launch** 단추에 있다고 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-146">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="8cd7d-147">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="8cd7d-148">LUIS 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-148">Create a LUIS app</span></span>
2. <span data-ttu-id="8cd7d-149">의도 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-149">Create intents</span></span>
3. <span data-ttu-id="8cd7d-150">발화 예제 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-150">Create example utterances</span></span>
4. <span data-ttu-id="8cd7d-151">엔터티 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-151">Create entities</span></span>
5. <span data-ttu-id="8cd7d-152">발화 예제에 엔터티 할당</span><span class="sxs-lookup"><span data-stu-id="8cd7d-152">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="8cd7d-153">앱 학습 테스트 및 게시</span><span class="sxs-lookup"><span data-stu-id="8cd7d-153">Train, test, and publish the app</span></span>
7. <span data-ttu-id="8cd7d-154">앱에 Azure 예측 리소스 할당</span><span class="sxs-lookup"><span data-stu-id="8cd7d-154">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="8cd7d-155">1. LUIS 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-155">1. Create a LUIS app</span></span>

<span data-ttu-id="8cd7d-156">이전 섹션에서 Azure 리소스를 만들 때 사용한 것과 동일한 사용자 계정을 사용하여 <a href="https://www.luis.ai" target="_blank">LUIS</a>에 로그인하고, 국가를 선택하고, 사용 약관에 동의합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-156">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="8cd7d-157">다음 단계에서 **Azure 계정을 연결**하라는 메시지가 표시되면 **평가판 키를 사용하여 계속**을 선택하여 Azure 작성 리소스를 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-157">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="8cd7d-158">LUIS에 이미 가입되어 있고 작성 평가판 키가 만료된 경우 [Azure 리소스 작성 키로 마이그레이션](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) 문서를 참조하여 LUIS 작성 리소스를 Azure로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-158">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="8cd7d-159">로그인하면 **내 앱** 페이지로 이동한 다음, **새 앱 만들기**를 클릭하고, **새 앱 만들기** 팝업 창에서 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-159">Once signed in, navigate to the **My apps** page, then click **Create new app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="8cd7d-160">**이름**에 대해 적절한 이름을 입력합니다(예: *MRTK Tutorials - AzureSpeechServices*).</span><span class="sxs-lookup"><span data-stu-id="8cd7d-160">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="8cd7d-161">**문화권**에 대해 **영어**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-161">For **Culture**, select **English**</span></span>
* <span data-ttu-id="8cd7d-162">**설명**에 대해 필요에 따라 적절한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-162">For **Description**, optionally enter a suitable description</span></span>

<span data-ttu-id="8cd7d-163">그런 다음, **완료** 단추를 클릭하여 새 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="8cd7d-165">새 앱이 만들어지면 해당 앱의 **대시보드** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="8cd7d-167">2. 의도 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-167">2. Create intents</span></span>

<span data-ttu-id="8cd7d-168">[대시보드] 페이지에서 빌드 > 앱 자산 > **의도** 페이지로 차례로 이동한 다음, **새 의도 만들기**를 클릭하고, **새 의도 만들기** 팝업 창에서 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create new intent** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="8cd7d-169">**의도 이름**에 대해 **PressButton**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="8cd7d-170">그런 다음, **완료** 단추를 클릭하여 새 의도를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="8cd7d-172">이 자습서에서는 Unity 프로젝트에서 이 의도를 'PressButton'이라는 이름으로 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="8cd7d-173">따라서 의도 이름을 똑같이 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="8cd7d-174">새 의도가 만들어지면 해당 의도의 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="8cd7d-176">3. 발화 예제 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-176">3. Create example utterances</span></span>

<span data-ttu-id="8cd7d-177">다음 발화 예제를 **PressButton** 의도의 **발화 예제** 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="8cd7d-178">activate launch sequence</span><span class="sxs-lookup"><span data-stu-id="8cd7d-178">activate launch sequence</span></span>
* <span data-ttu-id="8cd7d-179">show me a placement hint</span><span class="sxs-lookup"><span data-stu-id="8cd7d-179">show me a placement hint</span></span>
* <span data-ttu-id="8cd7d-180">initiate the launch sequence</span><span class="sxs-lookup"><span data-stu-id="8cd7d-180">initiate the launch sequence</span></span>
* <span data-ttu-id="8cd7d-181">press placement hints button</span><span class="sxs-lookup"><span data-stu-id="8cd7d-181">press placement hints button</span></span>
* <span data-ttu-id="8cd7d-182">give me a hint</span><span class="sxs-lookup"><span data-stu-id="8cd7d-182">give me a hint</span></span>
* <span data-ttu-id="8cd7d-183">push the launch button</span><span class="sxs-lookup"><span data-stu-id="8cd7d-183">push the launch button</span></span>
* <span data-ttu-id="8cd7d-184">i need a hint</span><span class="sxs-lookup"><span data-stu-id="8cd7d-184">i need a hint</span></span>
* <span data-ttu-id="8cd7d-185">press the reset button</span><span class="sxs-lookup"><span data-stu-id="8cd7d-185">press the reset button</span></span>
* <span data-ttu-id="8cd7d-186">time to reset the experience</span><span class="sxs-lookup"><span data-stu-id="8cd7d-186">time to reset the experience</span></span>
* <span data-ttu-id="8cd7d-187">go ahead and launch the rocket</span><span class="sxs-lookup"><span data-stu-id="8cd7d-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="8cd7d-188">모든 발화 예제가 추가되면 PressButton의 의도 페이지가 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="8cd7d-190">이 자습서에서는 Unity 프로젝트에서 'hint', 'hints', 'reset', 'launch'라는 단어를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="8cd7d-191">따라서 이러한 단어의 철자를 똑같이 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="8cd7d-192">4. 엔터티 만들기</span><span class="sxs-lookup"><span data-stu-id="8cd7d-192">4. Create entities</span></span>

<span data-ttu-id="8cd7d-193">PressButton 의도 페이지에서 빌드 > 앱 자산 > **엔터티** 페이지로 차례로 이동한 다음, **새 엔터티 만들기**를 클릭하고, **새 엔터티 만들기** 팝업 창에서 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create new entity** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="8cd7d-194">**엔터티 이름**에 대해 **Action**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="8cd7d-195">**엔터티 형식**에 대해 **단순**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-195">For **Entity type**, select **Simple**</span></span>

<span data-ttu-id="8cd7d-196">그런 다음, **완료** 단추를 클릭하여 새 엔터티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-196">Then click the **Done** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="8cd7d-198">이전 단계를 **반복**하여 **Target**이라는 다른 엔터티를 만듭니다. 이제 Action 및 Target이라는 두 엔터티가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="8cd7d-200">이 자습서에서는 Unity 프로젝트에서 이러한 엔터티를 'Action' 및 'Target'이라는 이름으로 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="8cd7d-201">따라서 엔터티 이름을 똑같이 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="8cd7d-202">5. 발화 예제에 엔터티 할당</span><span class="sxs-lookup"><span data-stu-id="8cd7d-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="8cd7d-203">[엔터티] 페이지에서 **PressButton** 의도 페이지로 다시 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="8cd7d-204">PressButton 의도 페이지로 돌아가면 **go**, **ahead** 단어를 차례로 클릭한 다음, 상황별 팝업 메뉴에서 **Action(단순)** 을 선택하여 **go ahead**에 대한 레이블을 **Action** 엔터티 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="8cd7d-206">**go ahead** 구가 이제 **Action** 엔터티 값으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="8cd7d-207">마우스 커서로 Action 엔터티 이름 위를 가리키면 연결된 Action 엔터티 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-207">If you hover your mouse cursor above the Action entity name, you can see the associated Action entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="8cd7d-209">위의 이미지에서 레이블 아래에 표시된 빨간색 선은 엔터티 값이 예측되지 않았음을 나타냅니다. 이는 다음 섹션에서 모델을 학습시킬 때 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="8cd7d-210">다음으로, **launch** 단어를 클릭한 다음, 상황별 팝업 메뉴에서 **Target(단순)** 을 선택하여 **launch**에 대한 레이블을 **Target** 엔터티 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="8cd7d-212">이제 **launch** 단어가 **Target** 엔터티 값으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-212">The **launch** word is now defined as a **Target** entity value.</span></span> <span data-ttu-id="8cd7d-213">마우스 커서로 Target 엔터티 이름 위를 가리키면 연결된 Target 엔터티 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-213">If you hover your mouse cursor above the Target entity name, you can see the associated Target entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="8cd7d-215">이제 PressButton 의도 발화 예제인 'go ahead and launch the rocket'은 다음과 같이 예측되도록 구성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-215">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="8cd7d-216">의도: PressButton</span><span class="sxs-lookup"><span data-stu-id="8cd7d-216">Intent: PressButton</span></span>
* <span data-ttu-id="8cd7d-217">Action 엔터티: go ahead</span><span class="sxs-lookup"><span data-stu-id="8cd7d-217">Action entity: go ahead</span></span>
* <span data-ttu-id="8cd7d-218">Target 엔터티: launch</span><span class="sxs-lookup"><span data-stu-id="8cd7d-218">Target entity: launch</span></span>

<span data-ttu-id="8cd7d-219">이전 2단계 프로세스를 **반복**하여 Action 및 Target 엔터티 레이블을 각 발화 예제에 할당합니다. 다음 단어에 대한 레이블을 **Target** 엔터티로 지정해야 한다는 점에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-219">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="8cd7d-220">**hint**(Unity 프로젝트에서 HintsButton을 대상으로 함)</span><span class="sxs-lookup"><span data-stu-id="8cd7d-220">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="8cd7d-221">**hints**(Unity 프로젝트에서 HintsButton을 대상으로 함)</span><span class="sxs-lookup"><span data-stu-id="8cd7d-221">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="8cd7d-222">**reset**(Unity 프로젝트에서 ResetButton을 대상으로 함)</span><span class="sxs-lookup"><span data-stu-id="8cd7d-222">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="8cd7d-223">**launch**(Unity 프로젝트에서 LaunchButton을 대상으로 함)</span><span class="sxs-lookup"><span data-stu-id="8cd7d-223">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="8cd7d-224">레이블이 모든 발화 예제에 지정되면 PressButton의 의도 페이지가 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-224">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

<span data-ttu-id="8cd7d-226">다른 방법으로 올바른 엔터티를 할당했는지 다시 확인하려면 **보기 옵션** 메뉴를 클릭하고 보기를 **엔터티 값 표시**로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-226">For an alternative way to double-check that you have assigned the correct entities, click the **View options** menu and switch the view to **Show entity values**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

<span data-ttu-id="8cd7d-228">이제 보기가 엔터티 값을 표시하도록 설정된 상태에서 마우스 커서로 레이블이 지정된 단어와 구 위를 가리키면 할당된 엔터티 이름을 빠르게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-228">Now, with the view set to show entity values, you can hover the mouse courser over the labeled words and phrases to quickly verify the assigned entity name:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="8cd7d-230">6. 앱 학습 테스트 및 게시</span><span class="sxs-lookup"><span data-stu-id="8cd7d-230">6. Train, test, and publish the app</span></span>

<span data-ttu-id="8cd7d-231">앱을 학습시키려면 **학습** 단추를 클릭하고 학습 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-231">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="8cd7d-233">위의 이미지에서 볼 수 있듯이 모든 레이블 아래의 빨간색 선이 제거되어 모든 엔터티 값이 예측되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-233">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="8cd7d-234">또한 [학습] 단추 왼쪽에 있는 상태 아이콘이 빨간색에서 녹색으로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-234">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="8cd7d-235">학습 프로세스가 완료되면 **테스트** 단추를 클릭한 다음, **go ahead and launch the rocket**을 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-235">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="8cd7d-237">테스트 발화가 처리되면 **검사**를 클릭하여 테스트 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-237">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="8cd7d-238">의도: PressButton(98.5% 확신도)</span><span class="sxs-lookup"><span data-stu-id="8cd7d-238">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="8cd7d-239">Action 엔터티: go ahead</span><span class="sxs-lookup"><span data-stu-id="8cd7d-239">Action entity: go ahead</span></span>
* <span data-ttu-id="8cd7d-240">Target 엔터티: launch</span><span class="sxs-lookup"><span data-stu-id="8cd7d-240">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="8cd7d-242">앱을 게시하려면 오른쪽 위에서 **게시** 단추를 클릭한 다음, **게시 슬롯 및 설정 선택** 팝업 창에서 **프로덕션**을 선택하고 **게시** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-242">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Publish** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="8cd7d-244">게시 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-244">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a><span data-ttu-id="8cd7d-246">7. 앱에 Azure 예측 리소스 할당</span><span class="sxs-lookup"><span data-stu-id="8cd7d-246">7. Assign an Azure prediction resource to the app</span></span>

<span data-ttu-id="8cd7d-247">관리 > 애플리케이션 설정 > **Azure 리소스** 페이지로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-247">Navigate to the Manage > Application Settings > **Azure Resources** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

<span data-ttu-id="8cd7d-249">[Azure 리소스] 페이지에서 **예측 리소스 추가** 단추를 클릭하고, **앱에 리소스 할당** 팝업 창에서 다음 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-249">On the Azure Resources page, click the **Add prediction resource** button and select the following values in the **Assign a resource to your app** popup window:</span></span>

* <span data-ttu-id="8cd7d-250">**테넌트 이름**에 대해 사용자의 테넌트 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-250">For **Tenant name**, select your tenant name</span></span>
* <span data-ttu-id="8cd7d-251">**구독 이름**에 대해 이전에 [Azure Language Understanding 리소스 만들기](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)에서 사용한 것과 동일한 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-251">For **Subscription Name**, select the same subscription you used earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>
* <span data-ttu-id="8cd7d-252">**LUIS 리소스 이름**에 대해 이전에 [Azure Language Understanding 리소스 만들기](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)에서 만든 예측 리소스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-252">For **LUIS resource name**, select the prediction resource you created earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>

<span data-ttu-id="8cd7d-253">그런 다음, **리소스 할당** 단추를 클릭하여 Azure 예측 리소스를 앱에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-253">Then click the **Assign resource** button to assign the Azure prediction resource to your app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

<span data-ttu-id="8cd7d-255">리소스가 할당되면 [Azure 리소스] 페이지가 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-255">When the resource has been assigned, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="8cd7d-257">Unity 프로젝트를 LUIS 앱에 연결</span><span class="sxs-lookup"><span data-stu-id="8cd7d-257">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="8cd7d-258">관리 > 애플리케이션 설정 > **Azure 리소스** 페이지에서 **복사** 아이콘을 클릭하여 **쿼리 예제**를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-258">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="8cd7d-260">Unity 프로젝트로 돌아가서 [계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **Lunarcom 의도 인식기(스크립트)** 구성 요소를 찾아서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-260">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="8cd7d-261">**LUIS 엔드포인트** 필드에서 이전 단계에서 복사한 **쿼리 예제**를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-261">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="8cd7d-263">의도 인식 테스트 및 향상</span><span class="sxs-lookup"><span data-stu-id="8cd7d-263">Testing and improving the intent recognition</span></span>

<span data-ttu-id="8cd7d-264">Unity 편집기에서 의도 인식을 직접 사용하려면 개발 컴퓨터에서 받아쓰기를 사용하도록 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-264">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="8cd7d-265">이 설정을 확인하려면 Windows **설정**을 연 다음, **개인 정보** > **음성**을 차례로 선택하고, **온라인 음성 인식**이 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-265">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="8cd7d-267">이제 게임 모드로 들어가면 먼저 로켓 단추를 눌러 의도 인식을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-267">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="8cd7d-268">그런 다음, 컴퓨터에 마이크가 있다고 가정하여 첫 번째 발화 예제인 **go ahead and launch the rocket**이라고 말하면 LunarModule이 우주로 발사되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-268">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="8cd7d-270">모든 **발화 예제**를 시도한 다음, **발화 예제의 일부 변형**뿐만 아니라 몇 가지 **임의 발화**도 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-270">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="8cd7d-271">다음으로, <a href="https://www.luis.ai" target="_blank">LUIS</a>로 돌아가서 빌드 > 앱 성능 향상 >  **엔드포인트 발화 검토** 페이지로 차례로 이동하고, **토글** 단추를 사용하여 기본 엔터티 보기에서 **토큰 보기**로 전환한 다음, 발화를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-271">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="8cd7d-272">**발화** 열에서 필요에 따라 할당된 레이블을 변경하고 제거하여 의도에 맞게 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-272">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="8cd7d-273">**맞춤 의도** 열에서 의도가 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-273">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="8cd7d-274">**추가/삭제** 열에서 녹색 확인 표시 단추를 클릭하여 발화를 추가하거나, 빨간색 x 단추를 클릭하여 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-274">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="8cd7d-275">발화를 원하는 만큼 검토한 경우 **학습** 단추를 클릭하여 모델을 다시 학습시킨 다음, **게시** 단추를 클릭하여 업데이트된 앱을 다시 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-275">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="8cd7d-277">엔드포인트 발화는 PressButton 의도에 맞추지 않지만, 해당 발화에 의도가 없음을 모델에 알리려면 맞춤 의도를 [없음]으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-277">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="8cd7d-278">앱 모델을 향상시키려면 이 프로세스를 원하는 횟수만큼 **반복**합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-278">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8cd7d-279">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-279">Congratulations</span></span>

<span data-ttu-id="8cd7d-280">이제 프로젝트에는 AI 지원 음성 명령이 있으므로 애플리케이션에서 정확한 명령을 발화하지 않더라도 사용자의 의도를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-280">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="8cd7d-281">디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd7d-281">Run the application on your device to ensure the feature is working properly.</span></span>
