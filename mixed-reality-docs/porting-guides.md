---
title: 포팅 가이드
description: 기존 몰입 형 응용 프로그램을 Windows Mixed Reality로 이식 하는 방법을 설명 하는 단계별 연습.
author: ChimeraScorn
ms.author: cwhite
ms.date: 10/02/2018
ms.topic: article
keywords: 포트, 포팅, unity, 미들웨어, 엔진, UWP
ms.openlocfilehash: ece478f6bc8f43fc75eb8271096cdec37c41dced
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387758"
---
# <a name="porting-guides"></a>포팅 가이드

> [!NOTE]
> HoloLens 2에 대 한 추가 지침은 [곧](index.md#news-and-notes)제공 될 예정입니다.

Windows 10에는 몰입 형 및 holographic 헤드셋에 대 한 지원이 직접 포함 되어 있습니다. Oculus Rift 또는 HTC Vive와 같은 다른 장치에 대 한 콘텐츠를 빌드한 경우 이러한 콘텐츠는 운영 체제의 플랫폼 API 위에 있는 라이브러리에 종속 됩니다. Windows Mixed Reality에 기존 콘텐츠를 가져오는 경우에는 Windows Api에 이러한 다른 Sdk를 사용 하는 방법의 대상을 변경 해야 합니다. [Mixed reality 용 Windows 플랫폼 api](https://docs.microsoft.com/uwp/api/Windows.Perception) 는 UWP (유니버설 Windows 플랫폼) 앱 모델 에서만 작동 합니다. 따라서 앱이 UWP에 대해 아직 빌드되지 않은 경우 UWP로 포팅 하는 작업은 포팅 환경에 포함 됩니다.

## <a name="porting-overview"></a>포팅 개요

개략적인 수준에서 다음은 기존 콘텐츠 포팅에 관련 된 단계입니다.
1. **PC에서 Windows 10의 작성자 업데이트 (16299)를 실행 하 고 있는지 확인 합니다.** 이러한 빌드는 혼합 현실 개발에 가장 안정적이 아니므로 Insider Skip에서 preview 빌드를 수신 하는 것이 더 이상 권장 되지 않습니다.
2. **최신 버전의 그래픽 또는 게임 엔진으로 업그레이드 합니다.** 게임 엔진은 Windows 10 SDK 버전 10.0.15063.0 (4 월 2017에 릴리스된) 이상을 지원 해야 합니다.
3. **미들웨어, 플러그 인 또는 구성 요소를 업그레이드 합니다.** 앱에 구성 요소가 있는 경우 최신 버전으로 업그레이드 하는 것이 좋습니다. 최신 버전의 가장 일반적인 플러그 인은 UWP를 지원 합니다.
4. **중복 된 sdk에 대 한 종속성을 제거**합니다. 콘텐츠를 대상으로 하는 장치에 따라 Windows Api를 대상으로 지정할 수 있도록 해당 SDK (예: SteamVR)를 제거 하거나 조건적으로 컴파일해야 합니다.
5. **빌드 문제를 해결 합니다.** 이때 포팅 연습은 앱, 엔진 및 구성 요소 종속성에 따라 다릅니다.

## <a name="common-porting-steps"></a>일반적인 포팅 단계

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>일반적인 1 단계: 적절 한 개발 하드웨어가 있는지 확인

[도구 설치](install-the-tools.md#for-immersive-vr-headset-development) 페이지에 권장 되는 개발 하드웨어가 나열 됩니다.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>일반 2 단계: 최신 Windows 10 flight로 업그레이드

Windows Mixed Reality 플랫폼은 아직 활성 개발 중 이며 가장 효과적으로 "Windows 참가자가 빠르게" 비행 하는 것이 좋습니다. Windows 항공편에 대 한 액세스 권한을 받으려면 [Windows 참가자 프로그램에 참여](https://insider.windows.com/)해야 합니다.
1. [Windows 10 크리에이터 스 업데이트](https://www.microsoft.com/software-download/windows10) 설치
2. Windows 참가자 프로그램에 [참여](https://insider.windows.com/) 합니다.
3. [개발자 모드](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) 사용
4. 설정--> 업데이트 & 보안 섹션을 통해 [Windows Insider Fast flight](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) 로 전환 합니다.

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>일반적인 3 단계: 최신 버전의 Visual Studio로 업그레이드
* Visual Studio 2019 [의 도구 설치 페이지를](install-the-tools.md#installation-checklist) 참조 하세요.

### <a name="common-step-4-be-ready-for-the-store"></a>일반적인 4 단계: 스토어 준비
* 즉, WACK ( [Windows 앱 인증 키트](https://developer.microsoft.com/windows/develop/app-certification-kit) )를 조기에 자주 사용 합니다.
* [이식성 분석기](https://docs.microsoft.com/dotnet/standard/portability-analyzer) 사용 ([다운로드](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>일반 5 단계: 올바른 어댑터 선택
* 두 개의 Gpu가 있는 노트북 같은 시스템에서 [올바른 어댑터를 대상](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)으로 합니다. 이는 ID3D11Device가 명시적 또는 암시적으로 (미디어 파운데이션) 해당 기능에 대해 생성 되는 기본 DirectX 앱 뿐만 아니라 Unity 앱에도 적용 됩니다.

## <a name="unity-porting-guidance"></a>Unity 포팅 지침

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity 1 단계: 일반적인 포팅 단계 수행

모든 일반적인 단계를 수행 합니다. #3 단계에서 **Unity를 사용한 게임 개발** 워크 로드를 선택 합니다. 아래 지침에서 최신 버전의 Unity를 설치 하므로 Unity 편집기의 선택적 구성 요소를 선택 취소할 수 있습니다.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity 2 단계: Windows MR 지원을 통해 Unity의 최신 공용 빌드로 업그레이드
1. 혼합 현실 지원을 통해 [Unity의 최신 권장 공용 빌드](install-the-tools.md) 를 다운로드 합니다.
2. 시작 하기 전에 프로젝트 복사본 저장
3. 포팅의 포팅에서 제공 되는 [설명서](https://docs.unity3d.com/Manual/UpgradeGuides.html) 를 검토 합니다.
4. 자동 API 업데이트 프로그램을 사용 하기 위한 Unity 사이트의 [지침](https://docs.unity3d.com/Manual/APIUpdater.html) 을 따르세요.
5. 프로젝트를 실행 하기 위해 수행 해야 하는 추가 변경 내용이 있는지 확인 하 고 나머지 오류와 경고를 사용 하 여 작업 합니다. 참고: 사용자가 의존 하는 미들웨어가 있는 경우 해당 미들웨어를 업데이트 해야 할 수 있습니다 (아래 3 단계의 자세한 내용 참조).

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity 3 단계: 미들웨어를 최신 버전으로 업그레이드

모든 Unity 업데이트를 사용 하 여 게임 또는 응용 프로그램이 종속 된 하나 이상의 미들웨어 패키지를 업데이트 해야 할 가능성이 있습니다. 또한 모든 미들웨어의 최신 버전에 있으면 이식 프로세스의 나머지 부분에서 성공 가능성이 높아집니다. 대부분의 미들웨어 패키지에는 UWP (유니버설 Windows 플랫폼에 대 한 지원이 최근에 추가 되었으며 최신 버전으로 업그레이드 하면 해당 작업을 활용할 수 있습니다.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity 4 단계: 유니버설 Windows 플랫폼에서 실행할 응용 프로그램 대상 (UWP)

도구를 설치한 후에는 유니버설 Windows 앱으로 앱을 실행 해야 합니다.
* Unity에서 제공 하는 [단계별 연습](https://unity3d.com/partners/microsoft/porting-guides) 을 참조 하세요. Windows MR에 대 한 최신 LTS 릴리스 (모든 20xx 릴리스)를 유지 해야 합니다.
* UWP 개발 리소스에 대 한 자세한 내용은 [Windows 10 게임 개발 가이드](https://docs.microsoft.com/windows/uwp/gaming/e2e)를 참조 하세요.
* Unity는 계속 해 서 IL2CPP 지원을 개선 하 고 있습니다. IL2CPP를 사용 하면 일부 UWP 포트를 훨씬 쉽게 만들 수 있습니다. 현재 .Net scripting 백 엔드를 대상으로 하는 경우 IL2CPP 백엔드를 활용 하기 위해를 변환 하는 것이 좋습니다.

참고: 응용 프로그램에 스트림에서의 match와 같은 장치 관련 서비스에 대 한 종속성이 있는 경우이 단계에서 사용 하지 않도록 설정 해야 합니다. 나중에 Windows에서 제공 하는 것과 동일한 서비스에 연결할 수 있습니다.

### <a name="unity-step-5-deprecated"></a>Unity 5 단계: Mapi

5 단계가 더 이상 필요 하지 않습니다. 단계 인덱싱이 동일 하 게 유지 되도록 여기에 남겨 둡니다.

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Unity 6 단계: Windows Mixed Reality 하드웨어 설정 가져오기
1. 모던 헤드셋 설정 [의 단계 검토](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. [Windows Mixed reality 시뮬레이터를 사용 하](using-the-windows-mixed-reality-simulator.md) 고 [windows mixed Reality 홈을 탐색](navigating-the-windows-mixed-reality-home.md) 하는 방법을 알아봅니다.

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity 7 단계: Windows Mixed Reality에서 실행할 응용 프로그램을 대상으로 합니다.
1. 먼저 특정 VR SDK와 관련 된 다른 모든 라이브러리 지원을 제거 하거나 조건부로 컴파일해야 합니다. 이러한 자산은 Windows Mixed Reality와 같이 다른 VR Sdk와 호환 되지 않는 방식으로 프로젝트의 설정 및 속성을 변경 하는 경우가 많습니다.
    * 예를 들어 프로젝트가 SteamVR SDK를 참조 하는 경우 Windows 스토어 빌드 대상으로 내보낼 때 이러한 prefabs 및 스크립트 API 호출을 제외 하도록 프로젝트를 업데이트 해야 합니다.
    * 다른 VR Sdk를 조건부로 제외 하기 위한 구체적인 단계는 곧 제공 될 예정입니다.
2. Unity 프로젝트에서 [Windows 10 SDK를 대상으로 합니다](holograms-100.md#target-windows-10-sdk) .
3. 각 장면에 대해 [카메라를 설정 합니다](holograms-100.md#chapter-2---setup-the-camera) .

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity 8 단계: 스테이지를 사용 하 여 바닥에 콘텐츠를 저장 합니다.

광범위 한 [환경 규모](coordinate-systems.md)에서 혼합 현실 환경을 빌드할 수 있습니다.

통합 된 **환경을**이식 하는 경우 Unity가 **고정** 된 추적 공간 종류로 설정 되었는지 확인 해야 합니다.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

이를 통해 Unity의 세계 좌표계를 설정 하 여 [고정 된 참조 프레임](coordinate-systems.md#spatial-coordinate-systems)을 추적할 수 있습니다. 고정 추적 모드에서 카메라의 기본 위치 바로 앞에 있는 편집기에 배치 된 콘텐츠 (앞으로-Z)는 앱이 시작 될 때 사용자 앞에 표시 됩니다. 사용자가 연결 된 원본을 recenter Unity의 XR를 호출할 수 있습니다 [. Recenter 메서드입니다.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

**대규모 환경이** 나 **공간 규모의 경험**을 이식 하는 경우 층에 상대적인 콘텐츠를 배치 합니다. 사용자의 층을 사용 하는 이유는 사용자의 정의 된 최고 수준 원점 및 선택적 대화방 경계를 나타내는 **[공간 단계](coordinate-systems.md#spatial-coordinate-systems)** 를 처음 실행 하는 동안 설정 하는 것입니다. 이러한 환경에서는 Unity가 **RoomScale** 추적 공간 형식으로 설정 되어 있는지 확인 해야 합니다. RoomScale가 기본값 이지만, 사용자가 보정 한 방에서 컴퓨터를 이동 하는 경우를 명시적으로 설정 하 고 true로 설정 하 여 사용자가 컴퓨터를 이동 하는 경우를 확인 하는 것이 좋습니다.

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

앱이 RoomScale 추적 공간 유형을 성공적으로 설정 하면 y = 0 평면에 배치 된 콘텐츠가 바닥에 표시 됩니다. (0, 0, 0)의 원점은 사용자가 대화방을 설치 하는 동안 구현 하는 바닥의 특정 위치가 되며,-Z는 설치 중에 전달 된 정방향 방향을 나타냅니다.

그런 다음 스크립트 코드에서 TryGetGeometry 메서드를 호출할 수 있습니다. XR 형식으로 경계 다각형을 가져오고 TrackedArea 경계 형식을 지정 합니다. 사용자가 경계 (꼭 짓 점 목록)를 정의 하는 경우 사용자에 게 **공간 확장 환경을** 제공 하 여 사용자가 만든 장면을 살펴볼 수 있다는 것을 알 수 있습니다.

사용자가 접근 하면 시스템에서 자동으로 경계를 렌더링 합니다. 앱은 경계 자체를 렌더링 하기 위해이 다각형을 사용할 필요가 없습니다.

자세한 내용은 [Unity의 좌표계](coordinate-systems-in-unity.md) 페이지를 참조 하세요.

일부 응용 프로그램에서는 사각형을 사용 하 여 상호 작용을 제한 합니다. 가장 큰 것으로 인 한 사각형 검색은 UWP API 또는 Unity에서 직접 지원 되지 않습니다. 아래에 연결 된 예제 코드는 추적 되는 범위 내에서 사각형을 찾는 방법을 보여 줍니다. 추론을 기반으로 하므로 최적의 솔루션을 찾지 못할 수 있지만 결과는 일반적으로 예상과 일치 합니다. 알고리즘의 매개 변수를 조정 하 여 처리 시간을 더 정확 하 게 찾을 수 있습니다. 이 알고리즘은 Unity의 5.6 preview MRTP 버전을 사용 하는 혼합 현실 도구 키트의 포크에 있습니다. 공개적으로 사용할 수 없습니다. 2017.2 이상 버전의 Unity에서 코드를 직접 사용할 수 있어야 합니다. 이 코드는 가까운 장래에 현재 MRTK로 포팅 됩니다.

[GitHub에 있는 코드의 zip 파일](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) 중요 한 파일:
* Asset/HoloToolkit/Stage/Scripts/StageManager-사용 예제
* Asset/HoloToolkit/Stage/Scripts/LargestRectangle-알고리즘 구현
* 자산/HoloToolkit-단위 테스트/편집기/단계/LargestRectangleTest 알고리즘의 간단한 테스트

결과의 예는 다음과 같습니다.

![결과 예제](images/largestrectangle-400px.jpg)

알고리즘은 Daniel Smilkov의 블로그를 기반으로 합니다. [다각형의 가장 큰 사각형](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Unity 9 단계: 입력 모델을 통해 작업

기존 HMD를 대상으로 하는 각 게임 또는 응용 프로그램에는 처리 하는 일련의 입력, 환경에 필요한 입력 형식 및 해당 입력을 가져오기 위해 호출 하는 특정 Api가 있습니다. Windows Mixed Reality에서 제공 되는 입력을 활용할 수 있도록 간단 하 고 간단 하 게 만드는 데 투자 했습니다.
1. Windows Mixed Reality에서 입력을 노출 하는 방법 및 응용 프로그램의 용도에 매핑되는 방법에 대 한 자세한 내용은 **[Unity의 입력 포팅 가이드](input-porting-guide-for-unity.md)** 를 참조 하세요.
2. Unity의 VR-SDK 입력 API를 사용할 것인지, MR 특정 입력 API를 사용할 것인지를 선택 합니다. 일반 입력. GetButton/Input. Getbutton Api는 현재 [Oculus 입력](https://docs.unity3d.com/Manual/OculusControllers.html) 및 [openvr 입력](https://docs.unity3d.com/Manual/OpenVRControllers.html)에 사용 되는 Unity VR 앱에서 사용 됩니다. 앱에서 동작 컨트롤러에 대해 이러한 Api를 이미 사용 하 고 있는 경우이 경로를 사용 하는 것이 가장 쉬운 경로입니다. 입력 관리자에서 단추와 축을 다시 매핑해야 하기만 하면 됩니다.
    * 일반적으로는 XR Api를 사용 하 여 Unity에서 동작 컨트롤러 데이터에 액세스할 수 있습니다. GetButton/Input. Getbutton Api 또는 MR 특정 UnityEngine. (이전에는 Unity 5.6의 UnityEngine. XR 네임 스페이스)
    * 게임 패드 및 동작 컨트롤러를 결합 하는 [도구 키트의 예제](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) 를 참조 하세요.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity 10 단계: 성능 테스트 및 튜닝

Windows Mixed Reality는 하이엔드 게임 Pc부터 광범위 한 시장 메인스트림 Pc까지 광범위 한 장치 클래스에서 사용할 수 있습니다. 대상 시장에 따라 응용 프로그램에 사용할 수 있는 계산 및 그래픽 예산에 상당한 차이가 있습니다. 이 포팅 연습을 수행 하는 동안 프리미엄 PC를 활용 하 고 앱에 사용할 수 있는 중요 한 계산 및 그래픽 예산이 있을 수 있습니다. 앱을 더 광범위 한 사용자가 사용할 수 있도록 하려는 경우 [대상으로 지정 하려는 대표 하드웨어](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)에서 앱을 테스트 하 고 프로 파일링 해야 합니다.

[Unity](https://docs.unity3d.com/Manual/Profiler.html) 및 [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) 에는 성능 프로파일러가 포함 되며, [Microsoft](understanding-performance-for-mixed-reality.md) 및 [Intel](https://software.intel.com/articles/vr-content-developer-guide) 은 성능 프로 파일링 및 최적화에 대 한 지침을 게시 합니다. [혼합 현실 성능을 이해](understanding-performance-for-mixed-reality.md)하는 데 사용할 수 있는 성능에 대 한 광범위 한 설명이 있습니다. Unity에 [대 한 성능 권장 사항](performance-recommendations-for-unity.md)에서 unity에 대 한 구체적인 정보를 제공 합니다.

## <a name="see-also"></a>참조
* [Unity 입력 포팅 가이드](input-porting-guide-for-unity.md)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [혼합 현실 성능 이해](understanding-performance-for-mixed-reality.md)
* [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)
* [UWP 용 Unity에 Xbox Live 지원 추가](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
