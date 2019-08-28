---
title: MR 및 Azure 302b-사용자 지정 비전
description: 이 과정을 완료 하 여 machine learning 모델을 학습 한 다음 학습 된 모델을 사용 하 여 혼합 현실 응용 프로그램 내에서 유사한 개체를 인식 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 사용자 지정 비전, hololens, 몰입 형, vr
ms.openlocfilehash: b173648e2e829e94e47306277bd7814a19842cae
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047217"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR 및 Azure 302b: 사용자 지정 비전

이 과정에서는 혼합 현실 응용 프로그램에서 Azure Custom Vision 기능을 사용 하 여 제공 된 이미지 내에서 사용자 지정 시각적 콘텐츠를 인식 하는 방법을 알아봅니다.

이 서비스를 사용 하면 개체 이미지를 사용 하 여 기계 학습 모델을 학습 시킬 수 있습니다. 그러면 학습 된 모델을 사용 하 여 Microsoft HoloLens의 카메라 캡처 또는 모던 (VR 용 PC) 헤드셋에 연결 된 카메라에 의해 제공 되는 것과 유사한 개체를 인식할 수 있습니다.

![과정 결과](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision는 개발자가 사용자 지정 이미지 분류자를 빌드할 수 있게 해 주는 Microsoft 인지 서비스입니다. 이러한 분류자는 새 이미지와 함께 사용 하 여 새 이미지 내의 개체를 인식 하거나 분류할 수 있습니다. 이 서비스는 간단 하 고 사용 하기 쉬운 온라인 포털을 제공 하 여 프로세스를 간소화 합니다. 자세한 내용은 [Azure Custom Vision Service 페이지](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)를 참조 하세요.

이 과정을 완료 하면 다음과 같은 두 가지 모드로 작업할 수 있는 혼합 현실 응용 프로그램이 만들어집니다.

-   **분석 모드**: 이미지를 업로드 하 고, 태그를 만들고, 서비스를 학습 하 여 다른 개체 (이 경우 마우스 및 키보드)를 인식할 수 있도록 하 여 Custom Vision Service를 수동으로 설정 합니다. 그런 다음 카메라를 사용 하 여 이미지를 캡처하는 HoloLens 앱을 만들고 실제 세계에서 해당 개체를 인식 해 봅니다.

-   **학습 모드**: 앱에서 "학습 모드"를 사용 하는 코드를 구현 합니다. 학습 모드에서는 HoloLens 카메라를 사용 하 여 이미지를 캡처하고, 캡처한 이미지를 서비스에 업로드 하 고, 사용자 지정 비전 모델을 학습할 수 있습니다.

이 과정을 통해 Custom Vision Service에서 Unity 기반 샘플 응용 프로그램으로 결과를 가져오는 방법을 배울 수 있습니다. 빌드할 수 있는 사용자 지정 응용 프로그램에 이러한 개념을 적용 하는 것이 좋습니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 302b: 사용자 지정 비전</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서 주로 HoloLens에 초점을 맞춘 반면,이 과정에서 배운 내용을 Windows Mixed Reality 모던 (VR) 헤드셋에도 적용할 수 있습니다. 모던 (VR) 헤드셋은 액세스할 수 있는 카메라를 포함 하지 않으므로 PC에 연결 된 외부 카메라가 필요 합니다. 이 과정을 진행 하면서 모던 (VR) 헤드셋을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다. [도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- 모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC
- [개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)
- PC에 연결 된 카메라 (몰입 형 헤드셋 개발용)
- Azure 설정 및 Custom Vision API 검색을 위한 인터넷 액세스
- Custom Vision Service에서 인식 하고자 하는 각 개체에 대해 5 개 이상의 이미지 (10 개 이상 권장)를 표시 합니다. 원할 경우 [이 과정에서 이미 제공 된 이미지 (컴퓨터 마우스 및 키보드) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)를 사용할 수 있습니다.

## <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
2.  HoloLens를 설정 하 고 테스트 합니다. HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다. 
3.  새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음). 

보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens-2)대 한 다음 링크를 참조 하세요.

센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.

## <a name="chapter-1---the-custom-vision-service-portal"></a>1 장-Custom Vision Service 포털

Azure에서 *Custom Vision Service* 을 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.

1.  먼저 [ *Custom Vision Service* 기본 페이지로 이동](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)합니다.

2.  **시작** 단추를 클릭 합니다.

    ![](images/AzureLabs-Lab302b-01.png)

3.  *Custom Vision Service* 포털에 로그인 합니다.

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

4.  처음으로 로그인 한 후에는 *서비스 사용 약관* 패널이 표시 됩니다. 확인란을 클릭 하 여 약관에 동의 합니다. 그런 다음 **동의 함**을 클릭 합니다.

    ![](images/AzureLabs-Lab302b-03.png)

