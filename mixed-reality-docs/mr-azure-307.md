---
title: MR 및 Azure 307-Machine learning
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Machine Learning Studio을 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 기계 학습, ml, 기계 학습 스튜디오, hololens, 몰입 형, vr
ms.openlocfilehash: e302e287049cd746a436904c2af2bcc2b0835796
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926614"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR 및 Azure 307: Machine learning

![최종 제품-시작](images/AzureLabs-Lab7-0.png)

이 과정에서는 Azure Machine Learning Studio를 사용 하 여 혼합 현실 응용 프로그램에 Machine Learning (ML) 기능을 추가 하는 방법에 대해 설명 합니다.

*Azure Machine Learning Studio* 는 개발자에 게 데이터 입력, 출력, 준비 및 시각화에 도움이 될 수 있는 많은 수의 기계 학습 알고리즘을 제공 하는 Microsoft 서비스입니다. 이러한 구성 요소를 통해 예측 분석 실험을 개발 하 고,이를 반복 하 고, 모델을 학습 하는 데 사용할 수 있습니다. 다음 교육을 통해 Azure 클라우드에서 모델을 작동 하도록 설정 하 여 새 데이터의 점수를 매길 수 있습니다. 자세한 내용은 [Azure Machine Learning Studio 페이지](https://azure.microsoft.com/services/machine-learning-studio/)를 참조 하세요.

이 과정을 완료 하면 혼합 현실의 헤드셋 응용 프로그램을 사용할 수 있으며 다음 작업을 수행 하는 방법이 학습 됩니다.

1.  *Azure Machine Learning Studio* 포털에 판매 데이터 표를 제공 하 고 인기 있는 항목의 향후 판매를 예측 하는 알고리즘을 디자인 합니다.
2.  ML 서비스에서 예측 데이터를 수신 하 고 해석할 수 있는 **Unity 프로젝트**를 만듭니다.
3.  선반에서 가장 인기 있는 판매 항목을 제공 하 여 **Unity 프로젝트**내에서 폐색 데이터를 시각적으로 표시 합니다.

응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다. 이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다. 이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.

이 과정은 다른 혼합 현실 랩을 직접 포함 하지 않는 자체 포함 된 자습서입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 307: Machine learning</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다. 과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다. HoloLens를 사용 하는 경우 음성 캡처 중에 몇 가지 echo를 확인할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다. [도구 설치 문서](install-the-tools.md)에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- 모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC
- [개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)
- Azure 설정 및 ML 데이터 검색에 대 한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 확인 사항

이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.) 

## <a name="chapter-1---azure-storage-account-setup"></a>1 장-계정 설정 Azure Storage

