---
title: HoloLens 2를 위한 기존 앱 준비
description: HoloLens(1세대) 및/또는 이전 MRTK에 기존 앱이 있고 MRTK 버전 2 및 HoloLens 2로 이식하려는 개발자를 위해 설계되었습니다.
author: grbury
ms.author: grbury
ms.date: 10/14/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, MRTK, MRTK version 2, HoloLens 2
ms.openlocfilehash: e1256cfaf9253a31161a836f75a90c64d17cf093
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438361"
---
# <a name="get-your-existing-app-ready-for-hololens-2"></a>HoloLens 2를 위한 기존 앱 준비

이 가이드는 HoloLens(1세대)용 기존 Unity 애플리케이션이 있는 개발자가 HoloLens 2 디바이스용 애플리케이션을 이식하는 것을 지원하기 위해 고안되었습니다. HoloLens(1세대) Unity 애플리케이션을 HoloLens 2로 이식하기 위한 핵심 단계에는 4가지가 있습니다. 

아래 섹션에서는 각 단계에 대한 정보를 자세히 설명합니다.

| 1단계 | 2단계 | 3단계 | 4단계 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 로고](images/visualstudio_logo.png) | ![Unity 로고](images/unity_logo.png)| ![Unity 아이콘](images/hololens2_icon.jpg) | ![MRTK 로고](images/MRTKIcon.jpg) |
| 최신 도구 다운로드 | Unity 프로젝트 업데이트 | ARM용 컴파일 | MRTK v2로 마이그레이션

필수 구성 요소:

개발자는 이식 프로세스를 시작하기 전에 소스 제어를 사용하여 애플리케이션의 원래 상태 스냅샷을 저장하는 것이 **좋습니다**. 또한 이 프로세스의 다양한 시점에서 검사점 상태를 *저장*하는 것이 좋습니다. 또한 이식 프로세스 동안 나란히 비교할 수 있도록 원래 애플리케이션의 다른 Unity 인스턴스를 유지하는 것이 매우 유용할 수 있습니다. 

> [!NOTE]
> 이식하기 전에 Windows Mixed Reality 개발을 위한 최신 도구를 설치했는지 확인합니다. 대부분의 기존 HoloLens 개발자의 경우 이 작업을 위해 최신 버전의 Visual Studio 2019로 업데이트하고 적절한 Windows SDK를 설치하게 됩니다. 이어지는 내용에서는 여러 다른 Unity 버전과 MRTK(Mixed Reality Toolkit) 버전 2를 좀 더 자세히 알아봅니다.
>
> 자세한 내용은 [도구 설치](install-the-tools.md)를 참조하세요.

## <a name="migrate-project-to-the-latest-version-of-unity"></a>최신 버전의 Unity로 프로젝트 마이그레이션

[MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)를 사용하는 경우 [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases)는 Unity 또는 MRTK가 획기적으로 변경되지 않는 가장 적합한 장기적인 지원 경로입니다. 또한 MRTK v2는 항상 Unity 2018 LTS를 지원하지만, Unity 2019.x 모두에 대한 지원이 반드시 보장되는 것은 아닙니다. 

[Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases)와 Unity 2019.x 간의 추가 차이점을 명확하게 하기 위해 이러한 두 버전 간의 장단점을 간략하게 설명하겠습니다. 주요 차이점은 Unity 2019에서 ARM64에 대한 컴파일 기능입니다. 

