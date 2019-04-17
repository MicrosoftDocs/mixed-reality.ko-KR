---
title: MR 및 Azure 301-언어 번역
description: 혼합된 현실 응용 프로그램에서 Azure Translator Text API를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, translator 텍스트, hololens, 몰입 형, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603609"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR 및 Azure 301: 외국어 번역

이 과정에서는 번역 기능 Translator Text API를 사용 하 여 Azure Cognitive Services를 사용 하 여 혼합된 현실 응용 프로그램을 추가 하는 방법을 배웁니다.

![최종 제품](images/AzureLabs-Lab1-00.png)

Translator Text API는 번역 서비스에서 거의 실시간으로 작동 하는 경우 서비스는 클라우드 기반, REST API 호출을 사용 하 여, 앱 수 있으며 다른 언어로 텍스트를 변환 하는 신경망 기계 번역 기술을 사용 합니다. 자세한 내용은 참조는 [Azure Translator Text API 페이지](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)합니다.

이 과정을 완료 하면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 응용 프로그램을 갖게 됩니다.

1.  사용자가 마이크는 몰입 형 (VR) 헤드셋에 연결 (또는 HoloLens의 내장 마이크)를 말하십시오.
2.  앱 받아쓰기 캡처하고 Azure Translator Text API에 전송 됩니다.
3.  변환 결과 Unity 장면에서 간단한 UI 그룹에 표시 됩니다.

이 코스 샘플 Unity 기반 응용 프로그램으로 Translator 서비스에서 결과 가져오는 방법을 배우게 됩니다. 사용자 지정 응용 프로그램을 작성 하려는 경우에 이러한 개념을 적용 하는 것이 됩니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 301: 외국어 번역</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다. 과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다. HoloLens를 사용 하는 경우 음성 캡처하는 동안 일부 echo를 확인할 수 있습니다.

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
- (없으면 헤드셋 내장 마이크와 스피커) 내장 마이크를 사용 하 여 헤드폰 집합
- Azure 설정 및 번역 검색에 대 한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 주의 사항

