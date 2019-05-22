---
title: MR 및 Azure 306-스트리밍 비디오
description: 혼합된 현실 응용 프로그램에서 Azure Media Services를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, media services에서 스트리밍 비디오를 360, 몰입 형, vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599485"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR 및 Azure 306: 스트리밍 비디오

![최종 제품-시작](images/AzureLabs-Lab6-00.png)
![최종 제품-시작](images/AzureLabs-Lab6-01.png)

이 과정에서는 알아봅니다 어떻게 Azure Media Services 스트리밍 몰입 형 헤드셋에서 360도 비디오 재생을 허용 하도록 Windows Mixed Reality VR 환경에 연결 합니다. 

**Azure Media Services** 은 오늘날 가장 인기 있는 모바일 장치에서 더 많은 대상과 연결에 브로드캐스트 품질 비디오 스트리밍 서비스를 제공 하는 서비스의 컬렉션입니다. 자세한 내용은 참조는 [Azure Media Services 페이지](https://azure.microsoft.com/services/media-services)합니다.

이 과정을 완료 해야 혼합된 현실 몰입 형 헤드셋 응용 프로그램을 다음을 수행할 수 있음:

1. 360도 비디오에서 검색을 **Azure Storage**을 통해 합니다 **Azure 미디어 서비스**합니다.

2. Unity 장면 내 검색된의 360도 비디오를 표시 합니다.

3. 두 개의 다른 비디오를 사용 하 여 두 장면 사이의 이동 합니다.

응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다. 이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다. 혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 306: 스트리밍 비디오</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다. 또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다. 내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구 문서 설치](install-the-tools.md)되지만 하지 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 합니다 .

다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.

