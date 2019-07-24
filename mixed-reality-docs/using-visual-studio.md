---
title: Visual Studio를 사용 하 여 배포 및 디버그
description: Visual Studio를 사용 하 여 HoloLens 및 Windows Mixed Reality 앱을 빌드, 디버그 및 배포 하는 방법입니다.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, 혼합 현실, 디버그, 배포
ms.openlocfilehash: 36ed428d69802084c3b953ac2fdce46844dfdc88
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387729"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Visual Studio를 사용 하 여 배포 및 디버그

DirectX 또는 Unity를 사용 하 여 혼합 현실 앱을 개발할 지 여부에 관계 없이 Visual Studio를 사용 하 여 디버깅 하 고 배포할 수 있습니다. 이 섹션에서는 다음에 대해 설명 합니다.
* Visual Studio를 통해 HoloLens 또는 Windows Mixed Reality 모던 헤드셋에 응용 프로그램을 배포 하는 방법입니다.
* Visual Studio에 기본 제공 되는 HoloLens 에뮬레이터를 사용 하는 방법입니다.
* 혼합 현실 앱을 디버그 하는 방법입니다.

## <a name="prerequisites"></a>사전 요구 사항
1. 설치 지침은 [도구 설치](install-the-tools.md) 를 참조 하세요.
2. Visual Studio 2015 업데이트 1, Visual Studio 2017 또는 Visual Studio 2019에서 새 유니버설 Windows 앱 프로젝트를 만듭니다. C#, C++및 JavaScript 프로젝트가 모두 지원 됩니다. (또는 지침에 따라 [Unity에서 앱 빌드를 만듭니다](holograms-100.md).)

## <a name="enabling-developer-mode"></a>개발자 모드 사용

먼저 장치에서 **개발자 모드** 를 사용 하도록 설정 하 여 시작 합니다. 그러면 Visual Studio가 해당 장치에 연결할 수 있습니다.

