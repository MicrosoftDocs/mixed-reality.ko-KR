---
title: Azure 공간 앵커 자습서-1. Azure 공간 앵커 시작
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 95e5a5bfbf289731512554f2e4e73feeae96f432
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68978002"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure 공간 앵커 시작

HoloLens 2 자습서의 두 번째 모듈을 시작 합니다. 시작 하기 전에 모든 [필수 구성 요소](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 를 완료 해야 합니다. 첫 번째 [기본 모듈](mrlearning-base.md) 을 아직 완료 하지 않은 경우 해당 모듈을 먼저 완료 하는 것이 좋습니다. 새 Unity 프로젝트에서 시작 하는 경우 [기본 모듈](mrlearning-base.md)의 새 프로젝트 만들기 단계를 따릅니다. 

## <a name="objectives"></a>목표

* HoloLens 2를 사용 하 여 Azure 공간 앵커로 개발 하는 기본 사항 알아보기

* 공간 앵커 만들기, 업로드 및 다운로드

## <a name="instructions"></a>지침

### <a name="downloading-and-importing-assets"></a>자산 다운로드 및 가져오기
시작 하기 전에 다음 자산을 다운로드 하 여 가져오세요.

[Azure 공간 앵커 v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[MR 기본 모듈 자산 팩 v 1.2](https://github.com/microsoft/MixedRealityLearning/releases/download/1.2/BaseModuleAssets-1.2.unitypackage)

[GLOBAL.ASA 모듈 Asset Pack v1.0](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.3)

[Mixed Reality Toolkit 2.0.0 RC1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)

> 참고: Azure 공간 앵커를 가져오는 방법에 대 한 구체적인 지침은 5 단계를 참조 하 고, MR 기본 모듈 자산 팩의 특정 지침에 대해서는 6 단계를 참조 하 고, Mixed Reality 도구 키트 (MRKT)에 대 한 특정 지침은 3 ~ 4 단계를 참조 하세요.

1. 프로젝트에 새 장면을 만듭니다. 장면 폴더를 마우스 오른쪽 단추로 클릭 하 고 만들기, 장면을 차례로 클릭 합니다. 새 장면 이름을 ASALearningmodule로 합니다.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. ASALearningmodule를 두 번 클릭 하 여 미리 정의 된 항목이 새 장면에 표시 되는지 확인 합니다. 
3. 혼합 현실 개발을 위한 장면을 구성 합니다. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 참고: 혼합 된 현실 도구 키트에 대 한 파일을 선택 해야 한다는 팝업이 표시 됩니다. 확인을 클릭 하면 4 단계로 이동 합니다.

4. MRTK에 대 한 파일을 선택 하는 경우 DefaultMixedRealityToolkitConfigurationProfile를 선택 합니다.

> 참고: 사용자 고유의 구성 프로필이 있는 경우이를 대신 사용 하세요.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

이제는 혼합 현실에 대해 장면이 구성 됩니다. 장면을 저장 해야 합니다 (ctrl/command + S를 사용 하 여이 작업을 수행 하거나 파일을 클릭 한 다음 저장을 클릭). 

5. [Azure 공간 앵커](https://github.com/azure/azure-spatial-anchors-samples/releases)를 가져옵니다. 공간 앵커를 사용 하려면이 자산을 가져와야 합니다. 위의 링크를 클릭 하 고 AzureSpatialAnchors. unitypackage를 마우스 오른쪽 단추로 클릭 합니다. 다른 이름으로 대상 저장을 클릭 하 고 컴퓨터에 저장 합니다. 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

저장 된 후 Unity로 돌아가서 자산을 클릭 하 고 패키지 가져오기로 이동 합니다. 그런 다음 사용자 지정 패키지 ...를 클릭 합니다. 컴퓨터 파일이 열립니다. 이렇게 하면 Azure 공간 앵커 패키지를 저장 한 위치를 찾아서 선택 합니다. 그런 다음 열기를 클릭 합니다.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

도구 및 설정 목록을 제공 하 고 가져올 항목을 요청 하는 팝업이 나타납니다. 사용할 수 있는 옵션을 ***모두*** 선택 하 고 가져오기를 클릭 합니다.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> 참고: 잠시 기다려 주세요. 가져오는 데 몇 분 정도 걸릴 수 있습니다. 

6. [MR 기본 모듈 자산 팩](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) 다음을 가져옵니다. 5 단계와 마찬가지로 위의 링크를 클릭 합니다. 그런 다음 unitypackage를 마우스 오른쪽 단추로 클릭 하 고 다른 이름으로 대상 저장을 클릭 하 여 컴퓨터에 저장 합니다.

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> 팁:  이러한 모든 자산을 찾고 쉽게 액세스할 수 있도록 동일한 폴더에 저장 합니다. 모든 것을 잘 구성 된 상태로 유지 합니다.

5 단계와 마찬가지로 Unity로 돌아가서 자산을 클릭 하 고 가져오기 패키지를 마우스로 가리킵니다. 사용자 지정 패키지 ...를 클릭 합니다. 컴퓨터 파일이 다시 표시 됩니다. 기본 모듈 자산 팩을 저장 한 위치로 이동 합니다. 선택 합니다. 열기를 클릭합니다.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> 참고: 이 모듈의 뒷부분에 더 많은 자산이 필요할 수 있습니다. 이 시점에서 언급 된 자산을 가져오려면 다음 단계를 수행 합니다. 

7. 이전 패키지를 가져오는 것과 동일한 방법을 사용 하 여 [global.asa 모듈 팩](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.3) 을 가져옵니다.

### <a name="configuring-your-scene"></a>장면 구성

이 섹션에서는 prefabs 및 스크립트를 장면에 추가 하 여 로컬 앵커와 Azure 공간 앵커가 응용 프로그램에서 작동 하는 방식에 대 한 기본 사항을 보여 주는 일련의 단추를 만듭니다.

8. 프로젝트 탭의 자산 폴더 아래에서 ASAmoduleAssets을 클릭 합니다. 선택 하면 두 개의 prefabs 표시 됩니다. ButtonParent 및 ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. 두 prefabs를 장면으로 끌어 놓습니다. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

참고: HoloLens에서 디버그 로그를 확인 하려는 경우 DebugWindow prefab을 ASAModuleAssets 폴더에서 장면으로 끌어서 놓을 수 있습니다. DebugWindowMessaging 스크립트를 DebugWindow inspector 패널에 연결 합니다. 디버그 창 사용 옵션을 사용 하도록 설정 하 고 DebugWindow prefab를 Debugwindow empty 필드로 끌어 놓습니다. 적절 한 경우에는 DebugWindow 위치를 조정 합니다.

10. 부모 앵커를 두 번 클릭 하 여 선택 합니다. 전체 장면을 보려면 보기를 조정 해야 할 수 있습니다. 필요에 따라 장면을 조정 합니다.

ParentAnchor prefab에 익숙해져야 합니다. 현재, ParentAnchor 라는 게임 개체는 데모용으로 색칠 된 큐브입니다. 결국 큐브를 숨기고 콘텐츠를 ParentAnchor의 자식으로 만듭니다. 이 prefab에는 AzureSpatialAnchorsDemoWrapper.cs 스크립트 (GLOBAL.ASA SDK에 포함) 및이 모듈의 일부로 ParentAnchor 개체에 포함 된 ASAmoduleScript.cs 스크립트가 포함 되어 있습니다. 

참고: 화면에 ButtonParent를 추가 하면 TMP 자산을 가져올지 묻는 팝업이 표시 됩니다. "TMP Essentials"만 가져옵니다. 그러면 장면에 많은 글꼴 텍스트가 표시 되 면 ButtonParent 개체를 삭제 하 고 ASAmoduleAssets 폴더에서 다시 추가 합니다.

11. 단추를 구성 합니다. ButtonParent prefab에서 레이블이 지정 된 여러 단추를 확인 합니다. 이러한 단추는 MRTK의 보도 Sablebutton prefabs에서 만들어집니다. [기본 모듈](mrlearning-base-ch2.md)에서 Pressable 단추를 만드는 방법에 대해 자세히 알아보세요. 각 단추에 대해 사용자가 아래 목록에 따라 단추를 누르거나 선택할 때 트리거되는 이벤트를 추가 합니다. 

- StartAzureSession 라는 단추에 대해 단추 누름 이벤트 트리거 뿐만 아니라 클릭 시 이벤트 트리거와 함께 새 이벤트를 만듭니다. ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StartAzureSession () 메서드를 할당 합니다.

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- 단추 이름 StopAzureSession에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다. ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StopAzureSession () 메서드를 할당 합니다.

- CreateAnchor 라는 단추에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다. ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 CreateAzureAnchor () 메서드를 할당 합니다.  이후에 ParentAnchor를 다시 다음 빈 필드로 끕니다.

- 이라는 단추의 경우 앵커를 검색 하기 시작 하 고, "이벤트 트리거" 및 [클릭 시 이벤트 트리거] 아래에 새 이벤트를 만듭니다. ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 FindAzureAnchor () 메서드를 할당 합니다.

- DeleteAzureAnchor 라는 단추에 대해 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다. ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 DeleteAzureAnchor () 메서드를 할당 합니다.  이후에 ParentAnchor 개체를 다시 다음 빈 필드로 끕니다.

- 이라는 단추의 경우 로컬 앵커를 삭제 하 고 단추 누름 이벤트 트리거와 On Click 이벤트 트리거와 함께 새 이벤트를 만듭니다. ParentAnchor 개체를 빈 필드로 끌고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 RemoveLocalAnchor () 메서드를 할당 합니다.

  Azure 공간 앵커를 설정 하려면 자산 폴더의 AzureSpatialAnchorsPlugin 폴더로 이동한 다음 예-> Resources-> AzureSpatialAnchorsDemoConfig file로 이동 합니다. 검사기 패널에서 이전에 만든 Azure 계정 ID 및 계정 키를 추가 합니다. 아직 만들지 않았거나 포함 하지 않은 경우 [필수 구성 요소](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)를 따르세요. module2chapter1step13im
  
  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a>기본 응용 프로그램 빌드 및 시연

이제 Azure 공간 앵커의 기본 사항을 보여 주기 위해 장면을 구성 했으므로 Azure 공간 앵커의 기본 동작을 작성 하 고 시연 하 게 됩니다. 

1. 이전 섹션의 Build Settings 창을 닫은 경우 File>Build Settings로 이동하여 Build Settings 창을 다시 엽니다.
![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)
2. 열려 있는 장면 추가 단추를 클릭 하 여 시도 하려는 장면이 빌드 목록의 장면에 있는지 확인 합니다.
3. 플랫폼이 유니버설 Windows 플랫폼로 설정 되었는지 확인 합니다. 그렇지 않은 경우 동일한로 설정 하세요.
4. 플레이어 설정 단추를 누르고 게시 설정으로 이동 합니다. 기능 아래에서 다음을 사용 하도록 설정 합니다. 인터넷, 인터넷 클라이언트 서버, 개인 네트워크 클라이언트 서버, 이동식 저장소, 웹캠, 마이크 및 공간 인식
5. 동일한 플레이어 설정에서 XR 설정으로 이동 하 고에서 지원 되는 가상 현실를 선택 합니다.
6. Build 단추를 눌러 빌드 프로세스를 시작합니다.
   ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)
7. 애플리케이션의 새 폴더를 만들고 이름을 지정합니다. 아래 이미지에서 응용 프로그램을 포함 하기 위해 이름이 앱 인 폴더를 만들었습니다. 폴더 선택을 클릭 하 여 새로 만든 폴더로 빌드를 시작 합니다. 빌드가 완료 되 면 Unity에서 빌드 설정 "창을 닫을 수 있습니다. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 참고: 빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다. "Error: CS0246 = "XX" 형식 또는 네임 스페이스 이름을 찾을 수 없습니다. using 지시문 또는 어셈블리 참조가 있는지 확인 하십시오. [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 를 설치 해야 할 수 있습니다. 
  >

8. 빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다. "MixedRealityBase" 솔루션을 두 번 클릭 하거나 해당 하는 이름을 두 번 클릭 합니다. 프로젝트에 대체 이름을 사용 하 여 Visual Studio에서 솔루션 파일을 연 경우

  > 참고: 빌드 폴더 내에 있는 .sln 파일과 혼동 하지 않도록 해당 폴더 외부에 비슷한 이름의 .sln 파일이 있기 때문에 새로 만든 폴더 (즉, 이전 단계의 명명 규칙에 따라 응용 프로그램 폴더)를 열어야 합니다. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> 참고: Visual Studio에서 새 구성 요소를 설치 하도록 요청 하는 경우 잠시 시간을 내 서 모든 필수 구성 요소가 ["도구 설치" 페이지](install-the-tools.md) 에 특정 한 대로 설치 되었는지 확인 하세요. 

9. USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다. 이 단원 지침에서는 HoloLens 2 장치를 사용 하 여 테스트를 배포할 것으로 가정 하지만 [hololens 2 에뮬레이터](using-the-hololens-emulator.md) 에 배포 하거나 [테스트용 로드에 대 한 앱 패키지](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>) 를 만들도록 선택할 수도 있습니다.

10. 디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다. 이번에 처음으로 HoloLens 2에 배포하는 경우리면 Visual Studio에서 pin 사용하여 HoloLens 2에 연결하도록 요구할 수 있습니다. 개발자 모드를 사용 하도록 설정 하거나 Visual Studio와 쌍을 설정 해야 하는 경우 [다음 지침](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) 을 따르세요.
11. ARM 아키텍처 뿐만 아니라 릴리스 구성을 선택 하 여 HoloLens 2를 빌드하기 위해 Visual Studio를 구성 합니다.
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)

12. 마지막 단계는 디버그 > 디버깅 하지 않고 시작을 선택 하 여 장치를 빌드하는 것입니다. 디버깅 하지 않고 시작을 선택 하면 Visual Studio에 디버깅 정보가 표시 되지 않고 빌드에 성공 했을 때 응용 프로그램이 장치에서 즉시 시작 됩니다. 따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다. 또한 응용 프로그램을 자동으로 시작 하지 않고도 빌드 > 솔루션 배포를 선택 하 여 장치에 배포할 수 있습니다.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)

13. 지침을 따릅니다. 
    응용 프로그램이 장치에서 실행 되는 경우 화면의 지시를 따릅니다. 아래 단계에 해당 하는 장면 단추를 누릅니다.

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 공간 앵커 세션을 시작 합니다.
    
    2. 큐브를 다른 위치로 이동 합니다.
    
    3. 큐브의 위치에 Azure 공간 앵커를 저장 합니다.
    
    4. Azure 공간 앵커 세션을 중지 합니다.
    
    5. 큐브의 로컬 앵커를 제거 하 여 사용자가 큐브를 이동할 수 있도록 합니다.
    
    6. 큐브를 다른 위치로 이동 합니다.
    
    7. Azure 공간 앵커 세션을 시작 합니다.
    
    8. Azure 공간 앵커를 찾습니다. 
    앵커를 만들 때 원래 위치로 다시 이동 해야 합니다.
    
    9. Azure 공간 앵커를 삭제 합니다.
    
    10. Azure 세션을 중지 합니다.

### <a name="anchoring-an-experience"></a>환경 고정

이전 섹션에서는 Azure 공간 앵커의 기본 사항을 배웠습니다. 큐브를 사용 하 여 연결 된 앵커를 사용 하 여 부모 게임 개체를 나타내고 시각화 했습니다. 이 섹션에서는 ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법에 대해 알아봅니다. 이 예에서는 [기본 모듈 단원 6](mrlearning-base-ch6.md)에서 만든 음력 모듈 어셈블리 데모 응용 프로그램을 사용 합니다.

1. 다음 그림에 표시 된 것 처럼 prefab 음력 모듈 어셈블리를 검색 하 고 계층 구조에 개체의 자식으로 끌어 놓습니다.

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 아래 이미지에 표시 된 것 처럼 큐브가 계속 노출 되도록 모듈 어셈블리 환경을 배치 합니다. 응용 프로그램에서 사용자는 큐브를 이동 하 여 전체 환경을 재배치할 수 있습니다. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> 참고: 환경을 둘러싸는 경계 상자를 설정/해제 하는 단추를 사용 하 고,이 단계에서 사용 되는 큐브와 같은 위치 조정 개체를 사용 하 고, 위치 및 회전 gizmo 그리려면을 사용 하는 등의 다양 한 사용자 환경 흐름을 사용 하 여 환경 위치를 조정 합니다. 및 기타.

## <a name="congratulations"></a>축하합니다.
이 자습서에서는 Azure 공간 앵커의 기본 사항을 배웠습니다. 이 단원에서는 Azure 세션을 시작 및 중지 하 고 단일 장치에서 azure 앵커를 만들고, 업로드 하 고, 다운로드 하는 데 필요한 다양 한 단계를 살펴볼 수 있는 몇 가지 단추를 제공 했습니다. 다음 단원에서는 응용 프로그램을 다시 시작한 후에도 검색을 위해 HoloLens 2에 Azure 앵커 Id를 저장 하는 방법에 대해 알아봅니다. 시리즈를 사용 하는 동안에는 여러 장치 간에 앵커 Id를 전송 하 여 공간 맞춤을 수행 하는 방법과 공유 자습서의 일부로 서 사용자가 사용할 수 있는 다중 사용자 공유 세션에 대해 알아봅니다.

[다음 단원: 2. Azure Spatial Anchors 저장, 검색 및 공유](mrlearning-asa-ch2.md)