- 개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용
- [Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md)
- Azure 설정 및 데이터 검색에 대 한 인터넷 액세스
- Mp4 형식으로 두 360도 비디오 (무료 비디오를 찾을 수 있습니다 [이 다운로드 페이지에서](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
2.  설정 하 고 혼합 현실 몰입 형 헤드셋을 테스트 합니다.

    > [!NOTE]
    > 해야 **되지** 이 과정에 대 한 동작 컨트롤러 필요 합니다. 몰입 형 헤드셋 설정만 지원에 필요한 경우 클릭 하십시오 [Windows Mixed Reality를 설정 하는 방법에 대 한 링크](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>장 1-Azure Portal: Azure Storage 계정 만들기

사용 하는 **Azure Storage 서비스**를 만들고 구성 해야 합니다는 **저장소 계정** Azure portal에서 합니다.

1.  에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

2.  일단 로그인 하면 클릭할 **저장소 계정** 왼쪽된 메뉴에서.

    ![Azure Storage 계정 설정](images/AzureLabs-Lab6-02.png)

3.  에 **Storage 계정** 탭을 클릭 **추가**합니다.

    ![Azure Storage 계정 설정](images/AzureLabs-Lab6-03.png)

4.  에 **저장소 계정 만들기** 탭:

    1.  삽입을 **이름을** 계정의 주의 숫자 및 소문자만이 필드를 허용 합니다.

    2.  에 대 한 **배포 모델** 선택 **Resource manager**합니다.

    3.  에 대 한 **계정 종류**를 선택 **저장소 (범용 v1)** 합니다.

    4.  에 대 한 **성능**, 선택 **Standard* 합니다.**

    5.  에 대 한 **복제** 선택 **로컬 중복 저장소 (LRS)** 합니다.

    6.  둡니다 **보안 전송 필요** 으로 **비활성**합니다.

    7.  선택 된 **구독**합니다.

    8.  선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.

    9.  확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다. 위치는 응용 프로그램은 실행할 지역의 것이 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

5.  이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.

    ![Azure Storage 계정 설정](images/AzureLabs-Lab6-04.png)

6.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

7.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![Azure Storage 계정 설정](images/AzureLabs-Lab6-05.png)

8.  이 시점에서 리소스에 따라, 다음 장으로 이동 필요가 없습니다.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Azure Portal-2 장: 미디어 서비스 만들기

Azure 미디어 서비스를 사용 하려면 (여기서는 계정 보유자는 활성화 해야 관리자) 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.

1.  Azure 포털에서 클릭 **리소스 만들기** 왼쪽 위에서 모서리 및 검색 **미디어 서비스** 키를 눌러 **Enter**합니다. 현재 원하는 리소스 아이콘이 분홍색 새 페이지를 표시 하려면이 옵션을 클릭 합니다.

    ![Azure Portal](images/AzureLabs-Lab6-06.png)

2.  새 페이지에 대 한 설명을 제공 합니다는 **미디어 서비스**합니다. 이 프롬프트의 왼쪽 아래에 있는 클릭 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.

    ![Azure Portal](images/AzureLabs-Lab6-07.png)

3.  클릭 한 후 **만들기** 새 미디어 서비스에 대 한 일부 세부 정보를 제공 해야 하는 패널이 표시 됩니다.

    1.  원하는 삽입 **계정 이름** 이 서비스 인스턴스에 대 한 합니다.

    2.  선택 된 **구독**합니다.

    3. 선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지). 
    
    > 자세한 하려는 경우 Azure 리소스 그룹에 대 한 따르세요 이렇게 [Azure 리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    4.  확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다. 위치는 응용 프로그램은 실행할 지역의 것이 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

    5.  에 대 한 합니다 **저장소 계정** 섹션을 클릭 합니다 **선택 하세요...**  섹션을 클릭 합니다 **저장소 계정** 마지막 챕터에서 작성 합니다.

    6.  이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.

    7.  **만들기**를 클릭합니다.

        ![Azure Portal](images/AzureLabs-Lab6-08.png)

4.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

5.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![Azure Portal](images/AzureLabs-Lab6-09.png)

6.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.

    ![Azure Portal](images/AzureLabs-Lab6-10.png)

7.  클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.

8.  왼쪽 패널 내에서 새 미디어 서비스 페이지에서 클릭 합니다 **자산** 링크 아래쪽 중간에 대 한입니다.

9.  페이지의 왼쪽 위 모서리에 있는 다음 페이지에서 클릭 **업로드**합니다.

    ![Azure Portal](images/AzureLabs-Lab6-11.png)

10. 클릭 합니다 **폴더** 아이콘 파일을 찾아 먼저 360 비디오를 스트리밍 하려는 선택 합니다. 
    
    > 이 수행할 수 있습니다 [샘플 비디오를 다운로드 하려면 링크](https://vimeo.com/214401712)합니다.

    ![Azure Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> 긴 파일 이름 인코더를 사용 하 여 문제를 발생할 수 있습니다: 따라서 비디오에 문제가 없는 되도록 비디오 파일 이름의 길이 줄이는 고려 합니다.

11. 진행률 표시줄 비디오 업로드가 완료 되 면 녹색으로 바뀝니다.

    ![Azure Portal](images/AzureLabs-Lab6-13.png)

12. 위의 텍스트를 클릭 (**yourservicename-자산**)를 반환 하는 **자산** 페이지입니다.

13. 비디오 성공적으로 업로드 되었는지 확인할 수 있습니다. 클릭 합니다.

    ![Azure Portal](images/AzureLabs-Lab6-14.png)

14. 리디렉션됩니다 페이지는 비디오에 대 한 자세한 정보 표시 됩니다. 클릭 하 여 인코딩해야 비디오를 사용 하는 일을 할 수는 **인코딩** 페이지의 왼쪽 위에 있는 단추입니다.

    ![Azure Portal](images/AzureLabs-Lab6-15.png)

15. 새 패널이 있는 인코딩 파일에 대 한 옵션을 설정할 수는 오른쪽에 표시 됩니다. (일부는 이미 설정 기본적으로) 다음 속성을 설정 합니다.

    1.  **미디어 인코더 이름 *Media Encoder Standard***

    2.  **인코딩 사전 설정을 *콘텐츠 적응 다중 비트 전송률 MP4***

    3.  **작업 이름 *설정은 Video1.mp4의 Media Encoder Standard 처리***

    4.  **출력 미디어 자산 이름 *설정은 Video1.mp4-Media Encoder Standard 인코딩***

        ![Azure Portal](images/AzureLabs-Lab6-16.png)

16. **만들기** 단추를 클릭합니다.

17. 막대를 사용 하 여 확인할 수 있습니다 **추가 하는 인코딩 작업**창을 클릭 하 고 패널 표시 된 Encoding 진행으로 표시 됩니다.

    ![Azure Portal](images/AzureLabs-Lab6-17.png)

    ![Azure Portal](images/AzureLabs-Lab6-18.png)

18. 작업이 완료 될 때까지 기다립니다. 완료 되 면 자유롭게 'X' 오른쪽 맨 위에 있는 해당 패널을 사용 하 여 패널을 닫습니다.

    ![Azure Portal](images/AzureLabs-Lab6-19.png)

    ![Azure Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > 이 데 걸리는 시간은 비디오의 파일 크기에 따라 달라 집니다. 이 프로세스에 다소 시간이 걸릴 수 있습니다.

19. 비디오의 인코딩된 버전을 만든 했으므로 액세스할 수 있도록 게시할 수 있습니다. 이렇게 하려면 파란색 링크를 클릭 **자산** 자산 페이지로 다시 이동 합니다.

    ![Azure Portal](images/AzureLabs-Lab6-21.png)

20. 다른와 함께 동영상을 보면 **자산 형식 *다중 비트 전송률 MP4* 합니다.

    ![Azure Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 초기 비디오를 함께 새 자산 임을 알 수 있습니다 *알 수 없는*, 있고 '0' 바이트로 것에 대 한 **크기**, 방금 업데이트에 대 한 창을 새로 고칩니다.

21. 이 새 자산을 클릭 합니다.

    ![Azure Portal](images/AzureLabs-Lab6-23.png)

22. 이전에이 다른 자산을 사용 하는 유사한 패널을 표시 됩니다. 클릭 합니다 **게시** 페이지의 위쪽 가운데에 있는 단추입니다.

    ![Azure Portal](images/AzureLabs-Lab6-24.png)

23. 설정 하 라는 메시지가 표시 됩니다는 **로케이터**, 파일/자산에서 s에 대 한 진입점을를 합니다. 시나리오에 대 한 다음 속성을 설정 합니다.

    1.  **Locator 유형을** > **점진적**합니다.

    2.  합니다 **날짜** 하 고 **시간** 에 설정할을 현재 날짜 로부터 이후의 시간 (이 경우 1 백 년). 에 맞게 변경 하거나 그대로 둡니다.

    > [!NOTE]
    > Locator 및 선택할 수 있습니다 하는 방법에 대 한 자세한 내용은 참조는 [Azure Media Services 설명서](https://docs.microsoft.com/azure/media-services/media-services-concepts)합니다.

24. 해당 패널의 맨 아래에서 클릭 합니다 **추가** 단추입니다.

    ![Azure Portal](images/AzureLabs-Lab6-25.png)

25. 비디오 게시 이제 되 고 해당 끝점을 사용 하 여 스트리밍할 수 있습니다. 페이지 아래쪽에 추가 된 **파일** 섹션. 비디오의 다양 한 인코딩된 버전 될 위치입니다. 하나 가능한 가장 높은 해상도 선택 (아래 이미지에서는 1920 x 960 파일), 후 오른쪽에 패널이 표시 됩니다. 여기서 찾을 수 있습니다는 **다운로드 URL**합니다. 복사해 **끝점** 나중에 코드에서에서 사용 됩니다.

    ![Azure Portal](images/AzureLabs-Lab6-26.png)    

    ![Azure Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > 누를 수도 있습니다는 **재생** 단추를 비디오를 재생 하 고 테스트 합니다.

26. 이제이 실험에서 사용할 두 번째 비디오를 업로드 해야 합니다. 두 번째 비디오에 대 한 동일한 프로세스를 반복 합니다. 위의 단계를 수행 합니다. 두 번째를 복사 **끝점** 수도 있습니다. 다음 사용 하 여 [두 번째 비디오를 다운로드 하려면 링크](https://vimeo.com/214402865)합니다.

27. 두 비디오를 게시 한 후 다음 장에서 이동할 준비가 되었습니다.

## <a name="chapter-3---setting-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 **Unity** 누릅니다 **새로 만들기**합니다. 

    ![Azure Portal](images/AzureLabs-Lab6-28.png)

2.  Unity 프로젝트 이름을 제공 해야 이제 삽입 **MR\_360VideoStreaming.** 합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**합니다. 위치를 적절 한 위치를 설정 합니다 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![Azure Portal](images/AzureLabs-Lab6-29.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio입니다.** 로 이동 ***편집할* *기본 설정*** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![Azure Portal](images/AzureLabs-Lab6-30.png)

4.  이동한 다음 ***파일* *빌드 설정*** 전환 하는 플랫폼이 **유니버설 Windows 플랫폼**, 합니다 클릭하여**플랫폼 전환** 단추입니다.

5.  또한 다음 사항을 확인 합니다

    1. **장치를 대상** 로 설정 된 **모든 장치입니다.**
    
    2.  **빌드 형식** 로 설정 된 **D3D 합니다.**

    3.  **SDK** 로 설정 된 **최신 설치 합니다.**

    4.  **Visual Studio 버전** 로 설정 된 **최신 설치 합니다.**

    5.  **빌드 및 실행** 로 설정 된 **로컬 컴퓨터입니다.**

    6.  설정에 대 한 걱정 하지 마십시오 **장면** 지금은 설정할 때 이러한 나중입니다.

    7.  이제 나머지 설정은 기본값으로 유지 됩니다.

        ![Unity 프로젝트 설정](images/AzureLabs-Lab6-31.png)

6.  에 **빌드 설정** 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 **검사기** 위치한. 

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  에 **기타 설정** 탭:

        1.  **스크립팅** **런타임 버전이** 있어야 **안정적인** (.NET 3.5와 같음).

        2. **백 엔드를 스크립팅** 있어야 **.NET.**

        3. **API 호환성 수준** 있어야 **.NET 4.6입니다.**

            ![Unity 프로젝트 설정](images/AzureLabs-Lab6-32.png)

    2.  패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.

        ![Unity 프로젝트 설정](images/AzureLabs-Lab6-33.png)

    3.  내 합니다 **게시 설정** 탭의 **기능**, 확인:

        - **InternetClient**

            ![Unity 프로젝트 설정](images/AzureLabs-Lab6-34.png)

8.  이러한 변경 했다면 닫습니다 합니다 **빌드 설정** 창입니다.

9.  프로젝트를 저장 합니다 **파일* *프로젝트 **저장 합니다.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>4 장-InsideOutSphere Unity 패키지 가져오기

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 선택한 다음에서 계속 **5 장**합니다. Unity 프로젝트 만들기를 계속 해야 합니다.

Unity 자산 패키지를 다운로드 해야 합니다.이 코스 이라는 [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)합니다.

방법 도움말 가져오기 합니다 **unitypackage**:

1.  사용자 앞에 Unity 대시보드를 클릭 **자산** 화면의 맨 위에 있는 메뉴에서 클릭 **가져오기 패키지 > 사용자 지정 패키지**합니다.

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-35.png)

2.  파일 선택기를 사용 하 여 선택 합니다 **InsideOutSphere.unitypackage** 패키징하고 클릭 **오픈**합니다. 이 자산에 대 한 구성 요소 목록에 나타납니다. 가져오기를 클릭 하 여 확인 **가져올**합니다.

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-36.png)

3.  가져오기 완료 되 고, 세 개의 새 폴더를 확인할 수 있습니다 **자료**, **모델**, 및 **Prefabs**, 추가한 사용자 **자산**폴더입니다. 이 종류의 폴더 구조는 Unity 프로젝트에 대 한 일반적인입니다.

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-37.png)

    1.  엽니다는 **모델** 폴더를 확인할 수는 **InsideOutSphere** 모델을 가져온 합니다.

    2.  내에서 **자료** 폴더를 찾을 수 있습니다 합니다 **InsideOutSpheres** 자료 *lambert1*를 호출 하는 자료와 함께 *ButtonMaterial*, 곧 표시 되는 GazeButton에서 사용 되는 합니다.

    3.  **Prefabs** 폴더에는 **InsideOutSphere** prefab 둘 다 포함 하는 합니다 **InsideOutSphere** *모델* 및 합니다  *GazeButton*합니다.

    4.  **포함 된 코드가 없습니다**,이 과정을 수행 하 여 코드를 작성 합니다.


4.  내에서 **계층**를 선택 합니다 **주 카메라** 개체 및 다음 구성 요소 업데이트:

    1.  **Transform**

        1.  위치 = **X**: 0, **Y**: 0, **Z**: 0.

        2. 회전 = **X**: 0, **Y**: 0, **Z**: 0.

        3. 크기 조정 **X**: 1, **Y**: 1, **Z**: 1.

    2.  **카메라**

        1. **플래그 지우기**: 단색입니다.

        2.  **평면 클리핑**: 거의: 0.1, 지금까지: 6.

            ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-38.png)

5.  로 이동 합니다 **Prefab** 폴더를 연 다음 마우스를 끌어를 **InsideOutSphere** 으로 prefab를 **계층** 패널.

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-39.png)

6.  확장 된 **InsideOutSphere** 내에서 개체를 **계층** 옆에 있는 작은 화살표를 클릭 하 여 합니다. 표시 됩니다는 **자식** 호출 아래에 있는 개체 **GazeButton**합니다. 이 장면 및 비디오를 변경 하려면 사용 됩니다.

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-40.png)

7.  검사기 창에서 클릭 합니다 **InsideOutSphere**의 변환 하는 구성 요소는 다음과 같은 속성이 설정 되어 있는지 확인 합니다.

    |            |    변환-위치   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    변환-회전   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     변환-확장     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-41.png)

8.  클릭 합니다 **GazeButton** 자식 개체를 설정 하 고 해당 **변환** 다음과 같습니다:

    |            |    변환-위치   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    변환-회전   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     변환-확장     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>-5 장 VideoController 클래스 만들기

합니다 **VideoController** 클래스 Azure 미디어 서비스에서 콘텐츠를 스트림 하는 데 사용할 수 있는 두 비디오 끝점을 호스트 합니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **자산 폴더**에 있는 **프로젝트** 패널과 클릭 **만들기 > 폴더**합니다. 폴더의 이름을 **스크립트**합니다.

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-43.png)

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-44.png)

2.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다.

3.  폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C\# 스크립트**합니다. 스크립트 이름을 **VideoController**합니다.

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-45.png)

4.  두 번 클릭 하 여 새 **VideoController** 스크립트를 사용 하 여 열고 **Visual Studio 2017.**

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-46.png)