Azure Translator API를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.
1.  [Azure Portal](https://portal.azure.com)에 로그인 합니다.

    > [!NOTE]
    > 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

2.  로그인 되 면 왼쪽 메뉴에서 **저장소 계정** 을 클릭 합니다.

    ![계정 설정 Azure Storage](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > 새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.

3.  **저장소 계정** 탭에서 **추가**를 클릭 합니다.

    ![계정 설정 Azure Storage](images/AzureLabs-Lab7-2.png)

4.  **저장소 계정 만들기** 패널에서 다음을 수행 합니다.

    1.  계정에 대 한 **이름을** 삽입 합니다 .이 필드에는 숫자 및 소문자만 허용 됩니다.
    2.  **배포 모델에서** **Resource manager**를 선택 합니다.
    3.  **계정 종류**에 대해 **저장소 (범용 v1)** 를 선택 합니다.
    4.  **성능**으로 **표준**을 선택 합니다.
    5.  **복제** 의 경우 **읽기 액세스-지역 중복 저장소 (RA-GRS)** 를 선택 합니다.
    6.  **보안 전송을** **사용 하지 않도록 설정**해야 합니다.
    7.  **구독**을 선택 합니다.
    4. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.
    
    5.  새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다. 위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

5.  또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.

    ![계정 설정 Azure Storage](images/AzureLabs-Lab7-3.png)

6.  **만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

7.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![계정 설정 Azure Storage](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>2 장-Azure Machine Learning Studio

*Azure Machine Learning*을 사용 하려면 응용 프로그램에서 사용할 수 있도록 Machine Learning 서비스의 인스턴스를 구성 해야 합니다.

1.  Azure Portal의 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 **Machine Learning Studio 작업 영역**을 검색 하 고 **enter**키를 누릅니다.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  새 페이지에 **Machine Learning Studio 작업 영역** 서비스에 대 한 설명이 제공 됩니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 클릭 하 여이 서비스와의 연결을 만듭니다.

3.  **만들기**를 클릭 하면 새 **Machine Learning Studio 서비스**에 대 한 몇 가지 세부 정보를 제공 해야 하는 창이 표시 됩니다.

    1.  이 서비스 인스턴스의 원하는 **작업 영역 이름을** 삽입 합니다.

    2.  **구독**을 선택 합니다.

    3. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다. 

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.

    4.  새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다. 위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다. 이전 장에서 Azure Storage를 만드는 데 사용한 것과 동일한 리소스 그룹을 사용 해야 합니다.

    5.  **저장소 계정** 섹션에서 **기존 항목 사용**을 클릭 한 다음 드롭다운 메뉴를 클릭 하 고 여기에서 마지막 챕터에서 만든 **저장소 계정을** 클릭 합니다.

    6.  드롭다운 메뉴에서 적절 한 **작업 영역 가격 책정 계층** 을 선택 합니다.

    7.  **웹 서비스 계획** 섹션에서 새로 **만들기** **를** 클릭 한 다음 텍스트 필드에 이름을 삽입 합니다.

    8.  **웹 서비스 계획 가격 책정 계층** 섹션에서 원하는 가격 책정 계층을 선택 합니다. **DEVTEST Standard** 라는 개발 테스트 계층은 무료로 제공 되어야 합니다.

    9.  또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.

    10. **만들기**를 클릭합니다.

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  **만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

5.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

8.  표시 되는 페이지의 **추가 링크** 섹션에서 **시작 Machine Learning Studio**를 클릭 합니다. 그러면 브라우저를 **Machine Learning Studio** 포털로 안내 합니다.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  오른쪽 위 또는 가운데에 있는 **로그인** 단추를 사용 하 여 Machine Learning Studio에 로그인 합니다.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>3 장-Machine Learning Studio: 데이터 집합 설치

Machine Learning 알고리즘의 작동 방법 중 하나는 기존 데이터를 분석 한 다음 기존 데이터 집합을 기반으로 향후 결과를 예측 하는 것입니다. 이는 일반적으로 기존 데이터를 더 많이 사용 하는 것을 의미 하므로 이후 결과를 예측 하는 알고리즘이 더 좋아집니다.

이 과정에서 ProductsTableCSV 이라는 샘플 테이블이 제공 [되며 여기에서 다운로드할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> 위의 .zip 파일에는 **ProductsTableCSV** 와 **unitypackage**가 모두 포함 되어 있습니다 .이 파일은 [6 장에서](#chapter-6---importing-the-mlproducts-unity-package)필요 합니다. 이 패키지는 csv 파일에 별도로 제공 되지만 해당 챕터에도 제공 됩니다.

이 샘플 데이터 집합에는 2017 년의 각 날짜의 매시간 가장 인기 있는 개체 레코드가 포함 되어 있습니다.
        
![Machine Learning Studio: 데이터 집합 설치](images/AzureLabs-Lab7-11.png)

예를 들어 오후 1 시 (시간 13)에서 2017의 1 일에 가장 잘 팔리는 항목은 솔트 및 고추입니다.

이 샘플 테이블에는 9998 개의 항목이 포함 되어 있습니다.

1.  **Machine Learning Studio** 포털로 다시 이동 하 여이 테이블을 ML에 대 한 **데이터 집합** 으로 추가 합니다. 화면의 왼쪽 아래에 있는 **+ 새로 만들기** 단추를 클릭 하 여이 작업을 수행 합니다.

    ![Machine Learning Studio: 데이터 집합 설치](images/AzureLabs-Lab7-12.png)

2.  섹션은 아래쪽에서 위쪽으로 제공 되며 왼쪽에는 탐색 패널이 있습니다. **로컬 파일에서**데이터 집합을 클릭 한 다음 오른쪽에 있는 **데이터 집합**을 클릭 합니다.

    ![Machine Learning Studio: 데이터 집합 설치](images/AzureLabs-Lab7-13.png)

3.  다음 단계를 수행 하 여 새 **데이터 집합** 을 업로드 합니다.

    1. 하드 드라이브에서 새 데이터 집합을 **찾아볼** 수 있는 업로드 창이 표시 됩니다.

        ![Machine Learning Studio: 데이터 집합 설치](images/AzureLabs-Lab7-14.png)

    2.  을 선택 하 고 다시 업로드 창에서 읽으려고 확인란을 선택 취소 합니다.

    3.  아래 텍스트 필드에서 데이터 집합 이름으로 **ProductsTableCSV** 를 입력 합니다 (자동으로 추가 해야 함).

    4.  **형식**에 대 한 드롭다운 메뉴를 사용 하 여 **헤더 (.csv)가 포함 된 일반 CSV 파일**을 선택 합니다.

    5.  업로드 창의 오른쪽 아래에 있는 틱을 누르면 **데이터 집합이** 업로드 됩니다.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>4 장-Machine Learning Studio: 실험

기계 학습 시스템을 구축 하려면 먼저 데이터에 대 한 이론적 유효성을 검사 하기 위해 실험을 빌드해야 합니다. 결과를 사용 하 여 더 많은 데이터가 필요한 지 또는 데이터와 가능한 결과 간의 상관 관계가 없는지를 알 수 있습니다.

실험 만들기를 시작 하려면 다음을 수행 합니다.

1.  페이지 왼쪽 아래에 있는 **+ 새로 만들기** 단추를 다시 클릭 한 다음 **실험** > **빈 실험**을 클릭 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-15.png)

2.  새 페이지가 빈 실험으로 표시 됩니다.

3.  왼쪽 패널에서 **내 데이터** 집합 > **저장 된 데이터 집합** 을 확장 하 고 **ProductsTableCSV** 를 **실험 캔버스로**끌어다 놓습니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-16.png)

4.  왼쪽 패널에서 **데이터 변환** > **샘플 및 분할**을 확장 합니다. 그런 다음 **데이터 분할** 항목을 **실험 캔버스로**끌어다 놓습니다. 데이터 분할 항목은 데이터 집합을 두 부분으로 분할 합니다. 기계 학습 알고리즘을 학습 하는 데 사용 하는 한 부분입니다. 두 번째 부분은 생성 된 알고리즘의 정확도를 평가 하는 데 사용 됩니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-17.png)

5.  캔버스의 데이터 분할 항목이 선택 된 상태에서 오른쪽 패널의 **첫 번째 출력 데이터 집합에 있는 행의 비율** 을 **0.7**로 편집 합니다. 이렇게 하면 데이터는 두 부분으로 분할 되 고 첫 번째 부분은 데이터의 70% 이며 두 번째 부분은 나머지 30%가 됩니다. 데이터가 무작위로 분할 되도록 하려면 **임의 분할** 확인란이 선택 되어 있는지 확인 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-18.png)

6.  캔버스의 **ProductsTableCSV** 항목 밑에서 분할 된 데이터 항목의 위쪽으로 연결을 끕니다. 이렇게 하면 항목을 연결 하 고 **ProductsTableCSV** 데이터 집합 출력 (데이터)을 분할 데이터 입력으로 보냅니다.  

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-19.png)

