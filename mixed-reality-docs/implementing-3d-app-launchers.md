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
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="63766-104">3D 앱 시작 관리자 (UWP 앱)를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="63766-105">이 몰입 형 헤드셋에 대 한 2017 Fall Creators Update (RS3)의 일부로 추가 된 기능과 Windows 사용 하 여 HoloLens 지 10 2018 년 4 월 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="63766-106">응용 프로그램의 몰입 형 헤드셋에서 10.0.16299 보다 크거나 같고 10.0.17125 HoloLens에 Windows SDK 버전을 대상으로 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="63766-107">최신 Windows SDK를 찾을 수 있습니다 [여기](https://developer.microsoft.com/windows/downloads/windows-10-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="63766-108">합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 출발점 응용 프로그램을 시작 하기 전에 사용자가 이동 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="63766-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="63766-109">UWP 응용 프로그램에 만들면 Windows Mixed Reality 기본적으로, 앱은 앱의 로고를 사용 하 여 2D 슬레이트로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="63766-110">Windows Mixed Reality 환경을 개발, 3D 시작 관리자 응용 프로그램에 대 한 기본 2D launcher를 재정의 하려면 선택적으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="63766-111">일반적으로 3D 시작 관리자 앱 내부에서 활성화 될 때 기본 2D 시작 관리자는 기본 Windows Mixed Reality 홈에서 사용자를 사용 하는 몰입 형 응용 프로그램을 실행 하는 데 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="63766-112">만들 수도 있습니다는 [3D 딥 링크 (secondaryTile)](#3d-deep-links-secondarytiles) 2D UWP 앱 내에서 콘텐츠를 3D 실행 프로그램으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="63766-113">3D 앱 시작 관리자 만들기 프로세스</span><span class="sxs-lookup"><span data-stu-id="63766-113">3D app launcher creation process</span></span>

<span data-ttu-id="63766-114">3D 앱 시작 관리자를 작성 하는 방법은 3 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="63766-115">디자인 및 concepting</span><span class="sxs-lookup"><span data-stu-id="63766-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="63766-116">모델링 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="63766-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="63766-117">응용 프로그램 (이 문서)에 통합</span><span class="sxs-lookup"><span data-stu-id="63766-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="63766-118">3D 자산 사용 하 여 응용 프로그램 시작 관리자를 작성 해야 하는 대로 사용 해야 합니다 [Windows Mixed Reality 작성 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 호환성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="63766-119">이 제작 사양을 충족 하지 못한 자산 Windows Mixed Reality 홈에서 렌더링 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="63766-120">3D 시작 관리자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="63766-121">Visual Studio에서 새 프로젝트를 만든 경우 앱의 이름 및 로고를 표시하는 간단한 기본 타일이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="63766-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="63766-122">이 2D 바꾸려면 기본 타일 정의의 일부로 "MixedRealityModel" 요소를 포함 하도록 응용 프로그램의 앱 매니페스트를 편집 하는 사용자 지정 3D 모델을 사용 하 여 표현 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="63766-123">2D로 되돌리려면 시작 관리자 매니페스트에서 MixedRealityModel 정의 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="63766-124">XML</span><span class="sxs-lookup"><span data-stu-id="63766-124">XML</span></span>

<span data-ttu-id="63766-125">먼저 현재 프로젝트에서 앱 패키지 매니페스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="63766-126">기본적으로 매니페스트 Package.appxmanifest 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="63766-127">Visual Studio를 사용 하는 경우 다음 솔루션 뷰어에서 매니페스트를 마우스 오른쪽 단추로 클릭 하 고 선택 **소스 보기** 를 편집 하는 것에 대 한 xml을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="63766-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="63766-128">매니페스트의 맨 위에 있는 uap5 스키마를 추가 하 고 네임 스페이스를 무시할 수로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="63766-129">그런 다음 응용 프로그램에 대 한 기본 타일에서 "MixedRealityModel"를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

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

<span data-ttu-id="63766-130">MixedRealityModel 요소를 앱 패키지에 저장 된 3D 자산을 가리키는 파일 경로 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="63766-131">3 차원 모델.glb 파일 형식을 사용 하 여 배달 하 고에 대해 작성 하는 현재 합니다 [지침을 작성 하는 Windows Mixed Reality 3D 자산](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="63766-132">자산 앱 패키지에 저장 되어야 하며 애니메이션 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="63766-133">"Path" 매개 변수를 지정 하지 않으면 Windows 3D 시작 관리자 대신 2D 슬레이트를 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="63766-134">**참고:** .glb 자산으로 표시 되어야 합니다 "콘텐츠" 빌드 설정에서 앱을 실행 하기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="63766-135">![솔루션 탐색기에서는.glb을 선택 하 고 속성 섹션을 사용 하 여 빌드 설정에서 "콘텐츠"으로 표시 합니다](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="63766-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="63766-136">*솔루션 탐색기에서는.glb을 선택 하 고 속성 섹션을 사용 하 여 빌드 설정에서 "콘텐츠"으로 표시 합니다*</span><span class="sxs-lookup"><span data-stu-id="63766-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="63766-137">경계 상자</span><span class="sxs-lookup"><span data-stu-id="63766-137">Bounding box</span></span>

<span data-ttu-id="63766-138">필요에 따라 개체에 대 한 추가 버퍼 영역을 추가 하는 경계 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="63766-139">경계 상자는 중심점 및 경계 상자의 가운데에서 각 축에서 가장자리 까지의 거리를 나타내는 익스텐트를 사용 하 여 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="63766-140">경계 상자에 대 한 단위는 1 단위에 매핑될 수 = 1 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="63766-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="63766-141">경계 상자를 제공 하지 않으면 다음 하나를 자동으로 적합 개체의 메시에 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="63766-142">제공 된 경계 상자 모델 보다 작은 경우 다음 조정 됩니다 메시 맞지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="63766-143">경계 상자 특성에 대 한 지원을 MixedRealityModel 요소에 속성으로 Windows RS4 업데이트와 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="63766-144">앱의 맨 위에 있는 경계 상자를 먼저 정의 하려면 매니페스트 uap6 스키마를 추가 하 고 해당 포함 ignorable 네임 스페이스로 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="63766-145">다음으로 MixedRealityModel 경계 상자를 정의 하려면 SpatialBoundingBox 속성 설정:</span><span class="sxs-lookup"><span data-stu-id="63766-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="63766-146">Unity를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="63766-146">Using Unity</span></span>

<span data-ttu-id="63766-147">Unity를 사용 하 여 작업 하는 경우 프로젝트를 작성 하 고 응용 프로그램 매니페스트를 편집할 수 전에 Visual Studio에서 열릴 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="63766-148">3D launcher 빌드하고 Unity에서 새 Visual Studio 솔루션을 배포할 때 매니페스트에 다시 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="63766-149">3D 딥 링크 (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="63766-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="63766-150">이 기능은 2018 년 4 월의 일부로 및 몰입 형 (VR) 헤드셋에 대 한 2017 Fall Creators Update (RS3)의 일부로 추가 된 HoloLens에 대 한 업데이트 (RS4).</span><span class="sxs-lookup"><span data-stu-id="63766-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="63766-151">응용 프로그램의 몰입 형 (VR) 헤드셋에서 10.0.16299 보다 크거나 같고 10.0.17125 HoloLens에 Windows SDK 버전을 대상으로 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="63766-152">최신 Windows SDK를 찾을 수 있습니다 [여기](https://developer.microsoft.com/windows/downloads/windows-10-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="63766-153">3D 딥 링크 (secondaryTiles) 2D UWP 앱 에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="63766-154">그러나 만들 수 있습니다는 [3D 앱 시작 관리자](implementing-3d-app-launchers.md) Windows Mixed Reality 홈에서 전용 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="63766-155">3D 모델에 앱을 배치 하는 기능을 추가 하 여 Windows Mixed Reality에 대 한 2D 응용 프로그램을 향상 시킬 수 있습니다 합니다 [홈 Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) 2D 앱 내 콘텐츠의 딥 링크와 마찬가지로 [2D 보조 타일](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) Windows 시작 메뉴에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="63766-156">예를 들어, 360 ° 사진 뷰어 응용 프로그램에 직접 연결 하거나 사용자가 작성자에 대 한 세부 정보 페이지가 열립니다는 자산의 컬렉션에서 3D 콘텐츠를 배치할 수 있도록 하는 360 ° photospheres를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="63766-157">3D 콘텐츠를 사용 하 여 2D 응용 프로그램의 기능을 확장할 수는 몇 가지이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="63766-158">3D "secondaryTile" 만들기</span><span class="sxs-lookup"><span data-stu-id="63766-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="63766-159">혼합된 현실 모델을 만들 때 정의 하 여 "secondaryTiles"를 사용 하 여 응용 프로그램에서 3D 콘텐츠를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="63766-160">혼합된 현실 모델은 앱 패키지에서 3D 자산을 참조 하 고 필요에 따라 경계 상자를 정의 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="63766-161">전용 뷰를 내에서 "secondaryTiles" 만들기는 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

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

### <a name="bounding-box"></a><span data-ttu-id="63766-162">경계 상자</span><span class="sxs-lookup"><span data-stu-id="63766-162">Bounding box</span></span>

<span data-ttu-id="63766-163">개체에 대 한 추가 버퍼 영역을 추가 하는 경계 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="63766-164">경계 상자는 중심점 및 경계 상자의 가운데에서 각 축에서 가장자리 까지의 거리를 나타내는 익스텐트를 사용 하 여 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="63766-165">경계 상자에 대 한 단위는 1 단위에 매핑될 수 = 1 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="63766-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="63766-166">경계 상자를 제공 하지 않으면 다음 하나를 자동으로 적합 개체의 메시에 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="63766-167">제공 된 경계 상자 모델 보다 작은 경우 다음 조정 됩니다 메시 맞지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="63766-168">활성화 동작</span><span class="sxs-lookup"><span data-stu-id="63766-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="63766-169">이 기능은 지원 되는 Windows RS4 업데이트를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="63766-170">이 기능을 사용 하려는 경우 응용 프로그램 10.0.17125 보다 크거나 같은 경우 Windows SDK의 버전을 대상으로 하는 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="63766-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="63766-171">사용자가이 선택할 때 어떻게 반응 하는지 제어 하는 3D secondaryTile의 정품 인증 동작을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="63766-172">이 혼합 현실에서 홈 purley 정보 또는 장식 된 3D 개체를 배치할 수입니다.</span><span class="sxs-lookup"><span data-stu-id="63766-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="63766-173">다음 활성화 동작 유형이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63766-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="63766-174">Default: 앱이 활성화 사용자가 3D secondaryTile 선택</span><span class="sxs-lookup"><span data-stu-id="63766-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="63766-175">None: 사용자가 아무 일도 발생 하는 3D secondaryTile 및 앱을 선택 하는 경우 활성화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="63766-176">가져오기 및 기존 "secondaryTile"를 업데이트 하는 중</span><span class="sxs-lookup"><span data-stu-id="63766-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="63766-177">개발자는 다시 이전에 지정 된 속성을 포함 하는 해당 기존 보조 타일 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="63766-178">속성 값을 변경 하 고 다음 updateasync ()를 호출 하 여 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="63766-179">Windows Mixed Reality 사용자 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="63766-180">Windows Mixed Reality 헤드셋에서 뷰에 표시 되 면 3D 딥 링크 (secondaryTiles)만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="63766-181">Windows Mixed Reality 헤드셋에 보기 표시 되지 않습니다 하는 경우에 정상적으로이 진입점을 숨기 거 나 오류 메시지를 표시 하 여 처리 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="63766-182">쿼리하여 확인할 수 있습니다 [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="63766-183">타일 알림</span><span class="sxs-lookup"><span data-stu-id="63766-183">Tile notifications</span></span>

<span data-ttu-id="63766-184">타일 알림을 현재 지원 하지 않는 3D 자산을 사용 하 여 업데이트를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="63766-185">즉, 개발자는 다음을 수행 하는 일을 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63766-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="63766-186">푸시 알림</span><span class="sxs-lookup"><span data-stu-id="63766-186">Push Notifications</span></span>
* <span data-ttu-id="63766-187">정기 폴링</span><span class="sxs-lookup"><span data-stu-id="63766-187">Periodic Polling</span></span>
* <span data-ttu-id="63766-188">예약 된 알림</span><span class="sxs-lookup"><span data-stu-id="63766-188">Scheduled Notifications</span></span>

<span data-ttu-id="63766-189">특성 및 2D 타일에 사용 되는 방법 및 다른 자세한 타일 기능에 대 한 합니다 [UWP 앱 설명서에 대 한 타일](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="63766-190">참조</span><span class="sxs-lookup"><span data-stu-id="63766-190">See also</span></span>

* <span data-ttu-id="63766-191">[혼합된 현실 모델 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) 3D 앱 시작 관리자를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="63766-192">3D 앱 시작 관리자 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="63766-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="63766-193">Windows Mixed Reality 집에서 사용할 3D 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="63766-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="63766-194">3D 앱 시작 관리자 (Win32 앱)를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="63766-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="63766-195">Windows Mixed Reality 홈 탐색</span><span class="sxs-lookup"><span data-stu-id="63766-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
