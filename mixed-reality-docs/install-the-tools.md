---
title: 도구 설치
description: 혼합 현실 개발을 위해 준비하려면 여기에서 시작합니다. 이 문서는 항상 Unity, Visual Studio, HoloLens와 Windows Mixed Reality 몰입형 헤드셋 개발에 권장되는 기타 도구의 최신 버전을 반영합니다.
author: thetuvix
ms.author: alexturn
ms.date: 3/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit
ms.openlocfilehash: 131d2a91c882fbcd31c4deb76a5ab5c3f97d7d42
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82137878"
---
# <a name="install-the-tools"></a>도구 설치

Microsoft HoloLens 및 Windows Mixed Reality 몰입형(VR) 헤드셋을 위한 애플리케이션을 빌드하는 데 필요한 도구를 다운로드하세요. Windows Mixed Reality 개발을 위한 별도 SDK는 없으므로 Windows 10 SDK에서 Visual Studio를 사용합니다.

혼합 현실 디바이스가 없나요? [HoloLens 에뮬레이터](using-the-hololens-emulator.md)를 설치하면 HoloLens 없이도 혼합 현실 앱의 일부 기능을 테스트할 수 있습니다. [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md)를 사용하여 몰입형 헤드셋을 위한 혼합 현실 앱을 테스트할 수도 있습니다.

혼합 현실 앱 만들기를 시작하는 가장 쉬운 방법은 Unity 게임 엔진을 설치하는 것입니다. 그러나 사용자 지정 엔진을 사용하려는 경우에는 DirectX에 대해 빌드할 수도 있습니다.

>[!TIP]
>이 페이지에 책갈피를 지정하고 정기적으로 확인하면서 혼합 현실 개발에 권장되는 각 도구를 최신 상태로 유지하세요.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>설치 검사 목록


