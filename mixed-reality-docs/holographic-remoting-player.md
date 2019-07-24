---
title: Holographic 원격 플레이어
description: Holographic Remoting Player는 Holographic 원격 기능을 지 원하는 PC 앱 및 게임에 연결 하는 동반 앱입니다. Holographic 원격 스트림은 Wi-fi 연결을 사용 하 여 PC에서 실시간으로 Microsoft HoloLens로 콘텐츠를 Holographic 합니다.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813715"
---
# <a name="holographic-remoting-player"></a>Holographic 원격 플레이어

Holographic Remoting Player는 Holographic 원격 기능을 지 원하는 PC 앱 및 게임에 연결 하는 동반 앱입니다. Holographic 원격 스트림은 Wi-fi 연결을 사용 하 여 PC에서 실시간으로 Microsoft HoloLens로 콘텐츠를 Holographic 합니다.

Holographic 원격 플레이어는 Holographic 원격을 지원 하도록 특별히 설계 된 PC 앱 에서만 사용할 수 있습니다.

Holographic 원격 플레이어는 HoloLens와 HoloLens 2 모두에 대해 사용할 수 있습니다.  HoloLens를 사용 하 여 Holographic Remoting을 지 원하는 PC 앱은 HoloLens 2와 Holographic Remtoing를 지원 하도록 업데이트 해야 합니다.  지원 되는 버전에 대 한 질문이 있으면 앱 공급자에 게 문의 하세요.

## <a name="connecting-to-the-holographic-remoting-player"></a>Holographic Remoting 플레이어에 연결

앱의 지침에 따라 Holographic Remoting 플레이어에 연결 합니다. 다음과 같이 원격 플레이어의 주 화면에서 볼 수 있는 HoloLens 장치의 IP 주소를 입력 해야 합니다.

![Holographic 원격 플레이어](images/holographicremotingplayer.png)

주 화면이 표시 될 때마다 앱이 연결 되어 있지 않은 것을 알 수 있습니다.

Holographic 원격 연결은 **암호화 되지 않습니다**. 신뢰 하는 보안 Wi-fi 연결을 통해 항상 Holographic Remoting을 사용 해야 합니다.

## <a name="quality-and-performance"></a>품질 및 성능

사용자 환경의 품질 및 성능은 다음과 같은 세 가지 요인에 따라 달라 집니다.
* **실행 중인 holographic 환경** -고해상도 또는 매우 상세 콘텐츠를 렌더링 하는 앱은 더 빠른 PC 또는 더 빠른 무선 연결을 필요로 할 수 있습니다.
* **Pc의 하드웨어** -pc는 초당 60 프레임에서 holographic 환경을 실행 하 고 인코딩할 수 있어야 합니다. 그래픽 카드의 경우 일반적으로 GeForce GTX 970 또는 AMD Radeon R 9 290 이상을 권장 합니다. 또한 특정 환경에는 더 높거나 낮은 끝 카드가 필요할 수 있습니다.
* **Wi-fi 연결** -Holographic 환경이 wi-fi를 통해 스트리밍됩니다. 낮은 혼잡이 있는 고속 네트워크를 사용 하 여 품질을 최대화 합니다. Wi-fi가 아닌 이더넷 케이블을 통해 연결 된 PC를 사용 하면 품질이 향상 될 수도 있습니다.

## <a name="diagnostics"></a>진단

연결의 품질을 측정 하려면 Holographic 원격 플레이어의 주 화면에 있는 동안 **"진단 사용"** 이라고 표시 합니다. 진단을 사용 하도록 설정 하면 앱에 다음이 표시 됩니다.
* **FPS** -원격 플레이어에서 초당 수신 및 렌더링 하는 렌더링 된 프레임의 평균 수입니다. 이상적인는 60 FPS입니다.
* **대기 시간** -프레임이 PC에서 HoloLens로 이동 하는 데 걸리는 평균 시간입니다. 더 낮은 방법이 있습니다. 이는 주로 Wi-fi 네트워크에 따라 다릅니다.

주 화면에서 **"진단 사용 안 함"** 을 사용 하 여 진단을 해제할 수 있습니다.

## <a name="pc-system-requirements"></a>PC 시스템 요구 사항
* PC에서 Windows 10 기념일 업데이트 이상을 실행 하 고 **있어야** 합니다.
* GeForce GTX 970 또는 AMD Radeon R 9 290 이상의 그래픽 카드를 권장 합니다.
* 무선 홉 수를 줄이려면 이더넷을 통해 PC를 네트워크에 연결 하는 것이 좋습니다.

## <a name="see-also"></a>관련 항목
* [홀로그램 원격 소프트웨어 사용 조건](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인 정보 취급 방침](https://go.microsoft.com/fwlink/?LinkId=521839)
