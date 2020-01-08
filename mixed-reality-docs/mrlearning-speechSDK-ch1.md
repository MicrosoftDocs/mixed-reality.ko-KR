---
title: Azure Speech Services 자습서-1. 음성 인식 및 기록을 통합 하 고 사용
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 05728cf090b2e998e92980816943a2c3bef18dfb
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334293"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. 음성 인식 및 기록을 통합 하 고 사용

## <a name="overview"></a>개요

이 자습서에서는 HoloLens 2와 함께 Azure Cognitive Services Speech SDK를 사용 하는 방법을 탐색 하는 혼합 현실 응용 프로그램을 만듭니다. 이 자습서 시리즈를 완료 한 후에는 장치의 마이크를 사용 하 여 음성 텍스트를 실시간으로 높여줄, 음성을 다른 언어로 번역 하 고, 음성 SDK의 의도 기능을 활용 하 여 인공 지능을 사용 하는 음성 명령을 이해할 수 있습니다. intelligence.

## <a name="objectives"></a>목표

* Azure Speech SDK를 HoloLens 2 응용 프로그램에 통합 하는 방법을 알아봅니다.
* 음성 명령을 사용 하는 방법 알아보기
* 음성 텍스트 기능 사용 방법 알아보기

## <a name="prerequisites"></a>전제 조건

>[!TIP]
>초보자를 위한 [자습서](mrlearning-base.md) 시리즈를 아직 완료 하지 않은 경우 해당 자습서를 먼저 완료 하는 것이 좋습니다.

* 올바른 [도구로](install-the-tools.md) 구성 된 WINDOWS 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 C# 기본 프로그래밍 기능
* [개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode) HoloLens 2 장치

>[!IMPORTANT]
>이 자습서 시리즈에는 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> 이 필요 하며 권장 버전은 unity 2019.1.14입니다. 이렇게 하면 위에 연결 된 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항이 나 권장 사항이 대체 됩니다.

## <a name="getting-started"></a>시작

1. Unity를 시작 하 고 새 프로젝트를 만듭니다. 프로젝트 이름 Speech SDK 학습 모듈을 입력 합니다. 프로젝트를 저장할 위치를 선택 합니다. 프로젝트 만들기를 클릭 합니다.

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    >위의 이미지에 표시 된 것 처럼 템플릿이 3D로 설정 되었는지 확인 합니다.

2. [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [기초 패키지 버전 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)을 다운로드하여 PC의 폴더에 저장합니다. 패키지를 Unity 프로젝트로 가져옵니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 초보자를 위한 [자습서-2 단원을 참조 하세요. 프로젝트 및 첫 번째 응용 프로그램 초기화](mrlearning-base-ch1.md)

3. Unity 자산 패키지용 Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage) 를 다운로드 하 여 가져옵니다. 자산을 클릭 하 고 패키지 가져오기를 선택한 다음 사용자 지정 패키지를 선택 하 여 음성 SDK 패키지를 가져옵니다. 이전에 다운로드 한 음성 SDK 패키지를 찾아서 열어서 가져오기 프로세스를 시작 합니다.

    ![mrlearning-speech-ch1-1-step3a](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-speech-ch1-1-step3b](images/mrlearning-speech-ch1-1-step3b.png)

4. 다음 팝업 창에서 가져오기를 클릭 하 여 음성 SDK 패키지 가져오기를 시작 합니다. 아래 이미지에 표시 된 것 처럼 모든 항목이 선택 되어 있는지 확인 합니다.

    ![mrlearning-speech-ch1-1-step4](images/mrlearning-speech-ch1-1-step4.png)

5. [이 링크](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)를 클릭 하 여 Lunarcom 패키지 라고도 하는 Speech SDK 모듈 자산 팩을 다운로드 합니다. Lunarcom asset 패키지는 Azure의 Speech SDK의 실용적인 사용을 보여 주기 위해이 단원 시리즈를 위해 개발 된 자산 및 스크립트 모음입니다. 궁극적으로 시작 자습서에서 개발한 음력 모듈 어셈블리 환경과 관련 된 음성 명령 터미널입니다 [-단원 7. 음력 모듈 샘플 응용 프로그램을 만듭니다](mrlearning-base-ch6.md).

