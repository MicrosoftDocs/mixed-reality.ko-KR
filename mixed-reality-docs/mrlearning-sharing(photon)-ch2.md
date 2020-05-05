---
title: 다중 사용자 기능 자습서 - 3. 여러 사용자 연결
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610872"
---
# <a name="2-connecting-multiple-users"></a>2. 여러 사용자 연결

이 자습서에서는 라이브 공유 환경의 일부로 여러 사용자를 연결하는 방법을 알아봅니다. 자습서를 마치면 여러 디바이스에서 애플리케이션을 실행하여 각 사용자가 다른 사용자의 아바타가 움직이는 것을 실시간으로 보게 할 수 있습니다.

## <a name="objectives"></a>목표

* 공유 환경에서 여러 사용자를 연결하는 방법 알아보기

## <a name="preparing-the-scene"></a>장면 준비

이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.

Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** 폴더로 이동합니다. CTRL 단추를 누른 상태에서 **DebugWindow**, **NetworkLobby**, **SharedPlayground**를 클릭하여 세 가지 프리팹을 선택합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

세 가지 프리팹을 선택한 상태로 Hierarchy 창으로 끌어서 장면에 추가합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>사용자 프리팹 만들기

이 섹션에서는 공유 환경의 사용자를 나타내는 데 사용할 프리팹을 만듭니다.

### <a name="1-create-and-configure-the-user"></a>1. 사용자 만들기 및 구성

Hierarchy 창에서 빈 영역을 마우스 오른쪽 단추로 클릭하고 **Create Empty**를 선택하여 빈 개체를 장면에 추가하고 개체의 이름을 **PhotonUser**로 지정하고 다음과 같이 구성합니다.

* 변환 **위치**는 X = 0, Y = 0, Z = 0으로 설정되어야 합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

**PhotonUser** 개체를 선택한 채로 Inspector 창에서 **Add Component** 단추를 사용하여 **Photon User (Script)** 구성 요소를 PhotonUser 개체에 추가합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

Inspector 창에서 **Add Component** 단추를 사용하여 **Generic Net Sync (Script)** 구성 요소를 PhotonUser 개체에 추가하고 다음과 같이 구성합니다.

* **Is User** 확인란을 선택합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

Inspector 창에서 **Add Component** 단추를 사용하여 **Photon View (Script)** 구성 요소를 PhotonUser 개체에 추가하고 다음과 같이 구성합니다.

* **Observed Components** 필드에 Generic Net Sync(Script) 구성 요소를 할당합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. 아바타 만들기

Hierarchy 창에서 **PhotonUser** 개체를 마우스 오른쪽 단추로 클릭하고 **3D Object** > **Sphere**를 선택하여 PhotonUser 개체의 자식으로 구형 개체를 만들어서 다음과 같이 구성합니다.

* 변환 **Position**은 X = 0, Y = 0, Z = 0으로 설정해야 합니다.
* 변환 **Scale**을 적절한 크기(예: X = 0.15, Y = 0.15, Z = 0.15)로 변경합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. 프리팹 만들기

Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

Resources 폴더를 선택한 상태에서 **PhotonUser** 개체를 Hierarchy 창에서 **Resources** 폴더로 **클릭하고 끌어서** PhotonUser 개체를 프리펩으로 만듭니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

Hierarchy 창에서 **PhotonUser** 개체를 마우스 오른쪽 단추로 클릭하고 **Delete**를 선택하여 장면에서 제거합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>사용자 프리팹을 인스턴스화하도록 PUN 구성

이 섹션에서는 이전 섹션에서 만든 PhotonUser 프리펩을 사용하도록 프로젝트를 구성합니다.

Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.

Hierarchy 창에서 **NetworkLobby** 개체를 펼쳐서 **NetworkRoom** 자식 개체를 선택한 다음, Inspector 창에서 **Photon Room (Script)** 구성 요소를 찾아서 다음과 같이 구성합니다.

* **Photon User Prefab** 필드에 Resources 폴더의 **PhotonUser** 프리팹을 할당합니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>여러 사용자 환경 체험

Unity 프로젝트를 빌드하고 HoloLens에 배포했으면 Unity로 돌아가서 HoloLens에서 애플리케이션이 실행되는 동안 재생 단추를 눌러 게임 모드로 들어갑니다. 머리(HoloLens)를 움직이면 HoloLens 사용자 아바타가 움직이는 것을 볼 수 있습니다.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법을 미리 알아보려면 [디바이스에 애플리케이션 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침을 참조할 수 있습니다.

> [!CAUTION]
> 애플리케이션에서 Photon에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.

## <a name="congratulations"></a>축하합니다.

여러 사용자가 동일한 환경에 연결하여 서로의 움직임을 볼 수 있도록 프로젝트를 구성하는 데 성공했습니다. 다음 자습서에서는 개체의 움직임도 여러 디바이스에서 공유되도록 기능을 구현합니다.

[다음 자습서: 2. 여러 사용자와 개체 이동 공유](mrlearning-sharing(photon)-ch3.md)
