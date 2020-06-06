---
title: 디바이스 포털 API 참조
description: HoloLens의 Windows 장치 포털에 대 한 API 참조
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows 장치 포털, API
ms.openlocfilehash: 17268c9a20d3da0ee90e5d6cead4342d3badf800
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451328"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="c7af8-104">디바이스 포털 API 참조</span><span class="sxs-lookup"><span data-stu-id="c7af8-104">Device portal API reference</span></span>

<span data-ttu-id="c7af8-105">[Windows 장치 포털](using-the-windows-device-portal.md) 의 모든 항목은 데이터에 액세스 하 고 프로그래밍 방식으로 장치를 제어 하는 데 사용할 수 있는 REST API의 맨 위에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="c7af8-106">앱 배포</span><span class="sxs-lookup"><span data-stu-id="c7af8-106">App deloyment</span></span>

<span data-ttu-id="c7af8-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="c7af8-108">앱을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-108">Uninstalls an app</span></span>

<span data-ttu-id="c7af8-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-109">Parameters</span></span>
* <span data-ttu-id="c7af8-110">package: 제거할 패키지의 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="c7af8-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="c7af8-112">앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-112">Installs an App</span></span>

<span data-ttu-id="c7af8-113">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-113">Parameters</span></span>
* <span data-ttu-id="c7af8-114">package: 설치할 패키지의 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="c7af8-115">Payload</span><span class="sxs-lookup"><span data-stu-id="c7af8-115">Payload</span></span>
* <span data-ttu-id="c7af8-116">여러 부분으로 구성 되는 http 본문</span><span class="sxs-lookup"><span data-stu-id="c7af8-116">multi-part conforming http body</span></span>

<span data-ttu-id="c7af8-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="c7af8-118">세부 정보를 사용 하 여 시스템에 설치 된 앱 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="c7af8-119">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-119">Return data</span></span>
* <span data-ttu-id="c7af8-120">세부 정보가 포함 된 설치 된 패키지 목록</span><span class="sxs-lookup"><span data-stu-id="c7af8-120">List of installed packages with details</span></span>

<span data-ttu-id="c7af8-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="c7af8-122">진행 중인 앱 설치의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="c7af8-123">덤프 컬렉션</span><span class="sxs-lookup"><span data-stu-id="c7af8-123">Dump collection</span></span>

<span data-ttu-id="c7af8-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="c7af8-125">테스트용으로 로드 앱에 대 한 크래시 덤프 수집 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="c7af8-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="c7af8-126">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-126">Parameters</span></span>
* <span data-ttu-id="c7af8-127">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="c7af8-127">packageFullname : package name</span></span>

<span data-ttu-id="c7af8-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="c7af8-129">테스트용으로 로드 apps 크래시 덤프 컬렉션에 대 한 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="c7af8-130">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-130">Parameters</span></span>
* <span data-ttu-id="c7af8-131">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="c7af8-131">packageFullname : package name</span></span>

<span data-ttu-id="c7af8-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="c7af8-133">테스트용으로 로드 앱에 대 한 덤프 제어 설정을 사용 하도록 설정 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="c7af8-134">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-134">Parameters</span></span>
* <span data-ttu-id="c7af8-135">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="c7af8-135">packageFullname : package name</span></span>

<span data-ttu-id="c7af8-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="c7af8-137">테스트용으로 로드 앱에 대 한 크래시 덤프를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c7af8-138">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-138">Parameters</span></span>
* <span data-ttu-id="c7af8-139">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="c7af8-139">packageFullname : package name</span></span>
* <span data-ttu-id="c7af8-140">파일 이름: 덤프 파일 이름</span><span class="sxs-lookup"><span data-stu-id="c7af8-140">fileName : dump file name</span></span>

<span data-ttu-id="c7af8-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="c7af8-142">테스트용으로 로드 앱에 대 한 크래시 덤프를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c7af8-143">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-143">Parameters</span></span>
* <span data-ttu-id="c7af8-144">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="c7af8-144">packageFullname : package name</span></span>
* <span data-ttu-id="c7af8-145">파일 이름: 덤프 파일 이름</span><span class="sxs-lookup"><span data-stu-id="c7af8-145">fileName : dump file name</span></span>

