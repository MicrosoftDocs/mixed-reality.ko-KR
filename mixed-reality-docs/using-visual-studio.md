---
title: Visual Studio를 사용하여 배포 및 디버깅
description: Visual Studio를 사용하여 HoloLens 및 Windows Mixed Reality용 앱을 빌드, 디버그 및 배포하는 방법을 알아봅니다.
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, 디버그, 배포
ms.openlocfilehash: b7e6a8d538670a53de20a2f3a2850639e756da1a
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830837"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Visual Studio를 사용하여 배포 및 디버깅

DirectX 또는 Unity를 사용하여 혼합 현실 앱을 개발할지에 관계없이 Visual Studio를 사용하여 디버그하고 배포할 수 있습니다. 이 섹션에서는 다음을 수행하는 방법을 알아봅니다.
* Visual Studio를 통해 애플리케이션을 HoloLens 또는 Windows Mixed Reality 몰입형 헤드셋에 배포합니다.
* Visual Studio에 기본 제공된 HoloLens 에뮬레이터를 사용합니다.
* 혼합 현실 앱을 디버그합니다.

## <a name="prerequisites"></a>필수 구성 요소
1. 설치 지침은 [도구 설치](install-the-tools.md)를 참조하세요.
2. Visual Studio에서 새 유니버설 Windows 앱 프로젝트를 만듭니다.  HoloLens(1세대)의 경우 Visual Studio 2017 이상을 사용합니다.  Holololens 2의 경우 Visual Studio 2019 16.2 이상을 사용합니다. C# 및 C++가 지원됩니다. (또는 지침에 따라 [Unity에서 앱을 만듭니다](holograms-100.md).)

## <a name="enabling-developer-mode"></a>개발자 모드 사용

먼저 디바이스에서 **개발자 모드**를 사용하도록 설정합니다. 그러면 Visual Studio에서 해당 디바이스에 연결할 수 있습니다.

