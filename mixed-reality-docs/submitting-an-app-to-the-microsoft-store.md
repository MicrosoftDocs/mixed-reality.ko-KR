---
title: Microsoft Store에 앱 제출
description: 이 문서에서는 앱을 패키지 하 고 테스트 하는 방법 및 스토어에서 앱을 검색 하는 데 도움이 되는 팁을 비롯 하 여 Microsoft Store에 혼합 현실 앱을 제출 하는 방법에 대 한 팁을 제공 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 앱, uwp, 제출, 제출, 필터, 메타 데이터, 시스템 요구 사항, 키워드, wack, 인증, 패키지, appx, 머천다이징
ms.openlocfilehash: f2eb4093a2bea51d8c39b94d23777e426810981e
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375810"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Microsoft Store에 앱 제출

[HoloLens](hololens-hardware-details.md) 와 WINDOWS 10 PC는 모두 [몰입 형 헤드셋](immersive-headset-hardware-details.md) 을 켜는 유니버설 Windows 플랫폼 앱을 실행 합니다. HoloLens 또는 PC (또는 둘 다)를 지 원하는 앱을 제출 하 든 관계 없이 [파트너 센터](https://partner.microsoft.com/dashboard)를 통해 Microsoft Store에 앱을 제출 합니다.

파트너 센터 개발자 계정이 아직 없는 경우 [지금 등록할](https://developer.microsoft.com/store/register)수 있습니다.

## <a name="packaging-a-mixed-reality-app"></a>혼합 현실 앱 패키징

### <a name="prepare-image-assets-included-in-the-appx"></a>Appx에 포함 된 이미지 자산 준비

저장소에 제출할 appx 패키지에 응용 프로그램을 빌드하기 위해 appx 빌드 도구에 필요한 몇 가지 이미지 자산이 있습니다. MSDN의 [타일 및 아이콘 자산에 대 한 지침](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) 을 자세히 알아볼 수 있습니다.

| 필수 자산 | 권장 크기 조정 | 이미지 형식 | 표시 되는 위치 | 
|----------|----------|----------|------------------|
| 71x71 정사각형 로고 | Any |  PNG | N/A | 
| 150x150 정사각형 로고 | 150x150 (100% scale) 또는 225x225 (150% scale) | PNG | Pin 및 모든 앱 시작 (310x310이 제공 되지 않은 경우), 스토어 검색 제안, 스토어 목록 페이지, 스토어 찾아보기, 스토어 검색 | 
|  310x150 너비가 긴 로고 |  Any  |  PNG  |  N/A | 
|  스토어 로고 |  75x75 (150% scale)  |  PNG  |  파트너 센터, 보고서 앱, 리뷰 작성, 내 라이브러리 | 
|  시작 화면 |  930x450 (150% scale)  |  PNG  |  2D 앱 시작 관리자 (슬레이트) | 

또한 HoloLens에서 활용할 수 있는 몇 가지 권장 자산이 있습니다.

| 권장 자산 | 권장 크기 조정 | 표시 되는 위치 | 
|----------|----------|----------|
|  사각형 310x310 로고 |  310x310 (150% scale) |  Pin 및 모든 앱 시작 | 

### <a name="live-tile-requirements"></a>라이브 타일 요구 사항

HoloLens의 시작 메뉴에는 가장 큰 포함 된 정사각형 타일 이미지가 사용 됩니다.

Microsoft에서 게시 한 일부 앱의 응용 프로그램에 3D 시작 관리자가 있는 것을 볼 수 있습니다. 개발자는 [이러한 지침](implementing-3d-app-launchers.md)을 사용 하 여 앱에 대 한 3d 시작 관리자를 추가할 수 있습니다.

### <a name="specifying-target-and-minimum-version-of-windows"></a>Windows의 대상 및 최소 버전 지정

혼합 현실 앱에 특정 버전의 Windows와 관련 된 기능이 포함 되어 있는 경우 유니버설 Windows 응용 프로그램에서 지원할 대상 및 최소 플랫폼 버전을 지정 하는 것이 중요 합니다.

**이는 windows 10 조 크리에이터 업데이트 (10.0;) 이상이 필요한 [Windows Mixed Reality 몰입 형 헤드셋](immersive-headset-hardware-details.md)을 대상으로 하는 앱의 경우 특히 그렇습니다. 빌드 16299)가 제대로 작동 하도록 합니다.**

Visual Studio에서 새 유니버설 Windows 프로젝트를 만들 때 대상 및 최소 Windows 버전을 설정 하 라는 메시지가 표시 됩니다. "프로젝트" 메뉴에서 기존 프로젝트에 대 한이 설정을 변경 하 고 드롭다운 메뉴의 아래쪽에 있는 "앱 이름 > 속성 <"로 변경할 수도 있습니다.

Visual Studio 2019의 최소 및 대상 플랫폼 버전 ![설정](images/visual-studio-min-version-500px.png)<br>
Visual Studio에서 최소 및 대상 플랫폼 버전 설정

### <a name="specifying-target-device-families"></a>대상 장치 패밀리 지정

Windows Mixed Reality 응용 프로그램 ( [HoloLens](hololens-hardware-details.md) 및 [몰입 형 헤드셋](immersive-headset-hardware-details.md)모두)은 유니버설 Windows 플랫폼의 일부 이므로 [대상 장치 패밀리가](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) "windows. 유니버설" 인 모든 앱 패키지는 HoloLens 또는 모던 헤드셋을 사용 하는 Windows 10 pc에서 실행할 수 있습니다. 즉, 앱 매니페스트에서 대상 장치 제품군을 지정 하지 않은 경우 의도 하지 않은 Windows 10 장치까지 앱을 실수로 열 수 있습니다. 아래 단계에 따라 원하는 Windows 10 장치 제품군을 지정한 다음, [저장소에 제출할 파트너 센터에서 앱 패키지를 업로드할 때 올바른 장치 패밀리가 선택 되었는지 다시 확인 합니다.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Visual Studio에서이 필드를 설정 하려면 appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 "코드 보기"를 선택한 후 TargetDeviceFamily 이름 필드를 찾습니다. 기본적으로 다음과 같이 표시 될 수 있습니다.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

앱이 **hololens**용으로 만들어지면 대상 장치 패밀리 "Holographic"를 지정 하 여 hololens에만 설치 되도록 할 수 있습니다. 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

앱에 눈길 추적 또는 직접 추적과 같이 특히 **HoloLens 2** 의 기능이 필요한 경우 대상 장치 패밀리 "Holographic" 및 MinVersion 10.0.18362.0를 지정 하 여 Windows 버전 18362 이상을 대상으로 지정 하도록 할 수 있습니다. 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

**Windows Mixed reality 모던 헤드셋**에 대해 앱을 만든 경우 "10.0.16299.0"의 대상 장치 패밀리를 지정 하 여 windows 10 컴퓨터 (Windows 혼합 현실에 필요) 업데이트를 사용 하는 Windows 10 pc에만 설치 되도록 할 수 있습니다.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

마지막으로, 앱이 **HoloLens 및 Windows Mixed Reality**에서 실행 되도록 설정 된 경우 해당 하는 두 장치 제품군에만 앱을 사용할 수 있도록 설정 하 고 각 대상 장치 제품군에 대 한 줄을 각 대상 장치 제품군에 대 한 줄을 포함 하 여 각각 올바른 최소 Windows 버전을 대상으로 지정할 수 있습니다.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

[Targetdevicefamily UWP 설명서](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)를 읽어 장치 패밀리를 대상으로 지정 하는 방법에 대해 자세히 알아볼 수 있습니다.

### <a name="associate-app-with-the-store"></a>앱을 스토어에 연결

Visual Studio 솔루션의 프로젝트 메뉴에서 "스토어 > 앱을 스토어와 연결"을 선택 합니다. 이 작업을 수행하는 경우 앱에서 구매 및 알림 시나리오를 테스트할 수 있습니다. 앱을 스토어에 연결 하는 경우 이러한 값은 로컬 컴퓨터의 현재 프로젝트에 대 한 응용 프로그램 매니페스트 파일에 다운로드 됩니다.
* 패키지 표시 이름
* 패키지 이름
* 게시자 ID
* 게시자 표시 이름
* 버전

매니페스트의 사용자 지정 .xml 파일을 만들어 기본 package.appxmanifest 파일을 재정의하는 경우 앱을 스토어에 연결할 수 없습니다. 사용자 지정 매니페스트 파일을 스토어에 연결하려고 하면 오류 메시지가 나타납니다.

### <a name="creating-an-upload-package"></a>업로드 패키지 만들기

[Windows 10 용 유니버설 windows 앱 패키징](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)의 지침을 따르세요.

업로드 패키지를 만드는 마지막 단계는 [Windows 앱 인증 키트](#windows-app-certification-kit)를 사용 하 여 패키지의 유효성을 검사 하는 것입니다.

다른 Windows 10 장치 제품군에서 사용할 수 있는 기존 제품에 대해 특별히 HoloLens 용 패키지를 추가 하는 경우 [특정 고객에 게 제공 되는 패키지](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)에 대 한 버전 번호의 영향 및 [패키지가 다른 운영 체제에 배포](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)되는 방법에 대해서도 알아볼 수 있습니다.

일반적인 지침은 장치에 적용 가능한 가장 높은 버전 번호 패키지가 저장소에 의해 배포 되는 것입니다.

Windows 범용 패키지와 Holographic 패키지 및 Windows 범용 패키지의 버전 번호가 높은 경우 HoloLens 사용자는 Windows. Holographic 대신 더 높은 버전 번호의 Windows를 다운로드 합니다. 패키지. 이 문제에 대 한 솔루션 몇 가지가 있습니다.
1. Holographic와 같은 플랫폼별 패키지의 버전이 Windows와 같은 플랫폼을 알 수 없는 패키지 보다 항상 높은 지 확인 합니다.
2. 플랫폼별 패키지를 사용 하는 경우에는 앱을 Windows로 패키지 하지 마십시오. 대신, 사용 하려는 특정 플랫폼에 대 한 Windows 범용 패키지를 패키지 합니다.

>[!NOTE]
> HoloLens (첫 번째 Gen)와 HoloLen 2 모두에서 앱을 지원 하려면 두 개의 앱 패키지를 업로드 해야 합니다. HoloLens에 대해 x86 (첫 번째 Gen)과 ARM 또는 ARM64를 포함 하는 하나는 HoloLens 2입니다. 
> 
> 패키지에 ARM 및 ARM64를 모두 포함 하는 경우 ARM64 버전이 HoloLens 2에서 사용 됩니다. 

>[!NOTE]
> 여러 대상 장치 패밀리에 적용 될 단일 패키지를 선언할 수 있습니다.

3. 모든 플랫폼에서 작동 하는 단일 Windows 범용 패키지를 만듭니다. 이에 대 한 지원은 지금 바로 사용할 수 없으므로 위의 해결 방법이 권장 됩니다.

## <a name="testing-your-app"></a>앱 테스트

### <a name="windows-app-certification-kit"></a>Windows 앱 인증 키트

Visual Studio를 통해 파트너 센터에 제출할 앱 패키지를 만들 때 앱 패키지 만들기 마법사는 생성 된 패키지에 대해 Windows 앱 인증 키트를 실행 하 라는 메시지를 표시 합니다. 저장소에 대 한 원활한 전송 프로세스를 수행 하기 위해 스토어에 제출 하기 전에 [Windows 앱 인증 키트 테스트가](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) 로컬 컴퓨터의 앱에 대해 통과 하는지 확인 하는 것이 가장 좋습니다. 원격 HoloLens에서 Windows 앱 인증 키트를 실행 하는 것은 현재 지원 되지 않습니다.

### <a name="run-on-all-targeted-device-families"></a>모든 대상 장치 제품군에서 실행

Windows 유니버설 플랫폼을 사용 하 여 모든 Windows 10 장치 제품군에서 실행 되는 단일 응용 프로그램을 만들 수 있습니다. 그러나 유니버설 Windows 앱이 모든 장치 제품군 에서만 작동 하도록 보장 하지는 않습니다. HoloLens 또는 다른 Windows 10 대상 장치 제품군에서 앱을 사용할 수 있도록 선택 하기 전에 각 장치 제품군에서 [앱을 테스트](testing-your-app-on-hololens.md) 하 여 적절 한 환경을 보장 하는 것이 중요 합니다.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>혼합 현실 앱을 스토어에 제출

Unity 프로젝트를 기반으로 하는 혼합 현실 앱을 제출 하는 경우 먼저이 [비디오](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) 를 참조 하세요.

일반적으로 HoloLens 및/또는 모던 헤드셋에서 작동 하는 Windows Mixed Reality 앱을 제출 하는 것은 Microsoft Store에 UWP 앱을 제출 하는 것과 같습니다. [이름을 예약 하 여 앱을 만든](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)후에는 [UWP 제출 검사 목록](https://docs.microsoft.com/windows/uwp/publish/app-submissions)을 따라야 합니다.

가장 먼저 수행할 작업 중 하나는 혼합 현실 환경에 대 한 [범주 및 하위 범주를 선택](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) 하는 것입니다. **앱에 적합 한 범주를 선택** 하 여 적합 한 매장 범주에서 응용 프로그램을 상품 하 고 관련 검색 쿼리를 사용 하 여 표시 되도록 하는 것이 중요 합니다. **VR 타이틀을 게임으로 나열 하면 앱에 대 한 노출이 더 우수 하지 않으며,** 더 많은 맞춤 및 복잡 한 범주에 표시 되지 않을 수 있습니다.

그러나 제출 프로세스에는 다음과 같은 네 가지 주요 영역이 있습니다.
1. [속성](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)의 **[제품 선언](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** 섹션에서
2. **[시스템 요구 사항](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** 섹션의 [속성](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)아래에 있습니다.
3. [패키지](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)의 **[장치 제품군 가용성](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** 섹션에서
4. **[저장소 목록 페이지](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 의 여러 필드에 있습니다.

### <a name="mixed-reality-product-declarations"></a>혼합 현실 제품 선언

앱 제출 프로세스의 **[속성](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 페이지에는 **[제품 선언](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** 섹션에서 혼합 현실과 관련 된 몇 가지 옵션이 있습니다.

![혼합 현실 제품 선언](images/product-declarations-900px.png)<br>
혼합 현실 제품 선언

먼저 응용 프로그램에서 혼합 현실 환경을 제공 하는 장치 유형을 확인 하는 것이 좋습니다. 이렇게 하면 앱이 스토어의 Windows Mixed Reality 컬렉션에 포함 되 고 몰입 형 헤드셋을 연결한 후 또는 HoloLens에서 저장소를 검색할 때 저장소를 검색 하는 사용자에 게 표시 됩니다.

"이 환경은 다음 위치에서 Windows Mixed Reality를 위해 설계 되었습니다."
* 모던 헤드셋이 사용자의 PC에 연결 된 경우 앱에서 VR 환경을 제공 하는 경우에만 **PC** 상자를 확인 합니다. 앱이 몰입 형 헤드셋에서 실행 되도록만 설계 되었는지 아니면 헤드셋이 연결 된 경우 혼합 현실 모드 및/또는 보너스 콘텐츠를 제공 하는 표준 PC 게임/앱 인지 여부를이 상자에서 선택 해야 합니다.
* 앱이 HoloLens에서 실행 될 때 holographic 환경을 제공 하는 경우에만 **hololens** 상자를 확인 합니다.
* 앱이 2017 빌드에서 [혼합 현실 아카데미 "Project 섬" 앱](mixed-reality-250.md) 과 같은 두 장치 유형에 대해 혼합 현실 환경을 제공 하는 경우 두 상자를 **모두** 선택 합니다.

위의 "PC"를 선택한 경우 "mixed reality setup" (활동 수준)을 설정 하는 것이 좋습니다. 이는 HoloLens에 연결 된 Pc에서 실행 되는 혼합 현실 환경에만 적용 됩니다 .이는 HoloLens의 혼합 현실 앱이 세계 규모가 고 사용자는 설치 중에 경계를 정의 하지 않습니다.
* 사용자가 한 위치에서 유지 하도록 디자인 된 앱의 경우에는 **장착 된 +** 대기를 선택 합니다. 예를 들어 항공기의 입장에서 게임을 하는 데 사용할 수 있습니다.
* 사용자가 설치 중에 정의 된 경계 내에서 사용자가 탐색 하는 의도를 사용 하 여 응용 프로그램을 디자인 하는 경우 **모든 환경** 을 선택 합니다. 예를 들어 공격을 회피 하는 데 사용 하는 경우에는 한 단계와 오리를 발생 시킬 수 있습니다.

### <a name="mixed-reality-system-requirements"></a>혼합 현실 시스템 요구 사항

앱 제출 프로세스의 **[속성](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 페이지에는 **[시스템 요구 사항](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** 섹션에서 혼합 현실과 관련 된 몇 가지 옵션이 있습니다.

![시스템 요구 사항](images/system-reqs-800px.png)<br>
시스템 요구 사항

이 섹션에서는 혼합 현실 앱에 대 한 최소 (필수) 하드웨어 및 권장 (선택 사항) 하드웨어를 식별 합니다.

**입력 하드웨어:**

앱이 **마이크** ( [음성 입력](voice-input.md)), **[Xbox 컨트롤러 또는 게임 패드](hardware-accessories.md#bluetooth-gamepads)** 및/또는 **[Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)** 를 지 원하는 경우 확인란을 사용 하 여 잠재 고객에 게 알립니다. 이 정보는 스토어의 앱 제품 세부 정보 페이지에 표시 되며, 앱이 적절 한 앱/게임 컬렉션에 포함 될 수 있도록 지원 합니다. 예를 들어, 이동 컨트롤러를 지 원하는 모든 게임에 대 한 컬렉션이 있을 수 있습니다.

"최소 하드웨어" 또는 입력 형식에 대 한 "권장 하드웨어" 확인란을 선택 하는 방법에 대해 설명 합니다. 

예를 들면 다음과 같습니다. 
* 게임에 동작 컨트롤러가 필요 하지만 마이크를 통해 음성 입력을 허용 하는 경우 "Windows Mixed Reality 동작 컨트롤러" 옆에 있는 "최소 하드웨어" 확인란을 선택 하 고 "마이크" 옆에 있는 "권장 하드웨어" 확인란을 선택 합니다. 
* Xbox 컨트롤러/게임 패드 또는 동작 컨트롤러 중 하나를 사용 하 여 게임을 재생할 수 있는 경우 "Xbox 컨트롤러 또는 게임 패드" 옆에 있는 "최소 하드웨어" 확인란을 선택 하 고, 동작 컨트롤러가 게임 패드의 단계별 경험을 제공할 가능성이 있으므로 "Windows Mixed Reality 동작 컨트롤러" 옆에 있는 "권장 하드웨어" 확인란을 선택할 수 있습니다.

**Windows Mixed Reality 모던 헤드셋:**

응용 프로그램을 사용 하는 데 몰입 형 헤드셋이 필요 하거나 선택 사항 인지 여부를 나타내는 것은 고객 만족도 및 교육에 매우 중요 합니다.

앱을 몰입 형 헤드셋을 통해서만 사용할 수 있는 경우 "Windows Mixed Reality 모던 헤드셋" 옆 *에 있는 "* 최소 하드웨어" 확인란을 선택 합니다. 이는 구매 단추 위에 경고로 스토어의 앱 제품 세부 정보 페이지에 표시 되며, 고객이 기존 데스크톱 앱과 같은 PC에서 작동 하는 앱을 구매 하는 것으로 생각 하지 않습니다.

앱이 기존 PC 앱과 같은 데스크톱에서 실행 되는 경우 모던 헤드셋이 연결 된 경우 (앱의 전체 콘텐츠를 사용할 수 있는지 여부에 관계 없이) VR 환경을 제공 하지만, "Windows Mixed Reality" 옆의 "권장 하드웨어" 확인란을 선택 합니다. 모던 헤드셋. " 앱이 몰입 형 헤드셋이 연결 되지 않은 기존 데스크톱 앱으로 작동 하는 경우 앱의 제품 세부 정보 페이지에서 [구매] 단추 위에 경고가 표시 되지 않습니다.

**PC 사양:**

앱이 최대한 많은 Windows Mixed Reality 모던 헤드셋 사용자에 게 도달 하 게 하려면 [통합 그래픽이 포함 된 Windows Mixed reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)PC의 PC 사양을 [대상](understanding-performance-for-mixed-reality.md) 으로 지정 해야 합니다.

혼합 현실 앱이 최소 Windows Mixed Reality PC 요구 사항을 대상으로 하는지 또는 특정 PC 구성 (예: [Windows Mixed Reality 울트라 pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)의 전용 GPU)이 필요한 지 여부는 "최소 하드웨어" 열에 관련 PC 사양을 사용 하 여 표시 해야 합니다.

혼합 현실 앱이 더 잘 수행 되도록 설계 되었거나 더 높은 해상도의 그래픽을 제공 하는 경우 특정 PC 구성 또는 그래픽 카드에서 관련 PC 사양이 "권장 하드웨어" 열에 표시 되어야 합니다.

혼합 현실 앱에서 PC에 연결 된 몰입 형 헤드셋을 사용 하는 경우에만 적용 됩니다. 혼합 현실 앱이 HoloLens 에서만 실행 되는 경우 HoloLens에 하드웨어 구성이 하나만 있으므로 PC 사양을 나타낼 필요가 없습니다.

### <a name="device-family-availability"></a>디바이스 패밀리 가용성

Visual Studio에서 [앱을 올바르게 패키지](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) 한 경우 앱 제출 프로세스의 패키지 페이지에서 앱을 업로드 하면 앱을 사용할 수 있는 장치 패밀리를 식별 하는 테이블이 생성 됩니다.

![장치 패밀리 가용성 테이블](images/device-family-table-900px.png)<br>
장치 패밀리 가용성 테이블

혼합 현실 앱이 몰입 형 헤드셋에서 작동 하는 경우 테이블에서 "Windows 10 Desktop" 이상을 선택 해야 합니다. 혼합 현실 앱이 HoloLens에서 작동 하는 경우 "Windows 10 Holographic" 이상을 선택 해야 합니다. 응용 프로그램이 Windows Mixed Reality 헤드셋 유형 (예: [Mixed Reality 아카데미 "Project 섬" 앱](mixed-reality-250.md))에서 실행 되는 경우 "Windows 10 Desktop" 및 "Windows 10 Holographic"을 모두 선택 해야 합니다.

>[!TIP]
>파트너 센터에서 패키지 매니페스트와 앱/게시자 계정 정보 간의 불일치와 관련 된 응용 프로그램의 패키지를 업로드할 때 많은 개발자가 오류를 실행 합니다. 이러한 오류는 Windows 개발자 계정에 연결 된 것과 동일한 계정 (파트너 센터에 로그인 하는 데 사용 하는 계정)을 사용 하 여 Visual Studio에 로그인 하면 자주 방지할 수 있습니다. 동일한 계정을 사용 하는 경우 앱을 패키지 하기 전에 Microsoft Store에서 해당 id와 앱을 연결할 수 있습니다.

앱을 Microsoft Store에 연결 ![](images/associate-your-app-700px.png)<br>
Visual Studio의 Microsoft Store에 앱 연결

### <a name="store-listing-page"></a>스토어 목록 페이지

앱 제출 프로세스의 [스토어 목록](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) 페이지에는 혼합 현실 앱에 대 한 유용한 정보를 추가할 수 있는 여러 위치가 있습니다.

>[!IMPORTANT]
>앱이 스토어에 의해 올바르게 분류 되 고 Windows Mixed Reality 고객이 검색할 수 있도록 하려면 앱에 대 한 "검색 용어" 중 하나로 **"Windows Mixed reality"** 를 추가 해야 합니다. "공유 필드" 섹션을 확장 하 여 검색 단어를 찾을 수 있습니다.

검색 단어에 Windows Mixed Reality를 추가 ![](images/search-terms-800px.png)<br>
용어 검색에 "Windows Mixed Reality" 추가

## <a name="offering-a-free-trial-for-your-game-or-app"></a>게임 또는 앱에 대 한 무료 평가판 제공

대부분의 소비자는 Windows Mixed Reality 모던 헤드셋을 구입 하기 전에 가상 현실에 대 한 경험이 없도록 제한 됩니다. 이는 강한 게임에서 짐작할 수 있는 것을 알 수 없으며 몰입 형 환경에서 자신의 편안한 임계값에 익숙하지 않을 수 있습니다. 많은 고객이 Windows mixed reality [pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)로 직장 배지가 달린 되지 않는 Pc에서 Windows mixed reality 몰입 형 헤드셋을 사용해 볼 수도 있습니다. 이러한 고려 사항 때문에 유료 현실 앱 또는 게임의 [무료 평가판](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) 을 제공 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목
* [혼합 현실](mixed-reality.md)
* [개발 개요](development.md)
* [앱 보기](app-views.md)
* [혼합 현실 성능 이해](understanding-performance-for-mixed-reality.md)
* [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)
* [HoloLens에서 앱 테스트](testing-your-app-on-hololens.md)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
