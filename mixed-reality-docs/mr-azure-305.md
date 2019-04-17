---
title: MR 및 Azure 305-함수 및 저장소
description: 혼합된 현실 응용 프로그램에서 Azure Storage 및 함수를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 함수, 저장소, hololens, vr, 몰입 형
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598300"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR 및 Azure 305: 함수 및 저장소

![최종 제품-시작](images/AzureLabs-Lab5-00.png)

이 과정에서는 Azure Functions를 사용 하 여 만들고, 혼합된 현실 응용 프로그램에서 Azure Storage 리소스를 사용 하 여 데이터를 저장 하는 방법을 배웁니다.

*Azure Functions* 작은 코드를 실행 하기 위해 개발자를 허용 하는 Microsoft 서비스에 '', Azure에서 functions 됩니다. 다양 한 이점을 가질 수 있는 로컬 응용 프로그램 보다는 클라우드의 작업을 위임 하는 방법을 제공 합니다. *Azure Functions* C를 비롯 한 여러 개발 언어를 지 원하는\#, F\#, Node.js, Java 및 PHP 합니다. 자세한 내용은 참조는 [문서에서는 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)합니다.

*Azure Storage* 는 개발자가 항상 사용 가능한, 보안, 지속형, 확장성 및 중복 되어 있으므로 보험을 사용 하 여 데이터를 저장 하는 Microsoft 클라우드 서비스입니다. 즉, Microsoft를 모든 유지 관리 및 중요 한 문제를 처리 합니다. 자세한 내용은 참조는 [Azure Storage 문서](https://docs.microsoft.com/azure/storage/common/storage-introduction)합니다.

이 과정을 마치면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 몰입 형 헤드셋 응용 프로그램을 갖게 됩니다.

1.  장면 주위 gaze 사용자를 허용 합니다.
2.  사용자 '단추' 3D에서 gazes 때 개체의 생성을 트리거하십시오.
3.  생성 된 개체는 Azure 함수에 의해 선택 됩니다.
4.  각 개체는 생성 된 대로 응용 프로그램의 개체 형식을 저장 한 *Azure File*에 있는 *Azure Storage*합니다.
5.  두 번째로 로드 시 합니다 *Azure 파일* 데이터를 검색 및 재생 응용 프로그램의 이전 인스턴스에서 작업을 생성 하는 데 사용 됩니다.

응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다. 이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다. 혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 합니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 및 Azure 305: 함수 및 저장소</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다. 과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.

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
- Azure 리소스 만들기에 대 한 Azure 계정에 대 한 구독
- Azure 설정 및 데이터 검색에 대 한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전 주의 사항

이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).

## <a name="chapter-1---the-azure-portal"></a>1 장-Azure Portal

사용 하는 **Azure Storage 서비스**를 만들고 구성 해야 합니다는 **저장소 계정** Azure portal에서 합니다.

1.  에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

