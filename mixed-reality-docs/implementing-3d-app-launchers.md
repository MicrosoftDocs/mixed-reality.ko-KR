---
title: 3D 앱 시작 관리자 (UWP 앱)를 구현 합니다.
description: 모두 HoloLens, (VR) 헤드셋 몰입 감이 뛰어난 3D 앱 시작 관리자 및 Windows Mixed Reality UWP 앱 및 게임 (Microsoft Store 통해 분산)에 대 한 로고를 만드는 방법입니다.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 로고, 아이콘, 모델링, 표시 아이콘, 3D 표시 아이콘, 타일, 라이브 큐브, 딥 링크, secondarytile, UWP 보조 타일
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604857"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>3D 앱 시작 관리자 (UWP 앱)를 구현 합니다.

> [!NOTE]
> 이 몰입 형 헤드셋에 대 한 2017 Fall Creators Update (RS3)의 일부로 추가 된 기능과 Windows 사용 하 여 HoloLens 지 10 2018 년 4 월 업데이트 합니다. 응용 프로그램의 몰입 형 헤드셋에서 10.0.16299 보다 크거나 같고 10.0.17125 HoloLens에 Windows SDK 버전을 대상으로 하는지 확인 합니다. 최신 Windows SDK를 찾을 수 있습니다 [여기](https://developer.microsoft.com/windows/downloads/windows-10-sdk)합니다.

합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 출발점 응용 프로그램을 시작 하기 전에 사용자가 이동 하는 위치입니다. UWP 응용 프로그램에 만들면 Windows Mixed Reality 기본적으로, 앱은 앱의 로고를 사용 하 여 2D 슬레이트로 시작 됩니다. Windows Mixed Reality 환경을 개발, 3D 시작 관리자 응용 프로그램에 대 한 기본 2D launcher를 재정의 하려면 선택적으로 정의할 수 있습니다. 일반적으로 3D 시작 관리자 앱 내부에서 활성화 될 때 기본 2D 시작 관리자는 기본 Windows Mixed Reality 홈에서 사용자를 사용 하는 몰입 형 응용 프로그램을 실행 하는 데 권장 됩니다. 만들 수도 있습니다는 [3D 딥 링크 (secondaryTile)](#3d-deep-links-secondarytiles) 2D UWP 앱 내에서 콘텐츠를 3D 실행 프로그램으로 합니다.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D 앱 시작 관리자 만들기 프로세스

3D 앱 시작 관리자를 작성 하는 방법은 3 단계가 있습니다.
1. [디자인 및 concepting](3d-app-launcher-design-guidance.md)
2. [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 응용 프로그램 (이 문서)에 통합

3D 자산 사용 하 여 응용 프로그램 시작 관리자를 작성 해야 하는 대로 사용 해야 합니다 [Windows Mixed Reality 작성 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 호환성을 확인 합니다. 이 제작 사양을 충족 하지 못한 자산 Windows Mixed Reality 홈에서 렌더링 되지 않습니다.

## <a name="configuring-the-3d-launcher"></a>3D 시작 관리자를 구성합니다.

Visual Studio에서 새 프로젝트를 만든 경우 앱의 이름 및 로고를 표시하는 간단한 기본 타일이 만들어집니다. 이 2D 바꾸려면 기본 타일 정의의 일부로 "MixedRealityModel" 요소를 포함 하도록 응용 프로그램의 앱 매니페스트를 편집 하는 사용자 지정 3D 모델을 사용 하 여 표현 합니다. 2D로 되돌리려면 시작 관리자 매니페스트에서 MixedRealityModel 정의 제거 합니다.

### <a name="xml"></a>XML

먼저 현재 프로젝트에서 앱 패키지 매니페스트를 찾습니다. 기본적으로 매니페스트 Package.appxmanifest 이름이 됩니다. Visual Studio를 사용 하는 경우 다음 솔루션 뷰어에서 매니페스트를 마우스 오른쪽 단추로 클릭 하 고 선택 **소스 보기** 를 편집 하는 것에 대 한 xml을 엽니다. 

매니페스트의 맨 위에 있는 uap5 스키마를 추가 하 고 네임 스페이스를 무시할 수로 포함 합니다.

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

그런 다음 응용 프로그램에 대 한 기본 타일에서 "MixedRealityModel"를 지정 합니다.

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

MixedRealityModel 요소를 앱 패키지에 저장 된 3D 자산을 가리키는 파일 경로 허용 합니다. 3 차원 모델.glb 파일 형식을 사용 하 여 배달 하 고에 대해 작성 하는 현재 합니다 [지침을 작성 하는 Windows Mixed Reality 3D 자산](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 지원 됩니다. 자산 앱 패키지에 저장 되어야 하며 애니메이션 현재 지원 되지 않습니다. "Path" 매개 변수를 지정 하지 않으면 Windows 3D 시작 관리자 대신 2D 슬레이트를 표시 됩니다. **참고:** .glb 자산으로 표시 되어야 합니다 "콘텐츠" 빌드 설정에서 앱을 실행 하기 전에 합니다.


![솔루션 탐색기에서는.glb을 선택 하 고 속성 섹션을 사용 하 여 빌드 설정에서 "콘텐츠"으로 표시 합니다](images/buildsetting-content-300px.png)<br>
*솔루션 탐색기에서는.glb을 선택 하 고 속성 섹션을 사용 하 여 빌드 설정에서 "콘텐츠"으로 표시 합니다*

### <a name="bounding-box"></a>경계 상자

필요에 따라 개체에 대 한 추가 버퍼 영역을 추가 하는 경계 상자를 사용할 수 있습니다. 경계 상자는 중심점 및 경계 상자의 가운데에서 각 축에서 가장자리 까지의 거리를 나타내는 익스텐트를 사용 하 여 지정 됩니다. 경계 상자에 대 한 단위는 1 단위에 매핑될 수 = 1 미터입니다. 경계 상자를 제공 하지 않으면 다음 하나를 자동으로 적합 개체의 메시에 합니다. 제공 된 경계 상자 모델 보다 작은 경우 다음 조정 됩니다 메시 맞지 않습니다.

경계 상자 특성에 대 한 지원을 MixedRealityModel 요소에 속성으로 Windows RS4 업데이트와 함께 제공 됩니다. 앱의 맨 위에 있는 경계 상자를 먼저 정의 하려면 매니페스트 uap6 스키마를 추가 하 고 해당 포함 ignorable 네임 스페이스로 합니다.

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
다음으로 MixedRealityModel 경계 상자를 정의 하려면 SpatialBoundingBox 속성 설정: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Unity를 사용 하 여

Unity를 사용 하 여 작업 하는 경우 프로젝트를 작성 하 고 응용 프로그램 매니페스트를 편집할 수 전에 Visual Studio에서 열릴 해야 합니다. 

>[!NOTE]
>3D launcher 빌드하고 Unity에서 새 Visual Studio 솔루션을 배포할 때 매니페스트에 다시 정의 해야 합니다.

## <a name="3d-deep-links-secondarytiles"></a>3D 딥 링크 (secondaryTiles)

> [!NOTE]
> 이 기능은 2018 년 4 월의 일부로 및 몰입 형 (VR) 헤드셋에 대 한 2017 Fall Creators Update (RS3)의 일부로 추가 된 HoloLens에 대 한 업데이트 (RS4). 응용 프로그램의 몰입 형 (VR) 헤드셋에서 10.0.16299 보다 크거나 같고 10.0.17125 HoloLens에 Windows SDK 버전을 대상으로 하는지 확인 합니다. 최신 Windows SDK를 찾을 수 있습니다 [여기](https://developer.microsoft.com/windows/downloads/windows-10-sdk)합니다.

>[!IMPORTANT]
>3D 딥 링크 (secondaryTiles) 2D UWP 앱 에서만 작동합니다. 그러나 만들 수 있습니다는 [3D 앱 시작 관리자](implementing-3d-app-launchers.md) Windows Mixed Reality 홈에서 전용 앱을 시작 합니다.

3D 모델에 앱을 배치 하는 기능을 추가 하 여 Windows Mixed Reality에 대 한 2D 응용 프로그램을 향상 시킬 수 있습니다 합니다 [홈 Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) 2D 앱 내 콘텐츠의 딥 링크와 마찬가지로 [2D 보조 타일](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) Windows 시작 메뉴에 있습니다. 예를 들어, 360 ° 사진 뷰어 응용 프로그램에 직접 연결 하거나 사용자가 작성자에 대 한 세부 정보 페이지가 열립니다는 자산의 컬렉션에서 3D 콘텐츠를 배치할 수 있도록 하는 360 ° photospheres를 만들 수 있습니다. 3D 콘텐츠를 사용 하 여 2D 응용 프로그램의 기능을 확장할 수는 몇 가지이 있습니다.

### <a name="creating-a-3d-secondarytile"></a>3D "secondaryTile" 만들기

혼합된 현실 모델을 만들 때 정의 하 여 "secondaryTiles"를 사용 하 여 응용 프로그램에서 3D 콘텐츠를 배치할 수 있습니다. 혼합된 현실 모델은 앱 패키지에서 3D 자산을 참조 하 고 필요에 따라 경계 상자를 정의 하 여 생성 됩니다. 

> [!NOTE]
> 전용 뷰를 내에서 "secondaryTiles" 만들기는 현재 지원 되지 않습니다.

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

개체에 대 한 추가 버퍼 영역을 추가 하는 경계 상자를 사용할 수 있습니다. 경계 상자는 중심점 및 경계 상자의 가운데에서 각 축에서 가장자리 까지의 거리를 나타내는 익스텐트를 사용 하 여 지정 됩니다. 경계 상자에 대 한 단위는 1 단위에 매핑될 수 = 1 미터입니다. 경계 상자를 제공 하지 않으면 다음 하나를 자동으로 적합 개체의 메시에 합니다. 제공 된 경계 상자 모델 보다 작은 경우 다음 조정 됩니다 메시 맞지 않습니다.

### <a name="activation-behavior"></a>활성화 동작

> [!NOTE]
> 이 기능은 지원 되는 Windows RS4 업데이트를 기준으로 합니다. 이 기능을 사용 하려는 경우 응용 프로그램 10.0.17125 보다 크거나 같은 경우 Windows SDK의 버전을 대상으로 하는 있는지 확인

사용자가이 선택할 때 어떻게 반응 하는지 제어 하는 3D secondaryTile의 정품 인증 동작을 정의할 수 있습니다. 이 혼합 현실에서 홈 purley 정보 또는 장식 된 3D 개체를 배치할 수입니다. 다음 활성화 동작 유형이 지원 됩니다.
1. Default: 앱이 활성화 사용자가 3D secondaryTile 선택
2. None: 사용자가 아무 일도 발생 하는 3D secondaryTile 및 앱을 선택 하는 경우 활성화 되지 않습니다.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>가져오기 및 기존 "secondaryTile"를 업데이트 하는 중

개발자는 다시 이전에 지정 된 속성을 포함 하는 해당 기존 보조 타일 목록을 가져올 수 있습니다. 속성 값을 변경 하 고 다음 updateasync ()를 호출 하 여 업데이트할 수도 있습니다.

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Windows Mixed Reality 사용자 인지 확인 합니다.

Windows Mixed Reality 헤드셋에서 뷰에 표시 되 면 3D 딥 링크 (secondaryTiles)만 만들 수 있습니다. Windows Mixed Reality 헤드셋에 보기 표시 되지 않습니다 하는 경우에 정상적으로이 진입점을 숨기 거 나 오류 메시지를 표시 하 여 처리 하는 것이 좋습니다. 쿼리하여 확인할 수 있습니다 [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)합니다.

## <a name="tile-notifications"></a>타일 알림

타일 알림을 현재 지원 하지 않는 3D 자산을 사용 하 여 업데이트를 전송 합니다. 즉, 개발자는 다음을 수행 하는 일을 할 수 없습니다.
* 푸시 알림
* 정기 폴링
* 예약 된 알림

특성 및 2D 타일에 사용 되는 방법 및 다른 자세한 타일 기능에 대 한 합니다 [UWP 앱 설명서에 대 한 타일](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)합니다.

## <a name="see-also"></a>참조

* [혼합된 현실 모델 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) 3D 앱 시작 관리자를 포함 합니다.
* [3D 앱 시작 관리자 디자인 지침](3d-app-launcher-design-guidance.md)
* [Windows Mixed Reality 집에서 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D 앱 시작 관리자 (Win32 앱)를 구현합니다.](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
