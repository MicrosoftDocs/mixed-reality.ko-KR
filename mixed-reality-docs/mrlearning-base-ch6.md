---
title: MR 학습 기본 모듈 - 달탐사선 어셈블리 샘플 환경
description: 이 단원에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730844"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR 학습 기본 모듈 - 달탐사선 어셈블리 샘플 환경

이 단원에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다. 사용자가 추적된 손을 사용하여 달탐사선 부품을 선택하고 달탐사선 조립을 시도하는 데 사용할 달탐사선 어셈블리 애플리케이션을 만들겠습니다. 누를 수 있는 단추를 사용하여 배치 힌트를 설정/해제하고 환경을 다시 설정하며 달탐사선을 우주로 발사합니다. 향후 자습서에서는 공간 맞춤을 위해 Azure Spatial Anchors를 사용하는 강력한 다중 사용자 사용 사례를 포함하여 이러한 경험을 지속적으로 구축해 나갈 것입니다.

## <a name="objectives"></a>목표

- 이전 단원의 여러 개념을 결합하여 고유한 환경 만들기
- 개체를 설정/해제하는 방법 알아보기
- 누를 수 있는 단추를 사용하여 복합 이벤트 트리거
- 강체 물리학 및 힘 사용
- 도구 설명 사용 살펴보기

## <a name="instructions"></a>지침

### <a name="configuring-the-lunar-module"></a>달탐사선 구성

이 챕터에서는 샘플 환경을 만드는 데 필요한 다양한 구성 요소를 소개합니다.

1. 달탐사선 어셈블리 프리팹을 기본 장면에 추가합니다. 이를 위해 프로젝트 탭에서 "Rocket Launcher_Tutorial"을 검색합니다. 이 프리팹은 Assets>BaseModuleAssets>Prefabs에서 찾을 수도 있습니다. 로켓 발사대 프리팹은 이름이 "tutorial"인 것과 "complete"인 것 등, 두 개가 있습니다. "Rocket Launcher_Tutorial" 프리팹을 기본 장면으로 끌어갑니다. 장면의 원하는 위치에 프리팹을 배치합니다.
   참고: "Rocket Launcher_Complete" 프리팹은 완성된 발사대로, 참고를 위해 제공된 것입니다. 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

계층 구조에 "Rocket Launcher_Tutorial" 게임 개체를 펼친 다음, "Lunar Module" 개체를 펼치면 "x-ray"라는 재료가 있는 여러 하위 개체가 표시됩니다. "x-ray" 재료는 사용자를 위한 배치 힌트로 사용할 약간 반투명 색상을 사용할 수 있습니다. 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 사용자가 상호 작용하는 달탐사선에는 아래 그림과 같이 다섯 가지 부분이 있습니다.

1.  탐사선 인클로저
2.  연료 탱크
3.  에너지 셀
4.  도킹 포털 
5.  외부 센서

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 참고: 기본 장면에 표시되는 게임 개체 이름은 장면의 개체 이름과 일치하지 않습니다.

2단계: 오디오 소스를 달탐사선에 추가합니다. 기본 장면 계층 구조에서 달탐사선을 선택하고 "구성 요소 추가"를 클릭합니다. "Audio Source"를 검색하고 개체에 추가합니다. 지금은 비워둡니다. 나중에 발사음을 재생하는 데 사용할 것입니다.
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 3단계: "배치 힌트 설정/해제" 스크립트를 추가합니다. "구성 요소 추가"를 클릭하고 "배치 힌트 설정/해제"를 검색합니다. 이것은 앞에서 언급한 반투명 힌트(x-ray 재료가 있는 개체)를 활성화 및 비활성화할 수 있는 사용자 지정 스크립트입니다. 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 4단계: 5개의 개체가 있으므로 게임 개체 배열 크기에 "5"를 입력합니다. 그러면 5개의 새 요소가 표시됩니다. 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

각각의 반투명 개체를 이름이 “없음(게임 개체)”인 상자로 끌어갑니다. 기본 장면에서 달탐사선으로부터 다음 개체를 끌어옵니다. 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

이제 "배치 힌트 설정/해제" 스크립트가 구성되었습니다. 이렇게 하면 힌트를 활성화하거나 비활성화할 수 있습니다.

5단계: "달탐사선 발사" 스크립트를 추가합니다. "구성 요소 추가" 단추를 클릭하고 “달탐사선 발사”를 검색하여 선택합니다. 이 스크립트는 달탐사선 발사를 담당합니다. 구성된 단추를 누르면 달탐사선의 강체 구성 요소에 상승력을 더하여 탐사선이 위쪽으로 발사되게 합니다. 실내에 있다면 달탐사선이 천장 메시에 충돌할 수 있습니다. 그러나 실외라면 우주로 무한 비행합니다. 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6단계: 추진력을 조정하여 달탐사선이 정상적으로 비행할 수 있게 합니다. 값 0.01을 시도해 봅니다. "Rb" 필드는 비워 둡니다. Rb는 Rigid Body(강체)를 뜻하며 이 필드는 런타임 중에 자동으로 채워집니다.

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>달탐사선 부분 개요
달탐사선 부분 부모 개체는 사용자가 상호 작용하는 개체의 컬렉션입니다. 게임 개체 이름(괄호 안의 이름으로 장면 레이블 붙임)은 아래 목록에 있습니다.

- Backpack(연료 탱크)
- GasTank(에너지 셀)
- TopLeftBody(탐사선 인클로저)
- Nose(도킹 포트)
- LeftTwirler(외부 센서)