2.  일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 *저장소 계정*를 클릭 하 고 **Enter**합니다.

    ![azure storage 검색](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.

3.  새 페이지에 대 한 설명을 제공 합니다는 *Azure Storage 계정* 서비스입니다. 선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.

    ![서비스 만들기](images/AzureLabs-Lab5-02.png)

4.  클릭 한 후 **만들기**:

    1.  삽입을 *이름을* 계정의 주의 숫자 및 소문자만이 필드를 허용 합니다.

    2.  에 대 한 *배포 모델*를 선택 **Resource manager**합니다.

    3.  에 대 한 *계정 종류*를 선택 **저장소 (범용 v1)** 합니다.

    4.  확인 합니다 *위치* (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다. 위치는 응용 프로그램은 실행할 지역의 것이 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

    5.  에 대 한 *복제* 선택 **읽기-액세스-지역 중복 저장소 (RA-GRS)** 합니다.

    6.  에 대 한 *성능*를 선택 **표준**합니다.

    7.  둡니다 *보안 전송 필요* 으로 **비활성**합니다.

    8.  선택 된 *구독*합니다.

    9. 선택 된 *리소스 그룹* 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지). 

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    10. 이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.

    11. **만들기**를 선택합니다.

        ![입력된 서비스 정보](images/AzureLabs-Lab5-03.png)

5.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

6.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![azure portal에서 새 알림](images/AzureLabs-Lab5-04.png)

7.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.

    ![리소스로 이동](images/AzureLabs-Lab5-05.png)

8.  클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 이동에서 새 *저장소 계정* 서비스 인스턴스.

    ![액세스 키](images/AzureLabs-Lab5-06.png)

9.  클릭 *선택키가*,이 클라우드 서비스에 대 한 끝점을 표시 합니다. 사용 하 여 *메모장* 또는 유사한 나중에 사용할 키 중 하나를 복사 합니다. 또한 합니다 *연결 문자열* 값을에서 사용 됩니다 합니다 *Azureservice* 나중에 만들 클래스.

    ![연결 문자열 복사](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>2 장-Azure 함수 설정

이제 작성을 **Azure** **함수** Azure 서비스에서.

사용할 수 있는 **Azure Function** 수행 하는 클래식 함수를 사용 하 여 차이 코드에서이 함수는 Azure 계정에 액세스 하려면 자격 증명이 있는 모든 응용 프로그램에서 액세스할 수 있습니다는 거의 모든 작업을 수행 하 합니다.

Azure Function을 만들려면:

1.  사용자 *Azure Portal*, 클릭 **새로 만들기** 왼쪽 위에서 모서리 및 검색할 *함수 앱*, 클릭 **Enter**합니다.

    ![함수 앱 만들기](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.

2.  새 페이지에 대 한 설명을 제공 합니다는 *Azure 함수 앱* 서비스입니다. 선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.

    ![함수 앱 정보](images/AzureLabs-Lab5-09.png)

3.  클릭 한 후 **만들기**:

    1.  제공 된 *앱 이름*합니다. 문자 및 숫자만 사용할 수 여기 (위쪽 또는 아래쪽 사례 허용 됨).

    2.  선호 하 *구독*합니다.

    3. 선택 된 *리소스 그룹* 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지). 

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.

    4.  이 연습에서는 선택 *Windows* 으로 선택한 **OS**합니다.

    5.  선택 *소비 계획* 에 대 한 합니다 **호스팅 계획**합니다.

    6.  확인 합니다 *위치* (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다. 위치는 응용 프로그램은 실행할 지역의 것이 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다. 최적의 성능을 위해 저장소 계정과 동일한 영역을 선택 합니다.

    7.  에 대 한 *저장소*를 선택 **사용 하 여 기존**를 찾아 다음 드롭다운 메뉴를 사용 하 여 이전에 만든된 저장소입니다.

    8.  둡니다 *Application Insights* 이 연습에 대 한 해제 합니다.

        ![입력된 함수 앱 세부 정보](images/AzureLabs-Lab5-10.png)

4.  **만들기** 단추를 클릭합니다.

5.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

6.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![새 azure portal 알림](images/AzureLabs-Lab5-11.png)

7.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다. 

    ![리소스 함수 앱으로 이동](images/AzureLabs-Lab5-12.png)

8.  클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 이동에서 새 *함수 앱* 서비스 인스턴스.

9.  에 *함수 앱* 대시보드를 위로 마우스를 가져가서 *함수*를 왼쪽에서 패널 내에서 발견 하 고 클릭 합니다 **+ (더하기)** 기호.

    ![새 함수 만들기](images/AzureLabs-Lab5-13.png)

10. 다음 페이지에서 확인 **Webhook + API** 을 선택 하면 한 *언어를 선택* 선택 **CSharp**처럼이 자습서에 사용 된 언어 됩니다. 마지막으로,를 클릭 합니다 **이 함수 만들기** 단추입니다.

    ![웹 후크 csharp 선택](images/AzureLabs-Lab5-14.png)

11. 코드 이동 되어야 합니다 (run.csx) 페이지 그렇지 않은 경우 왼쪽 패널에 있는 함수 목록에서 새로 만든된 함수를 클릭 합니다.

    ![새 함수 열기](images/AzureLabs-Lab5-15.png)

12. 함수에 다음 코드를 복사 합니다. 이 함수는 0과 호출 될 때 2 사이의 임의의 정수를 반환 하기만 하면 됩니다. 맨 위에 붙여넣을 자유롭게, 기존 코드에 대 한 걱정 하지 않습니다.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. **저장**을 선택합니다.

14. 결과 아래 이미지와 같이 표시 됩니다.

15. 클릭할 **함수 URL 가져오기** 숙지 합니다 *끝점* 표시 합니다. 에 삽입 해야 합니다 *Azureservice* 이 과정의 뒷부분에서 만들 클래스입니다.

    ![함수 끝점 가져오기](images/AzureLabs-Lab5-16.png)

    ![함수 끝점 가져오기](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

설정 하 고 혼합된 현실 몰입 형 헤드셋을 테스트 합니다.

> [!NOTE]
> 해야 **되지** 이 과정에 대 한 동작 컨트롤러 필요 합니다. 몰입 형 헤드셋 설정만 지원에 필요한 경우 하세요 [문서를 설정 하는 혼합된 현실 방문](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.

1.  Unity를 열고 클릭 **새로 만들기**합니다.

    ![새 unity 프로젝트 만들기](images/AzureLabs-Lab5-17.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. 삽입 **MR_Azure_Functions**합니다. 프로젝트 형식 설정 되어 있는지 확인 **3D**합니다. 설정 된 *위치* 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![새 unity 프로젝트에 이름을 부여합니다](images/AzureLabs-Lab5-18.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집할* > *기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![스크립트 편집기로 visual studio 설정](images/AzureLabs-Lab5-19.png)

4.  이동한 다음 **파일 > 빌드 설정** 플랫폼 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환** 단추입니다.

    ![uwp 플랫폼 전환](images/AzureLabs-Lab5-20.png)

5.  로 이동 **파일 > 빌드 설정** 되어 있는지 확인 합니다.

    1. **장치를 대상** 로 설정 된 **모든 장치**합니다.

        > Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.

    2. **빌드 형식** 로 설정 된 **D3D**

    3. **SDK** 로 설정 된 **가장 최근에 설치 된**

    4. **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**

    5. **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**

    6. 장면 저장 하 고 빌드에 추가 합니다.

        1.  선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.

            ![열기 장면 추가](images/AzureLabs-Lab5-21.png)

        2.  새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.

            ![백그라운드에서 폴더 만들기](images/AzureLabs-Lab5-22.png)

        3.  새로 만든 열 **장면** 폴더를 선택한 다음는 **파일 이름:** 텍스트 필드에 입력 **FunctionsScene**, 키를 누릅니다 **저장**합니다.

            ![함수 장면 저장](images/AzureLabs-Lab5-23.png)

6.  설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.

    ![함수 장면 저장](images/AzureLabs-Lab5-24.png)

7.  에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한.

    ![플레이어 설정 관리자에서](images/AzureLabs-Lab5-25.png)

8.  이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1.  에 **기타 설정** 탭:

        1.  **스크립팅 런타임 버전** 있어야 **실험적** (.NET 4.6 동등), 편집기를 다시 시작 해야를 트리거하는 합니다.
        2.  **백 엔드를 스크립팅** 있어야 **.NET**
        3.  **API 호환성 수준** 있어야 **.NET 4.6**

    2.  내 합니다 **게시 설정** 탭의 **기능**, 확인:
        
        -  **InternetClient**

            ![집합 기능](images/AzureLabs-Lab5-26.png)

    3.  패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK** 추가 됩니다.

        ![xr 하이 설정](images/AzureLabs-Lab5-27.png)

9.  년대 *빌드 설정* *Unity C# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.

    ![눈금 c# 프로젝트](images/AzureLabs-Lab5-28.png)

10.  빌드 설정 창을 닫습니다.

11. 장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).

## <a name="chapter-4---setup-main-camera"></a>4 장-주 카메라 설정

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드에 바로 계속, 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage),으로 프로젝트로 가져오는 것을 [사용자 지정 패키지](https://docs.unity3d.com/Manual/AssetPackages.html)합니다. 다음 장에서에서 Dll도 포함 됩니다. 가져온 후 계속 진행 [7 장](#chapter-7---create-the-azureservices-class)합니다. 

1.  에 *계층 패널*, 라는 개체를 보면 **주 카메라**, "내부" 응용 프로그램 되 면이 개체에 "head" 관점을 나타냅니다.

2.  사용자 앞에 Unity 대시보드를 선택 합니다 **주 카메라 GameObject**합니다. 합니다 *검사기 패널* (일반적으로 대시보드 내에서 오른쪽에 있음)의 다양 한 구성 요소에 표시 됩니다 *GameObject*를 사용 하 여 *변환* 맨 뒤에 *카메라*, 및 기타 구성 요소입니다. 위치가 올바르게 하므로 주 카메라의 변환을 다시 설정 해야 합니다.

3.  이렇게 하려면 선택 합니다 **기어** 카메라의 옆에 있는 아이콘 *변환* 구성 요소를 선택한 **재설정**합니다.

    ![변환 다시 설정](images/AzureLabs-Lab5-29.png)

4.  그런 다음 업데이트를 **변환** 모양 구성 요소:

    |         |    변환-위치   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 변환-회전 |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 변환-확장 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![카메라 변환 집합](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>5 장-Unity 장면 설정

1.  빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*아래에 있는 **3D 개체**, 추가 **평면**합니다.

    ![새 평면 만들기](images/AzureLabs-Lab5-31.png)

2.  사용 하 여 합니다 **평면** 선택한 개체에서 다음 매개 변수를 변경 합니다 *검사기 패널*:

    |       | 변환-위치 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 변환-확장 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![집합 평면 위치 및 크기 조정](images/AzureLabs-Lab5-32.png)

    ![면과 카메라 장면 보기로](images/AzureLabs-Lab5-33.png)

3.  빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*아래에 있는 **3D 개체**, 추가 **큐브**합니다.

    1.  큐브 이름 바꾸기 **GazeButton** (선택한 큐브를 사용 하 여 F2 키를 누릅니다 '').

    2.  다음 매개 변수를 변경 합니다 *검사기 패널*:

        |       | 변환-위치 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![집합 게이즈 단추 변환](images/AzureLabs-Lab5-34.png)

        ![장면 보기로 단추가 gaze](images/AzureLabs-Lab5-35.png)

    3.  클릭 합니다 **태그** 드롭다운 단추를 클릭 **태그 추가** 열려는 합니다 *태그 및 계층 창*.

        ![새 태그 추가](images/AzureLabs-Lab5-36.png)

        ![더하기 선택](images/AzureLabs-Lab5-37.png)

    4.  선택 합니다 **+ (더하기)** 단추를 및 합니다 *새 태그 이름* 필드를 입력 합니다 **GazeButton**, 키를 누릅니다 **저장**합니다.

        ![새 태그 이름](images/AzureLabs-Lab5-38.png)

    5.  클릭 합니다 **GazeButton** 개체를 *계층 패널*, 및를 *검사기 패널*, 새로 만든 할당 **GazeButton** 태그입니다.

        ![응시 단추 새 태그 할당](images/AzureLabs-Lab5-39.png)

4.  마우스 오른쪽 단추로 클릭 합니다 **GazeButton** 개체에서 *계층 패널*, 추가 **빈 GameObject** (으로 추가 됩니다.는 *자식* 개체)입니다.

5.  새 개체를 선택 하 고 이름을 **ShapeSpawnPoint**합니다.

    1.  다음 매개 변수를 변경 합니다 *검사기 패널*:

        |       | 변환-위치 |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![생성 포인트 변환 셰이프를 업데이트 합니다.](images/AzureLabs-Lab5-40.png)

        ![셰이프 생성 장면 관점](images/AzureLabs-Lab5-41.png)

6.  다음을 만듭니다는 **3D 텍스트** Azure 서비스의 상태에 피드백을 제공 하는 개체입니다.

    마우스 오른쪽 단추로 클릭 합니다 **GazeButton** 계층 구조에서 패널 다시 추가한를 **3D 개체 > 3D 텍스트** 개체를 *자식*합니다.

    ![새 3D 텍스트 개체 만들기](images/AzureLabs-Lab5-42.png)

7.  이름 바꾸기는 **3D 텍스트** 개체를 **AzureStatusText**합니다.

8.  변경 된 **AzureStatusText** 다음과 같이 변환 개체:

    |       | 변환-위치 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | 변환-확장 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > 이 수정 될 때 처럼 centre 해제 되도록 표시 되는 경우 걱정 하지 마십시오는 텍스트 메시 아래 구성 요소를 업데이트 합니다.

9.  변경 된 **텍스트 메시** 에 맞게 구성 요소는 아래:

    ![집합 텍스트 메시 구성 요소](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > 여기서 선택한 색은 16 진수 색: **000000FF**하지만 자유롭게 선택할 사용자 고유의만 읽을 수 있는지 확인 합니다.

10. 이제 계층 패널 구조에 다음과 같이 표시 됩니다.

    ![장면 뷰에서 텍스트 메시](images/AzureLabs-Lab5-43b.png)

10. 이제 장면 다음과 같이 표시 됩니다.

    ![장면 뷰에서 텍스트 메시](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>6 장-Unity에 대 한 Azure 저장소 가져오기

Azure Storage for Unity 사용 (자체는.Net 용 Azure SDK를 활용 함). 알아볼 수 있습니다이에 대 한 합니다 [Unity 문서에 대 한 Azure Storage](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)합니다.

플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다. 이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.

사용자 고유의 프로젝트에 SDK를 가져오려면 최신 다운로드 했는지 확인 [GitHub에서 '.unitypackage'](https://aka.ms/azstorage-unitysdk)합니다. 그런 다음 다음을 수행 합니다.

1.  추가 된 **.unitypackage** Unity 사용 하 여 파일을 **자산 > 패키지 가져오기 > 사용자 지정 패키지** 메뉴 옵션입니다.

2.  에 **Unity 패키지 가져오기** 팝업에서 선택할 수 있는 아래에 있는 모든 상자 **플러그 인* > * 저장소 * * 합니다. 이 과정에 대 한 필요 하지 않을 때 나머지 작업은 모두 선택 취소 합니다.

    ![패키지 가져오기](images/AzureLabs-Lab5-45.png)

3.  클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.

4.  로 이동 합니다 *저장소* 아래에 폴더 *플러그 인*프로젝트 보기 및 다음 플러그 인 선택 *만*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![모든 플랫폼을 선택 취소](images/AzureLabs-Lab5-46.png)

5.  사용 하 여 *이러한 특정 플러그 인* 선택 하면 **의 선택을 취소** *Any 플랫폼* 고 **의 선택을 취소** *WSAPlayer* 누른 **적용**합니다.

    ![플랫폼 dll를 적용 합니다.](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > 이러한 특정 플러그 인 Unity 편집기에서 사용할 수만 표시 됩니다. Unity에서 프로젝트를 내보낸 후 사용할 WSA 폴더에 같은 플러그 인의 다양 한 버전 때문입니다.

6.  에 *저장소* 플러그 인 폴더에만 선택 합니다.

    -   Microsoft.Data.Services.Client

        ![집합에 dll에 대 한 처리](images/AzureLabs-Lab5-48.png)

7.  확인 합니다 **없는 프로세스** 상자에 *플랫폼 설정* 클릭 **적용**합니다.

    ![없는 처리 적용](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > 표시 됩니다이 플러그 인 "처리 하지 않음" Unity 어셈블리 패 처가이 플러그 인을 처리 하는 데 문제가 있어. 플러그 인 처리 되지 않았습니다. 경우에 계속 작동 합니다.

## <a name="chapter-7---create-the-azureservices-class"></a>7-장 Azureservice 클래스 만들기

첫 번째 클래스를 만드는 것은 *Azureservice* 클래스입니다.

합니다 *Azureservice* 클래스에 대 한 지불 해야 합니다.

-   Azure 계정 자격 증명을 저장 합니다.

-   Azure 앱 함수를 호출 합니다.

-   업로드 및 Azure 클라우드 저장소에서 데이터 파일의 다운로드 합니다.

이 클래스 만들려면:

1.  마우스 오른쪽 단추로 클릭 합니다 *Asset* [프로젝트] 패널에 있는 **만들기 > 폴더**합니다. 폴더의 이름을 **스크립트**합니다.

    ![새 폴더 만들기](images/AzureLabs-Lab5-50.png)

    ![스크립트 폴더를 호출 합니다.](images/AzureLabs-Lab5-51.png)

2.  열려는 방금 만든 폴더를 두 번 클릭 합니다.

3.  폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다. 스크립트를 호출할 *Azureservice*합니다.

4.  두 번 클릭 하 여 새 *Azureservice* 클래스를 사용 하 여 *Visual Studio*합니다.

5.  맨 위에 다음 네임 스페이스를 추가 합니다 *Azureservice*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  내부의 다음 검사기 필드를 추가 합니다 *Azureservice* 클래스:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  그런 다음 내에서 다음 멤버 변수를 추가 합니다 *Azureservice* 클래스:

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > 바꿔야 합니다 *끝점* 하 고 *연결 문자열* 값과 값에 Azure storage에서 Azure Portal에서 찾을 수

8.  에 대 한 코드 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다. 이러한 메서드는 클래스를 초기화할 때 호출 됩니다.

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > 에 대 한 코드를 입력 했습니다 *CallAzureFunctionForNextShape()* 에 [향후 장](#chapter-10---completing-the-AzureServices-class)합니다.

9.  삭제 합니다 *update ()* 메서드가이 클래스는 사용 하지 것입니다.

10. Visual Studio에서 변경 내용을 저장 하 고 Unity로 돌아와서 키를 누릅니다.

11. 클릭 하 고 끌어서 합니다 *Azureservice* Scripts 폴더에서 클래스를 주 카메라 개체에는 *계층 패널*합니다.

12. 주 카메라를 선택 하 고 가져오는 합니다 **AzureStatusText** 아래에서 자식 개체를 **GazeButton** 개체를 내에 배치 합니다 **AzureStatusText** 참조 대상 필드를 *검사기*에 대 한 참조를 제공 하는 *Azureservice* 스크립트입니다.

    ![azure 상태 텍스트 참조 대상 할당](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>8-장 ShapeFactory 클래스 만들기

를 만들려면 다음 스크립트를 *ShapeFactory* 클래스입니다. 이 클래스의 역할은 요청을 만들면 새 셰이프를에서 만든 모양의 기록을 유지 하는 *모양 기록 목록*합니다. 셰이프를 만들 때마다를 *셰이프 기록 목록* 에서 업데이트 되는 *AzureService* 클래스를 저장 한 다음에 *Azure Storage*. 응용 프로그램이 시작 되 면 저장 된 파일에서 발견 되 면 프로그램 *Azure Storage*의 *셰이프 기록 목록* 를 검색 하 고 재생을 사용 하 여는 **3D 텍스트** 개체를 제공 하 생성 된 모양 인지 여부 또는 새 저장소에서입니다.

이 클래스를 만들려면:

1.  로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.

2.  폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다. 스크립트를 호출할 *ShapeFactory*합니다.

3.  두 번 클릭 하 여 새 *ShapeFactory* 스크립트를 사용 하 여 열고 *Visual Studio*합니다.

4.  확인 합니다 *ShapeFactory* 클래스는 다음 네임 스페이스를 포함 합니다.

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  아래에 표시 된 변수를 추가 합니다 *ShapeFactory* 바꾸고 클래스는 *start ()* 및 *Awake()* 아래와 함수:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  합니다 *CreateShape()* 메서드를 기반으로 제공 된 기본 도형 생성 *정수* 매개 변수입니다. 부울 매개 변수 저장소에서 현재 생성된 모양 인지 여부를 지정 하는 데 사용 되었거나 새. 다음 코드를 배치 하 *ShapeFactory* 이전 메서드 아래 클래스:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Unity를 반환 하기 전에 Visual Studio에서 변경 내용을 저장 해야 합니다.

8.  다시 Unity 편집기에서 클릭 하 고 끌어서 합니다 *ShapeFactory* 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체를 *계층 패널*.

9. 선택한 주 카메라를 사용 하 여 확인할 수 있습니다 합니다 *ShapeFactory* 스크립트 구성 요소가 누락 되었습니다 합니다 *Spawn 지점* 참조 합니다. 이 문제를 해결 하려면 끌어서를 **ShapeSpawnPoint** 에서 개체를 *계층 패널* 에 **Spawn 지점** 참조 대상입니다.

    ![집합 셰이프 팩터리 참조 대상](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>9-장 게이즈 클래스 만들기

만들어야 하는 마지막 스크립트를 *Gaze* 클래스입니다.

이 클래스는 생성을 담당를 **Raycast** 는 프로젝션 앞으로 사용자를 보고 하는 개체를 검색 하는 주 카메라에서. 사용자를 보고 하는 경우를 식별 하는 Raycast 해야이 경우는 **GazeButton** 장면에 개체 및 동작을 트리거합니다.

이 클래스 만들려면:

1.  로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.

2.  프로젝트 패널을 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다. 스크립트를 호출할 *Gaze*합니다.

3.  두 번 클릭 하 여 새 *Gaze* 스크립트를 사용 하 여 열고 *Visual Studio입니다.*

4.  다음 네임 스페이스 스크립트의 맨 위에 있는 포함 되는지 확인 합니다.

    ```csharp
        using UnityEngine;
    ```

5.  그런 다음 내에서 다음 변수를 추가 합니다 *Gaze* 클래스:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> 편집할 수 있으려면 이러한 변수 중 일부는 *편집기*합니다.

6.  에 대 한 코드를 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다.

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  와 함께 시작, 커서 개체를 만드는 다음 코드를 추가 합니다 *update ()* 이 GazeEnabled 부울 설정/해제 되 고 함께 Raycast 메서드를 실행 하는 메서드:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. 다음 추가 합니다 *UpdateRaycast()* 메서드는 Raycast 프로젝트는 적중 횟수 대상을 검색 합니다.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

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

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. 마지막으로 추가 합니다 *ResetFocusedObject()* 메서드 GazeButton 개체에 현재 색을 나타내는 여부 새 셰이프를 만들기가 있는지 여부를 설정/해제 됩니다.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Visual Studio에서 Unity를 반환 하기 전에 변경 내용을 저장 합니다.

11.  클릭 하 고 끌어서 합니다 *Gaze* Scripts 폴더에서 클래스를 **주 카메라** 개체를 *계층 패널*합니다.

## <a name="chapter-10---completing-the-azureservices-class"></a>10 장-Azureservice 클래스를 완료 합니다.

현재 위치에서 다른 스크립트를 사용 하 여 이제 수 있기 *완전* 는 *Azureservice* 클래스입니다. 이 통해 수행할 수 됩니다.

1.  라는 새 메서드 추가 *CreateCloudIdentityAsync()*, Azure와의 통신에 필요한 인증 변수를 설정할 수 있습니다.

    > 이 메서드는 또한 셰이프 목록을 포함 하는 이전에 저장 된 파일의 존재 여부 확인 됩니다.
    >
    > **파일이 있으면**, 사용자 사용 하지 않도록 설정 됩니다 *Gaze*에 저장 된 모양의 패턴에 따라 셰이프 작성, 트리거 및 합니다 **Azure Storage 파일**합니다. 사용자와이 볼 수는 **텍스트 메시** 표시 하면 'Storage' 또는 'New' 셰이프 원점에 따라 합니다.
    >
    > **파일이 없는 경우**를 활성화 합니다 *Gaze*를 보면 모양을 만들 수 있도록를 **GazeButton** 장면에서 개체.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  내에서 다음 코드 조각은는 *start ()* 에 전화를 걸 여기서; 메서드는 *CreateCloudIdentityAsync()* 메서드. 현재 복사 자유롭게 *start ()* 메서드를 사용 하 여는 아래:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  메서드에 대 한 코드를 입력 *CallAzureFunctionForNextShape()* 합니다. 이전에 만든 사용할지 *Azure 함수 앱* shape 인덱스를 요청 합니다. 새 셰이프 수신 되 면이 메서드는 셰이프를 보냅니다는 *ShapeFactory* 장면에 새 셰이프를 만드는 클래스입니다. 아래 코드의 본문을 완료 하는 데 *CallAzureFunctionForNextShape()* 합니다.

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  에 저장 셰이프 기록 목록에 저장 된 정수를 연결 하 여 문자열을 만드는 메서드를 추가 하면 *Azure Storage 파일*합니다.

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  에 있는 파일에 저장 된 텍스트를 검색 하는 메서드를 추가 하 *Azure Storage File* 및 *deserialize* 목록에 합니다.

6.  이 프로세스가 완료 되 면 메서드 다시 사용 하도록 설정 합니다 게이즈 장면에 사용자 추가 셰이프를 추가할 수 있도록 합니다.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Visual Studio에서 Unity를 반환 하기 전에 변경 내용을 저장 합니다.

## <a name="chapter-11---build-the-uwp-solution"></a>11 장-UWP 솔루션 빌드

빌드 프로세스를 시작 합니다.

1.  로 이동 **파일 > 빌드 설정**합니다.

    ![앱 빌드](images/AzureLabs-Lab5-54.png)

2.  **빌드**를 클릭합니다. Unity가 시작 됩니다는 *파일 탐색기* 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다. 해당 폴더를 이제 만들고 이름을 *앱*합니다. 사용 하 여 다음 합니다 *앱* 폴더 선택 키를 눌러 **폴더 선택**합니다.

3.  Unity 프로젝트를 빌드할 예정 된 *앱* 폴더입니다.

4.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 *파일 탐색기* 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.

## <a name="chapter-12---deploying-your-application"></a>12 장-응용 프로그램 배포

응용 프로그램을 배포 합니다.

1.  로 이동 합니다 *앱* 에서 만든 폴더를 [장의 마지막](#chapter-11---build-the-uwp-solution)합니다. 파일을 두 번 클릭 해야 하는 '.sln' 확장을 사용 하 여 앱 이름으로 표시 됩니다 하므로, 내에서 엽니다 *Visual Studio*합니다.

2.  에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.

3.  에 **솔루션 구성** 선택 **디버그**합니다.

    > Microsoft HoloLens 알 수 있습니다 것이 더 쉽게 *원격 컴퓨터*컴퓨터로 테더 링 없습니다 있도록 합니다. 그러나 또한 다음을 수행 해야 합니다.
    > - 알고는 **IP 주소** 내에서 찾을 수 있는 여 HoloLens의는 *설정 > 네트워크 및 인터넷 > Wi-fi > 고급 옵션*; IPv4는 주소를 사용 해야 합니다. 
    > - 확인 **개발자 모드** 됩니다 **에**에; *설정 > 업데이트 및 보안 > 개발자를 위한*합니다.

    ![솔루션 배포](images/AzureLabs-Lab5-55.png)

4.  로 이동 합니다 **빌드** 메뉴를 클릭 **솔루션 배포** 컴퓨터에 응용 프로그램을 테스트용으로 로드 하려면.

5.  앱 시작 하 고 테스트 준비가 설치 된 앱 목록에 나타나야 합니다.

## <a name="your-finished-azure-functions-and-storage-application"></a>Azure Functions 및 저장소 응용 프로그램 완료

축, Azure Functions와 Azure Storage 서비스를 활용 하는 혼합된 현실 앱을 작성 합니다. 앱 저장 된 데이터 및 해당 데이터를 기반으로 하는 작업을 제공 하는 일을 할 수 있습니다.

![최종 제품-종료](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

지점 및 지점에서 생성 된 개체를 생성 하는 레코드를 두 번째 생성을 만듭니다. 데이터 파일을 로드 하는 경우 원래 만들어진 위치에서 생성 되는 셰이프를 재생 합니다.

### <a name="exercise-2"></a>연습 2

다시 열 때마다 필요 하지 않고 앱을 다시 시작 하는 방법을 만듭니다. **백그라운드에서 로드** 좋은 장소에 시작 됩니다. 그 후에 저장 된 목록을 지울 것인지 방법을 만들어야 *Azure Storage*앱에서 쉽게 다시 설정할 수 있도록 합니다. 
