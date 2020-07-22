---
title: 시작 자습서 - 2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 4f72f70b9eaac159f7d9231e61f23d18d708d0c7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306278"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포

## <a name="overview"></a>개요

이 자습서에서는 새 Unity 프로젝트를 만들어서 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK(Mixed Reality Toolkit)</a> 개발에 맞게 구성하고, MRTK를 가져오는 방법을 알아봅니다. Visual Studio에서 HoloLens 2 또는 에뮬레이터로 기본 Unity 샘플 장면을 구성, 빌드 및 배포하는 과정도 안내합니다.

## <a name="objectives"></a>목표

* HoloLens 개발을 위해 Unity를 구성하는 방법 알아보기
* HoloLens에 앱을 빌드하고 배포하는 방법 알아보기
* 공간 매핑 메시, 손 메시 및 프레임 속도 카운터 경험하기

## <a name="creating-the-unity-project"></a>Unity 프로젝트 만들기

**Unity Hub**를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표**를 클릭합니다.

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

드롭다운에서 [필수 구성 요소](mr-learning-base-01.md#prerequisites)에 지정된 Unity **버전**을 선택합니다.

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Unity 허브에서 특정 Unity 버전을 사용할 수 없으면 Unity의 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>(아카이브 다운로드)에서 설치를 시작할 수 있습니다.

Create a new project(새 프로젝트 만들기) 창에서 다음을 수행합니다.

* **Templates(템플릿)** 가 **3D**로 설정되어 있는지 확인합니다.
* 적합한 **Project Name(프로젝트 이름)** 을 입력합니다(예: _MRTK 자습서_).
* 프로젝트를 저장할 적합한 **Location(위치)** 을 선택합니다(예: _D:\MixedRealityLearning_).
* **Create(만들기)** 단추를 클릭하여 새 Unity 프로젝트를 만들고 시작합니다.

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다. 따라서 Unity 프로젝트를 드라이브의 루트에 가깝게 저장해야 합니다.

Unity에서 프로젝트가 만들어질 때까지 기다립니다.

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>빌드 플랫폼 전환

Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>TextMeshPro 필수 리소스 가져오기

Unity 메뉴에서 **Window**(창) > **TextMeshPro** > **Import TMP Essential Resources**(TMP 필수 리소스 가져오기)를 선택하여 Import Unity Package(Unity 패키지 가져오기) 창을 엽니다.

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> TextMeshPro 필수 리소스는 MRTK의 UI 요소에 필요합니다. 프로젝트에서 MRTK의 UI 요소를 사용할 계획이 없으면 이 단계를 건너뛰어도 됩니다.

## <a name="importing-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 가져오기

다음 Unity 사용자 지정 패키지를 다운로드합니다.

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

Unity 메뉴에서 **Assets(자산)**  > **Import Package(패키지 가져오기)**  > **Custom Package(사용자 지정 패키지)...** 를 차례로 선택하여 Import package(패키지 가져오기)... 창을 엽니다.

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

패키지 가져오기... 창에서 다운로드한 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage**를 선택하고 **열기** 단추를 클릭합니다.

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>Unity 프로젝트 구성

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. MRTK Project Configurator 설정 적용

Unity가 이전 섹션에서 패키지 가져오기를 완료하면 MRTK Project Configurator 창이 표시됩니다. 그렇지 않으면 Unity 메뉴로 이동하고 **Mixed Reality Toolkit** > **유틸리티** > **Unity 프로젝트 구성**을 선택하여 Configurator 창을 엽니다.

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

MRTK Project Configurator 창에서 **Modify Configurations**(구성 수정) 섹션을 펼치고, 모든 옵션이 선택되어 있는지 확인한 후 **적용** 단추를 클릭하여 설정을 적용합니다.

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a>2. 추가 프로젝트 설정 구성

Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

프로젝트 설정 창에서 **플레이어** > **XR 설정**을 선택하고 **+** 아이콘을 클릭한 후 Windows Mixed Reality를 선택하여 Windows Mixed Reality SDK를 추가합니다.

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다. 그렇지 않으면 Unity 메뉴를 사용하여 엽니다.

MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer**를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

프로젝트 설정 창에서 **플레이어** > **XR 설정**을 선택한 다음, **Depth Format**(수준 형식) 드롭다운을 사용하여 **16비트 수준**을 선택합니다.

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

프로젝트 설정 창에서 **플레이어** > **게시 설정**을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> '패키지 이름'은 앱의 고유 식별자입니다. 이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.

> [!TIP]
> '제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다. 개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.

## <a name="creating-and-configuring-the-scene"></a>장면 만들기 및 구성

Unity 메뉴에서 **파일** > **New Scene**(새 장면)을 선택하여 새 장면을 만듭니다.

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

Unity 메뉴에서 **Mixed Reality Toolkit** > **Add to Scene and Configure...** (장면에 추가 및 구성)를 차례로 선택하여 MRTK를 현재 장면에 추가합니다.

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

계층 구조 창에 **MixedRealityToolkit** 개체가 아직 선택된 상태로 검사기 창에서 **MixedRealityToolkit** 구성 프로필이 **DefaultMixedRealityToolkitConfigurationProfile**로 설정되어 있는지 확인합니다.

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> 일반적으로는 HoloLens용으로 개발할 때 DefaultHoloLens2ConfigurationProfile을 사용합니다. 하지만 이 자습서에서는 DefaultMixedRealityToolkitConfigurationProfile을 사용한 후, 다음 자습서인 [MRTK 프로필 구성](mr-learning-base-03.md)에서 DefaultHoloLens2ConfigurationProfile로 변경합니다.

Unity 메뉴에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 차례로 선택하여 Save Scene(장면 저장) 창을 엽니다.

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

Save Scene 창에서 프로젝트의 **Scenes(장면)** 폴더로 이동하여 장면에 적합한 이름(예: _시작_)을 지정하고, **Save(저장)** 단추를 클릭하여 장면을 저장합니다.

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>HoloLens 2에 애플리케이션 빌드

### <a name="1-build-the-unity-project"></a>1. Unity 프로젝트 빌드

Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.

Build Settings 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가한 다음, **Build(빌드)** 단추를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

Build Universal Windows Platform 창에서 빌드를 저장할 적합한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어 적합한 이름(예: _GettingStarted_)을 지정한 다음, **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. 애플리케이션 빌드 및 배포

빌드 프로세스가 완료되면 Unity는 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다. 폴더 내부를 탐색하고 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 잠시 시간을 내어 **[도구 설치](install-the-tools.md)** 설명서의 필수 구성 요소가 모두 있는지 확인합니다.

**마스터** 또는 **릴리스** 구성, **ARM64** 아키텍처 및 **디바이스**를 대상으로 선택하여 HoloLens용 Visual Studio를 구성합니다.

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> HoloLens(1세대)에 배포하는 경우 **x86** 아키텍처를 선택합니다.

> [!NOTE]
> HoloLens의 경우 일반적으로 ARM 아키텍처용으로 빌드합니다. 하지만 Unity 2019.3에는 Visual Studio에서 ARM을 빌드 아키텍처로 선택할 때 오류가 발생하는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>알려진 문제</strong></a>가 있습니다. 권장 해결 방법은 ARM64용으로 빌드하는 것입니다. 그렇게 할 수 없으면 **편집 > 프로젝트 설정 > 플레이어 > 기타 설정**으로 이동하여 **Graphics Jobs**(그래픽 작업)을 사용하지 않도록 설정합니다.

> [!NOTE]
> 디바이스가 대상 옵션으로 보이지 않으면, Visual Studio 솔루션의 시작 프로젝트를 IL2CPP 프로젝트에서 UWP 프로젝트로 변경해야 할 수 있습니다. 이렇게 하려면 솔루션 탐색기에서 YourProjectName(유니버설 Windows)을 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.

HoloLens를 컴퓨터에 연결한 다음, **디버그** > **디버그하지 않고 시작**을 선택하여 빌드하고 디바이스에 배포합니다.

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> 디바이스에 빌드하기 전에 디바이스가 [개발자 모드]에 있고 개발 머신과 페어링되어야 합니다. 이 두 단계는 모두 [이러한 지침](using-visual-studio.md)에 따라 완료할 수 있습니다.

> [!TIP]
> [HoloLens 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 테스트용 로드 [앱 패키지](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)를 만들 수도 있습니다.

디버그하지 않고 시작을 사용하면 Visual Studio 디버거를 연결하지 않고 디바이스에서 앱이 자동으로 시작됩니다.

**빌드 > 솔루션 배포**를 선택하여 앱을 자동으로 시작하지 않고 디바이스에 배포합니다.

> [!NOTE]
>앱에 Diagnostics 프로파일러가 보일 수 있으며, 음성 명령 **Toggle Diagnostics**를 사용하여 표시 유형을 전환할 수 있습니다. 앱을 변경할 때 성능에 영향을 줄 수 있는 시점을 파악하려면 개발하는 동안 프로파일러가 대부분 표시되도록 하는 것이 좋습니다. 예를 들어 HoloLens 앱은 [60FPS에서 지속적으로 실행](understanding-performance-for-mixed-reality.md)해야 합니다.

## <a name="congratulations"></a>축하합니다.

이제 첫 번째 HoloLens 앱을 배포했습니다. 연습을 진행하는 동안 HoloLens가 인식한 표면을 덮는 공간 매핑 메시가 표시됩니다. 또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다. 이러한 기능은 MRTK에 포함된 몇 가지 기본적인 부분입니다. 다음 자습서에서는 장면에 콘텐츠를 추가하여 HoloLens와 MRTK의 기능을 살펴봅니다.

[다음 자습서: 3. MRTK 프로필 구성](mr-learning-base-03.md)
