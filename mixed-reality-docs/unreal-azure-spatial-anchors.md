---
title: Unreal의 Azure Spatial Anchors
description: Unreal 엔진에서 Azure Spatial Anchors 만들기에 대한 개요입니다.
author: hferrone
services: azure-spatial-anchors
ms.author: v-haferr
ms.date: 07/01/2020
ms.topic: tutorial
ms.service: azure-spatial-anchors
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure 개발, spatial anchors, 혼합 현실, 개발, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 홀로그램, 게임 개발
ms.openlocfilehash: c7189407bea4b38e7305f0dda7637b82d3325704
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377348"
---
# <a name="azure-spatial-anchors-in-unreal"></a>Unreal의 Azure Spatial Anchors

## <a name="overview"></a>개요

Azure Spatial Anchors는 Microsoft Mixed Reality 서비스이며, 증강 현실 디바이스를 사용하여 실제 세계에서 앵커 위치를 검색, 공유 및 유지하는 데 사용할 수 있습니다. 아래 설명서는 Azure Spatial Anchors 서비스를 Unreal 프로젝트에 통합하는 지침을 제공합니다. 자세한 내용은 [Azure Spatial Anchors 서비스](https://azure.microsoft.com/services/spatial-anchors/)를 참조하세요.

> [!IMPORTANT]
> 로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다. 앵커를 로컬로 디바이스에 저장하려는 경우, 해당 프로세스를 안내하는 [로컬 Spatial Anchors](unreal-spatial-anchors.md) 문서를 참조하세요. 로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

이 가이드를 완료하려면 다음이 필요합니다.

- [Unreal 버전 4.25](https://www.unrealengine.com/get-now) 이상 설치
- Unreal에 [HoloLens 2 프로젝트](unreal-uxt-ch1.md) 설정 
- [Azure Spatial Anchors 개요](https://docs.microsoft.com/azure/spatial-anchors/overview) 꼼꼼히 읽기
- C++ 및 Unreal에 대한 기본 지식

## <a name="getting-azure-spatial-anchors-account-info"></a>Azure Spatial Anchors 계정 정보 얻기

프로젝트에서 Azure Spatial Anchors를 사용하기 전에 다음을 수행해야 합니다.
* [공간 앵커 리소스를 만들고](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) 아래 나열된 계정 필드를 복사합니다. 다음 값은 애플리케이션의 계정으로 사용자를 인증하는 데 사용됩니다.
    * **계정 ID**
    * **계정 키**

자세한 내용은 [Azure Spatial Anchors 인증](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) 문서를 확인하세요.

> [!NOTE]
> Unreal 4.25의 Azure Spatial Anchors는 Azure AD 인증 토큰을 지원하지 않지만 이후 릴리스에서는 이 기능에 대한 지원이 제공될 예정입니다.

## <a name="adding-azure-spatial-anchors-plugins"></a>Azure Spatial Anchors 플러그 인 추가

다음을 수행하여 Unreal 에디터에서 Azure Spatial Anchors 플러그 인을 사용하도록 설정합니다.
1. **편집 > 플러그 인**을 클릭하고 **AzureSpatialAnchors** 및 **AzureSpatialAnchorsForWMR**을 검색합니다.
2. 두 플러그 인의 **사용** 확인란을 선택하여 애플리케이션에서 Azure Spatial Anchors 청사진 라이브러리에 액세스를 허용합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-01.png)

완료되면 Unreal 편집기를 다시 시작하여 플러그 인 변경 내용을 적용합니다. 이제 프로젝트에서 Azure Spatial Anchors를 사용할 준비가 되었습니다.

## <a name="starting-a-spatial-anchors-session"></a>Spatial Anchors 세션 시작
Azure Spatial Anchors 세션을 사용하면 클라이언트 애플리케이션에서 Azure Spatial Anchors 서비스와 통신할 수 있습니다. Azure Spatial Anchors를 만들고 유지하고 공유하려면 Azure Spatial Anchors 세션을 만들고 시작해야 합니다.

1. 애플리케이션에서 사용 중인 Pawn에 대한 청사진을 엽니다.
2. **계정 ID**와 **계정 키**에 대한 두 문자열 변수를 추가한 다음, Azure Spatial Anchors 계정에서 해당 값을 할당하여 세션을 인증합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-02.png)

다음을 수행하여 Azure Spatial Anchors 세션을 시작합니다.
1. HoloLens 애플리케이션에서 **AR 세션**을 실행 중인지 확인합니다. AR 세션이 실행될 때까지 Azure Spatial Anchors 세션을 시작할 수 없기 때문입니다. 설정되어 있지 않으면 [AR 세션 자산을 만듭니다](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).
2. **Azure Spatial Anchors 세션 시작** 사용자 지정 이벤트를 추가하고 아래 스크린샷에 표시된 대로 구성합니다.
    * 세션을 만들면 기본적으로 세션이 시작되지 않습니다. 따라서 개발자가 Azure Spatial Anchors 서비스를 통해 인증할 세션을 구성할 수 있습니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. **계정 ID** 및 **계정 키**를 제공하도록 Azure Spatial Anchors 세션을 구성합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. 애플리케이션이 Azure Spatial Anchors를 만들고 찾을 수 있도록 Azure Spatial Anchors 세션을 시작합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-05.png)

