---
title: Unity의 공간 소리
description: Unity 장면 내의 특정 3D 점에서 가져온 공간 소리를 재생 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 공간 음향, HRTF, 방 크기
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549074"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="6385c-104">Unity의 공간 소리</span><span class="sxs-lookup"><span data-stu-id="6385c-104">Spatial sound in Unity</span></span>

<span data-ttu-id="6385c-105">이 항목에서는 Unity 프로젝트에서 공간 소리를 사용 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="6385c-106">이 파일은 필수 플러그 인 파일 뿐만 아니라 공간 사운드를 사용 하는 Unity 구성 요소 및 속성을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="6385c-107">Unity에서 공간 소리 사용</span><span class="sxs-lookup"><span data-stu-id="6385c-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="6385c-108">Unity의 공간 사운드는 audio spatializer 플러그 인을 사용 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="6385c-109">플러그 인 파일은 Unity에 직접 번들로 제공 되므로 공간 소리를 사용 하도록 설정 하는 것은 **> 프로젝트 설정 > 오디오를 편집** 하 고 검사기의 **Spatializer 플러그 인** 을 **MS hrtf Spatializer**로 변경 하는 것 만큼 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="6385c-110">Microsoft spatializer는 현재 48000Hz만 지원 하기 때문에 시스템 출력 장치를 48000로 설정 하지 않은 경우에만 HRTF 오류가 발생 하지 않도록 시스템 샘플 주기를 48000으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="6385c-111">![오디오 관리자 검사기](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="6385c-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="6385c-112">*오디오 관리자 검사기*</span><span class="sxs-lookup"><span data-stu-id="6385c-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="6385c-113">이제 Unity 프로젝트가 공간 소리를 사용 하도록 구성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="6385c-114">개발에 Windows 10 PC를 사용 하지 않는 경우 편집기 또는 장치 (Windows 10 SDK를 사용 하는 경우에도)에서 공간 소리를 얻지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="6385c-115">Unity에서 공간 소리 사용</span><span class="sxs-lookup"><span data-stu-id="6385c-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="6385c-116">공간 사운드는 오디오 원본 구성 요소에 대 한 세 가지 설정을 조정 하 여 Unity 프로젝트에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="6385c-117">다음 단계는 오디오 원본 구성 요소에 대 한 공간 소리를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="6385c-118">**계층** 패널에서 **오디오 소스가**연결 된 게임 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="6385c-119">**검사기** 패널의 **오디오 원본** 구성 요소 아래에서</span><span class="sxs-lookup"><span data-stu-id="6385c-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="6385c-120">**Spatialize** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="6385c-121">**공간 Blend** 를 **3d** (숫자 값 1)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="6385c-122">최상의 결과를 위해서는 **3D 소리 설정** 을 확장 하 고 **볼륨 Rolloff** 을 **사용자 지정 Rolloff**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="6385c-123">![오디오 원본을 보여 주는 Unity의 검사기 패널](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="6385c-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="6385c-124">*오디오 원본을 보여 주는 Unity의 검사기 패널*</span><span class="sxs-lookup"><span data-stu-id="6385c-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="6385c-125">이제 프로젝트가 프로젝트 환경 내에 실제로 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="6385c-126">[공간 음향 디자인 지침](spatial-sound-design.md)에 대해 잘 알고 있는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="6385c-127">이러한 지침은 오디오를 프로젝트에 원활 하 게 통합 하 고 사용자가 만든 환경에 사용자를 컨퍼런스 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="6385c-128">공간 음향 설정 설정</span><span class="sxs-lookup"><span data-stu-id="6385c-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="6385c-129">Microsoft 공간 사운드 플러그 인은 오디오 시뮬레이션에 대 한 추가 제어를 허용 하기 위해 오디오 소스 별로 설정할 수 있는 추가 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="6385c-130">이 매개 변수는 시뮬레이트된 대화방의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="6385c-131">방 크기</span><span class="sxs-lookup"><span data-stu-id="6385c-131">Room Size</span></span>

<span data-ttu-id="6385c-132">공간 사운드로 시뮬레이션 되는 공간의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="6385c-133">회의실의 대략적인 크기는입니다. 작음 (사무실에서 작은 회의실), 중형 (대량 회의실) 및 큼 (auditorium).</span><span class="sxs-lookup"><span data-stu-id="6385c-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="6385c-134">또한 실내 크기를 none으로 지정 하 여 실외 환경을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="6385c-135">기본 방 크기는 작음입니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="6385c-136">예제</span><span class="sxs-lookup"><span data-stu-id="6385c-136">Example</span></span>

<span data-ttu-id="6385c-137">MixedRealityToolkit for Unity는 공간 음향 설정을 쉽게 설정 하는 정적 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="6385c-138">이 클래스는 [MixedRealityToolkit\SpatialSound 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) 에서 찾을 수 있으며 프로젝트의 모든 스크립트에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="6385c-139">프로젝트의 각 오디오 원본 구성 요소에서 이러한 매개 변수를 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="6385c-140">다음 예에서는 연결 된 오디오 소스에 대 한 중간 방 크기를 선택 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="6385c-141">Unity에서 매개 변수 직접 액세스</span><span class="sxs-lookup"><span data-stu-id="6385c-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="6385c-142">MixedRealityToolkit에서 뛰어난 오디오 도구를 사용 하지 않으려는 경우 HRTF 매개 변수를 변경 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="6385c-143">모든 HRTF 오디오 원본에 연결 하려는 *SetHRTF.cs* 이라는 스크립트에이를 복사 하 여 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="6385c-144">이를 통해 HRTF에 중요 한 매개 변수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-144">It lets you change parameters important to HRTF.</span></span>

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="6385c-145">혼합 현실 도구 키트의 공간 소리</span><span class="sxs-lookup"><span data-stu-id="6385c-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="6385c-146">HoloToolkit-Examples/SpatialSound/장면/U오디오 관리자 테스트. unity</span><span class="sxs-lookup"><span data-stu-id="6385c-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="6385c-147">Mixed Reality Toolkit의 다음 예는 소리를 사용 하 여 환경을 더 몰입로 만드는 방법을 보여 주는 일반적인 오디오 효과 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="6385c-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="6385c-148">HoloToolkit-Examples/SpatialSound/장면/기타 Lofitest unity</span><span class="sxs-lookup"><span data-stu-id="6385c-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="6385c-149">HoloToolkit-Examples/SpatialSound/장면/AudioOcclusionTest</span><span class="sxs-lookup"><span data-stu-id="6385c-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="6385c-150">참조</span><span class="sxs-lookup"><span data-stu-id="6385c-150">See also</span></span>
* [<span data-ttu-id="6385c-151">공간 음향</span><span class="sxs-lookup"><span data-stu-id="6385c-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="6385c-152">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="6385c-152">Spatial sound design</span></span>](spatial-sound-design.md)
