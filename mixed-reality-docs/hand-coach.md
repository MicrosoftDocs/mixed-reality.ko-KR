---
title: 손 coach
description: 3D 바늘은 시스템에서 사용자가 도움을 받을 수 있도록 사용자의 손을 감지 하지 못하는 경우에 트리거됩니다.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 손 coach, 몰입 형 헤드셋, MRTK, 실습, 실습 지원
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345670"
---
# <a name="hand-coach"></a>손 coach
![예: 손 coach](images/HandCoach/MRTK_handCoach.jpg)<br>

핸드 coach는 시스템에서 사용자의 손을 감지 하지 못하는 경우 트리거되는 3D 모델링 된 손을 갖습니다. 이 구성 요소는 제스처를 학습 하지 않았을 때 사용자에 게 안내 하는 데 도움이 되는 "교육" 구성 요소로 구현 됩니다. 사용자가 지정 된 기간 동안 지정 된 제스처를 수행 하지 않은 경우에는 손으로 지연 됩니다. 손 coach는 단추를 누르거나 홀로그램을 선택 하는 데 사용할 수 있습니다.  

## <a name="hand-coach-provided"></a>핸드 coach 제공 됨

현재 상호 작용 모델은 스크롤, 먼 선택 및 가까운 탭과 같은 다양 한 제스처 컨트롤을 나타냅니다. 다음은<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> Mrtk</a>에서 제공 되는 기존 손 제스처의 전체 목록입니다.

:::row:::
    :::column:::
       ![Near Select의 예](images/HandCoach/NearSelect.gif)<br>
       **거의 선택 된 사용 예 단추를 선택 하거나 interactable 개체를 닫는 방법을 보여 줍니다.**<br>
    :::column-end:::
    :::column:::
       ![대공 탭의 예](images/HandCoach/AirTap.gif)<br>
        **멀리 떨어져 있는 개체를 선택 하는 방법을 보여 주는 데 사용 되는 공기 탭의 예**<br>
    :::column-end:::
    :::column:::
       ![이동 예](images/HandCoach/Move.gif)<br>
       **공간에서 홀로그램을 이동 하는 방법을 보여 주는 데 사용 되는 개체를 공간으로 이동 하는 예제**<br>
    :::column-end:::
    :::column:::
       ![회전 예](images/HandCoach/Rotate.gif)<br>
       **회전-holograms 또는 개체를 회전 하는 방법을 보여 주는 데 사용 되는 예**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![크기 조정 예제](images/HandCoach/Scale.gif)<br>
       **Holograms를 더 크거나 작게 조작 하는 방법을 보여 주기 위해 사용 하는 규모의 예**<br>
    :::column-end:::
    :::column:::
       ![팜 위로의 예](images/HandCoach/PalmUp.gif)<br>
        **팜 up – 제안 된 사용의 예**<br>
    :::column-end:::
    :::column:::
       ![수동 대칭 이동의 예](images/HandCoach/HandFlip.gif)<br>
       **직접 대칭 이동-메뉴를 표시 하는 다른 방법**<br>
    :::column-end:::
    :::column:::
       ![스크롤 예](images/HandCoach/Scoll.gif)<br>
       **스크롤 예제-목록 또는 긴 문서 스크롤에 사용**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>설계 개념

Hololens2의 경우 instinctual 및 자연 핸드 제스처를 기반으로 하는 손으로의 상호 작용을 설계 했습니다. 이러한 경우가 대부분의 사용자에 게 직관적 이라고 생각 하므로 전용 제스처 학습 순간을 만들지 않습니다. 대신, holograms와 상호 작용 하는 데 익숙하지 않은 사용자에 게 이러한 제스처에 대해 알아보기 위해 손을 coach를 만들었습니다. 학습 시점이 없으면 사용자에 게 작업을 수행 하는 방법을 보여 주는 것이 가장 좋은 옵션입니다. 이 연구에서는 사용자가 제스처를 파악할 수 있었지만 약간의 지침을 필요로 했습니다. 사용자가 특정 기간 동안 개체와 상호 작용 하지 않는 것을 감지 하면 올바른 손 모양 및 손가락 배치를 시연 하는 손 모양 coach 트리거됩니다. 

### <a name="intuitive"></a>간단

실습에 애니메이션을 적용 하는 경우 분명 하 게 shoudn't 혼동을 발생 시킵니다. 바늘의 애니메이션은 사용자에 게 하기 호출할 사용자를 이해 하려는 제스처를 나타냅니다. 