5.  조건에 동의한 경우 포털의 *프로젝트* 섹션으로 이동 됩니다. **새 프로젝트**를 클릭 합니다.

    ![](images/AzureLabs-Lab302b-04.png)

6.  탭이 오른쪽에 표시 되 고 프로젝트의 일부 필드를 지정 하 라는 메시지가 표시 됩니다.

    1.  프로젝트의 *이름을* 삽입 합니다.

    2.  프로젝트에 대 한 *설명을* 삽입 합니다 (*선택 사항*).

    3.  리소스 그룹을 선택 하거나 새 *리소스 그룹* 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

    4. *프로젝트 형식을* **분류** 로 설정
    
    5. *도메인* 을 **일반**으로 설정 합니다.

        ![](images/AzureLabs-Lab302b-05.png)

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.

7.  작업이 완료 되 면 **프로젝트 만들기**를 클릭 하면 Custom Vision Service 프로젝트 페이지로 리디렉션됩니다.

## <a name="chapter-2---training-your-custom-vision-project"></a>2 장-Custom Vision 프로젝트 학습

Custom Vision 포털에서 기본 목표는 이미지의 특정 개체를 인식할 수 있도록 프로젝트를 학습 하는 것입니다. 응용 프로그램에서 인식 하는 각 개체에 대해 10 개 이상의 이미지가 필요 하지만 10 개 이상 필요 합니다. [이 과정에서 제공 되는 이미지 (컴퓨터 마우스 및 키보드)를 사용할 수](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)있습니다. 

Custom Vision Service 프로젝트를 학습 하려면:

1.  태그 옆에 있는 **단추를클릭+** 합니다.

    ![](images/AzureLabs-Lab302b-06.png)

2.  인식할 개체의 **이름을** 추가 합니다. **저장**을 클릭 합니다.

    ![](images/AzureLabs-Lab302b-07.png)

3.  **태그가** 추가 된 것을 확인할 수 있습니다 (표시 되기 위해 페이지를 다시 로드 해야 할 수 있음). 확인란이 아직 선택 되어 있지 않은 경우 새 태그 옆에 있는 확인란을 클릭 합니다.

    ![](images/AzureLabs-Lab302b-08.png)

4.  페이지의 가운데에 있는 **이미지 추가** 를 클릭 합니다.

    ![](images/AzureLabs-Lab302b-09.png)

5.  **로컬 파일 찾아보기**를 클릭 하 고, 업로드할 이미지를 검색 한 다음 선택 하 고 최소 5 (5)를 선택 합니다. 이러한 모든 이미지에는 학습 중인 개체가 포함 되어야 합니다.

    > [!NOTE]
    >  한 번에 여러 이미지를 선택 하 여 업로드할 수 있습니다.

6.  탭에서 이미지를 볼 수 있는 경우 **내 태그** 상자에서 적절 한 태그를 선택 합니다.

    ![](images/AzureLabs-Lab302b-10.png)

7.  **파일 업로드**를 클릭 합니다. 파일이 업로드 되기 시작 합니다. 업로드를 확인 한 후 **완료**를 클릭 합니다.

    ![](images/AzureLabs-Lab302b-11.png)

8.  같은 프로세스를 반복 하 여 **키보드** 라는 새 **태그** 를 만들고 적절 한 사진을 업로드 합니다. 새 태그를 만든 후 *마우스* 를 **선택 취소** 하 여 *이미지 추가* 창을 표시 합니다.

9.  두 태그를 모두 설정 했으면 **학습**을 클릭 하 고 첫 번째 학습 반복이 빌드를 시작 합니다.

    ![](images/AzureLabs-Lab302b-12.png)

10. 빌드된 후에는 **기본** 및 **예측 URL**이라는 두 개의 단추를 볼 수 있습니다. 먼저 **기본 설정** 을 클릭 한 다음 **예측 URL**을 클릭 합니다.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > 이에서 제공 하는 끝점 URL은 모든 *반복* 이 기본값으로 표시 된 것으로 설정 됩니다. 따라서 나중에 새 *반복* 을 만들고 기본값으로 업데이트할 경우에는 코드를 변경할 필요가 없습니다.

11. *예측 url*을 클릭 한 후에는 *메모장*을 열고, 코드에서 나중에 필요할 때 검색할 수 있도록 **url** 및 **예측 키**를 복사 하 여 붙여넣습니다.

    ![](images/AzureLabs-Lab302b-14.png)

12. 화면 오른쪽 위에 있는 **코그** 를 클릭 합니다.

    ![](images/AzureLabs-Lab302b-15.png)

13. **학습 키** 를 복사 하 여 나중에 사용할 수 있도록 *메모장*에 붙여넣습니다.

    ![](images/AzureLabs-Lab302b-16.png)