7.  왼쪽의 **실험** 패널에서 **Machine Learning** > **학습**을 확장 합니다. **모델 학습** 항목을 실험 캔버스로 끌어다 놓습니다. 캔버스는 아래와 동일 하 게 표시 되어야 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-20.png)

8.  **데이터 분할** 항목의 ***왼쪽 아래*** 에서 **모델 학습** 항목의 **오른쪽 위에** 연결을 끌어 놓습니다. 데이터 집합에서 처음 70%의 분할은 학습 모델에서 알고리즘을 학습 하는 데 사용 됩니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-21.png)

9.  캔버스에서 **모델 학습** 항목을 선택 하 고 브라우저 창의 오른쪽에 있는 **속성** 패널에서 **열 선택기 시작** 단추를 클릭 합니다.

10. 텍스트 상자에 **product** 를 입력 하 고 **enter**키를 누릅니다. *제품* 은 예측 학습을 위한 열로 설정 됩니다. 이를 수행 하 고 오른쪽 아래 모서리에 있는 **틱** 을 클릭 하 여 선택 대화 상자를 닫습니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-22.png)

11. **다중 클래스 로지스틱 회귀** 알고리즘을 학습 하 여 시간 및 날짜를 기준으로 가장 많이 판매 되는 **제품** 을 예측 하려고 합니다. Azure Machine Learning studio에서 제공 하는 다양 한 알고리즘에 대 한 세부 정보를 설명 하기 위해이 문서에서는 다루지 않지만 [Machine Learning Algorithm 참고 자료 시트](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet) 에서 더 많은 정보를 확인할 수 있습니다.

