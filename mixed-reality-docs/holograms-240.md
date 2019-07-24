---
title: MR 공유 240-여러 HoloLens 장치
description: Holograms를 공유 하는 방법에 대 한 자세한 내용은 Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 따르세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 공유, 네트워킹, 아카데미, 자습서
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522339"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR 공유 240: 여러 HoloLens 장치

Holograms는 공간에서 이동 하면서 전 세계에 남아 있습니다. HoloLens는 다양 한 [좌표계](coordinate-systems.md) 를 사용 하 여 개체의 위치와 방향을 추적 하는 방식으로 holograms을 유지 합니다. 이러한 좌표계를 장치 간에 공유할 때 공유 holographic 세계에 참여 하는 데 사용할 수 있는 공유 환경을 만들 수 있습니다.

이 자습서에서는 다음을 수행 합니다.

* 공유 환경의 네트워크를 설정 합니다.
* HoloLens 장치 간에 holograms을 공유 합니다.
* 공유 holographic 세계에서 다른 사람을 검색 하세요.
* 다른 플레이어를 대상으로 하 고 projectiles를 시작할 수 있는 공유 대화형 환경을 만듭니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 공유 240: 여러 HoloLens 장치</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 인터넷 액세스로 설치 된 올바른 [도구로](install-the-tools.md) 구성 된 WINDOWS 10 PC
* 개발용으로 두 개 이상의 HoloLens 장치를 [구성](using-visual-studio.md#enabling-developer-mode)했습니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
  * Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)를 사용 하세요.
  * Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)를 사용 하세요.
  * Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)를 사용 하세요.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다. 폴더 이름을 **SharedHolograms**로 유지 합니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)있습니다.

## <a name="chapter-1---holo-world"></a>1 장-Holo 세계

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

이 장에서는 첫 번째 Unity 프로젝트를 설정 하 고 빌드 및 배포 프로세스를 단계별로 진행 합니다.

### <a name="objectives"></a>목표

* Holographic apps를 개발 하는 Unity를 설정 합니다.
* 홀로그램을 확인 하세요.

### <a name="instructions"></a>지침

* Unity를 시작합니다.
* **열기**를 선택 합니다.
* 이전에 unarchived **SharedHolograms** 폴더로 위치를 입력 합니다.
* **프로젝트 이름** 을 선택 하 고 **폴더 선택**을 클릭 합니다.
* **계층**에서 **주 카메라** 를 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.
* HoloToolkit- **240/Prefabs/카메라** 폴더에서 **기본 카메라** prefab를 찾습니다.
* **주 카메라** 를 **계층**으로 끌어 놓습니다.
* **계층**에서 **만들기** 를 클릭 하 고 **빈 상태로 만들기**를 클릭 합니다.
* 새 **GameObject** 를 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 선택 합니다.
* GameObject의 이름을 **HologramCollection**로 바꿉니다.
* **계층**에서 **HologramCollection** 개체를 선택 합니다.
* **검사기** 에서 **변환 위치** 를로 설정 합니다. **.X 0, Y:-0.25, Z: 2**.
* **프로젝트 패널**의 **Holograms** 폴더에서 **EnergyHub** 자산을 찾습니다.
* **EnergyHub** 개체를 **프로젝트 패널** 에서 **계층** 으로 **HologramCollection의 자식**으로 끌어 놓습니다.
* **파일 > 다른 이름으로 장면 저장** ...을 선택 합니다.
* 장면 이름을 **SharedHolograms** 로 하 고 **저장**을 클릭 합니다.
* Holograms를 미리 보려면 Unity의 **재생** 단추를 누릅니다.
* **재생** 을 두 번 눌러 미리 보기 모드를 중지 합니다.

**Unity에서 Visual Studio로 프로젝트 내보내기**
* Unity에서 **파일 > 빌드 설정**을 선택 합니다.
* 열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.
* **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.
* **SDK** 를 **Universal 10**으로 설정 합니다.
* **대상 장치** 를 **HoloLens** 로 설정 하 고 **UWP 빌드 유형을** **D3D**로 설정 합니다.
* **Unity C# 프로젝트**를 확인 합니다.
* **빌드**를 클릭합니다.
* 표시 되는 파일 탐색기 창에서 "App" 이라는 **새 폴더** 를 만듭니다.
* 단일 **앱** 폴더를 클릭 합니다.
* **폴더 선택**을 누릅니다.
* Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.
* **앱** 폴더를 엽니다.
* **SharedHolograms** 를 열어 Visual Studio를 시작 합니다.
* Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.
* 로컬 컴퓨터 옆의 드롭다운 화살표를 클릭 하 고 **원격 장치**를 선택 합니다.
    * **주소** 를 HoloLens의 이름 또는 IP 주소로 설정 합니다. 장치 IP 주소를 알 수 없는 경우 **설정 > 네트워크 & 인터넷 > 고급 옵션** 을 확인 하거나 Cortana **"안녕하세요. 내 IP 주소는 무엇입니까?"** 를 확인 합니다.
    * **인증 모드** 를 **유니버설**으로 설정 된 상태로 둡니다.
    * **선택** 을 클릭 합니다.
