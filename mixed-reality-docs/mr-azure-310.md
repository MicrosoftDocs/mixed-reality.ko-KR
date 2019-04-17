---
title: MR 및 Azure 310-개체 검색
description: 기계 학습 모델을 학습 하는 방법을 알아보려면이 과정을 완료 하 고 유사한 개체와 혼합된 현실 응용 프로그램 내에서 실제 위치를 인식 하도록 학습된 된 모델을 사용 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure에서 사용자 지정 시각 검색, 혼합 현실, academy, unity, 자습서, api, hololens 개체
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597650"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-and-azure-310-object-detection"></a>Mr 및 Azure 310: 개체 검색

이 과정에서는 배웁니다 사용자 지정 시각적 콘텐츠 및 제공 된 이미지 내의 공간 위치를 인식 하는 방법을 Azure Custom Vision을 사용 하 여 혼합된 현실 응용 프로그램에서 "개체 검색" 기능입니다.

이 서비스를 사용 하면 개체 이미지를 사용 하 여 기계 학습 모델을 학습할 수 있습니다. 그런 다음 학습 된 모델은 유사한 개체를 인식 하 고 실제 환경에서의 위치를 Microsoft HoloLens 카메라 캡처에 의해 제공 또는 사용 카메라 몰입 형 (VR) 헤드셋에 대 한 PC에 연결 합니다.

