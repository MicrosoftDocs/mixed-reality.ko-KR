---
title: 장치 포털 API 참조
description: HoloLens의 Windows 장치 포털에 대 한 API 참조
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows 장치 포털, API
ms.openlocfilehash: 236de35c2c736fc5a0289b7be1f1548f0a08fa26
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278241"
---
# <a name="device-portal-api-reference"></a>장치 포털 API 참조

[Windows 장치 포털](using-the-windows-device-portal.md) 의 모든 항목은 데이터에 액세스 하 고 프로그래밍 방식으로 장치를 제어 하는 데 사용할 수 있는 REST API의 맨 위에 빌드됩니다.

## <a name="app-deloyment"></a>앱 배포

**/api/app/packagemanager/package (DELETE)**

앱을 제거 합니다.

매개 변수
* package: 제거할 패키지의 파일 이름입니다.

**/api/app/packagemanager/package (POST)**

앱을 설치 합니다.

매개 변수
* package: 설치할 패키지의 파일 이름입니다.

페이로드
* 여러 부분으로 구성 되는 http 본문

**/api/app/packagemanager/packages (GET)**

세부 정보를 사용 하 여 시스템에 설치 된 앱 목록을 검색 합니다.

데이터 반환
* 세부 정보가 포함 된 설치 된 패키지 목록

**/api/app/packagemanager/state (GET)**

진행 중인 앱 설치의 상태를 가져옵니다.

## <a name="dump-collection"></a>덤프 컬렉션

**/api/debug/dump/usermode/crashcontrol (DELETE)**

테스트용으로 로드 앱에 대 한 크래시 덤프 수집 사용 안 함

매개 변수
* packageFullname: 패키지 이름

**/api/debug/dump/usermode/crashcontrol (GET)**

테스트용으로 로드 apps 크래시 덤프 컬렉션에 대 한 설정을 가져옵니다.

매개 변수
* packageFullname: 패키지 이름

**/api/debug/dump/usermode/crashcontrol (POST)**

테스트용으로 로드 앱에 대 한 덤프 제어 설정을 사용 하도록 설정 하 고 설정 합니다.

매개 변수
* packageFullname: 패키지 이름

**/api/debug/dump/usermode/crashdump (DELETE)**

테스트용으로 로드 앱에 대 한 크래시 덤프를 삭제 합니다.

매개 변수
* packageFullname: 패키지 이름
* 파일 이름: 덤프 파일 이름

**/api/debug/dump/usermode/crashdump (GET)**

테스트용으로 로드 앱에 대 한 크래시 덤프를 검색 합니다.

매개 변수
* packageFullname: 패키지 이름
* 파일 이름: 덤프 파일 이름

데이터 반환
* 덤프 파일입니다. WinDbg 또는 Visual Studio를 사용 하 여 검사

**/api/debug/dump/usermode/dumps (GET)**

테스트용으로 로드 apps에 대 한 모든 크래시 덤프 목록을 반환 합니다.

데이터 반환
* 테스트용으로 로드 된 앱 당 크래시 덤프 목록

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

등록 된 공급자를 열거 합니다.

데이터 반환
* 공급자 목록, 이름 및 GUID

**/api/etw/session/realtime (GET/WebSocket)**

실시간 ETW 세션을 만듭니다. websocket을 통해 관리 됩니다.

데이터 반환
* 활성화 된 공급자의 ETW 이벤트

## <a name="holographic-os"></a>홀로그램 OS

**/api/holographic/os/etw/customproviders (GET)**

시스템에 등록 되지 않은 HoloLens 특정 ETW 공급자 목록을 반환 합니다.

**/api/holographic/os/services (GET)**

실행 중인 모든 서비스의 상태를 반환 합니다.

**/api/holographic/os/settings/ipd (GET)**

저장 된 IPD (Interpupillary distance)를 밀리미터 단위로 가져옵니다.

**/api/holographic/os/settings/ipd (POST)**

IPD를 설정 합니다.

매개 변수
* ipd: 밀리미터로 지정할 New IPD 값입니다.

**/api/holographic/os/webmanagement/settings/https (GET)**

디바이스 포털에 대한 HTTPS 요구 사항 가져오기

**/api/holographic/os/webmanagement/settings/https (POST)**

장치 포털에 대 한 HTTPS 요구 사항을 설정 합니다.

매개 변수
* 필수: 예, 아니요 또는 기본값

