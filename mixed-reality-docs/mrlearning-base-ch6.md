---
title: MR 학습 자료 모듈-음력 모듈 어셈블리 샘플 환경
description: 이 단원에서는 고유한 샘플 환경을 만들려면 이전 단원에서 학습 하는 여러 개념 결합 했습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 303ed17724ba8799490aa7bca7a60600f6e5349b
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929610"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR 학습 자료 모듈-음력 모듈 어셈블리 샘플 환경

이 단원에서는 고유한 샘플 환경을 만들려면 이전 단원에서 학습 하는 여러 개념 결합 했습니다. 추적된 손을 사용 하 여 음력 모듈 부분을 선택 하 고 음력 모듈을 조합 하는 사용자가 해야 하는 여기서 음력 모듈 어셈블리 응용 프로그램을 만듭니다. 배치 힌트를 경험에 따르면 다시 설정 하는 데 공간으로 음력 모듈 시작을 설정/해제 하려면 pressable 단추 사용! 나중에 자습서를 계속 예정 강력한 다중 사용자 사용 사례 공간 맞춤에 대 한 Azure 공간 앵커를 활용 하는 비롯 하 여이 환경을 구축 하 합니다.

## <a name="objectives"></a>목표

- 고유한 환경을 만들려면 이전 단원에서 여러 개념을 결합
- 개체를 설정/해제 하는 방법 알아보기
- Pressable 단추를 사용 하 여 복잡 한 이벤트 트리거
- Rigidbody 물리 및 강제 사용
- 탐색 도구 설명 사용

## <a name="instructions"></a>지침

### <a name="configuring-the-lunar-module"></a>음력 모듈 구성

이 챕터에서는 샘플 경험을 만드는 데 필요한 다양 한 구성 요소를 도입 했습니다 것입니다.

1. 음력 모듈 어셈블리 prefab 자료 장면에 추가 합니다. 사용자 프로젝트 탭에서이 위해 "Rocket Launcher_Tutorial." 검색 자산에는 prefab을 찾을 수 있습니다 > BaseModuleAssets > Prefabs 합니다. 두 rocket launcher prefabs; 표시 될 수 있습니다. 이름이 "자습서" 및 다른 이름으로 "완료합니다." "Rocket Launcher_Tutorial" prefab을 자료 장면 끕니다. 자유롭게 장면에 prefab의 배치를 배치할 수 있습니다.
   참고: "Rocket Launcher_Complete" prefab은 참조용으로 완료 된 시작 관리자를 구성 합니다. 

