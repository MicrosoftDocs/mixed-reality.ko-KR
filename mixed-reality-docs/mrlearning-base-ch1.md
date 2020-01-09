---
title: 시작 자습서 - 2. 프로젝트 및 첫 번째 애플리케이션 초기화
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334409"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. 프로젝트 및 첫 번째 애플리케이션 초기화

## <a name="overview"></a>개요

이 첫 번째 단원에서는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK(Mixed Reality Toolkit)</a>에서 제공해야 하는 기능 중 일부에 대해 알아보고, HoloLens 2용 첫 번째 애플리케이션을 시작하고, 이를 디바이스에 배포합니다.

## <a name="objectives"></a>목표

* HoloLens 개발을 위해 Unity를 구성합니다.
* 자산을 가져오고 장면을 설정합니다.
* 공간 매핑 메시, 손 메시 및 프레임 속도 카운터를 시각화합니다.

## <a name="create-new-unity-project"></a>새 Unity 프로젝트 만들기

1. Unity를 시작합니다.

2. **New**를 선택합니다.

    ![단원 1 섹션 1 단계 2](images/mrlearning-base-ch1-1-step2.JPG)

3. 프로젝트 이름(예: "MixedRealityBase")을 입력합니다.

    ![단원 1 섹션 1 단계 3](images/mrlearning-base-ch1-1-step3.JPG)

4. 프로젝트를 저장할 위치를 입력합니다.

    ![단원 1 섹션 1 단계 4](images/mrlearning-base-ch1-1-step4.JPG)

5. 프로젝트가 **3D**로 설정되어 있는지 확인합니다.

    ![단원 1 섹션 1 단계 5](images/mrlearning-base-ch1-1-step5.JPG)

