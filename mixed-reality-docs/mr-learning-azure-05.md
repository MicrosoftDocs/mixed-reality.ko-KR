---
title: Azure 클라우드 자습서 - 5. LUIS와 Azure Bot Service 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 Azure Bot Service 및 자연어 이해를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, 자습서, HoloLens, HoloLens 2, Azure Bot Service, LUIS, 자연어, 대화 봇
ms.localizationpriority: high
ms.openlocfilehash: e3a64488b1d6d22ac52f798fe90356ce8e995e26
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306513"
---
# <a name="5-integrating-azure-bot-service"></a>5. Azure Bot Service 통합

이 자습서에서는 **HoloLens 2** 데모 애플리케이션에서 **Azure Bot Service**를 사용하여 LUIS(Language Understanding)를 추가하고 **추적된 개체**를 검색할 때 봇에서 사용자를 지원할 수 있도록 하는 방법에 대해 알아봅니다. 이 자습서는 2부로 구성되어 있습니다. 1부에서는 [봇 작성기](https://docs.microsoft.com/composer/introduction)를 코드프리 솔루션으로 사용하여 봇을 만들고, 필요한 데이터를 봇에 공급하는 Azure Function을 간략히 살펴봅니다. 2부에서는 Unity 프로젝트에서 **BotManager(스크립트)** 를 통해 호스팅된 Bot Service를 사용합니다.

## <a name="objectives"></a>목표

## <a name="part-1"></a>1부

* Azure Bot Service에 대한 기본 사항 알아보기
* 봇 작성기를 사용하여 봇을 만드는 방법 알아보기
* Azure Function을 사용하여 Azure Storage에서 데이터를 제공하는 방법 알아보기

## <a name="part-2"></a>2부

* 이 프로젝트에서 Azure Bot Service를 사용하도록 장면을 설정하는 방법 알아보기
* 봇과의 대화를 통해 개체를 설정하고 찾는 방법 알아보기

## <a name="understanding-azure-bot-service"></a>Azure Bot Service 이해

**Azure Bot Service**를 사용하면 개발자가 **LUIS**를 통해 사용자와 자연스러운 대화를 유지할 수 있는 인텔리전트 봇을 만들 수 있습니다. 대화형 봇은 사용자가 애플리케이션과 상호 작용할 수 있는 방법을 확장할 수 있는 좋은 방법입니다. 봇은 [LUIS(Language Understanding)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp) 기능과 정교한 대화를 유지하기 위해 [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs)와 함께 기술 자료 역할을 수행할 수 있습니다.

[Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0)에 대해 자세히 알아보세요.

## <a name="part-1---creating-the-bot"></a>1부 - 봇 만들기

Unity 애플리케이션에서 봇을 사용하려면 먼저 봇을 개발하여 데이터를 제공하고 **Azure**에서 호스팅해야 합니다.
봇의 목표는 데이터베이스에 저장된 *추적된 개체*의 수를 계산하고, 해당 이름을 기준으로 *추적된 개체*를 찾고, 사용자에게 이에 대한 몇 가지 기본 정보를 알려주는 기능을 제공하는 것입니다.

### <a name="a-quick-look-into-tracked-objects-azure-function"></a>추적된 개체 Azure Function 빠르게 살펴보기

봇 만들기를 시작하지만 유용하게 만들려면 데이터를 가져올 수 있는 리소스를 제공해야 합니다. *봇*에서 **추적된 개체**의 수를 계산하고 이름을 기준으로 특정 개체를 찾고 세부 정보를 알려줄 수 있으므로 **Azure Table 스토리지**에 액세스할 수 있는 간단한 Azure Function을 사용합니다.

Azure Function 프로젝트인 [추적된 개체 Azure Function](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)을 다운로드합니다.

이 Azure Function에는 기본 *HTTP* *GET* 호출을 통해 호출할 수 있는 **Count** 및 **Find**의 두 가지 작업이 있습니다. 코드는 **Visual Studio**에서 검사할 수 있습니다.

[Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)에 대해 자세히 알아보세요.

**Count** 함수는 **Table 스토리지**에서 테이블의 모든 **TrackedObjects**를 매우 간단하게 쿼리합니다. 반면 **Find** 함수는 *GET* 요청에서 *name* 쿼리 매개 변수를 사용하고, 일치하는 **TrackedObject**를 **Table 스토리지**에 쿼리하고, DTO를 JSON으로 반환합니다.

이 **Azure Function**은 **Visual Studio**에서 직접 배포할 수 있습니다.
[Azure Function 배포](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml)에서 모든 관련 정보를 확인하세요.

배포가 완료되면 **Azure Portal**에서 해당 리소스를 열고, *설정* 섹션 아래에서 **구성**을 클릭합니다. **애플리케이션 설정**에서 *연결 문자열*을 **추적된 개체**가 저장된 **Azure Storage**에 제공해야 합니다. **새 애플리케이션 설정**을 클릭하고, 이름에 대해 **AzureStorageConnectionString**을 사용하며, 값에 대해 올바른 *연결 문자열*을 제공합니다. 그런 다음, **저장**을 클릭합니다. 그러면 **Azure Function**이 나중에 만들 *봇*을 지원할 준비가 됩니다.

### <a name="creating-a-conversation-bot"></a>대화 봇 만들기

Bot Framework 기반 대화형 봇은 여러 가지 방법으로 개발할 수 있습니다. 이 단원에서는 빠른 개발을 위한 완벽한 비주얼 디자이너인 [Bot Framework 작성기](https://docs.microsoft.com/composer/) 데스크톱 애플리케이션을 사용합니다.

최신 릴리스는 [Github 리포지토리](https://github.com/microsoft/BotFramework-Composer/releases)에서 다운로드할 수 있습니다. Windows, Mac 및 Linux에서 사용할 수 있습니다.

**Bot Framework 작성기**가 설치되면 애플리케이션을 시작하여 다음 인터페이스가 표시됩니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-1.png)

이 자습서에 필요한 대화 상자 및 트리거를 제공하는 봇 작성기 프로젝트가 준비되었습니다.
프로젝트인 [Bot Framework 작성기 프로젝트](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)를 다운로드합니다.

위쪽 메뉴 모음에서 **열기**를 클릭하고, 다운로드한 **TrackedObjectsBot**이라는 Bot Framework 프로젝트를 선택합니다. 프로젝트가 완전히 로드되면 프로젝트가 준비된 것입니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-2.png)

**대화 상자 패널**을 볼 수 있는 왼쪽에 집중하겠습니다. **TrackedObjectsBot**이라는 하나의 대화 상자가 있으며, 그 아래에는 여러 개의 **트리거**가 표시되어 있습니다.

[Bot Framework 개념](https://docs.microsoft.com/composer/concept-dialog)에 대해 자세히 알아보세요.

이러한 트리거는 다음을 수행합니다.

#### <a name="greeting"></a>Greeting

*사용자*가 대화를 시작할 때 채팅 *봇*의 진입점입니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a>AskingForCount

이 대화 상자는 *사용자*가 모든 **추적된 개체**의 수를 계산하도록 요청할 때 트리거됩니다.
트리거 구는 다음과 같습니다.

>* count me all(모두 계산)
>* how many are stored(저장된 수)

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-4.png)

[LUIS](https://docs.microsoft.com/composer/how-to-use-luis)에서 지원하므로 *사용자*는 이러한 구를 *사용자*와 자연스럽게 대화할 수 있는 정확한 방법으로 요청할 필요가 없습니다.

이 대화 상자에서 *봇*은 **Count** Azure Function과도 통신하며, 나중에 이에 대해 자세히 설명합니다.

#### <a name="unknown-intent"></a>Unknown Intent(알 수 없음 의도)

*사용자*의 입력이 다른 트리거 조건에 맞지 않고 질문을 다시 시도하여 사용자에게 응답하는 경우 이 대화 상자가 트리거됩니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a>FindEntity

마지막 대화 상자는 *봇* 메모리에서 데이터를 분기하고 저장함으로써 더 복잡합니다.
사용자에게 **추적된 개체**의 *이름*을 요청하고, **Find** Azure Function에 대한 쿼리를 수행하고, 응답을 사용하여 대화를 진행합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-6.png)

**추적된 개체**가 없으면 사용자에게 이를 알리고 대화가 종료됩니다. 문제가 있는 **추적된 개체**가 있으면 부팅에서 사용 가능한 속성을 확인하고 이를 보고합니다.

### <a name="adapting-the-bot"></a>봇 적응

**AskingForCount** 및 **FindEntity** 트리거에서 백 엔드와 통신해야 합니다. 즉 이전에 배포한 **Azure Function**의 올바른 URL을 추가해야 합니다.

대화 상자 패널에서 **AskingForCount**를 클릭하고 *HTTP 요청 보내기* 작업을 찾습니다. 여기서는 **Count** 함수 엔드포인트에 대한 올바른 URL을 변경해야 하는 **URL** 필드를 확인할 수 있습니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-1.png)