12. 왼쪽의 실험 항목 패널에서 **Machine Learning** 를 확장 하 > **모델** > **분류**를 초기화 하 고 **다중 클래스 로지스틱 회귀** 항목을 실험 캔버스로 끕니다.

13. **다중 클래스 로지스틱 회귀**의 아래쪽에 있는 출력을 **모델 학습** 항목의 왼쪽 위 입력에 연결 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-23.png)

14. 왼쪽 패널의 실험 항목 목록에서 **Machine Learning** > **점수**를 확장 하 고 **모델 점수 매기기** 항목을 캔버스로 끕니다.

15. **학습 모델**의 아래쪽에서 **점수 모델**의 왼쪽 위 입력에 출력을 연결 합니다.

16. **데이터 분할**에서 오른쪽 아래 출력을 **모델 점수 매기기** 항목의 오른쪽 위 입력에 연결 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-24.png)

17. 왼쪽 패널의 **실험** 항목 목록에서 **Machine Learning** > **평가**를 확장 하 고 **모델 평가** 항목을 캔버스로 끌어 놓습니다.

18. **점수 모델** 의 출력을 **평가 모델**의 왼쪽 위 입력에 연결 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-25.png)

19. 첫 번째 Machine Learning 실험을 빌드 했습니다. 이제 실험을 저장 하 고 실행할 수 있습니다. 페이지 아래쪽의 메뉴에서 **저장** 단추를 클릭 하 여 실험을 저장 한 다음 **실행** 을 클릭 하 여 실험을 시작 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-26.png)

20. 캔버스의 오른쪽 위에서 실험의 **상태** 를 볼 수 있습니다. 몇 분 정도 기다린 후 실험을 완료할 수 있습니다.

    > 실제 데이터 집합이 큰 경우 실험을 실행 하는 데 몇 시간이 걸릴 수 있습니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-27.png)

21. 캔버스에서 **모델 평가** 항목을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 마우스를 클릭 하 여 **평가 결과**를 가리킨 다음 **시각화**를 선택 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-28.png)

22. 평가 결과는 예상 결과와 실제 결과를 표시 하는 표시 됩니다. 이는 이전에 분할 된 원래 데이터 집합의 30%를 사용 하 여 모델을 평가 합니다. 결과가 적절 하지 않은 것을 볼 수 있습니다. 이상적으로는 각 행에 있는 가장 큰 숫자를 열에서 강조 표시 된 항목으로 지정할 수 있습니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-29.png)

23. **결과**를 닫습니다.

24. 새로 학습 된 Machine Learning 모델을 사용 하려면 **웹 서비스로**노출 해야 합니다. 이렇게 하려면 페이지 아래쪽의 메뉴에서 **웹 서비스 설정** 메뉴 항목을 클릭 하 고 **예측 웹 서비스**를 클릭 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-30.png)

25. 새 탭이 만들어지고 학습 모델을 병합 하 여 새 웹 서비스를 만듭니다. 

26. 페이지 아래쪽의 메뉴에서 **저장**을 클릭 한 다음 **실행**을 클릭 합니다. 실험 캔버스의 오른쪽 위 모서리에 상태가 업데이트 된 것을 볼 수 있습니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-31.png)

27. 실행이 완료 되 면 **웹 서비스 배포** 단추가 페이지 아래쪽에 표시 됩니다. 웹 서비스를 배포할 준비가 되었습니다. 페이지 아래쪽의 메뉴에서 **웹 서비스 배포** (클래식)를 클릭 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-32.png)

    > 브라우저에서 **허용**해야 하는 팝업을 허용할지 여부를 묻는 메시지가 표시 될 수 있습니다. 단, 배포 페이지가 표시 되지 않는 경우에는 **웹 서비스 배포** 를 다시 눌러야 할 수 있습니다. 

