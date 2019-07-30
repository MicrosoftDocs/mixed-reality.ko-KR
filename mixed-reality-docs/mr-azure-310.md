---
title: MR 및 Azure 310-개체 검색
description: 이 과정을 완료 하 여 machine learning 모델을 학습 한 다음, 학습 된 모델을 사용 하 여 혼합 현실 응용 프로그램 내에서 실제 세계의 유사한 개체와 해당 위치를 인식 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 사용자 지정 비전, 개체 검색, 혼합 현실, 아카데미, unity, 자습서, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544417"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-and-azure-310-object-detection"></a>Mr 및 Azure 310: 개체 검색

이 과정에서는 혼합 현실 응용 프로그램에서 Azure Custom Vision "개체 검색" 기능을 사용 하 여 제공 된 이미지 내에서 사용자 지정 시각적 콘텐츠와 해당 공간 위치를 인식 하는 방법을 알아봅니다.

이 서비스를 사용 하면 개체 이미지를 사용 하 여 기계 학습 모델을 학습 시킬 수 있습니다. Microsoft HoloLens의 카메라 캡처 또는 카메라를 사용 하 여 (VR 용 PC에 연결) 헤드셋에서 제공 하는 것 처럼 학습 된 모델을 사용 하 여 실제 세계에서 유사한 개체를 인식 하 고 해당 위치를 대략적으로 파악할 수 있습니다.

