---
title: MR 및 Azure 306-스트리밍 비디오
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Media Services을 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, media services, 스트리밍 비디오, 360, 몰입 형, vr
ms.openlocfilehash: 6585aa731ff7ebb89beae67ab0b61ac5ef026e47
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438569"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR 및 Azure 306: 스트리밍 비디오

최종 제품 시작](images/AzureLabs-Lab6-00.png)
![최종 제품 시작을 ![](images/AzureLabs-Lab6-01.png)

이 과정에서는 Azure Media Services을 Windows Mixed Reality VR 환경에 연결 하 여 몰입 형 헤드셋에서 스트리밍 360도 비디오 재생을 허용 하는 방법을 알아봅니다. 

**Azure Media Services** 는 브로드캐스트 품질의 비디오 스트리밍 서비스를 제공 하 여 오늘날 가장 인기 있는 모바일 장치에서 더 많은 사용자에 게 도달 하는 서비스 모음입니다. 자세한 내용은 [Azure Media Services 페이지](https://azure.microsoft.com/services/media-services)를 참조 하세요.

이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 모던 헤드셋 응용 프로그램이 만들어집니다.

1. **Azure 미디어 서비스**를 통해 **Azure Storage**에서 360 학위 비디오를 검색 합니다.

2. Unity 장면 내에서 검색 된 360 정도 비디오를 표시 합니다.

3. 두 개의 다른 비디오를 사용 하 여 두 장면을 이동 합니다.

응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다. 이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다. 이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 306: 스트리밍 비디오</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>필수 구성 요소

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다. [도구 설치 문서](install-the-tools.md)에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- 모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC
- [개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 몰입 (VR) 헤드셋](immersive-headset-hardware-details.md)
- Azure 설정 및 데이터 검색을 위한 인터넷 액세스
- Mp4 형식의 2 360 수준 비디오 ( [이 다운로드 페이지에서](https://www.mettle.com/360vr-master-series-free-360-downloads-page)일부 로열티 없는 비디오를 찾을 수 있음)

## <a name="before-you-start"></a>시작하기 전 확인 사항

1.  이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
2.  혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.

    > [!NOTE]
    > 이 과정에서는 동작 컨트롤러가 필요 **하지** 않습니다. 모던 헤드셋을 설정 하는 데 지원이 필요한 경우 [Windows Mixed Reality를 설정 하는 방법에 대 한 링크](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)를 클릭 하세요.

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>1 장-Azure Portal: Azure Storage 계정 만들기

**Azure Storage 서비스**를 사용 하려면 Azure Portal에서 **저장소 계정을** 만들고 구성 해야 합니다.

1.  [Azure Portal](https://portal.azure.com)에 로그인 합니다.

    > [!NOTE]
    > 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

2.  로그인 되 면 왼쪽 메뉴에서 **저장소 계정** 을 클릭 합니다.

    ![계정 설정 Azure Storage](images/AzureLabs-Lab6-02.png)

3.  **저장소 계정** 탭에서 **추가**를 클릭 합니다.

    ![계정 설정 Azure Storage](images/AzureLabs-Lab6-03.png)

4.  **저장소 계정 만들기** 탭에서 다음을 수행 합니다.

    1.  계정에 대 한 **이름을** 삽입 합니다 .이 필드에는 숫자 및 소문자만 허용 됩니다.

    2.  **배포 모델에서** **Resource manager**를 선택 합니다.

    3.  **계정 종류**에 대해 **저장소 (범용 v1)** 를 선택 합니다.

    4.  **성능**으로 **표준 *을 선택 합니다.**

    5.  **복제** 의 경우 **LRS (로컬 중복 저장소)** 를 선택 합니다.

    6.  **보안 전송을** **사용 하지 않도록 설정**해야 합니다.

    7.  **구독**을 선택 합니다.

    8.  리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.

    9.  새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다. 위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

5.  이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.

    ![계정 설정 Azure Storage](images/AzureLabs-Lab6-04.png)

6.  **만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

7.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![계정 설정 Azure Storage](images/AzureLabs-Lab6-05.png)

8.  이 시점에서 리소스를 따를 필요는 없으며, 다음 챕터로 이동 하기만 하면 됩니다.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>2 장-Azure Portal: Media Service 만들기

Azure 미디어 서비스를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다 (계정 소유자가 관리자 여야 함).

1.  Azure Portal의 왼쪽 위 모서리에서 **리소스 만들기** 를 클릭 하 고 **미디어 서비스를** 검색 한 후 **enter**키를 누릅니다. 현재 원하는 리소스에는 분홍색 아이콘이 있습니다. 새 페이지를 표시 하려면이를 클릭 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-06.png)

2.  새 페이지에는 **미디어 서비스**에 대 한 설명이 제공 됩니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 클릭 하 여이 서비스와의 연결을 만듭니다.

    ![Azure 포털](images/AzureLabs-Lab6-07.png)

3.  [ **만들기** ]를 클릭 하면 새 미디어 서비스에 대 한 세부 정보를 제공 해야 하는 위치에 표시 됩니다.

    1.  이 서비스 인스턴스에 대해 원하는 **계정 이름을** 삽입 합니다.

    2.  **구독**을 선택 합니다.

    3. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다. 
    
    > Azure 리소스 그룹에 대해 자세히 알아보려면 [Azure 리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.

    4.  새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다. 위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

    5.  **저장소 계정** 섹션에서 **선택 ...** 섹션을 클릭 한 다음, 마지막 챕터에서 만든 **저장소 계정을** 클릭 합니다.

    6.  또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.

    7.  **만들기**를 클릭합니다.

        ![Azure 포털](images/AzureLabs-Lab6-08.png)

4.  **만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

5.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![Azure 포털](images/AzureLabs-Lab6-09.png)

6.  알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-10.png)

7.  알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

8.  새 미디어 서비스 페이지의 왼쪽 패널에서 **자산** 링크를 클릭 합니다 (약 중간).

9.  페이지의 왼쪽 위 모서리에 있는 다음 페이지에서 **업로드**를 클릭 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-11.png)

10. **폴더** 아이콘을 클릭 하 여 파일을 검색 하 고 스트리밍할 첫 번째 360 비디오를 선택 합니다. 
    
    > 이 [링크를 따라 샘플 비디오를 다운로드할](https://vimeo.com/214401712)수 있습니다.

    ![Azure 포털](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> 긴 파일 이름으로 인해 인코더와 관련 된 문제가 발생할 수 있습니다. 따라서 비디오에 문제가 발생 하지 않도록 비디오 파일 이름의 길이를 줄이는 것이 좋습니다.

11. 비디오 업로드가 완료 되 면 진행률 표시줄이 녹색으로 바뀝니다.

    ![Azure 포털](images/AzureLabs-Lab6-13.png)

12. 위의 텍스트를 클릭 하 여 **자산** 페이지로 돌아갑니다.

13. 비디오를 성공적으로 업로드 한 것을 알 수 있습니다. 클릭 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-14.png)

14. 리디렉션되는 페이지에 비디오에 대 한 자세한 정보가 표시 됩니다. 비디오를 사용 하려면 페이지 왼쪽 위에 있는 **인코딩** 단추를 클릭 하 여 해당 비디오를 인코딩해야 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-15.png)

15. 파일에 대 한 인코딩 옵션을 설정할 수 있는 새 패널이 오른쪽에 표시 됩니다. 다음 속성을 설정 합니다. 일부 속성은 기본적으로 설정 되어 있습니다.

    1.  **미디어 인코더 이름 *Media Encoder Standard***

    2.  **인코딩 사전 설정 *콘텐츠 적응 다중 비트 전송률 MP4***

    3.  ***Video1의 작업 이름 Media Encoder Standard 처리 중입니다. mp4***

    4.  **출력 미디어 자산 이름 *Video1--Media Encoder Standard 인코드* 됨**

        ![Azure 포털](images/AzureLabs-Lab6-16.png)

16. **만들기** 단추를 클릭합니다.

17. **인코딩 작업이 추가**된 표시줄이 표시 되 면 해당 표시줄을 클릭 하면 인코딩 진행률이 표시 된 패널이 표시 됩니다.

    ![Azure 포털](images/AzureLabs-Lab6-17.png)

    ![Azure 포털](images/AzureLabs-Lab6-18.png)

18. 작업이 완료 될 때까지 기다립니다. 완료 되 면 해당 패널의 오른쪽 위에 있는 ' X '를 사용 하 여 패널을 자유롭게 닫습니다.

    ![Azure 포털](images/AzureLabs-Lab6-19.png)

    ![Azure 포털](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > 이 작업을 수행 하는 데 걸리는 시간은 비디오의 파일 크기에 따라 달라 집니다. 이 프로세스는 상당한 시간이 걸릴 수 있습니다.

19. 이제 인코딩된 버전의 비디오가 생성 되었으므로이를 게시 하 여 액세스할 수 있도록 할 수 있습니다. 이렇게 하려면 파란색 링크 **자산** 을 클릭 하 여 자산 페이지로 돌아갑니다.

    ![Azure 포털](images/AzureLabs-Lab6-21.png)

20. 비디오는 **자산 유형 _다중 비트 전송률 MP4_** 인 다른 비디오와 함께 표시 됩니다.

    ![Azure 포털](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 초기 비디오와 함께 새 자산을 *알*수 없으며, **크기**에 대해 ' 0 ' 바이트를 포함 하는 것을 확인할 수 있습니다 .이는 업데이트를 위해 창을 새로 고칩니다.

21. 새 자산을 클릭 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-23.png)

22. 이전에 사용 했던 것과 비슷한 패널이 표시 됩니다 .이는 다른 자산입니다. 페이지의 위쪽 가운데에 있는 **게시** 단추를 클릭 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-24.png)

23. 항목 지점인 **로케이터**를 자산의 파일/s로 설정 하 라는 메시지가 표시 됩니다. 시나리오에 대해 다음 속성을 설정 합니다.

    1.   > **점진적**으로 **로케이터 유형** 입니다.

    2.  **날짜** 및 **시간은** 현재 날짜부터 미래의 시간 (이 경우 100 년)으로 설정 됩니다. 그대로 두거나에 맞게 변경 합니다.

    > [!NOTE]
    > 로케이터 및 선택할 수 있는 옵션에 대 한 자세한 내용은 [Azure Media Services 설명서](https://docs.microsoft.com/azure/media-services/media-services-concepts)를 참조 하세요.

24. 해당 패널의 아래쪽에서 **추가** 단추를 클릭 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-25.png)

25. 이제 비디오가 게시 되 고 해당 끝점을 사용 하 여 스트리밍할 수 있습니다. 페이지 아래쪽에는 **파일** 섹션이 있습니다. 여기에는 다양 한 인코딩된 버전의 비디오가 있습니다. 가능한 가장 높은 해상도를 선택 하 고 (아래 이미지에서 1920x960 파일) 오른쪽에 패널이 표시 됩니다. 여기에서 **다운로드 URL**을 찾을 수 있습니다. 나중에 코드에서 사용할 때이 **끝점** 을 복사 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-26.png)    

    ![Azure 포털](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > **재생** 단추를 눌러 비디오를 재생 하 고 테스트할 수도 있습니다.

26. 이제이 랩에서 사용할 두 번째 비디오를 업로드 해야 합니다. 위의 단계를 수행 하 여 두 번째 비디오에 대해 동일한 프로세스를 반복 합니다. 두 번째 **끝점** 도 복사 해야 합니다. 다음 링크를 사용 [하 여 두 번째 비디오를 다운로드할 수](https://vimeo.com/214402865)있습니다.

27. 두 비디오를 모두 게시 한 후에는 다음 장으로 이동할 준비가 된 것입니다.

## <a name="chapter-3---setting-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

1.  **Unity** 를 열고 **새로 만들기**를 클릭 합니다. 

    ![Azure 포털](images/AzureLabs-Lab6-28.png)

2.  이제 Unity 프로젝트 이름을 제공 하 고 **MR\_360VideoStreaming**을 삽입 해야 합니다. 프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다. 위치를 적절 한 위치에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다. 그런 다음 **프로젝트 만들기**를 클릭 합니다.

    ![Azure 포털](images/AzureLabs-Lab6-29.png)

3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio** 로 설정 되어 있는지 확인 하는 것이 좋습니다. ***기본 설정* 편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![Azure 포털](images/AzureLabs-Lab6-30.png)

4.  그런 다음 ***파일* *빌드 설정*** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.

5.  또한 다음을 확인 합니다.

    1. **대상 장치** 는 **임의의 장치로** 설정 됩니다.
    
    2.  **빌드 형식이** D3D로 설정 됩니다 **.**

    3.  **SDK** 가 최신 설치로 설정 되어 **있습니다.**

    4.  **Visual Studio 버전이** 최신 설치로 설정 되어 **있습니다.**

    5.  **빌드 및 실행** 이 **로컬 컴퓨터** 로 설정 됩니다.

    6.  나중에 설정 하므로 지금 바로 **장면을** 설정 하는 것에 대해 걱정할 필요가 없습니다.

    7.  지금은 나머지 설정이 기본값으로 유지 되어야 합니다.

        ![Unity 프로젝트 설정](images/AzureLabs-Lab6-31.png)

6.  **빌드 설정** 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다. 

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  **기타 설정** 탭에서 다음을 수행 합니다.

        1.  **Scripting** **Runtime 버전** 은 **안정적** 이어야 합니다 (.net 3.5 해당).

        2. **Scripting 백엔드** 는 .net 이어야 합니다 **.**

        3. **API 호환성 수준은** **.net 4.6** 이어야 합니다.

            ![Unity 프로젝트 설정](images/AzureLabs-Lab6-32.png)

    2.  패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.

        ![Unity 프로젝트 설정](images/AzureLabs-Lab6-33.png)

    3.  **게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.

        - **InternetClient**

            ![Unity 프로젝트 설정](images/AzureLabs-Lab6-34.png)

8.  이러한 변경을 수행한 후에는 **빌드 설정** 창을 닫습니다.

9.  프로젝트를 저장 합니다. **파일* * 프로젝트 저장 * *.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>4 장-Into Out구에 Unity 패키지 가져오기

> [!IMPORTANT]
> 이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)를 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 **5 장**에서 계속 합니다. Unity 프로젝트를 만들어야 합니다.

이 과정에서는 [**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)이라는 Unity 자산 패키지를 다운로드 해야 합니다.

방법: **unitypackage**를 가져오는 방법:

1.  앞의 Unity 대시보드를 사용 하 여 화면 위쪽의 메뉴에서 **자산** 을 클릭 하 고 **패키지 가져오기 > 사용자 지정 패키지**를 클릭 합니다.

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-35.png)

2.  파일 선택기를 사용 하 여 **unitypackage** 패키지를 선택 하 고 **열기**를 클릭 합니다. 이 자산의 구성 요소 목록이 표시 됩니다. **가져오기를 클릭 하**여 가져오기를 확인 합니다.

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-36.png)

3.  가져오기가 완료 되 면 세 개의 새 폴더 ( **재질**, **모델**및 **Prefabs**)가 **자산** 폴더에 추가 된 것을 알 수 있습니다. 이러한 종류의 폴더 구조는 Unity 프로젝트에 일반적입니다.

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-37.png)

    1.  **모델** 폴더를 열면 **Into out구에** 모델을 가져왔는지 확인 합니다.

    2.  **재질** 폴더 내에서 GazeButton에서 사용 되는 *buttonmaterial*이라는 재질과 함께 **inlambert1 out구** 자료를 찾을 수 있습니다 .이는 곧 표시 될 것입니다.

    3.  **Prefabs** 폴더에는 **insideoutsphere** *모델* 및 *GazeButton*를 모두 포함 하는 **inprefab out구가** 포함 되어 있습니다.

    4.  **코드는 포함 되지 않으며**,이 과정을 수행 하 여 코드를 작성 합니다.


