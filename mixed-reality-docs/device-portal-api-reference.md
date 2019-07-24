---
title: 장치 포털 API 참조
description: HoloLens의 Windows 장치 포털에 대 한 API 참조
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows 장치 포털, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694427"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="9713d-104">장치 포털 API 참조</span><span class="sxs-lookup"><span data-stu-id="9713d-104">Device portal API reference</span></span>

<span data-ttu-id="9713d-105">[Windows 장치 포털](using-the-windows-device-portal.md) 의 모든 항목은 데이터에 액세스 하 고 프로그래밍 방식으로 장치를 제어 하는 데 사용할 수 있는 REST API의 맨 위에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="9713d-106">앱 배포</span><span class="sxs-lookup"><span data-stu-id="9713d-106">App deloyment</span></span>

<span data-ttu-id="9713d-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="9713d-108">앱을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-108">Uninstalls an app</span></span>

<span data-ttu-id="9713d-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-109">Parameters</span></span>
* <span data-ttu-id="9713d-110">패키지 제거할 패키지의 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="9713d-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="9713d-112">앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-112">Installs an App</span></span>

<span data-ttu-id="9713d-113">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-113">Parameters</span></span>
* <span data-ttu-id="9713d-114">패키지 설치할 패키지의 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="9713d-115">페이로드와</span><span class="sxs-lookup"><span data-stu-id="9713d-115">Payload</span></span>
* <span data-ttu-id="9713d-116">여러 부분으로 구성 되는 http 본문</span><span class="sxs-lookup"><span data-stu-id="9713d-116">multi-part conforming http body</span></span>

<span data-ttu-id="9713d-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="9713d-118">세부 정보를 사용 하 여 시스템에 설치 된 앱 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="9713d-119">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-119">Return data</span></span>
* <span data-ttu-id="9713d-120">세부 정보가 포함 된 설치 된 패키지 목록</span><span class="sxs-lookup"><span data-stu-id="9713d-120">List of installed packages with details</span></span>

<span data-ttu-id="9713d-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="9713d-122">진행 중인 앱 설치의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="9713d-123">덤프 컬렉션</span><span class="sxs-lookup"><span data-stu-id="9713d-123">Dump collection</span></span>

<span data-ttu-id="9713d-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="9713d-125">테스트용으로 로드 앱에 대 한 크래시 덤프 수집 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="9713d-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="9713d-126">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-126">Parameters</span></span>
* <span data-ttu-id="9713d-127">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="9713d-127">packageFullname : package name</span></span>

<span data-ttu-id="9713d-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="9713d-129">테스트용으로 로드 apps 크래시 덤프 컬렉션에 대 한 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="9713d-130">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-130">Parameters</span></span>
* <span data-ttu-id="9713d-131">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="9713d-131">packageFullname : package name</span></span>

<span data-ttu-id="9713d-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="9713d-133">테스트용으로 로드 앱에 대 한 덤프 제어 설정을 사용 하도록 설정 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="9713d-134">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-134">Parameters</span></span>
* <span data-ttu-id="9713d-135">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="9713d-135">packageFullname : package name</span></span>

<span data-ttu-id="9713d-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="9713d-137">테스트용으로 로드 앱에 대 한 크래시 덤프를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="9713d-138">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-138">Parameters</span></span>
* <span data-ttu-id="9713d-139">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="9713d-139">packageFullname : package name</span></span>
* <span data-ttu-id="9713d-140">파일 이름: 덤프 파일 이름</span><span class="sxs-lookup"><span data-stu-id="9713d-140">fileName : dump file name</span></span>

<span data-ttu-id="9713d-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="9713d-142">테스트용으로 로드 앱에 대 한 크래시 덤프를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="9713d-143">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-143">Parameters</span></span>
* <span data-ttu-id="9713d-144">packageFullname: 패키지 이름</span><span class="sxs-lookup"><span data-stu-id="9713d-144">packageFullname : package name</span></span>
* <span data-ttu-id="9713d-145">파일 이름: 덤프 파일 이름</span><span class="sxs-lookup"><span data-stu-id="9713d-145">fileName : dump file name</span></span>