서비스를 더 이상 사용하지 않는 경우 이벤트 그래프 청사진에서 Azure Spatial Anchors 리소스를 정리하는 것이 좋습니다.

1. Azure Spatial Anchors 세션을 중지합니다. 세션은 더 이상 실행되지 않지만 연결된 리소스가 Azure Spatial Anchors 플러그 인에 여전히 있습니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. Azure Spatial Anchors 세션을 제거하여 Azure Spatial Anchors 플러그 인에 여전히 알려져 있는 Azure Spatial Anchors 세션 리소스를 정리합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-07.png)

이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a>앵커 만들기
Azure Spatial Anchor는 증강 현실 애플리케이션 공간에서 실제 세계 포즈를 나타내며, 증강 현실 콘텐츠를 실제 세계의 위치에 고정합니다. Azure Spatial Anchors는 여러 사용자가 서로 공유할 수도 있습니다. 이러한 공유를 통해 다른 디바이스에서 그려진 증강 현실 콘텐츠를 실제 세계에서 동일한 위치에 배치할 수 있습니다. 

새 Azure Spatial Anchor를 만들려면 다음을 수행합니다.
1. Azure Spatial Anchors 세션이 실행 중인지 확인합니다. Azure Spatial Anchors 세션이 실행되고 있지 않으면 애플리케이션에서 Azure Spatial Anchor를 만들거나 유지할 수 없습니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. 위치를 유지해야 하는 Unreal **[장면 구성 요소](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** 를 만들거나 가져옵니다. 
    * 아래 이미지에서는 **앵커가 필요한 장면 구성 요소**라는 구성 요소가 변수로 사용됩니다. Unreal 장면 구성 요소는 [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) 및 Azure Spatial Anchor에 대해 애플리케이션 월드 변환을 설정하는 데 필요합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-10.png)

Unreal 장면 구성 요소에 대한 Azure Spatial Anchor를 생성하고 저장하려면 다음을 수행합니다.
1. Unreal 장면 구성 요소에 대한 [Pin 구성 요소](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)를 호출하고 장면 구성 요소의 **월드 변환**을 AR Pin에 사용되는 월드 변환으로 지정합니다.
    * Unreal은 Azure Spatial Anchor를 만드는 데 사용되는 AR Pin을 사용하여 애플리케이션 공간에서 AR 포인트를 추적합니다. Unreal에서 AR Pin은 HoloLens의 SpatialAnchor와 유사합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. 새로 만든 AR Pin을 사용하여 **Create Cloud Anchor**(클라우드 앵커 만들기)를 호출합니다.
    * Create Cloud Anchor(클라우드 앵커 만들기)는 Azure Spatial Anchor 서비스가 아닌 로컬에 Azure Spatial Anchor를 만듭니다. Azure Spatial Anchor의 매개 변수(예: 만료 날짜)는 서비스를 사용하여 Azure Spatial Anchor를 만들기 전에 설정할 수 있습니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. Azure Spatial Anchor 만료를 설정합니다. 이 함수의 Lifetime 매개 변수를 사용하면 개발자가 서비스에서 앵커를 유지해야 하는 시간을 초 단위로 지정할 수 있습니다.
    * 예를 들어, 일주일의 만료 시간 값은 60초 x 60분 x 24시간 x 7일 = 604,800초입니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-13.png)

앵커 매개 변수를 설정한 후에 저장할 준비가 된 것으로 앵커를 선언합니다. 아래 예제에서는 새로 만든 Azure Spatial Anchor가 저장이 필요한 Azure Spatial Anchors 세트에 추가됩니다. 이 세트는 Pawn 청사진에 대한 변수로 선언됩니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a>앵커 저장

매개 변수를 사용하여 Azure Spatial Anchor를 구성한 후 **Save Cloud Anchor**(클라우드 앵커 저장)를 호출합니다. Save Cloud Anchor(클라우드 앵커 저장)는 Azure Spatial Anchors 서비스에 대한 앵커를 선언합니다. Save Cloud Anchor(클라우드 앵커 저장) 호출이 성공하면 Azure Spatial Anchor 서비스의 다른 사용자가 Azure Spatial Anchor를 사용할 수 있습니다.  

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> Save Cloud Anchor(클라우드 앵커 저장)는 비동기 함수이며 게임 스레드 이벤트(예: **EventTick**)에서만 호출할 수 있습니다. Save Cloud Anchor(클라우드 앵커 저장)는 사용자 지정 청사진 함수에 사용 가능한 청사진 함수로 나타나지 않을 수 있습니다. 하지만 Pawn 이벤트 그래프 청사진 편집기에서는 사용할 수 있습니다.

아래 예에서 Azure Spatial Anchor는 입력 이벤트 콜백 중에 세트에 저장됩니다. 그런 다음, EventTick에 앵커가 저장됩니다. Azure Spatial Anchor를 저장하려면 Azure Spatial Anchors 세션에서 생성한 공간 데이터의 양에 따라 여러 번 시도가 필요할 수 있습니다. 그래서 Save 호출이 성공했는지 여부를 확인하는 것이 좋습니다.