4.  **계층**내에서 **주 카메라** 개체를 선택 하 고 다음 구성 요소를 업데이트 합니다.

    1.  **변환**

        1.  Position = **X**: 0, **Y**: 0, **Z**: 0.

        2. 회전 = **X**: 0, **Y**: 0, **Z**: 0.

        3. 크기 조정 **X**: 1, **Y**: 1, **Z**: 1.

    2.  **카메라**

        1. **플래그 지우기**: 단색입니다.

        2.  **클리핑 평면**: 근거리: 0.1, 먼: 6.

            ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-38.png)

5.  **Prefab** 폴더로 이동한 다음 **Insideoutsphere** Prefab을 **계층** 패널로 끌어옵니다.

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-39.png)

6.  옆의 작은 화살표를 클릭 하 여 **계층** 내에서 **Insideoutsphere** 개체를 확장 합니다. **GazeButton**라는 자식 개체 아래에 **자식** 개체가 표시 됩니다. 이는 장면을 변경 하는 데 사용 되며 비디오를 변경 하는 데 사용 됩니다.

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-40.png)

7.  검사기 창에서 **Insideoutsphere**변형 구성 요소를 클릭 하 고 다음 속성을 설정 했는지 확인 합니다.

    |            |    변환 위치   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    변환-회전   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     변환-배율     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-41.png)

