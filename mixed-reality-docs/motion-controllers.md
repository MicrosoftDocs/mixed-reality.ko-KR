---
title: 컨트롤러 동작
description: 혼합 현실 동작 컨트롤러에 대 한 세부 정보입니다.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 컨트롤러, 컨트롤러 동작
ms.openlocfilehash: b44964ab872bd080349ecf1b04b3f7082b521a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604962"
---
# <a name="motion-controllers"></a>컨트롤러 동작

동작 컨트롤러가 [하드웨어 accessories](hardware-accessories.md) 혼합된 현실에서 작업을 수행 하는 작업을 할 수 있도록 합니다. 통해 컨트롤러 동작의 장점은 [제스처](gestures.md) 컨트롤러 있다는 공간에서 정확한 위치 디지털 개체를 사용 하 여 미세 조정 된 상호 작용을 허용 합니다. Windows Mixed Reality 몰입 형 헤드셋에 대 한 동작 컨트롤러는 해당 환경에서 사용자는 조치를 취하는 기본 방법입니다.

![Windows Mixed Reality 동작 컨트롤러](images/winmr-ck-1080x1080-350px.jpg)


## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>기능</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> 컨트롤러 동작</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>하드웨어 세부 정보

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Windows Mixed Reality 동작 컨트롤러의 공간에 벽에 하드웨어를 설치 하지 않아도 즉, 몰입 형 헤드셋에 센서를 사용 하 여 필드의 보기 이동 정확 하 고 응답성이 뛰어난 추적을 제공 합니다. 이러한 동작 컨트롤러는 쉽게 설치 및 몰입 형 헤드셋 Windows Mixed Reality로 이식성을 제공 합니다. 장치 파트너가 홍보 하 고 이러한 컨트롤러 소매 선반에이 휴일을 판매 하도록 계획 합니다.

![컨트롤러에 알아봅니다](images/controllerimage-750px.png)<br>
*컨트롤러에 알아봅니다*

**기능은 다음과 같습니다.**
* 광학 추적
* 트리거
* 단추를 선택 합니다.
* 엄지 스틱
* 터치 패드

## <a name="setup"></a>설치 프로그램

### <a name="before-you-begin"></a>시작하기 전 주의 사항

**이 필요 합니다.**
* 두 동작 컨트롤러의 집합입니다.
* 4 개의 AA 배터리 합니다.
* PC Bluetooth 4.0을 지원 합니다.

**Windows, Unity 및 드라이버 업데이트 확인**
* 방문 [도구를 설치](install-the-tools.md) 혼합된 현실 개발 등 Windows에서 Unity의 기본 버전입니다.
* 최신 했는지 확인 [헤드셋 및 중인 컨트롤러 드라이버](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)합니다.

### <a name="pairing-controllers"></a>컨트롤러를 연결합니다.

호스트 PC 사용 하 여 컨트롤러 동작을 연결할 수 있습니다 다른 Bluetooth 장치와 같은 Windows 설정을 사용 하 여 합니다.