5.  코드 파일의 맨 위에 있는 네임 스페이스는 다음과 같이 업데이트 합니다.

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  다음 변수를 입력 합니다 **VideoController** 클래스와 함께 합니다 **Awake()** 메서드:

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

7.  이제 다음과 같습니다. Azure 미디어 서비스 비디오에서 끝점을 입력 하는 시간

    1.  첫 번째에는 *video1endpoint* 변수입니다.
    
    2.  에 두 번째는 *video2endpoint* 변수입니다.

    > [!WARNING]
    > 사용 하 여 알려진 문제가 *https* 2017.4.1f1 버전을 사용 하 여 Unity 내에서. 오류가 play에서 제공 하는 비디오를 'http'를 대신 사용해 보세요.

8.  다음으로 **start ()** 메서드를 편집 해야 합니다. 이 메서드는 사용자 Gaze 단추를 확인 하 여 (결과적으로 전환 되는 비디오) 장면 전환 될 때마다 트리거됩니다.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  다음은 **start ()** 메서드를 삽입 합니다 **PlayVideo()** *IEnumerator* 원활 하 게 (따라서 없습니다 끊김 표시 됩니다) 비디오를 시작 하는 데 사용할 메서드를 합니다.

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

10. 이 클래스에 대해 필요한 마지막 메서드는 **ChangeScene()** 장면 사이 교환에 사용 되는 메서드.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > **ChangeScene()** 방법은 유용한 C\# 라는 기능을 *조건부 연산자*합니다. 다음 값에 따라 반환 된 단일 문에서 모든 검사의 결과 및이 조건을 검사할 수 있습니다. 이 따라 [조건부 연산자에 자세히 알아보려면 링크](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)합니다.

