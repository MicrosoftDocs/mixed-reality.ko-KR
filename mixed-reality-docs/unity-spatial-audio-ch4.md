---
title: 공간 오디오 자습서-4. 런타임에 공간 오디오 사용 및 사용 안 함
description: 단추를 사용 하 여 런타임에 spatialization 오디오를 사용 하거나 사용 하지 않도록 설정 합니다.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오
ms.openlocfilehash: 3fc9b56dc58d4c19f229d92f4562f04cbca0e7a6
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182870"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="8e3f5-105">런타임에 spatialization 사용 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="8e3f5-105">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="8e3f5-106">목표</span><span class="sxs-lookup"><span data-stu-id="8e3f5-106">Objectives</span></span>
<span data-ttu-id="8e3f5-107">이 4 장에서는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-107">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="8e3f5-108">게임 개체에서 spatialization을 제어 하는 새 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-108">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="8e3f5-109">단추 작업에서 spatialization 컨트롤 스크립트를 구동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-109">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="8e3f5-110">Spatialization 컨트롤 스크립트 추가</span><span class="sxs-lookup"><span data-stu-id="8e3f5-110">Add spatialization control script</span></span>
<span data-ttu-id="8e3f5-111">**프로젝트** 창을 마우스 오른쪽 단추로 클릭 하 고 C# **만들기-> C# 스크립트**를 선택 하 여 새 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-111">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="8e3f5-112">스크립트 이름을 "SpatializeOnOff"로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-112">Name your script "SpatializeOnOff".</span></span>

![스크립트 만들기](images/spatial-audio/create-script.png)

<span data-ttu-id="8e3f5-114">**프로젝트** 창에서 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-114">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="8e3f5-115">기본 스크립트 내용을 다음과 같이 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="8e3f5-116">스크립트의 여러 줄이 주석 처리 됩니다. 이러한 줄은 [5 장에서](unity-spatial-audio-ch5.md)주석 처리가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-116">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="8e3f5-117">Spatialization를 사용 하거나 사용 하지 않도록 설정 하기 위해 스크립트는 **spatialization** 속성을 사용 하도록 설정 된 상태로 유지 하 여 **spatialBlend** 속성만 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-117">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="8e3f5-118">이 모드에서 Unity는 여전히 **볼륨** 곡선을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="8e3f5-119">그렇지 않고 사용자가 원본에서 멀리 spatialization 사용 하지 않도록 설정 하는 경우 볼륨이 갑자기 증가 하는 것을 알리는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="8e3f5-120">Spatialization를 완전히 사용 하지 않도록 설정 하려면 스크립트를 수정 하 여 **SourceObject** 변수의 **spatialization** 부울 속성도 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="8e3f5-121">스크립트를 연결 하 고 단추에서이를 구동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-121">Attach your script and drive it from the button</span></span>
<span data-ttu-id="8e3f5-122">**쿼드**의 **검사기** 창에서 **구성 요소 추가** 를 클릭 하 고 **Spatialize On Off** 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-122">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![쿼드 스크립트 추가](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="8e3f5-124">**쿼드**의 **Spatialize on Off** 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="8e3f5-124">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="8e3f5-125">**계층 구조** 에서 **PressableButtonHoloLens2-> iconandtext-> TextMeshPro** 하위 개체 찾기</span><span class="sxs-lookup"><span data-stu-id="8e3f5-125">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subobject in the **Hierarchy**</span></span>
2. <span data-ttu-id="8e3f5-126">**TextMeshPro** Suboject를 **Spatialize On Off** 구성 요소의 **ButtonTextObject** 필드로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-126">Drag the **TextMeshPro** suboject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="8e3f5-127">이러한 변경 후에는 **쿼드** 의 **Spatialize On Off** 구성 요소가 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Spatialize on off basic](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="8e3f5-129">단추가 해제 될 때 **Spatialize On Off** 스크립트를 호출 하는 단추를 설정 하려면 **PressableButtonHoloLens2** 개체의 **검사기** 창을 열고 **Interactable** 구성 요소를 찾은 후 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="8e3f5-130">**이벤트** 하위 섹션의 **OnClick ()** 영역 찾기</span><span class="sxs-lookup"><span data-stu-id="8e3f5-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="8e3f5-131">**계층** 에서 **4** 를 대상 개체 슬롯으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="8e3f5-132">작업 드롭다운 상자에서 **SpatializeOnOff. SwapSpatialization** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="8e3f5-133">이러한 변경 후에는 **Interactable** 구성 요소가 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-133">After these changes, the **Interactable** component will look like this:</span></span>

![단추 동작 설정](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="8e3f5-135">다음 단계</span><span class="sxs-lookup"><span data-stu-id="8e3f5-135">Next steps</span></span>
<span data-ttu-id="8e3f5-136">HoloLens 2 또는 Unity 편집기에서 앱을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="8e3f5-137">이제 앱에서 단추를 눌러 비디오에서 spatialization을 활성화 하 고 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="8e3f5-138">Unity 편집기에서 테스트 하는 경우 스페이스바를 눌러 스크롤 휠을 눌러 직접 시뮬레이션을 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

<span data-ttu-id="8e3f5-139">반향를 사용 하는 소리 소스에 인식 되는 거리를 추가 하려면 [5 장](unity-spatial-audio-ch5.md) 을 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-139">Continue on to [Chapter 5](unity-spatial-audio-ch5.md) to add perceived distance to sound sources using reverb.</span></span>

