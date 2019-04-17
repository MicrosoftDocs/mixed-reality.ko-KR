---
title: MR 입력 213
description: Unity에서 Visual Studio 및 몰입 형 헤드셋을 사용 하 여 컨트롤러 동작의 세부 정보를 알아보려면이 코딩 자습서를 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, 컨트롤러, academy 자습서 mixedrealitytoolkit-unity 몰입 형, 동작
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604702"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-input-213-motion-controllers"></a>MR 입력 213: 컨트롤러 동작

혼합된 현실 세계에서 동작 컨트롤러 다른 수준의 상호 작용을 추가합니다. 사용 하 여 [컨트롤러 동작](motion-controllers.md), 직접 집중 교육을 늘리면 더 자연 스러운 방식으로 실제 상황에서는 실제 조작 비슷합니다 개체 상호 작용 하 고 앱 환경을 근원 수 있습니다.

MR 입력 213에서 동작 컨트롤러의 입력된 이벤트를 단순 공간 그리기 환경을 만들어 살펴봅니다. 이 앱을 사용 하 여 사용자는 다양 한 유형의 브러시 및 색을 사용 하 여 3 차원 공간에서 그릴 수 있습니다.

## <a name="topics-covered-in-this-tutorial"></a>이 자습서에서 다루는 항목

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**컨트롤러 시각화**|**컨트롤러 입력된 이벤트**|**사용자 지정 컨트롤러 및 UI**|
|Unity 게임 모드 및 런타임의 동작 컨트롤러 모델을 렌더링 하는 방법을 알아봅니다.|다양 한 유형의 단추 이벤트 및 해당 응용 프로그램을 이해 합니다.|컨트롤러를 기반으로 UI 요소를 오버레이 하거나 완전히 사용자 지정 하는 방법에 알아봅니다.|

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 213: 컨트롤러 동작</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

몰입 형 헤드셋 설치 검사 목록에 표시 [이 페이지](install-the-tools.md)합니다.

