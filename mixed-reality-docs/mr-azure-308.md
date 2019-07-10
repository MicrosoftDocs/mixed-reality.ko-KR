---
title: MR, Azure 308부터-장치 간 알림
description: 혼합된 현실 응용 프로그램에서 Azure Notification Hubs, Azure Functions 및 Azure Storage 및 테이블을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 알림, 함수, 테이블, notification hubs를 몰입 형, hololens, vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694609"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR 및 Azure 308: 장치 간 알림

![최종 제품-시작](images/AzureLabs-Lab8-00.png)

이 과정에서는 Azure Notification Hubs, Azure Tables 및 Azure Functions를 사용 하 여 혼합된 현실 응용 프로그램에 Notification Hubs 기능을 추가 하는 방법을 배웁니다.

**Azure Notification Hubs** 는 개발자가 모든 플랫폼에서 클라우드 내에서 모든 전원이 대상 및 개인 설정 된 푸시 알림을 보낼 수 있는 Microsoft 서비스입니다. 효과적으로 최종 사용자와 통신 하는 개발자를 허용 또는 시나리오에 따라 다양 한 응용 프로그램 간의 통신도 수 있습니다. 자세한 내용은 참조는 **Azure Notification Hubs** [페이지](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)합니다.

**Azure Functions** 작은 코드를 실행 하기 위해 개발자를 허용 하는 Microsoft 서비스에 '', Azure에서 functions 됩니다. 다양 한 이점을 가질 수 있는 로컬 응용 프로그램 보다는 클라우드의 작업을 위임 하는 방법을 제공 합니다. **Azure Functions** C를 비롯 한 여러 개발 언어를 지 원하는\#, F\#, Node.js, Java 및 PHP 합니다. 자세한 내용은 참조는 **Azure Functions** [페이지](https://docs.microsoft.com/azure/azure-functions/functions-overview)합니다.

