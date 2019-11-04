---
title: MR 기본 사항 101-장치를 사용 하 여 프로젝트 완료
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 Windows Mixed Reality의 기본 사항을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, HoloLens, 홀로그램, 아카데미, 자습서
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434712"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. HoloLens 2에 대 한 [새로운 일련의 자습서](mrlearning-base.md) 가 게시 되었습니다.

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>MR 기본 사항 101: 장치를 사용 하 여 프로젝트 완료

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

이 자습서에서는 [응시](gaze-and-commit.md), [제스처](gaze-and-commit.md#composite-gestures), [음성 입력](voice-input.md), [공간 음향](spatial-sound.md) 및 [공간 매핑을](spatial-mapping.md) 비롯 한 HoloLens의 핵심 Windows Mixed Reality 기능을 보여 주는 Unity에서 빌드된 전체 프로젝트를 안내 합니다. .

자습서를 완료 하는 데 약 1 시간이 소요 됩니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 기본 사항 101: 장치를 사용 하 여 프로젝트 완료</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 확인 사항

### <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.
* [개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
  * Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)를 사용 하세요.
  * Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)를 사용 하세요.
  * Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)를 사용 하세요.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다. 폴더 이름을 **종이 접기**로 유지 합니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)있습니다.

## <a name="chapter-1---holo-world"></a>1 장-"Holo" 세계

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

이 장에서는 첫 번째 Unity 프로젝트를 설정 하 고 빌드 및 배포 프로세스를 단계별로 진행 합니다.

### <a name="objectives"></a>목표

* Holographic 개발용 Unity를 설정 합니다.
* 홀로그램을 만듭니다.
* 만든 홀로그램을 확인 하세요.

### <a name="instructions"></a>지침

* Unity를 시작합니다.
* **열기**를 선택 합니다.
* 이전에 보관 하지 않은 **종이 접기** 폴더로 위치를 입력 합니다.
* **종이** 를 선택 하 고 **폴더 선택**을 클릭 합니다.
* **종이** 에는 장면이 포함 되지 않으므로 빈 기본 장면을 새 파일에 저장 / **파일** 을 사용 하 여 새 파일을 **저장 합니다**.
* 새 장면 **종이** 의 이름을로 하 고 **저장** 단추를 누릅니다.

#### <a name="setup-the-main-virtual-camera"></a>기본 가상 카메라 설정

* **계층 패널**에서 **주 카메라**를 선택 합니다.
* **Inspector** 의 변환 위치를 **0, 0, 0**으로 설정 합니다.
* **Clear Flags** 속성을 찾고 Dropdown을 **Skybox** 에서 **Solid color**로 변경 합니다.
* 배경색 선택을 열려면 **배경** 필드를 클릭 합니다.
* **R, G, B 및 A** 를 **0**으로 설정 합니다.

#### <a name="setup-the-scene"></a>장면 설정

* **계층 패널**에서 **만들기** 를 클릭 하 고 **빈 상태로 만들기**를 클릭 합니다.
* 새 **GameObject** 를 마우스 오른쪽 단추로 클릭 하 고 이름 바꾸기를 선택 합니다. GameObject의 이름을 **OrigamiCollection**로 바꿉니다.
* 프로젝트 패널의 **Holograms** 폴더에서 자산을 확장 하 고 Holograms를 선택 하거나 프로젝트 패널에서 Holograms 폴더를 두 번 클릭 합니다.
  * **스테이지** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.
  * **Sphere1** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.
  * **Sphere2** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.
* **계층 패널** 에서 **방향 광원** 개체를 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.
* **Holograms** 폴더에서 **조명을** **계층 패널**의 루트로 끕니다.
* **계층**에서 **OrigamiCollection**를 선택 합니다.
* **검사기**에서 변환 위치를 **0,-0.5, 2.0**로 설정 합니다.
* Holograms를 미리 보려면 Unity의 **재생** 단추를 누릅니다.
* 미리 보기 창에 종이 개체를 표시 해야 합니다.
* **재생** 을 두 번 눌러 미리 보기 모드를 중지 합니다.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Unity에서 Visual Studio로 프로젝트 내보내기

