---
title: 도구 설치
description: 혼합된 현실 개발을 위해 준비 하려면 여기를 시작 합니다. 이 문서에서는 Unity, Visual Studio 및 HoloLens 및 Windows Mixed Reality 몰입 형 헤드셋 개발을 위한 권장 도구의 최신 버전을 항상 반영 해야 합니다.
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 최신 도구, 시작, 도구 키트, visual studio, unity, 기본 사항
ms.openlocfilehash: 32dcda0eceb8d3717de7b2502d86f03cda975b8f
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453732"
---
# <a name="install-the-tools"></a>도구 설치

Windows Mixed Reality 몰입 형 (VR) 헤드셋 및 Microsoft HoloLens 용 앱 개발 하는 데 필요한 도구를 가져옵니다. 별도 SDK에 대 한 Windows Mixed Reality 개발 작업 없이; Windows 10 SDK를 사용 하 여 Visual Studio를 사용 합니다.

혼합된 현실 장치가 없으세요? 설치할 수는 [HoloLens 에뮬레이터](using-the-hololens-emulator.md) 는 HoloLens 하지 않고 혼합된 현실 앱의 일부 기능을 테스트 합니다. 사용할 수도 있습니다는 [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md) 몰입 형 헤드셋에 대 한 혼합된 현실 앱을 테스트 합니다.

그러나 빌드할 수도 있습니다 DirectX에 대 한 사용자 지정 엔진을 사용 하려는 경우, 혼합 현실 앱 만들기 시작 하는 가장 쉬운 방법은으로 Unity 게임 엔진을 설치 하는 것이 좋습니다.

>[!TIP]
>이 페이지에 책갈피 지정 하 고 혼합된 현실 개발에 대 한 권장 되는 각 도구의 최신 버전을 최신 상태로 유지 하도록 정기적으로 확인 합니다.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>설치 검사 목록


