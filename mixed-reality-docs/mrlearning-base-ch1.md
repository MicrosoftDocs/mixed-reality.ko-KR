---
title: 시작 자습서 - 2. 프로젝트 및 첫 번째 애플리케이션 초기화
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: d3392df9bfad5938d71d3a01999be51834a98a5d
ms.sourcegitcommit: 87aca9c2b73b0e83cb70a46443dcdb08c3621005
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77373450"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. 프로젝트 및 첫 번째 애플리케이션 초기화

## <a name="overview"></a>개요

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
이 첫 번째 자습서에서는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK(Mixed Reality Toolkit)</a>에서 제공해야 하는 기능 중 일부에 대해 알아보고, HoloLens 2용 첫 번째 애플리케이션을 시작하고 이를 디바이스에 배포합니다.

## <a name="objectives"></a>목표

* HoloLens 개발을 위한 Unity 구성
* 자산 가져오기 및 장면 설정
* 공간 매핑 메시, 손 메시 및 프레임 속도 카운터 시각화

## <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 기본 C# 프로그래밍 기능
* [개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!IMPORTANT]
> 이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.

## <a name="create-new-unity-project"></a>새 Unity 프로젝트 만들기

**Unity Hub**를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표**를 클릭합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

위의 [필수 구성 요소](#prerequisites) 섹션에 지정된 Unity 버전을 선택합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

Create a new project(새 프로젝트 만들기) 창에서 다음을 수행합니다.

* **Templates(템플릿)** 가 **3D**로 설정되어 있는지 확인합니다.
* 적합한 **Project Name(프로젝트 이름)** 을 입력합니다(예: _MRTK 자습서_).
* 프로젝트를 저장할 적합한 **Location(위치)** 을 선택합니다(예: _D:\MixedRealityLearning_).
* **Create(만들기)** 단추를 클릭하여 새 Unity 프로젝트를 만들고 시작합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다. Unity는 이러한 제한의 영향을 받으며, 파일 경로가 255자를 초과하면 컴파일이 실패할 수 있습니다. 따라서 Unity 프로젝트를 드라이브의 루트에 최대한 가깝게 저장하는 것이 좋습니다.

Unity에서 프로젝트가 만들어질 때까지 기다립니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality를 위한 Unity 프로젝트 구성

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

이 섹션에서는 빌드 플랫폼을 전환하고, 가상 현실과 공간 인식을 사용하도록 설정합니다.

### <a name="1-switch-build-platform"></a>1. 빌드 플랫폼 전환

Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2. 가상 현실 사용

> [!NOTE]
> 양안식 비전, 즉 각 눈에 대해 다른 이미지 렌더링을 사용하도록 설정하므로 가상 현실을 사용하도록 설정하는 것은 혼합 현실 및 확대된 현실 헤드셋에도 적용됩니다.

Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

Project Settings 창에서 **Player(플레이어)**  > **XR Settings(XR 설정)** 를 차례로 선택하여 XR Settings를 펼칩니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

XR Settings에서 **Virtual Reality Supported(가상 현실 지원됨)** 확인란을 선택하여 가상 현실을 사용하도록 설정한 다음, **+** 아이콘을 클릭하고 **Windows Mixed Reality**를 선택하여 Windows Mixed Reality SDK를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

Unity에서 SDK 추가가 완료될 때까지 기다립니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

Unity에서 SDK 추가가 완료되면 다음과 같이 XR Settings를 최적화합니다.

* Windows Mixed Reality **Depth Format(깊이 형식)** 을 **16-bit depth(16비트 깊이)** 로 설정합니다.
* Windows Mixed Reality **Enable Depth Sharing(깊이 공유 사용)** 확인란을 선택합니다.
* 스테레오 **Rendering Mode(렌더링 모드)\*** 를 **Single Pass Instanced**로 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> Windows Mixed Reality용 Unity를 최적화하는 방법에 대해 자세히 알아보려면 [Unity 추천 설정](recommended-settings-for-unity.md) 설명서를 참조할 수 있습니다.

### <a name="3-enable-spatial-perception"></a>3. 공간 인식 사용

> [!NOTE]
> 공간 인식을 사용하면 Windows Mixed Reality 디바이스에서 공간 매핑 메시를 시각화할 수 있습니다.

Project Settings(프로젝트 설정) 창에서 **Player(플레이어)**  > **Publishing Settings(게시 설정)** 를 차례로 선택하여 Publishing Settings를 펼칩니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

Publishing Settings에서 **Capabilities(기능)** 섹션까지 아래로 스크롤하고 **SpatialPerception** 확인란을 선택합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

Publishing Settings 창을 닫습니다.

## <a name="import-textmesh-pro-essential-resources"></a>TextMesh Pro 필수 리소스 가져오기

> [!NOTE]
> Mixed Reality Toolkit의 UI 요소에 필요하므로 이 패키지를 가져옵니다.

Unity 메뉴에서 **Window(창)**  > **TextMeshPro** > **Import TMP Essential Resources(TMP 필수 리소스 가져오기)** 를 차례로 선택합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 가져오기

다음 Unity 사용자 지정 패키지를 다운로드합니다.

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.2.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage)

Unity 메뉴에서 **Assets(자산)**  > **Import Package(패키지 가져오기)**  > **Custom Package(사용자 지정 패키지)...** 를 차례로 선택하여 Import package(패키지 가져오기)... 창을 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