<span data-ttu-id="9713d-146">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-146">Return data</span></span>
* <span data-ttu-id="9713d-147">덤프 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-147">Dump file.</span></span> <span data-ttu-id="9713d-148">WinDbg 또는 Visual Studio를 사용 하 여 검사</span><span class="sxs-lookup"><span data-stu-id="9713d-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="9713d-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="9713d-150">테스트용으로 로드 apps에 대 한 모든 크래시 덤프 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="9713d-151">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-151">Return data</span></span>
* <span data-ttu-id="9713d-152">테스트용으로 로드 된 앱 당 크래시 덤프 목록</span><span class="sxs-lookup"><span data-stu-id="9713d-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="9713d-153">ETW</span><span class="sxs-lookup"><span data-stu-id="9713d-153">ETW</span></span>

<span data-ttu-id="9713d-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="9713d-155">등록 된 공급자를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-155">Enumerates registered providers</span></span>

<span data-ttu-id="9713d-156">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-156">Return data</span></span>
* <span data-ttu-id="9713d-157">공급자 목록, 이름 및 GUID</span><span class="sxs-lookup"><span data-stu-id="9713d-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="9713d-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9713d-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="9713d-159">실시간 ETW 세션을 만듭니다. websocket을 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="9713d-160">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-160">Return data</span></span>
* <span data-ttu-id="9713d-161">활성화 된 공급자의 ETW 이벤트</span><span class="sxs-lookup"><span data-stu-id="9713d-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="9713d-162">홀로그램 OS</span><span class="sxs-lookup"><span data-stu-id="9713d-162">Holographic OS</span></span>

<span data-ttu-id="9713d-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="9713d-164">시스템에 등록 되지 않은 HoloLens 특정 ETW 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="9713d-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="9713d-166">실행 중인 모든 서비스의 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-166">Returns the states of all services running.</span></span>

<span data-ttu-id="9713d-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="9713d-168">저장 된 IPD (Interpupillary distance)를 밀리미터 단위로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="9713d-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="9713d-170">IPD를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-170">Sets the IPD</span></span>

<span data-ttu-id="9713d-171">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-171">Parameters</span></span>
* <span data-ttu-id="9713d-172">ipd 밀리미터 단위로 설정할 새 IPD 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="9713d-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="9713d-174">디바이스 포털에 대한 HTTPS 요구 사항 가져오기</span><span class="sxs-lookup"><span data-stu-id="9713d-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="9713d-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="9713d-176">장치 포털에 대 한 HTTPS 요구 사항을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="9713d-177">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-177">Parameters</span></span>
* <span data-ttu-id="9713d-178">필수: 예, 아니요 또는 기본값</span><span class="sxs-lookup"><span data-stu-id="9713d-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="9713d-179">Holographic 인식</span><span class="sxs-lookup"><span data-stu-id="9713d-179">Holographic Perception</span></span>

<span data-ttu-id="9713d-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9713d-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="9713d-181">Websocket 업그레이드를 수락 하 고 30fps로 업데이트를 전송 하는 인식 클라이언트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="9713d-182">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-182">Parameters</span></span>
* <span data-ttu-id="9713d-183">clientmode: "활성"은 동적으로 설정할 수 없는 경우 시각적 추적 모드를 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="9713d-184">Holographic 열</span><span class="sxs-lookup"><span data-stu-id="9713d-184">Holographic Thermal</span></span>

<span data-ttu-id="9713d-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="9713d-186">장치의 열 단계 가져오기 (0 보통, 1 웜, 2 개 위험)</span><span class="sxs-lookup"><span data-stu-id="9713d-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="9713d-187">인식 시뮬레이션 컨트롤</span><span class="sxs-lookup"><span data-stu-id="9713d-187">Perception Simulation Control</span></span>

<span data-ttu-id="9713d-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="9713d-189">시뮬레이션 모드 가져오기</span><span class="sxs-lookup"><span data-stu-id="9713d-189">Get the simulation mode</span></span>

<span data-ttu-id="9713d-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="9713d-191">시뮬레이션 모드 설정</span><span class="sxs-lookup"><span data-stu-id="9713d-191">Set the simulation mode</span></span>

<span data-ttu-id="9713d-192">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-192">Parameters</span></span>
* <span data-ttu-id="9713d-193">모드: 시뮬레이션 모드: 기본값, 시뮬레이션, 원격, 레거시</span><span class="sxs-lookup"><span data-stu-id="9713d-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="9713d-194">**/api/holographic/simulation/control/stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="9713d-195">컨트롤 스트림을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-195">Delete a control stream.</span></span>

