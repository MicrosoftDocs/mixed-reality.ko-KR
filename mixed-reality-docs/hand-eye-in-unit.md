---
title: Unity에서의 트레일러 및 눈 추적
description: Unity에서 작업을 수행 하는 데는 두 가지 주요 방법, 즉 핸드 제스처와 동작 컨트롤러가 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 제스처, 동작 컨트롤러, unity, 응시, 입력
ms.openlocfilehash: b60c5567714893f2d1f2cc929e832bb851dd9e34
ms.sourcegitcommit: 4081dc2356fec0ea3625f1d989689cfbbb3fcf5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203322"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity에서의 트레일러 및 눈 추적

HoloLens 2에는 새로운 흥미로운 기능이 도입 되었습니다.

Unity에서 새로운 기능을 활용 하는 가장 쉬운 방법은 MRTK v 2를 통하는 것입니다. 또한 시작 하는 데 도움이 되는 몇 가지 예제 장면이 있습니다. 

* [MRTK v 2의 트레일러 식 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [MRTK v2에서 눈 추적 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)


## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>MRTK v 2의 실습, 눈동자 및 기타를 지 원하는 빌딩 블록

MRTK v2는 개발을 가속화 하는 데 도움이 되는 UI 컨트롤 및 구성 요소 집합을 제공 합니다. 

|  [![단추](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [경계 상자](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) [경계 상자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)![ | [![조작 처리기](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| HoloLens2's를 포함 하는 다양 한 입력 메서드를 지 원하는 button 컨트롤입니다. | 3D 공간에서 개체 조작을 위한 표준 UI | 하나 또는 두 개의 손을 사용 하 여 개체를 조작 하는 스크립트 |
|  [![슬레이트](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [슬레이트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [![시스템 키보드](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) [시스템 키보드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![Interactable](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| 트레일러 식 입력으로 스크롤을 지 원하는 2D 스타일 평면 | Unity에서 시스템 키보드를 사용 하는 예제 스크립트  | 시각적 상태 및 테마 지원과 함께 개체를 interactable 하는 스크립트 |
|  [해 찾기![](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [![개체 컬렉션](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [개체 컬렉션](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [![도구](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) 설명 [도구 설명](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| 태그 동반, 본문 잠금, 상수 보기 크기 및 표면 자기와 같은 다양 한 개체 위치 지정 동작 | 3 차원 모양의 개체 배열을 레이아웃 하는 스크립트 | 동작 컨트롤러 및 개체에 레이블을 지정 하는 데 사용할 수 있는 유연한 앵커/피벗 시스템을 포함 하는 주석 UI입니다. |
|  [![앱 바](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) [앱 바](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![포인터](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) [포인터](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) | [![Fingertip 시각화](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) [Fingertip 시각화](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| 경계 상자의 수동 활성화를 위한 UI | 다양 한 종류의 포인터에 대해 알아보기 | 직접 상호 작용에 대 한 신뢰도를 향상 시키는 fingertip의 시각적 affordance |
|  [![눈 추적: 대상 선택 항목](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) [추적: 대상 선택](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [![눈 추적: 탐색](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) [눈동자 추적: 탐색](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [![눈 추적: 열 지도](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [눈 추적: 열 지도](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 눈, 음성 및 손 입력을 결합 하 여 장면 전체의 holograms을 빠르고 간편 하 게 선택 | 표시 되는 내용에 따라 텍스트를 자동으로 운용 확대/축소 하는 방법에 대해 알아봅니다.| 사용자의 앱에서 보고 있는 사용자를 기록, 로드 및 시각화 하는 예제 |

## <a name="example-scenes"></a>예제 장면
[이 예제 장면](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)에서 MRTK의 다양 한 유형의 상호 작용 및 UI 컨트롤을 탐색 합니다.

**자산/MixedRealityToolkit/데모**폴더의 [Mixed Reality Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) 에서 다른 예제 장면을 찾을 수 있습니다.

[![장면 예](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>참고 항목

* [시선 기반 상호 작용](eye-gaze-interaction.md)
* [HoloLens 2의 시선 추적](eye-tracking.md)
* [응시 및 커밋](gaze-and-commit.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [손 - 가리키기 및 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [모션 컨트롤러](motion-controllers.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 추적](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
