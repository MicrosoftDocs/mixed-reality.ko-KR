---
title: DirectX의 공유 공간 앵커
description: 공간 앵커를 공유 하 여 두 HoloLens 장치를 동기화 하는 방법을 설명 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 동기화, 공간 앵커, 전송, 여럿이, 보기, 시나리오, 연습, 샘플 코드, Azure, Azure 공간 앵커, 자신
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516880"
---
# <a name="shared-experiences-in-directx"></a>DirectX의 공유 환경

공유 환경은 각 사용자가 각각의 HoloLens, iOS 또는 Android 장치를 포함 하는 여러 사용자가 일정 한 위치에 배치 된 동일한 홀로그램을 전체적으로 보고 상호 작용 하는 환경입니다. 공간 고정 공유를 통해 수행 됩니다.

## <a name="azure-spatial-anchors"></a>Azure 공간 앵커

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있는 내구성이 뛰어난 클라우드 지원 공간 앵커를 만들 수 있습니다.  여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.  이렇게 실제 세계 공유 환경을 제공합니다.

HoloLens, iOS 및 Android 디바이스에서 비대칭 홀로그램 지속에 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>를 사용할 수도 있습니다.  유지되는 클라우드 공간 앵커를 공유하면 여러 디바이스가 동시에 함께 존재하지 않는 경우에도 시간 경과에 따라 같은 지속형 홀로그램을 관찰할 수 있습니다.

HoloLens 앱에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 공간 앵커 HoloLens 빠른</a>시작을 사용해 보세요.

Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens에서 앵커를 만들고 찾을</a>수 있습니다.  <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 및 iOS</a> 에 대 한 연습을 사용할 수 있으므로 모든 장치에서 동일한 앵커를 공유할 수 있습니다.

## <a name="local-anchor-transfers"></a>로컬 앵커 전송

Azure 공간 앵커를 사용할 수 없는 경우 [로컬 앵커 전송](local-anchor-transfers-in-directx.md) 에서는 한 hololens 장치에서 두 번째 hololens 장치에서 가져올 앵커를 내보낼 수 있습니다.  이 방법은 Azure 공간 앵커 보다 더 강력 하지 않은 앵커 회수를 제공 하며, iOS 및 Android 장치는이 방식에서 지원 되지 않습니다.

## <a name="see-also"></a>참조
* [혼합 현실의 공유 환경](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">HoloLens 용 Azure 공간 앵커 SDK</a>