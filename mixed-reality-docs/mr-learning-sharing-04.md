---
title: 다중 사용자 기능 자습서 - 4. 여러 사용자와 개체 움직임 공유
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 7dbe25cd1b0329e366fcbd567074018025032f9e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376565"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. 여러 사용자와 개체 움직임 공유

이 자습서에서는 공유 환경의 모든 참가자가 협업하고 서로의 상호 작용을 볼 수 있도록 개체의 움직임을 공유하는 방법에 대해 알아봅니다.

## <a name="objectives"></a>목표

* 개체의 움직임을 공유하도록 프로젝트 구성
* 기본 다중 사용자 협업 앱을 빌드하는 방법 알아보기

## <a name="preparing-the-scene"></a>장면 준비

이 섹션에서는 자습서 프리팹을 추가하여 장면을 준비합니다.

Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** 폴더로 이동하여 **TableAnchor** 프리팹을 Hierarchy 창의 **SharedPlayground** 개체로 끌어와서 SharedPlayground 개체의 자식으로 장면에 추가합니다.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>개체를 인스턴스화하도록 PUN 구성

이 섹션에서는 [시작 자습서](mr-learning-base-01.md)에서 만든 Rover 탐색기 환경을 사용하도록 프로젝트를 구성하고 인스턴스화할 위치를 정의합니다.

Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.

Hierarchy 창에서 **NetworkLobby** 개체를 펼쳐서 **NetworkRoom** 자식 개체를 선택한 다음, Inspector 창에서 **Photon Room (Script)** 구성 요소를 찾아서 다음과 같이 구성합니다.

* **Rover 탐색기 프리팹** 필드에 대해 리소스 폴더에서 **RoverExplorer_Complete_Variant** 프리팹을 할당합니다.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

**NetworkRoom** 자식 개체가 선택된 상태로 Hierarchy 창에서 **TableAnchor** 개체를 펼친 다음, Inspector 창에서 **Photon Room (Script)** 구성 요소를 찾아서 다음과 같이 구성합니다.

* **Rocket 탐색기 위치** 필드에 대해 Hierarchy 창에서 TableAnchor > **Table** 자식 개체를 할당합니다.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>공유 개체 움직임 환경 체험

Unity 프로젝트를 빌드하고 HoloLens에 배포했으면 Unity로 돌아가서 HoloLens에서 앱이 실행되는 동안 재생 단추를 눌러 게임 모드로 들어갑니다. HoloLens에서 개체를 움직이면 Unity에서 개체가 움직이는 것을 볼 수 있습니다.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>축하합니다.

다른 사용자가 개체를 움직일 때 개체가 움직이는 것을 볼 수 있도록 개체 이동을 동기화하도록 프로젝트를 성공적으로 구성했습니다. 다음 자습서에서는 실제 환경에 맞게 환경을 조정하는 기능을 구현합니다. 이렇게 하면 사용자가 실제 위치에서 서로 볼 수 있으므로 개체는 모든 사용자에 대해 동일한 물리적 위치와 회전에 표시됩니다.

[다음 자습서: 5. 공유 환경에 Azure Spatial Anchors 통합](mr-learning-sharing-05.md)