| 도구 | 설명 | 참고 |
|---------|---------|---------|
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**(수동 설치 링크)</a> | PC의 운영 체제가 혼합 현실 애플리케이션을 빌드하는 플랫폼과 일치하도록 최신 버전의 Windows 10을 설치합니다. | **Windows 10 설치** <br> <ul><li>설정의 Windows 업데이트를 통해 또는 설치 미디어를 만들어(왼쪽 열의 링크 사용) 최신 버전의 Windows 10을 설치할 수 있습니다.<li>각 릴리스의 Windows 10에서 사용할 수 있는 최신 혼합 현실 기능에 대한 내용은 [현재 릴리스 정보](release-notes-october-2018.md)를 참조하세요.</ul> 설정 > 업데이트 및 보안 > 개발자용에서 **PC의 개발자 모드를 사용하도록 설정**합니다. <br><br> **엔터프라이즈 및 회사 관리 PC에 대한 참고 사항:** 조직의 IT 부서에서 PC를 관리하는 경우 업데이트하려면 해당 부서에 문의해야 할 수도 있습니다. <br><br> **Windows용 'N' 버전:** Windows Mixed Reality 몰입형(VR) 헤드셋은 'N' 버전의 Windows에서 지원되지 않습니다. |
| ![Visual Studio 로고](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019(16.2 이상)** (설치 링크)</a> | Windows 등을 위한 전기능 IDE(통합 개발 환경)입니다. Visual Studio를 사용하여 코드를 작성하고, 디버그하고, 테스트하고, 배포합니다. | 다음 워크로드를 설치합니다. <ul><li>**C++를 사용한 데스크톱 개발**</li><li>**UWP(유니버설 Windows 플랫폼) 개발**</li></ul>HoloLens 앱을 개발하려는 경우 UWP 워크로드 내에서 다음과 같은 선택적 구성 요소를 확인해야 합니다.<ul><li>**USB 디바이스 연결**</li></ul>**Unity에 대한 참고 사항:** 특정 목적을 위해 최신 버전의 Unity(비 LTS)를 설치하려는 경우가 아니면 Unity 워크로드를 Visual Studio 설치의 일부로 설치하지 *말고*, 대신 아래 설명된 것처럼 **Unity 2018.4 LTS** 스트림을 설치하는 것이 좋습니다.<br> <br>**참고:** Visual Studio 2019 버전 16.0의 혼합 현실 앱 디버깅에는 몇 가지 알려진 이슈가 있습니다.  **Visual Studio 2019 버전 16.2 이상**으로 업데이트하세요. |
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK(10.0.18362.0)** (수동 설치 링크)</a> | HoloLens 2에서 Windows 10 앱을 빌드하기 위한 최신 헤더와 라이브러리, 메타데이터, 도구를 제공합니다. | HoloLens 2 앱을 빌드하려면 Windows SDK 빌드 18362 이상을 설치해야 합니다.<br> <br> 데스크톱 Windows Mixed Reality 헤드셋 또는 HoloLens(1세대)용 애플리케이션만 개발하는 경우에는 Visual Studio 2017에서 설치된 Windows SDK를 사용할 수 있습니다. |
| ![Visual Studio 로고](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2126826" target="_blank">**HoloLens 2 에뮬레이터(2020년 4월 업데이트)** (설치 링크: 10.0.18362.1059)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens(1세대) 에뮬레이터**(설치 링크: 10.0.17763.134)</a> | 이 에뮬레이터를 사용하면 실제 HoloLens 없이도 HoloLens 가상 머신 이미지에서 애플리케이션을 실행할 수 있습니다.<br> <br> | 에뮬레이터 시작 방법에 대한 자세한 내용은 [HoloLens 에뮬레이터 사용](using-the-hololens-emulator.md)을 참조하세요.<br> <br> 에뮬레이터 설치를 성공적으로 수행하려면 **시스템에서 Hyper-V를 지원해야 합니다**. 자세한 내용은 아래 시스템 요구 사항 섹션을 참조하세요. <br>|

## <a name="choose-your-engine"></a>엔진 선택

:::row:::
    :::column:::
        <a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">![Unity](images/unity_logo.png)<br>**Unity**</a><br>
        일반적으로 Unity LTS(장기 지원) 스트림을 새 프로젝트를 시작할 최선의 버전으로 사용한 후, 최신 수정 버전으로 업데이트하여 안정적인 최신 수정 프로그램을 선택하는 것이 좋습니다.<br>
        <br>
        현재 권장 사항은 아래의 MRTK v2에 필요한 LTS 빌드인 **Unity 2018.4.x**를 사용하는 것입니다.<br>
        <br>
        일부 개발자는 특정 이유로 다른 버전의 Unity를 사용하려고 합니다. 이러한 경우 Unity는 다른 버전을 병렬로 설치하도록 지원합니다.<br>
        <br>
        HoloLens 2 또는 Windows Mixed Reality 몰입형 헤드셋용 Unity 앱 개발을 시작하려면 [Unity 개발 개요](unity-development-overview.md)를 참조하세요.<br>
        <br>
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">![MRTK](images/final_mrtk-small_logo.png)<br>**MRTK(Mixed Reality Toolkit)** </a><br>
        Unity용 MRTK(Mixed Reality Toolkit) v2는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.<br>
        <br>
        MRTK v2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다. 이 프로젝트는 혼합 현실 애플리케이션을 만들기 위한 진입 장벽을 낮추고 커뮤니티에 다시 기여하는 것을 목표로 합니다.
    :::column-end:::
    :::column:::
        <a href="https://docs.unrealengine.com//GettingStarted/Installation/index.html" target="_blank">![Unreal](images/Unreal_logo.png)<br>**Unreal**</a><br>
        Unreal Engine 4는 C++ 및 Blueprint 모두에서 혼합 현실을 완벽하게 지원하는 강력한 오픈 소스 생성 엔진입니다.<br>
        <br>
        Unreal Engine 4.24에 대한 HoloLens 지원은 현재 베타 버전입니다.<br>
        <br>
        Unreal을 사용하여 HoloLens 2 앱 개발을 시작하려면 [Unreal 개발 개요](unreal-development-overview.md)를 참조하세요.
    :::column-end:::
    :::column:::
        ![네이티브 앱 개발](images/visualstudio-small_logo.png)<br>
        [**네이티브(OpenXR)** ](openxr-getting-started.md)<br>
        Khronos의 로열티 없는 개방형 API 표준인 OpenXR은 여러 업체에서 제공하는 혼합 현실 스펙트럼의 방대한 디바이스에 대한 네이티브 액세스를 엔진에 제공합니다.  <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 프로젝트는 두 개의 Visual Studio 프로젝트 파일이 포함된 간단한 OpenXR 샘플을 보여주며, 두 파일 중 하나는 Win32 데스크톱 앱용이고 다른 하나는 UWP HoloLens 2 앱용입니다.<br>
        <br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">**네이티브(WinRT)** </a><br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">Windows Mixed Reality 네이티브 앱 템플릿</a>은 기본 API와 함께 DirectX를 사용하여 혼합 현실 앱을 작성하는 데 필요한 모든 기본 정보를 제공합니다. 렌더링 루프(또는 "게임 루프"), Direct3D 디바이스 및 컨텍스트를 관리하는 DeviceResources 도우미 클래스 및 간단한 예제 홀로그램 렌더러가 포함됩니다. Direct3D 11 및 Direct3D 12에서 사용 가능합니다.<br>
        <br>
        WinRT 또는 OpenXR을 사용하여 HoloLens 2 또는 Windows Mixed Reality 몰입형 헤드셋용 네이티브 앱 개발을 시작하려면 [네이티브 개발 개요](directx-development-overview.md)를 참조하세요.
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit(MRTK)

Mixed Reality Toolkit은 Microsoft HoloLens, Windows Mixed Reality 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안된 구성 요소 및 기능을 제공합니다. 이 프로젝트는 혼합 현실 애플리케이션을 만들기 위한 진입 장벽을 낮추고 커뮤니티에 다시 기여하는 것을 목표로 합니다.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit</a> - 혼합 현실 애플리케이션 개발을 가속화하기 위한 스크립트 및 구성 요소 컬렉션입니다.
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit-Unity</a> - 기본 도구 키트의 코드를 사용하며, Unity에서 더 쉽게 사용할 수 있도록 합니다.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>혼합 현실 개발을 위해 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다. 또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다. 일부 도구는 이전 운영 체제에서 지원되지 않습니다. 

### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 둘 다에 대한 시스템 요구 사항을 충족하는지 확인합니다. HoloLens 에뮬레이터를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인할 수 있습니다.

HoloLens 에뮬레이터를 시작하려면 [HoloLens 에뮬레이터 사용](using-the-hololens-emulator.md)을 참조하세요.

HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.

### <a name="for-immersive-vr-headset-development"></a>몰입형 (VR) 헤드셋 개발

>[!NOTE]
>다음 지침은 몰입형(VR) 헤드셋 *개발 PC*에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.

>[!WARNING]
>이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양*을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.

몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.

현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.

<table>
<tr>
<th></th><th> 최소값</th><th> 권장</th>
</tr><tr>
<td> 프로세서</td><td> <b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</td><td> <b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</td>
</tr><tr>
<td> GPU</td><td> <b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td><td><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td>
</tr><tr>
<td> GPU 드라이버 WDDM 버전</td><td colspan="2"> WDDM 2.2 드라이버</td>
</tr><tr>
<td> 열 디자인 전원</td><td colspan="2"> 15W 이상</td>
</tr><tr>
<td> 그래픽 디스플레이 포트</td><td colspan="2"> 헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</td>
</tr><tr>
<td> 디스플레이 해상도</td><td colspan="2"> 해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</td>
</tr><tr>
<td> 메모리</td><td> 8GB&#160;RAM 이상</td><td> 16GB RAM 이상</td>
</tr><tr>
<td> 스토리지</td><td colspan="2"> &gt;10GB의 추가 사용 가능 공간</td>
</tr><tr>
<td> USB 포트</td><td colspan="2"> 헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0(액세서리 연결용)</td>
</tr>
</table>

## <a name="see-also"></a>참고 항목

* [개발 개요](development.md)
* [HoloLens 에뮬레이터 사용](using-the-hololens-emulator.md)
* [Windows Mixed Reality 시뮬레이션 사용](using-the-windows-mixed-reality-simulator.md)
* [Unity 개발 개요](unity-development-overview.md)
* [Unreal 개발 개요](unreal-development-overview.md)
* [DirectX 개발 개요](directx-development-overview.md)
* [HoloLens 에뮬레이터 아카이브](hololens-emulator-archive.md)
