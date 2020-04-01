---
title: Azure Spatial Anchors 자습서 - 2. Azure Spatial Anchors 저장, 검색 및 공유
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362012"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Azure Spatial Anchors 저장, 검색 및 공유

이 자습서에서는 앵커 ID를 HoloLens 2의 스토리지에 저장하여 여러 앱 세션에서 Azure Spatial Anchors를 저장하는 방법에 대해 알아봅니다. 또한 다중 디바이스 앵커 맞춤을 위해 이 앵커 ID를 다른 디바이스와 공유하는 방법에 대해서도 알아봅니다.

## <a name="objectives"></a>목표

* 앱 세션 간의 지속성을 위해 HoloLens 2 로컬 디스크에서 Azure Spatial Anchor ID를 저장 및 검색하는 방법 알아보기
* 다중 디바이스 시나리오에서 사용자 간에 Azure Spatial Anchor ID를 공유하는 방법 알아보기

## <a name="preparing-the-scene"></a>장면 준비

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 차례로 이동합니다. CTRL 단추를 누른 채 **ButtonParent_SaveAnchorId** 및 **ButtonParent_ShareAnchorId**를 클릭하여 두 개의 프리팹을 선택한 다음, [계층 구조] 창으로 끌어 장면에 추가합니다.

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>앱 세션 간 Azure 앵커 유지 - 디스크에 앵커 ID 저장
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

이 섹션에서는 Azure 앵커 ID를 HoloLens 2 로컬 디스크로 저장하고 가져오는 방법에 대해 설명합니다. 이렇게 하면 서로 다른 앱 세션 간에 동일한 앵커 ID를 Azure에 쿼리하여 고정된 홀로그램을 이전 앱 세션과 동일한 위치에 지정할 수 있습니다.

[계층 구조] 창에서 두 개의 단추가 포함된 **ButtonParent_SaveAnchorId** 개체를 펼칩니다. 하나는 Azure 앵커 ID를 HoloLens 2 스토리지에 저장하는 단추이고, 다른 하나는 디스크에서 저장된 ID를 검색하는 단추입니다.

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

이전 자습서의 [장면을 작동하도록 단추 구성](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) 지침과 동일한 단계를 수행하여 두 개의 단추 각각에 **누름 가능한 단추 HoloLens 2(스크립트)** 구성 요소 및 **Interactable(스크립트)** 구성 요소를 구성합니다.

* **SaveAzureAnchorIdToDisk** 개체에 대해 AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 함수를 할당합니다.
* **GetAzureAnchorIdFromDisk** 개체에 대해 AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 함수를 할당합니다.

업데이트된 애플리케이션을 HoloLens에 빌드하는 경우 이제 Azure 앵커 ID를 저장하여 앱 세션 간에 Azure Spatial Anchors를 유지할 수 있습니다. 이를 테스트하려면 다음 단계를 수행합니다.

1. 로켓 발사대 환경을 원하는 위치로 이동합니다.
2. Azure 세션을 시작합니다.
3. Azure Anchor를 만듭니다(앵커를 로켓 발사대 환경의 위치에 만듦).
4. Azure 앵커 ID를 디스크에 저장합니다.
5. 애플리케이션을 다시 시작합니다.
6. 디스크에서 Azure 앵커를 가져옵니다(방금 저장한 앵커 ID를 로드함).
7. Azure 세션을 시작합니다.
8. Azure 앵커를 찾습니다(로켓 발사대 환경을 3단계의 위치에 배치함).

> [!NOTE]
> 애플리케이션을 완전히 다시 시작하려면 몰입형 앱 보기를 종료한 후, 혼합 현실 홈의 앱 창을 닫고 [시작] 메뉴에서 애플리케이션을 다시 시작합니다. 자세한 내용은 [HoloLens에서 앱 사용](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) 설명서를 참조하세요.

## <a name="share-azure-anchors-between-multiple-devices"></a>여러 디바이스 간에 Azure 앵커 공유