28. 실험을 만든 후에는 **API 키** 를 표시 하는 **대시보드** 페이지로 리디렉션됩니다. 잠시 동안 메모장에 복사 하 여 코드에서 곧 필요 합니다. API 키를 적어둔 후에는 키 아래의 **기본 끝점** 섹션에서 **요청/응답** 단추를 클릭 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > 이 페이지에서 테스트를 클릭 하는 경우 입력 데이터를 입력 하 고 출력을 볼 수 있습니다. **날짜** 와 **시간**을 입력 합니다. **제품** 항목을 비워 둡니다. 그런 다음 **확인** 단추를 클릭 합니다. 페이지 아래쪽의 출력에는 각 제품의 선택 가능성을 나타내는 JSON이 표시 됩니다.

29. Machine Learning Studio에 필요한 요청 구조에 대 한 지침 및 몇 가지 예제가 표시 되는 새 웹 페이지가 열립니다. 이 페이지에 표시 된 **요청 URI** 를 메모장에 복사 합니다.

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-34.png)

이제 연간 시간 및 요일과 상관 관계가 지정 된 구매 데이터를 기반으로 판매 될 가능성이 가장 높은 제품을 제공 하는 기계 학습 시스템을 빌드 했습니다.

웹 서비스를 호출 하려면 서비스 끝점에 대 한 URL과 서비스에 대 한 API 키가 필요 합니다. 상단 메뉴에서 **사용** 탭을 클릭 합니다.

**소비** 정보 페이지에는 코드에서 웹 서비스를 호출 하는 데 필요한 정보가 표시 됩니다. **기본 키** 와 **요청-응답** URL의 복사본을 가져옵니다. 다음 장에서 이러한 내용이 필요 합니다.

## <a name="chapter-5---setting-up-the-unity-project"></a>5 장-Unity 프로젝트 설정

혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.

> [!NOTE]
>  이 과정에서는 동작 컨트롤러가 필요 **하지** 않습니다. 모던 헤드셋을 설정 하는 데 지원이 필요한 경우 [여기](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)를 클릭 하세요.

1.  **Unity** 를 열고 **MR\_MachineLearning** 이라는 새 unity 프로젝트를 만듭니다. 프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.

2.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.  > **기본 설정** **편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다. **기본 설정** 창을 닫습니다.

3.  그런 다음 **파일** > **빌드 설정** 으로 이동 하 고 플랫폼 ***전환*** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.

4.  또한 다음을 확인 합니다.

    1.  **대상 장치** 는 **임의의 장치로**설정 됩니다.

        > Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.

    2.  **빌드 형식이** **D3D**로 설정 됩니다.

    3.  **SDK** 가 **최신 설치**로 설정 되어 있습니다.

    4.  **Visual Studio 버전이** **최신 설치**로 설정 되어 있습니다.

    5.  **빌드 및 실행** 이 **로컬 컴퓨터**로 설정 됩니다.

    6.  나중에 제공 되므로 지금은 **장면을** 설정 하는 것에 대해 걱정할 필요가 없습니다.

    7.  지금은 나머지 설정이 기본값으로 유지 되어야 합니다.

        ![Unity 프로젝트 설정](images/AzureLabs-Lab7-35.png)

5.  **빌드 설정** 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다. 

6. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  **기타 설정** 탭에서 다음을 수행 합니다.

        1.  **스크립팅** **런타임 버전이** **실험적** 이어야 함 (.net 4.6 해당)

        2. **Scripting 백엔드** 는 ***.net*** 이어야 합니다.

        3. **API 호환성 수준은** **.net 4.6** 이어야 합니다.

            ![Unity 프로젝트 설정](images/AzureLabs-Lab7-36.png)

    2.  **게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.

        - **InternetClient**

            ![Unity 프로젝트 설정](images/AzureLabs-Lab7-37.png)

    3.  패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.

        ![Unity 프로젝트 설정](images/AzureLabs-Lab7-38.png)

    

6.  **빌드 설정** 으로 돌아가서 *Unity C#*  프로젝트가 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다. 

7.  빌드 설정 창을 닫습니다.

