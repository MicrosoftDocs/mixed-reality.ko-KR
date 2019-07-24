---
title: MR 학습 기본 모듈 - 달탐사선 어셈블리 샘플 환경
description: 이 단원에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 79f2d3a4a3224533761ea2e4a7e73dc3d4d5e53e
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387690"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 음력 모듈 샘플 응용 프로그램 만들기

이 자습서에서는 이전 단원에서 설명한 여러 가지 개념을 결합 하 여 고유한 샘플 환경을 만듭니다. 사용자가 추적 된 손을 사용 하 여 음력 모듈 부분을 선택 하 고 음력 모듈을 조합 하 여 수행 해야 하는 음력 모듈 어셈블리 응용 프로그램을 만듭니다. Pressable 단추를 사용 하 여 배치 힌트를 전환 하 고, 경험을 다시 설정 하 고, 음력 모듈을 공간으로 시작 합니다. 이후 자습서에서는 공간 맞춤을 위해 Azure 공간 앵커를 활용 하는 강력한 다중 사용자 사용 사례를 포함 하 여이 환경을 계속 빌드할 예정입니다.

## <a name="objectives"></a>목표

- 이전 단원의 여러 개념을 결합하여 고유한 환경 만들기
- 개체를 설정/해제하는 방법 알아보기
- 누를 수 있는 단추를 사용하여 복합 이벤트 트리거
- 강체 물리학 및 힘 사용
- 도구 설명 사용 살펴보기

## <a name="instructions"></a>지침

### <a name="configuring-the-lunar-module"></a>달탐사선 구성

이 섹션에서는 샘플 환경을 만드는 데 필요한 다양 한 구성 요소를 소개 합니다.

1. 기본 장면에 prefab 음력 모듈 어셈블리를 추가 합니다. 이렇게 하려면 프로젝트 탭에서 로켓 Launcher_Tutorial을 검색 합니다. 
Prefab Prefabs에서 > > 자산의을 찾습니다. 또한 두 개의 로켓 시작 관리자 prefabs이 표시 됩니다. 이름이 "tutorial"이 고 다른 하나는 "complete"입니다. 로켓 Launcher_Tutorial prefab를 기본 장면으로 끌고 원하는 대로 배치 합니다.
   참고: 로켓 Launcher_Complete prefab는 참조를 위해 제공 되는 완성 된 시작 관리자입니다. 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

계층에서 로켓 Launcher_Tutorial game 개체를 확장 하 고 음력 Module 개체를 추가로 확장 하는 경우 "x-레이" 라는 재질을 포함 하는 여러 자식 개체를 찾을 수 있습니다. "X-y" 재질을 사용 하면 사용자에 대 한 배치 힌트로 사용할 약간의 반투명 색을 사용할 수 있습니다. 

![6 단원에서는 chapter1.txt 참고 목표](images/Lesson6_Chapter1_noteaim.PNG) 는 아래 이미지에 표시 된 것 처럼 사용자가 상호 작용 하는 음력 모듈에 5 가지 부분이 있습니다.

1.  탐사선 인클로저
2.  연료 탱크
3.  에너지 셀
4.  도킹 포털 
5.  외부 센서

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 참고: 기본 장면 계층 구조에 표시 되는 게임 개체 이름이 장면의 개체 이름과 일치 하지 않습니다.

