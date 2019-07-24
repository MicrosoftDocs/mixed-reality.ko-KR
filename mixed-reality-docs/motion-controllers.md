---
title: 동작 컨트롤러
description: 혼합 현실 동작 컨트롤러에 대 한 세부 정보입니다.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 컨트롤러, 동작 컨트롤러
ms.openlocfilehash: fc6b0dcf7f338224af9ea9bc59e07187c33adda2
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024557"
---
# <a name="motion-controllers"></a>동작 컨트롤러

동작 컨트롤러는 사용자가 혼합 현실에서 작업을 수행할 수 있게 해 주는 [하드웨어 액세서리](hardware-accessories.md) 입니다. [제스처](gestures.md) 를 통한 동작 컨트롤러의 이점은 컨트롤러의 공간이 정확 하 여 디지털 개체와의 세분화 된 상호 작용을 가능 하 게 하는 것입니다. Windows Mixed Reality 모던 헤드셋의 경우, 동작 컨트롤러는 사용자가 전 세계에서 작업을 수행 하는 기본 방법입니다.

![Windows Mixed Reality 동작 컨트롤러](images/winmr-ck-1080x1080-350px.jpg)


## <a name="device-support"></a>장치 지원

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>기능</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
</tr>
<tr>
     <td>동작 컨트롤러</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>하드웨어 세부 정보

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Windows Mixed Reality 동작 컨트롤러는 몰입 형 헤드셋의 센서를 사용 하 여 뷰 필드의 이동에 대 한 정확 하 고 응답성이 뛰어난 추적을 제공 합니다. 즉, 공간의 벽에 하드웨어를 설치할 필요가 없습니다. 이러한 동작 컨트롤러는 Windows Mixed Reality 모던 헤드셋과 동일한 설정 및 이식성을 제공 합니다. 이 명절을 통해 이러한 컨트롤러를 출시 하 고 판매할 수 있습니다.

![컨트롤러에 대 한 자세한 내용을 확인 하세요.](images/controllerimage-750px.png)<br>
*컨트롤러에 대 한 자세한 내용을 확인 하세요.*

**요소**
* 광학 추적
* 트리거되도록
* 잡기 단추
* 사용해
* 터치 패드

## <a name="setup"></a>설치 프로그램

### <a name="before-you-begin"></a>시작하기 전 주의 사항

**다음이 필요 합니다.**
* 두 개의 동작 컨트롤러 집합입니다.
* AA 배터리가 4 개 있습니다.
* Bluetooth 4.0을 지 원하는 PC입니다.

**Windows, Unity 및 드라이버 업데이트 확인**
* 혼합 현실 개발을 위해 기본 버전의 Windows, Unity 등의 [도구를 설치](install-the-tools.md) 하세요.
* 최신 [헤드셋 및 동작 컨트롤러 드라이버가](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)있는지 확인 합니다.

### <a name="pairing-controllers"></a>페어링 컨트롤러

다른 Bluetooth 장치와 마찬가지로 Windows 설정을 사용 하 여 호스트 PC와 동작 컨트롤러를 연결할 수 있습니다.