8.  프로젝트를 저장 합니다 (**파일 > 프로젝트 저장**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>6 장-MLProducts Unity 패키지 가져오기

이 과정에서는 [**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)라고 하는 Unity 자산 패키지를 다운로드 해야 합니다. 이 패키지는 미리 작성 된 모든 개체를 포함 하는 장면으로 완료 되며 모든 개체를 작동 하는 데 집중할 수 있습니다. **ShelfKeeper** 스크립트는 제공 되지만 장면 설정 구조를 위해 공용 변수만 보유 합니다. 다른 모든 섹션을 수행 해야 합니다. 

이 패키지를 가져오려면:

1.  앞의 Unity 대시보드를 사용 하 여 화면 위쪽의 메뉴에서 **자산** 을 클릭 한 다음 **패키지 가져오기, 사용자 지정 패키지를**클릭 합니다.

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-39.png)

2.  파일 선택기를 사용 하 여 **unitypackage** 패키지를 선택 하 고 **열기**를 클릭 합니다.

3.  이 자산의 구성 요소 목록이 표시 됩니다. **가져오기를 클릭 하**여 가져오기를 확인 합니다.

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-40.png)

4.  가져오기가 완료 되 면 Unity **프로젝트 패널**에 몇 가지 새 폴더가 표시 됩니다. 이러한 모델은 작업을 수행 하는 미리 작성 된 장면의 일부인 3D 모델 및 해당 재질입니다. 이 과정에서 대부분의 코드를 작성 합니다.

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-41.png)

5.  **프로젝트 패널** 폴더 내에서 **장면** 폴더를 클릭 하 고 내부 장면 ( **MR_MachineLearningScene**이라고 함)을 두 번 클릭 합니다. 장면이 열립니다 (아래 이미지 참조). 빨간색 다이아몬드가 없는 경우 **게임 패널**의 오른쪽 위에 있는 **gizmo 그리려면** 단추를 클릭 하면 됩니다.

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>7 장-Unity에서 Dll 검사

직렬화 및 역직렬화에 사용 되는 JSON 라이브러리의 사용을 활용 하기 위해 Newtonsoft.json DLL은에서 가져온 패키지를 사용 하 여 구현 되었습니다. 라이브러리에 올바른 구성이 있어야 합니다 (특히 코드가 작동 하지 않는 문제가 있는 경우). 

이렇게 하려면