* Unity에서 **파일 > 빌드 설정**을 선택 합니다.
* **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.
* **SDK** 를 **Universal 10** 으로 설정 하 고 **빌드 형식을** **D3D**로 설정 합니다.
* **Unity C# 프로젝트**를 확인 합니다.
* 열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.
* **빌드**를 클릭합니다.
* 표시 되는 파일 탐색기 창에서 "App" 이라는 **새 폴더** 를 만듭니다.
* 단일 **앱 폴더**를 클릭 합니다.
* **폴더 선택**을 누릅니다.
* Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.
* **앱** 폴더를 엽니다.
* (두 번 클릭) **종이**를 엽니다.
* Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.
* 장치 단추 옆의 화살표를 클릭 하 고 **원격 컴퓨터** 를 선택 하 여 wi-fi를 통해 배포 합니다.
  * **주소** 를 HoloLens의 이름 또는 IP 주소로 설정 합니다. 장치 IP 주소를 알 수 없는 경우 **설정 > 네트워크 & 인터넷 > 고급 옵션** 을 확인 하거나 Cortana **"안녕하세요. 내 IP 주소는 무엇입니까?"** 를 확인 합니다.
  * HoloLens가 USB를 통해 연결 된 경우 **장치** 를 선택 하 여 usb를 통해 배포할 수 있습니다.
  * **인증 모드** 를 **유니버설**으로 설정 된 상태로 둡니다.
  * **선택** 을 클릭 합니다.

* **디버그 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다. 처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.

* 이제 종이 접기 프로젝트가 빌드하여 HoloLens에 배포 되 고 실행 됩니다.
* HoloLens에 배치 하 고 새 holograms를 확인 하세요.

## <a name="chapter-2---gaze"></a>2 장-응시

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

이 장에서는 holograms와 상호 작용 하는 세 가지 방법, 즉 [응시](gaze-and-commit.md)를 소개 하겠습니다.

### <a name="objectives"></a>목표

* 전 세계 잠긴 커서를 사용 하 여 응시를 시각화 합니다.

### <a name="instructions"></a>지침

* Unity 프로젝트로 돌아가서 빌드 설정 창이 열려 있으면 닫습니다.
* **프로젝트 패널**에서 **Holograms** 폴더를 선택 합니다.
* **커서** 개체를 루트 수준에서 **계층 패널로** 끕니다.
* **커서** 개체를 두 번 클릭 하면 자세히 살펴볼 수 있습니다.
* 프로젝트 패널에서 **Scripts** 폴더를 마우스 오른쪽 단추로 클릭 합니다.
* **만들기** 하위 메뉴를 클릭 합니다.
* **C# 스크립트**를 선택 합니다.
* 스크립트 이름을 **WorldCursor**로 합니다. 참고: 이름은 대/소문자를 구분 합니다. .Cs 확장명을 추가할 필요가 없습니다.
* **계층 패널**에서 **Cursor** 개체를 선택 합니다.
* **WorldCursor** 스크립트를 **검사기 패널로**끌어 놓습니다.
* **WorldCursor** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
* 이 코드를 복사 하 여 **WorldCursor.cs** 에 붙여넣고 **모두 저장**합니다.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* **빌드 설정 > 파일**에서 응용 프로그램을 다시 빌드합니다.
* 이전에 HoloLens에 배포 하는 데 사용한 Visual Studio 솔루션으로 돌아갑니다.
* 메시지가 표시 되 면 ' 모두 다시 로드 '를 선택 합니다.
* **디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.
* 이제 장면을 살펴보고 커서가 개체 모양과 상호 작용 하는 방식을 확인 합니다.

## <a name="chapter-3---gestures"></a>3 장-제스처

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