<span data-ttu-id="c7af8-146">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-146">Return data</span></span>
* <span data-ttu-id="c7af8-147">덤프 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-147">Dump file.</span></span> <span data-ttu-id="c7af8-148">WinDbg 또는 Visual Studio를 사용 하 여 검사</span><span class="sxs-lookup"><span data-stu-id="c7af8-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="c7af8-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="c7af8-150">테스트용으로 로드 apps에 대 한 모든 크래시 덤프 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="c7af8-151">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-151">Return data</span></span>
* <span data-ttu-id="c7af8-152">테스트용으로 로드 된 앱 당 크래시 덤프 목록</span><span class="sxs-lookup"><span data-stu-id="c7af8-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="c7af8-153">ETW</span><span class="sxs-lookup"><span data-stu-id="c7af8-153">ETW</span></span>

<span data-ttu-id="c7af8-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="c7af8-155">등록 된 공급자를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-155">Enumerates registered providers</span></span>

<span data-ttu-id="c7af8-156">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-156">Return data</span></span>
* <span data-ttu-id="c7af8-157">공급자 목록, 이름 및 GUID</span><span class="sxs-lookup"><span data-stu-id="c7af8-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="c7af8-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="c7af8-159">실시간 ETW 세션을 만듭니다. websocket을 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="c7af8-160">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-160">Return data</span></span>
* <span data-ttu-id="c7af8-161">활성화 된 공급자의 ETW 이벤트</span><span class="sxs-lookup"><span data-stu-id="c7af8-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="c7af8-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="c7af8-162">Holographic OS</span></span>

<span data-ttu-id="c7af8-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="c7af8-164">시스템에 등록 되지 않은 HoloLens 특정 ETW 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="c7af8-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="c7af8-166">실행 중인 모든 서비스의 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-166">Returns the states of all services running.</span></span>

<span data-ttu-id="c7af8-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="c7af8-168">저장 된 IPD (Interpupillary distance)를 밀리미터 단위로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="c7af8-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="c7af8-170">IPD를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-170">Sets the IPD</span></span>

<span data-ttu-id="c7af8-171">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-171">Parameters</span></span>
* <span data-ttu-id="c7af8-172">ipd: 밀리미터로 지정할 New IPD 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="c7af8-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="c7af8-174">장치 포털에 대 한 HTTPS 요구 사항 가져오기</span><span class="sxs-lookup"><span data-stu-id="c7af8-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c7af8-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="c7af8-176">장치 포털에 대 한 HTTPS 요구 사항을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c7af8-177">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-177">Parameters</span></span>
* <span data-ttu-id="c7af8-178">필수: 예, 아니요 또는 기본값</span><span class="sxs-lookup"><span data-stu-id="c7af8-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="c7af8-179">Holographic 인식</span><span class="sxs-lookup"><span data-stu-id="c7af8-179">Holographic Perception</span></span>

<span data-ttu-id="c7af8-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="c7af8-181">Websocket 업그레이드를 수락 하 고 30fps로 업데이트를 전송 하는 인식 클라이언트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="c7af8-182">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-182">Parameters</span></span>
* <span data-ttu-id="c7af8-183">clientmode: "활성"은 동적으로 설정할 수 없는 경우 시각적 추적 모드를 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="c7af8-184">Holographic 열</span><span class="sxs-lookup"><span data-stu-id="c7af8-184">Holographic Thermal</span></span>

<span data-ttu-id="c7af8-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="c7af8-186">장치의 열 단계 가져오기 (0 보통, 1 웜, 2 개 위험)</span><span class="sxs-lookup"><span data-stu-id="c7af8-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="c7af8-187">인식 시뮬레이션 컨트롤</span><span class="sxs-lookup"><span data-stu-id="c7af8-187">Perception Simulation Control</span></span>

