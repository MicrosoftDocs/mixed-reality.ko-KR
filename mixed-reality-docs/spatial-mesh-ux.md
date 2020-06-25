---
title: 공간 메시 시각화
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 혼합 현실, HoloLens, UI 컨트롤, 상호 작용, UI, ux, UX 디자인, 공간 UI, 공간 상호 작용, 3D UI, 3D UX
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346136"
---
# <a name="spatial-mesh"></a>공간 메시

![공간 메시](images/UX/MRTK_PulseShader_SpatialMesh.gif)

공간 메시 시각화를 통해 사용자는 장치가 물리적 환경을 인식 하 고 이해 하는 방법을 배울 수 있습니다. 공간 컨텍스트를 제공 하는 것 외에도 적절 한 공간 메시 시각화를 통해 매력적인 및 마법 환경을 만들 수 있습니다.  

## <a name="design-guideline"></a>디자인 지침
사용자가 콘텐츠를 집중적으로 사용 하 고 상호 작용할 수 있도록 하는 것이 중요 하기 때문에 백그라운드에서 공간 메시를 지속적으로 반복적으로 시각화 하는 작업은 혼란을 받을 수 있습니다. 초기 실행에서 한 번만 또는 사용자가 공간을 대상으로 하 여 환경 메시를 볼 수 있는 명확한 의도를 표시 하는 경우에만 환경을 시각화 하는 것이 좋습니다. HoloLens 셸에서이 동작을 관찰할 수 있습니다.
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 공간 메시 시각화
MRTK는 공간 메시 시각화에 대 한 여러 자료를 제공 합니다.

- **MRTK_Wireframe, MRTK_Wireframe**: 기본 정적 공간 메시 재질: 애니메이션 없이 메시 윤곽선을 표시 합니다. 이 자료는 전체 공간 메시 기 하 도형을 표시 하기 때문에 디버깅 목적으로 유용 합니다. 그러나 프로덕션 환경에서는 권장 되지 않습니다.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.** 대만:이 자료는 공간 메시에 애니메이션 된 펄스 효과를 제공 합니다. 이 자료를 사용 하 여 특정 경험 또는 사용자의 공중 탭 입력에서 환경을 시각화할 수 있습니다. 예제는 **PulseShaderExamples** 을 참조 하세요.
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* 자세한 내용은 [Mrtk-공간 인식](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 및 [Mrtk-펄스 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) 를 참조 하세요.

<br>

---

## <a name="see-also"></a>참조

* [커서](cursors.md)
* [손 광선](point-and-commit.md)
* [Button](button.md)
* [상호 작용 가능한 개체](interactable-object.md)
* [경계 상자 및 앱 바](app-bar-and-bounding-box.md)
* [조작](direct-manipulation.md)
* [손 메뉴](hand-menu.md)
* [Near 메뉴](near-menu.md)
* [개체 컬렉션](object-collection.md)
* [음성 명령](voice-input.md)
* [키보드](keyboard.md)
* [Tooltip](tooltip.md)
* [슬레이트](slate.md)
* [슬라이더](slider.md)
* [셰이더](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)