### <a name="hololens"></a>HoloLens
1. HoloLens를 켜고 장치에 배치 합니다.
2. [블룸](gestures.md#bloom) 제스처를 수행하여 주 메뉴를 시작합니다.
3. **설정** 타일을 응시 하 고 [공중 탭](gestures.md#air-tap) 제스처를 수행 합니다. 두 번째 에어 탭을 수행하여 환경에 앱을 배치합니다. 앱을 배치한 후 앱 설정이 시작됩니다.
4. **업데이트** 메뉴 항목을 선택합니다.
5. **개발자용** 메뉴 항목을 선택합니다.
6. **개발자 모드**를 사용하도록 설정합니다. 그러면 [Visual Studio에서](using-visual-studio.md) HoloLens에 앱을 배포할 수 있습니다.
7. 선택 사항: 아래로 스크롤하고 **장치 포털**도 사용 하도록 설정 합니다. 이를 통해 웹 브라우저에서 HoloLens의 [Windows 장치 포털](using-the-windows-device-portal.md) 에 연결할 수도 있습니다.

### <a name="windows-pc"></a>Windows PC

PC에 연결 된 Windows Mixed Reality 헤드셋으로 작업 하는 경우 PC에서 **개발자 모드** 를 사용 하도록 설정 해야 합니다.
1. **설정** 으로 이동
2. **업데이트 및 보안** 선택
3. **개발자 용** 으로 선택
4. **개발자 모드**를 사용 하도록 설정 하 고, 선택한 설정에 대 한 부인 사항을 읽은 다음, 예를 클릭 하 여 변경 내용을 적용 합니다.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Wi-fi를 통한 앱 배포 (첫 번째 gen)
1. Visual Studio  에서 앱 ![에 대 한 x86 빌드 구성을 선택 합니다.](images/x86setting.png)
2. Visual Studio의 배포 대상 드롭다운 메뉴 ![원격 컴퓨터 배포 대상에서 **원격 컴퓨터** 를 선택 합니다.](images/remotemachinesetting.png)
3. 및 C++ JavaScript 프로젝트의 경우 **프로젝트 > 속성 > 구성 속성 > 디버깅**으로 이동 합니다. 프로젝트 C# 의 경우 연결을 구성 하기 위한 대화 상자가 자동으로 팝업 됩니다.
  a. **주소** 또는 **컴퓨터 이름** 필드에 장치의 IP 주소를 입력 합니다. **설정 > Network & Internet > 고급 옵션**에서 HOLOLENS의 ip 주소를 찾거나 Cortana에서 "내 IP 주소는 무엇입니까?"를 선택할 수 있습니다.
  b. Visual Studio에서 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** ![원격 연결 대화 상자로 설정](images/remotedeploy.png)
4. **디버그 > 디버깅 시작** 을 선택 하 여 앱을 배포 하![고 Visual Studio에서 디버깅 하지 않고 시작을 시작 합니다.](images/deploynodebugging.png)
5. PC에서 HoloLens에 앱을 처음으로 배포할 때 PIN을 입력 하 라는 메시지가 표시 됩니다. 아래 **장치** 연결 지침을 따릅니다.

HoloLens IP 주소가 변경 되 면 **프로젝트 > 속성 > 구성 속성 > 디버깅** 으로 이동 하 여 대상 컴퓨터의 IP 주소를 변경할 수 있습니다.

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>USB를 통해 앱 배포-HoloLens (첫 번째 gen)
1. Visual Studio  에서 앱 ![에 대 한 x86 빌드 구성을 선택 합니다.](images/x86setting.png)
2. Visual  Studio의 배포 대상 드롭다운 메뉴![장치 배포에서 장치를 선택 합니다.](images/buildsettingsusbdeploy.png)
3. **디버그 > 디버깅 시작** 을 선택 하 여 앱을 배포 하![고 Visual Studio에서 디버깅 하지 않고 시작을 시작 합니다.](images/deploynodebugging.png)
4. PC에서 HoloLens에 앱을 처음으로 배포할 때 PIN을 입력 하 라는 메시지가 표시 됩니다. 아래 **장치** 연결 지침을 따릅니다.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>로컬 PC 모던 헤드셋에 앱 배포

PC 또는 [혼합 현실 시뮬레이터](using-the-windows-mixed-reality-simulator.md)에 연결 하는 Windows Mixed Reality 몰입 형 헤드셋을 사용 하는 경우 다음 지침을 따르세요. 이러한 경우에는 로컬 PC에서 앱을 배포 하 고 실행 하기만 하면 됩니다.
1. 앱에 대 한 **x86** 또는 **x64** 빌드 구성 선택
2. 배포 대상 드롭다운 메뉴에서 **로컬 컴퓨터** 를 선택 합니다.
3. **디버그 > 디버깅 시작** 을 선택 하 여 앱을 배포 하 고 디버깅을 시작 합니다.

## <a name="pairing-your-device---hololens-1st-gen"></a>장치 페어링-HoloLens (첫 번째 gen)

처음으로 Visual Studio에서 HoloLens에 앱을 배포할 때 PIN을 입력 하 라는 메시지가 표시 됩니다. HoloLens에서 설정 앱을 시작 하 여 PIN을 생성 하 고 개발자를 **위한 업데이트 >** 으로 이동한 다음, **쌍**을 탭 합니다. HoloLens에 PIN이 표시 됩니다. Visual Studio에서이 PIN을 입력 합니다. 페어링이 완료 되 면 HoloLens에서 **완료** 를 눌러 대화 상자를 닫습니다. 이 PC는 이제 HoloLens와 페어링 되며 앱을 자동으로 배포할 수 있습니다. HoloLens에 앱을 배포 하는 데 사용 되는 모든 후속 PC에 대해 이러한 단계를 반복 합니다.

연결 된 모든 컴퓨터에서 HoloLens를 분리 하려면 **설정** 앱을 시작 하 고, **개발자 용 업데이트 >** 로 이동 하 고, **Clear**를 누릅니다.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>HoloLens (첫 번째 gen) 에뮬레이터에 앱 배포
1. **[HoloLens 에뮬레이터를 설치](install-the-tools.md)** 했는지 확인 합니다.
2. 앱에 대 한 **x86** 빌드 구성을 선택 합니다.
![Visual Studio의 x86 빌드 구성](images/x86setting.png)
3. Visual Studio의 배포 대상 드롭다운 메뉴![에뮬레이터 대상에서 **HoloLens 에뮬레이터** 를 선택 합니다.](images/deployemulator.png)
4. **디버그 > 디버깅 시작** 을 선택 하 여 앱을 배포 하![고 Visual Studio에서 디버깅 하지 않고 시작을 시작 합니다.](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>그래픽 디버거

Visual Studio 그래픽 진단 도구는 Holographic 앱을 작성 하 고 최적화 하는 데 매우 유용 합니다. 자세한 내용은 [MSDN의 Visual Studio 그래픽 진단](https://msdn.microsoft.com/library/hh315751.aspx) 를 참조 하세요.

**그래픽 디버거를 시작 하려면**
1. 위의 지침에 따라 장치 또는 에뮬레이터를 대상으로 합니다.
2. **디버그 > 그래픽으로 이동 하 > 진단을 시작** 합니다.
3. HoloLens를 사용 하 여 처음으로이 작업을 수행 하는 경우 "액세스 거부" 오류가 발생할 수 있습니다. 업데이트 된 권한이 적용 되도록 HoloLens를 다시 부팅 한 후 다시 시도 하세요.

## <a name="profiling"></a>프로파일링

Visual Studio 프로 파일링 도구를 사용 하 여 앱의 성능 및 리소스 사용을 분석할 수 있습니다. 여기에는 CPU, 메모리, 그래픽 및 네트워크 사용을 최적화 하는 도구가 포함 됩니다. 자세한 내용은 [MSDN에서 디버깅 하지 않고 진단 도구 실행](https://msdn.microsoft.com/library/dn957936.aspx) 을 참조 하세요.

**HoloLens를 사용 하 여 프로파일링 도구를 시작 하려면**
1. 위의 지침에 따라 장치 또는 에뮬레이터를 대상으로 합니다.
2. **디버그 > 디버깅 하지 않고 시작 진단 도구** 로 이동 ...
3. 사용 하려는 도구 선택
4. **시작** 클릭
5. HoloLens를 사용 하 여 처음으로이 작업을 수행 하는 경우 "액세스 거부" 오류가 발생할 수 있습니다. 업데이트 된 권한이 적용 되도록 HoloLens를 다시 부팅 한 후 다시 시도 하세요.

## <a name="debugging-an-installed-or-running-app"></a>설치 된 응용 프로그램 또는 실행 중인 응용 프로그램 디버깅

Visual Studio를 사용 하 여 Visual Studio 프로젝트에서 배포 하지 않고 설치 된 유니버설 Windows 앱을 디버그할 수 있습니다. 이는 설치 된 응용 프로그램 패키지를 디버깅 하려는 경우 또는 이미 실행 중인 응용 프로그램을 디버깅 하려는 경우에 유용 합니다.
1. **디버그-> 기타 디버그 대상으로 이동-> 설치 된 앱 패키지 디버그**
2. HoloLens 용 **원격 컴퓨터** 대상 또는 모던 헤드셋의 **로컬 컴퓨터** 를 선택 합니다.
3. 장치의 **IP 주소** 를 입력 하세요.
4. **유니버설** 인증 모드를 선택 합니다.
5. 이 창에는 실행 중인 앱과 비활성 앱이 모두 표시 됩니다. 디버그할 항목을 선택 합니다.
6. 디버그할 코드 형식 선택 (관리, 네이티브, 혼합)
7. **연결** 또는 **시작** 을 클릭 합니다.

## <a name="see-also"></a>참조
* [도구 설치](install-the-tools.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
* [UWP (유니버설 Windows 플랫폼) 앱 배포 및 디버깅](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [장치를 개발에 사용 하도록 설정](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