<span data-ttu-id="c7af8-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="c7af8-189">시뮬레이션 모드 가져오기</span><span class="sxs-lookup"><span data-stu-id="c7af8-189">Get the simulation mode</span></span>

<span data-ttu-id="c7af8-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="c7af8-191">시뮬레이션 모드 설정</span><span class="sxs-lookup"><span data-stu-id="c7af8-191">Set the simulation mode</span></span>

<span data-ttu-id="c7af8-192">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-192">Parameters</span></span>
* <span data-ttu-id="c7af8-193">모드: 시뮬레이션 모드: 기본값, 시뮬레이션, 원격, 레거시</span><span class="sxs-lookup"><span data-stu-id="c7af8-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="c7af8-194">**/api/holographic/simulation/control/stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="c7af8-195">컨트롤 스트림을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-195">Delete a control stream.</span></span>

<span data-ttu-id="c7af8-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="c7af8-197">컨트롤 스트림에 대 한 웹 소켓 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="c7af8-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="c7af8-199">컨트롤 스트림 (우선 순위는 필수)을 만들거나 만든 스트림에 데이터를 게시 합니다 (streamId 필요).</span><span class="sxs-lookup"><span data-stu-id="c7af8-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="c7af8-200">게시 된 데이터는 ' 응용 프로그램/8 진수 스트림 ' 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="c7af8-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="c7af8-202">' 시뮬레이션 ' 모드일 때 시스템 디스플레이에 렌더링 된 콘텐츠가 포함 된 시뮬레이션 비디오 스트림을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="c7af8-203">단순 형식 설명자 헤더는 처음에 전송 되 고, 그 뒤에는 각각 눈 인덱스와 질감 크기를 나타내는 헤더가 앞에 오는, 각각에는 h.264로 인코딩된 질감이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="c7af8-204">인식 시뮬레이션 재생</span><span class="sxs-lookup"><span data-stu-id="c7af8-204">Perception Simulation Playback</span></span>

<span data-ttu-id="c7af8-205">**/api/holographic/simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="c7af8-206">기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-206">Delete a recording.</span></span>

<span data-ttu-id="c7af8-207">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-207">Parameters</span></span>
* <span data-ttu-id="c7af8-208">녹음/녹화: 삭제할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="c7af8-209">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="c7af8-210">기록을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-210">Upload a recording.</span></span>

<span data-ttu-id="c7af8-211">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="c7af8-212">모든 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-212">Get all recordings.</span></span>

<span data-ttu-id="c7af8-213">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="c7af8-214">기록의 현재 재생 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="c7af8-215">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-215">Parameters</span></span>
* <span data-ttu-id="c7af8-216">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-216">recording : Name of recording.</span></span>

<span data-ttu-id="c7af8-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="c7af8-218">기록을 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-218">Unload a recording.</span></span>

<span data-ttu-id="c7af8-219">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-219">Parameters</span></span>
* <span data-ttu-id="c7af8-220">녹음/녹화: 언로드할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="c7af8-221">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="c7af8-222">기록을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-222">Load a recording.</span></span>

<span data-ttu-id="c7af8-223">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-223">Parameters</span></span>
* <span data-ttu-id="c7af8-224">기록: 로드할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="c7af8-225">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="c7af8-226">로드 된 모든 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-226">Get all loaded recordings.</span></span>

<span data-ttu-id="c7af8-227">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="c7af8-228">기록을 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-228">Pause a recording.</span></span>

<span data-ttu-id="c7af8-229">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-229">Parameters</span></span>
* <span data-ttu-id="c7af8-230">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-230">recording : Name of recording.</span></span>

<span data-ttu-id="c7af8-231">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="c7af8-232">기록을 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-232">Play a recording.</span></span>

<span data-ttu-id="c7af8-233">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-233">Parameters</span></span>
* <span data-ttu-id="c7af8-234">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-234">recording : Name of recording.</span></span>

<span data-ttu-id="c7af8-235">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="c7af8-236">기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-236">Stop a recording.</span></span>

<span data-ttu-id="c7af8-237">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-237">Parameters</span></span>
* <span data-ttu-id="c7af8-238">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-238">recording : Name of recording.</span></span>

