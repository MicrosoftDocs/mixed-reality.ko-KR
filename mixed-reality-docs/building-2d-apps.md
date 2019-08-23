---
title: 혼합 현실 용 2D UWP 앱 업데이트
description: 이 문서에서는 HoloLens 및 Windows Mixed Reality 모던 헤드셋에서 실행 되도록 기존 2D 유니버설 Windows 플랫폼 앱을 업데이트 하는 방법을 간략하게 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 앱, UWP, 플랫 앱, HoloLens, 모던 헤드셋, 앱 모델, 뒤로 단추, 앱 바, dpi, 해상도, 크기 조정
ms.openlocfilehash: f9792a7e5fd9729bf9f5f632c699c74c58c10ddf
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414219"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>혼합 현실 용 2D UWP 앱 업데이트

Windows Mixed Reality를 사용 하면 사용자가 실제 또는 디지털 세계에서 사용자의 holograms을 확인할 수 있습니다. 핵심으로, 몰입 형 헤드셋 액세서리를 연결 하는 HoloLens와 데스크톱 Pc는 모두 Windows 10 장치입니다. 즉, 저장소에서 거의 모든 UWP (유니버설 Windows 플랫폼) 앱을 2D 앱으로 실행할 수 있습니다.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>혼합 현실 용 2D UWP 앱 만들기

2D 앱을 혼합 현실 헤드셋으로 가져오는 첫 번째 단계는 사용자의 데스크톱 모니터에서 표준 2D 앱으로 앱을 실행 하는 것입니다.

### <a name="building-a-new-2d-uwp-app"></a>새 2D UWP 앱 빌드

혼합 현실 용 새 2D 앱을 빌드하려면 표준 UWP (2D 유니버설 Windows 플랫폼) 앱을 빌드 하기만 하면 됩니다. 해당 앱에 대 한 다른 앱 변경은 필요 하지 않으므로 혼합 현실에서 슬레이트로 실행 됩니다.

2D UWP 앱 빌드를 시작 하려면 [첫 번째 앱 만들기](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) 문서를 확인 하세요.

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>기존 2D 스토어 앱을 UWP로 가져오기

저장소에 2D Windows 앱이 이미 있는 경우 먼저 UWP (Windows 10 유니버설 Windows 플랫폼)를 대상으로 하 고 있는지 확인 해야 합니다. 현재 스토어 앱에서 발생할 수 있는 모든 잠재적인 시작 지점은 다음과 같습니다.
<br>

