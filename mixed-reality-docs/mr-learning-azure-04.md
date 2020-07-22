---
title: Azure 클라우드 자습서 - 4. Integrating Azure Spatial 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, hololens 2, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 4eac2b96519abeebc277a53ad83d1b6dec8d61fd
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305955"
---
# <a name="4-integrating-azure-spatial-anchors"></a>4. Integrating Azure Spatial 통합

이 자습서에서는 **Azure Spatial Anchors**를 사용하는 방법에 대해 설명합니다. **추적된 개체**의 위치를 Azure Spatial Anchors로 저장합니다. 그런 다음, 사용자에게 위치를 가리키는 안내 화살표가 있는 사용자를 쿼리하고 표시합니다.

## <a name="objectives"></a>목표

* Azure Spatial Anchors의 기본 사항에 대해 알아봅니다.
* 이 프로젝트에서 Azure Spatial Anchors를 사용하도록 장면을 설정하는 방법에 대해 알아봅니다.
* 위치 저장 및 쿼리를 통합하는 방법에 대해 알아봅니다.

## <a name="understanding-azure-spatial-anchors"></a>Azure Spatial Anchors 이해

 **Azure Spatial Anchors**는 Azure Cloud Services 제품군의 일부이며 앵커 위치를 저장하는 데 사용됩니다. 저장된 앵커 위치는 클라우드의 *앵커 ID* 기반으로 검색할 수 있습니다. 이 앵커 위치는 HoloLens, iOS 및 Android 디바이스와 같은 다중 플랫폼 디바이스에서 공유하고 액세스할 수 있습니다.

[Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview)에 대해 자세히 알아보세요.

## <a name="preparing-azure-spatial-anchors"></a>Azure Spatial Anchors 준비

시작하기 전에 Azure Portal에서 공간 앵커 리소스를 만들어야 합니다.
[공간 앵커 리소스](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)를 만드는 방법에 대해 알아봅니다.

## <a name="preparing-the-scene"></a>장면 준비

이 섹션에서는 장면을 구성하고 필요한 변경을 수행하는 방법을 알아봅니다.

Project 창에서 **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**로 이동합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

**Manager** 폴더에서 프리팹 **Anchor Manager**를 장면 Hierarchy에 끌어다 놓습니다.

Hierarchy에서 **Anchor Manager** GameObject를 선택하고 Inspector 섹션에서 **Spatial Anchor Manager**(스크립트)를 찾습니다. 계정 ID 및 키 필드를 찾아 이전 단계의 필수 구성 요소에서 만든 자격 증명을 추가합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

이제 장면 Hierarchy에서 **Scene Controller** 개체를 찾아 선택합니다. **Scene Controller** Inspector가 표시됩니다.

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

**Scene Controller** 구성 요소의 **Anchor Manager** 필드가 비어 있음을 확인하고, 장면의 Hierarchy에서 **Anchor Manager**를 해당 필드로 끌어서 놓고 장면을 저장합니다.

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a>HoloLens 2에 앱 빌드 및 배포

Azure Spatial Anchors는 Unity에서 실행할 수 없으므로 Azure Spatial Anchors 기능을 테스트하려면 프로젝트를 디바이스에 배포해야 합니다.

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법을 미리 알아보려면 [디바이스에 애플리케이션 빌드](mr-learning-base-ch1.md#build-your-application-to-your-device) 지침을 참조할 수 있습니다.

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>HoloLens 2에서 앱 실행 및 앱 내 지침 수행

### <a name="create-an-anchor-to-store-a-location"></a>위치를 저장할 앵커 만들기

이 섹션에서는 개체 위치를 저장하는 방법을 배웁니다.

애플리케이션을 실행하고 환경의 주 메뉴에서 **개체 설정**을 클릭합니다.

저장하려는 개체의 **이름**을 지정하고 **개체 설정**을 클릭하여 계속합니다. 개체에 대한 추가 정보를 추가하려면 **이미지**를 선택하고 개체에 대해 설명합니다.

위치를 저장하려면 **위치 저장**을 클릭합니다.

저장하려는 위치에 이동하여 놓을 수 있는 **앵커 포인터**가 표시됩니다. 그런 다음, 확인 팝업을 받게 됩니다. 위치를 확인하고 저장하려면 **예**를 클릭합니다. 그렇지 않으면 **아니오**를 클릭하고 위치를 다시 선택하여 위치를 변경할 수 있습니다.

**예**를 클릭하여 위치를 확인하면 위치 및 앵커 ID가 Azure 클라우드 스토리지에 저장됩니다. 저장되면 개체의 이름과 함께 앵커에 **개체 태그**가 표시됩니다.

이제 개체 위치가 성공적으로 저장되었습니다.

### <a name="query-for-finding-an-anchor-location"></a>앵커 위치를 찾기 위한 쿼리

앵커 위치를 성공적으로 저장한 후에는 주 메뉴에서 **개체 검색**을 선택하여 앵커 위치를 찾을 수 있습니다.

**개체 검색**을 클릭하면 검색할 개체의 이름을 지정해야 하는 새 창이 표시됩니다.

개체의 이름을 입력하고 **개체 검색**을 클릭합니다. 개체가 이전에 저장되고 데이터베이스에 있는 경우 이전에 저장한 개체의 모든 세부 정보를 포함하는 개체 카드를 가져옵니다.

이제 **위치 표시**를 클릭하여 개체를 찾을 수 있습니다. **위치 표시**를 클릭하면 시스템이 클라우드 스토리지에서 개체 주소를 쿼리합니다.

위치를 성공적으로 검색한 후 **화살표**를 통해 개체의 위치로 이동합니다. 개체의 위치를 찾을 때까지 화살표 표시를 따릅니다.

개체를 찾으면 개체 이름이 맨 위에 표시되고, 화살표 표시가 사라지고, 이제 **개체 태그**를 클릭하여 개체의 세부 정보를 볼 수 있습니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure Spatial Anchors가 Hololense 2에서 개체 위치를 저장하고 검색하는 방법을 배웠습니다.

최종 자습서에서는 **Azure Bot Service**를 사용하여 자연어를 애플리케이션에 대한 새로운 상호 작용 방법으로 추가하는 방법을 알아봅니다.

[다음 자습서: 5. LUIS와 Azure Bot Service 통합](mr-learning-azure-05.md)
