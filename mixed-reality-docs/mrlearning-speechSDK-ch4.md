---
title: Azure Speech Services 자습서 - 4. 의도 및 자연어 이해 설정
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Speech SDK를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: b2342e7d0d502af2787ca311d18a44f8726acf2d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028552"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. 의도 및 자연어 이해 설정

이 자습서에서는 Azure Speech Service의 의도 인식에 대해 살펴봅니다. 의도 인식 기능을 사용하면 애플리케이션에서 AI 지원 음성 명령을 갖출 수 있습니다. 여기서는 사용자가 비특정 음성 명령을 말할 수 있으며, 시스템에서 해당 의도를 이해할 수 있습니다.

## <a name="objectives"></a>목표

* LUIS 포털에서 의도, 엔터티 및 발화를 설정하는 방법 알아보기
* 애플리케이션에서 의도와 자연어 이해를 구현하는 방법 알아보기

## <a name="preparing-the-scene"></a>장면 준비

[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 의도 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** 폴더로 차례로 이동하고, **RocketLauncher_Complete** 프리팹을 [계층 구조] 창으로 끌어 카메라 앞의 적절한 위치에 배치합니다. 예를 들어 다음과 같습니다.

* 변환 **위치** X = 0, Y = -0.4, Z = 1
* 변환 **회전** X = 0, Y = 90, Z = 0

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

[계층 구조] 창에서 **Lunarcom** 개체를 다시 선택한 다음, **RocketLauncher_Complete** > **Button** 개체를 차례로 펼치고, 각 **Buttons** 개체의 자식 개체를 해당 **Lunar 발사 시스템 단추** 필드에 할당합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>Azure Language Understanding 리소스 만들기

이 섹션에서는 다음 섹션에서 만들 LUIS(Language Understanding Intelligent Service) 앱에 대한 Azure 예측 리소스를 만듭니다.

<a href="https://portal.azure.com" target="_blank">Azure</a>에 로그인하고, **리소스 만들기**를 클릭합니다. 그런 다음, **Language Understanding**을 검색하여 선택합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

**만들기** 단추를 클릭하여 이 서비스의 인스턴스를 만듭니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

[만들기] 페이지에서 **예측** 옵션을 클릭하고 다음 값을 입력합니다.

* 평가판 구독을 사용하는 경우 **구독**에 대해 **평가판**을 선택하고, 그렇지 않으면 다른 구독을 선택합니다.
* **리소스 그룹**에 대해 **새로 만들기** 링크를 클릭하고, 적절한 이름(예: *MRKT-Tutorials*)을 입력한 다음, **확인**을 클릭합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> 이 문서를 작성하는 시점부터 다음 섹션에서 LUIS(Language Understanding Intelligent Service)를 만들 때 LUIS 내에서 작성 평가판 키가 자동으로 생성되므로 작성 리소스를 만들 필요가 없습니다.

> [!TIP]
> 다른 적합한 리소스 그룹이 Azure 계정에 이미 있는 경우(예: [Azure Spatial Anchors](mrlearning-asa-ch1.md) 자습서를 완료한 경우), 새 리소스 그룹을 만드는 대신 이 리소스 그룹을 사용할 수 있습니다.

[만들기] 페이지에 있는 상태에서 다음 값을 입력합니다.

* **이름**에 대해 서비스에 적절한 이름을 입력합니다(예: *MRTK-Tutorial-AzureSpeechServices*).
* **예측 위치**에 대해 앱 사용자의 실제 위치와 가까운 위치(예: *(미국) 미국 서부*)를 선택합니다.
* **예측 가격 책정 계층**에 대해 이 자습서에서는 **F0(초당 5개 호출, 월당 10,000개 호출)** 을 선택합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

다음으로, **검토 + 만들기** 탭으로 이동하고, 세부 정보를 검토한 다음, 페이지 아래쪽에 있는 **만들기** 단추를 클릭하여 리소스 및 새 리소스 그룹(새로 만들도록 구성한 경우)을 만듭니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> [만들기] 단추를 클릭하면 서비스가 만들어질 때까지 기다려야 하며, 이 경우 몇 분 정도 걸릴 수 있습니다.

리소스 만들기 프로세스가 완료되면 **배포가 완료됨**이라는 메시지가 표시됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>LUIS(Language Understanding Intelligent Service) 만들기

이 섹션에서는 LUIS 앱을 만들고, 예측 모델을 구성 및 학습시키고, 이전 단계에서 만든 Azure 예측 리소스에 연결합니다.

특히 사용자가 작업을 수행해야 한다고 말하면 앱에서 사용자가 참조하는 단추에 따라 장면의 빨간색 단추 세 개 중 하나에서 Interactable.OnClick() 이벤트를 트리거하는 의도를 만듭니다.

예를 들어 사용자가 **go ahead and launch the rocket(계속 진행하여 로켓 발사)** 이라고 말하면 앱에서 **go ahead**가 일부 **작업**을 수행해야 함을 의미하고 **대상**에 대한 Interactable.OnClick() 이벤트가 **launch** 단추에 있다고 예측합니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. LUIS 앱 만들기
2. 의도 만들기
3. 발화 예제 만들기
4. 엔터티 만들기
5. 발화 예제에 엔터티 할당
6. 앱 학습 테스트 및 게시
7. 앱에 Azure 예측 리소스 할당

### <a name="1-create-a-luis-app"></a>1. LUIS 앱 만들기

이전 섹션에서 Azure 리소스를 만들 때 사용한 것과 동일한 사용자 계정을 사용하여 <a href="https://www.luis.ai" target="_blank">LUIS</a>에 로그인하고, 국가를 선택하고, 사용 약관에 동의합니다. 다음 단계에서 **Azure 계정을 연결**하라는 메시지가 표시되면 **평가판 키를 사용하여 계속**을 선택하여 Azure 작성 리소스를 대신 사용합니다.

> [!NOTE]
> LUIS에 이미 가입되어 있고 작성 평가판 키가 만료된 경우 [Azure 리소스 작성 키로 마이그레이션](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) 문서를 참조하여 LUIS 작성 리소스를 Azure로 전환할 수 있습니다.

로그인하면 **내 앱** 페이지로 이동한 다음, **새 앱 만들기**를 클릭하고, **새 앱 만들기** 팝업 창에서 다음 값을 입력합니다.

* **이름**에 대해 적절한 이름을 입력합니다(예: *MRTK Tutorials - AzureSpeechServices*).
* **문화권**에 대해 **영어**를 선택합니다.
* **설명**에 대해 필요에 따라 적절한 설명을 입력합니다.

그런 다음, **완료** 단추를 클릭하여 새 앱을 만듭니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

새 앱이 만들어지면 해당 앱의 **대시보드** 페이지로 이동합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2. 의도 만들기

[대시보드] 페이지에서 빌드 > 앱 자산 > **의도** 페이지로 차례로 이동한 다음, **새 의도 만들기**를 클릭하고, **새 의도 만들기** 팝업 창에서 다음 값을 입력합니다.

* **의도 이름**에 대해 **PressButton**을 입력합니다.

그런 다음, **완료** 단추를 클릭하여 새 의도를 만듭니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> 이 자습서에서는 Unity 프로젝트에서 이 의도를 'PressButton'이라는 이름으로 참조합니다. 따라서 의도 이름을 똑같이 지정해야 합니다.

새 의도가 만들어지면 해당 의도의 페이지로 이동합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3. 발화 예제 만들기

다음 발화 예제를 **PressButton** 의도의 **발화 예제** 목록에 추가합니다.

* activate launch sequence
* show me a placement hint
* initiate the launch sequence
* press placement hints button
* give me a hint
* push the launch button
* i need a hint
* press the reset button
* time to reset the experience
* go ahead and launch the rocket

모든 발화 예제가 추가되면 PressButton의 의도 페이지가 다음과 같이 표시됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> 이 자습서에서는 Unity 프로젝트에서 'hint', 'hints', 'reset', 'launch'라는 단어를 참조합니다. 따라서 이러한 단어의 철자를 똑같이 표시해야 합니다.

### <a name="4-create-entities"></a>4. 엔터티 만들기

PressButton 의도 페이지에서 빌드 > 앱 자산 > **엔터티** 페이지로 차례로 이동한 다음, **새 엔터티 만들기**를 클릭하고, **새 엔터티 만들기** 팝업 창에서 다음 값을 입력합니다.

* **엔터티 이름**에 대해 **Action**을 입력합니다.
* **엔터티 형식**에 대해 **단순**을 선택합니다.

그런 다음, **완료** 단추를 클릭하여 새 엔터티를 만듭니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

이전 단계를 **반복**하여 **Target**이라는 다른 엔터티를 만듭니다. 이제 Action 및 Target이라는 두 엔터티가 있습니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> 이 자습서에서는 Unity 프로젝트에서 이러한 엔터티를 'Action' 및 'Target'이라는 이름으로 참조합니다. 따라서 엔터티 이름을 똑같이 지정해야 합니다.

### <a name="5-assign-entities-to-the-example-utterances"></a>5. 발화 예제에 엔터티 할당

[엔터티] 페이지에서 **PressButton** 의도 페이지로 다시 이동합니다.

PressButton 의도 페이지로 돌아가면 **go**, **ahead** 단어를 차례로 클릭한 다음, 상황별 팝업 메뉴에서 **Action(단순)** 을 선택하여 **go ahead**에 대한 레이블을 **Action** 엔터티 값으로 지정합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

**go ahead** 구가 이제 **Action** 엔터티 값으로 정의됩니다. 마우스 커서로 Action 엔터티 이름 위를 가리키면 연결된 Action 엔터티 값이 표시됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> 위의 이미지에서 레이블 아래에 표시된 빨간색 선은 엔터티 값이 예측되지 않았음을 나타냅니다. 이는 다음 섹션에서 모델을 학습시킬 때 해결됩니다.

다음으로, **launch** 단어를 클릭한 다음, 상황별 팝업 메뉴에서 **Target(단순)** 을 선택하여 **launch**에 대한 레이블을 **Target** 엔터티 값으로 지정합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

이제 **launch** 단어가 **Target** 엔터티 값으로 정의됩니다. 마우스 커서로 Target 엔터티 이름 위를 가리키면 연결된 Target 엔터티 값이 표시됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

이제 PressButton 의도 발화 예제인 'go ahead and launch the rocket'은 다음과 같이 예측되도록 구성되었습니다.

* 의도: PressButton
* Action 엔터티: go ahead
* Target 엔터티: launch

이전 2단계 프로세스를 **반복**하여 Action 및 Target 엔터티 레이블을 각 발화 예제에 할당합니다. 다음 단어에 대한 레이블을 **Target** 엔터티로 지정해야 한다는 점에 유의하세요.

* **hint**(Unity 프로젝트에서 HintsButton을 대상으로 함)
* **hints**(Unity 프로젝트에서 HintsButton을 대상으로 함)
* **reset**(Unity 프로젝트에서 ResetButton을 대상으로 함)
* **launch**(Unity 프로젝트에서 LaunchButton을 대상으로 함)

레이블이 모든 발화 예제에 지정되면 PressButton의 의도 페이지가 다음과 같이 표시됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

다른 방법으로 올바른 엔터티를 할당했는지 다시 확인하려면 **보기 옵션** 메뉴를 클릭하고 보기를 **엔터티 값 표시**로 전환합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

이제 보기가 엔터티 값을 표시하도록 설정된 상태에서 마우스 커서로 레이블이 지정된 단어와 구 위를 가리키면 할당된 엔터티 이름을 빠르게 확인할 수 있습니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a>6. 앱 학습 테스트 및 게시

앱을 학습시키려면 **학습** 단추를 클릭하고 학습 프로세스가 완료될 때까지 기다립니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> 위의 이미지에서 볼 수 있듯이 모든 레이블 아래의 빨간색 선이 제거되어 모든 엔터티 값이 예측되었음을 나타냅니다. 또한 [학습] 단추 왼쪽에 있는 상태 아이콘이 빨간색에서 녹색으로 변경되었습니다.

학습 프로세스가 완료되면 **테스트** 단추를 클릭한 다음, **go ahead and launch the rocket**을 입력하고 Enter 키를 누릅니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

테스트 발화가 처리되면 **검사**를 클릭하여 테스트 결과를 확인합니다.

* 의도: PressButton(98.5% 확신도)
* Action 엔터티: go ahead
* Target 엔터티: launch

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

앱을 게시하려면 오른쪽 위에서 **게시** 단추를 클릭한 다음, **게시 슬롯 및 설정 선택** 팝업 창에서 **프로덕션**을 선택하고 **게시** 단추를 클릭합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

게시 프로세스가 완료될 때까지 기다립니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a>7. 앱에 Azure 예측 리소스 할당

관리 > 애플리케이션 설정 > **Azure 리소스** 페이지로 차례로 이동합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

[Azure 리소스] 페이지에서 **예측 리소스 추가** 단추를 클릭하고, **앱에 리소스 할당** 팝업 창에서 다음 값을 선택합니다.

* **테넌트 이름**에 대해 사용자의 테넌트 이름을 선택합니다.
* **구독 이름**에 대해 이전에 [Azure Language Understanding 리소스 만들기](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)에서 사용한 것과 동일한 구독을 선택합니다.
* **LUIS 리소스 이름**에 대해 이전에 [Azure Language Understanding 리소스 만들기](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)에서 만든 예측 리소스를 선택합니다.

그런 다음, **리소스 할당** 단추를 클릭하여 Azure 예측 리소스를 앱에 할당합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

리소스가 할당되면 [Azure 리소스] 페이지가 다음과 같이 표시됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>Unity 프로젝트를 LUIS 앱에 연결

관리 > 애플리케이션 설정 > **Azure 리소스** 페이지에서 **복사** 아이콘을 클릭하여 **쿼리 예제**를 복사합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

Unity 프로젝트로 돌아가서 [계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **Lunarcom 의도 인식기(스크립트)** 구성 요소를 찾아서 다음과 같이 구성합니다.

* **LUIS 엔드포인트** 필드에서 이전 단계에서 복사한 **쿼리 예제**를 붙여넣습니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>의도 인식 테스트 및 향상

Unity 편집기에서 의도 인식을 직접 사용하려면 개발 컴퓨터에서 받아쓰기를 사용하도록 허용해야 합니다. 이 설정을 확인하려면 Windows **설정**을 연 다음, **개인 정보** > **음성**을 차례로 선택하고, **온라인 음성 인식**이 설정되어 있는지 확인합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

이제 게임 모드로 들어가면 먼저 로켓 단추를 눌러 의도 인식을 테스트할 수 있습니다. 그런 다음, 컴퓨터에 마이크가 있다고 가정하여 첫 번째 발화 예제인 **go ahead and launch the rocket**이라고 말하면 LunarModule이 우주로 발사되는 것을 볼 수 있습니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

모든 **발화 예제**를 시도한 다음, **발화 예제의 일부 변형**뿐만 아니라 몇 가지 **임의 발화**도 시도합니다.

다음으로, <a href="https://www.luis.ai" target="_blank">LUIS</a>로 돌아가서 빌드 > 앱 성능 향상 >  **엔드포인트 발화 검토** 페이지로 차례로 이동하고, **토글** 단추를 사용하여 기본 엔터티 보기에서 **토큰 보기**로 전환한 다음, 발화를 검토합니다.

* **발화** 열에서 필요에 따라 할당된 레이블을 변경하고 제거하여 의도에 맞게 조정합니다.
* **맞춤 의도** 열에서 의도가 올바른지 확인합니다.
* **추가/삭제** 열에서 녹색 확인 표시 단추를 클릭하여 발화를 추가하거나, 빨간색 x 단추를 클릭하여 삭제합니다.

발화를 원하는 만큼 검토한 경우 **학습** 단추를 클릭하여 모델을 다시 학습시킨 다음, **게시** 단추를 클릭하여 업데이트된 앱을 다시 게시합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> 엔드포인트 발화는 PressButton 의도에 맞추지 않지만, 해당 발화에 의도가 없음을 모델에 알리려면 맞춤 의도를 [없음]으로 변경할 수 있습니다.

앱 모델을 향상시키려면 이 프로세스를 원하는 횟수만큼 **반복**합니다.

## <a name="congratulations"></a>축하합니다.

이제 프로젝트에는 AI 지원 음성 명령이 있으므로 애플리케이션에서 정확한 명령을 발화하지 않더라도 사용자의 의도를 인식할 수 있습니다. 디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.