마지막으로, **FindEntity** 트리거를 찾고 *HTTP 요청 보내기* 작업을 찾습니다. **URL** 필드에서 URL을 **Find** 함수 엔드포인트로 변경합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-2.png)

모든 설정이 완료되면 이제 봇을 배포할 준비가 되었습니다. Bot Framework 작성기가 설치되어 있으므로 여기서 직접 게시할 수 있습니다.

[봇 작성기에서 봇 게시](https://docs.microsoft.com/composer/how-to-publish-bot)에 대해 자세히 알아보세요.

> [!TIP]
> 더 많은 트리거 구, 새 응답 또는 대화 분기를 추가하여 봇을 자유롭게 재생해 보세요.

## <a name="part-2---putting-everything-together-in-unity"></a>2부 - Unity에 모든 항목 배치

### <a name="preparing-the-scene"></a>장면 준비

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** 폴더로 차례로 이동합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-1.png)

여기서 **ChatBotManager** 프리팹을 [계층 구조] 장면으로 이동합니다.

ChatBotManager가 장면에 추가되면 **채팅 봇 관리자** 구성 요소를 클릭합니다.
[검사기]에서 입력해야 하는 빈 **Direct Line 비밀 키** 필드가 표시됩니다.

> [!TIP]
> Azure Portal에서 이 자습서의 1부에서 만든 **봇 채널 등록** 형식의 리소스를 찾아서 *비밀 키*를 검색할 수 있습니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-2.png)

