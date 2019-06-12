---
title: HoloLens 2를 위한 앱 준비
description: HoloLens(1세대) 및/또는 이전 MRTK에 기존 앱이 있으며 MRTK 버전 2 및 HoloLens 2로 이식하려는 개발자를 대상으로 합니다.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, MRTK, MRTK version 2, HoloLens 2
ms.openlocfilehash: 02dabd21b7a6add2ce53fe291a447e49057184d0
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270390"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>HoloLens 2를 위한 기존 앱 준비

이 가이드는 HoloLens(1세대)용 기존 Unity 앱이 있는 개발자가 새 HoloLens 2 디바이스용 애플리케이션을 이식하는 것을 지원하기 위해 특수하게 고안되었습니다. HoloLens(1세대) Unity 앱을 HoloLens 2로 이식하기 위한 핵심 단계에는 4가지가 있습니다. 아래 섹션에서는 각 단계에 대한 정보를 자세히 설명합니다. 

| 1단계 | 2단계 | 3단계 | 4단계 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 로고](images/visualstudio_logo.png) | ![Unity 로고](images/unity_logo.png)| ![Unity 아이콘](images/hololens2_icon.jpg) | ![MRTK 로고](images/MRTKIcon.jpg) |
| 최신 도구 다운로드 | Unity 프로젝트 업데이트 | ARM용 컴파일 | MRTK v2로 마이그레이션

개발자는 이식 프로세스를 시작하기 전에 소스 제어를 활용하여 앱의 원래 상태 스냅샷을 저장하는 것이 **좋습니다**. 또한 이 프로세스의 다양한 시점에서 검사점 상태를 *저장*하는 것이 좋습니다. 또한 이식 프로세스 동안 나란히 비교할 수 있도록 원래 앱의 다른 Unity 인스턴스를 유지하는 것이 매우 유용할 수 있습니다. 

> [!NOTE]
> 이식하기 전에 Windows Mixed Reality 개발을 위한 최신 도구를 설치했는지 확인합니다. 대부분의 기존 HoloLens 개발자의 경우 이 작업을 위해 최신 Visual Studio 2017로 업데이트하고 적절한 Windows SDK를 설치하게 됩니다. 아래의 내용은 여러 다른 Unity 버전과 Mixed Reality Toolkit 버전 2를 좀 더 자세히 알아봅니다.
>
> 자세한 내용은 [도구 설치](install-the-tools.md)를 참조하세요.

## <a name="migrate-project-to-latest-version-of-unity"></a>최신 버전의 Unity로 프로젝트 마이그레이션

MRTK v2를 사용하는 경우 Unity 2018 LTS는 Unity 또는 MRTK가 획기적으로 변경되지 않는 가장 적합한 장기적인 지원 경로가 될 것입니다.  위의 "도구 설치"에 따르면 권장되는 Unity 빌드는 Unity 2018.3으로, Unity 2018용 LTS 릴리스가 될 것입니다.  그뿐 아니라 MRTK v2는 항상 Unity 2018 LTS를 지원할 예정이지만 모든 Unity 2019.x를 반드시 지원할 것으로 보장할 수 없습니다. 

Unity 2018.3.x 또는 Unity 2019.1.x 간의 추가적인 차이점을 명확히 나타내기 위해 아래에서는 이러한 두 버전 간의 장단점을 대략적으로 설명합니다. 두 버전의 중대한 주요 차이점은 Unity 2019에서는 ARM64용 컴파일을 수행할 수 있도록 지원된다는 것입니다. 

