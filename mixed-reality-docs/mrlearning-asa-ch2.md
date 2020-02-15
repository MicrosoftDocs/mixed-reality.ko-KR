---
title: Azure 공간 앵커 자습서-2. Azure 공간 앵커 저장, 검색 및 공유
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250749"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Azure 공간 앵커 저장, 검색 및 공유

이 자습서에서는 HoloLens 2의 저장소에 앵커 ID를 저장 하 여 여러 앱 세션에서 Azure 공간 앵커를 저장 하는 방법을 알아봅니다. 다중 장치 앵커 맞춤을 위해이 앵커 ID를 다른 장치에 공유 하는 방법에 대해서도 알아봅니다.

## <a name="objectives"></a>목표

* 앱 세션 간에 지 속성을 위해 HoloLens 2 로컬 디스크와의 Azure 공간 앵커 Id를 저장 하 고 검색 하는 방법에 대해 알아봅니다.
* 다중 장치 시나리오에서 사용자 간에 Azure 공간 앵커 Id를 공유 하는 방법을 알아봅니다.

## <a name="preparing-the-scene"></a>장면 준비

프로젝트 창에서 **자산** > **mrtk로 이동 합니다. AzureSpatialAnchors** > **Prefabs** 폴더입니다. CTRL 단추를 누른 채 **ButtonParent_SaveAnchorId** 를 클릭 하 고 **ButtonParent_ShareAnchorId** 두 Prefabs를 선택한 다음 계층 창으로 끌어 장면에 추가 합니다.

