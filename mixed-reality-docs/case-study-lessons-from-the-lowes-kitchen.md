---
title: 사례 연구-Lowe의 부엌 단원
description: HoloLens 팀은 Lowe의 HoloLens 프로젝트에서 파생 된 몇 가지 모범 사례를 공유 하려고 합니다.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe의, HoloLens, 주방, 사례 연구
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278131"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>사례 연구-Lowe의 부엌 단원

HoloLens 팀은 Lowe의 HoloLens 프로젝트에서 파생 된 몇 가지 모범 사례를 공유 하려고 합니다. 다음은 Satya의 2016 Ignite 키 노트에서 보여 주는 Lowe의 HoloLens에 대 한 비디오입니다.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Lowe의 HoloLens 모범 사례

두 개의 비디오에서는 4 월 2016 이후 두 Lowe의 상점에 있었던 Lowe의 HoloLens 파일럿에서 파생 된 모범 사례를 다룹니다. 주요 항목은 다음과 같습니다.
* 모바일 장치에 대 한 성능 최대화
* Full holographic 프레임을 사용 하 여 UX 메서드 만들기 (2 차 통신)
* 전체 자릿수 맞춤 (두 번째 대화)
* 공유 holographic 환경 (두 번째 대화)
* 고객과 상호 작용 (두 번째 대화)

## <a name="video-1"></a>비디오 1

**모바일 장치에 대 한 성능 최대화** HoloLens는 장치에서 모든 처리가 발생 하는 작업할 장치입니다. 모바일 플랫폼이 필요 하며 모바일 응용 프로그램을 만드는 것과 비슷한 마음가짐이 필요 합니다. 사용자에 게 맛 있는 환경을 제공 하기 위해 HoloLens 응용 프로그램에서 60FPS를 유지 관리 하는 것이 좋습니다. FPS가 낮으면 holograms가 불안정 해질 수 있습니다.

HoloLens에서 개발할 때 고려할 가장 중요 한 사항은 사용자 지정 셰이더 ( [Hololens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)에서 무료로 제공)를 사용 하 여 자산 최적화/decimation입니다. 또 다른 중요 한 고려 사항은 프로젝트의 시작 부분에서 프레임 속도로 측정 하는 것입니다. 프로젝트에 따라 자산을 표시 하는 순서가 큰 참가자로 될 수도 있습니다.
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>비디오 2

**전체 holographic 프레임으로 UX 메서드 만들기** 실제 세계의 holograms 배치를 이해 하는 것이 중요 합니다. Lowe는 holograms의 더 큰 환경을 볼 때 사용자가 holograms 경험 하는 데 도움이 되는 다양 한 UX 방법에 대해 이야기 합니다.

**전체 자릿수 맞춤** Lowe의 시나리오에서 실제 부엌에 대 한 holograms의 전체 자릿수 맞춤을 구현 하는 것이 가장 중요 했습니다. Microsoft는 사용자가 물리적 환경에서 변경한 유도 환경을 보장 하는 데 도움이 되는 기술에 대해 설명 합니다.

**공유 holographic 환경** 결합는 Lowe의 경험을 사용 하는 기본 방법입니다. 한 사람이 상판를 변경 하 고 다른 사용자가 변경 내용을 볼 수 있습니다. 이 "공유 환경" 이라고 합니다.

**고객과 상호 작용** Lowe의 디자이너는 HoloLens를 사용 하지 않지만 고객이 볼 수 있는 항목을 확인 해야 합니다. Microsoft는 UWP 응용 프로그램에서 고객이 볼 수 있는 사항을 캡처하는 방법을 보여 줍니다.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
