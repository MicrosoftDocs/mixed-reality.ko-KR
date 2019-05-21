---
title: MR 및 Azure 304-Face recognition 얼굴 인식
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 인식, 몰입 형, hololens, vr 얼굴 혼합 현실, academy, unity, 자습서, api,
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603809"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR 및 Azure 304: Face recognition 얼굴 인식

![이 과정을 완료 하는 결과](images/AzureLabs-Lab4-00.png)

이 과정에서 배웁니다 혼합된 현실 응용 프로그램에 얼굴 인식 기능을 추가 하는 방법을 Microsoft Face API를 사용 하 여 Azure Cognitive Services를 사용 하 여 합니다.

*Azure의 Face API* 는 개발자가 클라우드에서 최고급 얼굴 알고리즘을 제공 하는 Microsoft 서비스입니다. 합니다 *Face API* 두 가지 주요 기능이 있습니다: 얼굴 특성을 사용 하 여 감지 및 얼굴 인식 합니다. 이렇게 하면 개발자가 아니라 얼굴에 대 한 그룹 집합을 설정 하 고 그런 다음 보내기 쿼리 이미지를 나중에 얼굴에 속한 사용자를 결정 하 합니다. 자세한 내용은 참조는 [Azure Face recognition 얼굴 인식 페이지](https://azure.microsoft.com/services/cognitive-services/face/)합니다.

이 과정을 마치면 다음을 수행 하는 일을 할 수는 HoloLens 응용 프로그램을 혼합된 현실이 제공 됩니다.

1. 사용 하 여는 **탭 제스처** 온보드 HoloLens 카메라를 사용 하 여 이미지 캡처를 시작 합니다. 
2. 캡처된 이미지를 보낼 합니다 *Azure의 Face API* 서비스입니다.
3. 결과 수신 합니다 *Face API* 알고리즘입니다.
4. 일치 하는 사용자의 이름을 표시 하는 간단한 사용자 인터페이스를 사용 합니다.

이 하는 방법을 알려주는 Face API 서비스에서 혼합된 현실 Unity 기반 응용 프로그램에 결과 가져옵니다.

응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다. 이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다. 혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 304: Face recognition 얼굴 인식</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정 HoloLens에 주로 중점을 두고, 하는 동안 Windows Mixed Reality 몰입 형 (VR) 헤드셋을이 과정에서 배운 적용할 수 있습니다. 몰입 형 (VR) 헤드셋에 액세스할 수 있는 카메라 없기 때문에 PC에 연결 하는 외부 카메라를 해야 합니다. 과정을 따라가려면 정보 몰입 형 (VR) 헤드셋을 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.

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
- 카메라 (몰입 형 헤드셋 개발용) PC에 연결
- Face API 검색 및 Azure 설치에 대 한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
2.  설정 하 고 여 HoloLens를 테스트 합니다. 에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다. 
3.  (때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다. 

보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.

센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.

## <a name="chapter-1---the-azure-portal"></a>1 장-Azure Portal

사용 하는 *Face API* 서비스가 Azure에서 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.

1.  먼저에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다. 

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

2.  일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 *Face API*, 키를 눌러 **Enter**합니다.

    ![검색 api 얼굴](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.

3.  새 페이지에 대 한 설명을 제공 합니다는 *Face API* 서비스입니다. 선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.

    ![얼굴 api 정보](images/AzureLabs-Lab4-02.png)

4.  클릭 한 후 **만들기**:

    1. 이 서비스 인스턴스에 대해 원하는 이름을 입력 합니다.

    2. 구독을 선택 합니다.

    3. 첫 번째 경우, 적합 한 가격 책정 계층 선택 만들기 시간을 *Face API 서비스*, 무료 계층 (F0 라는)를 사용할 수 있어야 합니다.

    4. 선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지). 

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    5. UWP 앱 **Person Maker**, 위치에 대 한 ' 미국 서 부 '를 사용 해야는 나중에 사용 합니다.

    6. 이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.

    7. 선택 **만들기*합니다.** 

        ![만들 api 서비스를 직면 합니다.](images/AzureLabs-Lab4-03.png)

5.  클릭 한 후 **만들기*** 만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

6.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![서비스 만들기 알림](images/AzureLabs-Lab4-04.png)

7.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.

    ![리소스 알림으로 이동](images/AzureLabs-Lab4-05.png)

8.  준비 되 면 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.

    ![액세스 얼굴 api 키](images/AzureLabs-Lab4-06.png)

9.  이 자습서에서 응용 프로그램 서비스의 구독 '키'를 사용 하 여 수행 하는 서비스에 대 한 호출을 수행 해야 합니다. *빠른 시작* 페이지의 프로그램 *Face API* 서비스를 첫 번째 요소에 1, 번호는 *키 가져오기.*

10. 에 *서비스* 페이지 파란색을 선택 **키** 하이퍼링크 (빠른 시작 페이지의 경우) 또는 **키** 서비스 탐색 메뉴에서 링크 (가리키는 왼쪽에는 ' 키 ' 아이콘), 키를 표시 합니다.

    > [!NOTE] 
    > 키 중 하나를 기록해 나중에 필요 하므로, 보호 하며

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>2 장-' Person 작성자 ' UWP 응용 프로그램을 사용 하 여

라는 미리 작성 된 UWP 응용 프로그램을 다운로드 해야 [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)합니다. 이 앱은 단순한 이후 프로젝트는 의존 하는 Azure 항목을 만들 수 있도록 도구가이 과정에 대 한 최종 제품 없습니다.

**Person Maker** 사람 및 사용자 그룹을 사용 하 여 연결 된 Azure 항목을 만들 수 있습니다. 응용 프로그램 형식으로 다음 나중에 사용할 수는 FaceAPI 추가한 수신할 사용자의 얼굴 인식 하기 위해 필요한 모든 정보를 배치 됩니다. 

> [중요] **Person Maker** 일부 기본 제한이 사용 하 여 서비스 호출에 대 한 분당 횟수 초과 하지 않도록 하는 데는 **무료 구독 계층**합니다. 맨 위에 있는 녹색 텍스트 빨강으로 변경 하 고 조정이 발생 하는 경우 '활성'으로 업데이트 이 경우 (대기 다시 사용할 수 있습니다 하는 경우 업데이트 '에 활성 '으로, 얼굴 서비스에 액세스 하는 계속 다음 수까지) 응용 프로그램에 대 한 대기 합니다.

이 응용 프로그램을 사용 합니다 *Microsoft.ProjectOxford.Face* Face API의 사용 하 여 라이브러리를 활용할 수 있습니다. 이 라이브러리는 NuGet 패키지를 무료로 사용할 수 있습니다. 마찬가지로 및이 대 한 자세한 내용은 Api [API 참조 문서를 참조 하도록](https://docs.microsoft.com/azure/cognitive-services/face/apireference)합니다.

> [!NOTE] 
> 만 필요한 단계는 다음과 같습니다는 이러한 작업을 수행 하는 방법에 대 한 지침 문서를 추가 합니다. 합니다 **Person Maker** 앱 수 있습니다.
>
> - 만들기는 *Person Group*는 상호 연결 하려고 하는 여러 사용자 그룹 구성 됩니다. Azure 계정으로 여러 사용자 그룹을 호스트할 수 있습니다.
>
> - 만들기는 *Person*, 사용자 그룹의 멤버인입니다. 각 사용자의 개수가 *얼굴* 연결 된 이미지입니다.
>
> -  할당 *이미지에 직면* 에 *사용자*, Azure Face API 서비스가 인식할 수 있도록를 *Person* 해당 *얼굴*.
>
> -  *학습* 프로그램 *Azure API 서비스를 직면*합니다.

인식 되므로이 앱이 사용자를 인식 하도록 학습 하는 사용자 그룹에 추가 하려는 각 사용자의 10 개 확대 사진 해야 합니다. Windows 10 캠 앱에서는 이러한 도움이 됩니다. 각 사진 지우기 인지 확인 해야 합니다 (흐리게 표시, 가려지지, 또는 주체에서 멀리, 되 방지)를 더 이상 큰 이미지 파일 크기를 사용 하 여 사진을 jpg 또는 png 파일 형식에 **4MB**, 및 이상 **1KB**.

> [!NOTE]
> 이 자습서를 수행 하는 경우는 HoloLens를 넣으면 없습니다 살펴보면 직접 고유의 얼굴 학습용으로 사용 하지 마십시오. 동료 또는 동료 학생의 얼굴을 사용 합니다.

실행 중인 **Person Maker**:

1.  엽니다는 **PersonMaker** 폴더를 두 번 클릭 합니다 *PersonMaker 솔루션* 를 사용 하 여 엽니다 *Visual Studio*합니다.

2.  한 번 합니다 *PersonMaker 솔루션* 가 열려 있는지 확인 합니다.

    1. 합니다 *솔루션 구성* 로 설정 된 **디버그**합니다.

    2. 합니다 *솔루션 플랫폼* 로 설정 된 **x86**

    3. 합니다 *대상 플랫폼* 됩니다 **로컬 컴퓨터**합니다.

    4.  또한 해야 *NuGet 패키지 복원* (마우스 오른쪽 단추로 클릭 합니다 *솔루션* 선택한 **NuGet 패키지 복원**).

3.  클릭 *로컬 컴퓨터* 응용 프로그램이 시작 됩니다. 작은 화면에서 알고 있어야, 자세히 보려면를 스크롤할 수 있지만 모든 콘텐츠가 표시 되지 않을 수 있습니다.

    ![person 작성자 사용자 인터페이스](images/AzureLabs-Lab4-07.png)

4.  삽입 하 **Azure 인증 키**를 해야 하는에서 프로그램 *Face API* Azure 내에서 서비스 합니다.

5.  Insert의 경우:

    1. 합니다 *ID* 에 할당할 합니다 *Person Group*합니다. ID는 소문자, 공백 없이 이어야 합니다. Unity 프로젝트에서 나중에 필요한 수 만큼이이 ID를 기록해 둡니다.
    2. *이름을* 에 할당할 합니다 *Person Group* (공백이 있을 수 있음).


6.  키를 눌러 **사용자 그룹 만들기** 단추입니다. 단추 아래에 있는 확인 메시지가 표시 됩니다.

> [!NOTE]
> ' 액세스 거부 ' 오류를 사용 하는 경우 Azure 서비스에 대해 설정 된 위치를 확인 합니다. 위에서 설명한 대로이 앱은 ' 미국 서 부 '에 대 한 설계 되었습니다.

> [!IMPORTANT]
> 클릭할 수도 있습니다 있는지 확인할 수 있습니다 합니다 **알려진 그룹 인출** 단추: 이미 만든 경우 사용자 그룹 및 위시 새로 만들어야 하는 대신 사용 하기 위한 것입니다. 클릭할 경우 알고 있어야 *사용자 그룹을 만들* 알려진 그룹과이 또한 그룹 인출 합니다.

7.  삽입 합니다 *이름* 의 *Person* 만들려는 합니다.

    1. 클릭 합니다 **만들기 사용자** 단추입니다.

    2. 단추 아래에 있는 확인 메시지가 표시 됩니다.

    3. 이전에 만든 사용자를 삭제 하려는 경우, 키를 눌러 텍스트 상자에 이름을 작성할 수 있습니다 **사용자 삭제**

8.  10 개 그룹에 추가 하려는 사용자의 사진의 위치를 알고 있는지 확인 합니다.

9.  키를 눌러 **만들고 폴더 열기** 사람에 게 연결 된 폴더를 Windows 탐색기를 엽니다. 폴더에 10 개 이미지를 추가 합니다. 이러한 *JPG* 하거나 *PNG* 파일 형식입니다.

10. 클릭할 **Azure에 제출**합니다. 카운터 제출, 완료 되 면 메시지 뒤의 상태가 표시 됩니다.

11. 카운터 완료 된 후 확인 메시지가 표시 되어 클릭할 **학습** 서비스를 학습 합니다.

프로세스가 완료 되 면 Unity로 이동할 수 있습니다.

## <a name="chapter-3---set-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 *Unity* 누릅니다 **새로 만들기**합니다. 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab4-08.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. 삽입 **MR_FaceRecognition**합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**합니다. 설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab4-09.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집 > 기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab4-10.png)

4.  이동한 다음 **파일 > 빌드 설정** 플랫폼 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환** 단추입니다.

    ![빌드 설정 창, uwp 플랫폼 전환 합니다.](images/AzureLabs-Lab4-11.png)

5.  로 이동 **파일 > 빌드 설정** 되어 있는지 확인 합니다.

    1. **장치를 대상** 로 설정 된 **HoloLens**

        > 몰입 형 헤드셋, 설정 **대상 장치** 하 *모든 장치*합니다.

    2. **빌드 형식** 로 설정 된 **D3D**
    3. **SDK** 로 설정 된 **가장 최근에 설치 된**
    4. **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**
    5. **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**
    6. 장면 저장 하 고 빌드에 추가 합니다. 

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.

            ![추가 백그라운드에서 열기 단추를 클릭](images/AzureLabs-Lab4-12.png)

        2. 선택 된 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**.

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab4-13.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 **파일 이름**: 텍스트 필드에 입력 **FaceRecScene**, 키를 누릅니다 **저장**합니다.

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab4-14.png)

    7. 설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.

6. 에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한. 

    ![플레이어 설정 열기](images/AzureLabs-Lab4-15.png)

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. 에 **기타 설정** 탭:

        1. **스크립팅** **런타임 버전이** 있어야 **실험적** (.NET 4.6 동등). 이 변경 트리거할 편집기를 다시 시작 해야 합니다.
        2. **백 엔드를 스크립팅** 있어야 **.NET**
        3. **API 호환성 수준** 있어야 **.NET 4.6**

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab4-16.png)
      
    2. 내 합니다 **게시 설정** 탭의 **기능**, 확인:

        - **InternetClient**
        - **웹캠**

            ![게시 설정을 업데이트 합니다.](images/AzureLabs-Lab4-17.png)

    3. 패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab4-18.png)

