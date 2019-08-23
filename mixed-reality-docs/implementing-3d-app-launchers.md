---
title: 3D 앱 응용 프로그램 구현 (UWP 앱)
description: HoloLens 및 모던 (VR) 헤드셋 모두에서 Windows Mixed Reality UWP 앱 및 게임 (Microsoft Store을 통해 배포)에 대 한 3D 앱 다운로드 및 로고를 만드는 방법입니다.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 로고, 아이콘, 모델링, 시작 관리자, 3D 시작 관리자, 타일, 라이브 큐브, 딥 링크, secondarytile, 보조 타일, UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516731"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>3D 앱 응용 프로그램 구현 (UWP 앱)

> [!NOTE]
> 이 기능은 몰입 형 헤드셋에 대해 RS3 (2017) 크리에이터 업데이트의 일부로 추가 되었으며 Windows 10 4 월 2018 업데이트를 사용 하 여 HoloLens에서 지원 됩니다. 응용 프로그램이 10.0.16299의 버전을 대상으로 하는 Windows SDK의 버전을 대상으로 하는 작업을 대상으로 합니다. [여기](https://developer.microsoft.com/windows/downloads/windows-10-sdk)에서 최신 Windows SDK를 찾을 수 있습니다.

[Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 은 사용자가 응용 프로그램을 시작 하기 전에 수행 하는 시작 지점입니다. Windows Mixed Reality 용 UWP 응용 프로그램을 만들 때 기본적으로 앱은 앱 로고를 사용 하 여 2D 슬레이트 시작 됩니다. Windows Mixed Reality 환경을 개발 하는 경우 응용 프로그램의 기본 2D 시작 관리자를 재정의 하도록 3D 시작 관리자를 선택적으로 정의할 수 있습니다. 일반적으로 Windows Mixed Reality 홈에서 사용자를 제외 하는 몰입 형 응용 프로그램을 시작 하는 데 3D 시작을 사용 하는 것이 좋으며,이 경우에는 앱이 현재 활성화 될 때 기본 2D 시작 관리자가 선호 됩니다 [3d 딥 링크 (secondaryTile)](#3d-deep-links-secondarytiles) 를 2d UWP 앱 내 콘텐츠의 3d 시작 관리자로 만들 수도 있습니다.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D 앱 시작 관리자 만들기 프로세스

3D 앱 시작 관리자를 만드는 단계는 세 가지입니다.
1. [디자인 및 concepting](3d-app-launcher-design-guidance.md)
2. [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 응용 프로그램에 통합 (이 문서)

응용 프로그램에 대 한 관리자로 사용할 3D 자산은 호환성을 보장 하기 위해 [Windows Mixed Reality 제작 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 을 사용 하 여 작성 해야 합니다. 이 제작 사양을 충족 하지 못하는 자산은 Windows Mixed Reality 홈에서 렌더링 되지 않습니다.

## <a name="configuring-the-3d-launcher"></a>3D 시작 관리자 구성

Visual Studio에서 새 프로젝트를 만든 경우 앱의 이름 및 로고를 표시하는 간단한 기본 타일이 만들어집니다. 이 2D 표현을 사용자 지정 3D 모델로 바꾸려면 "MixedRealityModel" 요소를 기본 타일 정의의 일부로 포함 하도록 응용 프로그램의 응용 프로그램 매니페스트를 편집 합니다. 2D 시작 관리자로 되돌리려면 매니페스트에서 MixedRealityModel 정의를 제거 하면 됩니다.

### <a name="xml"></a>XML

먼저 현재 프로젝트에서 앱 패키지 매니페스트를 찾습니다. 기본적으로 매니페스트는 appxmanifest.xml로 이름이 지정 됩니다. Visual Studio를 사용 하는 경우 솔루션 뷰어에서 매니페스트를 마우스 오른쪽 단추로 클릭 하 고 **소스 보기** 를 선택 하 여 편집을 위해 xml을 엽니다. 

매니페스트 위쪽에서 uap5 스키마를 추가 하 고이를 무시할 수 있는 네임 스페이스로 포함 합니다.

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

다음으로 응용 프로그램의 기본 타일에서 "MixedRealityModel"를 지정 합니다.

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

MixedRealityModel 요소는 응용 프로그램 패키지에 저장 된 3D 자산을 가리키는 파일 경로를 허용 합니다. 현재는 .bb 파일 형식을 사용 하 여 전달 되 고 [Windows Mixed Reality 3d 자산 제작 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 에 따라 작성 된 3d 모델만 지원 됩니다. 자산은 앱 패키지에 저장 되어야 하 고 현재 애니메이션은 지원 되지 않습니다. "Path" 매개 변수를 비워 두면 Windows에서 3D 시작 관리자 대신 2D 슬레이트를 표시 합니다. **참고:** 응용 프로그램을 빌드하고 실행 하기 전에 빌드 설정에서 .bb 자산을 "콘텐츠"로 표시 해야 합니다.


![솔루션 탐색기에서. a s b를 선택 하 고 속성 섹션을 사용 하 여 빌드 설정에서 "콘텐츠"로 표시 합니다.](images/buildsetting-content-300px.png)<br>
*솔루션 탐색기에서. a s b를 선택 하 고 속성 섹션을 사용 하 여 빌드 설정에서 "콘텐츠"로 표시 합니다.*

### <a name="bounding-box"></a>경계 상자

경계 상자는 개체 주위에 추가 버퍼 영역을 선택적으로 추가 하는 데 사용할 수 있습니다. 경계 상자는 경계 상자 중심에서 각 축의 가장자리 까지의 거리를 나타내는 중심점 및 범위를 사용 하 여 지정 됩니다. 경계 상자의 단위는 1 단위 = 1 미터에 매핑할 수 있습니다. 경계 상자를 제공 하지 않으면 하나는 개체의 메시에 자동으로 맞춰집니다. 제공 된 경계 상자가 모델 보다 작으면 망상에 맞게 크기가 조정 됩니다.

경계 상자 특성에 대 한 지원은 Windows RS4 update와 함께 MixedRealityModel 요소에 대 한 속성으로 제공 됩니다. 응용 프로그램 매니페스트 맨 위에 있는 경계 상자를 먼저 정의 하려면 uap6 스키마를 추가 하 고이를 무시할 수 있는 네임 스페이스로 포함 합니다.

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
그런 다음 MixedRealityModel에서 SpatialBoundingBox 속성을 설정 하 여 경계 상자를 정의 합니다. 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Unity 사용

Unity를 사용 하는 경우 응용 프로그램 매니페스트를 편집 하려면 먼저 Visual Studio에서 프로젝트를 빌드하고 열어야 합니다. 

>[!NOTE]
>Unity에서 새 Visual Studio 솔루션을 빌드 및 배포 하는 경우 매니페스트에서 3D 시작 관리자를 다시 정의 해야 합니다.

## <a name="3d-deep-links-secondarytiles"></a>3D 딥 링크 (secondaryTiles)

> [!NOTE]
> 이 기능은 모던 용 2017 RS3 (RS4) 헤드셋의 일부로 추가 되었으며 HoloLens 용 (4 월 2018 업데이트)의 일부로 추가 되었습니다. 응용 프로그램이 10.0.16299 on 모던 (VR) 헤드셋 및 10.0.17125의 버전을 대상으로 하는 Windows SDK 버전을 대상으로 하는지 확인 합니다. [여기](https://developer.microsoft.com/windows/downloads/windows-10-sdk)에서 최신 Windows SDK를 찾을 수 있습니다.

>[!IMPORTANT]
>3D 딥 링크 (secondaryTiles)는 2D UWP 앱 에서만 작동 합니다. 그러나 Windows Mixed Reality 홈에서 전용 앱을 시작 하는 [3d 앱 시작 관리자](implementing-3d-app-launchers.md) 를 만들 수 있습니다.

응용 프로그램의 3D 모델을[ windows 혼합 현실](navigating-the-windows-mixed-reality-home.md)에 추가 하는 기능을 추가 하는 기능을 추가 하 여 Windows 혼합 현실에서 [2d 응용 프로그램](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)을 향상 시킬 수 있습니다. 예를 들어 360 ° photo viewer 앱에 직접 연결 되는 360 ° 인화지를 만들거나, 사용자가 저자에 대 한 세부 정보 페이지를 여는 자산 컬렉션에서 3D 콘텐츠를 넣을 수 있습니다. 3D 콘텐츠를 사용 하 여 2D 응용 프로그램의 기능을 확장 하는 몇 가지 방법입니다.

### <a name="creating-a-3d-secondarytile"></a>3D "secondaryTile" 만들기

만들 때 혼합 현실 모델을 정의 하 여 "secondaryTiles"을 사용 하 여 응용 프로그램의 3D 콘텐츠를 저장할 수 있습니다. 혼합 현실 모델은 앱 패키지에서 3D 자산을 참조 하 고 필요에 따라 경계 상자를 정의 하 여 생성 됩니다. 

> [!NOTE]
> 단독 보기 내에서 "secondaryTiles" 만들기는 현재 지원 되지 않습니다.

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>경계 상자

경계 상자는 개체 주위에 추가 버퍼 영역을 추가 하는 데 사용할 수 있습니다. 경계 상자는 경계 상자 중심에서 각 축의 가장자리 까지의 거리를 나타내는 중심점 및 범위를 사용 하 여 지정 됩니다. 경계 상자의 단위는 1 단위 = 1 미터에 매핑할 수 있습니다. 경계 상자를 제공 하지 않으면 하나는 개체의 메시에 자동으로 맞춰집니다. 제공 된 경계 상자가 모델 보다 작으면 망상에 맞게 크기가 조정 됩니다.

### <a name="activation-behavior"></a>활성화 동작

> [!NOTE]
> 이 기능은 Windows RS4 업데이트를 통해 지원 될 예정입니다. 이 기능을 사용 하려는 경우 응용 프로그램이 10.0.17125 이상 Windows SDK 버전을 대상으로 하 고 있는지 확인 합니다.

3D secondaryTile의 활성화 동작을 정의 하 여 사용자가 선택할 때 반응 하는 방식을 제어할 수 있습니다. 이는 purley 정보 또는 장식용 인 혼합 현실 홈에 3D 개체를 저장 하는 데 사용할 수 있습니다. 다음 활성화 동작 유형이 지원 됩니다.
1. 기본값: 사용자가 3D secondaryTile을 선택 하면 앱이 활성화 됩니다.
2. None: 사용자가 3D secondaryTile을 선택 하면 아무것도 발생 하지 않으며 앱이 활성화 되지 않습니다.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>기존 "secondaryTile" 가져오기 및 업데이트

개발자는 이전에 지정한 속성을 포함 하 여 기존 보조 타일의 목록을 다시 가져올 수 있습니다. 값을 변경한 다음 UpdateAsync ()를 호출 하 여 속성을 업데이트할 수도 있습니다.

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>사용자가 Windows Mixed Reality에 있는지 확인 하는 중

3D 딥 링크 (secondaryTiles)는 보기가 Windows Mixed Reality 헤드셋에 표시 되는 동안에만 만들 수 있습니다. Windows Mixed Reality 헤드셋에 보기가 표시 되지 않는 경우 진입점을 숨기 거 나 오류 메시지를 표시 하 여이를 정상적으로 처리 하는 것이 좋습니다. [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)를 쿼리하여이를 확인할 수 있습니다.

## <a name="tile-notifications"></a>타일 알림

타일 알림은 현재 3D 자산과 함께 업데이트를 전송 하는 것을 지원 하지 않습니다. 즉, 개발자가 다음을 수행할 수 없습니다.
* 푸시 알림
* 정기적 폴링
* 예약 된 알림

다른 타일 기능 및 특성과 2D 타일에 사용 되는 방법에 대 한 자세한 내용은 [UWP 앱에 대 한 타일 설명서](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)를 참조 하세요.

## <a name="see-also"></a>참조

* 3D 앱 시작 관리자를 포함 하는 [혼합 현실 모델 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) 입니다.
* [3D 앱 시작 관리자 디자인 지침](3d-app-launcher-design-guidance.md)
* [Windows Mixed Reality 홈에서 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D 앱 응용 프로그램 구현 (Win32 앱)](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
