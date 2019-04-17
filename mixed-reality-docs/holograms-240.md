---
title: MR 240-여러 HoloLens 장치를 공유 합니다.
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 홀로그램을 공유 하는 자세한 연습을 코딩이 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, 공유, 네트워킹, academy, 자습서
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601390"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR 240을 공유 합니다. 여러 HoloLens 장치

홀로그램 위치에 남아 있는 공간에 대 한 이동 하 여 세계에 제공 됩니다. HoloLens 곳에서 다양 한를 사용 하 여 홀로그램을 유지 [좌표계](coordinate-systems.md) 를 추적할 위치와 개체의 방향입니다. 장치 간에 이러한 좌표계를 공유 하는 경우 공유 holographic 환경에 참여할 수 있게 하는 공유 환경을 만들 수 있습니다.

이 자습서를 수행합니다.

* 공유 경험에 대 한 네트워크를 설정 합니다.
* 홀로그램 HoloLens 장치 간에 공유 합니다.
* 공유 holographic 세계의 다른 사용자를 검색 합니다.
* 다른 플레이어-대상으로 하 고 있습니다 무기를 시작할 수 있는 공유 대화형 환경 만들기

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 240을 공유 합니다. 여러 HoloLens 장치</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md) 인터넷 액세스를 사용 하 여 합니다.
* 두 개 이상의 HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.

### <a name="project-files"></a>프로젝트 파일

* 다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) 프로젝트에서 필요 합니다. Unity 2017.2 이상이 필요합니다.
  * Unity 5.6 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)합니다.
  * Unity 5.5 지원 해야 하는 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)합니다.
  * Unity 5.4 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)합니다.
* 취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다. 폴더 이름을 변수로 유지 **SharedHolograms**합니다.

>[!NOTE]
>을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)합니다.

## <a name="chapter-1---holo-world"></a>1 장-Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

이 챕터에 첫 번째 Unity 프로젝트 및 빌드를 단계별로 설치 및 배포 프로세스에서는 했습니다.

### <a name="objectives"></a>목표

* Holographic 앱을 개발 하는 Unity를 설치 합니다.
* 프로그램 홀로그램을 확인 하세요.

### <a name="instructions"></a>지침

* Unity를 시작 합니다.
* 선택 **열려**합니다.
* 위치를 입력 합니다 **SharedHolograms** 하면 이전에 보관 되지 않은 폴더입니다.
* 선택 **프로젝트 이름** 누릅니다 **폴더 선택**합니다.
* 에 **계층**를 마우스 오른쪽 단추로 클릭 합니다 **주 카메라** 선택한 **삭제**.
* 에 **HoloToolkit 공유-240/Prefabs/카메라** 폴더를 찾을 합니다 **주 카메라** prefab 합니다.
* 끌어서 놓기 합니다 **주 카메라** 에 **계층**합니다.
* 에 **계층**, 클릭 **만들기** 하 고 **빈 항목 만들기**.
* 새을 마우스 오른쪽 단추로 클릭 **GameObject** 선택한 **이름 바꾸기**합니다.
* GameObject 이름 바꾸기 **HologramCollection**합니다.
* 선택 된 **HologramCollection** 개체를 **계층**합니다.
* 에 **검사기** 설정 합니다 **위치를 변환** 에: **X: 0, Y:-0.25, Z: 2**.
* 에 **홀로그램** 폴더에는 **프로젝트 패널**, 찾을 **EnergyHub** 자산입니다.
* 끌어서 놓기는 **EnergyHub** 에서 개체를 **프로젝트 패널** 에 **계층** 으로 **HologramCollection 자식의**.
* 선택 **파일 >으로 장면 저장...**
* 장면 이름을 **SharedHolograms** 누릅니다 **저장**합니다.
* 키를 눌러 합니다 **재생** 여 홀로그램 미리 보기에 Unity에서 단추입니다.
* 키를 눌러 **재생** 미리 보기 모드를 중지 됩니다.