11. Visual Studio에서 Unity를 반환 하기 전에 변경 내용을 저장 합니다.

12. 다시 Unity 편집기에서 클릭 하 고 끌어서 합니다 **VideoController** 클래스 [] {.underline}는 **스크립트** 폴더를 **주 카메라** 개체를  **계층** 패널입니다.

13. 클릭 합니다 **주 카메라** 확인 합니다 **검사기 패널**. 새로 추가 된 스크립트 구성 요소에는 빈 값을 사용 하 여 필드를 표시 됩니다. 이것이 코드 내에서 공용 변수를 대상으로 하는 참조 필드입니다.

14. 끌어서를 **InsideOutSphere** 에서 개체를 **계층 패널** 에 **구체** 슬롯을 아래 그림과에서 같이 합니다.

    ![VideoController 클래스를 만듭니다](images/AzureLabs-Lab6-47.png)
    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>-6 장 게이즈 클래스 만들기

이 클래스는 생성을 담당를 **Raycast** 는 beprojected 전달할에서 합니다 **주 카메라**, 사용자를 보고 하는 개체를 검색 하 합니다. 이 경우에 **Raycast** 사용자를 보고 하는 경우를 식별 해야 합니다는 **GazeButton** 장면에 개체 및 동작을 트리거할 합니다.

