---
title: MR 입력 213
description: Unity, Visual Studio 및 몰입 형 헤드셋을 사용 하 여이 코딩 자습서를 수행 하 여 동작 컨트롤러의 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 동작 컨트롤러, 아카데미, 자습서
ms.openlocfilehash: e2199c3afed21f9396ed84f71093a8b2fb3bb23b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438551"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. HoloLens 2에 대 한 [새로운 일련의 자습서](mrlearning-base.md) 가 게시 되었습니다.

<br>

# <a name="mr-input-213-motion-controllers"></a>MR 입력 213: 동작 컨트롤러

혼합 현실 세계의 동작 컨트롤러는 다른 수준의 대화형 작업을 추가 합니다. [동작 컨트롤러](motion-controllers.md)를 사용 하 여 집중 교육 및 즐거움를 응용 프로그램 환경에서 확장 하는 실제 상호 작용과 비슷하게 보다 자연스럽 게 개체와 직접 상호 작용할 수 있습니다.

MR 입력 213에서는 간단한 공간 그리기 환경을 만들어 동작 컨트롤러의 입력 이벤트를 탐색 합니다. 이 앱을 사용 하면 다양 한 유형의 브러시 및 색을 사용 하 여 3 차원 공간으로 그릴 수 있습니다.

## <a name="topics-covered-in-this-tutorial"></a>이 자습서에서 다루는 항목

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**컨트롤러 시각화**|**컨트롤러 입력 이벤트**|**사용자 지정 컨트롤러 및 UI**|
|Unity의 게임 모드 및 런타임에 동작 컨트롤러 모델을 렌더링 하는 방법에 대해 알아봅니다.|다양 한 종류의 단추 이벤트 및 해당 응용 프로그램을 이해 합니다.|컨트롤러 위에 UI 요소를 오버레이 하거나 완전히 사용자 지정 하는 방법에 대해 알아봅니다.|

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 213: 동작 컨트롤러</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 확인 사항

### <a name="prerequisites"></a>필수 구성 요소

[이 페이지](install-the-tools.md)의 모던 헤드셋에 대 한 설치 검사 목록을 참조 하세요.