## <a name="holographic-perception"></a>Holographic 인식

**/api/holographic/perception/client (GET/WebSocket)**

Websocket 업그레이드를 수락 하 고 30fps로 업데이트를 전송 하는 인식 클라이언트를 실행 합니다.

매개 변수
* clientmode: "활성"은 동적으로 설정할 수 없는 경우 시각적 추적 모드를 강제로 실행 합니다.

## <a name="holographic-thermal"></a>Holographic 열

**/api/holographic/thermal/stage (GET)**

장치의 열 단계 가져오기 (0 보통, 1 웜, 2 개 위험)

## <a name="perception-simulation-control"></a>인식 시뮬레이션 컨트롤

**/api/holographic/simulation/control/mode (GET)**

시뮬레이션 모드 가져오기

**/api/holographic/simulation/control/mode (POST)**

시뮬레이션 모드 설정

매개 변수
* 모드: 시뮬레이션 모드: 기본값, 시뮬레이션, 원격, 레거시

**/api/holographic/simulation/control/stream (DELETE)**

컨트롤 스트림을 삭제 합니다.

**/api/holographic/simulation/control/stream (GET/WebSocket)**

컨트롤 스트림에 대 한 웹 소켓 연결을 엽니다.

**/api/holographic/simulation/control/stream (POST)**

컨트롤 스트림 (우선 순위는 필수)을 만들거나 만든 스트림에 데이터를 게시 합니다 (streamId 필요). 게시 된 데이터는 ' 응용 프로그램/8 진수 스트림 ' 형식 이어야 합니다.

## <a name="perception-simulation-playback"></a>인식 시뮬레이션 재생

**/api/holographic/simulation/playback/file (DELETE)**

기록을 삭제 합니다.

매개 변수
* 녹음/녹화: 삭제할 기록의 이름입니다.

**/api/holographic/simulation/playback/file (POST)**

기록을 업로드 합니다.

**/api/holographic/simulation/playback/files (GET)**

모든 기록을 가져옵니다.

**/api/holographic/simulation/playback/session (GET)**

기록의 현재 재생 상태를 가져옵니다.

매개 변수
* 기록: 기록의 이름입니다.

**/api/holographic/simulation/playback/session/file (DELETE)**

기록을 언로드합니다.

매개 변수
* 녹음/녹화: 언로드할 기록의 이름입니다.

**/api/holographic/simulation/playback/session/file (POST)**

기록을 로드 합니다.

매개 변수
* 기록: 로드할 기록의 이름입니다.

**/api/holographic/simulation/playback/session/files (GET)**

로드 된 모든 기록을 가져옵니다.

**/api/holographic/simulation/playback/session/pause (POST)**

기록을 일시 중지 합니다.

매개 변수
* 기록: 기록의 이름입니다.

**/api/holographic/simulation/playback/session/play (POST)**

기록을 재생 합니다.

매개 변수
* 기록: 기록의 이름입니다.

**/api/holographic/simulation/playback/session/stop (POST)**

기록을 중지 합니다.

매개 변수
* 기록: 기록의 이름입니다.

**/api/holographic/simulation/playback/session/types (GET)**

로드 된 기록에서 데이터의 형식을 가져옵니다.

매개 변수
* 기록: 기록의 이름입니다.

## <a name="perception-simulation-recording"></a>인식 시뮬레이션 기록

**/api/holographic/simulation/recording/start (POST)**

기록을 시작 합니다. 한 번에 하나의 기록만 활성화 될 수 있습니다. 헤드, 손, spatialMapping 또는 환경 중 하나를 설정 해야 합니다.

매개 변수
* head: 1로 설정 하 여 헤드 데이터를 기록 합니다.
* 실습: 1로 설정 하 여 손으로 데이터를 기록 합니다.
* spatialMapping: 1로 설정 하 여 공간 매핑을 기록 합니다.
* 환경: 환경 데이터를 기록 하려면 1로 설정 합니다.
* 이름: 기록의 이름입니다.
* singleSpatialMappingFrame: 단일 공간 매핑 프레임만 기록 하려면 1로 설정 합니다.

**/api/holographic/simulation/recording/status (GET)**

기록 상태를 가져옵니다.

**/api/holographic/simulation/recording/stop (GET)**

현재 기록을 중지 합니다. 기록이 파일로 반환 됩니다.

## <a name="mixed-reality-capture"></a>혼합 현실 캡처

