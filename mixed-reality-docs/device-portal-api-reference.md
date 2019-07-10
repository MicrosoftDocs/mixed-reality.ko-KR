---
title: 장치 포털 API 참조
description: HoloLens에 Windows Device Portal 대 한 API 참조
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694427"
---
# <a name="device-portal-api-reference"></a>장치 포털 API 참조

모든 항목을 [Windows Device Portal](using-the-windows-device-portal.md) 데이터에 액세스 하 고 장치를 프로그래밍 방식으로 제어 하는 데 사용할 수 있는 REST API를 기반으로 작성 됩니다.

## <a name="app-deloyment"></a>앱 배포

**/api/app/packagemanager/package (삭제)**

앱 제거

매개 변수
* 패키지: 제거할 패키지의 파일 이름입니다.

**/api/app/packagemanager/package (게시물)**

앱 설치

매개 변수
* 패키지: 설치할 패키지의 파일 이름입니다.

페이로드
* 표준에 맞는 다중 파트 http 본문

**/api/app/packagemanager/packages (GET)**

세부 정보를 사용 하 여 시스템에 설치 된 앱의 목록을 검색합니다

데이터를 반환 합니다.
* 세부 정보를 사용 하 여 설치 된 패키지 목록

**/api/app/packagemanager/state (GET)**

진행률 앱 설치에서의 상태를 가져옵니다.

## <a name="dump-collection"></a>덤프 컬렉션

**/api/debug/dump/usermode/crashcontrol (삭제)**

사용 하지 않도록 설정 크래시 덤프 수집을 테스트용으로 로드 된 앱에 대 한

매개 변수
* packageFullname: 패키지 이름

**/api/debug/dump/usermode/crashcontrol (GET)**

테스트용 로드 앱에 대 한 설정을 크래시 덤프 수집을 가져옵니다.

매개 변수
* packageFullname: 패키지 이름

**/api/debug/dump/usermode/crashcontrol (게시물)**

사용 하도록 설정 하 고 테스트용으로 로드 된 앱에 대 한 제어 설정을 덤프

매개 변수
* packageFullname: 패키지 이름

**/api/debug/dump/usermode/crashdump (DELETE)**

테스트용 로드 앱에 대 한 크래시 덤프를 삭제합니다.

매개 변수
* packageFullname: 패키지 이름
* fileName: 덤프 파일 이름

**/api/debug/dump/usermode/crashdump (GET)**

테스트용 로드 앱에 대 한 크래시 덤프를 검색합니다.

매개 변수
* packageFullname: 패키지 이름
* fileName: 덤프 파일 이름

데이터를 반환 합니다.
* 덤프 파일입니다. WinDbg 또는 Visual Studio를 사용 하 여 검사

**/api/debug/dump/usermode/dumps (GET)**

테스트용 로드 앱에 대 한 모든 크래시 덤프의 목록을 반환합니다.

데이터를 반환 합니다.
* 쪽 로드 된 앱 당 목록을 크래시 덤프

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

등록 된 공급자를 열거합니다.

데이터를 반환 합니다.
* 공급자, 이름 및 GUID의 목록

**/api/etw/session/realtime (GET/WebSocket)**

실시간 ETW 세션에 만듭니다. websocket을 통해 관리 합니다.

데이터를 반환 합니다.
* 활성화 된 공급자의 ETW 이벤트

## <a name="holographic-os"></a>홀로그램 OS

**/api/holographic/os/etw/customproviders (GET)**

시스템을 사용 하 여 등록 되지 않은 HoloLens 특정 ETW 공급자의 목록을 반환 합니다.

**/api/holographic/os/services (GET)**

실행 중인 모든 서비스의 상태를 반환 합니다.

**/api/holographic/os/settings/ipd (GET)**

밀리미터 단위로 저장된 IPD를 (Interpupillary 거리)를 가져옵니다.

**/api/holographic/os/settings/ipd (POST)**

IPD 설정

매개 변수
* ipd: 밀리미터 단위로 설정 하는 새 IPD 값

**/api/holographic/os/webmanagement/settings/https (GET)**

디바이스 포털에 대한 HTTPS 요구 사항 가져오기

**/api/holographic/os/webmanagement/settings/https (게시물)**

장치 포털에 대 한 HTTPS 요구 사항을 설정합니다

매개 변수
* 필요: 예, 아니요 또는 기본

## <a name="holographic-perception"></a>Holographic 인식

**/api/holographic/perception/client (GET/WebSocket)**