![mrlearning](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>앱 세션 간 Azure 앵커 유지-디스크에 앵커 ID 저장
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

이 섹션에서는 HoloLens 2 로컬 디스크와의 Azure 앵커 ID를 저장 하 고 검색 하는 방법에 대해 설명 합니다. 이렇게 하면 서로 다른 앱 세션 간에 동일한 앵커 ID를 사용 하 여 Azure를 쿼리하면 이전 앱 세션과 동일한 위치에서 앵커 된 holograms 위치를 지정할 수 있습니다.

계층 창에서 두 개의 단추를 포함 하는 **ButtonParent_SaveAnchorId** 개체를 확장 하 고, 하나는 HoloLens 2 저장소에 AZURE 앵커 id를 저장 하 고 다른 하나는 디스크에서 저장 된 id를 검색 하는 단추입니다.

![mrlearning](images/mrlearning-asa/tutorial2-section2-step1-1.png)

위의 자습서에서 [화면을 작동 하는 단추 구성](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) 에 있는 것과 동일한 단계를 수행 하 여 **Pressable Button Holo Lens 2 (스크립트)** 구성 요소를 구성 하 고, **Interactable (스크립트)** 구성 요소를 두 개의 각 단추에 구성 합니다.

* **SaveAzureAnchorIdToDisk** 개체의 경우 AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 함수를 할당 합니다.
* **GetAzureAnchorIdFromDisk** 개체의 경우 AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 함수를 할당 합니다.

HoloLens에 업데이트 된 응용 프로그램을 빌드하는 경우 이제 Azure 앵커 ID를 저장 하 여 앱 세션 간에 Azure 공간 앵커를 유지할 수 있습니다. 이를 테스트 하려면 다음 단계를 수행 하면 됩니다.

1. 로켓 시작 관리자 환경을 원하는 위치로 이동 합니다.
2. Azure 세션을 시작 합니다.
3. Azure 앵커 만들기 (로켓 시작 관리자 환경의 위치에 앵커 생성)
4. Azure 앵커 ID를 디스크에 저장 합니다.
5. 응용 프로그램을 다시 시작 합니다.
6. 디스크에서 Azure 앵커를 가져옵니다 (방금 저장 한 앵커 ID를 로드 함).
7. Azure 세션을 시작 합니다.
8. Azure 앵커 찾기 (3 단계의 위치에서 로켓 시작 관리자 환경을 배치 합니다.)

## <a name="share-azure-anchors-between-multiple-devices"></a>여러 장치 간에 Azure 앵커 공유

이 섹션에서는 여러 장치 간에 Azure 앵커 ID를 공유 하는 방법에 대해 설명 합니다. 이렇게 하면 여러 장치에서 동일한 앵커 ID를 사용 하 여 Azure를 쿼리하면 고정 된 holograms 공간적으로 정렬 될 수 있습니다. 공간 맞춤 (예: 여러 장치 간의 동일한 물리적 위치에 있는 동일한 holograms를 확인 하는 것은 HoloLens 2에서 로컬 공유 환경의 핵심입니다.

여러 가지 방법으로 여러 [사용자 기능 자습서](mrlearning-sharing(photon)-ch1.md) 시리즈에 설명 된 메서드를 비롯 하 여 장치 간에 Azure 앵커 id를 전송할 수 있습니다. 이 예제에서는 간단한 웹 서비스를 사용 하 여 장치 간에 앵커 Id를 업로드 하 고 다운로드 합니다.

계층 창에서 두 개의 단추를 포함 하는 **ButtonParent_ShareAnchorId** 개체를 확장 합니다. Azure 앵커 ID를 웹 서버에 업로드 하는 단추 하 나와 웹 서버에서 ID를 다운로드 하는 데 사용할 수 있는 단추는 다음과 같습니다.

![mrlearning](images/mrlearning-asa/tutorial2-section3-step1-1.png)

위의 자습서에서 [화면을 작동 하는 단추 구성](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) 에 있는 것과 동일한 단계를 수행 하 여 **Pressable Button Holo Lens 2 (스크립트)** 구성 요소를 구성 하 고, **Interactable (스크립트)** 구성 요소를 두 개의 각 단추에 구성 합니다.

* **ShareAzureAnchorIdToNetwork** 개체의 경우 AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 함수를 할당 합니다.
* **GetAzureAnchorIdFromNetwork** 개체의 경우 AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 함수를 할당 합니다.

두 HoloLens 장치에 업데이트 된 응용 프로그램을 빌드하는 경우 이제 Azure 앵커 ID를 공유 하 여 두 장치 간에 공간을 맞출 수 있습니다. 이를 테스트 하려면 다음 단계를 수행 하면 됩니다.

1. HoloLens 장치 1: 로켓 시작 관리자 환경을 원하는 위치로 이동 합니다.
2. HoloLens 장치 1: Azure 세션을 시작 합니다.
3. HoloLens 장치 1: Azure 앵커 만들기 (로켓 시작 관리자 환경의 위치에서 앵커 생성).
4. HoloLens 장치 1: Azure 앵커 ID를 네트워크에 공유 합니다.
5. HoloLens 장치 2: 응용 프로그램을 다시 시작 합니다.
6. HoloLens 장치 2: 네트워크에서 공유 앵커 ID 가져오기 (HoloLens 장치 1에서 공유 되는 앵커 ID 페치).
7. HoloLens 장치 2: Azure 세션을 시작 합니다.
8. HoloLens 장치 2: Azure 앵커 찾기 (3 단계의 위치에서 로켓 시작 관리자 환경을 배치)

> [!TIP]
> HoloLens가 하나만 있는 경우에도 두 번째 HoloLens 장치를 사용 하는 대신 응용 프로그램을 다시 시작 하 여 기능을 테스트할 수 있습니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Azure 공간 앵커 ID를 HoloLens의 로컬 디스크에 저장 하 여 응용 프로그램 세션 및 응용 프로그램 다시 시작 간에 Azure 공간 앵커를 유지 하는 방법을 배웠습니다. 또한 기본 다중 사용자, 정적 홀로그램 공유 환경에 대해 여러 장치 간에 Azure 공간 앵커를 공유 하는 방법을 배웠습니다.

다음 자습서에서는 사용자에 게 실시간 피드백을 제공 하는 방법을 알아봅니다. 이 피드백에는 앵커 만들기, 환경 이해의 품질 및 Azure 세션의 상태에 대 한 정보가 포함 됩니다. 피드백을 사용 하지 않으면 사용자는 앵커가 Azure에 성공적으로 업로드 되었는지 여부, 환경 품질이 앵커 만들기에 충분 한지 아니면 현재 상태 인지를 알 수 없습니다.

[다음 단원: 3. Azure 공간 고정 피드백 표시](mrlearning-asa-ch3.md)