이 클래스 만들려면:

1.  로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.

2.  마우스 오른쪽 단추로 클릭 합니다 **프로젝트** 패널 **만듭니다* *C\# 스크립트** 합니다. 스크립트 이름을 **Gaze**합니다.

3.  두 번 클릭 하 여 새 ***Gaze*** 스크립트를 사용 하 여 열고 **Visual Studio 2017.**

4.  스크립트의 맨 위에 다음 네임 스페이스를 확인 하 고 다른를 제거 합니다.

    ```csharp
    using UnityEngine;
    ```

5.  그런 다음 내에서 다음 변수를 추가 합니다 **Gaze** 클래스:

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

6.  에 대 한 코드를 **Awake()** 하 고 **start ()** 메서드는 이제 추가 해야 합니다.

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

7.  다음 코드를 추가 합니다 **update ()** 를 Raycast 프로젝트 대상 적중 횟수를 검색 하는 메서드:

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

8.  Visual Studio에서 Unity를 반환 하기 전에 변경 내용을 저장 합니다.

9.  클릭 하 고 끌어서 합니다 **Gaze** Scripts 폴더에서 클래스를 주 카메라 개체에는 **계층** 패널입니다.

## <a name="chapter-7---setup-the-two-unity-scenes"></a>7 장-설치 두 Unity 장면