이 섹션에서는 여러 디바이스 간에 Azure 앵커 ID를 공유하는 방법에 대해 알아봅니다. 이렇게 하면 여러 디바이스에서 동일한 앵커 ID를 Azure에 쿼리하여 고정된 홀로그램을 공간적으로 맞출 수 있습니다. 공간 맞춤, 즉 여러 디바이스 간에 동일한 실제 위치에서 동일한 홀로그램을 보는 것은 HoloLens 2에서 로컬 공유 환경의 핵심입니다.

[다중 사용자 기능 자습서](mrlearning-sharing(photon)-ch1.md) 시리즈에서 설명하는 방법을 포함하여 디바이스 간에 Azure 앵커 ID를 전송하는 여러 가지 방법이 있습니다. 이 예에서는 간단한 웹 서비스를 사용하여 디바이스 간에 앵커 ID를 업로드하고 다운로드합니다.

[계층 구조] 창에서 두 개의 단추가 포함된 **ButtonParent_ShareAnchorId** 개체를 펼칩니다. 하나는 Azure 앵커 ID를 웹 서버에 업로드하는 단추이고, 다른 하나는 웹 서버에서 ID를 다운로드하는 단추입니다.

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

이전 자습서의 [장면을 작동하도록 단추 구성](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) 지침과 동일한 단계를 수행하여 두 개의 단추 각각에 **누름 가능한 단추 HoloLens 2(스크립트)** 구성 요소 및 **Interactable(스크립트)** 구성 요소를 구성합니다.

* **ShareAzureAnchorIdToNetwork** 개체에 대해 AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 함수를 할당합니다.
* **GetAzureAnchorIdFromNetwork** 개체에 대해 AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 함수를 할당합니다.

업데이트된 애플리케이션을 두 개의 HoloLens 디바이스에 빌드하는 경우 이제 Azure 앵커 ID를 공유하여 두 디바이스 간에 공간을 맞출 수 있습니다. 이를 테스트하려면 다음 단계를 수행합니다.

1. HoloLens 디바이스 1: 로켓 발사대 환경을 원하는 위치로 이동합니다.
2. HoloLens 디바이스 1: Azure 세션을 시작합니다.
3. HoloLens 디바이스 1: Azure Anchor를 만듭니다(앵커를 로켓 발사대 환경의 위치에 만듦).
4. HoloLens 디바이스 1: Azure 앵커 ID를 네트워크에 공유합니다.
5. HoloLens 디바이스 2: 애플리케이션을 시작합니다.
6. HoloLens 디바이스 2: 네트워크에서 공유 앵커 ID를 가져옵니다(HoloLens 디바이스 1에서 방금 공유한 앵커 ID를 가져옴).
7. HoloLens 디바이스 2: Azure 세션을 시작합니다.
8. HoloLens 디바이스 2: Azure 앵커를 찾습니다(로켓 발사대 환경을 3단계의 위치에 배치함).

> [!TIP]
> 하나의 HoloLens만 있는 경우에도 두 번째 HoloLens 디바이스를 사용하는 대신 애플리케이션을 다시 시작하여 기능을 테스트할 수 있습니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure Spatial Anchor ID를 HoloLens의 로컬 디스크에 저장하여 애플리케이션 세션과 애플리케이션 다시 시작 간에 Azure Spatial Anchors를 유지하는 방법을 알아보았습니다. 또한 기본 다중 사용자, 정적 홀로그램 공유 환경을 위해 여러 디바이스 간에 Azure Spatial Anchors를 공유하는 방법도 알아보았습니다.

다음 자습서에서는 사용자에게 실시간 피드백을 제공하는 방법에 대해 알아봅니다. 이 피드백에는 앵커 만들기, 환경 이해 품질 및 Azure 세션 상태에 대한 정보가 포함됩니다. 피드백을 사용하지 않는 경우 사용자는 앵커가 Azure에 성공적으로 업로드되었는지 여부, 환경의 품질이 앵커를 만드는 데 충분한지 여부 또는 현재 상태를 알 수 없습니다.

[다음 단원: 3. Azure Spatial Anchor 피드백 표시](mrlearning-asa-ch3.md)
