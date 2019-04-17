---
title: 앱 모델
description: Windows Mixed Reality 유니버설 Windows 플랫폼, 모델 및 최신 Windows 앱에 대 한 환경에서 제공 하는 앱 모델을 사용 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP 앱 모델, 수명 주기를 일시 중단, 다시 시작, 타일, 뷰, 계약
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602998"
---
# <a name="app-model"></a>앱 모델

Windows Mixed Reality 제공한 앱 모델을 사용 하 여 [유니버설 Windows 플랫폼](https://docs.microsoft.com/windows/uwp/get-started/) (UWP) 모델 및 최신 Windows 앱에 대 한 환경. 설치, 업데이트, 버전 관리 된 앱은 하는 방법을 정의 하 고 안전 하 고 완전히 제거 하는 UWP 앱 모델. -방법 앱 실행, 중지 및 종료-응용 프로그램 수명 주기 및 방법 상태를 보존할 수 있기를 제어 합니다. 또한 통합 및 운영 체제, 파일 및 다른 앱의 상호 작용을 다룹니다.

![2D 앱을 Windows Mixed Reality 홈 점심 시간대를 영역에 정렬](images/20160112-055908-hololens-500px.jpg)<br>
*Windows Mixed Reality 홈 정렬 2D 뷰를 사용 하 여 앱*

## <a name="app-lifecycle"></a>앱 수명 주기

혼합된 현실 앱의 수명 주기는 배치, 시작, 종료 및 제거와 같은 표준 앱 개념 포함 됩니다.

### <a name="placement-is-launch"></a>Placement가 시작

앱 타일을 배치 하 여 혼합된 현실에서 모든 앱이 시작 (방금를 [Windows 보조 타일이](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile))에 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md). 앱 타일을에서 배치를 시작 앱을 실행 합니다. 이 앱 타일 유지 하 고 배치 되는 위치에 유지 하면 언제 든 지에 대 한 시작 관리자를 앱에 다시 확인 하려고 합니다. 예: 역할입니다.

![배치는 전 세계에서 보조 타일 배치](images/slide1-600px.png)<br>
*배치는 전 세계에서 보조 타일 배치*