* **디버그 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다. 처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device-hololens)으로 연결 해야 합니다.
* HoloLens에 배치 하 고 EnergyHub 홀로그램을 찾습니다.

## <a name="chapter-2---interaction"></a>2 장-상호 작용

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

이 장에서는 holograms와 상호 작용 합니다. 먼저, [응시](gaze.md)를 시각화 하는 커서를 추가 합니다. 그런 다음 [제스처](gestures.md) 를 추가 하 고 손을 사용 하 여 holograms을 공간에 넣습니다.

### <a name="objectives"></a>목표

* 응시 입력을 사용 하 여 커서를 제어 합니다.
* 제스처 입력을 사용 하 여 holograms와 상호 작용 합니다.

### <a name="instructions"></a>지침

**응시**
* **계층 패널** 에서 **HologramCollection** 개체를 선택 합니다.
* **검사기 패널** 에서 **구성 요소 추가** 단추를 클릭 합니다.
* 메뉴의 검색 상자에 **응시 관리자**를 입력 합니다. 검색 결과를 선택 합니다.
* **HoloToolkit-Sharing-240\Prefabs\Input** 폴더에서 **커서** 자산을 찾습니다.
* **커서** 자산을 **계층 구조**에 끌어다 놓습니다.

**지우는**
* **계층 패널** 에서 **HologramCollection** 개체를 선택 합니다.
* **구성 요소 추가** 를 클릭 하 고 검색 필드에 **제스처 관리자** 를 입력 합니다. 검색 결과를 선택 합니다.
* **계층 패널**에서 **HologramCollection**를 확장 합니다.
* 자식 **EnergyHub** 개체를 선택 합니다.
* **검사기 패널** 에서 **구성 요소 추가** 단추를 클릭 합니다.
* 메뉴에서 **홀로그램 배치**를 검색 상자에 입력 합니다. 검색 결과를 선택 합니다.
* **파일 > 장면 저장**을 선택 하 여 장면을 저장 합니다.

**배포 및 이용**
* 이전 장의 지침을 사용 하 여를 빌드하고 HoloLens에 배포 합니다.
* 앱이 HoloLens에서 시작 되 면 헤드를 이동 하 고 EnergyHub이 응시를 따라가는 방법을 확인 합니다.
* 홀로그램을 응시 할 때 커서가 어떻게 표시 되는지, 그리고 홀로그램에서 gazing 않을 때 점 빛의 변화를 확인 합니다.
* 비행기를 탭 하 여 홀로그램을 놓습니다. 지금은 프로젝트에서 홀로그램을 한 번만 추가할 수 있습니다 (다시 배포 다시 시도).

## <a name="chapter-3---shared-coordinates"></a>3 장-공유 좌표

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Holograms를 확인 하 고 상호 작용 하는 데 재미 있지만 더 살펴보겠습니다. 첫 번째 공유 환경을 설정 합니다. 즉, 모든 사람이 함께 볼 수 있습니다.

### <a name="objectives"></a>목표

* 공유 환경의 네트워크를 설정 합니다.
* 공통 참조 지점을 설정 합니다.
* 장치 간에 좌표계를 공유 합니다.
* 모든 사람이 동일한 홀로그램을 보게 됩니다.

>[!NOTE]
>공유 서버에 연결 하려면 앱에 대해 **Internetclientserver** 및 **PrivateNetworkClientServer** 기능을 선언 해야 합니다. 이 작업은 이미 Holograms 240에 있지만 사용자 고유의 프로젝트에 대해서는이를 염두에 두어야 합니다.
>1. Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.
>2. "Windows 스토어" 탭을 클릭 합니다.
>3. "게시 설정 > 기능" 섹션에서 **Internetclientserver** 기능 및 **PrivateNetworkClientServer** 기능을 확인 합니다.

### <a name="instructions"></a>지침

* **프로젝트 패널** 에서 **HoloToolkit-Sharing-240\Prefabs\Sharing** 폴더로 이동 합니다.
* **공유** Prefab을 **계층 패널로**끌어 놓습니다.

다음으로 공유 서비스를 시작 해야 합니다. 공유 환경에서 한 대의 **PC** 만이 단계를 수행 해야 합니다.
* Unity-위쪽 메뉴에서 **HoloToolkit-240 메뉴**를 선택 합니다.
* 드롭다운에서 **공유 서비스 시작** 항목을 선택 합니다.
* **개인 네트워크** 옵션을 선택 하 고 방화벽 프롬프트가 표시 되 면 **액세스 허용** 을 클릭 합니다.
* 공유 서비스 콘솔 창에 표시 된 IPv4 주소를 적어둡니다. 이는 서비스가 실행 되는 컴퓨터와 동일한 IP입니다.