Websocket 업그레이드를 수락 하 고 30fps에서 업데이트를 전송 하는 perception 클라이언트를 실행 합니다.

매개 변수
* clientmode: "활성" 강제로 visual 추적 모드 소극적으로 설정할 수 없는 경우

## <a name="holographic-thermal"></a>Holographic 열

**/api/holographic/thermal/stage (GET)**

장치 (보통 0, 1 웜, 중요 한 2)의 단계는 열 가져오기

## <a name="perception-simulation-control"></a>Perception 시뮬레이션 컨트롤

**/api/holographic/simulation/control/mode (GET)**

시뮬레이션 모드 가져오기

**/api/holographic/simulation/control/mode (게시물)**

시뮬레이션 모드 설정

매개 변수
* 모드: 시뮬레이션 모드: 기본, 시뮬레이션, 원격, 레거시

**/api/holographic/simulation/control/stream (삭제)**

컨트롤 스트림을 삭제 합니다.

**/api/holographic/simulation/control/stream (GET/WebSocket)**

컨트롤 스트림에 대 한 웹 소켓 연결을 엽니다.

**/api/holographic/simulation/control/stream (게시물)**

컨트롤 스트림 만들기 (우선 순위는 필요) (streamId 필요) 만든 스트림에 데이터를 게시 또는 합니다. 게시 된 데이터는 ' 응용 프로그램/옥텟 스트림 ' 형식일 수 해야 합니다.

## <a name="perception-simulation-playback"></a>Perception 시뮬레이션 재생

**/api/holographic/simulation/playback/file (삭제)**

기록을 삭제 합니다.

매개 변수
* 기록: 삭제할 기록의 이름입니다.

**/api/holographic/simulation/playback/file (게시물)**

녹음/녹화를 업로드 합니다.

**/api/holographic/simulation/playback/files (GET)**

모든 녹음/녹화를 가져옵니다.

**/api/holographic/simulation/playback/session (GET)**

기록의 현재 재생 상태를 가져옵니다.

매개 변수
* 기록: 기록의 이름입니다.

**/api/holographic/simulation/playback/session/file (삭제)**

녹음/녹화를 언로드하십시오.

매개 변수
* 기록: 언로드할 기록의 이름입니다.

**/api/holographic/simulation/playback/session/file (게시물)**

녹음/녹화를 로드 합니다.

매개 변수
* 기록: 로드할 기록의 이름입니다.

**/api/holographic/simulation/playback/session/files (GET)**

로드 된 모든 기록을 가져옵니다.

**/api/holographic/simulation/playback/session/pause (게시물)**

기록을 일시 중지 합니다.

매개 변수
* 기록: 기록의 이름입니다.

**/api/holographic/simulation/playback/session/play (게시물)**

녹음/녹화를 재생 합니다.

매개 변수
* 기록: 기록의 이름입니다.

**/api/holographic/simulation/playback/session/stop (게시물)**

녹음/녹화를 중지 합니다.

매개 변수
* 기록: 기록의 이름입니다.

**/api/holographic/simulation/playback/session/types (GET)**

로드 된 기록 데이터 형식을 가져옵니다.

매개 변수
* 기록: 기록의 이름입니다.

## <a name="perception-simulation-recording"></a>Perception 시뮬레이션 기록

**/api/holographic/simulation/recording/start (게시물)**

기록을 시작 합니다. 단일 녹음/녹화를 한 번에 활성화 될 수 있습니다. 헤드, 실습, spatialMapping 또는 환경 중 하나를 설정 해야 합니다.

매개 변수
* 헤드: 헤드 데이터 레코드에는 1로 설정 합니다.
* 실습: 직접 데이터를 기록 하려면 1로 설정 합니다.
* spatialMapping: 레코드 매핑 공간을 1로 설정 합니다.
* 환경: 환경 데이터를 기록 하려면 1로 설정 합니다.
* 이름: 기록의 이름입니다.
* singleSpatialMappingFrame: 단일 공간 매핑을 프레임에만 기록할 1로 설정 합니다.

**/api/holographic/simulation/recording/status (GET)**

가져오기 상태를 기록 합니다.

**/api/holographic/simulation/recording/stop (GET)**

현재 녹음/녹화를 중지 합니다. 기록 파일로 반환 됩니다.

## <a name="mixed-reality-capture"></a>혼합 현실 캡처

**/api/holographic/mrc/file (GET)**