이 챕터의 목적은 각 호스팅 비디오 스트림에 두 작업을 설정 하는 것입니다. 새 장면 편집 하는 경우 다시 설정할 필요가 없습니다 있도록 이미 만든 장면 복제 되도록 합니다 *GazeButton* 개체는 다른 위치에 있고 다른 모양을 합니다. 이 장면 사이 변경 하는 방법을 보여 줍니다.

1.  으로 이동 하 여이 작업을 수행할 **파일 >으로 장면 저장...** . 창 저장 나타납니다. 클릭 합니다 **새 폴더** 단추입니다.

    ![7 장-설치 두 Unity 장면](images/AzureLabs-Lab6-49.png)

2.  폴더의 이름을 **장면**합니다.

3.  합니다 **장면 저장** 창 열기 계속 됩니다. 새로 만든 엽니다 **장면** 폴더입니다.

4.  에 **파일 이름:** 텍스트 필드에 입력 **VideoScene1**를 누릅니다 **저장**합니다.

5.  Unity에서 다시 열에 **장면** 폴더를 마우스 왼쪽 클릭에 **VideoScene1** 파일입니다. 키보드를 사용 하 여 키를 누릅니다 **Ctrl + D** 해당 장면 복제

    > [!TIP]
    > 합니다 **중복** 명령으로 이동 하 여 수행할 수 있습니다 **편집 > 중복**합니다.

6.  자동으로 unity 장면 이름을 번호를 하나씩 늘립니다 않지만 어쨌든 이전에 삽입 된 코드와 일치 하는지 확인 하려면 확인 합니다.

    >  있어야 **VideoScene1** 하 고 **VideoScene2**합니다.

