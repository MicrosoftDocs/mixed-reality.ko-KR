---
title: 집에서 3D 모델의 배치를 사용 하도록 설정
description: Windows Mixed Reality 홈에 웹 사이트 또는 응용 프로그램에서 3D 모델을 배치 하는 방법
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, 모델, 홈에서 위치, 위치, 세계, 모델링, 혼합된 현실 홈, 웹, 앱
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829727"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>홈 혼합된 현실에서 3D 모델의 배치를 사용 하도록 설정

> [!NOTE]
> 일부로 추가 된이 기능을 [Windows 10 2018 년 4 월 업데이트](release-notes-april-2018.md)합니다. 이전 버전 Windows의이 기능을 사용 하 여 호환 되지 않습니다.

합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 출발점 응용 프로그램을 시작 하기 전에 사용자가 이동 하는 위치입니다. 일부 시나리오에서는 2D 앱 (예: 홀로그램 앱) 장식을 또는 전체 3d에서 추가로 조사에 대 한 3D 모델 혼합된 현실 홈에 직접 배치할 수 있도록 합니다. 합니다 *모델 프로토콜을 추가* 계속 유지 되며 여기서 같은 웹 사이트 또는 집 Windows Mixed Reality로 직접 응용 프로그램에서 3D 모델을 보낼 수 있습니다 [3D 앱 시작 관리자](3d-app-launcher-design-guidance.md), 2D 앱 및 제공 합니다. 

예를 들어, 응용 프로그램 카탈로그의 공간을 디자인 하기 위한 3D 가구를 표시 하는 개발 하는 경우 사용할 수는 *모델 프로토콜 추가* 카탈로그에서 해당 가구 3D 모델에 적용할 수 있도록 합니다. 사용자가 이동, 전 세계에 배치 되 면 크기 조정 및 집에서 다른 홀로그램 마찬가지로 이러한 3D 모델을 제거 합니다. 이 문서에서는 구현 하는 개요를 제공 합니다 *모델 프로토콜을 추가* 앱 또는 웹에서 3D 개체를 사용 하 여 세계를 데코 레이트 할 수 있도록 시작할 수 있도록 합니다.

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>모델 프로토콜 추가</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>개요

Windows Mixed Reality 홈에서 3D 모델의 배치를 사용 하도록 설정 하는 방법은 2 단계가 있습니다.
1. [3D 모델 홈 Windows Mixed Reality와 호환 되는지 확인](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)합니다.
2. 구현 된 *모델 프로토콜 추가* 응용 프로그램 또는 웹 페이지 (이 문서)에서.

## <a name="implementing-the-add-model-protocol"></a>구현 된 *모델 프로토콜 추가*

했으면를 [호환 3D 모델](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)를 구현할 수 있습니다 합니다 *모델 프로토콜을 추가* 웹 페이지 또는 응용 프로그램에서 다음 URI를 활성화 하 여:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

URI 원격 리소스를 가리키는 경우 다음이 자동으로 다운로드 되 고 홈에 배치 합니다. 집에서 추가 되기 전에 로컬 리소스의 혼합된 현실 홈 앱 데이터 폴더에 복사 됩니다. 사용자 수 실행 될 있는 이전 버전의 Windows 단추를 숨기 거 나 가능 하면 사용 하 여이 기능을 지원 하지 않는 시나리오에 대 한 계정에 환경을 디자인 하는 것이 좋습니다. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>호출 된 *모델 프로토콜 추가* 유니버설 Windows 플랫폼 앱에서:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>호출 된 *모델 프로토콜 추가* 웹 페이지에서:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>몰입 형 (VR) 헤드셋에 대 한 고려 사항

* 몰입 형 (VR) 헤드셋, 혼합 현실 포털 없는 호출 하기 전에 실행 중 이어야 합니다 *모델 프로토콜 추가*합니다. 이 경우에 *모델 프로토콜 추가* 혼합 현실 포털을 시작 하 고 개체 직접 여기서 헤드셋은 홈 혼합된 현실에서 열리면 배치 됩니다. 
* 호출할 때 합니다 *모델 프로토콜 추가* 이미 실행 하는 혼합 현실 포털을 사용 하 여 데스크톱에서 헤드셋 "절전 모드 해제" 인지를 확인 합니다. 그렇지 않은 경우 배치에 실패 합니다. 

## <a name="see-also"></a>참조

* [Windows Mixed Reality 집에서 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