**/api/holographic/mrc/file (GET)**

장치에서 혼합 된 현실 파일을 다운로드 합니다. 스트리밍을 위해 op = stream 쿼리 매개 변수를 사용 합니다.

매개 변수
* filename: hex64로 인코딩된 비디오 파일의 이름입니다.
* op: stream

**/api/holographic/mrc/file (DELETE)**

장치에서 혼합 된 현실 기록을 삭제 합니다.

매개 변수
* filename: 삭제할 파일의 이름 (hex64)입니다.

**/api/holographic/mrc/files (GET)**

장치에 저장 된 혼합 현실 파일의 목록을 반환 합니다.

**/api/holographic/mrc/photo (POST)**

혼합 현실 사진을 사용 하 고 장치에 파일을 만듭니다.

매개 변수
* holo: capture holograms: true 또는 false (기본값은 false)
* pv: PV 카메라 캡처: true 또는 false (기본값은 false)
* RenderFromCamera: (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)

**/api/holographic/mrc/settings (GET)**

기본 혼합 현실 캡처 설정을 가져옵니다.

**/api/holographic/mrc/settings (POST)**

기본 혼합 현실 캡처 설정을 설정 합니다.  이러한 설정 중 일부는 시스템의 MRC 사진 및 비디오 캡처에 적용 됩니다.

**/api/holographic/mrc/status (GET)**

기록 된 혼합 현실 상태 (실행 중, 중지 됨)를 가져옵니다.

**/api/holographic/mrc/thumbnail (GET)**

지정 된 파일에 대 한 미리 보기 이미지를 가져옵니다.

매개 변수
* 파일 이름: 미리 보기를 요청 하는 파일의 이름 (hex64)입니다.

**/api/holographic/mrc/video/control/start (POST)**

혼합 현실 기록을 시작 합니다.

매개 변수
* holo: capture holograms: true 또는 false (기본값은 false)
* pv: PV 카메라 캡처: true 또는 false (기본값은 false)
* mic: 마이크 캡처: true 또는 false (기본값은 false)
* 루프백: 응용 프로그램 오디오 캡처: true 또는 false (기본값은 false)
* RenderFromCamera: (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)
* vstab: (HoloLens 2만 해당) 비디오 안정화 사용: true 또는 false (기본값은 true)
* vstabbuffer: (HoloLens 2만 해당) 비디오 안정화 버퍼 대기 시간: 0-30 프레임 (기본값은 15 프레임)

**/api/holographic/mrc/video/control/stop (POST)**

현재 혼합 된 현실 기록을 중지 합니다.

## <a name="mixed-reality-streaming"></a>혼합 현실 스트리밍

HoloLens는 조각화 된 mp4의 청크 다운로드를 통해 혼합 현실의 실시간 미리 보기를 지원 합니다.

혼합 현실 스트림은 동일한 매개 변수 집합을 공유 하 여 캡처할 항목을 제어 합니다.
* holo: capture holograms: true 또는 false
* pv: PV 카메라 캡처: true 또는 false
* mic: 마이크 캡처: true 또는 false
* 루프백: 앱 오디오 캡처: true 또는 false

이러한 항목이 지정 되지 않은 경우 holograms, photo/video 카메라 및 앱 오디오가 캡처됩니다.<br>
지정 된 경우: 지정 되지 않은 매개 변수는 기본적으로 false로 설정 됩니다.

선택적 매개 변수 (HoloLens 2에만 해당)
* RenderFromCamera: photo/video 카메라의 관점에서 렌더링: true 또는 false (기본값은 true)
* vstab: 비디오 안정화 사용: true 또는 false (기본값은 false)
* vstabbuffer: 비디오 안정화 버퍼 대기 시간: 0-30 프레임 (기본값은 15 프레임)

**/api/holographic/stream/live.mp4 (GET)**

1280x720p 30fps 5Mbit 스트림입니다.

**/api/holographic/stream/live_high. mp4 (GET)**

1280x720p 30fps 5Mbit 스트림입니다.

**/api/holographic/stream/live_med. mp4 (GET)**

854x480p 30fps 2.5 Mbit 스트림입니다.

**/api/holographic/stream/live_low. mp4 (GET)**

428x240p 15fps 0.6 Mbit 스트림입니다.

## <a name="networking"></a>네트워킹

**/sh/svring/ipconfig (GET)**

현재 ip 구성을 가져옵니다.

