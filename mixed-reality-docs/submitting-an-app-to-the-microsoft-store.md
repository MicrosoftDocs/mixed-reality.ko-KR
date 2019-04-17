---
title: Microsoft Store 앱 제출
description: 이 문서는 혼합된 현실 앱을 패키지 하 고 앱과 인증을 전달 하는 스토어에서 앱의 검색 기능에 도움이 되는 팁을 테스트 하는 방법을 포함 하 여 Microsoft Store 제출에 대 한 팁을 제공 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 제출, 필터, 메타 데이터, 시스템 요구 사항, 키워드, wack, 인증, 패키지, appx, 머천다이징 uwp 앱 제출
ms.openlocfilehash: 4eb69fbaa22f4864305f09d5e1bf1c1860a0d31f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600865"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Microsoft Store 앱 제출

둘 다 [HoloLens](hololens-hardware-details.md) 및 Windows 10 PC 강화 하 [몰입 형 헤드셋](immersive-headset-hardware-details.md) 유니버설 Windows 플랫폼 앱을 실행 합니다. 앱을 통해 Microsoft Store 전송할 것 HoloLens 또는 PC (또는 둘 다)를 지 원하는 앱을 제출 하 고 있는지 여부를 [파트너 센터](https://partner.microsoft.com/dashboard)합니다.

파트너 센터 개발자 계정에 아직 없는 경우 [지금 등록](https://developer.microsoft.com/store/register)합니다.

## <a name="packaging-a-mixed-reality-app"></a>혼합된 현실 앱 패키징

### <a name="prepare-image-assets-included-in-the-appx"></a>준비 후 appx에 포함 된 이미지 자산

도구 빌드 appx appx 패키지를 스토어에 제출할 응용 프로그램을 작성 하는 데 필요한 이미지 자산을 여러 가지가 있습니다. 에 대 한 자세한 내용은 [타일과 아이콘 자산에 대 한 지침](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) MSDN에 있습니다.

| 필요한 자산 | 권장 되는 크기 조정 | 이미지 형식 | 이 표시 되는 위치? | 
|----------|----------|----------|------------------|
| 71x71 정사각형 로고 | 임의의 값 |  PNG | 해당 사항 없음 | 
| 정사각형 150 x 150 로고 | 150x150 (100% 배율) 또는 225 x 225 (150% 조정) | PNG | (310x310 정사각형 제공 되지 않는) 하는 경우 시작 pin 및 모든 앱, 스토어 검색 제안, 스토어 목록 페이지에서 저장소 찾아보기, 스토어 검색 | 
|  와이드 310 x 150 로고 |  임의의 값  |  PNG  |  해당 사항 없음 | 
|  스토어 로고 |  75 x 75 (150% 조정)  |  PNG  |  파트너 센터, 보고서 앱 리뷰, 라이브러리 작성 | 
|  시작 화면 |  930 x 450 (150% 조정)  |  PNG  |  2D 앱 시작 관리자 (슬레이트) | 

HoloLens 활용할 수 있는 몇 가지 권장 되는 자산도 있습니다.

| 권장 되는 자산 | 권장 되는 크기 조정 | 이 표시 되는 위치? | 
|----------|----------|----------|
|  사각형 310x310 정사각형 로고 |  310x310 정사각형 (150% 조정) |  Pin 및 모든 앱 시작 | 

### <a name="live-tile-requirements"></a>라이브 타일 요구 사항

시작 메뉴 HoloLens에 가장 큰 포함된 정사각형 타일 이미지를 사용 합니다.

Microsoft에서 게시 하는 일부 앱 응용 프로그램에 대 한 3D 시작 관리자는 볼 수 있습니다. 개발자가 사용 하 여 해당 앱에 대 한 3D 시작 관리자를 추가할 수 있습니다 [이러한 지침](implementing-3d-app-launchers.md)합니다.

### <a name="specifying-target-and-minimum-version-of-windows"></a>대상 및 최소 Windows 버전 지정

혼합된 현실 앱 Windows의 특정 버전과 관련 된 기능에 포함 된 경우에 대상 및 유니버설 Windows 응용 프로그램에서 지원할 최소 플랫폼 버전을 지정 해야 합니다.

**이 앱을 대상으로 하는 것이 특히 [Windows Mixed Reality 몰입 형 헤드셋](immersive-headset-hardware-details.md)에 Windows 10 Fall Creators Update (10.0; 이상이 필요 빌드 16299) 제대로 작동 합니다.**

Visual Studio에서 새 유니버설 Windows 프로젝트를 만들 때 대상 및 최소 버전의 Windows 설정 하 라는 메시지가 표시 됩니다. 또한 드롭다운 메뉴의 맨 아래에서 "< 앱 이름의 > 속성" 다음 "프로젝트" 메뉴에서 기존 프로젝트에 대해이 설정을 변경할 수 있습니다.

![최소 대상 플랫폼 버전이 Visual Studio 2017에서 집합과](images/visual-studio-min-version-500px.png)<br>
최소를 설정 하 고 Visual Studio에서 플랫폼 버전 대상

### <a name="specifying-target-device-families"></a>대상 장치 패밀리를 지정합니다.

Windows Mixed Reality 응용 프로그램 (둘 다에 대해 [HoloLens](hololens-hardware-details.md) 하 고 [몰입 형 헤드셋](immersive-headset-hardware-details.md)) 유니버설 Windows 플랫폼을 사용 하 여 모든 앱 패키지의 일부인는 [대상 장치 제품군](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)"windows.universal"인은 몰입 형 헤드셋을 사용 하 여 HoloLens 또는 Windows 10 Pc에서 실행할 수 있습니다. 즉, 앱 매니페스트에 대상 장치 제품군을 지정 하지 않으면 열 수 있습니다 실수로 의도 하지 않은 Windows 10 장치에 앱. 원하는 Windows 10 장치 제품군을 지정 하려면, 아래 단계에 따라 차례로 [스토어에 제출 하려면 파트너 센터에서 앱 패키지를 업로드 하면 올바른 장치 제품군은 선택 되어 있는지 다시 확인 합니다.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Visual Studio에서이 필드를 설정 하려면 Package.appxmanifest 마우스 오른쪽 단추로 클릭 하 고 "코드 보기"를 선택 TargetDeviceFamily 이름 필드를 찾습니다. 기본적으로 다음과 같습니다.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

앱에 대 한 만들어지면 **HoloLens**, 설치 되어 있는지만 HoloLens에 "Windows.Holographic"의 대상 장치 제품군을 지정 하 여 확인 수 있습니다. 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

앱에 대 한 만들어지면 **Windows Mixed Reality 몰입 형 헤드셋**, 설치 되어 있는지만 Windows 10 Fall Creators Update (Windows Mixed Reality에 필요)를 사용 하 여 Windows 10 Pc에서 대상을 지정 하면 확인 수 장치 패밀리 "Windows.Desktop" 및 "10.0.16299.0"의 MinVersion입니다.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

마지막으로 앱을 둘 다에서 실행 하려는 경우 **HoloLens 및 Windows Mixed Reality 몰입 형 헤드셋**, 앱 이러한 두 장치 제품군에만 사용할 수 있는 및 동시에 올바른 대상으로 각 되도록 보장할 수 있습니다 각 해당 MinVersion 사용 하 여 각 대상 장치 제품군에 대 한 줄을 포함 하 여 최소 Windows 버전입니다.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

참조 하 여 장치 제품군을 대상으로 하는 방법에 대 한 자세히 알아볼 수 있습니다 합니다 [TargetDeviceFamily UWP 설명서](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)합니다.

### <a name="associate-app-with-the-store"></a>스토어와 앱 연결

Visual Studio 솔루션에서 프로젝트 메뉴에서 "저장소 > 연결 앱을 스토어"를 선택 합니다. 이 작업을 수행 하는 경우에 앱에서 구매 및 알림 시나리오를 테스트할 수 있습니다. 저장소를 사용 하 여 앱을 연결 하는 경우 이러한 값이 로컬 컴퓨터에서 현재 프로젝트에 대 한 앱 매니페스트 파일로 다운로드 됩니다.
* 패키지 표시 이름
* 패키지 이름
* 게시자 ID
* 게시자 표시 이름
* 버전

매니페스트의 사용자 지정.xml 파일을 만들어 기본 package.appxmanifest 파일을 재정의 하는 경우 앱 스토어와 연결할 수 없습니다. 사용자 지정 매니페스트 파일을 스토어에 연결 하려고 하면 오류 메시지가 표시 됩니다.

### <a name="creating-an-upload-package"></a>업로드 패키지 만들기

지침에 따릅니다 [Windows 10 용 패키징 유니버설 Windows 앱](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)합니다.

업로드 패키지를 만드는 마지막 단계는 사용 하 여 패키지 유효성 검사를 [Windows 앱 인증 키트](#windows-app-certification-kit)합니다.

추가할 것 패키지 특히 HoloLens에 대 한 다른 Windows 10 장치 제품군에서 사용할 수 있는 기존 제품을를 또한 하려는 경우에 대 한 자세한 [특정 고객에 게 전달할지 버전 번호는 패키지에 미칠 수 있습니다 ](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx), 및 [패키지를 다른 운영 체제에 배포 되는 방식을](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)입니다.

일반적인 지침은 분산 저장소에서 하나를 장치에 적용 되는 가장 높은 버전 번호 패키지 수 것입니다.

HoloLens 사용자는 Windows.Holographic 대신 더 높은 버전 번호 Windows.Universal 패키지를 다운로드 합니다 Windows.Universal 패키지 및 Windows.Holographic 패키지 Windows.Universal 패키지에 더 높은 버전 번호를 하는 경우 패키지입니다. 이 문제에 대 한 솔루션 몇 가지가 있습니다.
1. Windows.Holographic 로드가 Windows.Universal 같은 플랫폼 독립적인 패키지 보다 더 높은 버전 번호와 같은 플랫폼 특정 패키지를 확인 하십시오.
2. Windows.Universal 플랫폼 특정 패키지-있는 경우 대신 package는 Windows.Universal 특정 플랫폼에서 사용할 수 있는 원하는 대로 앱을 패키지 되지 않습니다

>[!NOTE]
> 여러 대상 장치 제품군을 적용 하기 위해 단일 패키지를 선언할 수 있습니다.

3. 모든 플랫폼에서 작동 하는 단일 Windows.Universal 패키지를 만듭니다. 있도록 위 솔루션을 사용 하는 것이 좋습니다이 대 한 지원을 지금 유용한 아닙니다.

## <a name="testing-your-app"></a>앱 테스트

### <a name="windows-app-certification-kit"></a>Windows 앱 인증 키트

Visual Studio를 통해 파트너 센터에 전송할 앱 패키지를 만들 때 생성 되는 패키지에 대해 Windows 앱 인증 키트를 실행 하면 앱 패키지 만들기 마법사를 묻습니다. 저장소에 부드러운 제출 프로세스를 위해서는 것이 가장 좋습니다 되었는지 확인 하는 [Windows 앱 인증 키트 테스트](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) 스토어에 제출 하기 전에 앱에 대 한 로컬 컴퓨터에 전달 합니다. Windows 앱 인증 키트 원격 HoloLens 실행 현재 지원 되지 않습니다.

### <a name="run-on-all-targeted-device-families"></a>모든 대상된 장치 제품군에서 실행

Windows 유니버설 플랫폼을 사용 하면 모든 Windows 10 장치 제품군에서 실행 되는 단일 응용 프로그램을 만들 수 있습니다. 그러나 범용 Windows 앱 모든 장치 제품군에만 작동 보장 하지 않습니다. 앱 HoloLens 또는 다른 Windows 10 대상 장치 제품군에서 사용할 수 있도록 선택 하기 전에 반드시 했는지 [앱을 테스트할](testing-your-app-on-hololens.md) 좋은 환경을 보장 하려면 해당 장치 제품군의 각.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>혼합된 현실 앱 스토어에 제출

Unity 프로젝트를 기반으로 하는 혼합된 현실 앱을 제출 하는 경우 참조 하십시오 [비디오](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) 첫 번째입니다.

일반적으로 제출 Windows Mixed Reality HoloLens 및/또는 몰입 형 헤드셋에서 작동 하는 앱은 Microsoft Store 모든 UWP 앱을 제출 하는 것과 같습니다. 했으면 [해당 이름을 예약 하 여 앱을 만들었습니다](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)를 따라야 합니다 [UWP 제출 검사 목록](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

첫 번째 작업을 수행 중 하나인 [범주 및 하위 범주를 선택 합니다.](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) 혼합된 현실 환경에 대 한 합니다. 것이 중요 했는지 **앱에 대 한 가장 정확한 범주 선택** 오른쪽 저장소 범주에서 응용 프로그램을 상품 하 고 관련 된 검색 쿼리를 사용 하 여 표시 되도록 수 있도록 합니다. **게임 앱을 더 잘 노출 되지 것입니다 하는 대로 VR 제목 목록** 꽉 덜 자세한 맞춤 된 범주에 표시 되지 않을 수 있습니다.

그러나는 4 가지 핵심 영역에서 혼합 현실 별 선택 하려는 제출 프로세스
1. 에 **[제품 선언](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** 섹션 아래 [속성](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)합니다.
2. 에 **[시스템 요구 사항](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** 섹션 아래 [속성](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)합니다.
3. 에 **[장치 패밀리 가용성](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** 섹션 아래 [패키지](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)합니다.
4. 여러 합니다 **[스토어 목록 페이지](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 필드입니다.

### <a name="mixed-reality-product-declarations"></a>혼합된 현실 제품 선언

에 **[속성](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 페이지 앱 제출 프로세스의 혼합된 현실에 관련 된 몇 가지 옵션을 찾을 수는 **[제품 선언](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** 섹션입니다.

![혼합된 현실 제품 선언](images/product-declarations-900px.png)<br>
혼합된 현실 제품 선언

먼저 앱 혼합된 현실 환경 제공 하는 장치 유형을 식별 해야 합니다. 이렇게 하면 앱 스토어에서 Windows Mixed Reality 컬렉션에 포함 되어 있는지는 몰입 형 헤드셋을 연결한 후 (또는 HoloLens에 있는 저장소를 검색 하는 경우) 저장소를 검색 하는 사용자에 게 표시 되는 합니다.

옆에 "에서이 환경은 Windows 혼합된 현실 용으로 디자인 되었습니다."
* 확인 합니다 **PC** 앱 사용자의 PC에 연결 되어 있으면는 몰입 형 헤드셋 VR 환경을 제공 하는 경우에 합니다. 앱이 단독으로 몰입 형 헤드셋에서 실행 하도록 설계 되었습니다 또는 표준 PC 게임/앱을 헤드셋 연결 되 면 혼합된 현실 모드 및/또는 보너스 콘텐츠를 제공 하는 경우에이 상자를 확인 해야 합니다.
* 확인 합니다 **HoloLens** HoloLens에 실행 될 때 앱에 holographic 환경을 제공 하는 경우에 합니다.
* 확인 **둘 다** 상자 앱 혼합된 현실을 제공 하는 경우 장치 유형에 모두에 같은 경험을 [혼합된 현실 Academy "프로젝트 섬" 앱](mixed-reality-250.md) Build 2017에서.

"혼합된 현실 setup"을 설정 하려는 위의 "PC"를 선택한 경우 (작업 수준). 이 HoloLens에서 혼합된 현실 앱은 전 세계 규모와 사용자 설치 하는 동안 경계를 정의 하지 않는 몰입 형 헤드셋에 연결 하는 Pc에서 실행 되는 혼합된 현실 환경에만 적용 됩니다.
* 선택할 **Seated + 고정** 앱 (예를 들어 수 게임 항공기의 cockpit에 장착 하는 위치) 위치에 유지 되는 사용자는 의도 사용 하 여 설계 된 경우.
* 선택 **모든 환경을** 앱 설치 시 자신이 정의 된 경계 내에서 관련 사용자를 안내 하는 의도 사용 하 여 설계 되었습니다 경우 (게임 where 예로 들 수 있습니다 쪽 단계 하 오리 공격을 피할).

### <a name="mixed-reality-system-requirements"></a>혼합된 현실 시스템 요구 사항

에 **[속성](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 페이지 앱 제출 프로세스의 혼합된 현실에 관련 된 몇 가지 옵션을 찾을 수는 **[시스템 요구 사항](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** 섹션입니다.

![시스템 요구 사항](images/system-reqs-800px.png)<br>
시스템 요구 사항

이 섹션에서는 혼합된 현실 앱에 대 한 (필수)는 최소 하드웨어 및 (선택 사항) 권장된 하드웨어를 식별할 수 있습니다.

**입력된 하드웨어:**

확인란을 사용 하 여 앱에서 지원 하는지 잠재 고객에 게 알립니다 **마이크** (에 대 한 [입력 음성](voice-input.md)), **[Xbox 컨트롤러 또는 gamepad](hardware-accessories.md#bluetooth-gamepads)**, 및/또는  **[Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)** 합니다. 이 정보 스토어에서 앱의 제품 세부 정보 페이지에 표시 됩니다 및 적절 한 앱/게임 컬렉션에 포함 하는 앱은 데 도움이 됩니다 (예: 컬렉션 수 모든 게임 컨트롤러 동작 지원에 대 한 존재 함).

"최소 하드웨어" 또는 "권장 하드웨어" 입력된 형식에 대 한 확인란을 선택 하는 방법에 대 한 신중 하 게 됩니다. 

예를 들어 다음과 같은 가치를 제공해야 합니다. 
* 게임 동작 컨트롤러 필요 하지만 마이크를 통해 음성 입력을 허용 하는 경우 "Windows Mixed Reality 동작 컨트롤러" 옆에 있는 "최소 하드웨어" 확인란을 하지만 "마이크." 옆에 있는 "권장 하드웨어" 확인란을 선택합니다 
* "Xbox 컨트롤러 또는 gamepad" 옆에 있는 "최소 하드웨어" 확인란을 선택 하 고 "Windows Mixed Reality 동작 옆에 있는"권장 하드웨어"확인란을 선택 수는 Xbox 컨트롤러/gamepad 또는 동영상 컨트롤러 중 하나를 사용 하 여 게임을 재생할 수 있습니다, 하는 경우 가능성이 동작 컨트롤러로 "컨트롤러는 gamepad에서 환경의 스텝업을 제공 합니다.

**Windows Mixed Reality 몰입 형 헤드셋:**

몰입 형 헤드셋 앱을 사용 하는 데 필요한 며 하는지 여부를 나타내는 하는 것이 고객 만족 및 교육에 중요 합니다.

앱에서 하는 경우 *만* 몰입 형 헤드셋을 통해 사용할 수, "Windows Mixed Reality 몰입 형 헤드셋" 옆에 있는 "최소 하드웨어" 확인란을 선택 합니다. 이 표시 됩니다 스토어에서 앱의 제품 세부 정보 페이지에서 구매 단추 위의 경고로 고객에 게는 기존 데스크톱 앱 등 자신의 PC에서 작동 하는 앱을 구입 하 고는 생각 하도록 합니다.

앱을 기존 PC 앱 처럼 데스크톱에서 실행 되지만 몰입 형 헤드셋 연결 되어 있을 때 VR 환경을 제공 하는 경우 (앱의 전체 콘텐츠를 사용할 수 인지 또는 일부만), "Windows Mixed Reality 옆에 있는"권장 하드웨어"확인란을 선택 합니다. 몰입 형 헤드셋입니다. " 경고가 표시 됩니다 구매 단추 위의 앱의 제품 세부 정보 페이지에서 앱 함수는 몰입 형 헤드셋 없이 기존 데스크톱 앱으로 연결 하는 경우.

**PC 사양:**

최대한 많은 Windows Mixed Reality 몰입 형 헤드셋 사용자와 연결할 앱을 원한다 면 하려는 [대상](understanding-performance-for-mixed-reality.md) 에 대 한 PC 사양을 [통합된 그래픽을 사용 하 여 Windows 혼합 현실 Pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)합니다.

혼합된 현실 앱 최소 Windows Mixed Reality PC 요구 사항을 대상으로 하거나 특정 PC 구성 필요 여부 (등의 전용된 GPU를 [Windows Mixed Reality Ultra PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), 관련 된는 나타내야 "최소 하드웨어" 열에 있는 PC 사양입니다.

혼합된 현실 앱이 더 효과적으로 수행 하거나 더 높은 해상도 그래픽에는 특정 PC 구성 또는 그래픽 카드를 제공 하도록 설계 된 경우 관련 PC 사양에 대 한 "권장 하드웨어" 열을 사용 하 여이 나타내는 해야 있습니다.

이 혼합된 현실 앱이 PC에 연결 하는 몰입 형 헤드셋 사용 하는 경우에 적용 됩니다. HoloLens에서 혼합된 현실 앱만 실행 되 면 HoloLens에 하나의 하드웨어 구성을 PC 사양 나타낼 필요가 없습니다.

### <a name="device-family-availability"></a>디바이스 패밀리 가용성

했다면 [앱을 올바르게 패키지](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) Visual Studio에서 앱 제출 프로세스의 패키지 페이지에 업로드 해야 테이블을 만들 앱에 사용할 수 있는 장치 제품군을 식별 합니다.

![장치 패밀리 가용성 테이블](images/device-family-table-900px.png)<br>
장치 패밀리 가용성 테이블

혼합된 현실 앱 몰입 형 헤드셋에서 다음에서 작동 하는 경우 최소한 "Windows 10 Desktop" 테이블에서 선택 됩니다. 혼합된 현실 앱 HoloLens에서 다음에서 작동 하는 경우 최소한 "Windows 10 Holographic" 선택 해야 합니다. Windows Mixed Reality 헤드셋 양쪽에도 다른 여러 가지 앱을 실행 하는 경우는 [혼합된 현실 Academy "프로젝트 섬" 앱](mixed-reality-250.md), "Windows 10 Desktop" 및 "Windows 10 Holographic" 모두 선택 해야 합니다.

>[!TIP]
>대부분의 개발자는 패키지 매니페스트 및 파트너 센터에서 앱/게시자 계정 정보 간의 불일치와 관련 된 해당 앱의 패키지를 업로드 하는 경우 오류가 발생 합니다. 이러한 오류는 종종 Windows 개발자 계정 (파트너 센터에 로그인 하는 데 사용한 하나)에 연결 된 동일한 계정으로 Visual Studio에 로그인 하 여 방지할 수 있습니다. 동일한 계정을 사용 하는 경우 패키지 하기 전에 Microsoft Store 해당 id를 사용 하 여 앱을 연결할 수 있습니다.

![Microsoft Store 사용 하 여 앱 연결](images/associate-your-app-700px.png)<br>
Visual Studio에서 Microsoft Store 사용 하 여 앱 연결

### <a name="store-listing-page"></a>스토어 목록 페이지

에 [스토어 목록](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) 앱 제출 페이지 처리, 몇 가지 방법으로 혼합된 현실 앱에 대 한 유용한 정보를 추가할 수 있습니다.

>[!IMPORTANT]
>앱 스토어에 의해 분류 올바르게 이며 Windows Mixed Reality 고객에 게 검색할 수 있도록 추가할지 **"Windows Mixed Reality"** (있습니다 검색어를 확장 하 여 앱에 대 한 "검색 용어" 중 하나로 "공유 필드" 섹션 참조)입니다.

![Windows Mixed Reality 검색 단어를 추가 합니다.](images/search-terms-800px.png)<br>
"Windows Mixed Reality" 검색 용어를 추가 합니다.

## <a name="offering-a-free-trial-for-your-game-or-app"></a>게임 또는 앱에 대 한 평가판을 제공합니다.

많은 소비자 기능이 제한 됩니다 없는 환경에 가상 현실을 사용 하 여 Windows Mixed Reality 몰입 형 헤드셋을 구입 하기 전에 합니다. 강한 게임에서 예상 되는 모를 수 하며 자신의 몰입 형 환경 쾌적 임계값을 사용 하 여 생소할 수 있습니다. 많은 고객이으로 달린 되지 않은 pc에서 Windows Mixed Reality 몰입 형 헤드셋을 시도할 수도 있습니다 [Windows Mixed Reality Pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)합니다. 이러한 고려 사항 때문에 강력한 좋습니다 제품을 [무료 평가판](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) 유료 혼합된 현실 앱 또는 게임에 대 한 합니다.

## <a name="see-also"></a>참조
* [혼합 현실](mixed-reality.md)
* [개발 개요](development-overview.md)
* [앱 보기](app-views.md)
* [혼합된 현실에 대 한 성능 이해](understanding-performance-for-mixed-reality.md)
* [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)
* [HoloLens에 앱 테스트](testing-your-app-on-hololens.md)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