7.  에 두 장면 이동 **파일 > 빌드 설정**합니다. 사용 하 여는 **빌드 설정** 창이 열려 드래그 하 여 장면 합니다 **빌드 장면** 섹션입니다.

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > 모두에 백그라운드에서 선택할 수 있습니다 하 **장면** 보유를 통해 폴더를 **Ctrl** 단추를 한 다음 각 장면은 마우스 왼쪽 단추로 끌어서 마지막에서 두 합니다.

8.  닫기 합니다 **빌드 설정** 창에서 마우스 두 번 클릭 **VideoScene2**합니다.

9.  두 번째 장면을 열기를 클릭 합니다 **GazeButton** 의 자식 개체를 **InsideOutSphere**, 변환을 다음과 같이 설정:

    |            |    변환-위치   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    변환-회전   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     변환-확장     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. 사용 하 여는 **GazeButton** 를 선택한 상태로 조회에서 자식 합니다 **검사기** 및를 **메시 필터**. 옆에 작은 대상을 클릭 합니다 **메시** 참조 필드:

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-51.png)

11. A **메시 선택** 팝업 창이 표시 됩니다. 두 번 클릭 합니다 **큐브** 목록에서 메시 **자산**합니다.

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-52.png)

12. 합니다 **메시 필터** 업데이트 되며 이제는 **큐브**합니다. 이제 클릭 합니다 **기어** 옆에 아이콘 **구체 Collider** 클릭 **구성 요소 제거**,이 개체에서 collider를 삭제 하 합니다.

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-53.png)

13. 사용 하 여는 **GazeButton** 계속 선택한 상태에서 합니다 **구성 요소 추가** 아래쪽의 단추를 **검사기**합니다. 검색 필드에 입력 **상자**, 및 **상자 Collider** 옵션-추가 하려면 클릭 합니다를 **상자 Collider** 하 여 **GazeButton** 개체 .

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-54.png)

14. 그러나 합니다 **GazeButton** 는 부분적으로 업데이트 하는 이제 다른 모양으로 지금 만들려는 새 **자료**완전히 다른 찾아서 쉽게 보다 다른 개체로 인식할 수 있도록 합니다 첫 번째 장면 개체입니다.

15. 로 이동 하 **자료** 폴더 내에서 **프로젝트 패널**합니다. 복제는 **ButtonMaterial** 자료 (키를 누릅니다 **Ctrl** + **D** 키보드 또는 마우스 왼쪽 단추로 클릭 합니다 **자료**, 다음 **편집** 메뉴 옵션을 선택 파일 **중복**).

    ![7 장-설정 두 Unity 장면](images/AzureLabs-Lab6-55.png)
    ![7 장 두 Unity 장면 설정](images/AzureLabs-Lab6-56.png)

16. 새 **ButtonMaterial** 자료 (여기 라는 **ButtonMaterial 1**), 및 내는 **검사기**를 클릭 합니다 **Albedo** 색 창입니다. 다른 색을 선택할 수 있는 팝업 표시 됩니다 (원하는 중 선택), 한 다음 팝업을 닫습니다. 자료에는 자체 인스턴스를 됩니다 원래 다른 합니다.

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-57.png)

17. 새 끌어 **자료** 에 **GazeButton** 첫 번째 장면 단추에서 쉽게 구분할 수 있도록 이제 해당 확인을 완전히 업데이트 하려면 자식입니다.

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-58.png)

18. 이 시점에서 UWP 프로젝트를 빌드하기 전에 편집기에서 프로젝트를 테스트할 수 있습니다.

    -  키를 눌러 합니다 **재생** 단추를 **편집기** 헤드셋 wear 및 합니다.

        ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-59.png)

19. 두 살펴봅니다 **GazeButton** 첫 번째와 두 번째 비디오를 전환 하는 개체입니다.

## <a name="chapter-8---build-the-uwp-solution"></a>8 장-UWP 솔루션 빌드

편집기에 오류가 없는지 확인 한 후 빌드할 수 있습니다.

빌드:

1.  클릭 하 여 현재 장면 저장 **파일 > 저장**합니다.

2.  호출 확인란 **Unity C\# 프로젝트** (이 중요 한 빌드가 완료 된 후 클래스를 편집할 수)입니다.

3.  로 이동 **파일 > 빌드 설정**, 클릭 **빌드**합니다.

