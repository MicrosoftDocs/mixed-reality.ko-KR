---
title: MR 및 Azure 301-언어 번역
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Translator Text API을 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, translator 텍스트, hololens, 몰입 형, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554056"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR 및 Azure 301: 외국어 번역

이 과정에서는 Translator Text API와 함께 Azure Cognitive Services를 사용 하 여 혼합 현실 응용 프로그램에 번역 기능을 추가 하는 방법에 대해 설명 합니다.

![최종 제품](images/AzureLabs-Lab1-00.png)

Translator Text API은 거의 실시간으로 작동 하는 번역 서비스입니다. 서비스는 클라우드를 기반으로 하며, REST API 호출을 사용 하 여 앱은 신경망 번역 기술을 사용 하 여 텍스트를 다른 언어로 번역할 수 있습니다. 자세한 내용은 [Azure Translator Text API 페이지](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)를 참조 하세요.

이 과정이 완료 되 면 다음을 수행할 수 있는 혼합 현실 응용 프로그램이 만들어집니다.

1.  사용자는 몰입 형 (VR) 헤드셋 (또는 HoloLens의 기본 제공 마이크)에 연결 된 마이크를 말합니다.
2.  앱이 받아쓰기를 캡처하여 Azure Translator Text API에 보냅니다.
3.  번역 결과는 Unity 장면의 간단한 UI 그룹에 표시 됩니다.

