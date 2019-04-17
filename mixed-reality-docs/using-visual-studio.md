---
title: Visual Studio를 사용 하 여 배포 및 디버깅
description: 빌드, 디버그 및 HoloLens 및 Visual Studio를 사용 하 여 Windows Mixed Reality에 대 한 앱을 배포 하는 방법.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, 혼합 현실 등 디버그, 배포
ms.openlocfilehash: 6bd47d7212d321791a11ff4db91c3e172c91f463
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601370"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Visual Studio를 사용 하 여 배포 및 디버깅

혼합된 현실 앱 개발 DirectX 또는 Unity를 사용 하려는 지 여부에 디버깅 및 배포에 대 한 Visual Studio를 사용 합니다. 이 섹션에서는 배웁니다.
* Visual Studio를 통해 HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋 응용 프로그램을 배포 하는 방법입니다.
* Visual Studio에 기본 제공 HoloLens 에뮬레이터를 사용 하는 방법입니다.
* 혼합된 현실 앱을 디버그 하는 방법.

## <a name="prerequisites"></a>사전 요구 사항
1. 참조 [도구를 설치](install-the-tools.md) 설치 지침에 대 한 합니다.
2. Visual Studio 2015 업데이트 1 또는 Visual Studio 2017에서 새 유니버설 Windows 앱 프로젝트를 만듭니다. C#C++, 및 JavaScript 프로젝트 모두 지원 됩니다. (지침에 따르거나 [Unity에서 빌드를 앱을 만들](holograms-100.md).)

## <a name="enabling-developer-mode"></a>개발자 모드 사용

사용 하 여 시작 **개발자 모드** 장치의 Visual Studio에 연결할 수 있도록 합니다.

