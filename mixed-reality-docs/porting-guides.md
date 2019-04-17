---
title: 포팅 가이드
description: Windows Mixed Reality로 기존 몰입 형 응용 프로그램을 이식 하는 방법을 설명 하는 단계별 연습입니다.
author: ChimeraScorn
ms.author: cwhite
ms.date: 10/02/2018
ms.topic: article
keywords: 포트, 이식, unity, 미들웨어, 엔진을 UWP
ms.openlocfilehash: a4a8c78f1c45fd8e3b85a767d139bae9f67540e0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602180"
---
# <a name="porting-guides"></a>포팅 가이드

> [!NOTE]
> HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.

Windows 10 holographic 및 몰입 형 헤드셋에 대 한 지원이 직접 포함 됩니다. HTC 라고 외치 Oculus 리프트 등 다른 장치에 대 한 콘텐츠를 만든 경우 이러한 종속성이 있는 운영 체제의 플랫폼 API 위에 존재 하는 라이브러리입니다. Windows Mixed Reality를 기존 콘텐츠를 가져오는 Windows Api에 이러한 다른 Sdk의 사용 대상 다시 지정 해야 합니다. 합니다 [혼합된 현실에 대 한 Windows 플랫폼 Api](https://docs.microsoft.com/uwp/api/Windows.Perception) 유니버설 Windows 플랫폼 (UWP) 앱 모델 에서만 작동 합니다. 따라서 앱은 아직 빌드하지 uwp, UWP로 포팅 됩니다 이식 환경의 일부입니다.

## <a name="porting-overview"></a>포팅 개요

대략적으로, 다음은 기존 콘텐츠를 이식 하는 단계입니다.
1. **PC에서 Windows 10 Fall Creators Update (16299)를 실행 하 되 고 있는지 확인 하십시오.** 더 이상 좋습니다 Insider 건너뛰기 미리 링에서 빌드 미리 보기를 받는 해당 빌드가 혼합된 현실 개발을 위한 가장 안정적인 수 없습니다.
2. **그래픽 또는 게임 엔진의 최신 버전으로 업그레이드 합니다.** 게임 엔진 (2017 년 4 월에에서 릴리스됨) 하는 10.0.15063.0 버전의 Windows 10 SDK를 지원 해야 합니다. 이상.
3. **모든 미들웨어, 플러그 인 또는 구성 요소를 업그레이드 합니다.** 모든 구성 요소를 포함 하는 앱을 경우 최신 버전으로 업그레이드 하는 것이 좋습니다. 최신 버전의 가장 일반적인 플러그 인을 사용 하면 UWP에 대 한 지원이 있습니다.
4. **중복 된 Sdk에 대 한 종속성을 제거**합니다. 제거 하거나 조건부로 컴파일할 해당 SDK (예: SteamVR) out 해야 콘텐츠를 대상으로 하는 장치에 따라 Windows Api를 대신 대상 수 있도록 합니다.
5. **빌드 문제를 해결 합니다.** 이 시점에서 이식 실습 응용 프로그램, 프로그램 엔진 및 구성 요소 종속성이 있는에 따라 다릅니다.

## <a name="common-porting-steps"></a>이식 하는 일반적인 단계

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>일반적인 단계 1: 올바른 개발 하드웨어 했는지 확인

합니다 [도구를 설치](install-the-tools.md#for-immersive-vr-headset-development) 페이지 개발 권장된 하드웨어를 나열 합니다.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>일반적인 2 단계: Windows 10의 최신 비행으로 업그레이드

Windows Mixed Reality 플랫폼은 아직 활발 하 게 개발 하 고 가장 효과적인 방법은 좋습니다 "Windows 참가자 Fast" 비행에 합니다. Windows 항공편에 대 한 액세스를 가지려면 해야 [Windows 참가자 프로그램 참여](https://insider.windows.com/)합니다.
1. 설치는 [Windows 10 크리에이터 스 업데이트](https://www.microsoft.com/software-download/windows10)
2. [조인](https://insider.windows.com/) Windows 참가자 프로그램입니다.
3. 사용 하도록 설정 [개발자 모드](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. 으로 전환 합니다 [항공편 Windows Insider 빠른](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) 설정을 통해 업데이트 및 보안 섹션을-->

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>일반적인 3 단계: Visual Studio의 최신 빌드로 업그레이드
* 참조 하세요 [도구를 설치](install-the-tools.md#installation-checklist) Visual Studio 2017에서 페이지

### <a name="common-step-4-be-ready-for-the-store"></a>일반적인 4 단계: 저장소 준비
* 사용 하 여 [Windows 앱 인증 키트](https://developer.microsoft.com/windows/develop/app-certification-kit) (즉, WACK) 조기에 그리고 자주!
* 사용 하 여 [Portability Analyzer](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([다운로드](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>일반적인 5 단계: 올바른 어댑터를 선택 합니다.
* 두 개의 Gpu 사용 하 여 notebook 같은 시스템 [올바른 어댑터를 대상](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)합니다. 이 Unity 앱 뿐만 아니라 앱에 적용 됩니다 네이티브 DirectX는 ID3D11Device 만들어지는, 명시적 또는 암시적으로 (Media Foundation), 해당 기능에 대 한 합니다.

## <a name="unity-porting-guidance"></a>Unity 포팅 참고 자료

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity 1 단계: 일반적인 포팅 단계

모든 일반적인 단계를 수행 하십시오. 3 단계에서 선택 합니다 **Unity 사용한 게임 개발** 워크 로드. 있으므로 아래 지침에서 Unity의 최신 버전을 설치할 수 있습니다 Unity 편집기 선택적 구성 요소를 선택 취소할 수 있습니다.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity 2 단계: Windows MR 지원과 Unity의 최신 공용 빌드를로 업그레이드
1. 최신 다운로드 [Unity의 공용 빌드를 권장](install-the-tools.md) 혼합된 현실 지원 합니다.
2. 시작 하기 전에 프로젝트의 복사본을 저장 합니다.
3. 검토 합니다 [설명서](https://docs.unity3d.com/Manual/UpgradeGuides.html) 이식에서 Unity에서 사용할 수 있습니다.
4. 수행 합니다 [지침](https://docs.unity3d.com/Manual/APIUpdater.html) 해당 자동 API 업데이트를 사용 하 여 Unity의 사이트에서
5. 확인 및 실행 프로젝트를 가져올 수 있도록 해야 하는 추가 변경 내용이 있는지 확인 하 고 나머지 오류 및 경고를 통해 작동 합니다. 참고: 미들웨어에 종속 된 경우 (자세한 내용은 아래 3 단계에서) 시작 하는 미들웨어를 업데이트 해야 합니다.

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity 3 단계: 미들웨어를 최신 버전으로 업그레이드

모든 Unity 업데이트를 사용 하 여 게임 또는 응용 프로그램에 의존 하는 하나 이상의 미들웨어 패키지를 업데이트 해야 할 가능성이 있습니다. 또한 최신 버전의 모든 미들웨어를 사용 하 여 이식 프로세스의 나머지 부분 성공 가능성을 증가 합니다. 여러 미들웨어 패키지에 대 한 유니버설 Windows 플랫폼 (UWP) 지원을 추가 최근에 및 최신 버전으로 업그레이드 하면 해당 작업을 활용할 수 있습니다.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity 4 단계: 유니버설 Windows 플랫폼 (UWP)에서 실행 되도록 응용 프로그램 대상

도구를 설치한 후 앱을 유니버설 Windows 앱으로 실행 해야 합니다.
* 수행 합니다 [자세한 단계별 연습에서는](https://unity3d.com/partners/microsoft/porting-guides) Unity가 제공 합니다. 최신 LTS 릴리스 (20xx.4 릴리스)에 대 한 Windows MR에서 유지할지 note 하십시오.
* 잠시 살펴 자세한 UWP 개발 리소스에 대 한 합니다 [Windows 10 게임 개발 가이드](https://docs.microsoft.com/windows/uwp/gaming/e2e)합니다.
* Unity IL2CPP 지원을 개선 하기 위해 계속 되도록를 note 하십시오. IL2CPP 쉽게 일부 UWP 포트 현저 하 게 합니다. 현재.Net 스크립팅 백 엔드를 대상으로 지정 하면, IL2CPP 백 엔드를 대신 활용 하 여 변환 하는 것이 좋습니다.

참고: 응용 프로그램에서 스트림을 수행 하는 일치와 같은 장치 특정 서비스에 대 한 모든 종속성이이 단계에서 비활성화 해야 합니다. 나중에 Windows에서 제공 하는 해당 서비스 연결할 수 있습니다.

### <a name="unity-step-5-deprecated"></a>Unity 5 단계: (사용 되지 않음)

5 단계는 더 이상 필요 합니다. 동일 하 게 유지 단계의 인덱싱 있도록 여기 유지는 것입니다.

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Unity 6 단계: Windows Mixed Reality 하드웨어 설정 가져오기
1. 단계를 검토 [몰입 형 헤드셋 설치](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. 에 대 한 자세한 [Windows Mixed Reality 시뮬레이터를 사용 하 여](using-the-windows-mixed-reality-simulator.md) 고 [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity 단계 7: Windows Mixed Reality를 실행 하도록 응용 프로그램 대상
1. 첫째, 제거 하거나 조건부로 컴파일할 특정 VR SDK 관련 다른 라이브러리 지원 하세요. 이러한 자산 Windows Mixed Reality 같은 다른 VR Sdk와 호환 되지 않는 방식으로 프로젝트 속성과 설정에 자주 변경 됩니다.
    * 예를 들어, 프로젝트 SteamVR SDK에서 참조 하는 경우에 Windows 스토어 빌드 대상에 대 한 내보낼 때 이러한 prefabs 및 스크립트 API 호출을 제외 하도록 프로젝트를 업데이트 해야 합니다.
    * 조건에 따라 다른 VR Sdk를 제외 하기 위한 구체적인 단계는 곧 제공 됩니다.
2. Unity 프로젝트에서 [대상 Windows 10 SDK](holograms-100.md#target-windows-10-sdk)
3. 각 장면에 대 한 [카메라 설정](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity 8 단계: 단계를 사용 하 여 현장에서 콘텐츠를 배치 합니다.

혼합 현실 환경에서 다양 한 범위의 빌드할 수 있습니다 [눈금 환경을](coordinate-systems.md)합니다.

이식 하려는 경우는 **장착 규모 경험**, Unity로 설정 되어 있어야 합니다 **고정** 공간 형식을 추적:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

이 Unity의 세계 좌표 시스템 추적을 설정 합니다 [고정 참조 프레임](coordinate-systems.md#spatial-coordinate-systems)합니다. 고정 추적 모드에서 콘텐츠 편집기 카메라의 기본 위치 바로 앞에 배치 (앞으로-Z) 앱이 시작 되 면 사용자 앞에 표시 됩니다. Unity의 호출 수, 사용자의 원본 둘러싸기의 장착 [xr 하이 있습니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드.

이식 하려는 경우는 **고정 규모 경험** 또는 **방 규모 환경**, 있습니다 됩니다 수 배치 콘텐츠는 floor를 기준으로 합니다. 사용자에 대 한 이유를 사용 하 여 floor 합니다  **[공간 단계](coordinate-systems.md#spatial-coordinate-systems)** 층 원본 및 선택적인 공간이 경계 정의 된 사용자를 나타내는, 설정 하는 동안 먼저 실행 합니다. Unity로 설정 된 확인 해야 이러한 환경을 제공 합니다 **RoomScale** 공간 형식을 추적 합니다. RoomScale 기본값 이지만, 명시적으로 설정 하 고 사용자는 보정 대화방에서 자신의 컴퓨터를 이동 되었습니다 상황을 catch 하려면 true 다시 시작 하는 것이 좋습니다.

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

앱 공간 유형, 콘텐츠 y 배치 추적 RoomScale를 성공적으로 설정 되 면 0 평면 바닥에 표시 됩니다. 원점 (0, 0, 0)에서 사용자 공간 설치 하는 동안-앞쪽으로 설치 하는 동안 연결 된 것을 나타내는 Z를 사용 하 여 구현 하는 위치 현장에서 구체적인 장소를 수 있습니다.

스크립트 코드에서 수 있습니다 TryGetGeometry 메서드를 호출 하는 경계 다각형, 가져올 UnityEngine.Experimental.XR.Boundary 형식의 TrackedArea의 경계 형식을 지정 합니다. 안전 하 게 제공 하는 것을 알고 사용자 경계 (얻게 다시 꼭 짓 점 목록)을 정의 하는 경우는 **방 규모 환경** 위치 수 안내 장면 주위를 사용자에 게 만듭니다.

시스템 사용자 가까워지면 경계 렌더링 자동으로 참고 합니다. 앱이이 다각형을 사용 하 여 자체 경계를 렌더링할 필요가 없습니다.

자세한 내용은 참조는 [Unity의 좌표계](coordinate-systems-in-unity.md) 페이지입니다.

일부 응용 프로그램의 상호 작용을 제한 하는 사각형을 사용 합니다. 직접 UWP API 또는 Unity의 가장 큰 사각형 검색 지원 되지 않습니다. 예제 코드에 연결 아래 추적 된 범위 내에 사각형을 찾는 방법. 그러나 결과 기대와 대체적으로 일관적이 고 최적의 솔루션을 찾을 수 없습니다 있도록 기반 추론입니다. 처리 시간이 하더라도 더 정확한 결과를 찾을 알고리즘의 매개 변수를 튜닝할 수 있습니다. Unity의 MRTP 버전 5.6 미리 보기를 사용 하는 혼합 현실 도구 키트의 포크에서 알고리즘이입니다. 이 공개적으로 제공 되지 않습니다. 코드를 unity 2017.2 이상 버전에서 직접 사용할 수 있어야 합니다. 코드를 현재 MRTK에 가까운 장래에 이식할 수 됩니다.

[GitHub에서 코드의 zip 파일](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) 중요 한 파일:
* Assets/HoloToolkit/Stage/Scripts/StageManager.cs-사용법의 예
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle.cs-알고리즘 구현
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest.cs-알고리즘의 간단한 테스트

결과의 예:

![결과의 예](images/largestrectangle-400px.jpg)

알고리즘은 Daniel Smilkov 여 블로그를 기반으로 합니다. [Polygon에 있는 가장 큰 사각형](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Unity 9 단계: 입력된 모델을 통해 작동 합니다.

각 게임 또는 응용 프로그램을 기존 HMD를 대상으로 처리 하는 입력을 유형의 환경에 필요한 입력 및 해당 입력을 가져오는 호출 하는 특정 Api 집합을 갖습니다. 간단 하 고 Windows Mixed Reality에서 사용할 수 있는 입력을 활용 하려면 최대한 간단 하 게 확인 하는 동안에 투자 했습니다.
1. 읽고 합니다 **[포팅 가이드 Unity에 대 한 입력](input-porting-guide-for-unity.md)** Windows Mixed Reality를 하는 방법의 세부 정보에 대 한 입력을 노출 하 고 어떤 응용 프로그램에 매핑되는 방법을 오늘 수행할 수 있습니다.
2. Unity의 교차-VR-SDK 입력 API를 활용 하려는 여부 MR 특정 입력 API를 선택 합니다. 오늘에 대 한 Unity VR 앱에서 사용 하는 일반 Input.GetButton/Input.GetAxis Api [Oculus 입력](https://docs.unity3d.com/Manual/OculusControllers.html) 하 고 [OpenVR 입력](https://docs.unity3d.com/Manual/OpenVRControllers.html)합니다. 앱을 이미 사용 중인 이러한 Api 컨트롤러 동작에 대 한 경우이 가장 쉬운 경로-단추 및 축 입력 관리자를 다시 매핑할 하기만 합니다.
    * 크로스-VR-SDK Input.GetButton/Input.GetAxis Api 일반 또는 MR 별 UnityEngine.XR.WSA.Input Api를 사용 하 여 Unity의 동작 컨트롤러 데이터를 액세스할 수 있습니다. (이전에 Unity 5.6 UnityEngine.XR.WSA.Input 네임 스페이스)
    * 참조 된 [도구 키트의 예제에서는](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) gamepad 및 중인 컨트롤러를 결합 하 합니다.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity 10 단계: 성능 테스트 및 튜닝

Windows Mixed Reality 장치의 광범위 한 클래스에서 사용 가능을 게임 Pc를 광범위 한 시장으로 일반 Pc에서 높은 범위의 합니다. 대상으로 하는 어떤 시장에 따라 응용 프로그램에 대 한 사용 가능한 계산 및 그래픽 예산에서 큰 차이가 있습니다. 포팅이 연습에서는 프리미엄 PC를 활용 하 여 가능성이 및 앱에 사용 가능한 계산 및 그래픽 예산 중요 했습니다. 더 많은 청중에 게 앱을 제공 하려는 경우 테스트 하 고 앱에서 프로 파일링 해야 [대표 하드웨어 하려는 대상](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)합니다.

둘 다 [Unity](https://docs.unity3d.com/Manual/Profiler.html) 하 고 [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) 성능 프로파일러 및 모두 포함 [Microsoft](understanding-performance-for-mixed-reality.md) 및 [Intel](https://software.intel.com/articles/vr-content-developer-guide) 지침에 게시 성능 프로 파일링 및 최적화 합니다. 광범위 한 설명은 성능에서 제공 됩니다 [혼합 현실에 대 한 성능 이해](understanding-performance-for-mixed-reality.md)합니다. 또한 아래에서 Unity에 대 한 특정 세부 내용이 [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)합니다.

## <a name="see-also"></a>참조
* [포팅 가이드 Unity에 대 한 입력](input-porting-guide-for-unity.md)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [혼합된 현실에 대 한 성능 이해](understanding-performance-for-mixed-reality.md)
* [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)
* [UWP 용 Unity에 Xbox Live 지원 추가](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
