---
title: MR 및 Azure 308-장치 간 알림
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Notification Hubs, Azure Functions 및 Azure Storage와 테이블을 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 알림, 기능, 테이블, notification hubs, hololens, 몰입 형, vr
ms.openlocfilehash: d65750f37815efecae85e7bff85318a234079af8
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438752"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR 및 Azure 308: 장치 간 알림

![최종 제품-시작](images/AzureLabs-Lab8-00.png)

이 과정에서는 Azure Notification Hubs, Azure 테이블 및 Azure Functions를 사용 하 여 혼합 현실 응용 프로그램에 Notification Hubs 기능을 추가 하는 방법에 대해 설명 합니다.

**Azure Notification Hubs** 는 개발자가 대상 및 개인 설정 된 푸시 알림을 모든 플랫폼에 보낼 수 있도록 하는 Microsoft 서비스입니다. 모두 클라우드 내에서 제공 됩니다. 이를 통해 개발자는 시나리오에 따라 최종 사용자와 통신 하거나 다양 한 응용 프로그램 간에 통신할 수 있습니다. 자세한 내용은 **Azure Notification Hubs** [페이지](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)를 참조 하세요.

**Azure Functions** 는 개발자가 Azure에서 작은 코드, ' 함수 '를 실행할 수 있도록 해 주는 Microsoft 서비스입니다. 이렇게 하면 다양 한 이점을 얻을 수 있는 로컬 응용 프로그램이 아닌 클라우드로 작업을 위임할 수 있습니다. **Azure Functions** 는 C\#, F\#, Node.js, JAVA 및 PHP를 비롯 한 몇 가지 개발 언어를 지원 합니다. 자세한 내용은 **Azure Functions** [페이지](https://docs.microsoft.com/azure/azure-functions/functions-overview)를 참조 하세요.

**Azure Tables** 는 개발자가 구조화 되지 않은 SQL 데이터를 클라우드에 저장 하 여 어디서 나 쉽게 액세스할 수 있도록 하는 Microsoft 클라우드 서비스입니다. 이 서비스는 스키마 boasts 디자인 하 여 필요에 따라 테이블의 진화를 허용 하므로 매우 유연 합니다. 자세한 내용은 **Azure Tables** [페이지](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) 를 참조 하세요.

이 과정을 완료 한 후에는 다음과 같은 작업을 수행할 수 있는 혼합 현실 모던 헤드셋 응용 프로그램 및 데스크톱 PC 응용 프로그램이 포함 됩니다.

1. 데스크톱 PC 앱을 사용 하면 사용자가 마우스를 사용 하 여 2D 공간 (X 및 Y)으로 개체를 이동할 수 있습니다.

2. PC 앱 내의 개체 이동은 JSON을 사용 하 여 클라우드로 전송 됩니다. JSON은 개체 ID, 유형 및 변환 정보 (X 및 Y 좌표)를 포함 하는 문자열 형식입니다. 

3. 데스크톱 앱과 동일한 장면을 포함 하는 혼합 현실 앱은 데스크톱 PC 앱에 의해 업데이트 된 Notification Hubs 서비스에서 개체 이동에 대 한 알림을 받습니다. 

4. 개체 ID, 유형 및 변환 정보를 포함 하는 알림이 수신 되 면 혼합 현실 앱은 수신 된 정보를 자신의 장면에 적용 합니다.