![과정 결과](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision, 개체 검색** 은 개발자가 사용자 지정 이미지 분류자를 빌드할 수 있게 해 주는 Microsoft 서비스입니다. 이러한 분류자는 이미지 자체 내에서 **상자 경계** 를 제공 하 여 새 이미지 내에서 개체를 검색 하는 데 사용할 수 있습니다. 이 서비스는 간단 하 고 사용 하기 쉬운 온라인 포털을 제공 하 여이 프로세스를 간소화 합니다. 자세한 내용은 다음 링크를 방문 하세요.

* [Azure Custom Vision 페이지](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [제한 및 할당량](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

이 과정이 완료 되 면 다음을 수행할 수 있는 혼합 현실 응용 프로그램이 만들어집니다.

1. 사용자가 Azure Custom Vision Service, 개체 검색을 사용 하 여 학습 한 개체를 *응시* 할 수 있습니다. 
2. 사용자는 *탭* 제스처를 사용 하 여 원하는 항목의 이미지를 캡처합니다.
3. 앱이 Azure Custom Vision Service에 이미지를 보냅니다.
4. 인식 결과를 전 세계 공간 텍스트로 표시 하는 서비스의 회신이 표시 됩니다. 이는 인식 되는 개체의 세계 위치를 이해 하 고 이미지에서 검색 된 *태그* 를 사용 하 여 레이블 텍스트를 제공 하는 방법으로 Microsoft HoloLens의 공간 추적을 활용 하 여 수행 됩니다.

또한이 과정에서는 이미지 내에서 *경계 상자* 를 설정 하 여 이미지를 수동으로 업로드 하 고, 태그를 만들고, 서비스를 학습 하 여 다양 한 개체 (제공 된 예제에서 컵)를 인식할 수 있습니다. 

> [!IMPORTANT]
> 앱을 만들고 사용한 후 개발자는 Azure Custom Vision Service으로 다시 이동 하 고, 서비스에서 수행 하는 예측을 식별 하 고, 서비스가 누락 되었는지 여부를 확인 합니다. *경계 상자*조정). 그런 다음 서비스를 다시 학습 하 여 실제 개체를 인식할 가능성을 높일 수 있습니다.

이 과정에서는 Azure Custom Vision Service, 개체 검색에서 결과를 Unity 기반 샘플 응용 프로그램으로 가져오는 방법을 설명 합니다. 빌드할 수 있는 사용자 지정 응용 프로그램에 이러한 개념을 적용 하는 것이 좋습니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 310: 개체 검색</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다. [도구 설치](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- 개발 PC
- [개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [최신 Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- 개발자 모드를 사용 하는 [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)
- Azure 설정 및 Custom Vision Service 검색을 위한 인터넷 액세스
-  Custom Vision에서 인식할 수 있는 각 개체에 대해 15 개 이상의 이미지가 필요 합니다. 원할 경우이 과정에서 이미 제공 된 이미지 ( [일련의 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))를 사용할 수 있습니다.

## <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
2.  HoloLens를 설정 하 고 테스트 합니다. HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다. 
3.  새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음). 

보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens)대 한 다음 링크를 참조 하세요.

센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.

## <a name="chapter-1---the-custom-vision-portal"></a>1 장-Custom Vision 포털

**Azure Custom Vision Service**을 사용 하려면 응용 프로그램에서 사용할 수 있도록 인스턴스를 구성 해야 합니다.

1.  [ **Custom Vision Service** 기본 페이지로](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)이동 합니다.

2.  **시작**을 클릭 합니다.

    ![](images/AzureLabs-Lab310-01.png)

3.  Custom Vision 포털에 로그인 합니다.

    ![](images/AzureLabs-Lab310-02.png)

4.  아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

5.  처음으로 로그인 한 후에는 *서비스 사용 약관* 패널이 표시 됩니다. 확인란을 클릭 하 여 *약관에 동의*합니다. 그런 다음 **동의 함**을 클릭 합니다.

    ![](images/AzureLabs-Lab310-03.png)

6.  조건에 동의한 경우 이제 *내 프로젝트* 섹션에 있습니다. **새 프로젝트**를 클릭 합니다.

    ![](images/AzureLabs-Lab310-04.png)

7.  탭이 오른쪽에 표시 되 고 프로젝트의 일부 필드를 지정 하 라는 메시지가 표시 됩니다.

    1.  프로젝트 이름을 삽입 합니다.

    2.  프로젝트에 대 한 설명을 삽입 합니다 (**선택 사항**).

    3.  리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > [Azure 리소스 그룹에 대 한 자세한 내용을 보려면 관련 문서를 탐색](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) 하세요.

    4.  **프로젝트 형식을** **개체 검색 (미리 보기)** 으로 설정 합니다.

8.  작업이 완료 되 면 **프로젝트 만들기**를 클릭 하면 Custom Vision Service 프로젝트 페이지로 리디렉션됩니다.


## <a name="chapter-2---training-your-custom-vision-project"></a>2 장-Custom Vision 프로젝트 학습

Custom Vision 포털에서 기본 목표는 이미지의 특정 개체를 인식할 수 있도록 프로젝트를 학습 하는 것입니다.

응용 프로그램에서 인식 하는 각 개체에 대해 최소 15 개의 이미지가 필요 합니다. 이 과정에서 제공 되는 이미지 ([일련의 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))를 사용할 수 있습니다.

Custom Vision 프로젝트를 학습 하려면:

1.  **태그 옆**에 있는 **단추를클릭+** 합니다.

    ![](images/AzureLabs-Lab310-06.png)

2.  에 이미지를 연결 하는 데 사용 되는 태그의 **이름을** 추가 합니다. 이 예제에서는 cup 이미지를 사용 하 여 인식 하므로이 **컵**의 태그 이름을 지정 했습니다. 완료 되 면 **저장** 을 클릭 합니다.

    ![](images/AzureLabs-Lab310-07.png)

3.  **태그가** 추가 된 것을 확인할 수 있습니다 (표시 되기 위해 페이지를 다시 로드 해야 할 수 있음). 

    ![](images/AzureLabs-Lab310-08.png)

4.  페이지의 가운데에 있는 **이미지 추가** 를 클릭 합니다.

    ![](images/AzureLabs-Lab310-09.png)

5.  **로컬 파일 찾아보기**를 클릭 하 고, 한 개체에 대해 업로드할 이미지를 찾은 다음 최소 15 (15)입니다.

    > [!TIP]
    >  한 번에 여러 이미지를 선택 하 여 업로드할 수 있습니다.

    ![](images/AzureLabs-Lab310-10.png)

6.  프로젝트를 학습 하려는 모든 이미지를 선택 했으면 **파일 업로드** 를 누릅니다. 파일이 업로드 되기 시작 합니다. 업로드를 확인 한 후 **완료**를 클릭 합니다.

    ![](images/AzureLabs-Lab310-11.png)

7.  이 시점에서 이미지는 업로드 되지만 태그가 지정 되지 않습니다.

    ![](images/AzureLabs-Lab310-12.png)

8.  이미지에 태그를 사용 하려면 마우스를 사용 합니다. 이미지를 마우스로 가리키면 선택 항목 강조 표시를 통해 개체 주위에 선택 영역을 자동으로 그리면 도움을 받을 수 있습니다. 정확 하지 않은 경우 직접 그릴 수 있습니다. 마우스 왼쪽 단추를 누르고 선택 영역을 끌어 개체를 포함 하 여이를 수행 합니다. 

    ![](images/AzureLabs-Lab310-13.png) 

9. 이미지 내에서 개체를 선택 하 고 나 서 작은 프롬프트가 표시 되 면 *지역 태그를 추가*하 라는 메시지가 표시 됩니다. 위의 예제에서 이전에 만든 태그 (' 컵 ')를 선택 하거나 태그를 더 추가 하는 경우에 해당 태그를 입력 하 고 **+ (더하기)** 단추를 클릭 합니다.

    ![](images/AzureLabs-Lab310-14.png) 

10. 다음 이미지에 태그를 표시 하려면 블레이드의 오른쪽에 있는 화살표를 클릭 하거나 블레이드의 오른쪽 위 모퉁이에 있는 **X** 를 클릭 하 여 태그 블레이드를 닫은 후 다음 이미지를 클릭 하면 됩니다. 다음 이미지가 준비 되 면 동일한 절차를 반복 합니다. 모든 이미지에 태그를 지정 하기 전까지 업로드 한 모든 이미지에 대해이 작업을 수행 합니다. 

    > [!NOTE]
    >  아래 이미지와 같이 동일한 이미지에서 여러 개체를 선택할 수 있습니다. 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. 태그를 모두 지정 했으면 화면 왼쪽에 있는 **태그가 지정** 된 단추를 클릭 하 여 태그가 지정 된 이미지를 표시 합니다. 

    ![](images/AzureLabs-Lab310-16.png)

12. 이제 서비스를 학습할 준비가 되었습니다. **학습** 단추를 클릭 하면 첫 번째 학습 반복이 시작 됩니다.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. 빌드된 후에는 **기본** 및 **예측 URL**이라는 두 개의 단추를 볼 수 있습니다. 먼저 **기본 설정** 을 클릭 한 다음 **예측 URL**을 클릭 합니다.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > 이에서 제공 하는 끝점은 기본값으로 표시 된 *반복* 에 대해 설정 됩니다. 따라서 나중에 새 *반복* 을 만들고 기본값으로 업데이트할 경우에는 코드를 변경할 필요가 없습니다.

14. **예측 URL**을 클릭 하면 *메모장*을 열고, 코드에서 나중에 필요할 때 검색할 수 있도록 **url** ( **예측 엔드포인트**라고도 함) 및 **서비스 예측 키**를 복사 하 여 붙여넣습니다.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

1.  **Unity** 를 열고 **새로 만들기**를 클릭 합니다.

    ![](images/AzureLabs-Lab310-21.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. **CustomVisionObjDetection**을 삽입 합니다. 프로젝트 형식이 **3d**로 설정 되었는지 확인 하 고 위치를 적절 한 **위치** 에 적절 하 게 설정 합니다 (루트 디렉터리와 더 잘 됨). 그런 다음 **프로젝트 만들기**를 클릭 합니다.

    ![](images/AzureLabs-Lab310-22.png)

3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다. **기본 설정* *편집* > * 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio**로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![](images/AzureLabs-Lab310-23.png)

4.  그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 **플랫폼** 을 *유니버설 Windows 플랫폼*로 전환한 다음, **플랫폼 전환** 단추를 클릭 합니다.

    ![](images/AzureLabs-Lab310-24.png)

5.  동일한 **빌드 설정** 창에서 다음이 설정 되어 있는지 확인 합니다.

    1.  **대상 장치가** **HoloLens** 로 설정 됨        
    2.  **빌드 형식이** **D3D** 로 설정 됩니다.
    3.  **SDK** 가 **최신 설치** 로 설정 됨
    4.  **Visual Studio 버전이** **최신 설치** 로 설정 됨
    5.  **빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨            
    6.  **빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.

        ![](images/AzureLabs-Lab310-25.png)

6.  동일한 **빌드 설정** 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  **기타 설정** 탭에서 다음을 수행 합니다.

        1.  **Scripting Runtime 버전** 은 **실험적** (.net 4.6 이와 동일) 이어야 하며,이 경우 편집기를 다시 시작 해야 합니다.

        2. **Scripting 백엔드** 는 **.net**이어야 합니다.

        3. **API 호환성 수준은** **.net 4.6**이어야 합니다.

            ![](images/AzureLabs-Lab310-26.png)

    2.  **게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.

        1. **InternetClient**

        2.  **웹캠**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되었는지 확인 합니다.

        ![](images/AzureLabs-Lab310-29.png)

8.  **빌드 설정**으로 돌아가서 *\# Unity C 프로젝트가* 더 이상 회색으로 표시 되지 않습니다 .이 옆의 확인란을 선택 합니다.

9.  **빌드 설정** 창을 닫습니다.

10. **편집기**에서**프로젝트 설정** > 편집 > **그래픽**을 클릭 합니다.

    ![](images/AzureLabs-Lab310-30.png)

11. **검사기 패널** 에서 *그래픽 설정이* 열립니다. **항상 셰이더 포함**이라는 배열이 표시 될 때까지 아래로 스크롤합니다. **크기** 변수를 1 씩 늘려서 슬롯을 추가 합니다 .이 예제에서는 8 이므로 9로 만들었습니다. 새 슬롯은 아래와 같이 배열의 마지막 위치에 표시 됩니다.

    ![](images/AzureLabs-Lab310-31.png)

12. 슬롯에서 슬롯 옆의 작은 대상 원을 클릭 하 여 셰이더 목록을 엽니다. **레거시 셰이더/투명/확산** 셰이더를 찾아 두 번 클릭 합니다. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>4 장-CustomVisionObjDetection Unity 패키지 가져오기

이 과정에서는 **310. unitypackage**라는 Unity 자산 패키지가 제공 됩니다. 

> 잠깐만 전체 장면을 포함 하 여 Unity에서 지원 되는 모든 개체를 **unitypackage** 파일로 패키지 하 고 다른 프로젝트에서 내보내거나 가져올 수 있습니다. 서로 다른 **Unity 프로젝트**간에 자산을 이동 하는 가장 안전 하 고 가장 효율적인 방법입니다.

[여기에서 다운로드 해야 하는 Azure-MR-310 패키지](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)를 찾을 수 있습니다.

1.  앞의 Unity 대시보드를 사용 하 여 화면 위쪽의 메뉴에서 **자산** 을 클릭 하 고 **패키지 가져오기 > 사용자 지정 패키지**를 클릭 합니다.

    ![](images/AzureLabs-Lab310-33.png)

2.  파일 선택기를 사용 하 여 **310. unitypackage** 패키지를 선택 하 고 **열기**를 클릭 합니다. 이 자산의 구성 요소 목록이 표시 됩니다. **가져오기** 단추를 클릭 하 여 가져오기를 확인 합니다.

    ![](images/AzureLabs-Lab310-34.png)

3.  가져오기가 완료 되 면 패키지의 폴더가 **자산** 폴더에 추가 된 것을 알 수 있습니다. 이러한 종류의 폴더 구조는 Unity 프로젝트에 일반적입니다.

    ![](images/AzureLabs-Lab310-35.png)

    1.  **재질** 폴더는 **응시 커서**에서 사용 하는 자료를 포함 합니다. 

    2.  **플러그 인** 폴더는 코드에서 서비스 웹 응답을 deserialize 하는 데 사용 하는 newtonsoft.json DLL을 포함 합니다. 폴더 및 하위 폴더에 포함 된 두 가지 다른 버전은 Unity 편집기와 UWP 빌드 모두에서 라이브러리를 사용 하 고 작성할 수 있도록 하는 데 필요 합니다. 

    3.  **Prefabs** 폴더에는 장면에 포함 된 Prefabs이 포함 됩니다. 이러한 작업은 다음과 같습니다.

        1.  응용 프로그램에서 사용 되는 **GazeCursor**입니다. 는 SpatialMapping prefab와 함께 작동 하 여 물리적 개체의 맨 위에 장면에 배치할 수 있습니다.
        2.  **레이블**-필요할 때 장면에 개체 태그를 표시 하는 데 사용 되는 UI 개체입니다.
        3.  **SpatialMapping**는 응용 프로그램에서 Microsoft HoloLens의 공간 추적을 사용 하 여 가상 맵 만들기를 사용할 수 있도록 하는 개체입니다.

    4.  이 과정의 미리 작성 된 장면을 현재 포함 하는 **장면** 폴더입니다.

4.  **프로젝트 패널**에서 **장면** 폴더를 열고 **ObjDetectionScene**를 두 번 클릭 하 여이 과정에 사용할 장면을 로드 합니다.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **코드는 포함 되지 않으며**,이 과정을 수행 하 여 코드를 작성 합니다.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>5 장-CustomVisionAnalyser 클래스 만들기

이 시점에서 일부 코드를 작성할 준비가 되었습니다. **CustomVisionAnalyser** 클래스로 시작 합니다.

> [!NOTE]
> 아래에 표시 된 코드에서 수행 된 **Custom Vision Service**호출은 **Custom Vision REST API**를 사용 하 여 수행 됩니다. 이를 사용 하 여이 API를 구현 하 고 사용 하는 방법을 확인할 수 있습니다 (사용자가 직접 비슷한 항목을 구현 하는 방법을 이해 하는 데 유용). Microsoft는 서비스를 호출 하는 데 사용할 수 있는 **CUSTOM VISION SDK** 를 제공 합니다. 자세한 내용은 [CUSTOM VISION SDK 문서](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)를 참조 하세요.

이 클래스는 다음을 담당 합니다.

- 캡처된 최신 이미지를 바이트 배열로 로드 하 고 있습니다.

- 분석을 위해 바이트 배열을 Azure **Custom Vision Service** 인스턴스로 보냅니다.

- JSON 문자열로 응답을 수신 합니다.

- 응답을 deserialize 하 고 결과 **예측** 을 **SceneOrganiser** 클래스에 전달 하 여 응답이 표시 되는 방법을 처리 합니다.

이 클래스를 만들려면:

1.  **프로젝트 패널**에 있는 **자산 폴더**를 마우스 오른쪽 단추로 클릭 한 다음**폴더** **만들기** > 를 클릭 합니다. 폴더 **스크립트**를 호출 합니다.

    ![](images/AzureLabs-Lab310-37.png)

2.  새로 만든 폴더를 두 번 클릭 하 여 엽니다.

3.  폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음,**C\# 스크립트** **만들기** > 를 클릭 합니다. 스크립트 이름을 **CustomVisionAnalyser로 합니다.**

4.  새 **CustomVisionAnalyser** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.

5.  파일의 위쪽에서 참조 되는 다음 네임 스페이스가 있는지 확인 합니다.

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  **CustomVisionAnalyser** 클래스에서 다음 변수를 추가 합니다.

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
    > **서비스 예측 키** 를 **predictionKey** 변수에 삽입 하 고 **예측 끝점** 을 **predictionEndpoint** 변수에 삽입 해야 합니다. 위의 [2 장, 14 단계에서 메모장](#chapter-2---training-your-custom-vision-project)에 복사 했습니다.

7.  이제 initialize **()** 에 대 한 코드를 추가 하 여 인스턴스 변수를 초기화 해야 합니다.

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

8.  코 루틴 (아래의 static **GetImageAsByteArray ()** 메서드 사용)를 추가 합니다. 그러면 **ImageCapture** 클래스에서 캡처한 이미지의 분석 결과를 얻을 수 있습니다.

    > [!NOTE]
    > **AnalyseImageCapture** 코 루틴에는 아직 만들지 않은 **SceneOrganiser** 클래스에 대 한 호출이 있습니다. 따라서 **해당 줄을 현재 주석으로 처리**합니다.

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

9. **Start ()** 및 **Update ()** 메서드를 사용 하지 않으므로 삭제 합니다. 

10.  **Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.

> [!IMPORTANT]
> 앞에서 설명한 것 처럼 오류가 발생 한 것 처럼 보일 수 있는 코드에 대해 걱정 하지 마세요. 추가 클래스를 곧 제공 하면이 문제를 해결할 수 있습니다.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>6 장-CustomVisionObjects 클래스 만들기

지금 만들 클래스는 **CustomVisionObjects** 클래스입니다.

이 스크립트에는 다른 클래스에서 Custom Vision Service에 대 한 호출을 serialize 및 deserialize 하는 데 사용 하는 여러 개체가 포함 되어 있습니다.

이 클래스를 만들려면:

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다. CustomVisionObjects 스크립트를 호출 **합니다.**

2.  새 **CustomVisionObjects** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.

3.  파일의 위쪽에서 참조 되는 다음 네임 스페이스가 있는지 확인 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  **CustomVisionObjects** 클래스 내에서 **Start ()** 및 **Update ()** 메서드를 삭제 합니다 .이 클래스는 이제 비어 있어야 합니다.

    > [!WARNING]
    > 다음 명령을 신중 하 게 수행 하는 것이 중요 합니다. **CustomVisionObjects** 클래스 내에 새 클래스 선언을 배치 하면 **AnalysisRootObject** 및 **BoundingBox** 가 없다는 것을 나타내는 [10 장](#chapter-10---create-the-imagecapture-class)에서 컴파일 오류가 발생 합니다.

5.  **CustomVisionObjects** 클래스 *외부* 에 다음 클래스를 추가 합니다. 이러한 개체는 **newtonsoft.json** 라이브러리에서 응답 데이터를 serialize 및 deserialize 하는 데 사용 됩니다.

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

6.  **Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-7---create-the-spatialmapping-class"></a>7 장-SpatialMapping 클래스 만들기

이 클래스는 가상 개체와 실제 개체 간의 충돌을 검색할 수 있도록 장면에 **공간 매핑 Collider** 를 설정 합니다.

이 클래스를 만들려면:

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다. SpatialMapping 스크립트를 호출 **합니다.**

2.  새 **SpatialMapping** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.

3.  **SpatialMapping** 클래스 위에 참조 된 다음 네임 스페이스가 있는지 확인 합니다.

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  그런 다음 **SpatialMapping** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.

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

5.  절전 모드 **()** 를 추가 하 고 **Start ()** 를 추가 합니다.

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

6.  **Update ()** 메서드를 삭제 합니다.

7.  **Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.


## <a name="chapter-8---create-the-gazecursor-class"></a>8 장-GazeCursor 클래스 만들기

이 클래스는 이전 장에서 만든 **SpatialMappingCollider**을 사용 하 여 실제 공간에서 올바른 위치에 커서를 설정 하는 작업을 담당 합니다.

이 클래스를 만들려면:

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다. **GazeCursor** 스크립트를 호출 합니다.

2.  새 **GazeCursor** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.

3.  **GazeCursor** 클래스 위에 참조 된 다음 네임 스페이스가 있는지 확인 합니다.

    ```csharp
    using UnityEngine;
    ```

4.  그런 다음 **GazeCursor** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다. 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  **Start ()** 메서드를 다음 코드로 업데이트 합니다.

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

6.  **Update ()** 메서드를 다음 코드로 업데이트 합니다.

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
    > **SceneOrganiser** 클래스를 찾을 수 없다는 오류에 대해 걱정 하지 마세요. 다음 챕터에서 만듭니다.

7. **Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>9 장-SceneOrganiser 클래스 만들기

이 클래스는 다음을 수행 합니다.

-   적절 한 구성 요소를 연결 하 여 *기본 카메라* 를 설정 합니다.

-   개체가 검색 되 면 실제 환경에서 해당 위치를 계산 하 고 적절 한 **태그 이름을**사용 하 여 **태그 레이블을** 근처에 배치 해야 합니다.    

이 클래스를 만들려면:

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다. 스크립트 이름을 **SceneOrganiser**로 합니다.

2.  새 **SceneOrganiser** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.

3.  **SceneOrganiser** 클래스 위에 참조 된 다음 네임 스페이스가 있는지 확인 합니다.

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  그런 다음 **SceneOrganiser** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.

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

5.  **Start ()** 및 **Update ()** 메서드를 삭제 합니다.

6.  변수 아래에서 해제 **()** 메서드를 추가 합니다 .이 메서드는 클래스를 초기화 하 고 장면을 설정 합니다.

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

7.  **PlaceAnalysisLabel ()** 메서드를 추가 합니다 .이 메서드는 장면 (이 시점에서 사용자에 게 보이지 않음)의 레이블을 *인스턴스화합니다* . 또한 이미지가 배치 되는 4 개 (보이지 않음)를 배치 하 고 실제 세계와 겹칩니다. 분석 후 서비스에서 검색 된 상자 좌표가이 쿼드로 다시 추적 되어 실제 세계에 있는 개체의 대략적인 위치를 결정 하기 때문에이는 중요 합니다. 

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

8.  **FinaliseLabel ()** 메서드를 추가 합니다. 이 담당 합니다.

    *   신뢰 수준이 가장 높은 예측의 *태그로* *레이블* 텍스트를 설정 합니다.
    *   이전에 배치 하 고 장면에 레이블을 배치 하 여 쿼드 개체의 *경계 상자* 계산 호출
    *   실제 세계의 개체와 충돌 하는 *경계 상자*를 향해 Raycast를 사용 하 여 레이블 깊이를 조정 합니다.
    * 사용자가 다른 이미지를 캡처할 수 있도록 캡처 프로세스를 다시 설정 합니다.

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

9.  **CalculateBoundingBoxPosition ()** 메서드를 추가 합니다 .이 메서드는 서비스에서 검색 된 *경계 상자* 좌표를 변환 하 고 쿼드에 비례하여 다시 만드는 데 필요한 계산을 여러 개 호스팅합니다.

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

10. **Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.

    > [!IMPORTANT]
    > 계속 하기 전에 **CustomVisionAnalyser** 클래스를 열고 **AnalyseLastImageCaptured ()** 메서드 내에서 다음 줄의 *주석 처리를 제거* 합니다.
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
> **ImageCapture** 클래스 ' 찾을 수 없음 ' 메시지에 대해 걱정 하지 마세요. 다음 장에서 만듭니다.


## <a name="chapter-10---create-the-imagecapture-class"></a>10 장-ImageCapture 클래스 만들기

만들려는 다음 클래스는 **ImageCapture** 클래스입니다.

이 클래스는 다음을 담당 합니다.

*   HoloLens 카메라를 사용 하 여 이미지를 캡처하고 *앱* 폴더에 저장 합니다.
*   사용자 로부터 *탭* 제스처를 처리 합니다.

이 클래스를 만들려면:

1.  이전에 만든 **스크립트** 폴더로 이동 합니다.

2.  폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음,**C\# 스크립트** **만들기** > 를 클릭 합니다. 스크립트 이름을 **ImageCapture**로 합니다.

3.  새 **ImageCapture** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.

4.  파일의 맨 위에 있는 네임 스페이스를 다음으로 바꿉니다.

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  그런 다음 **ImageCapture** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.

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

6.  이제 **활성 ()** 및 **Start ()** 메서드에 대 한 코드를 추가 해야 합니다.

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

7.  탭 제스처가 발생할 때 호출 되는 처리기를 구현 합니다.

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
    > 커서가 **녹색이**면 카메라에서 이미지를 사용할 수 있음을 의미 합니다. 커서가 **빨간색**이면 카메라가 사용 중임을 의미 합니다.

8.  응용 프로그램이 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.

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

9.  사진이 캡처되고 분석 준비가 될 때 호출 되는 처리기를 추가 합니다. 그런 다음 결과가 분석을 위해 **CustomVisionAnalyser** 에 전달 됩니다.

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

10. **Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>11 장-장면에서 스크립트 설정

이 프로젝트에 필요한 모든 코드를 작성 했으므로 이제는 장면에서 스크립트를 설정 하 고 prefabs에서 제대로 동작 하도록 하는 시간입니다.

1.  **Unity 편집기**내의 **계층 패널**에서 **주 카메라**를 선택 합니다.
2.  **검사기 패널**에서 **주 카메라** 를 선택 하 고 **구성 요소 추가**를 클릭 한 다음 **SceneOrganiser** 스크립트를 검색 하 고 두 번 클릭 하 여 추가 합니다.

    ![](images/AzureLabs-Lab310-38.png)

3.  에 표시 된 것 처럼 **프로젝트 패널**에서 **Prefabs 폴더**를 열고 Prefab **label** 을 *기본 카메라*에 방금 추가한 **SceneOrganiser** 스크립트의 *레이블* 빈 참조 대상 입력 영역으로 끌어 옵니다. 아래 이미지:

    ![](images/AzureLabs-Lab310-39.png)

4.  **계층 패널**에서 **기본 카메라**의 **GazeCursor** 자식을 선택 합니다.
5.  **검사기 패널**에서 **GazeCursor** 가 선택 된 상태에서 **구성 요소 추가**를 클릭 한 다음 **GazeCursor** 스크립트를 검색 하 고 두 번 클릭 하 여 추가 합니다.

    ![](images/AzureLabs-Lab310-40.png)

6.  **계층 패널**에서 **기본 카메라**의 **SpatialMapping** 자식을 선택 합니다.
7.  **검사기 패널**에서 **SpatialMapping** 가 선택 된 상태에서 **구성 요소 추가**를 클릭 한 다음 **SpatialMapping** 스크립트를 검색 하 고 두 번 클릭 하 여 추가 합니다.

    ![](images/AzureLabs-Lab310-41.png)

설정 하지 않은 나머지 스크립트는 런타임 중에 **SceneOrganiser** 스크립트의 코드에 의해 추가 됩니다.

## <a name="chapter-12---before-building"></a>12 장-빌드하기 전

응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 Microsoft HoloLens로 테스트용으로 로드 해야 합니다.

이렇게 하려면 먼저 다음을 확인 해야 합니다.

-  [3 장](#chapter-3---set-up-the-unity-project) 에서 설명한 모든 설정이 올바르게 설정 됩니다.
- **SceneOrganiser** 스크립트는 **주 카메라** 개체에 연결 됩니다.
- **GazeCursor** 스크립트는 **GazeCursor** 개체에 연결 됩니다.
- **SpatialMapping** 스크립트는 **SpatialMapping** 개체에 연결 됩니다.
- [5 장](#chapter-5---create-the-customvisionanalyser-class), 6 단계:

    - **PredictionKey** 변수에 **서비스 예측 키** 를 삽입 해야 합니다.
    - **예측 끝점** 을 **predictionEndpoint** 클래스에 삽입 했습니다.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>13 장-UWP 솔루션 빌드 및 응용 프로그램 테스트용으로 로드

이제 Microsoft HoloLens에 배포할 수 있는 UWP 솔루션으로 응용 프로그램을 빌드할 준비가 되었습니다. 빌드 프로세스를 시작 하려면 다음을 수행 합니다.

1.  **파일 > 빌드 설정**으로 이동 합니다.

2.  Tick **Unity C\# 프로젝트**.

3.  열려 있는 **장면 추가**를 클릭 합니다. 이렇게 하면 현재 열려 있는 장면이 빌드에 추가 됩니다.

    ![](images/AzureLabs-Lab310-42.png)

4.  **빌드**를 클릭합니다. Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 *파일 탐색기* 창을 시작 합니다. 이제 해당 폴더를 만들고 이름을 **App**으로 만듭니다. 그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.

5.  Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.

6.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)

7.  Microsoft HoloLens에 배포 하려면 해당 장치의 IP 주소가 필요 하며 (원격 배포의 경우) **개발자 모드가** 설정 되어 있는지도 확인 해야 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1.  HoloLens를 입고 하는 동안 **설정을**엽니다.

    2.  **네트워크 & 인터넷** > **wi-fi** > **고급 옵션** 으로 이동 합니다.

    3.  **IPv4** 주소를 적어둡니다.

    4.  그런 다음 **설정**으로 다시 이동한 다음**개발자** 를 위한 **& 보안** > 을 업데이트 합니다.

    5.  에서 **개발자 모드** *를*설정 합니다.

8.  새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.

9.  솔루션 구성에서 **디버그**를 선택 합니다.

10. 솔루션 플랫폼에서 **x86, 원격 컴퓨터**를 선택 합니다. 원격 장치의 **IP 주소** (이 경우에는 기록한 Microsoft HoloLens)를 삽입 하 라는 메시지가 표시 됩니다.

    ![](images/AzureLabs-Lab310-43.png)

11. **빌드** 메뉴로 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.

12. 이제 앱이 Microsoft HoloLens의 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.

### <a name="to-use-the-application"></a>응용 프로그램을 사용 하려면:

* **Azure Custom Vision Service 및 개체 검색**을 사용 하 여 학습 하 고 **탭 제스처**를 사용 하 여 개체를 살펴보세요.
* 개체가 성공적으로 검색 되 면 세계 공백 *레이블 텍스트가* 태그 이름과 함께 표시 됩니다.

> [!IMPORTANT]
> 사진을 캡처하여 서비스로 보낼 때마다 서비스 페이지로 돌아가서 새로 캡처한 이미지를 사용 하 여 서비스를 다시 학습 수 있습니다. 처음에는 *경계 상자* 를 수정 하 여 보다 정확 하 고 서비스를 다시 학습 하는 것도 좋습니다.

> [!NOTE]
> Microsoft HoloLens 센서 및/또는 Unity의 SpatialTrackingComponent가 실제 개체를 기준으로 적절 한 colliders를 배치 하지 못할 때 배치 된 레이블 텍스트가 개체 근처에 나타나지 않을 수 있습니다. 해당 하는 경우 다른 화면에서 응용 프로그램을 사용 하십시오.

## <a name="your-custom-vision-object-detection-application"></a>Custom Vision, 개체 검색 응용 프로그램

축 하 합니다. Azure Custom Vision, 개체 검색 API를 활용 하는 혼합 현실 앱을 빌드하여 이미지에서 개체를 인식 한 다음 3D 공간에서 해당 개체에 대 한 대략적인 위치를 제공할 수 있습니다.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

텍스트 레이블에를 추가 하 여 반투명 큐브를 사용 하 여 3D *경계 상자*에 실제 개체를 래핑합니다.

### <a name="exercise-2"></a>연습 2

Custom Vision Service를 학습 하 여 더 많은 개체를 인식할 수 있습니다.

### <a name="exercise-3"></a>연습 3

개체가 인식 될 때 소리를 재생 합니다.

### <a name="exercise-4"></a>연습 4

API를 사용 하 여 응용 프로그램이 분석 하는 것과 동일한 이미지를 사용 하 여 서비스를 다시 학습 하므로 서비스를 보다 정확 하 게 만들 수 있습니다 (예측 및 학습을 동시에 수행).
