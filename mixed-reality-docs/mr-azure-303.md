---
title: MR 및 Azure 303-자연 언어 이해 (LUIS)
description: 혼합된 현실 응용 프로그램에서 Azure Intelligence Service LUIS (Language Understanding)를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 언어 인식 인텔리전스 서비스, luis, 몰입 형, hololens, vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603073"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR 및 Azure 303: 자연 언어 이해 (LUIS)

이 과정에서는 Language Understanding Language Understanding API를 사용 하 여 Azure Cognitive Services를 사용 하 여 혼합된 현실 응용 프로그램을 통합 하는 방법을 배웁니다.

![랩 결과](images/AzureLabs-Lab3-000.png)

*LUIS (language Understanding)* 는 사용자 수 원하는 고유한 단어 추출 통해 같은 사용자 입력에서 의미를 확인 하는 기능을 사용 하 여 응용 프로그램을 제공 하는 Microsoft Azure 서비스입니다. 이해 및 입력된 정보를 학습 하 고, 자세한 관련 정보를 사용 하 여 응답할 수 있는 기계 학습을 통해 수행 됩니다. 자세한 내용은 참조는 [Azure LUIS (Language Understanding) 페이지](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)합니다.

이 과정을 마치면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 몰입 형 헤드셋 응용 프로그램을 갖게 됩니다.

1.  사용자 입력된 음성 변환을, 몰입 형 헤드셋에 연결 된 마이크를 사용 하 여 캡처하십시오. 
2.  캡처된 받아쓰기를 전송 합니다 *Azure Language Understanding Intelligent Service* (*LUIS*). 
3.  LUIS 추출은 분석할 수 사용자의 요청 의도 확인 하려고 하며 송신 정보를 통해 의미 있는 합니다.

개발은 사용자 음성을 사용 및/또는 gaze 장면에 있는 개체의 색과 크기를 변경 하는 일을 할 수 있는 앱 만들기가 포함 됩니다. 컨트롤러 동작의 사용을 다루지 않습니다.

응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다. 이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다. 혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.

