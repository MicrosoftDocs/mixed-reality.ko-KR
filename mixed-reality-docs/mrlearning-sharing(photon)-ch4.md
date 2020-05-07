---
title: 다중 사용자 기능 자습서 - 5. 공유 환경에 Azure Spatial Anchors 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604974"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a>4. 공유 환경에 Azure Spatial Anchors 통합

이 자습서에서는 ASA(Azure Spatial Anchors)를 공유 환경에 통합하는 방법을 알아봅니다. ASA를 사용하면 여러 디바이스에서 실제 세계에 대한 공통 참조가 가능하기 때문에 사용자가 각자 실제 위치에서 서로를 볼 수 있고 동일한 위치에서 공유 환경을 볼 수 있습니다.

## <a name="objectives"></a>목표

* 다중 디바이스 맞춤을 위해 ASA를 공유 환경에 통합
* ASA가 로컬 공유 환경의 컨텍스트에서 작동하는 방식에 대한 기본 사항 알아보기

## <a name="preparing-the-scene"></a>장면 준비

Hierarchy 창에서 **SharedPlayground** 개체를 펼친 다음, **TableAnchor** 개체를 펼쳐서 자식 개체를 노출합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** 폴더로 이동하여 **Buttons** 프리팹을 Hierarchy 창의 **TableAnchor** 자식 개체 위로 끌어와서 TableAnchor 개체의 자식으로 장면에 추가합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>장면을 작동하도록 단추 구성

이 섹션에서는 Azure Spatial Anchors를 사용하여 공유 환경에서 공간 정렬을 구현하는 방법에 대한 기본 사항을 보여주는 일련의 단추 이벤트를 구성합니다.

Hierarchy 창에서 **Button** 개체를 펼치고 첫째 자식 단추 개체인 **StartAzureSession**을 선택합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

Inspector 창에서 **Interactable (Script)** 구성 요소를 찾아서 **OnClick ()** 이벤트를 다음과 같이 구성합니다.

* **None (Object)** 필드에는 **TableAnchor** 개체를 할당합니다.
* **No Function** 드롭다운에서 **AnchorModuleScript** > **StartAzureSession ()** 함수를 선택합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

Hierarchy 창에서 둘째 자식 단추 개체인 **CreateAzureAnchor**를 선택한 다음, Inspector 창에서 **Interactable (Script)** 구성 요소를 찾아서 **OnClick ()** 이벤트를 다음과 같이 구성합니다.

* **None (Object)** 필드에는 **TableAnchor** 개체를 할당합니다.
* **No Function** 드롭다운에서 **AnchorModuleScript** > **CreateAzureAnchor ()** 함수를 선택합니다.
* 새로운 **None (Game Object)** 필드가 나타나면 **TableAnchor** 개체를 할당합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

Hierarchy 창에서 셋째 자식 단추 개체인 **ShareAzureAnchor**를 선택한 다음, Inspector 창에서 **Interactable (Script)** 구성 요소를 찾아서 **OnClick ()** 이벤트를 다음과 같이 구성합니다.

* **None (Object)** 필드에는 **TableAnchor** 개체를 할당합니다.
* **No Function** 드롭다운에서 **SharingModuleScript** > **ShareAzureAnchor ()** 함수를 선택합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

Hierarchy 창에서 넷째 자식 단추 개체인 **GetAzureAnchor**를 선택한 다음, Inspector 창에서 **Interactable (Script)** 구성 요소를 찾아서 **OnClick ()** 이벤트를 다음과 같이 구성합니다.

* **None (Object)** 필드에는 **TableAnchor** 개체를 할당합니다.
* **No Function** 드롭다운에서 **SharingModuleScript** > **GetAzureAnchor ()** 함수를 선택합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Azure 리소스에 장면 연결

Hierarchy 창에서 **SharedPlayground** 개체를 펼치고 **TableAnchor** 개체를 선택합니다. 그런 다음, Inspector 창에서 **Spatial Anchor Manager (Script)** 구성 요소를 찾아서, 이 자습서 시리즈에서 [필수 구성 요소](mrlearning-sharing(photon)-ch1.md#prerequisites)의 일부로 생성된 Azure Spatial Anchors 계정의 자격 증명을 사용하여 **Credentials** 섹션을 구성합니다.

* **Spatial Anchors Account ID** 필드에 Azure Spatial Anchors 계정의 **계정 ID**를 붙여넣습니다.
* **Spatial Anchors Account Key** 필드에 Azure Spatial Anchors 계정의 기본 또는 보조 **액세스 키**를 붙여넣습니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

**TableAnchor** 개체가 선택된 상태로 Inspector 창에서 모든 스크립트 구성 요소가 활성화되어 있는지 확인합니다.

* **Spatial Anchor Manager (Script)** 구성 요소 옆에 있는 확인란을 선택하여 활성화합니다.
* **Anchor Module Script (Script)** 구성 요소 옆에 있는 확인란을 선택하여 활성화합니다.
* **Sharing Module Script (Script)** 구성 요소 옆에 있는 확인란을 선택하여 활성화합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>공간 맞춤 환경 체험

> [!NOTE]
> Azure Spatial Anchors는 Unity에서 실행할 수 없습니다. 따라서 Azure Spatial Anchors 기능을 테스트하려면 둘 이상의 HoloLens 디바이스에 프로젝트를 배포해야 합니다.

Unity 프로젝트를 빌드하여 두 개의 HoloLens 디바이스에 배포하면 Azure Anchor ID를 공유하여 디바이스 간의 공간 맞춤을 구현할 수 있습니다. 이를 테스트하려면 다음 단계를 수행합니다.

1. HoloLens 디바이스 1: **애플리케이션 시작**(로켓 발사대가 인스턴스화되어 테이블에 배치됩니다.)
2. HoloLens 디바이스 2: **애플리케이션 시작**(두 사용자 모두에게 로켓 발사대가 있는 테이블이 보이지만 테이블이 동일한 위치에 나타나지 않고 사용자가 있는 곳에 사용자 아바타가 나타나지 않습니다.)
3. HoloLens 디바이스 1: **Start Azure Session** 단추를 누릅니다.
4. HoloLens 디바이스 1: **Create Azure Anchor** 단추를 누릅니다. (TableAnchor 개체의 위치에 앵커를 만들고 Azure 리소스에 앵커 정보를 저장합니다.)
5. HoloLens 디바이스 1: **Share Azure Anchor** 단추를 누릅니다. (앵커 ID를 다른 사용자와 실시간으로 공유합니다.)
6. HoloLens 디바이스 2: **Start Azure Session** 단추를 누릅니다.
7. HoloLens 디바이스 2: **Get Azure Anchor** 단추를 누릅니다. (Azure 리소스에 연결하여 공유 앵커 ID에 대한 앵커 정보를 검색한 다음, HoloLens 디바이스 1에 앵커가 생성된 위치로 TableAnchor 개체를 이동합니다.)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure의 강력한 Spatial Anchors를 통합하여 공유 환경에서 디바이스를 맞추는 방법을 알아보았습니다. 이것으로 자습서 시리즈를 마치겠습니다. 이 시리즈에서는 Photon 계정과 애플리케이션을 설정하고, Photon과 PUN을 Unity 애플리케이션에 통합하고, 사용자 아바타와 공유 개체를 구성하고, 마지막으로 ASA를 사용하여 여러 참가자를 맞추는 방법을 알아보았습니다.