개발자는 현재 해당 프로젝트에 존재하는 [플러그 인 종속성](https://docs.unity3d.com/Manual/Plugins.html)을 평가하고 이러한 DLL을 ARM64용으로 빌드할 수 있는지 여부를 결정해야 합니다. ARM64용으로 강한 종속성 플러그 인을 빌드할 수 없는 경우 Unity 2018 LTS를 사용해야 합니다.


| Unity 2018 LTS | Unity 2019.x |
|----------|-------------------|
| ARM32 빌드 지원 | ARM64 및 ARM32 빌드 지원 |
| 안정적인 LTS 릴리스 빌드 | 베타 안정성 |
| [.NET 스크립팅 백 엔드](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *사용되지 않음* | [.NET 스크립팅 백 엔드](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *제거됨* |
| UNET 네트워킹 *사용되지 않음* | UNET 네트워킹 *사용되지 않음* |

## <a name="update-sceneproject-settings-in-unity"></a>Unity에서 장면/프로젝트 설정 업데이트

[Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) 또는 Unity 2019+로 업데이트한 후에는 디바이스에서 최적의 결과를 얻기 위해 Unity에서 특정 설정을 업데이트하는 것이 좋습니다. 이러한 설정은 **[Unity의 권장 설정](Recommended-settings-for-Unity.md)** 아래에서 자세히 설명되어 있습니다.

[.NET 스크립팅 백 엔드](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)가 Unity 2018에서 더 이상 사용되지 않으며 Unity 2019에서 *제거*되었음을 다시 반복해야 합니다. 개발자는 프로젝트를 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)로 전환하는 것을 고려해야 합니다. 

> [!NOTE]
> IL2CPP 스크립팅 백 엔드로 인해 Unity에서 Visual Studio로의 빌드 시간이 더 오래 걸릴 수 있으므로 개발자는 [IL2CPP 빌드 시간을 최적화](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)하도록 개발자 머신을 설정해야 합니다.
> 또한 대용량 자산(스크립트 파일 제외) 또는 지속적으로 변화하는 장면 및 자산을 포함하는 Unity 프로젝트에 맞게 [캐시 서버](https://docs.unity3d.com/Manual/CacheServer.html)를 설정하는 것도 유용할 수 있습니다. 프로젝트를 열 때 Unity는 정식 자산을 개발자 컴퓨터에 내부 캐시 형식으로 저장합니다. 따라서 항목이 수정되면 다시 가져온 후 다시 처리해야 합니다. 모든 개발자가 새 변경 내용을 로컬로 다시 가져오지 않고, 이 프로세스를 한 번 수행한 후 캐시 서버에 저장하고, 이후에 다른 개발자와 공유할 수 있으므로 시간을 절약할 수 있습니다.

업데이트된 Unity 버전으로 이동한 후에 주요 변경 내용을 처리한 다음, 개발자는 HoloLens(1세대)에서 현재 애플리케이션을 빌드하고 테스트해야 합니다. 또한 이때 소스 제어에 커밋을 만들고 저장하는 것이 좋습니다. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>ARM 프로세서에 대한 종속성/플러그 인 컴파일

HoloLens(1세대)는 x86 프로세서에서 애플리케이션을 실행하지만, HoloLens 2는 ARM 프로세서를 사용합니다. 따라서 ARM을 지원하도록 기존 HoloLens 애플리케이션을 이식해야 합니다. 앞에서 설명한 대로 Unity 2018 LTS는 ARM32 앱 컴파일을 지원하지만, Unity 2019.x는 ARM32 및 ARM64 앱 컴파일을 지원합니다. 구체적인 성능상 차이는 없으므로 ARM64 애플리케이션 개발이 일반적으로 선호됩니다. 그러나 이 경우 ARM64에 대해 모든 [플러그 인 종속성](https://docs.unity3d.com/Manual/Plugins.html)도 빌드해야 합니다. 

애플리케이션에서 모든 DLL 종속성을 검토하세요. 프로젝트에 더 이상 필요하지 않은 종속성은 모두 제거하는 것이 좋습니다. 필요한 나머지 플러그 인의 경우 해당 ARM32 또는 ARM64 이진 파일을 Unity 프로젝트로 수집합니다. 

관련 DLL을 수집한 후에는 Unity에서 Visual Studio 솔루션을 빌드한 후 Visual Studio에서 ARM용 AppX를 컴파일하여 ARM 프로세서용으로 애플리케이션을 빌드할 수 있는지 테스트합니다. 소스 제어 솔루션에서 커밋으로 애플리케이션을 저장하는 것도 유용합니다.

## <a name="update-to-mrtk-version-2"></a>MRTK 버전 2로 업데이트

[MRTK 버전 2](https://github.com/microsoft/MixedRealityToolkit-Unity)는 HoloLens(1세대) 및 HoloLens 2를 모두 지원하는 Unity 기반 새로운 툴킷입니다. 여기에는 새로운 HoloLens 2 기능(예: 손 상호 작용 및 시선 추적)도 추가되어 있습니다.

MRTK 버전 2를 사용하는 방법에 대한 자세한 내용은 다음을 참조하세요.
- [MRTK 방문 페이지](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
- [MRTK 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
- [MRTK 손](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSystem/HandTracking.html)
- [MRTK 시선 추적](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

### <a name="prepare-for-the-migration"></a>마이그레이션 준비

새 [MRTK v2용 *.unitypackage 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)을 삽입하기 전에 **1) MRTK v1과 통합되는 사용자 지정 코드** 및 **2) 입력 상호 작용 또는 UX 구성 요소에 대한 사용자 지정 코드** 인벤토리를 만드는 것이 좋습니다. MRTK v2를 수집하는 혼합 현실 개발자에게 가장 흔하게 나타나는 충돌은 입력 및 조작과 관련된 것입니다. 먼저 [MRTK v2 입력 모델](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)을 읽고 이해하는 것이 중요합니다.

마지막으로, 새 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)는 스크립트 및 장면 내 관리자 개체의 모델에서 구성 및 서비스 공급자 아키텍처로 전환되었습니다. 이로 인해 보다 명확한 장면 계층 구조 및 아키텍처 모델이 구현되지만, 새로운 구성 프로필을 이해하기 위한 학습 곡선이 필요합니다. 따라서 [Mixed Reality Toolkit 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)를 읽어보고 애플리케이션 요구에 맞게 조정해야 하는 중요한 설정 및 프로필에 익숙해지도록 합니다. 

### <a name="perform-the-migration"></a>마이그레이션 수행

[MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)를 가져온 후 Unity 프로젝트에서 많은 컴파일러 관련 오류가 나타날 수 있습니다. 새로운 네임스페이스 구조 및 새로운 구성 요소 이름 때문에 이러한 오류가 발생하는 것이 가장 일반적입니다. 새로운 네임스페이스 및 구성 요소에 맞게 스크립트를 수정하여 이러한 오류를 계속 해결합니다. 

HTK/MRTK와 MRTK v2 간의 특정 API 차이점에 대한 자세한 내용은 [MRTK 버전 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)의 이식 가이드를 참조하세요.

### <a name="best-practices"></a>모범 사례

- 기본적으로 [MRTK 표준 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)를 사용합니다.
- 한 번에 한 가지 중요 변경 유형 처리(예: IFocusable에서 [IMixedRealityFocusHandler](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler.html)로의 변경)
- 변경할 때마다 테스트하고 소스 제어를 사용합니다.
- 가능한 경우 기본 MRTK UX(단추, 슬레이트 등)를 사용합니다.
- MRTK 파일을 직접 수정하지 않고, MRTK 구성 요소에 대해 래퍼를 만듭니다.
    - 그러면 향후 MRTK 삽입 및 업데이트가 편리해집니다.
- MRTK에 제공된 샘플 장면(특히 *HandInteractionExamples.scene*)을 검토 및 탐색합니다.
- quads, colliders 및 TextMeshPro 텍스트를 사용하여 캔버스 기반 UI를 다시 빌드합니다.
- [깊이 버퍼 공유](camera-in-unity.md#sharing-your-depth-buffers-with-windows) 또는 [포커스 포인트 설정](focus-point-in-unity.md)을 사용하도록 설정합니다. 성능 향상을 위해 16비트 깊이 버퍼를 사용하는 것이 좋습니다. 색을 렌더링할 때 깊이도 렌더링하는지 확인합니다. Unity는 일반적으로 투명 및 텍스트 gameobject에 대한 깊이를 작성하지 않습니다. 
- 단일 패스 인스턴스 렌더링 경로를 설정합니다.
- [MRTK에 대한 HoloLens 2 구성 프로필](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html#hololens-2-profile)을 활용

### <a name="testing-your-application"></a>애플리케이션 테스트

MRTK 버전 2에서는, Unity에서 직접 손 상호 작용을 시뮬레이션하고, 손 상호 작용 및 시선 추적을 위한 API를 새로 개발할 수 있습니다. HoloLens 2 디바이스는 만족스러운 사용자 환경을 만드는 데 필요합니다. 더 잘 이해하기 위해 문서와 도구에 대한 연구를 시작하는 것이 좋습니다. [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)는 HoloLens(1세대)에서의 개발을 지원하며, 에어 탭을 통한 선택과 같은 기존 입력 모델을 HoloLens(1세대)에서 테스트할 수 있습니다. 

## <a name="updating-your-interaction-model-for-hololens-2"></a>HoloLens 2용 조작 모델 업데이트

애플리케이션을 HoloLens 2에 이식하고 준비한 경우 조작 모델 및 홀로그램 디자인 배치를 업데이트할 준비가 된 것입니다.
HoloLens(1세대)에서 해당 애플리케이션은 시야각에 맞도록 홀로그램이 비교적 멀리 떨어져 있는 응시 및 커밋 조작 모델을 사용할 확률이 높습니다.

HoloLens 2에 가장 적합하게 애플리케이션 디자인을 업데이트하는 단계는 다음과 같습니다.
1.  MRTK 구성 요소: 사전 작업에 따라, [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)를 추가한 경우 HoloLens 2에 맞게 디자인하고 최적화한 다양한 구성 요소/스크립트를 활용할 수 있습니다.

2.  조작 모델: 조작 모델을 업데이트하는 것이 좋습니다. 대부분의 시나리오에서는 응시 및 커밋에서 손 조작으로 전환하는 것이 좋습니다. 홀로그램이 일반적으로 손에 닿지 않는 경우 손으로 전환하면 원거리 조작 포인팅 레이 및 잡기 제스처가 표시됩니다.

3.  홀로그램 배치: 손 상호 작용 모델로 전환한 후에는 손으로 근거리 상호 작용 잡기 제스처를 사용하여 홀로그램을 좀 더 가깝게 옮겨서 직접 상호 작용할 수 있습니다. 직접 잡거나 조작하기 위해 좀 더 가깝게 이동하는 것이 바람직한 홀로그램 유형은 홀로그램을 잡고 조작할 때 HoloLens 2 시야각 내에 잘 맞는 작은 대상 메뉴, 컨트롤, 단추 및 더 작은 홀로그램입니다.
<br>
모든 애플리케이션 및 시나리오는 다르며, 피드백 및 지속적인 학습을 토대로 디자인 지침을 계속 조정한 후 게시할 예정입니다.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>x86에서 ARM으로 애플리케이션을 이동하는 방법에 대한 추가 주의 사항 및 학습

- 간단한 Unity 애플리케이션은 ARM 애플리케이션 번들을 빌드하거나 번들이 실행될 수 있도록 디바이스에 직접 배포할 수 있기 때문에 단순합니다. 일부 Unity 네이티브 플러그 인은 특정 개발 과제를 제시할 수 있습니다. 이 때문에 모든 Unity 네이티브 플러그 인을 Visual Studio 2019로 업그레이드한 다음, ARM용으로 다시 구축해야 합니다.

- 한 애플리케이션은 Unity AudioKinetic Wwise 플러그 인을 사용했으며, 해당 Unity 버전에 UWP ARM 플러그 인이 없었으므로 ARM에서 실행하기 위해 해당 애플리케이션으로 사운드 기능을 재작업하는 데 상당한 노력이 필요했습니다. 개발 계획에 필요한 모든 플러그 인이 Unity에 설치되어 있는지 확인해야 합니다.

- 일부 경우, 애플리케이션에 필요한 플러그 인에 UWP/ARM 플러그 인이 없을 수 있으며, 이 플러그 인은 애플리케이션을 HoloLens 2에서 이식하고 실행할 수 있는 기능을 차단합니다. 문제를 해결하고 ARM에 대한 지원을 제공하려면 플러그 인 공급 기업에게 문의하세요.

- 셰이더의 minfloat(및 min16float, minint 등의 변형)는 HoloLens 2에서 HoloLens(1세대)와는 다르게 동작할 수 있습니다. 특히, 적어도 지정된 수의 비트가 사용될 수 있습니다. Intel/Nvidia GPU에서는 대체적으로 32비트로 처리됩니다. ARM에서는 지정된 비트 수가 실제로 적용됩니다. 즉, 실제로 이러한 수는 HoloLens(1세대)의 경우보다 HoloLens 2에서 전체 자릿수 또는 범위가 더 적을 수 있습니다.

- _asm 명령은 ARM에서 작동하지 않는 것처럼 나타납니다. 즉, _asm 명령을 사용하는 모든 코드는 다시 작성해야 합니다.

- xmmintrin.h, emmintrin.h, tmmintrin.h 및 immintrin.h와 같은 다양한 헤더를 ARM에서 사용할 수 없으므로 SIMD 명령 세트는 ARM에서 지원되지 않습니다.

- ARM의 셰이더 컴파일러는 셰이더 로드 타임이 아니라, 셰이더가 로드되었거나 셰이더가 의존하는 대상이 변경된 이후의 첫 번째 그리기 호출 동안 실행됩니다. 프레임 속도에 미치는 영향은 컴파일해야 하는 셰이더 수에 따라 매우 확실하게 나타날 수 있습니다. 따라서 셰이더를 HoloLens 2와 HoloLens(1세대)에서 다른 방식으로 처리/패키지/업데이트해야 합니다.

## <a name="see-also"></a>참고 항목
* [도구 설치](install-the-tools.md)
* [MRTK 버전 2 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HTK API에서 MRTK API로](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
* [Unity 권장 설정](recommended-settings-for-unity.md)
* [혼합 현실의 성능 이해](understanding-performance-for-mixed-reality.md)