8.  **GazeButton** 자식 개체를 클릭 하 고 다음과 같이 **변환을** 설정 합니다.

    |            |    변환 위치   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    변환-회전   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     변환-배율     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>5 장-VideoController 클래스 만들기

**Videocontroller** 클래스는 Azure 미디어 서비스에서 콘텐츠를 스트리밍하는 데 사용 되는 두 개의 비디오 끝점을 호스팅합니다.

이 클래스를 만들려면:

1.  **프로젝트** 패널에 있는 **자산 폴더**를 마우스 오른쪽 단추로 클릭 하 고 **> 폴더 만들기**를 클릭 합니다. 폴더 이름을 **스크립트**로 합니다.

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-43.png)

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-44.png)

2.  **스크립트** 폴더를 두 번 클릭 하 여 엽니다.

3.  폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **> C\# 스크립트 만들기**를 클릭 합니다. 스크립트의 이름을 **Videocontroller**로 합니다.

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-45.png)

4.  새 **Videocontroller** 스크립트를 두 번 클릭 하 여 **Visual Studio 2017** 에서 엽니다.

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-46.png)

5.  다음과 같이 코드 파일의 맨 위에 있는 네임 스페이스를 업데이트 합니다.

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  **Videocontroller** 클래스에서 다음 변수를 해제 **()** 메서드와 함께 입력 합니다.

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  이제 Azure 미디어 서비스 비디오에서 끝점을 입력 하는 시간입니다.

    1.  *Video1endpoint* 변수에 대 한 첫 번째입니다.
    
    2.  *Video2endpoint* 변수에 대 한 두 번째입니다.

    > [!WARNING]
    > Unity에서 *https* 를 사용 하는 경우 버전 2017.4.1 f1를 사용 하는 것과 관련 된 알려진 문제가 있습니다. 비디오를 재생 하는 동안 오류가 발생 하는 경우 ' http '를 대신 사용해 보세요.

