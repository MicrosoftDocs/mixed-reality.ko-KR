---
title: MR Learning ASA 모듈 HoloLens 2 Azure 공간 앵커
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415273"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>HoloLens 2 Azure 공간 앵커를 사용 하 여 시작

HoloLens 2 자습서의 두 번째 모듈을 시작 합니다. 시작 하기 전에 해야 하는 모든의 합니다 [필수 구성 요소](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 완료 됩니다. 첫 번째 완료 하지 않은 경우 [기본 모듈입니다.](mrlearning-base.md) 아직 것이 좋습니다 해당 모듈을 먼저 완료 합니다. 새 Unity 프로젝트에서 시작 하는 경우의 새 프로젝트 만들기 단계를 수행 합니다 [기본 모듈입니다.](mrlearning-base.md)합니다. 

## <a name="objectives"></a>목표

* HoloLens 2를 사용 하 여 Azure 공간 앵커를 사용 하 여 개발 기본 사항 알아보기

* 만들기, 업로드 및 다운로드 공간 앵커

  

## <a name="instructions"></a>지침

### <a name="downloading-and-importing-assets"></a>다운로드 및 자산 가져오기
시작 하기 전에 다운로드 하 고 다음 자산을 가져옵니다.

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[자산 팩 MR 자료 모듈](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[자산 팩 ASA 모듈](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> 참고: Azure 공간 앵커, MR 자료 모듈 자산 팩에 대 한 지침이 6 단계 및 3-특정 지침은 4 단계 혼합 현실 도구 키트 (MRKT)에서 가져오는 방법에 대 한 지침이 5 단계를 참조 하세요.

1. 프로젝트에서 새 장면을 만듭니다. 장면 폴더를 마우스 오른쪽 단추로 클릭 하 고 "만들기", 다음 장면을 클릭 합니다. 새 장면을 ASALearningmodule 이름을 지정 합니다.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. 몇 가지 미리 정의 된 항목을 새 장면을 함께 표시를 보려는 ASALearningmodule를 두 번 클릭 합니다. 
3. 혼합된 현실 개발용 장면을 구성 합니다. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 참고: 포함 된 팝업이 표시 됩니다, 그리고 "혼합된 현실 도구 키트에 대 한 파일을 선택 해야 합니다." 확인을 클릭 하면 4 단계를 제공 합니다.

4. 선택 된 MRTK에 대 한 파일을 선택 DefaultMixedRealityToolkitConfigurationProfile 합니다.

   > 참고: 사용자 고유의 구성 프로필에 있는 경우 자유롭게을 대신 사용 하십시오.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

이제 장면 혼합된 현실 용 구성 됩니다. 장면 저장 합니다 (컨트롤을 사용 하 여이 작업을 수행할 명령을 + S 또는 파일을 클릭 한 다음 클릭 / 저장 시). 

5. 가져오기의 [Azure 공간 앵커](https://github.com/azure/azure-spatial-anchors-samples/releases)합니다. 공간 앵커를 사용 하려면이 자산을 가져와야 합니다. 위에 있는 링크를 클릭 하 고 AzureSpatialAnchors.unitypackage 마우스 오른쪽 단추로 클릭 합니다. 다른 이름으로 대상 저장 클릭 하 고 컴퓨터에 저장 합니다. 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   저장 한 후 Unity로 다시 자산 클릭, 패키지 가져오기로 이동 합니다. 사용자 지정 패키지를 클릭 하는 중... 컴퓨터 파일이 열립니다. 경우는 수행, Azure 공간 앵커 패키지를 저장 하는 위치를 찾아 선택 합니다. 열기를 클릭 합니다.

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   팝업 표시 providingg 도구 / 설정 및 가져오기에 라는 목록이 됩니다. 선택 ***모든*** 사용할 수 있는 옵션의 가져오기를 클릭 합니다.

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > 참고: 환자 일 걸립니다 잠시 시간을 가져옵니다. 

   6. 가져오기 [MR 자료 모듈 자산 팩](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) 다음입니다. 훨씬 단계 5와 같이 위의 링크를 클릭 합니다. 그런 다음 BasemoduleAssetsV1 1.unitypackag 마우스 오른쪽 단추로 클릭으로 대상 저장을 클릭 하 고 컴퓨터에 저장.

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > 팁:  쉽게 찾고 액세스할 수 있도록 동일한 폴더에 이러한 모든 자산을 저장 합니다. 간단 하 고 구성 된 모든 유지합니다.

   5 단계와 마찬가지로 Unity를 뒤로 이동, 자산을 클릭 하 고 패키지 가져오기 마우스로 합니다. 사용자 지정 패키지를 클릭 하는 중... 컴퓨터 파일은 다시 표시 됩니다. 기본 모듈 자산 팩을 저장 위치를 이동 합니다. 선택 합니다. 열기를 클릭합니다.

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > 참고: 나중에이 모듈에에서 필요한 자세한 자산 있을 수 있습니다. 이 시점에서 언급 된 모든 자산을 가져오려면 다음이 단계를 수행 합니다. 
                                                                                                                                                                                                                    
7. 동일한 접근 방식을 사용 하 여 이전 패키지를 가져올 때 ASA 모듈 ack를 가져옵니다.

### <a name="configuring-your-scene"></a>장면 구성

이 섹션에서는 prefabs 및 스크립트를 만드는 일련의 로컬 앵커와 Azure 공간 앵커 응용 프로그램에서 작동 하는 방법의 기본 개념을 보여 주는 단추 장면에 추가 합니다.

7. 자산 폴더 아래의 프로젝트 탭에서 ASAmoduleAssets 클릭 합니다. 선택 하면 두 prefabs 표시 됩니다. ButtonParent 및 ParentAnchor 합니다.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. 두 prefabs 장면 끌어다 놓습니다. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. 두 번 클릭 하 여 선택 부모 앵커입니다. 장면 전체를 보려면 보기를 조정 해야 합니다. 필요에 따라 장면을 조정 합니다.

    ParentAnchor prefab 숙지 합니다. 현재 게임 라는 개체 ParentAnchor, 데모용으로 색이 지정 된 큐브입니다. 결국 우리 ', ll 큐브를 숨기고는 ParentAnchor의 자식으로 콘텐츠를 배치 합니다. 이 prefab AzureSpatialAnchorsDemoWrapper.cs 스크립트 (ASA SDK 포함) 및 ParentAnchor 개체에이 모듈의 일부로 포함 된 ASAmoduleScript.cs 스크립트를 포함 합니다. 

10. 단추를 구성 합니다. ParentAnchor prefab 여러 레이블이 지정 된 단추 알 수 있습니다. 이러한 단추는 MRTK PressableButton prefabs에서 만들어집니다. Pressable 단추를 만드는 방법에 자세히 알아보려면 합니다 [기본 모듈입니다.](mrlearning-base-ch2.md)합니다. 각 단추에 대 한 키를 누르거나 아래 목록에 따라 단추를 선택 하는 경우 트리거되는 이벤트를 추가 합니다. 

- StartAzureSession, 라는 단추 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StartAzureSession() 메서드를 할당 합니다.

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- 단추 이름으로, StopAzureSession 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 StopAzureSession() 메서드를 할당 합니다.

- CreateAnchor, 라는 단추 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 CreateAzureAnchor() 메서드를 할당 합니다.

- 이벤트 트리거 시작 확인에 대 한 앵커 라는 단추에 대 한 단추 Presse에서 새 이벤트 만들기"와 클릭 이벤트 트리거. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 FindAzureAnchor() 메서드를 할당 합니다.

- DeleteAzureAnchor, 라는 단추 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 DeleteAzureAnchor() 메서드를 할당 합니다.

- 라는 로컬 앵커 삭제 단추의 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 RemoveLocalAnchor() 메서드를 할당 합니다.

### <a name="build-and-demonstrate-base-application"></a>빌드 및 기본 응용 프로그램을 보여 줍니다

장면을 Azure 공간 앵커의 기본 사항을 설명 하기 위해 구성 했으므로 작성 하 고 Azure 공간 앵커의 기본 동작을 보여 줍니다. 

1. 이전 섹션의 Build Settings 창을 닫은 경우 File>Build Settings로 이동하여 Build Settings 창을 다시 엽니다.
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. 열기 백그라운드에서 추가 단추를 클릭 하 여 시도 하려는 장면이 빌드 목록에 자동으로 확인 합니다.

3. Build 단추를 눌러 빌드 프로세스를 시작합니다.
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. 애플리케이션의 새 폴더를 만들고 이름을 지정합니다. 아래 이미지에서 앱 이름 가진 폴더가 응용 프로그램을 포함 하기 위해 만들어졌습니다. 새로 만든된 폴더에 빌드를 시작 폴더 선택를 클릭 합니다. Unity의 빌드가 완료 된 후 빌드 설정을 닫아도"창입니다. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 참고: 빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다. "Error: CS0246 = "XX"를 찾을 수 없는 tyoe 또는 네임 스페이스 이름 (사용 하는 누락 된 지시문 또는 어셈블리 참조가?). 설치 해야 할 수도 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. 빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다. 두 번 the"MixedRealityBase.sln 솔루션 또는 해당 이름을 클릭 합니다. Visual Studio에서 솔루션 파일을 열려면 프로젝트에 대 한 대체 이름을 사용 합니다.

  > 참고: (즉, 앱 폴더, 빌드 폴더 내에서.sln 파일을 사용 하 여 혼동 하면 안 되는 폴더 외부 이름이 비슷한.sln 파일 때문에 이전 단계에서 명명 규칙을 따르는 경우 새로 만든된 폴더를 열어야 합니다.입니다. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > 참고: 새 구성 요소를 설치를 묻는 메시지가 나타나면 Visual Studio 잠시 모든 필수 구성 요소가 설치 되어 있는지 확인 하려면에서 구체적 ["Tools 설치" 페이지](install-the-tools.md) 

6. USB 케이블을 사용하여 PC에 HoloLens 2를 연결합니다. 이러한 단원 지침 HoloLens 2 장치를 사용 하 여 테스트를 배포할 수 있다고 가정에서 수도 있습니다를 배포 하는 [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md) 를 만들도록 선택할는 [테스트용 로드 앱 패키지](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 디바이스로 빌드하기 전에 디바이스가 개발자 모드인지 확인합니다. 이번에 처음으로 HoloLens 2에 배포하는 경우리면 Visual Studio에서 pin 사용하여 HoloLens 2에 연결하도록 요구할 수 있습니다. 따릅니다 [이러한 지침](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) 개발자 모드를 사용 하도록 설정 하거나 Visual Studio를 쌍으로 연결 해야 하는 경우.

8. 릴리스 구성 및 "RM" 아키텍처를 선택 하 여 HoloLens 2에 구성에 대 한 Visual Studio를 구성 합니다.
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. 마지막 단계는 디버그를 선택 하 여 장치를 빌드할 수 > 디버깅 하지 않고 시작 합니다. 디버깅 하지 않고 시작을 선택 하면 응용 프로그램을 Visual Studio에 표시 되는 성공적인 빌드 다음 디버깅 정보에 따라 장치에 즉시 시작 됩니다. 따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다. 빌드를 선택할 수 있습니다 > 응용 프로그램을 자동으로 시작 하지 않고 장치에 배포할 솔루션을 배포 합니다.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. 지침을 따릅니다. 응용 프로그램은 장치에서 실행 하는 경우에 따라는 화면의 지침입니다. 아래 단계에 해당 되는 장면 단추를 누릅니다.
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 공간 앵커 세션을 시작 합니다.
    
    2. 큐브를 다른 위치로 이동 합니다.
    
    3. 큐브의 위치의 Azure 공간 앵커를 저장 합니다.
    
    4. Azure 공간 앵커 세션을 중지 합니다.
    
    5. 큐브에 큐브를 이동할 수 있도록 로컬 앵커를 제거 합니다.
    6. 큐브의 다른 위치를 이동 합니다.
    
    7. Azure 공간 앵커 세션을 시작 합니다.
    
    8. Azure 공간 aachors를 찾습니다. 
    
    e 되돌아가야 원래 위치로 있습니다 넣습니다 앵커를 만들 때).
    9. Azure 공간 앵커를 삭제 합니다.
    
    10. Azure 세션을 중지 합니다.

### <a name="anchoring-an-experience"></a>환경을 고정

이전 섹션에서는 Azure 공간 앵커의 기본 사항을 알아보았습니다. 큐브를 나타내는 연결 된 앵커를 사용 하 여 부모 게임 개체를 시각화 사용 했습니다. 이 섹션에서는 ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법을 알아봅니다. 예를 들어 음력 모듈 중 생성 된 어셈블리 데모 응용 프로그램을 사용 했습니다 [기본 모듈 6 단원](mrlearning-base-ch6.md)합니다.

1. 음력 모듈 어셈블리 전체 prefab을 검색 하 고 끌어온 사용자 계층 구조의 AnchorParent gameobject 자식인 아래 이미지에 표시 된 대로 키를 누릅니다.

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 모듈 어셈블리 위치에는 아래 이미지 에서처럼 큐브에 노출 됩니다 있도록 발생 합니다. 응용 프로그램에서 사용자가 큐브를 이동 하 여 전체 환경 위치 변경 될 수 있습니다. 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > 참고: 다양 한 경험을 둘러싸는 경계 상자를 설정/해제, 위치 및 회전 gizmo 사용 재배치 개체 (예: 큐브가이 단계에서 사용)를 사용 하는 단추 사용을 비롯 하 여 환경을 위치에 대 한 사용자 경험 흐름 및 기타 정보입니다.

## <a name="congratulations"></a>축하합니다.
이 단원에서는 Azure 공간 앵커의 기본 사항을 알아보았습니다. 이 esson 수 있는 여러 단추를 사용 하 여 시작 하 고 Azure 세션을 중지 하 고 만들기, 업로드 및 단일 장치에서 azure 앵커를 다운로드 하는 데 필요한 다양 한 단계를 살펴보면 제공 합니다. 다음 단원에서는 응용 프로그램 다시 시작 된 후에, 검색에 대 한 여 HoloLens 2 Azure 앵커 Id를 저장 하는 방법을 알아보겠습니다. 시리즈도 배웁니다 공간 맞춤 하 고 다중 사용자 세션 (곧 모듈을 공유 하는 일환으로 제공 합니다.)를 공유 하는 방법에 대 한 알아봅니다를 여러 장치 간에 앵커 Id를 전송 하는 방법

[다음 단원: ASA 단원 2](mrlearning-asa-ch2.md)