- 이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
- 이 자습서의 코드를 사용 하면 PC에 연결 된 기본 마이크 장치에서 기록할 수 있습니다. 기본 마이크 장치 음성 캡처를 사용 하려는 장치에 설정 되어 있는지 확인 합니다.
- 받아쓰기를 사용 하도록 설정 하려면 PC를 허용 하려면로 이동 **설정 > 개인 정보 > 음성 변환, 잉크 입력 및 입력** 단추를 선택 하 고 **켜기 음성 서비스 및 입력 제안을**합니다.
- 마이크와 연결할 헤드폰 (또는 기본 제공)를 사용 하는 경우, 헤드셋 옵션이 있는지 확인 "내 헤드셋 wear 있습니까 때 헤드셋 마이크 전환"에서 켜져 **설정 > 혼합 현실을 > 오디오 및 음성**.

   ![혼합된 현실 설정](images/AzureLabs-Lab1-00-5.png)

   ![마이크 설정](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> 이 랩의 몰입 형 헤드셋을 개발 하는 경우 발생할 수 있는 오디오 출력 장치 문제에 유의 합니다. Unity는 unity (Unity 2018.2) 이상 버전에서 수정 되는 문제 때문입니다. 문제는 런타임 시 기본 오디오 출력 장치를 변경 하지 Unity를 방지 합니다. 해결 방법으로, 위의 단계를 완료 해야 하 고 닫은 다음 다시이 문제가 발생 하는 자체 편집기를 엽니다.

## <a name="chapter-1--the-azure-portal"></a>1 장-Azure Portal

Azure의 Translator API를 사용 하려면 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.

1.  에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

2.  일단 로그인 하면 클릭할 **새로 만들기** 위쪽에서 왼쪽 모퉁이 검색 "Translator text API입니다." 선택 **입력**합니다.

    ![새 리소스](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.

3.  새 페이지에 대 한 설명을 제공 합니다는 *Translator Text API* 서비스입니다. 선택이 페이지의 왼쪽 아래에 있는 합니다 **만들기** 이 연결 서비스를 만들려면 단추입니다.

    ![Translator 텍스트 API 서비스 만들기](images/AzureLabs-Lab1-03.png)

4.  클릭 한 후 **만들기**:

    1. 원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.
    2. 적절 한 선택 **구독**합니다.
    3. 선택 합니다 **가격 책정 계층** 첫 번째 경우, 적절 한 시간 만들기는 *Translator 텍스트 서비스*, 무료 계층 (F0 라는)를 사용할 수 있어야 합니다.
    4. 선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 좋습니다 일반적인 리소스 그룹에서 (예: 이러한 labs) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    5. 확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다. 위치는 응용 프로그램은 실행할 지역의 것이 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.
    6. 이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.
    7. **만들기**를 선택합니다.

        ![만들기 단추를 선택 합니다.](images/AzureLabs-Lab1-04.png)

5.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.
6.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다. 

    ![Azure 서비스 만들기 알림](images/AzureLabs-Lab1-05.png)

7.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다. 

    ![리소스 팝업으로 이동 합니다.](images/AzureLabs-Lab1-06.png)

8.  클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 새 텍스트 API Translator 서비스 인스턴스로 이동 합니다. 

    ![Translator API 서비스 텍스트 페이지](images/AzureLabs-Lab1-07.png)

9.  이 자습서에서 응용 프로그램 서비스의 구독 키를 사용 하 여 수행 하는 서비스에 대 한 호출을 수행 해야 합니다. 
10. *빠른 시작* 페이지에 *Translator Text* 서비스를 이동 하 여 첫 번째 단계로 *키 가져오기*를 클릭 하 고 **키** (할 수 있습니다 또한 이렇게 열쇠 아이콘을 가리키는 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭 하 여). 이 서비스를 줄이면 *키*합니다.
11. 프로젝트에서 나중에이 필요 하므로 표시 된 키 중 하나가 복사본을 만듭니다. 

## <a name="chapter-2--set-up-the-unity-project"></a>2 장-Unity 프로젝트 설정

설정 하 고 혼합된 현실 몰입 형 헤드셋을 테스트 합니다.

> [!NOTE]
> 이 과정에 대 한 동작 컨트롤러 않아도 됩니다. 몰입 형 헤드셋 설정만 지원에 필요한 경우 하세요 [이 단계를 따라](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.

다음 혼합된 현실을 사용 하 여 개발 하는 것에 대 한 일반적인 집합 중인지 이며, 따라서 다른 프로젝트에 대 한 적절 한 템플릿:

1.  오픈 *Unity* 누릅니다 **새로 만들기**합니다. 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab1-08.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. 삽입 **MR_Translation**합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**합니다. 설정 된 *위치* 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab1-09.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집 > 기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab1-10.png)

4.  이동한 다음 **파일 > 빌드 설정** 플랫폼 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환** 단추입니다.

    ![빌드 설정 창, uwp 플랫폼 전환 합니다.](images/AzureLabs-Lab1-11.png)

5.  로 이동 **파일 > 빌드 설정** 되어 있는지 확인 합니다.

    1. **장치를 대상** 로 설정 된 **모든 장치**합니다.

        > Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.

    2. **빌드 형식** 로 설정 된 **D3D**
    3. **SDK** 로 설정 된 **가장 최근에 설치 된**
    4. **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**
    5. **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**
    6. 장면 저장 하 고 빌드에 추가 합니다.

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.

            ![추가 백그라운드에서 열기 단추를 클릭](images/AzureLabs-Lab1-12.png)

        2. 새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab1-13.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **MR_TranslationScene**, 키를 누릅니다 **저장**합니다.

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab1-14.png)

            > 주의 내에서 Unity 장면에 저장 해야 합니다 *자산* 폴더를 Unity 프로젝트와 연결 해야 합니다. 백그라운드에서 폴더 (및 다른 유사한 폴더)를 만들기 Unity 프로젝트를 구성 하는 일반적인 방법입니다.

    7. 설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.

6. 에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한. 

    ![플레이어 설정 열기](images/AzureLabs-Lab1-15.png)

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. 에 **기타 설정** 탭:

        1. **스크립팅 런타임 버전** 있어야 **안정적인** (.NET 3.5와 같음).
        2. **백 엔드를 스크립팅** 있어야 **.NET**
        3. **API 호환성 수준** 있어야 **.NET 4.6**

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab1-16.png)
      
    2. 내 합니다 **게시 설정** 탭의 **기능**, 확인:

        1. **InternetClient**
        2. **Microphone**

            ![게시 설정을 업데이트 합니다.](images/AzureLabs-Lab1-17.png)

    3. 패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab1-18.png)