8.  다음으로 **Start ()** 메서드를 편집 해야 합니다. 이 메서드는 사용자가 장면을 전환할 때마다 (따라서 비디오를 전환) 응시 단추를 살펴보면 트리거됩니다.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  **Start ()** 메서드를 따라 비디오를 원활 하 게 시작 하는 데 사용 되는 **playvideo ()** *IEnumerator* 메서드를 삽입 합니다 (끊길 표시 되지 않음).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. 이 클래스에 필요한 마지막 메서드는 **ChangeScene ()** 메서드로, 장면을 전환 하는 데 사용 됩니다.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > **ChangeScene ()** 메서드는 *조건 연산자*라고 하는 유용한 C\# 기능을 사용 합니다. 이렇게 하면 조건을 확인 한 다음 검사 결과에 따라 반환 되는 값을 모두 단일 문 내에서 수행할 수 있습니다. [조건 연산자에 대 한 자세한 내용을 보려면이 링크를](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)따르세요.

11. Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 합니다.

12. Unity 편집기로 돌아가서, **Videocontroller** 클래스 [from] {. 밑줄} **스크립트** 폴더를 **계층** 패널의 **기본 카메라** 개체로 끌어 놓습니다.

13. **주 카메라** 를 클릭 하 고 **검사기 패널**을 확인 합니다. 새로 추가한 스크립트 구성 요소에 빈 값이 있는 필드가 있음을 알 수 있습니다. 코드 내에서 공용 변수를 대상으로 하는 참조 필드입니다.

