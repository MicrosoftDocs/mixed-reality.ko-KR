---
title: Unity의 포커스 지점
description: 포커스 지점을 설정 하 여 Unity에서 홀로그램 안정성 수동 조정
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 포커스 지점, 포커스 평면, 안정화 평면, 안정화 지점, reprojection, LSR, 깊이 버퍼
ms.openlocfilehash: 9a7f30b552242b24a9a7b260b6574690a27d2c1d
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502624"
---
# <a name="focus-point-in-unity"></a>Unity의 포커스 지점

**네임 스페이스:** *unityengine. XR. WSA*<br>
**유형**: *HolographicSettings*

현재 표시 되는 holograms에서 안정화를 가장 잘 수행 하는 방법에 대 한 힌트를 HoloLens에 제공 하도록 [포커스 지점을](hologram-stability.md#reprojection) 설정할 수 있습니다.

Unity에서 포커스 지점을 설정 하려면 *HolographicSettings. SetFocusPointForFrame ()* 를 사용 하 여 모든 프레임을 설정 해야 합니다. 프레임에 대 한 포커스 지점이 설정 되지 않은 경우 기본 안정화 평면이 사용 됩니다.

> [!NOTE]
> 기본적으로 새 Unity 프로젝트에는 "깊이 버퍼 공유 사용" 옵션이 설정 되어 있습니다.  이 옵션을 사용 하는 경우 Windows 10 4 월 2018 업데이트 (RS4) 이상을 실행 하는 몰입 형 데스크톱 헤드셋 또는 HoloLens에서 실행 되는 Unity 앱은 앱이 자동으로 포커스 지점:
> * 모던 데스크톱 헤드셋에서 픽셀 단위 깊이 기반 재 프로젝션을 사용 합니다.
> * Windows 10 4 월 2018 업데이트 이상을 실행 하는 HoloLens에서이는 깊이 버퍼를 분석 하 여 최적의 안정화 평면을 자동으로 선택 합니다.
>
> 이러한 방법 중 하나는 각 프레임에 대 한 포커스 지점을 선택 하기 위해 앱에서 명시적으로 작업 하지 않고도 이미지 품질을 더욱 개선 하는 것입니다.  포커스 지점을 수동으로 제공 하는 경우 위에서 설명한 자동 동작이 재정의 되 고 일반적으로 홀로그램 안정성이 감소 됩니다.  일반적으로 Windows 10 4 월 2018 업데이트로 아직 업데이트 되지 않은 HoloLens에서 앱이 실행 되는 경우에만 수동 포커스 지점을 지정 해야 합니다.

### <a name="example"></a>예

*SetFocusPointForFrame* 정적 함수에서 사용할 수 있는 오버 로드에 의해 제안 된 대로 포커스 지점을 설정 하는 방법에는 여러 가지가 있습니다. 아래에서는 각 프레임에 대해 제공 된 개체에 포커스 평면을 설정 하는 간단한 예제를 제공 합니다.

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

위의 간단한 코드는 포커스가 있는 개체가 사용자 뒤에서 종료 되는 경우 홀로그램의 안정성을 낮출 수 있습니다.  따라서 일반적으로 포커스 지점을 수동으로 지정 하는 대신 "깊이 버퍼 공유 사용"을 설정 해야 합니다.

### <a name="see-also"></a>참고 항목
* [안정화 평면](hologram-stability.md#reprojection)
