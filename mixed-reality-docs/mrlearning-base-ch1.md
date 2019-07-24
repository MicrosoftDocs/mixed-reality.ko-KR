---
title: MR 학습 기본 모듈 - 프로젝트 초기화 및 첫 번째 애플리케이션
description: 혼합 현실 애플리케이션에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 51cfc123f7da8d25a53eecfb730f60cf10fe7377
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387788"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. 프로젝트 및 첫 번째 응용 프로그램 초기화

이 첫 번째 단원에서는 혼합 현실 도구 키트 (MRTK)가 제공 해야 하는 기능 중 일부에 대해 알아보고, HoloLens 2에 대 한 첫 번째 응용 프로그램을 시작 하 고, 장치에 배포 합니다.

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

1. 파일 > 빌드 설정으로 이동 하 여 빌드 설정 창을 엽니다.
![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)
2. 유니버설 Windows 플랫폼를 선택 하 여 유니버설 Windows 플랫폼로 전환 합니다. 플랫폼 전환 단추를 클릭 하 여 플랫폼을 전환 합니다. HoloLens 2에서 실행 되는 응용 프로그램은 UWP (유니버설 Windows 플랫폼)와 호환 되어야 합니다.
![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)
3. 아래 이미지에 표시 된 것 처럼 빌드 창에서 플레이어 설정을 클릭 하 여 가상 현실를 사용 하도록 설정 하 고, 검사기 패널의 XR 설정에서 가상 현실 지원 됨 확인란을 사용 하도록 설정 합니다. 참고로, 검사기 패널을 표시 하기 위해 빌드 설정 창을 끌어 올 수 있습니다. 가상 현실 지원 됨 확인란은 stereoscopic 비전 (각 눈에 서로 다른 이미지 렌더링)을 참조 하기 때문에 혼합 현실 및 확대 된 현실 헤드셋에도 적용 됩니다. ![Lesson1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)
4. 동일한 검사자 패널에서 기능 섹션의 공간 인식 확인란이 게시 설정에서 사용 하도록 설정 되어 있는지 확인 합니다. 공간 인식 기능을 사용 하면 HoloLens 2와 같은 혼합 현실 장치에서 공간 매핑 메시를 시각화할 수 있습니다. 게시 설정은 XR 설정 및 기타 설정에서 검사기 패널에 있습니다.
![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)

> 참고: 이 섹션에서는 사용 하지 않는 것이 좋습니다. 사용할 수 있는 몇 가지 다른 일반적인 기능에는 음성 명령을 위한 마이크와 네트워크 연결이 필요한 서비스에 연결 하기 위한 InternetClient가 포함 됩니다.

### <a name="import-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 가져오기

1. [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) Unity 패키지를 다운로드 하 고 PC의 폴더에 저장 합니다.