14. 아래 이미지에 표시 된 것 처럼 **계층 패널** 에서 **구** 슬롯으로 **in의 out구** 개체를 끌어 옵니다.

    videocontroller 클래스](images/AzureLabs-Lab6-47.png)
    만드는 ![![비디오 컨트롤러 클래스를 만듭니다](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>6 장-응시 클래스 만들기

이 클래스는 사용자가 보고 있는 개체를 검색 하기 위해 **기본 카메라**에서 전달 되는 **raycast** 를 만드는 역할을 합니다. 이 경우에는 사용자가 장면의 **GazeButton** 개체를 보고 동작을 트리거할 수 있는지 여부를 확인 **해야 합니다.**

이 클래스를 만들려면:

1.  이전에 만든 **스크립트** 폴더로 이동 합니다.

2.  **프로젝트** 패널을 마우스 오른쪽 단추로 클릭 하 고 **만들기* * C\# 스크립트 * *를 클릭 합니다. 스크립트 이름을 **응시**로 합니다.

3.  새 ***응시*** 스크립트를 두 번 클릭 하 여 **Visual Studio 2017** 에서 엽니다.

4.  다음 네임 스페이스가 스크립트의 맨 위에 있는지 확인 하 고 다른 네임 스페이스를 제거 합니다.

    ```csharp
    using UnityEngine;
    ```

5.  그런 다음, 다음 변수를 **응시** 클래스 내에 추가 합니다.

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  이제 해제 **()** 및 **Start ()** 메서드에 대 한 코드를 추가 해야 합니다.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  **Update ()** 메서드에 다음 코드를 추가 하 여 Raycast를 프로젝션 하 고 대상 적중을 검색 합니다.

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 합니다.

9.  Scripts 폴더의 Scripts **클래스를** 클릭 하 고 **계층** 패널의 기본 카메라 개체로 끕니다.

## <a name="chapter-7---setup-the-two-unity-scenes"></a>7 장-두 Unity 장면 설정

이 챕터의 목적은 각각 비디오를 스트리밍하는 두 개의 장면을 설정 하는 것입니다. 이미 만든 장면을 복제 하므로 다시 설정할 필요가 없습니다. 그러나 *GazeButton* 개체가 다른 위치에 있고 다른 모양을 갖도록 하기 위해 새 장면을 편집 하는 경우에는 새 장면을 편집 해도 됩니다. 이는 장면을 변경 하는 방법을 보여 주기 위한 것입니다.

1.  파일로 이동 하 여이 작업을 수행 하려면 **다른 이름으로 장면 저장**...을 > 합니다. 저장 창이 표시 됩니다. **새 폴더** 단추를 클릭 합니다.

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-49.png)

2.  폴더 이름을 **장면**으로 합니다.

3.  **장면 저장** 창이 계속 열려 있습니다. 새로 만든 **장면** 폴더를 엽니다.

4.  **파일 이름:** 텍스트 필드에 **VideoScene1**를 입력 하 고 **저장**을 누릅니다.

5.  Unity로 돌아가서, **장면** 폴더를 열고 **VideoScene1** 파일을 마우스 왼쪽 단추를 클릭 합니다. 키보드를 사용 하 고 **ctrl + D** 를 누르면 해당 장면이 복제 됩니다.

    > [!TIP]
    > **편집 > 복제**로 이동 하 여 **중복** 명령을 수행할 수도 있습니다.

6.  Unity는 장면 이름 번호를 자동으로 증가 하지만이를 확인 하 여 이전에 삽입 된 코드와 일치 하는지 확인 합니다.

    >  **VideoScene1** 및 **VideoScene2**가 있어야 합니다.

7.  두 개의 장면을 사용 하 여 **파일 > 빌드 설정**으로 이동 합니다. **빌드 설정** 창을 열고, **빌드 섹션에서** 장면을 장면을 끌어 옵니다.

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > **Ctrl** 단추를 누른 채 각 장면을 마우스 왼쪽 단추로 클릭 하 고 마지막으로 둘 다로 끌어 **장면** 폴더에서 두 장면을 모두 선택할 수 있습니다.

8.  **빌드 설정** 창을 닫고 **VideoScene2**을 두 번 클릭 합니다.

9.  두 번째 장면을 연 상태에서 **InGazeButton** 자식 개체를 클릭 하 고다음과 같이 변환을 설정 합니다.

    |            |    변환 위치   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    변환-회전   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     변환-배율     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. **GazeButton** child가 선택 된 상태에서 **검사기** 와 **메시 필터**를 확인 합니다. **메시** 참조 필드 옆에 있는 대상을 클릭 합니다.

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-51.png)