<span data-ttu-id="9713d-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9713d-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="9713d-197">컨트롤 스트림에 대 한 웹 소켓 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="9713d-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="9713d-199">컨트롤 스트림 (우선 순위는 필수)을 만들거나 만든 스트림에 데이터를 게시 합니다 (streamId 필요).</span><span class="sxs-lookup"><span data-stu-id="9713d-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="9713d-200">게시 된 데이터는 ' 응용 프로그램/8 진수 스트림 ' 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="9713d-201">인식 시뮬레이션 재생</span><span class="sxs-lookup"><span data-stu-id="9713d-201">Perception Simulation Playback</span></span>

<span data-ttu-id="9713d-202">**/api/holographic/simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="9713d-203">기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-203">Delete a recording.</span></span>

<span data-ttu-id="9713d-204">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-204">Parameters</span></span>
* <span data-ttu-id="9713d-205">기록할 삭제할 녹음의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="9713d-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="9713d-207">기록을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-207">Upload a recording.</span></span>

<span data-ttu-id="9713d-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="9713d-209">모든 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-209">Get all recordings.</span></span>

<span data-ttu-id="9713d-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="9713d-211">기록의 현재 재생 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="9713d-212">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-212">Parameters</span></span>
* <span data-ttu-id="9713d-213">기록할 기록 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-213">recording : Name of recording.</span></span>

<span data-ttu-id="9713d-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="9713d-215">기록을 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-215">Unload a recording.</span></span>

<span data-ttu-id="9713d-216">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-216">Parameters</span></span>
* <span data-ttu-id="9713d-217">기록할 언로드할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="9713d-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="9713d-219">기록을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-219">Load a recording.</span></span>

<span data-ttu-id="9713d-220">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-220">Parameters</span></span>
* <span data-ttu-id="9713d-221">기록할 로드할 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="9713d-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="9713d-223">로드 된 모든 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-223">Get all loaded recordings.</span></span>

<span data-ttu-id="9713d-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="9713d-225">기록을 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-225">Pause a recording.</span></span>

<span data-ttu-id="9713d-226">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-226">Parameters</span></span>
* <span data-ttu-id="9713d-227">기록할 기록 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-227">recording : Name of recording.</span></span>

<span data-ttu-id="9713d-228">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="9713d-229">기록을 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-229">Play a recording.</span></span>

<span data-ttu-id="9713d-230">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-230">Parameters</span></span>
* <span data-ttu-id="9713d-231">기록할 기록 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-231">recording : Name of recording.</span></span>

<span data-ttu-id="9713d-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="9713d-233">기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-233">Stop a recording.</span></span>

<span data-ttu-id="9713d-234">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-234">Parameters</span></span>
* <span data-ttu-id="9713d-235">기록할 기록 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-235">recording : Name of recording.</span></span>

<span data-ttu-id="9713d-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="9713d-237">로드 된 기록에서 데이터의 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="9713d-238">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-238">Parameters</span></span>
* <span data-ttu-id="9713d-239">기록할 기록 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="9713d-240">인식 시뮬레이션 기록</span><span class="sxs-lookup"><span data-stu-id="9713d-240">Perception Simulation Recording</span></span>

<span data-ttu-id="9713d-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="9713d-242">기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-242">Start a recording.</span></span> <span data-ttu-id="9713d-243">한 번에 하나의 기록만 활성화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="9713d-244">헤드, 손, spatialMapping 또는 환경 중 하나를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="9713d-245">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-245">Parameters</span></span>
* <span data-ttu-id="9713d-246">사장 1로 설정 하 여 헤드 데이터를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="9713d-247">훈련 손으로 데이터를 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="9713d-248">spatialMapping : 을 1로 설정 하 여 공간 매핑을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="9713d-249">개발 환경 데이터를 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="9713d-250">이름의 기록의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-250">name : Name of the recording.</span></span>
* <span data-ttu-id="9713d-251">singleSpatialMappingFrame : 단일 공간 매핑 프레임만 기록 하려면 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="9713d-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="9713d-253">기록 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-253">Get recording state.</span></span>

<span data-ttu-id="9713d-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="9713d-255">현재 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-255">Stop the current recording.</span></span> <span data-ttu-id="9713d-256">기록이 파일로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="9713d-257">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="9713d-257">Mixed Reality Capture</span></span>

