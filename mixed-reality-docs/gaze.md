---
title: 응시
description: 응시는 첫 번째 입력 형태 이며 혼합 현실에서 대상이 지정 되는 기본 형식입니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합 현실, 응시, 상호 작용, 디자인
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414376"
---
# <a name="gaze"></a>응시

**응시** 는 첫 번째 입력 형태 이며 혼합 현실에서 대상이 지정 되는 기본 형식입니다. 응시를 통해 사용자가 전 세계 어디에서 찾고 있는지를 알 수 있습니다. 실제 세계에서는 일반적으로 상호 작용 하려는 개체를 살펴봅니다. 이는 응시와 동일 합니다.

혼합 현실 헤드셋은 사용자 헤드의 위치와 방향을 사용 하 여 헤드 응시 벡터를 결정 합니다. 이 벡터를 사용자의 눈 사이에서 바로 미리 레이저 포인터로 생각할 수 있습니다. 사용자가 대화방을 볼 때 응용 프로그램은 자체 holograms 및 [공간 매핑](spatial-mapping.md) 메시를 사용 하 여 사용자가 볼 수 있는 가상 또는 실제 개체를 결정 하기 위해이 광선을 교차할 수 있습니다.

HoloLens 2에서 상호 작용은 사용자의 헤드 응시, 눈동자 응시 또는 근거리 또는 원거리 상호 작용을 통해 대상으로 지정할 수 있습니다.
HoloLens (첫 번째 gen)에서 상호 작용은 일반적으로 직접 위치에서 렌더링 하거나 상호 작용 하는 대신 사용자의 헤드 응시에서 대상으로 지정 해야 합니다. 상호 작용이 시작 된 후 [조작 또는 탐색](gestures.md#composite-gestures) 제스처와 같이 손의 상대 동작을 사용 하 여 [제스처](gestures.md)를 제어할 수 있습니다. 모던 헤드셋을 사용 하면 헤드 응시 또는 포인팅 가능 [동작 컨트롤러](motion-controllers.md)를 사용 하 여 대상으로 지정할 수 있습니다.

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

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
        <td>헤드 응시</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>아이 응시</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> HoloLens 2에 대 한 추가 지침은 [곧](index.md#news-and-notes)제공 될 예정입니다.


## <a name="uses-of-gaze"></a>응시 사용

혼합 현실 개발자는 head 또는 눈동자 응시를 사용 하 여 많은 작업을 수행할 수 있습니다.
* 앱은 사용자의 주의가 있는 위치를 확인 하기 위해 장면의 holograms와 교차할 수 있습니다.
* 앱은 사용자의 응시에 따라 제스처 및 컨트롤러 누름을 대상으로 지정할 수 있으므로 사용자가 선택, 활성화, 잡기, 스크롤 또는 holograms와 상호 작용할 수 있습니다.
* 앱을 사용 하면 사용자가 holograms 표면에 해당 응시 광선과 공간 매핑 메시를 교차 시켜 서 실제 표면에 놓을 수 있습니다.
* 앱은 사용자가 중요 한 개체의 방향을 확인 *하지 않는* 경우를 알 수 있습니다. 그러면 응용 프로그램에서 시각적 개체와 오디오 신호를 제공 하 여 해당 개체를 가리킬 수 있습니다.

## <a name="cursor"></a>Cursor

헤드 응시의 경우 대부분의 앱은 [커서](cursors.md) (또는 기타 청각/시각적 표시)를 사용 하 여 사용자가 상호 작용 하려는 항목을 사용자에 게 확실 하 게 제공 해야 합니다. 일반적으로 헤드 응시 광선이 먼저 개체와 교차 하는 위치에이 커서를 배치 합니다 .이는 홀로그램 또는 실제 표면이 될 수 있습니다.

![응시를 표시 하는 예제 시각적 커서](images/cursor.jpg)<br>
*응시를 표시 하는 예제 시각적 커서*

아이 응시의 경우 일반적으로 사용자에 게 혼란을 줄 수 있으므로 커서를 표시 *하지 않는* 것이 좋습니다. 대신 시각적 대상을 미세 하 게 강조 표시 하거나 매우 희미 한 눈 커서를 사용 하 여 사용자가 상호 작용할 정보를 제공 합니다. 자세한 내용은 HoloLens 2의 [눈동자 기반 입력에 대 한 디자인 지침](eye-tracking.md) 을 확인 하세요.

## <a name="giving-action-to-the-users-gaze"></a>사용자의 응시에 작업 제공

사용자가 응시를 사용 하 여 홀로그램 또는 실제 개체를 대상으로 지정 하 고 나면 다음 단계는 해당 개체에 대해 작업을 수행 하는 것입니다. 사용자가 작업을 수행 하는 기본 방법은 [제스처](gestures.md), [동작 컨트롤러](motion-controllers.md) 및 [음성을](voice-input.md)사용 하는 것입니다.

## <a name="see-also"></a>참조
* [MR 입력 210: 헤드 응시](holograms-210.md)
* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [Unity의 헤드 응시](gaze-in-unity.md)
* [눈동자-HoloLens에서 응시 2](eye-tracking.md)
* [Mixed Reality Toolkit를 사용 하 여 Unity의 눈동자 응시](https://aka.ms/mrtk-eyes)