11. **메시 선택** 팝업 창이 표시 됩니다. **자산**목록에서 **큐브** 메시를 두 번 클릭 합니다.

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-52.png)

12. **메시 필터** 는 업데이트 되 고 이제 **큐브**를 업데이트 합니다. 이제 **구 collider** 옆의 **기어** 아이콘을 클릭 하 고 **구성 요소 제거**를 클릭 하 여이 개체에서 Collider를 삭제 합니다.

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-53.png)

13. **GazeButton** 가 선택 된 상태에서 **검사기**아래쪽의 **구성 요소 추가** 단추를 클릭 합니다. 검색 필드에 **box**를 입력 하 고 **상자 collider** 가 옵션으로 선택 되어 **GazeButton** 개체에 **상자 collider** 를 추가 합니다.

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-54.png)

14. 이제 **GazeButton** 가 부분적으로 업데이트 되 고, 다른 것 처럼 보이지만, 이제는 새 **자료**를 만들어이를 완전히 다르게 표시 하 고 첫 번째 장면의 개체와 다른 개체로 인식 하기가 더 쉽습니다.

15. **프로젝트 패널**내에서 **재질** 폴더로 이동 합니다. **Buttonmaterial** 재질을 복제 합니다. 키보드에서 **Ctrl** + **D** 를 누르거나 **재질**을 마우스 왼쪽 단추로 클릭 한 다음 파일 **편집** 메뉴 옵션에서 **중복**을 선택 합니다.

    7 장 ![--두 Unity 장면을 설정](images/AzureLabs-Lab6-55.png)
    ![7 장--두 Unity 장면을 설정](images/AzureLabs-Lab6-56.png)