여러 번 학습 LUIS 준비가 되어에 나와 있는 [12 장](#chapter-12--improving-your-luis-service)합니다. LUIS의 학습을 수행한 회 더 나은 결과 받게 됩니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 및 Azure 303: 자연 언어 이해 (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다. 과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다. HoloLens를 사용 하는 경우 음성 캡처하는 동안 일부 echo를 확인할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다. 또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다. 내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 됩니다 있지만 문서 .

다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.

- 개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용
- [Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여](install-the-tools.md)
- [최신 Windows 10 SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여
- (없으면 헤드셋 내장 마이크와 스피커) 내장 마이크를 사용 하 여 헤드폰 집합
- Azure 설정 및 LUIS 검색에 대 한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다). 
2.  받아쓰기를 사용 하도록 설정 하려면 컴퓨터를 허용 하려면로 이동 **Windows 설정 > 개인 정보 > 음성 변환, 잉크 입력 및 입력** 단추를 누르고 **켜기 음성 서비스 및 입력 제안을**합니다.
3.  이 자습서의 코드를 사용 하면에서 기록 하는 **마이크 장치 기본** 컴퓨터에서 설정 합니다. 기본 마이크 장치 음성 캡처를 사용 하려는 것으로 설정 되어 있는지 확인 합니다.
4.  헤드셋 내장 마이크에 있는지 확인 옵션 *"내 헤드셋 wear 있습니까 때 헤드셋 마이크 전환"* 에서 켜져 합니다 *혼합 현실 포털* 설정 합니다.

    ![몰입 형 헤드셋 설정](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>1 장-Azure Portal 설정

사용 하는 *Language Understanding* 서비스가 Azure에서 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.

1.  에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

2.  일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 *Language Understanding*를 클릭 하 고 **Enter**합니다. 

    ![LUIS 리소스 만들기](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.
 
3.  새 페이지를 오른쪽 Language Understanding 서비스에 대 한 설명을 제공 합니다. 선택이 페이지의 왼쪽 아래에 있는 합니다 **만들기** 단추,이 서비스의 인스턴스를 만듭니다.

    ![LUIS 서비스 만들기-법적 고 지 사항](images/AzureLabs-Lab3-02.png)
 
4.  한 번 클릭 하면 만들기:

    1. 원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.
    2. 선택 된 **구독**합니다.
    3. 선택 합니다 **가격 책정 계층** 첫 번째 경우, 적절 한 시간 만들기는 *LUIS 서비스*, 무료 계층 (F0 라는)를 사용할 수 있어야 합니다. 사용 가능한 할당이이 과정에 대 한 충분 한 것 이어야 합니다.
    4. 선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 교육 과정)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지). 

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    5. 확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다. 위치는 응용 프로그램은 실행할 지역의 것이 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.
    6. 이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.
    7. **만들기**를 선택합니다.

        ![LUIS 서비스-사용자 입력 만들기](images/AzureLabs-Lab3-03.png)
 
5.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.
6.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다. 
 
    ![새 Azure 알림 이미지](images/AzureLabs-Lab3-04.png)

7.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.

    ![성공적으로 리소스 만들기 알림](images/AzureLabs-Lab3-05.png)
 
8.  클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 새 LUIS 서비스 인스턴스로 이동 합니다. 
 
    ![LUIS 키 액세스](images/AzureLabs-Lab3-06.png)

9.  이 자습서에서 응용 프로그램 서비스의 구독 키를 사용 하 여 수행 하는 서비스에 대 한 호출을 수행 해야 합니다.
10. *빠른 시작* 페이지의 프로그램 *LUIS API* 서비스에서 첫 번째 단계로 이동 *키 가져오기*, 클릭 **키** (수도 있습니다 이렇게 키 아이콘으로 표시 하 고 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭 하 여). 이 서비스를 줄이면 *키*합니다.
11. 프로젝트에서 나중에이 필요 하므로 표시 된 키 중 하나가 복사본을 만듭니다. 
12. 에 *서비스* 페이지에서 클릭 *Language Understanding Portal* LUIS 앱 내에서 새 서비스를 만드는 데 사용할 수 있는 웹 페이지로 리디렉션되어야 합니다. 

## <a name="chapter-2--the-language-understanding-portal"></a>2 장-Language Understanding Portal

이 섹션에서는 LUIS 포털에서 LUIS 앱을 확인 하는 방법을 배웁니다. 

> [!IMPORTANT]
> 주의 해당 설정 합니다 *엔터티*를 *의도*, 및 *길이 발언* 이 장에서 LUIS 서비스 구축에 첫 번째 단계:도 해야 재 학습 서비스를 여러 번 하므로 보다 정확 하 게 확인 합니다. 에 대해서는 서비스의 재 학습 합니다 [장의 마지막](#chapter-12--improving-your-luis-service) 이 물론 있도록 완료 하는 합니다.

1.  에 도달 하면 합니다 *Language Understanding Portal*, 없는 경우 이미 Azure portal로 동일한 자격 증명에 로그인 해야 합니다. 

    ![LUIS 로그인 페이지](images/AzureLabs-Lab3-07.png)
 
2.  시작 페이지를 찾아 클릭의 맨 아래로 스크롤하여 해야 LUIS를 사용 하 여 처음으로이 경우는 **만들 LUIS 앱** 단추입니다.

    ![LUIS 앱 페이지 만들기](images/AzureLabs-Lab3-08.png)
 
3.  일단 로그인 하면 클릭 **My apps** (없는 경우 해당 섹션에서 현재). 클릭할 수 있습니다 **새 앱 만들기**합니다.

    ![LUIS-내 앱 이미지](images/AzureLabs-Lab3-09.png)
 
4.  앱을 제공 된 *이름*합니다.
5.  영어가 아닌 언어를 이해할 수 할 앱을 하는 경우 변경 해야 합니다 *문화권* 적절 한 언어입니다.
6.  여기 추가할 수도 있습니다는 *설명* 새 LUIS 앱입니다.

    ![LUIS-새 앱 만들기](images/AzureLabs-Lab3-10.png)

7.  누르면 **수행**를 입력 합니다 *빌드* 새 페이지 *LUIS* 응용 프로그램입니다.
8.  여기 이해 하려면 몇 가지 중요 한 개념이 있습니다.

    -   *의도*, 다음 사용자에서는 쿼리에서 호출 되는 메서드를 나타냅니다. *의도* 하나 이상 있을 수 있습니다 *엔터티*합니다.
    -   *엔터티*, 관련 된 정보를 설명 하는 쿼리의의 구성 요소인 합니다 *의도*합니다.
    -   *길이 발언*, 개발자가 해당 LUIS를 사용 하 여 자체 학습 제공은 쿼리의 예입니다.

이러한 개념은 완벽 하 게 지우기 경우 처럼이 코스 명확 하 게 설명으로이 챕터에 걱정 하지 마십시오.

만들어 시작 합니다 *엔터티* 이 과정을 빌드하는 데 필요한 합니다.

9.  페이지의 왼쪽에서 클릭 *엔터티*, 클릭 **새 엔터티 만들기**합니다.

    ![새 엔터티 만들기](images/AzureLabs-Lab3-11.png)

10. 새 엔터티를 호출 *색*, 해당 유형을 설정 *단순*를 누릅니다 **수행**합니다.

    ![간단한 엔터티-색 만들기](images/AzureLabs-Lab3-12.png)
 
11. 엔터티를 만드는 데 3 개의 자세한 간단한 라는이 프로세스를 반복 합니다.

    -   *upsize*
    -   *downsize*
    -   *target*

결과 아래 이미지와 같이 표시 됩니다.

![엔터티 만들기의 결과](images/AzureLabs-Lab3-13.png)
 
이 시점에서 만들 수 있습니다 *의도*합니다. 

> [!WARNING]
> 삭제 하지 마십시오 합니다 **None** 의도 합니다.

12. 페이지의 왼쪽에서 클릭 **의도**, 클릭 **새 의도 만들기**합니다.

    ![새로운 인 텐트 만들기](images/AzureLabs-Lab3-14.png)

13. 새 호출 *의도* **ChangeObjectColor**합니다.

    > [!IMPORTANT]
    > 이렇게 *의도* 이름은이 과정의 뒷부분에 나오는 코드 내에서 따라서 최상의 결과 사용이 이름을 제공 하는 대로 정확 하 게 합니다.

일단 의도 페이지로 리디렉션됩니다 이름을 확인 합니다.

![LUIS-의도 페이지](images/AzureLabs-Lab3-15.png)

5 개 이상의 서로 다른 형식으로 라는 텍스트 상자는 표시 됩니다 *길이 발언*합니다.

> [!NOTE]
> LUIS는 모든 길이 발언을 소문자로 변환 합니다.

14. 다음 삽입 *Utterance* 상위 텍스트 상자에서 (텍스트를 사용 하 여 현재 *약 5 예제 입력...* )을 누릅니다 **Enter**:

```
The color of the cylinder must be red
```

새 *Utterance* 아래 목록에 표시 됩니다.

동일한 프로세스를 다음 다음 6 (6) 길이 발언을 삽입 합니다.

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

사용자가 만든 각 Utterance, 엔터티로 LUIS 사용 해야 하는 단어 식별 해야 합니다. 이 예제의 모든 색으로 레이블을 지정 해야는 *색* 엔터티와 대상으로 가능한 모든 참조는 *대상* 엔터티.

15. 이렇게 하려면 단어를 클릭 해 보십시오 *cylinder* 선택한 첫 번째 Utterance *대상*합니다.

    ![Utterance 대상 식별](images/AzureLabs-Lab3-16.png)
 
16. 이제 이라는 단어를 클릭 *빨간색* 선택한 첫 번째 Utterance *색*합니다.

    ![Utterance 엔터티 식별](images/AzureLabs-Lab3-17.png)
 
17. 다음 줄을 또한 레이블을 위치 *큐브* 이어야 합니다는 *대상*, 및 *검은색* 이어야 합니다는 *색*합니다. 단어를 사용 하 여 또한 *'this'* 를 *'그것'*, 및 *'이 object이 '* 를 제공 하 고, 따라서도 관련 되지 않은 대상 유형을 사용할 수 있어야 하는 합니다. 

18. 모든 대상이 눈에 띄도록 이라는 레이블이 지정 된 엔터티를 가질 때까지 위에서 설명한 프로세스를 반복 합니다. 참조는 아래 이미지는 데 도움이 필요한 경우.

    > [!TIP]
    > 경우 엔터티로으로 레이블을 단어 선택:
    > - 단일 단어 바로 대 한 클릭 합니다.
    > - 두 개 이상의 단어 집합의 경우 시작 부분 및 집합의 끝에 다음을 클릭 합니다.

    > [!NOTE]
    > 사용할 수는 *토큰 뷰* 토글 단추 사이 전환할 **엔터티 / 토큰 뷰**!

19. 결과 보여 주는 아래 이미지에 표시 된 대로 사용 해야 합니다 **엔터티 / 토큰 뷰**:

    ![토큰 및 엔터티 보기](images/AzureLabs-Lab3-18.png)
  
20. 이 시점에서 키를 눌러 합니다 **학습** 페이지의 오른쪽 위에 있는 단추 및 녹색으로 바뀌도록 하는 데이 작은 round 표시기에 대 한 대기 합니다. LUIS이이 의도 인식할 성공적으로 학습 되었으면 나타냅니다.

    ![LUIS 학습](images/AzureLabs-Lab3-19.png)
 
21. 연습으로 라는 새 의도 만들기 **ChangeObjectSize**, 엔터티를 사용 하 여 *대상*에 *업사이징*, 및 *줄이지*합니다.
22. 다음 8 (8) 표현에 대 한 삽입 이전 의도 동일한 프로세스를 수행 *크기* 변경:

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. 결과 아래 그림과에서 같은 같아야 합니다.

    ![ChangeObjectSize 토큰을 설정 / 엔터티](images/AzureLabs-Lab3-20.png) 

24. 두 의도 한 번 **ChangeObjectColor** 및 **ChangeObjectSize**, 만든 및 클릭을 학습 합니다 **게시** 페이지 위쪽 단추입니다.

    ![LUIS 서비스 게시](images/AzureLabs-Lab3-21.png)

25. 에 *게시* 페이지 완료 되며 코드에서 액세스할 수 있도록 LUIS 앱을 게시 합니다.

    1. 드롭다운을 내놓은 *에 게시* 으로 **프로덕션**.
    2. 설정 된 *표준 시간대* 표준 시간대로 합니다.
    3. 확인란 **Include 모든 의도 점수를 예측**합니다.
    4. 클릭할 **프로덕션 슬롯에 게시**합니다.

        ![게시 설정](images/AzureLabs-Lab3-22.png)

26. 단원의 *자원과 키*:

    1.  Azure Portal에서 서비스 인스턴스에 대해 설정 하는 지역을 선택 합니다.
    2.  알 수 있습니다는 **Starter_Key** 요소 아래에 무시 합니다.
    3.  클릭할 **키 추가** 삽입 합니다 *키* 서비스 인스턴스를 만들 때 Azure Portal에서 가져온입니다. Azure 및 LUIS 포털은 동일한 사용자에 로그인 하는 경우 제공 됩니다에 대 한 드롭다운 메뉴가 *테 넌 트 이름*를 *구독 이름*, 및 *키* (사용 하려는 Azure Portal에서 이전에 제공 된 동일한 이름을 갖습니다.

    > [!IMPORTANT] 
    > 아래 *끝점*, 키에 해당 하는 끝점의 복사본 삽입 한, 곧 코드에서 사용 됩니다.
 
## <a name="chapter-3--set-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 *Unity* 누릅니다 **새로 만들기**합니다. 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab3-24.png)

2.  Unity 프로젝트 이름을 제공 해야 이제 삽입 **MR_LUIS**합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**합니다. 설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab3-25.png)
 
3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 편집으로 이동 > 기본 설정으로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab3-26.png)
 
4.  이동한 다음 **파일 > 빌드 설정** 플랫폼 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환** 단추입니다.

    ![빌드 설정 창, uwp 플랫폼 전환 합니다.](images/AzureLabs-Lab3-27.png)
 
5.  로 이동 **파일 > 빌드 설정** 되어 있는지 확인 합니다.

    1. **장치를 대상** 로 설정 된 **모든 장치**

        > Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.

    2. **빌드 형식** 로 설정 된 **D3D**
    3. **SDK** 로 설정 된 **가장 최근에 설치 된**
    4. **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**
    5. **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**
    6. 장면 저장 하 고 빌드에 추가 합니다.

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.
        
            ![추가 백그라운드에서 열기 단추를 클릭](images/AzureLabs-Lab3-28.png)

        2. 새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab3-29.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **MR_LuisScene**, 키를 누릅니다 **저장**합니다.

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab3-30.png)

    7. 설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.

