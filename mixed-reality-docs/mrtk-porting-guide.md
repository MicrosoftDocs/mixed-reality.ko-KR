---
title: HoloLens 2에 대 한 앱 준비
description: HoloLens에 기존 앱이 있는 개발자를 목표로 (첫 번째 gen) 및/또는 이전 MRTK를 찾고 MRTK 버전 2 및 HoloLens 2로 이식 해야 합니다.
author: author:grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
keywords: Windows Mixed Reality MRTK MRTK 버전 2, HoloLens 2 테스트
ms.openlocfilehash: a5a329f69f5f9cc64666483adc92786ae8910b2f
ms.sourcegitcommit: 07773e094ace2e828e329bd55da759983be3b8c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/15/2019
ms.locfileid: "59605287"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>HoloLens 2에 대 한 기존 앱 준비

이 가이드 HoloLens 1 새 HoloLens 2 장치에 대 한 응용 프로그램 포트에 대 한 기존 Unity 앱 개발자를 위해 특별히 조정 됩니다. HoloLens 2 HoloLens 1 Unity 앱을 이식 하는 네 가지 주요 단계 있습니다. 아래 섹션에서는 각 단계에 대 한 정보를 자세히 설명 합니다. 

| 1단계 | 2단계 | 3단계 | 4단계 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 로고](images/visualstudio_logo.png) | ![Unity 로고](images/unity_logo.png)| ![Unity 아이콘](images/hololens2_icon.jpg) | ![MRTK 로고](images/MRTKIcon.jpg) |
| 최신 도구 다운로드 | Unity 프로젝트를 업데이트 합니다. | ARM에 대 한 컴파일 | MRTK v2로 마이그레이션

것 **좋습니다** , 이식 프로세스를 시작 하기 전에 개발자가 활용 하는 앱의 원래 상태 스냅숏을 저장 하려면 소스 제어 합니다. 또한 것이 좋습니다 *저장할* 프로세스 중 여러 지점에서 검사점 상태입니다. 또한 포트 프로세스 side by side 비교 가능 하도록 하려면 원래 앱의 다른 Unity 인스턴스가 있어야 하는 데 매우 유용할 수 있습니다. 

> [!NOTE]
> 이식 하기 전에 Windows Mixed Reality 개발에 대 한 설치 된 최신 도구 했는지를 확인 합니다. 대부분의 기존 HoloLens 개발자를 위한 주로 여기서 최신 Visual Studio 2017로 업데이트 하 고 적절 한 Windows SDK를 설치 합니다. 아래의 콘텐츠를 살펴보고 다른 Unity 버전 및 혼합 현실 도구 키트 버전 2에 추가 합니다.
>
> 자세한 내용은 참조 하십시오 [도구를 설치](install-the-tools.md)합니다.

## <a name="migrate-project-to-latest-version-of-unity"></a>Unity의 최신 버전으로 프로젝트 마이그레이션

Unity 응용 프로그램을 이식 하는 첫 번째 단계 Unity의 최신 버전에서 열 수 있습니다. 현재 두 가지 옵션에서 선택할 수 있습니다: Unity 2018.3.x 또는 Unity 2019.1.x 베타. 이러한 두 버전 간의 여러 장단점 있지만 significance의 주요 차이점은 ARM64 Unity 2019 +에 대 한 컴파일하는 기능을 합니다. 