1. 컨트롤러의 뒷면에 2 AA 배터리를 삽입 합니다. 현재 배터리 표지를 해제 합니다.
2. 외부 USB Bluetooth 어댑터는 기본 제공 하는 Bluetooth 라디오 대신를 사용 하는 경우 살펴보시기 합니다 [Bluetooth에 대 한 유용한 정보](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 계속 하기 전에 합니다. 기본 제공 라디오를 사용 하 여 데스크톱 구성에 대 한 안테나 연결 되었는지 확인 하십시오.
3. 오픈 **Windows 설정** -> **장치** -> **Bluetooth 추가 또는 기타 장치** -> **Bluetooth** "동작 컨트롤러 – 오른쪽"와 "동작 컨트롤러 – 왼쪽"의 이전 인스턴스를 모두 제거 합니다. 또한 목록 맨 아래에 다른 장치 범주를 확인 합니다.
4. 선택 **Bluetooth 추가 또는 기타 장치** 및 Bluetooth 장치를 검색 하기 시작 하는지 확인 합니다.
5. 컨트롤러에서 설정, 해제 되 면 buzzes 컨트롤러의 Windows 단추를 누릅니다.
6. Led까지 페어링 단추 (배터리 구획에서 탭)를 누른 펄스를 시작합니다.
7. "동작 컨트롤러-왼쪽" 또는 "동작 컨트롤러-오른쪽" 대기 목록 맨 아래에 표시 합니다. 쌍을 선택 합니다. 컨트롤러는 연결 된 경우 한 번 진동 됩니다.

   ![여러 인스턴스가 표시 목록 아래쪽에서 하나를 선택 하는 경우을 쌍으로 동작 컨트롤러를 선택 합니다.](images/450px-bluetooth-add-a-device-300px.png)<br>
   *"쌍;" 컨트롤러 동작 선택 인스턴스를 여러 개 있으면 목록 맨 아래에서 하나를 선택합니다*
   
8. Bluetooth 설정에서 표시 하는 컨트롤러를 살펴보면 **"마우스, 키보드 및 펜" 범주** 으로 **Connected**합니다. 이 시점에서 펌웨어 업데이트 – 발생할 수 있습니다 참조 [절로](motion-controllers.md#updating-controller-firmware)합니다.
9. 배터리 덮개를 다시 연결 합니다.
10. 두 번째 컨트롤러의 1-9 단계를 반복 합니다.

두 컨트롤러가 모두 성공적으로 쌍 후 설정에는 다음과 같습니다 아래 **"마우스, 키보드 및 펜" 범주** 

   ![연결 된 동작 컨트롤러](images/450px-motion-controller-connected-300px.png)<br>
   *연결 된 동작 컨트롤러*

페어링 한 후에 컨트롤러 꺼져있는 경우 해당 상태 쌍으로 연결 된으로 표시 됩니다. 경우 컨트롤러는 "기타" 범주 쌍만 부분적으로 완료 되었습니다 장치와 컨트롤러 기능 가져오려고 다시 수행할 필요가에서 영구적으로 유지 합니다.

### <a name="updating-controller-firmware"></a>컨트롤러 펌웨어를 업데이트 하는 중

* 몰입 형 헤드셋 사용자 PC에 연결 된 새 컨트롤러 펌웨어를 사용 하 고 펌웨어가 밀어넣습니다 동작 컨트롤러에 자동으로 다음에 켜져 합니다. 컨트롤러 펌웨어 업데이트 순환 동작에 대 한 자세한 LED 사분면 패턴에 의해 표시 됩니다 및 1 ~ 2 분입니다.
* 펌웨어 업데이트를 완료 된 후 컨트롤러가 다시 부팅 하 고 다시 연결 됩니다. 두 컨트롤러가 모두 이제 연결 되어야 합니다. 
    
    ![연결 된 컨트롤러](images/cyk-connected-300px.jpg)<br>
    *Bluetooth 설정에서 연결 된 컨트롤러*

* 컨트롤러 작업을 제대로 확인 합니다.
    1. 시작할 **혼합 현실 포털** 혼합 현실 집을 입력 합니다.
    2. 및 컨트롤러를 이동 하 고, 추적, 테스트 단추를 확인 하 고, 확인 [텔레포트](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 작동 합니다. 체크 아웃 하지 않으면 이러한 [컨트롤러 문제 해결 동작](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)합니다.

## <a name="gazing-and-pointing"></a>Gazing 및 가리키는

Windows Mixed Reality 상호 작용에 대 한 두 가지 주요 모델 지원 **gaze 및 커밋** 하 고 **가리키고 커밋**:
* 사용 하 여 **gaze 및 커밋**, 사용자가 사용 하 여 개체를 대상 해당 [gaze](gaze.md) 한 다음 직접 어 탭 ","는 gamepad ","는 clicker "또는" 음성 인식을 사용 하 여 개체를 선택 합니다.
* 사용 하 여 **가리키고 커밋**, 사용자가 대상 개체를 가리키고 가능한 동작 컨트롤러는 것을 목표로 하 고 다음 컨트롤러의 트리거를 사용 하 여 개체를 선택 합니다.

가능한 경우 동작 컨트롤러를 사용 하 여 가리키는 지원 해야 하는 앱 사용 게이즈 기반 상호 작용에 선택한 사용자에 게 사용 하는 장치를 입력 합니다.

### <a name="managing-recoil-when-pointing"></a>가리킬 때 recoil 관리

동작 컨트롤러를 사용 하 여 지점 및 커밋를 때 사용자가 해당 트리거를 풀링 하 여 조치를 취할 수 컨트롤러를 사용 합니다. 트리거를 활발 하 게 끌어오기 사용자 의도 보다 해당 트리거 끌어오기로 끝에 더 높은 컨트롤러를 지 향하는 끝날 수도 있습니다.

사용자 트리거를 끌어올 때 발생할 수 있는 이러한 모든 recoil를 관리 하려면 앱 트리거의 아날로그 축 값 0.0을 초과 하는 경우 해당 대상 광선을 고정할 수 있습니다. 다음 프레임을 사용 하는 대상 광선 몇 나중에 트리거 값 1.0 도달 최종 눌러 짧은 기간 내 발생으로 작업을 수행할 수 있습니다. 수준의 사용 하는 경우 [복합 탭 제스처](gestures.md#composite-gestures), Windows는이 대상을 관리 광선 캡처 및 시간 제한 수입니다.

## <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 포인팅 포즈 비교

Windows Mixed Reality 다양 한 폼 팩터 동작 컨트롤러에서는, 각 컨트롤러의 디자인을 사용 하 여 렌더링할 때 가리키는 사용 해야 다른 사용자의 직접 위치 사이의 "전달" 방향 해당 앱의 자연 관계를 컨트롤러입니다.

이러한 컨트롤러를 더 잘 나타내기 위해 두 가지 종류의 포즈 각 상호 작용 원본에 대해 조사할 수 있습니다는 **그립 자세** 하며 **포인터 자세**합니다.

### <a name="grip-pose"></a>그립 자세

합니다 **그립 포즈** 는 HoloLens 감지한 손 모양 손바닥 또는 동작 컨트롤러 보유 palm의 위치를 나타냅니다.

몰입 형 헤드셋 그립 포즈 가장 사용 렌더링 **사용자의 직접** 또는 **사용자의 직접에 보관 된 개체**검 또는 총 등입니다. 그립 자세는으로 동작 컨트롤러를 시각화 하는 경우에 사용 됩니다 합니다 **렌더링 가능한 모델** 제공 동작에 대 한 Windows에서 컨트롤러는 원본 및 회전 중심으로 그립 포즈를 사용 합니다.

그립 자세는 특히 다음과 같이 정의 됩니다.
* 합니다 **위치를 잡고**: 물론 컨트롤러를 보유 하는 경우 팜 중심 왼쪽 또는 오른쪽 가운데 그립 내의 위치를 조정 합니다. Windows Mixed Reality 동작 컨트롤러에서이 위치는 일반적으로 감각을 단추를 사용 하 여 맞춥니다.
* 합니다 **방향을 올바른 축 잡고**: 완전히 플랫 5 손가락 자세를 직접 열면 광선과 표준 프로그램 palm에서 (왼쪽된 palm, palm 오른쪽에서 이전 버전과에서 앞으로)
* 합니다 **방향을 정방향 축 잡고**: 부분적으로 (처럼 컨트롤러 보유) 직접을 닫을 때, 광선을 가리키는 "forward" 튜브를 통해 비 엄지 손가락으로 구성 합니다.
* 합니다 **축 위쪽 방향 잡고**: 오른쪽 정방향 정의 사용 권한에 포함 된 최대 축.

### <a name="pointer-pose"></a>포인터 자세

합니다 **포인터 포즈** 앞으로 가리키는 컨트롤러의 끝을 나타냅니다.

시스템 제공 포인터 자세는 raycast 했으면 **컨트롤러 모델 자체 렌더링**합니다. 일부 가상 건, 같은 컨트롤러 대신 다른 가상 개체를 렌더링 하는 경우 총 앱 정의 모델의 barrel 함께 전송 되는 ray 같은 가상 개체에 대 한 가장 자연 스러운 광선을 사용 하 여 가리켜야 합니다. 사용자가 가상 개체와 실제 컨트롤러 하지에서 볼 수 있으므로 가상 개체를 사용 하 여 가리키는 가능성이 됩니다 앱을 사용 하는 더 자연 스러운.

## <a name="controller-tracking-state"></a>컨트롤러 상태를 추적

헤드셋와 같은 Windows Mixed Reality 동작 컨트롤러 설정이 필요 하지 않습니다 외부 추적 센서입니다. 대신, 컨트롤러 자체 헤드셋의 센서에서 추적 됩니다.

사용자가 헤드셋의 필드의 보기 컨트롤러를 이동 하면 대부분의 경우에서 Windows 계속 컨트롤러 위치를 유추 하 고 앱을 제공 합니다. 경우 컨트롤러 근사치 정확도 위치로 컨트롤러의 위치는 삭제 하는 충분 한 시간에 대 한 추적 visual 끊어졌습니다.

이 시점에서 시스템 얼굴이 움직일, 여전히 해당 내부 방향 센서를 사용 하 여 컨트롤러의 true 방향을 노출 하는 동안 사용자의 위치를 추적 하는 사용자에 게 컨트롤러 본문 잠금을 됩니다. 컨트롤러를 사용 하 고 UI 요소를 활성화 하는 많은 앱은 사용자 알아채지 않으면 서의 대략적인 정확도 정상적으로 작동할 수 있습니다.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>상태를 명시적으로 추적 하는 방법에 대 한 추론

위치 추적 상태에 따라 다르게 처리 하려는 앱 수 있습니다 더 나아가 SourceLossRisk PositionAccuracy 등 컨트롤러의 상태에 대 한 속성을 검사 합니다.

<table>
<tr>
<th> 상태를 추적합니다. </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>높은 정확도</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>높은 정확도 (손실의 위험이)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>대략적인 정확도</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 대략 일치 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>위치가 없습니다</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 대략 일치 </td><td style="background-color: orange"> false</td>
</tr>
</table>



이러한 동작 컨트롤러 추적 상태는 다음과 같이 정의 됩니다.
* **높은 정확도 경우:** 동작 컨트롤러 헤드셋의 뷰 필드 내에 있는 동안 정확도 높은 위치, visual 추적에 따라 일반적으로 제공 됩니다. 참고는 컨트롤러를 이동 하는 일시적으로 보기의 필드를 벗어나거나 헤드셋 센서에서 일시적으로 가려지는지 (예: 사용자의 반면) 기반 컨트롤러의 관성 추적으로 짧은 시간에 대 한 정확도 높은 포즈 반환할 계속 자체입니다.
* **높은 정확도 (손실의 위험이):** 사용자 헤드셋의 뷰 필드의 가장자리를 넘어 동작 컨트롤러를 움직이면 헤드셋 곧 없게 됩니다 컨트롤러의 위치를 시각적으로 추적할 수 있습니다. 앱 경우 컨트롤러에 도달이 FOV 경계 확인 하 여 알고 합니다 **SourceLossRisk** 1.0에 도달 합니다. 이 시점에서 앱 꾸준하게 매우 고품질 발생 해야 하는 컨트롤러 제스처를 일시 중지 하도록 선택할 수 있습니다.
* **대략적인 정확도:** 경우 컨트롤러 근사치 정확도 위치로 컨트롤러의 위치는 삭제 하는 충분 한 시간에 대 한 추적 visual 끊어졌습니다. 이 시점에서 시스템 얼굴이 움직일, 여전히 해당 내부 방향 센서를 사용 하 여 컨트롤러의 true 방향을 노출 하는 동안 사용자의 위치를 추적 하는 사용자에 게 컨트롤러 본문 잠금을 됩니다. 컨트롤러를 사용 하 고 UI 요소를 활성화 하는 많은 앱 사용자 알아채지 않으면 서 일반 while로 대략적인 정확도 작동할 수 있습니다. 라우터로도 충분 입력된 요구 사항이 있는 앱에서이 삭제 감지 하도록 선택할 수 있습니다 **높은** 정확도 **근사치** 검사 하 여 정확도 **PositionAccuracy** 속성에 대 한 사용자에 게 더 넓은 hitbox 오프 스크린 대상에서이 시간 동안 예입니다.
* **위치가 없습니다.** 컨트롤러는 오랜 시간 동안 대략적인 정확도에서 작동할 수 있습니다, 있지만 때로는 시스템 임을 알고 있습니다 본문 잠긴 위치도 하지 의미 있는 지금은. 예를 들어 방금 설정 하는 컨트롤러 수 하지 관찰 한 시각적으로 또는 사용자가 다음 다른 사용자가 선택 하는 컨트롤러 작성 될 수 있습니다. 시스템에서 해당 시간에 앱에 그 위치를 제공 하지 것입니다 하 고 **TryGetPosition** false를 반환 합니다.

## <a name="interactions-low-level-spatial-input"></a>상호 작용 합니다. 하위 수준 공간 입력

실습 및 동작 컨트롤러에서 핵심 상호 작용은 **선택**를 **메뉴**를 **이해**를 **터치 패드**,  **엄지 스틱**, 및 **홈**합니다.
* **선택** 뒤에 릴리스 하는 키를 눌러 이루어진를 홀로그램을 활성화 하려면 기본 상호 작용입니다. 동작 컨트롤러용는 선택 키를 눌러 컨트롤러의 트리거를 사용 하 여 수행할 수 있습니다. Select를 수행 하는 다른 방법을 통해은 [음성 명령](voice-input.md) "Select"입니다. 모든 앱 내에서 동일한 선택 상호 작용을 사용할 수 있습니다. 생각 하는 Select 마우스에 해당 하는 한 번에 대해 알아봅니다 및 모든 앱에서 적용 하는 범용 작업을 클릭 합니다.
* **메뉴** 상황에 맞는 메뉴 표시 또는 다른 보조 동작을 수행 하는 데 사용 하는 개체에 대 한 역할에 대 한 보조 상호 작용입니다. 동작 컨트롤러를 사용 하 여 컨트롤러를 사용 하는 메뉴 작업을 수행할 수 있습니다 *메뉴* 단추입니다. (즉, 해당에 있는 햄버거 "메뉴" 아이콘을 사용 하 여 단추)
* **잡고** 는 어떻게 사용자가 직접 작업을 수행할 수 속속들이 조작할 수 있는 개체입니다. 동작 컨트롤러와 긴밀 하 게에 첫 번째 빼내 감각을 작업을 수행할 수 있습니다. 동작 컨트롤러는 감각을 잡기 단추, palm 트리거 또는 다른 센서를 사용 하 여 검색할 수 있습니다.
* **터치 패드** 터치 패드를 아래쪽 클릭 하 여 작업을 커밋하지 동작 컨트롤러의 터치 패드의 두 가지 크기를 화면에 따라 작업을 조정할 수 있습니다. 터치 패드를 누른된 상태로, 실행된 상태 및 정규화 된 XY 좌표를 제공합니다. X 및 Y-1에서 1 사이에서 center 사용 하 여 순환 터치 패드의 범위에 걸쳐 (0, 0). X에 대 한-1은 왼쪽 및 1 오른쪽에 표시 됩니다. Y에 대 한 아래에는-1 이며 1 맨 위에 있습니다.
* **엄지 스틱** 스틱을 아래로 클릭 하 여 작업을 커밋하지 동작 컨트롤러의 엄지 스틱 순환 해당 범위 내에서 이동 하 여 두 개의 차원에서 동작을 조정할 수 있습니다. 또한 스틱 누름된 상태를 제공 하 고 XY 좌표를 정규화 합니다. X 및 Y-1에서 1 사이에서 center 사용 하 여 순환 터치 패드의 범위에 걸쳐 (0, 0). X에 대 한-1은 왼쪽 및 1 오른쪽에 표시 됩니다. Y에 대 한 아래에는-1 이며 1 맨 위에 있습니다.
* **홈** 특수 시스템 작업이 다시 시작 메뉴로 이동 하는 데 사용 되는 합니다. 키보드 또는 Xbox 컨트롤러에 Xbox 단추에서 Windows 키를 눌러 비슷합니다. 동작 컨트롤러에서 Windows 단추를 눌러 홈 이동할 수 있습니다. 참고로 돌아갈 수 있습니다 항상 시작 "Hey Cortana, Go Home" 라는 가정에서. 앱으로 시스템에 의해 처리 되므로 이러한 홈 작업에 특히 대응할 수 없습니다.

## <a name="composite-gestures-high-level-spatial-input"></a>복합 제스처의 경우: 고급 공간 입력

둘 다 [제스처 전달](gestures.md) 대략적인의 공통 집합을 검색 하는 시간에 따른 동작 컨트롤러를 추적할 수 있습니다 하 고  **[복합 제스처](gestures.md#composite-gestures)** 합니다. 이렇게 하면 높은 수준의 검색할 앱 **탭**, **보유할**를 **조작** 및 **탐색** 제스처를 사용 하 여 사용자가 종료 여부를 실습 또는 컨트롤러입니다.

## <a name="rendering-the-motion-controller-model"></a>렌더링 동작 컨트롤러 모델

**3D 컨트롤러 모델** Windows를 사용할 수 있도록 앱의 각 동작 컨트롤러 렌더링 가능한 모델을 시스템에서 현재 활성화 합니다. 앱 동적으로 로드 하 고 런타임 시 이러한 시스템 제공 컨트롤러 모델을 표현 함으로써 앱이 이후 버전과 호환 나중에 컨트롤러 디자인을 확인할 수 있습니다.

이러한 렌더링 가능한 모델 모두 렌더링 되어야에 **그립 포즈** 컨트롤러의 모델의 원점으로 맞춥니다 실제 세계의이 지점입니다. 컨트롤러 모델을 렌더링 하는 경우 하고자 할 수 있습니다 다음 raycast에서 장면에는 **포인터 포즈**는 사용자가 자연스럽 게 기대를 가리키도록 해당 컨트롤러의 물리적 디자인을 지정 된 광선을 나타냅니다.

Unity에서 동적으로 컨트롤러 모델을 로드 하는 방법에 대 한 자세한 내용은 참조는 [Unity의 동작 컨트롤러 모델을 렌더링](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) 섹션입니다.

**2D 컨트롤러 라인 아트** 개발자도 플랫 "자습서" 또는 "방법"에서 2D 줄 아트 표현의 동작 컨트롤러를 사용 하려는 앱에 컨트롤러 팁, 명령을 앱에 컨트롤러 모델 자체를 연결 하는 것이 좋지만, UI입니다. 개발자를 위해,.png 동작 컨트롤러 줄 아트 파일을 모두 흑백 아래에서 사용할 수 있습니다 (마우스 오른쪽 단추 클릭 저장)를 만들었습니다.

![미리 보기 동작 컨트롤러 라인 아트](images/motioncontrollers-black-preview-300px.png)

 [고해상도 동작 컨트롤러에서 최신 줄 ' ' 흰색 ' '](images/motioncontrollers-white.png)
 
 [고해상도 동작 컨트롤러에서 최신 줄 ' ' black ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>FAQ

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>여러 Pc에 컨트롤러를 동작 쌍 있나요?

동작 컨트롤러 단일 PC를 사용 하 여 연결을 지원 합니다. 지침에 따르세요 [controller 설치 동작](motion-controllers.md#setup) 컨트롤러에 연결 합니다.

### <a name="how-do-i-update-motion-controller-firmware"></a>동작 컨트롤러 펌웨어를 업데이트 하려면 어떻게 해야 하나요?

동작 컨트롤러 펌웨어 헤드셋 드라이버의 일부 이며 자동 업데이트 됩니다 연결에 필요한 경우. 펌웨어 업데이트에는 일반적으로 Bluetooth 라디오 및 링크 품질에 따라 1 ~ 2 분 걸립니다. 드문 경우에서 컨트롤러 펌웨어 업데이트에는 최대 10 분, Bluetooth 연결 상태가 좋지 않은 또는 라디오 간섭 나타낼 수 있는 걸릴 수 있습니다. 참조 하세요 [Bluetooth 전문가 가이드의 모범 사례](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 연결 문제를 해결 합니다. 펌웨어 업데이트를 컨트롤러는 다시 부팅 후 호스트 PC (추적용 밝은 이동 Led 알 수 있습니다)에 다시 연결 합니다. 펌웨어 업데이트를 중단 되는 경우 (예를 들어 컨트롤러는 전원 손실) 컨트롤러는 전원이 켜져 다음에 다시 시도 됩니다.

### <a name="how-i-can-check-battery-level"></a>어떻게 배터리 수준을 확인할 수 있습니까?

에 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md), 가상 모델의 뒷면에 배터리 수준에 해당 참조를 컨트롤러를 설정할 수 있습니다. 실제 배터리 수준 표시기에 없는 경우

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>헤드셋 없이 이러한 컨트롤러를 사용할 수 있습니까? 조이스틱/트리거/etc 입력에 대 한?

유니버설 Windows 응용 프로그램에 대 한 없습니다

## <a name="troubleshooting"></a>문제 해결

참조 [컨트롤러 문제 해결 동작](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) 전문가 가이드에서.

## <a name="filing-motion-controller-feedbackbugs"></a>동작 컨트롤러 피드백/버그 신고

[의견을 보내 주십시오](give-us-feedback.md) 피드백 허브에서 "혼합된 현실 입력을->" 범주를 사용 합니다.

## <a name="see-also"></a>참조
* [제스처와 Unity의 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md)
* [응시, 제스처 및 DirectX에서 동작 컨트롤러](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [제스처](gestures.md)
* [MR 입력 213: 컨트롤러 동작](mixed-reality-213.md)
* [전문가 가이드: 홈 사용자 Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [전문가 가이드: Windows Mixed Reality에서 게임 및 앱 사용](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [추적 내부 스케일 아웃의 작동 원리](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
