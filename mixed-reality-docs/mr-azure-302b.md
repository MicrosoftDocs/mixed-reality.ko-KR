---
title: MR 및 Azure 302b-Custom vision
description: 기계 학습 모델을 학습 하는 방법을 알아보려면이 과정을 완료 하 고 혼합된 현실 응용 프로그램에서 유사한 개체를 인식 하도록 학습된 된 모델을 사용 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 사용자 지정 비전, hololens, 몰입 형, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600000"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR 및 Azure 302b: 사용자 지정 비전

이 과정에서는 배웁니다는 제공 된 이미지 내에서 사용자 지정 시각적 콘텐츠를 인식 하는 방법이 혼합된 현실 응용 프로그램에서 Azure 사용자 지정 비전 기능을 사용 하 여 합니다.

이 서비스를 사용 하면 개체 이미지를 사용 하 여 기계 학습 모델을 학습할 수 있습니다. 그런 다음 Microsoft HoloLens 또는 몰입 형 (VR) 헤드셋에 대 한 사용자 PC에 연결 된 카메라의 카메라 캡처에 의해 제공 된 유사한 개체를 인식 하도록 학습된 된 모델을 사용 합니다.

![과정 결과](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision는 Microsoft Cognitive 서비스 개발자는 사용자 지정 이미지 분류자를 만들 수 있습니다. 이러한 분류자 인식 하도록 새 이미지를 사용 하 여 사용할 수 있습니다 하거나 분류 하 고 새 이미지 내의 개체 지정 합니다. 서비스는 프로세스를 간소화 하는 간단 하 고, 사용 하기 쉬운 온라인 포털을 제공 합니다. 자세한 내용은 참조는 [Azure Custom Vision Service 페이지](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)합니다.

이 과정을 완료 하면 두 가지 모드로 작동할 수 있는 혼합된 현실 응용 프로그램을 갖게 됩니다.

-   **분석 모드**: Custom Vision Service 수동으로 설정 이미지를 업로드, 태그를 만들고, 서비스를 학습 하 여 다른 개체 (이 경우 마우스 및 키보드)를 인식 하도록 합니다. 그런 다음 카메라를 사용 하 여 이미지를 캡처하고 실제 환경에서 이러한 개체를 인식 하는 HoloLens 앱을 만듭니다.

-   **학습 모드**: 앱에서 "학습 모드" 수 있게 해 주는 코드를 구현 합니다. 학습 모드를 사용 하면 HoloLens' 카메라를 사용 하 여 이미지를 캡처, 서비스에 캡처된 이미지를 업로드 및 사용자 지정 비전 모델을 학습 수 있습니다.

이 코스 샘플 Unity 기반 응용 프로그램에 Custom Vision Service에서 결과 가져오는 방법을 배우게 됩니다. 사용자 지정 응용 프로그램을 작성 하려는 경우에 이러한 개념을 적용 하는 것이 됩니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 302b: 사용자 지정 비전</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정 HoloLens에 주로 중점을 두고, 하는 동안 Windows Mixed Reality 몰입 형 (VR) 헤드셋을이 과정에서 배운 적용할 수 있습니다. 몰입 형 (VR) 헤드셋에 액세스할 수 있는 카메라 없기 때문에 PC에 연결 하는 외부 카메라를 해야 합니다. 과정을 따라가려면 정보 몰입 형 (VR) 헤드셋을 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다. 또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다. 내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.

다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.

- 개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용
- [Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여
- 카메라 (몰입 형 헤드셋 개발용) PC에 연결
- Azure 설정 및 사용자 지정 Vision API 검색에 대 한 인터넷 액세스
- 일련의 최소 5 (5) 이미지 (10 개로 권장)를 인식 하도록 Custom Vision Service 원하는 각 개체에 대 한 합니다. 원하는 경우 사용할 수 있습니다 [(컴퓨터 마우스 및 키보드)이이 과정을 통해 이미 제공 되는 이미지 ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)합니다.

## <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
2.  설정 하 고 여 HoloLens를 테스트 합니다. 에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다. 
3.  (때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다. 

보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.

센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.

## <a name="chapter-1---the-custom-vision-service-portal"></a>1 장-Custom Vision Service 포털

사용 하 여 *Custom Vision Service* Azure에서 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.

1.  먼저 [로 이동 합니다 *Custom Vision Service* 기본 페이지](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)합니다.

2.  클릭 합니다 **시작** 단추입니다.

    ![](images/AzureLabs-Lab302b-01.png)

3.  에 로그인 합니다 *Custom Vision Service* 포털입니다.

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

4.  처음으로 로그인 한 후 메시지가 표시 됩니다와 합니다 *서비스 약관* 패널입니다. 약관에 동의 하는 확인란을 클릭 합니다. 클릭 **동의 함**합니다.

    ![](images/AzureLabs-Lab302b-03.png)

5.  조건에 동의 하지, 있습니다를 탐색 합니다 *프로젝트* 포털의 섹션입니다. 클릭할 **새 프로젝트**합니다.

    ![](images/AzureLabs-Lab302b-04.png)

6.  탭은 프로젝트의 일부 필드를 지정 하 라는 메시지가 표시 됩니다는 오른쪽에 표시 됩니다.

    1.  삽입 된 *이름을* 프로젝트에 대 한 합니다.

    2.  삽입 된 *설명을* 프로젝트에 대 한 (*선택적*).

    3.  선택 된 *리소스 그룹* 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).

    4. 설정 된 *프로젝트 형식* 에 **분류**
    
    5. 설정 된 *도메인* 으로 **일반**합니다.

        ![](images/AzureLabs-Lab302b-05.png)

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

7.  완료 되 면 클릭할 **프로젝트 만들기**, Custom Vision Service 프로젝트 페이지를 이동 합니다.

## <a name="chapter-2---training-your-custom-vision-project"></a>2 장-프로젝트에 사용자 지정 비전 교육

한 번 Custom Vision 포털에 기본 목표가 이미지에서 특정 개체를 인식 하도록 프로젝트를 학습 하는 것입니다. 최소 5 개의 이미지 해야 하지만 10 (10)를 인식 하도록 응용 프로그램 원하는 각 개체에 대 한 기본 설정 됩니다. [(컴퓨터 마우스 및 키보드)이이 과정을 통해 제공 되는 이미지를 사용할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)합니다. 

Custom Vision Service 프로젝트를 학습 합니다.

1.  클릭 합니다 **+** 단추 옆에 **태그입니다.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  추가 된 **이름을** 인식 하려는 개체의 합니다. 클릭할 **저장할**합니다.

    ![](images/AzureLabs-Lab302b-07.png)

3.  알 수 있습니다 하 **태그** 추가 되었습니다 (표시에 대 한 페이지를 다시 로드 해야 할). 아직 선택 하지 않은 경우에 새 태그와 함께 확인란을 클릭 합니다.

    ![](images/AzureLabs-Lab302b-08.png)

4.  클릭할 **이미지 추가** 페이지의 가운데에 있습니다.

    ![](images/AzureLabs-Lab302b-09.png)

5.  클릭할 **로컬 파일 찾아보기**를 검색 하 고 최소 되 고 업로드 하려는 이미지를 선택 5 (5). 이러한 이미지의 모든 교육 하는 개체를 포함 해야 해야 합니다.

    > [!NOTE]
    >  업로드 한 번에 여러 이미지를 선택할 수 있습니다.

6.  탭의 이미지를 보시 면에서 적절 한 태그를 선택 합니다 **태그 내** 상자입니다.

    ![](images/AzureLabs-Lab302b-10.png)

7.  클릭할 **파일 업로드**합니다. 파일 업로드를 시작 합니다. 업로드 확인 했으면 클릭 **수행**합니다.

    ![](images/AzureLabs-Lab302b-11.png)

8.  새 동일한 프로세스를 반복 **태그** 라는 **키보드** 에 대 한 적절 한 사진 업로드 합니다. 해야 **선택 취소** *마우스* 표시 하도록 새 태그를 만든 후는 *이미지를 추가할* 창.

9.  태그가 설정 모두를 만든 후 클릭 **학습**, 첫 번째 학습 반복은 개발을 시작 합니다.

    ![](images/AzureLabs-Lab302b-12.png)

10. 을 작성 하는 라는 두 개의 단추를 볼 수는 **기본값으로** 하 고 **예측 URL**합니다. 클릭할 **기본값으로** 첫째, 클릭 **예측 URL**합니다.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > 끝점 URL이 제공 되는 중에 설정 되어 *반복* 기본으로 표시 되었습니다. 따라서 새를 나중에 확인 하는 경우 *반복* 기본값으로 업데이트, 코드를 변경 해야 합니다.

11. 클릭 한 후 *예측 URL*오픈 *메모장*, 복사 및 붙여넣기 합니다 **URL** 및 **예측 키**수 있도록, 코드에서 나중에 필요할 때 검색 합니다.

    ![](images/AzureLabs-Lab302b-14.png)

12. 클릭 합니다 **코그** 맨 위에 있는 화면의 오른쪽입니다.

    ![](images/AzureLabs-Lab302b-15.png)

13. 복사를 **교육 키** 에 붙여 넣습니다를 *메모장*, 나중에 사용할 수 있습니다.

    ![](images/AzureLabs-Lab302b-16.png)

14. 복사할 수도 하 **프로젝트 Id**에 붙여넣습니다 하 *메모장* 나중에 사용할 파일입니다.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 *Unity* 누릅니다 **새로 만들기**합니다.

    ![](images/AzureLabs-Lab302b-17.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. Insert **AzureCustomVision.** 프로젝트 템플릿은 설정 되어 있는지 확인 **3D**합니다. 설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집할* > *기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![](images/AzureLabs-Lab302b-19.png)

4.  이동한 다음 **파일 > 빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환** 선택 항목을 적용 하려면 단추.

    ![](images/AzureLabs-Lab302b-20.png)

5.  여전히 **파일 > 빌드 설정** 되어 있는지 확인 합니다.

    1.  **장치를 대상** 로 설정 된 **Hololens**

        > 몰입 형 헤드셋, 설정 **대상 장치** 하 *모든 장치*합니다.
        
    2.  **빌드 형식** 로 설정 된 **D3D**
    3.  **SDK** 로 설정 된 **가장 최근에 설치 된**
    4.  **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**
    5.  **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**
    6.  장면 저장 하 고 빌드에 추가 합니다. 

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.

            ![](images/AzureLabs-Lab302b-21.png)

        2. 새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.

            ![](images/AzureLabs-Lab302b-22.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름:* 텍스트 필드에 입력 **CustomVisionScene**, 클릭 **저장**합니다.

            ![](images/AzureLabs-Lab302b-23.png)

            > 주의 내에서 Unity 장면에 저장 해야 합니다 *자산* 폴더를 Unity 프로젝트와 연결 해야 합니다. 백그라운드에서 폴더 (및 다른 유사한 폴더)를 만들기 Unity 프로젝트를 구성 하는 일반적인 방법입니다.
            
    7.  설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.

        ![](images/AzureLabs-Lab302b-24.png)

6.  에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한.

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  에 **기타 설정** 탭:

        1.  **스크립팅 런타임 버전** 해야 **실험적 (.NET 4.6 동등)**, 편집기를 다시 시작 해야 실행 합니다.

        2. **백 엔드를 스크립팅** 있어야 **.NET**

        3. **API 호환성 수준** 있어야 **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  내 합니다 **게시 설정** 탭의 **기능**, 확인:

        1. **InternetClient**

        2.  **웹캠**

        3. **Microphone**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.

    ![](images/AzureLabs-Lab302b-27.png)

8.  년대 *빌드 설정* *Unity C\# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.

9.  빌드 설정 창을 닫습니다.

10.  장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>4 장-Unity에서 Newtonsoft DLL 가져오기

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [302b.unitypackage-MR-Azure](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [6 장](#chapter-6---create-the-customvisionanalyser-class)합니다.

이 과정을 사용 해야 합니다 **Newtonsoft** 라이브러리 자산에는 DLL로 추가할 수 있습니다. 포함 하는 패키지 [이 링크에서이 라이브러리를 다운로드할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)합니다.
Newtonsoft 라이브러리를 프로젝트로 가져오는이 과정을 통해 제공 된 Unity 패키지를 사용 합니다.

1.  추가 된 *.unitypackage* 사용 하 여 Unity에는 **자산* > *가져오기* *패키지*  >  *사용자 지정* *패키지** 메뉴 옵션입니다.

2.  에 **Unity 패키지 가져오기** 표시 되는 상자에서 아래에 있는 포함 하 여 모든 것을 확인 **플러그 인** 을 선택 합니다.

    ![](images/AzureLabs-Lab302b-28.png)

3.  클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.

4.  로 이동 합니다 **Newtonsoft** 아래에 폴더 **플러그 인** 프로젝트 보기를 선택 합니다 *Newtonsoft.Json 플러그 인*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  사용 하 여는 *Newtonsoft.Json 플러그 인* 되도록 선택 하면 **Any 플랫폼** 는 **unchecked**, 한지 확인 합니다 **WSAPlayer** 이기도 **unchecked**, 클릭 **적용**합니다. 이 파일이 올바르게 구성 되어 있는지 확인 합니다.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > 이러한 플러그 인을 표시만 Unity 편집기에서 사용 되도록 구성 합니다. Unity에서 프로젝트를 내보낸 후 사용 되는 WSA 폴더에서 다른 집합을 있습니다.

6.  열어야 할 때 다음에 **WSA** 폴더 내에서 합니다 **Newtonsoft** 폴더입니다. 방금 구성한 동일한 파일의 복사본을 볼 수 있습니다. 파일을 선택 하 고 [관리자]에서 확인 하는
    -   **모든 플랫폼** 는 **선택 취소 되어 있음** 
    -   **만** **WSAPlayer** 는 **확인**
    -   **처리 하지 않음** 는 **확인**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>5 장-카메라 설정

1.  계층 구조 창에서 선택 합니다 *주 카메라*합니다.

2.  선택한 후에의 모든 구성 요소를 볼 수는 합니다 *주 카메라* 에 *검사기 패널*합니다.

    1.  합니다 *카메라* 개체의 이름은 **주 카메라** (맞춤법 참고!)

    2.  주 카메라 **태그** 으로 설정 되어 있어야 **MainCamera** (맞춤법 참고!)

    3.  있는지 확인 합니다 **변환 위치** 로 설정 된 **0, 0, 0**

    4.  설정할 **플래그 지우기** 하 **단색** (이 대 한 무시 몰입 형 헤드셋).

    5.  설정 된 **백그라운드** 카메라의 색 구성 요소를 **검정, 알파 0 (16 진수 코드: #00000000)** (이 대 한 무시 몰입 형 헤드셋).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>-6 장 CustomVisionAnalyser 클래스를 만듭니다.

이 시점에서 일부 코드를 작성할 준비가 되었습니다.

사용 하 여 시작 합니다 *CustomVisionAnalyser* 클래스입니다.

> [!NOTE]
> 에 대 한 호출을 **Custom Vision Service** 표시 된 코드에서 다음 사용 하 여 이루어집니다를 **사용자 지정 비전 REST API**합니다. 이 사용 하 여을 통해 구현 (비슷한을 직접 구현 하는 방법을 이해 하는 데 유용함)이이 API를 사용 하는 방법을 표시 됩니다. 인식 하며 Microsoft 제공 하는 수를 **Custom Vision Service SDK** 서비스를 호출 하기 위해 사용할 수도 있는 합니다. 자세한 내용은 참조는 [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) 문서.

이 클래스는 담당 합니다.

-   캡처된 바이트의 배열로 최신 이미지를 로드 합니다.

-   Azure는 바이트 배열 보내기 *Custom Vision Service* 분석에 대 한 인스턴스.

-   JSON 문자열로 응답을 수신 합니다.

-   응답을 역직렬화 하 고 결과 전달 *예측* 에 *SceneOrganiser* 응답을 표시 하는 방법을 처리 하는 클래스입니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 *자산 폴더* 에 *프로젝트 패널*, 클릭 **만들기 > 폴더**합니다. 폴더를 호출 **스크립트**합니다.

    ![](images/AzureLabs-Lab302b-33.png)

2.  열려는 방금 만든 폴더를 두 번 클릭 합니다.

3.  폴더를 마우스 오른쪽 단추로 클릭 **Create** > **C\# 스크립트**합니다. 스크립트 이름을 *CustomVisionAnalyser*합니다.

4.  새 두 번 클릭 *CustomVisionAnalyser* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.

5.  다음과 일치 하도록 파일의 맨 위에 있는 네임 스페이스를 업데이트 합니다.

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  에 *CustomVisionAnalyser* 클래스를 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 삽입 해야 하 **예측 키** 에 **predictionKey** 변수 및 **예측 끝점** 에 **predictionEndpoint** 변수입니다. 에 복사해 둔 *메모장* 과정의 앞부분에 나오는.

7.  에 대 한 코드 **Awake()** 이제 인스턴스 변수를 초기화 하려면 추가 해야 합니다.

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  메서드 삭제 **start ()** 하 고 **update ()** 합니다.

9.  다음으로 코 루틴을 추가 (정적을 사용 하 여 **GetImageAsByteArray()** 아래 메서드)에서 캡처된 이미지의 분석 결과 얻을 합니다 *ImageCapture* 클래스입니다.

    > [!NOTE]
    > 에 **AnalyseImageCapture** 코 루틴을 호출 하는 *SceneOrganiser* 만들려면 아직 수 있는 클래스. 따라서 **이러한 지금은 줄 주석**합니다.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>7-장 CustomVisionObjects 클래스 만들기

만든 클래스에서 이제는 합니다 *CustomVisionObjects* 클래스입니다.

이 스크립트는 다른 클래스를 직렬화 및 역직렬화에 대 한 호출에 사용 되는 개체의 수를 포함 합니다 *Custom Vision Service*합니다.

> [!WARNING]
> Custom Vision Service,으로 제공 하는 끝점 확인을 수행 하는 것은 다음 JSON 구조 설정한 작업할 [ *사용자 지정 비전 예측 v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)합니다. 업데이트 해야 다른 버전이 있는 경우는 아래 구조입니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다. 스크립트를 호출할 *CustomVisionObjects*합니다.

2.  새 두 번 클릭 **CustomVisionObjects** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.

3.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  삭제를 **start ()** 및 **update ()** 내부 메서드를 *CustomVisionObjects* 클래스이 클래스는 이제 비워둘 수 있습니다.

5.  다음 클래스를 추가 **외부** 는 *CustomVisionObjects* 클래스입니다. 사용 되는 이러한 개체는 *Newtonsoft* 응답 데이터 serialize 및 deserialize 하는 라이브러리:

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>8-장 VoiceRecognizer 클래스 만들기

이 클래스는 사용자의 음성 입력을 인식 합니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다. 스크립트를 호출할 *VoiceRecognizer*합니다.

2.  새 두 번 클릭 **VoiceRecognizer** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.

3.  위의 다음 네임 스페이스를 추가 합니다 *VoiceRecognizer* 클래스:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  다음 내에서 다음 변수를 추가 합니다 *VoiceRecognizer* 위의 클래스는 *start ()* 메서드:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  추가 된 **Awake()** 및 **start ()** 메서드는 사용자를 설정 합니다 *키워드* 이미지에 태그를 연결 될 때 인식 되도록 합니다.

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  삭제 된 **update ()** 메서드.

7.  음성 입력이 인식 될 때마다 호출 되는 다음 처리기를 추가 합니다.

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.

> [!NOTE]
> 제공 하는 경우는 추가 클래스는 곧 해결 됩니다에서 오류가 나타날 수 있습니다 하는 코드에 대 한 걱정 마십시오.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>9-장 CustomVisionTrainer 클래스 만들기

이 클래스는 일련의 학습에 웹 호출을 연결 합니다 *Custom Vision Service*합니다. 각 호출 코드를 바로 위에 자세히 설명 되어 있습니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다. 스크립트를 호출할 *CustomVisionTrainer*합니다.

2.  새 두 번 클릭 *CustomVisionTrainer* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.

3.  위의 다음 네임 스페이스를 추가 합니다 *CustomVisionTrainer* 클래스:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  다음 내에서 다음 변수를 추가 합니다 *CustomVisionTrainer* 위의 클래스는 **start ()** 메서드. 

    > [!NOTE]
    > 여기에 학습 URL 내에서 제공 됩니다는 *사용자 지정 비전 교육 1.2* 설명서의 구조 및: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > 자세한 내용은 참조는 [ *v1.2 참조 사용자 지정 비전 교육 API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)합니다.

    > [!WARNING]
    > Custom Vision Service 사용 된 JSON 구조를 학습 모드를 제공 하는 끝점의 참고를 수행 하는 것 (내 합니다 **CustomVisionObjects** 클래스)를 사용 하려면 설정한 [  *사용자 지정 비전 교육 v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)합니다. 업데이트 해야 다른 버전이 있는 경우는 *개체* 구조입니다.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > 추가 해야 하 **서비스 키** (학습 키) 값 및 **프로젝트 Id** 값을 적어둔 이전;이 값은 있습니다 [과정 (이전 포털에서 수집 2 장 이상 10 단계)](#chapter-2---training-your-custom-vision-oroject)합니다.

5.  다음을 추가 합니다 **start ()** 하 고 **Awake()** 메서드. 이러한 메서드 초기화에서 라고 하며 UI 설정에 대 한 호출을 포함 합니다.

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  삭제 된 **update ()** 메서드. 이 클래스에이 필요 하지 않습니다.

7.  추가 된 **RequestTagSelection()** 메서드. 이 메서드는 이미지 캡처 되었으며 장치에 저장 될 때 호출 되는 첫 번째 전송할 준비가 되었습니다 및 합니다 *Custom Vision Service*, 학습 하 합니다. 이 메서드는 사용자는 캡처된 이미지에 태그 지정 하는 데 사용할 수 있습니다 키워드 집합을 학습 UI에에서 표시 됩니다. 에 알림을 제공 합니다 *VoiceRecognizer* 클래스 음성 입력에 대 한 사용자에 게 수신 대기를 시작 합니다.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  추가 된 **VerifyTag()** 메서드. 이 메서드는 인식 음성 입력 받을 합니다 **VoiceRecognizer** 클래스를 사용 하 여 유효성을 확인 하 고 다음 학습 프로세스를 시작 합니다.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  추가 된 **SubmitImageForTraining()** 메서드. 이 메서드는 Custom Vision Service 학습 프로세스를 시작 됩니다. 첫 번째 단계를 검색 하는 것은 **태그 Id** 사용자의 유효성이 검사 된 음성 입력와 연결 된 서비스에서. 합니다 **태그 Id** 은 다음 이미지와 함께 업로드 됩니다.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. 추가 된 **TrainCustomVisionProject()** 메서드. 이미지 제출 되었으며 태그가 지정 되 면이 메서드를 호출 합니다. 서비스 및 이미지에 제출 된 모든 이전 이미지를 사용 하 여 학습을 수행할 수 있는 새로운 반복을 만들어집니다 방금 업로드 한 합니다. 이 메서드가 새로 만든 설정할 메서드를 호출 하 고 학습 완료 되 면 **반복** 으로 **기본**분석을 위해 사용 하는 끝점은 최신 학습된 반복 되도록 합니다.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. 추가 된 **SetDefaultIteration()** 메서드. 이 메서드는 이전에 생성 되 고 학습 된 반복으로 설정 됩니다 *기본*입니다. 완료 되 면이 메서드는 서비스에서 기존 이전 반복을 삭제 해야 합니다. 이 과정을 작성 하는 동시에 최대 10 번 반복 서비스에서 동시에 존재할 수 제한이 됩니다.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. 추가 된 **DeletePreviousIteration()** 메서드. 이 메서드를 찾아 이전 기본이 아닌 반복 삭제:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. 마지막으로 하는 방법으로이 클래스에 추가 합니다 **GetImageAsByteArray()** 메서드 웹 호출에서 사용 하 여 바이트 배열로 캡처된 이미지를 변환할 합니다.

    ```csharp
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

14. 변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>10-장 SceneOrganiser 클래스 만들기

이 클래스는:

-   만들기는 **커서** 주 카메라에 연결 하는 개체입니다.

-   만들기는 **레이블** 서비스는 실제 개체를 인식 하는 경우 표시 되는 개체입니다.

-   적절 한 구성 요소를 연결 하 여 주 카메라를 설정 합니다.

-   에 있는 경우 **분석 모드**, 주 카메라의 위치를 기준으로 적절 한 세계 좌표 공간에서 런타임 시 레이블을 생성 및 Custom Vision Service에서 받은 데이터를 표시 합니다.

-   에 있는 경우 **학습 모드**, 학습 프로세스의 여러 단계를 표시 하는 UI를 생성 합니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다. 스크립트 이름을 *SceneOrganiser*합니다.

2.  새 두 번 클릭 *SceneOrganiser* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.

3.  하나의 네임 스페이스만 해야 위의 다른를 제거 합니다 *SceneOrganiser* 클래스:

    ```csharp
    using UnityEngine;
    ```

4.  다음 내에서 다음 변수를 추가 합니다 *SceneOrganiser* 위의 클래스는 **start ()** 메서드:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  삭제 된 **start ()** 하 고 **update ()** 메서드.

6.  변수를 바로 아래 추가 합니다 **Awake()** 메서드 클래스를 초기화 하 고 장면 설정 합니다.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  이제 추가 합니다 **CreateCameraCursor()** 만들고 주 카메라 커서를 배치 하는 메서드 및 **CreateLabel()** 메서드를 **Analysis 레이블** 개체 .

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. 추가 된 **SetCameraStatus()** 텍스트 메시 카메라의 상태를 제공 하는 메시지를 처리 하는 메서드.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. 추가 합니다 **PlaceAnalysisLabel()** 하 고 **SetTagsToLastLabel()** 생성 되며 장면에 Custom Vision Service의 데이터를 표시 하는 메서드.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. 마지막으로 추가 합니다 **CreateTrainingUI()** 메서드를 응용 프로그램 학습 모드 상태인 경우 학습 프로세스의 여러 단계를 표시 하는 UI를 생성 합니다. 이 메서드는 카메라 상태 개체를 만드는 성능을 활용도 됩니다.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. 변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.

> [!IMPORTANT]
> 계속 하기 전에 엽니다는 **CustomVisionAnalyser** 클래스 및 내 합니다 **AnalyseLastImageCaptured()** 메서드를 *주석 처리를 제거* 다음 줄:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>11-장 ImageCapture 클래스 만들기

다음 클래스를 만드는 것은 *ImageCapture* 클래스입니다.

이 클래스는 담당 합니다.

-   HoloLens 카메라를 사용 하 고 저장 하는 이미지를 캡처하는 *앱* 폴더입니다.

-   사용자에서 탭 제스처를 처리 합니다.

-   유지 관리 합니다 *Enum* 응용 프로그램에서 실행을 결정 하는 값 *분석* 모드 또는 *학습* 모드.

이 클래스를 만들려면:

1.  로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.

2.  폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C\# 스크립트**합니다. 스크립트 이름을 *ImageCapture*합니다.

3.  새 두 번 클릭 **ImageCapture** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.

4.  파일의 맨 위에 있는 네임 스페이스를 다음으로 바꿉니다.

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  다음 내에서 다음 변수를 추가 합니다 *ImageCapture* 위의 클래스는 **start ()** 메서드:

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  탭 제스처 발생할 때 호출 되는 처리기를 구현 합니다.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > *분석* 모드는 **TapHandler** 메서드 역할을 시작 하거나 사진 캡처 루프를 중지 하는 스위치입니다.
    >
    > *교육* 모드 카메라에서 이미지를 캡처하지 것입니다.
    >
    > 커서 녹색 이면 카메라는 이미지를 사용할 수를 의미 합니다.
    >
    > 커서 빨간색 이면 카메라 사용량이 의미 합니다.

8.  응용 프로그램 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  사진을 캡처한 시간과 분석할 준비가 되었을 때 호출 되는 처리기를 추가 합니다. 결과가 전달 되는 *CustomVisionAnalyser* 또는 *CustomVisionTrainer* 모드에 따라 코드에서 설정 됩니다.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.

11. 모든 스크립트를 완료 했으므로 Unity 편집기에서 돌아가서 누른 채 끌어서 합니다 **SceneOrganiser** 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체는 *계층 패널*합니다.

## <a name="chapter-12---before-building"></a>빌드하기 전에 12 장

응용 프로그램의 철저 한 테스트를 수행 하려면 해야 테스트용으로 로드 하 여 HoloLens에 있습니다.

를 수행 하기 전에 확인 합니다.

- 에 언급 된 모든 설정을 합니다 [Chapter 2](#chapter-2---training-your-custom-vision-project) 올바르게 설정 됩니다.

- 모든 필드를 **주 카메라**, 검사기 패널 올바르게 할당 됩니다.

- 스크립트 **SceneOrganiser** 에 연결할 때 합니다 **주 카메라** 개체입니다.

- 삽입 해야 하 **예측 키** 에 **predictionKey** 변수입니다.

- 삽입 한 사용자 **예측 끝점** 에 **predictionEndpoint** 변수입니다.

- 삽입 한 사용자 **교육 키** 에 **trainingKey** 의 변수를 *CustomVisionTrainer* 클래스입니다.

- 삽입 한 사용자 **프로젝트 ID** 에 **projectId** 의 변수는 *CustomVisionTrainer* 클래스.

## <a name="chapter-13---build-and-sideload-your-application"></a>13 장-빌드 및 테스트용으로 로드 응용 프로그램

시작 하는 *빌드* 프로세스:

1.  로 이동 **파일 > 빌드 설정**합니다.

2.  눈금 **Unity C\# 프로젝트**합니다.

3.  **빌드**를 클릭합니다. Unity가 시작 됩니다는 **파일 탐색기** 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다. 해당 폴더를 이제 만들고 이름을 **앱**합니다. 사용 하 여 다음 합니다 **앱** 폴더를 선택, 클릭 **폴더 선택**합니다.

4.  Unity 프로젝트를 빌드할 예정 된 **앱** 폴더입니다.

5.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.

HoloLens에 배포 합니다.

1.  (배포에 대 한 원격), 여 HoloLens의 IP 주소를 사용 해야 하 고 중인에 HoloLens 되도록 **개발자 모드**합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1.  에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.

    2.  로 이동 **네트워크 및 인터넷** > **Wi-fi** > **고급 옵션**

    3.  참고 합니다 **IPv4** 주소입니다.

    4.  다음으로 다시 이동할 **설정을**, 한 다음 **업데이트 및 보안** > **개발자를 위한**

    5.  설정할 **에서 개발자 모드가**합니다.

2.  새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.

3.  에 *솔루션 구성* 선택 **디버그**합니다.

4.  에 *솔루션 플랫폼*를 선택 **x86, 원격 컴퓨터**합니다. 삽입 하 라는 메시지가 표시 됩니다는 **IP 주소** 원격 장치 (여 HoloLens,이 경우 둔).

    ![](images/AzureLabs-Lab302b-34.png)

5. 로 이동 **빌드할** 메뉴를 클릭 **솔루션 배포** 을 사이드 로드에 HoloLens에 응용 프로그램입니다.

6. 앱에 HoloLens 시작할 준비가에 설치 된 앱 목록에 나타나야 합니다.

> [!NOTE]
> 몰입 형 헤드셋을 배포 하려면 설정 합니다 **솔루션 플랫폼** 를 *로컬 컴퓨터*, 설정 및를 **구성** 에 *디버그*, 를사용하여*x86* 으로 **플랫폼**합니다. 로컬 배포 후 컴퓨터를 사용 하 여는 **빌드** 메뉴 항목을 선택 하 *솔루션 배포*합니다. 

## <a name="to-use-the-application"></a>응용 프로그램을 사용 합니다.

앱 기능 사이 전환할 *교육* 모드 및 *예측* 모드를 업데이트 해야 합니다 **AppMode** 이며 변수는 **Awake()** 내에 있는 메서드를 *ImageCapture* 클래스입니다.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
로 구분하거나 여러
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

*교육* 모드:

- 살펴봅니다 **마우스** 또는 **키보드** 사용 하는 **탭 하기 제스처**합니다.

- 다음으로, 텍스트 태그를 제공 하 라는 메시지가 표시 됩니다.

- 예를 들어 하나 **마우스** 하거나 **키보드**합니다.


*예측* 모드:

- 개체를 살펴보고 사용 합니다 **탭 하기 제스처**합니다.

- 확률이 가장 높은 (이 정규화 된)를 사용 하 여 검색 된 개체를 제공 하 텍스트가 나타납니다.

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>14-장 평가 하 고 사용자 지정 비전 모델을 향상 시키기

서비스를 보다 정확 하 게 확인을 계속 하려면 예측에 사용 된 모델을 학습 해야 합니다. 둘 다를 사용 하 여 새 응용 프로그램을 사용 하 여 이렇게 합니다 *교육* 하 고 *예측* 모드를 사용 하 여이 장에서 다루는 내용는 포털을 방문 하 여 두 번째 요구 합니다. 포털에 여러 번 다시 방문, 모델을 지속적으로 향상 시킬 준비 수 있습니다.

1. 마찬가지로 Azure 사용자 지정 비전 포털로 이동 하 고 프로젝트가 있는 경우 선택 합니다 *예측* 탭 (에서 페이지의 위쪽 가운데):

    ![](images/AzureLabs-Lab302b-35.png)

2. 응용 프로그램을 실행 하는 동안 서비스에 전송 된 모든 이미지 표시 됩니다. 이미지를 가리키면 해당 이미지에 대해 수행 된 예측을 사용 하 여 제공 됩니다.

    ![](images/AzureLabs-Lab302b-36.png)

3. 열려는 이미지 중 하나를 선택 합니다. 열기 되 면 오른쪽에 해당 이미지에 대 한 예측이 표시 됩니다. 수 예측 잘못 되었으며 서비스의 학습 모델에이 이미지를 추가, 클릭 하려는 경우는 *태그 내* 상자 입력과 연결할 태그를 선택 합니다. 완료 되 면 클릭 합니다 *저장 후 닫기* 맨 오른쪽 단추를 다음 이미지는 진행 합니다.

    ![](images/AzureLabs-Lab302b-37.png)

4. 이미지의 그리드로 다시 했으면 하는 태그를 추가 (저장), 이미지를 확인할 수 있습니다 제거 됩니다. 태그가 지정 된 항목 내에 있지 않은 것이 생각 하는 모든 이미지를 찾을 경우 삭제할 수 있습니다 합니다 (이렇게 하려면 여러 이미지에 대 한) 해당 이미지에 눈금을 클릭 하 고 클릭 한 다음 *삭제* 그리드 페이지의 오른쪽 위 모서리에 있습니다. 뒤에 오는 팝업에서 클릭할 수 중 하나 *예, 삭제* 또는 *No*하 여 삭제를 확인 하거나 각각을 취소 합니다. 

    ![](images/AzureLabs-Lab302b-38.png)

5. 계속 하려면 준비가 되었을 때 클릭 녹색 *학습* 오른쪽 위에 있는 단추입니다. 모든 이미지는 이제 제공한 (수 있는 보다 정확 하 게)를 사용 하 여 서비스 모델 학습 됩니다. 학습 완료 되 면 클릭 해야 합니다 *기본값으로* 단추 한 번 더 있도록에 *예측 URL* 계속 가장 최신의 반복입니다. 서비스를 사용 하 여 합니다.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>완성 된 Custom Vision API 응용 프로그램

축, 실제 개체를 인식 하 고, 서비스 모델을 학습, 표시 된 것의 신뢰도 표시 하려면 Azure Custom Vision API를 활용 하는 혼합된 현실 앱을 작성 합니다.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

학습 하 **Custom Vision Service** 자세한 개체를 인식 합니다.

### <a name="exercise-2"></a>연습 2

학습 한 내용으로 확장 하는 방법,으로 다음 연습을 완료 합니다.

개체 인식 되 면 소리를 재생 합니다.

### <a name="exercise-3"></a>연습 3

앱을 분석 하는 동일한 이미지를 사용 하 여 서비스를 다시 학습에 따라서 서비스를 보다 정확 하 게 확인 API를 사용 하 여 (예측 및 교육을 동시에 수행 됨).
