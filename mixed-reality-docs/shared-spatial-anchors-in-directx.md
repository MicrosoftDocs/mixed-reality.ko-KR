---
title: DirectX의 공간 앵커를 공유합니다.
description: 공간 앵커를 공유 하 여 두 개의 HoloLens 장치를 동기화 하는 방법에 설명 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 동기화, 공간 앵커, 전송, 멀티 플레이 게임, 보기, 시나리오, 연습, 샘플 코드, Azure, Azure 공간 앵커 ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605062"
---
# <a name="shared-experiences-in-directx"></a>DirectX의 공유 환경

공유 경험을 여러 사용자가 자신의 HoloLens, iOS 또는 Android 장치를 사용 하 여 전체적으로 확인 하 고 있는 공간에서 고정된 소수점에 배치 되는 동일한 홀로그램 상호 작용 하나입니다. 이 공간 앵커 공유를 통해 수행 됩니다.

## <a name="azure-spatial-anchors"></a>Azure 공간 앵커

사용할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 앵커를 만들 내구성이 있는 클라우드 기반 공간에 앱 여러 HoloLens, iOS 및 Android 장치에서 찾을 수는 있습니다.  일반적인 공간 앵커를 여러 장치를 공유 각 사용자는 동일한 실제 위치에 해당 앵커에 상대적인 렌더링 된 콘텐츠를 볼 수입니다.  따라서 실시간 공유 환경.

사용할 수도 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> HoloLens, iOS 및 Android 장치에서 비동기 홀로그램 지 속성에 대 한 합니다.  견고한 클라우드 공간 앵커를 공유 하 여 여러 장치 관찰할 수 있습니다 동일한 지속형된 홀로그램 시간이 지남에 따라 해당 장치를 동시에 함께 있는 경우에 합니다.

5 분을 사용해으로 시작 하려면 HoloLens 앱에서 공유 환경을 구축 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">공간 앵커 HoloLens Azure 빠른 시작</a>합니다.

Azure 공간 앵커를 사용 하 여 실행을 했으면 할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens에 앵커를 찾아서 만들</a>합니다.  연습에 사용할 수 있는 <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 및 iOS</a> 도 모든 장치에서 동일한 앵커를 공유할 수 있도록 합니다.

## <a name="local-anchor-transfers"></a>로컬 앵커 전송

Azure 공간 앵커를 사용할 수 없습니다 상황에서 [로컬 앵커 전송](local-anchor-transfers-in-directx.md) 두 번째 HoloLens 장치에서 가져올 앵커를 내보내려면 하나 HoloLens 장치를 사용 하도록 설정 합니다.  이 방법은 Azure 공간 앵커 보다 덜 강력 앵커 회수를 제공 하 고이 접근 방식에서 iOS 및 Android 장치를 지원 하지 않는 note 합니다.

## <a name="see-also"></a>참조
* [혼합된 현실 환경 공유했습니다](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure 공간 앵커 HoloLens 용 SDK</a>