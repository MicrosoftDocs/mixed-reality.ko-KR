---
title: 혼합된 현실에 대 한 2D UWP 앱 업데이트
description: 이 문서는 HoloLens 및 Windows Mixed Reality 몰입 형 헤드셋에서 실행 되도록 기존 2D 유니버설 Windows 플랫폼 앱 업데이트를 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 앱을 UWP 앱 플랫, HoloLens, 몰입 형 헤드셋을 앱 모델을 다시 앱 바, 단추, dpi, 해상도, 크기 조정
ms.openlocfilehash: 35a2e7774a79e35893821467f7e9ef8c004efa20
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602185"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>혼합된 현실에 대 한 2D UWP 앱 업데이트

Windows Mixed Reality에 물리적 또는 디지털 세계에서와 관련해 서, 올바른 것 처럼 홀로그램을 보려는 사용자 수 있습니다. 근본적으로 HoloLens 및 몰입 형 헤드셋 accessories로 연결한 데스크톱 Pc는 Windows 10 장치 즉, 거의 모든 유니버설 Windows 플랫폼 (UWP) 앱 스토어에서 2D 앱으로 실행할 수 있다고 합니다.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>혼합된 현실에 대 한 2D UWP 앱 만들기

혼합된 현실 헤드셋 2D 앱을 가져오는 첫 번째 단계는 앱을 데스크톱 모니터에서 표준 2D 앱으로 실행 하는 것입니다.

### <a name="building-a-new-2d-uwp-app"></a>새 2D UWP 앱 빌드

혼합된 현실에 대 한 2D 새 앱을 빌드하려면 표준 2D 유니버설 Windows 플랫폼 (UWP) 앱을 빌드하면 됩니다. 기타 앱 변경은 필요 하지 않습니다 다음 혼합된 현실에서 슬레이트를 실행 하는 앱에 대 한 합니다.

2D UWP 앱 빌드 시작을 확인 합니다 [첫 번째 앱 만들기](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) 문서.

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>기존 2D 스토어 앱을 UWP로 가져오기

저장소에서 2D Windows 앱을 이미 있는 경우 Windows 10 유니버설 Windows 플랫폼 (UWP) 대상를 먼저 확인 해야 합니다. 다음은 모든 잠재적인 시작 지점을 스토어 앱을 사용 하 여 지금 할 수 있습니다.
<br>