### <a name="hololens"></a>HoloLens
1. HoloLens를 켜고 디바이스에 배치합니다.
2. [블룸](system-gesture.md#bloom) 제스처를 수행하여 주 메뉴를 시작합니다.
3. **설정** 타일을 보고, [에어 탭](gaze-and-commit.md#composite-gestures) 제스처를 수행합니다. 두 번째 에어 탭을 수행하여 환경에 앱을 배치합니다. 앱을 배치한 후 앱 설정이 시작됩니다.
4. **업데이트** 메뉴 항목을 선택합니다.
5. **개발자용** 메뉴 항목을 선택합니다.
6. **개발자 모드**를 사용하도록 설정합니다. 그러면 [Visual Studio에서 HoloLens로 앱을 배포](using-visual-studio.md)할 수 있습니다.
7. 옵션: 아래로 스크롤하여 **디바이스 포털**도 사용하도록 설정합니다. 이렇게 하면 웹 브라우저에서 HoloLens의 [Windows 디바이스 포털](using-the-windows-device-portal.md)에도 연결할 수 있습니다.

### <a name="windows-pc"></a>Windows PC

PC에 연결된 Windows Mixed Reality 헤드셋을 사용하는 경우 PC에서 **개발자 모드**를 사용하도록 설정해야 합니다.
1. **설정**으로 이동합니다.
2. **업데이트 및 보안**을 선택합니다.
3. **개발자용**을 선택합니다.
4. **개발자 모드**를 사용하도록 설정하고, 선택한 설정에 대한 고지 사항을 읽은 다음, [예]를 클릭하여 변경 내용을 적용합니다.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Wi-Fi를 통해 앱 배포 - HoloLens(1세대)
1. 앱에 대해 **x86** 빌드 구성을 선택합니다. ![Visual Studio의 x86 빌드 구성](images/x86setting.png)
2. 배포 대상 드롭다운 메뉴에서 **원격 머신**을 선택합니다. ![Visual Studio의 원격 머신 배포 대상](images/remotemachinesetting.png)
3. C++ 및 JavaScript 프로젝트의 경우 **프로젝트 > 속성 > 구성 속성 > 디버깅**으로 차례로 이동합니다. C# 프로젝트의 경우 연결을 구성하는 대화 상자가 자동으로 표시됩니다.
  a. **주소** 또는 **머신 이름** 필드에서 디바이스의 IP 주소를 입력합니다. **설정 > 네트워크 및 인터넷 > 고급 옵션** 아래에서 HoloLens의 IP 주소를 찾거나, Cortana에 "내 IP 주소가 무엇입니까?"라고 질문할 수 있습니다.
  b. [인증 모드]를 **유니버설(암호화되지 않은 프로토콜)** 로 설정합니다. ![Visual Studio의 원격 연결 대화 상자](images/remotedeploy.png)
4. **디버그 > 디버깅 시작**을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다. ![Visual Studio의 디버깅하지 않고 시작](images/deploywithdebugging.png)
5. PC에서 앱을 HoloLens에 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다. 아래의 **디바이스 페어링** 지침을 따릅니다.

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Wi-Fi를 통해 앱 배포 - HoloLens 2
1. 앱에 대해 **ARM** 또는 **ARM64** 빌드 구성을 선택합니다. ![Visual Studio의 ARM64 빌드 구성](images/arm64setting.png)
2. 배포 대상 드롭다운 메뉴에서 **원격 머신**을 선택합니다. ![Visual Studio의 원격 머신 배포 대상](images/remotemachinesetting_arm64.png)
3. C++ 및 JavaScript 프로젝트의 경우 **프로젝트 > 속성 > 구성 속성 > 디버깅**으로 차례로 이동합니다. C# 프로젝트의 경우 연결을 구성하는 대화 상자가 자동으로 표시됩니다.
  a. **주소** 또는 **머신 이름** 필드에서 디바이스의 IP 주소를 입력합니다. **설정 > 네트워크 및 인터넷 > 고급 옵션** 아래에서 HoloLens의 IP 주소를 찾거나, Cortana에 "내 IP 주소가 무엇입니까?"라고 질문할 수 있습니다.
  b. [인증 모드]를 **유니버설(암호화되지 않은 프로토콜)** 로 설정합니다. ![Visual Studio의 원격 연결 대화 상자](images/remotedeploy.png)
4. **디버그 > 디버깅 시작**을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다. ![Visual Studio의 디버깅하지 않고 시작](images/deploywithdebugging.png)
5. PC에서 앱을 HoloLens에 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다. 아래의 **디바이스 페어링** 지침을 따릅니다.

HoloLens IP 주소가 변경되면 **프로젝트 > 속성 > 구성 속성 > 디버깅**으로 차례로 이동하여 대상 머신의 IP 주소를 변경할 수 있습니다.

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>USB를 통해 앱 배포 - HoloLens(1세대)
1. 앱에 대해 **x86** 빌드 구성을 선택합니다. ![Visual Studio의 x86 빌드 구성](images/x86setting.png)
2. 배포 대상 드롭 다운 메뉴에서 **디바이스**를 선택합니다. ![Visual Studio의 디바이스 배포](images/buildsettingsusbdeploy.png)
3. **디버그 > 디버깅 시작**을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다. ![Visual Studio의 디버깅하지 않고 시작](images/deploywithdebugging.png)
4. PC에서 앱을 HoloLens에 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다. 아래의 **디바이스 페어링** 지침을 따릅니다.

## <a name="deploying-an-app-over-usb---hololens-2"></a>USB를 통해 앱 배포 - HoloLens 2
1. 앱에 대해 **ARM** 또는 **ARM64** 빌드 구성을 선택합니다. ![Visual Studio의 ARM64 빌드 구성](images/arm64setting.png)
2. 배포 대상 드롭 다운 메뉴에서 **디바이스**를 선택합니다. ![Visual Studio의 디바이스 배포](images/buildsettingsusbdeploy_arm64.png)
3. **디버그 > 디버깅 시작**을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다. ![Visual Studio의 디버깅하지 않고 시작](images/deploywithdebugging.png)
4. PC에서 앱을 HoloLens에 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다. 아래의 **디바이스 페어링** 지침을 따릅니다.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>로컬 PC에 앱 배포 - 몰입형 헤드셋

PC 또는 [Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md)에 연결되는 Windows Mixed Reality 몰입형 헤드셋을 사용하는 경우 다음 지침을 따릅니다. 이러한 경우 로컬 PC에 앱을 배포하고 실행하기만 하면 됩니다.
1. 앱에 대해 **x86** 또는 **x64** 빌드 구성을 선택합니다.
2. 배포 대상 드롭다운 메뉴에서 **로컬 머신**을 선택합니다.
3. **디버그 > 디버깅 시작**을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다.

## <a name="pairing-your-device"></a>디바이스 페어링

앱을 Visual Studio에서 HoloLens로 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다. HoloLens에서 Settings 앱을 실행하여 PIN을 생성하고, **업데이트 > 개발자용**으로 차례로 이동하여 **페어링**을 탭합니다. HoloLens에 PIN이 표시됩니다. Visual Studio에서 이 PIN을 입력합니다. 페어링이 완료되면 HoloLens에서 **완료**를 탭하여 대화 상자를 해제합니다. 이 PC는 이제 HoloLens와 페어링되어 앱을 자동으로 배포할 수 있습니다. 앱을 HoloLens에 배포하는 데 사용되는 모든 후속 PC에 대해 이러한 단계를 반복하세요.

페어링된 모든 컴퓨터에서 HoloLens와의 페어링을 해제하려면 **Settings** 앱을 시작하고, **업데이트 > 개발자용**으로 차례로 이동하여 **지우기**를 탭합니다.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>HoloLens(1세대) 에뮬레이터에 앱 배포
1. **[HoloLens 에뮬레이터를 설치](install-the-tools.md)** 했는지 확인합니다.
2. 앱에 대해 **x86** 빌드 구성을 선택합니다.
![Visual Studio의 x86 빌드 구성](images/x86setting.png)
3. 배포 대상 드롭다운 메뉴에서 **HoloLens 에뮬레이터**를 선택합니다. ![Visual Studio의 에뮬레이터 대상](images/deployemulator.png)
4. **디버그 > 디버깅 시작**을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다. ![Visual Studio의 디버깅하지 않고 시작](images/deploywithdebugging.png)

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>HoloLens 2 에뮬레이터에 앱 배포
1. **[HoloLens 에뮬레이터를 설치](install-the-tools.md)** 했는지 확인합니다.
2. 앱에 대해 **x86** 또는 **x64** 빌드 구성을 선택합니다.
![Visual Studio의 x86 빌드 구성](images/x86setting.png)
3. 배포 대상 드롭 다운 메뉴에서 **HoloLens 2 에뮬레이터**를 선택합니다. ![Visual Studio의 에뮬레이터 대상](images/deployemulator2.png)
4. **디버그 > 디버깅 시작**을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다. ![Visual Studio의 디버깅하지 않고 시작](images/deploywithdebugging.png)

## <a name="graphics-debugger-for-hololens-1st-gen"></a>HoloLens(1세대)용 그래픽 디버거

Visual Studio 그래픽 진단 도구는 홀로그램 앱을 작성하고 최적화하는 경우에 매우 유용합니다. 자세한 내용은 [MSDN의 Visual Studio 그래픽 진단](https://msdn.microsoft.com/library/hh315751.aspx)을 참조하세요.

**그래픽 디버거를 시작하려면**
1. 위의 지침에 따라 디바이스 또는 에뮬레이터를 대상으로 지정합니다.
2. **디버그 > 그래픽 > 진단 시작**으로 차례로 이동합니다.
3. HoloLens를 사용하여 이 작업을 처음 수행하는 경우 "액세스 거부" 오류가 발생할 수 있습니다. 업데이트된 권한이 적용되도록 HoloLens를 다시 부팅하여 다시 시도하세요.

## <a name="profiling"></a>프로파일링

Visual Studio 프로파일링 도구를 사용하면 앱의 성능 및 리소스 사용을 분석할 수 있습니다. 여기에는 CPU, 메모리, 그래픽 및 네트워크 사용을 최적화하는 도구가 포함됩니다. 자세한 내용은 [MSDN의 디버깅하지 않고 진단 도구 실행](https://msdn.microsoft.com/library/dn957936.aspx)을 참조하세요.

**HoloLens를 사용하여 프로파일링 도구를 시작하려면**
1. 위의 지침에 따라 디바이스 또는 에뮬레이터를 대상으로 지정합니다.
2. **디버그 > 디버깅하지 않고 진단 도구 시작...** 으로 차례로 이동합니다.
3. 사용하려는 도구를 선택합니다.
4. **시작**을 클릭합니다.
5. HoloLens를 사용하여 이 작업을 처음 수행하는 경우 "액세스 거부" 오류가 발생할 수 있습니다. 업데이트된 권한이 적용되도록 HoloLens를 다시 부팅하여 다시 시도하세요.

## <a name="debugging-an-installed-or-running-app"></a>설치되었거나 실행 중인 앱 디버깅

Visual Studio를 사용하여 Visual Studio 프로젝트에서 배포하지 않고 설치된 유니버설 Windows 앱을 디버그할 수 있습니다. 설치된 앱 패키지를 디버그하거나 이미 실행 중인 앱을 디버그하려는 경우에 유용합니다.
1. **디버그 -> 기타 디버그 대상 -> 설치된 앱 패키지 디버그**로 차례로 이동합니다.
2. HoloLens의 경우 **원격 머신** 대상을 선택하고, 몰입형 헤드셋의 경우 **로컬 머신** 대상을 선택합니다.
3. 디바이스의 **IP 주소**를 입력합니다.
4. **유니버설** 인증 모드를 선택합니다.
5. 창에 실행 중인 앱과 비활성 앱이 모두 표시됩니다. 디버그하려는 앱을 선택합니다.
6. 디버그할 코드 형식(관리, 네이티브, 혼합)을 선택합니다.
7. **연결** 또는 **시작**을 클릭합니다.

## <a name="see-also"></a>참고 항목
* [도구 설치](install-the-tools.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
* [UWP(유니버설 Windows 플랫폼) 앱 배포 및 디버깅](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [디바이스를 개발에 사용하도록 설정](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
