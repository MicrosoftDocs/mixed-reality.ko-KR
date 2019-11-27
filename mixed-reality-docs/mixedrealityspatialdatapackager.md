---
title: 혼합 현실 공간 데이터 포장기 설명서
description: 혼합 현실 공간 데이터 포장기 사용에 대 한 설명서
author: alfred-msft
ms.author: yuripek
ms.date: 05/16/2019
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager, MixedRealitySpatialDataPackager
ms.openlocfilehash: 3beb8f9168bfb6fd921d6d5c1eb6d250c70a714d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539685"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>혼합 현실 공간 데이터 포장기 설명서

>[!NOTE]
> 이 도구 및 해당 작업은 있는 그대로 제공 됩니다. 이는 아무런 공지 없이 변경 될 수 있으며 이후 Windows 또는 Windows Mixed Reality HMD 릴리스와 호환 되지 않을 수 있습니다.

## <a name="download"></a>다운로드
 [여기에서 MixedRealitySpatialDataPackager](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip) 다운로드

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능과</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>혼합 현실 공간 데이터 패키지 작성</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>빠른

혼합 현실 공간 데이터 포장기 도구는 두 단계 내보내기 및 가져오기 프로세스를 통해 대상 앱의 공간 데이터를 한 PC에서 다른 PC로 복사 합니다. 이 도구는 관리자 권한으로 실행 해야 하며 가져올 때 기존 공간 데이터를 삭제 해야 합니다. 내보내기는 기존 공간 데이터를 그대로 유지 합니다.

주요 요구 사항 및 제한 사항:

1. 도구는 관리자 권한으로 실행 해야 합니다. 
2. 도구를 실행 한 후 혼합 현실 포털이 불안정 한 경우 PC를 다시 시작 해야 할 수 있음
3. 공간 데이터 버전 불일치 또는 비호환 문제가 발생할 때 도구가 실행 되지 않습니다.
4. 가져오기에서 기존 공간 데이터를 지웁니다.
5. 가져오기 프로세스가 실패 하는 경우 이전 데이터를 이전에 내보내서 백업 하지 않으면 복원할 수 없습니다.
6. 공간 지도 데이터에 대 한 "읽기 전용" 모드의 가져오기 기능 품질
***

## <a name="mapping-best-practices"></a>매핑 모범 사례

1. 제어판에서 기존 맵 지우기 (설정-> 혼합 현실-> 환경-> 환경 데이터 지우기)
2. 적절 한 추적을 위한 충분 한 조명이 있는지 확인 하 고 잠긴 맵 모드를 실행 하는 경우 동일한 조명 유지 관리 시도
3. 가능 하면 짙은 그림자 영역 옆에 높은 조명 영역을 방지 하 여 조명 동적 범위를 낮게 유지 합니다.
4. 비어 있는 textureless 서피스를 최소화 합니다. 예를 들어, 흰색 벽에 다른 포스터의 범위를 둡니다.
5. 장면에서 이동 하는 것과 같은 동적 개체 없이 공간 매핑
6. 가져올 때 맵 잠금 (Insider Preview를 통해 사용 가능)
7. 지도의 잠금을 해제 하 고 품질이 저하 되거나 환경에서 변경 된 경우 (개체 레이아웃의 조명 또는 변경) 환경을 다시 검사 합니다.
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>부록 스크립트를 사용 하 여 혼합 현실 공간 데이터 패키지 실행

Microsoft는 map 패키지 작성 도구를 실행 하는 MRSpatialPackagerHelperScript를 제공 했습니다. 


스크립트 매개 변수는 아래에 정의 되어 있습니다.

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

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Powershell 스크립트 예제 사용법 및 출력

.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName 관리자-모드 내보내기-MapxPath D:\temp\-LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>MixedRealityPackager를 사용 하 여 내보내는 방법
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

Maps에서 맵 내보내기는 두 개의 mapx 파일 (. mapx 및 sa. mapx)을 생성 합니다. 내보내기 프로세스 중에 지정 된 앱과 사용자가 만든 경계 (있는 경우)를 제외 하 고 모든 공간 앵커가 제거 됩니다. 원본 패키지 제품군 이름이 기존에 설치 된 앱과 일치 해야 합니다. 그렇지 않으면 exe가 실패 합니다.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>MixedRealityPackager를 사용 하 여 가져오는 방법
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
가져오기는 기존 공간 데이터를 삭제 하 고 지정 된 디렉터리의 데이터로 바꿉니다. 앱 이름 입력은 공간 앵커를 가져올 대상 앱의 패키지 이름을 지정 하 고, 대상 사용자 SID는 가져온 공간 앵커에 대 한 액세스 권한이 있어야 하는 사용자를 지정 합니다. 대상 패키지 제품군 이름 및 사용자 Sid는 PC의 기존 값과 일치 해야 합니다. 그렇지 않으면 exe가 실패 합니다.


***
## <a name="error-messages"></a>오류 메시지
또한 오류 아래의 오류 메시지도 HRESULT와 함께 제공 됩니다.

### <a name="if-there-was-an-error-invalid-arguments"></a>오류 인수가 잘못 된 경우
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>실행 파일이 관리자 모드에서 실행 되지 않은 경우
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>드라이버를 사용 하거나 사용 하지 않도록 설정 하는 동안 오류가 발생 한 경우
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>공간 데이터베이스 버전의 유효성을 검사 하는 동안 오류가 발생 한 경우
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>대상 가져오기/내보내기 앱에 대해 제공 된 패키지 패밀리 이름의 유효성을 검사 하는 동안 오류가 발생 한 경우
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>사용자 SID의 유효성을 검사 하는 동안 오류가 발생 한 경우
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>대상 또는 원본 공간 데이터 파일과 관련 된 오류가 발생 한 경우
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>스펙트럼/SharedRealitySvc 시작 및 중지와 관련 된 오류가 발생 한 경우
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