6. Mixed Reality Toolkit 및 Speech SDK를 가져오는 것과 비슷한 단계를 수행 하 여 Lunarcom asset 패키지를 Unity 프로젝트로 가져옵니다.

7. MRTK (Mixed Reality Toolkit)를 구성 합니다.

    이렇게 하려면 창의 위쪽에 있는 혼합 현실 도구 키트 패널을 클릭 한 다음 장면에 추가 및 구성을 선택 합니다.

    ![mrlearning-speech-ch1-1-step7a](images/mrlearning-speech-ch1-1-step7a.png)

    표시 되는 팝업에서 DefaultHoloLens2ConfigurationProfile을 선택 하 여 Mixed Reality Toolkit의 활성 프로필로 설정 합니다.

    ![mrlearning-speech-ch1-1-step7b](images/mrlearning-speech-ch1-1-step7b.png)

8. 이제 장면에 MRTK의 여러 새 항목이 있습니다. "파일"을 클릭 하 고 [다른 이름으로 저장]을 클릭 한 후 장면 이름을 SpeechScene로 설정 하 여 장면을 다른 이름으로 저장 합니다.

    >[!NOTE]
    >프로젝트에 MRTK를 추가 하 고 재생 모드로 들어가지 않는 경우 장면에서 Play를 누르면 Unity를 다시 시작 해야 할 수 있습니다.

9. 장면 계층에서 MixedRealityToolkit 개체를 선택한 상태에서 검사기 패널에서 복사 & 사용자 지정을 클릭 하 여 프로필 복제 팝업을 엽니다. 프로필 복제 팝업에서 사용자 지정 프로필에 적합 한 이름 (예: Custom HoloLens2ConfigurationProfile)을 입력 합니다. 복제를 클릭 하 여 사용자 지정 구성 프로필을 만들고 활성 프로필로 설정 합니다.

    ![mrlearning-speech-ch1-1-step9](images/mrlearning-speech-ch1-1-step9.png)

10. 또한 검사기 패널 (계층에서 MixedRealityToolkit 개체가 선택 된 상태)에서 진단 시스템 사용 오른쪽에 있는 상자를 선택 취소 하 여 진단 시스템을 사용 하지 않도록 설정 합니다.

    ![mrlearning-speech-ch1-1-step10](images/mrlearning-speech-ch1-1-step10.png)

11. 이 자습서에서는 음성 인식 및 기록을 위해 입력 음성 명령을 사용 합니다. 입력 프로필을 복제 하 여 음성 설정을 변경 하겠습니다.

    장면 계층 구조에서 MixedRealityToolkit 개체를 선택한 상태에서 검사기 패널의 작은 복제 단추를 클릭 하 여 프로필 복제 팝업을 엽니다. 복제 프로필 팝업에서 사용자 지정 프로필에 대 한 적절 한 이름 (예: Custom HoloLens2InputSystemProfile)을 입력 한 다음 복제를 클릭 하 여 사용자 지정 입력 시스템 프로필을 만들고 활성 프로필로 설정 합니다.

    ![mrlearning-speech-ch1-1-step11](images/mrlearning-speech-ch1-1-step11.png)

12. 입력 프로필이 복제 되 면 음성 섹션을 확장 하 고 이전 단계와 동일한 프로세스를 수행 하 여 음성 명령 프로필을 복제 합니다.

    ![mrlearning-speech-ch1-1-step12](images/mrlearning-speech-ch1-1-step12.png)

13. 음성 섹션에서 일반 설정으로 이동 하 고 시작 동작을 수동 시작으로 변경 합니다.

    ![mrlearning-speech-ch1-1-step13](images/mrlearning-speech-ch1-1-step13.png)

14. 프로젝트 패널에서 Lunarcom 폴더를 확장 하 고 Lunarcom_Base prefab를 장면 계층 구조에 끌어 놓습니다.

    ![mrlearning-speech-ch1-1-step14](images/mrlearning-speech-ch1-1-step14.png)