공유 환경에 참여 하는 **모든 pc** 의 나머지 지침을 따릅니다.
* **계층**에서 **공유** 개체를 선택 합니다.
* **검사자**의 **공유 단계** 구성 요소에서 **서버 주소** 를 ' localhost '에서 SharingService를 실행 하는 컴퓨터의 IPv4 주소로 변경 합니다.
* **계층** 에서 **HologramCollection** 개체를 선택 합니다.
* **검사기** 에서 **구성 요소 추가** 단추를 클릭 합니다.
* 검색 상자에 **가져오기 내보내기 앵커 관리자**를 입력 합니다. 검색 결과를 선택 합니다.
* **프로젝트 패널** 에서 **Scripts** 폴더로 이동 합니다.
* **HologramPlacement** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Unity로 돌아가서 **계층 패널**에서 **HologramCollection** 를 선택 합니다.
* **검사기 패널** 에서 **구성 요소 추가** 단추를 클릭 합니다.
* 메뉴에서 **앱 상태 관리자**검색 상자에를 입력 합니다. 검색 결과를 선택 합니다.

**배포 및 이용**
* HoloLens 장치에 대 한 프로젝트를 빌드합니다.
* 첫 번째에 배포할 HoloLens를 하나 지정 합니다. EnergyHub을 시작 하기 전에 Anchor가 서비스에 업로드 될 때까지 기다려야 합니다 (30-60 초 정도 걸릴 수 있음). 업로드가 완료 될 때까지 탭 제스처는 무시 됩니다.
* EnergyHub가 배치 된 후에는 해당 위치가 서비스에 업로드 되 고 다른 모든 HoloLens 장치에 배포할 수 있습니다.
* 새 HoloLens가 먼저 세션에 조인 하면 해당 장치에서 EnergyHub 위치가 올바르지 않을 수 있습니다. 그러나 anchor 및 EnergyHub 위치가 서비스에서 다운로드 되는 즉시 EnergyHub는 새 공유 위치로 이동 해야 합니다. 이 문제가 ~ 30-60 초 이내에 발생 하지 않는 경우 더 많은 환경 단서를 수집 하도록 앵커를 설정 하는 경우 원래 HoloLens가 있었던 위치를 살펴보세요. 위치가 여전히 잠겨 있지 않으면 장치에 다시 배포 합니다.
* 장치를 모두 준비 하 고 앱을 실행 하는 경우 EnergyHub을 찾습니다. 홀로그램의 위치와 텍스트가 접하는 방향을 모두 동의할 수 있나요?

## <a name="chapter-4---discovery"></a>4 장-검색

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

이제 모든 사용자가 동일한 홀로그램을 볼 수 있습니다. 이제 shared holographic 세계에 연결 된 다른 모든 사용자를 확인해 보겠습니다. 이 장에서는 동일한 공유 세션에서 다른 모든 HoloLens 장치의 헤드 위치와 회전을 가져옵니다.

### <a name="objectives"></a>목표

* 공유 환경에서 서로를 검색 합니다.
* 플레이어 아바타를 선택 하 고 공유 합니다.
* 플레이어 아바타를 모든 사용자의 헤드 옆에 연결 합니다.

### <a name="instructions"></a>지침

* **프로젝트 패널** 에서 **Holograms** 폴더로 이동 합니다.
* **PlayerAvatarStore** 를 **계층**으로 끌어 놓습니다.
* **프로젝트 패널** 에서 **Scripts** 폴더로 이동 합니다.
* **AvatarSelector** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* **계층** 에서 **HologramCollection** 개체를 선택 합니다.
* **검사기** 에서 **구성 요소 추가**를 클릭 합니다.
* 검색 상자에 **로컬 플레이어 관리자**를 입력 합니다. 검색 결과를 선택 합니다.
* **계층** 에서 **HologramCollection** 개체를 선택 합니다.
* **검사기** 에서 **구성 요소 추가**를 클릭 합니다.
* 검색 상자에 **원격 플레이어 관리자**를 입력 합니다. 검색 결과를 선택 합니다.
* Visual Studio에서 **HologramPlacement** 스크립트를 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Visual Studio에서 **AppStateManager** 스크립트를 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**배포 및 이용**
* 프로젝트를 빌드하고 HoloLens 장치에 배포 합니다.
* Ping 소리가 들리면 아바타 선택 메뉴를 찾고 공중 탭 제스처를 사용 하 여 아바타를 선택 합니다.
* Holograms을 확인 하지 않는 경우 HoloLens가 서비스와 통신 하는 동안 커서 주위의 점 빛이 다른 색으로 전환 됩니다. 초기화 (진한 자주), 앵커 다운로드 (녹색), 위치 데이터 가져오기/내보내기 (노랑), 앵커 (파란색)를 업로드 합니다. 커서 주위의 점 조명이 기본 색 (연한 자주색) 이면 세션의 다른 플레이어와 상호 작용할 준비가 된 것입니다.
* 공간에 연결 된 다른 사용자를 살펴보세요. 어깨 위에 holographic 로봇이 떠 모방 해당 헤드 동작을 합니다.