| 도구 | 설명 | 참고 |
|---------|---------|---------|
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(수동 설치 링크)</a> | PC의 운영 체제는 혼합된 현실 앱을 빌드하는 플랫폼을 일치 하도록 Windows 10의 최신 버전을 설치 합니다. | **Windows 10 설치** <br> <ul><li>설정에서 또는 설치 미디어 (왼쪽된 열에서 링크 사용)를 만들어 Windows Update를 통해 Windows 10의 최신 버전을 설치할 수 있습니다.<li>참조 [현재 릴리스](release-notes-october-2018.md) 최신에 대 한 정보에 대 한 각 릴리스의 Windows 10을 사용 하 여 실제로 기능을 사용할 수 있는 혼합 합니다.</ul> **PC에서 개발자 모드가 사용 하도록 설정** 설정 > 업데이트 및 보안 > 개발자를 위한 합니다. <br><br> **엔터프라이즈 및 회사 관리 되는 Pc에 대 한 참고:** PC 관리 하는 경우는 조직의 IT 부서를 업데이트 하기 위해 연결할 해야 할 수 있습니다. <br><br> **Windows의 ' n ' 버전:** Windows Mixed Reality 몰입 형 (VR) 헤드셋 ' n ' 버전의 Windows에서 지원 되지 않습니다. |
| ![Visual Studio 로고](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>(설치 링크)</a> | Windows 및 기타 정보에 대 한 완전 한 기능을 갖춘 통합된 개발 환경 (IDE)입니다. Visual Studio 코드를 작성, 디버그, 테스트 및 배포를 사용 합니다. | **설치할 워크 로드:** <ul><li>사용한 데스크톱 개발C++</li><li>유니버설 Windows 플랫폼 개발</li></ul>**Unity에 대 한 정보:** 특정 목적을 위해 Unity의 최신 (비-LTS) 버전을 설치 하려는 의도적으로 하지 않는 한 것이 좋습니다 *되지* Unity 워크 로드의 일부로 설치할 때 Visual Studio를 설치 하 고 대신 2018.4 LTS를 설치 아래 설명 된 대로 Unity의 스트림입니다.<br> <br>**참고:** 현재 Visual Studio 2019에서 혼합된 현실 개발의 몇 가지 알려진된 문제가 있습니다.  이제 Visual Studio 2017을 사용 하 여 계속 진행 하는 것이 좋습니다. |
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>(수동 설치 링크)</a> | HoloLens 2에서 Windows 10 앱을 빌드하기 위한 최신 헤더, 라이브러리, 메타 데이터 및 도구를 제공 합니다. | HoloLens 2 앱을 빌드하려면 Windows SDK 빌드 18362 이상을 설치 해야 합니다.<br> <br> Windows Mixed Reality 헤드셋 데스크톱 또는 HoloLens 용 앱 개발 하 고만 경우 (첫 번째 gen) Visual Studio 2017에서 설치 된 Windows SDK를 사용할 수 있습니다. |
| ![Visual Studio 로고](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**HoloLens 2 Emulator**<br>(설치 링크: 10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (첫 번째 gen) 에뮬레이터**<br>(설치 링크: 10.0.17763.253)</a> | 에뮬레이터를 사용 하면 실제 HoloLens 하지 않고 HoloLens 가상 머신 이미지에서 앱을 실행할 수 있습니다.<br> <br> 이 패키지에도 Visual Studio 용 holographic DirectX 프로젝트 템플릿을 포함 합니다. | 참조 [HoloLens 에뮬레이터를 사용 하 여](using-the-hololens-emulator.md) 에뮬레이터를 시작 하기 대 한 자세한 내용은 합니다.<br> <br> **시스템에서 Hyper-v를 지원 해야** 에뮬레이터 설치가 제대로 되려면 합니다. 자세한 내용은 아래 시스템 요구 사항 섹션을 참조 하세요. 원하는 경우에 에뮬레이터가 없어도 템플릿만 설치를 선택할 수 있습니다.<br>|
| ![Unity 로고](images/unity_logo.png)<br><br><a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">**Unity 2018.4**<br>(설치 링크)</a> | Unity 게임 엔진은 Windows Mixed Reality 기능에 대 한 기본 제공 지원으로 혼합된 현실 환경을 만드는 가장 쉬운 방법입니다. | 일반적으로 권장 Unity LTS (긴 용어 지원) 스트림 하는 새 프로젝트를 시작 하는 데 사용할 가장 적합 한 버전으로를 안정적인 최신 수정 프로그램을 선택 하는 최신 버전으로 업데이트 합니다.<br> <br>현재 권장 사항을 사용 하는 것 **Unity 2018.4.x**, 아래 MRTK v2에 대 한 필요한 LTS 빌드는 합니다.<br> <br>일부 개발자는 특정 이유로 다른 버전의 Unity 사용 하려고 합니다. 이러한 경우 Unity는 서로 다른 버전의 side-by-side-설치를 지원합니다. |
| ![MRTK 로고](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**Unity 용 혼합된 현실 도구 키트 (MRTK v2)** </a> | Unity에 대 한 MRTK v2는 오픈 소스 플랫폼 간 개발 키트 혼합된 현실 응용 프로그램에 대 한 경우<br><br> Microsoft HoloLens, (VR) 헤드셋을 몰입 형 Windows Mixed Reality 및 OpenVR 플랫폼을 대상으로 하는 응용 프로그램의 개발을 가속화 MRTK v2 것입니다. 프로젝트는 혼합된 현실 응용 프로그램을 만드는 항목에는 barrier를 줄이기 위한 및 증가 우리가 커뮤니티에 다시 기여 합니다. | 프로젝트의 방문에 대해 MRTK v2 자세히 알아보세요 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">GitHub wiki</a>합니다. |


## <a name="mixed-reality-toolkit"></a>혼합된 현실 도구 키트

혼합 현실 도구 키트 구성 요소 및 Microsoft HoloLens, Windows Mixed Reality 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 응용 프로그램의 개발을 가속화할 수 있는 기능을 제공 합니다. 프로젝트는 장벽이 혼합된 현실 응용 프로그램을 만들고 우리가 증가 함에 따라 커뮤니티에 다시 기여에 항목을 줄이는 목표로 합니다.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit Unity</a> -기본 도구 키트의 코드를 사용 하 고 Unity에서 사용 하기가 쉬워집니다.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> -코드 bits 및 HoloLens 또는 몰입 형 (VR) 헤드셋에서 직접 실행 되지 않을 수 있는 구성 요소 이지만 Windows Mixed Reality를 대상으로 작성 된 쌍을 경험 하는 대신 합니다.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>혼합된 현실 개발을 위한 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에 적합합니다. 또한이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서 지원 됩니다. 참고는 일부 도구는 이전 운영 체제에서 지원 됩니다. 

### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위한 개발 PC 설정할 때 했는지의 시스템 요구 사항을 모두 충족 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 하 고 <a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>합니다. HoloLens 사용 하려는 경우 (첫 번째 gen)에 PC 충족 하는지 확인 하려는 에뮬레이터 합니다 [HoloLens 에뮬레이터 시스템 요구 사항](using-the-hololens-emulator.md#hololens-emulator-system-requirements) 도 합니다.

HoloLens emulator 시작을 참조 하세요 [HoloLens 에뮬레이터를 사용 하 여](using-the-hololens-emulator.md)입니다.

HoloLens와 Windows Mixed Reality 몰입 형 (VR) 헤드셋에 대 한 개발 하려는 경우 한 시스템 권장 사항 및 요구 사항 아래 섹션에 사용 하세요.

### <a name="for-immersive-vr-headset-development"></a>몰입 형 (VR) 헤드셋 개발용

>[!NOTE]
>다음 지침을 몰입 형 헤드셋 (VR)에 대 한 현재 최소 및 권장 사양을 *개발 PC*를 정기적으로 업데이트할 수 있습니다.

>[!WARNING]
>이를 혼동 하지 마십시오는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)는 윤곽선을 *소비자 PC 사양* 몰입 형 (VR) 헤드셋 앱 이나 게임을 대상 해야 하는 합니다.

몰입 형 헤드셋 개발 PC 큰 HDMI 및/또는 USB 3.0 포트에 없는 경우 해야 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) 헤드셋을 연결 합니다.

현재 [알려진 문제](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) 특히 하이브리드 그래픽이 있는 노트북을 사용 하 여 일부 하드웨어 구성 합니다.

<table>
<tr>
<th></th><th> 최소</th><th> 권장</th>
</tr><tr>
<td> 프로세서</td><td> <b>Notebook:</b> Intel 모바일 Core i5 7 생성 CPU, 듀얼 코어 하이퍼 스레딩을 사용 하 여 <b>데스크톱:</b> 여섯 번째 세대 CPU, 하이퍼 스레딩을 사용 하 여 듀얼 코어 Intel 데스크톱 i5 <b>또는</b> AMD FX4350 4.2 Ghz의 쿼드 코어 해당</td><td> <b>데스크톱:</b> 여섯 번째 세대 (6 코어) 데스크톱 Intel i7 <b>또는</b> AMD Ryzen 5 1600 (6 코어, 12 스레드)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965 M, AMD RX 460 M (2GB) 같거나 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 같거나 DX12 지원 GPU</td><td><b>데스크톱:</b> 1060/NVIDIA GTX 980, AMD Radeon RX 480 (2GB) 같거나 DX12 지원 GPU</td>
</tr><tr>
<td> GPU 드라이버 WDDM 버전</td><td colspan="2"> WDDM 2.2 드라이버</td>
</tr><tr>
<td> 열 디자인 Power</td><td colspan="2"> 15W 이상</td>
</tr><tr>
<td> 그래픽 포트 표시</td><td colspan="2"> 사용 가능한 그래픽 x 1에 대 한 포트를 표시&#160;헤드셋 (HDMI 1.4 또는 HDMI 2.0 또는 90 Hz 헤드셋에 DisplayPort 1.2 60hz 헤드셋에 DisplayPort 1.2)</td>
</tr><tr>
<td> 디스플레이 해상도</td><td colspan="2"> 해결 방법: SVGA (800 x 600) 또는 비트 자세히: 픽셀당 색의 32 비트</td>
</tr><tr>
<td> 메모리</td><td> 8&#160;GB RAM 이상</td><td> 16GB RAM 이상</td>
</tr><tr>
<td> 저장 공간</td><td colspan="2"> &gt;사용 가능한 공간이 추가로 10GB</td>
</tr><tr>
<td> USB 포트</td><td colspan="2"> 1 개 사용할 수 있는 USB 헤드셋 (USB 3.0 Type-A)에 대 한 포트 <b>참고 합니다. USB은 900mA 최소를 제공 해야 합니다.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (액세서리 연결용)</td>
</tr>
</table>

## <a name="see-also"></a>참조

* [개발 개요](development-overview.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
* [Windows Mixed Reality 시뮬레이션 사용](using-the-windows-mixed-reality-simulator.md)
* [Unity 개발 개요](unity-development-overview.md)
* [DirectX 개발 개요](directx-development-overview.md)
* [HoloLens 에뮬레이터 아카이브](hololens-emulator-archive.md)
