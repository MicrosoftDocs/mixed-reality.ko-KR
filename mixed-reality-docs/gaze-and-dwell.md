---
title: 헤드 게이즈 및 유지
description: Head 게이즈 및 지속 입력된 모델 개요
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실을 응시, 유지, 상호 작용 디자인
ms.openlocfilehash: 9f9fa89d7730e21e89bd24ce3b483d129c8a16db
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730775"
---
# <a name="head-gaze-and-dwell"></a>헤드 게이즈 및 유지

실습, 도구 및 파트를 사용 하 여 꽉 찼을 때 tedious 어렵거나 제스처 수 있습니다. 음성 명령, 제스처 같은 과도 하 게 큰 조건 예를 들어 특정 상황에서 신뢰할 수 있는 취소할 수 있습니다. 또한 컨트롤 컴퓨터에 음성을 사용 하 여 전체적으로 일반적인 아니지만 확실히 steam를 확보 됩니다! 헤드 게이즈 및 지속 heads-up 및 HoloLens에 핸 즈 프리 작업에 대 한 가장 친숙 하 고 마스터 간편한 메커니즘을 제공 합니다. 또한 헤드 게이즈 이며 지속 100% 신뢰할 수 있는 운영 환경에서 노이즈가 간섭 또는 대기 제약 조건과 관계입니다.

## <a name="scenarios"></a>시나리오

헤드 게이즈 및 지속 사람의 손에 다른 작업을 사용 하 고 음성 되지 100% 안정적이 지 않거나 환경 또는 소셜 제약 조건으로 인해 있고 그 시나리오에서 훨씬 더 뛰어납니다. 좋은 예는 HoloLens 자동차 엔진을 복구 하는 동안 참조 정보를 오버레이 하는 사람입니다. With tools 또는 엔진 구획에 의존 하는 것 처럼 해당 본문을 지 원하는 업무는 있습니다. 차고 공간은 banging 나 도구, 음성 명령을 어렵게의 웅웅거리는 신호음 상수를 사용 하 여 클라우드,입니다. 헤드 게이즈 및 지속 방해 하지 않고 해당 참조 자료를 자신 있게 이동할 HoloLens에 있는 사용자가 워크플로 허용 합니다. 

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>입력된 모델</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>헤드 게이즈 및 유지</td>
        <td>권장 ✔️</td>
        <td>권장 ✔️</td>
        <td>권장 ✔️</td>
    </tr>
</table>

## <a name="goals"></a>목표

음성 사용 하지 않고 완전히 핸 즈 프리 상호 작용 하는 메커니즘을 제공 합니다.

## <a name="design-principles"></a>디자인 원칙

1. "을 무기로 Gaze" 방지

    헤드 게이즈 및 지속 직관적으로 시각적 피드백 하는데 너무 많은 피드백 간주를 유도할 수 있습니다. 피드백을 어떤는 대상으로 하 하지 자동 선택 되지만 의도 대해 알고 사용자 데 도움이 됩니다. 텍스트, 아이콘 및 레이블을 읽으려면 person 장소 absorb 선택 하기 전에 정보를 제공 하는 추가 고려 사항이 필요 합니다.
    
2. 금발 속도 검색 합니다.
    
    지속 상호 작용 탐색에 미치는 영향에 따라 다른 타이머를 가질 수 있습니다-자주 사용 되는 함수 일반적으로에서 이익을 채우기 시간을 단축 동안 더 파생적 함수 채우기 시간이 더에서 이점을 얻을 수 있습니다. 이러한 타이머를 표시할 채우기 효과 사용 하는 경우 채우기 색의 애니메이션 곡선 느낌 채우기 시간 단축을 영향을 주게 수 있습니다. 고려 사항 fast/중간/느린 사용자 결정을 사용 하도록 설정 하려면 취해야 속도 재정의 입력 합니다.
    
3. Yo-yo 효과를 no-no의 예를 들어합니다

    Yo-yo 효과 헤드 이동 콘텐츠 및 head 게이즈 지속 컨트롤 배치 하면 지속적으로 반복 해 서 위쪽 / 아래쪽을 확인 하 게 하는 경우 나타날 수 있습니다 하는 불편 패턴입니다. 예를 들어 아래쪽 헤드 게이즈 및 지속 단추는 목록 탐색에 자세히 설명 하지 조회 결과 확인 유지 등을 다운의-확인 루프를 유도 합니다. 이 결과 패턴 편리 하 게 되었으며 탐색 컨트롤 작은 백-및-명시 해야 하는 중앙된 위치에 배치 하 여 하지 않아야 합니다. 해당 효과 기준으로 지속 단추의 배치가 편안 하 게 중요 합니다.

## <a name="ux-guidelines-and-best-practices"></a>UX 지침 및 모범 사례

### <a name="target-sizes"></a>대상 크기
  쉽게 액세스할 수 있도록, 헤드 게이즈 및 만큼 넓은 공간 이어야 comforatably 대상으로 해야 하는 대상에 자세히 설명 하지 누른 1의 헤드 stabily 대상에서 정해진된 시간에 대 한 합니다. 가장 편안한 경험을 얻는 2도의 최소 대상 크기를 사용 하는 것이 좋습니다. 

### <a name="visual-feedback"></a>시각적 피드백

