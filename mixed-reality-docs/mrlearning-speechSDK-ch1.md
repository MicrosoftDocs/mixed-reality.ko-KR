---
title: Azure Speech Services 자습서 - 1. 음성 인식 및 전사 통합 및 사용
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Speech SDK를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: f376ab268e9c2869e48b325fa728672a16ee6d32
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303684"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. 음성 인식 및 전사 통합 및 사용

## <a name="overview"></a>개요


이 자습서 시리즈에서는 HoloLens 2에서 Azure Speech Services의 사용을 검색하는 Mixed Reality 애플리케이션을 만듭니다. 이 자습서 시리즈를 완료하면 디바이스의 마이크를 사용하여 음성을 텍스트로 실시간으로 전사하고, 음성을 다른 언어로 번역하고, 의도 인식 기능을 활용하여 AI를 통해 음성 명령을 이해할 수 있습니다.

## <a name="objectives"></a>목표

* Azure Speech Services를 HoloLens 2 애플리케이션과 통합하는 방법 알아보기
* 음성 인식을 사용하여 텍스트를 전사하는 방법 알아보기

## <a name="prerequisites"></a>필수 구성 요소

>[!TIP]
>[시작 자습서](mr-learning-base-01.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.

* 올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 기본 C# 프로그래밍 기능
* [개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!IMPORTANT]
> 이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.

## <a name="creating-and-preparing-the-unity-project"></a>Unity 프로젝트 만들기 및 준비

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정
2. [빌드 플랫폼 전환](mr-learning-base-02.md#configuring-the-unity-project)
3. [TextMeshPro 필수 리소스 가져오기](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Unity 프로젝트 구성](mr-learning-base-02.md#configuring-the-unity-project)
6. [장면 만들기 및 구성](mr-learning-base-02.md#creating-and-configuring-the-scene) 및 장면에 적절한 이름(예: *AzureSpeechServices*) 지정

그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경하고, 공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.

## <a name="configuring-the-speech-commands-start-behavior"></a>음성 명령 시작 동작 구성

음성 인식 및 전사에 음성 SDK를 사용하므로 음성 SDK 기능을 방해하지 않도록 MRTK 음성 명령을 구성해야 합니다. 이를 위해 음성 명령 시작 동작을 [자동 시작]에서 [수동 시작]으로 변경할 수 있습니다.

[계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 채 [검사기] 창에서 **입력** 탭을 선택하고, **DefaultHoloLens2InputSystemProfile** 및 **DefaultMixedRealitySpeechCommandsProfile**을 복제한 다음, 음성 명령 **시작 동작**을 **수동 시작**으로 변경합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> MRTK 프로필을 복제하고 구성하는 방법에 대한 자세한 내용은 [Mixed Reality Toolkit 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.

## <a name="configuring-the-capabilities"></a>기능 구성

Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 연 다음, **플레이어** >  **게시 설정** 섹션을 차례로 찾습니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다. 그런 다음, **InternetClientServer** 및 **PrivateNetworkClientServer** 기능을 사용하도록 설정합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage)(최신 버전)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.

자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a>장면 준비

이 섹션에서는 자습서 프리팹을 추가하여 장면을 준비하고, 장면을 제어하는 Lunarcom 컨트롤러(스크립트) 구성 요소를 구성합니다.

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** 폴더로 차례로 이동하고, **Lunarcom** 프리팹을 [계층 구조] 창으로 끌어 장면에 추가합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

[계층 구조] 창에서 **Lunarcom** 개체를 선택한 채로 [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 컨트롤러(스크립트)** 구성 요소를 Lunarcom 개체에 추가합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> Lunarcom 컨트롤러(스크립트) 구성 요소는 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공되었습니다.

**Lunarcom** 개체를 선택한 상태에서 이 개체를 펼쳐 자식 개체를 표시한 다음, **Terminal** 개체를 Lunarcom 컨트롤러(스크립트) 구성 요소의 **터미널** 필드로 끕니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

**Lunarcom** 개체를 선택한 상태에서 Terminal 개체를 펼쳐 자식 개체를 표시한 다음, **ConnectionLight** 개체 및 **OutputText** 개체를 각각 Lunarcom 컨트롤러(스크립트) 구성 요소의 **연결 조명** 필드 및 **출력 텍스트** 필드로 끕니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

**Lunarcom** 개체를 선택한 상태에서 Buttons 개체를 펼쳐 자식 개체를 표시한 다음, [검사기] 창에서 **단추** 목록을 펼치고, **크기**를 3으로 설정하고, **MicButton**, **SatelliteButton** 및 **RocketButton** 필드를 각각 **요소** 0, 1 및 2 필드로 끕니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Unity 프로젝트를 Azure 리소스에 연결

Azure Speech Services를 사용하려면 Azure 리소스를 만들고, Speech Service에 대한 API 키를 얻어야 합니다. [Speech Service 체험해 보기](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) 지침을 수행하고, 서비스 지역(위치라고도 함) 및 API 키(Key1 또는 Key2라고도 함)를 적어둡니다.

[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **Lunarcom 컨트롤러(스크립트)** 구성 요소의 **Speech SDK 자격 증명** 섹션을 찾아서 다음과 같이 구성합니다.

* **Speech Service API 키** 필드에서 API 키(Key1 또는 Key2)를 입력합니다.
* **Speech Service 지역** 필드에서 공백 없이 소문자를 사용하여 서비스 지역(위치)을 입력합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>음성 인식을 사용하여 음성 전사

[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 음성 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> Lunarcom 음성 인식기(스크립트) 구성 요소는 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공되었습니다.

이제 게임 모드로 들어가면 먼저 마이크 단추를 눌러 음성 인식을 테스트할 수 있습니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

그런 다음, 마이크가 컴퓨터에 있다고 가정하여 사용자가 무언가를 말하면 음성이 터미널 패널에 전사됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> 애플리케이션에서 Azure에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.

## <a name="congratulations"></a>축하합니다.

Azure에서 구동하는 음성 인식을 구현했습니다. 디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.

다음 자습서에서는 Azure 음성 인식을 사용하여 명령을 실행하는 방법에 대해 알아봅니다.

[다음 자습서: 2. 음성 인식을 사용하여 명령 실행](mrlearning-speechSDK-ch2.md)