8.  년대 *빌드 설정*를 **Unity C# 프로젝트** 가 더 이상 회색;이 옆의 확인란을 선택 합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).

## <a name="chapter-4---main-camera-setup"></a>4 장-주 카메라 설정

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드에 바로 계속, 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage),으로 프로젝트로 가져오는 것을 [사용자 지정 패키지](https://docs.unity3d.com/Manual/AssetPackages.html)합니다. 이 패키지의 가져오기를 포함 하는 주의 합니다 *Newtonsoft DLL*에서 다루고 [5 장](#chapter-5--import-the-newtonsoft.json-library)합니다. 따라서 가져온에서 계속할 수 있습니다 [Chapter 6](#chapter-6-create-the-faceanalysis-class)합니다.

1.  에 *계층 구조* 패널을 선택 합니다 **주 카메라**합니다.

2.  선택한 후에의 모든 구성 요소를 볼 수는 합니다 **주 카메라** 에 *검사기 패널*합니다.

    1. 합니다 **카메라 개체** 이름은 **주 카메라** (맞춤법 참고!)

    2. 주 카메라 **태그** 으로 설정 되어 있어야 **MainCamera** (맞춤법 참고!)

    3. 있는지 확인 합니다 **변환 위치** 로 설정 된 **0, 0, 0**

    4. 설정할 **플래그 지우기** 에 **단색**

    5. 설정 된 **백그라운드** 카메라 구성 요소의 색 **검정, 알파 0 (코드를 16 진수: #00000000)**

        ![카메라 구성 요소 설정](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>5 장-Newtonsoft.Json 라이브러리 가져오기

> [!IMPORTANT]
> '.Unitypackage'에서 가져온 경우는 [장의 마지막](#chapter-4--main-camera-setup),이 챕터를 건너뛸 수 있습니다.

봇 서비스에 보내고 받은 개체를 serialize 및 deserialize 하는 데 다운로드 해야 합니다 *Newtonsoft.Json* 라이브러리입니다. 호환 되는이 잘못 Unity 폴더 구조를 사용 하 여 이미 구성 된 버전을 찾을 수 있습니다 [Unity 패키지 파일](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)합니다. 

라이브러리를 가져오려면:

1.  Unity 패키지를 다운로드 합니다.
2.  클릭할 **자산**를 **패키지를 가져올**를 **사용자 지정 패키지**합니다.

    ![Newtonsoft.Json 라이브러리 가져오기](images/AzureLabs-Lab4-20.png)

3.  Unity 패키지를 다운로드 한 살펴보고 열기를 클릭 합니다.
4.  패키지의 모든 구성 요소는 선택 및 클릭 했는지 **가져오기**합니다.

    ![Newtonsoft.Json 라이브러리 가져오기](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>-6 장 FaceAnalysis 클래스 만들기

FaceAnalysis 클래스의 목적은 Azure 얼굴 인식 서비스와 통신 하는 데 필요한 메서드를 호스트 하는 것입니다. 

- 서비스 캡처 이미지를 보내면 해당 분석 및 내에서 얼굴 식별 하 고 알려진된 사람에 게 속해 있는 경우를 결정 합니다. 
- 알려진된 사용자가 있으면이 클래스는 이름과 UI 텍스트에 장면으로 표시 됩니다.

만들려는 합니다 *FaceAnalysis* 클래스:

 1. 마우스 오른쪽 단추로 클릭 합니다 *Assets 폴더* 클릭 한 다음 [프로젝트] 패널에 **Create** > **폴더**합니다. 폴더를 호출 **스크립트**합니다. 

    ![FaceAnalysis 클래스를 만듭니다.](images/AzureLabs-Lab4-22.png)

2.  열려는 방금 만든 폴더를 두 번 클릭 합니다. 
3.  폴더를 마우스 오른쪽 단추로 클릭 **Create**  >   **C# 스크립트**. 스크립트를 호출할 *FaceAnalysis*합니다. 
4.  두 번 클릭 하 여 새 *FaceAnalysis* 스크립트를 Visual Studio 2017을 사용 하 여 엽니다.
5.  위의 다음 네임 스페이스를 입력 합니다 *FaceAnalysis* 클래스:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  이제 모든 deserialising에 사용 되는 개체를 추가 해야 합니다. 이러한 개체를 추가 해야 합니다. **외부** 의 합니다 *FaceAnalysis* 스크립트 (아래에 중괄호 아래). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. 합니다 *start ()* 하 고 *update ()* 메서드를 사용 하지 것입니다, 되므로 지금 삭제 합니다. 

8.  내 합니다 *FaceAnalysis* 클래스를 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > 대체는 **키** 하며 **personGroupId** 서비스 키와 이전에 만든 그룹의 Id입니다.

9.  추가 합니다 *Awake()* initialises 클래스, 메서드를 추가 합니다 *ImageCapture* 주 카메라 클래스 레이블을 만드는 메서드를 호출 하:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. 추가 된 *CreateLabel()* 메서드를 *레이블* 분석 결과 표시 하는 개체:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. 추가 된 *DetectFacesFromImage()* 하 고 *GetImageAsByteArray()* 메서드. 전자는 후자는 캡처된 이미지를 바이트 배열로 변환 하는 데 필요한 모든 가능한 얼굴 제출 된 이미지를 검색 하는 얼굴 인식 서비스를 요청 합니다.

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. 추가 *IdentifyFaces()* 메서드를 요청 합니다 *얼굴 인식 서비스* 제출 된 이미지에 이전에 검색 된 모든 알려진된 얼굴을 식별 하 합니다. 요청은 이름이 아니라 식별된 하는 사용자의 id를 반환 합니다.

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. 추가 된 *GetPerson()* 메서드. 사용자 id,이 메서드 다음에 대 한 요청 함으로써 합니다 *얼굴 인식 서비스* 식별 된 사용자의 이름을 반환 하려면:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  해야 **저장할** Unity 편집기로 다시 이동 하기 전에 변경 합니다.
15.  Unity 편집기에서 프로젝트 패널의 스크립트 폴더에서 FaceAnalysis 스크립트에서 주 카메라 개체를 끌어 합니다 *계층 패널*합니다. 새 스크립트 구성 요소 이므로 주 카메라에 추가 됩니다. 

![FaceAnalysis 주 카메라를 배치 합니다.](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>7-장 ImageCapture 클래스 만들기

용도 *ImageCapture* 클래스와 통신 하는 데 필요한 메서드를 호스트 하는 프로그램 *Azure 얼굴 인식 서비스* 에서 얼굴 식별을 캡처할 이미지를 분석 하 및 알려진된 사람에 게 속하는지 확인 합니다. 알려진된 사용자가 있으면이 클래스는 이름과 UI 텍스트에 장면으로 표시 됩니다.

만들려는 합니다 *ImageCapture* 클래스:
 
1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 이전에 만든 다음 클릭 **만들기**를  **C# 스크립트**. 스크립트를 호출할 *ImageCapture*합니다. 
2.  두 번 클릭 하 여 새 *ImageCapture* 스크립트를 Visual Studio 2017을 사용 하 여 엽니다.
3.  ImageCapture 클래스 위에 다음 네임 스페이스를 입력 합니다.

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  내 합니다 *ImageCapture* 클래스를 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  추가 된 *Awake()* 하 고 *start ()* 클래스를 초기화 하 고 사용자 제스처를 캡처하려면 HoloLens를 허용 하는 데 필요한 메서드:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  추가 된 *TapHandler()* 사용자가 수행할 때 호출 되는 *누릅니다* 제스처:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  추가 된 *ExecuteImageCaptureAndAnalysis()* 의 이미지 캡처 프로세스를 시작 하는 메서드:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  사진 캡처 프로세스가 완료 될 때 호출 되는 처리기를 추가 합니다.

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. 해야 **저장할** Unity 편집기로 다시 이동 하기 전에 변경 합니다.

## <a name="chapter-8---building-the-solution"></a>8 장-솔루션 구축

응용 프로그램의 철저 한 테스트를 수행 하려면 해야 테스트용으로 로드 하 여 HoloLens에 있습니다.

를 수행 하기 전에 확인 합니다.

-   3 장에서 언급 한 모든 설정은 올바르게 설정 됩니다. 
-   스크립트 *FaceAnalysis* 주 카메라 개체에 연결 됩니다. 
-   모두를 **인증 키** 하 고 **그룹 Id** 내에서 설정한 합니다 *FaceAnalysis* 스크립트.

이 안내는 솔루션을 빌드할 준비가 되었습니다. 솔루션을 빌드한 후에 응용 프로그램을 배포할 준비가 됩니다.

빌드 프로세스를 시작 합니다.

1.  현재 장면 파일 저장을 클릭 하 여 저장 합니다.
2.  파일, 빌드 설정으로 이동 열기 백그라운드에서 추가 클릭 합니다.
3.  눈금 Unity 해야 C# 프로젝트입니다.

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab4-24.png)

4.  빌드를 누릅니다. 이렇게 하면 Unity를 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 하는 파일 탐색기 창의 시작 됩니다. 이제 Unity 프로젝트 내에서 해당 폴더를 만들기 및 앱을 호출 합니다. 다음 앱 폴더를 선택한 상태에서 폴더 선택 키를 누릅니다. 
5.  Unity는 프로젝트를 빌드할 앱 폴더에 시작 됩니다. 
6.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 빌드 위치에서 파일 탐색기 창이 열립니다.

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab4-25.png)

7.  앱 폴더를 엽니다 연 다음 새 프로젝트 솔루션 (처럼 위의 MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>9 장-응용 프로그램 배포

HoloLens에 배포 합니다.

1.  (배포에 대 한 원격), 여 HoloLens의 IP 주소를 사용 해야 하 고 중인에 HoloLens 되도록 **개발자 모드**합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1. 에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.
    2. 로 **네트워크 및 인터넷 > Wi-fi > 고급 옵션**
    3. 참고 합니다 **IPv4** 주소입니다.
    4. 다음으로 다시 이동할 **설정을**, 다음 **업데이트 및 보안 > 개발자 용** 
    5. 개발자 모드를 설정 합니다.

2.  새 Unity 빌드에 이동 (합니다 *앱* 폴더) 사용 하 여 솔루션 파일을 엽니다 *Visual Studio*합니다.
3.  솔루션 구성 선택에서 **디버그**합니다.
4.  솔루션 플랫폼에서 선택 **x86**하십시오 **원격 컴퓨터**합니다. 

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab4-26.png)
 
5.  로 이동 합니다 **빌드 메뉴** 클릭 **솔루션 배포**, 응용 프로그램에 HoloLens 테스트용으로 로드 하려면.
6.  앱에 HoloLens 시작할 준비가에 설치 된 앱 목록에 나타나야 합니다.

> [!NOTE]
> 몰입 형 헤드셋을 배포 하려면 설정 합니다 **솔루션 플랫폼** 를 *로컬 컴퓨터*, 설정 및를 **구성** 에 *디버그*, 를사용하여*x86* 으로 **플랫폼**합니다. 로컬 배포 후 컴퓨터를 사용 하 여는 **빌드 메뉴**을 선택 하면 *솔루션 배포*합니다. 


## <a name="chapter-10---using-the-application"></a>10 장-응용 프로그램을 사용 하 여

1.  착용 하는 HoloLens, 앱을 시작 합니다.
2.  등록 된 사용자 확인 합니다 *Face API*합니다. 다음 사항을 확인하세요.

    -  개인의 얼굴 되어 있지 않고 너무 멀리 떨어진 명확 하 게 표시
    -  환경 조명 너무 어두운 아닙니다.

3.  탭 제스처를 사용 하 여 사용자의 그림을 캡처합니다.
4.  응용 프로그램에서 분석 요청을 보내고 응답을 수신 될 때까지 기다립니다.
5.  사용자가 성공적으로 인식 하는 경우 사용자의 이름을 UI 텍스트로 표시 됩니다.
6.  몇 초 마다 탭 제스처를 사용 하는 캡처 프로세스를 반복할 수 있습니다.

## <a name="your-finished-azure-face-api-application"></a>완성 된 Azure Face API 응용 프로그램

축, 이미지 내에서 얼굴을 감지 하 여 알려진된 모든 얼굴 식별 Azure Face recognition 얼굴 인식 서비스를 활용 하는 혼합된 현실 앱을 작성 합니다.

![이 과정을 완료 하는 결과](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

합니다 **Azure의 Face API** 단일 이미지에서 최대 64 개의 얼굴을 감지 만큼 충분히 강력 합니다. 많은 사람들이 간에 두세 개의 얼굴을 인식할 수 있도록 응용 프로그램을 확장 합니다.

### <a name="exercise-2"></a>연습 2

합니다 **Azure의 Face API** 모든 종류의 특성 정보를 제공할 수 이기도 합니다. 응용 프로그램에이 통합 합니다. 함께 사용 하면 훨씬 더 흥미로운 수는 [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)합니다.