|  시작점  |  AppX 매니페스트 플랫폼 대상  |  이 유니버설를 만드는 방법 | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight 응용 프로그램 매니페스트 |  [WinRT로 마이그레이션](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 범용  |  8.1 플랫폼 대상을 포함 하지 않는 AppX 매니페스트  |  [앱을 유니버설 Windows 플랫폼로 마이그레이션](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 스토어 8  |  플랫폼 대상이 포함 되지 않은 8 개의 AppX 매니페스트  |  [앱을 유니버설 Windows 플랫폼로 마이그레이션](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 스토어 8.1 유니버설  |  8.1 플랫폼 대상을 포함 하지 않는 AppX 매니페스트  |  [앱을 유니버설 Windows 플랫폼로 마이그레이션](https://msdn.microsoft.com/library/mt148501.aspx) | 

현재 2D Unity 앱이 Win32 앱 ("PC, Mac & Linux 독립 실행형" 빌드 대상)으로 빌드된 경우, 대신 Unity를 "유니버설 Windows 플랫폼" 빌드 대상으로 전환 하 여 혼합 현실를 대상으로 지정할 수 있습니다.

[아래](#publish-and-maintain-your-universal-app)Holographic 장치 제품군을 사용 하 여 HoloLens로 특별히 앱을 제한할 수 있는 방법에 대해 설명 합니다.

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Windows Mixed Reality 몰입 형 헤드셋에서 2D 앱 실행

응용 프로그램을 개발 하 고 모니터에서 시도 하는 데스크톱 컴퓨터에 2D 앱을 배포한 경우 이미 몰입 형 데스크톱 헤드셋에서 사용해 볼 준비가 된 것입니다.

혼합 현실 헤드셋 내의 시작 메뉴로 이동 하 여 해당 위치에서 앱을 시작 하면 됩니다. Desktop shell과 holographic shell은 모두 동일한 UWP 앱 집합을 공유 하므로 Visual Studio에서 배포한 앱은 이미 있어야 합니다.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>몰입 형 헤드셋 및 HoloLens를 모두 대상으로 지정

축하합니다. 이제 앱이 UWP (Windows 10 유니버설 Windows 플랫폼)를 사용 하 고 있습니다.

이제 앱은 데스크톱, 모바일, Xbox, Windows Mixed Reality 모던 헤드셋, HoloLens 및 향후 Windows 장치와 같은 오늘날의 Windows 장치에서 실행할 수 있습니다. 그러나 실제로 이러한 모든 장치를 대상으로 하려면 앱이 Windows 유니버설 장치 제품군을 대상으로 하는지 확인 해야 합니다.

### <a name="change-your-device-family-to-windowsuniversal"></a>장치 패밀리를 Windows로 변경

이제 Windows 10 UWP 앱을 HoloLens에서 실행할 수 있도록 AppX 매니페스트로 이동 하겠습니다.
* **Visual Studio** 를 사용 하 여 앱의 솔루션 파일을 열고 앱 패키지 매니페스트로 이동 합니다.
* 솔루션에서 appxmanifest.xml 파일을 마우스 오른쪽 단추로 클릭 하 고 **코드 보기** 로 이동 합니다 **.**<br>
  ![솔루션 탐색기의 appxmanifest.xml](images/openappxmanifest-500px.png)<br>
* 종속성 섹션의 대상 플랫폼이 Windows의 유니버설 인지 확인 합니다.
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Save!

개발 환경에 Visual Studio를 사용 하지 않는 경우 원하는 텍스트 편집기에서 **appxmanifest.xml** 를 열어 **Windows. 유니버설** *targetdevicefamily*를 대상으로 할 수 있습니다.

### <a name="run-in-the-hololens-emulator"></a>HoloLens 에뮬레이터에서 실행

이제 UWP 앱이 "Windows 유니버설"를 대상으로 하기 때문에 앱을 빌드하고 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)에서 실행 하겠습니다.
* [HoloLens 에뮬레이터를 설치](install-the-tools.md)했는지 확인 합니다.
* Visual Studio에서 앱에 대 한 **x86** 빌드 구성을 선택 합니다.

  ![Visual Studio의 x86 빌드 구성](images/x86setting.png)<br>
* 배포 대상 드롭다운 메뉴에서 **HoloLens 에뮬레이터** 를 선택 합니다.

  ![배포 대상 목록의 HoloLens 에뮬레이터](images/deployemulator-500px.png)<br>
* **디버그 > 디버깅 시작** 을 선택 하 여 앱을 배포 하 고 디버깅을 시작 합니다.
* 에뮬레이터가 시작 되 고 앱이 실행 됩니다.
* 키보드, 마우스 및/또는 Xbox 컨트롤러를 사용 하 여 응용 프로그램을 시작할 수 있습니다.

  ![UWP 샘플로 로드 된 HoloLens 에뮬레이터](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>다음 단계

이 시점에서 다음 두 가지 중 하나가 발생할 수 있습니다.
1. 앱이 에뮬레이터에 배치 된 후 시작을 표시 하 고 실행을 시작 합니다. 굉장한!
2. 또는 2D 홀로그램에 대 한 로딩 애니메이션이 표시 되 면 로드는 중지 되 고 시작 화면에 앱이 표시 됩니다. 즉, 오류가 발생 하 여 혼합 현실에서 앱을 개발 하는 방법을 이해 하는 데 더 많은 조사가 필요 합니다.

UWP 앱이 HoloLens에서 시작 되지 않도록 하는 것이 무엇 인지 알 수 있도록 하려면 디버깅 해야 합니다.

### <a name="running-your-uwp-app-in-the-debugger"></a>디버거에서 UWP 앱 실행

이러한 단계는 Visual Studio 디버거를 사용 하 여 UWP 앱을 디버깅 하는 과정을 안내 합니다.
* 아직 수행 하지 않은 경우 Visual Studio에서 솔루션을 엽니다. 대상을 **HoloLens 에뮬레이터** 로 변경 하 고 빌드 구성을 **x 86**으로 변경 합니다.
* **디버그 > 디버깅 시작** 을 선택 하 여 앱을 배포 하 고 디버깅을 시작 합니다.
* 마우스, 키보드 또는 Xbox 컨트롤러를 사용 하 여 응용 프로그램을 전 세계에 두십시오.
* 이제 Visual Studio가 앱 코드에서 중단 됩니다.
  - 처리 되지 않은 오류로 인해 앱이 즉시 중단 되거나 중단 되지 않는 경우 앱의 핵심 기능에 대 한 테스트 통과를 통해 모든 것이 실행 중이 고 작동 하는지 확인 합니다. 아래 그림과 같은 오류가 표시 될 수 있습니다 (처리 중인 내부 예외). 앱 환경에 영향을 주는 내부 오류가 발생 하지 않도록 하려면 자동화 된 테스트 및 단위 테스트를 실행 하 여 모든 항목이 예상 대로 작동 하는지 확인 합니다.

![시스템 예외를 보여 주는 UWP 샘플로 로드 된 HoloLens 에뮬레이터](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>UI 업데이트

이제 UWP 앱이 모던 헤드셋 및/또는 HoloLens에서 2D 홀로그램로 실행 되므로 멋진 모습을 확인할 수 있습니다. 고려해 야 할 몇 가지 사항은 다음과 같습니다.
* Windows Mixed Reality는 고정 해상도로 모든 2D 앱을 실행 하 고 853x480 유효 픽셀에 해당 하는 DPI를 실행 합니다. 설계가이 규모에서 구체화 되어야 하는 경우 아래 디자인 지침을 검토 하 여 HoloLens 및 몰입 형 헤드셋의 경험을 향상 시키는 것이 좋습니다.
* Windows Mixed Reality는 2d 라이브 타일을 [지원 하지](app-model.md) 않습니다. 핵심 기능에서 라이브 타일에 대 한 정보를 표시 하는 경우 해당 정보를 다시 앱으로 이동 하거나 [3d 앱 다운로드](3d-app-launcher-design-guidance.md)를 탐색 하는 것이 좋습니다.

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 앱 보기 해상도 및 배율 인수

![반응 형 디자인에서](images/scale-500px.png)

Windows 10은 모든 시각적 디자인을 실제 화면 픽셀에서 **유효 픽셀로**이동 합니다. 즉, 개발자는 효율적인 픽셀에 대 한 Windows 10 인적 인터페이스 지침에 따라 UI를 디자인 하 고, Windows 크기 조정을 통해 장치, 해상도, DPI 등의 유용성에 대 한 효과적인 픽셀 크기를 보장 합니다. 이 [빌드](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)에 [대 한 자세한 내용은 MSDN의 유용한](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) 정보를 참조 하세요.

다양 한 거리에서 전 세계에 앱을 제공 하는 고유한 기능을 사용 하는 경우에도 대화형/제스처를 사용 하 여 최상의 가독성을 얻을 수 있도록 TV와 유사한 거리를 표시 하는 것이 좋습니다. 이로 인해 Mixed Reality 홈의 가상 슬레이트는 다음 위치에 플랫 UWP 보기를 표시 합니다.

**1280x720, 150% DPI** (853x480 유효 픽셀)

이 해상도에는 다음과 같은 여러 가지 이점이 있습니다.
* 이 유효 픽셀 레이아웃은 태블릿 또는 소형 데스크톱과 동일한 정보 밀도를 가집니다.
* Xbox One에서 실행 되는 UWP 앱의 고정 DPI 및 유효 픽셀과 일치 하므로 장치 간에 원활한 환경을 사용할 수 있습니다.
* 이 크기는 전 세계의 앱에 대 한 운영 거리 범위에서 크기를 조정할 때 적절 하 게 보입니다.

### <a name="2d-app-view-interface-design-best-practices"></a>2D 앱 뷰 인터페이스 디자인 모범 사례

**시겠습니까**
* 스타일, 글꼴 크기 및 단추 크기에 대 한 [Windows 10 휴먼 인터페이스 지침 (gg)](https://dev.windows.com/design) 을 따릅니다. HoloLens는 앱이 호환 되는 앱 패턴, 읽을 수 있는 텍스트 크기 및 적절 한 적중 대상 크기 조정 작업을 수행 하도록 합니다.
* UI가 응답성이 뛰어난 [디자인](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) 을 위한 모범 사례를 준수 하는지 확인 하 고 HoloLen의 고유한 해상도 및 DPI를 확인 합니다.
* Windows의 "light" 색 테마 권장 사항을 사용 합니다.

**안 함:**
* 혼합 현실에서는 사용자가 헤드셋에서 친숙 한 경험을 사용할 수 있도록 UI를 너무 크게 변경 합니다.

### <a name="understand-the-app-model"></a>앱 모델 이해

혼합 현실 용 [앱 모델](app-model.md) 은 많은 앱이 함께 살고 있는 혼합 현실 홈을 사용 하도록 설계 되었습니다. 이는 여러 개의 2D 앱을 한 번에 실행 하는 데스크톱에 해당 하는 혼합 현실 이라고 생각 하면 됩니다. 앱의 수명 주기, 타일 및 앱의 다른 주요 기능에 영향을 미칩니다.

### <a name="app-bar-and-back-button"></a>앱 바 및 뒤로 단추

2D 보기는 해당 콘텐츠 위의 앱 표시줄로 데코 레이트 됩니다. 앱 바에는 앱 별 개인 설정의 두 지점이 있습니다.

**제목:** 응용 프로그램 인스턴스와 연결 된 타일의 *displayname* 을 표시 합니다.

**뒤로 단추:** 누를 때 *[요청](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 된 이벤트를 발생 시킵니다. 뒤로 단추 표시 유형은 *[Systemnavigationmanager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 에 의해 제어 됩니다.

![2D 앱 보기의 앱 바 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*2D 앱 보기의 앱 바 UI*

### <a name="test-your-2d-apps-design"></a>2D 앱 디자인 테스트

앱을 테스트 하 여 텍스트를 읽을 수 있고, 단추가 가능, 전체 앱이 올바른지 확인 하는 것이 중요 합니다. 해상도가 1280x720 @150%로 설정 된 데스크톱 헤드셋, HoloLens, 에뮬레이터 또는 터치 장치를 [테스트](testing-your-app-on-hololens.md)할 수 있습니다.

## <a name="new-input-possibilities"></a>새 입력 가능성

HoloLens는 고급 깊이 센서를 사용 하 여 전 세계를 보고 사용자를 확인 합니다. 이를 통해 [블 룸](gestures.md#bloom) 및 [공중 탭](gestures.md#air-tap)과 같은 고급 손 제스처를 사용할 수 있습니다. 또한 강력한 마이크는 [음성 환경을](voice-input.md)사용할 수 있습니다.

데스크톱 헤드셋을 사용 하면 사용자가 동작 컨트롤러를 사용 하 여 앱을 가리키고 조치를 취할 수 있습니다. 또한 사용자는 게임 패드를 사용 하 여 개체를 해당 응시로 대상으로 지정할 수 있습니다.

Windows는 UWP 앱에 대해 이러한 복잡성을 모두 처리 하 고, [응시](gaze.md), 제스처, 음성 및 동작 컨트롤러 입력을 입력 메커니즘을 추상화 하는 [포인터 이벤트](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) 로 변환 합니다. 예를 들어 사용자가 손 모양으로 마우스를 이동 하거나 이동 컨트롤러에서 Select 트리거를 끌어올 수 있지만, 2D 응용 프로그램은 입력의 출처를 알 필요가 없습니다. 즉, 터치 스크린에서와 같이 2D touch press만 표시 됩니다.

UWP 앱을 HoloLens로 가져올 때 입력에 대해 알고 있어야 하는 개략적인 개념/시나리오는 다음과 같습니다.
* [응시](gaze.md) 는 호버 이벤트로 바뀌고,이 이벤트는 예기치 않게 메뉴, flyouts 또는 기타 사용자 인터페이스 요소를 앱 주위에 gazing 하 여 팝업 할 수 있습니다.
* 응시는 마우스 입력 만큼 정확 하지 않습니다. 터치 편한 모바일 응용 프로그램과 마찬가지로 HoloLens에 적절 한 크기의 적중 대상을 사용 합니다. 앱의 가장자리 근처에 있는 작은 요소는 특히 상호 작용 하기가 어렵습니다.
* 사용자는 스크롤에서 끌어서 두 손가락 이동으로 이동 하도록 입력 모드를 전환 해야 합니다. 터치 입력 용으로 설계 된 앱의 경우 두 손가락 이동 후에 주요 기능이 잠기지 않도록 합니다. 그렇다면 두 손가락 이동을 시작할 수 있는 단추와 같은 대체 입력 메커니즘을 고려해 야 합니다. 예를 들어 맵 앱은 두 손가락 패닝으로 확대할 수 있지만 한 번 클릭으로 동일한 확대/축소 상호 작용을 시뮬레이트하는 더하기, 빼기 및 회전 단추가 있습니다.

[음성 입력](voice-input.md) 은 혼합 현실 환경의 중요 한 부분입니다. 헤드셋을 사용할 때 Windows 10 Cortana를 켜는 모든 음성 Api를 사용 하도록 설정 했습니다.

## <a name="publish-and-maintain-your-universal-app"></a>유니버설 앱 게시 및 유지 관리

앱이 실행 되 고 있으면 앱을 패키지 하 여 [Microsoft Store에 제출](submitting-an-app-to-the-microsoft-store.md)합니다.

## <a name="see-also"></a>참조
* [앱 모델](app-model.md)
* [응시](gaze.md)
* [지우는](gestures.md)
* [모션 컨트롤러](motion-controllers.md)
* [음성 입력 ](voice-input.md)
* [Microsoft Store에 앱 제출](submitting-an-app-to-the-microsoft-store.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