**Visual studio에서 Unity 프로젝트 내보내기**
* Unity select에서 **파일 > 빌드 설정**합니다.
* 클릭 **열기 장면 추가** 장면에 추가 합니다.
* 선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 클릭 **플랫폼 전환**합니다.
* 설정할 **SDK** 하 **유니버설 10**합니다.
* 설정 **대상 장치** 하 **HoloLens** 하 고 **UWP 빌드 형식** 에 **D3D**합니다.
* 확인할 **Unity C# 프로젝트**합니다.
* **빌드**를 클릭합니다.
* 표시 되는 파일 탐색기 창에서 만들기를 **새 폴더** 이름을 "App"입니다.
* 한 번 클릭 합니다 **앱** 폴더입니다.
* 키를 눌러 **폴더 선택**합니다.
* Unity 완료 되 면 파일 탐색기 창이 나타납니다.
* 엽니다는 **앱** 폴더입니다.
* 오픈 **SharedHolograms.sln** Visual Studio를 시작 합니다.
* 에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **X86**합니다.
* 로컬 컴퓨터 옆에 있는 드롭다운 화살표를 클릭 하 고 선택 **원격 장치**합니다.
    * 설정 된 **주소** 이름 또는 IP 주소에 HoloLens 합니다. 장치 IP 주소를 모르는 경우 찾는 위치 **설정 > 네트워크 및 인터넷 > 고급 옵션** Cortana 요청 또는 **"Hey Cortana, 내 IP 주소는 무엇 인가요?"**
    * 유지 된 **인증 모드** 로 설정 **유니버설**합니다.
    * 클릭 **선택**