2. Assets>Import>Custom Package를 클릭하여 Mixed Reality Toolkit 패키지를 가져옵니다. 1단계에서 다운로드한 Mixed Reality Toolkit 패키지를 찾은 후 열어 가져오기 프로세스를 시작합니다. 가져오기 프로세스가 진행될 때까지 몇 분 정도 기다립니다.
    ![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 다음 팝업 창에서 가져오기를 클릭 하 여 Mixed Reality Toolkit 가져오기를 시작 합니다. 이미지에 표시 된 것 처럼 모든 항목을 확인 합니다. Mixed Reality Toolkit 기본 설정을 적용 하는 팝업 대화 상자가 표시 되 면 적용을 클릭 합니다.
    ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 구성

1. 메뉴 모음에서 혼합 현실 도구 키트 > 구성을 선택 하 여 MRTK를 구성 합니다. Mixed Reality Toolkit을 가져온 후에 이 메뉴 항목이 보이지 않으면 Unity를 다시 시작합니다.
  ![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)

  > 참고: 혼합 현실 도구 키트에 대 한 프로필을 선택 하 라는 팝업 대화 상자가 표시 될 수 있습니다. 그렇다면 확인을 선택 하 고 "DefaultMixedRealityToolkitConfigurationProfile" 라는 프로필을 선택 합니다.

2. 장면에는 몇 가지 새로운 항목과 MRTK의 수정 내용이 포함 됩니다. 파일 > 다른 이름으로 저장을 클릭 하 여 장면을 다른 이름으로 저장 하 고 BaseScene 등의 이름을 지정 합니다. 프로젝트의 자산 폴더에 있는 장면 폴더에 저장 하 여 장면을 구성 된 상태로 유지 합니다.
  ![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>디바이스로 애플리케이션 빌드

1. 이전 섹션에서 빌드 설정 창을 닫은 경우 파일 > 빌드 설정으로 이동 하 여 빌드 설정 창을 다시 엽니다.
    ![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)

2. 열려 있는 장면 추가 단추를 클릭 하 여 시도 하려는 장면이 빌드 목록의 장면에 있는지 확인 합니다.

3. Build 단추를 눌러 빌드 프로세스를 시작합니다.
    ![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. 애플리케이션의 새 폴더를 만들고 이름을 지정합니다. 아래 이미지에서 응용 프로그램을 포함 하기 위해 이름이 앱 인 폴더를 만들었습니다. 폴더 선택을 클릭 하 여 새로 만든 폴더로 빌드를 시작 합니다. 빌드가 완료 된 후 Unity에서 빌드 설정 창을 닫을 수 있습니다. 
    ![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)

  > 참고: 빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다. 오류가 표시 되는 경우 "오류: CS0246 = "XX" 형식 또는 네임 스페이스 이름을 찾을 수 없습니다. using 지시문 또는 어셈블리 참조가 있는지 확인 하십시오. 그렇다면 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 를 설치 해야 할 수 있습니다.
  >

5. 빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다. MixedRealityBase 솔루션을 두 번 클릭 하거나 프로젝트에 대체 이름을 사용 하는 경우 Visual Studio에서 솔루션 파일을 엽니다.

  > 참고: 새로 만든 폴더 (이전 단계에서 명명 규칙을 준수 하는 경우에는 앱 폴더)를 열어야 합니다 .이 폴더에는 빌드 폴더 내에 있는 .sln 파일과 혼동 하지 않는 유사 하 게 이름이 지정 된 .sln 파일도 있습니다. 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

  > 참고: Visual Studio에서 새로운 구성 요소를 설치하라는 메시지를 표시하면 ["도구 설치" 페이지](install-the-tools.md)에 지정된 모든 필수 구성 요소가 설치되어 있는지 확인합니다.

6. HoloLens 2를 PC에 연결 합니다. 이러한 지침에서는 HoloLens 2 장치를 사용 하 여 테스트를 배포할 것으로 가정 하지만 [hololens 2 에뮬레이터](using-the-hololens-emulator.md) 에 배포 하거나 [테스트용 로드에 대 한 앱 패키지](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>) 를 만들도록 선택할 수도 있습니다.

7. 디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다. HoloLens 2에 처음으로 배포 하는 경우 Visual Studio는 HoloLens 2를 PIN과 페어링 하도록 요청할 수 있습니다. 개발자 모드를 사용하도록 설정하거나 Visual Studio와 페어링해야 하는 경우 [다음 지침](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)를 따르세요.

8. 릴리스 구성 및 ARM 아키텍처를 선택 하 여 HoloLens 2를 빌드하기 위해 Visual Studio를 구성 합니다.
    ![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 마지막 단계는 디버그 > 디버깅 하지 않고 시작을 선택 하 여 장치를 빌드하는 것입니다. 디버깅 하지 않고 시작을 선택 하면 빌드에 성공 하면 응용 프로그램이 장치에서 즉시 시작 되 고 Visual Studio에는 디버깅 정보가 나타나지 않습니다. 따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다. 또한 응용 프로그램을 자동으로 시작 하지 않고도 빌드 > 솔루션 배포를 선택 하 여 장치에 배포할 수 있습니다.
    ![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>축하합니다.

이제 첫 번째 HoloLens 2 응용 프로그램을 배포 했습니다. 연습을 진행 하면서 HoloLens 2에서 인식 하는 모든 표면을 포함 하는 공간 메쉬가 표시 되어야 합니다. 또한 손으로 직접 추적 하 고 프레임 속도 카운터를 통해 응용 프로그램 성능에 대 한 경험을 유지 하기 위한 표시기가 표시 되어야 합니다. 이러한 기능은 Mixed Reality Toolkit과 함께 기본적으로 포함되어 있는 기본적인 기능 중 일부에 불과합니다. 이 단원에서는 HoloLens 2 및 Mixed Reality Toolkit의 기능을 완벽 하 게 탐색할 수 있도록 장면에 더 많은 콘텐츠와 대화형 작업을 추가 하기 시작 합니다.

>참고: [5단원](mrlearning-base-ch5.md)의 음성 명령을 사용하여 프레임 속도 카운터를 설정/해제하는 방법을 알아봅니다.

[다음 단원: 사용자 인터페이스, 직접 추적 및 혼합 현실 도구 키트 구성](mrlearning-base-ch2.md)
