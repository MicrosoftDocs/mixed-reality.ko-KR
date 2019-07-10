---
title: MR 및 311-Microsoft Graph, Azure
description: Microsoft Graph를 활용 하 고 혼합된 현실 응용 프로그램에서 생산성을 높이 데이터에 연결 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, microsoft graph, hololens, 몰입 형, vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694522"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-and-azure-311---microsoft-graph"></a>MR 및 311-Microsoft Graph, Azure

이 과정에서 사용 하는 방법을 배우게 됩니다 *Microsoft Graph* 혼합된 현실 응용 프로그램에서 보안 인증을 사용 하 여 Microsoft 계정에 로그인 합니다. 그런 다음 검색 하 고 예약 된 회의 응용 프로그램 인터페이스에 표시 됩니다.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* 는 여러 Microsoft 서비스에 액세스할 수 있도록 Api의 집합입니다. Microsoft에 설명 합니다 Microsoft Graph 관계에 의해 연결 된 리소스의 행렬으로 응용 프로그램을 모든 종류의 연결 된 사용자 데이터에 액세스할 수 있도록 의미 합니다. 자세한 내용은 참조는 [Microsoft Graph 페이지](https://developer.microsoft.com/graph)합니다.

개발 응시를 안전 하 게 Microsoft 계정에 로그인 하 라는 메시지가 나타납니다 구를 누른 다음에 사용자가 지시 하는 위치는 앱을 만드는 포함 됩니다. 계정에 로그인 한 사용자를 하루에 예약 된 회의의 목록을 볼 수 됩니다.

이 과정을 마치면 다음을 수행 하는 일을 할 수는 HoloLens 응용 프로그램을 혼합된 현실이 제공 됩니다.

1.  사용자 (로그인을 다시 앱으로 다시를 앱 외부로 이동) Microsoft 계정에 로그인 하 라는 메시지를 표시할 개체 탭 탭 제스처를 사용 합니다.
2.  하루에 예약 된 회의의 목록을 봅니다. 

응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다. 이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다. 혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 311 Azure: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다. 또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다. 내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.

다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.

- PC 개발
- [Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여
- Azure 설정 및 Microsoft Graph 데이터 검색에 대 한 인터넷 액세스
- 유효한 **Microsoft 계정** (개인 또는 회사/학교)
- 동일한 Microsoft 계정을 사용 하 여 현재 날짜에 대해 예약 된 몇 회의

### <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
2.  설정 하 고 여 HoloLens를 테스트 합니다. 에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다. 
3.  (때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다. 

보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.

센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>1-장 응용 프로그램 등록 포털에서 앱 만들기

시작 하려면를 만들어 응용 프로그램에 등록 해야 합니다 **응용 프로그램 등록 포털**합니다.

이 챕터에 수도 있습니다. 호출을 수행할 수 있도록 서비스 키 *Microsoft Graph* 계정 콘텐츠를 액세스할 수 있습니다.

1.  로 이동 합니다 [Microsoft 응용 프로그램 등록 포털](https://apps.dev.microsoft.com) 및 Microsoft 계정으로 로그인 합니다. 로그인 하면, 리디렉션됩니다 하는 **응용 프로그램 등록 포털**합니다.

2.  에 **내 응용 프로그램** 섹션에서 단추를 클릭 **앱 추가**합니다.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > 합니다 **응용 프로그램 등록 포털** 여부 이전에 작업을 수행한에 따라 다르게 보일 수 있습니다 *Microsoft Graph*합니다. 아래 스크린샷은 이러한 서로 다른 버전을 표시 합니다.

3.  응용 프로그램 및 클릭에 대 한 이름 추가 **만들기**합니다.

    ![](images/AzureLabs-Lab311-03.png)

4.  응용 프로그램을 만든 후 응용 프로그램 기본 페이지로 리디렉션됩니다. 복사 합니다 **응용 프로그램 Id** 안전한 곳에이 값을 메모를 코드에서 곧 사용 됩니다.

    ![](images/AzureLabs-Lab311-04.png)

5.  에 **플랫폼** 섹션에, 반드시 **네이티브 응용 프로그램** 표시 됩니다. 하는 경우 *되지* 클릭할 **플랫폼 추가** 선택한 **네이티브 응용 프로그램**합니다.

    ![](images/AzureLabs-Lab311-05.png)

6.  같은 페이지에 이라는 섹션에서 아래로 스크롤하여 **Microsoft Graph 권한** 응용 프로그램에 대 한 사용 권한을 추가 해야 합니다. 클릭할 **추가** 옆에 **위임 된 권한**합니다.

    ![](images/AzureLabs-Lab311-06.png)

7.  사용자의 일정에 액세스 하도록 응용 프로그램을 원하므로 확인란 호출 **Calendars.Read** 클릭 **확인**합니다.

    ![](images/AzureLabs-Lab311-07.png)

8.  아래로 스크롤하여을 클릭 합니다 **저장** 단추입니다.

    ![](images/AzureLabs-Lab311-08.png)

9.  저장을 확인할 수는 및에서 로그 아웃 수를 **응용 프로그램 등록 포털**합니다.

## <a name="chapter-2---set-up-the-unity-project"></a>2 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 *Unity* 누릅니다 **새로 만들기**합니다.

    ![](images/AzureLabs-Lab311-09.png)

2.  Unity 프로젝트 이름을 제공 해야 합니다. 삽입 **MSGraphMR**합니다. 프로젝트 템플릿은 설정 되어 있는지 확인 **3D**합니다. 설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![](images/AzureLabs-Lab311-10.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집할** > **기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![](images/AzureLabs-Lab311-11.png)

4.  로 이동 **파일** > **빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환** 선택 항목을 적용 하는 단추입니다.

    ![](images/AzureLabs-Lab311-12.png)

5.  있는 동안 **파일** > **빌드 설정**, 있는지 확인 합니다.

    1. **장치를 대상** 로 설정 된 **HoloLens**
    2. **빌드 형식** 로 설정 된 **D3D**
    3. **SDK** 로 설정 된 **가장 최근에 설치 된**
    4. **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**
    5. **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**
    6. 장면 저장 하 고 빌드에 추가 합니다.

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.

            ![](images/AzureLabs-Lab311-13.png)

        2. 따라서 모든 미래를 장면에 대 한 새 폴더를 만듭니다. 선택 된 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**.

            ![](images/AzureLabs-Lab311-14.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **MR_ComputerVisionScene**, 클릭 **저장** .

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > 주의 내에서 Unity 장면에 저장 해야 합니다 *자산* 폴더를 Unity 프로젝트와 연결 해야 합니다. 백그라운드에서 폴더 (및 다른 유사한 폴더)를 만들기 Unity 프로젝트를 구성 하는 일반적인 방법입니다.

    7.  설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.

6.  에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한. 

    ![](images/AzureLabs-Lab311-16.png)

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. 에 **기타 설정** 탭:

        1.  **스크립팅** **런타임 버전** 있어야 **실험적** (.NET 4.6 동등), 편집기를 다시 시작 해야를 트리거하는 합니다.

        2. **백 엔드를 스크립팅** 있어야 **.NET**

        3. **API 호환성 수준** 있어야 **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  내 합니다 **게시 설정** 탭의 **기능**, 확인:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 확인 **지원 되는 가상 현실**, 있는지 확인 합니다 **Windows Mixed Reality SDK** 추가 됩니다.

        ![](images/AzureLabs-Lab311-19.png)

8.  년대 *빌드 설정*를 *Unity C# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.

9.  닫기 합니다 *빌드 설정* 창입니다.

10.  장면 및 프로젝트 저장 (**파일** > **장면 저장 파일** > **프로젝트 저장**).

## <a name="chapter-3---import-libraries-in-unity"></a>3 장-Unity에서 가져오기 라이브러리

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [311.unitypackage-MR-Azure](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [5 장](#chapter-5---create-meetingsui-class)합니다.

사용 하도록 *Microsoft Graph* 해야 하는 Unity 내에서 사용 합니다 **Microsoft.Identity.Client** DLL입니다. 그러나 Microsoft Graph SDK를 사용 하는 것, 즉 프로젝트 post-build 편집 Unity 프로젝트를 구성한 후에 NuGet 패키지를 추가 해야 합니다 합니다. Unity를 직접 필요한 Dll을 가져오는 간단한 간주 됩니다.

> [!NOTE]
> 플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다. 이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.

가져오려는 *Microsoft Graph* 고유한 프로젝트로 [MSGraph_LabPlugins.zip 파일 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)합니다. 테스트 된 라이브러리의 버전을 사용 하 여이 패키지를 만들었습니다.

Unity 프로젝트에 사용자 지정 Dll을 추가 하는 방법에 대 한 자세한 내용을 원한다 [이 링크를 따라](https://docs.unity3d.com/Manual/UsingDLL.html)합니다.

패키지를 가져오려면:

1.  Unity를 사용 하 여 Unity 패키지를 추가 합니다 **자산** > **패키지 가져오기** > **Custom Package** 메뉴 옵션입니다. 방금 다운로드 한 패키지를 선택 합니다.

2.  에 **Unity 패키지 가져오기** 표시 되는 상자에서 아래에 있는 포함 하 여 모든 것을 확인 **플러그 인** 을 선택 합니다.

    ![](images/AzureLabs-Lab311-20.png)

3.  클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.

4.  로 이동 합니다 **MSGraph** 아래에 폴더 **플러그 인** 에 *프로젝트 패널* 이라는 플러그 인을 선택 하 고 **Microsoft.Identity.Client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  사용 하 여는 *플러그 인* 되도록 선택 하면 **Any 플랫폼** 이 선택 취소 한 다음 확인 **WSAPlayer** 이 선택도 취소 클릭 **적용**. 이 파일이 올바르게 구성 되어 있는지 확인 합니다.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > 이러한 플러그 인을 표시만 Unity 편집기에서 사용 되도록 구성 합니다. 다양 한 Dll 프로젝트가 유니버설 Windows 응용 프로그램으로 Unity에서 내보낸 후 사용 되는 WSA 폴더에 있습니다.

6.  열어야 할 때 다음에 **WSA** 폴더 내에서 합니다 **MSGraph** 폴더입니다. 방금 구성한 동일한 파일의 복사본을 볼 수 있습니다. 파일을 선택한 다음 검사기:

    -   되도록 **Any 플랫폼** 는 **unchecked**, 하 고 **만** **WSAPlayer** 는 **체크**.

    -   확인 **SDK** 로 설정 된 **UWP**, 및 **백 엔드 스크립팅** 로 설정 된 **.net**

    -   했는지 **처리 하지** 됩니다 **체크**합니다.

        ![](images/AzureLabs-Lab311-23.png)

7.  **적용**을 클릭합니다.

## <a name="chapter-4---camera-setup"></a>4 장-카메라 설정

이 장에서 동안 주 카메라 장면의을 설정 합니다.

1.  에 *계층 패널*를 선택 합니다 **주 카메라**합니다.

2.  선택한 후에의 모든 구성 요소를 볼 수는 합니다 **주 카메라** 에 *검사기* 패널입니다.

    1.  합니다 **카메라 개체** 이름은 **주 카메라** (맞춤법 참고!)

    2.  주 카메라 **태그** 으로 설정 되어 있어야 **MainCamera** (맞춤법 참고!)

    3.  있는지 확인 합니다 **변환 위치** 로 설정 된 **0, 0, 0**

    4.  설정할 **플래그 지우기** 에 **단색**

    5.  설정 된 **배경색** 카메라 구성 요소의 **검정, 알파 0** **(코드를 16 진수: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  마지막 개체 구조를 *계층 패널* 아래 이미지에 표시 된 것 처럼 보여야 합니다.

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>5 장-MeetingsUI 클래스 만들기

생성 해야 하는 첫 번째 스크립트 **MeetingsUI**를 담당 하는 호스팅 및 (환영 메시지, 지침 및 모임 세부 정보) 응용 프로그램의 UI를 채우는 합니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **자산** 폴더에는 *프로젝트 패널*을 선택한 후 **만들기** > **폴더**합니다. 폴더의 이름을 **스크립트**합니다.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  열기는 **스크립트** 폴더 그런 다음 해당 폴더 내에서 마우스 오른쪽 단추로 클릭 합니다 **만들기**  >   **C# 스크립트**. 스크립트 이름을 **MeetingsUI 합니다.**

    ![](images/AzureLabs-Lab311-28.png)

3.  새 두 번 클릭 **MeetingsUI** 스크립트를 사용 하 여 열고 *Visual Studio*합니다.

4.  다음 네임 스페이스를 삽입 합니다.

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  클래스 내에서 다음 변수를 삽입 합니다.

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  그런 다음 대체는 **start ()** 메서드 추가 **Awake()** 메서드. 이러한 클래스를 초기화할 때 호출 됩니다.

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  생성을 담당 하는 메서드를 추가 합니다 *회의 UI* 현재 모임 요청 하는 경우 입력:

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **삭제할** 는 **update ()** 메서드 및 **변경 내용을 저장** Unity를 반환 하기 전에 Visual Studio에서. 

## <a name="chapter-6---create-the-graph-class"></a>-6 장 그래프 클래스 만들기

만들려면 다음 스크립트를 **그래프** 스크립트입니다. 이 스크립트는 사용자를 인증 하 고 사용자의 일정에서 현재 날짜에 대 한 예약 된 회의 검색에 대 한 호출을 담당 합니다.

이 클래스를 만들려면:

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다.

2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**. 스크립트 이름을 **그래프**합니다.

3.  스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.

4.  다음 네임 스페이스를 삽입 합니다.

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > 이 스크립트의 코드 부분 래핑하는 것을 알 수 있습니다 [미리 컴파일 지시문](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), Visual Studio 솔루션을 빌드할 때 라이브러리를 사용 하 여 문제를 방지 하기 위해서입니다.

5.  삭제를 **start ()** 하 고 **update ()** 메서드를 사용 되지 것입니다.

6.  외부 합니다 **그래프** 클래스, 매일 예약 된 회의 나타내는 JSON 개체를 deserialize 하는 데 필요한 다음 개체를 삽입 합니다.

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  내부를 **그래프** 클래스를 다음 변수를 추가 합니다.

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > 변경 합니다 **appId** 값을 합니다 **앱 Id** 에서 기록한  **[1 장](#chapter-1---create-your-app-in-the-application-registration-portal), 4 단계**합니다. 이 값에 표시 된 것과 동일 해야 합니다 **응용 프로그램 등록 포털** 응용 프로그램 등록 페이지에 있습니다.

8.  내 합니다 **그래프** 클래스, 메서드를 추가 합니다 **SignInAsync()** 및 **AquireTokenAsync()** 는 사용자 로그인 자격 증명을 삽입 하 라는 메시지가 표시 됩니다.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  다음 두 메서드를 추가 합니다.

    1.  **BuildTodayCalendarEndpoint()** , 빌드 및 예약 된 회의 검색 하는 기간을 지정 하는 URI입니다.

    2.  **ListMeetingsAsync()** 에 요청에서 예약 된 회의 *Microsoft Graph*합니다.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. 이제 완료 합니다 **그래프** 스크립트입니다. **변경 내용을 저장** Unity를 반환 하기 전에 Visual Studio에서.

## <a name="chapter-7---create-the-gazeinput-script"></a>7-장 GazeInput 스크립트 만들기

이제 만들려는 합니다 **GazeInput**합니다. 이 클래스는 처리 하 고 사용자의 게이즈를 사용 하는 추적을 **Raycast** 에서 들어오는 합니다 **주 카메라**, 앞으로 프로젝션 합니다.

스크립트를 만들려면:

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다.

2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**. 스크립트 이름을 **GazeInput**합니다.

3.  스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.

4.  추가 함께 아래 것과 일치 하도록 네임 스페이스 코드를 변경는 ' **\[System.Serializable\]** ' 위의 태그에 **GazeInput** 클래스를 serialize 할 수 있도록 합니다.

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  내 합니다 **GazeInput** 클래스를 다음 변수를 추가 합니다.

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  추가 된 **CreateCursor()** 장면에서 HoloLens 커서를 만들고에서 메서드를 호출 하는 메서드는 **start ()** 메서드:

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  다음 방법 Raycast 게이즈를 사용 하도록 설정 하 고 추적 합니다 포커스가 있는 개체입니다.

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **변경 내용을 저장** Unity를 반환 하기 전에 Visual Studio에서.

## <a name="chapter-8---create-the-interactions-class"></a>8-장 상호 작용 클래스 만들기

만들려는 해야 합니다 **상호 작용** 담당 하는 스크립트:

-   처리를 **누릅니다** 상호 작용 및 **카메라 Gaze**, "단추" 장면에서 로그를 사용 하 여 상호 작용할 수 있습니다.

-   사용자와 상호 작용 하는 장면에서 개체 "단추"에서 로그를 만듭니다.

스크립트를 만들려면:

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다.

2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**. 스크립트 이름을 **상호 작용**합니다.

3.  스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.

4.  다음 네임 스페이스를 삽입 합니다.

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  상속을 변경 합니다 **상호 작용** 에서 클래스 *MonoBehaviour* 에 **GazeInput**합니다.

    ~~공용 클래스 상호 작용 합니다. MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  내부를 **상호 작용** 클래스에 다음 변수를 삽입 합니다.

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  대체는 **시작** 메서드를 '기본' 게이즈 클래스 메서드를 호출 하는 재정의 메서드를 사용 하는 것이 표시 됩니다. **Start ()** 입력된 인식에 대 한 등록 하 고 로그인을 만드는 클래스를 초기화 하는 경우 호출 될 *단추* 장면에서:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  추가 된 **CreateSignInButton()** 로그인을 인스턴스화하는 메서드를 *단추* 장면에서 해당 속성을 설정:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  추가 합니다 **GestureRecognizer_Tapped()** 메서드 수에 대 한 응답을 *탭* 사용자 이벤트입니다.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **삭제할** 는 **update ()** 메서드를 차례로 **변경 내용을 저장** Unity를 반환 하기 전에 Visual Studio에서.

## <a name="chapter-9---set-up-the-script-references"></a>9 장-스크립트 참조 설정

이 챕터에 배치 해야 합니다 **상호 작용** 스크립트에 **주 카메라**합니다. 해당 스크립트는 필요할 수 있는 다른 스크립트를 배치 하는 것을 처리 한 다음 합니다.

-  **스크립트** 폴더에는 *프로젝트 패널*, 스크립트를 끌어 **상호 작용** 에 **주 카메라** 개체, 다음 그림과 같이 합니다.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>10 장-태그 설정

코드를 응시 처리 태그를 사용 하 게 **SignInButton** 개체를 식별 하는 사용자가 상호 작용할에 로그인 하 *Microsoft Graph*합니다.

태그를 만들려면:

1.  Unity 편집기에서 클릭 합니다 **주 카메라** 에 *계층 패널*합니다.

2.  에 *검사기 패널* 클릭 합니다 **MainCamera** *태그* 드롭다운 목록을 열지 합니다. 클릭 **태그를 추가 하는 중...**

    ![](images/AzureLabs-Lab311-30.png)

3.  클릭 합니다 **+** 단추입니다.

    ![](images/AzureLabs-Lab311-31.png)

4.  태그 이름으로 작성할 **SignInButton** 고 저장을 클릭 합니다.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>11 장-UWP로 Unity 프로젝트 빌드

이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.

1.  이동할 *빌드 설정* (**파일* > *설정**빌드).

    ![](images/AzureLabs-Lab311-33.png)

2.  경우에 눈금 **Unity C\# 프로젝트**합니다.

3.  **빌드**를 클릭합니다. Unity가 시작 됩니다는 **파일 탐색기** 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다. 해당 폴더를 이제 만들고 이름을 **앱**합니다. 사용 하 여 다음 합니다 **앱** 폴더를 선택, 클릭 **폴더 선택**합니다.

4.  Unity 프로젝트를 빌드할 예정 된 **앱** 폴더입니다.

5.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.

## <a name="chapter-12---deploy-to-hololens"></a>12-장 HoloLens에 배포

HoloLens에 배포 합니다.

1.  (배포에 대 한 원격), 여 HoloLens의 IP 주소를 사용 해야 하 고 확인에 HoloLens가 **개발자 모드입니다.** 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1.  에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.

    2.  로 이동 **네트워크 및 인터넷** > **Wi-fi** > **고급 옵션**

    3.  참고 합니다 **IPv4** 주소입니다.

    4.  다음으로 다시 이동할 **설정을**, 한 다음 **업데이트 및 보안** > **개발자를 위한**

    5.  설정할 **에서 개발자 모드가**합니다.

2.  새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.

3.  에 **솔루션 구성** 선택 **디버그**합니다.

4.  에 **솔루션 플랫폼**를 선택 **x86, 원격 컴퓨터**합니다. 삽입 하 라는 메시지가 표시 됩니다는 **IP 주소** 원격 장치 (여 HoloLens,이 경우 둔).

    ![](images/AzureLabs-Lab311-34.png)

5.  로 이동 **빌드할** 메뉴를 클릭 **솔루션 배포** 을 사이드 로드에 HoloLens에 응용 프로그램입니다.

6.  앱에 HoloLens 시작할 준비가에 설치 된 앱 목록에 나타나야 합니다.

## <a name="your-microsoft-graph-hololens-application"></a>Microsoft Graph HoloLens 응용 프로그램

축 하 읽고 사용자 일정 데이터를 표시 하는 Microsoft Graph를 활용 하는 혼합된 현실 앱 빌드 했습니다.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

Microsoft Graph를 사용 하 여 사용자에 대 한 다른 정보를 표시 하려면

-   사용자 전자 메일 프로필 사진 / 전화 번호

### <a name="exercise-1"></a>연습 1

Microsoft Graph UI 이동할 음성 제어를 구현 합니다.