예를 들어 사용자가 단추를 누르기를 원하는 경우 단추를 누르는 손을 트리거합니다.

![예: 손 모양 coach 가까이 누르기](images/HandCoach/NearSelect_unity.gif)<br>
*보석 가까이 누르기를 보여 주는 손 Coach*  

### <a name="hand-scale"></a>수동 크기 조정

UI 메뉴를 사용 하 여 다양 한 손 크기를 테스트 하 고 실제로는 크기에 따라 menacing 느낌이 있지만 너무 작은 경우에는 제스처를 보고 이해 하기 어렵습니다. 

**음성 전달 및 손**

사용자가 음성을 통해 일련의 지침을 수신 하 고 직접 coach를 통해 다양 한 지침을 볼 수 있다고 생각 하지 마세요. 토대로 오버 로드를 줄이기 위해 사용자에 게 집중 하 고 경합에 집중 하는 데 도움이 되는 지침을 시퀀싱 합니다.


## <a name="can-i-create-my-own"></a>직접 만들 수 있나요?

예. 게임에 고유한 제스처를 만들어 커뮤니티에 다시 참가 하는 것이 좋습니다.
다운로드 가능한 앱에 사용할 수 있는 Rigged 손의 Maya 파일을 제공 합니다. <a href="files/HandCoach_MRTK.zip">다운로드 HandCoach_MRTK.zip</a>

![Maya의 애니메이션 실습 예](images/HandCoach/MayaSelect_Gif.gif)<br>
*Maya의 상자에 애니메이션을 적용 하는 Poking 예*


**권장 authoring tool**

