---
title: 홀로그램 원격 플레이어
description: Holographic Remoting Player는 Holographic 원격 기능을 지 원하는 PC 앱 및 게임에 연결 하는 동반 앱입니다. Holographic 원격 스트림은 Wi-fi 연결을 사용 하 여 PC에서 실시간으로 Microsoft HoloLens로 콘텐츠를 Holographic 합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 8b1d58b2c2ce8f379a87059bb5add0f85f507259
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061136"
---
# <a name="holographic-remoting-player"></a>홀로그램 원격 플레이어

>[!IMPORTANT]
>HoloLens 2에 대 한 Holographic 원격은 주요 버전 변경입니다. [Hololens 용 원격 응용 프로그램 **(첫 번째 gen)** ](add-holographic-remoting.md) 은 NuGet 패키지 **버전 1.x** 를 사용 해야 하며, [hololens 용 원격 응용 프로그램 **2** 는](holographic-remoting-create-host.md) 2.x를 사용 해야 합니다. x **. x.** 즉, HoloLens 2 용으로 작성 된 원격 응용 프로그램은 HoloLens (첫 번째 gen)와 호환 되지 않으며 그 반대의 경우도 마찬가지입니다.

[Holographic Remoting Player](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) 는 Holographic 원격 기능을 지 원하는 PC 앱 및 게임에 연결 하는 동반 앱입니다. Holographic 원격 스트림은 Wi-fi 연결을 사용 하 여 PC에서 실시간으로 Microsoft HoloLens로 콘텐츠를 Holographic 합니다.

Holographic 원격 플레이어는 Holographic 원격을 지원 하도록 특별히 설계 된 PC 앱 에서만 사용할 수 있습니다.

Holographic 원격 플레이어는 HoloLens (첫 번째 gen)와 HoloLens 2 모두에 대해 사용할 수 있습니다.  HoloLens를 사용 하 여 Holographic Remoting을 지 원하는 PC 앱은 HoloLens 2를 사용 하는 Holographic Remoting을 지원 하도록 업데이트 해야 합니다. 지원 되는 버전에 대 한 질문이 있으면 앱 공급자에 게 문의 하세요.