<span data-ttu-id="9713d-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="9713d-259">장치에서 혼합 된 현실 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="9713d-260">스트리밍을 위해 op = stream 쿼리 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="9713d-261">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-261">Parameters</span></span>
* <span data-ttu-id="9713d-262">이름도 가져올 비디오 파일의 이름 (hex64)입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="9713d-263">op: stream</span><span class="sxs-lookup"><span data-stu-id="9713d-263">op : stream</span></span>

<span data-ttu-id="9713d-264">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="9713d-265">장치에서 혼합 된 현실 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="9713d-266">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-266">Parameters</span></span>
* <span data-ttu-id="9713d-267">이름도 삭제할 파일의 이름 (hex64)입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="9713d-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="9713d-269">장치에 저장 된 혼합 현실 파일의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="9713d-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="9713d-271">혼합 현실 사진을 사용 하 고 장치에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="9713d-272">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-272">Parameters</span></span>
* <span data-ttu-id="9713d-273">holo: capture holograms: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="9713d-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="9713d-274">pv: PV 카메라 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="9713d-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="9713d-275">RenderFromCamera: (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="9713d-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="9713d-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="9713d-277">기본 혼합 현실 캡처 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="9713d-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="9713d-279">기본 혼합 현실 캡처 설정을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="9713d-280">이러한 설정 중 일부는 시스템의 MRC 사진 및 비디오 캡처에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="9713d-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="9713d-282">기록 된 혼합 현실 상태 (실행 중, 중지 됨)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="9713d-283">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="9713d-284">지정 된 파일에 대 한 미리 보기 이미지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="9713d-285">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-285">Parameters</span></span>
* <span data-ttu-id="9713d-286">이름도 미리 보기를 요청 하는 파일의 이름 (hex64)입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="9713d-287">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="9713d-288">혼합 현실 기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="9713d-289">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-289">Parameters</span></span>
* <span data-ttu-id="9713d-290">holo: capture holograms: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="9713d-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="9713d-291">pv: PV 카메라 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="9713d-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="9713d-292">mic: 마이크 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="9713d-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="9713d-293">루프백: 응용 프로그램 오디오 캡처: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="9713d-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="9713d-294">RenderFromCamera: (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="9713d-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="9713d-295">vstab : (HoloLens 2만 해당) 비디오 안정화 사용: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="9713d-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="9713d-296">vstabbuffer: (HoloLens 2만 해당) 비디오 안정화 버퍼 대기 시간: 0-30 프레임 (기본값은 15 프레임)</span><span class="sxs-lookup"><span data-stu-id="9713d-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="9713d-297">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="9713d-298">현재 혼합 된 현실 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="9713d-299">혼합 현실 스트리밍</span><span class="sxs-lookup"><span data-stu-id="9713d-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="9713d-300">HoloLens는 조각화 된 mp4의 청크 다운로드를 통해 혼합 현실의 실시간 미리 보기를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="9713d-301">혼합 현실 스트림은 동일한 매개 변수 집합을 공유 하 여 캡처할 항목을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="9713d-302">holo: capture holograms: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="9713d-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="9713d-303">pv: PV 카메라 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="9713d-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="9713d-304">mic: 마이크 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="9713d-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="9713d-305">루프백: 앱 오디오 캡처: true 또는 false</span><span class="sxs-lookup"><span data-stu-id="9713d-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="9713d-306">이러한 항목이 지정 되지 않은 경우 holograms, photo/video 카메라 및 앱 오디오가 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="9713d-307">지정 된 경우: 지정 되지 않은 매개 변수는 기본적으로 false로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="9713d-308">선택적 매개 변수 (HoloLens 2에만 해당)</span><span class="sxs-lookup"><span data-stu-id="9713d-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="9713d-309">RenderFromCamera: photo/video 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)</span><span class="sxs-lookup"><span data-stu-id="9713d-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="9713d-310">vstab: 비디오 안정화 사용: true 또는 false (기본값은 false)</span><span class="sxs-lookup"><span data-stu-id="9713d-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="9713d-311">vstabbuffer: 비디오 안정화 버퍼 대기 시간: 0-30 프레임 (기본값은 15 프레임)</span><span class="sxs-lookup"><span data-stu-id="9713d-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="9713d-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="9713d-313">1280x720p 30fps 5Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="9713d-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="9713d-315">1280x720p 30fps 5Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="9713d-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="9713d-317">854x480p 30fps 2.5 Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="9713d-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="9713d-319">428x240p 15fps 0.6 Mbit 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="9713d-320">네트워킹</span><span class="sxs-lookup"><span data-stu-id="9713d-320">Networking</span></span>

<span data-ttu-id="9713d-321">**/sh/svring/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="9713d-322">현재 ip 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="9713d-323">OS 정보</span><span class="sxs-lookup"><span data-stu-id="9713d-323">OS Information</span></span>

<span data-ttu-id="9713d-324">**///s/정보 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="9713d-325">운영 체제 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-325">Gets operating system information</span></span>

<span data-ttu-id="9713d-326">**/api/oss (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="9713d-327">컴퓨터 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-327">Gets the machine name</span></span>

<span data-ttu-id="9713d-328">**/api/oss (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="9713d-329">컴퓨터 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-329">Sets the machine name</span></span>

<span data-ttu-id="9713d-330">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-330">Parameters</span></span>
* <span data-ttu-id="9713d-331">이름의 새 컴퓨터 이름, hex64 인코딩,를로 설정</span><span class="sxs-lookup"><span data-stu-id="9713d-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="9713d-332">성능 데이터</span><span class="sxs-lookup"><span data-stu-id="9713d-332">Performance data</span></span>

<span data-ttu-id="9713d-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="9713d-334">세부 정보를 사용 하 여 실행 중인 프로세스의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="9713d-335">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-335">Return data</span></span>
* <span data-ttu-id="9713d-336">프로세스 목록 및 각 프로세스에 대 한 세부 정보를 포함 하는 JSON</span><span class="sxs-lookup"><span data-stu-id="9713d-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="9713d-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="9713d-338">시스템 성능 통계 (i/o 읽기/쓰기, 메모리 통계 등)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="9713d-339">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-339">Return data</span></span>
* <span data-ttu-id="9713d-340">시스템 정보를 포함 하는 JSON: CPU, GPU, 메모리, 네트워크, IO</span><span class="sxs-lookup"><span data-stu-id="9713d-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="9713d-341">Power</span><span class="sxs-lookup"><span data-stu-id="9713d-341">Power</span></span>

<span data-ttu-id="9713d-342">**/sh/svhhhhhs (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="9713d-343">현재 배터리 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-343">Gets the current battery state</span></span>

<span data-ttu-id="9713d-344">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="9713d-345">시스템이 저전원 상태 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="9713d-346">원격 제어</span><span class="sxs-lookup"><span data-stu-id="9713d-346">Remote Control</span></span>

<span data-ttu-id="9713d-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="9713d-348">대상 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-348">Restarts the target device</span></span>

<span data-ttu-id="9713d-349">**/sh/svcontroli (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="9713d-350">대상 장치를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="9713d-351">작업 관리자</span><span class="sxs-lookup"><span data-stu-id="9713d-351">Task Manager</span></span>

<span data-ttu-id="9713d-352">**/api/taskmanager/app/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="9713d-353">최신 앱을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-353">Stops a modern app</span></span>

<span data-ttu-id="9713d-354">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-354">Parameters</span></span>
* <span data-ttu-id="9713d-355">패키지 Hex64 인코드된 앱 패키지의 전체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="9713d-356">forcestop : 모든 프로세스를 강제로 중지 (= 예)</span><span class="sxs-lookup"><span data-stu-id="9713d-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="9713d-357">**/sh/svaryer/ps (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="9713d-358">최신 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-358">Starts a modern app</span></span>

<span data-ttu-id="9713d-359">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-359">Parameters</span></span>
* <span data-ttu-id="9713d-360">appid 시작 하는 앱의 PRAID, hex64 인코드</span><span class="sxs-lookup"><span data-stu-id="9713d-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="9713d-361">패키지 Hex64 인코드된 앱 패키지의 전체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="9713d-362">WiFi 관리</span><span class="sxs-lookup"><span data-stu-id="9713d-362">WiFi Management</span></span>

<span data-ttu-id="9713d-363">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="9713d-364">무선 네트워크 인터페이스를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="9713d-365">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-365">Return data</span></span>
* <span data-ttu-id="9713d-366">세부 정보를 포함 하는 무선 인터페이스 목록 (GUID, 설명 등)</span><span class="sxs-lookup"><span data-stu-id="9713d-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="9713d-367">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9713d-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="9713d-368">지정 된 인터페이스에서 네트워크와 연결 된 프로필을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="9713d-369">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-369">Parameters</span></span>
* <span data-ttu-id="9713d-370">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="9713d-370">interface : network interface guid</span></span>
* <span data-ttu-id="9713d-371">프로필: 프로필 이름</span><span class="sxs-lookup"><span data-stu-id="9713d-371">profile : profile name</span></span>

<span data-ttu-id="9713d-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="9713d-373">지정 된 네트워크 인터페이스의 무선 네트워크를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="9713d-374">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-374">Parameters</span></span>
* <span data-ttu-id="9713d-375">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="9713d-375">interface : network interface guid</span></span>

<span data-ttu-id="9713d-376">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-376">Return data</span></span>
* <span data-ttu-id="9713d-377">네트워크 인터페이스에서 찾을 수 있는 무선 네트워크 목록 (세부 정보 포함)</span><span class="sxs-lookup"><span data-stu-id="9713d-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="9713d-378">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="9713d-379">지정 된 인터페이스의 네트워크에 연결 하거나 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="9713d-380">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-380">Parameters</span></span>
* <span data-ttu-id="9713d-381">인터페이스: 네트워크 인터페이스 guid</span><span class="sxs-lookup"><span data-stu-id="9713d-381">interface : network interface guid</span></span>
* <span data-ttu-id="9713d-382">ssid: ssid, hex64 인코딩, 연결</span><span class="sxs-lookup"><span data-stu-id="9713d-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="9713d-383">op: 연결 또는 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="9713d-383">op : connect or disconnect</span></span>
* <span data-ttu-id="9713d-384">createprofile: 예 또는 아니요</span><span class="sxs-lookup"><span data-stu-id="9713d-384">createprofile : yes or no</span></span>
* <span data-ttu-id="9713d-385">키: shared key, hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="9713d-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="9713d-386">Windows 성능 레코더</span><span class="sxs-lookup"><span data-stu-id="9713d-386">Windows Performance Recorder</span></span>

<span data-ttu-id="9713d-387">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="9713d-388">WPR 프로필을 업로드 하 고 업로드 된 프로필을 사용 하 여 추적을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="9713d-389">페이로드와</span><span class="sxs-lookup"><span data-stu-id="9713d-389">Payload</span></span>
* <span data-ttu-id="9713d-390">여러 부분으로 구성 되는 http 본문</span><span class="sxs-lookup"><span data-stu-id="9713d-390">multi-part conforming http body</span></span>

<span data-ttu-id="9713d-391">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-391">Return data</span></span>
* <span data-ttu-id="9713d-392">WPR 세션 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-392">Returns the WPR session status.</span></span>

<span data-ttu-id="9713d-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="9713d-394">WPR 세션의 상태를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="9713d-395">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-395">Return data</span></span>
* <span data-ttu-id="9713d-396">WPR 세션 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-396">WPR session status.</span></span>

<span data-ttu-id="9713d-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="9713d-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="9713d-398">WPR (성능) 추적 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="9713d-399">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-399">Return data</span></span>
* <span data-ttu-id="9713d-400">추적 ETL 파일을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-400">Returns the trace ETL file</span></span>

<span data-ttu-id="9713d-401">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="9713d-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="9713d-402">WPR (성능) 추적 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="9713d-403">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9713d-403">Parameters</span></span>
* <span data-ttu-id="9713d-404">profile 프로필 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-404">profile : Profile name.</span></span> <span data-ttu-id="9713d-405">사용 가능한 프로필은 perfprofiles/profile. json에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="9713d-406">데이터 반환</span><span class="sxs-lookup"><span data-stu-id="9713d-406">Return data</span></span>
* <span data-ttu-id="9713d-407">시작 시 WPR 세션 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9713d-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="9713d-408">참조</span><span class="sxs-lookup"><span data-stu-id="9713d-408">See also</span></span>
* [<span data-ttu-id="9713d-409">Windows 디바이스 포털 사용</span><span class="sxs-lookup"><span data-stu-id="9713d-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="9713d-410">장치 포털 핵심 API 참조 (UWP)</span><span class="sxs-lookup"><span data-stu-id="9713d-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