## <a name="chapter-5---placement"></a>5 장-배치

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

이 장에서는 실제 세계 표면에 앵커를 배치할 수 있도록 합니다. 공유 좌표를 사용 하 여 공유 환경에 연결 된 모든 사람 사이에서 중간 지점에 해당 앵커를 추가 합니다.

### <a name="objectives"></a>목표

* 플레이어의 헤드 위치에 따라 공간 지도에 holograms을 배치 합니다.

### <a name="instructions"></a>지침

* **프로젝트 패널** 에서 **Holograms** 폴더로 이동 합니다.
* **CustomSpatialMapping** Prefab를 **계층 구조**에 끌어다 놓습니다.
* **프로젝트 패널** 에서 **Scripts** 폴더로 이동 합니다.
* **AppStateManager** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* **프로젝트 패널** 에서 **Scripts** 폴더로 이동 합니다.
* **HologramPlacement** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**배포 및 이용**
* 프로젝트를 빌드하고 HoloLens 장치에 배포 합니다.
* 앱이 준비 되 면 원 안에 표시 되 고 EnergyHub이 모든 사람의 중앙에 표시 되는 방식을 확인 합니다.
* 을 탭 하 여 EnergyHub을 놓습니다.
* 음성 명령 ' 다시 설정 대상 '을 사용 하 여 EnergyHub 백업을 선택 하 고 그룹으로 함께 작업 하 여 홀로그램을 새 위치로 이동 합니다.

## <a name="chapter-6---real-world-physics"></a>6 장-실제 세계 물리학

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

이 장에서는 실제 화면을 바운스 하는 holograms을 추가 합니다. 사용자와 친구 모두에 의해 시작 되는 프로젝트를 사용 하 여 공간을 채웁니다.

### <a name="objectives"></a>목표

* 실제 표면에서 바운스 된 projectiles를 시작 합니다.
* 다른 플레이어가 볼 수 있도록 projectiles을 공유 합니다.

### <a name="instructions"></a>지침

* **계층** 에서 **HologramCollection** 개체를 선택 합니다.
* **검사기** 에서 **구성 요소 추가**를 클릭 합니다.
* 검색 상자에 나이 **시작 관리자**를 입력 합니다. 검색 결과를 선택 합니다.

**배포 및 이용**
* HoloLens 장치를 빌드하고 배포 합니다.
* 앱이 모든 장치에서 실행 되는 경우에는 공기 탭을 수행 하 여 실제 화면에서 멀리 있는 게임을 시작 합니다.
* 멀리가 다른 플레이어의 아바타와 충돌 하는 경우 어떻게 되나요?를 참조 하세요.

## <a name="chapter-7---grand-finale"></a>7 장-그랜드 Finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

이 장에서는 공동 작업 에서만 검색할 수 있는 포털을 살펴봅니다.

### <a name="objectives"></a>목표

* 함께 작동 하 여 비밀 포털을 projectiles 앵커에서 충분 한를 시작 합니다.

### <a name="instructions"></a>지침

* **프로젝트 패널** 에서 **Holograms** 폴더로 이동 합니다.
* 지 **각 자산을** **HologramCollection의 자식**으로 끌어 놓습니다.
* **HologramCollection** 가 선택 된 상태에서 **검사기**의 **구성 요소 추가** 단추를 클릭 합니다.
* 메뉴의 검색 상자에 **ExplodeTarget**을 입력 합니다. 검색 결과를 선택 합니다.
* **HologramCollection** 를 선택 하면 **계층 구조** 에서 **EnergyHub** 개체를 **검사기**의 **대상** 필드로 끕니다.
* **HologramCollection** 를 선택 하면 **계층 구조** 에서 지 수 **개체를** **검사기**의 지 **수 필드로** 끕니다.

**배포 및 이용**
* HoloLens 장치를 빌드하고 배포 합니다.
* 앱이 시작 되 면 함께 공동 작업 하 여 EnergyHub에서 projectiles를 시작 합니다.
* 지가 표시 되 면 projectiles를 실행 합니다 (추가 재미를 위해 로봇이 세 번 적중).