이제 **ChatBotManager** 개체를 **ChatBotPanel** 개체에 연결된 **ChatBotController** 구성 요소에 연결합니다. [계층 구조]에서 **ChatBotPanel**을 선택합니다. 그러면 빈 **채팅 봇 관리자** 필드가 표시됩니다. **ChatBotManager** 개체를 [계층 구조]에서 빈 **채팅 봇 관리자** 필드로 끕니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-3.png)

다음으로, 사용자가 상호 작용할 수 있도록 **ChatBotPanel**을 여는 방법이 필요합니다. [장면] 창에서 **MainMenu** 개체에 *채팅 봇* 사이드 단추가 있음을 알 수 있습니다. 이 단추는 이 문제를 해결하는 데 사용됩니다.

[계층 구조]에서 **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**을 차례로 찾고, [검사기]에서 *ButtonConfigHelper* 스크립트를 찾습니다. **OnClick()** 이벤트 콜백에 빈 슬롯이 표시됩니다. **ChatBotPanel**을 이벤트 슬롯으로 끌어서 놓고, 드롭다운 목록에서 *GameObject*를 탐색한 다음, 하위 메뉴에서 *SetActive(부울)* 를 선택하고, 확인란을 사용하도록 설정합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-4.png)

이제 주 메뉴에서 채팅 봇을 확인할 수 있으며, 해당 장면을 사용할 준비가 되었습니다.

### <a name="putting-the-bot-to-a-test"></a>테스트에 봇 배치

#### <a name="asking-about-the-quantity-of-tracked-objects"></a>추적된 개체 수 요청

먼저 데이터베이스에 저장된 **추적된 개체**의 수를 봇에 요청합니다.

> [!NOTE]
> *텍스트 음성 변환*과 같은 서비스를 사용하지 못할 수 있으므로 이번에는 HoloLens 2에서 애플리케이션을 실행해야 합니다.

HoloLens 2에서 애플리케이션을 실행하고, 주 메뉴 옆에 있는 *채팅 봇* 단추를 클릭합니다.
봇에서 인사말을 보내면 이제 **개체의 수가 얼마나 되나요?** 라고 요청합니다.
수량을 알려주고 대화가 종료됩니다.

#### <a name="asking-about-a-tracked-object"></a>추적된 개체 요청

이제 애플리케이션을 다시 실행하고, 이번에는 **추적된 개체 찾기**를 요청합니다. 그러면 봇에서 사용자에게 "car"로 응답해야 하는 이름 또는 데이터베이스에 있는 것으로 확인된 다른 *추적된 개체*의 이름을 요청합니다. 봇에서 설명 및 공간 앵커가 지정되어 있는지 여부와 같은 세부 정보를 알려줍니다.

> [!TIP]
> 존재하지 않는 **추적된 개체**를 요청하고 봇에서 응답하는 방법을 확인해 보세요.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure Bot Framework를 사용하여 자연어 대화를 통해 애플리케이션과 상호 작용하는 방법을 알아보았습니다. 사용자 고유의 봇을 개발하는 방법과 이를 실행할 수 있도록 하기 위해 이동한 모든 요소를 알아보았습니다.

## <a name="conclusion"></a>결론

이 자습서 시리즈의 과정을 통해 **Azure 클라우드 서비스**에서 새롭고 흥미로운 기능을 애플리케이션에 제공하는 방법을 경험했습니다.
이제 **Azure Storage**를 사용하여 데이터와 이미지를 클라우드에 저장하고, **Azure Custom Vision**을 사용하여 이미지를 연결하고 모델을 학습시키며, **Azure Spatial Anchors**를 사용하여 개체를 로컬 컨텍스트에 가져오고, **LUIS에서 구동하는 Azure Bot Framework**를 구현하여 새롭고 자연스러운 상호 작용 패턴에 적합한 대화형 봇을 추가할 수 있습니다.
