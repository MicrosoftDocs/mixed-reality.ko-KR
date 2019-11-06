---
title: Unity의 공간 소리
description: Unity 장면 내의 특정 3D 점에서 가져온 공간 소리를 재생 합니다.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, 공간 음향, HRTF, 방 크기
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641070"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="9680e-104">Unity의 공간 소리</span><span class="sxs-lookup"><span data-stu-id="9680e-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="9680e-105">이 페이지는 Unity mixed reality 프로젝트에서 Microsoft HRTF spatializer를 사용 하 고 디자인 하는 데 도움이 되는 리소스에 대 한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9680e-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="9680e-106">Spatialization 사용</span><span class="sxs-lookup"><span data-stu-id="9680e-106">Enable spatialization</span></span>

<span data-ttu-id="9680e-107">프로젝트의 오디오 설정에서 **MS HRTF Spatializer** 를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9680e-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="9680e-108">자세한 내용은 [Unity의 spatializer 설명서](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9680e-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="9680e-109">**오디오 원본을** 계층의 개체에 연결 하 고, **spatialization 사용** 확인란을 선택 하 고 **공간 Blend** 슬라이더를 ' 1 '로 이동 하 여 spatialization를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9680e-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="9680e-110">자세한 내용은 [Unity의 오디오 원본 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9680e-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="9680e-111">Spatialization를 사용 하 여 디자인</span><span class="sxs-lookup"><span data-stu-id="9680e-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="9680e-112">거리 기반 감쇠</span><span class="sxs-lookup"><span data-stu-id="9680e-112">Distance-based attenuation</span></span>
<span data-ttu-id="9680e-113">Unity의 기본 거리 기반 감소는 로그 rolloff를 사용 하 여 최소 거리가 1 미터이 고 최대 거리가 500 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="9680e-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="9680e-114">이는 시나리오에 적합 하거나, 소스를 너무 빨리 경우 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9680e-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="9680e-115">거리 감소 곡선에 대 한 권장 설정은 [혼합 현실의 소리 디자인](spatial-sound-design.md) 을 참조 하세요. unity에서 이러한 곡선을 설정 하는 방법에 대 한 자세한 내용은 [unity의 오디오 소스 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9680e-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="9680e-116">환경</span><span class="sxs-lookup"><span data-stu-id="9680e-116">Environment</span></span>
<span data-ttu-id="9680e-117">**MS HRTF Spatializer** 에는 [네 개의 반향 설정이](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) 있고 기본값은 ' small ' 인 대화방 반향 구성 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9680e-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="9680e-118">Spatialized 오디오 소스가 있는 Unity의 각 개체에 다음 C# 스크립트를 연결 하 여 각 오디오 원본에 대해 대화방 설정을 프로그래밍 방식으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9680e-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

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

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="9680e-119">Unity 공간 음향 예</span><span class="sxs-lookup"><span data-stu-id="9680e-119">Unity spatial sound examples</span></span>
<span data-ttu-id="9680e-120">Mixed Reality Toolkit (MRTK)에는 혼합 현실에서 오디오 효과를 적용 하는 방법에 대 한 예제가 포함 되어 있습니다. [mrtk 데모](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span><span class="sxs-lookup"><span data-stu-id="9680e-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>