>[!TIP]
>[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 Holographic 원격 플레이어는 [windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)를 실행 하는 windows pc 에서도 사용할 수 있습니다.

## <a name="connecting-to-the-holographic-remoting-player"></a>Holographic Remoting 플레이어에 연결

앱의 지침에 따라 Holographic Remoting 플레이어에 연결 합니다. 다음과 같이 원격 플레이어의 기본 화면에서 볼 수 있는 HoloLens 장치의 IP 주소를 입력 해야 합니다.

![홀로그램 원격 플레이어](images/holographicremotingplayer.png)

주 화면이 표시 될 때마다 앱이 연결 되어 있지 않은 것을 알 수 있습니다.

Holographic 원격 연결은 **암호화 되지 않습니다**. 신뢰 하는 보안 Wi-fi 연결을 통해 항상 Holographic Remoting을 사용 해야 합니다.

## <a name="quality-and-performance"></a>품질 및 성능

사용자 환경의 품질 및 성능은 다음과 같은 세 가지 요인에 따라 달라 집니다.
* **실행 중인 holographic 환경** -고해상도 또는 매우 상세 콘텐츠를 렌더링 하는 앱은 더 빠른 PC 또는 더 빠른 무선 연결을 필요로 할 수 있습니다.
* **Pc의 하드웨어** -pc는 초당 60 프레임에서 holographic 환경을 실행 하 고 인코딩할 수 있어야 합니다. 그래픽 카드의 경우 일반적으로 GeForce GTX 970 또는 AMD Radeon R 9 290 이상을 권장 합니다. 또한 특정 환경에는 더 높거나 낮은 끝 카드가 필요할 수 있습니다.
* **Wi-fi 연결** -Holographic 환경이 wi-fi를 통해 스트리밍됩니다. 낮은 혼잡이 있는 고속 네트워크를 사용 하 여 품질을 최대화 합니다. Wi-fi가 아닌 이더넷 케이블을 통해 연결 된 PC를 사용 하면 품질이 향상 될 수도 있습니다.

## <a name="diagnostics"></a>진단

연결의 품질을 측정 하려면 Holographic 원격 플레이어의 주 화면에 있는 동안 **"진단 사용"** 이라고 표시 합니다. 진단을 사용 하도록 설정 하면 **HoloLens (첫 번째 gen)** 에서 앱이 다음과 같이 표시 됩니다.

* **FPS** -원격 플레이어에서 초당 수신 및 렌더링 하는 렌더링 된 프레임의 평균 수입니다. 이상적인는 60 FPS입니다.
* **대기 시간** -프레임이 PC에서 HoloLens로 이동 하는 데 걸리는 평균 시간입니다. 더 낮은 방법이 있습니다. 이는 주로 Wi-fi 네트워크에 따라 다릅니다.

**HoloLens 2** 에서 앱은 다음과 같이 표시 됩니다.

![Holographic 원격 플레이어 진단](images/holographicremotingplayer-diag.png)

* **Render** -원격 플레이어가 마지막 1 초 동안 렌더링 한 프레임의 수입니다. 네트워크를 통해 도착 한 프레임 수와는 독립적입니다 ( **비디오 프레임**참조). 또한 렌더링 된 프레임 간의 마지막 초당 평균/최대 렌더링 델타 시간 (밀리초)이 표시 됩니다.

* **비디오 프레임** -표시 되는 첫 번째 숫자는 건너뛴 비디오 프레임, 두 번째 숫자는 다시 사용 된 비디오 프레임, 세 번째는 비디오 프레임으로 수신 됩니다. 모든 숫자는 마지막 1 초 동안의 카운트를 나타냅니다.
    * ```Received frames```마지막 1 초 동안 도착 한 비디오 프레임의 수입니다. 정상 조건에서는 60 이어야 하지만 네트워크 문제로 인해 프레임이 삭제 되었거나 원격/원격 쪽에서 예상 된 속도로 프레임을 생성 하지 않는다는 표시기가 아닌 것입니다.
    * ```Reused frames```마지막 1 초 동안 두 번 이상 사용 되는 비디오 프레임의 수입니다. 예를 들어 비디오 프레임이 늦게 도착 하면 플레이어의 렌더링 루프는 여전히 프레임을 렌더링 하지만 이전 프레임에 이미 사용 된 비디오 프레임을 *다시* 사용 해야 합니다.
    * ```Skipped frames```플레이어의 렌더링 루프에서 사용 되지 않은 비디오 프레임의 수입니다. 예를 들어 네트워크 지터는 비디오 프레임이 도착 해도 더 이상 균등 하 게 배포 되지 않는 효과를 가질 수 있습니다. 예를 들어, 일부는 지연 된 것이 고 다른 항목은 60Hz에서 실행 될 때 16.66 밀리초의 델타를 포함 하지 않는 시간에 발생 합니다. 플레이어의 렌더링 루프의 두 틱 사이에 둘 이상의 프레임이 도착 하는 경우 발생할 수 있습니다. 이 경우 플레이어는 가장 최근에 받은 비디오 프레임을 항상 표시 하는 것으로 예상 되는 하나 이상의 프레임을 *건너뜁니다* .

    >[!NOTE]
    >네트워크 지터를 향한 경우 건너뛴 후 다시 사용 된 프레임은 일반적으로 동일 합니다. 반대로 건너뛴 프레임만 표시 되는 경우 플레이어는 대상 프레임 속도로 적중 되지 않는다는 표시기입니다. 이 경우 문제를 진단할 때 최대 렌더링 델타 시간을 눈에 파악 해야 합니다.

* **비디오 프레임 델타** -마지막 1 초 동안 받은 비디오 프레임 사이의 최소/최대 델타입니다. 일반적으로이 수는 네트워크 지터로 인해 발생 하는 문제가 발생 하는 경우 건너뛴/재사용 된 프레임과 관련이 있습니다.
* **Latency** -마지막 1 초 동안의 평균 소요 시간 (밀리초)입니다. 이 컨텍스트를 사용 하는 경우 HoloLens 디스플레이에 해당 포즈/원격 분석 데이터에 대 한 비디오 프레임을 표시할 때까지 HoloLens에서 원격/원격 쪽으로 포즈/센서 데이터를 전송 하는 데 걸리는 시간을 의미 합니다.
* **삭제 된 비디오 프레임** -마지막 1 초 동안 그리고 연결이 설정 된 후 삭제 된 비디오 프레임의 수입니다. 삭제 된 비디오 프레임의 주요 원인은 비디오 프레임이 순서 대로 도착 하지 않는 경우이 고, 그 이유는 이미 최신 항목 이므로 삭제 해야 하는 경우입니다. 이는 삭제 된 *프레임과* 유사 하지만 원인이 원격 스택에서 더 낮은 수준에 있습니다. 삭제 된 비디오 프레임은 매우 잘못 된 네트워크 상태 에서만 예상 됩니다.



주 화면에서 **"진단 사용 안 함"** 을 사용 하 여 진단을 해제할 수 있습니다.

## <a name="pc-system-requirements"></a>PC 시스템 요구 사항
* PC에서 Windows 10 기념일 업데이트 이상을 실행 하 고 **있어야** 합니다.
* GeForce GTX 970 또는 AMD Radeon R 9 290 이상의 그래픽 카드를 권장 합니다.
* 무선 홉 수를 줄이려면 이더넷을 통해 PC를 네트워크에 연결 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목
* [HoloLens (첫 번째 gen): Holographic 원격 추가](add-holographic-remoting.md)
* [HoloLens 2: Holographic Remoting 원격 앱 작성](holographic-remoting-create-host.md)
* [홀로그램 원격 소프트웨어 사용 조건](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)