16. 새 **buttonmaterial** 재질 (여기서는 **buttonmaterial 1**이라고 함)을 선택 하 고 **검사기**내에서 **albedo** 색 창을 클릭 합니다. 다른 색을 선택할 수 있는 팝업이 표시 됩니다. 여기서 원하는 것을 선택 하 고 팝업을 닫습니다. 자료는 자체 인스턴스가 되며 원본과 다릅니다.

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-57.png)

17. 새 **자료** 를 **GazeButton** 자식으로 끌어 옵니다. 그러면 첫 번째 장면 단추와 쉽게 구분할 수 있도록 모양이 완전히 업데이트 됩니다.

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-58.png)

18. 이 시점에서 UWP 프로젝트를 빌드하기 전에 편집기에서 프로젝트를 테스트할 수 있습니다.

    -  **편집기** 에서 **재생** 단추를 누르고 헤드셋을 착용 합니다.

        ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-59.png)

19. 두 개의 **GazeButton** 개체를 확인 하 여 첫 번째와 두 번째 비디오 간을 전환 합니다.

## <a name="chapter-8---build-the-uwp-solution"></a>8 장-UWP 솔루션 빌드

편집기에 오류가 없으면 빌드할 준비가 된 것입니다.

빌드:

1.  **파일 > 저장**을 클릭 하 여 현재 장면을 저장 합니다.

2.  **Unity C\# 프로젝트** 라는 상자를 선택 합니다 .이는 빌드를 완료 한 후 클래스를 편집할 수 있도록 하기 때문에 중요 합니다.

