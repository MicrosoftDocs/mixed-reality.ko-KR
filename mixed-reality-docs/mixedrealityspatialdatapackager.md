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
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="cd773-104">혼합된 현실 공간 데이터 패키지 작성 도구 설명서</span><span class="sxs-lookup"><span data-stu-id="cd773-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="cd773-105">이 도구 및 해당 작업으로 제공 됩니다-됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="cd773-106">모든 예 고 없이 변경 될 수 있습니다 이며 향후 Windows와 호환 되지 않을 수 있습니다 하거나 Windows Mixed Reality HMD 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="cd773-107">다운로드</span><span class="sxs-lookup"><span data-stu-id="cd773-107">Download</span></span>
 <span data-ttu-id="cd773-108">다운로드 [MixedRealitySpatialDataPackager 여기](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="cd773-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="cd773-109">빠른 시작</span><span class="sxs-lookup"><span data-stu-id="cd773-109">Quickstart</span></span>

<span data-ttu-id="cd773-110">혼합 현실 공간 데이터 Packager 도구는 PC가 2 단계를 통해 다른 내보내기 및 가져오기 프로세스 하나에서 대상 앱의 공간 데이터를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="cd773-111">도구를 관리자 권한으로 실행 해야 하 고 가져올 때 기존 공간 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="cd773-112">내보내기 기존 공간 데이터는 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="cd773-113">주요 요구 사항 및 제한 사항:</span><span class="sxs-lookup"><span data-stu-id="cd773-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="cd773-114">도구를 관리자 권한으로 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="cd773-115">혼합 현실 포털 안정적이 지 않은 후 도구를 실행 하는 경우에 PC를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="cd773-116">공간 데이터 버전 불일치 또는 비 호환성 문제가 발생 하는 경우 도구 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="cd773-117">도구는 가져오기의 공간 데이터를 기존 지워집니다 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="cd773-118">내보내 이전에 의해 백업 된 경우가 아니면 데이터 복원할 수 없는 이전 가져오기 프로세스가 실패 하는 경우</span><span class="sxs-lookup"><span data-stu-id="cd773-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="cd773-119">지도 공간 데이터에 대 한 "읽기 전용" 모드에 따라 가져오기 기능의 품질</span><span class="sxs-lookup"><span data-stu-id="cd773-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="cd773-120">매핑 모범 사례</span><span class="sxs-lookup"><span data-stu-id="cd773-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="cd773-121">제어판에서 기존 맵을 선택 취소 (설정에는 혼합 현실->-> 환경-> 일반 환경 데이터)</span><span class="sxs-lookup"><span data-stu-id="cd773-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="cd773-122">적절 한 추적 및 조명은 유지 관리 하는 것이 하려고 잠긴된 지도 모드를 실행 하는 경우에 대 한 충분 한 조명 확인</span><span class="sxs-lookup"><span data-stu-id="cd773-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="cd773-123">가능한 경우 조명 동적 범위 낮게 유지 어두운, 숨겨진 영역 옆에 있는 높은 조명의 영역을 방지 하 여</span><span class="sxs-lookup"><span data-stu-id="cd773-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="cd773-124">빈 최소화, textureless 표면은 흰색 벽에 예를 들어 다른 포스터의 범위를 배치</span><span class="sxs-lookup"><span data-stu-id="cd773-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="cd773-125">사용자를 이동 하는 등 장면에서 동적 개체 없이 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="cd773-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="cd773-126">가져오기 (Insider Preview를 통해 사용 가능)에서 지도 잠그려면</span><span class="sxs-lookup"><span data-stu-id="cd773-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="cd773-127">지도 잠금 해제 하 고 저하 품질 추적 및/또는 (조명 또는 개체 레이아웃의 변경) 환경에서 변경 내용이 경우 환경의 다시 검사</span><span class="sxs-lookup"><span data-stu-id="cd773-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="cd773-128">도우미 스크립트를 사용 하 여 실행 중인 혼합된 현실 공간 데이터 Packager</span><span class="sxs-lookup"><span data-stu-id="cd773-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="cd773-129">지도 packager 도구를 실행 하는 MRSpatialPackagerHelperScript.ps1 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="cd773-130">스크립트 매개 변수는 아래 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-130">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="cd773-131">Powershell 스크립트 예제 사용법 및 출력</span><span class="sxs-lookup"><span data-stu-id="cd773-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="cd773-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span><span class="sxs-lookup"><span data-stu-id="cd773-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="cd773-133">MixedRealityPackager.exe를 사용 하 여 내보내기 하는 방법</span><span class="sxs-lookup"><span data-stu-id="cd773-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="cd773-134">장치 맵 내보내기 het.mapx 및 sa.mapx 두 mapx 파일 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="cd773-135">내보내기 프로세스 중 모든 공간 앵커 (있는 경우)에 지정된 된 응용 프로그램 및 사용자가 만든 경계를 제외 하 고 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="cd773-136">원본 패키지 제품군 이름에는 설치 된 기존 응용 프로그램 일치 해야 합니다 또는 exe가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="cd773-137">MixedRealityPackager.exe를 사용 하 여 가져오기 방법</span><span class="sxs-lookup"><span data-stu-id="cd773-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="cd773-138">가져오기 기존 공간 데이터를 삭제 하 여 지정된 된 디렉터리의 데이터로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="cd773-139">앱 이름 입력에 대 한 공간 앵커는 대상 앱의 패키지 이름을 가져와야 하 고 대상 사용자 SID를 가져온된 공간 앵커에 액세스할 수 있어야 하는 사용자 지정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="cd773-140">대상 패키지 제품군 이름 및 Sid 사용자 PC에 대 한 기존 값을 일치 해야 합니다 또는 exe가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd773-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="cd773-141">오류 메시지</span><span class="sxs-lookup"><span data-stu-id="cd773-141">Error Messages</span></span>
<span data-ttu-id="cd773-142">또한 오류 아래 오류 메시지와도 함께 HRESULT를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="cd773-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="cd773-143">오류가 잘못 된 인수가 발생 한 경우</span><span class="sxs-lookup"><span data-stu-id="cd773-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="cd773-144">관리자 모드에서 실행 파일 실행 되지 않았습니다 하는 경우</span><span class="sxs-lookup"><span data-stu-id="cd773-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="cd773-145">활성화 또는 비활성화 드라이버에 오류가 발생 한 경우</span><span class="sxs-lookup"><span data-stu-id="cd773-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="cd773-146">공간 데이터베이스 버전 유효성 검사 오류가 발생 한 경우</span><span class="sxs-lookup"><span data-stu-id="cd773-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="cd773-147">Import/export 대상 앱에 대해 제공 된 패키지 제품군 이름 유효성 검사 오류가 발생 한 경우</span><span class="sxs-lookup"><span data-stu-id="cd773-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="cd773-148">사용자 SID를 유효성 검사 오류가 발생 한 경우</span><span class="sxs-lookup"><span data-stu-id="cd773-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="cd773-149">발생 한 경우 오류와 관련 된 공간 데이터 원본 또는 대상 파일</span><span class="sxs-lookup"><span data-stu-id="cd773-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="cd773-150">시작 하 고 스펙트럼/SharedRealitySvc의 중단에 관련 된 오류의 경우</span><span class="sxs-lookup"><span data-stu-id="cd773-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
