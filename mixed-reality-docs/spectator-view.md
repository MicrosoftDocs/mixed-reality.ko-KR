---
title: Spectator 보기
description: 외부 장치에서 홀로그램 혼합된 현실 환경 비디오 녹화 또는 외장 디스플레이에서 혼합된 현실 경험을 보여 주는 수단으로 시각화 합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: IPad, iPhone, iOS spectator 보기 OpenCV, 카메라, ARKit, HoloLens, 혼합 현실, MixedRealityToolkit, 데모, 레코드
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602270"
---
# <a name="spectator-view-for-hololens"></a>HoloLens spectator 보기

![표식](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a>현재 리팩터링

> [!NOTE]
>HoloLens spectator 보기 적극적으로 리팩터링하려 합니다. 이 작업은 미리 보기 통합 및 Pro 코드 베이스 되며 HoloLens 2 지원을 확장 합니다. 

현재 보려는 Spectator 보기 리팩터링 상태의 MixedRealityToolkit와 MixedRealityToolkit Unity 리포지토리에서 ' 기능/spectatorView ' 분기를 확인:

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

및

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a>개요

HoloLens, 착용 하는 경우에서는 것을 잊어버릴 경우가 있는 사용자 수 일어날 수 없는 없는 것. Spectator 보기를 통해 다른 사람에 게는 2D 화면의 해당 환경에서 보게 HoloLens 사용자.
Spectator 보기 (미리 보기)는 홀로그램 HD, Spectator 보기 Pro를 위한 것 홀로그램 전문가 품질 기록 하는 동안 기록에 빠르고 경제적인 방법입니다.

다음 표에서 옵션 및 해당 기능을 모두 보여 줍니다. 비디오 녹화 요구에 가장 잘 맞는 옵션을 선택 합니다.

|                                      | Spectator 보기 (미리 보기) |              Spectator 보려면 Pro              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 품질                         |         Full HD         |        (따라 DSLR) filming 전문가 품질      |
| 쉽게 카메라 이동                      |            ✔            |                                             |
| 3 인칭 보기                    |            ✔            |                      ✔                      |
| 화면에 스트리밍할 수 있습니다.           |            ✔            |                      ✔                      |
| 이식 가능                             |            ✔            |                                             |
| 무선                             |            ✔            |                                             |
| 추가 필수 하드웨어         |     iPhone (또는 iPad)    | HoloLens + Rig + 삼각대 + DSLR + PC + Unity |
| 하드웨어 투자                  |           낮음           |                     높음                    |
| 플랫폼 간                       |           iOS           |                                             |
| 뷰어 상호 작용할 수 있습니다.                  |            ✔            |                                             |
| 네트워킹 필요 (UNET 스크립팅) |            ✔            |                      ✔                      |
| 런타임 설치 기간               |         인스턴트         |                     슬로우                    |

## <a name="spectator-view-preview"></a>Spectator 보기 (미리 보기)

![표식](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a>사용 사례

- HD에서 filming 홀로그램: Spectator 보기 (미리 보기)를 사용 하는 iPhone을 사용 하 여 혼합된 현실 경험을 기록할 수 있습니다. Full HD에서 기록 하 고 홀로그램 및 그림자에 앤티앨리어싱을 적용 합니다. 홀로그램 비디오를 캡처하는 비용 효율적이 고 빠른 방법입니다.
- 라이브 데모: Stream 라이브 혼합된 현실 iPhone 또는 iPad를 지연 없는에서 직접 Apple TV에 환경을!
- 게스트를 사용 하 여 환경을 공유 합니다. HoloLens가 아닌 사용자가 휴대폰 또는 태블릿에서 직접 홀로그램 환경 수 있습니다.

### <a name="current-features"></a>현재 기능

- 휴대폰을 세션에 추가 하는 것에 대 한 자동 검색을 네트워크입니다.
- 사용자가 올바른 세션에 추가 되므로 자동 세션 처리 합니다.
- 공간 홀로그램, 홀로그램 정확히 동일한 위치에서 모든 사용자가 표시 되도록 동기화 합니다.
- iOS (ARKit 사용 가능 장치)를 지원 합니다.
- 여러 iOS 게스트입니다.
- 비디오 + 홀로그램 + 앰비언트 사운드 + 홀로그램 소리를 기록 합니다.
- 비디오를 저장,를 전자 메일로 보내거나 다른 지원 앱과 공유할 수 있도록 시트를 공유 합니다.


>[!NOTE] 
>Spectator 보기 Pro 버전 코드를 사용 하 여 Spectator 보기 (미리 보기) 코드를 사용할 수 없습니다. 홀로그램의 비디오 기록을 필요한 경우 새 프로젝트에서 구현 하는 좋습니다.

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a>라이선스

- [OpenCV-(3 절 BSD 라이선스)](https://opencv.org/license.html)
- [Unity ARKit-(MIT 라이선스)](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a>Spectator 보기 (미리 보기)를 설정 하는 방법

### <a name="requirements"></a>요구 사항

- [Spectator 보기 플러그 인 및 필요한 OpenCV 이진 파일](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) -아래 Spectator 보기 기본 플러그 인을 빌드하는 방법에 대 한 세부 정보를 찾을 수 있습니다. 생성 된 이진 파일에서 다음이 필요 합니다.

    - opencv_aruco343.dll
    - opencv_calib3d343.dll
    - opencv_core343.dll
    - opencv_features2d343.dll
    - opencv_flann343.dll
    - opencv_imgproc343.dll

    - zlib1.dll
    - SpectatorViewPlugin.dll
- Spectator 뷰는 해당 네트워크 검색 및 공간 동기화에 대 한 Unity 네트워킹 (UNET)를 사용합니다. 즉 장치 간에 동기화를 적용 하는 동안 모든 상호 작용 해야 합니다.
- Unity 2017.2.1p2 이상
- 하드웨어
    - HoloLens
    - Windows 10을 실행 하는 Windows PC
    - ARKit 호환 장치 (iPhone 6s부터 / iPad Pro 2016부터 / iPad 2017 이상)-iOS 11 실행 이상
    - 부터 xcode 9.2 사용 하 여 Mac
- Apple 개발자 계정, 평가판 또는 [유료](https://developer.apple.com/)
- Microsoft Visual Studio 2017

### <a name="building-the-spectator-view-native-plugin"></a>Spectator 보기 기본 플러그 인 작성

필요한 파일을 생성 하려면 다음이 단계를 수행 합니다. https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md

### <a name="project-setup"></a>프로젝트 설정

1. 장면 준비, 전 세계 루트 gameobject 아래에 포함 된 장면 내 모든 보이는 gameobject를 보장 합니다.

    ![전 세계 루트](images/SpecViewPhoneWorldRoot2.PNG)

2. SpectatorView prefab 추가 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) 장면에 있습니다.
3. SpectatorViewNetworking prefab 추가 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) 장면에 있습니다.
4. SpectatorViewNetworking gameobject를 선택 하 고 SpectatorViewNetworkingManager 구성 요소에는 몇 가지 항목을 연결할 수 있습니다. 왼쪽에 그대로 유지 하는 경우 필요한 스크립트 런타임 시이 구성 요소 검색 됩니다.
    - Marker Detection HoloLens -> SpectatorView/Hololens/MarkerDetection
    - 표식을 생성 3D SpectatorView/IPhone/SyncMarker/3DMarker->

    ![SpectatorView 네트워크 검색](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a>앱 네트워킹

- Spectator UNET를 사용 하 여 해당 네트워킹에 대 한 뷰와 사용자를 위해 모든 호스트 클라이언트 연결을 관리 합니다.
- 앱 특정 데이터를 동기화 하 고 예를 들어 SyncVars NetworkTransform, NetworkBehavior를 사용 하 여 구현 해야 합니다.
- Unity 네트워킹에 대 한 자세한 내용은 참조 하십시오 [멀티 플레이 게임 및 네트워킹](https://docs.unity3d.com/Manual/UNet.html)합니다. (참고: UNet는 더 이상 사용 되지 않습니다. 이 문제를 해결 Spectator 보기 코드 베이스의 현재 리팩터링)

### <a name="building-for-each-platform-hololens-or-ios"></a>각 플랫폼 (HoloLens 또는 iOS)

- IOS 용으로 빌드하 하는 경우 이것은 아직이 플랫폼과 호환 MRTK의 GLTF 구성 요소를 제거 해야 합니다.
- SpectatorView prefab의 최상위 수준에 ' 플랫폼 Switcher' 라는 구성 요소입니다. 에 대 한 빌드 하려는 플랫폼을 선택 합니다.
    - 'Hololens'를 선택 하는 경우 iPhone gameobject 비활성화 될 SpectatorView prefab의 아래에 있는 모든 gameobject 및 'Hololens' 활성화에서 모든 gameobject 표시 됩니다.
    - 플랫폼에 따라 선택 하 여는 HoloToolkit 되 잠시 걸릴 수 있습니다이 프로젝트에서 추가 또는 제거 합니다.

    ![플랫폼 전환기](images/SpecViewPhoneSwitcher.PNG)

- Unity 사용 하 여 확인할 수 없는 문제로 인해 같은 Unity 편집기 인스턴스 (간의 닫지 Unity 빌드 안 함)를 사용 하 여 응용 프로그램의 모든 버전을 빌드를 확인 합니다.

### <a name="running-your-app"></a>앱 실행

작성 하 고 응용 프로그램 및 HoloLens iPhone에서의 버전을 배포 후에 연결할 수 있어야 합니다.

1. 장치와 같은 Wi-fi 네트워크에 있는지 확인 합니다.
2. 순서에 관계 없이 두 장치에서 응용 프로그램을 시작 합니다. IPhone에서 응용 프로그램을 시작 하는 프로세스를 켜고 사진을 찍을 시작 HoloLens 카메라를 트리거해야 합니다.
3. IPhone 앱이 시작 되는 즉시 바닥 나 테이블과 같은 표면에 표시 됩니다. 화면 발견 되 면 아래와 유사한 표식을 표시 되어야 합니다. 이 마커는 HoloLens를 보여 줍니다.

    ![표식](images/SpecViewPhoneMarker.PNG)

4. 표식에 감지 되 면 여는 HoloLens 사라져야 및 두 장치를 연결 하 고이 공간적으로 동기화 해야 합니다.

### <a name="recording-video"></a>비디오 녹화

1. 를 캡처하고 iPhone에서 비디오를 저장 하려면 페이지를 누르고 화면 1 초입니다. [기록] 메뉴를 열립니다.
2. 빨간색 record 단추를 탭, 화면 녹화를 시작 하기 전에 카운트다운이 시작 됩니다.
3. 기록 탭 완료 화면 다른 1 초 동안 보관을 중지 단추를 누릅니다.
4. 미리 보기 단추 (파란색 단추)가 나타나지 녹화 한 비디오 로드 되 면 기록 된 비디오를 시청 하려면 탭 하세요.
5. 카메라 앨범에 저장 하는 선택한 공유 시트를 엽니다.

### <a name="example-scene"></a>예제 장면

예제 장면에서 찾을 수 있습니다 [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)

### <a name="troubleshooting"></a>문제 해결

**Unity 편집기에는 HoloLens 장치에 의해 호스트 되는 세션에 연결 되지 않는**

- Windows 방화벽을 수 있습니다.
- Windows 방화벽 옵션으로 이동 합니다.
- 앱 또는 Windows 방화벽을 통해 기능을 허용 합니다.
- 인스턴스에 대 한 모든 목록 틱에서 Unity 편집기의 도메인, 사설 및 공용입니다.
- 그런 다음 Windows 방화벽 옵션을 다시 이동 합니다.
- 고급 설정을 클릭 합니다.
- 인바운드 규칙을 클릭 합니다.
- 모든 인스턴스가 Unity 편집기의 녹색 틱이 있어야 합니다.
- Unity 편집기의 모든 인스턴스에 대 한 녹색 틱이 없는 합니다.
    - 두 번 클릭 합니다.
    - 작업 대화 상자에서 연결 허용을 선택 합니다.
    - 확인을 클릭합니다.
    - Unity 편집기를 다시 시작 합니다.

**런타임 시 iPhone 화면에는 "찾기 Floor..."이 표시 됩니다. 하지만 AR 마커를 표시 하지 않습니다.**

- IPhone 가로 화면을 가리키는 바닥 이나 테이블 iPhone 카메라를 사용해 서 원하는 됩니다. 이 화면을 HoloLens와 공간적으로 동기화 하는 데 필요한 찾을 ARKit 도움이 됩니다.

**HoloLens 카메라 본체가 켜지 지 않는다 자동으로 iPhone 하려고 할 때 조인 합니다.**

- HoloLens와 iPhone 같은 Wi-fi 네트워크에서 실행 되 고 있는지 확인 하십시오.

**Spectator 보기 응용 프로그램에 모바일 장치를 시작할 때 다른 Spectator 보기 앱을 실행 하는 다른 hololens 자신의 카메라 설정**

- Goto NewDeviceDiscovery 구성 요소 및 두 개의 고유 값에 브로드캐스트 키와 브로드캐스트 포트를 변경 합니다.
- SpectatorViewDiscovery 이동한 다른 고유한 숫자 집합 키 브로드캐스트 및 브로드캐스트 포트를 변경 합니다.

**HoloLens mac Unity 편집기를 사용 하 여 연결 되지 않습니다.**

- Unity 버전에 연결할 수 있는 알려진된 문제입니다. 여전히 건물 iPhone 작동 하 고 정상적으로 연결 해야 합니다.

**HoloLens 카메라가 설정 하지만 마커를 검색할 수 없는 합니다.**

- 같은 Unity 편집기 인스턴스 (간의 닫지 Unity 빌드 안 함)를 사용 하 여 응용 프로그램의 모든 버전을 빌드하는 것을 확인 합니다. Unity 사용 하 여 알 수 없는 문제 때문입니다.

## <a name="spectator-view-pro"></a>Spectator 보려면 Pro

![Spectator 뷰 설정](images/spectatorview-300px.png)

Spectator 보기 Pro를 사용 하 여 이러한 네 가지 구성 요소가 포함 됩니다.
1. 기반으로 하는 spectator 보기 위해 특별히 빌드된 앱 [혼합된 현실 환경 공유할](shared-experiences-in-mixed-reality.md)합니다.
2. 사용자가 앱을 사용 하 여 HoloLens 착용입니다.
3. Spectator 보기 카메라 rig 3 인칭 관점 비디오를 제공 합니다.
4. Spectator 보기 비디오를 공유할 앱 및 합치기를 홀로그램을 실행 하는 데스크톱 PC.

![Spectator 보기 Pro 설정](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a>사용 사례

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


*여전히 이미지, 비디오 클립을 또는 라이브 데모를 보려면이 든 상관 없이 프로그램 holographic 만들기 공유 spectator 보기를 사용할 수 있습니다.*


이 기술은 잘 작동 하는 세 가지 주요 시나리오는

**1. 사진 캡처**<br>
이 기술을 사용 하 여 홀로그램의 고해상도 이미지를 캡처할 수 있습니다. 이벤트를 마케팅 콘텐츠를 소개, 잠재적 클라이언트에 게 보내거나도 Windows 스토어에 응용 프로그램을 제출 이러한 이미지를 사용할 수 있습니다. 이러한 이미지를 캡처하는 데 사용할 것인지는 사진 카메라를 결정 하, 따라서 품질 DSLR 카메라가 좋습니다.


![Spectator 보기 Pro 사진 캡처 예제](images/fall-350px.jpg)<br>
*사진 캡처 예제-바닥에 표시 되 게 밑바닥 이루어져 있습니다.*


**2. 비디오 캡처**<br>
비디오는 최적의 스토리 holographic 앱 경험 많은 사용자와 공유 하기 위한 메커니즘을 지시 합니다. Spectator 보기에는 카메라, lens 고 프레이밍 가장 짝패가 앱 소개 하고자 하는 방법을 선택할 수 있습니다. 배치 하면 사용할 수 있는 비디오 하드웨어를 기반으로 비디오 품질을 제어 합니다.

![Spectator 보기 Pro 비디오 캡처 예제](images/spectatorviewvideo.gif)<br>
*비디오 캡처 예제-혼합된 현실 공동 작업을 기록 합니다.*


**3. 라이브 데모**<br>
카메라 위치 안정적인 / 제어 된 유지 spectator 보기는 라이브 데모에 대 한 기본 설정된 방법. 고품질 비디오 카메라를 사용할 수 있으므로 큰 화면을 위한 고품질 이미지를 생성할 수도 있습니다. 해당 설정에 대 한 줄에서 대기 하는 즉시 참가자 개까지 화면에 라이브 데모를 스트리밍에 대 한 적절 한 이기도 합니다.

### <a name="comparing-video-capture-techniques"></a>비디오 캡처 기술 비교

[혼합 현실 캡처](mixed-reality-capture.md) (MRC) 비디오 조합으로 구성 된 첫 번째 사용자-의-관점에서 표시 하는 HoloLens 사용자가 제공 합니다. Spectator 보기 홀로그램 및 HoloLens 장치 착용 사용자 환경을 보려면 비디오 관찰자 허용 3 인칭 관점에서 비디오를 생성 합니다. 카메라의 선택 했으므로 더 높은 해상도 및 MRC 이미지에 사용 되는 기본 제공 HoloLens 카메라 보다 더 나은 품질 이미지 spectator 보기도 생성할 수 있습니다. 이러한 이유로 spectator 보기는 더 적합 마케팅 비디오, Windows 스토어에서 앱 이미지 또는 대상에 대 한 실시간 보기를 프로젝션 합니다.

![Microsoft 기조 프레젠테이션에서 사용 하는 전문 카메라 보기 Pro spectator](images/spectator-view-professional-red-camera-300px.jpg)<br>
*Microsoft 기조 프레젠테이션에서 사용 하는 전문 카메라 보기 Pro spectator*


Spectator 보기를 표시 하는 Microsoft HoloLens 환경을 대상 그룹을 처음부터 제품 2015 년 1 월에에서 발표 했을 때 필수적인 부분을 되었습니다. 사용 되는 전문 설정을 많이 요구 하는 비용이 많이 드는 가격 태그를 절감 했습니다. 예를 들어, 카메라 genlock 신호를 사용 하 여 추적 시스템 HoloLens를 사용 하 여 조정 하는 정확한 시간을 확인 합니다. 이 설치에서 spectator 보기 카메라를 이동할 수 있었습니다 홀로그램 HoloLens에서 직접 경험을 표시 하는 사용자의 환경에 맞게 안정적인 하면서.

Spectator 보기의 오픈 소스 버전 trades 카메라 rig를 전체 설치의 비용을 크게 낮추기 위해 이동 기능을 해제 합니다. 이 프로젝트는 HoloLens에 엄격 하 게 탑재 하는 외부 카메라를 사용 하 여 고화질 사진을 찍고 holographic Unity 프로젝트의 비디오. **라이브 데모 중 카메라는 고정된 된 위치에 유지 되어야 합니다.** 카메라 이동 홀로그램 지터 또는 드리프트 발생할 수 있습니다. 비디오 프레임의 타이밍 및 렌더링을 PC에 제공 될 수 있습니다 정확 하 게 동기화 되지 때문입니다. 따라서 카메라를 계속 유지 또는 이동 제한 보이는 하는 사람을 HoloLens에 가까운 결과 생성 합니다.

앱 spectator 보기에 대 한 준비를 위해 작성 해야는 [경험을 공유](holograms-240.md) 앱 HoloLens 뿐만 아니라 Unity 편집기의 바탕 화면에서 앱이 실행 수를 확인 합니다. 데스크톱 버전의 앱에 추가 구성 요소를 렌더링된 홀로그램을 사용 하 여 비디오 피드 하는 복합 기본 제공 해야 합니다.

## <a name="how-to-set-up-spectator-view-pro"></a>Spectator 보기 Pro 설정 하는 방법 

### <a name="requirements"></a>요구 사항

![Spectator 보기 Pro Rig](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a>하드웨어 구입 목록

아래 권장 되는 하드웨어 목록을 이지만 너무 호환 다른 단위를 사용 하 여 실험할 수 있습니다. 

|하드웨어 구성 요소                                                                     |권장               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|HoloLens 에뮬레이터를 사용 하 여 holographic 개발에 대해 작동 하는 PC 구성  |                              | 
|Out HDMI 또는 사진 캡처 SDK 사용 하 여 카메라                                             | 사진 및 비디오 캡처에 대 한 테스트를 거쳤습니다 합니다 [율이 EOS 5d 표시 III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) 카메라입니다. 라이브 데모에 대 한 테스트를 거쳤습니다 합니다 [Blackmagic 디자인 프로덕션 카메라 4k](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k)합니다.<br><br>단, 모든 카메라 HDMI (예: GoPro) out을 사용 하 여 작동 해야 합니다. 다양 한 비디오를 사용 합니다 [율이 EF 14 mm f/2.8 L II USM 매우 광범위 각도 고정 렌즈](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), 요구 사항을 충족 하는 카메라 렌즈를 선택 해야 하지만 합니다. | 
|카드 색 프레임 카메라 rig를 보정 복합 장면 미리 보기를 활용 하려면 PC에 대 한 캡처 |  테스트를 거쳤습니다 합니다 [Blackmagic 디자인 강도 Pro 4k 캡처 카드](https://www.amazon.com/dp/B00U3QNP7Q)합니다. | 
|케이블                                                                                 |  [미니 HDMI를 HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) 카메라 캡처 카드에 연결 합니다. 카메라에 맞는 HDMI 폼 팩터를 구매를 확인 합니다. (GoPro를 통해 예를 들어 출력 [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)<br><br>[HDMI 케이블](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) 복합 preview 모니터 또는 텔레비전에 피드를 보기 위한 | 
|Aluminum 대괄호에 HoloLens 카메라에 연결할 컴퓨터. | [Aluminum 대괄호](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|3D는 카메라 hotshoe에 HoloLens 탑재를 연결 하는 어댑터를 인쇄 합니다.| [3D 인쇄 어댑터](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|Hotshoe fastener hotshoe 어댑터를 탑재 하려면                                       |  [Hotshoe Fastener](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|선별 된 너트, bolt 및 도구                                                |  [1/4-20 "너트](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[1/4-20 "x 3/4" Bolt](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[7 월 16 너트 드라이버](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[T15 Torx](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[T7 Torx](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a>소프트웨어 구성 요소

1. 소프트웨어를 다운로드 합니다 [spectator 보려면 GitHub 프로젝트](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)합니다.
2. [Blackmagic Capture Card SDK](https://www.blackmagicdesign.com/support).\
 데스크톱 비디오 개발자 SDK "최신 다운로드"를에서 검색 합니다.
3. [Blackmagic 데스크톱 비디오 런타임](https://www.blackmagicdesign.com/support). \
 데스크톱 비디오 소프트웨어 업데이트 "최신 버전 다운로드"에 대 한 검색 합니다. \
 SDK 버전을 버전 번호가 일치를 확인 합니다.
4. [OpenCV 3.1](https://opencv.org/releases.html) 보정 또는 Blackmagic 캡처 카드 없이 비디오 캡처에 대 한 합니다.
5. [SDK 율이](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (선택 사항). \
 율이 카메라를 사용 하는 경우 율이 SDK에 대 한 액세스 권한이 더 높은 해상도 이미지를 사용자 PC에 카메라가 tether 수 있습니다.
6. Holographic 응용 프로그램 개발에 대 한 unity. \
 OSS 프로젝트에서 지원 되는 버전을 찾을 수 있습니다.
7. 최신 업데이트가 포함 된 visual Studio 2015

### <a name="building-your-own-spectator-view-pro-camera"></a>사용자 고유의 Spectator 보기 Pro 카메라 구축

**공지 및 고 지 사항:** 수정할 때는 HoloLens 하드웨어 (등 "spectator 보기" 프로그램 HoloLens 설정에 국한 되지 않음) 기본 안전 주의 사항은 항상 관찰 해야 합니다. 수정 하기 전에 모든 지침 및 설명서를 읽습니다. 것이 모든 지침 및 지시에 따라 도구를 사용 해야 합니다. 구매 하였거나 라이선스에 HoloLens 제한적된 보증 또는 보증도 하지 않습니다. 해당을 참조 하세요 [HoloLens 사용권 계약 또는 사용 약관 및 판매](https://www.microsoft.com/hololens/support/warranty) 보증 옵션을 이해 합니다.

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a>Rig 어셈블리

![HoloLens 및 DSLR 카메라를 사용 하 여 어셈블된 Spectator 보기 Pro rig를 지원 합니다.](images/assembly.gif)<br>
*HoloLens 및 DSLR 카메라를 사용 하 여 어셈블된 Spectator 보기 Pro rig*


* headband는 HoloLens에서 제거할 T7 스크루 드라이버를 사용 합니다. 나사에 완화 되 면 다른 쪽에서 클립을 사용 하 여 해당 포크 합니다.
* 내부에 나사 한도 제거 작은 머리 스크루 드라이버를 사용 하 여 HoloLens 하이퍼바이저 앞입니다.
* T15 스크루 드라이버를 사용 하 여 작은 torx bolt는 사용자를 제거해 HoloLens 대괄호를 제거할 및 후크 모양의 첨부 파일입니다.
* 앞면 대괄호의 돌출을 사용 하 여는 하이퍼바이저의 안쪽에 노출 된 구멍에 맞춰 정렬 된 대괄호에는 HoloLens를 배치 합니다. HoloLens' 무기 거래 대괄호의 맨 아래에 핀으로 위치에 유지 되어야 합니다.
* 다시 연결 하는 및를 대괄호로 HoloLens 보안 후크 모양의 첨부 파일입니다.
* 카메라의 hotshoe를 hotshoe fastener를 연결 합니다.
* Hotshoe fastener에 탑재 어댑터를 연결 합니다.
* 좁은 쪽은 앞으로 연결 되므로 어댑터와 동시에 카메라의 렌즈를 회전 합니다.
* 7 월 16 너트 드라이버를 사용 하 여 1/4"너트를 사용 하 여 현재 위치에서 어댑터를 보호 합니다.
* HoloLens' 하이퍼바이저 전면의와 최대한 가까이 카메라의 렌즈의 맨 앞으로 이므로 어댑터에 대 한 괄호를 배치 합니다.
* 7 월 16 너트 드라이버를 사용 하 여 4 1/4"nuts and bolt를 사용 하 여는 괄호를 연결 합니다.

#### <a name="pc-setup"></a>PC 설정
* 소프트웨어 구성 요소 섹션에서 소프트웨어를 설치 합니다.
* 마더보드에 열기 PCIe 슬롯에 캡처 카드를 추가 합니다.
* 카메라에서 외부 HDMI 슬롯에는 HDMI 케이블 (HDMI에서) 해당 캡처 카드.
* 선택적인 미리 보기 모니터로 캡처 카드 center HDMI 슬롯 (HDMI 스케일 아웃)에서 HDMI 케이블을 연결 합니다.

#### <a name="camera-setup"></a>카메라 설정
* 3: 4 사진 확인 전체 해상도 1920x1080 보다는 자른를 출력 하므로 카메라 비디오 모드로 변경 합니다.
* 카메라 HDMI 설정을 찾아서 사용 하도록 설정 **미러링** 하거나 **듀얼 모니터**합니다.
* 1080 p 출력 해상도 설정 합니다.
* 해제 **화면에서 보기 Live 표시** 하므로 모든 화면 오버레이 피드 복합에 나타나지 않습니다.
* 카메라를 켜려면 **Live 보기**합니다.
* 사용 하는 경우는 **율이 SDK** flash 단위 사용, 사용 하지 않도록 설정 하려는 **LV 자동 해결**합니다.
* 외부 HDMI 슬롯에는 HDMI 케이블 카메라에서 (HDMI에서) 해당 캡처 카드.

#### <a name="calibration"></a>보정

Spectator 보기 rig를 설정한 후에 HoloLens에 카메라의 위치 및 회전 오프셋을 얻기 위해 조정 해야 합니다.
* Calibration\Calibration.sln 아래 보정 Visual Studio 솔루션을 엽니다.
* 이 솔루션에서는 타사 파티 원본의 inc 위치에 대 한 매크로 만드는 파일 dependencies.props를 찾을 수 있습니다.
* 이 파일을 업데이트할 위치를 사용 하 여 설치한 OpenCV 3.1, Blackmagic SDK 및 율이 SDK (있는 경우)

![Visual Studio에서 종속성 위치 스냅숏](images/dependencies-600px.png)<br>
*Visual Studio에서 종속성 위치 스냅숏*


* 보정 패턴 Calibration\CalibrationPatterns\2_66_grid_FULL.png 플랫, 엄격한 화면에 인쇄 합니다.
* PC에 USB를 통해 여 HoloLens를 연결 합니다.
* 전처리기 정의 업데이트할 **HOLOLENS_USER** 하 고 **HOLOLENS_PW** 에서 **stdafx.h** HoloLens' 장치 포털 자격 증명을 사용 하 여 합니다.
* HDMI 통해 카메라 캡처 카드에 연결 하 고 전원을 켭니다.
* 보정 솔루션을 실행 합니다.
* 다음과 같은 뷰 주변 체크 무늬 패턴을 이동 합니다.

![보정 Spectator 보기 Pro rig](images/calibration.gif)<br>
*보정 Spectator 보기 Pro rig*


* 그림은 바둑판 표시 되 면 자동으로 수행 됩니다. 다음 포즈로 진행 하기 전에 HoloLens의 하이퍼바이저에 흰색 광원을 찾습니다.
* 완료 되 면 키를 눌러 **Enter** 보정 앱 만들려면 포커스에는 **CalibrationData.txt** 파일.
* 이 파일에 저장 됩니다 **Documents\CalibrationFiles\CalibrationData.txt**
* 보정 데이터를 정확 하 게이 파일을 검사 합니다.
   * **DSLR RMS** 0에 가까워야 합니다.
   * **HoloLens RMS** 0에 가까워야 합니다.
   * **스테레오 RMS** 수 20-50, 이것은 허용 때문에 두 카메라 간에 보기의 필드는 다를 수 있습니다.
   * **번역** 연결 된 카메라의 렌즈를 HoloLens' 카메라의 거리입니다. 미터입니다.
   * **회전** identity에 가까워야 합니다.
   * **DSLR_fov** y 값이 세로 보기의 필드 필터의 초점 모든 카메라 본문 자르기 요소를 예상 가까워야 합니다.
* 이해 하기 표시 되지 않으면 위의 값 중 하나를 조정 합니다.
* 이 파일을 복사 합니다 **자산** Unity 프로젝트의 디렉터리입니다.

### <a name="compositor"></a>Compositor

작성자는 Unity 편집기의 창으로 실행 되는 Unity 확장입니다. 이 작업이 가능 하도록 Compositor Visual Studio 솔루션을 먼저 빌드해야 해야 합니다.
* Compositor\Compositor.sln 아래 Compositor Visual Studio 솔루션을 엽니다
* 위의 보정 솔루션에서 동일한 조건을 사용 하 여 dependencies.props를 업데이트 합니다. 보정 단계를 수행 하는 경우이 파일은 이미 업데이트 되었습니다.
* 릴리스 및 Unity 버전의 아키텍처와 일치 하는 아키텍처 전체 솔루션을 빌드하십시오. 확실 하지 않은의 경우 x86 및 x64)를 빌드하십시오.
* X64에 대 한 솔루션을 빌드한 경우 또한 프로젝트를 빌드합니다 SpatialPerceptionHelper x86 있으므로 HoloLens에서을 실행 합니다.
* 응용 프로그램이 실행 되는 경우에 Unity를 닫습니다. Unity는 Dll은 런타임에 변경 되는 경우 다시 시작할 수 있어야 합니다.
* Unity 프로젝트에이 솔루션에서 빌드한 Dll에 복사할 Compositor\CopyDLL.cmd를 실행 합니다. 이 스크립트는 포함 된 샘플 프로젝트에 Dll을 복사 합니다. 설정 된 사용자 고유의 프로젝트를 만든 후 CopyDLL 있습니다도 복사할 프로젝트의 자산 디렉터리를 가리키는 명령줄 인수를 사용 하 여 실행할 수 있습니다.
* 샘플 Unity 앱을 시작 합니다.

### <a name="unity-app"></a>Unity 앱

Compositor는 Unity 편집기의 창으로 실행 됩니다. 포함 된 샘플 프로젝트에 모든 설정 되 면 Dll이 복사 됩니다 compositor spectator 보기를 사용 하 여 작동 합니다.

Spectator view 필요으로 실행 되도록 응용 프로그램을 [경험을 공유](holograms-240.md)합니다. 이 HoloLens에서 발생 하는 응용 프로그램 상태 변경 네트워크를 통해 너무 Unity에서 실행 되는 앱을 업데이트 해야 한다는 것을 의미 합니다.

새 Unity 프로젝트에서 시작 하며, 경우에 일부 설치 프로세스를 먼저 수행 해야 합니다.
* 복사본 **자산/추가 기능/HolographicCameraRig** 프로젝트에 샘플 프로젝트에서.
* 프로젝트에 최신 MixedRealityToolkit 추가 포함 **공유**, **csc.rsp**, **gmcs.rsp**, 및 **smcs.rsp**합니다.
* 추가 프로그램 **CalibrationData.txt** 자산 디렉터리에 파일입니다.

![Unity 자산 디렉터리 스냅숏](images/files-400px.png)

* 추가 된 **HolographicCameraRig\Prefabs\SpectatorViewManager** 장면 prefab 및 필드를 입력 합니다.
   * **HolographicCameraManager** HolographicCameraRig prefab 디렉터리에서 HolographicCameraManager prefab으로 채워져야 합니다.
   * **앵커** HolographicCameraRig prefab 디렉터리에서 앵커 prefab으로 채워져야 합니다.
   * **공유** 는 MixedRealityToolkit에서 공유 prefab으로 채워져야 합니다.
   * 참고: 이러한 prefabs 이미 있는 경우 프로젝트 계층 구조에서 기존 prefabs이이 부분은 대신 사용 됩니다.
   * **Spectator 보기 IP** spectator 보기 rig에 연결 하 여 HoloLens의 IP 여야 합니다.
   * **공유 서비스 IP** MixedRealityToolkit SharingService를 실행 하는 PC의 IP 여야 합니다.
   * 선택 사항: 여러 PC에 연결 된 rig를 보고 하는 여러 spectator 있으면의 **로컬 컴퓨터 IP** spectator 보기 rig와 통신 하는 PC를 사용 하 여 설정 해야 합니다.

![Unity에서 spectator 보기 관리자 속성](images/spectatorviewmanager-500px.png)

* 시작 된 MixedRealityToolkit **공유 서비스**
* 빌드하고 spectator 보기 rig에 연결 하는 HoloLens에 D3D UWP 앱을 배포 합니다.
* 환경에서 다른 HoloLens 장치에 앱을 배포 합니다.
* 확인 합니다 **백그라운드에서 실행** 확인란 **플레이어 설정/편집/프로젝트**합니다.

![Unity의 배경 설정에서 실행](images/run-in-bg-400px.png)
* Compositor 창의 시작 **Spectator 보기/작성자**

![Unity의 spectator 뷰에 대 한 작성자 보기](images/compositor-500px.png)

* 이 창에서는 수 있습니다.
   * 비디오 녹화 시작
   * 사진 가져오기
   * 홀로그램 불투명도 변경 합니다.
   * (조정 하는 캡처 카드 대기 시간에 대 한 계정에 색 타임 스탬프) 프레임 오프셋 변경
   * 캡처에 저장 된 디렉터리를 엽니다.
   * (프로젝트에의 한 SpatialMappingManager 있으면) spectator 보기 카메라에서 공간 매핑 데이터를 요청
   * 장면의 복합 뷰 뿐만 아니라 색, 홀로그램, 및 알파 채널을 개별적으로 시각화 합니다.
   * 카메라를 켭니다.
   * Unity에서 play 키를 누릅니다.
   * 카메라를 이동할 때 있는 피드 카메라 색을 기준으로 실제 환경에서 Unity에서 제공 해야 합니다.

## <a name="see-also"></a>참조

* [혼합된 현실 캡처](mixed-reality-capture.md) 
* [개발자를 위한 실제로 캡처 혼합](mixed-reality-capture-for-developers.md)
* [혼합된 현실 환경 공유했습니다](shared-experiences-in-mixed-reality.md)
* [GitHub에서 보기 (미리 보기) 코드 spectator](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [Spectator GitHub에서 네이티브 코드 보기 (미리 보기)](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [GitHub에서 보기 Pro 코드 spectator](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