15. 계층에서 Lunarcom_Base 개체를 선택 하 고 위치가 x = 0, y = 0 및 z = 0으로 설정 되어 있고 x = 0, y = 0 및 z = 0으로 설정 된 회전을 설정 했는지 확인 합니다. 크기를 읽기 x = 0.008, y = 0.008 및 z = 0.01로 설정 합니다.

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. 구성 요소 추가를 클릭 하 고 Lunarcom Controller를 검색 하 여 선택 합니다. 이 스크립트는 6 단계에서 가져온 Lunarcom asset pack에 포함 되어 있습니다.

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. 응용 프로그램을 Azure Cognitive Services에 연결 하려면 음성 서비스에 대 한 구독 키 (API 키 라고도 함)를 입력 해야 합니다. [여기](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) 의 지침에 따라 무료 구독 키를 가져옵니다. 구독 키를 가져온 후 아래 이미지에 나와 있는 것 처럼 검사기 패널에서 LunarcomController 구성 요소의 Speech Service API 키 필드에 입력 합니다.

18. 구독 키에 등록할 때 선택한 지역을 검사기 패널의 LunarcomController 구성 요소에 있는 음성 서비스 지역 필드에 입력 합니다. 예를 들어 "westus"에서 지역 서 부 형식의 경우입니다.

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. 계층에서 왼쪽에 있는 화살표를 클릭 하 여 Lunarcom_Base 개체를 확장 합니다. 그런 다음 아래 그림에 표시 된 것 처럼 자식 개체 "터미널"에 대해 동일한 작업을 수행 합니다.

20. Lunarcom_Base가 선택 된 상태에서 아래 이미지에 표시 된 것 처럼 계층의 Lunarcom 텍스트를 클릭 하 고 검사기 패널의 LunarcomController 구성 요소에 있는 출력 텍스트 슬롯으로 끕니다.

21. 터미널 개체와 연결 라이트 컨트롤러 슬롯에 대 한 연결 조명 개체를 사용 하 여 동일한 작업을 수행 합니다.

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. 검사기 패널에서 LunarcomController 스크립트의 Lunarcom Buttons 섹션 옆에 있는 화살표를 클릭 하 고 크기를 3으로 변경 합니다. Enter 키를 누르거나를 반환 합니다. 이렇게 하면 세 개의 새 요소 필드가 표시 됩니다.

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. 계층 구조에서 옆에 있는 화살표를 클릭 하 고 위와 동일한 프로세스를 사용 하 여 Lunarcom 단추를 확장 하 고, gameobject의 LunarcomController 구성 요소에서 Mic, 위성 및 로켓을 각각 0, 1 및 2 참조 요소로 끌어 옵니다. 검사기 패널.

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. 계층에서 Lunarcom_Base "개체를 선택 합니다. 검사기 패널에서 구성 요소 추가를 클릭 하 고 Lunarcom Speech 인식기를 검색 하 여 선택 합니다. 동일한 단계를 반복 하 여 Lunarcom Wake Word 인식기를 추가 합니다.

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. 절전 모드 해제 단어 슬롯에서 터미널 활성화를 입력 합니다. Word 슬롯 해제에서 터미널 해제를 입력 합니다.

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="build-your-application-to-your-device"></a>디바이스로 애플리케이션 빌드

1. 파일 > 빌드 설정으로 이동 하 여 빌드 설정 창을 다시 엽니다.

    ![images/mrlearning-ch1-1 단계](images/mrlearning-speach-ch1-2-step1.jpg)

2. “Add Open Scenes” 단추를 클릭하여 사용하려는 장면이 "Scenes in Build" 목록에 있는지 확인합니다.

3. 플레이어 설정 단추를 누르고 게시 설정으로 이동 합니다. 기능 아래에서 인터넷, 인터넷 클라이언트 서버, 개인 네트워크 클라이언트 서버, 마이크 및 공간 인식을 사용 하도록 설정 합니다.

4. 동일한 플레이어 설정에서 XR 설정으로 이동 하 고에서 지원 되는 가상 현실를 선택 합니다.