3D 아티스트 중에는 [Autodesk의 Maya](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 를 사용 하도록 선택 하 고,이를 사용 하 여 자산이 생성 되는 방식을 변환할 수 있습니다. 제공 되는 실습 파일은 Maya 이진 파일 이므로 Maya를 사용 하 여 애니메이션을 적용 하 고 내보내는 것이 좋습니다. 다른 3D 프로그램을 사용 하려는 경우에는 다음을 참조 <b>하세요. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">HandCoachMRTK_FBX.zip다운로드</a> 하 여 사용자 고유의 컨트롤러 설치를 만듭니다. 

제공 된 다운로드 가능 maya 손으로 제공 된 파일을 사용 하는 경우 unity의 손을 0.6으로 축소 하는 것이 좋습니다.

![예: Maya의 핸드 coach rig](images/HandCoach/MayaExample.png)<br>
*Rigged 손*

### <a name="technical-specs"></a>기술 사양

*   두 개의 전달 파일은 Maya Ascii 형식으로 사용할 수 있습니다.
*    오른쪽 및 왼쪽은 Maya 이진 형식으로 사용할 수 있습니다.
*   Maya 파일을 24FPS로 설정
*   파일 내에는 두 개의 핸드 또는 단일 면 제스처에 사용할 수 있는 왼쪽과 오른쪽이 있습니다. 오른쪽은 기본적으로 표시 됩니다.
*   약 10 개의 프레임에 대 한 버퍼를 시작 부분에 그대로 두고 페이드를 종료 하는 것이 좋습니다.
*   지정 된 대상을 사용 하 여 개체에 애니메이션 효과를 주려면 기본 상자 또는 Null에 애니메이션 효과를 주는 것이 가장 좋습니다.
*   상자와 같은 물리적 개체에 애니메이션 효과를 적용 하는 경우에는 Maya에서 번역에 애니메이션 효과를 주지 않지만 Unity 또는 코드에서 애니메이션 효과를 주기 위해 대기 하는 것이 가장 좋습니다.
*   표시 되는 애니메이션은 의미 있는 정보를 전달 하는 데 1.5 초 여야 합니다.
*   애니메이션에 만족 하는 경우:
    *   모든 연결점 및 굽기 키 프레임 선택
    *   컨트롤러를 삭제 하 고, 조인트 및 메시를 선택 하 고, FBX로 내보내기를 선택 합니다.
    *  여러 애니메이션이 있는 경우 Maya의 기본 제공 게임 내보내기를 사용할 수 있습니다.https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Maya에서 내보내기

애니메이션에 만족 하는 경우
* 모든 조인트 선택: 계층 > 선택

     ![예: 메뉴 위치](images/HandCoach/Hierarchy.png)<br>
* 애니메이션 굽기: 애니메이션 > 키 > 굽기 애니메이션으로 전환

     ![예: 메뉴 위치](images/HandCoach/BakeAnimation.png)<br>
* 컨트롤러 Rig: Outliner > MainR_Grp 또는 MainL_Grp를 삭제 합니다.

     ![예: 메뉴 위치](images/HandCoach/ControllerRig.png)<br>

* FBX로 내보내기: Select JNT + 메시: File > 선택 영역 내보내기 (옵션 상자) > 선택 영역 내보내기

     ![예: 메뉴 위치](images/HandCoach/OptionBox.png)<br>

     ![예: 메뉴 위치](images/HandCoach/SelectionExport.png)<br>

     ![예: 메뉴 위치](images/HandCoach/FBXSelection.png)<br>


 FBX로 내보내고 Unity로 이동 하는 경우에는 0.6에 맞게 조정 합니다. 이는 손을 표시 하는 데 완벽 한 균형을 갖고 있습니다. 

![예: Unity 설정](images/HandCoach/HandHintScale.png)<br>
*MRTK에서 찾은 HandCoach_R prefab에 대 한 Unity 설정*


## <a name="implementing-hands-into-your-unity-project"></a>Unity 프로젝트에 대 한 직접 구현

### <a name="best-practices"></a>모범 사례
*    Unity의 손을 0.6으로 축소 하는 것이 좋습니다.
*   손을 두 번 재생 하 고, 완료 되지 않은 경우 제스처가 완료 될 때까지 지속적으로 반복 됩니다. 사용자가를 등록 하 고 제스처를 볼 수 있도록 하려면 두 번 반복 해야 합니다. 바늘은 루프 간에 페이드 인 및 페이드 아웃 해야 합니다. 
 *  사용자의 손을 HL2 카메라에서 볼 수 있지만 사용자가 필요한 상호 작용을 수행 하지 않는 경우 10 초 후에도 손을 표시 합니다.
*   사용자의 손을 HL2 카메라에 표시 되지 않으면 5 초 후에도 손을 표시 합니다.  
*   애니메이션 중간의 HL2 카메라에서 사용자의 손을 시각적으로 추적 하는 경우 애니메이션이 완료 되 고 페이드 아웃 됩니다.
*   음성을 포함 하는 경우에는 손 제스처에 해당 하는 것이 좋습니다.
*   한 번 이상 실습을 수행한 경우에는 사용자가 중지 된 것으로 검색 된 경우에만 제스처를 반복 합니다.
*   특정 손가락/손 위치가 중요 한 경우 사용자가 애니메이션에서 이러한 미묘한 차이를 명확 하 게 볼 수 있도록 합니다. 가장 중요 한 부분이 명확 하 게 표시 되도록 손을 준. 
* 손으로 왜곡 된 경우 Unity의 품질 설정으로 이동 하 여 뼈의 크기를 늘려야 합니다. 
 Unity의 편집 > 프로젝트 설정 > 품질 > 기타 > 혼합 가중치로 이동 합니다. 부드러운 조인트를 보려면 "4 뼈"가 선택 되어 있는지 확인 합니다. 

   ![예: 메뉴 위치](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a>피해야 할 사항
* 너무 크게 크기 조정
* 사용자에 게 너무 가까운 손을 두기
* 손을 한 번만 지정 해야 합니다. 교육을 통해 혼란을 야기 하 고 messiness 수 있습니다.
*   Unity로 가져오면 최신 MRTK를 다운로드 하세요.https://github.com/microsoft/MixedRealityToolkit-Unity
    *   재질: Teaching_Hand2
    *   스크립트: <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">mrtk 손 coach</a> 에 대 한 mrtk 지침 참조
    *   프로젝트별 설정
        *   UWP로 설정 된 장면: Windows Mixed Reality의 [Unity 구성 프로젝트](Configure-Unity-Project.md) 에서 지침을 찾을 수 있습니다.

## <a name="see-also"></a>참조
* [상호 작용-기본 사항](interaction-fundamentals.md)
* [자산 생성 프로세스](asset-creation-process.md)
* [제스처](gestures.md)
* [도구 설치](install-the-tools.md)
* [Unity 프로젝트 구성](Configure-Unity-Project.md)
* [Unity 개발 개요](unity-development-overview.md)
* [MRTK 101](mrtk-101.md)