앵커가 저장되지 않은 경우 아직 저장이 필요한 앵커 세트에 다시 추가합니다. 향후 EventTicks는 Azure Spatial Anchor 서비스에 앵커가 성공적으로 저장될 때까지 저장을 시도할 예정입니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-16.png)

앵커가 저장되면 애플리케이션에 콘텐츠를 배치하기 위해 AR Pin의 변환을 참조 변환으로 사용할 수 있습니다. 다른 사용자가 이 앵커를 감지하고 AR 콘텐츠를 실제 세계의 여러 디바이스에 맞출 수 있습니다.

## <a name="deleting-an-anchor"></a>앵커 삭제

**Delete Cloud Anchor**(클라우드 앵커 삭제)를 호출하여 Azure Spatial Anchor 서비스에서 앵커를 삭제할 수 있습니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> Delete Cloud Anchor(클라우드 앵커 삭제)는 잠재 함수이며 게임 스레드 이벤트(예: EventTick)에서만 호출할 수 있습니다. Delete Cloud Anchor(클라우드 앵커 삭제)는 사용자 지정 청사진 함수에는 사용 가능한 청사진 함수로 나타나지 않을 수 있습니다. 하지만 Pawn 이벤트 그래프 청사진 편집기에서는 사용할 수 있습니다.

아래 예제에서는 사용자 지정 입력 이벤트에서 앵커에 삭제 플래그가 지정됩니다. 그런 다음 EventTick에서 삭제를 시도합니다. 앵커 삭제가 실패하면 삭제 플래그가 지정된 앵커 세트에 Azure Spatial Anchor를 추가하고 나중에 EventTicks에서 다시 시도합니다.

이제 이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a>기존 앵커 찾기

Azure Spatial Anchors를 만드는 것 외에도 Azure Spatial Anchors 서비스를 사용하여 피어에서 만든 앵커를 감지할 수 있습니다.

1. 감지할 앵커에 대한 Azure Spatial Anchor 식별자를 확보합니다.
    * 앵커 식별자는 이전 Azure Spatial Anchors 세션에서 동일한 디바이스로 만든 앵커에 대해 확보할 수 있습니다. Azure Spatial Anchors 서비스와 상호 작용하는 피어 디바이스에서 만들고 공유할 수도 있습니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. **AzureSpatialAnchorsEvent** 구성 요소를 Pawn 청사진에 추가합니다.
    * 이 구성 요소를 사용하면 다양한 Azure Spatial Anchors 이벤트(예: Azure Spatial Anchors가 있을 때 호출되는 이벤트)를 구독할 수 있습니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. **AzureSpatialAnchorsEvent** 구성 요소에 대한 **ASAAnchor Located 대리자**를 구독합니다.
    * 대리자는 Azure Spatial Anchors 계정과 연결된 새 앵커가 배치되는 경우 해당 애플리케이션에 알려줍니다.
    * 이벤트 콜백을 사용하면 Azure Spatial Anchors 세션을 사용하여 피어가 만든 Azure Spatial Anchors에는 기본적으로 AR Pin이 생성되지 않습니다. 감지된 Azure Spatial Anchor에 대한 AR Pin을 만들려면 개발자가 **Create ARPin Around Azure Cloud Spatial Anchor**(Azure Cloud Spatial Anchor에 대한 ARPin 만들기)를 호출하면 됩니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-20.png)

Azure Spatial Anchor 서비스를 사용하여 피어에서 만든 Azure Spatial Anchors를 찾기 위해 애플리케이션은 **Azure Spatial Anchors Watcher**를 만들어야 합니다.
1. Azure Spatial Anchors 세션이 실행 중인지 확인합니다.
2. **AzureSpatialAnchorsLocateCriteria**를 만듭니다.
    * 다양한 위치 매개 변수(예: 사용자와의 거리 또는 다른 앵커와의 거리)를 지정할 수 있습니다.
3. **AzureSpatialAnchorsLocateCritieria**에서 원하는 Azure Spatial Anchor 식별자를 선언합니다.
4. **Create Watcher**(감시자 만들기)를 호출합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-21.png)

이제 애플리케이션이 Azure Spatial Anchors 서비스에 알려진 Azure Spatial Anchors를 찾기 시작합니다. 따라서, 피어에서 만든 Azure Spatial Anchors를 사용자가 찾을 수 있습니다.

Azure Spatial Anchor를 찾은 후 **Stop Watcher**(감시자 중지)를 호출하여 Azure Spatial Anchors Watcher를 중지하고 감시자 리소스를 정리합니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-22.png)

마지막 이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-23.png)


## <a name="next-steps"></a>다음 단계
* [로컬 Spatial Anchors](unreal-spatial-anchors.md)
* [Spatial Anchors 설명서](https://docs.microsoft.com/azure/spatial-anchors/)
* [Spatial Anchor 기능](https://azure.microsoft.com/services/spatial-anchors/#features)
* [효과적인 앵커 환경 지침](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)