4.  Buildthe 솔루션을 저장할 폴더를 선택 하 라는 메시지가 표시 됩니다.

5.  만들기는 **빌드** 폴더 및 해당 폴더 내에서 원하는 적절 한 이름을 다른 폴더를 만듭니다.

6.  새 폴더를 클릭 한 다음 클릭 **폴더 선택**하므로, 해당 위치에서 빌드를 시작 하려면 해당 폴더를 선택 합니다.

    ![8 장-UWP 솔루션을 빌드합니다](images/AzureLabs-Lab6-60.png)
    ![8 장 UWP 솔루션 빌드](images/AzureLabs-Lab6-61.png)

7.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치는 창입니다.

## <a name="chapter-9---deploy-on-local-machine"></a>로컬 컴퓨터에서 장 9-배포

빌드가 완료 되 면을 **파일 탐색기** 빌드 위치에서 창이 표시 됩니다. 에 빌드된 라는 폴더를 열고 Visual Studio 2017을 사용 하 여 솔루션을 열려면 해당 폴더 내의 솔루션 (.sln) 파일을 두 번 클릭 합니다.

일만 남게 작업을 수행 하는 컴퓨터에 앱 배포 (또는 *로컬 컴퓨터*).

로컬 컴퓨터에 배포 합니다.

1.  **Visual Studio 2017**, 방금 만든 솔루션 파일을 엽니다.

2.  에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.

3.  에 **솔루션 구성** 선택 **디버그**합니다.

    ![9 장-로컬 컴퓨터에 배포](images/AzureLabs-Lab6-62.png)

4.  이제 솔루션 패키지를 복원 해야 합니다. 마우스 오른쪽 단추로 클릭 하 **솔루션**를 클릭 하 고 **솔루션용 NuGet 패키지 복원 하는 중...**

    > [!NOTE] 
    > Unity 기본 제공 된 패키지 수를 대상으로 하 여 로컬 컴퓨터 참조를 사용 하 여 작동 해야 하기 때문에 수행 됩니다.

5.  로 이동 **빌드 메뉴** 을 클릭할 **솔루션 배포** 을 컴퓨터에 응용 프로그램을 사이드 로드 합니다. Visual Studio 먼저 작성 되며 그런 다음 응용 프로그램을 배포 합니다.

6.  이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.

    ![9 장-로컬 컴퓨터에 배포](images/AzureLabs-Lab6-63.png)

혼합 현실 응용 프로그램을 실행 하는 경우 내 야 합니다 **InsideOutSphere** 앱 내에서 사용 하는 모델입니다. 이 구 비디오를 스트리밍할 수를 (큐브 뷰의 이러한 촬영 된)는 들어오는 비디오의 360도 뷰를 제공 합니다. 하지 마세요 앱이 사용할 수 있는 인터넷 속도 따라 몇 로드 시간 (초)을 사용 하는 비디오 경우 놀랄 비디오 요구 사항에 맞춰 페치 및 다운로드에 있으므로 앱으로 스트림 합니다.
준비 되 면 장면을 변경 하 고 gazing 빨간색 구체에 의해 두 번째 비디오를 엽니다. 그런 다음 자유롭게 돌아가 파란색 큐브를 사용 하 여 두 번째 장면에서!

## <a name="your-finished-azure-media-service-application"></a>완성 된 Azure 미디어 서비스 응용 프로그램
 
축 하 360 비디오를 스트리밍하려면 Azure 미디어 서비스를 활용 하는 혼합된 현실 앱을 빌드 했습니다.

![랩 결과](images/AzureLabs-Lab6-00.png)

![랩 결과](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>보너스 연습

**연습 1**

것만 단일 장면을 사용 하 여이 자습서에서 비디오를 변경 하는 것이 가능 합니다. 응용 프로그램을 사용 하 여 실험 하 고 단일 장면으로! 아마도 다른 비디오 목록에 추가 합니다.

**연습 2**

Azure 및 Unity를 사용 하 여 실험 하 고 앱이 인터넷에 연결의 강도 따라 다른 파일 크기를 사용 하 여 비디오를 자동으로 선택 하는 데는 기능을 구현 하려고 합니다.