2단계: 오디오 소스를 달탐사선에 추가합니다. 기본 장면 계층 구조에서 음력 모듈이 선택 되어 있는지 확인 하 고 구성 요소 추가를 클릭 합니다. 오디오 소스를 검색 하 고 개체에 추가 합니다. 지금은 비워둡니다. 나중에 발사음을 재생하는 데 사용할 것입니다.

 ![6 단원에서는 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
3단계: 스크립트를 추가 하 고 배치 힌트를 설정/해제 합니다. 구성 요소 추가를 클릭 하 고 배치 힌트 설정/해제를 검색 합니다. 이 스크립트는 앞에서 언급 한 반투명 힌트 (x-레이 재료를 사용 하는 개체)를 켜고 끌 수 있는 사용자 지정 스크립트입니다.  
![6 단원에서는 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
4단계: 5 개의 개체가 있으므로 게임 개체 배열 크기에 대해 "5"를 입력 합니다. 그러면 5 개의 새 요소가 표시 됩니다.  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

각 투명 개체를 모든 이름 (Game 개체) 상자로 끕니다.
기본 장면에서 달탐사선으로부터 다음 개체를 끌어옵니다. 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

이제 배치 힌트 설정/해제 스크립트가 구성 됩니다. 그러면 힌트를 켜고 끌 수 있습니다.

5단계: 시작 음력 모듈 스크립트를 추가 합니다. 구성 요소 추가 단추를 클릭 하 고 "시작 음력 모듈"을 검색 하 여 선택 합니다. 이 스크립트는 음력 모듈을 시작 합니다. 구성 된 단추를 누르면 음력 모듈의 고정 본문 구성 요소에 상향 force가 추가 되 고 모듈이 위쪽으로 시작 됩니다. 실내에 있다면 달탐사선이 천장 메시에 충돌할 수 있습니다. 그러나 실외라면 우주로 무한 비행합니다. 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6단계: 추진력을 조정하여 달탐사선이 정상적으로 비행할 수 있게 합니다. 값 0.01을 시도해 봅니다. "Rb" 필드는 비워 둡니다. Rb는 Rigid Body(강체)를 뜻하며 이 필드는 런타임 중에 자동으로 채워집니다.

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>음력 모듈 부분 개요
음력 모듈 파트 부모 개체는 사용자가 상호 작용 하는 개체의 컬렉션입니다. Paretheses에 이름이 지정 된 장면이 있는 게임 개체 이름이 아래 목록에 제공 됩니다.

- Backpack(연료 탱크)
- GasTank(에너지 셀)
- TopLeftBody(탐사선 인클로저)
- Nose(도킹 포트)
- LeftTwirler(외부 센서)

이러한 각 개체에는 4 단원에 설명 된 조작 처리기가 있습니다. 조작 처리기를 사용 하면 사용자가 개체를 잡아 조작할 수 있습니다. 또한 두 개의 전달 조작 형식이 이동 및 회전으로 설정 되어 있습니다. 즉 사용자는 개체를 이동할 수만 있고 크기를 변경할 수는 없습니다. 어셈블리 애플리케이션에서 필요한 기능입니다.
또한 모듈 파트의 직접 상호 작용에 대해서만 허용 하도록 Far 조작이 선택 취소 되어 있습니다.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

파트 어셈블리 데모 스크립트 (위에 표시 됨)는 사용자가 음력 모듈에 저장 하는 개체를 관리 하는 스크립트입니다. 

필드를 놓을 개체는 위의 이미지에 표시 된 것 처럼 선택한 변환 이며, 연결 된 개체와 연결 된 백팩/연료 탱크입니다. 

근거리 거리 및 원거리 거리 설정에 따라 부품이 제자리에 스냅 되거나 출시 될 수 있는 근접성이 결정 됩니다. 예를 들어 백팩/연료 탱크는 한 곳에 맞추기 전에 음력 모듈에서 0.1 단위 여야 합니다. 먼 거리 설정은 개체가 음력 모듈에서 분리 될 수 있는 위치를 설정 합니다. 이 경우 사용자의 손이 백팩/연료 탱크를 쥐고 달탐사선에서 0.2단위 떨어지게 끌어 위치에서 분리해야 합니다.

도구 설명 개체는 장면의 도구 설명 레이블입니다. 개체를 제자리에 물릴 때 레이블은 사용할 수 없습니다. 

오디오 소스가 자동으로 grabbed 됩니다. 

### <a name="placement-hints-buttons"></a>배치 힌트 단추
[2단원](mrlearning-base-ch2.md)에서는 항목 색상 변경이나 눌렀을 때 사운드를 재생하는 등의 작업을 수행하는 단추를 배치 및 구성하는 방법을 알아보았습니다. 이제 이 원칙을 사용하여 배치 힌트를 설정/해제하는 단추를 구성해 보겠습니다. 

목표는 사용자가 배치 힌트 단추를 누를 때마다 투명 한 배치 힌트의 표시 유형을 전환 하도록 단추를 구성 하는 것입니다. 

1단계: 기본 장면 계층 구조에서 배치 힌트 개체가 선택 되어 있는 동안에는 inspector 패널의 빈 런타임 전용 슬롯으로 음력 모듈을 이동 합니다. 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 2단계: 이제 함수 없음 드롭다운 목록을 클릭 합니다. TogglePlacementHints로 이동 하 고 해당 메뉴 아래에서 ToggleGameObjects ()를 선택 합니다. ToggleGameObjects ()는 단추를 누를 때마다 표시 되거나 표시 되지 않도록 배치 힌트를 설정 및 해제 합니다.  
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>다시 설정 단추 구성

사용자가 실수로 또는 실수로 개체를 throw 하거나 환경을 다시 설정 하려는 경우가 있습니다. 다시 설정 단추는 환경을 다시 시작 하는 기능을 추가 합니다. 

1단계: 다시 설정 단추를 선택 합니다. 기본 장면에는 이름이 ResetRoundButton입니다. 

2단계: 기본 장면 계층 구조에서 클릭 하 여 기본 장면 계층에서 빈 슬롯으로 이동 합니다.
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3단계: 함수 없음 드롭다운 메뉴를 선택 하 고 LaunchLunarModule를 마우스로 가리킨 다음 resetModule ()을 선택 합니다.

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 참고: 기본적으로 GameObject BroadcastMessage는 배치를 ResetPlacement 합니다. 그러면 RocketLauncher_Tutorial의 모든 자식 개체에 대해 ResetPlacement 라는 메시지가 브로드캐스트합니다. ResetPlacement ()에 대 한 메서드가 있는 개체는 위치를 다시 설정 하 여 해당 메시지에 응답 합니다. 

### <a name="launching-the-lunar-module"></a>음력 모듈 시작
이 섹션에서는 시작 단추를 구성 하는 방법을 explaings. 이렇게 하면 사용자가 단추를 누르고 음력 모듈을 공간으로 시작할 수 있습니다.

1단계: 시작 단추를 선택 합니다. 기본 장면에서 LaunchRoundButton가 호출 됩니다. Inspector 패널의 Touch End 아래에 있는 빈 슬롯으로 음력 모듈을 끕니다.
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 2단계: 함수 없음 드롭다운 메뉴를 선택 하 고 LaunchLunarModule를 마우스로 가리킨 다음 StopThruster ()를 선택 합니다. 이는 사용자가 음력 모듈에 제공할 위한 것 크기를 제어 합니다. 
 ![6 단원에서는 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)  
3단계: ButtonPressed () 아래에서 음력 모듈 (클릭, 길게 및 끌기)을 빈 슬롯에 추가 합니다. 

4단계: 함수 없음 드롭다운 메뉴를 클릭 하 고 LaunchLunarModule를 마우스로 가리킨 다음 StartThruster ()를 선택 합니다. 
 ![6 단원에서는 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)  
5단계: 로켓이 꺼진 경우 음악이 재생 되도록 음력 모듈에 음악을 추가 합니다. 이렇게 하려면 음력 모듈을 단추 누름 () 아래의 빈 슬롯으로 끕니다.

6단계: 함수 없음 드롭다운 메뉴를 선택 하 고 오디오 소스를 마우스로 가리킨 다음 PlayOneShot (오디오 클립)를 선택 합니다. MRTK에 포함된 여러 사운드를 원하는 대로 살펴봅니다. 이 예에서는 "MRTK_Gem"를 사용 합니다.
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>축하합니다. 
이 응용 프로그램을 완전히 구성 했습니다. 이제 play를 누르면 음력 모듈을 완전히 조합 하 고, 힌트를 전환 하 고, 음력 모듈을 시작 하 고 다시 시작 하도록 다시 설정할 수 있습니다.