* 클릭 **디버그 > 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다. 처음으로 장치에 배포할 경우 해야 [Visual Studio를 사용 하 여 쌍](using-visual-studio.md#pairing-your-device-hololens)합니다.
* 에 HoloLens에 놓고 EnergyHub 홀로그램을 찾습니다.

## <a name="chapter-2---interaction"></a>2 장-상호 작용

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

이 장에서 홀로그램 상호 작용 합니다. 먼저 커서를 시각화에 추가한 우리의 [Gaze](gaze.md)합니다. 그런 다음 추가할 것 [제스처](gestures.md) 를 사용 하 여, 이제 직접 우리의 홀로그램 공간에 배치 합니다.

### <a name="objectives"></a>목표

* 커서를 제어 하려면 입력 게이즈를 사용 합니다.
* 홀로그램 상호 작용할 수 입력 제스처를 사용 합니다.

### <a name="instructions"></a>지침

**응시**
* 에 **계층 패널** 선택 합니다 **HologramCollection** 개체입니다.
* 에 **검사기 패널** 클릭 합니다 **구성 요소 추가** 단추입니다.
* 메뉴에서 검색 상자에 입력 **Gaze Manager**합니다. 검색 결과 선택 합니다.
* 에 **HoloToolkit 공유 240\Prefabs\Input** 폴더를 찾기는 **커서** 자산입니다.
* 끌어서 놓기 합니다 **커서** 자산에는 **계층**합니다.

**제스처**
* 에 **계층 패널** 선택 합니다 **HologramCollection** 개체입니다.
* 클릭 **Add Component** 유형과 **제스처 관리자** 검색 필드에 합니다. 검색 결과 선택 합니다.
* 에 **계층 패널**를 확장 하 고 **HologramCollection**합니다.
* 선택 된 자식 **EnergyHub** 개체입니다.
* 에 **검사기 패널** 클릭 합니다 **구성 요소 추가** 단추입니다.
* 메뉴에서 검색 상자에 입력 **홀로그램 배치**합니다. 검색 결과 선택 합니다.
* 선택 하 여 장면 저장 **파일 > 저장 장면**합니다.

**배포 하 고 이용할 수 있습니다**
* 빌드 및 이전 장에서 지침을 사용 하 여 HoloLens에 배포 합니다.
* 앱이 출시 되 면 여 HoloLens, 머리를 이동 하 고는 EnergyHub 프로그램 게이즈를 따라가는 방법을 확인 합니다.
* 커서를 홀로그램으로 gaze 때 표시 되 고를 홀로그램에서 gazing 되지 경우 점 광원으로 변경 하는 방법을 살펴보세요.
* 홀로그램 배치에 어 탭을 수행 합니다. 프로젝트에서이 이번에는 홀로그램 한 번 (다시 시도에 다시 배포)만 배치할 수 있습니다.

## <a name="chapter-3---shared-coordinates"></a>3 장-공유 조정

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

재미를 확인 하 여 홀로그램, 상호 작용 하지만 나아가 보겠습니다. 첫 번째 공유 경험-모든 사람이 함께 볼 수는 홀로그램 설정 됩니다.

### <a name="objectives"></a>목표

* 공유 경험에 대 한 네트워크를 설정 합니다.
* 공용 참조 지점을 설정 합니다.
* 장치의 좌표 시스템을 공유 합니다.
* 모든 사용자가 동일한 홀로그램 표시 됩니다.

>[!NOTE]
>합니다 **InternetClientServer** 하 고 **PrivateNetworkClientServer** 공유 서버에 연결 하는 앱에 대 한 기능을 선언 해야 합니다. 이루어지는를 이미 홀로그램 240 하지만이 사용자의 프로젝트에 대 한 염두에 둡니다.
>1. Unity 편집기에서 "> 프로젝트 설정 > Player 편집"로 이동 하 여 플레이어 설정으로 이동 합니다.
>2. "Windows Store" 탭을 클릭
>3. "게시 설정 > 기능" 섹션을 확인 합니다 **InternetClientServer** 기능 하며 **PrivateNetworkClientServer** 기능

### <a name="instructions"></a>지침

* 에 **프로젝트 패널** 로 이동 합니다 **HoloToolkit 공유 240\Prefabs\Sharing** 폴더입니다.
* 끌어서 놓기 합니다 **공유** 으로 prefab 합니다 **계층 패널**합니다.

다음 공유 서비스를 시작 해야 합니다. 만 **PC** 공유 환경이 단계를 수행 해야 합니다.
* Unity-는 위 메뉴에서 선택 합니다 **HoloToolkit 공유 240 메뉴**합니다.
* 선택 된 **공유 서비스 시작** 드롭다운 목록에서 항목입니다.
* 확인 합니다 **사설망** 옵션을 클릭 **액세스를 허용** 방화벽 프롬프트를 표시 하는 경우.
* 공유 서비스 콘솔 창에 표시 된 IPv4 주소를 적어 note 합니다. 서비스에서 실행 되는 컴퓨터와 동일한 IP입니다.

지침 따릅니다 **모든 Pc** 는 공유 환경에 연결 됩니다.
* 에 **계층**를 선택 합니다 **공유** 개체입니다.
* 에 **검사기**의 **공유 단계** 구성 요소를 변경 합니다 **서버 주소** 'localhost' SharingService.exe를 실행 하는 컴퓨터의 IPv4 주소에서.
* 에 **계층 구조** 선택 합니다 **HologramCollection** 개체입니다.
* 에 **검사기** 클릭 합니다 **구성 요소 추가** 단추입니다.
* 검색 상자에 입력 **가져오기 내보내기 앵커 Manager**합니다. 검색 결과 선택 합니다.
* 에 **프로젝트 패널** 로 이동 합니다 **스크립트** 폴더입니다.
* 두 번 클릭 합니다 **HologramPlacement** 스크립트 Visual Studio에서 엽니다.
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

* Unity에서 다시 선택 합니다 **HologramCollection** 에 **계층 패널**합니다.
* 에 **검사기 패널** 클릭 합니다 **구성 요소 추가** 단추입니다.
* 메뉴에서 검색 상자에 입력 **앱 상태 관리자**합니다. 검색 결과 선택 합니다.

**배포 하 고 이용할 수 있습니다**
* HoloLens 장치에 대 한 프로젝트를 빌드하십시오.
* 첫 번째를 배포 하려면 하나의 HoloLens를 지정 합니다. 앵커는 EnergyHub 저장 하기 전에 서비스에 업로드할 때까지 대기 해야 합니다 (정도 걸리며 ~ 30 ~ 60 초)입니다. 업로드가 완료 될 때까지 탭 제스처는 무시 됩니다.
* EnergyHub 배치 된 후 서비스에 업로드할 해당 위치 및 다른 모든 HoloLens 장치에 배포할 수 있습니다.
* 새 HoloLens 세션에 먼저 가입는 EnergyHub 위치의 해당 장치에서 올바르지 않을 수 있습니다. 그러나 앵커 및 EnergyHub 위치 서비스에서 다운로드 했거나, 즉시는 EnergyHub 새, 공유 위치로 이동 해야 합니다. 이 ~ 30 ~ 60 내에서 발생 하지 않습니다 하는 경우 시간 (초), 자세한 환경을 위한 정보 수집에 앵커를 설정할 때 원래 HoloLens가를 설명 합니다. 위치 잠그지 않습니다 하는 경우에 장치에 다시 배포 합니다.
* 경우 장치는 모두 준비 하 고 앱을 실행 합니다 EnergyHub 찾습니다. 홀로그램의 위치에 모두 동의할 수 방향을 텍스트 연결 및?

## <a name="chapter-4---discovery"></a>4 장-검색

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

이제 동일한 홀로그램을 볼 수 있습니다 everyone! 이제 공유 holographic 세계에 연결 된 다른 모든 사용자를 확인해 보겠습니다. 이 챕터에서는 헤드 위치와 같은 공유 세션에서 다른 모든 HoloLens 장치 회전을 잡고 됩니다 것입니다.

### <a name="objectives"></a>목표

* 공유 경험에서 서로 검색 합니다.
* 선택 하 고 플레이어 아바타를 공유 합니다.
* 모든 사용자의 헤드 옆에 있는 플레이어 아바타를 연결 합니다.

### <a name="instructions"></a>지침

* 에 **프로젝트 패널** 로 이동 합니다 **홀로그램** 폴더입니다.
* 끌어서 놓기 합니다 **PlayerAvatarStore** 에 **계층**합니다.
* 에 **프로젝트 패널** 로 이동 합니다 **스크립트** 폴더입니다.
* 두 번 클릭 합니다 **AvatarSelector** 스크립트 Visual Studio에서 엽니다.
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

* 에 **계층 구조** 선택 합니다 **HologramCollection** 개체입니다.
* 에 **검사기** 클릭 **구성 요소 추가**합니다.
* 검색 상자에 입력 **로컬 플레이어 관리자**합니다. 검색 결과 선택 합니다.
* 에 **계층 구조** 선택 합니다 **HologramCollection** 개체입니다.
* 에 **검사기** 클릭 **구성 요소 추가**합니다.
* 검색 상자에 입력 **원격 Player Manager**합니다. 검색 결과 선택 합니다.
* 엽니다는 **HologramPlacement** Visual Studio의 스크립트입니다.
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

* 엽니다는 **AppStateManager** Visual Studio의 스크립트입니다.
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

**배포 하 고 이용할 수 있습니다**
* 빌드 및 HoloLens 장치에 프로젝트를 배포 합니다.
* 대 한 ping 소리가 아바타 선택 메뉴을 어 탭 제스처를 사용 하 여 아바타를 선택 합니다.
* 모든 홀로그램을 확인 하지 하는 경우 커서 주위 밝은 지점 바뀝니다 다른 색에 HoloLens 서비스와 통신 하는 경우: 초기화 (진한 자주색), 위치 데이터 (노란색) 가져오기/내보내기 앵커 (녹색) 다운로드 앵커 (파란색)을 업로드 합니다. 커서 주위 밝은 지점과 기본 색 (옅은 자주) 인 경우 다음 준비가 세션에서 다른 플레이어와 상호 작용.
* 다른 사용자를 살펴보고 공간-에 연결 됩니다 해당 자격 증명 입력 위에 부동 및 해당 헤드 동작이 모방 holographic 로봇!

## <a name="chapter-5---placement"></a>5 장-배치

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

이 챕터에서는 실제 화면에 배치할 수 앵커를 만들 수 것입니다. 공유 좌표는 앵커 공유 환경에 연결 된 모든 사용자 사이의 중간 지점 전환 사용 하겠습니다.

### <a name="objectives"></a>목표

* 홀로그램 플레이어의 헤드 위치에 따라 공간 지도에 배치 합니다.

### <a name="instructions"></a>지침

* 에 **프로젝트 패널** 로 이동 합니다 **홀로그램** 폴더입니다.
* 끌어서 놓기는 **CustomSpatialMapping** 끌어다 prefab 합니다 **계층**.
* 에 **프로젝트 패널** 로 이동 합니다 **스크립트** 폴더입니다.
* 두 번 클릭 합니다 **AppStateManager** 스크립트 Visual Studio에서 엽니다.
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

* 에 **프로젝트 패널** 로 이동 합니다 **스크립트** 폴더입니다.
* 두 번 클릭 합니다 **HologramPlacement** 스크립트 Visual Studio에서 엽니다.
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

**배포 하 고 이용할 수 있습니다**
* 빌드 및 HoloLens 장치에 프로젝트를 배포 합니다.
* 앱 준비 되 면 원에 구축 하 고는 EnergyHub everyone의 가운데에 표시 되는 방식을 확인 합니다.
* EnergyHub 배치 하려면 탭 하세요.
* 홀로그램을 새 위치로 이동할 대상 재설정 '는 EnergyHub 다시 선택 하 고 그룹으로 함께 작동을 음성 명령을 실행 하십시오.

## <a name="chapter-6---real-world-physics"></a>6 장-실제 물리학

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

이 장에서 실제 화면 히 면 튀어 홀로그램 추가 하겠습니다. 가득 차와 친구에서 시작 하는 프로젝트에 공간을 시청 하세요.

### <a name="objectives"></a>목표

* 실제 화면 히 면 튀어 무기를 시작 합니다.
* 다른 플레이어 볼 수 있도록 합니다 무기를 공유 합니다.

### <a name="instructions"></a>지침

* 에 **계층 구조** 선택 합니다 **HologramCollection** 개체입니다.
* 에 **검사기** 클릭 **구성 요소 추가**합니다.
* 검색 상자에 입력 **멀리 Launcher**합니다. 검색 결과 선택 합니다.

**배포 하 고 이용할 수 있습니다**
* 빌드 및 HoloLens 장치에 배포 합니다.
* 모든 장치에서 앱 실행 중일 때 실제 화면에서 멀리 시작에 어 탭을 수행 합니다.
* 프로그램 멀리 다른 플레이어의 아바타와 충돌 하는 경우를 확인 하세요!

## <a name="chapter-7---grand-finale"></a>7 장-실현할

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

이 챕터에서는 공동 작업을 사용 하 여 검색할 수 있는 포털을 찾아 됩니다.

### <a name="objectives"></a>목표

* 암호 포털을 파악 하는 앵커에 충분 한 무기를 시작 하려면 함께!

### <a name="instructions"></a>지침

* 에 **프로젝트 패널** 로 이동 합니다 **홀로그램** 폴더입니다.
* 끌어서 놓기 합니다 **지 하** 자산을 **HologramCollection 자식의**합니다.
* 사용 하 여 **HologramCollection** 선택 합니다 **구성 요소 추가** 단추를 **검사기**합니다.
* 메뉴에서 검색 상자에 입력 **ExplodeTarget**합니다. 검색 결과 선택 합니다.
* 사용 하 여 **HologramCollection** 에서 선택한를 **계층** 끌어 합니다 **EnergyHub** 개체를 **대상** 필드에 **검사기**합니다.
* 사용 하 여 **HologramCollection** 에서 선택한 합니다 **계층** 끌어를 **지 하** 개체를 **지 하** 필드에  **검사기**합니다.

**배포 하 고 이용할 수 있습니다**
* 빌드 및 HoloLens 장치에 배포 합니다.
* 앱이 시작 되는 EnergyHub에서 무기를 시작 하려면 공동 합니다.
* 지 하 세계에는 다음이 표시 되 면 무기 지 하 로봇 (적중 추가 재미 있는 작업에 대해 세 번 로봇)에서 시작 합니다.