배치 완료 되는 즉시 (배치 하 여 시작 된 경우가 아니면를 [앱을](app-model.md#protocols) 시작), 앱을 시작 합니다. Windows Mixed Reality 제한 된 수의 앱을 한 번에 실행할 수 있습니다. 배치 하는 앱을 시작 하는 즉시 저장할 때마다 앱의 마지막 상태 스크린샷 해당 앱 타일이를 두면 다른 활성 앱 중단 될 수 있습니다. 참조 [Windows 10 UWP 앱 수명 주기](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) 다시 시작 및 기타 앱 수명 주기 이벤트 처리에 대 한 자세한 내용은 합니다.

![앱 타일에 배치한 후 실행을 시작](images/slide2-500px.png) ![실행을 일시 중단 되거나 실행 되지 않는 앱에 대 한 상태 다이어그램](images/ic576232-500px.png)<br>
*왼쪽: 타일을 배치한 후 앱 실행을 시작 합니다. 오른쪽: 실행 중, 일시 중단 또는 실행 되지 않는 앱에 대 한 상태 다이어그램입니다.*

### <a name="remove-is-closeterminate-process"></a>제거는 닫기/종료 프로세스

전 세계에서 배치 앱 타일을 제거 하면이 기본 프로세스를 닫습니다. 이 앱은 종료를 보장 하거나 문제가 앱을 다시 시작에 대 한 유용할 수 있습니다.

### <a name="app-suspensiontermination"></a>앱 일시 중단/종료

에 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md), 사용자가 앱에 대 한 여러 진입점을 만들 수 있습니다. 시작 메뉴에서 앱을 시작 하 고 전 세계의 앱 타일을 배치 하 여이 수행 합니다. 각 앱 타일 다른 진입점으로 작동 하 고 별도 타일 인스턴스를 시스템 있습니다. 에 대 한 쿼리 [SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) 하면를 **SecondaryTile** 각 앱 인스턴스에 대 한 합니다.

UWP 앱을 일시 중단 때 현재 상태의 스크린샷을 가져옵니다.

![일시 중단 된 앱에 대 한 스크린샷이 나와 있습니다.](images/slide9-800px.png)<br>
*일시 중단 된 앱에 대 한 스크린샷이 나와 있습니다.*

다른 Windows 10 셸에에서 하나의 주요 차이점은 앱을 통해 앱 인스턴스 활성화 알림을 어떻게 합니다 [CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) 하 고 [CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) 이벤트입니다.

|  시나리오 |  다시 시작  |  활성화됨 | 
|----------|----------|----------|
|  시작 메뉴에서 앱의 새 인스턴스를 시작 합니다.  |   |  **활성화** 새 [TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  시작 메뉴에서 앱의 두 번째 인스턴스를 시작 합니다.  |   |  **활성화** 새 **TileId** | 
|  현재 활성화 되지 않은 앱의 인스턴스를 선택 합니다.  |   |  **활성화** 사용 하 여 합니다 **TileId** 인스턴스와 연결 된 | 
|  다른 앱을 선택한 다음 이전에 활성 인스턴스를 선택 합니다.  |  **다시 시작** 발생  |  | 
|  다른 앱을 선택한 다음 이전에 활성화 되지 않은 인스턴스를 선택 합니다.  |  **다시 시작** 발생  |  그런 다음 **Activated** 사용 하 여 합니다 **TileId** 인스턴스와 연결 된 | 

### <a name="extended-execution"></a>확장된 실행

경우에 따라 앱을 백그라운드에서 작업을 수행 하거나 오디오 재생을 계속 해야 합니다. [백그라운드 작업](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) HoloLens에서 사용할 수 있습니다.

![앱이 백그라운드에서 실행할 수 있습니다.](images/slide10-800px.png)<br>
*앱이 백그라운드에서 실행할 수 있습니다.*

## <a name="app-views"></a>앱 보기

앱을 활성화 하는 경우 표시 하려는 뷰의 유형을 선택할 수 있습니다. 앱에 대 한 **CoreApplication**, 기본은 항상 [앱 보기](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) 와 임의 개수의 만들려면 원하는 앱 보기에 추가 합니다. 바탕 화면에서 창으로 앱 보기를 생각할 수 있습니다. 혼합된 현실 앱 템플릿을 여기서 기본 앱 보기는 Unity 프로젝트를 만듭니다 [몰입 형](app-views.md)합니다. 

앱에는 XAML와 같은 기술을 사용 하 여 앱 내 구매 등의 Windows 10 기능을 사용 하 여 추가 2D 앱 보기를 만들 수 있습니다. 앱이 다른 Windows 10 장치에 대 한 UWP 앱으로 시작 하는 경우 기본 뷰 2D 이지만 있습니다 수 없습니다 "불을" 혼합된 현실에서 몰입 형 환경을 volumetrically 표시 하는 추가 앱 보기를 추가 하 여 합니다. 슬라이드 쇼 단추 world 및 화면 앱에서 사진을 날아 하는 몰입 형 앱 보기를 전환 하는 위치는 XAML에서 사진 뷰어 앱을 작성 한다고 가정 합니다.

![2D 뷰 또는 몰입 형 뷰를 실행 중인 앱 수 있습니다.](images/slide3-800px.png)<br>
*2D 뷰 또는 몰입 형 뷰를 실행 중인 앱 수 있습니다.*

### <a name="creating-an-immersive-view"></a>몰입 형 뷰를 만들기

혼합된 현실 앱은 사용 하 여 이루어집니다 몰입 형 보기를 만드는 것은 [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) 형식입니다.

가 순수한 몰입 형 앱을 항상 만들어야 시작, 몰입 형 뷰를 데스크톱에서 시작 하는 경우에 합니다. 몰입 형 뷰는 항상에서 생성 된 위치에 관계 없이 헤드셋을 표시 합니다. 몰입 형 보기를 활성화 혼합 현실 포털 표시 되며 해당 헤드셋에 추가할 사용자를 안내 합니다.

데스크톱 모니터에 대 한 2D 뷰를 사용 하 여 시작 하는 앱 헤드셋에서 콘텐츠를 표시 하도록 보조 몰입 형 보기를 만들 수 있습니다. 이 예제는 헤드셋에서 360도 비디오를 표시 하는 모니터에서 2D Edge 창.

![몰입 형 보기에서 실행 되는 앱은 하나만 표시](images/slide4-800px.png)<br>
*몰입 형 보기에서 실행 되는 앱은 하나만 표시*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 홈에서 2D 보기

몰입 형 보기 이외의 어떠한 작업도 세상에서 2D 뷰로 렌더링 됩니다.

앱에는 모두 데스크톱 모니터 및 헤드셋 2D 보기가 있을 수 있습니다. 참고 헤드셋 또는 모니터에서 생성 된 보기와 같은 셸에서 새 2D 뷰를 표시 됩니다. 혼합 현실 홈 및 모니터 간에 2D 뷰를 이동할 사용자나 앱에 대 한 현재 불가능 합니다.

![다른 앱과 혼합 된 환경에서 공간을 공유 하는 2D 보기에서 실행 되는 앱](images/slide5-800px.png)<br>
*2D 보기에서 실행 되는 앱 다른 앱을 사용 하 여 공간을 공유*

### <a name="placement-of-additional-app-tiles"></a>추가 앱 타일의 배치

원하는 환경에서 볼 2D 사용 하 여 여러 앱을 배치할 수 있습니다 합니다 [보조 타일 Api](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)합니다. 이러한 "고정된" 타일은 사용자 배치 해야 하 고 다음 나중에 하 여 앱을 시작 시작 화면으로 표시 됩니다. Windows Mixed Reality 현재 지원 하지 않습니다 라이브 타일로 2D 타일 콘텐츠를 렌더링 합니다.

![앱에서 보조 타일을 사용 하 여 여러 배치를 가질 수 있습니다.](images/slide6-800px.png)<br>
*앱에서 보조 타일을 사용 하 여 여러 배치를 가질 수 있습니다.*

### <a name="switching-views"></a>뷰 전환

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>2D XAML 뷰에서 몰입 형 보기로 전환

앱을 XAML XAML을 사용 하는 경우 [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) 앱의 첫 번째 보기에서 제어 합니다. 앱을 활성화 하기 전에 몰입도 높은 뷰로 전환 해야 합니다 **CoreWindow**몰입 형 환경에 직접 앱이 시작 되도록 합니다.

사용 하 여 [CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) 하 고 [ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) 활성 뷰를 확인 합니다.

> [!NOTE]
>* 지정 하지 않으면 합니다 [ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) 플래그를 **SwitchAsync** 경우 몰입 형 뷰나 슬레이트 앱을 시작 하는 XAML 보기에서 전환 제거 될 예정 전 세계에서.
>* **SwitchAsync** 를 사용 하 여 호출 해야 합니다 [디스패처](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) 로 전환 하는 뷰와 연결 된입니다.
>* 해야 **SwitchAsync** 가상 키보드를 시작 하거나 다른 앱을 활성화 해야 하는 경우 XAML 보기.

![앱은 2D 뷰 및 몰입 형 뷰 간에 전환할 수 있습니다](images/slide7-600px.png) ![혼합 된 환경 및 기타 앱 사라집니다 앱을 몰입도 높은 뷰로 전환 되 면](images/slide8-600px.png)<br>
*왼쪽: 앱 2D 보기와 더불어 몰입 보기 간에 전환할 수 있습니다. 오른쪽: 앱을 몰입도 높은 뷰로 전환 되 면 Windows Mixed Reality 홈 및 기타 앱 사라집니다.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>전환 몰입 형 뷰에서 키보드 XAML 보기

뷰 전환 백-및-명시 하는 한 가지 일반적인 이유를 혼합된 현실 앱에서 키보드를 표시 합니다. 셸에서 앱이 2D 보기를 표시 하는 경우 시스템 키보드를 표시할 수만 있습니다. 앱을 가져올 텍스트 입력 해야 하는 경우 텍스트 입력된 필드를 사용 하 여 사용자 지정 XAML 보기를 제공 하 고를 전환 하 고, 다음 입력 완료 된 후에 다시를 전환 수 있습니다 것.

이전 섹션에서 사용할 수 있습니다와 같은 **ApplicationViewSwitcher.SwitchAsync** 몰입 형 보기에서 XAML 보기로 다시 전환 합니다.

## <a name="app-size"></a>앱 크기

2D 앱 보기 고정된 가상 슬레이트를 항상 표시 됩니다. 이렇게 하면 모든 2D 보기 정확히 동일한 양의 콘텐츠를 표시 합니다. 앱의 2D 보기의 크기에 대 한 자세한 내용은 일부는 다음과 같습니다.
* 앱의 가로 세로 비율 크기를 조정 하는 동안 유지 됩니다.
* 앱 [해상도 크기 조정 비율](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) 크기를 조정 하 여 변경 되지 않습니다.
* 앱은 전 세계의 실제 크기를 쿼리할 수 없습니다.

![고정 된 창 크기를 사용 하 여 2D 앱 표시](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*고정 된 창 크기를 사용 하 여 2D 뷰를 사용 하 여 앱 표시*

## <a name="app-tiles"></a>앱 타일

시작 메뉴 pin에 대 한 표준 작은 타일 및 중간 크기 타일을 사용 하며 **모든 앱** 혼합된 현실에서 목록입니다. 

![Windows Mixed Reality의 시작 메뉴](images/start-500px.png)<br>
*Windows Mixed Reality의 시작 메뉴*

## <a name="app-to-app-interactions"></a>앱 상호 작용 하는 앱

앱을 빌드할 때 Windows 10에서 사용할 수 있는 다양 한 앱을 통신 메커니즘에는 액세스할을 수 있습니다. 대부분의 새 프로토콜 Api 및 파일 등록 앱 시작 및 통신을 사용 하도록 설정 하려면 HoloLens에서 완벽 하 게 작동 합니다. 

참고는 데스크톱 헤드셋을 지정 된 파일 확장명과 연결 된 앱 또는 프로토콜 데스크톱 슬레이트 또는 데스크톱 모니터에만 나타날 수 있는 Win32 앱을 수 있습니다.

### <a name="protocols"></a>프로토콜

HoloLens에 앱을 통해 시작 하도록 지원 합니다 [Windows.System.Launcher Api](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)합니다.

몇 가지 다른 응용 프로그램을 시작할 때 고려해 야 합니다.

* 와 같은 비 모달 시작을 수행할 때 [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), 사용자와 상호 작용 하기 전에 앱을 배치 해야 합니다.

* 와 같은 모달 시작을 통해 수행할 때 [LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), 모달 앱 창 위에 배치 됩니다.

* Windows Mixed Reality 전용 뷰를 기반으로 응용 프로그램을 오버레이 수 없습니다. 시작된 된 앱을 표시 하기 위해 Windows 데 사용자 다시 전 세계의 응용 프로그램을 표시 합니다.

### <a name="file-pickers"></a>파일 선택기

HoloLens 둘 다를 지 원하는 [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) 하 고 [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 계약입니다. 그러나 앱 없음는 미리 설치 파일 선택기 계약과 충족 하는 합니다. Microsoft Store-예: OneDrive-이러한 앱을 설치할 수 있습니다.

둘 이상의 파일 선택기 앱이 설치 되어 있다면 표시 되지 않습니다 모든 명확성 UI 실행 하는 앱 선택 대신, 설치 된 첫 번째 파일 선택 기가 선택 됩니다. 파일을 저장 하는 경우 타임 스탬프를 포함 하는 파일 이름이 생성 됩니다. 이 사용자가 변경할 수 없습니다.

기본적으로 다음 확장 로컬로 지원 됩니다.

|  앱  |  Extensions | 
|----------|----------|
|  사진  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>앱 계약 및 Windows Mixed Reality 확장

앱 계약 및 확장 지점 파일 확장명을 처리 또는 백그라운드 작업을 사용 하 여 같은 하위 수준 운영 체제 기능을 활용 하기 위해 앱 등록을 수 있습니다. 지원 되거나 지원 되지 않는 계약 및 HoloLens에 확장점의 목록입니다.

|  계약 또는 확장  |  지원 되나요? | 
|----------|----------|
| [계정 그림 공급자 (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | 지원되지 않음 | 
| [Alarm](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | 지원되지 않음 | 
| [앱 서비스](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | 지원 되지만 완벽 하 게 작동 하지 않음 | 
| [약속 공급자](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | 지원되지 않음 | 
| [자동 실행 (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | 지원되지 않음 | 
| [백그라운드 작업 (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | 부분적으로 지원 됩니다 (일부 트리거 작업) | 
| [업데이트 작업 (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | 지원됨 | 
| [캐시 된 파일 업데이트 프로그램 계약](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | 지원됨 | 
| [카메라 설정 (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | 지원되지 않음 | 
| [전화 걸기 프로토콜](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | 지원되지 않음 | 
| [파일 활성화 (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | 지원됨 | 
| [파일 열기 선택기 계약](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | 지원됨 | 
| [파일 저장 선택기 계약](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | 지원됨 | 
| [잠금 화면 호출](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | 지원되지 않음 | 
| [미디어 재생](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | 지원되지 않음 | 
| [재생 계약](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | 지원되지 않음 | 
| [사전 설치 된 구성 작업](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | 지원되지 않음 | 
| [3D 인쇄 워크플로](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | 지원됨 | 
| [인쇄 작업 설정 (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | 지원되지 않음 | 
| [URI 활성화 (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | 지원됨 | 
| [제한 된 시작](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | 지원되지 않음 | 
| [검색 계약](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | 지원되지 않음 | 
| [설정 계약](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | 지원되지 않음 | 
| [공유 계약](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | 지원되지 않음 | 
| [SSL/certificates (확장)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | 지원됨 | 
| [웹 계정 공급자](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | 지원됨 | 

## <a name="app-file-storage"></a>앱 파일 저장소

모든 저장소 사용 하는 것은 [Windows.Storage 네임 스페이스](https://docs.microsoft.com/uwp/api/Windows.Storage)합니다. 자세한 내용은 다음 설명서를 참조 하세요. HoloLens 앱 저장소 동기화/로밍 하는 것을 지원 하지 않습니다.

* [파일, 폴더 및 라이브러리](https://docs.microsoft.com/windows/uwp/files/index)
* [설정 및 기타 앱 데이터 저장 및 검색](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>알려진된 폴더

참조 [KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) UWP 앱에 대 한 전체 세부 정보에 대 한 합니다.

<table>
<tr>
<th> 속성</th><th> HoloLens 지원</th><th> 몰입 형 헤드셋 지원</th><th> 설명</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>앱 캡처합니다 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>카메라 앨범 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>문서 라이브러리를 가져옵니다. 일반적인 용도 위한 문서 라이브러리를 사용 하는 것이 없습니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>음악 라이브러리를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>3D 개체 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>사진 라이브러리를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">재생 목록</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>재생 목록 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>사진을 저장 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>비디오 라이브러리를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>홈 그룹 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>미디어의 폴더 서버 Digital Living Network Alliance (DLNA ()) 장치를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>기록 된 통화 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>이동식 장치 폴더를 가져옵니다.</td>
</tr>
</table>

## <a name="app-package"></a>앱 패키지

Windows 10을 사용 하 여 더 이상 대상 운영 체제 대신 [하나 이상의 장치 제품군을 앱 대상](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families)합니다. 디바이스 패밀리는 디바이스 패밀리 내의 장치에서 기대할 수 있는 API, 시스템 특성 및 동작을 식별합니다. 또한 장치에서 앱을 설치할 수 있는 집합을 결정 합니다 [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)합니다.

* 데스크톱 헤드셋 및 HoloLens를 대상으로 앱을 대상으로 합니다 **Windows.Universal** 장치 제품군입니다.
* 데스크톱 헤드셋을 대상으로 앱을 대상으로 합니다 **Windows.Desktop** 장치 제품군입니다.
* HoloLens만을 대상으로 앱을 대상으로 합니다 **Windows.Holographic** 장치 제품군입니다.

## <a name="see-also"></a>참조

* [앱 보기](app-views.md)
* [혼합된 현실에 대 한 2D UWP 앱 업데이트](building-2d-apps.md)
* [3D 앱 시작 관리자 디자인 지침](3d-app-launcher-design-guidance.md)
* [3D 앱 시작 관리자를 구현합니다.](implementing-3d-app-launchers.md)