-  플러그 인 폴더 안의 Newtonsoft.json 파일을 마우스 왼쪽 단추를 클릭 하 고 **검사기 패널**을 확인 합니다. **모든 플랫폼이** 선택 인지 확인 합니다. **UWP 탭** 으로 이동 하 여 **처리 안 함** 이 선택 인지 확인 합니다.

    ![Unity에서 Dll 가져오기](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>8 장-ShelfKeeper 클래스 만들기

**ShelfKeeper** 클래스는 장면에서 생성 된 UI 및 제품을 제어 하는 메서드를 호스팅합니다.

가져온 패키지의 일부로이 클래스는 완료 되지 않았지만 제공 됩니다. 이제 해당 클래스를 완료 하는 시간입니다.

1.  **Scripts** 폴더에서 **ShelfKeeper** 스크립트를 두 번 클릭 하 여 **Visual Studio 2017**을 사용 하 여 엽니다.

2.  스크립트에 있는 모든 코드를 다음 코드로 바꿉니다 .이 코드는 시간 및 날짜를 설정 하 고 메서드를 사용 하 여 제품을 표시 합니다.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  **Unity**로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.

4.  Unity 편집기로 돌아가서 **ShelfKeeper** 클래스가 아래와 동일한 지 확인 합니다.

    ![ShelfKeeper 클래스 만들기](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > 스크립트에 참조 대상이 없으면 (예: *날짜 (텍스트 메시)* ) **계층 패널**에서 대상 필드로 해당 개체를 끌어 놓기만 하면 됩니다. 필요한 경우 아래에서 설명을 참조 하세요.
    > 
    > 1.  **ShelfKeeper** 구성 요소 스크립트를 마우스 왼쪽 단추를 클릭 하 여 **생성 지점** 배열을 엽니다. 하위 섹션은 배열 크기를 나타내는 **size**라는 것으로 나타납니다. **크기** 옆의 텍스트 상자에 **3** 을 입력 하 고 **enter**키를 누릅니다. 그러면 아래에 세 개의 슬롯이 생성 됩니다.
    > 2. **계층 구조** 내에서 해당 개체 옆에 있는 화살표를 마우스 왼쪽 단추를 클릭 하 여 **시간 표시** 개체를 확장 합니다. 다음으로, **검사기** 가 해당 정보를 표시 하도록 **계층 구조**내에서 ***주 카메라*** 를 클릭 합니다.
    > 3. **계층 패널**에서 **주 카메라** 를 선택 합니다. **계층 패널** 의 **날짜** 및 **시간** 개체를 **ShelfKeeper** 구성 요소에 있는 **주 카메라** 의 **검사기** 내에서 **날짜 텍스트** 및 **시간 텍스트** 슬롯으로 끕니다.
    > 4. 이미지에 표시 된 것 처럼 **계층 패널** ( *선반* 개체 아래)의 **생성** 지점을 **3 개의** **요소** 참조 대상으로 끌어옵니다.
    > 
    >     ![ShelfKeeper 클래스 만들기](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>9 장-제품 예측 클래스 만들기

만들려는 다음 클래스는 **제품 예측** 클래스입니다.

이 클래스는 다음을 담당 합니다.

-   현재 날짜 및 시간을 제공 하 여 **Machine Learning 서비스** 인스턴스를 쿼리 합니다.

-   JSON 응답을 사용 가능한 데이터로 deserialize 합니다.

-   데이터 해석, 3 개의 권장 제품 검색

-   **ShelfKeeper** 클래스 메서드를 호출 하 여 장면의 데이터를 표시 합니다.

이 클래스를 만들려면:

1.  **프로젝트 패널**의 **스크립트** 폴더로 이동 합니다.

2.  폴더 내부를 마우스 오른쪽 단추로 클릭 하 >  **C# 스크립트**를 **만듭니다** . 스크립트 **제품 예측**을 호출 합니다.

3.  새 **제품 예측** 스크립트를 두 번 클릭 하 여 **Visual Studio 2017**에서 엽니다.

4.  **파일 수정이 검색 되었습니다** . 대화 상자가 나타나면 ***솔루션 다시 로드**를 클릭 합니다.

5.  제품 예측 클래스의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  **제품 예측** 클래스 내에서 여러 중첩 클래스로 구성 된 다음 두 개체를 삽입 합니다. 이러한 클래스는 Machine Learning 서비스에 대 한 JSON을 serialize 및 deserialize 하는 데 사용 됩니다.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  그런 다음 앞의 코드 위에 다음 변수를 추가 합니다. JSON 관련 코드는 스크립트의 맨 아래, 다른 모든 코드 아래, 그 밖의 코드 아래에 있습니다.

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Machine Learning 포털에서 여기에 있는 **기본 키** 와 **요청-응답 끝점**을 변수에 삽입 해야 합니다. 아래 이미지는에서 키와 끝점을 가져온 위치를 보여 줍니다. 
    >  
    > ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-53-2.png)

8.  **Start ()** 메서드 내에이 코드를 삽입 합니다. **Start ()** 메서드는 클래스가 초기화 될 때 호출 됩니다.

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  다음은 Windows에서 날짜 및 시간을 수집 하 고이를 Machine Learning 실험에서 테이블에 저장 된 데이터와 비교 하는 데 사용할 수 있는 형식으로 변환 하는 메서드입니다.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. 이 클래스는 사용 하지 않으므로 **Update ()** 메서드를 **삭제할** 수 있습니다.

11. 현재 날짜와 시간을 Machine Learning 끝점에 전달 하 고 JSON 형식으로 응답을 수신 하는 다음 메서드를 추가 합니다.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. JSON 응답을 deserialize 하 고 deserialization 결과를 **ShelfKeeper** 클래스에 전달 하는 다음 메서드를 추가 합니다. 이 결과는 현재 날짜 및 시간에 가장을 판매 하기 위해 예측 된 세 항목의 이름입니다. 이전 메서드 아래의 **제품 예측** 클래스에 아래 코드를 삽입 합니다.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. **Visual Studio** 를 저장 하 고 **Unity**에 다시 헤드를 저장 합니다.

14. **스크립트** 폴더의 **제품 예측** 클래스 스크립트를 **기본 카메라** 개체로 끌어 놓습니다.

15. 장면 및 프로젝트 **파일** 을 저장 하 > **장면/파일** > 저장 **프로젝트**를 저장 합니다.

## <a name="chapter-10---build-the-uwp-solution"></a>10 장-UWP 솔루션 빌드

이제 프로젝트가 독립 실행형 응용 프로그램으로 실행 될 수 있도록 프로젝트를 UWP 솔루션으로 빌드할 시간입니다.

빌드:

1.  **파일** > **장면 저장**을 클릭 하 여 현재 장면을 저장 합니다.

2.  **파일** > **빌드 설정** 으로 이동

3.  **Unity C# 프로젝트** 라는 상자를 선택 합니다 .이는 빌드 완료 후 클래스를 편집할 수 있도록 하기 때문에 중요 합니다.

4.  열려 있는 **장면 추가**를 클릭 합니다.

5.  **빌드**를 클릭합니다.

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-54.png)

6.  솔루션을 빌드하는 데 사용할 폴더를 선택 하 라는 메시지가 표시 됩니다.

7.  **빌드** 폴더를 만들고 해당 폴더 내에서 원하는 적절 한 이름을 사용 하 여 다른 폴더를 만듭니다.

8.  새 폴더를 클릭 한 다음 **폴더 선택**을 클릭 하 여 해당 위치에서 빌드를 시작 합니다.

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-55.png)

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-56.png)