* 이 자습서에는 [Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe) 가 필요 합니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일을 다운로드](https://github.com/Microsoft/MixedReality213/archive/master.zip) 하 고 바탕 화면에 파일을 추출 합니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/MixedReality213)있습니다.

## <a name="unity-setup"></a>Unity 설치

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>목표

* Windows Mixed Reality 개발을 위한 Unity 최적화
* 혼합 현실 설치 카메라
* 설정 환경

### <a name="instructions"></a>지침

* Unity를 시작합니다.
* **열기**를 선택 합니다.
* 바탕 화면으로 이동 하 여 이전에 unarchived **MixedReality213** 폴더를 찾습니다.
* **폴더 선택**을 클릭합니다.
* Unity에서 프로젝트 파일 로드를 마치면 Unity 편집기를 볼 수 있습니다.
* Unity에서 **파일 > 빌드 설정**을 선택 합니다.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 단추를 클릭 합니다.
* 대상 장치를 **모든 장치로** 설정
* 빌드 유형을 **D3D** 로 설정
* SDK를 **최신 설치** 로 설정
* **Unity C# 프로젝트** 확인
    * 이를 통해 Unity 프로젝트를 다시 빌드하지 않고 Visual Studio 프로젝트에서 스크립트 파일을 수정할 수 있습니다.
* **플레이어 설정**을 클릭 합니다.
* **검사기** 패널에서 아래쪽으로 스크롤합니다.
* XR 설정에서 **지원 되는 가상 현실** 확인
* 가상 현실 Sdk에서 **Windows Mixed reality** 를 선택 합니다.

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* **빌드 설정** 창을 닫습니다.

### <a name="project-structure"></a>프로젝트 구조

이 자습서에서는 **[Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용 합니다. [이 페이지](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)에서 릴리스를 찾을 수 있습니다.

![ProjectStructure](images/mr213-projectstructure-650px.png)

**참조용으로 완료 된 장면**

* **백그라운드** 폴더 아래에 두 개의 완료 된 Unity 장면을 찾을 수 있습니다.
    * **MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면
    * **MixedReality213Advanced**: 여러 브러시를 사용 하 여 고급 디자인을 위한 장면 완료

**자습서에 대 한 새 장면 설정**

* Unity에서 **파일 > 새 장면** 을 클릭 합니다.
* **기본 카메라** 및 **방향성 광원** 삭제
* **프로젝트 패널**에서 다음 prefabs을 검색 하 여 **계층** 패널로 끌어옵니다.
    * Asset/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * 자산/AppPrefabs/**환경**

    ![카메라 및 환경](images/mr213-cameraenvironment-300px.jpg)

* 혼합 현실 도구 키트에는 두 가지 카메라 prefabs 있습니다.
    * **MixedRealityCamera. prefab**: 카메라 전용
    * **MixedRealityCameraParent prefab**: 카메라 + Teleportation + 경계
    * 이 자습서에서는 teleportation 기능 없이 **MixedRealityCamera** 를 사용 합니다. 이로 인해 사용자가 접지 되도록 기본적인 층을 포함 하는 간단한 **환경** prefab를 추가 했습니다.
    * **MixedRealityCameraParent**를 사용 하 여 teleportation에 대 한 자세한 내용은 [고급 디자인-teleportation 및 locomotion](#advanced-design---teleportation-and-locomotion) 를 참조 하세요.

**Skybox 설정**

* **창 > 조명 > 설정** 을 클릭 합니다.
* **Skybox 재질 필드** 의 오른쪽에 있는 원을 클릭 합니다.
* ' 회색 '을 입력 하 고 **SkyboxGray** (자산/AppPrefabs/Support/재질/SkyboxGray)를 선택 합니다.

    ![Skybox 설정](images/mr123-skyboxsetting-400px.jpg)

* 할당 된 회색 그라데이션 Skybox을 볼 수 있도록 **Skybox** 옵션을 선택 합니다.

    ![Skybox 옵션 설정/해제](images/mr213-skyboxcheck-400px.jpg)

* MixedRealityCamera, 환경 및 회색 skybox이 포함 된 장면을 다음과 같이 표시 됩니다.

    ![MixedReality213 환경](images/mr213-environment-600px.jpg)

* **파일 > 장면 저장을** 클릭 합니다.
* 모든 이름의 장면 폴더 아래에 장면 **저장**

## <a name="chapter-1---controller-visualization"></a>1 장-컨트롤러 시각화

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>목표

* Unity의 게임 모드 및 런타임에 동작 컨트롤러 모델을 렌더링 하는 방법에 대해 알아봅니다.

Windows Mixed Reality는 컨트롤러 시각화를 위한 애니메이션 컨트롤러 모델을 제공 합니다. 앱에서 컨트롤러 시각화에 대해 수행할 수 있는 몇 가지 방법이 있습니다.

* 기본값-수정 하지 않고 기본 컨트롤러 사용
* 하이브리드-기본 컨트롤러를 사용 하지만 일부 요소 또는 겹쳐 있는 UI 구성 요소를 사용자 지정 합니다.
* 대체-컨트롤러에 대해 사용자 지정 된 사용자 지정 3D 모델 사용

이 장에서는 이러한 컨트롤러 사용자 지정의 예제에 대해 알아봅니다.

### <a name="instructions"></a>지침

* **프로젝트** 패널의 검색 상자에 **motioncontrollers** 를 입력 합니다. 자산/HoloToolkit/입력/Prefabs/에서 찾을 수도 있습니다.
* **Motioncontrollers** Prefab을 **계층** 패널로 끌어 옵니다.
* **계층** 패널에서 **motioncontrollers** prefab를 클릭 합니다.

**MotionControllers prefab**

**Motioncontrollers** prefab에는 대체 컨트롤러 모델용 슬롯을 제공 하는 **Motioncontroller시각기** 스크립트가 있습니다. 손 또는 소드와 같은 사용자 지정 3D 모델을 할당 하 고 ' 항상 대체 왼쪽/오른쪽 모델 사용 '을 선택 하면 기본 모델 대신 해당 모델이 표시 됩니다. 4 장에서이 슬롯을 사용 하 여 컨트롤러 모델을 브러시로 바꿉니다.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**지침**

* **검사기** 패널에서 **Motioncontrollervisualizer** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.

**MotionControllerVisualizer 도우미 스크립트**

**Motioncontrollervisualizer** 및 **Motioncontrollervisualizer** 클래스는 기본 컨트롤러 모델을 액세스 & 수정 하는 방법을 제공 합니다. **Motioncontrollervisualizer** 는 Unity의 **InteractionSourceDetected** 이벤트를 구독 하 고 발견 되 면 컨트롤러 모델을 자동으로 인스턴스화합니다.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

컨트롤러 모델은 고 지 수 [설정](https://github.com/KhronosGroup/glTF)에 따라 제공 됩니다. 이 형식은 공통 형식을 제공 하기 위해 만들어졌지만 3D 자산의 전송 및 압축 풀기의 프로세스를 개선 합니다. 이 경우 가능한 한 원활 하 게 사용자 환경을 만들고 사용자가 사용 중일 수 있는 동작 컨트롤러의 버전을 보장 하지 않기 때문에 런타임에 컨트롤러 모델을 검색 하 고 로드 해야 합니다. 이 과정에서 혼합 현실 도구 키트를 통해 Khronos 그룹의 [Unity글 tf 프로젝트](https://github.com/KhronosGroup/UnityGLTF)버전을 사용 합니다.

컨트롤러가 전달 된 후에는 스크립트에서 **Motioncontrollerinfo** 를 사용 하 여 특정 컨트롤러 요소에 대 한 변환을 찾아 스스로 위치를 올바르게 지정할 수 있습니다.

이후 장에서는 이러한 스크립트를 사용 하 여 UI 요소를 컨트롤러에 연결 하는 방법을 배웁니다.

*일부 스크립트에서는 #if 된 코드 블록을 찾을 수 있습니다 **. UNITY_EDITOR** 또는 **UNITY_WSA**. 이러한 코드 블록은 Windows에 배포할 때 UWP 런타임에만 실행 됩니다. Unity 편집기와 UWP 앱 런타임에서 사용 하는 Api 집합이 다르기 때문입니다.*

* 장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.

헤드셋에서 이동 컨트롤러를 사용 하는 장면을 볼 수 있습니다. 단추 클릭, 엄지 스틱 움직임 및 터치 패드 touch 강조 표시에 대 한 자세한 애니메이션을 볼 수 있습니다.

![MR213_Controller 시각화 기본값](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>2 장-컨트롤러에 UI 요소 연결

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>목표

* 동작 컨트롤러의 요소에 대 한 자세한 정보
* 컨트롤러의 특정 부분에 개체를 연결 하는 방법 알아보기

이 장에서는 사용자가 언제 든 지 쉽게 액세스 하 고 조작할 수 있는 사용자 인터페이스 요소를 컨트롤러에 추가 하는 방법을 배웁니다. 또한 터치 패드 입력을 사용 하 여 간단한 색 선택 UI를 추가 하는 방법을 알아봅니다.

### <a name="instructions"></a>지침

* **프로젝트** 패널에서 **Motioncontrollerinfo** 스크립트를 검색 합니다.
* 검색 결과에서 **Motioncontrollerinfo** 스크립트를 두 번 클릭 하 여 Visual Studio의 코드를 확인 합니다.

**MotionControllerInfo 스크립트**

첫 번째 단계는 UI를 연결 하려는 컨트롤러의 요소를 선택 하는 것입니다. 이러한 요소는 **MotionControllerInfo.cs**의 **controllerelementenum** 에 정의 되어 있습니다.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **홈**
* **메뉴**
* **잡습니다**
* **사용해**
* **선택**
* **터치패드**
* **가리키기 포즈** –이 요소는 정방향 방향을 가리키는 컨트롤러의 팁을 나타냅니다.

**지침**

* **프로젝트** 패널에서 **AttachToController** 스크립트를 검색 합니다.
* 검색 결과에서 **AttachToController** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.

**AttachToController 스크립트**

**AttachToController** 스크립트는 및 요소를 통해 지정 된 컨트롤러에 개체를 연결 하는 간단한 방법을 제공 합니다.

**AttachElementToController ()** 에서

* **Motioncontrollerinfo를** 사용 하 여 사용 하기
* **Motioncontrollerinfo. TryGetElement ()를** 사용 하 여 컨트롤러의 특정 요소를 가져옵니다.
* 컨트롤러 모델에서 요소의 변환을 검색 한 후 해당 개체의 부모 개체를 부모로 설정 하 고 개체의 로컬 위치를 0으로 & 설정 합니다.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

**AttachToController** 스크립트를 사용 하는 가장 간단한 방법은 **Color kerwheel** 의 경우와 마찬가지로이 스크립트에서 상속 하는 것입니다. **OnAttachToController** 및 **OnDetatchFromController** 함수를 재정의 하 여 컨트롤러를 검색/연결 해제 하는 경우 설정/분석을 수행 합니다.

**지침**

* **프로젝트** 패널에서 검색 상자 **Colorpickerwheel**을 입력 합니다. 자산/AppPrefabs/에서 찾을 수도 있습니다.
* **Colorprefab Kerwheel** 을 **계층** 패널로 끌어 옵니다.
* **계층** 패널에서 **Colorpickerwheel** prefab를 클릭 합니다.
* **검사기** 패널에서 **Colorpickerwheel** 스크립트를 두 번 클릭 하 여 Visual Studio의 코드를 확인 합니다.

![Colorprefab Kerwheel](images/mr213-colorpickerwheel-1000px.jpg)

**Color Kerwheel 스크립트**

**ColorAttachToController Kerwheel** 은를 상속 하므로 **검사기** 패널에 **손** 및 **요소가** 표시 됩니다. UI를 왼쪽 컨트롤러의 터치 패드 요소에 연결 합니다.

![Color Kerwheel 스크립트](images/mr213-attachtocontroller-300px.jpg)

**Colorpickerwheel** 은 **OnAttachToController** 및 **OnDetatchFromController** 를 재정의 하 여 입력 이벤트를 구독 합니다 .이 이벤트는 다음 챕터에서 터치 패드 입력을 사용 하 여 색을 선택 하는 데 사용 됩니다.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* 장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.

**개체를 컨트롤러에 연결 하는 다른 방법**

스크립트는 **AttachToController** 에서 상속 하 고 **OnAttachToController**를 재정의 하는 것이 좋습니다. 그러나 이것이 항상 가능 하지는 않습니다. 다른 방법으로는 독립 실행형 구성 요소로 사용 합니다. 이는 스크립트를 리팩터링 하지 않고 컨트롤러에 기존 prefab를 연결 하려는 경우에 유용할 수 있습니다. 설치를 수행 하기 전에 클래스에서 IsAttached을 true로 설정할 때까지 대기 하기만 하면 됩니다. 이 작업을 수행 하는 가장 간단한 방법은 ' Start '에 코 루틴를 사용 하는 것입니다.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>3 장-터치 패드 입력 작업

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>목표

* 터치 패드 입력 데이터 이벤트를 가져오는 방법 알아보기
* 앱 환경에 대 한 터치 패드 축 위치 정보를 사용 하는 방법을 알아봅니다.

### <a name="instructions"></a>지침

* **계층** 패널에서 **Colorpickerwheel** 을 클릭 합니다.
* **검사기** 패널의 **Animatior**아래에서 **ColorPickerWheelController** 을 두 번 클릭 합니다.
* **애니메이터** 탭이 열려 있는 것을 볼 수 있습니다.

**Unity 애니메이션 컨트롤러를 사용 하 여 UI 표시/숨기기**

애니메이션을 사용 하 여 **Colorpickerwheel** UI를 표시 하거나 숨기려면 [Unity의 애니메이션 시스템](https://docs.unity3d.com/Manual/AnimationOverview.html)을 사용 합니다. **Colorpickerwheel**의 **Visible** 속성을 true 또는 false 트리거로 설정 하면 애니메이션 트리거가 **표시** 되 고 **숨겨집니다** . **표시** 및 **숨기기** 매개 변수는 **ColorPickerWheelController** 애니메이션 컨트롤러에서 정의 됩니다.

![Unity 애니메이션 컨트롤러](images/mr123-animationcontroller-550px.jpg)

**지침**

* **계층** 패널에서 **Colorpickerwheel** prefab를 선택 합니다.
* **검사기** 패널에서 **Colorpickerwheel** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.

**Color Kerwheel 스크립트**

**Color Kerwheel** 은 Unity 이벤트를 수신 하는 Unity의 **InteractionSourceUpdated** 이벤트를 구독 합니다.

**InteractionSourceUpdated ()** 에서 스크립트는 먼저 다음을 확인 합니다.

* 는 실제로 터치 패드 이벤트 (.obj. 상태)입니다. **touchpadTouched**)
* 왼쪽 컨트롤러에서 생성 됩니다 **(obj. source. 손**)

둘 다 true 이면 터치 패드 위치 (obj. 상태)입니다. **touchpadPosition**)가 **selectorPosition**에 할당 됩니다.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

**표시 되** 는 속성을 기반으로 하는 **Update ()** 에서 색 선택의 애니메이터 구성 요소에 표시 및 숨기기 애니메이션 트리거를 트리거합니다.

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

**Update ()** 에서 **selectorPosition** 는 UV 위치를 반환 하는 색 휠의 메시 collider에서 광선을 캐스팅 하는 데 사용 됩니다. 그런 다음이 위치를 사용 하 여 색 휠의 질감의 픽셀 좌표 및 색 값을 찾을 수 있습니다. 이 값은 **Selectedcolor** 속성을 통해 다른 스크립트에서 액세스할 수 있습니다.

![색 선택 휠 Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>4 장-컨트롤러 모델 재정의

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>목표

* 사용자 지정 3D 모델을 사용 하 여 컨트롤러 모델을 재정의 하는 방법에 대해 알아봅니다.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>지침

* **계층** 패널에서 **motioncontrollers** 를 클릭 합니다.
* **오른쪽의 대체 컨트롤러** 필드 오른쪽에 있는 원을 클릭 합니다.
* **' BrushController**'을 입력 하 고 결과에서 prefab를 선택 합니다. 자산/AppPrefabs/**BrushController**에서 찾을 수 있습니다.
* **항상 대체 권한 모델 사용** 을 선택 합니다.

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController** Prefab는 **계층** 패널에 포함할 필요가 없습니다. 그러나 자식 구성 요소를 체크 아웃 하려면:

* **프로젝트** 패널에서 **BrushController** 를 입력 하 고 **BrushController** prefab를 **계층** 패널로 끌어옵니다.

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

**팁** 구성 요소는 **BrushController**에서 찾을 수 있습니다. 이를 사용 하 여 줄 그리기를 시작/중지 합니다.

* **계층** 패널에서 **BrushController** 를 삭제 합니다.
* 장면을 **저장** 하 고 **재생** 단추를 클릭 합니다. 오른쪽 동작 컨트롤러를 교체 하는 브러시 모델을 볼 수 있습니다.

## <a name="chapter-5---painting-with-select-input"></a>5 장-선택 입력으로 그리기

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>목표

* 선택 단추 이벤트를 사용 하 여 선 그리기를 시작 및 중지 하는 방법에 대해 알아봅니다.

### <a name="instructions"></a>지침

* **프로젝트** 패널에서 **BrushController** prefab를 검색 합니다.
* **검사기** 패널에서 **BrushController** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.

**BrushController 스크립트**

**BrushController** 는 InteractionManager의 **InteractionSourcePressed** 및 **InteractionSourceReleased** 이벤트를 구독 합니다. **InteractionSourcePressed** 이벤트가 트리거되면 브러시의 **그리기** 속성이 true로 설정 됩니다. **InteractionSourceReleased** 이벤트가 트리거되면 브러시의 **그리기** 속성이 false로 설정 됩니다.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

**Draw** 를 true로 설정 하는 동안 브러시는 인스턴스화된 Unity **LineRenderer**의 요소를 생성 합니다. 이 prefab에 대 한 참조는 브러시의 **Stroke prefab** 필드에 저장 됩니다.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

색 선택 휠 UI에서 현재 선택 된 색을 사용 하려면 **BrushController** 에 **Colorpickerwheel** 개체에 대 한 참조가 있어야 합니다. **BrushController** prefab는 런타임에 대체 컨트롤러로 인스턴스화되기 때문에 장면의 개체에 대 한 모든 참조는 런타임에 설정 되어야 합니다. 이 경우 GameObject를 사용 하 여 **ColorFindObjectOfType** 를 찾습니다.

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* 장면을 **저장** 하 고 **재생** 단추를 클릭 합니다. 오른쪽 컨트롤러의 선택 단추를 사용 하 여 선을 그리고 그릴 수 있습니다.

## <a name="chapter-6---object-spawning-with-select-input"></a>6 장-선택 입력으로 개체 생성

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>목표

* 선택 및 이해 단추 입력 이벤트를 사용 하는 방법을 알아봅니다.
* 개체를 인스턴스화하는 방법 알아보기

### <a name="instructions"></a>지침

* **프로젝트** 패널의 검색 상자에 **ObjectSpawner** 를 입력 합니다. 자산/AppPrefabs/에서 찾을 수도 있습니다.
* **ObjectSpawner** Prefab를 **계층** 패널로 끌어 옵니다.
* **계층** 패널에서 **ObjectSpawner** 를 클릭 합니다.
* **ObjectSpawner** 에는 **Color Source**라는 필드가 있습니다.
* **계층** 패널에서 **Colorpickerwheel** 참조를이 필드로 끌어 옵니다.

    ![개체 Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* **계층** 패널에서 **ObjectSpawner** prefab을 클릭 합니다.
* **검사기** 패널에서 **ObjectSpawner** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.

**ObjectSpawner 스크립트**

**ObjectSpawner** 는 기본 메시 (cube, 구, 실린더)의 복사본을 공간으로 인스턴스화합니다. **InteractionSourcePressed** 감지 되 면이를 확인 하 고 **InteractionSourcePressType** 또는 **InteractionSourcePressType** 이벤트 인지 여부를 확인 합니다.

이 이벤트 **의 경우 현재** 메시 유형 (구, 큐브, 실린더)의 인덱스를 증가 시킵니다.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

**Select** 이벤트의 경우 **SpawnObject ()** 에서 새 개체가 인스턴스화되어, 부모로 해제 되 고, 전 세계에 릴리스됩니다.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner** 는 **Color kerwheel** 을 사용 하 여 표시 개체의 재질 색을 설정 합니다. 생성 된 개체에는이 자료의 인스턴스가 제공 되므로 색을 유지 합니다.

* 장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.

[클릭] 단추를 사용 하 여 개체를 변경 하 고 [선택] 단추를 사용 하 여 개체를 생성할 수 있습니다.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>혼합 현실 포털에 앱 빌드 및 배포

* Unity에서 **파일 > 빌드 설정**을 선택 합니다.
* 열려 있는 장면 **추가** 를 클릭 하 여 현재 장면을 **빌드 장면**에 추가 합니다.
* **빌드**를 클릭합니다.
* "App" 이라는 **새 폴더** 를 만듭니다.
* 단일 **앱** 폴더를 클릭 합니다.
* **폴더 선택**을 클릭합니다.
* Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.
* **앱** 폴더를 엽니다.
* **YourSceneName** Visual Studio 솔루션 파일을 두 번 클릭 합니다.
* Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64**로 변경 합니다.
* 장치 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **로컬 컴퓨터**를 선택 합니다.
* 메뉴에서 **디버그 >-디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.

이제 앱이 혼합 현실 포털에 빌드되고 설치 됩니다. 혼합 현실 포털의 시작 메뉴를 통해 다시 시작할 수 있습니다.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>방사형 레이아웃을 사용 하는 고급 디자인-브러시 도구

![MixedReality213 주](images/mr213-main-600px.jpg)

이 장에서는 기본 동작 컨트롤러 모델을 사용자 지정 브러시 도구 컬렉션으로 바꾸는 방법을 배웁니다. 참조를 위해, **장면 폴더 아래** 에서 완료 된 장면 **MixedReality213Advanced** 를 찾을 수 있습니다.

### <a name="instructions"></a>지침

* **프로젝트** 패널의 검색 상자에 **BrushSelector** 를 입력 합니다. 자산/AppPrefabs/에서 찾을 수도 있습니다.
* **BrushSelector** Prefab를 **계층** 패널로 끌어 옵니다.
* 조직의 경우 **브러시** 라는 빈 GameObject를 만듭니다.
* **프로젝트** 패널에서 다음 Prefabs을 **브러시로** 끌어 옵니다.
    * 자산/AppPrefabs/**BrushFat**
    * 자산/AppPrefabs/**BrushThin**
    * 자산/AppPrefabs/**지우개**
    * 자산/AppPrefabs/**Markerfat**
    * 자산/AppPrefabs/**Markerthin**
    * 자산/AppPrefabs/**연필**

    ![브러시](images/mixedreality213-brushes-250px.png)

* **계층** 패널에서 **motioncontrollers** prefab를 클릭 합니다.
* **검사기** 패널에서 항상 **동작 컨트롤러 시각화 도우미** 의 **대체 오른쪽 모델 사용** 확인란을 선택 취소 합니다.
* **계층** 패널에서 **BrushSelector** 를 클릭 합니다.
* **BrushSelector** 에 **colorpicker** 라는 필드가 있습니다.
* **계층** 패널에서 **Colorpickerwheel** 을 **Inspector** 패널의 **colorpicker** 필드로 끕니다.

    ![브러시 선택기에 ColorPickerWheel 할당](images/mr213-brushselector-500px.jpg)

* **계층** 패널의 **BrushSelector** prefab에서 **메뉴** 개체를 선택 합니다.
* **검사기** 패널의 **lineobjectcollection** 구성 요소 아래에서 **개체** 배열 드롭다운을 엽니다. 빈 슬롯이 6 개 표시 됩니다.
* **계층** 패널에서 **브러시** GameObject의 각 prefabs 부모를 각각 순서 대로 이러한 슬롯으로 끕니다. (프로젝트 폴더의 prefabs가 아니라 장면에서 prefabs을 끌지 확인 하세요.)

![브러시 선택기](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefab**

**BrushSelector** 는 **AttachToController**를 상속 하므로 **검사기** 패널에서 및 **요소** **옵션을 표시** 합니다. **오른쪽** 및 **포인팅 포즈** 를 선택 하 여 정방향 컨트롤러에 브러시 도구를 연결 합니다.

**BrushSelector** 는 다음과 같은 두 가지 유틸리티를 사용 합니다.

* **Ellipse**: 타원 셰이프를 따라 공간에 요소를 생성 하는 데 사용 됩니다.
* **Lineobjectcollection**: 모든 줄 클래스 (예: 타원)에서 생성 된 요소를 사용 하 여 개체를 배포 합니다. 타원 셰이프를 따라 브러시를 배치 하는 데 사용할 것입니다.

결합 하면 이러한 유틸리티를 사용 하 여 방사형 메뉴를 만들 수 있습니다.

**LineObjectCollection 스크립트**

**Lineobjectcollection** 에는 줄을 따라 분산 된 개체의 크기, 위치 및 회전에 대 한 컨트롤이 있습니다. 이는 브러시 선택기와 같은 방사형 메뉴를 만드는 데 유용 합니다. 가운데 선택 된 위치에 따라 아무것도 확장 되지 않는 브러시의 모양을 만들려면 **objectscale** 곡선이 가운데에서 증가 하 고 가장자리에서 tapers 합니다.

**BrushSelector 스크립트**

**BrushSelector**의 경우 절차적 애니메이션을 사용 하도록 선택 했습니다. 먼저, 브러시 모델은 **Lineobjectcollection** 스크립트에 의해 타원에 배포 됩니다. 그런 다음, 각 브러시는 선택 항목에 따라 변경 되는 **DisplayMode** 값을 기반으로 사용자 손으로 위치를 유지 관리 합니다. 사용자가 브러시를 선택할 때 브러시 위치 전환이 중단 될 확률이 높다는 것으로 인해 절차적 접근 방식을 선택 했습니다. Mecanim 애니메이션은 중단을 정상적으로 처리할 수 있지만 간단한 Lerp 작업 보다 복잡 한 경향이 있습니다.

**BrushSelector** 는 두 가지 조합을 모두 사용 합니다. 터치 패드 입력이 검색 되 면 브러시 옵션이 표시 되 고 방사형 메뉴를 따라 확장 됩니다. 제한 시간 (사용자가 선택 했음을 나타냄) 후에 브러시 옵션이 다시 축소 되어 선택한 브러시만 남게 됩니다.

**터치 패드 입력 시각화**

컨트롤러 모델이 완전히 바뀐 경우에도 원래 모델 입력에 대 한 입력을 표시 하는 것이 유용할 수 있습니다. 이를 통해 실제로 사용자의 작업을 수행할 수 있습니다. **BrushSelector** 의 경우 입력을 받을 때 터치 패드가 잠깐 표시 되도록 선택 했습니다. 이렇게 하려면 컨트롤러에서 터치 패드 요소를 검색 하 고 해당 재질을 사용자 지정 재질로 바꾼 다음, 터치 패드 입력을 마지막으로 받은 시간을 기준으로 해당 재질의 색에 그라데이션을 적용 합니다.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**터치 패드가 입력 된 브러시 도구 선택**

브러시 선택기에서 터치 패드의 누른 입력을 검색 하면 입력의 위치를 확인 하 여 왼쪽 또는 오른쪽에 있는지 확인 합니다.

**Select보도 Sedamount를 사용 하 여 두께 스트로크**

**InteractionSourcePressed ()** 에서 **InteractionSourcePressType** 이벤트 대신 **select보도 sedamount**를 통해 눌린 금액의 아날로그 값을 가져올 수 있습니다. 이 값은 **InteractionSourceUpdated ()** 에서 검색할 수 있습니다.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**지우개 스크립트**

**지우개** 는 기본 **브러시**의 **drawovertime ()** 함수를 재정의 하는 특수 한 유형의 브러시입니다. 그리기가 true 인 동안 지우개는 해당 팁이 기존 브러시 스트로크와 교차 하는지 확인 합니다. 이렇게 하면 축소 하 고 삭제할 큐에 추가 됩니다.

## <a name="advanced-design---teleportation-and-locomotion"></a>고급 디자인-Teleportation 및 locomotion

사용자가 엄지 스틱을 사용 하 여 teleportation를 사용 하 여 장면 주위로 이동할 수 있도록 하려면 **MixedRealityCamera**대신 **MixedRealityCameraParent** 를 사용 합니다. **Inputmanager** 및 **DefaultCusor**도 추가 해야 합니다. **MixedRealityCameraParent** 에는 이미 **Motioncontrollers** 와 **경계가** 자식 구성 요소로 포함 되어 있으므로 기존 **motioncontrollers** 및 **Environment** prefab을 제거 해야 합니다.

### <a name="instructions"></a>지침

* **계층** 패널에서 **MixedRealityCamera**, **Environment** 및 **motioncontrollers** 를 삭제 합니다.
* **프로젝트 패널**에서 다음 prefabs을 검색 하 여 **계층** 패널로 끌어옵니다.
    * Asset/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * 자산/AppPrefabs/입력/Prefabs/**Inputmanager**
    * 자산/AppPrefabs/입력/Prefabs/커서/**Defaultcursor**

    ![혼합 현실 카메라 부모](images/mr213-cameraparent-300px.png)

* **계층** 패널에서 **입력 관리자** 를 클릭 합니다.
* **검사기** 패널에서 **간단한 단일 포인터 선택기** 섹션까지 아래로 스크롤합니다.
* **계층** 패널에서 **defaultcursor** 를 **커서** 필드로 끌어 옵니다.

    ![DefaultCursor 할당](images/mr213-defaultcursor-500px.png)

* 장면을 **저장** 하 고 **재생** 단추를 클릭 합니다. 엄지 스틱을 사용 하 여 왼쪽/오른쪽 또는 텔레포트로 회전할 수 있습니다.

## <a name="the-end"></a>끝

이 자습서의 끝입니다! 배운 내용:

* Unity의 게임 모드 및 런타임에서 동작 컨트롤러 모델을 사용 하는 방법을 설명 합니다.
* 다양 한 형식의 단추 이벤트 및 해당 응용 프로그램을 사용 하는 방법입니다.
* 컨트롤러 위에 UI 요소를 오버레이 하거나 완전히 사용자 지정 하는 방법입니다.

이제 이동 컨트롤러를 사용 하 여 사용자 고유의 몰입 형 환경을 만들 준비가 되었습니다.

## <a name="completed-scenes"></a>완료 된 장면

* Unity의 **프로젝트** 패널에서 **장면** 폴더를 클릭 합니다.
* 두 Unity sceens **MixedReality213** 및 **MixedReality213Advanced**를 찾을 수 있습니다.
    * **MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면
    * **MixedReality213Advanced**: 선택 단추의 보도 금액 예제를 사용 하는 여러 브러시가 있는 완료 된 장면

## <a name="see-also"></a>참고 항목

* [MR 입력 213 프로젝트 파일](https://github.com/Microsoft/MixedReality213)
* [혼합 현실 도구 키트-동작 컨트롤러 테스트 장면](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [혼합 현실 도구 키트-잡기 메커니즘](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [동작 컨트롤러 개발 지침](motion-controllers.md)