6. **Create Project**를 클릭합니다.

    ![단원 1 섹션 1 단계 6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality를 위한 Unity 프로젝트 구성

1. **파일** > **빌드 설정**으로 차례로 이동하여 *빌드 설정* 창을 엽니다.

    ![단원 1 섹션 2 단계 1](images/mrlearning-base-ch1-2-step1.JPG)

2. *유니버설 Windows 플랫폼*을 선택하고, **플랫폼 전환** 단추를 클릭하여 플랫폼을 전환합니다. HoloLens 2에서 실행되는 애플리케이션은 UWP(유니버설 Windows 플랫폼)와 호환되어야 합니다.

    ![단원 1 섹션 2 단계 2](images/mrlearning-base-ch1-2-step2.JPG)

3. [빌드] 창에서 **플레이어 설정** 단추를 클릭하여 가상 현실을 사용하도록 설정하고, 아래 이미지와 같이 검사기 패널의 [XR 설정] 아래에서 *가상 현실 지원* 확인란을 사용하도록 설정합니다. 검사기 패널을 표시하기 위해 *빌드 설정* 창을 다른 위치로 끌어야 할 수도 있습니다. 또한 *가상 현실 지원* 확인란은 입체 시각(stereoscopic vision, 각 눈에 대해 서로 다른 이미지 렌더링)을 사용하도록 설정한다는 것을 나타내므로 Mixed Reality(혼합 현실) 및 Augmented Reality(확대된 현실) 헤드셋에도 적용됩니다.

    ![단원 1 섹션 2 단계 3](images/mrlearning-base-ch1-2-step3.JPG)

4. [XR 설정] 아래에서 *스테레오 렌더링 모드*를 *단일 패스 인스턴스화됨*으로 변경합니다. 이 [렌더링 파이프라인 스타일](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)은 일반적으로 HoloLens 2에 가장 적합합니다. Unity 환경의 다른 성능 구성에 관심이 있는 경우 [이 지침](recommended-settings-for-unity.md)을 따르세요.

    ![단원 1 섹션 2 단계 4](images/mrlearning-base-ch1-2-step4.jpg)

5. 동일한 검사기 패널에 있는 *게시 설정* 아래의 [기능] 섹션에서 *Spatial Perception* 확인란을 사용하도록 설정되어 있는지 확인합니다. Spatial Perception(공간 인식)을 사용하면 HoloLens 2와 같은 혼합 현실 디바이스에서 공간 매핑 메시를 시각화할 수 있습니다. [게시 설정]은 검사기 패널에서 [XR 설정] 위와 [기타 설정] 아래에 있습니다.

    ![단원 1 섹션 2 단계 5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    >이 섹션에서 사용되지는 않지만, 사용하도록 설정할 수 있는 몇 가지 다른 일반적인 기능으로 *Microphone*(음성 명령용) 및 *InternetClient*(네트워크 연결이 필요한 서비스 연결용)가 있습니다.

## <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 가져오기

1. [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [기초 패키지 버전 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)을 다운로드하여 PC의 폴더에 저장합니다.

2. 이전 단계에서 다운로드한 *Mixed Reality Toolkit* 패키지를 가져옵니다. 먼저 **자산** > **가져오기** > **사용자 지정 패키지**를 클릭하고, *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage*를 선택하고, 이를 열어 가져오기 프로세스를 시작합니다. 가져오기 프로세스가 완료될 때까지 몇 분 정도 기다리세요.

    ![단원 1 섹션 3 단계 2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![단원 1 섹션 3 단계 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. 다음 팝업 창에서 **가져오기**를 클릭하여 선택한 패키지를 Unity 프로젝트로 가져오기 시작합니다. 이미지와 같이 모든 항목이 선택되어 있는지 확인합니다.

    ![단원 1 섹션 3 단계 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Mixed Reality Toolkit 기본 설정을 적용하도록 요청하는 팝업 대화 상자가 표시되면 **적용**을 클릭합니다. MRTK는 자동화된 설정을 위해 가져올 때 누락된 추천 설정이 있는지 프로젝트를 분석합니다. 설정에 따라 팝업이 아래 이미지와 다르게 보일 수 있습니다.

    ![단원 1 섹션 3 단계 4 참고 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 구성

1. 메뉴 모음에서**Mixed Reality Toolkit** > **장면에 추가 및 구성..** 을 차례로 선택하여 *Mixed Reality Toolkit*를 현재 장면에 추가합니다. Mixed Reality Toolkit을 가져온 후에 이 메뉴 항목이 보이지 않으면 Unity를 다시 시작합니다.

    ![단원 1 섹션 4 단계 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > [Mixed Reality Toolkit용 프로필](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)을 선택하기 위한 팝업 대화 상자가 표시될 수 있습니다. *DefaultHoloLens2ConfigurationProfile*이라는 프로필을 두 번 클릭하여 선택합니다.

2. 장면에는 몇 가지 새로운 항목과 수정이 있습니다. **파일** > **다른 이름으로 저장...** 을 클릭하여 장면을 다른 이름으로 저장하고, 해당 장면에 *BaseScene*과 같은 이름을 지정합니다. 프로젝트의 *Assets* 폴더에 있는 *Scenes* 폴더에 저장하여 장면을 정리합니다.

    ![단원 1 섹션 4 단계 2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![단원 1 섹션 4 단계 2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a>디바이스로 애플리케이션 빌드

1. 이전 섹션에서 *빌드 설정* 창을 닫은 경우 **파일** > **빌드 설정**으로 차례로 이동하여 *빌드 설정* 창을 다시 엽니다.

    ![단원 1 섹션 5 단계 1](images/mrlearning-base-ch1-5-step1.JPG)

2. 장면이 Unity에서 열려 있는 상태에서 **열린 장면 추가** 단추를 클릭하여 방금 만든 장면이 *빌드 중 장면* 목록에 있는지 확인합니다.

3. **빌드** 단추를 눌러 빌드 프로세스를 시작합니다.

    ![단원 1 섹션 5 단계 3](images/mrlearning-base-ch1-5-step3.JPG)

4. 애플리케이션의 새 폴더를 만들고 이름을 지정합니다. 아래 이미지에서는 애플리케이션을 포함할 App이라는 폴더가 만들어졌습니다. **폴더 선택**을 클릭하여 빌드를 새로 만든 폴더에 시작합니다. 빌드가 완료되면에 Unity에서 *빌드 설정* 창을 닫을 수 있습니다.

    ![단원 1 섹션 5 단계 4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    >빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다. 오류: CS0246 = "XX" 유형 또는 네임스페이스 이름을 찾을 수 없습니다. using 지시문 또는 어셈블리 참조가 누락되었습니까?와 같은 오류가 표시되는 경우 [Windows 10 SDK(10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)를 설치해야 할 수 있습니다.

5. 빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다. *MixedRealityBase.sln* 솔루션 또는 해당 이름(프로젝트에 대한 대체 이름을 사용한 경우)을 두 번 클릭하여 Visual Studio에서 솔루션 파일을 엽니다.

    >[!NOTE]
    >새로 만든 폴더(즉, 이전 단계의 명명 규칙을 따르는 경우 *App* 폴더)를 열어야 합니다. 이 폴더 외부에 비슷한 이름의 .sln 파일이 있으므로 빌드 폴더 내의 .sln 파일과 혼동하지 않도록 주의합니다. 폴더 구조는 아래 이미지와 비슷하게 표시됩니다.
    >
    >Visual Studio에서 새로운 구성 요소를 설치하라는 메시지를 표시하면 ["도구 설치" 페이지](install-the-tools.md)에 지정된 모든 필수 구성 요소가 설치되어 있는지 확인합니다.

    ![단원 1 섹션 5 단계 5](images/mrlearning-base-ch1-5-step5.JPG)

6. HoloLens 2를 PC에 연결합니다. 이러한 지침에서는 HoloLens 2 디바이스에 배포한다고 가정하지만, [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 [테스트용으로 로드할 앱 패키지](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)를 만들도록 선택할 수도 있습니다.

    >[!IMPORTANT]
    >디바이스에 빌드하기 전에 디바이스가 *개발자 모드*에 있고 개발 머신과 페어링되어야 합니다. 이 두 단계는 모두 [이 지침](using-visual-studio.md)에 따라 완료할 수 있습니다.

7. *릴리스* 또는 *마스터* 구성, *ARM* 아키텍처 및 대상으로 *디바이스*를 선택하여 HoloLens 2에 빌드하도록 Visual Studio를 구성합니다.

    ![단원 1 섹션 5 단계 8](images/mrlearning-base-ch1-5-step7.JPG)

8. 마지막 단계는 **디버그** > **디버깅하지 않고 시작**을 차례로 선택하여 빌드하고 디바이스에 배포하는 것입니다. *디버깅하지 않고 시작*을 선택하면 빌드 성공 시 애플리케이션이 디바이스에서 즉시 시작되지만, 디버거가 연결되지 않고 정보가 Visual Studio에 표시되지 않습니다. 따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.

    > [!NOTE]
    > 애플리케이션을 자동으로 시작하지 않고 **빌드** > **솔루션 배포**를 차례로 선택하여 디바이스에 배포할 수도 있습니다.

    ![단원 1 섹션 5 단계 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>축하합니다.

이제 첫 번째 HoloLens 2 애플리케이션을 배포했습니다. 연습을 진행하면서 HoloLens 2에서 인식한 모든 표면이 포함된 공간 매핑 메시가 표시됩니다. 또한 손을 추적하기 위한 손 및 손가락의 표시기와 애플리케이션 성능을 감시하기 위한 프레임 속도 카운터가 표시됩니다. 이러한 기능은 Mixed Reality Toolkit과 함께 기본적으로 포함되어 있는 기본적인 기능 중 일부에 불과합니다. 다음 단원에서는 더 많은 콘텐츠와 대화형 작업을 장면에 추가하여 HoloLens 2 및 Mixed Reality Toolkit의 기능을 전체적으로 살펴볼 수 있습니다.

> [!NOTE]
> 앱에서 시각적 프로파일러를 확인할 수 있습니다. [5단원](mrlearning-base-ch5.md)의 음성 명령을 사용하여 프레임 속도 카운터를 설정/해제하는 방법을 설명합니다. 일반적으로 코드 변경이 성능에 영향을 줄 수 있는 경우를 이해하기 위해 개발 중에 항상 시각적 프로파일러를 표시하는 것이 좋습니다. HoloLens 2 애플리케이션은 [60FPS에서 지속적으로 실행](understanding-performance-for-mixed-reality.md)되어야 합니다.

[다음 단원: 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 도구 키트 구성](mrlearning-base-ch2.md)
