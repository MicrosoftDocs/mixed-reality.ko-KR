---
title: MR 및 Azure 311-Microsoft Graph
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Microsoft Graph 활용 하 고 생산성을 높이는 데이터에 연결 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, microsoft graph, hololens, 몰입 형, vr
ms.openlocfilehash: 775971c4e4289d2dc963dfa2bf033192d9f3489e
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047200"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-and-azure-311---microsoft-graph"></a>MR 및 Azure 311-Microsoft Graph

이 과정에서는 혼합 현실 응용 프로그램 내에서 보안 인증을 사용 하 여 Microsoft 계정에 로그인 하는 데 *Microsoft Graph* 를 사용 하는 방법을 알아봅니다. 그런 다음 응용 프로그램 인터페이스에서 예약 된 모임을 검색 하 고 표시 합니다.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* 은 다양 한 Microsoft 서비스에 액세스할 수 있도록 설계 된 api 집합입니다. Microsoft는 관계를 통해 연결 되는 리소스의 행렬로 Microsoft Graph에 대해 설명 합니다. 즉, 응용 프로그램에서 모든 종류의 연결 된 사용자 데이터에 액세스할 수 있습니다. 자세한 내용은 [Microsoft Graph 페이지](https://developer.microsoft.com/graph)를 참조 하세요.

개발에는 사용자에 게 암호를 입력 하 라는 메시지가 표시 된 후 구를 탭 하 여 사용자에 게 안전 하 게 Microsoft 계정에 로그인 하 라는 메시지가 표시 되는 앱을 만들 수 있습니다. 자신의 계정에 로그인 한 후에는 사용자가 하루에 예약 된 모임 목록을 볼 수 있습니다.

이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 HoloLens 응용 프로그램이 만들어집니다.

1.  탭 제스처를 사용 하 여 개체를 탭 합니다. 그러면 사용자에 게 Microsoft 계정에 로그인 하 라는 메시지가 표시 됩니다 .이를 통해 로그인 하 고 다시 앱으로 다시 이동 합니다.
2.  하루에 예약 된 모임 목록을 표시 합니다. 

응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다. 이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다. 이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다. [도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- 개발 PC
- [개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 개발자 모드를 사용 하는 [Microsoft HoloLens](hololens-hardware-details.md)
- Azure 설정 및 Microsoft Graph 데이터 검색을 위한 인터넷 액세스
- 유효한 **Microsoft 계정** (개인 또는 회사/학교)
- 동일한 Microsoft 계정을 사용 하 여 현재 날짜에 대해 예약 된 몇 개의 모임

### <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
2.  HoloLens를 설정 하 고 테스트 합니다. HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다. 
3.  새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음). 

보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens-2)대 한 다음 링크를 참조 하세요.

센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>1 장-응용 프로그램 등록 포털에서 앱 만들기

먼저 응용 프로그램 **등록 포털**에서 응용 프로그램을 만들고 등록 해야 합니다.

이 장에서는 계정 콘텐츠에 액세스 하기 위해 *Microsoft Graph* 에 대 한 호출을 수행할 수 있도록 하는 서비스 키를 찾을 수도 있습니다.

1.  [Microsoft 응용 프로그램 등록 포털](https://apps.dev.microsoft.com) 로 이동 하 여 microsoft 계정으로 로그인 합니다. 로그인 하면 **응용 프로그램 등록 포털로**리디렉션됩니다.

2.  **내 응용 프로그램** 섹션에서 **앱 추가**단추를 클릭 합니다.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **응용 프로그램 등록 포털** 은 이전에 *Microsoft Graph*작업을 수행 했는지 여부에 따라 달라질 수 있습니다. 아래 스크린샷에서는 이러한 다양 한 버전을 표시 합니다.

3.  응용 프로그램의 이름을 추가 하 고 **만들기**를 클릭 합니다.

    ![](images/AzureLabs-Lab311-03.png)

4.  응용 프로그램을 만든 후에는 응용 프로그램 기본 페이지로 리디렉션됩니다. **응용 프로그램 Id** 를 복사 하 고 안전한 위치에이 값을 기록해 두어야 합니다. 코드에서 바로 사용 합니다.

    ![](images/AzureLabs-Lab311-04.png)

5.  **플랫폼** 섹션에서 **네이티브 응용 프로그램이** 표시 되는지 확인 합니다. **플랫폼 추가** 를 클릭 하 고 **네이티브 응용 프로그램**을 선택 합니다.

    ![](images/AzureLabs-Lab311-05.png)

6.  동일한 페이지에서 아래로 스크롤하고 **Microsoft Graph 권한** 섹션에서 응용 프로그램에 대 한 추가 권한을 추가 해야 합니다. **위임 된 권한**옆의 **추가** 를 클릭 합니다.

    ![](images/AzureLabs-Lab311-06.png)

7.  응용 프로그램에서 사용자의 일정에 액세스 하도록 하려면 일정 확인란을 선택 하 고 **확인**을 클릭 합니다 **.**

    ![](images/AzureLabs-Lab311-07.png)

8.  아래쪽으로 스크롤하고 **저장** 단추를 클릭 합니다.

    ![](images/AzureLabs-Lab311-08.png)

9.  저장이 확인 되 고 **응용 프로그램 등록 포털**에서 로그 아웃할 수 있습니다.

## <a name="chapter-2---set-up-the-unity-project"></a>2 장-Unity 프로젝트 설정

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

1.  *Unity* 를 열고 **새로 만들기**를 클릭 합니다.

    ![](images/AzureLabs-Lab311-09.png)

2.  Unity 프로젝트 이름을 제공 해야 합니다. **Msgraphmr**을 삽입 합니다. 프로젝트 템플릿이 **3d**로 설정 되었는지 확인 합니다. 위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다. 그런 다음 **프로젝트 만들기**를 클릭 합니다.

    ![](images/AzureLabs-Lab311-10.png)

3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다. **기본 설정** **편집** > 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![](images/AzureLabs-Lab311-11.png)

4.  **파일** 빌드 설정으로 이동 하 고 유니버설 Windows 플랫폼를 선택한 후 플랫폼 전환 단추를 클릭 하 여 선택 항목을 적용 합니다. > 

    ![](images/AzureLabs-Lab311-12.png)

5.  **파일** > **빌드 설정**에서 다음을 확인 합니다.

    1. **대상 장치가** **HoloLens** 로 설정 됨
    2. **빌드 형식이** **D3D** 로 설정 됩니다.
    3. **SDK** 가 **최신 설치** 로 설정 됨
    4. **Visual Studio 버전이** **최신 설치** 로 설정 됨
    5. **빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨
    6. 장면을 저장 하 고 빌드에 추가 합니다.

        1. 이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다. 저장 창이 표시 됩니다.

            ![](images/AzureLabs-Lab311-13.png)

        2. 이에 대 한 새 폴더 및 향후 장면을 만듭니다. 새 **폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면**으로 만듭니다.

            ![](images/AzureLabs-Lab311-14.png)

        3. 새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **MR_ComputerVisionScene**를 입력 하 고 **저장**을 클릭 합니다.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Unity 프로젝트와 연결 되어 있어야 하므로 *자산* 폴더 내에 unity 장면을 저장 해야 합니다. 배경 폴더 (및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구조화 하는 일반적인 방법입니다.

    7.  *빌드 설정*의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.

6.  *빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다. 

    ![](images/AzureLabs-Lab311-16.png)

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. **기타 설정** 탭에서 다음을 수행 합니다.

        1.  **스크립팅** **런타임 버전** 은 **실험적** (.net 4.6와 동일) 이어야 하며,이 경우 편집기를 다시 시작 해야 합니다.

        2. **Scripting 백엔드** 는 **.net** 이어야 합니다.

        3. **API 호환성 수준은** **.net 4.6** 이어야 합니다.

            ![](images/AzureLabs-Lab311-17.png)

    2.  **게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음)에서 **가상 현실 지원**을 확인 하 고 **Windows Mixed Reality SDK** 가 추가 되었는지 확인 합니다.

        ![](images/AzureLabs-Lab311-19.png)

8.  *빌드 설정*으로 돌아가서 *Unity C# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.

9.  *빌드 설정* 창을 닫습니다.

10.  장면 및 프로젝트를 저장 합니다 (**파일** > **저장 장면/파일** > **저장 프로젝트**).

## <a name="chapter-3---import-libraries-in-unity"></a>3 장-Unity에서 라이브러리 가져오기

> [!IMPORTANT]
> 이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면이 [311. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)를 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [5 장에서 계속 진행 합니다. ](#chapter-5---create-meetingsui-class).

Unity 내에서 *Microsoft Graph* 를 사용 하려면 **Microsoft. Identity. Client** DLL을 사용 해야 합니다. 그러나 Microsoft Graph SDK를 사용할 수 있지만 Unity 프로젝트를 빌드한 후에 NuGet 패키지를 추가 해야 합니다 (프로젝트 빌드 후 편집). 필요한 Dll을 Unity로 직접 가져오는 것이 더 간단 합니다.

> [!NOTE]
> 현재 Unity에는 가져온 후 플러그 인을 다시 구성 해야 하는 알려진 문제가 있습니다. 이러한 단계 (이 섹션에서는 4-7)는 버그가 해결 된 후 더 이상 필요 하지 않습니다.

사용자 고유의 프로젝트로 *Microsoft Graph* 를 가져오려면 [MSGraph_LabPlugins 파일을 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)합니다. 이 패키지는 테스트 된 라이브러리 버전을 사용 하 여 만들어졌습니다.

Unity 프로젝트에 사용자 지정 Dll을 추가 하는 방법에 대 한 자세한 내용을 보려면 [이 링크를 따르세요](https://docs.unity3d.com/Manual/UsingDLL.html).

패키지를 가져오려면:

1.  **자산** > **가져오기**패키지사용자 > **지정 패키지** 메뉴 옵션을 사용 하 여 unity 패키지를 unity에 추가 합니다. 방금 다운로드 한 패키지를 선택 합니다.

2.  표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** 을 포함 하 여 모든 항목을 선택 했는지 확인 합니다.

    ![](images/AzureLabs-Lab311-20.png)

3.  **가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.

4.  *프로젝트 패널* 에서 **플러그** 인의 **Msgraph** 폴더로 이동 하 고 **Microsoft. Identity. Client**라는 플러그 인을 선택 합니다.

    ![](images/AzureLabs-Lab311-21.png)

5.  *플러그 인* 을 선택 하 고 **모든 플랫폼이** 선택 취소 되어 있는지 확인 한 다음 **WSAPlayer** 도 선택 취소 되어 있는지 확인 하 고 **적용**을 클릭 합니다. 이는 파일이 올바르게 구성 되었는지 확인 하기 위한 것입니다.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > 이러한 플러그 인을 표시 하면 Unity 편집기 에서만 사용 하도록 구성 됩니다. WSA 폴더에는 프로젝트를 Unity에서 유니버설 Windows 응용 프로그램으로 내보낸 후에 사용 되는 다른 Dll 집합이 있습니다.

6.  다음으로, **Msgraph** 폴더 내에서 **WSA** 폴더를 열어야 합니다. 방금 구성한 파일의 복사본이 표시 됩니다. 파일을 선택한 다음 검사기에서 다음을 수행 합니다.

    -   **모든 플랫폼이** **선택 취소**되어 있고 **WSAPlayer** **만** **선택**되어 있는지 확인 합니다.

    -   **SDK** 가 **UWP**로 설정 되어 있고 **Scripting 백 엔드가** **Dot** 로 설정 되었는지 확인 합니다.

    -   **처리 안 함** 이 **선택**되어 있는지 확인 합니다.

        ![](images/AzureLabs-Lab311-23.png)

7.  **적용**을 클릭합니다.

## <a name="chapter-4---camera-setup"></a>4 장-카메라 설정

이 챕터에서는 장면의 기본 카메라를 설정 합니다.

1.  *계층 패널*에서 **기본 카메라**를 선택 합니다.

2.  선택한 후에는 *검사기* 패널에서 **주 카메라** 의 모든 구성 요소를 볼 수 있습니다.

    1.  **카메라 개체** 의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).

    2.  기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).

    3.  **변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.

    4.  **Clear 플래그** 를 **Solid 색** 으로 설정

    5.  카메라 구성 요소의 **배경색** 을 **검은색, 알파 0** **(16 진수 코드: #00000000)** 으로 설정 합니다.

        ![](images/AzureLabs-Lab311-24.png)

3.  *계층 패널* 의 최종 개체 구조는 아래 이미지에 표시 된 것과 같아야 합니다.

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>5 장-MeetingsUI 클래스 만들기

만들어야 하는 첫 번째 스크립트는 **MeetingsUI**입니다 .이 스크립트는 응용 프로그램의 UI (환영 메시지, 지침 및 모임 세부 정보)를 호스트 하 고 채우는 역할을 합니다.

이 클래스를 만들려면:

1.  *프로젝트 패널*에서 **자산** 폴더를 마우스 오른쪽 단추로 클릭 한 다음**폴더** **만들기** > 를 선택 합니다. 폴더 이름을 **스크립트**로 합니다.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  **스크립트** 폴더를 열고 해당 폴더 내에서 **C# 스크립트** **만들기**  >  를 마우스 오른쪽 단추로 클릭 합니다. 스크립트 이름을 **MeetingsUI로 합니다.**

    ![](images/AzureLabs-Lab311-28.png)

3.  새 **MeetingsUI** 스크립트를 두 번 클릭 하 여 *Visual Studio*에서 엽니다.

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

6.  그런 다음 **Start ()** 메서드를 바꾸고 해제 **()** 메서드를 추가 합니다. 이러한 작업은 클래스가 초기화 될 때 호출 됩니다.

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

7.  *모임 UI* 만들기를 담당 하는 메서드를 추가 하 고 요청 시 현재 모임으로 채웁니다.

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

8. **Update ()** 메서드를 **삭제** 하 고 Unity로 반환 하기 전에 Visual Studio에서 **변경 내용을 저장** 합니다. 

## <a name="chapter-6---create-the-graph-class"></a>6 장-그래프 클래스 만들기

만들 다음 스크립트는 **그래프** 스크립트입니다. 이 스크립트는를 호출 하 여 사용자를 인증 하 고 사용자의 일정에서 현재 날짜에 대 한 예약 된 모임을 검색 하는 작업을 담당 합니다.

이 클래스를 만들려면:

1.  **Scripts** 폴더를 두 번 클릭 하 여 엽니다.

2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**. 스크립트 **그래프**의 이름을로 합니다.

3.  스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.

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
    > 이 스크립트에 포함 된 코드의 일부는 [미리 컴파일 지시문](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)을 기반으로 하기 때문에 Visual Studio 솔루션을 빌드할 때 라이브러리 문제를 방지할 수 있습니다.

5.  **Start ()** 및 **Update ()** 메서드를 사용 하지 않으므로 삭제 합니다.

6.  **Graph** 클래스 외부에서 매일 예약 된 모임을 나타내는 JSON 개체를 deserialize 하는 데 필요한 다음 개체를 삽입 합니다.

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

7.  **Graph** 클래스 내에서 다음 변수를 추가 합니다.

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
    > **AppId** 값을  **[1 장](#chapter-1---create-your-app-in-the-application-registration-portal), 4 단계**에서 적어둔 **앱 Id** 로 변경 합니다. 이 값은 응용 프로그램 등록 페이지의 **응용 프로그램 등록 포털** 에 표시 되는 값과 동일 해야 합니다.

8.  **Graph** 클래스 내에서 **SignInAsync ()** 및 **AquireTokenAsync ()** 메서드를 추가 하 여 사용자에 게 로그인 자격 증명을 삽입 하 라는 메시지를 표시 합니다.

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

9.  다음 두 가지 메서드를 추가 합니다.

    1.  **BuildTodayCalendarEndpoint ()** -예약 된 모임이 검색 되는 날짜 및 시간 범위를 지정 하는 URI를 작성 합니다.

    2.  **ListMeetingsAsync ()** - *Microsoft Graph*에서 예약 된 모임을 요청 합니다.

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

10. 이제 **Graph** 스크립트를 완료 했습니다. Unity로 반환 하기 전에 Visual Studio에서 **변경 내용을 저장** 합니다.

## <a name="chapter-7---create-the-gazeinput-script"></a>7 장-GazeInput 스크립트 만들기

이제 **GazeInput**을 만듭니다. 이 클래스는 **기본 카메라**에서 들어오는 **raycast** 를 사용 하 여 앞으로 프로젝션 하는 사용자의 응시를 처리 하 고 추적 합니다.

스크립트를 만들려면 다음을 수행 합니다.

1.  **Scripts** 폴더를 두 번 클릭 하 여 엽니다.

2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**. 스크립트 이름을 **GazeInput**로 합니다.

3.  스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.

4.  Serialize 할 수 있도록 **GazeInput** 클래스 위에 ' **\[\]** system.string ' 태그를 추가 하는 것과 함께 아래와 일치 하도록 네임 스페이스 코드를 변경 합니다.

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  **GazeInput** 클래스 내에서 다음 변수를 추가 합니다.

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

6.  **CreateCursor ()** 메서드를 추가 하 여 장면에 HoloLens 커서를 만들고 **Start ()** 메서드에서 메서드를 호출 합니다.

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

7.  다음 메서드는 응시 Raycast를 사용 하도록 설정 하 고 포커스가 있는 개체를 추적 합니다.

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

8.  Unity로 반환 하기 전에 Visual Studio에서 **변경 내용을 저장** 합니다.

## <a name="chapter-8---create-the-interactions-class"></a>8 장-상호 작용 클래스 만들기

이제 다음을 담당 하는 **상호 작용** 스크립트를 만들어야 합니다.

-   사용자가 장면에서 "button"의 로그인과 상호 작용할 수 있도록 하는 **탭** 상호 작용 및 **카메라 응시**를 처리 합니다.

-   사용자가 상호 작용할 수 있도록 장면에 "button" 개체의 로그를 만듭니다.

스크립트를 만들려면 다음을 수행 합니다.

1.  **Scripts** 폴더를 두 번 클릭 하 여 엽니다.

2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**. 스크립트 **상호 작용**의 이름을로 합니다.

3.  스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.

4.  다음 네임 스페이스를 삽입 합니다.

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  **상호 작용** 클래스의 상속을 *MonoBehaviour* 에서 **GazeInput**로 변경 합니다.

    ~~공용 클래스 상호 작용: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  **상호 작용** 클래스 내에서 다음 변수를 삽입 합니다.

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  **Start** 메서드를 대체 합니다. ' base ' 응시 클래스 메서드를 호출 하는 재정의 메서드입니다. **Start ()** 는 클래스가 초기화 되 고, 입력 인식을 등록 하 고, 장면에 로그인 *단추* 를 만들 때 호출 됩니다.

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

8.  **CreateSignInButton ()** 메서드를 추가 합니다 .이 메서드는 장면의 로그인 *단추* 를 인스턴스화하고 해당 속성을 설정 합니다.

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

9.  *탭핑* 사용자 이벤트에 대해 응답 하는 **GestureRecognizer_Tapped ()** 메서드를 추가 합니다.

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

10. **Update ()** 메서드를 **삭제** 한 다음 Unity로 반환 하기 전에 Visual Studio에서 **변경 내용을 저장** 합니다.

## <a name="chapter-9---set-up-the-script-references"></a>9 장-스크립트 참조 설정

이 장에서는 **기본 카메라**에 **상호 작용** 스크립트를 저장 해야 합니다. 그런 다음이 스크립트는 필요한 위치에 다른 스크립트를 배치 하는 것을 처리 합니다.

-  아래 그림과 같이 *프로젝트 패널*의 **Scripts** 폴더에서 스크립트 **상호 작용** 을 **주 카메라** 개체로 끌어 옵니다.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>10 장-태그 설정

응시를 처리 하는 코드는 **SignInButton** 태그를 사용 하 여 사용자가 *Microsoft Graph*에 로그인 하기 위해 상호 작용 하는 개체를 식별 합니다.

태그를 만들려면 다음을 수행 합니다.

1.  Unity 편집기의 *계층 패널*에서 **주 카메라** 를 클릭 합니다.

2.  *Inspector 패널* 에서 **maincamera** *태그* 를 클릭 하 여 드롭다운 목록을 엽니다. **태그 추가** ...를 클릭 합니다.

    ![](images/AzureLabs-Lab311-30.png)

3.  **+** 단추를 클릭 합니다.

    ![](images/AzureLabs-Lab311-31.png)

4.  태그 이름을 **SignInButton** 로 작성 하 고 저장을 클릭 합니다.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>11 장-UWP에 Unity 프로젝트 빌드

이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.

1.  이동할 *빌드 설정* (**파일*>*설정** 빌드).

    ![](images/AzureLabs-Lab311-33.png)

2.  아직 없는 경우 tick **\# Unity C 프로젝트**입니다.

3.  **빌드**를 클릭합니다. Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 **파일 탐색기** 창을 시작 합니다. 이제 해당 폴더를 만들고 이름을 **App**으로 만듭니다. 그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.

4.  Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.

5.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)

## <a name="chapter-12---deploy-to-hololens"></a>12 장-HoloLens에 배포

HoloLens에 배포 하려면:

1.  HoloLens의 IP 주소 (원격 배포의 경우)가 필요 하 고 HoloLens가 **개발자 모드** 에 있는지 확인 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1.  HoloLens를 입고 하는 동안 **설정을**엽니다.

    2.  **네트워크 & 인터넷** > **wi-fi** > **고급 옵션** 으로 이동 합니다.

    3.  **IPv4** 주소를 적어둡니다.

    4.  그런 다음 **설정**으로 다시 이동한 다음**개발자** 를 위한 **& 보안** > 을 업데이트 합니다.

    5.  **에서 개발자 모드를**설정 합니다.

2.  새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.

3.  **솔루션 구성** 에서 **디버그**를 선택 합니다.

4.  **솔루션 플랫폼**에서 **X86, 원격 컴퓨터**를 선택 합니다. 원격 장치의 **IP 주소** (이 경우에는 HoloLens)를 삽입 하 라는 메시지가 표시 됩니다.

    ![](images/AzureLabs-Lab311-34.png)

5.  **빌드** 메뉴로 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.

6.  이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되어 시작할 준비가 되었습니다!

## <a name="your-microsoft-graph-hololens-application"></a>Microsoft Graph HoloLens 응용 프로그램

축 하 합니다. Microsoft Graph를 활용 하 여 사용자 달력 데이터를 읽고 표시 하는 혼합 현실 앱을 빌드 했습니다.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

Microsoft Graph를 사용 하 여 사용자에 대 한 기타 정보 표시

-   사용자 전자 메일/전화 번호/프로필 사진

### <a name="exercise-1"></a>연습 1

음성 컨트롤을 구현 하 여 Microsoft Graph UI를 탐색 합니다.