방사형 채우기 지속 타이머를 나타내는 데 사용 하는 경우에 단추의 센터에서 시작 합니다. 일관 된 응답 다른 단추는 다른 모든 방향으로 보다 덜 혼동 됩니다. 

  * 이 규칙은 방향 상호 작용 (예를 들어, nav 위쪽/아래쪽/왼쪽/오른쪽, 등)에 있지만 손상 수 있습니다. 예를 들어, Microsoft Dynamics 365 가이드는 다음/이전에는 예외를 발생 중인 오른쪽 채우기 남습니다.
  * 해제 단추를 설정/해제 하는 등의 시나리오에 대 한 외부에서 방사형 채우기를 반전 하는 것이 좋습니다. 단추를 하나 누르는의 역 느낌은 유지 하기 위해 유용한 visual 패턴. 

### <a name="progressive-disclosure"></a>점진적 공개

점진적 표시만 상호 작용의 각 단계에서 관련이 최대한 자세하게 보여 주는 것을 의미 합니다. 유지에 대 한 즉, 지속 대상 (예: 목록 컨트롤)에서 강조 표시에 표시 됩니다.

 ### <a name="oversized-targets"></a>너무 큰된 대상
지속 지역 Microsoft Dynamics 365 가이드에서 뒤로 단추 사용을 쉽게 수행할 수 있도록 비활성 아이콘 보다 클 수 있습니다.

### <a name="prevent-flickering-with-delayed-feedback"></a>지연된 피드백을 사용 하 여 깜박임을 방지합니다
누군가가 지속 대상 위로 이동할 때 깜박임을 방지 하려면 시각적 피드백을 시작 하기 전에 잠시를 사용 합니다.
* 응용 프로그램 느낌 사후 대응 하므로 자주를 사용 하 여 단추 inteacted, 짧은 지연 시간을 유지 합니다.
* Infrequenctly 상호 작용할 되는 단추에 대 한 지연 시간이 길어지는 twitchy 생각 하는 인터페이스를 방지 하려면 approprate 수 있습니다.

## <a name="ui-patterns"></a>UI 패턴

### <a name="high-frequency-buttons"></a>높은 빈도 단추
![Microsoft Dynamics 365 가이드 다음 단추](images/GuideNextButton.png "Microsoft Dynamics 365 가이드 다음 단추") 빈도가 높은 단추는 응용 프로그램을 통해 일반적으로 사용 되는 단추입니다. 이러한 좋은 예는 Microsoft Dynamics 365 가이드의 다음 및 뒤로 단추가 있습니다.

* 높은 빈도 단추 해야 하는 중...
  * 큰 단추를 더 쉬워질 헤드 게이즈를 사용 하 여 적중
  * 눈 높이 인체 범주인 방지를 거의 유지 합니다.

### <a name="low-frequency-buttons"></a>낮은 빈도 단추
낮은 빈도 단추는 됩니다 하지 상호 작용으로 정기적으로 응용 프로그램에 걸쳐 있는 단추가 있습니다. 좋은 예로 설정 메뉴에 액세스 하는 단추 또는 모든 작업의 선택을 취소 하는 단추 수 있습니다.

* 실수로 인 한 활성화 하지 않으려면 자주 헤드 게이즈 경로 모니터로 이러한 단추를 유지 하려고 합니다. 

### <a name="confirmations"></a>확인
![Microsoft Dynamics 365 가이드 확인 대화 상자가](images/GuidesConfirmation.png "Microsoft Dynamics 365 가이드 확인 대화 상자")

액션에 비용 청구, 작업, 삭제 또는 긴 프로세스를 시작와 같은 중요 한 영향, 사용자가 단추를 선택 하려는 것인지 유용 합니다. 헤드 게이즈 및 유지에 대 한 Ui 있습니다은 몇 가지 패턴과 확인 대화 상자에 대 한 고려 사항:

  * 주 단추 강조 표시를 선택 영역이 보여 줍니다.
  * 강조 표시 선택 영역이으로 동시 지속 대상을 표시 합니다.
  * 보조 단추에 대 한 헤드 게이즈에서 지속 대상을 표시 합니다.
        
### <a name="toggle-buttons"></a>설정/해제 단추
설정/해제 단추에는 제대로 작동 하려면 몇 가지 미묘한 논리가 필요 합니다. 개인 것 토글 단추와 근무 중인 직원에 주의 단추를 종료 하 고 유지 하는 논리를 다시 시작으로 돌아 오세요에 필요 합니다. 설정 단추는 비활성 상태와 일반 활성 반드시 합니다. 

### <a name="list-views"></a>목록 보기
![Microsoft Dynamics 365 가이드 확인 대화 상자가](images/GuidesListView.png "Microsoft Dynamics 365 가이드 확인 대화 상자") 목록 뷰 게이즈 헤드에 대 한 특정 챌린지 있고 입력을 유지 합니다. 사람들이 tiptoe 지속 대상 주위에 있는 같은 생각 하지 않고 콘텐츠를 검색할 수 해야 합니다. 

목록 뷰를 디자인 하기 위한 몇 가지 팁:
* 헤드 gazed 헤드 게이즈가 특정 지속 대상에 없으면 유지를 시작 하지 않으면 경우 강조 표시 하 여 전체 행을 있어야 합니다.
* visual 노이즈를 줄이기 위해 행이 강조 표시 하는 경우에 유지 대상을 표시 합니다.
* 명확 하 고 지속 대상의 위치를 사용 하 여 일관 된 수입니다.
* 모든 대상의 반복적인 UI를 방지 하려면 한 번에 대해 자세히 설명 하지 표시 안 함
* 다시 동일한 패턴을 UX 경험을 설정 하는 가능한 한 자주 사용
 
 ## <a name="see-also"></a>참조
* [직접 조작](direct-manipulation.md)
* [지점 및 커밋](point-and-commit.md)
* [상호 작용 기본 사항](interaction-fundamentals.md)
* [헤드 게이즈 및 커밋](gaze-and-commit.md)
* [응시 및 음성](voice-design.md)