![6 단원 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

재질 "x-ray." 라는 여러 자식 개체 표시는 계층의 "Rocket Launcher_Tutorial" 게임 개체를 확장 하 고 "음력 모듈" 개체를 더 확장 "X-레이" 자료 약간 반투명 색을 사용자에 대 한 배치 힌트로 사용 하는 수 있습니다. 

![6 단원 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 하려는 사용자 상호 작용 아래 이미지 에서처럼 음력 모듈에 5 개 부분이 있습니다.

1.  Rover 인클로저
2.  연료 탱크
3.  에너지 셀
4.  도킹 포털 
5.  외부 센서

![6 단원 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 참고: 장면에 있는 개체의 이름에는 기본 장면 계층에 표시 되는 게임 개체 이름이 일치 하지 않습니다.

2단계: 오디오 소스 음력 모듈에 추가 합니다. 음력 모듈 기본 장면 계층에서 선택 되어 있는지 확인 하 고 "구성 요소를 추가 합니다." 클릭 "오디오 원본"에 대 한 검색 하 고 개체에 추가 합니다. 비워 둠 지금은 나중에 시작 소리를 재생 하려면이 사용 됩니다.
 ![6 단원 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 3 단계: "설정/해제 배치 힌트입니다." 스크립트 추가 "구성 요소 추가" 및 "설정/해제 배치 힌트입니다."에 대 한 검색을 클릭 합니다. 이것이 앞에서 언급 한 반투명 힌트 (x-레이 자료를 사용 하 여 개체)를 켜거나 끌 수 있도록 사용자 지정 스크립트입니다. 
![6 단원 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 4 단계: 5 개의 개체가 있으므로 게임 개체 배열 크기에 대 한 "5"에 입력 합니다. 그런 다음 5 개의 새 요소가 표시 됩니다. 

![6 단원 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

"None (게임 개체)입니다."를 표시 하는 상자를 끌어 각 반투명 개체 기본 장면에 음력 모듈에서 다음 개체를 끌어 옵니다. 

• 백팩

•   GasTank

• Topleftbody

• 코

• LeftTwirler

 ![6 단원 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

이제 "배치 힌트를 설정/해제" 스크립트 구성 됩니다. 이렇게 하면 힌트를 켜거나 끄고를 있습니다.

5단계: "음력 모듈 시작" 스크립트를 추가 합니다. "구성 요소 추가" 단추를 클릭, "시작 음력 모듈"에 대 한 검색 하 고 선택 합니다. 이 스크립트는 음력 모듈을 실행 해야 합니다. 구성된 단추를 누를 것 음력 모듈의 rigid 바디 구성 요소를 위쪽 force 추가 하 고 모듈을 위쪽으로 시작 하면 합니다. 인 경우 실내 음력 모듈에 ceiling 메시에 대해 충돌할 수 있습니다. 하지만 옥외 있다면이 fly에서 공간에 무기한으로 합니다. 

![6 단원 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6단계: 음력 모듈까지 정상적으로 비행 됩니다 있도록 위한 것을 조정 합니다. 0.01의 값을 시도 합니다. "Rb" 필드를 비워 둡니다. Rb rigid 바디를 의미 하 고 런타임에이 필드를 자동으로 채워지지 것입니다.

![6 단원 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>음력 모듈 부분 개요
음력 모듈 부분 부모 개체에는 사용자와 상호 작용할 개체의 컬렉션입니다. 장면 이름을 paretheses에서 레이블이 지정) (으로 게임 개체 이름은 아래 목록에 제공 됩니다.

- 백팩을 (연료 탱크가)
- GasTank (에너지 셀)
- TopLeftBody (Rover 인클로저)
- 코 (도킹 포털)
- LeftTwirler (외부 센서)

4 단원에서 설명 했 듯이 이러한 각 개체에는 조작 처리기를 확인 합니다. 조작 처리기를 사용 하 여 사용자 잡고 개체를 조작할 수 있습니다. 또한 "두 전달된 조작 유형" 설정 "이동 및 회전 합니다."로 설정 되어 있는지를 note합니다 이 개체를 이동 하 고 어셈블리 응용 프로그램에 대 한 원하는 기능에는 해당 크기를 변경 하지 사용자만 허용 합니다.
또한 먼 조작 모듈 부분의 직접적인 상호 작용에 대해서만 허용 하도록 선택 되지 않습니다.

![6 단원 Chapter2im](images/Lesson6_Chapter2im.PNG)

파트 어셈블리 데모 스크립트 (위에 표시 됨)는 사용자가 음력 모듈에 배치 될 개체를 관리 하는 스크립트입니다. 

"개체를 현재 위치" 필드 선택 (n 이미지 위의 백팩을/연료 탱크가의 경우)에 연결할 수 있는 개체와는 변환입니다. 

"가까운 거리" 및 "훨씬 Distance" 설정 하려는 파트 진행에서 맞춰집니다 또는 릴리스될 근접도 확인 하는 것에 대 한 책임이 있습니다. 예를 들어 백팩을/연료 탱크 제자리에 맞출 음력 모듈에서 0.1 단위 되도록 해야 합니다. "지금까지 거리" 개체 음력 모듈에서 분리 되도록 해야 하는 위치를 설정 합니다. 이 경우 사용자의 직접 백팩을/연료 탱크를 잡고 위치로 다시 맞추기에서 제거할 음력 모듈에서 0.2 단위 이었기 해야 합니다.

"도구 설명 개체"은 장면에서 도구 설명 레이블입니다. 개체 위치에 모눈을 레이블이 비활성화 됩니다. 

오디오 소스 자동으로 잡을 수 있습니다. 

### <a name="placement-hints-buttons"></a>배치 힌트 단추
[단원 2](mrlearning-base-ch2.md)를 배치 하 고 항목의 색 변경 작업을 수행 하거나 푸시 될 때 소리를 재생 하는 단추를 구성 하는 방법을 알아보았습니다. 배치 힌트를 표시 하거나 숨기는 단추를 구성 하는 것을 이러한 원칙을 사용 하도록 계속 됩니다. 

목표 반투명 배치 힌트의 표시 유형을 설정/해제는 배치 힌트 단추를 누를 때마다 있도록 단추가 구성 하는 것입니다. 

1단계: 배치 힌트 개체를 기본 장면 계층 구조에서 선택한 음력 모듈 검사기 창에서 빈 런타임은 슬롯으로 이동 합니다. 
 ![6 단원 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 2 단계: 이제 드롭다운 목록을 라고 표시 된 부분, "function 없습니다."를 클릭 해당 메뉴 및 "TogglePlacementHints," 아래로 이동 "ToggleGameObjects ()"를 선택 합니다. ToggleGameObjects()는 배치 힌트를 설정 / 해제 단추를 누를 때마다 표시 되거나 숨겨지도록 수 있도록 합니다.
 ![6 단원 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>구성 다시 설정 단추

사용자는 실수 또는 실수로 throw 하거나 제거 하려는 환경을 rest 경우가 됩니다. 다시 설정 단추 환경을 다시 시작 하는 기능을 추가 합니다. 

1단계: 다시 설정 단추를 선택 합니다. 기본 장면에서 라고 하는 "ResetRoundButton." 

2단계: 기본 장면 계층 음력 모듈 "단추가 눌림" 아래에서 빈 슬롯 끌어옵니다 [관리자] 패널입니다.
 ![6 단원 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3단계: "Function 없습니다" 라는 드롭다운 메뉴를 선택 하 고 "LaunchLunarModule." 위로 이제 "resetModule ()"를 선택

![6 단원 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 참고: 기본적으로 "GameObject.BroadcastMessage" 하도록 구성 되어 있는지 "ResetPlacement." 알 수 있습니다. 이 메시지를 브로드캐스팅하는 RocketLauncher_Tutorial의 모든 자식 개체에 대 한 "ResetPlacement"를 호출 합니다. "ResetPlacement()"에 대 한 메서드가 포함 된 모든 개체의 위치를 다시 설정 하 여 해당 메시지에 응답 합니다. 

### <a name="launching-the-lunar-module"></a>음력 모듈 시작
이 챕터 [시작] 단추를 구성 했습니다. 이렇게 하면 사용자가 단추를 눌러를 공간으로 음력 모듈을 시작 합니다.

1단계: [시작] 단추를 선택 합니다. (기본 장면에서 라고 하는 "LaunchRoundButton"). 검사기 창에서 "터치 End" 아래에서 빈 슬롯을 음력 모듈을 끕니다.
 ![6 단원 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 2 단계: "Function 없습니다." 라는 드롭다운 메뉴를 선택 합니다. "LaunchLunarModule" 위에 놓고 "StopThruster ()"를 선택 합니다. 이 얼마나 러스트 음력 모듈에 사용자가 제어 합니다. 
 ![6 단원 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 3 단계: "ButtonPressed()"에서 음력 모듈 (클릭, 대기 중 및 끌기) 빈 슬롯을 추가 합니다. 

4단계: "Function 없습니다" 라는 드롭다운 메뉴를 클릭 하 고 "LaunchLunarModule" 마우스로 "StartThruster ()"를 선택 합니다. 
 ![6 단원 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 5 단계: 음악을 rocket이 시작 하는 경우 연동 되도록 음악 음력 모듈에 추가 합니다. 이렇게 하려면 "단추 Pressed()" 아래에서 다음 빈 슬롯을 음력 모듈을 끌어 놓습니다.

6단계: "Function 없습니다" 라는 드롭다운 메뉴를 선택 하 고 "AudioSource" 마우스로 "PlayOneShot (AudioClip)."를 선택 합니다. 다양 한 소리를 MRTK 함께 살펴보시기 바랍니다. 예를 들어 하겠습니다 "MRTK_Gem."를 사용 하 여 계속 합니다.
 ![6 단원 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>축 하. 
이 응용 프로그램을 완전히 구성한! 이제 play를 누르면 완벽 하 게 음력 모듈을 조합, 힌트를 설정/해제, 음력 모듈을 시작 하 수 것부터 다시 다시 설정 합니다.
