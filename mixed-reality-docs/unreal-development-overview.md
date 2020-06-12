---
title: Unreal 개발 개요
description: Unreal Engine 4를 사용하는 혼합 현실 개발의 개요
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 스트리밍, 원격, 혼합 현실, 개발, 시작, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 특징, 홀로그램, 게임 개발
ms.openlocfilehash: 3e3862bd701d6e873f623abc9f9cda0b3085e753
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330160"
---
# <a name="unreal-development-overview"></a>Unreal 개발 개요

<a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="혼합 현실 문서"> 혼합 현실 애플리케이션</a>의 시작은 방대한 작업입니다. 새로운 개념, 플랫폼 및 최첨단 하드웨어가 장애물처럼 느껴질 수 있습니다. 그러나 Unreal 개발자라면 운이 좋습니다. <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality 문서">Windows Mixed Reality</a>(VR) 및 <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="HoloLens 2 문서">HoloLens 2</a>(AR)에 이제 Unreal Engine의 최신 <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 릴리스 정보"> 릴리스</a>가 포함되었습니다. 이 업데이트의 내용은 다음과 같습니다.
* Mixed Reality UX Tools 플러그 인 지원
* OpenXR 지원
* 데스크톱 앱의 앱 원격 작업
* 성능 향상
* 혼합 현실 캡처
* Azure Spatial Anchors 초기 지원

Unreal 개발이 처음이라면 모르는 상태에서 넘어가지 마세요. Unreal <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">자습서 시리즈</a>를 탐색하여 필요한 지식을 갖추고 Unreal <a href="https://www.unrealengine.com/marketplace//store" target="_blank">마켓플레이스</a> 및 혼합 현실 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">포럼</a>에서 자산 및 지원을 모색합니다. 이러한 리소스를 통해 오늘날의 혼합 현실 시장에서 구축자와 문제 해결자 커뮤니티에 연결할 수 있습니다.

## <a name="mixed-reality-toolkit-for-unreal"></a>Unreal용 Mixed Reality Toolkit

[Unreal용 Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unreal)는 Unreal에서의 개발 속도를 높이도록 설계된 구성 요소의 세트입니다. 각 구성 요소에는 몰입형 환경 설정을 위한 플러그 인, 샘플, 설명서가 포함되어 있습니다. 

[Unreal UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)는 릴리스된 첫 번째 구성 요소이며 현재 HoloLens 2에서만 지원됩니다. 구성 요소 플러그 인에는 다음과 같은 공통 UX 기능의 코드, 청사진, 예제 자산이 들어 있습니다.
* 입력 시뮬레이션
* 손 조작 행위자
* 누를 수 있는 단추 구성 요소
* 조작자 구성 요소
* 따르기 동작 구성 요소

기능 세부 정보 및 프로젝트 설정에 대한 정보는 [Unreal용 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) GitHub 리포지토리에서 살펴볼 수 있습니다.

## <a name="tutorial"></a>자습서

새 기술을 익히는 가장 좋은 방법은 직접 무언가를 구축해 보는 것입니다. UX Tools 플러그 인으로 HoloLens 2를 위한 [간단한 체스 앱을 빌드 및 배포](unreal-uxt-ch1.md)하는 방법을 배워보는 것은 좋은 출발이 될 것입니다. 

이 엔드투엔드 자습서 시리즈는 공통 조작 UX 구성 요소와 시나리오에 실습 연결을 제공합니다. 프로젝트 설정, 장면에 조작 추가, 디바이스 또는 에뮬레이터 배포를 작업하게 됩니다. Windows 10, 에뮬레이터 및 Visual Studio 2019만 있으면 됩니다.


## <a name="performance"></a>성능

혼합 현실 개발에서는 플랫폼에 따라 성능 체크포인트가 있습니다. 홀로그램이 안정적이고 표시되고 빠르게 응답하려면 HoloLens 2 앱이 초당 60프레임으로 실행되어야 합니다. 다행이 Unreal은 [성능 권장 사항](performance-recommendations-for-unreal.md)을 제공하므로 애플리케이션에서 이를 달성할 수 있습니다.

## <a name="guides-to-specific-features"></a>특정 기능에 대한 가이드

자습서 시리즈에서 다루지 않은 혼합 현실 개발의 몇 가지 핵심 기능을 제공합니다. 세부 정보 및 실제 애플리케이션은 다음 가이드를 참조하세요. 
* [손 추적](unreal-hand-tracking.md)
* [시선 추적](unreal-gaze-input.md)
* [공간 매핑](unreal-spatial-mapping.md)
* [공간 앵커](unreal-spatial-anchors.md)
* [음성 입력 ](unreal-voice-input.md)
* [HoloLens 카메라](unreal-hololens-camera.md)
* [QR 코드](unreal-qr-codes.md)


## <a name="supported-features"></a>지원되는 기능

| HoloLens 2 기능 | 지원되는 가장 빠른 Unreal Engine 버전 |
| ----------- | ----------- |
| ARM64 지원 | 4.23 |
| PC에서 스트리밍 | 4.23 |
| 공간 매핑 | 4.23 |
| 손 및 관절 추적 | 4.23 |
| 시선 추적 | 4.23 |
| 음성 입력 | 4.23 |
| 공간 앵커 | 4.23 |
| 카메라 액세스 | 4.23 |
| QR 코드 | 4.23 |
| 공간 오디오 | 4.23 |
| 스트리밍을 위한 관람자 화면 지원 | 4.24 |
| 스트리밍을 통한 평면 LSR | 4.24 |
| 샘플 앱([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 및 [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| 모바일 다중 보기: 60FPS 성능 도달 | 4.25 |
| 세 번째 카메라 렌더링 | 4.25 |
| 패키지 데스크톱 앱에서 스트리밍 | 4.25 |
| Azure Spatial Anchors for HoloLens 2(베타) | 4.25 |
| OpenXR 지원(베타) | 4.25 |
| UX Tools 지원(0.8) | 4.25 |
| 개발자 문서 및 자습서 | 4.25 |

## <a name="see-also"></a>참고 항목
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">에뮬레이터 및 디바이스에 스트리밍 및 배포하는 방법에 대한 Unreal 문서</a>
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">모바일 디바이스에 대한 Unreal 성능 지침</a>
