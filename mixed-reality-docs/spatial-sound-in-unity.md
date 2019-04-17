---
title: Unity에서 공간 소리
description: 공간 소리를 재생 하는 작업은 Unity 장면 내 특정 3D 지점에서 제공 됩니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity를 공간 소리 HRTF, 공간 크기
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597515"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="0c379-104">Unity에서 공간 소리</span><span class="sxs-lookup"><span data-stu-id="0c379-104">Spatial sound in Unity</span></span>

<span data-ttu-id="0c379-105">이 항목에는 Unity 프로젝트에서 공간 소리를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="0c379-106">필요한 플러그 인 파일 뿐만 아니라 Unity 구성 요소 및 공간 소리를 사용할 수 있는 속성을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="0c379-107">Unity에서 공간 소리를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="0c379-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="0c379-108">Unity에서 공간 소리는 오디오 입체 음향 플러그 인을 사용 하 여 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="0c379-109">공간 소리를 사용 하도록 설정 하려고 하는 것 만큼 쉽습니다 이므로 플러그 인 파일을 Unity에 직접 묶이는 **편집 > 프로젝트 설정 > 오디오** 변경과 합니다 **입체 음향 플러그 인** 는관리자의 **MS HRTF 입체 음향**합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="0c379-110">Microsoft 입체 음향만를 지원 하므로 48000 Hz 현재 드문 경우 이지만 시스템 출력 장치 설정 되지 않았음을 48000를 이미 HRTF 오류를 방지 하기 위해 48000를 시스템 샘플 요금은도 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="0c379-111">![AudioManager 검사기](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="0c379-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="0c379-112">*AudioManager 검사기*</span><span class="sxs-lookup"><span data-stu-id="0c379-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="0c379-113">Unity 프로젝트는 이제 공간 소리를 사용 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="0c379-114">개발을 위한 Windows 10 PC를 사용 하지 않는 경우 얻을 수 없습니다 공간 소리 편집기에서 나 장치의 (경우에 Windows 10 SDK를 사용 하는).</span><span class="sxs-lookup"><span data-stu-id="0c379-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="0c379-115">Unity에서 공간 소리를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="0c379-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="0c379-116">공간 사운드 오디오 원본 구성 요소에 세 가지 설정을 조정 하 여 Unity 프로젝트에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="0c379-117">다음 단계를 공간 사운드 오디오 원본 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="0c379-118">에 **계층 구조** 패널에 연결 하는 게임 개체를 선택 합니다 **오디오 원본**합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="0c379-119">에 **검사기** 패널의 합니다 **오디오 원본** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0c379-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="0c379-120">확인 합니다 **Spatialize** 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="0c379-121">설정할 **공간 Blend** 하 **3D** (숫자 값 1).</span><span class="sxs-lookup"><span data-stu-id="0c379-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="0c379-122">최상의 결과 확장 하 고 **3D 소리 설정** 설정 **볼륨 롤오프** 하 **사용자 지정 롤오프**합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="0c379-123">![오디오 소스를 표시 하는 Unity inspector 패널](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="0c379-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="0c379-124">*오디오 소스를 표시 하는 Unity inspector 패널*</span><span class="sxs-lookup"><span data-stu-id="0c379-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="0c379-125">소리 이제 실제로 프로젝트의 환경 내에서 존재!</span><span class="sxs-lookup"><span data-stu-id="0c379-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="0c379-126">잘 알고는 것이 좋습니다 합니다 [공간 소리 디자인 지침](spatial-sound-design.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="0c379-127">이러한 지침을 통해 프로젝트에 오디오를 원활 하 게 통합 하는 데 사용자가 만든 환경에 사용자를 추가로 세계 체험해 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="0c379-128">소리 공간 설정</span><span class="sxs-lookup"><span data-stu-id="0c379-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="0c379-129">에 설정할 수 있습니다 하는 추가 매개 변수를 제공 하는 Microsoft 공간 소리 플러그 인을 오디오 소스 별로 오디오 시뮬레이션을 추가로 제어할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="0c379-130">이 매개 변수는 시뮬레이션 된 공간의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="0c379-131">공간 크기</span><span class="sxs-lookup"><span data-stu-id="0c379-131">Room Size</span></span>

<span data-ttu-id="0c379-132">크기를 공간 소리 기준으로 시뮬레이션 되는 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="0c379-133">대화방의 대략적인 크기는 다음과 같습니다. (작은 회의실에 office) 소, 중 (큰 회의실) 및 대규모 (강당).</span><span class="sxs-lookup"><span data-stu-id="0c379-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="0c379-134">또한 none 실외 환경을 시뮬레이션 하는 공간 크기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="0c379-135">기본 공간 크기가 작습니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="0c379-136">예제</span><span class="sxs-lookup"><span data-stu-id="0c379-136">Example</span></span>

<span data-ttu-id="0c379-137">Unity에 대 한 MixedRealityToolkit 공간 소리 설정을 쉽게 설정 하는 정적 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="0c379-138">이 클래스에서 찾을 수 있습니다 합니다 [MixedRealityToolkit\SpatialSound 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) 프로젝트에서 모든 스크립트에서 호출 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="0c379-139">프로젝트의 각 오디오 원본 구성 요소에 이러한 매개 변수를 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="0c379-140">다음 예제에서는 연결된 된 오디오 원본에 대 한 중간 공간 크기를 선택 하면 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="0c379-141">Unity에서 매개 변수를 직접 액세스</span><span class="sxs-lookup"><span data-stu-id="0c379-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="0c379-142">MixedRealityToolkit의 뛰어난 오디오 도구를 사용 하지 않으려는 경우 HRTF 매개 변수 변경 하는 방법을 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="0c379-143">복사/붙여 넣을 수 있습니다이 호출 스크립트로 *SetHRTF.cs* 모든 HRTF AudioSource에 연결 하려고 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="0c379-144">HRTF에 중요 한 매개 변수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="0c379-145">혼합된 현실 도구 키트의 공간 소리</span><span class="sxs-lookup"><span data-stu-id="0c379-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="0c379-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="0c379-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="0c379-147">혼합 현실 도구 키트에서 다음 예제는 소리를 사용 하 여 사용자 환경을 더 몰입 형을 확인 하는 방법을 보여 주는 예제는 일반 오디오 효과입니다.</span><span class="sxs-lookup"><span data-stu-id="0c379-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="0c379-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="0c379-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="0c379-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="0c379-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="0c379-150">참조</span><span class="sxs-lookup"><span data-stu-id="0c379-150">See also</span></span>
* [<span data-ttu-id="0c379-151">소리 공간</span><span class="sxs-lookup"><span data-stu-id="0c379-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="0c379-152">공간 적절 하 게 디자인</span><span class="sxs-lookup"><span data-stu-id="0c379-152">Spatial sound design</span></span>](spatial-sound-design.md)