개발자는 현재 해당 프로젝트에 존재하는[플러그 인 종속성](https://docs.unity3d.com/Manual/Plugins.html)과 이러한 DLL을 ARM64용으로 빌드할 수 있는지 여부를 평가해야 합니다. ARM64용으로 강한 종속성 플러그 인을 빌드할 수 없는 경우 Unity 2018 LTS를 활용해야 합니다.


| Unity 2018.3.x | Unity 2019.1+ |
|----------|-------------------|
| ARM32 빌드 지원 | ARM64 및 ARM32 빌드 지원 |
| 안정적인 LTS 릴리스 빌드 | 베타 안정성 |
| [.NET 스크립팅 백 엔드](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *사용되지 않음* | [.NET 스크립팅 백 엔드](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *제거됨* |
| UNET 네트워킹 *사용되지 않음* | UNET 네트워킹 *제거됨* |

## <a name="update-sceneproject-settings-in-unity"></a>Unity에서 장면/프로젝트 설정 업데이트

Unity 2018.3.x 또는 Unity 2019+로 업데이트한 후에는 디바이스에서 최적의 결과를 얻기 위해 Unity에서 특정 설정을 업데이트하는 것이 좋습니다. 이러한 설정은 **[Unity의 권장 설정](Recommended-settings-for-Unity.md)** 아래에서 자세히 설명되어 있습니다.

다시 말하지만 [.NET 스크립팅 백 엔드](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)는 Unity 2018에서 더 이상 사용되지 않고 Unity 2019에서 *제거*되었으므로 개발자는 프로젝트를 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)로 전환할 것을 강력히 고려해야 합니다. 

> [!NOTE]
> IL2CPP 스크립팅 백 엔드는 Unity에서 Visual Studio로의 빌드 시간이 더 오래 걸리도록 할 수 있으므로 개발자는 [IL2CPP 빌드 시간을 최적화](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)하도록 개발자 컴퓨터를 설정해야 합니다.
> 또한 대용량 자산(스크립트 파일 제외) 또는 지속적으로 변화하는 장면/자산을 포함하는 Unity 프로젝트에 맞게 [캐시 서버](https://docs.unity3d.com/Manual/CacheServer.html)를 설정하는 것도 유용할 수 있습니다. 프로젝트를 열 때 Unity는 정식 자산을 개발자 컴퓨터에 내부 캐시 형식으로 저장합니다. 따라서 항목이 수정되면 다시 가져온 후 다시 처리해야 합니다. 모든 개발자가 새 변경 내용을 로컬로 다시 가져오지 않고, 이 프로세스를 한 번 수행한 후 캐시 서버에 저장하고, 이후에 다른 개발자와 공유할 수 있으므로 시간을 절약할 수 있습니다.

업데이트된 Unity 버전으로 이동한 후에 주요 변경 내용을 처리한 다음, HoloLens(1세대)에서 현재 앱을 빌드하고 테스트해야 합니다. 또한 이때 소스 제어를 위한 커밋을 만들고 저장하는 것이 좋습니다. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>ARM 프로세서에 대한 종속성/플러그 인 컴파일

HoloLens(1세대)은 x86 프로세서에서 애플리케이션을 실행했지만, 새 HoloLens 2 디바이스는 ARM 프로세서를 활용합니다. 따라서 기존 애플리케이션을 ARM을 지원하도록 이식해야 합니다. 앞에서 설명한 대로 Unity 2018은 ARM32 앱 컴파일을 지원하지만, Unity 2019+는 ARM64 앱 컴파일을 지원합니다. 구체적인 성능상 차이는 없으므로 ARM64 애플리케이션 개발이 일반적으로 선호됩니다. 그러나 이 경우 ARM64에 대해 모든 [플러그 인 종속성](https://docs.unity3d.com/Manual/Plugins.html)도 빌드해야 합니다. 

현재 애플리케이션에서 모든 DLL 종속성을 검토하세요. 종속성이 더 이상 필요하지 않으면 프로젝트에서 제거하는 것이 좋습니다. 필요한 나머지 플러그 인의 경우 해당 ARM32 또는 ARM64 이진 파일을 Unity 프로젝트로 수집합니다. 

관련 DLL을 수집한 후에는 Unity에서 Visual Studio 솔루션을 빌드한 후 Visual Studio에서 ARM용 AppX를 컴파일하여 ARM 프로세서용으로 애플리케이션을 빌드할 수 있는지 테스트합니다. 이러한 목적으로 소스 제어 솔루션에서 커밋을 저장하는 것도 유용합니다. 

## <a name="update-to-mrtk-version-2"></a>MRTK 버전 2로 업데이트

MRTK 버전 2는 두 HoloLens(1세대) 및 HoloLens 2를 둘 다 지원하는 Unity 기반의 새 도구 키트로, 손 조작 및 시선 추적과 같은 새로운 HoloLens 2 기능이 모두 추가되었습니다.

### <a name="prepare-for-the-migration"></a>마이그레이션 준비

새 [MRTK v2용 *.unitypackage 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)을 삽입하기 전에 **1) MRTK v1과 통합되는 사용자 지정 코드** 및 **2) 입력 상호 작용 또는 UX 구성 요소에 대한 사용자 지정 코드** 인벤토리를 만드는 것이 좋습니다. 새 MRTK v2를 수집하는 혼합 현실 개발자에게 가장 흔하게 나타나는 충돌은 입력 및 조작과 관련된 것입니다. 따라서 먼저 [MRTK v2 입력 모델](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)을 읽고 이해하는 것이 중요합니다.

마지막으로, 새 MRTK v2는 스크립트 및 장면 내 관리자 개체에서 구성 및 서비스 공급자 아키텍처로 전환되었습니다. 이로 인해 보다 명확한 장면 계층 구조 및 아키텍처 모델이 구현되지만, 새로운 구성 프로필을 이해하기 위한 학습 곡선이 필요합니다. 따라서 [Mixed Reality Toolkit 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)를 읽어보고 애플리케이션 요구에 맞게 조정해야 하는 중요한 설정 및 프로필에 익숙해지도록 합니다. 

### <a name="perform-the-migration"></a>마이그레이션 수행

MRTK v2를 가져온 후 Unity 프로젝트에서 많은 컴파일러 관련 오류가 나타날 수 있습니다. 새로운 네임스페이스 구조 및 새로운 구성 요소 이름 때문에 이러한 오류가 발생하는 것이 가장 일반적입니다. 새로운 네임스페이스 및 구성 요소에 맞게 스크립트를 수정하여 이러한 오류를 계속 해결합니다. 

HTK/MRTK과 MRTK 버전 2 간의 특정 API 차이점에 대한 자세한 내용은 [MRTK 버전 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)의 이식 가이드를 참조하세요.

### <a name="best-practices"></a>최선의 구현 방법

- 기본적으로 MRTK 표준 셰이더 사용
- 한 번에 한 가지 중요 변경 유형 처리(예: IFocusable에서 IMixedRealityFocusHandler로의 변경)
- 변경할 때마다 테스트하고 소스 제어 활용
- 가능한 경우 기본 MRTK UX(단추, 슬레이트 등) 사용
- MRTK 파일을 직접 수정하지 않도록 하고, 대신 MRTK 구성 요소에 대해 래퍼 생성
    - 이를 통해 향후 MRTK 삽입 및 업데이트로부터 보호
- MRTK에 제공된 샘플 장면(특히 *HandInteractionExamples.scene*)을 검토 및 탐색
- 대신 quads, colliders 및 TextMeshPro 텍스트를 사용하여 캔버스 기반 UI 다시 빌드

### <a name="testing-your-application"></a>애플리케이션 테스트

이제 [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1)부터는 HoloLens 2 구성 요소 및 기능을 MRTK 버전 2에서 사용할 수 있으므로, Unity에서 직접 손 조작을 시뮬레이트하고, 손 조작 및 시선 추적을 위한 새 API를 개발할 수 있습니다.  HoloLens 2 디바이스는 유용한 환경을 만드는 데 필요하지만, 적어도 도구 및 설명서에서 학습을 시작할 수 있습니다. 또한 MRTK v2는 HoloLens(1세대)에서의 개발을 지원하므로, 에어 탭을 통한 선택과 같은 기존 입력 모델을 HoloLens(1세대) 디바이스에서 여전히 테스트할 수 있습니다. 

## <a name="updating-interaction-model-for-hololens-2"></a>HoloLens 2용 조작 모델을 업데이트

HoloLens 2를 앱을 이식하고 위해 준비한 경우 조작 모델 및 홀로그램 디자인/배치를 업데이트할 준비가 된 것입니다.
HoloLens(1세대)에서 가져온 앱은 시야각에 맞도록 홀로그램이 비교적 멀리 떨어져 있는 응시 및 커밋 조작 모델을 사용할 확률이 높습니다.

HoloLens 2에 가장 적합하게 앱 디자인을 업데이트하는 단계:
1.  MRTK 구성 요소: 사전 작업에 따라, MRTK v2를 추가한 경우 HoloLens 2에 맞게 디자인하고 최적화한 다양한 구성 요소/스크립트를 활용할 수 있습니다.

2.  조작 모델: 조작 모델을 업데이트하는 것이 좋습니다.  대부분의 시나리오에서는 응시 및 커밋에서 손 조작으로 전환하는 것이 좋습니다.  홀로그램이 일반적으로 손에 닿지 않는 경우 손으로 전환하면 먼 거리 조작 포인팅 레이 및 잡기 제스처가 표시됩니다.
참고: 태스크 작업자가 공구를 잡고 있는 경우와 같이 핸즈프리 조작 모델이 필요한 시나리오가 있으며 이러한 경우에 맞는 특정 디자인 지침이 있습니다. 

3.  홀로그램 배치: 손 조작 모델로 전환한 후에는 근거리 조작 잡기 제스처를 사용하여 손으로 홀로그램을 직접 조작하기 위해 일부 홀로그램을 좀 더 가깝게 이동하는 것이 좋습니다.  직접 잡거나 조작하기 위해 좀 더 가깝게 이동하는 것이 바람직한 홀로그램 유형은 홀로그램을 잡고 조작할 때 HoloLens 2 시야각 내에 잘 맞는 작은 대상 메뉴, 컨트롤, 단추 및 더 작은 홀로그램입니다.
<br>
모든 앱 및 시나리오는 다르며, 피드백 및 지속적인 학습을 토대로 디자인 지침을 계속 조정한 후 게시할 예정입니다.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>x86에서 ARM으로 앱을 이동하기 위한 추가 학습

- 직선 Unity 앱은 단순하므로 ARM appx 번들을 빌드하거나 디바이스에 직접 배포한 후 실행할 수 있습니다.
문제는 Unity 앱이 기본 플러그 인을 사용할 때 발생합니다.  모든 기본 플러그 인은 VS2017로 업그레이드하고, ARM용으로, Unity 2019를 사용할 때는 ARM64용으로 다시 빌드해야 합니다.

- 하나의 앱이 Unity용 AudioKinetic Wwise 플러그 인을 사용했으며 사용된 버전에는 UWP ARM 플러그 인이 없었습니다. 애플리케이션의 소리가 ARM에서 작동하는 데 며칠이 걸렸습니다.

- 또 다른 경우에서 앱 필수 플러그 인에 대해 UWP/ARM 플러그 인이 존재하지 않아 HoloLens 2에서 이식 및 실행하지 못할 수 있습니다.  ARM을 차단 해제하고 지원하기 위해 플러그 인 공급자와 계약해야 할 수 있습니다.

- 셰이더의 minfloat(및 min16float, minint 등의 변형)은 HoloLen 2에서 HoloLens(1세대)와는 다르게 동작할 수 있습니다. 특히, “적어도 지정된 수의 비트가 사용될 수 있습니다.” Intel/Nvidia GPU에서는 대체적으로 32비트로 처리됩니다. ARM에서는 지정된 비트 수가 실제로 적용됩니다. 즉, 실제로 이러한 수는 HoloLens(1세대)의 경우보다 HoloLens 2에서 전체 자릿수/범위가 더 적을 수 있습니다.

- _asm 명령은 ARM에서 작동하지 않는 것처럼 나타납니다. 즉, _asm 명령을 사용하는 모든 코드는 다시 작성해야 합니다.

- SIMD 명령 집합은 ARM에서 지원되지 않습니다. 즉, xmmintrin.h, emmintrin.h, tmmintrin.h 및 immintrin.h와 같은 다양한 헤더를 ARM에서 사용할 수 없습니다.

- ARM의 셰이더 컴파일러는 셰이더 로드 타임이 아니라, 셰이더가 로드되었거나 셰이더가 의존하는 대상이 변경된 이후의 첫 번째 그리기 호출 동안 실행됩니다. 프레임 속도에 미치는 영향은 컴파일해야 하는 셰이더 수에 따라 매우 확실하게 나타날 수 있습니다. 따라서 셰이더를 HoloLens 2와 HoloLens(1세대)에서 다른 방식으로 처리/패키지/업데이트해야 합니다.

## <a name="see-also"></a>참고 항목
* [MRTK 버전 2 시작](mrtk-getting-started.md)
* [MRTK 버전 2 HowTo](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [도구 설치](install-the-tools.md)
* [Unity 권장 설정](recommended-settings-for-unity.md)
* [혼합 현실의 성능 이해](understanding-performance-for-mixed-reality.md)