이 과정에서는 변환기 서비스에서 Unity 기반 샘플 응용 프로그램으로 결과를 가져오는 방법을 설명 합니다. 빌드할 수 있는 사용자 지정 응용 프로그램에 이러한 개념을 적용 하는 것이 좋습니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 301: 외국어 번역</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다. 과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다. HoloLens를 사용 하는 경우 음성 캡처 중에 몇 가지 echo를 확인할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다. [도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- 모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC
- [개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)
- 기본 제공 마이크가 있는 헤드폰 집합 (헤드셋에 기본 제공 mic 및 스피커가 없는 경우)
- Azure 설정 및 번역 검색을 위한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 주의 사항

- 이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
- 이 자습서의 코드를 사용 하 여 PC에 연결 된 기본 마이크 장치에서 기록할 수 있습니다. 기본 마이크 장치가 음성 캡처에 사용할 장치로 설정 되었는지 확인 합니다.
- PC에서 받아쓰기를 사용 하도록 허용 하려면 **설정 > 개인 정보 > 음성, 필기 & 입력** 으로 이동 하 고, **음성 서비스 설정 및 제안 입력**단추를 선택 합니다.
- 헤드셋 (또는 기본 제공)에 연결 된 마이크 및 헤드폰을 사용 하는 경우 **설정 > 혼합 현실 > 오디오 및 음성**에서 "헤드셋을 사용할 때 헤드셋 mic로 전환" 옵션이 켜 졌는 지 확인 합니다.

   ![혼합 현실 설정](images/AzureLabs-Lab1-00-5.png)

   ![마이크 설정](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> 이 랩에서 모던 헤드셋을 개발 하는 경우 오디오 출력 장치 문제가 발생할 수 있습니다. 이 문제는 unity의 문제 때문에 발생 합니다 .이 문제는 unity (Unity 2018.2)의 이후 버전에서 수정 되었습니다. 이 문제는 Unity에서 런타임에 기본 오디오 출력 장치를 변경 하지 못하도록 합니다. 이 문제를 해결 하려면 위의 단계를 완료 했는지 확인 하 고,이 문제가 자체적으로 표시 되 면 편집기를 닫았다가 다시 열어야 합니다.

## <a name="chapter-1--the-azure-portal"></a>1 장-Azure Portal

Azure Translator API를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.

1.  [Azure Portal](https://portal.azure.com)에 로그인 합니다.

    > [!NOTE]
    > 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

2.  로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 "Translator Text API"를 검색 합니다. **Enter 키**를 선택 합니다.

    ![새 리소스](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.

3.  새 페이지에 *Translator Text API* 서비스에 대 한 설명이 제공 됩니다. 이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.

    ![Translator Text API 서비스 만들기](images/AzureLabs-Lab1-03.png)

4.  **만들기**를 클릭 하면 다음을 클릭 합니다.

    1. 이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.
    2. 적절 한 **구독**을 선택 합니다.
    3. 적절 한 **가격 책정 계층** 을 선택 합니다. *Translator Text 서비스*를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.
    4. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.

    5. 새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다. 위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.
    6. 또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.
    7. **만들기**를 선택합니다.

        ![만들기 단추를 선택 합니다.](images/AzureLabs-Lab1-04.png)

5.  **만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.
6.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다. 

    ![Azure 서비스 만들기 알림](images/AzureLabs-Lab1-05.png)

7.  알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 

    ![리소스 팝업으로 이동 합니다.](images/AzureLabs-Lab1-06.png)

8.  알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 새 Translator Text API 서비스 인스턴스로 이동 됩니다. 

    ![Translator Text API 서비스 페이지](images/AzureLabs-Lab1-07.png)

9.  이 자습서에서 응용 프로그램은 서비스에 대 한 호출을 수행 해야 하며, 서비스의 구독 키를 사용 하 여 수행 됩니다. 
10. *Translator Text* 서비스의 *빠른 시작* 페이지에서 첫 번째 단계로 이동 하 고 *키*를 클릭 한 다음 **키** 를 클릭 합니다 .이를 위해 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭 하 여이를 수행할 수도 있습니다. 키 아이콘으로 표시 됨). 이렇게 하면 서비스 *키*가 표시 됩니다.
11. 프로젝트에서 나중에 필요 하므로 표시 된 키 중 하나를 복사 합니다. 

## <a name="chapter-2--set-up-the-unity-project"></a>2 장-Unity 프로젝트 설정

혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.

> [!NOTE]
> 이 과정에서는 동작 컨트롤러가 필요 하지 않습니다. 몰입 형 헤드셋을 설정 하는 데 지원이 필요한 경우 [다음 단계를 수행](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)하세요.

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정 이며, 따라서 다른 프로젝트에 적합 한 템플릿입니다.

1.  *Unity* 를 열고 **새로 만들기**를 클릭 합니다. 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab1-08.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. **MR_Translation**을 삽입 합니다. 프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다. 위치를 적절 한 *위치* 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다. 그런 다음 **프로젝트 만들기**를 클릭 합니다.

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab1-09.png)

3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다. **> 기본 설정 편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab1-10.png)

4.  그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.

    ![빌드 설정 창에서 플랫폼을 UWP로 전환 합니다.](images/AzureLabs-Lab1-11.png)

5.  **파일 > 빌드 설정** 으로 이동 하 고 다음을 확인 합니다.

    1. **대상 장치** 는 **임의의 장치로**설정 됩니다.

        > Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.

    2. **빌드 형식이** **D3D** 로 설정 됩니다.
    3. **SDK** 가 **최신 설치** 로 설정 됨
    4. **Visual Studio 버전이** **최신 설치** 로 설정 됨
    5. **빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨
    6. 장면을 저장 하 고 빌드에 추가 합니다.

        1. 이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다. 저장 창이 표시 됩니다.

            ![열린 장면 추가 단추를 클릭 합니다.](images/AzureLabs-Lab1-12.png)

        2. 이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab1-13.png)

        3. 새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **MR_TranslationScene**를 입력 하 고 **저장**을 누릅니다.

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab1-14.png)

            > Unity 프로젝트와 연결 되어 있어야 하므로 *자산* 폴더 내에 unity 장면을 저장 해야 합니다. 배경 폴더 (및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구조화 하는 일반적인 방법입니다.

    7. *빌드 설정*의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.

6. *빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다. 

    ![플레이어 설정을 엽니다.](images/AzureLabs-Lab1-15.png)

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. **기타 설정** 탭에서 다음을 수행 합니다.

        1. **Scripting Runtime 버전** 은 **안정적** 이어야 합니다 (.net 3.5 해당).
        2. **Scripting 백엔드** 는 **.net** 이어야 합니다.
        3. **API 호환성 수준은** **.net 4.6** 이어야 합니다.

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab1-16.png)
      
    2. **게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.

        1. **InternetClient**
        2. **마이크로**

            ![게시 설정을 업데이트 하는 중입니다.](images/AzureLabs-Lab1-17.png)

    3. 패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab1-18.png)

8.  **빌드 설정**으로 돌아가서 *Unity C# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).

