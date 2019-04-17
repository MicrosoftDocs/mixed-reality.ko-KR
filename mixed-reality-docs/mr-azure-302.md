---
title: MR 및 Azure 302-Computer vision
description: 혼합된 현실 응용 프로그램에서 Azure의 Computer Vision을 사용 하 여 제공 된 이미지를 내에서 시각적 콘텐츠를 인식 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 컴퓨터 비전, hololens, 몰입 형, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597890"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR 및 Azure 302: 컴퓨터 비전

이 과정에서는 배웁니다는 제공 된 이미지 내에서 시각적 콘텐츠를 인식 하는 방법이 혼합된 현실 응용 프로그램에서 Azure 컴퓨터 비전 기능을 사용 하 여 합니다.

인식 결과 설명 tags로 표시 됩니다. 기계 학습 모델을 학습 하지 않고도이 서비스를 사용할 수 있습니다. 구현에서 기계 학습 모델을 학습에 필요한 경우 참조 [MR 및 Azure 302b](mr-azure-302b.md)합니다.

![랩 결과](images/AzureLabs-Lab2-000.png)

Microsoft Computer Vision Api 개발자 이미지 처리 및 분석 (사용 하 여 정보를 반환)를 사용 하 여 제공 하도록 설계 된 고급 알고리즘을 사용 하 여 클라우드에서 모든 집합이 있습니다. 개발자는 이미지 또는 이미지 URL을 업로드 하 고 Microsoft Computer Vision API 알고리즘 분석 시각적 콘텐츠를 입력 한 다음 정보를 반환할 수에 있는 사용자 선택에 따라 얼굴 (검색 등 유형 및 이미지의 품질을 식별 합니다. 해당 좌표)를 반환 하 고, 태그 지정 또는 이미지 분류 합니다. 자세한 내용은 참조는 [Azure Computer Vision API 페이지](https://azure.microsoft.com/services/cognitive-services/computer-vision/)합니다.

이 과정을 마치면 다음을 수행 하는 일을 할 수는 HoloLens 응용 프로그램을 혼합된 현실이 제공 됩니다.

1.  탭 제스처를 사용 하 여 HoloLens의 카메라는 이미지를 캡처합니다 됩니다.
2.  이미지는 Azure Computer Vision API Service에 보내집니다. 
3.  인식 개체에서 Unity 장면에 배치 하는 간단한 UI 그룹 나열 됩니다.

응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다. 이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다. 혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 302: 컴퓨터 비전</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정 HoloLens에 주로 중점을 두고, 하는 동안 Windows Mixed Reality 몰입 형 (VR) 헤드셋을이 과정에서 배운 적용할 수 있습니다. 몰입 형 (VR) 헤드셋에 액세스할 수 있는 카메라 없기 때문에 PC에 연결 하는 외부 카메라를 해야 합니다. 과정을 따라가려면 정보 몰입 형 (VR) 헤드셋을 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다. 또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다. 내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 됩니다 있지만 문서 .

다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.

- 개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용
- [Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여
- 카메라 (몰입 형 헤드셋 개발용) PC에 연결
- Azure 설정 및 Computer Vision API 검색에 대 한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
2.  설정 하 고 여 HoloLens를 테스트 합니다. 에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다. 
3.  (때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다. 

보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.

센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.

## <a name="chapter-1--the-azure-portal"></a>1 장-Azure Portal

사용 하는 *Computer Vision API* 서비스가 Azure에서 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.

1.  먼저에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다. 

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

2.  일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 *Computer Vision API*를 클릭 하 고 **Enter**합니다.

    ![Azure에서 새 리소스 만들기](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.
 
3.  새 페이지에 대 한 설명을 제공 합니다는 *Computer Vision API* 서비스입니다. 이 페이지의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.

    ![컴퓨터 비전 api 서비스에 대 한](images/AzureLabs-Lab2-01.png)
 
4.  클릭 한 후 **만들기**:

    1. 원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.
    2. 선택 된 **구독**합니다.
    3. 선택 된 **가격 책정 계층** 첫 번째 경우, 적절 한 시간 만들기를 *Computer Vision API* 서비스, 무료 계층 (F0 라는)를 사용할 수 있어야 합니다.
    4. 선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지). 

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    5. (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹의 위치를 결정 합니다. 위치는 응용 프로그램은 실행할 지역의 것이 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

    6. 이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.
    7. 만들기를 클릭 합니다.

        ![서비스 만들기 정보](images/AzureLabs-Lab2-02.png)

5.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.
6.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![새 서비스에 대 한 새 알림이 나타납니다.](images/AzureLabs-Lab2-03.png) 
 
7.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다. 

    ![리소스를 이동 단추를 선택 합니다.](images/AzureLabs-Lab2-04.png)
 
8. 클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 새 Computer Vision API 서비스 인스턴스로 이동 합니다. 

    ![새 Computer Vision API 서비스](images/AzureLabs-Lab2-05.png)
 
9.  이 자습서에서 응용 프로그램 서비스의 구독 키를 사용 하 여 수행 하는 서비스에 대 한 호출을 수행 해야 합니다.
10. *빠른 시작* 페이지의 프로그램 *Computer Vision API* 서비스에서 첫 번째 단계로 이동 *키 가져오기*, 클릭 **키** ( 또한 이렇게 하려면 열쇠 아이콘을 가리키는 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭 하 여). 이 서비스를 줄이면 *키*합니다.
11. 프로젝트에서 나중에이 필요 하므로 표시 된 키 중 하나가 복사본을 만듭니다. 

12. 로 다시 이동 합니다 *빠른 시작* 페이지 및 여기에서 끝점을 가져옵니다. 회원님의 지역에 따라 다를 수 있습니다 (있는 경우 나중에 코드 변경 확인 해야 합니다). 사용 하 여 나중에이 끝점의 복사본을 수행 합니다.

    ![새 Computer Vision API 서비스](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > 다양 한 끝점은 무엇을 확인할 수 있습니다 [여기](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)합니다. 

## <a name="chapter-2--set-up-the-unity-project"></a>2 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 *Unity* 누릅니다 **새로 만들기**합니다. 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab2-06.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. 삽입 **MR_ComputerVision**합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**합니다. 설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab2-07.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집 > 기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab2-08.png)

4.  이동한 다음 **파일 > 빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환** 선택 항목을 적용 하려면 단추.

    ![빌드 설정 창, uwp 플랫폼 전환 합니다.](images/AzureLabs-Lab2-10.png)

5.  여전히 **파일 > 빌드 설정** 되어 있는지 확인 합니다.

    1. **장치를 대상** 로 설정 된 **HoloLens**

        > 몰입 형 헤드셋, 설정 **대상 장치** 하 *모든 장치*합니다.

    2. **빌드 형식** 로 설정 된 **D3D**
    3. **SDK** 로 설정 된 **가장 최근에 설치 된**
    4. **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**
    5. **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**
    6. 장면 저장 하 고 빌드에 추가 합니다.

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.
        
            ![추가 백그라운드에서 열기 단추를 클릭](images/AzureLabs-Lab2-11.png)

        2. 새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab2-12.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **MR_ComputerVisionScene**, 클릭 **저장** .

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab2-13.png)

            > 주의 내에서 Unity 장면에 저장 해야 합니다 *자산* 폴더를 Unity 프로젝트와 연결 해야 합니다. 백그라운드에서 폴더 (및 다른 유사한 폴더)를 만들기 Unity 프로젝트를 구성 하는 일반적인 방법입니다.

    7. 설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.

6. 에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한. 

    ![플레이어 설정 열기](images/AzureLabs-Lab2-14.png)

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. 에 **기타 설정** 탭:

        1. **스크립팅 런타임 버전** 있어야 **안정적인** (.NET 3.5와 같음).
        2. **백 엔드를 스크립팅** 있어야 **.NET**
        3. **API 호환성 수준** 있어야 **.NET 4.6**

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab2-15.png)
      
    2. 내 합니다 **게시 설정** 탭의 **기능**, 확인:

        1. **InternetClient**
        2. **웹캠**

            ![게시 설정을 업데이트 합니다.](images/AzureLabs-Lab2-16.png)

    3. 패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab2-17.png)

8.  년대 *빌드 설정* _Unity C#_  프로젝트는 더 이상 회색으로;이 옆의 확인란을 선택 합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).

## <a name="chapter-3--main-camera-setup"></a>3 장-주 카메라 설정

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage),으로 프로젝트로 가져올는 [사용자 지정 패키지 ](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [5 장](#chapter-5--create-the-resultslabel-class)합니다.

1.  에 *계층 패널*를 선택 합니다 **주 카메라**합니다. 
2.  선택한 후에의 모든 구성 요소를 볼 수는 합니다 **주 카메라** 에 *검사기 패널*합니다.

    1. 합니다 **카메라 개체** 이름은 **주 카메라** (맞춤법 참고!)
    2. 주 카메라 **태그** 으로 설정 되어 있어야 **MainCamera** (맞춤법 참고!)
    3. 있는지 확인 합니다 **변환 위치** 로 설정 된 **0, 0, 0**
    4. 설정할 **플래그 지우기** 하 **단색** (이 대 한 무시 몰입 형 헤드셋).
    5. 설정 된 **백그라운드** 카메라 구성 요소의 색 **검정, 알파 0 (16 진수 코드: #00000000)** (이 대 한 무시 몰입 형 헤드셋).

        ![카메라 구성 요소를 업데이트 합니다.](images/AzureLabs-Lab2-18.png)
 
3.  에 연결 하는 간단한 "Cursor" 개체를 만들 해야 하는 다음에 **주 카메라**는 이미지 분석을 배치 하는 도움말을 출력 응용 프로그램을 실행 중인 경우. 이 커서는 카메라 포커스의 중심점을 결정 합니다.

커서를 만들려면:

1.  에 *계층 패널*를 마우스 오른쪽 단추로 클릭 합니다 **주 카메라**합니다. 아래 **3D 개체**, 클릭 **구체**합니다.

    ![커서 개체를 선택 합니다.](images/AzureLabs-Lab2-19.png)
 
2.  이름 바꾸기는 **구체** 에 **커서** (커서 개체를 두 번 클릭 하거나 선택한 개체를 사용 하 여 'F2' 키보드 단추를 눌러)를 자식으로 있는 인지 확인 하 고는 **주 카메라**.

3.  에 *계층 패널*, 마우스 왼쪽 단추로 클릭 합니다 **커서**합니다. 선택 커서를 사용 하 여에서 다음 변수를 조정 합니다 *검사기 패널*:

    1. 설정 된 *위치를 변환* 에 **0, 0, 5**
    2. 설정 된 *크기 조정* 에 **0.02, 0.02, 0.02**

        ![변환 위치 및 배율을 업데이트 합니다.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>4 장-레이블 시스템 설치

HoloLens' 카메라를 사용 하 여 이미지를 캡처한 후 해당 이미지에 전송 됩니다 하 *Azure Computer Vision API* 분석에 대 한 서비스 인스턴스. 

해당 분석 결과를 호출 하는 인식할 수 있는 개체 목록이 됩니다 **태그**합니다. 

사진의 찍을 때 위치에서 이러한 태그를 표시할 레이블 (세계 좌표 공간에서 3D 텍스트)를 사용 합니다.

다음 단계에서는 보여 설정 하는 방법의 **레이블** 개체입니다.

1.  계층 구조 창에서 (위치 상관 없이 시점에서)에서 아무 곳 이나 마우스 오른쪽 단추로 클릭 **3D 개체**, 추가 된 **3D 텍스트**합니다. 이름을 **LabelText**합니다.

    ![3D 텍스트 개체를 만듭니다.](images/AzureLabs-Lab2-21.png)
 
2.  에 *계층 패널*, 마우스 왼쪽 단추로 클릭 합니다 **LabelText**합니다. 사용 하 여 합니다 **LabelText** 에서 다음 변수를 조정 옵션을 선택 합니다 *검사기 패널*:

    1. 설정 된 **위치** 에 **0,0,0**
    2. 설정 된 **크기 조정** 에 **0.01, 0.01, 0.01**
    3. 구성 요소의 **텍스트 메시**:
    4. 내에서 모든 텍스트를 바꿉니다 **텍스트**, "..."를 사용 하 여        
    5. 설정 된 **앵커** 에 **중간 Center**
    6. 설정 된 **맞춤** 에 **Center**
    7. 설정 된 **탭 크기** 에 **4**
    8. 설정 된 **글꼴 크기** 에 **50**
    9. 설정 된 **Color** 에 **#FFFFFFFF**

    ![텍스트 구성 요소](images/AzureLabs-Lab2-21-5.png)

3.  끌어서 합니다 **LabelText** 에서 *계층 패널*에 *자산 폴더*내에서에서 *프로젝트 패널*. 이렇게 하면 합니다 **LabelText** Prefab을 한다는 코드에서 인스턴스화될 수 있도록 합니다.

    ![LabelText 개체의 prefab을 만듭니다.](images/AzureLabs-Lab2-22.png)
 
4.  삭제 해야 합니다 **LabelText** 에서 합니다 *계층 패널*여 장면에서 표시 되지 것입니다 있도록 합니다. 호출에서 개별 인스턴스에 대 한 자산 폴더에서는 prefab을 지금 그대로 장면 내에 유지 되도록 않아도가 됩니다. 
5.  마지막 개체 구조를 *계층 패널* 아래 이미지에 표시 된 것 처럼 보여야 합니다.

    ![계층 구조 패널의 최종 구조입니다.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>5 장-ResultsLabel 클래스 만들기

생성 해야 하는 첫 번째 스크립트는 *ResultsLabel* 다음 담당 하는 클래스: 

- 적절 한 전 세계 공간의 카메라의 위치를 기준으로 레이블을 만드는 중입니다.
- 이미지 중심이 되에서 태그를 표시 합니다.

이 클래스를 만들려면: 

1.  마우스 오른쪽 단추로 클릭 합니다 *프로젝트 패널*, 한 다음 **만들기 > 폴더**. 폴더의 이름을 **스크립트**합니다. 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab2-24.png)

2.  사용 하 여 합니다 **스크립트** 폴더 만들기, 두 번 클릭 하 여 엽니다. 해당 폴더를 마우스 오른쪽 단추로 선택 내에서 다음 **만들기 >** 한 다음  **C# 스크립트**합니다. 스크립트 이름을 *ResultsLabel*합니다. 

3.  두 번 클릭 하 여 새 *ResultsLabel* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.

4.  클래스 내에 다음 코드를 삽입 합니다 *ResultsLabel* 클래스:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.
7.  다시는 *Unity 편집기*, 클릭 하 고 끌어를 *ResultsLabel* 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체에는  *계층 패널*합니다.
8.  클릭 합니다 **주 카메라** 확인 합니다 *검사기 패널*.

카메라에 끌어 놓을 스크립트에서 두 필드는 알 수 있습니다. **커서** 하 고 **Prefab 레이블을**합니다.

9.  호출 된 개체를 끌어 **커서** 에서 합니다 *계층 패널* 명명 된 슬롯에 **커서**아래 이미지에서 보여준 것 처럼 합니다.
10. 호출 된 개체를 끌어 **LabelText** 에서 *Assets 폴더* 에 *프로젝트 패널* 명명 된 슬롯에 **레이블 Prefab**에서처럼는 아래 이미지입니다. 

    ![Unity 내에서 참조 대상을 설정 합니다.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>6 장-ImageCapture 클래스 만들기

다음 클래스를 만드는 것은 *ImageCapture* 클래스입니다. 이 클래스는 담당 합니다.

-   HoloLens 카메라를 사용 하 여 앱 폴더에 저장 하는 이미지를 캡처합니다.
-   사용자에서 탭 제스처를 캡처합니다.

이 클래스를 만들려면: 

1.  로 이동 합니다 **스크립트** 이전에 만든 폴더입니다. 
2.  폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다. 스크립트를 호출할 *ImageCapture*합니다. 
3.  두 번 클릭 하 여 새 *ImageCapture* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.
4.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  다음 내에서 다음 변수를 추가 합니다 *ImageCapture* 위의 클래스는 *start ()* 메서드:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
합니다 **tapsCount** 변수에 사용자에서 캡처한 탭 제스처의 번호를 저장 합니다. 이 숫자는 캡처된 이미지의 이름 지정에 사용 됩니다.

6.  에 대 한 코드 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다. 이러한 클래스를 초기화할 때 호출 됩니다.

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
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
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
합니다 *TapHandler()* 메서드 사용자에서 캡처한 탭의 수를 증가 시키고 현재 커서 위치를 사용 하 여 새 레이블을 배치 하려면 위치를 결정 합니다.

이 메서드를 호출 합니다 *ExecuteImageCaptureAndAnalysis()* 이 응용 프로그램의 핵심 기능을 시작 하는 메서드.

8.  이미지 캡처 되었으며 저장 되 면 다음 처리기가 호출 됩니다. 프로세스가 성공 하면 결과에 전달 됩니다 합니다 *VisionManager* (만들려면 아직 된)는 분석용입니다.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  그런 다음 응용 프로그램 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> 이 시점에 표시 되는 오류를 확인할 수 있습니다 합니다 *Unity 편집기 콘솔 패널이*합니다. 코드를 참조 하기 때문에 이것이 합니다 *VisionManager* 만든 다음 장에서 클래스입니다.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>7 장-Azure 및 이미지 분석 호출

만들어야 하는 마지막 스크립트를 *VisionManager* 클래스입니다. 

이 클래스는 담당 합니다.

-   캡처된 바이트의 배열로 최신 이미지를 로드 합니다.
-   보내는 바이트 배열에 *Azure Computer Vision API* 분석에 대 한 서비스 인스턴스.
-   JSON 문자열로 응답을 수신 합니다.
-   응답을 역직렬화 하 고 결과 태그를 전달 합니다 *ResultsLabel* 클래스입니다.
 
이 클래스를 만들려면:

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 
2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 *VisionManager*합니다. 
3.  새 스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.
4.  네임 스페이스의 맨 위에 있는 다음과 같을 수를 업데이트 합니다 *VisionManager* 클래스:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  스크립트의 맨 위에 있는 *내* 는 *VisionManager* 클래스 (위에 합니다 *start ()* 메서드), 두 개를 생성 해야 *클래스* 는 Azure에서 deserialize 된 JSON 응답을 나타냅니다.

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *TagData* 하 고 *AnalysedObject* 클래스 해야 합니다 *[System.Serializable]* Unity를 사용 하 여 deserialize 할 수 있으려면 선언 앞에 추가 하는 특성 라이브러리입니다.

6.  VisionManager 클래스에 다음 변수를 추가 해야 합니다.

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > 삽입 해야 하 **인증 키** 에 **authorizationKey** 변수입니다. 가 기록한 사용자 **인증 키** 이 과정의 시작 부분 [1 장](#chapter-1--the-azure-portal)합니다.

    > [!WARNING] 
    > 합니다 **visionAnalysisEndpoint** 변수이 예제에 지정 된 것과에서 다를 수 있습니다. 합니다 **서 부-us** 엄격 하 게 미국 서 부 지역에 대해 만든 서비스 인스턴스를 가리킵니다. 사용 하 여이 업데이트 하 [끝점 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); 여기는 몇 가지 예는 다음과 같을 수 있습니다.
    > - 유럽 서 부: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 동남 아시아의 경우: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 오스트레일리아 동부: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Awake에 대 한 코드는 이제 추가 해야 합니다. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  그런 다음에 의해 캡처된 이미지의 분석 결과 얻을 코 루틴 (정적 스트림 메서드를 사용 하면 아래)를 추가 합니다 *ImageCapture* 클래스입니다. 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.
10. 다시 Unity 편집기에서 클릭 하 고 끌어서 합니다 *VisionManager* 및 *ImageCapture* 에서 클래스를 **스크립트** 폴더를 **주 카메라**개체를 *계층 패널*합니다. 

## <a name="chapter-8--before-building"></a>8 장-빌드하기 전에

응용 프로그램의 철저 한 테스트를 수행 하려면 해야 테스트용으로 로드 하 여 HoloLens에 있습니다.
를 수행 하기 전에 확인 합니다.

-   에 언급 된 모든 설정이 [Chapter 2](#chapter-2--set-up-the-unity-project) 올바르게 설정 됩니다. 
-   에 연결 된 모든 스크립트를 **주 카메라** 개체입니다. 
-   모든 필드를 *주 카메라 검사기 패널* 올바르게 할당 됩니다.
-   삽입 해야 하 **인증 키** 에 **authorizationKey** 변수입니다.
-   또한 체크 인 끝점을 확인 하 *VisionManager* 스크립트 및에 맞도록 *에* 지역 (이 문서에서는 *서 부-us* 기본적으로).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>9-장 UWP 솔루션 및 테스트용으로 로드 응용 프로그램 빌드
이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.

1.  이동할 *빌드 설정* - **파일 > 빌드 설정...**
2.  *빌드 설정* 창에서 클릭 **빌드**합니다.

    ![Unity에서 앱 빌드](images/AzureLabs-Lab2-26.png)

3.  경우에 눈금 **Unity C# 프로젝트**합니다.
4.  **빌드**를 클릭합니다. Unity가 시작 됩니다는 *파일 탐색기* 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다. 해당 폴더를 이제 만들고 이름을 *앱*합니다. 사용 하 여 다음 합니다 *앱* 폴더 선택 키를 눌러 **폴더 선택**합니다. 
5.  Unity 프로젝트를 빌드할 예정 된 *앱* 폴더입니다. 
6.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 *파일 탐색기* 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.

## <a name="chapter-10--deploy-to-hololens"></a>HoloLens에 장 10-배포

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

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab2-27.png)
 
5.  로 이동 합니다 **빌드 메뉴** 클릭 **솔루션 배포**, 응용 프로그램에 HoloLens 테스트용으로 로드 하려면.
6.  앱에 HoloLens 시작할 준비가에 설치 된 앱 목록에 나타나야 합니다.

> [!NOTE]
> 몰입 형 헤드셋을 배포 하려면 설정 합니다 **솔루션 플랫폼** 를 *로컬 컴퓨터*, 설정 및를 **구성** 에 *디버그*, 를사용하여*x86* 으로 **플랫폼**합니다. 로컬 배포 후 컴퓨터를 사용 하 여는 **빌드 메뉴**을 선택 하면 *솔루션 배포*합니다. 

## <a name="your-finished-computer-vision-api-application"></a>완성 된 Computer Vision API 응용 프로그램

축, 실제 개체 인식 신뢰도를 표시 된 것을 표시 하는 Azure Computer Vision API를 활용 하는 혼합된 현실 앱을 작성 합니다.

![랩 결과](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

사용한 마찬가지로 *태그* 매개 변수 (내에서 볼 수 있듯이 *끝점* 내에서 사용 합니다 *VisionManager*)을 다른 정보를 검색 하는 앱을 확장 합니다. 살펴보겠습니다 에 액세스할 수 있는 다른 매개 변수 [여기](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)합니다.

### <a name="exercise-2"></a>연습 2

숫자를 숨기기 아마도 더 편안 하 고 읽기 쉬운 방식으로 반환된 된 Azure 데이터를 표시 합니다. 처럼 봇 사용자 소통할 수 있습니다.