4단원에서 논의한 것처럼 각각의 개체에는 조작 처리기가 있습니다. 조작 처리기를 사용하여 사용자가 개체를 잡고 조작할 수 있습니다. 또한 “two handed manipulation type(양손 조작 설정)”이 “move and rotate(이동 및 회전)”로 되어 있습니다. 즉 사용자는 개체를 이동할 수만 있고 크기를 변경할 수는 없습니다. 어셈블리 애플리케이션에서 필요한 기능입니다.
또한 모듈 부분의 직접 상호 작용만 허용하기 위해 먼 조작을 선택하지 않았습니다.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

파트 어셈블리 데모 스크립트(위에 표시)는 사용자가 달탐사선에 개체를 배치하는 것을 관리하는 스크립트입니다. 

"Object To Place" 필드는 연결될 수 있는 개체와 함께 선택된 변환입니다(위의 이미지의 경우 백팩/연료 탱크). 

"Near Distance" 및 "Far Distance" 설정은 부품이 제 위치에 고정되거나 위치에서 분리되는 근접도를 결정합니다. 예를 들어, 백팩/연료 탱크가 위치에 고정되려면 달탐사선에서 0.1단위 떨어져 있어야 합니다. "Far Distance"는 개체가 달탐사선에서 떨어져야 하는 위치를 설정합니다. 이 경우 사용자의 손이 백팩/연료 탱크를 쥐고 달탐사선에서 0.2단위 떨어지게 끌어 위치에서 분리해야 합니다.

"Tool Tip Object"는 장면의 도구 설명 레이블입니다. 개체가 위치에 잠기면 레이블이 비활성화됩니다. 

오디오 소스는 자동으로 잡힙니다. 

### <a name="placement-hints-buttons"></a>배치 힌트 단추
[2단원](mrlearning-base-ch2.md)에서는 항목 색상 변경이나 눌렀을 때 사운드를 재생하는 등의 작업을 수행하는 단추를 배치 및 구성하는 방법을 알아보았습니다. 이제 이 원칙을 사용하여 배치 힌트를 설정/해제하는 단추를 구성해 보겠습니다. 

사용자가 배치 힌트 단추를 누를 때마다 반투명 배치 힌트의 표시를 설정/해제하는 단추를 구성하려 합니다. 

1단계: 기본 장면 계층 구조에서 배치 힌트 개체를 선택한 상태에서 달탐사선을 검사기 창의 빈 “runtime only” 슬롯으로 이동합니다. 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 2단계: 이제 드롭다운 목록의 "no function" 부분을 클릭합니다. "TogglePlacementHints"까지 아래로 이동하고 이 메뉴에서 "ToggleGameObjects ()"를 선택합니다. ToggleGameObjects()는 배치 힌트를 설정/해제하여 단추를 누를 때마다 힌트가 표시되거나 표시되지 않게 합니다.
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>다시 설정 단추 구성

사용자가 실수하거나, 우발적으로 개체를 버리거나, 단순히 작업을 중단하고 쉬고 싶은 경우가 있습니다. 다시 설정 단추는 환경을 다시 시작하는 기능을 추가합니다. 

1단계: 다시 설정 단추를 선택합니다. 기본 장면에서 이름이 "ResetRoundButton"입니다. 

2단계: 기본 장면 계층 구조에서 달탐사선을 검사기 창의 "button pressed" 아래 빈 슬롯으로 끌어옵니다.
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3단계: "no function"이라 적힌 드롭다운 메뉴를 선택하고 "LaunchLunarModule" 위에 커서를 올립니다. 이제 "resetModule ()"을 선택합니다.

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 참고: 기본적으로 "GameObject.BroadcastMessage"가 "ResetPlacement"로 구성되어 있습니다. 이것은 RocketLauncher_Tutorial의 모든 자식 개체에 대해 "ResetPlacement" 메시지를 브로드캐스트합니다. "ResetPlacement()"에 대한 메서드를 갖는 모든 개체는 그 위치를 다시 설정하는 것으로 메시지에 응답합니다. 

### <a name="launching-the-lunar-module"></a>달탐사선 발사
이 챕터에서는 발사 단추를 구성합니다. 이를 통해 사용자가 이 단추를 눌러 달탐사선을 우주로 발사할 수 있습니다.

1단계: 발사 단추를 선택합니다(기본 장면에서 이름이 "LaunchRoundButton"임). 달탐사선을 검사기 창의 "Touch End" 아래 빈 슬롯으로 끌어옵니다.
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 2단계: "no function"이라는 드롭다운 메뉴를 선택합니다. "LaunchLunarModule" 위에 커서를 올리고 "StopThruster ()"를 선택합니다. 이것은 사용자가 달탐사선에 부여할 추진력 크기를 제어합니다. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 3단계: "ButtonPressed()"에서 달탐사선을 빈 슬롯에 추가합니다(클릭하고 누른 상태에서 끌기). 

4단계: "no function"이라 적힌 드롭다운 메뉴를 클릭하고 "LaunchLunarModule" 위에 커서를 올린 다음, "StartThruster ()"를 선택합니다. 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 5단계: 로켓이 발사되면 음악이 재생되도록 음악을 달탐사선에 추가합니다. 이를 위해 달탐사선을 "Button Pressed()" 아래 다음 빈 슬롯으로 끌어옵니다.

6단계: "no function"이라는 드롭다운 메뉴를 선택하고 "AudioSource"에 커서를 놓은 다음, “PlayOneShot (AudioClip)”을 선택합니다. MRTK에 포함된 여러 사운드를 원하는 대로 살펴봅니다. 이 예제에서는 “MRTK_Gem”을 사용하려고 합니다.
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>축하합니다. 
이 애플리케이션의 구성을 마쳤습니다. 이제 재생을 누르면 달탐사선을 완전히 조립하고, 힌트를 설정/해제하며, 달탐사선을 발사하고, 다시 설정하여 처음부터 다시 시작할 수 있습니다.
