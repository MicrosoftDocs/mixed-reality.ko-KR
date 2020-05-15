---
title: Unreal 개발 개요
description: Unreal Engine 4를 사용하는 혼합 현실 개발의 개요
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 스트리밍, 원격, 혼합 현실, 개발, 시작, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 특징, 홀로그램
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851567"
---
# <a name="unreal-development-overview"></a>Unreal 개발 개요

이제 Unreal Engine 4는 Windows VR(Mixed Reality) 및 HoloLens 2(AR) 디바이스용 앱 개발을 완벽하게 지원합니다. Unreal 개발을 처음 접하는 경우 <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Unreal Engine 4 시작</a> 페이지를 살펴보세요. 자산이 필요한 경우 Unreal에는 포괄적인 <a href="https://www.unrealengine.com/marketplace//store" target="_blank">마켓플레이스</a>가 있습니다. 

Unreal 개발의 기본 사항을 이해했으면 다음 섹션의 자습서를 확인하여 HoloLens에서 앱을 빌드하고 실행하는 방법을 알아보세요. <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality 포럼</a>을 방문하여 Unreal에서 혼합 현실 앱을 빌드하는 커뮤니티에 참여하세요. 발생하는 문제의 해결 방법을 찾기에 가장 좋은 장소입니다.

## <a name="tutorial"></a>자습서

통합형 자습서를 따라 HoloLens 2용 [간단한 체스 앱을 빌드 및 배포](unreal-uxt-ch1.md)하는 방법에 대해 알아봅니다. 이 자습서에서는 UX Tools 플러그 인을 사용하여 단추와 조작자를 비롯한 대화형 UX 구성 요소를 사용하여 빠르게 앱을 개발합니다. UX Tools 플러그 인에 대한 자세한 내용은 MRTK에 대한 다음 섹션을 참조하세요. 

## <a name="mixed-reality-toolkit-for-unreal"></a>Unreal용 Mixed Reality Toolkit

[Unreal용 Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unreal)은 플러그인, 샘플 및 설명서의 형태로 구성된 구성 요소 세트로, Unreal Engine을 사용하여 혼합 현실 애플리케이션을 빠르게 개발할 수 있도록 설계되었습니다. 이 도구 키트의 일부로 출시된 첫 번째 구성 요소는 HoloLens 2 프로젝트에 추가하여 HoloLens 2 애플리케이션을 위한 UX 기능을 제공할 수 있는 플러그 인인 [Unreal용 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)입니다. Mixed Reality Toolkit 및 Unreal용 UX Tools에 대한 설명서는 각각의 GitHub 리포지토리에서 찾을 수 있습니다. 

## <a name="performance"></a>성능

홀로그램이 안정적이고 표시되고 빠르게 응답하려면 HoloLens 2 앱이 초당 60프레임으로 실행되어야 합니다. 앱에서 이 속도를 구현하려면 [Unreal을 사용하기 위한 권장 성능](performance-recommendations-for-unreal.md)을 따르는 것이 좋습니다. 

## <a name="guides-to-specific-features"></a>특정 기능에 대한 가이드

Unreal의 특정 기능을 사용하는 방법을 알아보려면 아래 가이드를 확인하세요. 
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
