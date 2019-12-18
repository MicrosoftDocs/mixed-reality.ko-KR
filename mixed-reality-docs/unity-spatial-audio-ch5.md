---
title: 공간 오디오 자습서-5. 반향를 사용 하 여 공간 오디오에 거리 추가
description: 반향 효과를 추가 하 여 공간 오디오에 대 한 거리 변동의 의미를 향상 시킵니다.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182740"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="e2788-105">반향를 사용 하 여 공간 오디오에 거리 추가</span><span class="sxs-lookup"><span data-stu-id="e2788-105">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="e2788-106">목표</span><span class="sxs-lookup"><span data-stu-id="e2788-106">Objectives</span></span>
<span data-ttu-id="e2788-107">이전 장에서는 spatialization를 소리에 추가 하 여 방향을 지정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-107">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="e2788-108">이 다섯 번째 장에서는 소리에 거리를 지정 하기 위해 반향 효과를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-108">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="e2788-109">목표는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-109">Our objectives are to:</span></span>
* <span data-ttu-id="e2788-110">반향을 추가 하 여 사운드 소스의 인식 된 거리 향상</span><span class="sxs-lookup"><span data-stu-id="e2788-110">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="e2788-111">홀로그램에 대 한 수신기의 거리를 사용 하 여 소리의 인식 거리 제어</span><span class="sxs-lookup"><span data-stu-id="e2788-111">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="e2788-112">믹서 그룹 및 반향 효과 추가</span><span class="sxs-lookup"><span data-stu-id="e2788-112">Add a mixer group and a reverb effect</span></span>
<span data-ttu-id="e2788-113">[2 장에서](unity-spatial-audio-ch2.md)는 믹서를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-113">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="e2788-114">믹서에는 기본적으로 **Master**라는 **그룹** 하나가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-114">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="e2788-115">약간의 소리에 반향 효과를 적용 하려는 경우에만 해당 소리에 대해 두 번째 **그룹** 을 추가 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-115">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="e2788-116">**그룹**을 추가 하려면 **오디오 믹서** 에서 **마스터** 그룹을 마우스 오른쪽 단추로 클릭 하 고 **하위 그룹 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-116">To add a **Group**, right click on the **Master** group in the **Audio Mixer** and choose **Add child group**:</span></span>

![자식 그룹 추가](images/spatial-audio/add-child-group.png)

<span data-ttu-id="e2788-118">이 예제에서는 새 그룹 "방 효과"의 이름을 지정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-118">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="e2788-119">각 **그룹** 에는 고유한 영향 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-119">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="e2788-120">새 그룹에서 **추가 ...** 를 클릭 하 고 **SFX 반향**를 선택 하 여 새 그룹에 반향 효과를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-120">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![SFX 반향 추가](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="e2788-122">오디오 용어로 원래의 unreverberated 오디오를 _마른 경로_라고 하며, 반향 필터를 사용 하 여 필터링 한 후의 오디오를도로 _경로_라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-122">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="e2788-123">두 경로는 모두 오디오 출력으로 전송 되 고, 이러한 혼합의 상대적인 강도를 고 지 _/건조_합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-123">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="e2788-124">가 중/마른 조합은 거리의 의미에 크게 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-124">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="e2788-125">**SFX 반향** 에는 효과 내에서도로/마른 조합을 조정 하는 컨트롤이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-125">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="e2788-126">**Microsoft Spatializer** 플러그 인은 마른 경로를 처리 하기 때문에 **SFX 반향** 를 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-126">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="e2788-127">**SFX 반향**의 **검사기** 창에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-127">On the **Inspector** pane of your **SFX Reverb**:</span></span>
* <span data-ttu-id="e2788-128">마른 수준 속성을 가장 낮은 설정 (-1만 mB)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-128">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="e2788-129">방 속성을 가장 높은 설정 (0mb)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-129">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="e2788-130">이러한 변경 후에는 **SFX 반향** 의 **검사기** 창이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-130">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![SFX 반향 속성](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="e2788-132">다른 설정은 시뮬레이트된 대화방의 느낌을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-132">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="e2788-133">특히, **감소 시간은** 인식 된 대화방 크기와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-133">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="e2788-134">비디오 재생에서 반향 사용</span><span class="sxs-lookup"><span data-stu-id="e2788-134">Enable reverb on the video playback</span></span>
<span data-ttu-id="e2788-135">오디오 원본에서 반향를 사용 하도록 설정 하는 두 가지 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-135">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="e2788-136">**오디오 소스** 를 해당 **그룹** 으로 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-136">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="e2788-137">처리를 위해 오디오를 **그룹** 에 전달 하도록 **Microsoft Spatializer** 플러그 인을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-137">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="e2788-138">다음 단계에서는 오디오 라우팅을 제어 하도록 스크립트를 조정 하 고 **Microsoft Spatializer** 플러그 인과 함께 제공 되는 컨트롤 스크립트를 연결 하 여 데이터를 반향에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-138">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="e2788-139">**쿼드**의 **검사기** 창에서 **구성 요소 추가** 를 클릭 하 고 **방 효과 보내기 수준** 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-139">On the **Inspector** pane for the **Quad**, click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![송신 수준 스크립트 추가](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="e2788-141">**Microsoft Spatializer** 플러그 인의 **공간 효과 보내기 수준** 기능을 사용 하도록 설정 하지 않으면 효과 처리를 위해 오디오를 Unity 오디오 엔진으로 다시 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-141">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="e2788-142">**대화방 효과 송신 수준** 구성 요소에는 반향 처리를 위해 Unity 오디오 엔진으로 보낸 오디오의 수준을 설정 하는 그래프 컨트롤이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-142">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="e2788-143">곡선을 클릭 하 고 아래로 끌어 수준을 about-30dB로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-143">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![반향 곡선 조정](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="e2788-145">다음으로 **SpatializeOnOff** 스크립트에서 주석 처리 된 4 줄의 주석 처리를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-145">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="e2788-146">이제 스크립트는 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-146">The script will now look like this:</span></span>
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

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
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="e2788-147">이러한 줄 주석 처리 스크립트에 대 한 두 개의 속성을 **검사기** 창에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-147">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="e2788-148">이를 설정 하려면 **쿼드** **Spatialize on Off** 구성 요소의 **검사기** 창에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-148">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad**:</span></span>
* <span data-ttu-id="e2788-149">**방 효과 그룹** 속성을 새 대화방 효과 믹서 그룹으로 설정</span><span class="sxs-lookup"><span data-stu-id="e2788-149">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="e2788-150">마스터 **그룹** 속성을 마스터 믹서 그룹으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-150">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="e2788-151">이러한 변경 후 **Spatialize On Off** 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-151">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Spatialize On Off 확장](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="e2788-153">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e2788-153">Next steps</span></span>

<span data-ttu-id="e2788-154">HoloLens 2 또는 Unity 편집기에서 앱을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="e2788-154">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="e2788-155">이제 앱에서 단추를 터치 하 여 spatialization를 활성화 하는 경우 스크립트는 비디오의 오디오를 대화방 효과 그룹으로 라우팅하고 반향를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-155">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="e2788-156">스테레오로 전환 하는 경우 오디오를 마스터 그룹으로 라우팅하고 반향를 추가 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-156">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="e2788-157">Unity 용 HoloLens 2 공간 오디오 자습서를 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-157">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="e2788-158">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="e2788-158">Congratulations!</span></span>