|  시작 지점  |  AppX 매니페스트 플랫폼 대상  |  이 유니버설을 확인 하는 방법 | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight 응용 프로그램 매니페스트 |  [WinRT로 마이그레이션](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 유니버설  |  8.1 대상 플랫폼을 포함 하지 않는 AppX 매니페스트  |  [유니버설 Windows 플랫폼 앱 마이그레이션](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 스토어 8  |  플랫폼 대상에 포함 되지 않은 8 AppX 매니페스트  |  [유니버설 Windows 플랫폼 앱 마이그레이션](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 스토어 8.1 유니버설  |  8.1 대상 플랫폼을 포함 하지 않는 AppX 매니페스트  |  [유니버설 Windows 플랫폼 앱 마이그레이션](https://msdn.microsoft.com/library/mt148501.aspx) | 

2D Unity 앱을 지금 (의 "PC, Mac 및 Linux 독립 실행형" 빌드 대상)는 Win32 응용 프로그램으로 개발 된 경우에 대신 "유니버설 Windows 플랫폼" 빌드 대상에 Unity를 전환 하 여 혼합된 현실을 대상 수 있습니다.

Windows.Holographic 장치 제품군을 사용 하 여 HoloLens에 맞게 앱을 제한할 수 있습니다 하는 방법에 대해 알아보겠습니다 [아래](#publish-and-maintain-your-universal-app)합니다.

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Windows Mixed Reality 몰입 형 헤드셋에서 2D 앱 실행

2D 앱 개발 및 모니터에서이 시도 하는 데스크톱 컴퓨터를 배포한 경우는 몰입 형 데스크톱 헤드셋에서 시도할 준비가 이미 완료 되었습니다!

혼합된 현실 헤드셋 내 시작 메뉴로 이동 하 고 여기에서 앱을 시작 하기만 됩니다. 데스크톱 셸 및 holographic 셸 UWP 앱의 동일한 집합을 공유 하 고 있으므로 앱 이미 있는 것은 Visual Studio에서 배포한 후 키를 누릅니다.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>몰입 형 헤드셋 및 HoloLens 모두 대상으로 지정

축하합니다. 이제 앱을 Windows 10 유니버설 Windows 플랫폼 (UWP)를 사용 합니다.

이제 앱에서 데스크톱, 모바일, Xbox, Windows Mixed Reality 몰입 형 헤드셋, HoloLens도 향후 Windows 장치 등 오늘날의 Windows 장치에서 실행할 수 있습니다. 그러나 실제로 모든 해당 장치를 대상으로 해야 Windows.Universal 장치 제품군을 대상으로 앱을 확인 합니다.

### <a name="change-your-device-family-to-windowsuniversal"></a>장치 제품군에 Windows.Universal 변경

이제 Windows 10 UWP 앱 HoloLens에서 실행할 수 있도록 프로그램 AppX 매니페스트로 이동 하겠습니다.
* 앱의 솔루션 파일을 엽니다 **Visual Studio** 이동한 다음 앱 패키지 매니페스트
* 마우스 오른쪽 단추로 클릭 합니다 **Package.appxmanifest** 솔루션의 파일을 이동할 **코드 보기**<br>
  ![솔루션 탐색기에서 package.appxmanifest](images/openappxmanifest-500px.png)<br>
* 종속성 섹션에 Windows.Universal 대상 플랫폼 확인
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 저장.

개발 환경에 대 한 Visual Studio를 사용 하지 않는 경우 열 수 있습니다 **AppXManifest.xml** 대상으로 하는 확인 하기 위해 선택한 텍스트 편집기에는 **Windows.Universal**  *TargetDeviceFamily*합니다.

### <a name="run-in-the-hololens-emulator"></a>HoloLens 에뮬레이터에서 실행

이제는 UWP 앱이 "windows.universal" 인 대상으로, 보겠습니다 앱 빌드 및 실행 합니다 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)합니다.
* 했는지 [HoloLens 에뮬레이터 설치](install-the-tools.md)합니다.
* Visual Studio에서 선택 합니다 **x86** 빌드 앱에 대 한 구성

  ![x86 빌드 구성에 Visual Studio](images/x86setting.png)<br>
* 선택 **HoloLens 에뮬레이터** 배포 대상 드롭다운 메뉴에서

  ![배포 대상 목록에 HoloLens 에뮬레이터](images/deployemulator-500px.png)<br>
* 선택 **디버그 > 디버깅 시작** 앱 배포 및 디버깅을 시작 합니다.
* 에뮬레이터 시작 되며 앱을 실행 합니다.
* 키보드, 마우스 및/또는 Xbox 컨트롤러를, 시작 전 세계에 앱을 배치 합니다.

  ![HoloLens 에뮬레이터 UWP 샘플을 사용 하 여 로드](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>다음 단계

이 시점에서 두 가지 중 하나가 발생할 수 있습니다.
1. 앱의 시작을 표시 되며 에뮬레이터에 배치 된 후 실행을 시작! 굉장한!
2. 또는 2D 홀로그램에 대 한 로드 애니메이션, 표시 되 면 로드 중지 되 고 시작 화면에서 해당 앱에만 나타납니다. 즉, 잘못 된 것을 앱에 활기를 혼합 현실에서 하는 방법을 이해 하려면 자세한 조사 걸립니다.

HoloLens에서 시작할 수 없는 원인을 UWP 앱의 맨 아래를 이동 하려면 디버그 해야 합니다.

### <a name="running-your-uwp-app-in-the-debugger"></a>디버거에서 UWP 앱 실행

다음이 단계를 안내 Visual Studio 디버거를 사용 하 여 UWP 앱을 디버깅 합니다.
* 이미 않았다면 Visual Studio에서 솔루션을 엽니다. 대상에 변경 된 **HoloLens 에뮬레이터** , 빌드 구성을 **x86**합니다.
* 선택 **디버그 > 디버깅 시작** 앱 배포 및 디버깅을 시작 합니다.
* 마우스, 키보드 또는 Xbox 컨트롤러를 사용 하 여 전 세계에 앱을 배치 합니다.
* Visual Studio는 앱 코드에서 이제 어딘가에 중단 됩니다.
  - 앱 즉시 충돌 또는 처리 되지 않은 오류로 인해 디버거를 중단 하지 않습니다, 경우에 모든 실행 되 고 있는지와 작동 하도록 앱의 핵심 기능 중 테스트 단계를 통해 이동 합니다. (내부 예외를 처리 하는) 아래의 같은 오류가 표시 될 수 있습니다. 내부 오류는 앱의 경험에 영향을 주는 놓치지 되도록 자동화 된 테스트 및 예상 대로 작동 하는 모든 항목이 있는지 확인 하는 단위 테스트를 통해 실행 합니다.

![HoloLens 에뮬레이터 시스템 예외를 보여 주는 UWP 샘플을 사용 하 여 로드](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>UI를 업데이트 합니다.

이제 몰입 형 헤드셋 및/또는 2D 홀로그램으로 HoloLens로 UWP 앱 실행 중이면 다음 만들 멋진 보이도록 합니다. 고려할 사항은 다음과 같습니다.
* Windows Mixed Reality 853 x 480 효과적인 픽셀로 고정된 해상도와 DPI는 2D 모든 앱을 실행 됩니다. 디자인 하는 경우이 규모 구체화 해야 하는 것이 좋습니다. 및 HoloLens 및 몰입 형 헤드셋 환경을 개선 하려면 아래 디자인 지침을 검토 합니다.
* Windows Mixed Reality [지원 하지 않습니다](app-model.md) 2D 라이브 타일입니다. 핵심 기능에는 라이브 타일에 정보를 보여주며, 해당 정보를 앱으로 다시 이동 하는 것이 좋습니다. 아니면 탐색 [3D 앱 시작 관리자](3d-app-launcher-design-guidance.md)합니다.

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 앱 보기 확인 및 확장 비율

![반응 형 디자인에서](images/scale-500px.png)

실제 화면 픽셀에서 모든 시각적 디자인을 이동 하는 Windows 10 **효과적인 픽셀**합니다. 즉, 개발자가 Windows 10 Human Interface Guidelines 효과적인 픽셀에 대 한 다음 해당 UI를 디자인 하 고 Windows 확장을 통해 이러한 효과적인 픽셀에 적절 한 크기 등 여러 장치에서 해상도, DPI, 유용성에 대 한 합니다. 이 참조 하세요 [MSDN의 훌륭한 읽기](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) 이 뿐만 아니라 자세한 [빌드 프레젠테이션](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)합니다.

거리의 범위에서 사용자 환경에서 앱을 배치할 고유 기능을 사용 하더라도 TV 모양의 보기 거리는 최상의 가독성 및 게이즈/제스처와 상호 작용을 생성 하기 위해 권장 됩니다. 따라서 혼합 현실 집에서 슬레이트를 가상 플랫 UWP 보기에 표시 됩니다.

**1280 x 720, 150 %DPI** (853 x 480 효과적인 픽셀)

이 해결 방법 몇 가지 이점이 있습니다.
* 태블릿 또는 작은 데스크톱으로 동일한 정보 밀도 대 한이 효과적인 픽셀 레이아웃을 해야 합니다.
* 고정된 DPI 및 Xbox One 장치 간에 원활한 환경을 사용 하도록 설정에서 실행 중인 UWP 앱에 대 한 효과적인 픽셀 일치 합니다.
* 이 크기의 거리 환경에서 앱에 대 한 운영 범위 간에 크기를 조정할 때 정상적으로 진행 합니다.

### <a name="2d-app-view-interface-design-best-practices"></a>2D 앱 보기 인터페이스 디자인 모범 사례

**Do:**
* 수행 합니다 [Windows 10 휴먼 인터페이스 지침 (HIG)](https://dev.windows.com/design) 스타일, 글꼴 크기 및 단추 크기에 대 한 합니다. HoloLens는에 게 앱은 호환 앱 패턴, 읽을 수 있는 텍스트 크기 및 적절 한 적중 횟수 대상 크기 조정 작업을 수행 합니다.
* UI 다음과 같이 프로그램에 대 한 모범 사례를 확인 [반응 형 디자인](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) 보기 HoloLen의 고유한 해상도와 DPI 좋습니다.
* Windows에서 "밝은" 색 테마 권장 사항을 사용 합니다.

**안 함:**
* 혼합된 현실 등 사용자에 게 친숙 한 환경을 헤드셋 내부 및 외부에 있는 경우 UI을 너무 크게 변경 합니다.

### <a name="understand-the-app-model"></a>응용 프로그램 모델 이해

합니다 [앱 모델](app-model.md) 혼합된 현실 많은 앱 함께 live 혼합 현실 가정용을 사용 하도록 설계 된에 대 한 합니다. 생각할 바탕 화면 혼합된 현실 해당 하는 한 번에 많은 2D 앱을 실행 합니다. 이 앱 수명 주기, 타일 및 앱의 다른 주요 기능에 영향을 줍니다.

### <a name="app-bar-and-back-button"></a>앱 바 및 뒤로 단추

2D 뷰 콘텐츠 위에 앱 막대를 장식 합니다. 앱 바에는 앱 별 개인 설정의 두 요소가:

**제목:** 표시 된 *displayname* 앱 인스턴스와 연결 된 타일

**뒤로 단추:** 발생 합니다 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 누르면 이벤트입니다. 뒤로 단추 표시에 의해 제어 됩니다  *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 합니다.

![앱 모음 UI에서 2D 앱 보기](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*앱 모음 UI에서 2D 앱 보기*

### <a name="test-your-2d-apps-design"></a>2D 앱의 디자인을 테스트

텍스트를 읽을 수 있는 단추는 대상 지정이 가능 합니다 하 고 전체 앱 올바르면 되도록 앱을 테스트 하는 것이 반드시 합니다. 할 수 있습니다 [테스트할](testing-your-app-on-hololens.md) 데스크톱 헤드셋는 HoloLens, 에뮬레이터, 또는 1280 x 720는 해상도 사용 하 여 터치 장치에 @150%입니다.

## <a name="new-input-possibilities"></a>새 입력된 가능성

HoloLens 고급 깊이 센서를 사용 하 여 전 세계 보고 사용자를 참조 하세요. 와 같은 고급 손 제스처를 따라서 [블 룸](gestures.md#bloom) 하 고 [어 탭](gestures.md#air-tap)합니다. 강력한 마이크 사용 하도록 설정할 수도 [환경을 음성](voice-input.md)합니다.

데스크톱 헤드셋을 사용 하 여 사용자 앱에서 가리키고 취할 동작 컨트롤러를 사용할 수 있습니다. 또한 해당 게이즈를 사용 하 여 개체를 대상으로 하는 gamepad를 사용할 수 있습니다.

Windows 담당 모든 UWP 앱에 대 한이 복잡성이 변환에 [gaze](gaze.md), 제스처와 음성 및 동작에 대 한 컨트롤러 입력 [포인터 이벤트](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) 입력된 메커니즘을 추상화 하는 합니다. 예를 들어 사용자 자신의 손으로 어 탭을 완료 또는 선택 트리거 동작 컨트롤러에서 가져온 경우 아니지만 2D 응용 프로그램에 알고 있는 입력에서 가져온 키를 눌러을 2D 터치 터치 스크린에서 작업 하는 경우만 표시 됩니다.

HoloLens을 UWP 앱을 제공 하는 경우 입력에 대 한 이해 해야 높은 수준의 개념/시나리오는 다음과 같습니다.
* [Gaze](gaze.md) 예기치 않게 메뉴, 플라이 아웃 또는 기타 사용자 인터페이스 요소 앱 주위 gazing 하 여 팝업을 트리거할 수 있는 가리키기 이벤트로 변환 합니다.
* 응시도 마우스 입력으로 정확 하지 않습니다. 사용 하 여 HoloLens, 유사한 기능은 터치 하기 쉬운 모바일 응용 프로그램에 대 한 적중 횟수 대상 크기가 적절 하 게 합니다. 앱의 가장자리에 가깝게 작은 요소는 특히 하드 상호 작용할 수 있습니다.
* 사용자가 스크롤 두 손가락 이동으로 끌어서 이동할 입력된 모드를 전환 해야 합니다. 터치 입력에 대 한 앱 디자인 된 경우에 주요 기능 두 손가락 이동 뒤 잠겨 있는지 확인 하는 것이 좋습니다. 그렇다면 두 손가락 이동 시작할 수 있는 단추와 같은 대체 입력된 메커니즘 것이 좋습니다. 예를 들어 맵 앱 두 손가락 이동으로 확대/축소 수 더하기, 빼기,에 있고 단일 클릭 만으로 동일한 확대/축소 상호 작용을 시뮬레이션 하는 단추를 회전 합니다.

[입력 음성](voice-input.md) 혼합된 현실 환경의 중요 한 부분입니다. 음성 헤드셋을 사용 하는 경우 Cortana를 강화 하는 Windows 10에 있는 Api의 모든 활성화 했습니다.

## <a name="publish-and-maintain-your-universal-app"></a>게시 및 유니버설 앱을 유지 관리

앱 시작 및 실행 되 면 앱을 패키지 [Microsoft Store 제출](submitting-an-app-to-the-microsoft-store.md)합니다.

## <a name="see-also"></a>참조
* [앱 모델](app-model.md)
* [응시](gaze.md)
* [제스처](gestures.md)
* [컨트롤러 동작](motion-controllers.md)
* [음성](voice-input.md)
* [Microsoft Store 앱 제출](submitting-an-app-to-the-microsoft-store.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
