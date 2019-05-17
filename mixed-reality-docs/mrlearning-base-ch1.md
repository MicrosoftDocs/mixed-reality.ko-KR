---
title: MR 학습 자료 모듈-프로젝트 초기화 및 첫 번째 응용 프로그램
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65814008"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR 학습 자료 모듈-프로젝트 초기화 및 첫 번째 응용 프로그램

이 첫 번째 단원에서는 혼합 현실 도구 키트를 제공, HoloLens 2에 대 한 첫 번째 응용 프로그램을 시작, 장치에 배포 하는 기능 중 일부를 배웁니다.

## <a name="objectives"></a>목표

* HoloLens 개발에 대 한 Unity를 최적화 합니다.
* 자산을 가져오고 장면 설정 합니다.
* 공간 메시, 직접 메시와 프레임 속도 카운터를 시각화 합니다.

## <a name="instructions"></a>지침

### <a name="create-new-unity-project"></a>새 Unity 프로젝트 만들기

1. Unity를 시작 합니다.
2. **New**를 선택합니다.
![1 단원 Chapter1 2 단계](images/Lesson1Chapter1Step2.JPG)
3. 프로젝트 이름 (예: 입력 "MixedRealityBase").
![1 단원 Chapter1 3 단계](images/Lesson1Chapter1Step3.JPG)
4. 프로젝트를 저장할 위치를 입력 합니다.
![1 단원 Chapter1 4 단계](images/Lesson1Chapter1Step4.JPG)
5. 프로젝트 설정 되어 있는지 확인 **3D**합니다.
![1 단원 Chapter1 5 단계](images/Lesson1Chapter1Step5.JPG)
6. 클릭 **프로젝트를 만들**합니다.
![1 단원 Chapter1 6 단계](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality에 대 한 Unity 프로젝트를 구성 합니다.

1. 파일로 이동 하 여 빌드 설정 창을 열고 > 빌드 설정 합니다.
![1 단원 Chapter4 1 단계](images/Lesson1Chapter4Step1.JPG)
2. "유니버설 Windows 플랫폼"을 선택 하 여 "유니버설 Windows 플랫폼"으로 전환 하 고 플랫폼 전환 "플랫폼 전환" 단추를 클릭 합니다. HoloLens 2에서 실행 중인 앱 수 유니버설 Windows 플랫폼 (UWP) 해야 합니다.
![1 단원 Chapter4 2 단계](images/Lesson1Chapter4Step2.JPG)
3. 가상 현실 빌드 창에서 플레이어 설정을 클릭 하 여 사용 하도록 설정 하 고 검사기 창에서 xr 하이 설정에서 "가상 현실 지원" 확인란을 아래 그림과에서 같이 설정 합니다. [관리자] 패널을 확인 하기 위해 "빌드 설정" 창으로 끌 수 해야 할 수 있습니다 note 하십시오. 혼합 현실에도 적용 됩니다 "가상 현실 지원" 확인란을 선택 / AR 헤드셋 stereoscopic vision (렌더링 다른 이미지를 각 눈.)을 사용 하려면 참조 하기 때문에 ![1 단원 Chapter4 3 단계](images/Lesson1Chapter4Step3.JPG)
4. 동일한 검사기 창에서 게시 설정에서 기능 섹션에서 "공간 인식" 확인란 설정 되어 있는지 확인 합니다. 공간 인식 하면 혼합된 현실 장치 HoloLens 2 예: 공간 매핑 메시를 시각화할 수 있습니다. 위의 "xr 하이 설정을" 및 "기타 설정입니다." [관리자] 패널에 있는 게시 설정
![1 단원 Chapter4 4 단계](images/Lesson1Chapter4Step4.JPG)

> 참고: 사용 하도록 설정 하려는 경우 몇 가지 다른 일반적인 기능 (예: 음성 명령) 마이크 등 InternetClient (에 대 한 네트워크 연결을 요구 하는 서비스에 연결)이이 섹션에서 사용 되지 않지만

### <a name="import-the-mixed-reality-toolkit"></a>혼합된 현실 도구 키트 가져오기

1. 다운로드 합니다 [혼합 현실 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) unity 패키지를 PC의 폴더에 저장 합니다.

2. 자산을 클릭 하 여 혼합 현실 Toolkit 패키지 > 가져오기 > 사용자 지정 패키지 있습니다. 1 단계에서에서 다운로드 한 혼합 현실 Toolkit 패키지를 검색 하 여 가져오기 프로세스를 시작 하려면 엽니다. 가져오기 프로세스의 경우 몇 분을 정도 걸립니다.
    ![1 단원 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![1 단원 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 다음 팝업 창에서 혼합 현실 Toolkit 가져오기를 시작 하려면 "가져오기"를 클릭 합니다. 이미지에 나와 있는 것 처럼 모든 항목을 확인을 확인 합니다. 혼합 현실 Toolkit 기본 설정을 적용 하는 팝업 대화 상자가 나타나면 "적용 합니다."을 클릭 합니다.
    ![1 단원 Chapter2 3 단계의](images/Lesson1Chapter2Step3.JPG) ![1 단원 Chapter2 3 단계](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>혼합된 현실 도구 키트를 구성 합니다.

1. 혼합된 현실 Toolkit 표시줄 메뉴에서 선택 하 여 혼합 도구 키트 구성 > 구성 합니다. 이 메뉴 항목이 보이지 않으면 혼합된 현실 도구 키트를 가져온 후 Unity를 다시 시작 하십시오.
![1 단원 Chapter3 1 단계](images/Lesson1Chapter3Step1.JPG)
2. 장면은 이제 몇 가지 새로운 항목 및 수정에 혼합 현실 도구 키트에서 있습니다. 파일을 클릭 하 여 다른 이름으로 장면 저장 > 다른 이름으로 저장 하 고 이름을 장면 BaseScene 예를 들어 있습니다. 프로젝트의 자산 폴더에 있는 "백그라운드 에서" 폴더에 저장 하 여 구성 된 장면을 유지 합니다.
![1 단원 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![1 단원 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>장치에 응용 프로그램 빌드

1. 이전 섹션에서 빌드 설정 창을 닫은 경우 파일로 이동 하 여 빌드 설정 창을 다시 열고 > 빌드 설정 합니다.
    ![1 단원 Chapter5 1 단계](images/Lesson1Chapter5Step1.JPG)

2. 확인 하려는 장면 "Scenes in Build" 목록에서 "Open 장면 추가" 단추를 클릭 하 여 합니다.

3. 빌드 프로세스를 시작 하려면 빌드 단추를 누릅니다.
    ![1 단원 Chapter5 3 단계](images/Lesson1Chapter5Step3.JPG)

4. 페이지를 만들고 응용 프로그램에 대 한 새 폴더 이름을 지정 합니다. 폴더 이름 사용 하 여 아래 이미지에서 "App" 응용 프로그램을 포함 하기 위해 만들어졌습니다. 새로 만든된 폴더에 빌드를 시작 하려면 "폴더 선택"을 클릭 합니다. 빌드가 완료 된 후에 Unity에서 "빌드 설정" 창을 닫을 수 있습니다. 
    ![1 단원 Chapter5 4 단계](images/Lesson1Chapter5Step4.JPG)

  > 참고: 빌드에 실패 하는 경우 빌드 다시 시도 또는 Unity를 다시 시작 하 고 다시 작성 합니다. 와 같은 오류를 표시 하는 경우 "오류: CS0246 = "XX"를 찾을 수 없는 형식 또는 네임 스페이스 이름 (사용 하는 누락 된 지시문 또는 어셈블리 참조가?) "를 설치 해야 할 수 있습니다 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. 빌드가 완료 된 후 새로 빌드된 응용 프로그램 파일이 들어 새로 만든된 폴더를 엽니다. 두 번 클릭 "MixedRealityBase.sln" 솔루션 (또는 해당 이름, 프로젝트에 대 한 대체 이름을 사용 하는 경우) Visual Studio에서 솔루션 파일을 엽니다.

  > 참고: 새로 만든된 폴더 (즉, "앱" 폴더를 이전 단계에서 명명 규칙을 따르는 경우)를 열어야 외부 빌드 폴더 내에서.sln 파일와 혼동 해서는 안 됩니다 해당 폴더에서 이름이 비슷한.sln 파일으로 합니다. 

![1 단원 Chapter5 5 단계](images/Lesson1Chapter5Step5.JPG)

  > 참고: Visual Studio에서는 새로운 구성 요소를 설치 하도록 요구 하세요 잠시으로 모든 필수 구성 요소가 설치 되어 있는지 확인 하는 경우 지정할 ["Tools 설치" 페이지](install-the-tools.md)

6. USB 케이블을 사용 하 여 PC에 HoloLens 2를 꽂습니다. 이러한 단원 지침 HoloLens 2 장치를 사용 하 여 테스트를 배포할 수 있다고 가정에서 수도 있습니다를 배포 하는 [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md) 를 만들도록 선택할는 [테스트용 로드 앱 패키지](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 장치를 빌드하기 전에 장치가 개발자 모드에서 인지를 확인 합니다. 처음 HoloLens 2 배포 인 경우 Visual Studio pin 사용 하 여 HoloLens 2에 연결 하도록 요청할 수 있습니다. 따르세요 [이러한 지침](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) 개발자 모드를 사용 하도록 설정 하거나 Visual Studio를 쌍으로 연결 해야 하는 경우.

8. "릴리스" 구성과 "ARM" 아키텍처를 선택 하 여 HoloLens 2에 구성에 대 한 Visual Studio를 구성 합니다.
    ![1 단원 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 마지막 단계는 디버그를 선택 하 여 장치를 빌드할 수 > 디버깅 하지 않고 시작 합니다. "디버깅 하지 않고 시작"을 선택 하면 응용 프로그램을 즉시 Visual Studio에 표시 되는 디버깅 정보 없이 성공적으로 빌드된 시 장치의 시작 합니다. 즉, 응용 프로그램을 중지 하지 않고 응용 프로그램에 HoloLens 2에서 실행 되는 동안 USB 케이블을 끊을 수 있습니다. 빌드를 선택할 수 있습니다 > 응용 프로그램을 자동으로 시작 하지 않고 장치에 배포할 솔루션을 배포 합니다.
    ![1 단원 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>축 하.

이제 이제 배포한 첫 번째 HoloLens 2 응용 프로그램입니다. 주위를 탐색할 때 공간 메시 HoloLens 2에서 인식 된 있어야 하는 모든 화면 설명 표시 되어야 합니다. 또한 실습 및 직접 추적에 대 한 손가락 및 앱 성능을 주시 하는 것에 대 한 프레임 속도 카운터에 표시기를 표시 됩니다. 이들은 기본적으로 혼합 현실 도구 키트를 사용 하 여 포함 된 기본 부분 일부에 불과합니다. 단원에서는 HoloLens 2 및 혼합 현실 Toolkit의 기능을 완벽 하 게 탐색할 수 있도록 장면에 추가 콘텐츠 및 대화형 작업 추가 시작 합니다.

>참고: 에 음성 명령을 사용 하 여 프레임 속도 카운터를 전환 하는 방법을 다루는 것 [Lesson 5](mrlearning-base-ch5.md)

[다음 단원: 사용자 인터페이스를 직접 추적 하 고 혼합 현실 도구 키트 구성](mrlearning-base-ch2.md)