![과정 결과](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision, 개체 감지** 개발자는 사용자 지정 이미지 분류자를 만들 수 있는 Microsoft 서비스 됩니다. 이러한 분류자 사용할 수 있습니다 새 이미지를 사용 하 여 제공 하 여 해당 새 이미지 내의 개체를 검색할 **경계 상자** 이미지 자체 내에서. 서비스는이 프로세스를 간소화 하는 간단 하 고, 사용 하기 쉬운 온라인 포털을 제공 합니다. 자세한 내용은 다음 링크를 방문 합니다.

* [Azure Custom Vision 페이지](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [제한 및 할당량](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

이 과정을 완료 하면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 응용 프로그램을 갖게 됩니다.

1. 사용자 수 *gaze* Azure Custom Vision Service, 개체 감지를 사용 하 여 학습 하는 개체입니다. 
2. 사용자가 사용할 합니다 *탭* 제스처에서 찾고 있는 항목의 이미지를 캡처합니다.
3. 앱에서 Azure Custom Vision Service에 이미지를 전송 됩니다.
4. 세계 좌표 공간 텍스트로 인식 결과 표시 하는 서비스에서 회신이 됩니다. Microsoft HoloLens ' 공간 추적을 인식할 수 있는 개체의 세계 좌표 위치를 이해 하 고 사용 하는 방법으로 활용 하 여을 통해이 작업을 수행할 수는 합니다 *태그* 어떤에서 발견 되는 이미지를 사용 하 여 연결 레이블 텍스트를 제공 합니다.

과정에 대해서도 다루는 수동으로 업로드 이미지에 태그를 만들기 및 학습 다른 인식 하는 서비스 개체 (제공 된 예제는 cup), 여 설정 합니다 *경계 상자의* 제출한 이미지 내에서. 

> [!IMPORTANT]
> 생성 및 사용 하 여 앱의 다음 개발자는 Azure Custom Vision Service를 다시 탐색 식별 서비스에 대 한 예측 하 고 있었는지 여부를 결정할는 올바른 여부 (아무 것도 서비스 태그를 통해 누락 및 조정 된 *경계 상자*). 서비스 수 다음 다시 학습 해야, 실제 개체 인식 가능성 늘어납니다.

이 과정을 샘플 Unity 기반 응용 프로그램에 Azure Custom Vision Service, 개체 검색에서에서 결과 가져오는 방법을 배우게 됩니다. 사용자 지정 응용 프로그램을 작성 하려는 경우에 이러한 개념을 적용 하는 것이 됩니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 310: 개체 검색</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다. 또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다. 내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.

다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.

- PC 개발
- [Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [최신 Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) 개발자 모드를 설정 하 여
- Azure 설정 및 Custom Vision Service 검색에 대 한 인터넷 액세스
-  일련의 적어도 15 개의 이미지는 필요한)를 인식 하는 사용자 지정 비전 원하는 각 개체에 대 한 합니다. 원하는,이 과정을 통해 이미 제공 되는 이미지를 사용할 수 있습니다 [cup 일련](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
2.  설정 하 고 여 HoloLens를 테스트 합니다. 에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다. 
3.  (때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다. 

보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.

센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.

## <a name="chapter-1---the-custom-vision-portal"></a>1 장-사용자 지정 비전 포털

사용 하 여 **Azure Custom Vision Service**, 응용 프로그램에 사용할 수 있도록 해당 인스턴스를 구성 해야 합니다.

1.  탐색할 [에 **Custom Vision Service** 기본 페이지](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)합니다.

2.  클릭할 **Getting Started**합니다.

    ![](images/AzureLabs-Lab310-01.png)

3.  사용자 지정 비전 포털에 로그인 합니다.

    ![](images/AzureLabs-Lab310-02.png)

4.  Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

5.  처음으로 로그인 한 후 메시지가 표시 됩니다와 합니다 *서비스 약관* 패널입니다. 확인란을 클릭 *약관에 동의*합니다. 누른 **동의 함**합니다.

    ![](images/AzureLabs-Lab310-03.png)

6.  조건에 동의 하지, 현재 위치는 합니다 *내 프로젝트* 섹션입니다. 클릭할 **새 프로젝트**합니다.

    ![](images/AzureLabs-Lab310-04.png)

7.  탭은 프로젝트의 일부 필드를 지정 하 라는 메시지가 표시 됩니다는 오른쪽에 표시 됩니다.

    1.  프로젝트 이름을 삽입 합니다.

    2.  프로젝트에 대 한 설명을 삽입 (**선택 사항**)

    3.  선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 교육 과정)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > 하려는 경우 [자세한 Azure 리소스 그룹에 대 한 연결된 Docs로 이동](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  설정 된 **프로젝트 형식** 으로 **개체 감지 (미리 보기)** 합니다.

8.  완료 되 면 클릭할 **프로젝트 만들기**, 및 Custom Vision Service 프로젝트 페이지로 리디렉션됩니다.


## <a name="chapter-2---training-your-custom-vision-project"></a>2 장-프로젝트에 사용자 지정 비전 교육

한 번 사용자 지정 비전 포털의 기본 목표가 방법은 학습 이미지에서 특정 개체를 인식 하 여 프로젝트입니다.

원하는 응용 프로그램을 인식 하는 각 개체에 대해 적어도 15 개의 이미지를 해야 합니다. 이 과정을 통해 제공 되는 이미지를 사용할 수 있습니다 ([cup 일련](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Custom Vision 프로젝트를 학습 합니다.

1.  클릭 합니다 **+** 옆에 단추 **태그**합니다.

    ![](images/AzureLabs-Lab310-06.png)

2.  추가 된 **이름을** 사용 하 여 이미지를 연결 하는 데 사용할 수 있는 태그입니다. Cup 이미지 인식,이 대 한 태그는 명명 된 하므로 사용 하는 것이 예제의 **Cup**합니다. 클릭 **저장할** 한 번 완료 합니다.

    ![](images/AzureLabs-Lab310-07.png)

3.  알 수 있습니다 하 **태그** 추가 되었습니다 (표시에 대 한 페이지를 다시 로드 해야 할). 

    ![](images/AzureLabs-Lab310-08.png)

4.  클릭할 **이미지 추가** 페이지의 가운데에 있습니다.

    ![](images/AzureLabs-Lab310-09.png)

5.  클릭할 **로컬 파일 찾아보기**, 하나의 개체에 대 한 15 최소 되 고 사용 하 여 (15) 업로드 하려는 이미지를 이동 합니다.

    > [!TIP]
    >  업로드 한 번에 여러 이미지를 선택할 수 있습니다.

    ![](images/AzureLabs-Lab310-10.png)

6.  키를 눌러 **파일 업로드** 사용 하 여 프로젝트를 학습 하려는 모든 이미지를 선택 합니다. 파일 업로드를 시작 합니다. 업로드 확인 했으면 클릭 **수행**합니다.

    ![](images/AzureLabs-Lab310-11.png)

7.  이 시점에서 이미지 업로드 되지만 태그가 지정 되지 됩니다.

    ![](images/AzureLabs-Lab310-12.png)

8.  이미지에 태그를 추가 하 여 마우스를 사용 합니다. 이미지를 가리키면 강조 표시 선택 영역이 때문에 개체 주위에 선택 영역을 자동으로 그려 도움이 됩니다. 정확 하지 않으면 고유한 그릴 수 있습니다. 이렇게 하려면 개체를 포함 하도록 선택 영역을 끌어서 마우스 왼쪽 단추 클릭 마우스의 보유 합니다. 

    ![](images/AzureLabs-Lab310-13.png) 

9. 선택 된 이미지 내의 개체의 다음 작은 프롬프트 수 묻습니다 *Region 태그 추가*합니다. 이전에 만든된 태그 ('Cup'를 위 예제의)를 선택 하거나 더 많은 태그를 추가 하는 경우에 입력 하 고 클릭 합니다 **+ (더하기)** 단추입니다.

    ![](images/AzureLabs-Lab310-14.png) 

10. 다음 이미지에 태그를 추가 하는 블레이드의 오른쪽 화살표를 클릭 하거나 태그 블레이드를 닫을 수 있습니다 (클릭 하 여 합니다 **X** 블레이드의 오른쪽 위 모서리에서) 다음 이미지를 클릭 하 고 있습니다. 준비 된 다음 이미지를 만든 후에 동일한 절차를 반복 합니다. 모든 이미지를 업로드 하면 모든 태그가 지정 됩니다 될 때까지이 작업을 수행 합니다. 

    > [!NOTE]
    >  아래 이미지와 같이 동일한 이미지에서 여러 개체를 선택할 수 있습니다. 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. 모든 태그가 지정를 클릭 합니다 **태그가 지정 된** 태그가 지정 된 이미지를 표시 하려면 화면 왼쪽의 단추입니다. 

    ![](images/AzureLabs-Lab310-16.png)

12. 이제 서비스를 학습 준비가 되었습니다. 클릭 합니다 **학습** 단추 및 첫 번째 학습 반복이 시작 됩니다.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. 을 작성 하는 라는 두 개의 단추를 볼 수는 **기본값으로** 하 고 **예측 URL**합니다. 클릭할 **기본값으로** 첫째, 클릭 **예측 URL**합니다.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > 이 제공 되는 끝점 중로 설정 되어 *반복* 기본으로 표시 되었습니다. 따라서 새를 나중에 확인 하는 경우 *반복* 기본값으로 업데이트, 코드를 변경 해야 합니다.

14. 클릭 한 후 **예측 URL**오픈 *메모장*, 복사 및 붙여넣기를 **URL** (라고도 하 **예측 끝점**) 하며 **서비스 예측 키**코드에서 나중에 필요할 때 검색할 수 있도록 합니다.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 **Unity** 누릅니다 **새로 만들기**합니다.

    ![](images/AzureLabs-Lab310-21.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. 삽입 **CustomVisionObjDetection**합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**를 설정 합니다 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록 더). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![](images/AzureLabs-Lab310-22.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집할* > *기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![](images/AzureLabs-Lab310-23.png)

4.  이동한 다음 **파일 > 빌드 설정** 전환 합니다 **플랫폼** 에 *유니버설 Windows 플랫폼*, 클릭는 **플랫폼 전환** 단추입니다.

    ![](images/AzureLabs-Lab310-24.png)

5.  동일한 **빌드 설정** 창에서 다음 설정 되어 있는지 확인 합니다.

    1.  **장치를 대상** 로 설정 된 **HoloLens**        
    2.  **빌드 형식** 로 설정 된 **D3D**
    3.  **SDK** 로 설정 된 **가장 최근에 설치 된**
    4.  **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**
    5.  **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**            
    6.  설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.

        ![](images/AzureLabs-Lab310-25.png)

6.  동일한 **빌드 설정** 창을 합니다 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 **검사기** 위치한.

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  에 **기타 설정** 탭:

        1.  **스크립팅 런타임 버전** 있어야 **실험적** (.NET 4.6 동등), 편집기를 다시 시작 해야를 트리거하는 합니다.

        2. **백 엔드를 스크립팅** 있어야 **.NET**합니다.

        3. **API 호환성 수준** 있어야 **.NET 4.6**합니다.

            ![](images/AzureLabs-Lab310-26.png)

    2.  내 합니다 **게시 설정** 탭의 **기능**, 확인:

        1. **InternetClient**

        2.  **웹캠**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **지원 되는 가상 현실**, 있는지 확인 합니다는 **Windows 혼합 실제로 SDK** 추가 됩니다.

        ![](images/AzureLabs-Lab310-29.png)

8.  년대 **빌드 설정**를 *Unity C\# 프로젝트* 를 더 이상 사용할 수 없습니다:이 옆의 확인란을 선택 합니다.

9.  닫기 합니다 **빌드 설정** 창입니다.

10. 에 **편집기**, 클릭 **편집** > **프로젝트 설정** > **그래픽**합니다.

    ![](images/AzureLabs-Lab310-30.png)

11. 에 **검사기 패널** 는 *그래픽 설정* 열립니다. 라는 배열을 표시 될 때까지 아래로 스크롤하여 **셰이더를 항상 포함**합니다. 늘려 슬롯을 추가 합니다 **크기** 씩 변수 (이 예제에서는 8 인 았 어 있으므로 9). 새 슬롯이 나타납니다 배열의 마지막 위치에 아래와 같이:

    ![](images/AzureLabs-Lab310-31.png)

12. 슬롯에서 슬롯 셰이더 목록을 열려면 옆의 작은 대상 원을 클릭 합니다. 검색할 합니다 **레거시 셰이더/Transparent/확산** 셰이더 두 번 클릭 합니다. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>4 장-CustomVisionObjDetection Unity 패키지 가져오기

Unity 자산 패키지와 함께 제공 되는이 과정 이라는 **Azure-MR-310.unitypackage**합니다. 

> [팁] 전체 작업을 포함 하 여 Unity에서 지 원하는 모든 개체에 패키징할 수 있습니다는 **.unitypackage** 파일 및 내보낸 / 다른 프로젝트에서 가져온입니다. 서로 다른 자산을 이동할, 가장 안전 하 고 가장 효율적인 방법입니다 **Unity 프로젝트**합니다.

찾을 수 있습니다 합니다 [여기에서 다운로드 해야 하는 Azure-MR-310 패키지](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)합니다.

1.  사용자 앞에 Unity 대시보드를 클릭 **자산** 화면의 맨 위에 있는 메뉴에서 클릭 **가져오기 패키지 > 사용자 지정 패키지**합니다.

    ![](images/AzureLabs-Lab310-33.png)

2.  파일 선택기를 사용 하 여 선택 하는 **Azure-MR-310.unitypackage** 패키징하고 클릭 **열기**합니다. 이 자산에 대 한 구성 요소 목록에 나타납니다. 가져오기를 클릭 하 여 확인 합니다 **가져올** 단추입니다.

    ![](images/AzureLabs-Lab310-34.png)

3.  가져오기 완료 되 고, 패키지에서 폴더를 추가 이제가 확인할 수 있습니다 하 **자산** 폴더입니다. 이 종류의 폴더 구조는 Unity 프로젝트에 대 한 일반적인입니다.

    ![](images/AzureLabs-Lab310-35.png)

    1.  합니다 **자료** 폴더에서 사용 하는 자료를 포함 합니다 **Gaze 커서**합니다. 

    2.  합니다 **플러그 인** 폴더 코드에서 서비스 웹 응답을 deserialize 하는 데 사용 되는 Newtonsoft DLL이 포함 됩니다. 폴더 및 하위 폴더에 포함 된 2 개의 서로 다른 버전은 사용 되 고 Unity 편집기와 UWP 빌드에서 빌드된 라이브러리를 허용 하는 데 필요한입니다. 

    3.  합니다 **Prefabs** 장면에 포함 된 prefabs 폴더에 있습니다. 다음과 같습니다.

        1.  합니다 **GazeCursor**, 응용 프로그램에 사용 되는 커서입니다. 실제 개체 위에 장면에 배치할 수 있게 되기를 SpatialMapping prefab 함께 작동 합니다.
        2.  합니다 **레이블**, 개체인 UI 필요한 경우 장면에서 object 태그를 표시 하는 데 사용 합니다.
        3.  합니다 **SpatialMapping**를 사용 하도록 응용 프로그램을 활성화 하는 개체 공간 Microsoft HoloLens 추적을 사용 하 여 가상 맵을 만듭니다.

    4.  합니다 **장면** 현재이 과정에 대 한 미리 작성된 된 장면을 포함 하는 폴더입니다.

4.  열기를 **장면** 폴더에서는 **프로젝트 패널**, 두 번 클릭 하 고는 **ObjDetectionScene**,이 과정에 대해 사용할 장면을 로드 하 합니다.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **포함 된 코드가 없습니다**,이 과정을 수행 하 여 코드를 작성 합니다.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>-5 장 CustomVisionAnalyser 클래스를 만듭니다.

이 시점에서 일부 코드를 작성할 준비가 되었습니다. 사용 하 여 시작 합니다 **CustomVisionAnalyser** 클래스입니다.

> [!NOTE]
> 에 대 한 호출을 **Custom Vision Service**아래에 표시 된 코드에서,를 사용 하 여는 **사용자 지정 비전 REST API**합니다. 이 사용 하 여을 통해 구현 (비슷한을 직접 구현 하는 방법을 이해 하는 데 유용함)이이 API를 사용 하는 방법을 표시 됩니다. 인식 하며 Microsoft 제공 하는 수를 **Custom Vision SDK** 서비스를 호출 하기 위해 사용할 수도 있는 합니다. 자세한 내용은 참조는 [Custom Vision SDK 문서](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)합니다.

이 클래스는 담당 합니다.

- 캡처된 바이트의 배열로 최신 이미지를 로드 합니다.

- Azure는 바이트 배열 보내기 **Custom Vision Service** 분석에 대 한 인스턴스.

- JSON 문자열로 응답을 수신 합니다.

- 응답을 역직렬화 하 고 결과 전달 **예측** 에 **SceneOrganiser** 응답을 표시 하는 방법을 처리 하는 클래스입니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **자산 폴더**에 있는 합니다 **프로젝트 패널**, 클릭 **만들기** > **폴더**합니다. 폴더를 호출 **스크립트**합니다.

    ![](images/AzureLabs-Lab310-37.png)

2.  새로 만든된 폴더를 두 번 클릭 합니다.

3.  폴더를 마우스 오른쪽 단추로 클릭 **Create** > **C\# 스크립트**합니다. 스크립트 이름을 **CustomVisionAnalyser 합니다.**

4.  새 두 번 클릭 **CustomVisionAnalyser** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**

5.  파일의 맨 위에서 참조 하는 다음 네임 스페이스가 있는지 확인 합니다.

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  에 **CustomVisionAnalyser** 클래스를 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 삽입 해야 하 **서비스 예측 키** 에 **predictionKey** 변수 및 **예측 끝점** 에 **predictionEndpoint**  변수입니다. 에 복사해 둔 [메모장 이전, Chapter 2 단계에서 14](#chapter-2---training-your-custom-vision-project)합니다.

7.  에 대 한 코드 **Awake()** 이제 인스턴스 변수를 초기화 하려면 추가 해야 합니다.

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  추가 코 루틴 (정적을 사용 하 여 **GetImageAsByteArray()** 아래 메서드)에서 캡처된 이미지의 분석 결과 얻을 합니다 **ImageCapture** 클래스.

    > [!NOTE]
    > 에 **AnalyseImageCapture** 코 루틴을 호출 하는 **SceneOrganiser** 만들려면 아직 수 있는 클래스. 따라서 **이러한 지금은 줄 주석**합니다.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. 삭제를 **start ()** 하 고 **update ()** 메서드를 사용 되지 것입니다. 

10.  변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.

> [!IMPORTANT]
> 앞에서 설명한 대로 수행 걱정할 필요 없이 코드를 제공 하는 경우는 더욱 클래스는 곧 해결 됩니다에서 오류가 나타날 수 있습니다.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>-6 장 CustomVisionObjects 클래스 만들기

만든 클래스에서 이제는 합니다 **CustomVisionObjects** 클래스입니다.

이 스크립트는 다른 클래스를 직렬화 및 역직렬화 Custom Vision Service에 대 한 호출에 사용 되는 개체의 수를 포함 합니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다. 스크립트를 호출 합니다 **CustomVisionObjects 합니다.**

2.  새 두 번 클릭 **CustomVisionObjects** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**

3.  파일의 맨 위에서 참조 하는 다음 네임 스페이스가 있는지 확인 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  삭제를 **start ()** 및 **update ()** 내부 메서드를 **CustomVisionObjects** 클래스,이 클래스는 이제 비워둘 수 있습니다.

    > [!WARNING]
    > 신중 하 게 다음 지침을 따르는 것입니다. 새 클래스 선언 안에 넣으면 합니다 **CustomVisionObjects** 클래스 컴파일 오류가 발생 합니다 [10 장](#chapter-10---create-the-imagecapture-class)않는다는, 하는 **AnalysisRootObject** 및  **BoundingBox** 찾을 수 없습니다.

5.  다음 클래스를 추가 *외부* 는 **CustomVisionObjects** 클래스입니다. 사용 되는 이러한 개체는 **Newtonsoft** 응답 데이터 serialize 및 deserialize 하는 라이브러리:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.

## <a name="chapter-7---create-the-spatialmapping-class"></a>7-장 SpatialMapping 클래스 만들기

이 클래스는 설정 된 **공간 매핑 Collider** 가상 개체와 실제 개체 간의 충돌을 감지할 수 있으므로 장면에 있습니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다. 스크립트를 호출 합니다 **SpatialMapping 합니다.**

2.  새 두 번 클릭 **SpatialMapping** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**

3.  위에서 참조 된 다음 네임 스페이스가 있는지 확인 합니다 **SpatialMapping** 클래스:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  그런 다음 내에서 다음 변수를 추가 합니다 **SpatialMapping** 위의 클래스는 **start ()** 메서드:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  추가 된 **Awake()** 하 고 **start ()**:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  삭제 된 **update ()** 메서드.

7.  변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.


## <a name="chapter-8---create-the-gazecursor-class"></a>8-장 GazeCursor 클래스 만들기

이 클래스는 실제 공간에서 올바른 위치에 커서를 설정 하는 일을 담당 만들어 사용 합니다 **SpatialMappingCollider**이전 장에서 생성 합니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다. 스크립트를 호출 합니다 **GazeCursor**

2.  새 두 번 클릭 **GazeCursor** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**

3.  위에서 참조 된 네임 스페이스 했는지 확인 합니다 **GazeCursor** 클래스:

    ```csharp
    using UnityEngine;
    ```

4.  다음 내에서 다음 변수를 추가 합니다 **GazeCursor** 위의 클래스는 **start ()** 메서드. 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  업데이트를 **start ()** 메서드를 다음 코드로:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  업데이트를 **update ()** 메서드를 다음 코드로:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > 에 대 한 오류에 대 한 걱정 하지 마십시오 합니다 **SceneOrganiser** 되 찾을 수 없으면 다음 장에서 만들려는 클래스입니다.

7. 변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>9-장 SceneOrganiser 클래스 만들기

이 클래스는:

-   설정 된 *주 카메라* 적절 한 구성 요소를 연결 하 여 합니다.

-   실제 및 위치에 해당 위치를 계산 하는 일을 담당 될 때 개체 감지 되 면을 **태그 레이블** 적절 한 근처 **태그 이름**합니다.    

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다. 스크립트 이름을 **SceneOrganiser**합니다.

2.  새 두 번 클릭 **SceneOrganiser** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**

3.  위에서 참조 된 다음 네임 스페이스가 있는지 확인 합니다 **SceneOrganiser** 클래스:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  다음 내에서 다음 변수를 추가 합니다 **SceneOrganiser** 위의 클래스는 **start ()** 메서드:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  삭제 된 **start ()** 하 고 **update ()** 메서드.

6.  변수를 아래에 추가 합니다 **Awake()** 메서드 클래스를 초기화 하 고 장면 설정 합니다.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  추가 된 **PlaceAnalysisLabel()** 메서드를 *인스턴스화* (이 시점에서 표시 되지 않는 사용자에 게) 장면 레이블. 또한는 쿼드 (또한 보이지 않음) 여기서 이미지 배치 되 면 하 고 실제와 겹치는 배치 합니다. 이 분석으로 실제 환경에서 개체의 대략적인 위치를 결정이 쿼드 다시 추적할지 후 서비스에서 검색 상자 좌표 중요 합니다. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  추가 된 **FinaliseLabel()** 메서드. 이 담당 합니다.

    *   설정 합니다 *레이블* 텍스트를 *태그* 가장 안정적으로 예측 합니다.
    *   계산을 호출 합니다 *경계 상자* 에 이전에 있는 4 개의 개체, 장면에 레이블을 배치 합니다.
    *   방향으로 Raycast를 사용 하 여 레이블 크기를 조정 합니다 *경계 상자*는 실제에서 개체에 대해 충돌 합니다.
    * 다른 이미지를 캡처할 수 있도록 하는 캡처 프로세스를 다시 설정 합니다.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  추가 합니다 **CalculateBoundingBoxPosition()** 숫자로 변환 하는 데 필요한 계산을 호스트 하는 메서드는 *경계 상자* 좌표 서비스에서 검색 하 고 다시 쿼드에서 비례적으로.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. 변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.

    > [!IMPORTANT]
    > 계속 하기 전에 엽니다는 **CustomVisionAnalyser** 클래스 및 내 합니다 **AnalyseLastImageCaptured()** 메서드를 *주석 처리를 제거* 다음 줄:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> 걱정 하지 마십시오는 **ImageCapture** '을 찾을 수 없습니다' 메시지 클래스를 다음 장에서 만들어집니다.


## <a name="chapter-10---create-the-imagecapture-class"></a>10-장 ImageCapture 클래스 만들기

다음 클래스를 만드는 것은 **ImageCapture** 클래스입니다.

이 클래스는 담당 합니다.

*   HoloLens 카메라를 사용 하 고 저장 하는 이미지를 캡처하는 *앱* 폴더입니다.
*   처리 *누릅니다* 사용자에서 제스처입니다.

이 클래스를 만들려면:

1.  로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.

2.  폴더를 마우스 오른쪽 단추로 클릭 **Create** > **C\# 스크립트**합니다. 스크립트 이름을 **ImageCapture**합니다.

3.  새 두 번 클릭 **ImageCapture** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**

4.  파일의 맨 위에 있는 네임 스페이스를 다음으로 바꿉니다.

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  다음 내에서 다음 변수를 추가 합니다 **ImageCapture** 위의 클래스는 **start ()** 메서드:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  에 대 한 코드 **Awake()** 하 고 **start ()** 메서드는 이제 추가 해야 합니다.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  탭 제스처 발생할 때 호출 되는 처리기를 구현 합니다.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > 커서를 놓으면 **녹색**, 즉, 카메라는 이미지를 사용할 수 있습니다. 커서를 놓으면 **빨간색**, 즉, 카메라 사용 중입니다.

8.  응용 프로그램 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  사진을 캡처한 시간과 분석할 준비가 되었을 때 호출 되는 처리기를 추가 합니다. 결과 전달 되어는 **CustomVisionAnalyser** 분석 합니다.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>11 장-장면에 있는 스크립트 설정

이 프로젝트에 필요한 코드를 모두 작성 했으므로 시간이 올바르게 작동 하기 위해를 prefabs 장면에 스크립트를 설정 합니다.

1.  내에서 **Unity 편집기**의 **계층 패널**를 선택 합니다 **주 카메라**합니다.
2.  에 **검사기 패널**를 사용 하 여는 **주 카메라** 클릭을 선택 **구성 요소 추가**, 검색 한 다음 **SceneOrganiser** 스크립트 및 두 번 클릭을 추가 합니다.

    ![](images/AzureLabs-Lab310-38.png)

3.  에 **프로젝트 패널**를 엽니다는 **Prefabs 폴더**, 끌어를 **레이블** 으로 prefab를 *레이블* 빈 참조 대상의 영역을 입력는 **SceneOrganiser** 스크립트에 방금 추가한 합니다 *주 카메라*아래 이미지에서 보여준 것 처럼:

    ![](images/AzureLabs-Lab310-39.png)

4.  **계층 패널**를 선택 합니다 **GazeCursor** 자식의 **주 카메라**.
5.  에 **검사기 패널**를 사용 하 여는 **GazeCursor** 클릭을 선택 **구성 요소 추가**, 검색 한 다음 **GazeCursor** 스크립트 및 두 번 클릭을 추가 합니다.

    ![](images/AzureLabs-Lab310-40.png)

6.  를 다시는 **계층 패널**를 선택 합니다 **SpatialMapping** 자식의 **주 카메라**.
7.  에 **검사기 패널**를 사용 하 여는 **SpatialMapping** 클릭을 선택 **구성 요소 추가**, 검색 한 다음 **SpatialMapping** 스크립트 및 추가를 두 번 클릭 합니다.

    ![](images/AzureLabs-Lab310-41.png)

나머지 스크립트의 수를 하지 않은 일련의 코드에 의해 추가 됩니다는 **SceneOrganiser** 런타임에 스크립트입니다.

## <a name="chapter-12---before-building"></a>빌드하기 전에 12 장

응용 프로그램의 철저 한 테스트를 수행 하려면 해야 테스트용으로 로드 하 여 Microsoft HoloLens 합니다.

를 수행 하기 전에 확인 합니다.

-  에 언급 된 모든 설정 합니다 [3 장](#chapter-3---set-up-the-unity-project) 올바르게 설정 됩니다.
- 스크립트 **SceneOrganiser** 에 연결할 때 합니다 **주 카메라** 개체입니다.
- 스크립트 **GazeCursor** 에 연결할 때 합니다 **GazeCursor** 개체입니다.
- 스크립트 **SpatialMapping** 에 연결할 때 합니다 **SpatialMapping** 개체입니다.
- [5 장](#chapter-5---create-the-customvisionanalyser-class), 6 단계:

    - 삽입 해야 하 **서비스 예측 키** 에 **predictionKey** 변수입니다.
    - 삽입 한 사용자 **예측 끝점** 에 **predictionEndpoint** 클래스입니다.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>13-장 UWP 솔루션 및 테스트용으로 로드 응용 프로그램 만들기

Microsoft HoloLens 배포할 수 있게 될 UWP 솔루션으로 응용 프로그램을 빌드할 준비가 되었습니다. 빌드 프로세스를 시작 합니다.

1.  로 이동 **파일 > 빌드 설정**합니다.

2.  눈금 **Unity C\# 프로젝트**합니다.

3.  클릭할 **열고 장면 추가**합니다. 이렇게 하면 현재 열려 장면 빌드에 추가 됩니다.

    ![](images/AzureLabs-Lab310-42.png)

4.  **빌드**를 클릭합니다. Unity가 시작 됩니다는 *파일 탐색기* 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다. 해당 폴더를 이제 만들고 이름을 **앱**합니다. 사용 하 여 다음 합니다 **앱** 폴더를 선택, 클릭 **폴더 선택**합니다.

5.  Unity 프로젝트를 빌드할 예정 된 **앱** 폴더입니다.

6.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.

7.  Microsoft HoloLens를 배포 하려면 해야 해당 장치의 IP 주소 (배포에 대 한 원격), 및도 하는지 확인 해야 했습니다 **개발자 모드** 설정 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1.  에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.

    2.  로 이동 **네트워크 및 인터넷** > **Wi-fi** > **고급 옵션**

    3.  참고 합니다 **IPv4** 주소입니다.

    4.  다음으로 다시 이동할 **설정을**, 한 다음 **업데이트 및 보안** > **개발자를 위한**

    5.  설정할 **개발자 모드** *에서*합니다.

8.  새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.

9.  솔루션 구성 선택에서 **디버그**합니다.

10. 솔루션 플랫폼에서 선택 **x86, 원격 컴퓨터**합니다. 삽입 하 라는 메시지가 표시 됩니다는 **IP 주소** 원격 장치 (의 Microsoft HoloLens,이 경우 둔).

    ![](images/AzureLabs-Lab310-43.png)

11. 로 이동 합니다 **빌드** 메뉴를 클릭 **솔루션 배포** 을 사이드 로드에 HoloLens에 응용 프로그램입니다.

12. 앱 시작 준비가 Microsoft HoloLens 설치 된 앱 목록에 나타나야 합니다.

### <a name="to-use-the-application"></a>응용 프로그램을 사용 합니다.

* 사용 하 여 학습 하는 개체를 확인 하 **Azure Custom Vision Service, 개체 감지**를 사용 하 여를 **탭 하기 제스처**합니다.
* 개체가 성공적으로 검색 되 면 세계 좌표 *레이블 텍스트* 태그 이름으로 표시 됩니다.

> [!IMPORTANT]
> 사진을 캡처하고 서비스에 보낼 때마다에 서비스 페이지로 다시 이동 하 고 새로 캡처한 이미지를 사용 하 여 서비스를 다시 학습 수 있습니다. 를 시작할 때 것도 수정 해야 합니다 *경계 상자* 더 정확 하 게 서비스를 다시 학습 하 합니다.

> [!NOTE]
> Microsoft HoloLens 센서 및/또는 Unity의 SpatialTrackingComponent 실제 개체를 기준으로 하는 적절 한 colliders, 배치에 실패 한 경우 배치 된 레이블 텍스트 개체 거의 나타나지 않을 수 있습니다. 이 경우 다른 화면에서 응용 프로그램을 사용 하려고 합니다.

## <a name="your-custom-vision-object-detection-application"></a>사용자 지정 비전, 개체 감지 응용 프로그램

축 하 Azure Custom Vision, 이미지에서 개체를 인식 하 고 3D 공간에서 해당 개체에 대 한 대략적인 위치를 제공할 수 있는 개체 검색 API를 활용 하는 혼합된 현실 앱을 빌드 했습니다.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

3d에서 실제 개체를 래핑할 반투명 하 게 큐브는 사용할 텍스트 레이블 추가 *경계 상자*합니다.

### <a name="exercise-2"></a>연습 2

더 많은 개체를 인식 하 여 Custom Vision Service를 학습 합니다.

### <a name="exercise-3"></a>연습 3

개체 인식 되 면 소리를 재생 합니다.

### <a name="exercise-4"></a>실습 4

앱을 분석 하는 동일한 이미지를 사용 하 여 서비스를 다시 학습에 따라서 서비스를 보다 정확 하 게 확인 API를 사용 하 여 (예측 및 교육을 동시에 수행 됨).