3.  **파일 > 빌드 설정**으로 이동 하 고 **빌드**를 클릭 합니다.

4.  솔루션을 buildthe 폴더를 선택 하 라는 메시지가 표시 됩니다.

5.  **빌드** 폴더를 만들고 해당 폴더 내에서 원하는 적절 한 이름을 사용 하 여 다른 폴더를 만듭니다.

6.  새 폴더를 클릭 한 다음 **폴더 선택**을 클릭 하 여 해당 폴더를 선택 하 고 해당 위치에서 빌드를 시작 합니다.

    ![장 8 장--![챕터를](images/AzureLabs-Lab6-60.png)
    UWP 솔루션 빌드](images/AzureLabs-Lab6-61.png)

7.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다.

## <a name="chapter-9---deploy-on-local-machine"></a>9 장-로컬 컴퓨터에 배포

빌드가 완료 되 면 빌드 위치에 **파일 탐색기** 창이 표시 됩니다. 이름을 지정 하 고 빌드한 폴더를 연 다음 해당 폴더 내에서 솔루션 (.sln) 파일을 두 번 클릭 하 여 Visual Studio 2017에서 솔루션을 엽니다.

남은 작업은 사용자의 컴퓨터 (또는 *로컬 컴퓨터*)에 앱을 배포 하는 것입니다.

로컬 컴퓨터에 배포 하려면:

1.  **Visual Studio 2017**에서 방금 만든 솔루션 파일을 엽니다.

2.  **솔루션 플랫폼**에서 **X86, 로컬 컴퓨터**를 선택 합니다.

3.  **솔루션 구성** 에서 **디버그**를 선택 합니다.

    ![9 장--로컬 컴퓨터에 배포](images/AzureLabs-Lab6-62.png)

4.  이제 솔루션에 대 한 패키지를 복원 해야 합니다. **솔루션**을 마우스 오른쪽 단추로 클릭 하 고 **솔루션에 대 한 NuGet 패키지 복원** ...을 클릭 합니다.

    > [!NOTE] 
    > 이 작업은 Unity가 빌드된 패키지가 로컬 컴퓨터 참조를 대상으로 해야 하기 때문에 수행 됩니다.

5.  **빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드. Visual Studio는 먼저 응용 프로그램을 빌드한 다음 배포 합니다.

6.  이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.

    ![9 장--로컬 컴퓨터에 배포](images/AzureLabs-Lab6-63.png)

Mixed Reality 응용 프로그램을 실행 하는 경우 앱 내에서 사용한 **Into Out구에** 모델 내에 있습니다. 이 구는 이러한 종류의 관점에서 filmed 된 들어오는 비디오 (360)를 제공 하 여 비디오가 스트리밍되는 위치입니다. 비디오를 로드 하는 데 몇 초 정도 걸릴 수 있으며, 비디오를 가져와 다운로드 한 다음 앱으로 스트리밍하려면 앱에 사용 가능한 인터넷 속도가 적용 됩니다.
준비가 되 면 장면을 변경 하 고 red 구를 gazing 하 여 두 번째 비디오를 엽니다. 그런 다음 두 번째 장면에서 파란색 큐브를 사용 하 여 뒤로 이동 합니다.

## <a name="your-finished-azure-media-service-application"></a>완성 된 Azure Media Service 응용 프로그램
 
축 하 합니다. Azure 미디어 서비스를 활용 하 여 360 비디오를 스트리밍하는 혼합 현실 앱을 빌드 했습니다.

![랩 결과](images/AzureLabs-Lab6-00.png)

![랩 결과](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>보너스 연습

**연습 1**

이 자습서 내에서 단일 장면을 사용 하 여 비디오를 변경 하는 것만 가능 합니다. 응용 프로그램을 실험 하 고 단일 장면으로 만듭니다. 혼합에 다른 비디오를 추가할 수도 있습니다.

**연습 2**

Azure 및 Unity를 실험 하 고 인터넷 연결의 강도에 따라 앱에서 다른 파일 크기의 비디오를 자동으로 선택 하는 기능을 구현 해 보세요.