Import package... 창에서 다운로드한 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage**를 선택하고 **Open(열기)** 단추를 클릭합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit용 Unity 프로젝트 구성

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

패키지를 가져오면 MRTK Project Configurator(MRTK 프로젝트 구성기) 창이 표시됩니다. 그렇지 않으면 Unity 메뉴에서 **Mixed Reality Toolkit** > **Utilities(유틸리티)**  > **Configure Unity Project(Unity 프로젝트 구성)** 를 차례로 선택하여 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

MRTK Project Configurator 창에서 **Modify Configurations(구성 수정)** 섹션을 펼치고, **Enable MSBuild for Unity(Unity용 MSBuild 사용)** 확인란을 <u>선택 취소</u>하고, 다른 모든 옵션이 선택되었는지 확인한 다음, **Apply(적용)** 단추를 클릭하여 해당 설정을 적용합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> Unity용 MSBuild는 사용할 SDK 중 일부만 지원할 수 있으며, 사용하도록 설정된 후에 이를 사용하지 않도록 설정하는 것이 어려울 수 있습니다. 따라서 Unity용 MSBuild를 사용하지 않는 것이 좋습니다.

## <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 구성
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

Unity 메뉴에서 **Mixed Reality Toolkit** > **Add to Scene and Configure(장면에 추가 및 구성)...** 를 차례로 선택하여 Mixed Reality Toolkit를 현재 장면에 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

Hierarchy(계층 구조) 창에서 MixedRealityToolkit 개체를 선택한 상태로 검사기 창에서 Mixed Reality Toolkit 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

Unity 메뉴에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 차례로 선택하여 Save Scene(장면 저장) 창을 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

Save Scene 창에서 프로젝트의 **Scenes(장면)** 폴더로 이동하여 장면에 적합한 이름(예: _시작_)을 지정하고, **Save(저장)** 단추를 클릭하여 장면을 저장합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>디바이스로 애플리케이션 빌드

### <a name="1-build-the-unity-project"></a>1. Unity 프로젝트 빌드

Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.

Build Settings 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가한 다음, **Build(빌드)** 단추를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

Build Universal Windows Platform 창에서 빌드를 저장할 적합한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어 적합한 이름(예: _GettingStarted_)을 지정한 다음, **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. 애플리케이션 빌드 및 배포

빌드 프로세스가 완료되면 Unity에서 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다. 폴더 내부를 탐색하고 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 [도구 설치](install-the-tools.md) 설명서에서 지정한 대로 모든 필수 구성 요소가 설치되어 있는지 확인합니다.

Visual Studio에서 **마스터** 또는 **릴리스** 구성, **ARM** 아키텍처 및 **디바이스**를 대상으로 선택하여 HoloLens 2를 구성합니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

HoloLens 2를 컴퓨터에 연결합니다.

> [!IMPORTANT]
> 디바이스에 빌드하기 전에 디바이스가 [개발자 모드]에 있고 개발 머신과 페어링되어야 합니다. 이 두 단계는 모두 [이러한 지침](using-visual-studio.md)에 따라 완료할 수 있습니다.

마지막 단계는 **디버그** > **디버깅하지 않고 시작**을 차례로 선택하여 빌드하고 디바이스에 배포하는 것입니다.

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

이러한 지침에서는 HoloLens 2 디바이스에 배포한다고 가정하지만, [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 [사이드로드용 앱 패키지](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)를 만들 수도 있습니다.

[디버깅하지 않고 시작]을 선택하면 빌드 성공 시 애플리케이션이 디바이스에서 즉시 시작되지만, 디버거가 연결되지 않고 정보가 Visual Studio에 표시되지 않습니다. 따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.

애플리케이션을 자동으로 시작하지 않고 디바이스에 배포하려면 빌드 > 솔루션 배포를 차례로 선택합니다.

## <a name="congratulations"></a>축하합니다.

<!-- TODO: Consider cleanup and adding in app screenshots -->
이제 첫 번째 HoloLens 2 애플리케이션을 배포했습니다. 연습을 진행하면서 HoloLens 2에서 인식한 모든 표면이 포함된 공간 매핑 메시가 표시됩니다. 또한 손을 추적하기 위한 손 및 손가락의 표시기와 애플리케이션 성능을 감시하기 위한 프레임 속도 카운터가 표시됩니다. 이러한 기능은 Mixed Reality Toolkit과 함께 기본적으로 포함되어 있는 기본적인 기능 중 일부에 불과합니다. 다음 자습서에서는 더 많은 콘텐츠와 대화형 작업을 장면에 추가하여 HoloLens 2 및 Mixed Reality Toolkit의 기능을 완벽하게 살펴볼 수 있습니다.

> [!NOTE]
> 앱에서 진단 프로파일러를 확인할 수 있습니다. **Toogle Diagnostics** 음성 명령을 사용하여 표시 유형을 전환할 수 있습니다. 그러나 일반적으로 개발 중에 프로파일러를 항상 표시하여 앱의 변경이 성능에 영향을 줄 수 있는 시기를 파악하는 것이 좋습니다. 예를 들어 HoloLens 2 애플리케이션은 [60FPS로 계속 실행](understanding-performance-for-mixed-reality.md)해야 합니다.

[다음 자습서: 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 도구 키트 구성](mrlearning-base-ch2.md)
