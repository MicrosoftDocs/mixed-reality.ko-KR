---
title: Azure 클라우드 자습서 - 3. Azure Custom Vision 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 Azure Custom Vision을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens, HoloLens 2, Azure Custom Vision, Azure Cognitive Services
ms.localizationpriority: high
ms.openlocfilehash: c3ba5a715b0e77d7869d598a472341cd390c2d23
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306123"
---
# <a name="3-integrating-azure-custom-vision"></a>3. Azure Custom Vision 통합

이 자습서에서는 **Azure Custom Vision**을 사용하는 방법을 알아봅니다. 사진 세트를 업로드하여 *추적된 개체*와 연결하고 **Custom Vision** 서비스에 업로드하여 학습 프로세스를 시작합니다. 그런 다음, 이 서비스를 사용하여 웹캠 피드에서 사진을 캡처하여 *추적된 개체*를 감지합니다.

## <a name="objectives"></a>목표

* Azure Custom Vision에 대한 기본 사항 알아보기
* 이 프로젝트에서 Custom Vision을 사용하도록 장면을 설정하는 방법 알아보기
* 이미지 업로드, 학습 및 감지를 통합하는 방법 알아보기

## <a name="understanding-azure-custom-vision"></a>Azure Custom Vision 이해

**Azure Custom Vision**은 **Cognitive Services** 제품군에 속하며 이미지 분류자를 학습시키는 데 사용됩니다. 이미지 분류자는 학습된 모델을 사용하여 일치하는 태그를 적용하는 AI 서비스입니다. 이 분류 기능은 애플리케이션이 *추적된 개체*를 감지하는 데 사용됩니다.

[Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)에 대해 자세히 알아보세요.

## <a name="preparing-azure-custom-vision"></a>Azure Custom Vision 준비

시작하려면 그 전에 사용자 지정 비전 프로젝트를 만들어야 하며, 가장 빠른 방법은 웹 포털을 사용하는 것입니다.

이 [빠른 시작 자습서](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)를 *이미지 업로드 및 태그 지정* 섹션까지 수행하여 계정과 프로젝트를 설정합니다.

> [!WARNING]
> 모델을 학습시키려면 태그당 태그 2개 및 이미지 5개 이상이 있어야 합니다. 이 애플리케이션을 사용하려면 이미지가 5개 이상인 태그를 하나 이상 만들어야 합니다. 그래야 나중에 학습 과정에서 실패하지 않습니다.

## <a name="preparing-the-scene"></a>장면 준비

프로젝트 창에서 **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** 폴더로 이동합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

여기에서 프리팹 **ObjectDetectionManager**를 장면 계층 구조로 끌어옵니다.

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

Hierarchy(계층 구조) 창에서 **ObjectDetectionManager** 개체를 찾아서 선택합니다.
**ObjectDetectionManager** 프리팹에는 **ObjectDetectionManager(스크립트)** 가 포함되어 있으며 Inspector(인스펙터) 창에서 볼 수 있듯이 여러 설정에 따라 달라집니다.

## <a name="retrieving-azure-api-resource-credentials"></a>Azure API 리소스 자격 증명 검색

**ObjectDetectionManager(스크립트)** 설정에 필요한 자격 증명은 Azure Portal 및 Custom Vision 포털에서 검색할 수 있습니다.

### <a name="azure-portal"></a>Azure Portal

이 자습서의 *장면 준비* 섹션에서 만든 **Cognitive Services** 유형의 Custom Vision 리소스를 찾아서 이동합니다. 여기에서 *키 및 엔드포인트*를 클릭하여 필요한 자격 증명을 검색합니다.

### <a name="custom-vision-dashboard"></a>Custom Vision 대시보드

[Custom Vision](https://www.customvision.ai/projects) 대시보드에서 이 자습서용으로 만든 프로젝트를 열고 페이지 오른쪽 위 모서리 기어 아이콘을 클릭하여 설정 페이지를 엽니다. 오른쪽 *리소스* 섹션에서 필요한 자격 증명을 찾을 수 있습니다.

**ObjectDetectionManager(스크립트)** 가 올바르게 설정되었으면 장면 계층 구조에서 **SceneController** 개체를 찾아서 선택합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

**SceneController** 구성 요소의 *Object Detection Manager*(개체 감지 관리자) 필드가 비어 있는 것이 보이면 **ObjectDetectionManager**를 계층 구조에서 이 필드로 끌어오고 장면을 저장합니다.

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>이미지 가져오기 및 업로드

장면을 실행하고 **Set Object**(개체 설정)를 클릭한 후 [이전 단원](mr-learning-azure-02.md)에서 만든 **추적된 개체** 중 하나의 이름을 입력합니다. 이제 **Object Card**(개체 카드) 아래쪽에서 있는 **Computer Vision** 단추를 클릭합니다.

새 창이 열리면 이미지 인식을 위해 모델을 학습시키기 위한 사진을 6장 찍어야 합니다. **Camera** 단추를 클릭하고 추적할 개체를 보면서 AirTap을 수행하는 동작을 6번 수행합니다.

> [!TIP]
> 모델 학습을 향상시키려면 각 이미지를 서로 다른 각도와 조명 조건에서 찍습니다.

이미지가 충분해지면 **Train**(학습) 단추를 클릭하여 클라우드에서 모델 학습 프로세스를 시작합니다. 학습을 활성화하면 모든 이미지가 업로드되고 학습이 시작되며, 최대 1분 이상 걸릴 수 있습니다. 메뉴 안의 메시지는 현재 진행 상황을 나타내며 완료가 나타나면 애플리케이션을 중지할 수 있습니다.

> [!TIP]
> **ObjectDetectionManager(스크립트)** 는 찍힌 이미지를 Custom Vision 서비스에 직접 업로드합니다. 대안으로, Custom Vision API는 이미지 URL을 허용하며, 연습으로 **ObjectDetectionManager(script)** 를 수정하여 이미지를 Blob 스토리지에 대신 업로드할 수 있습니다.

## <a name="detect-objects"></a>개체 감지

이제 학습된 모델을 테스트에 추가하고, 애플리케이션을 실행하고, 주 메뉴에서 **검색 개체**를 클릭하고 해당 **추적된 개체**의 이름을 입력할 수 있습니다. **Object Card**(개체 카드)가 표시되면 **Custom Vision** 단추를 클릭합니다. 여기에서 **ObjectDetectionManager**는 카메라의 배경에서 이미지를 캡처하기 시작하고 진행률이 메뉴에 표시됩니다. 모델을 학습시키는 데 사용한 개체로 카메라를 향하게 하면 잠시 후에 개체를 감지하는 것이 보입니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure Custom Vision을 사용하여 이미지를 학습시키고 분류 서비스를 사용하여 연결된 **추적된 개체**와 일치하는 이미지를 감지하는 방법을 알아보았습니다.

다음 자습서에서는 Azure Spatial Anchors를 사용하여 추적된 개체를 물질계의 위치에 링크하는 방법과 사용자를 추적된 개체에 링크된 위치로 안내하는 화살표를 표시하는 방법을 알아봅니다.

[다음 자습서: 4. Azure Spatial Anchors 통합](mr-learning-azure-04.md)