1. 컨트롤러 후면에 2 개 AA 배터리를 삽입 합니다. 지금은 배터리 덮개를 종료 합니다.
2. 기본 제공 Bluetooth 라디오 대신 외부 USB Bluetooth 어댑터를 사용 하는 경우 계속 하기 전에 [bluetooth 모범 사례](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 를 검토 하세요. 기본 제공 라디오를 사용 하는 데스크톱 구성의 경우 안테나가 연결 되어 있는지 확인 하세요.
3. **Windows 설정** -> **장치** ->  열기 bluetooth 또는 기타 장치 bluetooth를 추가 하 고 "동작 컨트롤러 – 오른쪽" 및 "동작 컨트롤러-왼쪽"의 이전 인스턴스를 모두 제거 합니다. ->  목록의 맨 아래에 있는 기타 장치 범주도 선택 합니다.
4. **Bluetooth 또는 다른 장치 추가** 를 선택 하 고 bluetooth 장치 검색을 시작 합니다.
5. 컨트롤러의 Windows 단추를 길게 눌러 컨트롤러를 켜고 buzzes 면 해제 합니다.
6. Led가 펄스를 시작할 때까지 페어링 단추 (배터리 구획의 탭)를 길게 누릅니다.
7. 목록의 맨 아래에 "동작 컨트롤러-왼쪽" 또는 "동작 컨트롤러 오른쪽"이 표시 될 때까지 기다립니다. 페어링 하려면 선택 합니다. 컨트롤러는 연결 될 때 한 번 진동 됩니다.

   ![여러 인스턴스가 목록의 아래쪽에 표시 되는 항목을 선택 하는 경우 연결할 동작 컨트롤러를 선택 합니다.](images/450px-bluetooth-add-a-device-300px.png)<br>
   *"동작 컨트롤러"를 선택 하 여 페어링 합니다. 인스턴스가 여러 개 있는 경우 목록의 맨 아래에서 하나를 선택 합니다.*
   
8. 컨트롤러가 Bluetooth 설정의 **"마우스, 키보드, & 펜" 범주** 아래에 **연결**됨으로 표시 됩니다. 이 시점에서 펌웨어 업데이트를 가져올 수 있습니다. [다음 섹션](motion-controllers.md#updating-controller-firmware)을 참조 하세요.
9. 배터리 덮개를 다시 연결 합니다.
10. 두 번째 컨트롤러에 대해 1-9 단계를 반복 합니다.

두 컨트롤러를 성공적으로 연결한 후 설정은 **"마우스, 키보드, & 펜" 범주** 아래에 다음과 같이 표시 됩니다. 

   ![연결 된 동작 컨트롤러](images/450px-motion-controller-connected-300px.png)<br>
   *연결 된 동작 컨트롤러*

페어링 후 컨트롤러가 꺼져 있으면 해당 상태는 페어링된 것으로 표시 됩니다. 컨트롤러가 "기타 장치"에서 영구적으로 유지 되는 경우 범주 페어링은 부분적 으로만 완료 되어 컨트롤러 기능을 얻기 위해 다시 수행 해야 합니다.

### <a name="updating-controller-firmware"></a>컨트롤러 펌웨어 업데이트

* 모던 헤드셋이 PC에 연결 되어 있고 새 컨트롤러 펌웨어를 사용할 수 있는 경우 다음에 설정 될 때 자동으로 펌웨어가 이동 컨트롤러에 푸시됩니다. 컨트롤러 펌웨어 업데이트는 원형 동작에서 비추는 LED 사분면 패턴으로 표시 되며 1-2 분이 소요 됩니다.
* 펌웨어 업데이트가 완료 되 면 컨트롤러를 다시 부팅 하 고 다시 연결 합니다. 이제 두 컨트롤러를 연결 해야 합니다. 
    
    ![연결 된 컨트롤러](images/cyk-connected-300px.jpg)<br>
    *Bluetooth 설정에서 연결 된 컨트롤러*

* 컨트롤러가 제대로 작동 하는지 확인 합니다.
    1. **혼합 현실 포털** 을 시작 하 고 혼합 현실 홈을 입력 합니다.
    2. 컨트롤러를 이동 하 고 추적, 테스트 단추를 확인 하 고 [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 작동 하는지 확인 합니다. 그렇지 않으면 [동작 컨트롤러 문제 해결](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)을 확인 하세요.

## <a name="gazing-and-pointing"></a>Gazing 및 가리키기

Windows Mixed Reality는 상호 작용, **응시, 커밋** , **지점 및 커밋**에 대 한 두 가지 주요 모델을 지원 합니다.
* 사용자는 **응시 및 커밋을**사용 하 여 사용자가 자신의 [응시](gaze.md) 를 사용 하 여 개체를 대상으로 지정한 다음 핸드 공기 탭, 게임 패드, clicker 또는 음성으로 개체를 선택 합니다.
* **지점 및 커밋을**사용 하 여 사용자는 대상 개체에서 포인팅 가능 동작 컨트롤러를 목표로 한 다음 컨트롤러의 트리거를 사용 하 여 개체를 선택할 수 있습니다.

동작 컨트롤러를 가리키는 응용 프로그램은 가능한 경우에도 사용자가 사용 하는 입력 장치에 대 한 선택 항목을 제공 하는 응시 기반 상호 작용을 가능 하 게 합니다.

### <a name="managing-recoil-when-pointing"></a>가리킬 때 recoil 관리

동작 컨트롤러를 사용 하 여 지점 및 커밋을 수행 하는 경우 사용자는 컨트롤러를 사용 하 여 대상으로 지정한 다음 해당 트리거를 당겨 작업을 수행 합니다. 트리거 vigorously를 끌어오는 사용자는 의도 한 대로 트리거 끌어오기의 끝에서 컨트롤러의 상위 수준으로 끝날 수 있습니다.

사용자가 트리거를 끌어올 때 발생할 수 있는 이러한 recoil를 관리 하기 위해 트리거의 아날로그 축 값이 0.0 이상으로 증가 하는 경우 앱에서 대상 광선을 맞출 수 있습니다. 그런 다음 짧은 시간 내에 최종 키가 발생 하는 한, 나중에 트리거 값이 1.0에 도달 하면 몇 개 프레임을 대상으로 하는 작업을 수행할 수 있습니다. 상위 수준 [복합 탭 제스처](gestures.md#composite-gestures)를 사용 하는 경우 Windows에서이 대상 지정 광선 캡처 및 시간 초과를 관리 합니다.

## <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 및 포인팅 포즈

Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 하며, 각 컨트롤러의 디자인이 사용자의 손 위치와 앱에서 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다. controller.

이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스, **그립 포즈** 및 **포인터 포즈**에 대해 조사할 수 있는 두 가지 종류의 포즈를 확인할 수 있습니다.

### <a name="grip-pose"></a>그립 포즈

**그립 포즈** 는 HoloLens에서 감지한 손바닥의 위치 또는 동작 컨트롤러를 보유 하는 야자나무를 나타냅니다.

몰입 형 헤드셋에서 그립 포즈는 사용자 **의 손을** 만들거나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다. 동작 컨트롤러에 대해 Windows에서 제공 하는 **렌더링할 모델** 은 동작 컨트롤러를 시각화할 때에도 그립 포즈를 사용 합니다.

그립 포즈는 구체적으로 다음과 같이 정의 됩니다.
* **그립 위치**: 중심 컨트롤러를 자연스럽 게 사용할 때 왼쪽 또는 오른쪽으로 조정 하 여 그립 내에서 위치를 가운데에 맞춥니다. Windows Mixed Reality 동작 컨트롤러에서이 위치는 일반적으로 보통 클릭 단추와 맞춥니다.
* **그립 방향의 오른쪽 축입니다**. 손을 완전히 열어 평평한 5 손가락 포즈를 형성 하는 경우 야자나무 (왼쪽 야자나무에서 전방, 오른쪽 팜)에 있는 광선
* **그립 방향의 앞 축**: 컨트롤러를 보유 하 고 있는 것 처럼 부분적으로 닫는 경우 엄지 단추가 아닌 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.
* **그립 방향의 위쪽 축입니다**. 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.

### <a name="pointer-pose"></a>포인터 포즈

**포인터 포즈** 는 컨트롤러의 팁을 나타냅니다.

시스템 제공 포인터 포즈는 **컨트롤러 모델 자체를 렌더링**하는 경우 raycast에 가장 잘 사용 됩니다. 컨트롤러 대신 다른 가상 개체 (예: 가상 사용자)를 렌더링 하는 경우 앱 정의 된 포 모델의 배럴을 따라 이동 하는 광선과 같이 해당 가상 개체에 가장 자연 스러운 광선을 가리켜야 합니다. 사용자는 가상 개체를 볼 수 있고 실제 컨트롤러는 볼 수 없으므로 가상 개체를 가리키면 앱을 사용 하는 것이 더 자연스럽 게 될 수 있습니다.

## <a name="controller-tracking-state"></a>컨트롤러 추적 상태

헤드셋 처럼 Windows Mixed Reality 동작 컨트롤러를 사용 하려면 외부 추적 센서를 설정 하지 않아도 됩니다. 대신, 컨트롤러는 헤드셋 자체의 센서에 의해 추적 됩니다.

사용자가 컨트롤러를 헤드셋의 뷰 필드에서 밖으로 이동 하는 경우 대부분의 경우 Windows는 컨트롤러 위치를 계속 유추 하 고 앱에 제공 합니다. 컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다.

이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다. 컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>명시적 추적 상태에 대 한 추론

추적 상태에 따라 위치를 다르게 처리 하려는 앱은 더 나아가 컨트롤러의 상태에 대 한 속성 (예: SourceLossRisk 및 PositionAccuracy)을 검사할 수 있습니다.

<table>
<tr>
<th> 상태 추적 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>높은 정확도</b> </td><td style="background-color: green; color: white"> &lt;1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>높은 정확도 (손실 위험)</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>대략적인 정확도</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: orange"> 대략 일치 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>위치 없음</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: orange"> 대략 일치 </td><td style="background-color: orange"> false</td>
</tr>
</table>



이러한 동작 컨트롤러 추적 상태는 다음과 같이 정의 됩니다.
* **높은 정확도:** 동작 컨트롤러는 헤드셋의 보기 필드 내에 있지만 일반적으로 시각적 추적에 따라 정확도가 높은 위치를 제공 합니다. 일시적으로 보기의 필드를 벗어나거나 헤드셋 센서에서 일시적으로 가려진 이동 컨트롤러 (예: 사용자)는 컨트롤러의 관성 추적을 기반으로 짧은 시간 동안 계속 해 서 정확도가 높은 포즈를 반환 합니다. 자체.
* **높은 정확도 (손실 위험):** 사용자가 이동 컨트롤러를 헤드셋의 보기 필드 가장자리를 지나서 이동할 때 헤드셋은 곧 컨트롤러의 위치를 시각적으로 추적할 수 없습니다. 앱은 **SourceLossRisk** reach 1.0을 확인 하 여 컨트롤러가이 FOV 경계에 도달한 경우를 인식 합니다. 이 시점에서 앱은 매우 높은 품질의 동작을 안정적으로 스트리밍하는 데 필요한 컨트롤러 제스처를 일시 중지 하도록 선택할 수 있습니다.
* **대략적인 정확도:** 컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다. 이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다. 컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다. 입력 요구 사항이 많은 앱은 사용자에 게 오프 스크린 대상에 대 한 hitbox을 제공 하는 등의 방법으로 **positionaccuracy** 속성을 검사 하 여 정확도가 **높은** 정확도 **부터 정확도까지** 이러한 삭제를 합리적으로 선택할 수 있습니다. 이 시간 동안.
* **위치 없음:** 컨트롤러는 오랜 시간 동안 정확한 정확도로 작동할 수 있지만 때때로 본문 잠금 위치가 중요 하지 않은 것을 시스템에서 인식 하는 경우도 있습니다. 예를 들어 방금 설정 된 컨트롤러가 시각적으로 관찰 되지 않았거나 사용자가 다른 사용자가 선택 하는 컨트롤러를 배치할 수 있습니다. 이러한 시간에 시스템은 앱에 어떤 위치도 제공 하지 않으며 **TryGetPosition** 는 false를 반환 합니다.

## <a name="interactions-low-level-spatial-input"></a>확인할 하위 수준 공간 입력

손으로 이동 하 고 이동 하는 컨트롤러의 핵심 상호 작용은 **선택**, **메뉴** **, 방법**, **터치 패드**, **엄지 스틱**및 **홈**입니다.
* Press를 선택 하 고 릴리스를 차례로 선택 하 여 홀로그램을 활성화 하는 기본 상호 작용을 **선택** 합니다. 동작 컨트롤러의 경우 컨트롤러의 트리거를 사용 하 여 Select 누르기를 수행 합니다. Select를 수행 하는 다른 방법은 [음성 명령](voice-input.md) "Select"를 말하는 것입니다. 모든 앱 내에서 동일한 select 상호 작용을 사용할 수 있습니다. Select를 마우스 클릭에 해당 하는 것으로 생각 하 고, 한 번 알아보고 모든 앱에 적용 하는 범용 작업을 선택 합니다.
* **메뉴** 는 상황에 맞는 메뉴를 끌어오거나 다른 보조 작업을 수행 하는 데 사용 되는 개체의 동작에 대 한 보조 상호 작용입니다. 동작 컨트롤러를 사용 하면 컨트롤러의 *메뉴* 단추를 사용 하 여 메뉴 작업을 수행할 수 있습니다. (즉, 햄버거 "메뉴" 아이콘이 있는 단추)
* 사용자가 직접 개체에 대 한 작업을 수행 하 여 조작 하는 방법을 **이해** 하는 것이 좋습니다. 동작 컨트롤러를 사용 하 여 펀치를 긴밀 하 게 배치 하 여 동작을 수행할 수 있습니다. 동작 컨트롤러는 잡기 단추, 팜 트리거 또는 기타 센서를 사용 하 여 감지기를 감지할 수 있습니다.
* **터치 패드** 를 통해 사용자는 동작 컨트롤러의 터치 패드 화면에 있는 두 차원의 작업을 조정 하 여 터치 패드에서 다운을 클릭 하 여 작업을 커밋할 수 있습니다. 터치 패드는 누름 상태, 작업 상태 및 정규화 된 XY 좌표를 제공 합니다. 원형 터치 패드 범위에서 X 및 Y의 범위는-1에서 1 사이 이며 중심은 (0, 0)입니다. X의 경우-1은 왼쪽에 있고 1은 오른쪽에 있습니다. Y의 경우-1은 아래쪽에 있고 1은 맨 위에 있습니다.
* **엄지 스틱** 을 사용 하면 동작 컨트롤러의 엄지 스틱을 원형 범위 내에서 이동 하 고 엄지 스틱에서 아래로 클릭 하 여 작업을 커밋하는 방식으로 두 차원의 작업을 조정할 수 있습니다. 또한 Thumbsticks는 눌러진 상태와 정규화 된 XY 좌표를 제공 합니다. 원형 터치 패드 범위에서 X 및 Y의 범위는-1에서 1 사이 이며 중심은 (0, 0)입니다. X의 경우-1은 왼쪽에 있고 1은 오른쪽에 있습니다. Y의 경우-1은 아래쪽에 있고 1은 맨 위에 있습니다.
* **Home** 은 시작 메뉴로 다시 이동 하는 데 사용 되는 특수 시스템 작업입니다. 키보드에서 Windows 키를 누르거나 Xbox 컨트롤러의 Xbox 단추를 누르는 것과 비슷합니다. 동작 컨트롤러에서 Windows 단추를 눌러 홈으로 이동할 수 있습니다. "안녕하세요 Cortana, Go Home"을 참조 하 여 언제 든 지 시작할 수 있습니다. 앱은 시스템에 의해 처리 되기 때문에 특히 홈 작업에 대응할 수 없습니다.

## <a name="composite-gestures-high-level-spatial-input"></a>복합 제스처: 상위 수준 공간 입력

[핸드 제스처](gestures.md) 와 동작 컨트롤러를 시간에 따라 추적 하 여 상위 수준 **[복합 제스처](gestures.md#composite-gestures)** 의 공통 집합을 검색할 수 있습니다. 이를 통해 앱은 사용자가 직접 또는 컨트롤러를 사용 하 든 관계 없이 상위 수준 **탭**, **보유**, **조작** 및 **탐색** 제스처를 검색할 수 있습니다.

## <a name="rendering-the-motion-controller-model"></a>동작 컨트롤러 모델 렌더링

**3d 컨트롤러 모델** Windows에서는 현재 시스템에서 활성 상태인 각 동작 컨트롤러의 렌더링할 모델을 앱에서 사용할 수 있습니다. 앱이 시스템 제공 컨트롤러 모델을 런타임에 동적으로 로드 하 고이를 표시 하는 방식으로 앱이 이후 컨트롤러 디자인과 호환 되는지 확인할 수 있습니다.

이러한 렌더링할 모델은 모델의 원점이 실제 세계의이 지점에 맞춰져 있으므로 컨트롤러의 **그립 포즈** 에서 렌더링 되어야 합니다. 컨트롤러 모델을 렌더링 하는 경우에는 해당 컨트롤러의 물리적 디자인을 고려 하 여 사용자가 의도적으로 가리키는 광선을 나타내는 **포인터 포즈**에서 장면으로의 장면을 raycast 수 있습니다.

Unity에서 동적으로 컨트롤러 모델을 로드 하는 방법에 대 한 자세한 내용은 [unity에서 동작 컨트롤러 모델 렌더링](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) 섹션을 참조 하세요.

**2d 컨트롤러 선 아트** 앱 내 컨트롤러 모델 자체에 앱 컨트롤러의 팁과 명령을 연결 하는 것이 좋지만 일부 개발자는 플랫 "자습서" 또는 "방법" UI에서 동작 컨트롤러의 2D 선 아트를 사용할 수 있습니다. 이러한 개발자에 게는 다음의 검은색과 흰색 모두에서 .png 동작 컨트롤러 라인 아트 파일을 사용할 수 있습니다 (저장 하려면 마우스 오른쪽 단추 클릭).

![동작 컨트롤러의 미리 보기 라인 아트](images/motioncontrollers-black-preview-300px.png)

 [' ' ' 흰색 ' ' '의 전체 해상도 동작 컨트롤러 라인 아트](images/motioncontrollers-white.png)
 
 [' ' ' Black ' ' '의 전체 해상도 동작 컨트롤러 라인 아트](images/motioncontrollers-black.png)

## <a name="faq"></a>FAQ

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>여러 Pc에 동작 컨트롤러를 페어링 할 수 있나요?

동작 컨트롤러는 단일 PC와의 페어링을 지원 합니다. 컨트롤러를 페어링 하려면 [동작 컨트롤러 설정](motion-controllers.md#setup) 에 대 한 지침을 따르세요.

### <a name="how-do-i-update-motion-controller-firmware"></a>동작 컨트롤러 펌웨어를 업데이트 어떻게 할까요??

동작 컨트롤러 펌웨어는 헤드셋 드라이버의 일부 이며 필요한 경우 연결 시 자동으로 업데이트 됩니다. 펌웨어 업데이트는 일반적으로 Bluetooth 송수신 장치 및 링크 품질에 따라 1-2 분이 소요 됩니다. 드문 경우 지만 컨트롤러 펌웨어 업데이트에는 최대 10 분이 걸릴 수 있으며,이로 인해 Bluetooth 연결 또는 라디오 간섭을 일으킬 수 있습니다. 연결 문제를 해결 하려면 [열성적인 가이드의 Bluetooth 모범 사례](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 를 참조 하세요. 펌웨어 업데이트 후 컨트롤러는 다시 부팅 되 고 호스트 PC에 다시 연결 됩니다. (Led가 추적을 위해 밝게 표시 될 수 있습니다.) 펌웨어 업데이트가 중단 된 경우 (예: 컨트롤러에 전원이 들어오지 않음) 다음에 컨트롤러 전원을 켤 때 다시 시도 됩니다.

### <a name="how-i-can-check-battery-level"></a>배터리 수준을 확인할 수 있는 방법은 무엇입니까?

[Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md)에서 컨트롤러를 사용 하 여 가상 모델의 뒷면에 있는 배터리 수준을 확인할 수 있습니다. 물리적 배터리 수준 표시기는 없습니다.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>헤드셋 없이 이러한 컨트롤러를 사용할 수 있나요? 조이스틱/트리거/등의 입력만 있으면 됩니다.

유니버설 Windows 응용 프로그램에는 적합 하지 않습니다.

## <a name="troubleshooting"></a>문제 해결

열성적인 가이드의 [동작 컨트롤러 문제 해결](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) 을 참조 하세요.

## <a name="filing-motion-controller-feedbackbugs"></a>동작 컨트롤러 피드백/버그 파일링

"혼합 현실-> 입력" 범주를 사용 하 여 피드백 허브에 [피드백을 제공](give-us-feedback.md) 합니다.

## <a name="see-also"></a>참조
* [Unity의 제스처 및 모션 컨트롤러](gestures-and-motion-controllers-in-unity.md)
* [DirectX의 헤드 및 모션 컨트롤러](hands-and-motion-controllers-in-directx.md)
* [제스처](gestures.md)
* [MR 입력 213: 모션 컨트롤러](mixed-reality-213.md)
* [열성적인 가이드: Windows Mixed Reality 홈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [열성적인 가이드: Windows Mixed Reality에서 게임 & 앱 사용](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [외부 추적 작동 방법](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
