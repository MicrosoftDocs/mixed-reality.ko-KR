---
title: 장치 포털 API 참조
description: HoloLens에 Windows Device Portal 대 한 API 참조
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603278"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="96771-104">장치 포털 API 참조</span><span class="sxs-lookup"><span data-stu-id="96771-104">Device portal API reference</span></span>

<span data-ttu-id="96771-105">모든 항목을 [Windows Device Portal](using-the-windows-device-portal.md) 데이터에 액세스 하 고 장치를 프로그래밍 방식으로 제어 하는 데 사용할 수 있는 REST API를 기반으로 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96771-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="96771-106">앱 배포</span><span class="sxs-lookup"><span data-stu-id="96771-106">App deloyment</span></span>

<span data-ttu-id="96771-107">**/api/app/packagemanager/package (삭제)**</span><span class="sxs-lookup"><span data-stu-id="96771-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="96771-108">앱 제거</span><span class="sxs-lookup"><span data-stu-id="96771-108">Uninstalls an app</span></span>

<span data-ttu-id="96771-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-109">Parameters</span></span>
* <span data-ttu-id="96771-110">패키지: 제거할 패키지의 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="96771-111">**/api/app/packagemanager/package (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="96771-112">앱 설치</span><span class="sxs-lookup"><span data-stu-id="96771-112">Installs an App</span></span>

<span data-ttu-id="96771-113">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-113">Parameters</span></span>
* <span data-ttu-id="96771-114">패키지: 설치할 패키지의 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="96771-115">페이로드</span><span class="sxs-lookup"><span data-stu-id="96771-115">Payload</span></span>
* <span data-ttu-id="96771-116">표준에 맞는 다중 파트 http 본문</span><span class="sxs-lookup"><span data-stu-id="96771-116">multi-part conforming http body</span></span>

<span data-ttu-id="96771-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="96771-118">세부 정보를 사용 하 여 시스템에 설치 된 앱의 목록을 검색합니다</span><span class="sxs-lookup"><span data-stu-id="96771-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="96771-119">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-119">Return data</span></span>
* <span data-ttu-id="96771-120">세부 정보를 사용 하 여 설치 된 패키지 목록</span><span class="sxs-lookup"><span data-stu-id="96771-120">List of installed packages with details</span></span>

<span data-ttu-id="96771-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="96771-122">진행률 앱 설치에서의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="96771-123">덤프 컬렉션</span><span class="sxs-lookup"><span data-stu-id="96771-123">Dump collection</span></span>

<span data-ttu-id="96771-124">**/api/debug/dump/usermode/crashcontrol (삭제)**</span><span class="sxs-lookup"><span data-stu-id="96771-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="96771-125">사용 하지 않도록 설정 크래시 덤프 수집을 테스트용으로 로드 된 앱에 대 한</span><span class="sxs-lookup"><span data-stu-id="96771-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="96771-126">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-126">Parameters</span></span>
* <span data-ttu-id="96771-127">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="96771-127">packageFullname : package name</span></span>

<span data-ttu-id="96771-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="96771-129">테스트용 로드 앱에 대 한 설정을 크래시 덤프 수집을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="96771-130">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-130">Parameters</span></span>
* <span data-ttu-id="96771-131">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="96771-131">packageFullname : package name</span></span>

<span data-ttu-id="96771-132">**/api/debug/dump/usermode/crashcontrol (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="96771-133">사용 하도록 설정 하 고 테스트용으로 로드 된 앱에 대 한 제어 설정을 덤프</span><span class="sxs-lookup"><span data-stu-id="96771-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="96771-134">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-134">Parameters</span></span>
* <span data-ttu-id="96771-135">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="96771-135">packageFullname : package name</span></span>

<span data-ttu-id="96771-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="96771-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="96771-137">테스트용 로드 앱에 대 한 크래시 덤프를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="96771-138">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-138">Parameters</span></span>
* <span data-ttu-id="96771-139">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="96771-139">packageFullname : package name</span></span>
* <span data-ttu-id="96771-140">fileName: 덤프 파일 이름</span><span class="sxs-lookup"><span data-stu-id="96771-140">fileName : dump file name</span></span>

<span data-ttu-id="96771-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="96771-142">테스트용 로드 앱에 대 한 크래시 덤프를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="96771-143">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-143">Parameters</span></span>
* <span data-ttu-id="96771-144">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="96771-144">packageFullname : package name</span></span>
* <span data-ttu-id="96771-145">fileName: 덤프 파일 이름</span><span class="sxs-lookup"><span data-stu-id="96771-145">fileName : dump file name</span></span>

<span data-ttu-id="96771-146">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-146">Return data</span></span>
* <span data-ttu-id="96771-147">덤프 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-147">Dump file.</span></span> <span data-ttu-id="96771-148">WinDbg 또는 Visual Studio를 사용 하 여 검사</span><span class="sxs-lookup"><span data-stu-id="96771-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="96771-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="96771-150">테스트용 로드 앱에 대 한 모든 크래시 덤프의 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="96771-151">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-151">Return data</span></span>
* <span data-ttu-id="96771-152">쪽 로드 된 앱 당 목록을 크래시 덤프</span><span class="sxs-lookup"><span data-stu-id="96771-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="96771-153">ETW</span><span class="sxs-lookup"><span data-stu-id="96771-153">ETW</span></span>

<span data-ttu-id="96771-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="96771-155">등록 된 공급자를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-155">Enumerates registered providers</span></span>

<span data-ttu-id="96771-156">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-156">Return data</span></span>
* <span data-ttu-id="96771-157">공급자, 이름 및 GUID의 목록</span><span class="sxs-lookup"><span data-stu-id="96771-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="96771-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="96771-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="96771-159">실시간 ETW 세션에 만듭니다. websocket을 통해 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="96771-160">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-160">Return data</span></span>
* <span data-ttu-id="96771-161">활성화 된 공급자의 ETW 이벤트</span><span class="sxs-lookup"><span data-stu-id="96771-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="96771-162">홀로그램 OS</span><span class="sxs-lookup"><span data-stu-id="96771-162">Holographic OS</span></span>

<span data-ttu-id="96771-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="96771-164">시스템을 사용 하 여 등록 되지 않은 HoloLens 특정 ETW 공급자의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="96771-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="96771-166">실행 중인 모든 서비스의 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-166">Returns the states of all services running.</span></span>

<span data-ttu-id="96771-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="96771-168">밀리미터 단위로 저장된 IPD를 (Interpupillary 거리)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="96771-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="96771-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="96771-170">IPD 설정</span><span class="sxs-lookup"><span data-stu-id="96771-170">Sets the IPD</span></span>

<span data-ttu-id="96771-171">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-171">Parameters</span></span>
* <span data-ttu-id="96771-172">ipd: 밀리미터 단위로 설정 하는 새 IPD 값</span><span class="sxs-lookup"><span data-stu-id="96771-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="96771-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="96771-174">디바이스 포털에 대한 HTTPS 요구 사항 가져오기</span><span class="sxs-lookup"><span data-stu-id="96771-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="96771-175">**/api/holographic/os/webmanagement/settings/https (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="96771-176">장치 포털에 대 한 HTTPS 요구 사항을 설정합니다</span><span class="sxs-lookup"><span data-stu-id="96771-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="96771-177">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-177">Parameters</span></span>
* <span data-ttu-id="96771-178">필요: 예, 아니요 또는 기본</span><span class="sxs-lookup"><span data-stu-id="96771-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="96771-179">Holographic 인식</span><span class="sxs-lookup"><span data-stu-id="96771-179">Holographic Perception</span></span>

<span data-ttu-id="96771-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="96771-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="96771-181">Websocket 업그레이드를 수락 하 고 30fps에서 업데이트를 전송 하는 perception 클라이언트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="96771-182">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-182">Parameters</span></span>
* <span data-ttu-id="96771-183">clientmode: "활성" 강제로 visual 추적 모드 소극적으로 설정할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="96771-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="96771-184">Holographic 열</span><span class="sxs-lookup"><span data-stu-id="96771-184">Holographic Thermal</span></span>

<span data-ttu-id="96771-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="96771-186">장치 (보통 0, 1 웜, 중요 한 2)의 단계는 열 가져오기</span><span class="sxs-lookup"><span data-stu-id="96771-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="96771-187">Perception 시뮬레이션 컨트롤</span><span class="sxs-lookup"><span data-stu-id="96771-187">Perception Simulation Control</span></span>

<span data-ttu-id="96771-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="96771-189">시뮬레이션 모드 가져오기</span><span class="sxs-lookup"><span data-stu-id="96771-189">Get the simulation mode</span></span>

<span data-ttu-id="96771-190">**/api/holographic/simulation/control/mode (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="96771-191">시뮬레이션 모드 설정</span><span class="sxs-lookup"><span data-stu-id="96771-191">Set the simulation mode</span></span>

<span data-ttu-id="96771-192">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-192">Parameters</span></span>
* <span data-ttu-id="96771-193">모드: 시뮬레이션 모드: 기본, 시뮬레이션, 원격, 레거시</span><span class="sxs-lookup"><span data-stu-id="96771-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="96771-194">**/api/holographic/simulation/control/stream (삭제)**</span><span class="sxs-lookup"><span data-stu-id="96771-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="96771-195">컨트롤 스트림을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-195">Delete a control stream.</span></span>

<span data-ttu-id="96771-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="96771-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="96771-197">컨트롤 스트림에 대 한 웹 소켓 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="96771-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="96771-198">**/api/holographic/simulation/control/stream (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="96771-199">컨트롤 스트림 만들기 (우선 순위는 필요) (streamId 필요) 만든 스트림에 데이터를 게시 또는 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="96771-200">게시 된 데이터는 ' 응용 프로그램/옥텟 스트림 ' 형식일 수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="96771-201">Perception 시뮬레이션 재생</span><span class="sxs-lookup"><span data-stu-id="96771-201">Perception Simulation Playback</span></span>

<span data-ttu-id="96771-202">**/api/holographic/simulation/playback/file (삭제)**</span><span class="sxs-lookup"><span data-stu-id="96771-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="96771-203">기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-203">Delete a recording.</span></span>

<span data-ttu-id="96771-204">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-204">Parameters</span></span>
* <span data-ttu-id="96771-205">기록: 삭제할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="96771-206">**/api/holographic/simulation/playback/file (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="96771-207">녹음/녹화를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-207">Upload a recording.</span></span>

<span data-ttu-id="96771-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="96771-209">모든 녹음/녹화를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-209">Get all recordings.</span></span>

<span data-ttu-id="96771-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="96771-211">기록의 현재 재생 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="96771-212">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-212">Parameters</span></span>
* <span data-ttu-id="96771-213">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-213">recording : Name of recording.</span></span>

<span data-ttu-id="96771-214">**/api/holographic/simulation/playback/session/file (삭제)**</span><span class="sxs-lookup"><span data-stu-id="96771-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="96771-215">녹음/녹화를 언로드하십시오.</span><span class="sxs-lookup"><span data-stu-id="96771-215">Unload a recording.</span></span>

<span data-ttu-id="96771-216">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-216">Parameters</span></span>
* <span data-ttu-id="96771-217">기록: 언로드할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="96771-218">**/api/holographic/simulation/playback/session/file (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="96771-219">녹음/녹화를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-219">Load a recording.</span></span>

<span data-ttu-id="96771-220">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-220">Parameters</span></span>
* <span data-ttu-id="96771-221">기록: 로드할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="96771-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="96771-223">로드 된 모든 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-223">Get all loaded recordings.</span></span>

<span data-ttu-id="96771-224">**/api/holographic/simulation/playback/session/pause (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="96771-225">기록을 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-225">Pause a recording.</span></span>

<span data-ttu-id="96771-226">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-226">Parameters</span></span>
* <span data-ttu-id="96771-227">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-227">recording : Name of recording.</span></span>

<span data-ttu-id="96771-228">**/api/holographic/simulation/playback/session/play (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="96771-229">녹음/녹화를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-229">Play a recording.</span></span>

<span data-ttu-id="96771-230">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-230">Parameters</span></span>
* <span data-ttu-id="96771-231">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-231">recording : Name of recording.</span></span>

<span data-ttu-id="96771-232">**/api/holographic/simulation/playback/session/stop (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="96771-233">녹음/녹화를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-233">Stop a recording.</span></span>

<span data-ttu-id="96771-234">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-234">Parameters</span></span>
* <span data-ttu-id="96771-235">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-235">recording : Name of recording.</span></span>

<span data-ttu-id="96771-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="96771-237">로드 된 기록 데이터 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="96771-238">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-238">Parameters</span></span>
* <span data-ttu-id="96771-239">기록: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="96771-240">Perception 시뮬레이션 기록</span><span class="sxs-lookup"><span data-stu-id="96771-240">Perception Simulation Recording</span></span>

<span data-ttu-id="96771-241">**/api/holographic/simulation/recording/start (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="96771-242">기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-242">Start a recording.</span></span> <span data-ttu-id="96771-243">단일 녹음/녹화를 한 번에 활성화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96771-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="96771-244">헤드, 실습, spatialMapping 또는 환경 중 하나를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="96771-245">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-245">Parameters</span></span>
* <span data-ttu-id="96771-246">헤드: 헤드 데이터 레코드에는 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="96771-247">실습: 직접 데이터를 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="96771-248">spatialMapping: 레코드 매핑 공간을 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="96771-249">환경: 환경 데이터를 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="96771-250">이름: 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-250">name : Name of the recording.</span></span>
* <span data-ttu-id="96771-251">singleSpatialMappingFrame: 단일 공간 매핑을 프레임에만 기록할 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="96771-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="96771-253">가져오기 상태를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-253">Get recording state.</span></span>

<span data-ttu-id="96771-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="96771-255">현재 녹음/녹화를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-255">Stop the current recording.</span></span> <span data-ttu-id="96771-256">기록 파일로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96771-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="96771-257">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="96771-257">Mixed Reality Capture</span></span>

<span data-ttu-id="96771-258">**/api/holographic/mrc/file (삭제)**</span><span class="sxs-lookup"><span data-stu-id="96771-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="96771-259">장치에서 기록 하는 혼합된 현실을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="96771-260">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-260">Parameters</span></span>
* <span data-ttu-id="96771-261">파일 이름: 삭제할 파일의 인코딩 이름 hex64</span><span class="sxs-lookup"><span data-stu-id="96771-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="96771-262">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="96771-263">가져옵니다 기본 혼합 현실을 캡처 설정</span><span class="sxs-lookup"><span data-stu-id="96771-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="96771-264">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="96771-265">장치에서 혼합된 현실 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="96771-266">사용 하 여 op = 스트리밍에 대 한 스트림 쿼리 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="96771-267">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-267">Parameters</span></span>
* <span data-ttu-id="96771-268">파일 이름: 가져올 비디오 파일의 인코딩 이름 hex64</span><span class="sxs-lookup"><span data-stu-id="96771-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="96771-269">op : stream</span><span class="sxs-lookup"><span data-stu-id="96771-269">op : stream</span></span>

<span data-ttu-id="96771-270">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="96771-271">지정된 된 파일에 대 한 축소판 이미지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="96771-272">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-272">Parameters</span></span>
* <span data-ttu-id="96771-273">파일 이름: 미리 보기 요청 되는 파일의 인코딩 이름 hex64</span><span class="sxs-lookup"><span data-stu-id="96771-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="96771-274">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="96771-275">혼합된 현실 기록 (실행, 중지)의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="96771-276">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="96771-277">장치에 저장 하는 혼합된 현실 파일 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="96771-278">**/api/holographic/mrc/settings (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="96771-279">집합 기본 혼합 현실을 캡처 설정</span><span class="sxs-lookup"><span data-stu-id="96771-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="96771-280">**/api/holographic/mrc/video/control/start (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="96771-281">혼합된 현실 녹음/녹화 시작</span><span class="sxs-lookup"><span data-stu-id="96771-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="96771-282">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-282">Parameters</span></span>
* <span data-ttu-id="96771-283">holo: 홀로그램 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="96771-284">pv: 캡처 PV 카메라: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="96771-285">mic: 캡처 마이크: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="96771-286">루프백: 앱 오디오 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="96771-287">**/api/holographic/mrc/video/control/stop (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="96771-288">중지 현재 혼합 현실 기록</span><span class="sxs-lookup"><span data-stu-id="96771-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="96771-289">**/api/holographic/mrc/photo (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="96771-290">혼합된 현실 사진을 촬영 하 고 장치에서 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="96771-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="96771-291">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-291">Parameters</span></span>
* <span data-ttu-id="96771-292">holo: 홀로그램 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="96771-293">pv: 캡처 PV 카메라: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="96771-294">혼합된 현실 스트리밍</span><span class="sxs-lookup"><span data-stu-id="96771-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="96771-295">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="96771-296">조각난 mp4의 청크 분할 다운로드를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="96771-297">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-297">Parameters</span></span>
* <span data-ttu-id="96771-298">holo: 홀로그램 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="96771-299">pv: 캡처 PV 카메라: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="96771-300">mic: 캡처 마이크: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="96771-301">루프백: 앱 오디오 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="96771-302">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="96771-303">조각난 mp4의 청크 분할 다운로드를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="96771-304">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-304">Parameters</span></span>
* <span data-ttu-id="96771-305">holo: 홀로그램 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="96771-306">pv: 캡처 PV 카메라: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="96771-307">mic: 캡처 마이크: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="96771-308">루프백: 앱 오디오 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="96771-309">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="96771-310">조각난 mp4의 청크 분할 다운로드를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="96771-311">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-311">Parameters</span></span>
* <span data-ttu-id="96771-312">holo: 홀로그램 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="96771-313">pv: 캡처 PV 카메라: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="96771-314">mic: 캡처 마이크: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="96771-315">루프백: 앱 오디오 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="96771-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="96771-317">조각난 mp4의 청크 분할 다운로드를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="96771-318">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-318">Parameters</span></span>
* <span data-ttu-id="96771-319">holo: 홀로그램 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="96771-320">pv: 캡처 PV 카메라: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="96771-321">mic: 캡처 마이크: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="96771-322">루프백: 앱 오디오 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="96771-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="96771-323">네트워킹</span><span class="sxs-lookup"><span data-stu-id="96771-323">Networking</span></span>

<span data-ttu-id="96771-324">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="96771-325">현재 ip 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="96771-326">OS 정보</span><span class="sxs-lookup"><span data-stu-id="96771-326">OS Information</span></span>

<span data-ttu-id="96771-327">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="96771-328">운영 체제 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-328">Gets operating system information</span></span>

<span data-ttu-id="96771-329">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="96771-330">컴퓨터 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-330">Gets the machine name</span></span>

<span data-ttu-id="96771-331">**/api/os/machinename (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="96771-332">컴퓨터 이름 설정</span><span class="sxs-lookup"><span data-stu-id="96771-332">Sets the machine name</span></span>

<span data-ttu-id="96771-333">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-333">Parameters</span></span>
* <span data-ttu-id="96771-334">이름: 새 컴퓨터 이름으로 설정 하려면 인코딩된 hex64</span><span class="sxs-lookup"><span data-stu-id="96771-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="96771-335">성능 데이터</span><span class="sxs-lookup"><span data-stu-id="96771-335">Performance data</span></span>

<span data-ttu-id="96771-336">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="96771-337">세부 정보를 사용 하 여 실행 중인 프로세스 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="96771-338">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-338">Return data</span></span>
* <span data-ttu-id="96771-339">프로세스 및 각 프로세스에 대 한 세부 정보 목록 사용 하 여 JSON</span><span class="sxs-lookup"><span data-stu-id="96771-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="96771-340">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="96771-341">(읽기/쓰기 I/O, 메모리 통계 등 시스템 성능 통계를 반환합니다.입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="96771-342">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-342">Return data</span></span>
* <span data-ttu-id="96771-343">시스템 정보를 사용 하 여 JSON입니다. CPU, GPU, Memory, Network, IO</span><span class="sxs-lookup"><span data-stu-id="96771-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="96771-344">Power</span><span class="sxs-lookup"><span data-stu-id="96771-344">Power</span></span>

<span data-ttu-id="96771-345">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="96771-346">현재 배터리 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96771-346">Gets the current battery state</span></span>

<span data-ttu-id="96771-347">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="96771-348">시스템 절전 모드 인지 확인</span><span class="sxs-lookup"><span data-stu-id="96771-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="96771-349">원격 제어</span><span class="sxs-lookup"><span data-stu-id="96771-349">Remote Control</span></span>

<span data-ttu-id="96771-350">**/api/control/restart (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="96771-351">대상 장치를 다시 시작</span><span class="sxs-lookup"><span data-stu-id="96771-351">Restarts the target device</span></span>

<span data-ttu-id="96771-352">**/api/control/shutdown (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="96771-353">대상 장치 종료</span><span class="sxs-lookup"><span data-stu-id="96771-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="96771-354">작업 관리자</span><span class="sxs-lookup"><span data-stu-id="96771-354">Task Manager</span></span>

<span data-ttu-id="96771-355">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="96771-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="96771-356">최신 앱을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-356">Stops a modern app</span></span>

<span data-ttu-id="96771-357">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-357">Parameters</span></span>
* <span data-ttu-id="96771-358">패키지: 인코딩된 hex64 앱 패키지의 전체 이름</span><span class="sxs-lookup"><span data-stu-id="96771-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="96771-359">forcestop : 모든 프로세스 중지를 강제 (= yes)</span><span class="sxs-lookup"><span data-stu-id="96771-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="96771-360">**/api/taskmanager/app (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="96771-361">최신 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-361">Starts a modern app</span></span>

<span data-ttu-id="96771-362">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-362">Parameters</span></span>
* <span data-ttu-id="96771-363">appid: 앱의 시작 PRAID hex64 인코딩</span><span class="sxs-lookup"><span data-stu-id="96771-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="96771-364">패키지: 인코딩된 hex64 앱 패키지의 전체 이름</span><span class="sxs-lookup"><span data-stu-id="96771-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="96771-365">WiFi Management</span><span class="sxs-lookup"><span data-stu-id="96771-365">WiFi Management</span></span>

<span data-ttu-id="96771-366">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="96771-367">무선 네트워크 인터페이스를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="96771-368">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-368">Return data</span></span>
* <span data-ttu-id="96771-369">세부 정보 (GUID, 설명 등)를 사용 하 여 무선 인터페이스 목록</span><span class="sxs-lookup"><span data-stu-id="96771-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="96771-370">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="96771-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="96771-371">지정된 된 인터페이스에 네트워크와 연결 된 프로필을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="96771-372">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-372">Parameters</span></span>
* <span data-ttu-id="96771-373">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="96771-373">interface : network interface guid</span></span>
* <span data-ttu-id="96771-374">프로필: 프로필 이름</span><span class="sxs-lookup"><span data-stu-id="96771-374">profile : profile name</span></span>

<span data-ttu-id="96771-375">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="96771-376">지정 된 네트워크 인터페이스에서 무선 네트워크를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="96771-377">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-377">Parameters</span></span>
* <span data-ttu-id="96771-378">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="96771-378">interface : network interface guid</span></span>

<span data-ttu-id="96771-379">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-379">Return data</span></span>
* <span data-ttu-id="96771-380">세부 정보를 사용 하 여 네트워크 인터페이스에 무선 네트워크 목록</span><span class="sxs-lookup"><span data-stu-id="96771-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="96771-381">**/api/wifi/network (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="96771-382">연결 또는 지정된 된 인터페이스의 네트워크로의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="96771-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="96771-383">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-383">Parameters</span></span>
* <span data-ttu-id="96771-384">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="96771-384">interface : network interface guid</span></span>
* <span data-ttu-id="96771-385">ssid: ssid, hex64 연결할 인코딩</span><span class="sxs-lookup"><span data-stu-id="96771-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="96771-386">op: 연결 또는 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="96771-386">op : connect or disconnect</span></span>
* <span data-ttu-id="96771-387">createprofile: 예 또는 아니요</span><span class="sxs-lookup"><span data-stu-id="96771-387">createprofile : yes or no</span></span>
* <span data-ttu-id="96771-388">키: 공유 키를 hex64 인코딩</span><span class="sxs-lookup"><span data-stu-id="96771-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="96771-389">Windows 성능 기록기</span><span class="sxs-lookup"><span data-stu-id="96771-389">Windows Performance Recorder</span></span>

<span data-ttu-id="96771-390">**/api/wpr/customtrace (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="96771-391">WPR 프로필을 업로드 하 고 업로드 된 프로필을 사용 하 여 추적을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="96771-392">페이로드</span><span class="sxs-lookup"><span data-stu-id="96771-392">Payload</span></span>
* <span data-ttu-id="96771-393">표준에 맞는 다중 파트 http 본문</span><span class="sxs-lookup"><span data-stu-id="96771-393">multi-part conforming http body</span></span>

<span data-ttu-id="96771-394">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-394">Return data</span></span>
* <span data-ttu-id="96771-395">WPR 세션 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-395">Returns the WPR session status.</span></span>

<span data-ttu-id="96771-396">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="96771-397">WPR 세션의 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="96771-398">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-398">Return data</span></span>
* <span data-ttu-id="96771-399">WPR 세션 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-399">WPR session status.</span></span>

<span data-ttu-id="96771-400">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="96771-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="96771-401">WPR (성능) 추적 세션 중지</span><span class="sxs-lookup"><span data-stu-id="96771-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="96771-402">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-402">Return data</span></span>
* <span data-ttu-id="96771-403">추적 ETL 파일을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-403">Returns the trace ETL file</span></span>

<span data-ttu-id="96771-404">**/api/wpr/trace (게시물)**</span><span class="sxs-lookup"><span data-stu-id="96771-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="96771-405">세션 추적 WPR (성능)를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="96771-406">매개 변수</span><span class="sxs-lookup"><span data-stu-id="96771-406">Parameters</span></span>
* <span data-ttu-id="96771-407">프로필: 프로필 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="96771-407">profile : Profile name.</span></span> <span data-ttu-id="96771-408">사용 가능한 프로필 perfprofiles/profiles.json에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96771-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="96771-409">데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-409">Return data</span></span>
* <span data-ttu-id="96771-410">시작 시 WPR 세션 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="96771-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="96771-411">참조</span><span class="sxs-lookup"><span data-stu-id="96771-411">See also</span></span>
* [<span data-ttu-id="96771-412">Windows Device Portal 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="96771-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="96771-413">장치 포털 core API 참조 (UWP)</span><span class="sxs-lookup"><span data-stu-id="96771-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