<span data-ttu-id="c7af8-239">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="c7af8-240">로드 된 기록에서 데이터의 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="c7af8-241">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-241">Parameters</span></span>
* <span data-ttu-id="c7af8-242">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="c7af8-243">인식 시뮬레이션 기록</span><span class="sxs-lookup"><span data-stu-id="c7af8-243">Perception Simulation Recording</span></span>

<span data-ttu-id="c7af8-244">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="c7af8-245">기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-245">Start a recording.</span></span> <span data-ttu-id="c7af8-246">한 번에 하나의 기록만 활성화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="c7af8-247">헤드, 손, spatialMapping 또는 환경 중 하나를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="c7af8-248">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-248">Parameters</span></span>
* <span data-ttu-id="c7af8-249">head: 1로 설정 하 여 헤드 데이터를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="c7af8-250">실습: 1로 설정 하 여 손으로 데이터를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="c7af8-251">spatialMapping: 1로 설정 하 여 공간 매핑을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="c7af8-252">환경: 환경 데이터를 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="c7af8-253">이름: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-253">name : Name of the recording.</span></span>
* <span data-ttu-id="c7af8-254">singleSpatialMappingFrame: 단일 공간 매핑 프레임만 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="c7af8-255">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="c7af8-256">기록 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-256">Get recording state.</span></span>

<span data-ttu-id="c7af8-257">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="c7af8-258">현재 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-258">Stop the current recording.</span></span> <span data-ttu-id="c7af8-259">기록이 파일로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="c7af8-260">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="c7af8-260">Mixed Reality Capture</span></span>

<span data-ttu-id="c7af8-261">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="c7af8-262">장치에서 혼합 된 현실 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="c7af8-263">스트리밍을 위해 op = stream 쿼리 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="c7af8-264">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-264">Parameters</span></span>
* <span data-ttu-id="c7af8-265">filename: hex64로 인코딩된 비디오 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="c7af8-266">op: stream</span><span class="sxs-lookup"><span data-stu-id="c7af8-266">op : stream</span></span>

