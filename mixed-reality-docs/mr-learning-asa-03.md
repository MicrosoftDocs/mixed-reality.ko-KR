---
title: Azure Spatial Anchors 자습서 - 3. Azure Spatial Anchors 저장, 검색 및 공유
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 25676404a71daf41b6a5c7587fa9bed95ab813f6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305972"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a>3. Azure Spatial Anchors 저장, 검색 및 공유

이 자습서에서는 앵커 ID를 HoloLens 2의 스토리지에 저장하여 여러 앱 세션에서 Azure Spatial Anchors를 저장하는 방법에 대해 알아봅니다. 또한 다중 디바이스 앵커 맞춤을 위해 이 앵커 ID를 다른 디바이스와 공유하는 방법에 대해서도 알아봅니다.

## <a name="objectives"></a>목표

* 여러 앱 세션 간에 공간 맞춤을 달성하는 방법에 대해 알아봅니다.
* 여러 디바이스 간의 공간 맞춤을 구현하는 방법에 대해 알아봅니다.

## <a name="preparing-the-scene"></a>장면 준비

Hierarchy 창에서 **ButtonParent** 개체를 확장합니다. **마지막 네 개의 자식 단추** 개체를 선택합니다. Inspector 창에서 이름 필드 옆에 있는 확인란을 **선택**하여 모든 개체를 활성화하도록 합니다.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

Hierarchy 창에서 **ButtonParent** 개체를 선택합니다. 그런 다음, Inspector 창에서 **GridObjectCollection** 구성 요소를 찾고 **컬렉션 업데이트** 단추를 클릭하여 모든 **ButtonParent** 개체의 자식 개체 위치를 업데이트합니다.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a>앱 세션 간에 Azure Spatial Anchors 유지

이 섹션에서는 Azure Anchor ID를 HoloLens 로컬 디스크로 저장하고 가져오는 방법에 대해 설명합니다. 이렇게 하면 서로 다른 앱 세션 간에 동일한 앵커 ID에 대한 Azure를 쿼리할 수 있습니다. 이를 통해 앵커된 holograms가 이전 앱 세션과 동일한 위치에 배치됩니다.

Hierarchy 창에서 **ButtonParent** 개체를 확장하고 **SaveAzureAnchorIdToDisk** 및 **GetAzureAnchorIdFromDisk**라는 두 개의 단추를 찾습니다.

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

이전 자습서의 [장면을 작동하도록 단추 구성](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) 지침과 동일한 단계를 수행하여 두 개의 단추 각각에 **Interactable(스크립트)** 구성 요소를 구성합니다.

* **SaveAzureAnchorIdToDisk** 단추 개체에 대해 AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 함수를 할당합니다.
* **GetAzureAnchorIdFromDisk** 단추 개체에 대해 AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 함수를 할당합니다.

업데이트된 앱을 HoloLens에 빌드하는 경우 이제 Azure Anchor ID를 저장하여 앱 세션 간에 Azure Spatial Anchors를 유지할 수 있습니다. 이를 테스트하려면 다음 단계를 수행합니다.

1. Rover 탐색기를 원하는 위치로 이동합니다.
2. Azure 세션을 시작합니다.
3. Azure Anchor를 만듭니다(앵커를 Rover 탐색기의 위치에 만듦).
4. Azure 앵커 ID를 디스크에 저장합니다.
5. 앱을 다시 시작합니다.
6. 디스크에서 Azure 앵커를 가져옵니다(방금 저장한 앵커 ID를 로드함).
7. Azure 세션을 시작합니다.
8. Azure 앵커를 찾습니다(Rover 탐색기를 3단계의 위치에 배치함).

> [!NOTE]
> 앱을 완전히 다시 시작하려면 몰입형 앱 보기를 종료한 후, 혼합 현실 홈의 앱 창을 닫고 [시작] 메뉴에서 앱을 다시 시작합니다. 자세한 내용은 [HoloLens에서 앱 사용](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) 설명서를 참조하세요.

