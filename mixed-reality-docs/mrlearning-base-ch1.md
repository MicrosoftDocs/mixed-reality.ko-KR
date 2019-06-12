---
title: MR 학습 기본 모듈 - 프로젝트 초기화 및 첫 번째 애플리케이션
description: 혼합 현실 애플리케이션에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65814008"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR 학습 기본 모듈 - 프로젝트 초기화 및 첫 번째 애플리케이션

이 첫 번째 단원에서는 Mixed Reality Toolkit이 제공해야 하는 몇 가지 기능을 알아보고, HoloLens 2용 첫 번째 애플리케이션을 시작한 후 디바이스에 배포합니다.

## <a name="objectives"></a>목표

* HoloLens 개발을 위해 Unity를 최적화합니다.
* 자산을 가져오고 장면을 설정합니다.
* 공간 메시, 손 메시 및 프레임 속도 카운터의 시각화

## <a name="instructions"></a>지침

### <a name="create-new-unity-project"></a>새 Unity 프로젝트 만들기

1. Unity를 시작합니다.
2. **New**를 선택합니다.
![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)
3. 프로젝트 이름(예: "MixedRealityBase")을 입력합니다.
![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)
4. 프로젝트를 저장할 위치를 입력합니다.
![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)
5. 프로젝트가 **3D**로 설정되어 있는지 확인합니다.
![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)
6. **Create Project**를 클릭합니다.
![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality를 위한 Unity 프로젝트 구성

1. File>Build Settings로 이동하여 Build Settings 창을 엽니다.
![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)
2. "Universal Windows Platform"을 선택하여 "Universal Windows Platform"으로 전환하고 "Switch Platform" 단추를 클릭하여 플랫폼을 전환합니다. HoloLens 2에서 실행 중인 앱은 UWP(유니버설 Windows 플랫폼)이 되어야 합니다.
![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)
3. 아래 그림과 같이 Build 창에서 Player Settings를 클릭하여 가상 현실을 사용하도록 설정한 후 inspector 패널에서 XR Settings 아래에 있는 "Virtual Reality Supported" 확인란을 사용하도록 설정합니다. inspector 패널을 보기 위해 "Build Settings" 창을 다른 위치로 끌어야 할 수도 있습니다. "Virtual Reality Supported" 확인란은 입체 영상을 지원하는 것을 나타내므로(양쪽 눈에 대해 다른 이미지 렌더링) 혼합 현실/AR 헤드셋에도 적용됩니다. ![Lesson1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)
4. 동일한 inspector 패널에서 Publishing Settings 아래의 capabilities 섹션에서 “Spatial Perception” 확인란이 사용하도록 설정되어 있는지 확인합니다. 공간 인식을 사용하면 HoloLens 2와 같은 혼합 현실 디바이스에서 공간 매핑 메시를 시각화할 수 있습니다. Publishing Settings는 Inspector 패널에서 "XR Settings" 위, "Other Settings” 아래에 있습니다.
![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)

> 참고: 이 섹션에서는 사용되지 않지만, 사용하려고 할 수 있는 몇 가지 다른 일반적인 기능에는 Microphone(음성 명령용) 및 InternetClient(네트워크 연결이 필요한 서비스에 연결하는 데 사용)가 포함됩니다.

### <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 가져오기

1. [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) unity 패키지를 다운로드한 후 PC의 폴더에 저장합니다.

2. Assets>Import>Custom Package를 클릭하여 Mixed Reality Toolkit 패키지를 가져옵니다. 1단계에서 다운로드한 Mixed Reality Toolkit 패키지를 찾은 후 열어 가져오기 프로세스를 시작합니다. 가져오기 프로세스가 진행될 때까지 몇 분 정도 기다립니다.
    ![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 다음 팝업 창에서 "Import"를 클릭하여 Mixed Reality Toolkit을 가져옵니다. 이미지에 나와 있는 것처럼 모든 항목이 선택되었는지 확인합니다. Mixed Reality Toolkit 기본 설정을 적용할지 묻는 팝업 대화 상자가 나타나면 "Apply"를 클릭합니다.
    ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 구성

1. 메뉴 모음에서 Mixed Reality Toolkit > Configure를 선택하여 Mixed Reality Toolkit을 구성합니다. Mixed Reality Toolkit을 가져온 후에 이 메뉴 항목이 보이지 않으면 Unity를 다시 시작합니다.
![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)
2. 장면은 이제 Mixed Reality Toolkit에서 가져온 몇 가지 새로운 항목 및 수정 사항을 포함합니다. File>Save As를 클릭하여 장면을 다른 이름으로 저장하고 이름을 지정합니다(예: BaseScene). 프로젝트의 Assets 폴더에 있는 "Scenes" 폴더에 저장하여 장면을 체계적으로 정리합니다.
![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>디바이스로 애플리케이션 빌드

1. 이전 섹션의 Build Settings 창을 닫은 경우 File>Build Settings로 이동하여 Build Settings 창을 다시 엽니다.
    ![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)

2. “Add Open Scenes” 단추를 클릭하여 사용하려는 장면이 "Scenes in Build" 목록에 있는지 확인합니다.

3. Build 단추를 눌러 빌드 프로세스를 시작합니다.
    ![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. 애플리케이션의 새 폴더를 만들고 이름을 지정합니다. 아래 이미지에서는 애플리케이션을 포함할 폴더가 이름 "App"을 사용하여 생성되었습니다. “Select Folder”를 클릭하여 새로 만든 폴더로 빌드를 시작합니다. 빌드가 완료된 후에 Unity에서 "Build Settings" 창을 닫을 수 있습니다. 
    ![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)

  > 참고: 빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다. "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)"가 표시되면 [Windows 10 SDK(10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)를 다시 설치해야 할 수 있습니다.
  >

5. 빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다. "MixedRealityBase.sln" 솔루션(또는 프로젝트에 다른 이름을 사용한 경우 해당 이름)을 두 번 클릭하여 Visual Studio에서 솔루션 파일을 엽니다.

  > 참고: 새로 만든 폴더(즉, 이전 단계의 명명 규칙을 따르는 경우 "App" 폴더)를 열어야 합니다. 이 폴더 밖에 비슷한 이름의 .sln 파일이 있으므로 build 폴더 내의 .sln 파일과 혼동하지 않도록 주의합니다. 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

  > 참고: Visual Studio에서 새로운 구성 요소를 설치하라는 메시지를 표시하면 ["도구 설치" 페이지](install-the-tools.md)에 지정된 모든 필수 구성 요소가 설치되어 있는지 확인합니다.

6. USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다. 이러한 단원 지침에서는 사용자가 HoloLens 2 디바이스를 사용하여 테스트를 배포한다고 가정하지만, [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 [테스트용으로 로드할 앱 패키지](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)를 만들도록 선택할 수도 있습니다.

7. 디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다. 이번에 처음으로 HoloLens 2에 배포하는 경우리면 Visual Studio에서 pin 사용하여 HoloLens 2에 연결하도록 요구할 수 있습니다. 개발자 모드를 사용하도록 설정하거나 Visual Studio와 페어링해야 하는 경우 [다음 지침](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)를 따르세요.

8. "Release" 구성과 "ARM" 아키텍처를 선택하여 HoloLens 2로 빌드하기 위해 Visual Studio를 구성합니다.
    ![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 마지막 단계는 디버그>디버깅하지 않고 시작을 선택하여 디바이스로 빌드하는 것입니다. "디버깅하지 않고 시작"을 선택하면 빌드 성공 시 애플리케이션이 디바이스에서 즉시 시작되지만, Visual Studio에 디버깅 정보가 표시되지 않습니다. 따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다. 빌드>솔루션 배포를 선택하여 디바이스로 배포할 때 애플리케이션이 자동으로 시작되지 않도록 할 수도 있습니다.
    ![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>축하합니다.

이제 첫 번째 HoloLens 2 애플리케이션을 배포했습니다. 왔다갔다 해보면 공간 메시가 HoloLens 2에서 인식된 모든 표면을 덮고 있는 것을 볼 수 있습니다. 또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다. 이러한 기능은 Mixed Reality Toolkit과 함께 기본적으로 포함되어 있는 기본적인 기능 중 일부에 불과합니다. 다음에 제공될 단원에서는 장면에 더 많은 콘텐츠와 대화형 작업을 추가하여 HoloLens 2 및 Mixed Reality Toolkit의 기능 전체를 살펴볼 수 있습니다.

>참고: [5단원](mrlearning-base-ch5.md)의 음성 명령을 사용하여 프레임 속도 카운터를 설정/해제하는 방법을 알아봅니다.

[다음 단원: 사용자 인터페이스, 직접 추적 및 혼합 현실 도구 키트 구성](mrlearning-base-ch2.md)