## <a name="os-information"></a>OS 정보

**///s/정보 (GET)**

운영 체제 정보를 가져옵니다.

**/api/oss (GET)**

컴퓨터 이름을 가져옵니다.

**/api/oss (POST)**

컴퓨터 이름을 설정 합니다.

매개 변수
* 이름: 새 컴퓨터 이름, hex64 인코딩,를로 설정

## <a name="performance-data"></a>성능 데이터

**/api/resourcemanager/processes (GET)**

세부 정보를 사용 하 여 실행 중인 프로세스의 목록을 반환 합니다.

데이터 반환
* 프로세스 목록 및 각 프로세스에 대 한 세부 정보를 포함 하는 JSON

**/api/resourcemanager/systemperf (GET)**

시스템 성능 통계 (i/o 읽기/쓰기, 메모리 통계 등)를 반환 합니다.

데이터 반환
* 시스템 정보를 포함 하는 JSON: CPU, GPU, 메모리, 네트워크, IO

## <a name="power"></a>전원

**/sh/svhhhhhs (GET)**

현재 배터리 상태를 가져옵니다.

**/api/power/state (GET)**

시스템이 저전원 상태 인지 여부를 확인 합니다.

## <a name="remote-control"></a>원격 제어

**/api/control/restart (POST)**

대상 장치를 다시 시작 합니다.

**/sh/svcontroli (POST)**

대상 장치를 종료 합니다.

## <a name="task-manager"></a>작업 관리자

**/api/taskmanager/app/app (DELETE)**

최신 앱을 중지 합니다.

매개 변수
* 패키지: 앱 패키지의 전체 이름, hex64 인코드
* forcestop: 모든 프로세스를 강제로 중지 합니다 (= 예).

**/sh/svaryer/ps (POST)**

최신 앱을 시작 합니다.

매개 변수
* appid: 시작 하는 앱의 PRAID, hex64 인코드
* 패키지: 앱 패키지의 전체 이름, hex64 인코드

## <a name="wifi-management"></a>WiFi 관리

**/api/wifi/interfaces (GET)**

무선 네트워크 인터페이스를 열거 합니다.

데이터 반환
* 세부 정보를 포함 하는 무선 인터페이스 목록 (GUID, 설명 등)

**/api/wifi/network (DELETE)**

지정 된 인터페이스에서 네트워크와 연결 된 프로필을 삭제 합니다.

매개 변수
* 인터페이스: 네트워크 인터페이스 guid
* 프로필: 프로필 이름

**/api/wifi/networks (GET)**

지정 된 네트워크 인터페이스의 무선 네트워크를 열거 합니다.

매개 변수
* 인터페이스: 네트워크 인터페이스 guid

데이터 반환
* 네트워크 인터페이스에서 찾을 수 있는 무선 네트워크 목록 (세부 정보 포함)

**/api/wifi/network (POST)**

지정 된 인터페이스의 네트워크에 연결 하거나 연결을 끊습니다.

매개 변수
* 인터페이스: 네트워크 인터페이스 guid
* ssid: ssid, hex64 인코딩, 연결
* op: 연결 또는 연결 끊기
* createprofile: 예 또는 아니요
* 키: shared key, hex64 encoded

## <a name="windows-performance-recorder"></a>Windows 성능 레코더

**/api/wpr/customtrace (POST)**

WPR 프로필을 업로드 하 고 업로드 된 프로필을 사용 하 여 추적을 시작 합니다.

페이로드
* 여러 부분으로 구성 되는 http 본문

데이터 반환
* WPR 세션 상태를 반환 합니다.

**/api/wpr/status (GET)**

WPR 세션의 상태를 검색 합니다.

데이터 반환
* WPR 세션 상태입니다.

**/api/wpr/trace (GET)**

WPR (성능) 추적 세션을 중지 합니다.

데이터 반환
* 추적 ETL 파일을 반환 합니다.

**/api/wpr/trace (POST)**

WPR (성능) 추적 세션을 시작 합니다.

매개 변수
* 프로필: 프로필 이름입니다. 사용 가능한 프로필은 perfprofiles/profile. json에 저장 됩니다.

데이터 반환
* 시작 시 WPR 세션 상태를 반환 합니다.

## <a name="see-also"></a>참고 항목
* [Windows 디바이스 포털 사용](using-the-windows-device-portal.md)
* [장치 포털 핵심 API 참조 (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