6. 에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한. 

    ![플레이어 설정 열기](images/AzureLabs-Lab3-31.png) 
 
7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. 에 **기타 설정** 탭:

        1. **스크립팅 런타임 버전** 있어야 **안정적인** (.NET 3.5와 같음).
        2. **백 엔드를 스크립팅** 있어야 **.NET**
        3. **API 호환성 수준** 있어야 **.NET 4.6**

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab3-32.png)
      
    2. 내 합니다 **게시 설정** 탭의 **기능**, 확인:

        1. **InternetClient**
        2. **Microphone**

            ![게시 설정을 업데이트 합니다.](images/AzureLabs-Lab3-33.png)

    3. 패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab3-34.png)

8.  년대 *빌드 설정* _Unity C#_  프로젝트는 더 이상 회색으로;이 옆의 확인란을 선택 합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).

## <a name="chapter-4--create-the-scene"></a>4 장-장면 만들기

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage),으로 프로젝트로 가져올는 [사용자 지정 패키지 ](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [5 장](#chapter-5--create-the-microphonemanager-class)합니다. 

1.  빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*아래에 있는 **3D 개체**, 추가 **평면**합니다.

    ![평면을 만듭니다.](images/AzureLabs-Lab3-35.png)

2.  주의 내에서 마우스 오른쪽 단추로 때 합니다 *계층* 다시 선택한 마지막 개체에도 있는 경우 개체를 더 만들려면 선택한 개체 부모가 될 새 개체의 합니다. 빈 공간을 계층 내에서 마우스 왼쪽 단추로 클릭 하 고 마우스 오른쪽 단추로 클릭 한 다음이 문제를 방지 합니다.

3.  다음 개체를 추가 하려면 위의 절차를 반복 합니다.

    1. *구*
    2. *원기둥*
    3. *Cube*
    4. *3D 텍스트*

4.  결과 장면 *계층* 아래 이미지 처럼 보여야 합니다.

    ![장면 계층 설치 합니다.](images/AzureLabs-Lab3-36.png)
 
5.  마우스 왼쪽 단추로 클릭 합니다 **주 카메라** 살펴볼 것을 선택 하려면를 *검사기 패널* 모든 카메라 개체 표시 됩니다는 해당 구성 요소입니다.
6.  클릭 합니다 **구성 요소 추가** 맨 아래쪽에 있는 단추를 *검사기 패널*합니다.

    ![오디오 소스 추가](images/AzureLabs-Lab3-37.png)
 
7.  라는 구성 요소에 대 한 검색 *오디오 원본*위와 같이 합니다.
8.  되었는지도 확인 합니다 *변환* 주 카메라의 구성 요소 (0,0,0)으로 설정 되 면이 키를 눌러 가능 합니다 **기어** 카메라의 옆에 있는 아이콘 *변환* 구성 요소 선택 하 고 **재설정**합니다. 합니다 *변환* 구성 요소는 다음과 같이 보입니다.

    1.  *위치* 로 설정 된 **0, 0, 0**합니다.
    2.  *회전* 로 설정 된 **0, 0, 0**합니다.

    > [!NOTE] 
    > Microsoft HoloLens 대 한 다음을 변경 해야의 일부인 합니다 **카메라** 에 있는 구성 요소에 **주 카메라**:
    > - **플래그를 지웁니다.** 단색입니다.
    > - **백그라운드** ' 검정, 알파 0'-16 진수 색: #00000000 합니다.

9.  마우스 왼쪽 단추로 클릭 합니다 **평면** 하 여 선택 합니다. 에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:

    |       | 변환- *위치* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. 마우스 왼쪽 단추로 클릭 합니다 **구체** 하 여 선택 합니다. 에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:

    |       | 변환- *위치* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. 마우스 왼쪽 단추로 클릭 합니다 **Cylinder** 하 여 선택 합니다. 에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:

    |       | 변환- *위치* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. 마우스 왼쪽 단추로 클릭 합니다 **큐브** 하 여 선택 합니다. 에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:

    |        | 변환- *위치* |       |  \| |       | 변환- *회전* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. 마우스 왼쪽 단추로 클릭 합니다 **새 텍스트** 개체를 선택 합니다. 에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:

    |       | 변환- *위치* |       |  \| |       | 변환- *확장* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. 변경 **글꼴 크기** 에 **텍스트 메시** 구성 요소를 **50**합니다.
15. 변경 된 *이름* 의 **텍스트 메시** 개체를 **받아쓰기 텍스트**합니다.

    ![3D 텍스트 개체 만들기](images/AzureLabs-Lab3-38.png)
 
16. 이제 계층 패널 구조에 다음과 같이 표시 됩니다.

    ![장면 뷰에서 텍스트 메시](images/AzureLabs-Lab3-38b.png)


17. 최종 장면 아래 이미지와 같습니다.

    ![장면 뷰입니다.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>5 장-MicrophoneManager 클래스 만들기

첫 번째 스크립트를 만드는 것은 *MicrophoneManager* 클래스입니다. 다음에 만듭니다는 *LuisManager*의 *행동* 클래스 및 마지막으로 *Gaze* 클래스 (자유롭게도 설명 하지만 이러한 이제 모든 만들기 연결할 각 장).

합니다 *MicrophoneManager* 클래스는 담당 합니다.

-   헤드셋 이나 컴퓨터 (중 하나는 기본)에 연결 하 여 녹음 장치를 검색 합니다.
-   (의견) 오디오를 캡처하고 받아쓰기를 사용 하 여 문자열로 저장 합니다.
-   음성, 일시 중지 되 면 받아쓰기를 제출 합니다 *LuisManager* 클래스입니다. 

이 클래스를 만들려면: 

1.  마우스 오른쪽 단추로 클릭 합니다 *프로젝트 패널*를 **만들기 > 폴더**합니다. 폴더를 호출 **스크립트**합니다. 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab3-40.png)
 
2.  사용 하 여 합니다 **스크립트** 가 만든 폴더를 두 번 클릭 하 여 엽니다. 그런 다음, 해당 폴더 내에서 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 *MicrophoneManager*합니다. 

3.  두 번 클릭 *MicrophoneManager* 사용 하 여 열려는 *Visual Studio*합니다.
4.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  그런 다음 내에서 다음 변수를 추가 합니다 *MicrophoneManager* 클래스:

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  에 대 한 코드 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다. 이러한 클래스를 초기화할 때 호출 됩니다.

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  이제 앱을 시작 및 음성 캡처를 중지 하 고 전달 하는 메서드를 *LuisManager* 곧 빌드하게 되는 클래스입니다. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  추가 된 *받아쓰기 처리기* 음성을 놓을 때 호출 되는 합니다. 이 메서드는 받아쓰기 텍스트를 전달 합니다 *LuisManager* 클래스입니다.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > 삭제 합니다 *update ()* 메서드가이 클래스는 사용 하지 것입니다.

9.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

    > [!NOTE]
    > 이 시점에 표시 되는 오류를 확인할 수 있습니다 합니다 *Unity 편집기 콘솔 패널이*합니다. 코드를 참조 하기 때문에 이것이 합니다 *LuisManager* 만든 다음 장에서 클래스입니다.

## <a name="chapter-6--create-the-luismanager-class"></a>6 장-LUISManager 클래스 만들기

만들기 위한 시간이 합니다 *LuisManager* Azure LUIS 서비스를 호출 하 게 하는 클래스입니다. 

이 클래스의 목적은 받아쓰기 텍스트를 수신 하는 것을 *MicrophoneManager* 클래스 및 보낼 합니다 *Azure Language Understanding API* 분석할 합니다.

이 클래스를 역직렬화 하는 *JSON* 응답의 적절 한 메서드를 호출 합니다 *동작도* 클래스는 작업을 트리거합니다.

이 클래스를 만들려면: 

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 
2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 *LuisManager*합니다. 
3.  스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.
4.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  세 가지 클래스를 만들어 시작 합니다 **내** 는 *LuisManager* 클래스 (동일한 스크립트 파일에서 위의 *start ()* 메서드)를 나타내는 deserialize 된 형식 Azure에서 JSON 응답입니다.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  다음으로 내에서 다음 변수를 추가 합니다 *LuisManager* 클래스:
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  해야에서 LUIS 끝점을 이제 배치 (있음 LUIS 포털에서 해야) 합니다.

8.  에 대 한 코드를 *Awake()* 메서드는 이제 추가 해야 합니다. 이 메서드는 클래스를 초기화할 때 호출 됩니다.

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  이제이 응용 프로그램에서 받은 받아쓰기를 사용 하 여 메서드를 *MicrophoneManager* 클래스를 *LUIS*, 다음 받고 응답을 역직렬화 합니다. 
10. 인스턴스에 전달 되는 의도 및 연결 된 엔터티 값 결정 되 면 합니다 *동작도* 의도 한 동작을 트리거하는 클래스입니다.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. 이라는 새 메서드를 만듭니다 *AnalyseResponseElements()* 결과이 읽힙니다 *AnalysedQuery* 엔터티를 확인 합니다. 전달 인스턴스의 됩니다 해당 엔터티 확인 되 면 합니다 *동작도* 작업에서 사용 하는 클래스입니다.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > 삭제 합니다 *start ()* 하 고 *update ()* 메서드가이 클래스에서 사용 하지 것입니다.

12. 변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

> [!NOTE]
> 이 시점에 표시 되는 몇 가지 오류를 확인할 수 있습니다 합니다 *Unity 편집기 콘솔 패널이*합니다. 코드를 참조 하기 때문에 이것이 합니다 *행동* 다음 장에서 만들려는 클래스.

## <a name="chapter-7--create-the-behaviours-class"></a>7 장-동작도 클래스 만들기

합니다 *동작도* 클래스에서 제공 하는 엔터티를 사용 하 여 작업을 트리거할 합니다 *LuisManager* 클래스입니다.

이 클래스를 만들려면: 

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 
2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 *동작도*입니다. 
3.  사용 하 여 열고 스크립트를 두 번 클릭 *Visual Studio*합니다.
4.  그런 다음 내에서 다음 변수를 추가 합니다 *동작도* 클래스:

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  추가 된 *Awake()* 메서드 코드입니다. 이 메서드는 클래스를 초기화할 때 호출 됩니다.

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  다음 메서드 호출을 *LuisManager* 클래스 (이전에 만든) 인지 쿼리의 대상 개체를 적절 한 조치를 트리거해야 합니다.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  추가 합니다 *FindTarget()* 결정 하기 위해 메서드를 *Gameobject* 현재 의도의 대상입니다. 이 메서드는 대상의 기본값은 *GameObject* 되 "gazed" 명시적 대상이 없습니다. 엔터티에 정의 된 경우.

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > 삭제 합니다 *start ()* 하 고 *update ()* 메서드가이 클래스에서 사용 하지 것입니다.

8.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

## <a name="chapter-8--create-the-gaze-class"></a>8 장 – 게이즈 클래스 만들기

마지막으로 클래스는이 앱을 완료 해야 합니다 *Gaze* 클래스입니다. 이 클래스에 대 한 참조를 업데이트 합니다 *GameObject* 현재 사용자의 visual 포커스가 있는 합니다.

이 클래스 만들려면: 

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 
2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 *Gaze*합니다. 
3.  사용 하 여 열고 스크립트를 두 번 클릭 *Visual Studio*합니다.
4.  이 클래스에 다음 코드를 삽입 합니다.

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

## <a name="chapter-9--completing-the-scene-setup"></a>9 장-장면 설치 완료

1.  장면의 설치를 완료 하려면 끌어 Scripts 폴더에서 만든 각 스크립트를 **주 카메라** 개체를 *계층 패널*합니다.
2.  선택 합니다 **주 카메라** 확인 합니다 *검사기 패널*, 연결 상태는 각 스크립트를 확인할 수 있어야 하 고 아직 설정 된 각 스크립트에 매개 변수가 표시 됩니다.

    ![카메라 참조 대상을 설정 합니다.](images/AzureLabs-Lab3-41.png)

3.  이러한 매개 변수를 올바르게 설정 하려면 다음이 지침을 따릅니다.

    1. *MicrophoneManager*:

        - *계층 패널*, 끌어를 **받아쓰기 텍스트** 개체를 **받아쓰기 텍스트** 매개 변수 값 상자.

    2. *행동*에서 *계층 패널*:

        - 끌어서를 **구체** 개체를 *구체* 참조 대상 상자.
        - 끌어서 합니다 **Cylinder** 에 *원기둥* 참조 대상 상자입니다.
        - 끌기 합니다 **큐브** 에 *큐브* 참조 대상 상자입니다.

    3. *Gaze*:

        - 설정 합니다 *Gaze 최대 거리* 하 **300** (아직 없는) 경우입니다. 

4.  결과 아래 이미지와 같이 표시 됩니다.

    ![이제 설정 카메라 참조 대상을 표시 합니다.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>10 장-Unity 편집기에서 테스트

장면 설정을 제대로 구현 하는 테스트입니다.

다음을 확인합니다.

-   에 연결 된 모든 스크립트를 **주 카메라** 개체입니다. 
-   모든 필드를 *주 카메라 검사기 패널* 올바르게 할당 됩니다.

1.  키를 눌러 합니다 **재생** 단추를 *Unity 편집기*합니다. 앱을 연결된 하는 몰입 형 헤드셋 내에서 실행 되어야 합니다.

2.  와 같은 몇 가지 길이 발언을 시도 합니다.

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 변경 하는 기본 오디오 장치에 대 한 Unity 콘솔에 오류를 표시 하는 경우 장면 예상 대로 작동 하지 않을 수 있습니다. 혼합된 현실 포털에 있는 헤드셋에 대 한 기본 제공 마이크를 사용 하 여 처리 하는 방식 때문입니다. 이 오류가 표시, 단순히 장면 중지 및 다시 시작 하 고으로 작동 해야 하는 경우 필요 합니다.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>11 장-빌드 및 UWP 솔루션 테스트용으로 로드

Unity 편집기에서 응용 프로그램 작동 하는지 확인 한 후를 빌드하고 배포할 수 있습니다.

빌드:

1.  클릭 하 여 현재 장면 저장 **파일 > 저장**합니다.
2.  로 이동 **파일 > 빌드 설정**합니다.
3.  라는 상자를 눈금 **Unity C# 프로젝트** (표시 및 UWP 프로젝트에서 생성 되 면 코드를 디버깅 하는 데 유용 합니다.
4.  클릭할 **열려 장면 추가**, 클릭 **빌드**합니다.

    ![빌드 설정 창](images/AzureLabs-Lab3-43.png)

4.  솔루션을 빌드 하려는 폴더를 선택 하 라는 메시지가 표시 됩니다. 

5.  만들기는 *빌드* 폴더 및 해당 폴더 내에서 원하는 적절 한 이름을 다른 폴더를 만듭니다. 
6.  클릭 **폴더 선택** 해당 위치에서 빌드를 시작 합니다.
 
    ![빌드 폴더를 만듭니다](images/AzureLabs-Lab3-44.png)
    ![선택 빌드 폴더](images/AzureLabs-Lab3-45.png)
 
7.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치는 창입니다.

로컬 컴퓨터에 배포 합니다.

1.  *Visual Studio*에서 만든 솔루션 파일을 엽니다 합니다 [이전 장](#chapter-10--test-in-the-unity-editor)합니다.
2.  에 **솔루션 플랫폼**를 선택 **x86**를 **로컬 컴퓨터**합니다.
3.  에 **솔루션 구성** 선택 **디버그**합니다.

    > Microsoft HoloLens 알 수 있습니다 것이 더 쉽게 *원격 컴퓨터*컴퓨터로 테더 링 없습니다 있도록 합니다. 그러나 또한 다음을 수행 해야 합니다.
    > - 알고는 **IP 주소** 내에서 찾을 수 있는 여 HoloLens의는 *설정 > 네트워크 및 인터넷 > Wi-fi > 고급 옵션*; IPv4는 주소를 사용 해야 합니다. 
    > - 확인 **개발자 모드** 됩니다 **에**에; *설정 > 업데이트 및 보안 > 개발자를 위한*합니다.

    ![앱 배포](images/AzureLabs-Lab3-46.png)
 
4.  로 이동 합니다 **빌드 메뉴** 를 클릭 **솔루션 배포** 컴퓨터에 응용 프로그램을 테스트용으로 로드 하려면.
5.  앱 시작 될 준비가 되었습니다. 설치 된 앱 목록에 나타나야 합니다.
6.  시작 되 면 앱 하 라는 메시지가 나타납니다에 대 한 액세스 권한을 부여 합니다 _마이크_합니다. 사용 하 여는 *동작 컨트롤러*, 또는 *음성 입력*, 또는 *키보드* 를 눌러 합니다 **예** 단추. 

## <a name="chapter-12--improving-your-luis-service"></a>12 장-LUIS 서비스 개선

>[!IMPORTANT] 
> 이 장에서 것이 매우 중요 하 고 LUIS 서비스의 정확도 높이 데 도움이 되는 대로 여러 번 시 interated 되도록 해야 할 수 있습니다:이 완료 하면 확인 합니다.

LUIS를 제공한 이해가 수준 향상을 위해 새 길이 발언을 캡처하고 사용 하 여 LUIS 앱을 다시 학습 해야 합니다.

예를 들어 LUIS "Increase" 이해 하 고 "업사이징" 교육 받은 수 있지만 "확대"와 같은 단어 이해 하기 위해 앱 있습니다 원하지?

응용 프로그램을 몇 번 사용 하면 LUIS에서 수집 된 및 LUIS 포털에서 사용할 수 있는 말씀 하 신 모든 것이 됩니다.

1.  이 포털 응용 프로그램으로 이동 [링크](https://www.luis.ai/home), 하 고 로그인 합니다.
2.  MS 자격 증명으로 로그인 되 면 클릭 하면 *앱 이름*합니다.
3.  클릭 합니다 **끝점 길이 발언 검토** 페이지의 왼쪽에 단추입니다.

    ![검토 길이 발언](images/AzureLabs-Lab3-47.png)
 
4.  응용 프로그램에 혼합된 현실에서 LUIS를 보낸 대상이 눈에 띄도록 목록이 표시 됩니다.

    ![목록 길이 발언](images/AzureLabs-Lab3-48.png)
 
강조 표시 된 일부 알 수 있습니다 *엔터티*합니다. 

강조 표시 된 각 단어를 마우스로 각 Utterance를 검토 하 고 및 엔터티는 누락 된 엔터티 인식 된 올바르게 잘못 된 엔터티는 확인할 수 있습니다.

위의 예제에서 찾을 수는 단어 "창"가 강조 표시 되었습니다 대상으로 하므로 마우스로 단어를 마우스로 클릭 하 여 수행 하는 실수를 수정 하는 데 필요한 것 **레이블 제거**합니다.

![확인 길이 발언](images/AzureLabs-Lab3-49.png)
![레이블 이미지 제거](images/AzureLabs-Lab3-50.png)
 
5.  완전히 잘못 된 길이 발언을 발견할 경우 삭제할 수 있습니다를 사용 하는 **삭제** 화면 오른쪽의 단추입니다.

    ![잘못 된 길이 발언 삭제](images/AzureLabs-Lab3-51.png)

6.  LUIS를 Utterance를 올바르게 해석에 생각 하는 경우 사용 하 여 이해를 확인할 수 있습니다 또는 합니다 **정렬 의도 추가** 단추입니다.

    ![정렬 된 의도 추가](images/AzureLabs-Lab3-52.png)

7.  표시 된 모든 길이 발언을 정렬 한 후 해 사용할 수 있는 경우 자세히 보려면 페이지를 다시 로드 합니다.
8.  것이 매우 중요 응용 프로그램 이해를 향상 시킬 수 만큼이 단계를 반복 합니다. 

**즐거운 시간 보내세요!**

## <a name="your-finished-luis-integrated-application"></a>완성 된 LUIS 통합 응용 프로그램

축 하 Azure 언어 인식 인텔리전스 서비스는 사용자의 표시를 이해 하 고 해당 정보에는 act를 활용 하는 혼합된 현실 앱을 빌드 했습니다.

![랩 결과](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

이 응용 프로그램을 사용 하는 동안는 Floor 개체 응시 하 게 요청 하 여 해당 색을 변경 하는 경우이 수행을 확인할 수 있습니다. Floor 색 변경에서 응용 프로그램을 중지 하는 방법에 대해 작업할 수 있습니까?

### <a name="exercise-2"></a>연습 2

확장 된 LUIS 및 앱 기능 장면;에서 개체에 대 한 추가 기능을 추가 해 보십시오. 예를 들어 게이즈 사용자에 따라 적중된 지점을 라는 및 그런 다음 기존 명령을 사용 하 여 현재 장면 개체와 함께 해당 개체를 사용할 수 있는 새 개체를 만듭니다. 