14. 또한 **프로젝트 Id**를 복사 하 고 나중에 사용할 수 있도록 *메모장* 파일에 붙여 넣습니다.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

1.  *Unity* 를 열고 **새로 만들기**를 클릭 합니다.

    ![](images/AzureLabs-Lab302b-17.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. **AzureCustomVision을 삽입 합니다.** 프로젝트 템플릿이 **3d**로 설정 되었는지 확인 합니다. 위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다. 그런 다음 **프로젝트 만들기**를 클릭 합니다.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다. **기본 설정* *편집*  > * 으로 이동한 다음 새 창에서 **외부 도구** 로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![](images/AzureLabs-Lab302b-19.png)

4.  그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 **유니버설 Windows 플랫폼**을 선택한 후 **플랫폼 전환** 단추를 클릭 하 여 선택 항목을 적용 합니다.

    ![](images/AzureLabs-Lab302b-20.png)

5.  아직 **파일 > 빌드 설정을** 사용 하 고 있는지 확인 합니다.

    1.  **대상 장치가** **Hololens** 로 설정 됨

        > 모던 헤드셋의 경우 **대상 장치** 를 *모든 장치로*설정 합니다.
        
    2.  **빌드 형식이** **D3D** 로 설정 됩니다.
    3.  **SDK** 가 **최신 설치** 로 설정 됨
    4.  **Visual Studio 버전이** **최신 설치** 로 설정 됨
    5.  **빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨
    6.  장면을 저장 하 고 빌드에 추가 합니다. 

        1. 이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다. 저장 창이 표시 됩니다.

            ![](images/AzureLabs-Lab302b-21.png)

        2. 이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음

            ![](images/AzureLabs-Lab302b-22.png)

        3. 새로 만든 **장면** 폴더를 연 다음 *파일 이름:* 텍스트 필드에 **CustomVisionScene**를 입력 하 고 **저장**을 클릭 합니다.

            ![](images/AzureLabs-Lab302b-23.png)

            > Unity 프로젝트와 연결 되어 있어야 하므로 *자산* 폴더 내에 unity 장면을 저장 해야 합니다. 배경 폴더 (및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구조화 하는 일반적인 방법입니다.
            
    7.  *빌드 설정*의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.

        ![](images/AzureLabs-Lab302b-24.png)

6.  *빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  **기타 설정** 탭에서 다음을 수행 합니다.

        1.  **Scripting Runtime 버전** 은 **실험적 (.Net 4.6 이와 동일)** 이어야 하며,이 경우 편집기를 다시 시작 해야 합니다.

        2. **Scripting 백엔드** 는 **.net** 이어야 합니다.

        3. **API 호환성 수준은** **.net 4.6** 이어야 합니다.

        ![](images/AzureLabs-Lab302b-25.png)

    2.  **게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.

        1. **InternetClient**

        2.  **웹캠**

        3. **마이크로**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.

    ![](images/AzureLabs-Lab302b-27.png)

8.  *빌드 설정* 으로 돌아가기 *Unity C\# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다 .이 옆의 확인란을 선택 합니다.

9.  빌드 설정 창을 닫습니다.

10.  장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>4 장-Unity에서 Newtonsoft.json DLL 가져오기

> [!IMPORTANT]
> 이 과정의 *Unity 설정* 구성 요소를 건너뛰고 바로 코드를 계속 진행 하려면이 [302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)를 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [6 장에서 계속 진행 합니다. ](#chapter-6---create-the-customvisionanalyser-class).

이 과정에서는 **newtonsoft.json** 라이브러리를 사용 해야 합니다 .이 라이브러리는 자산에 DLL로 추가할 수 있습니다. 이 라이브러리를 포함 하는 패키지는 [이 링크에서 다운로드할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Newtonsoft.json 라이브러리를 프로젝트로 가져오려면이 과정에서 제공 되는 Unity 패키지를 사용 합니다.

1.  **자산* *가져오기 패키지* 사용자 지정 패키지 메뉴 옵션을 사용 하 여 unitypackage을 Unity에 추가 합니다. >  > *

2.  표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** 을 포함 하 여 모든 항목을 선택 했는지 확인 합니다.

    ![](images/AzureLabs-Lab302b-28.png)

3.  **가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.

4.  프로젝트 뷰에서 **플러그 인** 의 **newtonsoft.json** 폴더로 이동 하 고 *newtonsoft.json 플러그 인*을 선택 합니다.

    ![](images/AzureLabs-Lab302b-29.png)

5.  *Newtonsoft.json 플러그 인* 을 선택 하 고 **모든 플랫폼이** 선택 **취소**되어 있는지 확인 한 다음 **WSAPlayer** 도 **선택 취소**되어 있는지 확인 하 고 **적용**을 클릭 합니다. 이는 파일이 올바르게 구성 되었는지 확인 하기 위한 것입니다.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > 이러한 플러그 인을 표시 하면 Unity 편집기 에서만 사용 하도록 구성 됩니다. WSA 폴더에는 프로젝트를 Unity에서 내보낸 후에 사용 되는 다른 집합이 있습니다.

6.  다음으로 **newtonsoft.json** 폴더 내에서 **WSA** 폴더를 열어야 합니다. 방금 구성한 파일의 복사본이 표시 됩니다. 파일을 선택 하 고 검사기에서 다음을 확인 합니다.
    -   **모든 플랫폼이** **선택 취소** 되어 있음 
    -   **만** **WSAPlayer** **확인** 됨
    -   **Dont 프로세스** 를 **선택 했습니다** .

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>5 장-카메라 설정

1.  계층 패널에서 *기본 카메라*를 선택 합니다.

2.  선택한 후에는 *검사기 패널*에서 *주 카메라* 의 모든 구성 요소를 볼 수 있습니다.

    1.  *카메라* 개체의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).

    2.  기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).

    3.  **변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.

    4.  **Clear 플래그** 를 **단색** 으로 설정 합니다. 몰입 형 헤드셋의 경우이를 무시 합니다.

    5.  카메라 구성 요소의 **배경색** 을 **검은색, 알파 0 (16 진수 코드: #00000000)** 으로 설정 합니다 (몰입 형 헤드셋의 경우 무시).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>6 장-CustomVisionAnalyser 클래스 만들기

이 시점에서 일부 코드를 작성할 준비가 되었습니다.

*CustomVisionAnalyser* 클래스로 시작 합니다.

> [!NOTE]
> 아래에 표시 된 코드에서 **Custom Vision Service** 호출은 **Custom Vision REST API**를 사용 하 여 수행 됩니다. 이를 사용 하 여이 API를 구현 하 고 사용 하는 방법을 확인할 수 있습니다 (사용자가 직접 비슷한 항목을 구현 하는 방법을 이해 하는 데 유용). Microsoft는 서비스를 호출 하는 데 사용할 수 있는 **CUSTOM VISION SERVICE SDK** 를 제공 합니다. 자세한 내용은 [CUSTOM VISION SERVICE SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) 문서를 참조 하세요.

이 클래스는 다음을 담당 합니다.

-   캡처된 최신 이미지를 바이트 배열로 로드 하 고 있습니다.

-   분석을 위해 바이트 배열을 Azure *Custom Vision Service* 인스턴스로 보냅니다.

-   JSON 문자열로 응답을 수신 합니다.

-   응답을 deserialize 하 고 결과 *예측* 을 *SceneOrganiser* 클래스에 전달 하 여 응답이 표시 되는 방법을 처리 합니다.

이 클래스를 만들려면:

1.  *프로젝트 패널*에 있는 *자산 폴더* 를 마우스 오른쪽 단추로 클릭 한 다음 **> 폴더 만들기**를 클릭 합니다. 폴더 **스크립트**를 호출 합니다.

    ![](images/AzureLabs-Lab302b-33.png)

2.  위에서 만든 폴더를 두 번 클릭 하 여 엽니다.

3.  폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음,**C\# 스크립트** **만들기** > 를 클릭 합니다. 스크립트 이름을 *CustomVisionAnalyser*로 합니다.

4.  새 *CustomVisionAnalyser* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.

5.  다음과 일치 하도록 파일 위쪽에서 네임 스페이스를 업데이트 합니다.

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  *CustomVisionAnalyser* 클래스에서 다음 변수를 추가 합니다.

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
    > **예측 키** 를 **predictionKey** 변수에 삽입 하 고 **예측 끝점** 을 **predictionEndpoint** 변수에 삽입 했는지 확인 합니다. 이 과정의 앞부분에서 *메모장* 에 복사 했습니다.

7.  이제 initialize **()** 에 대 한 코드를 추가 하 여 인스턴스 변수를 초기화 해야 합니다.

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

8.  **Start ()** 및 **Update ()** 메서드를 삭제 합니다.

9.  그런 다음 *ImageCapture* 클래스에서 캡처된 이미지의 분석 결과를 가져오는 코 루틴 (아래 정적 **GetImageAsByteArray ()** 메서드 포함)를 추가 합니다.

    > [!NOTE]
    > **AnalyseImageCapture** 코 루틴에는 아직 만들지 않은 *SceneOrganiser* 클래스에 대 한 호출이 있습니다. 따라서 **해당 줄을 현재 주석으로 처리**합니다.

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

10.  **Unity**로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>7 장-CustomVisionObjects 클래스 만들기

지금 만들 클래스는 *CustomVisionObjects* 클래스입니다.

이 스크립트에는 다른 클래스에서 *Custom Vision Service*에 대 한 호출을 serialize 및 deserialize 하는 데 사용 하는 여러 개체가 포함 되어 있습니다.

> [!WARNING]
> 아래 JSON 구조가 [*Custom Vision 예측 v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)에서 작동 하도록 설정 되었으므로 Custom Vision Service에서 제공 하는 끝점을 기록해 두어야 합니다. 다른 버전이 있는 경우 아래 구조를 업데이트 해야 할 수 있습니다.

이 클래스를 만들려면:

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다. *CustomVisionObjects*스크립트를 호출 합니다.

2.  새 **CustomVisionObjects** 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.

3.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  *CustomVisionObjects* 클래스 내에서 **Start ()** 및 **Update ()** 메서드를 삭제 합니다. 이 클래스는 이제 비어 있어야 합니다.

5.  *CustomVisionObjects* 클래스 **외부** 에 다음 클래스를 추가 합니다. 이러한 개체는 *newtonsoft.json* 라이브러리에서 응답 데이터를 serialize 및 deserialize 하는 데 사용 됩니다.

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a>8 장-VoiceRecognizer 클래스 만들기

이 클래스는 사용자의 음성 입력을 인식 합니다.

이 클래스를 만들려면:

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다. *VoiceRecognizer*스크립트를 호출 합니다.

2.  새 **VoiceRecognizer** 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.

3.  *VoiceRecognizer* 클래스 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  그런 다음 *VoiceRecognizer* 클래스 내에서 *Start ()* 메서드 위의 다음 변수를 추가 합니다.

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

5.  사용 가능한 **()** 및 **Start ()** 메서드를 추가 합니다. 후자는 이미지에 태그를 연결할 때 인식할 사용자 *키워드* 를 설정 합니다.

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

6.  **Update ()** 메서드를 삭제 합니다.

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

8.  **Unity**로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.

> [!NOTE]
> 오류가 발생 하는 것 처럼 보일 수 있는 코드에 대해 걱정 하지 마세요. 추가 클래스를 곧 제공 하면이 문제를 해결할 수 있습니다.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>9 장-CustomVisionTrainer 클래스 만들기

이 클래스는 일련의 웹 호출을 연결 하 여 *Custom Vision Service*를 학습 합니다. 각 호출은 코드 바로 위에 자세히 설명 되어 있습니다.

이 클래스를 만들려면:

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다. *CustomVisionTrainer*스크립트를 호출 합니다.

2.  새 *CustomVisionTrainer* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.

3.  *CustomVisionTrainer* 클래스 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  그런 다음 *CustomVisionTrainer* 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다. 

    > [!NOTE]
    > 여기에 사용 된 학습 URL은 *Custom Vision 교육 1.2* 설명서에 제공 되며 구조는 다음과 같습니다. https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > 자세한 내용은 [*Custom Vision 학습 v 1.2 참조 API를 참조*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)하세요.

    > [!WARNING]
    > **CustomVisionObjects** 클래스 내에서 사용 되는 JSON 구조가 [*Custom Vision 학습 v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)와 함께 작동 하도록 설정 되었으므로 Custom Vision Service에서 학습 모드를 제공 하는 끝점을 기록해 두어야 합니다. 다른 버전이 있는 경우 *개체* 구조를 업데이트 해야 할 수 있습니다.

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
    > 앞에서 설명한 대로 **서비스 키** (학습 키) 값 및 **프로젝트 Id** 값을 추가 했는지 확인 합니다. 이러한 값은 [과정의 앞부분에서 (2 장, 10 단계부터) 포털에서 수집한](#chapter-2---training-your-custom-vision-project)값입니다.

5.  다음 **Start ()** 및 **활성 ()** 메서드를 추가 합니다. 이러한 메서드는 초기화 시 호출 되며 UI를 설정 하는 호출을 포함 합니다.

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

6.  **Update ()** 메서드를 삭제 합니다. 이 클래스에는이 클래스가 필요 하지 않습니다.

7.  **RequestTagSelection ()** 메서드를 추가 합니다. 이 메서드는 이미지를 캡처하고 장치에 저장 한 후에는이 메서드를 학습 하기 위해 *Custom Vision Service*에 제출할 준비가 되었을 때 가장 먼저 호출 됩니다. 이 메서드는 학습 UI에서 사용자가 캡처된 이미지에 태그를 지정할 때 사용할 수 있는 키워드 집합을 표시 합니다. 또한 *VoiceRecognizer* 클래스에서 음성 입력을 위해 사용자에 게 수신 대기를 시작 하도록 경고 합니다.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  **Verifytag ()** 메서드를 추가 합니다. 이 메서드는 **VoiceRecognizer** 클래스에서 인식 하는 음성 입력을 받고 유효성을 확인 한 다음 학습 프로세스를 시작 합니다.

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

9.  **Submitimagefortraining ()** 메서드를 추가 합니다. 이 메서드는 Custom Vision Service 교육 프로세스를 시작 합니다. 첫 번째 단계는 사용자의 확인 된 음성 입력과 연결 된 서비스에서 **태그 Id** 를 검색 하는 것입니다. **태그 Id** 는 이미지와 함께 업로드 됩니다.

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

10. **TrainCustomVisionProject ()** 메서드를 추가 합니다. 이미지를 제출 하 고 태그를 지정 하면이 메서드가 호출 됩니다. 서비스에 제출 된 모든 이전 이미지와 방금 업로드 한 이미지를 사용 하 여 학습 되는 새 반복을 만듭니다. 교육이 완료 되 면이 메서드는 새로 생성 된 **반복** 을 **기본값으로**설정 하는 메서드를 호출 하 여 분석에 사용 하는 끝점이 최신 학습 된 반복 임을 표시 합니다.

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

11. **SetDefaultIteration ()** 메서드를 추가 합니다. 이 메서드는 이전에 만들어지고 학습 된 반복을 *기본값으로*설정 합니다. 완료 되 면이 메서드는 서비스에서 기존 반복을 삭제 해야 합니다. 이 과정을 작성할 당시에는 서비스에서 동시에 사용할 수 있는 최대 10 개 반복의 제한이 있습니다.

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

12. **DeletePreviousIteration ()** 메서드를 추가 합니다. 이 메서드는 이전의 기본이 아닌 반복을 찾아 삭제 합니다.

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

13. 이 클래스에서 추가 하는 마지막 메서드는 웹 호출에서 바이트 배열로 캡처된 이미지를 변환 하는 데 사용 되는 **GetImageAsByteArray ()** 메서드입니다.

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

14. **Unity**로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>10 장-SceneOrganiser 클래스 만들기

이 클래스는 다음을 수행 합니다.

-   기본 카메라에 연결할 **커서** 개체를 만듭니다.

-   서비스에서 실제 개체를 인식할 때 표시 되는 **레이블** 개체를 만듭니다.

-   적절 한 구성 요소를 연결 하 여 기본 카메라를 설정 합니다.

-   **분석 모드**의 경우 기본 카메라의 위치를 기준으로 적절 한 세계 공간에서 런타임에 레이블을 생성 하 고 Custom Vision Service에서 받은 데이터를 표시 합니다.

-   **학습 모드인**경우 학습 프로세스의 다양 한 단계를 표시 하는 UI를 생성 합니다.

이 클래스를 만들려면:

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다. 스크립트 이름을 *SceneOrganiser*로 합니다.

2.  새 *SceneOrganiser* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.

3.  네임 스페이스는 하나만 필요 하며 *SceneOrganiser* 클래스 위에서 다른 네임 스페이스를 제거 합니다.

    ```csharp
    using UnityEngine;
    ```

4.  그런 다음 *SceneOrganiser* 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.

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

5.  **Start ()** 및 **Update ()** 메서드를 삭제 합니다.

6.  변수 바로 아래에서 해제 **()** 메서드를 추가 하 여 클래스를 초기화 하 고 장면을 설정 합니다.

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

7.  이제 주 카메라 커서를 만들고 배치 하는 **CreateCameraCursor ()** 메서드를 추가 하 고 **CreateLabel ()** 메서드를 추가 하 여 **분석 레이블** 개체를 만듭니다.

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

8. **SetCameraStatus ()** 메서드를 추가 합니다 .이 메서드는 카메라 상태를 제공 하는 텍스트 메시에 사용할 메시지를 처리 합니다.

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

9. **PlaceAnalysisLabel ()** 및 **SetTagsToLastLabel ()** 메서드를 추가 합니다 .이 메서드는 Custom Vision Service에서 장면으로 데이터를 생성 하 고 표시 합니다.

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

10. 마지막으로, 응용 프로그램이 학습 모드일 때 학습 프로세스의 여러 단계를 표시 하는 UI를 생성 하는 **CreateTrainingUI ()** 메서드를 추가 합니다. 또한이 메서드는 카메라 상태 개체를 만들 asha 됩니다.

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

11. **Unity**로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.

> [!IMPORTANT]
> 계속 하기 전에 **CustomVisionAnalyser** 클래스를 열고 **AnalyseLastImageCaptured ()** 메서드 내에서 다음 줄의 *주석 처리를 제거* 합니다.
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>11 장-ImageCapture 클래스 만들기

만들려는 다음 클래스는 *ImageCapture* 클래스입니다.

이 클래스는 다음을 담당 합니다.

-   HoloLens 카메라를 사용 하 여 이미지를 캡처하고 *앱* 폴더에 저장 합니다.

-   사용자 로부터 탭 제스처를 처리 합니다.

-   응용 프로그램을 *분석* 모드에서 실행할지 아니면 *학습* 모드로 실행할지를 결정 하는 *열거형* 값을 유지 관리 합니다.

이 클래스를 만들려면:

1.  이전에 만든 **스크립트** 폴더로 이동 합니다.

2.  폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **> C\# 스크립트 만들기**를 클릭 합니다. 스크립트 이름을 *ImageCapture*로 합니다.

3.  새 **ImageCapture** 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.

4.  파일의 맨 위에 있는 네임 스페이스를 다음으로 바꿉니다.

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  그런 다음 *ImageCapture* 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.

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

6.  이제 **활성 ()** 및 **Start ()** 메서드에 대 한 코드를 추가 해야 합니다.

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

7.  탭 제스처가 발생할 때 호출 되는 처리기를 구현 합니다.

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
    > *분석* 모드에서 **TapHandler** 메서드는 사진 캡처 루프를 시작 하거나 중지 하는 스위치 역할을 합니다.
    >
    > *학습* 모드에서는 카메라에서 이미지를 캡처합니다.
    >
    > 커서가 녹색이 면 카메라에서 이미지를 사용할 수 있음을 의미 합니다.
    >
    > 커서가 빨간색 이면 카메라가 사용 중임을 의미 합니다.

8.  응용 프로그램이 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.

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

9.  사진이 캡처되고 분석 준비가 될 때 호출 되는 처리기를 추가 합니다. 그런 다음 코드가 설정 된 모드에 따라 결과를 *CustomVisionAnalyser* 또는 *CustomVisionTrainer* 에 전달 합니다.

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

10. **Unity**로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.

11. 모든 스크립트가 완료 되었으므로 Unity 편집기로 돌아가서 **scripts** 폴더의 **SceneOrganiser** 클래스를 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다.

## <a name="chapter-12---before-building"></a>12 장-빌드하기 전

응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 HoloLens에 테스트용으로 로드 해야 합니다.

이렇게 하려면 먼저 다음을 확인 해야 합니다.

- [2 장](#chapter-2---training-your-custom-vision-project) 에서 설명한 모든 설정이 올바르게 설정 됩니다.

- **주 카메라**검사기 패널의 모든 필드가 제대로 할당 됩니다.

- **SceneOrganiser** 스크립트는 **주 카메라** 개체에 연결 됩니다.

- **예측 키** 를 **predictionKey** 변수에 삽입 했는지 확인 합니다.

- **예측 끝점** 을 **predictionEndpoint** 변수에 삽입 했습니다.

- *CustomVisionTrainer* 클래스의 **TrainingKey** 변수에 **학습 키** 를 삽입 했습니다.

- *CustomVisionTrainer* 클래스의 **PROJECTID** 변수에 **프로젝트 ID** 를 삽입 했습니다.

## <a name="chapter-13---build-and-sideload-your-application"></a>13 장-응용 프로그램 빌드 및 테스트용으로 로드

*빌드* 프로세스를 시작 하려면 다음을 수행 합니다.

1.  **파일 > 빌드 설정**으로 이동 합니다.

2.  Tick **Unity C\# 프로젝트**.

3.  **빌드**를 클릭합니다. Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 **파일 탐색기** 창을 시작 합니다. 이제 해당 폴더를 만들고 이름을 **App**으로 만듭니다. 그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.

4.  Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.

5.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)

HoloLens에 배포 하려면:

1.  HoloLens의 IP 주소 (원격 배포의 경우)가 필요 하 고 HoloLens가 **개발자 모드**에 있는지 확인 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1.  HoloLens를 입고 하는 동안 **설정을**엽니다.

    2.  **네트워크 & 인터넷** > **wi-fi** > **고급 옵션** 으로 이동 합니다.

    3.  **IPv4** 주소를 적어둡니다.

    4.  그런 다음 **설정**으로 다시 이동한 다음**개발자** 를 위한 **& 보안** > 을 업데이트 합니다.

    5.  **에서 개발자 모드를**설정 합니다.

2.  새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.

3.  *솔루션 구성* 에서 **디버그**를 선택 합니다.

4.  *솔루션 플랫폼*에서 **X86, 원격 컴퓨터**를 선택 합니다. 원격 장치의 **IP 주소** (이 경우에는 HoloLens)를 삽입 하 라는 메시지가 표시 됩니다.

    ![](images/AzureLabs-Lab302b-34.png)

5. **빌드** 메뉴로 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.

6. 이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되어 시작할 준비가 되었습니다!

> [!NOTE]
> 모던 헤드셋에 배포 하려면 **솔루션 플랫폼** 을 *로컬 컴퓨터*로 설정 하 고 **구성을** *디버그*로 설정 하 고 *x 86* 을 **플랫폼**으로 설정 합니다. 그런 다음 **빌드** 메뉴 항목을 사용 하 여 *솔루션 배포*를 선택 하 여 로컬 컴퓨터에 배포 합니다. 

## <a name="to-use-the-application"></a>응용 프로그램을 사용 하려면:

*학습* 모드와 *예측* 모드 간에 앱 기능을 전환 하려면 ImageCapture 클래스 내에 있는 **()** 메서드에 있는 **appmode** 변수를 업데이트 해야 합니다.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
로 구분하거나 여러
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

*학습* 모드:

- **마우스** 또는 **키보드** 를 확인 하 고 **탭 제스처**를 사용 합니다.

- 그런 다음 태그를 제공 하 라는 텍스트가 표시 됩니다.

- **마우스** 또는 **키보드**를 표시 합니다.


*예측* 모드에서:

- 개체를 확인 하 고 **탭 제스처**를 사용 합니다.

- 확률이 가장 높은 개체 (정규화 됨)를 제공 하는 텍스트가 표시 됩니다.

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>14 장-Custom Vision 모델 평가 및 개선

서비스를 보다 정확 하 게 만들려면 예측에 사용 되는 모델을 계속 학습 해야 합니다. 이 작업은 *학습* 및 *예측* 모드 모두에서 새로운 응용 프로그램을 사용 하 여 수행 되며, 후자는이 장에서 설명 하는 포털을 방문 해야 합니다. 모델을 지속적으로 개선 하기 위해 포털을 여러 번 다시 방문할 준비를 해야 합니다.

1. Azure Custom Vision 포털에 다시 이동 하 여 프로젝트에 있는 경우 페이지의 상단 가운데에서 *예측* 탭을 선택 합니다.

    ![](images/AzureLabs-Lab302b-35.png)

2. 응용 프로그램이 실행 되는 동안 서비스에 전송 된 모든 이미지가 표시 됩니다. 이미지를 마우스로 가리키면 해당 이미지에 대해 수행 된 예측이 제공 됩니다.

    ![](images/AzureLabs-Lab302b-36.png)

3. 이미지 중 하나를 선택 하 여 엽니다. 열린 후에는 해당 이미지에 대 한 예측이 오른쪽에 표시 됩니다. 예측이 올바르고이 이미지를 서비스의 학습 모델에 추가 하려는 경우 *내 태그* 입력 상자를 클릭 하 고 연결 하려는 태그를 선택 합니다. 작업이 완료 되 면 오른쪽 아래에 있는 *저장 및 닫기* 단추를 클릭 하 고 다음 이미지를 계속 진행 합니다.

    ![](images/AzureLabs-Lab302b-37.png)

4. 이미지 그리드로 돌아가서 태그를 추가 하 고 저장 한 이미지를 제거할 것을 알 수 있습니다. 태그가 지정 된 항목이 없는 것으로 생각 되는 이미지를 찾은 경우 해당 이미지에서 틱을 클릭 하 고 (여러 이미지에 대해이 작업을 수행할 수 있음) 그리드 페이지의 오른쪽 위 모퉁이에서 *삭제* 를 클릭 하 여 삭제할 수 있습니다. 다음에 나오는 팝업에서 *예, 삭제* 또는 *아니요*를 클릭 하 여 삭제를 확인 하거나 취소할 수 있습니다. 

    ![](images/AzureLabs-Lab302b-38.png)

5. 계속할 준비가 되 면 오른쪽 위에 있는 녹색 *학습* 단추를 클릭 합니다. 서비스 모델은 제공 된 모든 이미지를 사용 하 여 학습 됩니다 (더 정확 하 게 함). 학습을 완료 한 후에는 *기본 설정* 단추를 한 번 더 클릭 하 여 *예측 URL* 에서 서비스의 최신 반복을 계속 사용할 수 있도록 해야 합니다.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>완료 된 Custom Vision API 응용 프로그램

축 하 합니다. Azure Custom Vision API를 활용 하 여 실제 개체를 인식 하 고, 서비스 모델을 학습 하 고, 표시 되는 내용에 대 한 확신을 표시 하는 혼합 현실 앱을 빌드 했습니다.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

**Custom Vision Service** 를 학습 하 여 더 많은 개체를 인식할 수 있습니다.

### <a name="exercise-2"></a>연습 2

학습 한 내용을 확장 하는 방법으로 다음 연습을 완료 합니다.

개체가 인식 될 때 소리를 재생 합니다.

### <a name="exercise-3"></a>연습 3

API를 사용 하 여 응용 프로그램이 분석 하는 것과 동일한 이미지를 사용 하 여 서비스를 다시 학습 하므로 서비스를 보다 정확 하 게 만들 수 있습니다 (예측 및 학습을 동시에 수행).