8.  년대 **빌드 설정**를 *Unity C# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).

## <a name="chapter-3--main-camera-setup"></a>3 장-주 카메라 설정

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드에 바로 계속, 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage),으로 프로젝트로 가져올를 [ *사용자 지정 패키지*](https://docs.unity3d.com/Manual/AssetPackages.html)를 선택한 다음에서 계속 [5 장](#chapter-5--create-the-results-class)합니다. Unity 프로젝트 만들기를 계속 해야 합니다.

1.  에 *계층 패널*, 라는 개체를 보면 **주 카메라**, "내부" 응용 프로그램 되 면이 개체에 "head" 관점을 나타냅니다.
2.  사용자 앞에 Unity 대시보드를 선택 합니다 **주 카메라 GameObject**합니다. 합니다 *검사기 패널* (일반적으로 대시보드 내에서 오른쪽에 있음)의 다양 한 구성 요소에 표시 됩니다 *GameObject*를 사용 하 여 *변환* 맨 뒤에 *카메라*, 및 기타 구성 요소입니다. 위치가 올바르게 하므로 주 카메라의 변환을 다시 설정 해야 합니다.
3.  이 작업을 수행 하려면 선택 합니다 **기어** 카메라의 옆에 있는 아이콘 *변환* 구성 요소 및 선택 **재설정**. 

    ![주 카메라 변환을 다시 설정 합니다.](images/AzureLabs-Lab1-19.png)
 
4.  합니다 *변환* 구성 요소는 다음과 같이 보입니다.

    1. 합니다 *위치* 로 설정 된 **0, 0, 0**
    2. *회전* 로 설정 된 **0, 0, 0**
    3. 및 *크기 조정* 로 설정 된 **1, 1, 1**

        ![카메라에 대 한 정보를 변환 합니다.](images/AzureLabs-Lab1-20.png)

5.  사용 하 여 다음 합니다 **주 카메라** 선택한 개체를 참조 하십시오는 **구성 요소 추가** 의 맨 아래에 있는 단추를 *검사기 패널*합니다. 
6.  해당 단추를 선택 하 고 검색 (입력 하거나 *오디오 원본* 섹션을 탐색 하거나 검색 필드에) 라는 구성 요소에 대 한 **오디오 원본** 아래와 같이 선택 (키를 눌러 입력에 또한 작동)입니다.
7.  *오디오 원본* 에 추가할 구성 요소를 **주 카메라**아래 설명 된 대로, 합니다.

    ![오디오 원본 구성 요소를 추가 합니다.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Microsoft HoloLens 대 한 다음을 변경 해야의 일부인 합니다 **카메라** 구성 요소에 **주 카메라**:
    > - **플래그를 지웁니다.** 단색입니다.
    > - **백그라운드** ' 검정, 알파 0'-16 진수 색: #00000000 합니다.

## <a name="chapter-4--setup-debug-canvas"></a>4 장-설치 디버그 캔버스

입력 및 변환의 출력을 표시 하려면 기본 UI를 작성 해야 합니다. 이 과정에 대 한 데이터를 표시 하려면 여러 'Text' 개체를 사용 하 여 캔버스 UI 개체를 만듭니다.

1.  빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*아래에 있는 **UI**, 추가 **캔버스**합니다.

    ![새 캔버스 UI 개체를 추가 합니다.](images/AzureLabs-Lab1-22.png)

2.  선택 된 경우 캔버스 개체를 사용 하 여는 *검사기 패널* ('캔버스' 구성 요소 내)을 변경 **렌더링 모드** 에 **세계 좌표 공간**입니다. 
3.  다음으로, 다음 매개 변수를 변경 합니다 *검사기 창의 Rect 변환*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Width* -    500
    3. *높이* -300
    4. *크기 조정* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![캔버스에 대 한 rect 변환을 업데이트 합니다.](images/AzureLabs-Lab1-23.png)
 
4.  마우스 오른쪽 단추로 클릭는 **캔버스** 에 *계층 패널*아래에 있는 **UI**, 추가 **패널**합니다. 이렇게 **패널** 텍스트에 장면에 표시 됩니다 하는 경우 배경이 제공 됩니다.
5.  마우스 오른쪽 단추로 클릭는 **패널** 에 *계층 패널*아래에 있는 **UI**, 추가 **텍스트 개체**합니다. 총에서 4 개의 UI 텍스트 개체를 만든 때까지 동일한 프로세스를 반복 (힌트: 선택한 첫 번째 'Text' 개체에 있는 경우 단순히 누르면 **Ctrl + 했습니다 '**, 총에서 4 개 생길 때까지 복제할). 
6.  각각에 대해 **텍스트 개체**선택 하 고 사용 하 여는 아래에서 매개 변수를 설정 하는 테이블의 *검사기 패널*합니다.

    1. 에 대 한 합니다 *Rect 변환* 구성 요소:

        | 이름                   | 변환- *위치*             | 너비      | 높이    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. 에 대 한 합니다 **텍스트 (스크립트)** 구성 요소:


        | 이름                   | 텍스트 모드               | 글꼴 크기    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | 마이크 상태: | 20           |
        | AzureResponseLabel     | Azure 웹 응답 | 20           |
        | DictationLabel         |   방금 말한:   | 20           |
        | TranslationResultLabel |    변환:    | 20           |

        ![UI 레이블에 대 한 해당 값을 입력 합니다.](images/AzureLabs-Lab1-24.png)

    3. 또한, 글꼴 스타일을 확인 **굵게**합니다. 이렇게 하면 텍스트를 쉽게 읽을 수 있습니다.

        ![굵은 글꼴입니다.](images/AzureLabs-Lab1-25.png)

7.  각 *UI 텍스트 개체* 에서 만든 [5 장](#chapter-5--create-the-results-class)에서 새 *자식* **UI 텍스트 개체**합니다. 이러한 자식 응용 프로그램의 출력을 표시 합니다. 만들 *자식* 의도 한 부모를 마우스 오른쪽 단추로 클릭을 통해 개체 (예: *MicrophoneStatusLabel*)를 선택한 **UI** 를 선택한 **텍스트**.
8.  이러한 자식 각각 선택 하 고 사용 하 여는 아래 검사기 창에서 매개 변수를 설정 하는 테이블입니다.

    1. 에 대 한 합니다 **Rect 변환** 구성 요소:

        | 이름                  | 변환- *위치* | 너비      | 높이    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. 에 대 한 합니다 **텍스트 (스크립트)** 구성 요소:

        | 이름                  | 텍스트 모드          | 글꼴 크기    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 다음으로, 각 텍스트 구성 요소에 대 한 'centre' 맞춤 옵션을 선택 합니다.

    ![텍스트를 맞춥니다.](images/AzureLabs-Lab1-26.png)

10. 되도록 합니다 **자식 UI 텍스트가** 개체를 쉽게 읽을 수, 변경 해당 *색*합니다. (현재 ' 검은색') 옆에 있는 표시줄에서 클릭 하 여이 작업을 수행할 *Color*합니다. 

    ![UI 텍스트 출력에 대 한 값을 해당 입력 합니다.](images/AzureLabs-Lab1-27.png)
 
11. 그런 다음 새로운 작은, *색* 창에서 변경 합니다 *16 진수 색* 에: **0032EAFF**

    ![색을 파랑으로 업데이트 합니다.](images/AzureLabs-Lab1-28.png)
 
12. 다음은 하는 방법을 **UI** 같아야 합니다.
    1.  에 *계층 패널*:

        ![제공 된 구조 계층 구조를 포함 합니다.](images/AzureLabs-Lab1-29.png)

    2.  에 *장면* 하 고 *뷰를 게임*:

        ![장면 및 게임 보기를 동일한 구조에 있습니다.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>5 장-결과 클래스 만들기

생성 해야 하는 첫 번째 스크립트는 *결과* 변환의 결과 확인 하는 방법을 제공 하는 일을 담당 하는 클래스입니다. 클래스는 저장 하 고 다음을 표시 합니다. 

- Azure에서 응답 결과입니다.
- 마이크 상태입니다. 
- 받아쓰기 (텍스트 음성)의 결과입니다.
- 변환의 결과입니다.

이 클래스를 만들려면: 

1.  마우스 오른쪽 단추로 클릭 합니다 *프로젝트 패널*, 한 다음 **만들기 > 폴더**. 폴더의 이름을 **스크립트**합니다. 
 
    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab1-31.png)

    ![스크립트 폴더를 엽니다.](images/AzureLabs-Lab1-32.png)
 
2.  사용 하 여 합니다 **스크립트** 폴더 만들기, 두 번 클릭 하 여 엽니다. 해당 폴더를 마우스 오른쪽 단추로 선택 내에서 다음 **만들기 >** 한 다음  **C# 스크립트**합니다. 스크립트 이름을 *결과*합니다. 

    ![첫 번째 스크립트를 만듭니다.](images/AzureLabs-Lab1-33.png)
 
3.  두 번 클릭 하 여 새 *결과* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.
4.  다음 네임 스페이스를 삽입 합니다.

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  클래스 내에서 다음 변수를 삽입 합니다.

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  추가한 합니다 *Awake()* 메서드는 클래스를 초기화할 때 호출 됩니다. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  마지막으로 UI 다양 한 결과 정보를 출력 하는 일을 담당 하는 메서드를 추가 합니다. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

## <a name="chapter-6--create-the-microphonemanager-class"></a>6 장-만들기 합니다 *MicrophoneManager* 클래스

두 번째 클래스를 만드는 것은 *MicrophoneManager*합니다.

이 클래스는 담당 합니다.

- 헤드셋 이나 컴퓨터 (중 기본)에 연결 하 여 녹음 장치를 검색 합니다.
- (의견) 오디오를 캡처하고 받아쓰기를 사용 하 여 문자열로 저장 합니다.
- 음성, 일시 중지 되 면 변환기 클래스에 받아쓰기를 제출 합니다.
- 원하는 경우에 음성 캡처를 중지할 수 있습니다 하는 메서드를 호스트 합니다.

이 클래스를 만들려면: 
1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 
2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 *MicrophoneManager*합니다. 
3.  새 스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.
4.  네임 스페이스의 맨 위에 있는 다음과 같을 수를 업데이트 합니다 *MicrophoneManager* 클래스:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  그런 다음 내에서 다음 변수를 추가 합니다 *MicrophoneManager* 클래스:

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  에 대 한 코드를 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다. 이러한 클래스를 초기화할 때 호출 됩니다.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  할 수 있습니다 *삭제할* 는 *update ()* 이 클래스는 사용 하지 않으므로 메서드.
8.  이제 앱을 시작 및 음성 캡처를 중지 하 고 전달 하는 메서드를 *Translator* 곧 빌드하게 되는 클래스입니다. 다음 코드를 복사 하 고 아래에 붙여 합니다 *start ()* 메서드.

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > 이 응용 프로그램을 만들지 것입니다 하지만 이용 합니다 *StopCapturingAudio()* 메서드도 제공 되어 여기에서 응용 프로그램에서 오디오 캡처를 중지 하는 기능을 구현 하려는 경우.

9.  이제 음성을 중지 될 때 호출 되는 받아쓰기 처리기를 추가 해야 합니다. 이 메서드는 지정 된 텍스트를 전달한 합니다 *Translator* 클래스입니다.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Unity를 반환 하기 전에 Visual Studio에서 변경 내용을 저장 해야 합니다.

> [!WARNING]  
> 이 시점에 표시 되는 오류를 확인할 수 있습니다 합니다 *Unity 편집기 콘솔* 패널 ("이름 '변환기'가 없습니다..."). 코드를 참조 하기 때문에 이것이 합니다 *Translator* 클래스를 만든 다음 장에서 합니다.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>7 장-Azure 및 translator 서비스 호출

만들어야 하는 마지막 스크립트를 *Translator* 클래스입니다. 

이 클래스는 담당 합니다.

-   응용 프로그램을 인증 *Azure*, exchange에 **인증 토큰**합니다.
-   사용 하 여는 **인증 토큰** 텍스트를 제출 하려면 (에서 받은 *MicrophoneManager* 클래스) 번역할입니다.
-   변환 된 결과 받고에 전달 된 *결과* UI에 시각화할 클래스입니다.

이 클래스 만들려면: 
1.  로 이동 합니다 **스크립트** 이전에 만든 폴더입니다. 
2.  마우스 오른쪽 단추로 클릭 합니다 **프로젝트 패널**를 **만들기 > C# 스크립트**합니다. 스크립트를 호출할 *Translator*합니다.
3.  두 번 클릭 하 여 새 *Translator* 열려는 스크립트 **Visual Studio를 사용 하 여**입니다.
4.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  그런 다음 내에서 다음 변수를 추가 합니다 *Translator* 클래스:

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - 언어를 삽입 하는 언어 **enum** 은 예제 일 뿐입니다. 자유롭게; 하려는 경우 더 추가 합니다 [API는 60 개 이상의 언어를 지원](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (방법 포함).
    > - [사용 가능한 언어를 포함 하는 좀 더 대화형 페이지](https://www.microsoft.com/translator/business/languages/), 하지만 페이지가 사이트 언어로 설정 된 경우 작업에 표시 주의 ' en-' (및 네이티브 언어로 가능성이 리디렉션이 Microsoft 사이트). 사이트 URL을 변경 하 여 또는 페이지의 맨 아래에 언어를 변경할 수 있습니다.
    > - 합니다 **authorizationKey** 위의 코드 조각에서 값 이어야 합니다는 **키** 에 구독할 때 수신 합니다 *Azure Translator Text API*합니다. 이 다룬 [1 장](#chapter-1--the-azure-portal)합니다.

6.  에 대 한 코드를 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다. 
7.  이 경우 코드는 호출할 *Azure* 권한 부여 키를 사용 하 여를 *토큰*합니다.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > 토큰은 10 분 후 만료 됩니다. 앱에 대 한 시나리오에 따라 여러 번 호출 하는 동일한 코 루틴을 확인 해야 합니다.

8.  토큰을 가져오려면 코 루틴 다음과 같습니다.

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > IEnumerator 메서드의 이름을 편집 하는 경우 **GetTokenCoroutine()** 를 업데이트 해야 합니다 *StartCoroutine* 및 *StopCoroutine* 위의 코드에서 문자열 값을 호출 합니다. [Unity 설명서에 따라](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), 특정 중지 *코 루틴*, 하는 문자열 값 메서드를 사용 해야 합니다.

9.  다음으로, 수신한 텍스트 번역을 가져오려면 (메서드로 "지원" stream 바로 아래)는 코 루틴을 추가 합니다 *MicrophoneManager* 클래스입니다. 이 코드를 보낼 쿼리 문자열을 만듭니다는 *Azure Translator Text API*, 내부 Unity UnityWebRequest 클래스를 사용 하 여 쿼리 문자열을 사용 하 여 끝점에 'Get' 호출을 합니다. 결과 변환 결과 개체에서 설정에 사용 됩니다. 아래 코드 구현을 보여 줍니다.

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. 변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

## <a name="chapter-8--configure-the-unity-scene"></a>8 장 – Unity 장면 구성

1.  다시 Unity 편집기에서 클릭 하 고 끌어서 합니다 *결과* 클래스 *에서* 는 **스크립트** 폴더를 **주 카메라** 개체에는  *계층 패널*합니다.
2.  클릭 합니다 **주 카메라** 확인 합니다 *검사기 패널*. 내에서 새로 추가 된 점을 확인할 수 있습니다 *스크립트* 구성 요소를 빈 값을 사용 하 여 4 개의 필드가 있습니다. 이들은 코드에서 속성에 대 한 출력 참조입니다. 
3.  적절 한 끌어 **텍스트** 에서 개체를 *계층 패널* 아래 이미지와 같이 4 개의 해당 슬롯에 있습니다.

    ![지정 된 값을 사용 하 여 대상 참조를 업데이트 합니다.](images/AzureLabs-Lab1-34.png)
  
4.  다음을 클릭 하 고 끌어서를 *Translator* 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체를 *계층 패널*합니다. 
5.  클릭 한 다음, 끌어서 합니다 *MicrophoneManager* 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체를 *계층 패널*. 
6.  마지막으로, 클릭 합니다 **주 카메라** 확인 합니다 *검사기 패널*. 끌어 놓은 스크립트에는 두 드롭다운 상자를 사용 하면 언어를 설정 하는 것을 확인할 수 있습니다.
 
    ![의도 한 번역 언어는 입력을 확인 합니다.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>9 장-혼합된 현실에서 테스트

이 시점에서 장면 올바르게 구현 되었는지 테스트 해야 합니다.

다음을 확인합니다.

- 에 언급 된 모든 설정이 [1 장](#chapter-1--the-azure-portal) 올바르게 설정 됩니다. 
- 합니다 *결과*, *Translator*, 및 *MicrophoneManager*, 스크립트에 연결 된 합니다 **주 카메라** 개체입니다. 
- 배치 했으면 하 *Azure Translator Text API* 서비스 **키** 내 합니다 **authorizationKey** 내에서 변수를 *Translator* 스크립트입니다.  
- 모든 필드를 *주 카메라 검사기 패널* 올바르게 할당 됩니다.
- 마이크 장면을 실행 하는 경우 작동 (그렇지 않은 경우 연결 된 마이크 인지 확인 합니다 *기본* 장치 및 있다고 [Windows 내에서 올바르게 설정](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

키를 눌러 몰입 형 헤드셋을 테스트할 수 있습니다 합니다 **재생** 단추를 *Unity 편집기*합니다.
앱 연결된 몰입 형 헤드셋을 통해 작동 해야 합니다.

> [!WARNING]  
> 변경 하는 기본 오디오 장치에 대 한 Unity 콘솔에 오류를 표시 하는 경우 장면 예상 대로 작동 하지 않을 수 있습니다. 혼합된 현실 포털에 있는 헤드셋에 대 한 기본 제공 마이크를 사용 하 여 처리 하는 방식 때문입니다. 이 오류가 표시, 단순히 장면 중지 및 다시 시작 하 고으로 작동 해야 하는 경우 필요 합니다.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>장 10-UWP 솔루션 및 로컬 컴퓨터에 테스트용으로 로드를 생성 합니다.

이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.

1.  이동할 **빌드 설정**: **파일 > 빌드 설정...**
2.  **빌드 설정** 창에서 클릭 **빌드**합니다.

    ![Unity 장면을 빌드하십시오.](images/AzureLabs-Lab1-36.png)
  
3.  경우에 눈금 **Unity C# 프로젝트**합니다.
4.  **빌드**를 클릭합니다. Unity가 시작 됩니다는 *파일 탐색기* 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다. 해당 폴더를 이제 만들고 이름을 *앱*합니다. 사용 하 여 다음 합니다 *앱* 폴더 선택 키를 눌러 **폴더 선택**합니다. 
5.  Unity 프로젝트를 빌드할 예정 된 *앱* 폴더입니다. 
6.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 *파일 탐색기* 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.

## <a name="chapter-11--deploy-your-application"></a>11 장-응용 프로그램 배포

응용 프로그램을 배포 합니다.

1.  새 Unity 빌드에 이동 (합니다 *앱* 폴더) 사용 하 여 솔루션 파일을 엽니다 *Visual Studio*합니다.
2.  솔루션 구성 선택에서 **디버그**합니다.
3.  솔루션 플랫폼에서 선택 **x86**하십시오 **로컬 컴퓨터**합니다. 

    > Microsoft HoloLens 알 수 있습니다 것이 더 쉽게 *원격 컴퓨터*컴퓨터로 테더 링 없습니다 있도록 합니다. 그러나 또한 다음을 수행 해야 합니다.
    > - 알고는 **IP 주소** 내에서 찾을 수 있는 여 HoloLens의는 *설정 > 네트워크 및 인터넷 > Wi-fi > 고급 옵션*; IPv4는 주소를 사용 해야 합니다. 
    > - 확인 *개발자 모드* 됩니다 **에**에; *설정 > 업데이트 및 보안 > 개발자를 위한*합니다.

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab1-37.png)
    
 
4.  로 이동 **빌드 메뉴** 를 클릭 **솔루션 배포** 사용자 PC에 응용 프로그램을 테스트용으로 로드 하려면.
5.  이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.
6.  시작 되 면 앱 하 라는 메시지가 나타납니다 마이크에 대 한 액세스 권한을 부여 합니다. 클릭 해야 합니다 **예** 단추입니다.
7.  번역을 시작할 준비가 되었습니다!

## <a name="your-finished-translation-text-api-application"></a>완성 된 변환 텍스트 API 응용 프로그램

축, 음성을 번역 된 텍스트로 변환 하는 Azure 번역 텍스트 API를 활용 하는 혼합된 현실 앱을 작성 합니다.

![최종 제품입니다.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

있습니다 텍스트 음성 변환 기능을 추가할 수는 앱에 반환 된 텍스트를 음성으로 변환 되어 있도록?

### <a name="exercise-2"></a>연습 2

사용자가 앱 언어를 변경할 때마다 다시 작성 하지 않아도 되므로 앱 자체 내에서 원본 및 출력 언어 ('from' 및 'to')을 변경할 수 있도록 합니다.