9.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)

## <a name="chapter-11---deploy-your-application"></a>11 장-응용 프로그램 배포

응용 프로그램을 배포 하려면:

1.  새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.

2.  Visual Studio를 연 상태에서 NuGet 패키지를 복원 해야 합니다 .이 작업은 솔루션 탐색기 (Visual Studio의 오른쪽에 있음)에서 MachineLearningLab_Build 솔루션을 마우스 오른쪽 단추로 클릭 한 다음 NuGet 패키지 복원을 클릭 하 여 수행할 수 있습니다.

    ![NuGet 패키지 추가](images/AzureLabs-Lab7-57.png)

3.  솔루션 구성에서 **디버그**를 선택 합니다.

4.  솔루션 플랫폼에서 **x86**, **로컬 컴퓨터**를 선택 합니다. 

    > Microsoft HoloLens의 경우 컴퓨터에 테더 링 된 하지 않도록 *원격 컴퓨터*를 설정 하는 것이 더 쉬울 수 있습니다. 그러나 다음을 수행 해야 합니다.
    > - HoloLens의 **IP 주소** 를 알고 있습니다. *설정 > 네트워크 & 인터넷 > Wi-fi > 고급 옵션*에서 찾을 수 있습니다. IPv4는 사용 해야 하는 주소입니다. 
    > - **개발자 모드가** **설정**되어 있는지 확인 합니다. *개발자를 위한 업데이트 & 보안 > > 설정*에서 찾을 수 있습니다.

    ![NuGet 패키지 추가](images/AzureLabs-Lab7-58.png)

5.  **빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 PC에 테스트용으로 로드.

6.  이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.

Mixed Reality 응용 프로그램을 실행 하는 경우 Unity 장면에 설정 된 도구를 볼 수 있으며, 초기화에서 Azure 내에 설정 된 데이터가 인출 됩니다. 데이터는 응용 프로그램 내에서 deserialize 되며, 현재 날짜 및 시간에 대 한 세 가지 상위 결과가 시각적으로 제공 됩니다.


## <a name="your-finished-machine-learning-application"></a>완성 된 Machine Learning 응용 프로그램
 
축 하 합니다. Azure Machine Learning를 활용 하 여 데이터 예측을 만들고 장면에 표시 하는 혼합 현실 앱을 빌드 했습니다.

![NuGet 패키지 추가](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>조사할

**연습 1**

응용 프로그램의 정렬 순서를 실험 하 고이 데이터가 유용할 수 있으므로 세 개의 하위 예측이 선반에 표시 되도록 합니다.

**연습 2**

**Azure 테이블** 을 사용 하 여 새 테이블에 날씨 정보를 채우고 데이터를 사용 하 여 새 실험을 만듭니다.
