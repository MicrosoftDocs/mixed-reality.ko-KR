---
title: 혼합된 현실 공간 데이터 패키지 작성 도구 설명서
description: 혼합 현실 공간 데이터 Packager를 사용 하 여에 대 한 설명서
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942109"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>혼합된 현실 공간 데이터 패키지 작성 도구 설명서

>[!NOTE]
> 이 도구 및 해당 작업으로 제공 됩니다-됩니다. 모든 예 고 없이 변경 될 수 있습니다 이며 향후 Windows와 호환 되지 않을 수 있습니다 하거나 Windows Mixed Reality HMD 해제 합니다.

## <a name="download"></a>다운로드
 다운로드 [MixedRealitySpatialDataPackager 여기](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>빠른 시작

혼합 현실 공간 데이터 Packager 도구는 PC가 2 단계를 통해 다른 내보내기 및 가져오기 프로세스 하나에서 대상 앱의 공간 데이터를 복사 합니다. 도구를 관리자 권한으로 실행 해야 하 고 가져올 때 기존 공간 데이터를 삭제 합니다. 내보내기 기존 공간 데이터는 그대로 둡니다.

주요 요구 사항 및 제한 사항:

1. 도구를 관리자 권한으로 실행 해야 합니다. 
2. 혼합 현실 포털 안정적이 지 않은 후 도구를 실행 하는 경우에 PC를 다시 시작 해야 합니다.
3. 공간 데이터 버전 불일치 또는 비 호환성 문제가 발생 하는 경우 도구 실행 되지 않습니다.
4. 도구는 가져오기의 공간 데이터를 기존 지워집니다 합니다.
5. 내보내 이전에 의해 백업 된 경우가 아니면 데이터 복원할 수 없는 이전 가져오기 프로세스가 실패 하는 경우
6. 지도 공간 데이터에 대 한 "읽기 전용" 모드에 따라 가져오기 기능의 품질
***

## <a name="mapping-best-practices"></a>매핑 모범 사례

1. 제어판에서 기존 맵을 선택 취소 (설정에는 혼합 현실->-> 환경-> 일반 환경 데이터)
2. 적절 한 추적 및 조명은 유지 관리 하는 것이 하려고 잠긴된 지도 모드를 실행 하는 경우에 대 한 충분 한 조명 확인
3. 가능한 경우 조명 동적 범위 낮게 유지 어두운, 숨겨진 영역 옆에 있는 높은 조명의 영역을 방지 하 여
4. 빈 최소화, textureless 표면은 흰색 벽에 예를 들어 다른 포스터의 범위를 배치
5. 사용자를 이동 하는 등 장면에서 동적 개체 없이 공간 매핑
6. 가져오기 (Insider Preview를 통해 사용 가능)에서 지도 잠그려면
7. 지도 잠금 해제 하 고 저하 품질 추적 및/또는 (조명 또는 개체 레이아웃의 변경) 환경에서 변경 내용이 경우 환경의 다시 검사
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>도우미 스크립트를 사용 하 여 실행 중인 혼합된 현실 공간 데이터 Packager

지도 packager 도구를 실행 하는 MRSpatialPackagerHelperScript.ps1 제공 했습니다. 


스크립트 매개 변수는 아래 정의 됩니다.

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Powershell 스크립트 예제 사용법 및 출력

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>MixedRealityPackager.exe를 사용 하 여 내보내기 하는 방법
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

장치 맵 내보내기 het.mapx 및 sa.mapx 두 mapx 파일 생성 합니다. 내보내기 프로세스 중 모든 공간 앵커 (있는 경우)에 지정된 된 응용 프로그램 및 사용자가 만든 경계를 제외 하 고 제거 됩니다. 원본 패키지 제품군 이름에는 설치 된 기존 응용 프로그램 일치 해야 합니다 또는 exe가 실패 합니다.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>MixedRealityPackager.exe를 사용 하 여 가져오기 방법
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
가져오기 기존 공간 데이터를 삭제 하 여 지정된 된 디렉터리의 데이터로 바꿉니다. 앱 이름 입력에 대 한 공간 앵커는 대상 앱의 패키지 이름을 가져와야 하 고 대상 사용자 SID를 가져온된 공간 앵커에 액세스할 수 있어야 하는 사용자 지정을 지정 합니다. 대상 패키지 제품군 이름 및 Sid 사용자 PC에 대 한 기존 값을 일치 해야 합니다 또는 exe가 실패 합니다.


***
## <a name="error-messages"></a>오류 메시지
또한 오류 아래 오류 메시지와도 함께 HRESULT를 사용 하 여

### <a name="if-there-was-an-error-invalid-arguments"></a>오류가 잘못 된 인수가 발생 한 경우
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>관리자 모드에서 실행 파일 실행 되지 않았습니다 하는 경우
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>활성화 또는 비활성화 드라이버에 오류가 발생 한 경우
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>공간 데이터베이스 버전 유효성 검사 오류가 발생 한 경우
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Import/export 대상 앱에 대해 제공 된 패키지 제품군 이름 유효성 검사 오류가 발생 한 경우
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>사용자 SID를 유효성 검사 오류가 발생 한 경우
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>발생 한 경우 오류와 관련 된 공간 데이터 원본 또는 대상 파일
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>시작 하 고 스펙트럼/SharedRealitySvc의 중단에 관련 된 오류의 경우
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
