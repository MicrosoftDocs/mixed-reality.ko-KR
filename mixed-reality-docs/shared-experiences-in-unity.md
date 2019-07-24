---
title: Unity의 공유 환경
description: Unity 응용 프로그램에서 여러 사용자 간에 동일한 holograms를 공유 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 공유, 고정, WorldAnchor, MR 공유 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure 공간 앵커,
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516796"
---
# <a name="shared-experiences-in-unity"></a>Unity의 공유 환경

공유 환경은 각 사용자가 각각의 HoloLens, iOS 또는 Android 장치를 포함 하는 여러 사용자가 일정 한 위치에 배치 된 동일한 홀로그램을 전체적으로 보고 상호 작용 하는 환경입니다. 공간 고정 공유를 통해 수행 됩니다.

## <a name="azure-spatial-anchors"></a>Azure 공간 앵커

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있는 내구성이 뛰어난 클라우드 지원 공간 앵커를 만들 수 있습니다.  여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.  이렇게 실제 세계 공유 환경을 제공합니다.

HoloLens, iOS 및 Android 디바이스에서 비대칭 홀로그램 지속에 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>를 사용할 수도 있습니다.  유지되는 클라우드 공간 앵커를 공유하면 여러 디바이스가 동시에 함께 존재하지 않는 경우에도 시간 경과에 따라 같은 지속형 홀로그램을 관찰할 수 있습니다.

Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.

Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.

## <a name="local-anchor-transfers"></a>로컬 앵커 전송

Azure 공간 앵커를 사용할 수 없는 경우 [로컬 앵커 전송](local-anchor-transfers-in-unity.md) 에서는 한 hololens 장치에서 두 번째 hololens 장치에서 가져올 앵커를 내보낼 수 있습니다.  이 방법은 Azure 공간 앵커 보다 더 강력 하지 않은 앵커 회수를 제공 하며, iOS 및 Android 장치는이 방식에서 지원 되지 않습니다.

## <a name="see-also"></a>참조
* [혼합 현실의 공유 환경](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a>