## <a name="sharing-azure-spatial-anchors-between-devices"></a>디바이스 간에 Azure Spatial Anchors 공유

이 섹션에서는 여러 디바이스 간에 Azure 앵커 ID를 공유하는 방법에 대해 알아봅니다. 이렇게 하면 여러 디바이스에서 동일한 앵커 ID를 Azure에 쿼리하여 고정된 홀로그램을 공간적으로 맞출 수 있습니다. 공간 맞춤, 즉 여러 디바이스 간에 동일한 실제 위치에서 동일한 홀로그램을 보는 것은 HoloLens 2에서 로컬 공유 환경의 핵심입니다.

[다중 사용자 기능 자습서](mr-learning-sharing-02.md) 시리즈에서 설명하는 방법을 포함하여 디바이스 간에 Azure 앵커 ID를 전송하는 여러 가지 방법이 있습니다. 이 예에서는 간단한 웹 서비스를 사용하여 디바이스 간에 앵커 ID를 업로드하고 다운로드합니다.

Hierarchy 창에서 **ButtonParent** 개체를 확장합니다.   **ShareAzureAnchorIdToNetwork** 및 **GetAzureAnchorIdFromNetwork**라는 두 단추를 찾습니다.

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

이전 자습서의 [장면을 작동하도록 단추 구성](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) 지침과 동일한 단계를 수행하여 두 개의 단추 각각에 **Interactable(스크립트)** 구성 요소를 구성합니다.

* **ShareAzureAnchorIdToNetwork** 개체에 대해 AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 함수를 할당합니다.
* **GetAzureAnchorIdFromNetwork** 개체에 대해 AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 함수를 할당합니다.

업데이트된 앱을 두 개의 HoloLens 디바이스에 빌드하는 경우 이제 Azure 앵커 ID를 공유하여 공간을 맞출 수 있습니다. 이를 테스트하려면 다음 단계를 수행합니다.

1. HoloLens 디바이스 1: Rover 탐색기를 원하는 위치로 이동합니다.
2. HoloLens 디바이스 1: Azure 세션을 시작합니다.
3. HoloLens 디바이스 1: Azure Anchor를 만듭니다(앵커를 Rover 탐색기의 위치에 만듦).
4. HoloLens 디바이스 1: Azure 앵커 ID를 네트워크에 공유합니다.
5. HoloLens 디바이스 2: 앱을 시작합니다.
6. HoloLens 디바이스 2: 네트워크에서 공유 앵커 ID를 가져옵니다(HoloLens 디바이스 1에서 방금 공유한 앵커 ID를 가져옴).
7. HoloLens 디바이스 2: Azure 세션을 시작합니다.
8. HoloLens 디바이스 2: Azure Anchor를 찾습니다(Rover 탐색기를 3단계의 위치에 배치함).

> [!TIP]
> 하나의 HoloLens만 있는 경우에도 두 번째 HoloLens 디바이스를 사용하는 대신 앱을 다시 시작하여 기능을 테스트할 수 있습니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure Spatial Anchor ID를 HoloLens의 로컬 디스크에 저장하여 앱 세션과 앱 다시 시작 간에 Azure Spatial Anchors를 유지하는 방법을 알아보았습니다. 또한 기본 다중 사용자, 정적 홀로그램 공유 환경을 위해 여러 디바이스 간에 Azure Spatial Anchors를 공유하는 방법도 알아보았습니다.

다음 자습서에서는 사용자에게 실시간 피드백을 제공하는 방법에 대해 알아봅니다. 이 피드백에는 앵커 만들기, 환경 이해 품질 및 Azure 세션 상태에 대한 정보가 포함됩니다. 피드백을 사용하지 않는 경우 사용자는 앵커가 Azure에 성공적으로 업로드되었는지 여부, 환경의 품질이 앵커를 만드는 데 충분한지 여부 또는 현재 상태를 알 수 없습니다.

[다음 자습서: 4. Azure Spatial Anchor 피드백 표시](mr-learning-asa-04.md)
