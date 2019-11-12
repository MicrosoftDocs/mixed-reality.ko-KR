---
title: Azure Speech Services 자습서-4. 의도 및 자연어 이해 설정
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 9235452d9dce38e9d849821a694a5d4c710d8e87
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913334"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. 의도 및 자연어 이해 설정

이 단원에서는 Azure Speech Service의 의도 기능을 살펴봅니다. 의도 기능을 사용 하면 사용자가 특정 음성 명령을 사용 하지 않아도 되 고 시스템에서 해당 의도를 인식할 수 있는 AI 지원 음성 명령으로 응용 프로그램을 활용할 수 있습니다. 이 단원에서는 Azure LUIS 포털을 설정 하 고, 의도/엔터티/길이 발언를 설정 하 고, 의도 리소스를 게시 하 고, Unity 앱을 의도 리소스에 연결 하 고, 첫 번째 의도 API 호출을 수행 합니다.

## <a name="objectives"></a>목표

- 응용 프로그램에서 의도 및 자연어 이해를 설정 하는 방법을 알아봅니다.
- Azure의 LUIS 포털을 설정 하는 방법 알아보기
- Azure에서 의도, 엔터티 및 길이 발언를 설정 하는 방법을 알아봅니다.

## <a name="instructions"></a>지침

1. 컴퓨터에서 받아쓰기를 사용 하도록 허용 합니다. 이렇게 하려면 Windows 설정으로 이동 하 여 "개인 정보"를 선택 하 고 "speech"를 선택한 다음 "& 음성"을 선택 하 여 음성 서비스를 켜고 제안 사항을 입력 합니다.

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. [Azure Portal](https://portal.azure.com/)에 로그인 합니다. 로그인 하면 리소스 만들기를 클릭 하 고 "Language Understanding"를 검색 한 다음 enter 키를 누릅니다.

    ![mrlearning-speech-ch4-1-step2](images/mrlearning-speech-ch4-1-step2.png)

3. **만들기** 단추를 클릭 하 여이 서비스의 인스턴스를 만듭니다.

    ![mrlearning-speech-ch4-1-step3a](images/mrlearning-speech-ch4-1-step3a.png)

    리소스에 **이름을**지정 합니다 (예: *Speech-SDK-학습-모듈*). **구독**의 경우 평가 계정이 있는 경우 *종 량* 제 또는 *무료 내역* 을 선택 합니다. 그런 다음 **새로 만들기** 링크를 클릭 하 여 새 **리소스 그룹** 을 만들고, 이름을 입력 합니다 (예: *HoloLens-2-자습서-리소스 그룹*), **확인** 단추를 차례로 클릭 합니다.

    ![mrlearning-speech-ch4-1-step3b](images/mrlearning-speech-ch4-1-step3b.png)

4. **제작 위치** 및 **런타임 위치**를 선택 합니다 .이 자습서에서는 *미국 서 부*를 사용 합니다. 그런 다음 **제작 가격 책정 계층** 및 **런타임 가격 책정 계층**에 대해 *F0 (월별 초당 5 개 호출, 매월 10k 호출)* 를 선택 합니다. 마지막으로, **만들기** 단추를 클릭 하 여 새 리소스 그룹 뿐만 아니라 리소스를 만듭니다.

    ![mrlearning-speech-ch4-1-step4](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    >만들기 단추를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

5. 리소스 만들기 프로세스가 완료 되 면 **배포가 완료 되었습니다**. 메시지가 표시 됩니다.

    ![mrlearning-speech-ch4-1-step5](images/mrlearning-speech-ch4-1-step5.png)

6. 동일한 사용자 계정을 사용 하 여 [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) 포털에 로그인 하 고, 국가를 선택 하 고, 사용 약관에 동의 합니다.

    >[!NOTE]
    >Language Understanding 포털에 도달 하면 Azure Portal와 동일한 자격 증명을 사용 하 여 로그인 해야 할 수 있습니다. LUIS를 처음 사용 하는 경우 시작 페이지의 아래쪽으로 스크롤하여 "LUIS 만들기" 앱 단추를 찾아 클릭 해야 합니다.

7. 로그인 한 후 내 앱 (현재 해당 섹션에 있지 않은 경우)을 클릭 합니다. 그런 다음 새 앱 만들기를 클릭할 수 있습니다. 새 앱의 이름을 "Speech SDK Learning Module"으로 합니다. 설명 필드에 "Speech SDK Learning Module"을 추가 합니다. 그런 다음 "완료"를 클릭 합니다.

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    >앱이 영어와 다른 언어를 파악 해야 하는 경우 "Culture"를 적절 한 언어로 변경 해야 합니다.

8. 오른쪽 위에 있는 "빌드"를 클릭 합니다.

9. 왼쪽의 앱 자산에서 "의도"를 선택한 다음 "새 의도 만들기"를 클릭 하 고 이름을 "보도 ..."로 설정 합니다.

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    >Lunarcom 앱이 이름으로 참조 하기 때문에이 자습서에 사용 된 의도 및 엔터티 이름을 사용 하는 것이 중요 합니다.

    >[!NOTE]
    >이제 "보도" 및 "없음"의 두 가지 의도를 가집니다.

10. 왼쪽의 앱 자산에서 "엔터티"를 선택 하 고 "새 엔터티 만들기"를 클릭 하 고 "Action"으로 이름을로 설정 하 고 엔터티 형식을 "Simple"로 유지 합니다.

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. "새 엔터티 만들기"를 다시 클릭 하 고 이름을 "대상"으로 한 다음 엔터티 형식을 "Simple"로 유지 합니다.

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. 왼쪽의 앱 자산에서 "의도"를 선택 하 고 10 단계에서 만든 "보도" 의도를 클릭 합니다.

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. 오른쪽에 있는 "보기 옵션" 드롭다운을 클릭 하 고 "엔터티 값 표시"를 선택 합니다.

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    "예제 입력 ..."을 클릭 합니다. 상자로. 그런 다음 길이 발언을 입력 합니다.

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. 오른쪽의 "보기 옵션" 드롭다운을 클릭 하 고 "엔터티 이름 표시"를 선택 합니다.

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. 각각의 10 길이 발언는 다음 위치에 1이 있는 엔터티 레이블을 포함 해야 합니다. 자주 단어를 클릭 하 고 팝업에서 "레이블 제거" 및 2를 선택 합니다. 레이블을 지정 해야 하는 단어를 클릭 하 고 팝업에서 적절 한 레이블을 선택 합니다.

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. 이제 모델을 게시 하려면 오른쪽 위에 있는 "학습"을 클릭 합니다. 그런 다음 처리가 완료 되 면 오른쪽 위에 있는 "테스트"를 클릭 합니다.

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. 텍스트 상자에 "시작 단추를 선택 하십시오."를 입력 합니다.

    >[!NOTE]
    >길이 발언 중 하나에서 작업으로 "선택"을 추가 하지 않았지만 "검사"를 클릭 하면 모델은 동작 엔터티로 "select"를 인식 합니다.
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. 이제 오른쪽 위에 있는 "게시"를 클릭 합니다. 드롭다운에 "Production"가 표시 되는지 확인 하 고 팝업 에서도 "게시"를 클릭 합니다.

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. 게시 된 후에는 페이지 맨 위에 녹색 막대가 표시 됩니다.  녹색 막대를 클릭 하 여 "관리" 페이지로 이동 합니다.

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. 왼쪽에 있는 "응용 프로그램 설정"의 "키 및 끝점"을 클릭 합니다. 그런 다음 "게시"를 "프로덕션"으로 설정 합니다. 자신의 이름과 일치 하도록 표준 시간대를 설정 하 고 상자를 선택 하 여 예측 된 의도 점수를 모두 포함 합니다. 마지막으로 "리소스 할당"을 클릭 합니다.

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. 첫 번째 드롭다운에서 테 넌 트를 선택 하 고 구독 이름 드롭다운에서 "종 량 제"을 선택 합니다. LUIS 리소스 이름 아래에서 1-5 단계에서 앞서 만든 리소스를 선택 합니다. 그런 다음 "리소스 할당"을 클릭 합니다.

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    >다음 섹션에서 쉽게 액세스할 수 있도록 방금 할당 한 리소스와 연결 된 끝점 URL을 복사 하 여 저장 해야 합니다.

    >[!NOTE]
    >테 넌 트 이름에 대해이 응용 프로그램에 대해 만든 회사 또는 프로필을 배치 합니다.

22. 이제 Unity에서 새 앱을 열고 계층에서 Lunarcom_Base 개체를 선택 합니다. 검사기 패널에서 "구성 요소 추가"를 클릭 하 고 "LunarcomIntentRecognizer"를 검색 하 여 선택 합니다.

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. 검사기 패널에서 "LunarcomIntentRecognizer"의 Luis 끝점 필드에 22 단계에서 저장 한 끝점 URL을 입력 합니다.

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    >검사기 패널의 "LunarcomOfflineRecognizer" 구성 요소에서 "SimulateOfflineMode"에 대해 "사용 안 함"이 선택 되어 있는지 확인 합니다. 그렇지 않으면 프로그램 테스트가 작동 하지 않습니다.

24. Unity 편집기에서 재생 단추를 누르고 로켓 단추를 클릭 하 여 의도 인식을 시작 합니다. "로켓 시작 단추를 선택 하십시오." 라는 구를 Utter.

    >[!NOTE]
    >앱에서 원하는 함수를 인식 하 고 로켓 단추를 활성화 했습니다.
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>축하합니다.

이 단원에서는 AI 지원 음성 명령을 추가 하는 방법을 배웠습니다. 이제 프로그램에서 정확한 음성 명령을 utter 하지 않아도 사용자의 의도를 인식할 수 있습니다.