응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다. 이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다. 이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다. 이 과정은 다른 혼합 현실 랩을 직접 포함 하지 않는 자체 포함 된 자습서입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 308: 장치 간 알림</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다. 과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다. HoloLens를 사용 하는 경우 음성 캡처 중에 몇 가지 echo를 확인할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다. [도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- 모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC
- [개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)
- Azure 설치 및 Notification Hubs 액세스를 위한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 확인 사항

- 이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
- Microsoft 개발자 포털 및 응용 프로그램 등록 포털의 소유자 여야 합니다. 그렇지 않으면 [2 장의](#chapter-2---retrieve-your-new-apps-credentials)앱에 액세스할 수 있는 권한이 없는 것입니다.

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>1 장-Microsoft 개발자 포털에서 응용 프로그램 만들기

**Azure Notification Hubs** 서비스를 사용 하려면 응용 프로그램을 등록 해야 하므로 알림을 보내고 받을 수 있도록 Microsoft 개발자 포털에서 응용 프로그램을 만들어야 합니다.

1.  [Microsoft 개발자 포털](https://developer.microsoft.com/dashboard)에 로그인 합니다.

    > Microsoft 계정에 로그인 해야 합니다.

2.  대시보드에서 **새 앱 만들기**를 클릭 합니다.

    ![앱 만들기](images/AzureLabs-Lab8-01.png)

3.  새 앱의 이름을 예약 해야 하는 팝업이 표시 됩니다. 텍스트 상자에 적절 한 이름을 삽입 합니다. 선택한 이름을 사용할 수 있으면 텍스트 상자의 오른쪽에 눈금이 표시 됩니다. 사용 가능한 이름을 삽입 한 후에는 팝업의 왼쪽 아래에 있는 **제품 이름 예약** 단추를 클릭 합니다.

    ![이름 바꾸기](images/AzureLabs-Lab8-02.png)

4.  이제 앱을 만들었으므로 다음 장으로 이동할 준비가 되었습니다.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>2 장-새 앱 자격 증명 검색

새 앱이 나열 되는 응용 프로그램 등록 포털에 로그인 하 고 **Azure Portal**내에서 **Notification Hubs 서비스** 를 설정 하는 데 사용 되는 자격 증명을 검색 합니다.

1.  [응용 프로그램 등록 포털](https://apps.dev.microsoft.com)로 이동 합니다.

    ![응용 프로그램 등록 포털](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > 로그인 하려면 Microsoft 계정을 사용 해야 합니다.  
    > Windows 스토어 개발자 포털을 사용 하 여 이전 [챕터](#chapter-1---create-an-application-on-the-microsoft-developer-portal)에서 사용한 Microsoft 계정 **이어야 합니다** .

2.  **내 응용 프로그램** 섹션에서 앱을 찾을 수 있습니다. 해당 파일을 찾으면 앱 이름 및 **등록**을 포함 하는 새 페이지로 이동 합니다.

    ![새로 등록 된 앱](images/AzureLabs-Lab8-04.png)

3.  등록 페이지 아래로 스크롤하여 **응용 프로그램 암호** 섹션과 앱에 대 한 **패키지 SID** 를 찾습니다. 다음 장에서 **Azure Notification Hubs 서비스** 를 설정 하는 데 사용할 두 가지를 모두 복사 합니다.

    ![응용 프로그램 암호](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>3 장-Azure Portal 설정: Notification Hubs 서비스 만들기

앱 자격 증명이 검색 되 면 azure Notification Hubs 서비스를 만들 Azure Portal로 이동 해야 합니다.

1.  [Azure Portal](https://portal.azure.com)에 로그인 합니다.

    > [!NOTE] 
    > 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

2.  로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 **알림 허브**를 검색 한 다음 ***Enter 키***를 누릅니다.

    ![알림 허브 검색](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 새 단어는 ***새*** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.

3.  새 페이지에 *Notification Hubs* 서비스에 대 한 설명이 제공 됩니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.

    ![notification hubs 인스턴스 만들기](images/AzureLabs-Lab8-07.png)

4.  ***만들기***를 클릭 하면 다음을 클릭 합니다.

    1.  이 서비스 인스턴스의 원하는 이름을 삽입 합니다.

    2.  이 앱에 연결할 수 있는 **네임 스페이스** 를 제공 합니다.

    3.  위치를 선택 **합니다.**

    4.  리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요. 

    5.  적절 한 **구독**을 선택 합니다.

    6.  또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.

    7. **만들기**를 선택합니다.

        ![서비스 정보 입력](images/AzureLabs-Lab8-08.png)

5.  **만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

6.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![알림](images/AzureLabs-Lab8-09.png)

7.  알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 새 **알림 허브** 서비스 인스턴스로 이동 됩니다.

    ![리소스로 이동](images/AzureLabs-Lab8-10.png)
    
8.  개요 페이지의 페이지 아래쪽에서 **Windows (WNS)를 클릭 합니다.** 오른쪽의 패널은 이전에 설정한 앱에서 **패키지 SID** 및 **보안 키**를 필요로 하는 두 개의 텍스트 필드를 표시 하도록 변경 됩니다.

    ![새로 만든 허브 서비스](images/AzureLabs-Lab8-11.png)

9. 세부 정보를 올바른 필드에 복사한 후에는 **저장**을 클릭 합니다. 그러면 알림 허브가 성공적으로 업데이트 되 면 알림이 표시 됩니다.

    ![보안 세부 정보 복사](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>4 장-Azure Portal 설정: 테이블 서비스 만들기

Notification Hubs 서비스 인스턴스를 만든 후에는 Azure Portal로 다시 이동 합니다. 여기서 저장소 리소스를 만들어 Azure Tables 서비스를 만듭니다.

1.  아직 로그인 하지 않은 경우 [Azure Portal](https://portal.azure.com)에 로그인 합니다.

2.  로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 **저장소 계정**을 검색 한 다음 **Enter 키**를 누릅니다.

    > [!NOTE] 
    > 새 단어는 ***새*** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.

3.  목록에서 **저장소 계정-blob, 파일, 테이블, 큐** 를 선택 합니다.

    ![저장소 계정 검색](images/AzureLabs-Lab8-13.png)

4.  새 페이지에 **저장소 계정** 서비스에 대 한 설명이 제공 됩니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스의 인스턴스를 만듭니다.

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab8-14.png)

5.  **만들기**를 클릭 하면 패널이 표시 됩니다.

    1. 이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다 (모두 소문자 여야 함).

    2. **배포 모델**에서 **리소스 관리자**를 클릭 합니다.

    3.  **계정 종류**의 경우 드롭다운 메뉴에서 **저장소 (범용 v1)** 를 선택 합니다.

    4. 적절 한 **위치**를 선택 합니다.
    
    5.  **복제** 드롭다운 메뉴에서 **읽기 액세스-지역 중복 저장소 (RA-GRS)** 를 선택 합니다.

    6.  **성능**으로 **표준**을 클릭 합니다.

    7.  **보안 전송 필요** 섹션에서 **사용 안 함**을 선택 합니다.

    8.  **구독** 드롭다운 메뉴에서 적절 한 구독을 선택 합니다.

    9.  리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.

    10. 이 옵션을 선택 하는 경우 **가상 네트워크** 를 **사용 하지 않도록 설정** 된 상태로 둡니다.

    11. **만들기**를 클릭합니다.

        ![저장소 정보 입력](images/AzureLabs-Lab8-15.png)

6.  **만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

7.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다. 알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

    ![새 저장소 알림](images/AzureLabs-Lab8-16.png)

8.  알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 새 저장소 서비스 인스턴스 개요 페이지로 이동 됩니다.

    ![리소스로 이동](images/AzureLabs-Lab8-17.PNG)

9. 개요 페이지에서 오른쪽에 있는 **테이블**을 클릭 합니다.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 오른쪽의 패널은 새 테이블을 추가 해야 하는 **Table service** 정보를 표시 하도록 변경 됩니다. 이렇게 하려면 왼쪽 위 모서리에서 **테이블** **+** 단추를 클릭 합니다.

    ![테이블 열기](images/AzureLabs-Lab8-19.png)

11. **테이블 이름을**입력 해야 하는 새 페이지가 표시 됩니다. 이 이름은 이후 장에서 응용 프로그램의 데이터를 참조 하는 데 사용 됩니다. 적절 한 이름을 삽입 하 고 **확인을**클릭 합니다.

    ![새 테이블 만들기](images/AzureLabs-Lab8-20.png)    

12. 새 테이블을 만든 후에는 **Table service** 페이지 (아래쪽)에서 볼 수 있습니다.

    ![새 테이블을 만들었습니다.](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>5 장-Visual Studio에서 Azure 테이블 완료

이제 **Table service** storage 계정이 설정 되었으므로 데이터를 추가 하 여 정보를 저장 하 고 검색 하는 데 사용 됩니다. 테이블 편집은 **Visual Studio**를 통해 수행할 수 있습니다.

1.  **Visual Studio**를 엽니다.

2.  메뉴에서 **보기** > **클라우드 탐색기**를 클릭 합니다.

    ![클라우드 탐색기 열기](images/AzureLabs-Lab8-22.png)

3.  **클라우드 탐색기** 은 도킹 된 항목으로 열립니다. 로드 시 시간이 걸릴 수 있으므로 잠시 기다려 주십시오.

    > [!NOTE] 
    > *저장소 계정을* 만드는 데 사용한 구독이 표시 되지 않는 경우 다음을 확인 합니다. 
    > - Azure Portal에 사용한 것과 동일한 계정에 로그인 합니다.
    > - 계정 관리 페이지에서 구독을 선택 했습니다 (계정 설정에서 필터를 적용 해야 할 수 있음).  
    >
    >   ![구독 찾기](images/AzureLabs-Lab8-22-5.png)

4.  Azure cloud services가 표시 됩니다. **저장소 계정을** 찾고 왼쪽에 있는 화살표를 클릭 하 여 계정을 확장 합니다.

    ![저장소 계정 열기](images/AzureLabs-Lab8-23.png)

5.  확장 되 면 새로 만든 **저장소 계정을** 사용할 수 있습니다. 저장소 왼쪽에 있는 화살표를 클릭 한 다음 확장 되 면 **테이블** 을 찾아 해당 옆의 화살표를 클릭 하 여 마지막 챕터에서 만든 **테이블** 을 표시 합니다. **테이블**을 두 번 클릭 합니다.

    ![장면 개체 테이블 열기](images/AzureLabs-Lab8-24.png)

6.  Visual Studio 창의 중앙에서 테이블이 열립니다. 테이블 아이콘을 클릭 하 고 **+** ()를 클릭 합니다.

    ![새 테이블 추가](images/AzureLabs-Lab8-25.png)

7.  *엔터티를 추가*하 라는 창이 표시 됩니다. 각각 몇 가지 속성을 포함 하는 세 개의 엔터티를 전체로 만듭니다. *PartitionKey* 및 *rowkey* 는 테이블에서 데이터를 찾기 위해 사용 되므로 이미 제공 된 것을 알 수 있습니다. 

    ![파티션 및 행 키](images/AzureLabs-Lab8-26.png)

8. 다음과 같이 **PartitionKey** 및 **rowkey** *값* 을 업데이트 합니다. 즉, 사용자가 추가 하는 각 행 속성에 대해이 작업을 수행 해야 하지만 매번 rowkey를 증가 시킵니다.

    ![올바른 값 추가](images/AzureLabs-Lab8-26-5.png)

9.  데이터 행을 더 추가 하려면 **속성 추가** 를 클릭 합니다. 첫 번째 빈 테이블이 아래 표와 일치 하는지 확인 합니다.

10. 작업이 완료 되 면 **확인을** 클릭 합니다.

    ![완료 되 면 확인을 클릭 합니다.](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > **X**, **Y**, **Z**항목의 **형식을** **Double**로 변경 했는지 확인 합니다. 

11. 이제 테이블에 데이터 행이 있다는 것을 알 수 있습니다. **+** (더하기) 아이콘을 다시 클릭 하 여 다른 엔터티를 추가 합니다.

    ![첫 번째 행](images/AzureLabs-Lab8-27-5.png)

12. 추가 속성을 만든 다음 아래 표시 된 것과 일치 하도록 새 엔터티의 값을 설정 합니다.

    ![큐브 추가](images/AzureLabs-Lab8-28.png)

13. 마지막 단계를 반복 하 여 다른 엔터티를 추가 합니다. 이 엔터티의 값을 아래에 표시 된 값으로 설정 합니다.

    ![원통 추가](images/AzureLabs-Lab8-29.png)

14. 이제 테이블이 아래와 같이 표시 됩니다.

    ![테이블 완료](images/AzureLabs-Lab8-30.png)

15. 이 챕터를 완료 했습니다. 저장 해야 합니다.

## <a name="chapter-6---create-an-azure-function-app"></a>6 장-Azure 함수 앱 만들기

데스크톱 응용 프로그램에서 **테이블** 서비스를 업데이트 하 고 알림 **허브**를 통해 알림을 보내기 위해 호출 하는 Azure 함수 앱를 만듭니다.

먼저 Azure 함수에서 필요한 라이브러리를 로드 하도록 허용 하는 파일을 만들어야 합니다.

1.  **메모장** 을 엽니다 (Windows 키를 누르고 메모장을 입력).

    ![메모장 열기](images/AzureLabs-Lab8-31.png)

2.  메모장을 열고 아래에 JSON 구조를 삽입 합니다. 이 작업을 완료 한 후에는 데스크톱에 프로젝트를 **json**으로 저장 합니다. 이름 지정이 올바른지 확인 하는 것이 **중요 합니다.** 이 파일은 함수가 사용 하는 라이브러리를 정의 합니다. NuGet을 사용 하는 경우 익숙할 것입니다.

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

3.  [Azure Portal](https://portal.azure.com)에 로그인 합니다.

4.  로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 **함수 앱**를 검색 한 후 **enter**키를 누릅니다.

    ![함수 앱 검색](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.

5.  새 페이지에 **함수 앱** 서비스에 대 한 설명이 제공 됩니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.

    ![함수 앱 인스턴스](images/AzureLabs-Lab8-33.png)

6.  **만들기**를 클릭 한 후에는 다음을 입력 합니다.

    1. **앱 이름**에 대해 원하는 이름을이 서비스 인스턴스에 삽입 합니다.

    2. **구독**을 선택 합니다.

    3. 적절 한 가격 책정 계층을 선택 합니다. **함수 앱 서비스**를 처음 만드는 경우 무료 계층을 사용할 수 있어야 합니다.

    4. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.

    5. **OS**의 경우 원하는 플랫폼인 Windows를 클릭 합니다.

    6. **호스팅 계획** 을 선택 합니다 .이 자습서는 **소비 계획**을 사용 합니다.

    7. 위치 선택 **(이전 단계에서 빌드한 저장소와 동일한 위치 선택)**

    8. **저장소** 섹션의 경우 **이전 단계에서 만든 저장소 서비스를 선택 해야**합니다.

    9. 이 앱에 *Application Insights* 필요 **하지 않으므로 자유롭게 그대로 둡니다.**

    10. **만들기**를 클릭합니다.

        ![새 인스턴스 만들기](images/AzureLabs-Lab8-34.png)

7.  **만들기** 를 클릭 하면 서비스를 만들 때까지 기다려야 합니다 .이 경우에는 1 분 정도 걸릴 수 있습니다.

8.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![새 알림](images/AzureLabs-Lab8-35.png)

9.  알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

10. 알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 

    ![리소스로 이동](images/AzureLabs-Lab8-36.png)

11. *함수*옆에 있는 **+** (더하기) 아이콘을 클릭 하 여 *새를 만듭니다*.

    ![새 함수 추가](images/AzureLabs-Lab8-37.png)

12. 중앙 패널 내에서 **함수** 만들기 창이 표시 됩니다. 패널의 위쪽 절반에 있는 정보를 무시 하 고 사용자 지정 함수를 클릭 합니다 .이 함수는 아래와 같이 파란색 영역에서 아래쪽에 있는 **사용자 지정 함수**를 클릭 합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab8-38.png)

13. 창 내의 새 페이지에 다양 한 함수 형식이 표시 됩니다. 아래로 스크롤하여 자주색 형식을 확인 하 고 **HTTP PUT** 요소를 클릭 합니다.

    ![http put 링크](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > 페이지 아래로 스크롤해야 할 수도 있습니다 (Azure Portal 업데이트를 수행 하는 경우이 이미지는 정확히 동일 하지 않을 수 있음). 그러나 *HTTP PUT*이라는 요소를 찾고 있습니다.

14. **HTTP PUT** 창이 표시 됩니다. 여기에서 함수를 구성 해야 합니다 (이미지는 아래 참조).

    1.  **언어** 의 경우 드롭다운 메뉴를 사용 하 여 C\#를 선택 합니다.

    2.  **이름** 에 대해 적절 한 이름을 입력 합니다.

    3.  **인증 수준** 드롭다운 메뉴에서 **함수**를 선택 합니다.

    4.  **테이블 이름** 섹션의 경우 이전에 **테이블** 서비스를 만드는 데 사용한 정확한 이름을 사용 해야 합니다 (같은 문자를 포함).

    5.  **저장소 계정 연결** 섹션에서 드롭다운 메뉴를 사용 하 고 여기에서 저장소 계정을 선택 합니다. 표시 되지 않는 경우 섹션 제목과 함께 **새** 하이퍼링크를 클릭 하 여 저장소 계정이 나열 될 다른 패널을 표시 합니다.

        ![새 저장소](images/AzureLabs-Lab8-40.png)

15. **만들기** 를 클릭 하면 설정이 성공적으로 업데이트 되었다는 알림이 표시 됩니다.

    ![create 함수](images/AzureLabs-Lab8-41.png)

16. **만들기**를 클릭 한 후에는 함수 편집기로 리디렉션됩니다.

    ![함수 코드 업데이트](images/AzureLabs-Lab8-42.png)

17. 함수 편집기에 다음 코드를 삽입 합니다 (함수의 코드 대체).

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
    > 함수는 포함 된 라이브러리를 사용 하 여 Unity 장면에서 이동 된 개체의 이름과 위치를 C# **UnityGameObject**라는 개체로 받습니다. 그런 다음이 개체를 사용 하 여 생성 된 테이블 내에서 개체 매개 변수를 업데이트 합니다. 이를 통해 함수는 생성 된 알림 허브 서비스를 호출 하 여 모든 구독 응용 프로그램에 알립니다.

18. 코드가 준비 되 면 **저장**을 클릭 합니다.

19. 그런 다음 페이지의 오른쪽에 있는 **\<** (화살표) 아이콘을 클릭 합니다.

    ![업로드 패널 열기](images/AzureLabs-Lab8-43.png)

20. 패널은 오른쪽에서 오른쪽으로 이동 합니다. 해당 패널에서 **업로드**를 클릭 하면 파일 브라우저가 나타납니다.

21. 로 이동 하 여 이전에 **메모장** 에서 만든 **프로젝트. json** 파일을 클릭 한 다음 **열기** 단추를 클릭 합니다. 이 파일은 함수에서 사용할 라이브러리를 정의 합니다.

    ![json 업로드](images/AzureLabs-Lab8-44.png)

22. 파일이 업로드 되 면 오른쪽의 패널에 표시 됩니다. 이 단추를 클릭 하면 **함수** 편집기 내에서 열립니다. 다음 이미지와 **정확히** 동일 하 게 표시 되어야 합니다 (23 단계 아래).

23. 그런 다음 왼쪽 패널의 **함수**아래에서 **통합** 링크를 클릭 합니다.

    ![기능 통합](images/AzureLabs-Lab8-45.png)

24. 다음 페이지의 오른쪽 위 모서리에서 **고급 편집기** (아래 참조)를 클릭 합니다.

    ![고급 편집기 열기](images/AzureLabs-Lab8-46.png)

25. 다음 코드 조각으로 바꾸어야 하는 중간 패널에서 **함수 json** 파일이 열립니다. 이 함수는 빌드하는 함수와 함수에 전달 되는 매개 변수를 정의 합니다.

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

26. 이제 편집기는 아래 이미지와 같습니다.

    ![표준 편집기로 돌아가기](images/AzureLabs-Lab8-47.png)

27. 방금 삽입 한 입력 매개 변수가 테이블 및 저장소 세부 정보와 일치 하지 않을 수 있으므로 사용자 정보로 업데이트 해야 합니다. 다음에 설명 된 대로 **이 작업을 수행 하지 마십시오**. 페이지의 오른쪽 위 모퉁이에 있는 **표준 편집기** 링크를 클릭 하면 돌아갑니다.

28. **표준 편집기**로 돌아가서 **입력**아래의 **Azure Table Storage (테이블)** 를 클릭 합니다. 
    
    ![테이블 입력](images/AzureLabs-Lab8-47-5.png)

29. 다음과 같이 다를 수 있으므로 **사용자** 의 정보와 일치 하는지 확인 합니다 (다음 단계 아래에 이미지가 있음).

    1.  **테이블 이름**: Azure Storage 테이블 서비스 내에서 만든 테이블의 이름입니다.

    2.  **Storage 계정 연결:** 드롭다운 메뉴와 함께 표시 되는 **새로 만들기**를 클릭 하면 창 오른쪽에 패널이 표시 됩니다.

        ![새 저장소](images/AzureLabs-Lab8-48.png)

        1.  함수 앱을 호스트 하기 위해 이전에 만든 **저장소 계정을**선택 **합니다.**

        2. **저장소 계정** 연결 값이 생성 된 것을 알 수 있습니다.

        3. 작업을 완료 한 후에는 **저장** 을 눌러야 합니다.

    3.  **입력** 페이지는 이제 **사용자** 정보를 표시 하는 아래와 일치 해야 합니다.

        ![입력 완료](images/AzureLabs-Lab8-49.png)

30. 그런 다음, **출력**아래에서 **Azure notification hubs (알림)** 를 클릭 합니다. 다음 단계는 다를 수 있으므로 **사용자** 의 정보와 일치 하는지 확인 합니다 (다음 단계 아래에 이미지가 있음).

    1.  **알림 허브 이름**: 이전에 만든 **알림 허브** 서비스 인스턴스의 이름입니다.

    2.  **네임 스페이스 연결 Notification Hubs**: 드롭다운 메뉴와 함께 표시 되는 **새로 만들기**를 클릭 합니다.

        ![출력 검사](images/AzureLabs-Lab8-50.png)

    3. 이전에 설정한 **알림 허브**의 **네임 스페이스** 를 선택 해야 하는 **연결** 팝업이 표시 됩니다 (아래 이미지 참조).

    4. 중간 드롭다운 메뉴에서 **알림 허브** 이름을 선택 합니다.

    5.  **정책** 드롭다운 메뉴를 **Defaultfullsharedaccesssignature**로 설정 합니다.

    6. 뒤로 이동 하려면 **선택** 단추를 클릭 합니다.

        ![출력 업데이트](images/AzureLabs-Lab8-51.png)

31.  이제 **출력** 페이지가 아래와 일치 하지만 **사용자** 의 정보를 포함 합니다. **저장**을 눌러야 합니다.

> [!WARNING]
> *알림 허브 이름을 직접 편집 하지 마십시오* . 이전 단계를 올바르게 수행한 경우에는 **고급 편집기**를 사용 하 여 모두 수행 해야 합니다.

![출력 완료](images/AzureLabs-Lab8-50.png)

32. 이 시점에서 함수를 테스트 하 여 작동 하는지 확인 해야 합니다. 이렇게 하려면 다음을 수행합니다. 

    1. 함수 페이지로 이동 합니다.

        ![출력 완료](images/AzureLabs-Lab8-50-1.png)

    2. 함수 페이지로 돌아가서 페이지 맨 오른쪽의 **테스트** 탭을 클릭 하 여 *테스트* 블레이드를 엽니다.

        ![출력 완료](images/AzureLabs-Lab8-50-2.png)

    3. 블레이드의 **요청 본문** 텍스트 상자 내에 아래 코드를 붙여넣습니다.

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

    4. 테스트 코드가 준비 되 면 오른쪽 아래에 있는 **실행** 단추를 클릭 하면 테스트가 실행 됩니다. 테스트의 출력 로그는 콘솔 영역에서 함수 코드 아래에 표시 됩니다.

        ![출력 완료](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 위의 테스트가 실패 하는 경우 위의 단계를 정확히, 특히 **통합 패널**내에서 설정 했는지 확인 해야 합니다. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>7 장-데스크톱 Unity 프로젝트 설정

> [!IMPORTANT]
> 지금 만들고 있는 데스크톱 응용 프로그램은 Unity 편집기에서 작동 **하지** 않습니다. Visual Studio (또는 배포 된 응용 프로그램)를 사용 하 여 응용 프로그램을 빌드한 후 편집기 외부에서 실행 해야 합니다. 

다음은 Unity 및 mixed reality를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.

> [!NOTE] 
> 이 과정에서는 동작 컨트롤러가 필요 **하지** 않습니다. 모던 헤드셋을 설정 하는 데 지원이 필요한 경우 [Windows Mixed Reality를 설정 하는 방법에 대 한 링크](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)를 참조 하세요.

1.  **Unity** 를 열고 **새로 만들기**를 클릭 합니다.

    ![새 unity 프로젝트](images/AzureLabs-Lab8-52.png)

2.  Unity 프로젝트 이름, insert **UnityDesktopNotifHub**을 제공 해야 합니다. 프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다. 위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다. 그런 다음 **프로젝트 만들기**를 클릭 합니다.

    ![프로젝트 만들기](images/AzureLabs-Lab8-53.png)

3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.  > **기본 설정** **편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![외부 VS 도구 설정](images/AzureLabs-Lab8-54.png)

4.  그런 다음 **파일** > **빌드 설정** 으로 이동 하 고 **유니버설 Windows 플랫폼**을 선택한 후 **플랫폼 전환** 단추를 클릭 하 여 선택 항목을 적용 합니다.

    ![플랫폼 전환](images/AzureLabs-Lab8-55.png)

5.  **파일** > **빌드 설정**에 있는 동안 다음을 확인 합니다.

    1.  **대상 장치가** **모든 장치로** 설정 됨

        > 이 응용 프로그램은 데스크톱을 위한 것 이므로 **모든 장치** 여야 합니다.

    2.  **빌드 형식이** **D3D** 로 설정 됩니다.

    3.  **SDK** 가 **최신 설치** 로 설정 됨

    4.  **Visual Studio 버전이** **최신 설치** 로 설정 됨

    5.  **빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨

    6.  여기서는 장면을 저장 하 고 빌드에 추가 하는 것이 좋습니다.

        1. 이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다. 저장 창이 표시 됩니다.

            ![열려 있는 장면 추가](images/AzureLabs-Lab8-56.png)

        2. 이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음

            ![새 장면 폴더](images/AzureLabs-Lab8-57.png)

        3. 새로 만든 **장면** 폴더를 연 다음 **파일 이름:** 텍스트 필드에 **Nh\_Desktop\_장면**을 입력 하 고 **저장**을 누릅니다.

            ![새 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  **빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.

6.  동일한 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.

7.  이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  **기타 설정** 탭에서 다음을 수행 합니다.

        1.  **스크립팅 런타임 버전이** 실험적 이어야 함 **(.net 4.6 해당)**

        2. **Scripting 백엔드** 는 **.net** 이어야 합니다.

        3. **API 호환성 수준은** **.net 4.6** 이어야 합니다.

            ![4.6 네트워크 버전](images/AzureLabs-Lab8-59.png)

    2.  **게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.

        - **InternetClient**

            ![tick 인터넷 클라이언트](images/AzureLabs-Lab8-60.png)

8.  **빌드 설정** 으로 돌아가기 *Unity C\# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.

9.  **빌드 설정** 창을 닫습니다.

10. 장면 및 프로젝트 **파일** 을 저장 하 > **장면/파일** > 저장 **프로젝트**를 저장 합니다.

    > [!IMPORTANT]
    > 이 프로젝트에 대 한 *Unity 설정* 구성 요소 (데스크톱 앱)를 건너뛰고 코드를 바로 계속 하려면 unitypackage를 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 챕터에서 계속 [합니다.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage) [ 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  스크립트 구성 요소를 추가 해야 합니다.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>8 장-Unity에서 Dll 가져오기

Unity에 Azure Storage를 사용 하 게 됩니다 (자체는 Azure 용 .Net SDK를 활용). 자세한 내용은 [Unity Azure Storage에 대](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)한이 링크를 참조 하세요.

현재 Unity에는 가져온 후 플러그 인을 다시 구성 해야 하는 알려진 문제가 있습니다. 이러한 단계 (이 섹션에서는 4-7)는 버그가 해결 된 후 더 이상 필요 하지 않습니다.

SDK를 고유한 프로젝트로 가져오려면 GitHub에서 최신 [**unitypackage**](https://aka.ms/azstorage-unitysdk) 를 다운로드 했는지 확인 합니다. 그런 후에 다음을 수행 합니다.

1.  **\> \> 패키지 가져오기 사용자 지정 패키지** 메뉴 옵션의 자산을 사용 하 여 **unitypackage** 을 Unity에 추가 합니다.

2.  팝업 되는 **Unity 패키지 가져오기** 상자에서 * **플러그 인* \> * 저장소 * * * 아래의 모든 항목을 선택할 수 있습니다.  이 과정에서 필요 하지 않으므로 다른 모든 항목을 선택 취소 합니다.

    ![패키지로 가져오기](images/AzureLabs-Lab8-61.png)

3.  ***가져오기*** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.

4.  프로젝트 뷰에서 **플러그 인** 의 **저장소** 폴더로 이동 하 고 다음 플러그 인 *만*선택 합니다.

    -   Microsoft. Data Edm
    -   Microsoft. Data OData
    -   Windowsazure.servicebus
    -   Newtonsoft.json
    -   System.string

![모든 플랫폼 선택 취소](images/AzureLabs-Lab8-62.png)

5.  *이러한 특정 플러그* 인을 선택 하 고 **플랫폼** 을 선택 **취소** 하 고 **WSAPlayer** **선택을 취소** 한 후 **적용**을 클릭 합니다.

    ![플랫폼 dll 적용](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > 이러한 특정 플러그인을 Unity 편집기 에서만 사용 하도록 표시 합니다. 이는 프로젝트를 Unity에서 내보낸 후에 사용 되는 WSA 폴더에 동일한 플러그 인의 버전이 서로 다르기 때문입니다.

6.  **저장소** 플러그 인 폴더에서 다음만을 선택 합니다.

    -   Microsoft. Data. Service. 클라이언트

        ![dll에 대해 처리 안 함 설정](images/AzureLabs-Lab8-64.png)

7.  **플랫폼 설정** 에서 **처리 안 함** 상자를 선택 하 고 ***적용***을 클릭 합니다.

    ![처리 안 함 적용](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Unity 어셈블리 patcher이 플러그 인을 처리 하는 데 어려움을 겪고 있으므로이 플러그 인을 "처리 안 함"으로 표시 합니다. 플러그 인은 처리 되지 않은 경우에도 계속 작동 합니다.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>9 장-데스크톱 Unity 프로젝트에서 TableToScene 클래스 만들기

이제이 응용 프로그램을 실행 하는 코드가 포함 된 스크립트를 만들어야 합니다.

만들어야 하는 첫 번째 스크립트는 다음을 담당 하는 **TableToScene**입니다.

-   Azure 테이블 내에서 엔터티를 읽습니다.
-   테이블 데이터를 사용 하 여 생성할 개체와 위치를 결정 합니다.

만들어야 하는 두 번째 스크립트는 다음을 담당 하는 **Cloudscene**됩니다.

-   왼쪽 클릭 이벤트를 등록 하 여 사용자가 장면 주위로 개체를 끌어올 수 있도록 합니다.
-   이 Unity 장면에서 개체 데이터를 직렬화 하 고 Azure 함수 앱로 보냅니다.

이 클래스를 만들려면:

1.  프로젝트 패널에 있는 **자산** 폴더를 마우스 오른쪽 단추로 클릭 하 > **폴더**를 **만듭니다** . 폴더 이름을 **스크립트**로 합니다.

    ![스크립트 폴더 만들기](images/AzureLabs-Lab8-66.png)

    ![스크립트 폴더 만들기 2](images/AzureLabs-Lab8-67.png)

2.  위에서 만든 폴더를 두 번 클릭 하 여 엽니다.

3.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 >  **C# 스크립트** **만들기** 를 클릭 합니다. 스크립트 이름을 **TableToScene**로 합니다.

    ![새 c # 스크립트](images/AzureLabs-Lab8-68.png)
    ![TableToScene 이름 바꾸기](images/AzureLabs-Lab8-69.png)

4.  스크립트를 두 번 클릭 하 여 Visual Studio 2017에서 엽니다.

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
    > **AccountName** 값을 Azure Storage 서비스 이름 및 **accountKey** 값으로 대체 하 고 Azure Portal에서 Azure Storage 서비스의 키 값으로 대체 합니다 (아래 이미지 참조). 
    >
    > ![계정 키 페치](images/AzureLabs-Lab8-70.png)

7.  이제 **Start ()** 및 **활성 ()** 메서드를 추가 하 여 클래스를 초기화 합니다.

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

8.  **TableToScene** 클래스 내에서 Azure 테이블의 값을 검색 하는 메서드를 추가 하 고이를 사용 하 여 장면에서 적절 한 기본 형식을 생성 합니다.

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

9.  **TableToScene** 클래스 외부에서는 응용 프로그램에서 **테이블 엔터티**를 serialize 및 deserialize 하는 데 사용 하는 클래스를 정의 해야 합니다.

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

10. Unity 편집기로 다시 이동 하기 전에를 **저장** 해야 합니다.

11. **계층** 패널에서 **주 카메라** 를 클릭 하 여 해당 속성이 **검사기**에 표시 되도록 합니다.

12. **Scripts** 폴더가 열리면 스크립트 **TableToScene 파일** 을 선택 하 여 **기본 카메라로**끌어 놓습니다. 결과는 다음과 같아야 합니다.

    ![주 카메라에 스크립트 추가](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>10 장-데스크톱 Unity 프로젝트에서 CloudScene 클래스 만들기

만들어야 하는 두 번째 스크립트는 다음을 담당 하는 **Cloudscene**됩니다.

-   왼쪽 클릭 이벤트를 등록 하 여 사용자가 장면 주위로 개체를 끌어올 수 있도록 합니다.

-   이 Unity 장면에서 개체 데이터를 직렬화 하 고 Azure 함수 앱로 보냅니다.

두 번째 스크립트를 만들려면 다음을 수행 합니다.

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **만들기**, **C\# 스크립트**를 차례로 클릭 합니다. 스크립트 **Cloudscene** 이름
    
    ![새 c # 스크립트](images/AzureLabs-Lab8-72.png)
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

4.  아래 이미지에 나와 있는 것 처럼 azure Portal에서 azure 함수 앱 서비스의 azure 함수 앱 URL을 사용 하 여 **azureFunctionEndpoint** 값을 대체 합니다.

    ![함수 URL 가져오기](images/AzureLabs-Lab8-74.png)

5.  이제 **Start ()** 및 **활성 ()** 메서드를 추가 하 여 클래스를 초기화 합니다.

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

6.  **Update ()** 메서드 내에서 마우스 입력을 감지 하 고 끌 수 있는 다음 코드를 추가 합니다. 이렇게 하면 장면의 gameobject 이동 합니다. 사용자가 개체를 끌어서 놓으면 개체의 이름과 좌표가 **UpdateCloudScene ()** 메서드에 전달 됩니다 .이 서비스는 azure 테이블을 업데이트 하 고 알림을 트리거하는 azure 함수 앱 서비스를 호출 합니다.

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

7.  이제 다음과 같이 **UpdateCloudScene ()** 메서드를 추가 합니다.

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

8.  코드를 저장 하 고 Unity로 돌아가기

9.  **Cloudscene** 스크립트를 **기본 카메라로**끌어 놓습니다. 

    1. **계층** 패널에서 **주 카메라** 를 클릭 하 여 해당 속성이 **검사기**에 표시 되도록 합니다. 

    2. **Scripts** 폴더가 열리면 **cloudscene** 스크립트를 선택 하 고 **기본 카메라로**끌어 놓습니다. 결과는 다음과 같아야 합니다.

        > ![클라우드 스크립트를 기본 카메라로 끌어 옵니다.](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>11 장-UWP에 데스크톱 프로젝트 빌드

이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었습니다.

1.  **빌드 설정** (**파일** > **빌드 설정**)으로 이동 합니다.

2.  **빌드 설정** 창에서 **빌드**를 클릭 합니다.

    ![프로젝트 빌드](images/AzureLabs-Lab8-76.png)

3.  빌드할 위치를 묻는 메시지를 표시 하는 **파일 탐색기** 창이 표시 됩니다. 왼쪽 위 모서리에서 **새 폴더** 를 클릭 하 여 새 폴더를 만들고 이름을 **작성**합니다.

    ![빌드용 새 폴더](images/AzureLabs-Lab8-77.png)

    1.  새 **빌드** 폴더를 열고 **새 폴더** 를 한 번 더 사용 하 여 다른 폴더를 만든 다음 **데스크톱\_앱\_이름을 n h**로 합니다.

        ![폴더 이름 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  **Nh\_Desktop\_앱** 을 선택 합니다. **폴더 선택**을 클릭 합니다. 프로젝트를 빌드하는 데 1 분 정도 걸립니다.

4.  빌드 다음에는 새 프로젝트의 위치를 보여 주는 **파일 탐색기** 가 표시 됩니다. 그러나 다음 몇 장에서는 먼저 다른 Unity 프로젝트를 만들어야 하므로 열 필요가 없습니다.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>12 장-혼합 현실 Unity 프로젝트 설정

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

1.  **Unity** 를 열고 **새로 만들기**를 클릭 합니다.

    ![새 unity 프로젝트](images/AzureLabs-Lab8-79.png)

2.  이제 Unity 프로젝트 이름, insert **UnityMRNotifHub**을 제공 해야 합니다. 프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다. 위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다. 그런 다음 **프로젝트 만들기**를 클릭 합니다.

    ![이름 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.  > **기본 설정** **편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![외부 편집기를 VS로 설정](images/AzureLabs-Lab8-81.png)

4.  그런 다음 **파일** > **빌드 설정** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.

    ![플랫폼을 UWP로 전환](images/AzureLabs-Lab8-82.png)

5.  **파일** > **빌드 설정** 으로 이동 하 고 다음을 확인 합니다.

    1.  **대상 장치가** **모든 장치로** 설정 됨

        > Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.

    2.  **빌드 형식이** **D3D** 로 설정 됩니다.

    3.  **SDK** 가 **최신 설치** 로 설정 됨

    4.  **Visual Studio 버전이** **최신 설치** 로 설정 됨

    5.  **빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨

    6.  여기서는 장면을 저장 하 고 빌드에 추가 하는 것이 좋습니다.

        1. 이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다. 저장 창이 표시 됩니다.

            ![열려 있는 장면 추가](images/AzureLabs-Lab8-83.png)

        2. 이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음

            ![새 장면 폴더](images/AzureLabs-Lab8-84.png)

        3. 새로 만든 **장면** 폴더를 연 다음 **파일 이름:** 텍스트 필드에 **Nh\_MR\_장면**을 입력 하 고 **저장**을 누릅니다.

            ![새 장면-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  **빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.

6.  동일한 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.    

    ![플레이어 설정 열기](images/AzureLabs-Lab8-86.png)

7.  이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  **기타 설정** 탭에서 다음을 수행 합니다.

        1.  **스크립팅 런타임 버전이** **실험적** 이어야 함 (.net 4.6 해당)
        2.  **Scripting 백엔드** 는 ***.net*** 이어야 합니다.
        3.  **API 호환성 수준은** **.net 4.6** 이어야 합니다.

            ![api 호환성](images/AzureLabs-Lab8-87.png)

    2.  패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.

        ![xr 설정 업데이트](images/AzureLabs-Lab8-88.png)        

    3.  **게시 설정** 탭의 **기능**아래에서 다음을 수행 합니다.

        - **InternetClient**           

            ![tick 인터넷 클라이언트](images/AzureLabs-Lab8-89.png)

8.  **빌드 설정**으로 돌아가서 **Unity C# 프로젝트가** 더 이상 회색으로 표시 되지 않습니다 .이 옆의 확인란을 선택 합니다.

9.  이러한 변경 작업을 수행한 후 빌드 설정 창을 닫습니다.

10. 장면 및 프로젝트 **파일** 을 저장 하 > **장면/파일** > 저장 **프로젝트**를 저장 합니다.

    > [!IMPORTANT]
    > 이 프로젝트에 대 한 *Unity 설정* 구성 요소 (혼합 현실 앱)를 건너뛰고 바로 코드를 계속 사용 하려면 [unitypackage를 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)하 고 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [ 14 장](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). 스크립트 구성 요소를 추가 해야 합니다.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>13 장-Mixed Reality Unity 프로젝트에서 Dll 가져오기

Unity 라이브러리 (Azure 용 .Net SDK 사용)에 대 한 Azure Storage를 사용 합니다. Unity를 사용 하 여 [Azure Storage를 사용 하는 방법에 대 한 링크를](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)참조 하세요.
현재 Unity에는 가져온 후 플러그 인을 다시 구성 해야 하는 알려진 문제가 있습니다. 이러한 단계 (이 섹션에서는 4-7)는 버그가 해결 된 후 더 이상 필요 하지 않습니다.

SDK를 고유한 프로젝트로 가져오려면 최신 [unitypackage](https://aka.ms/azstorage-unitysdk)를 다운로드 했는지 확인 합니다. 그런 후에 다음을 수행 합니다.

1.  위에서 다운로드 한 unitypackage을 >  > **패키지 가져오기** **사용자 지정 패키지** 메뉴 **옵션을 사용** 하 여 Unity에 추가 합니다.

2.  표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** > **저장소**에서 모든 항목을 선택할 수 있습니다.

    ![패키지 가져오기](images/AzureLabs-Lab8-90.png)

3.  **가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.

4.  프로젝트 뷰에서 **플러그 인** 의 **저장소** 폴더로 이동 하 고 다음 플러그 인 *만*선택 합니다.

    -   Microsoft. Data Edm
    -   Microsoft. Data OData
    -   Windowsazure.servicebus
    -   Newtonsoft.json
    -   System.string

    ![플러그 인 선택](images/AzureLabs-Lab8-91.png)

5.  *이러한 특정 플러그* 인을 선택 하 고 **플랫폼** 을 선택 **취소** 하 고 **WSAPlayer** **선택을 취소** 한 후 **적용**을 클릭 합니다.

    ![플랫폼 변경 내용 적용](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > 이러한 특정 플러그인을 Unity 편집기 에서만 사용 하도록 표시 하 고 있습니다. 이는 프로젝트를 Unity에서 내보낸 후에 사용 되는 WSA 폴더에 동일한 플러그 인의 버전이 서로 다르기 때문입니다.

6.  **저장소** 플러그 인 폴더에서 다음만을 선택 합니다.

    -   Microsoft. Data. Service. 클라이언트

        ![data services 클라이언트 선택](images/AzureLabs-Lab8-93.png)

7.  **플랫폼 설정** 에서 **처리 안 함** 상자를 선택 하 고 **적용**을 클릭 합니다.

    ![처리 안 함](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Unity 어셈블리 patcher이 플러그 인을 처리 하는 데 어려움이 있으므로이 플러그 인을 "처리 안 함"으로 표시 합니다. 플러그 인은 처리 되지 않은 경우에도 계속 작동 합니다.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>14 장-mixed reality Unity 프로젝트에서 TableToScene 클래스 만들기

**TableToScene** 클래스는 [9 장](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)에서 설명한 것과 동일 합니다. [9 장](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)에서 설명한 것과 동일한 절차에 따라 혼합 현실 Unity 프로젝트에서 동일한 클래스를 만듭니다.

이 챕터를 완료 한 후에는 두 **Unity 프로젝트** 에서이 클래스를 기본 카메라에 설정 합니다.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>15 장-Mixed Reality Unity 프로젝트에서 NotificationReceiver 클래스 만들기

생성 해야 하는 두 번째 스크립트는 다음과 같은 작업을 담당 하는 **Notificationreceiver**입니다.

-   초기화할 때 알림 허브에 앱을 등록 하는 중입니다.
-   알림 허브에서 들어오는 알림을 수신 대기 합니다.
-   수신 된 알림에서 개체 데이터를 deserialize 합니다.
-   Deserialize 된 데이터를 기반으로 장면에서 Gameobject를 이동 합니다.

**Notificationreceiver** 스크립트를 만들려면 다음을 수행 합니다.

1.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **만들기**, **C\# 스크립트**를 차례로 클릭 합니다. 스크립트의 이름을 **Notificationreceiver**로 합니다.

    ![새 c # 스크립트](images/AzureLabs-Lab8-95.png)
    ![이름을 NotificationReceiver로 만듭니다](images/AzureLabs-Lab8-96.png)

2.  스크립트를 두 번 클릭 하 여 엽니다.

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

5.  **HubName** 값을 알림 허브 서비스 이름으로 대체 하 고, **HubListenEndpoint** 값을 Azure Portal의 액세스 정책 탭, azure Notification Hub Service에 있는 끝점 값으로 대체 합니다 (아래 이미지 참조).

    ![notification hubs 정책 끝점 삽입](images/AzureLabs-Lab8-97.png)

6.  이제 **Start ()** 및 **활성 ()** 메서드를 추가 하 여 클래스를 초기화 합니다.

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

7.  **Waitfornotification** 메서드를 추가 하 여 앱이 주 스레드를 사용 하 여 충돌 방지 없이 알림 허브 라이브러리에서 알림을 받을 수 있도록 합니다.

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

8.  다음 메서드인 **Initnotificationasync ()** 는 초기화 시 Notification hubs 서비스에 응용 프로그램을 등록 합니다. Unity는 프로젝트를 빌드할 수 없으므로 코드는 주석 처리 됩니다. Visual Studio에서 Azure Messaging Nuget 패키지를 가져올 때 주석이 제거 됩니다.

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

9.  알림을 받을 때마다 다음 처리기 **채널\_PushNotificationReceived ()** 가 트리거됩니다. 이 알림은 데스크톱 응용 프로그램에서 이동 된 Azure 테이블 엔터티가 되는 알림을 deserialize 하 고 MR 장면에서 해당 하는 GameObject를 같은 위치로 이동 합니다. 
    
    > [!IMPORTANT]
    > 코드는 Visual Studio 내에서 Nuget 패키지 관리자를 사용 하 여 Unity 프로젝트를 빌드한 후 추가 될 Azure 메시징 라이브러리를 참조 하므로 주석 처리 됩니다. 따라서 Unity 프로젝트는 주석 처리 되지 않은 경우에는 빌드할 수 없습니다. 프로젝트를 빌드한 다음 Unity로 돌아가려면 해당 코드를 **다시 주석** 으로 처리 해야 합니다.

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

11. **계층** 패널에서 **주 카메라** 를 클릭 하 여 해당 속성이 **검사기**에 표시 되도록 합니다.

12. **Scripts** 폴더를 연 상태에서 **notificationreceiver** 스크립트를 선택 하 고 **기본 카메라로**끌어 옵니다. 결과는 다음과 같아야 합니다.

    ![알림 수신기 스크립트를 카메라로 끌어 옵니다.](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Microsoft HoloLens에 대해이를 개발 하는 경우 다음과 같이 **기본 카메라**의 *카메라* 구성 요소를 업데이트 해야 합니다.
    > - 플래그 지우기: 단색
    > - 배경: 검정

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>16 장-UWP에 혼합 현실 프로젝트 빌드

이 장은 이전 프로젝트에 대 한 빌드 프로세스와 동일 합니다. 이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.

1.  **빌드 설정** ( **파일** > **빌드 설정** )으로 이동 합니다.

2.  **빌드 설정** 메뉴에서 **Unity C# 프로젝트***가 선택 (빌드 후이 프로젝트의 스크립트를 편집할 수 있음)를 확인 합니다.

3.  이 작업을 완료 한 후 **빌드**를 클릭 합니다.

    ![프로젝트 빌드](images/AzureLabs-Lab8-99.png)

4.  빌드할 위치를 묻는 메시지를 표시 하는 **파일 탐색기** 창이 표시 됩니다. 왼쪽 위 모서리에서 **새 폴더** 를 클릭 하 여 새 폴더를 만들고 이름을 **작성**합니다.

    ![빌드 폴더 만들기](images/AzureLabs-Lab8-100.png)

    1.  새 **빌드** 폴더를 열고 **새 폴더** 를 한 번 더 사용 하 여 다른 폴더를 만든 다음 이름을 **Nh\_MR\_앱**으로 이름을 추가 합니다.

        ![NH_MR_Apps 폴더 만들기](images/AzureLabs-Lab8-101.png)

    2.  **Nh\_MR\_앱** 을 선택 합니다. **폴더 선택**을 클릭 합니다. 프로젝트를 빌드하는 데 1 분 정도 걸립니다.

5.  빌드를 수행 하면 새 프로젝트의 위치에서 **파일 탐색기** 창이 열립니다.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>17 장-UnityMRNotifHub 솔루션에 NuGet 패키지 추가

> [!WARNING] 
> 다음 NuGet 패키지를 추가 하 고 다음 [챕터](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)에서 코드의 주석 처리를 제거 하면 Unity 프로젝트에서 다시 열 때 코드가 오류를 표시 한다는 점에 주의 하세요. 이전 단계로 돌아가서 Unity 편집기에서 계속 편집 하려는 경우에는 일부 코드에 대 한 설명이 필요 합니다. 그런 다음 Visual Studio로 돌아가서 다시 주석 처리를 제거 합니다. 

혼합 현실 빌드가 완료 되 면 빌드한 mixed reality 프로젝트로 이동 하 고 해당 폴더 내에서 솔루션 파일 (.sln)을 두 번 클릭 하 여 Visual Studio 2017에서 솔루션을 엽니다.
이제 **Windowsazure.servicebus** NuGet 패키지를 추가 해야 합니다. 알림 허브에서 알림을 수신 하는 데 사용 되는 라이브러리입니다.

NuGet 패키지를 가져오려면:

1.  **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭 합니다.

2.  **NuGet 패키지 관리**를 클릭 합니다.

    ![nuget 관리자 열기](images/AzureLabs-Lab8-102.png)

3.  ***찾아보기*** 탭을 선택 하 고 **windowsazure.servicebus**를 검색 합니다.

    ![windows azure 메시징 패키지 찾기](images/AzureLabs-Lab8-103.png)

4.  아래와 같이 결과를 선택 하 고 오른쪽 창에서 **프로젝트**옆에 있는 확인란을 선택 합니다. 그러면 **프로젝트**옆에 있는 확인란에 틱이 포함 되 고, **어셈블리-CSharp** 및 **UnityMRNotifHub** 프로젝트 옆에 있는 확인란과 함께 추가 됩니다.

    ![모든 프로젝트의 tick](images/AzureLabs-Lab8-104.png)

5.  처음에 제공 되는 버전은이 프로젝트와 호환 **되지 않을 수 있습니다** . 따라서 **버전**옆에 있는 드롭다운 메뉴를 클릭 하 고 **버전 0.1.7.9**를 클릭 한 다음 **설치**를 클릭 합니다.

6.  이제 NuGet 패키지를 설치 했습니다. **Notificationreceiver** 클래스에서 입력 한 주석 처리 된 코드를 찾고 주석을 제거 합니다.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>18 장-UnityMRNotifHub 응용 프로그램 편집, NotificationReceiver 클래스

**NuGet 패키지**를 추가한 후에는 **notificationreceiver** 클래스 내에서 일부 코드의 *주석 처리를 제거* 해야 합니다.

여기에는 다음이 포함됩니다.

1. 위쪽의 네임 스페이스:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. **InitNotificationsAsync ()** 메서드 내의 모든 코드는 다음과 같습니다.

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
> 위의 코드에 주석이 포함 되어 있습니다. 해당 주석을 실수로 *주석 처리가 제거* 하지 않았는지 확인 합니다 (!가 있는 경우 코드가 컴파일되지 않음).

3. 그리고 마지막으로 **Channel_PushNotificationReceived** 이벤트는 다음과 같습니다.

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

이러한 주석 처리가 제거을 사용 하 여 저장 한 후 다음 챕터로 이동 합니다.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>19 장-혼합 현실 프로젝트를 스토어 앱에 연결

이제 랩 시작 시에서 만든 스토어 앱에 **혼합 현실** 프로젝트를 연결 해야 합니다.

1.  솔루션을 엽니다.

2.  솔루션 탐색기 패널에서 UWP 앱 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **스토어**로 이동 및 **스토어에 앱 연결**...을 마우스 오른쪽 단추로 클릭 합니다.

    ![저장소 연결 열기](images/AzureLabs-Lab8-105.png)

3.  **응용 프로그램을 Windows 스토어에 연결**이라는 새 창이 표시 됩니다. **다음**을 클릭합니다.

    ![다음 화면으로 이동](images/AzureLabs-Lab8-106.png)

4.  로그인 한 계정과 연결 된 모든 응용 프로그램을 로드 합니다. 계정에 로그인 하지 않은 경우이 페이지 **에 로그인 할 수 있습니다** .

5.  이 자습서의 시작 부분에서 만든 **스토어 앱 이름을** 찾아 선택 합니다. **Next**를 클릭합니다.

    ![상점 이름 찾기 및 선택](images/AzureLabs-Lab8-107.png)

6.  **연결**을 클릭 합니다.

    ![앱 연결](images/AzureLabs-Lab8-108.png)

7.  이제 앱이 스토어 앱에 **연결** 됩니다. 알림을 사용 하도록 설정 하는 데 필요 합니다.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>20 장-UnityMRNotifHub 및 UnityDesktopNotifHub 응용 프로그램 배포

이 장은 두 명의 사용자에 게 더 쉬울 수 있습니다. 즉, 실행 중인 앱을 모두 포함 하 고 컴퓨터 데스크톱에서 실행 하는 앱과 몰입 형 헤드셋 내에서 다른 항목을 포함 합니다.

모던 헤드셋 앱은 장면 (로컬 Gameobject의 위치 변경)에 대 한 변경 내용을 받기 위해 대기 중 이며, 데스크톱 앱은 MR 앱에 공유 되는 로컬 장면 (위치 변경)을 변경 합니다. 수신자가 수신을 시작할 수 있도록 먼저 MR 앱을 배포한 다음 데스크톱 앱을 배포 하는 것이 좋습니다.

로컬 컴퓨터에 **UnityMRNotifHub** 앱을 배포 하려면 다음을 수행 합니다.

1.  **Visual Studio 2017**에서 **UnityMRNotifHub** 앱의 솔루션 파일을 엽니다.

2.  **솔루션 플랫폼**에서 **X86, 로컬 컴퓨터**를 선택 합니다.

3.  **솔루션 구성** 에서 **디버그**를 선택 합니다.

    ![프로젝트 구성 설정](images/AzureLabs-Lab8-109.png)

4.  **빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드.

5.  이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.

로컬 컴퓨터에 **UnityDesktopNotifHub** 앱을 배포 하려면 다음을 수행 합니다.

1.  **Visual Studio 2017**에서 **UnityDesktopNotifHub** 앱의 솔루션 파일을 엽니다.

2.  **솔루션 플랫폼**에서 **X86, 로컬 컴퓨터**를 선택 합니다.

3.  **솔루션 구성** 에서 **디버그**를 선택 합니다.

    ![프로젝트 구성 설정](images/AzureLabs-Lab8-110.png)

4.  **빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드.

5.  이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.

6.  혼합 현실 응용 프로그램을 시작한 다음 데스크톱 응용 프로그램을 시작 합니다.

두 응용 프로그램을 모두 실행 하는 경우 마우스 왼쪽 단추를 사용 하 여 바탕 화면 장면에서 개체를 이동 합니다. 이러한 위치 변경은 로컬로 수행 되 고 serialize 되며 함수 앱 서비스로 전송 됩니다. 그러면 함수 앱 서비스에서 알림 허브와 함께 테이블을 업데이트 합니다. 업데이트를 받으면 알림 허브는 등록 된 모든 응용 프로그램 (이 경우에는 몰입 형 헤드셋 앱)에 업데이트 된 데이터를 직접 전송 합니다. 그러면 들어오는 데이터를 deserialize 하 고 새 위치 데이터를 로컬 개체에 적용 합니다. 장면에서 이동


## <a name="your-finished-your-azure-notification-hubs-application"></a>Azure Notification Hubs 응용 프로그램 완성
 
축 하 합니다. Azure Notification Hubs 서비스를 활용 하 고 앱 간의 통신을 허용 하는 혼합 현실 앱을 빌드 했습니다.
 
![최종 제품 종료](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

Gameobject 색을 변경 하는 방법을 설명 하 고 장면을 표시 하는 다른 앱으로 알림을 보낼 수 있나요?

### <a name="exercise-2"></a>연습 2

Gameobject의 이동을 MR 앱에 추가 하 고 데스크톱 앱에서 업데이트 된 장면을 볼 수 있나요?