<span data-ttu-id="c7af8-267">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="c7af8-268">장치에서 혼합 된 현실 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="c7af8-269">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-269">Parameters</span></span>
* <span data-ttu-id="c7af8-270">filename: 삭제할 파일의 이름 (hex64)입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="c7af8-271">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="c7af8-272">장치에 저장 된 혼합 현실 파일의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="c7af8-273">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="c7af8-274">혼합 현실 사진을 사용 하 고 장치에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="c7af8-275">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-275">Parameters</span></span>
* <span data-ttu-id="c7af8-276">holo: capture holograms: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="c7af8-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="c7af8-277">pv: PV 카메라 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="c7af8-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="c7af8-278">RenderFromCamera: (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="c7af8-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="c7af8-279">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="c7af8-280">기본 혼합 현실 캡처 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="c7af8-281">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="c7af8-282">기본 혼합 현실 캡처 설정을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="c7af8-283">이러한 설정 중 일부는 시스템의 MRC 사진 및 비디오 캡처에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="c7af8-284">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="c7af8-285">Windows 장치 포털 내 혼합 현실 캡처의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-285">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="c7af8-286">***응답***</span><span class="sxs-lookup"><span data-stu-id="c7af8-286">***Response***</span></span>

<span data-ttu-id="c7af8-287">응답에는 Windows 장치 포털이 비디오를 기록 하 고 있는지 여부를 나타내는 JSON 속성이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-287">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="c7af8-288">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-288">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="c7af8-289">지정 된 파일에 대 한 미리 보기 이미지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-289">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="c7af8-290">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-290">Parameters</span></span>
* <span data-ttu-id="c7af8-291">파일 이름: 미리 보기를 요청 하는 파일의 이름 (hex64)입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-291">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="c7af8-292">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-292">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="c7af8-293">혼합 현실 기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-293">Starts a mixed reality recording</span></span>

<span data-ttu-id="c7af8-294">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-294">Parameters</span></span>
* <span data-ttu-id="c7af8-295">holo: capture holograms: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="c7af8-295">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="c7af8-296">pv: PV 카메라 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="c7af8-296">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="c7af8-297">mic: 마이크 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="c7af8-297">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="c7af8-298">루프백: 응용 프로그램 오디오 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="c7af8-298">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="c7af8-299">RenderFromCamera: (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="c7af8-299">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="c7af8-300">vstab: (HoloLens 2만 해당) 비디오 안정화 사용: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="c7af8-300">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="c7af8-301">vstabbuffer: (HoloLens 2만 해당) 비디오 안정화 버퍼 대기 시간: 0-30 프레임 (기본값은 15 프레임)</span><span class="sxs-lookup"><span data-stu-id="c7af8-301">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="c7af8-302">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-302">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="c7af8-303">현재 혼합 된 현실 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-303">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="c7af8-304">혼합 현실 스트리밍</span><span class="sxs-lookup"><span data-stu-id="c7af8-304">Mixed Reality Streaming</span></span>

<span data-ttu-id="c7af8-305">HoloLens는 조각화 된 mp4의 청크 다운로드를 통해 혼합 현실의 실시간 미리 보기를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-305">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="c7af8-306">혼합 현실 스트림은 동일한 매개 변수 집합을 공유 하 여 캡처할 항목을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-306">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="c7af8-307">holo: capture holograms: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="c7af8-307">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c7af8-308">pv: PV 카메라 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="c7af8-308">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c7af8-309">mic: 마이크 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="c7af8-309">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c7af8-310">루프백: 앱 오디오 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="c7af8-310">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="c7af8-311">이러한 항목이 지정 되지 않은 경우 holograms, photo/video 카메라 및 앱 오디오가 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-311">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="c7af8-312">지정 된 경우: 지정 되지 않은 매개 변수는 기본적으로 false로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-312">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="c7af8-313">선택적 매개 변수 (HoloLens 2에만 해당)</span><span class="sxs-lookup"><span data-stu-id="c7af8-313">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="c7af8-314">RenderFromCamera: photo/video 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="c7af8-314">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="c7af8-315">vstab: 비디오 안정화 사용: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="c7af8-315">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="c7af8-316">vstabbuffer: 비디오 안정화 버퍼 대기 시간: 0-30 프레임 (기본값은 15 프레임)</span><span class="sxs-lookup"><span data-stu-id="c7af8-316">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="c7af8-317">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-317">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="c7af8-318">1280x720p 30fps 5Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="c7af8-319">**/api/holographic/stream/live_high. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-319">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="c7af8-320">1280x720p 30fps 5Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-320">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="c7af8-321">**/api/holographic/stream/live_med. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-321">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="c7af8-322">854x480p 30fps 2.5 Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-322">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="c7af8-323">**/api/holographic/stream/live_low. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-323">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="c7af8-324">428x240p 15fps 0.6 Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-324">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="c7af8-325">네트워킹</span><span class="sxs-lookup"><span data-stu-id="c7af8-325">Networking</span></span>

<span data-ttu-id="c7af8-326">**/sh/svring/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-326">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="c7af8-327">현재 ip 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-327">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="c7af8-328">OS 정보</span><span class="sxs-lookup"><span data-stu-id="c7af8-328">OS Information</span></span>

<span data-ttu-id="c7af8-329">**///s/정보 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-329">**/api/os/info (GET)**</span></span>

<span data-ttu-id="c7af8-330">운영 체제 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-330">Gets operating system information</span></span>

<span data-ttu-id="c7af8-331">**/api/oss (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-331">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="c7af8-332">컴퓨터 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-332">Gets the machine name</span></span>

<span data-ttu-id="c7af8-333">**/api/oss (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-333">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="c7af8-334">컴퓨터 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-334">Sets the machine name</span></span>

<span data-ttu-id="c7af8-335">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-335">Parameters</span></span>
* <span data-ttu-id="c7af8-336">이름: 새 컴퓨터 이름, hex64 인코딩,를로 설정</span><span class="sxs-lookup"><span data-stu-id="c7af8-336">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="c7af8-337">성능 데이터</span><span class="sxs-lookup"><span data-stu-id="c7af8-337">Performance data</span></span>

<span data-ttu-id="c7af8-338">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-338">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="c7af8-339">세부 정보를 사용 하 여 실행 중인 프로세스의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-339">Returns the list of running processes with details</span></span>

<span data-ttu-id="c7af8-340">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-340">Return data</span></span>
* <span data-ttu-id="c7af8-341">프로세스 목록 및 각 프로세스에 대 한 세부 정보를 포함 하는 JSON</span><span class="sxs-lookup"><span data-stu-id="c7af8-341">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="c7af8-342">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-342">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="c7af8-343">시스템 성능 통계 (i/o 읽기/쓰기, 메모리 통계 등)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-343">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="c7af8-344">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-344">Return data</span></span>
* <span data-ttu-id="c7af8-345">시스템 정보를 포함 하는 JSON: CPU, GPU, 메모리, 네트워크, IO</span><span class="sxs-lookup"><span data-stu-id="c7af8-345">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="c7af8-346">고급</span><span class="sxs-lookup"><span data-stu-id="c7af8-346">Power</span></span>

<span data-ttu-id="c7af8-347">**/sh/svhhhhhs (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-347">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="c7af8-348">현재 배터리 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-348">Gets the current battery state</span></span>

<span data-ttu-id="c7af8-349">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-349">**/api/power/state (GET)**</span></span>

<span data-ttu-id="c7af8-350">시스템이 저전원 상태 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-350">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="c7af8-351">원격 제어</span><span class="sxs-lookup"><span data-stu-id="c7af8-351">Remote Control</span></span>

<span data-ttu-id="c7af8-352">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-352">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="c7af8-353">대상 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-353">Restarts the target device</span></span>

<span data-ttu-id="c7af8-354">**/sh/svcontroli (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-354">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="c7af8-355">대상 장치를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-355">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="c7af8-356">작업 관리자</span><span class="sxs-lookup"><span data-stu-id="c7af8-356">Task Manager</span></span>

<span data-ttu-id="c7af8-357">**/api/taskmanager/app/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-357">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="c7af8-358">최신 앱을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-358">Stops a modern app</span></span>

<span data-ttu-id="c7af8-359">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-359">Parameters</span></span>
* <span data-ttu-id="c7af8-360">패키지: 앱 패키지의 전체 이름, hex64 인코드</span><span class="sxs-lookup"><span data-stu-id="c7af8-360">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="c7af8-361">forcestop: 모든 프로세스를 강제로 중지 합니다 (= 예).</span><span class="sxs-lookup"><span data-stu-id="c7af8-361">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="c7af8-362">**/sh/svaryer/ps (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-362">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="c7af8-363">최신 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-363">Starts a modern app</span></span>

<span data-ttu-id="c7af8-364">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-364">Parameters</span></span>
* <span data-ttu-id="c7af8-365">appid: 시작 하는 앱의 PRAID, hex64 인코드</span><span class="sxs-lookup"><span data-stu-id="c7af8-365">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="c7af8-366">패키지: 앱 패키지의 전체 이름, hex64 인코드</span><span class="sxs-lookup"><span data-stu-id="c7af8-366">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="c7af8-367">WiFi 관리</span><span class="sxs-lookup"><span data-stu-id="c7af8-367">WiFi Management</span></span>

<span data-ttu-id="c7af8-368">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-368">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="c7af8-369">무선 네트워크 인터페이스를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-369">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="c7af8-370">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-370">Return data</span></span>
* <span data-ttu-id="c7af8-371">세부 정보를 포함 하는 무선 인터페이스 목록 (GUID, 설명 등)</span><span class="sxs-lookup"><span data-stu-id="c7af8-371">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="c7af8-372">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-372">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="c7af8-373">지정 된 인터페이스에서 네트워크와 연결 된 프로필을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-373">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="c7af8-374">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-374">Parameters</span></span>
* <span data-ttu-id="c7af8-375">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="c7af8-375">interface : network interface guid</span></span>
* <span data-ttu-id="c7af8-376">프로필: 프로필 이름</span><span class="sxs-lookup"><span data-stu-id="c7af8-376">profile : profile name</span></span>

<span data-ttu-id="c7af8-377">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-377">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="c7af8-378">지정 된 네트워크 인터페이스의 무선 네트워크를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-378">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="c7af8-379">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-379">Parameters</span></span>
* <span data-ttu-id="c7af8-380">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="c7af8-380">interface : network interface guid</span></span>

<span data-ttu-id="c7af8-381">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-381">Return data</span></span>
* <span data-ttu-id="c7af8-382">네트워크 인터페이스에서 찾을 수 있는 무선 네트워크 목록 (세부 정보 포함)</span><span class="sxs-lookup"><span data-stu-id="c7af8-382">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="c7af8-383">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-383">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="c7af8-384">지정 된 인터페이스의 네트워크에 연결 하거나 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-384">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="c7af8-385">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-385">Parameters</span></span>
* <span data-ttu-id="c7af8-386">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="c7af8-386">interface : network interface guid</span></span>
* <span data-ttu-id="c7af8-387">ssid: ssid, hex64 인코딩, 연결</span><span class="sxs-lookup"><span data-stu-id="c7af8-387">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="c7af8-388">op: 연결 또는 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="c7af8-388">op : connect or disconnect</span></span>
* <span data-ttu-id="c7af8-389">createprofile: 예 또는 아니요</span><span class="sxs-lookup"><span data-stu-id="c7af8-389">createprofile : yes or no</span></span>
* <span data-ttu-id="c7af8-390">키: shared key, hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="c7af8-390">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="c7af8-391">Windows 성능 레코더</span><span class="sxs-lookup"><span data-stu-id="c7af8-391">Windows Performance Recorder</span></span>

<span data-ttu-id="c7af8-392">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-392">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="c7af8-393">WPR 프로필을 업로드 하 고 업로드 된 프로필을 사용 하 여 추적을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-393">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="c7af8-394">Payload</span><span class="sxs-lookup"><span data-stu-id="c7af8-394">Payload</span></span>
* <span data-ttu-id="c7af8-395">여러 부분으로 구성 되는 http 본문</span><span class="sxs-lookup"><span data-stu-id="c7af8-395">multi-part conforming http body</span></span>

<span data-ttu-id="c7af8-396">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-396">Return data</span></span>
* <span data-ttu-id="c7af8-397">WPR 세션 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-397">Returns the WPR session status.</span></span>

<span data-ttu-id="c7af8-398">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-398">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="c7af8-399">WPR 세션의 상태를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-399">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="c7af8-400">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-400">Return data</span></span>
* <span data-ttu-id="c7af8-401">WPR 세션 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-401">WPR session status.</span></span>

<span data-ttu-id="c7af8-402">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-402">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="c7af8-403">WPR (성능) 추적 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-403">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="c7af8-404">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-404">Return data</span></span>
* <span data-ttu-id="c7af8-405">추적 ETL 파일을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-405">Returns the trace ETL file</span></span>

<span data-ttu-id="c7af8-406">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="c7af8-406">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="c7af8-407">WPR (성능) 추적 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-407">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="c7af8-408">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7af8-408">Parameters</span></span>
* <span data-ttu-id="c7af8-409">프로필: 프로필 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-409">profile : Profile name.</span></span> <span data-ttu-id="c7af8-410">사용 가능한 프로필은 perfprofiles/profile. json에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-410">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="c7af8-411">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="c7af8-411">Return data</span></span>
* <span data-ttu-id="c7af8-412">시작 시 WPR 세션 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7af8-412">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7af8-413">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7af8-413">See also</span></span>
* [<span data-ttu-id="c7af8-414">Windows 디바이스 포털 사용</span><span class="sxs-lookup"><span data-stu-id="c7af8-414">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="c7af8-415">장치 포털 핵심 API 참조 (UWP)</span><span class="sxs-lookup"><span data-stu-id="c7af8-415">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