* 이 자습서에서는 [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>프로젝트 파일

* [파일을 다운로드할](https://github.com/Microsoft/MixedReality213/archive/master.zip) 프로젝트에 필요한 및 바탕 화면에 압축을 풉니다.

>[!NOTE]
>을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/MixedReality213)합니다.

## <a name="unity-setup"></a>Unity 설치

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>목표

* Unity에 대 한 Windows Mixed Reality 개발 최적화
* 혼합된 현실 카메라 설정
* 환경 설정

### <a name="instructions"></a>지침

* Unity를 시작 합니다.
* 선택 **열려**합니다.
* 찾기 바탕 화면으로 이동 합니다 **MixedReality213 마스터** 하면 이전에 보관 되지 않은 폴더입니다.
* **폴더 선택**을 클릭합니다.
* Unity 프로젝트 파일 로드 완료 되 면 Unity 편집기 수 있습니다.
* Unity에서 선택 **파일 > 빌드 설정**합니다.

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* 선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 나열 하 고 클릭 합니다 **플랫폼 전환** 단추입니다.
* 대상 장치를 설정 **모든 장치**
* 빌드 형식으로 **D3D**
* SDK로 **가장 최근에 설치 된**
* 확인할 **Unity C# 프로젝트**
    * 이렇게 하면 Unity 프로젝트를 다시 작성 하지 않고 Visual Studio 프로젝트에서 스크립트 파일을 수정할 수 있습니다.
* 클릭 **플레이어 설정**합니다.
* 에 **검사기** 패널 맨 아래로 스크롤
* Xr 하이 설정에서 확인 **가상 현실 지원**
* 가상 현실 Sdk 선택 **Windows Mixed Reality**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* 닫기 **빌드 설정** 창입니다.

### <a name="project-structure"></a>프로젝트 구조

이 자습서에서는  **[혼합 현실 Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 합니다. 릴리스를 찾을 수 있습니다 [이 페이지](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)합니다.

![ProjectStructure](images/mr213-projectstructure-650px.png)

**참조에 대 한 완료 된 장면**
* 완료 하는 두 Unity 장면에서 찾을 수 있습니다 **장면** 폴더입니다.
    * **MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면
    * **MixedReality213Advanced**: 여러 브러시를 사용 하 여 고급 디자인에 대 한 장면 완료

**이 자습서에 대 한 새 장면 설치**
* Unity에서 클릭 **파일 > 새 장면**
* 삭제할 **주 카메라** 고 **Directional Light**
* **프로젝트 패널**를 검색 하 고 끌어에 다음 prefabs 합니다 **계층** 패널:
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/**Environment**

![카메라 및 환경](images/mr213-cameraenvironment-300px.jpg)
* 혼합 현실 도구 키트의 카메라 prefabs 두 가지가 있습니다.
    * **MixedRealityCamera.prefab**: 카메라만
    * **MixedRealityCameraParent.prefab**: 카메라 + 텔레포트 경계
    * 이 자습서에서는 사용할지 **MixedRealityCamera** 텔레포트 기능 없이 합니다. 이 인해 간단한 추가한 **환경** prefab 접지 느낌 사용자 기본 floor를 포함 하는 합니다.
    * 사용 하 여 텔레포트에 자세히 알아보려면 **MixedRealityCameraParent**를 참조 하세요 [텔레포트 및 locomotion 디자인-고급](#advanced-design---teleportation-and-locomotion)

**Skybox 설치**
* 클릭 **창 > 조명 > 설정**
* 오른쪽에 원을 클릭을 **Skybox 자료 필드**
* '회색' 입력 하 고 선택 **SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![Skybox를 설정합니다.](images/mr123-skyboxsetting-400px.jpg)
* 확인할 **Skybox** 옵션을 볼 수 회색 그라데이션 skybox 할당

![설정/해제 skybox 옵션](images/mr213-skyboxcheck-400px.jpg)
* MixedRealityCamera, 환경 및 회색 skybox를 사용 하 여 장면 다음과 같이 표시 됩니다.

![MixedReality213 환경](images/mr213-environment-600px.jpg)
* 클릭 **파일 >으로 장면 저장**
* **저장** 장면 폴더 이름으로 장면

## <a name="chapter-1---controller-visualization"></a>1 장-컨트롤러 시각화

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>목표

* 컨트롤러 모델 Unity 게임 모드와 런타임 동작을 렌더링 하는 방법을 알아봅니다.

Windows Mixed Reality 컨트롤러 시각화에는 애니메이션된 컨트롤러 모델을 제공합니다. 앱에서 컨트롤러 시각화에 대해 수행할 수 있는 몇 가지가 있습니다.
* 기본값-수정 하지 않고 기본 컨트롤러를 사용 하 여
* 하이브리드-기본 컨트롤러를 사용 하 여 있지만 해당 요소 중 일부를 사용자 지정 또는 UI 구성 요소를 오버레이
* 대체-자체를 사용 하 여 컨트롤러에 대 한 3D 모델을 사용자 지정

이 챕터에서는 이러한 컨트롤러 사용자 지정의 예에 대 한 배웁니다.

### <a name="instructions"></a>지침

* 에 **프로젝트** 패널에서 입력 **MotionControllers** 검색 상자에 있습니다. 자산/HoloToolkit/입력/Prefabs 아래에서 찾을 수 있습니다/입니다.
* 끌어서 합니다 **MotionControllers** 으로 prefab 합니다 **계층** 패널.
* 클릭 합니다 **MotionControllers** 의 prefab 합니다 **계층** 패널.

**MotionControllers prefab**

**MotionControllers** prefab에는 **MotionControllerVisualizer** 대체 컨트롤러 모델에 대 한 슬롯을 제공 하는 스크립트입니다. 손 모양 검 등 사용자 고유의 사용자 지정 3D 모델을 할당 하 고 ' 항상 사용 하 여 대체 왼쪽/오른쪽 모델 '을 확인 하는 경우 기본 모델 대신 표시 됩니다. 이 슬롯 4 장의 컨트롤러 모델은 브러시를 바꾸려면 사용 합니다.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**지침**
* 에 **검사기** 패널에서 두 번 클릭 **MotionControllerVisualizer** Visual Studio의 코드를 참조 하는 스크립트

**MotionControllerVisualizer 스크립트**

합니다 **MotionControllerVisualizer** 하 고 **MotionControllerInfo** 클래스에 액세스 하는 기본 컨트롤러 모델을 수정할 수 있는 방법을 제공 합니다. **MotionControllerVisualizer** Unity의 구독할 **InteractionSourceDetected** 이벤트 및 파일이 있는 경우 컨트롤러 모델을 자동으로 인스턴스화합니다.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

컨트롤러 모델에 따라 전달할지 [glTF 사양](https://github.com/KhronosGroup/glTF)합니다. 전송 및 3D 자산을 압축 하는 프로세스를 개선 하는 동안 일반적인 형식으로 제공 형식이으로 작성 되었습니다. 이 경우 검색 하 여 사용자의 환경을 최대한 원활 하 게 확인 하려고 하 고 동작 컨트롤러 버전 사용자를 사용할 수 있습니다는 보장 되지 않습니다는 런타임 시 컨트롤러 모델을 로드 해야 합니다. 혼합 현실 도구 키트를 통해이 과정에서는 Khronos 그룹의 버전을 사용 하 여 [UnityGLTF 프로젝트](https://github.com/KhronosGroup/UnityGLTF)합니다.

컨트롤러를 전달한 후 스크립트 사용할 수 있습니다 **MotionControllerInfo** 를 특정 컨트롤러 요소에 대 한 변환의 찾을 자체 올바르게 배치할 수 있습니다.

뒷부분에 나오는 챕터에에서는 이러한 스크립트를 사용 하 여 컨트롤러에 UI 요소를 연결 하는 방법을 배웁니다.

*일부 스크립트를 사용 하 여 코드 블록을 찾을 수 있습니다 **#if! UNITY_EDITOR** 나 **UNITY_WSA**합니다. 이러한 코드 블록에 Windows를 배포할 때 UWP 런타임 에서만 실행 됩니다. Unity 편집기 및 UWP 앱 런타임에서 사용 되는 Api 집합은 다른 때문입니다.*
* **저장할** 장면과 클릭 합니다 **재생** 단추입니다.

헤드셋에서 동작 컨트롤러를 사용 하 여 장면의 참조 할 수 있습니다. 단추 클릭, 엄지 스틱 이동 및 터치 패드 터치 강조 표시에 대 한 자세한 애니메이션을 볼 수 있습니다.

![MR213_Controller 시각화 기본](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>2 장-UI 요소는 컨트롤러에 연결

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>목표

* 동작 컨트롤러의 요소에 알아봅니다
* 컨트롤러의 특정 부분에 개체를 연결 하는 방법에 알아봅니다.

이 챕터에서는 사용자 수 쉽게 액세스 하 고 언제 든 지에 조작 하는 컨트롤러에 사용자 인터페이스 요소를 추가 하는 방법을 배웁니다. 단순한 색 선택기 입력 터치 패드를 사용 하 여 UI를 추가 하는 방법 또한 배웁니다.

### <a name="instructions"></a>지침

* 에 **프로젝트** 패널에서 검색할 **MotionControllerInfo** 스크립트입니다.
* 검색 결과에서 두 번 클릭 **MotionControllerInfo** 스크립트를 Visual Studio에서 코드를 참조 하세요.

**MotionControllerInfo 스크립트**

첫 번째 단계 UI에 연결 하려는 컨트롤러의 요소를 선택 하는 것입니다. 이러한 요소에 정의 된 **ControllerElementEnum** 에 **MotionControllerInfo.cs**합니다.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **홈**
* **메뉴**
* **이해**
* **Thumbstick**
* **Select**
* **터치패드**
* **포인팅 포즈** –이 요소 끝을 가리키는 정방향 컨트롤러를 나타냅니다.

**지침**
* 에 **프로젝트** 패널에서 검색할 **AttachToController** 스크립트입니다.
* 검색 결과에서 두 번 클릭 **AttachToController** 스크립트를 Visual Studio에서 코드를 참조 하세요.

**AttachToController 스크립트**

합니다 **AttachToController** 스크립트는 모든 개체 요소를 사용 하는 손 지정 된 컨트롤러를 연결 하는 간단한 방법을 제공 합니다.

In **AttachElementToController()**,
* 선호도 사용 하 여 확인 **MotionControllerInfo.Handedness**
* 사용 하 여 컨트롤러의 특정 요소를 가져옵니다 **MotionControllerInfo.TryGetElement()**
* 요소를 검색 한 후 컨트롤러 모델 부모 아래에 있는 해당 개체에서에서 변환 하 고 개체의 로컬 위치 및 회전을 0으로 설정 합니다.

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

사용 하는 가장 간단한 방법은 **AttachToController** 의 경우 처럼 스크립트에서 상속 하는 **ColorPickerWheel 합니다.** 재정의 하기만 합니다 **OnAttachToController** 및 **OnDetatchFromController** 설치를 수행 하기 위해 함수 / 컨트롤러 감지 되거나 연결이 끊어진 경우 분석 합니다.

**지침**
* 에 **프로젝트** 패널에서 검색 상자에 입력 **ColorPickerWheel**합니다. 자산/AppPrefabs 아래에서 찾을 수 있습니다/입니다.
* 끌기 **ColorPickerWheel** 으로 prefab 합니다 **계층** 패널입니다.
* 클릭 합니다 **ColorPickerWheel** 의 prefab 합니다 **계층** 패널.
* 에 **검사기** 패널에서 두 번 클릭 **ColorPickerWheel** 스크립트를 Visual Studio에서 코드를 참조 하세요.

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel 스크립트**

이후 **ColorPickerWheel** 상속 **AttachToController**를 보여 줍니다 **선호도** 및 **요소** 에  **검사기** 패널입니다. 왼쪽된 컨트롤러에서 터치 패드 요소에 UI 연결에서는 했습니다.

![ColorPickerWheel 스크립트](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** 재정의 된 **OnAttachToController** 하 고 **OnDetatchFromController** 색 선택 영역에 대 한 다음 챕터에서 사용할 입력된 이벤트를 구독할 수 터치 패드를 입력 합니다.

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
* **저장할** 장면과 클릭 합니다 **재생** 단추입니다.

**컨트롤러에 개체를 연결 하는 것에 대 한 대체 메서드**

스크립트에서 상속 하는 것이 좋습니다 **AttachToController** 시키고 **OnAttachToController**합니다. 그러나이 항상 못할 합니다. 대신 독립 실행형 구성 요소로 사용 됩니다. 이 스크립트를 리팩터링 하지 않고는 기존 prefab 컨트롤러에 연결 하려는 경우 유용할 수 있습니다. IsAttached 하도록 설정할 때까지 기다리는 클래스 하기만 설정을 수행 하기 전에 true입니다. 이 작업을 수행 하는 가장 간단한 방법은 코 루틴을 사용 하 여 '시작 합니다.'가

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>3 장-터치 입력을 사용 하 여 작업

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>목표

* 터치 패드 입력된 데이터 이벤트를 받는 방법
* 앱 환경에 대 한 터치 패드 축 위치 정보를 사용 하는 방법 알아보기

### <a name="instructions"></a>지침

* 에 **계층 구조** 패널에서 **ColorPickerWheel**
* 에 **검사기** 패널의 **Animatior**를 두 번 클릭 **ColorPickerWheelController**
* 볼 수 있습니다 **애니메이터** 열린 탭

**Unity의 애니메이션 컨트롤러를 사용 하 여 UI 표시/숨기기**

표시 하거나 숨기려면 합니다 **ColorPickerWheel** 애니메이션을 사용 하 여 UI를 사용 하 여 [Unity의 애니메이션 시스템](https://docs.unity3d.com/Manual/AnimationOverview.html)입니다. 설정 합니다 **ColorPickerWheel**의 **Visible** 속성을 true 또는 false 트리거 **표시** 하 고 **숨기기** 애니메이션 트리거. **표시** 하 고 **숨기기** 에 정의 된 매개 변수를 **ColorPickerWheelController** 애니메이션 컨트롤러입니다.

![Unity 애니메이션 컨트롤러](images/mr123-animationcontroller-550px.jpg)

**지침**
* 에 **계층 구조** 패널에서 **ColorPickerWheel** prefab
* 에 **검사기** 패널에서 두 번 클릭 **ColorPickerWheel** Visual Studio의 코드를 참조 하는 스크립트

**ColorPickerWheel 스크립트**

**ColorPickerWheel** Unity의 구독할 **InteractionSourceUpdated** 터치 이벤트를 수신 대기 하는 이벤트입니다.

**InteractionSourceUpdated()**, 스크립트는 먼저 확인 하는지 확인 해야 합니다.
* 터치 패드 이벤트 실제로 (obj.state. **touchpadTouched**)
* 왼쪽된 컨트롤러에서 시작 (obj.state.source. **사용 하는 손**)

둘 다 true 인 경우에 터치 패드 위치 (obj.state. **touchpadPosition**)에 할당 됩니다 **selectorPosition**합니다.

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

**update ()** 에 따라 **표시** 속성을 트리거하는 색 선택기의 애니메이터 구성 요소에서 표시 / 숨기기 애니메이션 트리거

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

**update ()** 하십시오 **selectorPosition** 광선을 그린 UV 위치를 반환 하는 색상표의 메시 collider에 캐스팅 하는 데 사용 됩니다. 이 위치 픽셀 좌표를 찾아 색 색상표의 질감의 값을 사용할 수 있습니다. 이 값은 다른 스크립트를 통해 액세스할 수 합니다 **SelectedColor** 속성입니다.

![색 선택기 휠 플레이어가](images/mr213-colorpickerwheel-raycast-700px.png)

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

* 사용자 지정 3D 모델을 사용 하 여 컨트롤러 모델을 재정의 하는 방법에 알아봅니다.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>지침

* 클릭 **MotionControllers** 에 **계층** 패널입니다.
* 오른쪽에 원을 클릭 합니다 **대체 오른쪽 컨트롤러** 필드입니다.
* 입력 **' BrushController**'를 prefab 결과에서 선택 합니다. 자산/AppPrefabs 아래에서 찾을 수 있습니다/**BrushController**합니다.
* 확인 **항상 대체 오른쪽 모델 사용**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

합니다 **BrushController** prefab에 포함 될 필요가 없습니다 합니다 **계층** 패널입니다. 그러나 하위 구성 요소를 확인 합니다.
* 에 **프로젝트** 패널에 입력 합니다 **BrushController** 끌어서 **BrushController** 으로 prefab 합니다 **계층** 패널.

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

찾을 수 있습니다 합니다 **팁** 구성 요소 **BrushController**합니다. 해당 변환 그리기 줄 시작/중지에 사용 됩니다.
* 삭제 된 **BrushController** 에서 합니다 **계층** 패널입니다.
* **저장할** 장면과 클릭 합니다 **재생** 단추입니다. 브러시 모델 오른쪽 동작 컨트롤러를 교체 했습니다. 참조 할 수 있습니다.

## <a name="chapter-5---painting-with-select-input"></a>5 장-선택 입력을 사용 하 여 그리기

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>목표

* 선택 단추 이벤트를 사용 하 여 시작 하 고 선 그리기를 중지 하는 방법 알아보기

### <a name="instructions"></a>지침

* 검색 **BrushController** 의 prefab 합니다 **프로젝트** 패널입니다.
* 에 **검사기** 패널에서 두 번 클릭 **BrushController** Visual Studio의 코드를 참조 하는 스크립트

**BrushController 스크립트**

**BrushController** InteractionManager의 구독할 **InteractionSourcePressed** 하 고 **InteractionSourceReleased** 이벤트입니다. 때 **InteractionSourcePressed** 이벤트는 트리거되지 브러시의 **그리기** 속성이 true는 경우 **InteractionSourceReleased** 이벤트가 트리거될 브러시의 **그리기** 속성이 false로 설정 됩니다.

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

하는 동안 **그릴** 로 설정 된 true 브러시에에서 생성 됩니다 포인트는 인스턴스화된 Unity **LineRenderer**합니다. 브러시의에이 prefab에 대 한 참조 유지 **스트로크 Prefab** 필드입니다.

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

색 선택기 휠 UI에서에서 현재 선택한 색을 사용 하도록 **BrushController** 에 대 한 참조가 있어야 합니다 **ColorPickerWheel** 개체입니다. 때문에 합니다 **BrushController** prefab 대체 컨트롤러로 런타임에 인스턴스화됩니다, 장면의 개체에 대 한 참조를 런타임에 설정 해야 합니다. 이 경우에 사용 하 여 **GameObject.FindObjectOfType** 찾으려고 합니다 **ColorPickerWheel**:

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
* **저장할** 장면과 클릭 합니다 **재생** 단추입니다. 선을 그리는 및 선택 단추를 사용 하 여 오른쪽 컨트롤러에서 페인트 하는 일을 할 수 있습니다.

## <a name="chapter-6---object-spawning-with-select-input"></a>-6 장 입력 Select를 사용 하 여 개체 생성

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>목표

* 선택 사용 방법 알아보기 단추 입력된 이벤트를 이해 하 고
* 개체를 인스턴스화하는 방법을 알아봅니다

### <a name="instructions"></a>지침

* 에 **프로젝트** 패널에서 입력 **ObjectSpawner** 검색 상자에 있습니다. 자산/AppPrefabs 아래에서 찾을 수 있습니다 /
* 끌어서 합니다 **ObjectSpawner** 으로 prefab 합니다 **계층** 패널.
* 클릭 **ObjectSpawner** 에 **계층** 패널입니다.
* **ObjectSpawner** 라는 필드가 **색 소스**합니다.
* **계층 구조** 패널에서 끌어 합니다 **ColorPickerWheel** 이 필드에 대 한 참조입니다.

![개체 Spawner 검사기](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* 클릭 합니다 **ObjectSpawner** 의 prefab 합니다 **계층** 패널.
* 에 **검사기** 패널에서 두 번 클릭 **ObjectSpawner** 스크립트를 Visual Studio에서 코드를 참조 하세요.

**ObjectSpawner 스크립트**

합니다 **ObjectSpawner** 공간으로 기본 메시 (큐브, 구, 실린더)의 복사본을 인스턴스화합니다. 경우는 **InteractionSourcePressed** 선호도 확인 하는 경우 검색 되는 **InteractionSourcePressType.Grasp** 하거나 **InteractionSourcePressType.Select** 이벤트입니다.

에 **이해** 이벤트 현재 메시 유형 (구, 큐브의 원기둥)의 인덱스를 1만 큼

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

에 대 한는 **선택** 이벤트의 **SpawnObject()**, 새 개체는 인스턴스화된, 부모가 및 전 세계에 출시 합니다.

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

합니다 **ObjectSpawner** 사용 하는 **ColorPickerWheel** 표시 개체의 재질의 색을 설정 하려면. 생성 된 개체는 해당 색을 유지 하므로이 자료의 인스턴스를 제공 됩니다.
* **저장할** 장면과 클릭 합니다 **재생** 단추입니다.

감각을 단추를 사용 하 여 개체를 변경 하 고 선택 단추를 사용 하 여 개체를 생성 하는 일을 할 수 있습니다.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>빌드 및 혼합 현실 포털에 앱 배포
* Unity에서 선택 **파일 > 빌드 설정**합니다.
* 클릭 **열려 장면 추가** 현재 장면에 추가 하는 **Scenes In Build**합니다.
* **빌드**를 클릭합니다.
* 만들기는 **새 폴더** 이름을 "App"입니다.
* 한 번 클릭 합니다 **앱** 폴더입니다.
* **폴더 선택**을 클릭합니다.
* Unity 완료 되 면 파일 탐색기 창이 나타납니다.
* 엽니다는 **앱** 폴더입니다.
* 두 번 클릭 **YourSceneName.sln** Visual Studio 솔루션 파일입니다.
* 에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **X64**합니다.
* 선택한 장치 단추 옆의 드롭다운 화살표를 클릭 **로컬 컴퓨터**합니다.
* 클릭 **디버그-> 디버깅 없이 시작** 누르거나 메뉴에서 **ctrl+f5**합니다.

이제 앱 작성 및 혼합 현실 포털에 설치 합니다. 혼합 현실 포털에서 시작 메뉴를 통해이 작업을 다시 시작할 수 있습니다.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>고급 디자인-방사형 레이아웃을 사용 하 여 브러시 도구

![MixedReality213 Main](images/mr213-main-600px.jpg)

이 챕터에서는 사용자 지정 브러시 도구 컬렉션을 사용 하 여 기본 동작 컨트롤러 모델을 대체 하는 방법을 배웁니다. 참조를 위해 완성 된 장면을 찾을 수 있습니다 **MixedReality213Advanced** 아래에서 **장면** 폴더입니다.

### <a name="instructions"></a>지침

* 에 **프로젝트** 패널에서 입력 **BrushSelector** 검색 상자에 있습니다. 자산/AppPrefabs 아래에서 찾을 수 있습니다 /
* 끌어서 합니다 **BrushSelector** 으로 prefab 합니다 **계층** 패널.
* 조직에 대 한 호출 빈 GameObject를 만듭니다 **브러시**
* prefabs 다음 끌어 합니다 **프로젝트** 에 패널 **브러시**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Assets/AppPrefabs/**Eraser**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Assets/AppPrefabs/**Pencil**

![브러시](images/mixedreality213-brushes-250px.png)
* 클릭 **MotionControllers** 의 prefab 합니다 **계층** 패널입니다.
* 에 **검사기** 패널에서 선택 취소 **항상 사용 하 여 대체 오른쪽 모델** 에 **동작 컨트롤러 시각화 도우미**
* 에 **계층 구조** 패널에서 **BrushSelector**
* **BrushSelector** 라는 필드가 **ColorPicker**
* **계층 구조** 패널에서 끌어 합니다 **ColorPickerWheel** 에 **ColorPicker** 필드에 **검사기** 패널.

![선택기 브러시 ColorPickerWheel 할당](images/mr213-brushselector-500px.jpg)
* 에 **계층** 패널의 **BrushSelector** prefab을 선택 합니다 **메뉴** 개체입니다.
* 에 **검사기** 패널의 합니다 **LineObjectCollection** 구성 요소를 엽니다는 **개체** 배열 드롭다운 합니다. 6 빈 슬롯을 볼 수 있습니다.
* **계층** 패널에서 각 아래 부모가 prefabs 끌어 합니다 **브러시** GameObject 순서에 관계 없이 이러한 슬롯으로 합니다. (프로젝트 폴더에 prefabs 없습니다 장면에서를 prefabs 끌어 온 있는지 확인 합니다.)

![브러시 선택기](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefab**

이후를 **BrushSelector** 상속 **AttachToController**를 보여 줍니다 **선호도** 및 **요소** 옵션에  **검사기** 패널입니다. 선택한 **오른쪽** 및 **내포할 가리키는** 브러시 도구 정방향으로 오른쪽 컨트롤러에 연결 합니다.

합니다 **BrushSelector** 두 유틸리티 사용:
* **타원**: 타원 도형 함께 공간에서 요소를 생성 하는 데 사용 합니다.
* **LineObjectCollection**: 모든 줄 클래스 (예: 타원)에 의해 생성 된 요소를 사용 하 여 개체를 배포 합니다. 새로운 사용 타원 모양 따라 여 브러시에 적용할입니다.

를 결합 하면 이러한 유틸리티 방사형 메뉴를 만드는 데 사용할 수 있습니다.

**LineObjectCollection 스크립트**

**LineObjectCollection** 크기, 위치 및 해당 선을 따라 배포 된 개체의 회전을 위한 컨트롤을 포함 합니다. 이것이 브러시 선택기와 같은 방사형 메뉴를 만드는 데 유용 합니다. 모양을 만들려면 브러시 확장 되는에서 선택한 가운데 위치에 접근 하는 대로 nothing 합니다 **ObjectScale** 가장자리 해제 테이퍼 센터에 대 한 최대치를 곡선입니다.

**BrushSelector 스크립트**

경우에 **BrushSelector**, 절차 애니메이션을 사용 하기로 결정 했습니다. 브러시 모델에서 타원에 배포 되는 먼저 합니다 **LineObjectCollection** 스크립트입니다. 그런 다음 각 브러시는 해당 위치에 따라 사용자의 직접 유지 관리에 대 한 해당 **DisplayMode** 선택에 따라 변경 하는 값입니다. 사용자가 브러시 중단 되는 브러시 위치 전환의 높은 확률으로 인해 방법을 절차적 방법과 선택 했습니다. Mecanim 애니메이션 중단을 정상적으로 처리할 수 있지만 간단한 Lerp 작업 보다 더 복잡할 수 있습니다.

**BrushSelector** 둘의 조합을 사용 합니다. 터치 패드 입력 감지 되 면 브러시 옵션 표시 됩니다 및 방사형 메뉴 따라 강화 합니다. (선택 된 내용이 있는지를 나타내는) 제한 시간 후 브러시 옵션 확장 아래로 마찬가지로 선택된 된 브러시를 종료 합니다.

**터치 입력을 시각화**

컨트롤러 모델에 완전히 대체 하는 경우에도 유용한 입력에 원래 모델 입력으로 표시할 수 있습니다. 이렇게 하면 실제로 사용자의 작업을 포함 합니다. 에 대 한 합니다 **BrushSelector** 입력을 받으면 터치 패드를 간단 하 게 표시 되도록 설정 하기로 결정 했습니다. 사용자 지정 자료를 사용 하 여 해당 자료를 교체 컨트롤러에서 터치 패드 요소를 검색 하 여 수행 했지만 다음 마지막 시간 터치 패드에 따라 해당 재질의 색 그라데이션을 적용 입력이 수신 됩니다.

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

**터치 입력을 사용 하 여 브러시 도구 선택**

브러시 선택기 터치 패드의 누름된 입력을 감지 하면 왼쪽 이나 오른쪽으로 것인지 확인에 입력 될 내용의 위치를 확인 합니다.

**SelectPressedAmount 사용 하 여 스트로크 두께**

대신 합니다 **InteractionSourcePressType.Select** 이벤트에는 **InteractionSourcePressed()** 를 통해 누름 양의 아날로그 가치를 얻을 수 **selectPressedAmount**. 이 값을 검색할 수 있습니다 **InteractionSourceUpdated()** 합니다.

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

**지우개** 는 특수 한 유형의 기본 재정의 하는 브러시 **브러시**의 **DrawOverTime()** 함수입니다. 그리기 참이 면이 지우개 모든 기존 브러시 스트로크를 사용 하 여 해당 팁과 교차 하는 경우를 확인 합니다. 이 경우 아래로 축소 됩니다 큐에 추가 되며 삭제.

## <a name="advanced-design---teleportation-and-locomotion"></a>고급 디자인-텔레포트 및 locomotion

장면 텔레포트 엄지 스틱을 사용 하 여를 사용 하 여 이동, 사용 하 여 사용자를 허용 하려는 경우 **MixedRealityCameraParent** of **MixedRealityCamera**합니다. 추가 해야 **InputManager** 하 고 **DefaultCusor**합니다. 이후 **MixedRealityCameraParent** 이미 포함 되어 **MotionControllers** 하 고 **경계** 으로 자식 구성 요소를 제거 해야 기존  **MotionControllers** 하 고 **환경** prefab 합니다.

### <a name="instructions"></a>지침

* 에 **계층 구조** 패널에서 삭제 **MixedRealityCamera**에 **환경** 및 **MotionControllers**
* **프로젝트 패널**를 검색 하 고 끌어에 다음 prefabs 합니다 **계층** 패널:
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

![혼합된 현실 카메라 부모](images/mr213-cameraparent-300px.png)
* 에 **계층 구조** 패널에서 **입력 관리자**
* 에 **검사기** 패널에서 아래로 스크롤하여 합니다 **간단한 단일 포인터 선택기** 섹션
* **계층 구조** 패널에서 끌어 **DefaultCursor** 에 **커서** 필드

![기본 커서를 할당합니다.](images/mr213-defaultcursor-500px.png)
* **저장할** 장면과 클릭 합니다 **재생** 단추입니다. 왼쪽/오른쪽 또는 텔레포트 회전 하려면 스틱을 사용할 수 없게 됩니다.

## <a name="the-end"></a>끝

및이 자습서의 끝입니다! 알아보았습니다.
* Unity의 게임 모드와 런타임 동작 컨트롤러 모델을 사용 하는 방법입니다.
* 다양 한 유형의 단추 이벤트 및 해당 응용 프로그램을 사용 하는 방법입니다.
* 컨트롤러를 기반으로 UI 요소를 오버레이 또는 완전히 사용자 지정 하는 방법.

이제 동작 컨트롤러를 사용 하 여 몰입 형 환경을 만들기 시작할 준비가 되었습니다!

## <a name="completed-scenes"></a>완료 된 장면

* Unity의 **프로젝트** 패널을 클릭 합니다 **장면** 폴더입니다.
* 두 가지 Unity sceens 보면 **MixedReality213** 하 고 **MixedReality213Advanced**합니다.
    * **MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면
    * **MixedReality213Advanced**: 선택 단추를 누릅니다 시간 예제를 사용 하 여 여러 브러시를 사용 하 여 완료 된 장면

## <a name="see-also"></a>참조

* [MR 입력 213 프로젝트 파일](https://github.com/Microsoft/MixedReality213)
* [혼합된 현실 Toolkit-장면 동작 컨트롤러 테스트](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [혼합된 현실 도구 키트-잡기 메커니즘](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [동작 컨트롤러 개발 지침](motion-controllers.md)