이 장에서는 [제스처](gaze-and-commit.md#composite-gestures)에 대 한 지원을 추가 합니다. 사용자가 용지 구를 선택 하면 Unity의 물리학 엔진을 사용 하 여 무게를 설정 하 여 구를 설정 합니다.

### <a name="objectives"></a>목표

* 선택 제스처를 사용 하 여 holograms를 제어 합니다.

### <a name="instructions"></a>지침

먼저 스크립트를 만든 다음 선택 제스처를 검색할 수 있습니다.

* **Scripts** 폴더에서 **GazeGestureManager**라는 스크립트를 만듭니다.
* **GazeGestureManager** 스크립트를 계층의 **OrigamiCollection** 개체로 끌어 옵니다.
* Visual Studio에서 **GazeGestureManager** 스크립트를 열고 다음 코드를 추가 합니다.

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Scripts 폴더에 **SphereCommands**이라는 다른 스크립트를 만듭니다.
* 계층 구조 뷰에서 **OrigamiCollection** 개체를 확장 합니다.
* **SphereCommands** 스크립트를 계층 패널의 **Sphere1** 개체로 끌어 옵니다.
* **SphereCommands** 스크립트를 계층 패널의 **Sphere2** 개체로 끌어 옵니다.
* 편집을 위해 Visual Studio에서 스크립트를 열고 기본 코드를 다음으로 바꿉니다.

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* 앱을 내보내고, 빌드하여 HoloLens에 배포 합니다.
* 구 중 하나를 확인 합니다.
* 선택 제스처를 수행 하 고 아래 화면에 대 한 구 드롭다운을 시청 합니다.

## <a name="chapter-4---voice"></a>4 장-음성

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

이 장에서는 두 개의 [음성 명령](voice-input.md)에 대 한 지원을 추가 합니다. "다시 설정"은 삭제 된 구를 원래 위치로 반환 하 고, "삭제 구"는 구가 되도록 합니다.

### <a name="objectives"></a>목표

* 백그라운드에서 항상 수신 대기 하는 음성 명령을 추가 합니다.
* 음성 명령에 반응 하는 홀로그램을 만듭니다.

### <a name="instructions"></a>지침

* **Scripts** 폴더에서 **SpeechManager**라는 스크립트를 만듭니다.
* **SpeechManager** 스크립트를 계층의 **OrigamiCollection** 개체로 끌어 옵니다.
* Visual Studio에서 **SpeechManager** 스크립트를 엽니다.
* 이 코드를 복사 하 여 **SpeechManager.cs** 에 붙여넣고 **모두 저장**합니다.

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Visual Studio에서 **SphereCommands** 스크립트를 엽니다.
* 다음과 같이 스크립트를 업데이트 합니다.

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* 앱을 내보내고, 빌드하여 HoloLens에 배포 합니다.
* 구 중 하나를 확인 하 고 "**삭제 구**" 라고 표시 합니다.
* 초기 위치로 다시 전환 하기 위해 "**세계 재설정**" 이라고 말할 수 있습니다.

## <a name="chapter-5---spatial-sound"></a>5 장-공간 소리

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

이 장에서는 앱에 음악을 추가한 다음 특정 작업에 대 한 음향 효과를 트리거합니다. 3D 공간에서 소리를 특정 위치에 제공 하기 위해 [공간 소리](spatial-sound.md) 를 사용할 예정입니다.

### <a name="objectives"></a>목표

* 전 세계에서 holograms를 들어봅니다.

### <a name="instructions"></a>지침

* Unity의 상단 메뉴에서 선택 **> 프로젝트 설정 > 오디오를 편집** 합니다.
* 오른쪽의 검사기 패널에서 **Spatializer 플러그 인** 설정을 찾아 **MS hrtf Spatializer**를 선택 합니다.
* 프로젝트 패널의 **Holograms** 폴더에서 **외계** 개체를 계층 패널의 **OrigamiCollection** 개체로 끌어옵니다.
* **OrigamiCollection** 를 선택 하 고 검사기 패널에서 **오디오 원본** 구성 요소를 찾습니다. 다음 속성을 변경 합니다.
  * **Spatialize** 속성을 확인 합니다.
  * 절전 모드 **해제를 확인 합니다.**
  * 슬라이더를 오른쪽으로 끌어 **공간 Blend** 를 **3d** 로 변경 합니다. 슬라이더를 이동 하는 경우 값은 0에서 1로 변경 됩니다.
  * **Loop** 속성을 선택 합니다.
  * **3D 소리 설정**을 확장 하 고 **Doppler 수준**에 대해 **0.1** 을 입력 합니다.
  * **볼륨 Rolloff** 를 **로그 Rolloff**로 설정 합니다.
  * **최대 거리** 를 **20**으로 설정 합니다.
* **Scripts** 폴더에서 **SphereSounds**라는 스크립트를 만듭니다.
* **SphereSounds** 를 계층의 **Sphere1** 및 **Sphere2** 개체로 끌어서 놓습니다.
* Visual Studio에서 **SphereSounds** 를 열고 다음 코드를 업데이트 하 고 **모두 저장**합니다.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* 스크립트를 저장 하 고 Unity로 돌아갑니다.
* 앱을 내보내고, 빌드하여 HoloLens에 배포 합니다.
* 스테이지에서 가깝게 이동 하 여 다른 쪽으로 이동 하 여 소리 변경을 기다립니다.

## <a name="chapter-6---spatial-mapping"></a>6 장-공간 매핑

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

이제 [공간 매핑을](spatial-mapping.md) 사용 하 여 실제 개체에 게임 보드를 추가 하겠습니다.

### <a name="objectives"></a>목표

* 실제 세계를 가상 세계에 가져오세요.
* 가장 중요 한 위치에 holograms을 두십시오.

### <a name="instructions"></a>지침

* Unity의 프로젝트 패널에서 **Holograms** 폴더를 클릭 합니다.
* **공간 매핑** 자산을 **계층**의 루트로 끌어 옵니다.
* 계층에서 **공간 매핑** 개체를 클릭 합니다.
* **검사기 패널**에서 다음 속성을 변경 합니다.
  * **시각적 개체 메시 그리기** 상자를 선택 합니다.
  * **그리기 자료** 를 찾고 오른쪽에 있는 원을 클릭 합니다. 위쪽의 검색 필드에 "**골격형**"을 입력 합니다. 결과를 클릭 한 다음 창을 닫습니다. 이렇게 하면 재질 그리기 값이 와이어 프레임으로 설정 됩니다.
* 앱을 내보내고, 빌드하여 HoloLens에 배포 합니다.
* 앱이 실행 되 면 와이어 프레임 메쉬가 실제 세계를 오버레이 합니다.
* 롤링 구가 단계를 어떻게 진행 하는지 확인 합니다.

이제 OrigamiCollection를 새 위치로 이동 하는 방법을 보여 드리겠습니다.

* **Scripts** 폴더에서 **TapToPlaceParent**라는 스크립트를 만듭니다.
* **계층**에서 **OrigamiCollection** 를 확장 하 고 **단계** 개체를 선택 합니다.
* **TapToPlaceParent** 스크립트를 Stage 개체로 끌어 놓습니다.
* Visual Studio에서 **TapToPlaceParent** 스크립트를 열고 다음으로 업데이트 합니다.

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* 앱을 내보내고 빌드하고 배포 합니다.
* 이제 gazing을 사용 하 고, 선택 제스처를 사용 하 고, 새 위치로 이동 하 고, 선택 제스처를 다시 사용 하 여 특정 위치에 게임을 삽입할 수 있습니다.

## <a name="chapter-7---holographic-fun"></a>7 장-Holographic 재미

### <a name="objectives"></a>목표

* Holographic 지 수에 대 한 입구를 표시 합니다.

### <a name="instructions"></a>지침

이제 holographic 지 수를 파악 하는 방법을 보여 드리겠습니다.

* 프로젝트 패널의 **Holograms** 폴더에서 다음을 수행 합니다.
  * 지 **수를 계층으로 끌어** **OrigamiCollection**의 자식으로 만듭니다.
* **Scripts** 폴더에서 **HitTarget**라는 스크립트를 만듭니다.
* **계층**에서 **OrigamiCollection**를 확장 합니다.
* **스테이지** 개체를 확장 하 고 **대상** 개체 (파란색 팬)를 선택 합니다.
* **HitTarget** 스크립트를 **대상** 개체로 끌어 옵니다.
* Visual Studio에서 **HitTarget** 스크립트를 열고 다음으로 업데이트 합니다.

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* Unity에서 **대상** 개체를 선택 합니다.
* 이제 **적중 대상** 구성 요소에서 두 개의 공용 속성이 표시 되 고 장면에서 개체를 참조 해야 합니다.
  * 계층 **패널의** 지 **속성을** **적중 대상** 구성 요소의 지 속성 속성으로 끌어 옵니다.
  * **단계** 를 **계층** 패널에서 개체로 끌어 **적중 대상** 구성 요소의 속성을 **숨깁니다** .
* 앱을 내보내고 빌드하고 배포 합니다.
* 바닥에 종이를 놓고 선택 제스처를 사용 하 여 구를 끌어 놓습니다.
* 구가 대상 (파란색 팬)에 도달 하면 폭발이 발생 합니다. 컬렉션이 숨겨지고 지 수에 대 한 구멍이 표시 됩니다.

## <a name="the-end"></a>끝

이 자습서의 끝입니다!

배운 내용:

* Unity에서 holographic 앱을 만드는 방법
* 응시, 제스처, 음성, 소리 및 공간 매핑을 활용 하는 방법입니다.
* Visual Studio를 사용 하 여 앱을 빌드하고 배포 하는 방법입니다.

이제 사용자 고유의 holographic 환경을 만들 준비가 되었습니다!

## <a name="see-also"></a>참고 항목

* [MR 기본 사항 101E: 에뮬레이터를 사용 하 여 프로젝트 완료](holograms-101e.md)
* [응시](gaze-and-commit.md)
* [헤드 게이즈 및 커밋](gaze-and-commit.md)
* [음성 입력 ](voice-input.md)
* [공간 음향](spatial-sound.md)
* [공간 매핑](spatial-mapping.md)