장치에서 혼합된 현실 파일을 다운로드 합니다. 사용 하 여 op = 스트리밍에 대 한 스트림 쿼리 매개 변수입니다.

매개 변수
* 파일 이름: 가져올 비디오 파일의 인코딩 이름 hex64
* op : stream

**/api/holographic/mrc/file (삭제)**

장치에서 기록 하는 혼합된 현실을 삭제 합니다.

매개 변수
* 파일 이름: 삭제할 파일의 인코딩 이름 hex64

**/api/holographic/mrc/files (GET)**

장치에 저장 하는 혼합된 현실 파일 목록을 반환 합니다.

**/api/holographic/mrc/photo (게시물)**

혼합된 현실 사진을 촬영 하 고 장치에서 파일을 만듭니다.

매개 변수
* holo: 홀로그램 캡처: true 또는 false (기본값은 false)
* pv: 캡처 PV 카메라: true 또는 false (기본값은 false)
* RenderFromCamera : 사진/비디오 카메라의 관점에서 렌더링 (HoloLens 2에만 해당): true 또는 false (기본값: true)

**/api/holographic/mrc/settings (GET)**

가져옵니다 기본 혼합 현실을 캡처 설정

**/api/holographic/mrc/settings (게시물)**

집합 기본 혼합 현실을 캡처 설정 합니다.  이러한 설정 중 일부는 시스템의 MRC 사진 및 비디오 캡처에 적용 됩니다.

**/api/holographic/mrc/status (GET)**

혼합된 현실 기록 (실행, 중지)의 상태를 가져옵니다.

**/api/holographic/mrc/thumbnail (GET)**

지정된 된 파일에 대 한 축소판 이미지를 가져옵니다.

매개 변수
* 파일 이름: 미리 보기 요청 되는 파일의 인코딩 이름 hex64

**/api/holographic/mrc/video/control/start (게시물)**

혼합된 현실 녹음/녹화 시작

매개 변수
* holo: 홀로그램 캡처: true 또는 false (기본값은 false)
* pv: 캡처 PV 카메라: true 또는 false (기본값은 false)
* mic: 캡처 마이크: true 또는 false (기본값은 false)
* 루프백: 앱 오디오 캡처: true 또는 false (기본값은 false)
* RenderFromCamera : 사진/비디오 카메라의 관점에서 렌더링 (HoloLens 2에만 해당): true 또는 false (기본값: true)
* vstab : 사용 비디오 안정화 (HoloLens 2에만 해당): true 또는 false (기본값: true)
* vstabbuffer: 비디오 안정화 버퍼 대기 시간 (HoloLens 2에만 해당): 0 ~ 30 프레임 (기본값은 15 프레임)

**/api/holographic/mrc/video/control/stop (게시물)**

중지 현재 혼합 현실 기록

## <a name="mixed-reality-streaming"></a>혼합된 현실 스트리밍

HoloLens는 조각화 된 mp4의 청크 다운로드를 통해 혼합된 현실의 실시간 미리 보기를 지원합니다.

혼합된 현실 스트림이 캡처됩니다 제어 하는 매개 변수의 동일한 집합을 공유 합니다.
* holo: 홀로그램 캡처: true 또는 false
* pv: 캡처 PV 카메라: true 또는 false
* mic: 캡처 마이크: true 또는 false
* 루프백: 앱 오디오 캡처: true 또는 false

지정 된이 없는 경우: 홀로그램, 사진/비디오 카메라 및 앱 오디오를 캡처할 수<br>
지정 된 경우: 지정 되지 않은 매개 변수를 false로 기본값은

선택적 매개 변수 (HoloLens 2에만 해당)
* RenderFromCamera: 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값: true)
* vstab: 비디오 안정화를 사용 하도록 설정: true 또는 false (기본값은 false)
* vstabbuffer: 비디오 안정화 버퍼 대기 시간: 0 ~ 30 프레임 (기본값은 15 프레임)

**/api/holographic/stream/live.mp4 (GET)**

1280x720p 30fps 5Mbit 스트림입니다.

**/api/holographic/stream/live_high.mp4 (GET)**

1280x720p 30fps 5Mbit 스트림입니다.

**/api/holographic/stream/live_med.mp4 (GET)**

854x480p 30fps 2.5Mbit 스트림입니다.

**/api/holographic/stream/live_low.mp4 (GET)**

428x240p 15 fps 0.6Mbit 스트림입니다.

## <a name="networking"></a>네트워킹

**/api/networking/ipconfig (GET)**