모든 개발자 평가 [플러그 인 종속성](https://docs.unity3d.com/Manual/Plugins.html) 현재에 존재 하는 프로젝트 및 여부는 ARM64 용 이러한 Dll를 빌드할 수 있습니다. ARM64 용 강한 종속성 플러그 인을 빌드할 수 없습니다, 하나는 경우 Unity 2018 LTS를 활용 하 합니다. ARM64로 이식 일반적으로 필요한 경우 가능 하면 다양 한 성능 향상 ARM32 비교 하 여 장치에서 볼 수 있습니다.

또한 혼합 현실 Toolkit V2는 항상 Unity 2018 LTS에 대 한 지원을 보장 하지만 반드시 Unity 2019.x+의 모든 반복에 대 한 지원을 보장. 

| Unity 2018.3.x | Unity 2019.1+ |
|----------|-------------------|
| ARM32 빌드 지원 | ARM64 및 ARM32 빌드 지원 |
| 안정적인 LTS 릴리스 빌드 | 베타 안정성 |
| [.NET 스크립트 백 엔드](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *사용 되지 않음* | [.NET 스크립트 백 엔드](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *제거* |
| UNET 네트워킹 *사용 되지 않음* | UNET 네트워킹 *제거* |

## <a name="update-sceneproject-settings-in-unity"></a>Unity에서 장면/프로젝트 설정 업데이트

Unity를 업데이트 한 후 2018.3.x 또는 Unity 2019 +, 것이 좋습니다 최적의 결과 장치에 대 한 Unity에서 특정 설정을 업데이트 합니다. 이러한 설정은 아래에서 자세히 설명 되어 있습니다  **[Unity에 대 한 설정을 권장](Recommended-settings-for-Unity.md)** 합니다.

다시 반복 해야 하는 [스크립팅 하는.NET 백 엔드](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) Unity 2018 년에 되지 및 *제거* Unity 2019에 따라서 개발자가 고려해 야 로프로젝트를전환[ IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)합니다. 

> [!NOTE]
> IL2CPP 스크립팅 백 엔드 Unity에서 Visual studio에 빌드 시간이 더를 일으킬 수 있으며 개발자는 개발자 컴퓨터를 설정 해야 하므로 [IL2CPP 빌드 시간 최적화](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)합니다.

업데이트 된 Unity 버전으로 이동 하 고 나면 주요 변경 내용이 해결을 한 후 개발자는 빌드 및 테스트 HoloLens에서 자신의 현재 앱 (첫 번째 gen). 또한 만들고 소스 제어에 대 한 커밋을 저장 하는 적절 한 지점입니다. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>ARM 프로세서에 대 한 종속성/플러그 인 컴파일

HoloLens (첫 번째 gen) x86 응용 프로그램을 실행할 새 HoloLens 2 장치는 ARM 프로세서를 활용 하는 동안 프로세서. 따라서 기존 응용 프로그램 ARM을 지원 하도록 이식 해야 합니다. 앞에서 설명한 대로 Unity 2018 Unity 2019 + ARM64 앱에 대 한 컴파일 지원 하지만 ARM32 앱에 대 한 컴파일을 지원 합니다. 재료는 성능 차이 ARM64 응용 프로그램에 대 한 개발 하는 것은 일반적으로 기본 설정입니다. 그러나이 위해서는 모든 [플러그 인 종속성](https://docs.unity3d.com/Manual/Plugins.html) ARM64 용 빌드할 수도 있습니다. 

현재 응용 프로그램에서 모든 DLL 종속성을 검토 합니다. 종속성을 더 이상 필요한 경우에 프로젝트에서 제거 하려면이 좋습니다. 필요한 나머지 플러그 인에 대 한 Unity 프로젝트에 해당 ARM32 또는 ARM64 이진 파일을 수집 합니다. 

관련 Dll을 수집, 후 Unity에서 Visual Studio 솔루션을 구축 하 고 ARM 프로세서에 대 한 응용 프로그램을 작성할 수 있는지를 테스트 하려면 Visual Studio에서 ARM에 대 한 AppX를 컴파일하십시오. 소스 제어 솔루션에서 커밋 저장할 것은 권장이 다른 지점입니다. 

## <a name="update-to-mrtk-version-2"></a>MRTK 버전 2 업데이트

MRTK 버전 2는 두 HoloLens 지원 되는 Unity 기반으로 새 도구 키트 (첫 번째 gen) 및 HoloLens 2 하 고 있는 새 HoloLens 2 기능을 모두 추가한와 같은 상호 작용을 제공할 시각 추적 합니다.

### <a name="prepare-for-the-migration"></a>마이그레이션을 위한 준비

새 수집 하기 전에 [MRTK v2에 대 한 *.unitypackage 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)를 인벤토리 하는 것이 좋습니다 **MRTK v1을 사용 하 여 통합 하는 1) 사용자 지정 코드** 및 **2) 사용자 지정 코드 입력된 상호 작용 또는 UX 구성 요소에 대 한**합니다. 가장 일반적이 고 널리 알려진 충돌 새 MRTK v2 수집 혼합 현실 개발자에 대 한 입력 및 상호 작용에 포함 됩니다. 따라서 것이 좋습니다. 읽기 시작할 이해 하 고는 [MRTK v2 입력된 모델](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)합니다.

마지막으로, 새 MRTK v2 서비스 공급자 아키텍처를 구성 하려면 스크립트 및 관리자 장면에서 개체 모델에서 전환 되었습니다. 이 클리너 장면 계층 구조 및 아키텍처 모델 줄어들지만 학습 곡선 새 구성 프로필을 이해 하는 데 필요 합니다. 따라서 읽어보세요 합니다 [혼합 현실 도구 키트 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) 다양 한 중요 한 설정 및 프로필 응용 프로그램의 요구에 맞게 조정 하는 데 익숙해지고 시작 합니다. 

### <a name="perform-the-migration"></a>마이그레이션을 수행합니다

MRTK v2를 가져온 후 Unity 프로젝트에는 있을 많은 컴파일러 관련 오류입니다. 이 가장 일반적으로 인해 새 네임 스페이스 구조 및 새 구성 요소 이름입니다. 새 네임 스페이스 및 구성 요소에 스크립트를 수정 하 여 이러한 오류를 해결 하려면 계속 진행 합니다. 

특정 API 차이점과 HTK/MRTK MRTK 버전 2에 대 한 자세한 내용은 포팅 가이드를 참조 합니다 [MRTK 버전 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)합니다.

### <a name="best-practices"></a>모범 사례

- 표준 MRTK 셰이더 사용을 선호 합니다.
- 하나의 주요 작업을 변경 유형 (예: IMixedRealityFocusHandler IFocusable)
- 변경할 때마다 테스트 및 소스 제어를 활용 합니다.
- 기본값 (단추, 슬레이트, 등) MRTK UX를 사용 가능한 경우
- MRTK 파일을 직접 수정 하지 않는 것을 대신 MRTK 구성 요소에 대 한 래퍼를 만들려면
    - 이렇게 하면 이후 MRTK ingestions 및 업데이트에 대해 보호 됩니다.
- 검토 및 MRTK에 제공 된 샘플 장면을 탐색 (특히 *HandInteractionExamples.scene*)
- 대신 quads, colliders TextMeshPro 텍스트와 캔버스 기반 UI를 다시 작성

### <a name="testing-your-application"></a>응용 프로그램 테스트

이제는 HoloLens 2 구성 요소 및 기능 MRTK 버전 2에서에서 사용할 수 있는의 일부로 [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1), Unity에서 직접 직접 상호 작용을 시뮬레이션 하 고 직접 상호 작용 및 시선 추적에 대 한 새 Api에 대해 개발할 수 있습니다.  HoloLens 2 장치는 훌륭한 환경을 만드는 데 필요한 도구 및 설명서에 학습을 시작할 수 하나 이상 있지만. 또한 MRTK v2 HoloLens에 개발을 지원 (첫 번째 gen) 및 HoloLens에 어 탭을 통해 선택 계속 테스트할 수와 같은 기존 입력의 모델 즉, (첫 번째 gen) 장치. 

## <a name="updating-interaction-model-for-hololens-2"></a>HoloLens 2에 대 한 상호 작용 모델을 업데이트 하는 중입니다.

이식 및 HoloLens 2에 대 한 준비 앱을 만든 후 상호 작용 모델 및 홀로그램 디자인/배치를 업데이트 하는 것이 좋습니다. 준비가 되었습니다.
HoloLens에서 오는 (첫 번째 gen) 앱에 게이즈 및 커밋 상호 작용 모델을 사용 하 여 홀로그램 보기의 필드에 맞게 상대적으로 멀리 떨어진 곳입니다.

HoloLens 2에 대 한 가장 앱 디자인을 업데이트 하는 단계:
1.  MRTK 구성 요소: 사전 작업 당 MRTK v2를 추가한 경우 다양 한 구성 요소/있는 개의 스크립트가 있으며 활용 하 여 설계 되었으며 HoloLens 2에 대 한 최적화 합니다.

2.  상호 작용 모델: 상호 작용 모델을 업데이트 하는 것이 좋습니다.  대부분의 시나리오에서 게이즈에서 전환 하는 것이 좋습니다 하 고 실습을 커밋합니다.  연결할 arm에서 일반적으로 되 여 홀로그램을 사용 하 여 바늘으로 전환 먼 상호 작용 포인팅 광선의 결과 제스처를 선택 합니다.
참고: 핸 즈 프리 상호 작용 모델은 도구를 보유 하는 작업자와 같이 필요한 경우에 대 한 지침이 특정 디자인 하는 시나리오를 가지 있습니다. 

3.  홀로그램 배치: 실습 상호 작용 모델에서 전환한 후 이동 일부 홀로그램 가깝게 거의 상호 작용 잡기 제스처를 사용 하 여를 손으로 홀로그램와 직접 상호 작용 하는 것이 좋습니다.  직접 가져오기 또는 상호 작용에 한걸음 권장 홀로그램 유형은 대상 메뉴, 컨트롤, 단추 및 HoloLens 2 보기의 필드 위치와 방향을 잃기를 홀로그램을 검사 하는 경우 내에 맞는 더 작은 제공 합니다.
<br>
모든 앱 및 시나리오 다른 이며 지속적으로 구체화 하 고 디자인 지침 피드백에 따라 및 학습을 계속 게시할 예정입니다.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>앱에서 x86 ARM 이동 추가 학습

- 실행 되 고 ARM appx 번들을 빌드하거나 장치에 직접 배포할 수 있습니다 직선 Unity 앱은 간단 합니다.
문제는 Unity 앱은 네이티브 플러그 인을 사용 하는 경우에 제공 됩니다.  기본 플러그 인의 모든 VS2017를 업그레이드 하 고, ARM 및 ARM64, Unity 2019 다시 작성 해야 합니다.

- 하나의 앱 Unity에 대 한 AudioKinetic Wwise 플러그 인을 사용 하 고 사용 되는 버전을 UWP ARM 플러그 인 않은 키를 누릅니다. ARM에서 작동 하도록 응용 프로그램에 소리를 다시 작동 하는 데는 며칠이 걸렸습니다.

- 다른 경우에서 UWP/ARM 플러그 인을 앱에 필요한 플러그 인을 차단 하는 포트 및 HoloLens 2에서 실행 하는 기능에 대 한 없을 수도 있습니다.  플러그 인 공급자를 사용 하 여 engagement 차단을 해제 하 고 ARM를 지 원하는 데 필요할 수 있습니다.

- 셰이더는 minfloat (및 변형 min16float, minint, 등...) HoloLens 보다 HoloLen 2에서 다르게 동작할 수 있습니다 (첫 번째 gen). 특히 이러한 보장 "적어도 사용할 비트 수를 지정 된"입니다. Intel/Nvidia Gpu에서 이러한 이라고 할 처리할지를 32 비트입니다. ARM에에서 지정 된 비트 수가 실제로 적용 됩니다. 즉,는 실제로 이러한 숫자 수 범위가 적은 정밀도/HoloLens 2 HoloLens 보다 (첫 번째 gen).

- _Asm 지침 _asm 지침을 사용 하 여 모든 코드 다시 작성 해야 합니다. 즉, ARM에서 작동 하도록 표시 되지 않습니다.

- SIMD 명령 집합 ARM에서 지원 되지 않습니다. 이 xmmintrin.h, emmintrin.h, tmmintrin.h, 및 immintrin.h ARM에서 사용할 수 없는 같은 다양 한 헤더를 의미 합니다.

- 셰이더의 로드 된 또는 셰이더 것에 의존 하 여 첫 번째 그리기 호출 동안 ARM 실행 시 셰이더 컴파일러 셰이더 로드 시 없습니다 변경 되었습니다. 프레임 속도에 미치는 영향은 셰이더 얼마나 많은 컴파일이 필요에 따라 확실 될 수 있습니다. 이것은 다양 한 방법을 셰이더 처리/패키지/업데이트 HoloLens 2 vs HoloLens에 따라 다르게 이어야 합니다 (첫 번째 gen).

## <a name="see-also"></a>참조
* [MRTK 버전 2 사용 하 여 시작](mrtk-getting-started.md)
* [MRTK Version 2 HowTo](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [도구 설치](install-the-tools.md)
* [Unity에 대 한 권장된 설정](recommended-settings-for-unity.md)
* [혼합 현실에 대 한 성능 이해](understanding-performance-for-mixed-reality.md)