5. Build 단추를 눌러 빌드 프로세스를 시작합니다.

    ![mrlearning-ch1-2-5 단계](images/mrlearning-speach-ch1-2-step5.jpg)

6. 애플리케이션의 새 폴더를 만들고 이름을 지정합니다. 아래 이미지에서는 애플리케이션을 포함할 폴더가 이름 "App"을 사용하여 생성되었습니다. “Select Folder”를 클릭하여 새로 만든 폴더로 빌드를 시작합니다. 빌드가 완료된 후에 Unity에서 "Build Settings" 창을 닫을 수 있습니다.

    ![mrlearning-ch1-2-6 단계](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    >빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다. "Error: CS0246 = using 지시문 또는 어셈블리 참조가 있는지 확인 하십시오."와 같은 오류가 표시 되는 경우 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) 를 설치 해야 할 수 있습니다.

7. 빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다. ".Sln" 솔루션 파일을 두 번 클릭 하 여 Visual Studio에서 솔루션 파일을 엽니다.

    >[!NOTE]
    >빌드 폴더 내에 있는 .sln 파일과는 다른 폴더 외부에 유사한 이름의 .sln 파일이 있으므로 새로 만든 폴더 (즉, 이전 단계의 명명 규칙에 따라 "App" 폴더)를 열어야 합니다. 

    ![mrlearning-ch1-2-step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    >Visual Studio에서 새 구성 요소를 설치 하도록 요청 하는 경우 ["도구 설치" 페이지](install-the-tools.md) 에 지정 된 대로 모든 필수 구성 요소를 설치 해야 합니다.

8. USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다. 이러한 단원 지침에서는 사용자가 HoloLens 2 디바이스를 사용하여 테스트를 배포한다고 가정하지만, [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 [테스트용으로 로드할 앱 패키지](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)를 만들도록 선택할 수도 있습니다.

9. 디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다. 이번에 처음으로 HoloLens 2에 배포하는 경우리면 Visual Studio에서 pin 사용하여 HoloLens 2에 연결하도록 요구할 수 있습니다. 개발자 모드를 사용하도록 설정하거나 Visual Studio와 페어링해야 하는 경우 [다음 지침](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)를 따르세요.

10. "Release" 구성과 "ARM" 아키텍처를 선택하여 HoloLens 2로 빌드하기 위해 Visual Studio를 구성합니다.

    ![mrlearning-ch1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. 마지막 단계는 디버그>디버깅하지 않고 시작을 선택하여 디바이스로 빌드하는 것입니다. "디버깅하지 않고 시작"을 선택하면 빌드 성공 시 애플리케이션이 디바이스에서 즉시 시작되지만, Visual Studio에 디버깅 정보가 표시되지 않습니다. 따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다. 빌드>솔루션 배포를 선택하여 디바이스로 배포할 때 애플리케이션이 자동으로 시작되지 않도록 할 수도 있습니다.

    ![mrlearning-ch1-2-step11. P](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a>축하합니다.

Azure에서 제공 하는 응용 프로그램에서 음성 인식을 설정 했습니다. 응용 프로그램을 실행 하 여 모든 기능과 기능이 제대로 작동 하는지 확인 합니다. 22 단계에서 입력 한 절전 모드 해제 단어를 말한 후 터미널을 활성화 합니다. 마이크 단추를 선택 하 여 음성 인식을 시작 합니다. 말하기를 시작 합니다. 말할 때 터미널에 transcribed 단어가 표시 됩니다. 음성 인식을 중지 하려면 마이크 단추를 두 번 누릅니다. 터미널을 해제 하 여 Lunarcom 터미널을 숨깁니다. 다음 단원에서는 장치 지원 음성 인식을 사용 하도록 동적으로 전환 하는 방법에 대해 설명 합니다 .이는 HoloLens 2가 오프 라인 상태 이기 때문에 Azure의 speech SDK를 사용할 수 없는 경우입니다.

[다음 자습서: 2. 로컬 음성-텍스트 번역을 위한 오프 라인 모드 추가](mrlearning-speechSDK-ch2.md)