현재 ip 구성을 가져옵니다.

## <a name="os-information"></a>OS 정보

**/api/os/info (GET)**

운영 체제 정보를 가져옵니다.

**/api/os/machinename (GET)**

컴퓨터 이름을 가져옵니다.

**/api/os/machinename (게시물)**

컴퓨터 이름 설정

매개 변수
* 이름: 새 컴퓨터 이름으로 설정 하려면 인코딩된 hex64

## <a name="performance-data"></a>성능 데이터

**/api/resourcemanager/processes (GET)**

세부 정보를 사용 하 여 실행 중인 프로세스 목록을 반환 합니다.

데이터를 반환 합니다.
* 프로세스 및 각 프로세스에 대 한 세부 정보 목록 사용 하 여 JSON

**/api/resourcemanager/systemperf (GET)**

(읽기/쓰기 I/O, 메모리 통계 등 시스템 성능 통계를 반환합니다.입니다.

데이터를 반환 합니다.
* 시스템 정보를 사용 하 여 JSON입니다. CPU, GPU, Memory, Network, IO

## <a name="power"></a>전원

**/api/power/battery (GET)**

현재 배터리 상태를 가져옵니다.

**/api/power/state (GET)**

시스템 절전 모드 인지 확인

## <a name="remote-control"></a>원격 제어

**/api/control/restart (게시물)**

대상 장치를 다시 시작

**/api/control/shutdown (게시물)**

대상 장치 종료

## <a name="task-manager"></a>작업 관리자

**/api/taskmanager/app (DELETE)**

최신 앱을 중지합니다.

매개 변수
* 패키지: 인코딩된 hex64 앱 패키지의 전체 이름
* forcestop : 모든 프로세스 중지를 강제 (= yes)

**/api/taskmanager/app (게시물)**

최신 앱을 시작합니다.

매개 변수
* appid: 앱의 시작 PRAID hex64 인코딩
* 패키지: 인코딩된 hex64 앱 패키지의 전체 이름

## <a name="wifi-management"></a>WiFi Management

**/api/wifi/interfaces (GET)**

무선 네트워크 인터페이스를 열거합니다.

데이터를 반환 합니다.
* 세부 정보 (GUID, 설명 등)를 사용 하 여 무선 인터페이스 목록

**/api/wifi/network (DELETE)**

지정된 된 인터페이스에 네트워크와 연결 된 프로필을 삭제 합니다.

매개 변수
* 인터페이스: 네트워크 인터페이스 guid
* 프로필: 프로필 이름

**/api/wifi/networks (GET)**

지정 된 네트워크 인터페이스에서 무선 네트워크를 열거합니다.

매개 변수
* 인터페이스: 네트워크 인터페이스 guid

데이터를 반환 합니다.
* 세부 정보를 사용 하 여 네트워크 인터페이스에 무선 네트워크 목록

**/api/wifi/network (게시물)**

연결 또는 지정된 된 인터페이스의 네트워크로의 연결을 끊습니다.

매개 변수
* 인터페이스: 네트워크 인터페이스 guid
* ssid: ssid, hex64 연결할 인코딩
* op: 연결 또는 연결 끊기
* createprofile: 예 또는 아니요
* 키: 공유 키를 hex64 인코딩

## <a name="windows-performance-recorder"></a>Windows 성능 기록기

**/api/wpr/customtrace (게시물)**

WPR 프로필을 업로드 하 고 업로드 된 프로필을 사용 하 여 추적을 시작 합니다.

페이로드
* 표준에 맞는 다중 파트 http 본문

데이터를 반환 합니다.
* WPR 세션 상태를 반환합니다.

**/api/wpr/status (GET)**

WPR 세션의 상태를 검색합니다.

데이터를 반환 합니다.
* WPR 세션 상태입니다.

**/api/wpr/trace (GET)**

WPR (성능) 추적 세션 중지

데이터를 반환 합니다.
* 추적 ETL 파일을 반환합니다.

**/api/wpr/trace (게시물)**

세션 추적 WPR (성능)를 시작 합니다.

매개 변수
* 프로필: 프로필 이름입니다. 사용 가능한 프로필 perfprofiles/profiles.json에 저장 됩니다.

데이터를 반환 합니다.
* 시작 시 WPR 세션 상태를 반환합니다.

## <a name="see-also"></a>참조
* [Windows 디바이스 포털 사용](using-the-windows-device-portal.md)
* [장치 포털 core API 참조 (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
