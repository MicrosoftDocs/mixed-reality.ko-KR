---
title: Unity의 공간 소리
description: Unity 장면 내의 특정 3D 점에서 공간 소리를 재생 합니다.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, 공간 음향, HRTF, 방 크기
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181993"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="a1269-104">Unity의 공간 소리</span><span class="sxs-lookup"><span data-stu-id="a1269-104">Spatial sound in Unity</span></span>

<span data-ttu-id="a1269-105">이 페이지는 Unity의 공간 소리에 대 한 리소스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="a1269-106">Spatializer 옵션</span><span class="sxs-lookup"><span data-stu-id="a1269-106">Spatializer options</span></span>
<span data-ttu-id="a1269-107">혼합 현실 응용 프로그램에 대 한 Spatializer 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="a1269-108">*MS HRTF Spatializer*입니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="a1269-109">Unity는 *Windows Mixed Reality* 선택적 패키지의 일부로이를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="a1269-110">이는 높은 비용의 단일 소스 아키텍처에서 CPU에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="a1269-111">이는 이전에 원본 HoloLens 응용 프로그램과의 호환성을 위해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="a1269-112">*Microsoft Spatializer*입니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="a1269-113">[Microsoft Spatializer GitHub 리포지토리에서](https://github.com/microsoft/spatialaudio-unity)사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="a1269-114">이는 저렴 한 ' 다중 원본 ' 아키텍처를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="a1269-115">HoloLens 2에서이는 하드웨어 가속기로 오프 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="a1269-116">새 응용 프로그램의 경우 *Microsoft Spatializer*를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="a1269-117">Spatialization 사용</span><span class="sxs-lookup"><span data-stu-id="a1269-117">Enable spatialization</span></span>

<span data-ttu-id="a1269-118">[Unity 용 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) 을 사용 하 여 _SpatialAudio. Spatializer_ 을 설치 하 고 프로젝트의 오디오 설정에서 **microsoft Spatializer** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="a1269-119">그런 다음 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-119">Then:</span></span>
* <span data-ttu-id="a1269-120">계층의 개체에 **오디오 소스** 연결</span><span class="sxs-lookup"><span data-stu-id="a1269-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="a1269-121">**Spatialization 사용** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="a1269-122">**공간 Blend** 슬라이더를 ' 1 '로 이동</span><span class="sxs-lookup"><span data-stu-id="a1269-122">Move the **Spatial Blend** slider to '1'</span></span>

<span data-ttu-id="a1269-123">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1269-123">For more details, see:</span></span>
* [<span data-ttu-id="a1269-124">Microsoft spatializer GitHub 리포지토리</span><span class="sxs-lookup"><span data-stu-id="a1269-124">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="a1269-125">Microsoft의 spatializer 자습서</span><span class="sxs-lookup"><span data-stu-id="a1269-125">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="a1269-126">Unity의 오디오 소스 설명서</span><span class="sxs-lookup"><span data-stu-id="a1269-126">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="a1269-127">Unity의 spatializer 설명서</span><span class="sxs-lookup"><span data-stu-id="a1269-127">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="a1269-128">거리 기반 감쇠</span><span class="sxs-lookup"><span data-stu-id="a1269-128">Distance-based attenuation</span></span>
<span data-ttu-id="a1269-129">Unity의 기본 거리 기반 감소는 로그 rolloff를 사용 하 여 최소 거리가 1 미터이 고 최대 거리가 500 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-129">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="a1269-130">이러한 설정은 시나리오에 대해 적용 될 수 있으며, 원본이 너무 빨리 또는 너무 느리게 경우 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-130">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="a1269-131">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1269-131">For more details, see:</span></span>
* <span data-ttu-id="a1269-132">권장 설정에 대해 [혼합 현실에서 설계](spatial-sound-design.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-132">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="a1269-133">이러한 곡선을 설정 하는 방법에 대 한 지침은 [Unity의 오디오 소스 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1269-133">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="a1269-134">잔</span><span class="sxs-lookup"><span data-stu-id="a1269-134">Reverb</span></span>
<span data-ttu-id="a1269-135">_Microsoft Spatializer_ 는 기본적으로 사후 Spatializer 효과를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-135">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="a1269-136">Spatialized 원본에 대해 반향 및 기타 효과를 사용 하도록 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-136">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="a1269-137">각 원본에 **대화방 효과 보내기 수준** 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="a1269-137">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="a1269-138">각 원본에 대 한 전송 수준 곡선을 조정 하 여 효과 처리를 위해 그래프로 다시 보낸 오디오의 이득을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1269-138">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="a1269-139">자세한 내용은 [spatializer 자습서의 5 장](unity-spatial-audio-ch5.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1269-139">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="a1269-140">Unity 공간 음향 예</span><span class="sxs-lookup"><span data-stu-id="a1269-140">Unity spatial sound examples</span></span>
<span data-ttu-id="a1269-141">Unity의 공간 음향 예는 다음을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1269-141">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="a1269-142">MRTK 데모</span><span class="sxs-lookup"><span data-stu-id="a1269-142">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="a1269-143">[Microsoft Spatializer 샘플 프로젝트](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="a1269-143">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="a1269-144">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a1269-144">Next steps</span></span>
* [<span data-ttu-id="a1269-145">혼합 현실에서의 소리 디자인</span><span class="sxs-lookup"><span data-stu-id="a1269-145">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="a1269-146">Microsoft의 spatializer 자습서</span><span class="sxs-lookup"><span data-stu-id="a1269-146">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