### <a name="hololens"></a>HoloLens
1. HoloLens에 설정 하 고 장치에 배치 합니다.
2. [블룸](gestures.md#bloom) 제스처를 수행하여 주 메뉴를 시작합니다.
3. 응시 합니다 **설정** 타일을 수행 합니다 [어 탭](gestures.md#air-tap) 제스처입니다. 두 번째 에어 탭을 수행하여 환경에 앱을 배치합니다. 앱을 배치한 후 앱 설정이 시작됩니다.
4. **업데이트** 메뉴 항목을 선택합니다.
5. **개발자용** 메뉴 항목을 선택합니다.
6. **개발자 모드**를 사용하도록 설정합니다. 이렇게 하면 하 [Visual Studio에서 앱을 배포할](using-visual-studio.md) 에 HoloLens에 합니다.
7. 선택 사항: 아래로 스크롤하여 사용 하도록 설정할 수도 **장치 포털**합니다. 또한 그러면에 연결 하는 [Windows Device Portal](using-the-windows-device-portal.md) 웹 브라우저에서에 HoloLens에 합니다.

### <a name="windows-pc"></a>Windows PC

Windows Mixed Reality 헤드셋 PC에 연결을 사용 하는 경우 활성화 해야 **개발자 모드** PC에 있습니다.
1. 로 **설정**
2. 선택 **업데이트 및 보안**
3. 선택 **개발자를 위한**
4. 사용 하도록 설정 **개발자 모드**를 선택한 설정에 대 한 고 지 사항을 읽은 후 변경 내용을 적용 하려면 예 클릭 합니다.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Wi-fi-HoloLens 통해 앱을 배포 (첫 번째 범용)
1. 선택 된 **x86** 빌드 구성 앱에 대 한 ![x86 빌드 구성에 Visual Studio](images/x86setting.png)
2. 선택 **원격 컴퓨터** 배포 대상 드롭다운 메뉴에서 ![Visual Studio에서 원격 컴퓨터 배포 대상](images/remotemachinesetting.png)
3. 에 대 한 C++ 및 JavaScript 프로젝트로 이동 **프로젝트 > 속성 > 구성 속성 > 디버깅**합니다. 에 대 한 C# 프로젝트에 연결을 구성 하려면 자동으로 팝업 대화 상자 됩니다.
  a. 장치의 IP 주소를 입력 합니다 **주소** 하거나 **컴퓨터 이름** 필드입니다. 아래에 HoloLens에 IP 주소를 찾으려면 **설정 > 네트워크 및 인터넷 > 고급 옵션**, "내 ip 란?" Cortana 요청할 수 있습니다 또는
  b. 인증 모드를 설정 **유니버설 (암호화 되지 않은 프로토콜)**![Visual Studio에서 원격 연결 대화 상자](images/remotedeploy.png)
4. 선택 **디버그 > 디버깅 시작** 앱 배포 및 디버깅을 시작 하려면![Visual Studio에서 디버깅 하지 않고 시작](images/deploynodebugging.png)
5. PC에서 프로그램 HoloLens에 앱을 배포 하면 처음으로 PIN에 대 한 라는 메시지가 표시 됩니다. 수행 합니다 **장치 쌍** 아래 지침입니다.

HoloLens IP 주소가 변경 되 면로 이동 하 여 대상 컴퓨터의 IP 주소를 변경할 수 있습니다 **프로젝트 > 속성 > 구성 속성 > 디버깅**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>USB-HoloLens 통해 앱을 배포 (첫 번째 범용)
1. 선택 된 **x86** 빌드 구성 앱에 대 한 ![x86 빌드 구성에 Visual Studio](images/x86setting.png)
2. 선택 **장치** 배포 대상 드롭다운 메뉴에서![Visual Studio에서 장치 배포](images/buildsettingsusbdeploy.png)
3. 선택 **디버그 > 디버깅 시작** 앱 배포 및 디버깅을 시작 하려면![Visual Studio에서 디버깅 하지 않고 시작](images/deploynodebugging.png)
4. PC에서 프로그램 HoloLens에 앱을 배포 하면 처음으로 PIN에 대 한 라는 메시지가 표시 됩니다. 수행 합니다 **장치 쌍** 아래 지침입니다.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>몰입 형 헤드셋-로컬 PC에 앱 배포

사용자 PC에 연결 하는 Windows Mixed Reality 몰입 형 헤드셋을 사용 하는 경우 다음이 지침에 따라 또는 [혼합 현실 시뮬레이터](using-the-windows-mixed-reality-simulator.md)합니다. 이러한 경우에 배포 하 고 로컬 PC에 앱을 실행 합니다.
1. 선택 된 **x86** 하거나 **x64** 빌드 앱에 대 한 구성
2. 선택 **로컬 컴퓨터** 배포 대상 드롭다운 메뉴에서
3. 선택 **디버그 > 디버깅 시작** 앱 배포 및 디버깅을 시작 하려면

## <a name="pairing-your-device---hololens-1st-gen"></a>HoloLens 장치-페어링 (첫 번째 범용)

처음에 HoloLens에 Visual Studio에서 앱을 배포 하면 PIN에 대 한 라는 메시지가 표시 됩니다. 에 HoloLens, 설정 앱을 시작 하 여 PIN을 생성로 이동 **업데이트 > 개발자를 위한** 를 눌러 **쌍**합니다. PIN에 HoloLens;에 표시 됩니다. Visual Studio에서이 PIN을 입력 합니다. 페어링이 완료 한 후 누르세요 **수행** 대화 상자를 해제 하 여 HoloLens에 있습니다. 이 PC는 이제는 HoloLens와 연결 하 고 앱을 자동으로 배포 하는 일을 할 수 있습니다. 에 HoloLens에 앱을 배포 하는 데 사용 되는 모든 후속 PC에 대 한이 단계를 반복 합니다.

취소 쌍에 HoloLens와 연결 된 모든 컴퓨터에서 시작 합니다 **설정** 앱으로 이동 **업데이트 > 개발자 용** 탭 및 **지우기**합니다.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>HoloLens에 앱 배포 (첫 번째 gen) 에뮬레이터
1. 했는지  **[HoloLens 에뮬레이터 설치](install-the-tools.md)** 합니다.
2. 선택 된 **x86** 빌드 앱에 대 한 구성 합니다.
![x86 빌드 구성에 Visual Studio](images/x86setting.png)
3. 선택 **HoloLens 에뮬레이터** 배포 대상 드롭다운 메뉴에서![Visual Studio에서 에뮬레이터 대상](images/deployemulator.png)
4. 선택 **디버그 > 디버깅 시작** 앱 배포 및 디버깅을 시작 하려면![Visual Studio에서 디버깅 하지 않고 시작](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>그래픽 디버거

Visual Studio 그래픽 진단 도구를 작성 하 고 Holographic 앱을 최적화 하는 경우에 매우 유용 합니다. 참조 [MSDN의 Visual Studio 그래픽 진단](https://msdn.microsoft.com/library/hh315751.aspx) 전체 세부 정보에 대 한 합니다.

**그래픽 디버거를 시작 하려면**
1. 장치 또는 에뮬레이터를 대상으로 위의 지침에 따라
2. 로 **디버그 > 그래픽 > 진단 시작**
3. 첫 번째에 HoloLens를 사용 하 여이 작업을 수행 "액세스 거부" 오류가 발생할 수 있습니다. 업데이트 된 권한을 적용 하 고 다시 시도 허용 하 여 HoloLens 다시 부팅 합니다.

## <a name="profiling"></a>프로 파일링

Visual Studio 프로 파일링 도구를 사용 하면 앱의 성능 및 리소스 사용량을 분석할 수 있습니다. 이 CPU, 메모리, 그래픽, 최적화 및 사용 하 여 네트워크 도구가 포함 되어 있습니다. 참조 [MSDN의 디버깅 하지 않고 진단 도구 실행](https://msdn.microsoft.com/library/dn957936.aspx) 전체 세부 정보에 대 한 합니다.

**HoloLens를 사용 하 여 프로 파일링 도구를 시작 하려면**
1. 장치 또는 에뮬레이터를 대상으로 위의 지침에 따라
2. 로 **디버그 > 디버깅 하지 않고 진단 도구를 시작 하는 중...**
3. 사용 하려는 도구 선택
4. 클릭 **시작**
5. 첫 번째에 HoloLens를 사용 하 여이 작업을 수행 "액세스 거부" 오류가 발생할 수 있습니다. 업데이트 된 권한을 적용 하 고 다시 시도 허용 하 여 HoloLens 다시 부팅 합니다.

## <a name="debugging-an-installed-or-running-app"></a>설치 또는 실행 중인 앱 디버깅

Visual Studio 프로젝트에서 배포 하지 않고 설치 된 유니버설 Windows 앱을 디버그 하려면 Visual Studio를 사용할 수 있습니다. 설치 된 앱 패키지를 디버그 하려는 경우 또는 이미 실행 중인 앱을 디버그 하려는 경우에 유용 합니다.
1. 로 **디버그 다른 디버그-> 대상에 설치 된 앱 패키지 디버그->**
2. 선택 된 **원격 컴퓨터** HoloLens에 대 한 대상 또는 **로컬 컴퓨터** 몰입 형 헤드셋에 대 한 합니다.
3. 입력 장치의 **IP 주소**
4. 선택 된 **유니버설** 인증 모드
5. 창의 실행 및 비활성 응용 프로그램을 보여 줍니다. 디버그 하려는 것을 선택 합니다.
6. (관리, 네이티브, 혼합) 디버깅할 코드 형식을 선택 합니다.
7. 클릭 **첨부할** 또는 **시작**

## <a name="see-also"></a>참조
* [도구 설치](install-the-tools.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
* [유니버설 Windows 플랫폼 (UWP) 앱을 디버깅 및 배포](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [개발용 장치를 사용 하도록 설정](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
