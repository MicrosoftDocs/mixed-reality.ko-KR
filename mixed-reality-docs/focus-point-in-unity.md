---
title: Unity의 포커스 지점
description: 포커스 지점을 설정 하 여 Unity에서 홀로그램 안정성을 수동으로 조정
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 포커스 지점을, 포커스 평면, 안정화 평면, 안정화 지점, reprojection, LSR, 깊이 버퍼
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604882"
---
# <a name="focus-point-in-unity"></a>Unity의 포커스 지점

**Namespace:** *UnityEngine.XR.WSA*<br>
**형식**: *HolographicSettings*

합니다 [지점 집중](hologram-stability.md#stabilization-plane) HoloLens 가장 안정화를 홀로그램에서 현재 수행 하는 방법에 대 한 힌트를 제공 하는로 설정 되 고 표시할 수 있습니다.

Unity에서의 포커스 지점을 설정 하려는 경우 사용 하 여 모든 프레임을 설정할 수 해야 *HolographicSettings.SetFocusPointForFrame()* 합니다. 프레임의 포커스 지점을 설정 되지 않은 경우 기본 안정화 평면 사용 됩니다.

> [!NOTE]
> 새 Unity 프로젝트는 기본적으로 설정 "깊이 버퍼 공유 사용" 옵션을 적용 합니다.  이 옵션을 몰입 형 데스크톱 헤드셋 또는 Windows를 실행 하는 HoloLens에서 실행 중인 Unity 앱을 10 2018 년 4 월 업데이트 (RS4) 나중에 앱을 지정 하지 않고 자동으로 홀로그램 안정성을 최적화 하기 위해 Windows 깊이 버퍼 제출 또는 포커스 지점:
> * 몰입 형 데스크톱 헤드셋에서 픽셀 별 깊이 기반 reprojection을 이렇게 합니다.
> * HoloLens 실행 Windows 10 2018 년 4 월 업데이트는 최적의 안정화 평면을 자동으로 선택 하려면 깊이 버퍼 분석이 나중에 또는 합니다.
>
> 각 접근 방법을 제공 해야 명시적 작업 없이 더 나은 이미지 품질 포커스 지점을 선택 하려면 앱에서 각 프레임입니다.  참고를 제공 하는 포커스 지점을 수동으로 경우는 위에서 설명한 자동 동작을 재정의 하 홀로그램 안정성 일반적으로 줄어듭니다.  일반적으로 지정 해야 수동 포커스 지점을 windows 아직 업데이트 되지 않은 HoloLens에 앱이 실행 하는 경우 10 2018 년 4 월 업데이트 합니다.

### <a name="example"></a>예제

사용할 수 있는 오버 로드에서 제안 된 포커스 지점으로 설정 하는 방법은 여러 가지는 *SetFocusPointForFrame* 정적 함수입니다. 아래는 각 프레임 제공된 된 개체를 포커스 평면을 설정 하는 간단한 예제:

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

위의 간단한 코드 면 포커스가 있는 개체 사용자 뒤 홀로그램 안정성을 줄이는 끝날 수도 있습니다 note 합니다.  이 때문에 수동으로 포커스 지점을 지정 하는 대신 일반적으로 "깊이 버퍼 공유 사용"을 설정 해야 합니다.

### <a name="see-also"></a>참조
* [안정화 평면](hologram-stability.md#stabilization-plane)