## <a name="chapter-3--main-camera-setup"></a>3 장-기본 카메라 설정

> [!IMPORTANT]
> 이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [unitypackage를 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)하 여 프로젝트에 [*사용자 지정 패키지로*](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [5 장](#chapter-5--create-the-results-class)에서 계속 합니다. Unity 프로젝트를 만들어야 합니다.

1.  *계층 패널*에서 **주 카메라**라는 개체를 찾을 수 있습니다 .이 개체는 응용 프로그램 "내부"에 있는 경우의 "헤드" 관점을 나타냅니다.
2.  앞의 Unity 대시보드를 사용 하 여 **기본 카메라 GameObject**를 선택 합니다. *검사기 패널* (일반적으로 대시보드 내에서 오른쪽에 있음)에는 해당 *GameObject*의 다양 한 구성 요소, 위쪽의 *변환* , *카메라*및 기타 구성 요소가 표시 됩니다. 기본 카메라의 변환을 다시 설정 해야 올바른 위치에 배치 됩니다.
3.  이렇게 하려면 카메라의 *변형* 구성 요소 옆에 있는 **기어** 아이콘을 선택 하 고 **다시 설정**을 선택 합니다. 

    ![기본 카메라 변환을 다시 설정 합니다.](images/AzureLabs-Lab1-19.png)
 
4.  *변환* 구성 요소는 다음과 같습니다.

    1. *위치* 는 **0, 0,** 0으로 설정 됩니다.
    2. *회전이* **0, 0, 0** 으로 설정 됩니다.
    3. 및 *소수 자릿수* 는 **1, 1, 1** 로 설정 됩니다.

        ![카메라에 대 한 변환 정보](images/AzureLabs-Lab1-20.png)

5.  그런 다음 **기본 카메라** 개체를 선택 하 고 *검사기 패널*의 맨 아래에 있는 **구성 요소 추가** 단추를 참조 하세요. 
6.  이 단추를 선택 하 고 아래와 같이 **오디오 원본** 이라는 구성 요소에 대 한 *오디오 소스* 를 검색 필드에 입력 하거나 섹션을 탐색 하 여 검색 하 고 선택한 다음 선택 합니다. (또한 enter 키를 누르면 작동 함)
7.  아래와 같이 *오디오 원본* 구성 요소가 **기본 카메라**에 추가 됩니다.

    ![오디오 원본 구성 요소를 추가 합니다.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Microsoft HoloLens의 경우 **기본 카메라**의 **카메라** 구성 요소에 포함 되는 다음도 변경 해야 합니다.
    > - **플래그 지우기:** 단색입니다.
    > - **배경** ' Black, Alpha 0 ' – 16 진수 색: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>4 장-디버그 캔버스 설정

변환의 입력 및 출력을 표시 하려면 기본 UI를 만들어야 합니다. 이 과정에서는 데이터를 표시 하는 여러 ' Text ' 개체를 포함 하는 Canvas UI 개체를 만듭니다.

1.  *계층 패널*의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **UI**에서 **캔버스**를 추가 합니다.

    ![새 Canvas UI 개체를 추가 합니다.](images/AzureLabs-Lab1-22.png)

2.  Canvas 개체가 선택 된 상태에서 ' Canvas ' 구성 요소 내의 *검사기 패널* 에서 **렌더링 모드** 를 **세계 공간**으로 변경 합니다. 
3.  다음으로, *검사기 패널의 Rect 변환*에서 다음 매개 변수를 변경 합니다.

    1. *POS*    X 0 Z 40 -  
    2. *너비* -500
    3. *높이* -300
    4. *크기 조정* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![캔버스의 rect 변환을 업데이트 합니다.](images/AzureLabs-Lab1-23.png)
 
4.  *계층 패널*의 **UI**아래에서 **캔버스** 를 마우스 오른쪽 단추로 클릭 하 고 **패널**을 추가 합니다. 이 **패널** 은 장면에 표시 되는 텍스트에 대 한 배경을 제공 합니다.
5.  *계층 패널*의 **패널** 에서 **UI**를 마우스 오른쪽 단추로 클릭 하 고 **텍스트 개체**를 추가 합니다. 총 4 개의 UI 텍스트 개체를 만들 때까지 동일한 프로세스를 반복 합니다 (힌트: 첫 번째 ' 텍스트 ' 개체가 선택 된 경우 **' ctrl ' + d '** 를 눌러 합계를 4 개까지)를 복제할 수 있습니다. 
6.  각 **텍스트 개체**에 대해 선택 하 고 아래 표를 사용 하 여 *검사기 패널*에서 매개 변수를 설정 합니다.

    1. *Rect Transform* 구성 요소의 경우:

        | 이름                   | 변환 *위치*             | 너비      | 높이    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. **텍스트 (스크립트)** 구성 요소:


        | 이름                   | 텍스트 모드               | 글꼴 크기    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | 마이크 상태: | 20           |
        | AzureResponseLabel     | Azure 웹 응답 | 20           |
        | DictationLabel         |   앞서 언급 한 것입니다.   | 20           |
        | TranslationResultLabel |    변환    | 20           |

        ![UI 레이블에 해당 하는 값을 입력 합니다.](images/AzureLabs-Lab1-24.png)

    3. 또한 글꼴 스타일을 **굵게 표시**합니다. 이렇게 하면 텍스트를 더 쉽게 읽을 수 있습니다.

        ![굵은 글꼴입니다.](images/AzureLabs-Lab1-25.png)

7.  [5 장](#chapter-5--create-the-results-class)에서 만든 각 *ui 텍스트 개체* 에 대해 새 *자식* **ui 텍스트 개체**를 만듭니다. 이러한 자식은 응용 프로그램의 출력을 표시 합니다. 원하는 부모 (예: *MicrophoneStatusLabel*)를 마우스 오른쪽 단추로 클릭 한 다음 **UI** 를 선택 하 고 **텍스트**를 선택 하 여 *자식* 개체를 만듭니다.
8.  이러한 각 자식에 대해 선택 하 고 아래 표를 사용 하 여 검사기 패널에서 매개 변수를 설정 합니다.

    1. **Rect Transform** 구성 요소의 경우:

        | 이름                  | 변환 *위치* | 너비      | 높이    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y-30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y-30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y-30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y-30 Z 0          | 300        | 30        |

    2. **텍스트 (스크립트)** 구성 요소:

        | 이름                  | 텍스트 모드          | 글꼴 크기    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 다음으로 각 텍스트 구성 요소에 대 한 ' 중앙 ' 맞춤 옵션을 선택 합니다.

    ![텍스트 맞춤.](images/AzureLabs-Lab1-26.png)

10. **자식 UI 텍스트** 개체를 쉽게 읽을 수 있도록 하려면 *색*을 변경 합니다. *색*옆에 있는 막대 (현재 ' 검은색 ')를 클릭 하 여이 작업을 수행 합니다. 

    ![UI 텍스트 출력에 해당 하는 값을 입력 합니다.](images/AzureLabs-Lab1-27.png)
 
11. 그런 다음, 작은 *색* 창에서 *16 진수 색* 을 다음과 같이 변경 합니다. **0032EAFF**

    ![색을 파랑으로 업데이트 합니다.](images/AzureLabs-Lab1-28.png)
 
12. **UI** 를 표시 하는 방법은 다음과 같습니다.
    1.  *계층 패널*에서 다음을 수행 합니다.

        ![제공 된 구조체에 계층이 있습니다.](images/AzureLabs-Lab1-29.png)

    2.  *장면* 및 *게임 보기*에서 다음을 수행 합니다.

        ![장면 및 게임 보기가 동일한 구조에 있어야 합니다.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>5 장-결과 클래스 만들기

만들어야 하는 첫 번째 스크립트는 변환 결과를 확인 하는 방법을 제공 하는 *결과* 클래스입니다. 클래스는 다음을 저장 하 고 표시 합니다. 

- Azure의 응답 결과입니다.
- 마이크 상태입니다. 
- 받아쓰기 (음성 텍스트)의 결과입니다.
- 변환의 결과입니다.

이 클래스를 만들려면: 

1.  *프로젝트 패널*을 마우스 오른쪽 단추로 클릭 하 고 **> 폴더를 만듭니다**. 폴더 이름을 **스크립트**로 합니다. 
 
    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab1-31.png)

    ![Scripts 폴더를 엽니다.](images/AzureLabs-Lab1-32.png)
 
2.  **Scripts** 폴더 만들기를 사용 하 여 두 번 클릭 하 여 엽니다. 그런 다음 해당 폴더 내에서를 마우스 오른쪽 단추로 클릭 하 고 **> 만들기** 를 선택 하 고  **C# 스크립트**를 선택 합니다. 스크립트 *결과*의 이름을로 합니다. 

    ![첫 번째 스크립트를 만듭니다.](images/AzureLabs-Lab1-33.png)
 
3.  새 *결과* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.
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

6.  그런 다음, 다시 사용할 수 있는 *()* 메서드를 추가 합니다 .이 메서드는 클래스가 초기화 될 때 호출 됩니다. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  마지막으로 다양 한 결과 정보를 UI에 출력 하는 메서드를 추가 합니다. 

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

8.  *Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-6--create-the-microphonemanager-class"></a>6 장 – *MicrophoneManager* 클래스 만들기

만들려는 두 번째 클래스는 *MicrophoneManager*입니다.

이 클래스는 다음을 담당 합니다.

- 헤드셋 또는 컴퓨터에 연결 된 기록 장치 검색 (기본값)
- 오디오 (음성)를 캡처하고 받아쓰기를 사용 하 여 문자열로 저장 합니다.
- 음성이 일시 중지 되 면 받아쓰기를 Translator 클래스에 제출 합니다.
- 원할 경우 음성 캡처를 중지할 수 있는 메서드를 호스팅합니다.

이 클래스를 만들려면: 
1.  **스크립트** 폴더를 두 번 클릭 하 여 엽니다. 
2.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다. 스크립트 이름을 *MicrophoneManager*로 합니다. 
3.  새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
4.  *MicrophoneManager* 클래스의 맨 위에서 다음과 같이 네임 스페이스를 업데이트 합니다.

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  그런 다음 *MicrophoneManager* 클래스 안에 다음 변수를 추가 합니다.

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

6.  이제 해제 *()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다. 이러한 작업은 클래스가 초기화 될 때 호출 됩니다.

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

7.  이 클래스는 사용 하지 않으므로 *Update ()* 메서드를 *삭제할* 수 있습니다.
8.  이제 앱에서 음성 캡처를 시작 및 중지 하는 데 사용 하는 메서드를 사용 하 여 곧 빌드할 *변환기* 클래스로 전달 합니다. 다음 코드를 복사 하 여 *Start ()* 메서드 아래에 붙여 넣습니다.

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
    > 이 응용 프로그램은이 응용 프로그램을 사용 하지 않지만 여기서는 *Stopcapturingaudio ()* 메서드도 제공 했습니다. 응용 프로그램에서 오디오 캡처를 중지 하는 기능을 구현 해야 합니다.

9.  이제 음성이 중지 될 때 호출 되는 받아쓰기 처리기를 추가 해야 합니다. 그런 다음이 메서드는 지시한 텍스트를 *Translator* 클래스로 전달 합니다.

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

10. Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 해야 합니다.

> [!WARNING]  
> 이 시점에서 *Unity 편집기 콘솔* 패널에 오류가 표시 됩니다 ("' 번역기 ' 이름 '이 (가) 없습니다 ..."). 이는 코드에서 다음 챕터에서 만들 *Translator* 클래스를 참조 하기 때문입니다.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>7 장 – Azure 및 translator 서비스에 대 한 호출

생성 해야 하는 마지막 스크립트는 *Translator* 클래스입니다. 

이 클래스는 다음을 담당 합니다.

-   **인증 토큰**에 대해 Exchange에서 *Azure*를 사용 하 여 앱을 인증 합니다.
-   **인증 토큰** 을 사용 하 여 번역할 텍스트 ( *MicrophoneManager* 클래스에서 수신)를 제출 합니다.
-   번역 된 결과를 수신 하 고 UI에서 시각화할 *결과* 클래스에 전달 합니다.

이 클래스를 만들려면: 
1.  이전에 만든 **스크립트** 폴더로 이동 합니다. 
2.  **프로젝트 패널**을 마우스 오른쪽 단추로 클릭 하 **> C# 스크립트를 만듭니다**. 스크립트 *변환기*를 호출 합니다.
3.  새 *변환기* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.
4.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  그런 다음 *Translator* 클래스 내에 다음 변수를 추가 합니다.

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
    > - 언어 **열거형** 에 삽입 된 언어는 예제 일 뿐입니다. 원한다 면 자유롭게 추가할 수 있습니다. [API는 60 개 이상의 언어](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (클링온어 포함)를 지원 합니다.
    > - 사용 가능한 언어를 포함 하는 [대화형 페이지는 더 많이](https://www.microsoft.com/translator/business/languages/)있습니다. 페이지는 사이트 언어가 ' en-us '로 설정 된 경우에만 작동 하는 것 처럼 보이지만 Microsoft 사이트는 네이티브 언어로 리디렉션될 가능성이 높습니다. 페이지의 맨 아래에 있는 사이트 언어를 변경 하거나 URL을 변경할 수 있습니다.
    > - 위의 코드 조각에서 **authorizationkey** 값은 *Azure Translator Text API*에 구독할 때 받은 **키** 여야 합니다. 이 내용은 [1 장](#chapter-1--the-azure-portal)에서 설명 했습니다.

6.  이제 해제 *()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다. 
7.  이 경우 코드는 *토큰*을 가져오기 위해 권한 부여 키를 사용 하 여 *Azure* 에 대 한 호출을 수행 합니다.

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
    > 토큰은 10 분 후에 만료 됩니다. 앱의 시나리오에 따라 동일한 코 루틴 호출을 여러 번 수행 해야 할 수도 있습니다.

8.  토큰을 가져오는 코 루틴는 다음과 같습니다.

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
    > IEnumerator 메서드 **GetTokenCoroutine ()** 의 이름을 편집 하는 경우 위의 코드에서 *StartCoroutine* 및 *StopCoroutine* 호출 문자열 값을 업데이트 해야 합니다. [Unity 설명서에 따라](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)특정 *코 루틴*을 중지 하려면 string value 메서드를 사용 해야 합니다.

9.  다음으로, 코 루틴 (바로 아래에 "지원" 스트림 메서드 포함)를 추가 하 여 *MicrophoneManager* 클래스에서 받은 텍스트의 변환을 가져옵니다. 이 코드는 *Azure Translator Text API*에 보낼 쿼리 문자열을 만든 다음 내부 Unity UnityWebRequest 클래스를 사용 하 여 쿼리 문자열을 사용 하 여 끝점에 대 한 ' Get ' 호출을 수행 합니다. 결과를 사용 하 여 결과 개체에서 변환을 설정 합니다. 아래 코드는 구현을 보여 줍니다.

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

10. *Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-8--configure-the-unity-scene"></a>8 장-Unity 장면 구성

1.  Unity 편집기로 돌아가서 **Scripts** 폴더의 *Results* *클래스를* 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다.
2.  **주 카메라** 를 클릭 하 고 *검사기 패널*을 확인 합니다. 새로 추가한 *스크립트* 구성 요소에는 빈 값을 갖는 4 개의 필드가 있습니다. 다음은 코드의 속성에 대 한 출력 참조입니다. 
3.  아래 이미지에 표시 된 것 처럼 적절 한 **텍스트** 개체를 *계층 패널* 에서 4 개의 슬롯으로 끕니다.

    ![지정 된 값을 사용 하 여 대상 참조를 업데이트 합니다.](images/AzureLabs-Lab1-34.png)
  
4.  그런 다음 **Scripts** 폴더의 *Translator* 클래스를 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다. 
5.  그런 다음 **Scripts** 폴더에서 *MicrophoneManager* 클래스를 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다. 
6.  마지막으로, **주 카메라** 를 클릭 하 고 *검사기 패널*을 확인 합니다. 끌어 온 스크립트에서 언어를 설정 하는 데 사용할 수 있는 두 개의 드롭다운 상자가 표시 됩니다.
 
    ![원하는 번역 언어가 입력 인지 확인 합니다.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>9 장-혼합 현실에서 테스트

이 시점에서 장면이 제대로 구현 되었는지 테스트 해야 합니다.

다음을 확인합니다.

- [1 장](#chapter-1--the-azure-portal) 에서 설명한 모든 설정이 올바르게 설정 됩니다. 
- *결과*, *번역기*및 *MicrophoneManager*스크립트는 **주 카메라** 개체에 연결 됩니다. 
- *Azure Translator Text API* 서비스 **키** 를 *Translator* 스크립트 내 **authorizationkey** 변수 내에 배치 했습니다.  
- *기본 카메라 검사기 패널* 의 모든 필드가 제대로 할당 됩니다.
- 장면을 실행할 때 마이크가 작동 합니다 (그렇지 않은 경우 연결 된 마이크가 *기본* 장치이 고 [Windows 내에서 올바르게 설정](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)했는지 확인).

*Unity 편집기*에서 **재생** 단추를 눌러 몰입 형 헤드셋을 테스트할 수 있습니다.
앱은 연결 된 모던 헤드셋을 통해 작동 해야 합니다.

> [!WARNING]  
> Unity 콘솔에 기본 오디오 장치 변경에 대 한 오류가 표시 되 면 장면이 예상 대로 작동 하지 않을 수 있습니다. 이는 혼합 현실 포털이이를 포함 하는 헤드셋의 기본 제공 마이크를 처리 하는 방식 때문입니다. 이 오류가 표시 되 면 장면을 중지 하 고 다시 시작 하 고 예상 대로 작동 해야 합니다.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>10 장 – 로컬 컴퓨터에서 UWP 솔루션 및 테스트용으로 로드 빌드

이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.

1.  **빌드 설정**으로 이동 합니다. **빌드 설정 > 파일 ...**
2.  **빌드 설정** 창에서 **빌드**를 클릭 합니다.

    ![Unity 장면을 빌드합니다.](images/AzureLabs-Lab1-36.png)
  
3.  아직 없는 경우 tick **Unity C# 프로젝트**입니다.
4.  **빌드**를 클릭합니다. Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 *파일 탐색기* 창을 시작 합니다. 이제 해당 폴더를 만들고 이름을 *App*으로 만듭니다. 그런 다음 *앱* 폴더를 선택 하 고 **폴더 선택**을 누릅니다. 
5.  Unity는 *응용* 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다. 
6.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 *파일 탐색기* 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)

## <a name="chapter-11--deploy-your-application"></a>11 장 – 응용 프로그램 배포

응용 프로그램을 배포 하려면:

1.  새 Unity 빌드 ( *앱* 폴더)로 이동 하 여 *Visual Studio*에서 솔루션 파일을 엽니다.
2.  솔루션 구성에서 **디버그**를 선택 합니다.
3.  솔루션 플랫폼에서 **x86**, **로컬 컴퓨터**를 선택 합니다. 

    > Microsoft HoloLens의 경우 컴퓨터에 테더 링 된 하지 않도록 *원격 컴퓨터*를 설정 하는 것이 더 쉬울 수 있습니다. 그러나 다음을 수행 해야 합니다.
    > - HoloLens의 **IP 주소** 를 알고 있습니다. *설정 > 네트워크 & 인터넷 > Wi-fi > 고급 옵션*에서 찾을 수 있습니다. IPv4는 사용 해야 하는 주소입니다. 
    > - *개발자 모드가* **설정**되어 있는지 확인 합니다. *개발자를 위한 업데이트 & 보안 > > 설정*에서 찾을 수 있습니다.

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab1-37.png)
    
 
4.  **빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 PC에 테스트용으로 로드.
5.  이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.
6.  앱이 시작 되 면 마이크에 대 한 액세스 권한을 부여 하 라는 메시지가 표시 됩니다. **예** 단추를 클릭 해야 합니다.
7.  이제 번역을 시작할 준비가 되었습니다.

## <a name="your-finished-translation-text-api-application"></a>완성 된 번역 텍스트 API 응용 프로그램

축 하 합니다. Azure Translation 텍스트 API를 활용 하 여 음성을 번역 된 텍스트로 변환 하는 혼합 현실 앱을 빌드 했습니다.

![최종 제품.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

텍스트 음성 변환 기능을 앱에 추가 하 여 반환 된 텍스트를 말할 수 있나요?

### <a name="exercise-2"></a>연습 2

사용자가 앱 자체 내에서 원본 및 출력 언어 (' from ' 및 ' to ')를 변경할 수 있으므로 언어를 변경할 때마다 앱을 다시 빌드할 필요가 없습니다.