**Azure 테이블** 는 클라우드에 구조화 된 비 SQL 데이터를 저장 하는 개발자를 허용 하는 Microsoft 클라우드 서비스를 쉽게 액세스할 수 있도록 어디서 나 합니다. 서비스 소재 필요에 따라 테이블의 발전에 대 한 허용, 스키마 없이 디자인 되어 있으므로 매우 유연 합니다. 자세한 내용은 참조는 **Azure Tables** [페이지](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

이 과정을 완료 해야 혼합된 현실 헤드셋 몰입 형 응용 프로그램 및 데스크톱 PC는 응용 프로그램을, 다음을 수행할 수 있게 됩니다.

1. 데스크톱 PC 앱에서는 사용자 (X, Y)으로 2D 공간에서 개체를 이동 하려면 마우스를 사용 합니다.

2. PC 앱 내에서 개체의 이동 문자열의 형태로 될 JSON을 사용 하 여, 형식, 개체 ID를 포함 하는 클라우드로 전송 되 고 정보 (X 및 Y 좌표)을 변환 합니다. 

3. 혼합된 현실 앱, 데스크톱 앱에는 동일한 장면에 Notification Hubs 서비스 (업데이트 된 데스크톱 PC 앱에서)에서 개체 이동에 대 한 알림을 받습니다. 

4. 개체 ID, 형식 및 변환 정보를 포함 될, 알림을 받으면 혼합된 현실 앱 자체 장면에 받은 정보를 적용 됩니다.

응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다. 이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다. 혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다. 이 과정은 다른 혼합 현실 Labs를 직접 포함 하지 않는 자체 포함 된 자습서입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 308: 장치 간 알림</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Azure 설정에 대 한 알림 허브에 액세스 하려면 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 주의 사항

- 이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
- Microsoft 개발자 포털 및 응용 프로그램 등록 포털의 소유자 여야 합니다, 그렇지 않으면 있습니다 응용 프로그램에 액세스할 수 있는 권한이 [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials)합니다.

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>장 1-Microsoft 개발자 포털에서 응용 프로그램 만들기

사용 하 여 **Azure Notification Hubs** 서비스 해야 Microsoft 개발자 포털에서 응용 프로그램을 만들려면 응용 프로그램을 보내고 알림을 받을 수 있도록 등록 해야 하는 대로 합니다.

1.  에 로그인 합니다 [Microsoft 개발자 포털](https://developer.microsoft.com/dashboard)합니다.

    > Microsoft 계정에 로그인 해야 합니다.

2.  대시보드에서 클릭 **새 앱 만들기**합니다.

    ![앱 만들기](images/AzureLabs-Lab8-01.png)

3.  새 앱 이름 예약 해야 하는 여기서 팝업 표시 됩니다. 텍스트 상자에 적절 한 이름을; 삽입 선택한 이름 사용 가능한 경우 입력란의 오른쪽에는 눈금 표시 됩니다. 삽입 하는 사용 가능한 이름을 만든 후 클릭 합니다 **제품 이름 예약** 팝업의 왼쪽 아래에는 단추입니다.

    ![역방향 이름](images/AzureLabs-Lab8-02.png)

4.  이제 만든 앱을 다음 장에서 이동할 준비가 됩니다.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>새 앱 자격 증명을 검색 하는-2 장

여기서 새 앱 나열 됩니다 하 고 설치 프로그램에 사용 되는 자격 증명을 검색할 응용 프로그램 등록 포털에 로그인 합니다 **Notification Hubs 서비스** 내 합니다 **Azure Portal**.

1.  로 이동 합니다 [응용 프로그램 등록 포털](http://apps.dev.microsoft.com)합니다.

    ![응용 프로그램 등록 포털](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > 로그인 하려면 Microsoft 계정을 사용 해야 합니다.  
    > 이 **해야 합니다** 이전에 사용한 Microsoft 계정 [장](#chapter-1---create-an-application-on-the-microsoft-developer-portal), Windows 스토어 개발자 포털을 사용 합니다.

2.  응용 프로그램을 보면 합니다 **내 응용 프로그램** 섹션입니다. 을 찾은 후 클릭 하 고 앱이 있는 새 페이지로 이동 됩니다 이름 더하기 **등록**합니다.

    ![새로 등록 된 앱](images/AzureLabs-Lab8-04.png)

3.  검색할 등록 페이지를 아래로 스크롤하여 사용자 **응용 프로그램 비밀** 섹션 및 **패키지 SID** 앱에 대 한 합니다. 설정 사용에 대 한 모두 복사 합니다 **Azure Notification Hubs 서비스** 다음 장에서 합니다.

    ![응용 프로그램 비밀](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Azure Portal 설치-3 장: Notification Hubs 서비스 만들기

앱 자격 증명을 사용 하 여 검색 해야 Azure Notification Hubs 서비스를 만들려는 Azure Portal로 이동 합니다.

1.  에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.

    > [!NOTE] 
    > Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

2.  일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 **알림 허브**를 클릭 하 고 ***Enter***합니다.

    ![알림 허브에 대 한 검색](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 단어 ***새로 만들기*** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.

3.  새 페이지에 대 한 설명을 제공 합니다는 *Notification Hubs* 서비스입니다. 선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.

    ![notification hubs 인스턴스 만들기](images/AzureLabs-Lab8-07.png)

4.  클릭 한 후 ***만들기***:

    1.  이 서비스 인스턴스에 대해 원하는 이름을 입력 합니다.

    2.  제공 된 **네임 스페이스** 이 앱과 연결할 수는 있습니다.

    3.  선택 된 **위치 합니다.**

    4.  선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다. 

    5.  적절 한 선택 **구독**합니다.

    6.  이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.

    7. **만들기**를 선택합니다.

        ![서비스 세부 정보 입력](images/AzureLabs-Lab8-08.png)

5.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

6.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![알림(notification)](images/AzureLabs-Lab8-09.png)

7.  클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 이동에서 새 **알림 허브** 서비스 인스턴스.

    ![리소스로 이동](images/AzureLabs-Lab8-10.png)
    
8.  페이지 아래쪽의 중간 개요 페이지에서 클릭 **Windows (WNS).** 오른쪽 패널을 필요로 하는 텍스트 필드를 두 표시로 변경 됩니다 하 **패키지 SID** 하 고 **보안 키**, 이전에 설정한 앱에서.

    ![새로 만든 허브 서비스](images/AzureLabs-Lab8-11.png)

9. 올바른 필드에 세부 정보를 복사한 후 클릭 **저장할**, 알림 허브 업데이트 되었을 때 알림을 받습니다.

    ![보안 세부 정보 복사](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Azure Portal 설치-4 장: Table Service 만들기

Notification Hubs 서비스 인스턴스를 만든 후 Azure Portal에서 저장소 리소스를 만들어 Azure 테이블 서비스를 만들로 다시 이동 합니다.

1.  아직 로그인 하지 않은, 경우에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.

2.  로그인 되 면 클릭 **새로 만들기** 왼쪽 위에서 모서리 및 검색 **저장소 계정**를 클릭 하 고 **Enter**합니다.

    > [!NOTE] 
    > 단어 ***새로 만들기*** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.

3.  선택 **저장소 계정-blob, 파일, 테이블, 큐** 목록에서.

    ![저장소 계정에 대 한 검색](images/AzureLabs-Lab8-13.png)

4.  새 페이지에 대 한 설명을 제공 합니다는 **저장소 계정** 서비스입니다. 선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 단추,이 서비스의 인스턴스를 만듭니다.

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab8-14.png)

5.  클릭 한 후 **만들기**를 패널에 표시 됩니다.

    1. 원하는 삽입 **이름을** (모두 소문자 여야 함)이 서비스 인스턴스에 대 한 합니다.

    2. 에 대 한 **배포 모델**, 클릭 **Resource manager**합니다.

    3.  에 대 한 **계정 종류**, 선택 드롭다운 메뉴를 사용 하 여 **저장소 (범용 v1)** 합니다.

    4. 적절 한 선택 **위치**합니다.
    
    5.  에 대 한 합니다 **복제** 드롭다운 메뉴에서 **읽기-액세스-지역 중복 저장소 (RA-GRS)** 합니다.

    6.  에 대 한 **성능**, 클릭 **표준**합니다.

    7.  내 합니다 **보안 전송 필요** 섹션에서 **비활성화**합니다.

    8.  **구독** 드롭다운 메뉴에서 적절 한 구독을 선택 합니다.

    9.  선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    10. 둡니다 **가상 네트워크** 으로 **비활성** 선택할 경우.

    11. **만들기**를 클릭합니다.

        ![저장소 세부 정보 입력](images/AzureLabs-Lab8-15.png)

6.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

7.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다. 새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.

    ![새 저장소 알림](images/AzureLabs-Lab8-16.png)

8.  클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 새 저장소 서비스 인스턴스 개요 페이지로 이동 수는 있습니다.

    ![리소스로 이동](images/AzureLabs-Lab8-17.PNG)

9. 개요 페이지를 오른쪽에서 클릭 **테이블**합니다.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 오른쪽 패널을 표시 하도록 변경 됩니다 합니다 **테이블 서비스** 정보, 여기서 새 테이블을 추가 해야 합니다. 클릭 하 여이 작업을 수행 합니다 **+** **테이블** 왼쪽 위 모퉁이에 있는 단추입니다.

    ![테이블 열기](images/AzureLabs-Lab8-19.png)

11. 새 페이지가 표시 될 입력 해야 하는 여기서는 **테이블 이름**합니다. 뒷부분에서 응용 프로그램에서 데이터를 참조 하는 데 사용할 이름입니다. 적절 한 이름을 삽입 하 고 클릭 **확인**합니다.

    ![새 테이블 만들기](images/AzureLabs-Lab8-20.png)    

12. 새 테이블을 만든 후에 내에서 볼 수는 합니다 **테이블 서비스** 페이지 (아래쪽).

    ![만든 새 테이블](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>5 장-Visual Studio에서 Azure 테이블을 완료 합니다.

이제 프로그램 **테이블 서비스** 저장소 계정에 설치 되어, 정보 저장 및 검색에 사용 되는 데이터를 추가할 차례입니다. 테이블에 대 한 편집을 통해 수행할 수 있습니다 **Visual Studio**합니다.

1.  오픈 **Visual Studio**합니다.

2.  메뉴에서 클릭 **뷰** > **클라우드 탐색기**합니다.

    ![클라우드 탐색기를 열으십시오](images/AzureLabs-Lab8-22.png)

3.  합니다 **클라우드 탐색기** 열립니다 도킹 된 항목으로 일 환자, 대로 로드 시간이 걸릴 수 있습니다.

    > [!NOTE] 
    > 만드는 데 사용한 구독 하는 경우에 *저장소 계정* 표시 되지 않으면 했는지 확인 합니다. 
    > - Azure Portal에 사용한 것과 동일한 계정에 로그인 합니다.
    > - (계정 설정에서 필터를 적용 해야 할) 계정 관리 페이지에서 구독을 선택 합니다.  
    >
    >   ![구독을 찾을](images/AzureLabs-Lab8-22-5.png)

4.  Azure 클라우드 서비스에 표시 됩니다. 찾을 **저장소 계정** 계정을 확장 하는 왼쪽에 있는 화살표를 클릭 합니다.

    ![열려 있는 저장소 계정](images/AzureLabs-Lab8-23.png)

5.  새로 만든 확장 되 면 **저장소 계정** 사용할 수 있어야 합니다. 저장소, 왼쪽에 있는 화살표를 클릭 하 고 확장 되 면 찾습니다 **테이블** 표시 하려면 옆에 있는 화살표를 클릭 합니다 **테이블** 마지막 단원에서 만든 합니다. 두 번 클릭 하 여 **테이블**합니다.

    ![장면 개체 테이블 열기](images/AzureLabs-Lab8-24.png)

6.  테이블에는 Visual Studio 창의 가운데에 열립니다. 가 있는 테이블 아이콘을 클릭 합니다 **+** (및)에 있습니다.

    ![새 테이블 추가](images/AzureLabs-Lab8-25.png)

7.  수는 창이 나타나면 묻는 *엔터티 추가*합니다. 여러 속성을 사용 하 여 각 총에서 세 개의 엔터티가 만들어집니다. 점을 확인할 수 있습니다 *PartitionKey* 하 고 *RowKey* 기본적으로 제공의 데이터를 테이블에서 사용 됩니다. 

    ![파티션 및 행 키](images/AzureLabs-Lab8-26.png)

8. 업데이트를 *값* 의 **PartitionKey** 및 **RowKey** 같이 (에 추가한 각 행 속성에 대해이 작업을 수행 해야 하지만 RowKey을 증가 될 때마다):

    ![올바른 값 추가](images/AzureLabs-Lab8-26-5.png)

9.  클릭 **속성 추가** 데이터의 추가 행을 추가 합니다. 일치 하 여 첫 번째 빈 테이블은 아래 테이블입니다.

10. 클릭 **확인** 완료 되 면 합니다.

    ![완료 확인 클릭](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > 변경 했는지 확인 합니다 **형식** 의 **X**를 **Y**, 및 **Z**, 항목을 **Double**합니다. 

11. 이제 데이터 행이 있는 테이블을 확인할 수 있습니다. 클릭 합니다 **+** (다른 엔터티를 추가 하려면 다시 아이콘 더하기).

    ![첫 번째 행](images/AzureLabs-Lab8-27-5.png)

12. 추가 속성을 만들고 아래 표시 된 것과 일치 하도록 새 엔터티의 값을 설정 합니다.

    ![큐브를 추가 합니다.](images/AzureLabs-Lab8-28.png)

13. 다른 엔터티를 추가 하기 위한 마지막 단계를 반복 합니다. 아래 표시 된 것이 엔터티에 대 한 값을 설정 합니다.

    ![원기둥 추가](images/AzureLabs-Lab8-29.png)

14. 이제 테이블 아래 처럼 보여야 합니다.

    ![전체 테이블](images/AzureLabs-Lab8-30.png)

15. 이 챕터를 완료 했습니다. 저장 해야 합니다.

## <a name="chapter-6---create-an-azure-function-app"></a>-6 장 Azure 함수 앱 만들기

업데이트를 데스크톱 응용 프로그램에서 호출할 Azure 함수 앱을 만듭니다는 **테이블** 서비스를 통해 알림을 보내고 합니다 **알림 허브**합니다.

먼저 필요한 라이브러리를 로드 하 여 Azure Function을 사용 하면 파일을 만드는 해야 합니다.

1.  오픈 **메모장** (키 Windows 키와 notepad).

    ![메모장을 열려면](images/AzureLabs-Lab8-31.png)

2.  열기 메모장을 사용 하 여 아래 JSON 구조를 삽입 합니다. 작업을 수행한 후으로 바탕 화면에 저장 **project.json**합니다. 명명이 올바른 것: 확인 수행 **.txt 없는** 파일 확장명입니다. 익숙할 것 NuGet을 사용한 경우이 파일에서 함수를 사용 하는 라이브러리를 정의 합니다.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.

4.  일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 **함수 앱**, 키를 눌러 **Enter**합니다.

    ![함수 앱에 대 한 검색](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.

5.  새 페이지에 대 한 설명을 제공 합니다는 **함수 앱** 서비스입니다. 선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.

    ![함수 앱 인스턴스](images/AzureLabs-Lab8-33.png)

6.  클릭 한 후 **만들기**, 다음을 입력 합니다.

    1. 에 대 한 **앱 이름**,이 서비스 인스턴스에 대해 원하는 이름을 입력 합니다.

    2. 선택 된 **구독**합니다.

    3. 첫 번째 경우, 적합 한 가격 책정 계층 선택 만들기 시간을 **함수 앱 서비스**, 무료 계층을 사용할 수 있어야 합니다.

    4. 선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    5. 에 대 한 **OS**를 원하는 플랫폼으로 Windows를 클릭 합니다.

    6. 선택 된 **호스팅 계획** (이 자습서를 사용 하는 **소비 계획**.

    7. 선택 된 **위치** **(이전 단계에서 만든 저장소와 동일한 위치를 선택)**

    8. 에 대 한 합니다 **저장소** 섹션인 **이전 단계에서 만든 저장소 서비스를 선택 해야 합니다**합니다.

    9. 필요 하지 것입니다 *Application Insights* 이 앱에서 에게도 그대로 **해제**합니다.

    10. **만들기**를 클릭합니다.

        ![새 인스턴스 만들기](images/AzureLabs-Lab8-34.png)

7.  클릭 한 후 **만들기** 만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

8.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![새 알림](images/AzureLabs-Lab8-35.png)

9.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.

10. 클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 

    ![리소스로 이동](images/AzureLabs-Lab8-36.png)

11. 클릭 합니다 **+** (더하기) 옆에 아이콘 *함수*를 *새로 만들기*합니다.

    ![새 함수를 추가 합니다.](images/AzureLabs-Lab8-37.png)

12. 중앙 패널에는 **함수** 만들기 창이 표시 됩니다. 패널의 위쪽 절반에서 정보를 무시 하 고 클릭 **사용자 지정 함수**합니다 (아래와 같이 파란색 영역)의 맨 아래 근처에 있는 합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab8-38.png)

13. 창 내에서 새 페이지에는 다양 한 함수 형식 표시 됩니다. 자주색 형식을 보려면 아래로 스크롤하여 **HTTP PUT** 요소입니다.

    ![http put 링크](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > 그러나 다운 추가로 스크롤해야 할 수도 페이지 (및이 이미지 같지 않을 수 있습니다 정확 하 게 동일 하며 Azure Portal 업데이트 수행 하는 경우) 라는 이름의 요소에 대 한 원하는 *HTTP PUT*합니다.

14. 합니다 **HTTP PUT** 함수 (아래 이미지 참조)를 구성 해야 하는 창이 표시 됩니다.

    1.  에 대 한 **언어로** C를 선택 하 고 드롭다운 메뉴를 사용 하 여\#입니다.

    2.  에 대 한 **이름을** 적절 한 이름을 입력 합니다.

    3.  에 **인증 수준을** 드롭다운 메뉴에서 **함수**합니다.

    4.  에 대 한 합니다 **테이블 이름** 정확한 이름을 만드는 데 사용 해야 하는 섹션에 **테이블** 이전 (포함 된 동일한 대/소문자) 서비스입니다.

    5.  내 합니다 **Storage 계정 연결** 섹션 드롭다운 메뉴를 사용 하 고 여기에서 저장소 계정을 선택 합니다. 클릭 하지는 **새로 만들기** 저장소 계정의 나타나야 하는 다른 패널에 표시할 섹션 제목 함께 하이퍼링크입니다.

        ![새 저장소](images/AzureLabs-Lab8-40.png)

15. 클릭 **만들기** 및 설정을 성공적으로 업데이트 된 알림을 받게 됩니다.

    ![함수 만들기](images/AzureLabs-Lab8-41.png)

16. 클릭 한 후 **만들기**, 함수 편집기로 이동 합니다.

    ![함수 코드 업데이트](images/AzureLabs-Lab8-42.png)

17. (함수에서 코드를 대체) 하는 함수 편집기에 다음 코드를 삽입:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > 포함 된 라이브러리를 사용 하는 수신 이동 된 개체의 위치와 이름을 Unity 장면에서 (로 C# 이라는 개체 **UnityGameObject**). 이 개체는 만들어진된 테이블 내에서 개체 매개 변수를 업데이트 한 다음 사용 됩니다. 함수는 다음에 모든 구독된 응용 프로그램에 알립니다는 만든 알림 허브 서비스에 대 한 호출을 만듭니다.

18. 코드, 클릭 **저장할**합니다.

19. 다음을 클릭 합니다 **\<** 페이지의 오른쪽에 (화살표) 아이콘을 합니다.

    ![열기 업로드 패널](images/AzureLabs-Lab8-43.png)

20. 패널은 오른쪽에서에서 슬라이드 됩니다. 해당 창에서 클릭 **업로드**, 파일 탐색기에 표시 됩니다.

21. 찾아 클릭 합니다는 **project.json** 파일에서 만든 **메모장** 이전에 클릭 하 고는 **열기** 단추입니다. 이 파일은 라이브러리 함수를 사용할지를 정의 합니다.

    ![json 업로드](images/AzureLabs-Lab8-44.png)

22. 파일 업로드에 오른쪽 패널에 표시 됩니다. 내에서 열기를 클릭 하 여 **함수** 편집기입니다. 찾아야 **정확 하 게** (아래 23 단계) 다음 이미지와 동일 합니다.

23. 그런 다음, 왼쪽 패널에서 아래 **함수**를 클릭 합니다 **통합** 링크 합니다.

    ![함수를 통합 합니다.](images/AzureLabs-Lab8-45.png)

24. 다음 페이지 상단 오른쪽 모서리에서 클릭 **고급 편집기** (아래와 같이).

    ![고급 편집기 열기](images/AzureLabs-Lab8-46.png)

25. A **function.json** 파일이 다음 코드 조각을 사용 하 여 교체 해야 하는 가운데 창에서 열립니다. 작성 하는 함수 및 매개 변수를 정의 하는이 함수에 전달 합니다.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. 이제 편집기 아래 이미지 처럼 보여야 합니다.

    ![표준 편집기 돌아가기](images/AzureLabs-Lab8-47.png)

27. 방금 삽입 한 입력된 매개 변수 테이블 및 저장소 세부 정보를 일치 하지 않을 수 및 사용자 정보로 업데이트 해야 합니다를 확인할 수 있습니다. **이렇게 하지 않으면 여기**처럼 다음 적용 됩니다. 클릭할 합니다 **표준 편집기** 뒤로 돌아가서 페이지의 오른쪽 위 모서리에 있는 링크를 합니다.

28. 다시 합니다 **표준 편집기**, 클릭 **Azure Table Storage (테이블)** 아래에 있는 **입력**합니다. 
    
    ![입력 테이블](images/AzureLabs-Lab8-47-5.png)

29. 다음 일치 항목을 확인 **여** 정보를 다른 것으로 (다음 단계를 아래 이미지는):

    1.  **테이블 이름**: Azure Storage, 테이블 서비스 내에서 만든 테이블의 이름입니다.

    2.  **저장소 계정 연결:** 클릭 **새**드롭다운 메뉴와 함께 표시 되 고 창의 오른쪽에 패널이 표시 됩니다.

        ![새 저장소](images/AzureLabs-Lab8-48.png)

        1.  선택 하 **저장소 계정**, 호스트에 이전에 만든 된 **함수 앱.**

        2. 합니다 **저장소 계정** 연결 값이 생성 되었습니다.

        3. 키를 눌러 해야 **저장할** 완료 되 면 합니다.

    3.  **입력** 페이지과 일치 해야는 아래에서 보여 주는 **프로그램** 정보입니다.

        ![입력 완료](images/AzureLabs-Lab8-49.png)

30. 다음으로, 클릭 **Azure 알림 허브 (알림)** -아래 **출력**합니다. 다음과 일치 하도록 보장 **여** 정보를 다른 것으로 (다음 단계를 아래 이미지는):

    1.  **알림 허브 이름**:의 이름입니다 하 **알림 허브** 이전에 만든 서비스 인스턴스입니다.

    2.  **Notification Hubs 네임 스페이스 연결**: 클릭 **새**, 드롭다운 메뉴와 함께 표시 되는 합니다.

        ![출력 확인](images/AzureLabs-Lab8-50.png)

    3. **연결** 팝업이 표시 됩니다 (아래 이미지 참조)를 선택 해야 합니다 **Namespace** 의 **알림 허브**, 이전에 설정 하는 합니다.

    4. 선택 하면 **알림 허브** 중간 드롭다운 메뉴에서 이름입니다.

    5.  설정 된 **정책** 드롭다운 메뉴를 **DefaultFullSharedAccessSignature**합니다.

    6. 클릭 합니다 **선택** 다시 이동 합니다.

        ![출력 업데이트](images/AzureLabs-Lab8-51.png)

31.  **출력** 페이지과 일치 해야 합니다 아래 같지만 **에** 정보 대신 합니다. 키를 눌러 해야 **저장할**합니다.

> [!WARNING]
> *알림 허브 이름의 직접 편집 하지 마십시오* (이 모든 작업은 사용 하는 **고급 편집기**경우 이전 단계를 올바르게 수행 합니다.

![전체 출력](images/AzureLabs-Lab8-50.png)

32. 이 시점에서 작동 하도록 함수를 테스트 해야 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면 

    1. 한 번 더 함수 페이지로 이동 합니다.

        ![전체 출력](images/AzureLabs-Lab8-50-1.png)

    2. 함수 페이지 다시 클릭 합니다 **테스트** 열리는 페이지의 맨 오른쪽 탭의 *테스트* 블레이드에서:

        ![전체 출력](images/AzureLabs-Lab8-50-2.png)

    3. 내 합니다 **요청 본문** 붙여넣기 블레이드의 텍스트 상자는 아래 코드:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. 테스트 코드를 클릭 합니다 **실행** 단추 오른쪽 맨 아래에 있고 테스트 실행 됩니다. 테스트의 출력 로그를 콘솔 영역에 함수 코드에 표시 됩니다.

        ![전체 출력](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 위의 테스트에 실패 하면 해야 위의 단계를 정확 하 게 수행 하는 두 번 확인 내의 설정을 특히 합니다 **패널을 통합**합니다. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>7 장-데스크톱 Unity 프로젝트 설정

> [!IMPORTANT]
> 이제 만들려는 데스크톱 응용 프로그램 **것입니다** Unity 편집기에서 작동 합니다. Visual Studio를 사용 하 여 응용 프로그램 (또는 배포 된 응용 프로그램)를 작성 하는 다음 편집기 외부에서 실행 해야 합니다. 

다음은 일반적인 등록 Unity를 사용 하 여 개발 및 혼합된 현실에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

설정 하 고 혼합된 현실 몰입 형 헤드셋을 테스트 합니다.

> [!NOTE] 
> 해야 **되지** 이 과정에 대 한 동작 컨트롤러 필요 합니다. 몰입 형 헤드셋 설정만 지원에 필요한 경우 따르세요 이렇게 [Windows Mixed Reality를 설정 하는 방법에 대 한 링크](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.

1.  오픈 **Unity** 누릅니다 **새로 만들기**합니다.

    ![새 unity 프로젝트](images/AzureLabs-Lab8-52.png)

2.  Unity 프로젝트 이름을 삽입 해야 **UnityDesktopNotifHub**합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**합니다. 설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![프로젝트 만들기](images/AzureLabs-Lab8-53.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집할** > **기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![집합 외부 VS 도구](images/AzureLabs-Lab8-54.png)

4.  이동한 다음 **파일** > **빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환**단추를 선택 항목을 적용 합니다.

    ![플랫폼 전환](images/AzureLabs-Lab8-55.png)

5.  있는 동안 **파일** > **빌드 설정**, 있는지 확인 합니다.

    1.  **장치를 대상** 로 설정 된 **모든 장치**

        > 이 응용 프로그램 수는 데스크톱 이므로 이어야 합니다 **모든 장치**

    2.  **빌드 형식** 로 설정 된 **D3D**

    3.  **SDK** 로 설정 된 **가장 최근에 설치 된**

    4.  **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**

    5.  **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**

    6.  여기 하는 동안 가치가 장면 저장 하 고 빌드에 추가 합니다.

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.

            ![열기 장면 추가](images/AzureLabs-Lab8-56.png)

        2. 새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.

            ![새 백그라운드에서 폴더](images/AzureLabs-Lab8-57.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 **파일 이름:** 텍스트 필드에 입력 **NH\_데스크톱\_장면**, 누릅니다 **저장할**합니다.

            ![new NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.

6.  같은 창에서 클릭 하는 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치는 **검사기** 위치한.

7.  이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  에 **기타 설정** 탭:

        1.  **스크립팅 런타임 버전** 있어야 **실험적 (.NET 4.6 동등)**

        2. **백 엔드를 스크립팅** 있어야 **.NET**

        3. **API 호환성 수준** 있어야 **.NET 4.6**

            ![net 버전 4.6](images/AzureLabs-Lab8-59.png)

    2.  내 합니다 **게시 설정** 탭의 **기능**, 확인:

        - **InternetClient**

            ![눈금 인터넷 클라이언트](images/AzureLabs-Lab8-60.png)

8.  년대 **빌드 설정** *Unity C\# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.

9.  닫기 합니다 **빌드 설정** 창입니다.

10. 장면 및 프로젝트 저장할 **파일** > **장면 저장 파일** > **프로젝트를 저장할**합니다.

    > [!IMPORTANT]
    > 건너뛸 하려는 경우는 *Unity 설정* (데스크톱 앱)이이 프로젝트에 대 한 구성 요소 코드에 바로 계속를 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [9 장에서](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)합니다.  스크립트 구성 요소를 추가 해야 계속 합니다.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>8 장-Unity에서 Dll 가져오기

Azure Storage for Unity 사용 (자체는.Net 용 Azure SDK를 활용 함). 자세한 내용은이 작업 수행 [Unity에 대 한 Azure Storage에 대 한 링크](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)합니다.

플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다. 이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.

사용자 고유의 프로젝트에 SDK를 가져오려면 최신 다운로드 했는지 확인 [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) GitHub에서. 그런 다음 다음을 수행 합니다.

1.  추가 합니다 **.unitypackage** 사용 하 여 Unity에는 **자산 \> 패키지 가져오기 \> 사용자 지정 패키지** 메뉴 옵션입니다.

2.  에 **Unity 패키지 가져오기** 팝업에서 선택할 수 있는 아래에 있는 모든 상자 * **플러그 인* \> * 저장소 * * * 합니다.  이 과정에 대 한 필요 하지 않을 때 나머지 작업은 모두 선택 취소 합니다.

    ![패키지 가져오기](images/AzureLabs-Lab8-61.png)

3.  클릭 합니다 ***가져오기*** 프로젝트에 항목을 추가 하려면 단추입니다.

4.  로 이동 합니다 **저장소** 아래에 폴더 **플러그 인** 프로젝트에서 표시 하 고 다음 플러그 인 선택 *만*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![모든 플랫폼을 선택 취소](images/AzureLabs-Lab8-62.png)

5.  사용 하 여 *이러한 특정 플러그 인* 선택 하면 **의 선택을 취소** **Any 플랫폼** 고 **의 선택을 취소** **WSAPlayer** 누른 **적용**합니다.

    ![플랫폼 dll를 적용 합니다.](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > 이러한 특정 플러그 인 Unity 편집기에서 사용할 수만 표시 됩니다. Unity에서 프로젝트를 내보낸 후 사용할 WSA 폴더에 같은 플러그 인의 다양 한 버전 때문입니다.

6.  에 **저장소** 플러그 인 폴더에만 선택 합니다.

    -   Microsoft.Data.Services.Client

        ![집합에 dll에 대 한 처리](images/AzureLabs-Lab8-64.png)

7.  확인 합니다 **없는 프로세스** 상자에 **플랫폼 설정** 클릭 ***적용***합니다.

    ![없는 처리 적용](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > 표시 됩니다이 플러그 인 "처리"를 Unity 어셈블리 패 처가이 플러그 인을 처리 하는 데 문제가 있어. 플러그 인 처리 되지 않았습니다. 경우에 계속 작동 합니다.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>9-장 데스크톱 Unity 프로젝트에서 TableToScene 클래스 만들기

이제이 응용 프로그램을 실행 하는 코드를 포함 하는 스크립트를 작성 해야 합니다.

생성 해야 하는 첫 번째 스크립트 **TableToScene**를 담당 하는:

-   Azure 테이블 내 엔터티를 읽는 중입니다.
-   테이블 데이터를 사용 하 여 생성, 개체를 결정에 위치 합니다.

생성 해야 하는 두 번째 스크립트 **CloudScene**를 담당 하는:

-   장면 관련 개체를 끌어서 놓을 수 있도록 마우스 왼쪽 단추 클릭 이벤트를 등록 합니다.
-   이 Unity 장면에서 개체 데이터를 직렬화 하 고 Azure 함수 앱으로 전송 합니다.

이 클래스를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **Asset** 폴더는 프로젝트 패널 **만들기** > **폴더**합니다. 폴더의 이름을 **스크립트**합니다.

    ![스크립트 폴더 만들기](images/AzureLabs-Lab8-66.png)

    ![2 스크립트 폴더 만들기](images/AzureLabs-Lab8-67.png)

2.  열려는 방금 만든 폴더를 두 번 클릭 합니다.

3.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**. 스크립트 이름을 **TableToScene**합니다.

    ![새 c# 스크립트](images/AzureLabs-Lab8-68.png)
    ![TableToScene 이름 바꾸기](images/AzureLabs-Lab8-69.png)

4.  Visual Studio 2017에서 열려는 스크립트를 두 번 클릭 합니다.

5.  다음 네임 스페이스를 추가 합니다.

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  클래스 내에서 다음 변수를 삽입 합니다.

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > 대체는 **accountName** Azure Storage 서비스 이름 값 및 **accountKey** (참조 아래 이미지) Azure Portal에서 Azure Storage 서비스에 있는 키 값을 갖는 값입니다. 
    >
    > ![계정 키 가져오기](images/AzureLabs-Lab8-70.png)

7.  이제 추가 합니다 **start ()** 하 고 **Awake()** 클래스를 초기화 하는 방법입니다.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  내 합니다 **TableToScene** 클래스, Azure 테이블에서 값을 검색 하 고 사용 하 여 장면에서 적절 한 기본 형식을 생성 하는 메서드를 추가 합니다.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  외부 합니다 **TableToScene** serialize 및 deserialize 하는 응용 프로그램에서 사용 되는 클래스를 정의 해야 하는 클래스는 **테이블 엔터티**합니다.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. 했는지 **저장할** Unity 편집기로 다시 이동 하기 전에 합니다.

11. 클릭 합니다 **주 카메라** 에서 **계층** 패널에서 해당 속성에 표시 되도록 합니다 **검사기**.

12. 사용 하 여 합니다 **스크립트** 폴더를 열고 스크립트를 선택 **TableToScene 파일** 끕니다 합니다 **주 카메라**합니다. 결과 다음과 같이 합니다.

    ![주 카메라에 스크립트 추가](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>10-장 데스크톱 Unity 프로젝트에서 CloudScene 클래스 만들기

생성 해야 하는 두 번째 스크립트 **CloudScene**를 담당 하는:

-   장면 관련 개체를 끌어서 놓을 수 있도록 마우스 왼쪽 단추 클릭 이벤트를 등록 합니다.

-   이 Unity 장면에서 개체 데이터를 직렬화 하 고 Azure 함수 앱으로 전송 합니다.

두 번째 스크립트를 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기**에 **C\# 스크립트**합니다. 스크립트 이름을 **CloudScene**
    
    ![새 c# 스크립트](images/AzureLabs-Lab8-72.png)
    ![CloudScene 이름 바꾸기](images/AzureLabs-Lab8-73.png)

2.  다음 네임 스페이스를 추가 합니다.

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  다음 변수를 삽입 합니다.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  대체는 **azureFunctionEndpoint** 아래 이미지에 표시 된 대로 Azure Portal에서 Azure 함수 앱 서비스에 Azure 함수 앱 URL을 사용 하 여 값:

    ![함수 URL 가져오기](images/AzureLabs-Lab8-74.png)

5.  이제 추가 합니다 **start ()** 하 고 **Awake()** 클래스를 초기화 하는 방법입니다.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  내 합니다 **update ()** 메서드 검색 마우스 입력 및 끌어서 장면에서 Gameobject 이동에 다음 코드를 추가 합니다. 사용자가 끌어 하 고 개체를 삭제 하는 경우이 이름 및 개체의 좌표를 메서드에 전달할 **UpdateCloudScene()** 에 서비스 호출 하 여 Azure 함수 앱, Azure 테이블 및 트리거를 업데이트 하면는 알림입니다.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  이제 추가 합니다 **UpdateCloudScene()** 아래와 같이 메서드:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  코드를 저장 하 고 Unity에 반환 합니다.

9.  끌기 합니다 **CloudScene** 에 스크립트를 **주 카메라**합니다. 

    1. 클릭 합니다 **주 카메라** 에서 **계층** 패널에서 해당 속성에 표시 되도록 합니다 **검사기**. 

    2. 사용 하 여는 **스크립트** 폴더 열기를 선택 합니다 **CloudScene** 스크립팅하고 끕니다를 **주 카메라**합니다. 결과 다음과 같이 합니다.

        > ![주 카메라 클라우드 스크립트 끌어](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>11 장-uwp 데스크톱 프로젝트 빌드

이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되었습니다.

1.  이동할 **빌드 설정** (**파일** > **빌드 설정**).

2.  **빌드 설정** 창에서 클릭 **빌드**합니다.

    ![프로젝트 빌드](images/AzureLabs-Lab8-76.png)

3.  A **파일 탐색기** 창은 팝업에서 위치를 빌드에 대 한 메시지를 표시 합니다. 새 폴더를 만듭니다 (클릭 하 여 **새 폴더** 왼쪽 위 모서리에), 이름을 **빌드**합니다.

    ![빌드에 대 한 새 폴더](images/AzureLabs-Lab8-77.png)

    1.  새로운 **빌드** 폴더를 다른 폴더를 만들고 (사용 하 여 **새 폴더** 번), 하 고 이름을 **NH\_데스크톱\_앱**합니다.

        ![폴더 이름을 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  사용 하 여 합니다 **NH\_Desktop\_앱** 선택 합니다. 클릭 **폴더 선택**합니다. 프로젝트 빌드를 1 분 정도 걸립니다.

4.  다음 빌드에서 **파일 탐색기** 새 프로젝트의 위치를 표시 하는 데 나타납니다. 그러나 다른을 만들어야 하는 대로 Unity 프로젝트 먼저 다음의 몇 장을 열 필요가 없습니다.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>12 장-혼합 현실 Unity 프로젝트 설정

다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 **Unity** 누릅니다 **새로 만들기**합니다.

    ![새 unity 프로젝트](images/AzureLabs-Lab8-79.png)

2.  Unity 프로젝트 이름을 제공 해야 이제 삽입 **UnityMRNotifHub**합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**합니다. 설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집할** > **기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![vs 외부 편집기 설정](images/AzureLabs-Lab8-81.png)

4.  이동한 다음 **파일** > **빌드 설정** 플랫폼에서 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환**  단추입니다.

    ![UWP 플랫폼 전환](images/AzureLabs-Lab8-82.png)

5.  로 이동 **파일** > **빌드 설정** 되어 있는지 확인 합니다.

    1.  **장치를 대상** 로 설정 된 **모든 장치**

        > Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.

    2.  **빌드 형식** 로 설정 된 **D3D**

    3.  **SDK** 로 설정 된 **가장 최근에 설치 된**

    4.  **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**

    5.  **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**

    6.  여기 하는 동안 가치가 장면 저장 하 고 빌드에 추가 합니다.

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.

            ![열기 장면 추가](images/AzureLabs-Lab8-83.png)

        2. 새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.

            ![새 백그라운드에서 폴더](images/AzureLabs-Lab8-84.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 **파일 이름:** 텍스트 필드에 입력 **NH\_MR\_장면**, 누릅니다  **저장**합니다.

            ![new scene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.

6.  같은 창에서 클릭 하는 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치는 **검사기** 위치한.    

    ![플레이어 설정 열기](images/AzureLabs-Lab8-86.png)

7.  이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  에 **기타 설정** 탭:

        1.  **스크립팅 런타임 버전** 있어야 **실험적** (.NET 4.6 동등)
        2.  **백 엔드를 스크립팅** 있어야 ***.NET***
        3.  **API 호환성 수준** 있어야 **.NET 4.6**

            ![api 호환성](images/AzureLabs-Lab8-87.png)

    2.  패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가

        ![xr 하이 설정 업데이트](images/AzureLabs-Lab8-88.png)        

    3.  내 합니다 **게시 설정** 탭의 **기능**, 도대체:

        - **InternetClient**           

            ![눈금 인터넷 클라이언트](images/AzureLabs-Lab8-89.png)

8.  년대 **빌드 설정**를 **Unity C# 프로젝트** 를 더 이상 사용할 수 없습니다:이 옆의 확인란을 선택 합니다.

9.  이러한 변경과 수행할 빌드 설정 창을 닫습니다.

10. 장면 및 프로젝트 저장할 **파일** > **장면 저장 파일** > **프로젝트를 저장할**합니다.

    > [!IMPORTANT]
    > 건너뛸 하려는 경우는 *Unity 설정* (혼합 현실 앱)이이 프로젝트에 대 한 구성 요소 코드에 바로 계속를 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage),으로 프로젝트로가져올[ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 선택한 다음에서 계속 [14 장](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)합니다. 스크립트 구성 요소를 추가 해야 계속 합니다.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>13 장-혼합된 현실 Unity 프로젝트에서 Dll 가져오기

Unity 라이브러리 (.NET SDK를 사용 하 여 Azure에 대 한)에 대 한 Azure Storage 사용 됩니다. 이 수행 하십시오 [Unity를 사용 하 여 Azure Storage를 사용 하는 방법에 대 한 링크](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)합니다.
플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다. 이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.

사용자 고유의 프로젝트에 SDK를 가져오려면 최신 다운로드 했는지 확인 [.unitypackage](https://aka.ms/azstorage-unitysdk)합니다. 그런 다음 다음을 수행 합니다.

1.  Unity를 사용 하 여 위에서 다운로드 한.unitypackage를 추가 합니다 **자산** > **패키지 가져오기** > **Custom Package** 메뉴 옵션 .

2.  에 **Unity 패키지 가져오기** 팝업에서 선택할 수 있는 아래에 있는 모든 상자 **플러그 인** > **저장소**합니다.

    ![패키지 가져오기](images/AzureLabs-Lab8-90.png)

3.  클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.

4.  로 이동 합니다 **저장소** 아래에 폴더 **플러그 인** 프로젝트에서 표시 하 고 다음 플러그 인 선택 *만*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![플러그 인 선택](images/AzureLabs-Lab8-91.png)

5.  사용 하 여 *이러한 특정 플러그 인* 선택 하면 **의 선택을 취소** **Any 플랫폼** 고 **의 선택을 취소** **WSAPlayer** 누른 **적용**합니다.

    ![플랫폼 변경 내용 적용](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > 이러한 특정 플러그 인만 Unity 편집기에서 사용 하도록 표시 됩니다. Unity에서 프로젝트를 내보낸 후 사용할 WSA 폴더에 같은 플러그 인의 다양 한 버전 때문입니다.

6.  에 **저장소** 플러그 인 폴더에만 선택 합니다.

    -   Microsoft.Data.Services.Client

        ![data services 클라이언트를 선택 합니다.](images/AzureLabs-Lab8-93.png)

7.  확인 합니다 **없는 프로세스** 상자에 **플랫폼 설정** 클릭 **적용**합니다.

    ![처리 하지 않음](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > 표시 하는이 플러그 인 "처리 하지 않음" Unity 어셈블리 패 처가이 플러그 인을 처리 하는 데 문제가 있어. 플러그 인 처리 되지 않습니다 하는 경우에 계속 작동 합니다.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>14 장-혼합된 현실 Unity 프로젝트에서 TableToScene 클래스 만들기

합니다 **TableToScene** 클래스에 설명 된 것 같습니다 [9 장에서](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)합니다. 동일한 절차를 수행 하는 Unity 프로젝트에 설명 된 혼합된 현실에서 동일한 클래스를 만듭니다 [9 장에서](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)합니다.

이 장의 모두 완료 한 후에 **Unity 프로젝트** 이 클래스는 주 카메라에서 설정 해야 합니다.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>15 장-혼합 현실 Unity 프로젝트에서 NotificationReceiver 클래스 만들기

생성 해야 하는 두 번째 스크립트 **NotificationReceiver**를 담당 하는:

-   초기화 시 알림 허브를 사용 하 여 앱을 등록 합니다.
-   알림 허브에서 보내는 알림을 수신 합니다.
-   받은 알림에서 개체 데이터를 역직렬화 합니다.
-   Deserialize 된 데이터를 기반으로 하는 장면에서의 Gameobject를 이동 합니다.

만들려는 합니다 **NotificationReceiver** 스크립트:

1.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기**에 **C\# 스크립트**합니다. 스크립트 이름을 **NotificationReceiver**합니다.

    ![새 c# 스크립트를 만듭니다](images/AzureLabs-Lab8-95.png)
    ![NotificationReceiver 이름을](images/AzureLabs-Lab8-96.png)

2.  열려는 스크립트를 두 번 클릭 합니다.

3.  다음 네임 스페이스를 추가 합니다.

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  다음 변수를 삽입 합니다.

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  대체는 **hubName** 알림 허브 서비스 이름, 값 및 **hubListenEndpoint** Azure 알림 허브 서비스, 액세스 정책 탭에 있는 끝점 값을 사용 하 여 값을 Azure Portal (아래 이미지 참조).

    ![notification hubs 정책 끝점 삽입](images/AzureLabs-Lab8-97.png)

6.  이제 추가 합니다 **start ()** 하 고 **Awake()** 클래스를 초기화 하는 방법입니다.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  추가 된 **WaitForNotification** 주 스레드를 사용 하 여 충돌 없이 Notification Hub 라이브러리에서 알림을 받도록 앱을 허용 하는 방법.

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  다음 메서드를 **InitNotificationAsync()** , 초기화 시 알림 허브 서비스를 사용 하 여 응용 프로그램을 등록 합니다. 코드 주석 처리 되어 Unity 프로젝트를 빌드할 수 있습니다. Visual Studio에서 Azure 메시징 Nuget 패키지를 가져올 때 주석을 제거 합니다.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  다음 처리기 **채널\_PushNotificationReceived()** , 알림의 받을 때마다 트리거됩니다. 데스크톱 응용 프로그램을 이동 된 Azure 테이블 엔터티로 이동한 다음 해당 GameObject MR 장면에서 같은 위치에 있는 알림을 역직렬화 하는 것입니다. 
    
    > [!IMPORTANT]
    > 코드를 Visual Studio 내에서 Nuget 패키지 관리자를 사용 하 여 Unity 프로젝트를 빌드한 후 추가 하는 Azure 메시징 라이브러리에 참조 하기 때문에 코드는 주석입니다. 따라서 Unity 프로젝트 주석으로 처리 하지 않는 한 없습니다를 빌드할 수 됩니다. 수는 해야 프로젝트를 빌드 및 Unity에 반환 하려면 해야 **주석 다시** 코드입니다.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Unity 편집기로 다시 이동 하기 전에 변경 내용을 저장 해야 합니다.

11. 클릭 합니다 **주 카메라** 에서 **계층** 패널에서 해당 속성에 표시 되도록 합니다 **검사기**.

12. 사용 하 여는 **스크립트** 폴더 열기를 선택 합니다 **NotificationReceiver** 스크립팅하고 끕니다를 **주 카메라**합니다. 결과 다음과 같이 합니다.

    ![카메라에 알림 수신기 스크립트를 끌어 옵니다.](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > 를 개발 하는이 Microsoft HoloLens 대 한 업데이트 해야 합니다는 **주 카메라**의 *카메라* 구성 요소 되도록 합니다.
    > - 플래그를 지웁니다. 단색
    > - Background: 검정

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>16 장-uwp 혼합된 현실 프로젝트 빌드

이 장에서 빌드 프로세스는 이전 프로젝트에 대 한 동일 합니다. 이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.

1.  이동할 **빌드 설정** ( **파일** > **빌드 설정** ).

2.  **빌드 설정** 메뉴에서 확인 **Unity C# 프로젝트*** 선택 됩니다 (수 있는이 프로젝트의 스크립트는 빌드 후 편집 하려면).

3.  이 완료 되 면 클릭 **빌드**합니다.

    ![프로젝트 빌드](images/AzureLabs-Lab8-99.png)

4.  A **파일 탐색기** 창은 팝업에서 위치를 빌드에 대 한 메시지를 표시 합니다. 새 폴더를 만듭니다 (클릭 하 여 **새 폴더** 왼쪽 위 모서리에), 이름을 **빌드**합니다.

    ![빌드 폴더 만들기](images/AzureLabs-Lab8-100.png)

    1.  새로운 **빌드** 폴더를 다른 폴더를 만들고 (사용 하 여 **새 폴더** 번), 하 고 이름을 **NH\_MR\_앱**합니다.

        ![NH_MR_Apps 폴더 만들기](images/AzureLabs-Lab8-101.png)

    2.  사용 하 여 합니다 **NH\_MR\_앱** 선택 합니다. 클릭 **폴더 선택**합니다. 프로젝트 빌드를 1 분 정도 걸립니다.

5.  다음 빌드에는 **파일 탐색기** 새 프로젝트의 위치에서 창이 열립니다.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>17 장-UnityMRNotifHub 솔루션에 NuGet 패키지 추가

> [!WARNING] 
> 해제해 서는 다음 NuGet 패키지를 추가 하면 (다음에서 코드를 주석 처리 제거 [장](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), 코드를 Unity 프로젝트 내에서 다시 열 때 오류가 표시 됩니다. 뒤로 돌아가서 Unity 편집기의 편집을 계속 하려는 경우 해당 errosome 코드를 주석으로 한 Visual Studio에서 다시 되 면 나중에 다시 주석 필요 합니다. 

혼합된 현실 빌드가 완료 되 면 혼합된 현실 프로젝트를 빌드한로 이동 및 Visual Studio 2017을 사용 하 여 솔루션을 열려면 해당 폴더 내의 솔루션 (.sln) 파일을 두 번 클릭 합니다.
이제 추가 해야 합니다 **WindowsAzure.Messaging.managed** NuGet 패키지를 알림 허브에서 알림을 수신 하는 데 사용 되는 라이브러리입니다.

NuGet 패키지를 가져오려면:

1.  에 **솔루션 탐색기**, 솔루션을 마우스 오른쪽 단추로 클릭

2.  클릭할 **NuGet 패키지 관리**합니다.

    ![nuget 관리자를 열려면](images/AzureLabs-Lab8-102.png)

3.  선택 된 ***찾아보기*** 탭 및 검색할 **WindowsAzure.Messaging.managed**합니다.

    ![windows azure 메시징 패키지 찾기](images/AzureLabs-Lab8-103.png)

4.  결과 (아래와 같이)를 선택 하 고 오른쪽 창에서의 확인란을 선택 옆 **프로젝트**합니다. 이 틱의에서 배치 확인란 옆에 **프로젝트**, 옆에 있는 확인란이 함께 합니다 **어셈블리 CSharp** 하 고 **UnityMRNotifHub** 프로젝트.

    ![모든 프로젝트를 선택 합니다.](images/AzureLabs-Lab8-104.png)

5.  처음에 제공 된 버전이 **아닐** 이 프로젝트와 호환 되어야 합니다. 따라서 옆에 드롭다운 메뉴에서 클릭 **버전**, 클릭 **버전 0.1.7.9**, 클릭 **설치**합니다.

6.  이제 NuGet 패키지 설치를 완료 합니다. 에 입력 한 설명이 포함 된 코드를 **NotificationReceiver** 클래스 및 주석을 제거...



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>18 장-편집 UnityMRNotifHub 응용 프로그램, NotificationReceiver 클래스

추가한 경우 다음 합니다 **NuGet 패키지**, 해야 *주석 처리를 제거* 내에서 코드의 일부를 **NotificationReceiver** 클래스.

다음을 포함합니다.

1. 맨 위에 있는 네임 스페이스:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. 내의 모든 코드를 **InitNotificationsAsync()** 메서드:

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> 위의 코드에 주석을: 했는지 실수로 *주석 처리가 제거 된* (코드는 컴파일되지 않습니다 경우!)으로 주석입니다.

3. 마지막으로, 합니다 **Channel_PushNotificationReceived** 이벤트:

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

이러한 주석 처리가 제거 된를 사용 하 여 저장 하 고 다음 장에서를 계속 확인 합니다.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>19 장-스토어 앱에 혼합된 현실 프로젝트 연결

연결 해야 합니다 **혼합 현실을** 스토어 앱 랩의 시작에서 만든 프로젝트입니다.

1.  솔루션을 엽니다.

2.  이동 하려면 솔루션 탐색기 창에서 UWP 앱 프로젝트를 마우스 오른쪽 단추로 클릭 **스토어**, 및 **스토어와 앱을 연결 하는 중...** .

    ![저장소 연결을 열기](images/AzureLabs-Lab8-105.png)

3.  새 창을 호출 나타납니다 **Windows 스토어와 앱 연결**합니다. **다음**을 클릭합니다.

    ![다음 화면으로 이동](images/AzureLabs-Lab8-106.png)

4.  로그인 하는 계정에 연결 된 모든 응용 프로그램을 로드 됩니다. 계정에 로그인 하지 않은 경우 **로그인** 페이지입니다.

5.  찾을 합니다 **스토어 앱 이름을** 이 자습서의 시작 부분에 만들고 선택 합니다. 그리고 **다음**을 클릭합니다.

    ![찾기 및 저장소 이름을 선택합니다](images/AzureLabs-Lab8-107.png)

6.  클릭 **연결**합니다.

    ![앱 연결](images/AzureLabs-Lab8-108.png)

7.  앱이 이제 **관련 된** 스토어 앱을 사용 하 여 합니다. 이 알림을 사용 하도록 설정 하는 데 필요한 경우

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>20 장-UnityMRNotifHub 및 UnityDesktopNotifHub 응용 프로그램 배포

이 장에서 실행 되는 앱, 데스크톱 컴퓨터에서 실행 중인 컴퓨터를 한와 몰입 형 헤드셋 내에서 다른 결과가 포함 됩니다 두 사람이 사용 하 여 더 쉬울 수 있습니다.

몰입 형 헤드셋 앱 장면 (로컬 Gameobject의 위치 변경)에 변경 내용을 수신 대기 중인 및 데스크톱 앱은 변경할 수 MR 앱에 공유 되는 해당 로컬 장면 (위치 변경). 데스크톱 앱은 뒤에 수신기에서 수신 대기를 시작할 수 있도록 MR 앱을 먼저 배포 하는 것이 만듭니다.

배포 하는 **UnityMRNotifHub** 로컬 컴퓨터에 앱:

1.  솔루션 파일을 열고 프로그램 **UnityMRNotifHub** 에서 앱 **Visual Studio 2017**합니다.

2.  에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.

3.  에 **솔루션 구성** 선택 **디버그**합니다.

    ![프로젝트 구성 설정](images/AzureLabs-Lab8-109.png)

4.  로 이동 **빌드 메뉴** 을 클릭할 **솔루션 배포** 을 컴퓨터에 응용 프로그램을 사이드 로드 합니다.

5.  이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.

배포 하는 **UnityDesktopNotifHub** 로컬 컴퓨터에서 앱:

1.  솔루션 파일을 열고 프로그램 **UnityDesktopNotifHub** 에서 앱 **Visual Studio 2017**합니다.

2.  에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.

3.  에 **솔루션 구성** 선택 **디버그**합니다.

    ![프로젝트 구성 설정](images/AzureLabs-Lab8-110.png)

4.  로 이동 **빌드 메뉴** 을 클릭할 **솔루션 배포** 을 컴퓨터에 응용 프로그램을 사이드 로드 합니다.

5.  이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.

6.  뒤에 데스크톱 응용 프로그램 혼합된 현실 응용 프로그램을 시작 합니다.

실행 중인 두 응용 프로그램을 사용 하 여 (왼쪽 마우스 단추를 사용 하 여) 데스크톱 장면에 개체를 이동 합니다. 이러한 위치 변경 내용은 로컬로 만든, serialize 되며 함수 앱 서비스로 전송 합니다. 함수 앱 서비스에서 알림 허브와 함께 테이블을 업데이트 합니다. 업데이트를 수신, 알림 허브는 보내기 업데이트 된 데이터를 직접 모든 등록 된 응용 프로그램 (이 경우 몰입 형 헤드셋 앱), 그러면 들어오는 데이터를 deserialize 하 고 로컬 개체에 새 위치 데이터를 적용 합니다. 장면에서 이동 합니다.


## <a name="your-finished-your-azure-notification-hubs-application"></a>사용자 Azure Notification Hubs 응용 프로그램을 완료 합니다.
 
축, Azure Notification Hubs 서비스를 활용 하 고 앱 간의 통신을 허용 하는 혼합된 현실 앱을 작성 합니다.
 
![최종 제품-종료](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

장면을 보는 다른 앱으로 해당 알림을 보내고는 Gameobject의 색을 변경 하는 방법을 사용할 수 있습니다?

### <a name="exercise-2"></a>연습 2

수는 Gameobject 이동을 MR 앱에 추가 하 고 데스크톱 앱에서 업데이트 된 장면을 참조 하세요?
