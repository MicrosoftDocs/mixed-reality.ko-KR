---
title: Holographic Remoting 플레이어
description: Holographic 원격 플레이어는 PC 앱과 게임 Holographic 원격 지에 연결 하는 도우미 앱. Holographic 원격 PC에서의 Microsoft HoloLens holographic 콘텐츠를 스트리밍합니다 실시간으로 Wi-fi 연결을 사용 합니다.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605002"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting 플레이어

Holographic 원격 플레이어는 PC 앱과 게임 Holographic 원격 지에 연결 하는 도우미 앱. Holographic 원격 PC에서의 Microsoft HoloLens holographic 콘텐츠를 스트리밍합니다 실시간으로 Wi-fi 연결을 사용 합니다.

Holographic 원격 플레이어 Holographic 원격을 지원 하도록 특별히 설계 된 PC 앱만 사용할 수 있습니다.

> [!NOTE]
> HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.

## <a name="connecting-to-the-holographic-remoting-player"></a>Holographic 원격 플레이어에 게 연결

Holographic 원격 플레이어에 게 연결 하는 앱의 지침을 따릅니다. 다음과 같이 원격 플레이어의 주 화면에서 볼 수 있는 HoloLens 장치, IP 주소를 입력 해야 합니다.

![Holographic Remoting 플레이어](images/holographicremotingplayer.png)

주 화면에 표시 될 때마다 연결 앱 있는지 알 수 있습니다.

Holographic 원격 연결이 보면 **암호화 되지 않은**합니다. 항상 신뢰할 수 있는 보안 Wi-fi 연결을 통해 Holographic Remoting을 사용 해야 합니다.

## <a name="quality-and-performance"></a>품질 및 성능

품질 및 성능을 경험의 세 가지 요인에 따라 달라 집니다.
* **실행 중인 홀로그램 환경** -고해상도 또는 매우 자세한 콘텐츠를 렌더링 하는 앱은 더 빠른 PC 또는 무선 연결을 더 빠르게 필요할 수 있습니다.
* **PC의 하드웨어** -PC를 실행 하 고 초당 60 프레임으로 holographic 환경을 인코딩할 수 해야 합니다. 그래픽 카드에 대 한 일반적으로 GeForce GTX 970 또는 AMD Radeon R9 290 더 나은 권장 합니다. 마찬가지로 특정 환경을 높거나 낮은 엔드 카드가 필요할 수 있습니다.
* **Wi-fi 연결** -holographic 환경을 Wi-fi를 통해 스트리밍됩니다. 품질을 최대화 하기 위해 낮은 정체를 사용 하 여 고속 네트워크를 사용 합니다. 이더넷 케이블을 통해 연결 된 PC를 사용 하 여, Wi-fi, 대신 향상 될 수 있습니다 품질입니다.

## <a name="diagnostics"></a>진단

연결의 품질을 측정 하려면 예를 들어 **"진단 사용"** Holographic 원격 플레이어의 주 화면에 있는 동안에 있습니다. 진단 설정 되 면 앱은 보여 줍니다.
* **FPS** -렌더링 된 프레임의 평균 원격 플레이어 받고 초당 렌더링 됩니다. 60 FPS 것이 가장 좋습니다.
* **대기 시간** -프레임은 HoloLens로 PC에서 하는 데 걸리는 평균 기간입니다. 낮을수록 좋습니다. 이 Wi-fi 네트워크에 따라 크게 좌우 됩니다.

메인 화면에서 말하면 **"진단 사용 안 함"** 진단을 해제 하려면.

## <a name="pc-system-requirements"></a>PC 시스템 요구 사항
* PC **해야** Windows 10 1 주년 업데이트 실행 중 이어야 합니다.
* GeForce GTX 970 또는 AMD Radeon R9 290 더 나은 그래픽 카드는 것이 좋습니다.
* PC를 통해 무선 홉 수를 줄이기 위해 이더넷 네트워크에 연결 하는 것이 좋습니다.

## <a name="see-also"></a>관련 항목
* [Holographic 원격 소프트웨어 사용 조건](microsoft-holographic-remoting-software-license-terms.md)
* [Microsoft 개인정보취급방침](https://go.microsoft.com/fwlink/?LinkId=521839)
