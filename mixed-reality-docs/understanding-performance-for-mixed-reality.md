---
title: 혼합 현실 성능 이해
description: Windows Mixed Reality 앱 성능을 최적화 하는 방법에 대 한 고급 항목 및 세부 정보
author: troy-ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 성능, 최적화, CPU, GPU
ms.openlocfilehash: 4a0f4cd9caea5dd601ad663801e760261980c429
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84111020"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="66e1e-104">혼합 현실의 성능 이해</span><span class="sxs-lookup"><span data-stu-id="66e1e-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="66e1e-105">이 문서에서는 혼합 현실 앱의 성능에 대 한 중요 한 개념을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-105">This article is an introduction to understanding the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="66e1e-106">최적의 프레임 속도에서 응용 프로그램이 실행 되지 않으면 사용자 환경이 크게 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="66e1e-107">Holograms가 불안정 하 게 표시 되 고 환경에 대 한 헤드 추적이 부정확 하 게 표시 되어 사용자에 게 잘못 된 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-107">Holograms will appear unstable and head tracking of the environment will be inaccurate, leading to a poor experience for the user.</span></span> <span data-ttu-id="66e1e-108">성능은 혼합 현실 개발의 경우 첫 번째 클래스 기능으로 간주 되어야 하며,이는 폴란드어 작업이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-108">Performance must be considered a first class feature for mixed reality development and not a polish task.</span></span>

<span data-ttu-id="66e1e-109">각 대상 플랫폼에 대 한 성능의 프레임 속도 값은 아래에 나열 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-109">The performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="66e1e-110">플랫폼</span><span class="sxs-lookup"><span data-stu-id="66e1e-110">Platform</span></span> | <span data-ttu-id="66e1e-111">대상 프레임 율</span><span class="sxs-lookup"><span data-stu-id="66e1e-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="66e1e-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="66e1e-112">HoloLens</span></span>](hololens-hardware-details.md) | <span data-ttu-id="66e1e-113">60FPS</span><span class="sxs-lookup"><span data-stu-id="66e1e-113">60 FPS</span></span> |
| [<span data-ttu-id="66e1e-114">Windows Mixed Reality 울트라 Pc</span><span class="sxs-lookup"><span data-stu-id="66e1e-114">Windows Mixed Reality Ultra PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="66e1e-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="66e1e-115">90 FPS</span></span> |
| [<span data-ttu-id="66e1e-116">Windows Mixed Reality Pc</span><span class="sxs-lookup"><span data-stu-id="66e1e-116">Windows Mixed Reality PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="66e1e-117">60FPS</span><span class="sxs-lookup"><span data-stu-id="66e1e-117">60 FPS</span></span> |

<span data-ttu-id="66e1e-118">아래 프레임 워크는 대상 프레임 속도 적중에 대 한 모범 사례를 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-118">The framework below outlines best practices for hitting target frame rates.</span></span> <span data-ttu-id="66e1e-119">Unity에서 개발 하는 경우 unity 환경에서 프레임 속도를 측정 하 고 개선 하는 방법에 대 한 팁은 [unity의 성능 권장 사항 문서](performance-recommendations-for-unity.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66e1e-119">If developing in Unity, consider reading the [performance recommendations for Unity article](performance-recommendations-for-unity.md) for tips on measuring and improving framerate in the Unity environment.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="66e1e-120">성능 병목 상태 이해</span><span class="sxs-lookup"><span data-stu-id="66e1e-120">Understanding performance bottlenecks</span></span>

<span data-ttu-id="66e1e-121">앱에 실적이 떨어지는 프레임 속도가 있는 경우 첫 번째 단계는 응용 프로그램의 계산 집약적 위치를 분석 하 고 이해 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-121">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="66e1e-122">장면을 렌더링 하는 작업을 담당 하는 두 가지 기본 프로세서는 CPU와 GPU입니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-122">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="66e1e-123">이러한 각 항목은 혼합 현실 앱의 다양 한 측면을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-123">Each of these handle different aspects of your Mixed Reality app.</span></span> <span data-ttu-id="66e1e-124">병목 현상이 발생할 수 있는 세 가지 주요 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-124">There are three key places where bottlenecks may occur:</span></span> 

1. <span data-ttu-id="66e1e-125">**앱 스레드-CPU** -이 스레드는 응용 프로그램 논리를 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-125">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="66e1e-126">여기에는 입력, 애니메이션, 물리 및 기타 응용 프로그램 논리가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-126">This includes processing input, animations, physics, and other app logic.</span></span>
2. <span data-ttu-id="66e1e-127">**CPU에 스레드 CPU 렌더링** -이 스레드는 gpu에 그리기 호출을 전송 하는 일을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-127">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="66e1e-128">응용 프로그램에서 큐브나 모델 등의 개체를 렌더링 하려는 경우이 스레드는 이러한 작업을 수행 하기 위해 GPU에 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-128">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU to perform these operations.</span></span>
3. <span data-ttu-id="66e1e-129">**GPU** -이 프로세서는 가장 일반적으로 응용 프로그램의 그래픽 파이프라인을 처리 하 여 3d 데이터 (모델, 질감 등)를 픽셀로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-129">**GPU** - This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc.) into pixels.</span></span> <span data-ttu-id="66e1e-130">궁극적으로 장치 화면에 제출할 2D 이미지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-130">It ultimately produces a 2D image to submit to your device's screen.</span></span>

![프레임 수명](images/lifetime-of-a-frame.png)

<span data-ttu-id="66e1e-132">일반적으로 HoloLens 응용 프로그램은 GPU에 바인딩되므로 항상 그렇지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-132">Generally, HoloLens applications will be GPU bound, but not always.</span></span> <span data-ttu-id="66e1e-133">아래 도구와 기술을 사용 하 여 특정 앱의 병목 현상이 발생 하는 위치를 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-133">Use the tools and techniques below to understand where your particular app is bottlenecked.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="66e1e-134">응용 프로그램을 분석 하는 방법</span><span class="sxs-lookup"><span data-stu-id="66e1e-134">How to analyze your application</span></span>

<span data-ttu-id="66e1e-135">혼합 현실 응용 프로그램의 성능 프로필을 이해 하는 데 사용할 수 있는 많은 도구가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-135">There are many tools that allow you to understand the performance profile of your mixed reality application.</span></span> <span data-ttu-id="66e1e-136">이를 통해 병목 상태를 해결할 수 있는 위치와 이유를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-136">These will enable you to find where and why you have bottlenecks, so you can address them.</span></span>

<span data-ttu-id="66e1e-137">응용 프로그램에 대 한 심층 프로 파일링 정보를 얻을 수 있는 몇 가지 일반적인 도구는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-137">Below are some common tools to gain deep profiling information for your application:</span></span>
- [<span data-ttu-id="66e1e-138">Intel 그래픽 성능 분석기</span><span class="sxs-lookup"><span data-stu-id="66e1e-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="66e1e-139">Visual Studio 그래픽 디버거</span><span class="sxs-lookup"><span data-stu-id="66e1e-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [<span data-ttu-id="66e1e-140">Unity 프로파일러</span><span class="sxs-lookup"><span data-stu-id="66e1e-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="66e1e-141">Unity 프레임 디버거</span><span class="sxs-lookup"><span data-stu-id="66e1e-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="66e1e-142">모든 환경에서 프로 파일링 하는 방법</span><span class="sxs-lookup"><span data-stu-id="66e1e-142">How to profile in any environment</span></span>

<span data-ttu-id="66e1e-143">응용 프로그램에서 GPU가 바인딩되어 있는지 아니면 CPU에 바인딩되어 있는지를 확인 하는 한 가지 방법은 렌더링 대상 출력의 해상도를 낮추는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-143">One way to determine if you are GPU bound or CPU bound in your application is to decrease the resolution of the render target output.</span></span> <span data-ttu-id="66e1e-144">계산 되는 픽셀 수를 줄이면 GPU 부하가 감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-144">By reducing the number of pixels to calculate, this will reduce your GPU load.</span></span> <span data-ttu-id="66e1e-145">장치는 작은 질감으로 렌더링 된 다음 위쪽의 샘플을 통해 최종 이미지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-145">The device will render to a smaller texture, then up-sample to display your final image.</span></span>

<span data-ttu-id="66e1e-146">렌더링 해상도를 줄이고 나면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-146">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="66e1e-147">응용 프로그램 프레임 속도가 **늘어나면** **GPU가 바인딩될** 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-147">Application framerate **increases**, then you are likely **GPU Bound**</span></span>
1) <span data-ttu-id="66e1e-148">응용 프로그램 프레임 속도가 **변경 되지**않은 경우 **CPU 바인딩될** 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-148">Application framerate **unchanged**, then you are likely **CPU Bound**</span></span>

>[!NOTE]
><span data-ttu-id="66e1e-149">Unity는 *[Xrsettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 통해 런타임에 응용 프로그램의 렌더링 대상 해상도를 쉽게 수정할 수 있는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-149">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="66e1e-150">장치에 표시 되는 최종 이미지의 해상도는 고정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-150">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="66e1e-151">플랫폼은 디스플레이에서 렌더링 하기 위한 더 높은 해상도 이미지를 빌드하기 위해 낮은 해상도 출력을 샘플링 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-151">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="66e1e-152">응용 프로그램을 개선 하는 방법</span><span class="sxs-lookup"><span data-stu-id="66e1e-152">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="66e1e-153">CPU 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="66e1e-153">CPU performance recommendations</span></span>

<span data-ttu-id="66e1e-154">일반적으로 CPU의 혼합 현실 응용 프로그램에서 대부분의 작업은 장면의 "시뮬레이션"을 수행 하 고 응용 프로그램 논리를 처리 하는 작업을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-154">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing your application logic.</span></span> <span data-ttu-id="66e1e-155">다음 영역은 일반적으로 최적화를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-155">The following areas are usually targeted for optimization:</span></span>

- <span data-ttu-id="66e1e-156">애니메이션</span><span class="sxs-lookup"><span data-stu-id="66e1e-156">Animations</span></span>
- <span data-ttu-id="66e1e-157">물리</span><span class="sxs-lookup"><span data-stu-id="66e1e-157">Physics</span></span>
- <span data-ttu-id="66e1e-158">메모리 할당</span><span class="sxs-lookup"><span data-stu-id="66e1e-158">Memory allocations</span></span>
- <span data-ttu-id="66e1e-159">복합 알고리즘 (예:</span><span class="sxs-lookup"><span data-stu-id="66e1e-159">Complex algorithms (i.e</span></span> <span data-ttu-id="66e1e-160">역 기구학, 경로 찾기)</span><span class="sxs-lookup"><span data-stu-id="66e1e-160">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="66e1e-161">GPU 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="66e1e-161">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="66e1e-162">대역폭 및 채우기 빈도 이해</span><span class="sxs-lookup"><span data-stu-id="66e1e-162">Understanding bandwidth vs. fill rate</span></span>
<span data-ttu-id="66e1e-163">GPU에서 프레임을 렌더링 하는 경우 응용 프로그램은 일반적으로 메모리 대역폭이 나 채우기 속도로 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-163">When rendering a frame on the GPU, an application is generally either bound by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="66e1e-164">**메모리 대역폭** 은 GPU에서 메모리를 통해 수행할 수 있는 읽기 및 쓰기의 률입니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-164">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="66e1e-165">대역폭 제한을 확인 하려면 질감 품질을 줄이고 프레임 속도가 개선 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-165">To identify bandwidth limitations, reduce texture quality and check if the framerate has improved.</span></span>
    - <span data-ttu-id="66e1e-166">Unity에서는 **Edit** **Texture Quality**  >  **프로젝트 설정**  >  **[품질 설정](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 편집에서 질감 품질을 변경 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-166">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="66e1e-167">**채우기 비율은** GPU에서 초당 그릴 수 있는 픽셀을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-167">**Fill rate** refers to the pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="66e1e-168">채우기 속도 제한을 파악 하려면 디스플레이 해상도를 낮추고 프레임 속도가 개선 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-168">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="66e1e-169">Unity에서는 *[Xrsettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 통해이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-169">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="66e1e-170">메모리 대역폭은 일반적으로 다음 중 하나에 대 한 최적화를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-170">Memory bandwidth generally involves optimizations to either:</span></span>
1) <span data-ttu-id="66e1e-171">텍스처 해상도 줄이기</span><span class="sxs-lookup"><span data-stu-id="66e1e-171">Decrease texture resolutions</span></span>
2) <span data-ttu-id="66e1e-172">질감 (법선, 반사 등)을 덜 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-172">Utilize fewer textures (normals, specular, etc.)</span></span>

<span data-ttu-id="66e1e-173">채우기 비율은 최종 렌더링 된 픽셀에 대해 계산 되어야 하는 작업의 수를 줄이는 데 중점을 두었습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-173">Fill rate is focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="66e1e-174">여기에는 축소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-174">This includes reducing:</span></span>
1) <span data-ttu-id="66e1e-175">렌더링/처리할 개체 수</span><span class="sxs-lookup"><span data-stu-id="66e1e-175">Number of objects to render/process</span></span>
2) <span data-ttu-id="66e1e-176">셰이더 당 작업 수</span><span class="sxs-lookup"><span data-stu-id="66e1e-176">Number of operations per shader</span></span>
3) <span data-ttu-id="66e1e-177">최종 결과 (기 하 도형 셰이더, 사후 처리 효과 등)에 대 한 GPU 스테이지 수</span><span class="sxs-lookup"><span data-stu-id="66e1e-177">Number of GPU stages to final result (geometry shaders, post-processing effects, etc.)</span></span>
4) <span data-ttu-id="66e1e-178">렌더링할 픽셀 수 (해상도 표시)</span><span class="sxs-lookup"><span data-stu-id="66e1e-178">Number of pixels to render (display resolution)</span></span>

#### <a name="reduce-polygon-count"></a><span data-ttu-id="66e1e-179">다각형 수 줄이기</span><span class="sxs-lookup"><span data-stu-id="66e1e-179">Reduce polygon count</span></span>

<span data-ttu-id="66e1e-180">다각형 수가 높을수록 GPU에 대 한 작업이 더 많이 발생 합니다. 장면의 [다각형 수를 줄이면](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) 렌더링 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-180">Higher polygon counts result in more operations for the GPU; [reducing the number of polygons](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in your scene will reduce the render time.</span></span> <span data-ttu-id="66e1e-181">비용이 많이 들 수 있는 기 하 도형에 음영을 지정 하는 다른 요인이 있지만 polygon 수는 장면을 렌더링 하는 데 소요 되는 비용을 결정 하는 가장 간단한 메트릭입니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-181">There are other factors involved in shading the geometry that can be expensive, but polygon count is the simplest metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="66e1e-182">과도 한 그리기 제한</span><span class="sxs-lookup"><span data-stu-id="66e1e-182">Limit overdraw</span></span>

<span data-ttu-id="66e1e-183">Occluding 개체에 의해 숨겨질 때 여러 개체가 렌더링 되지만 화면에 표시 되지 않는 경우에는 높은 오버 그리기가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-183">High overdraw occurs when multiple objects are rendered but not shown on screen as they are hidden by an occluding object.</span></span> <span data-ttu-id="66e1e-184">개체 뒤에 개체를 포함 하는 벽을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-184">Imagine looking at a wall that has objects behind it.</span></span> <span data-ttu-id="66e1e-185">모든 기 하 도형은 렌더링을 위해 처리 되지만 불투명 벽만 렌더링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-185">All of the geometry would be processed for rendering, but only the opaque wall needs to be rendered.</span></span> <span data-ttu-id="66e1e-186">이로 인해 불필요 한 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-186">This results in unnecessary operations.</span></span>

#### <a name="shaders"></a><span data-ttu-id="66e1e-187">셰이더</span><span class="sxs-lookup"><span data-stu-id="66e1e-187">Shaders</span></span>

<span data-ttu-id="66e1e-188">셰이더는 GPU에서 실행 되는 작은 프로그램으로, 렌더링에서 다음과 같은 두 가지 중요 한 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-188">Shaders are small programs that run on the GPU and perform two important steps in rendering:</span></span>
1) <span data-ttu-id="66e1e-189">그려야 하는 꼭 짓 점 및 화면 공간에 있는 위치 결정 (꼭 짓 점 셰이더)</span><span class="sxs-lookup"><span data-stu-id="66e1e-189">Determining which vertices should be drawn and where they are in screen space (the Vertex shader)</span></span>
    - <span data-ttu-id="66e1e-190">꼭 짓 점 셰이더는 일반적으로 모든 메시에 대해 꼭 짓 점에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-190">The Vertex shader is generally executed per vertex for every mesh.</span></span>
2) <span data-ttu-id="66e1e-191">각 픽셀의 색 확인 (픽셀 셰이더)</span><span class="sxs-lookup"><span data-stu-id="66e1e-191">Determining the color of each pixel (the Pixel shader)</span></span>
    - <span data-ttu-id="66e1e-192">픽셀 셰이더는 기 하 도형에 의해 렌더링 되는 질감에 대해 렌더링 되는 픽셀 마다 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-192">The Pixel shader is executed per pixel rendered by the geometry to the texture being rendered to.</span></span>

<span data-ttu-id="66e1e-193">일반적으로 셰이더는 많은 변환 및 조명 계산을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-193">Typically, shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="66e1e-194">복합 조명 모델, 그림자 및 기타 작업은 환상적인 결과를 생성할 수 있지만 가격과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-194">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="66e1e-195">셰이더에서 계산 된 작업의 수를 줄이면 프레임 당 GPU에 필요한 작업을 크게 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-195">Reducing the number of operations computed in shaders can greatly reduce the work needed for the GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="66e1e-196">셰이더 코딩 권장 사항</span><span class="sxs-lookup"><span data-stu-id="66e1e-196">Shader coding recommendations</span></span>

- <span data-ttu-id="66e1e-197">가능 하면 이중 선형 필터링 사용</span><span class="sxs-lookup"><span data-stu-id="66e1e-197">Use bilinear filtering, whenever possible</span></span>
- <span data-ttu-id="66e1e-198">곱하기 및 추가를 동시에 수행 하기 위해 MAD 내장 함수를 사용 하도록 식 다시 정렬</span><span class="sxs-lookup"><span data-stu-id="66e1e-198">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="66e1e-199">CPU에서 최대한 Precalculate 하 고 재질에 상수로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-199">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="66e1e-200">**픽셀 셰이더의 작업을 꼭 짓 점 셰이더로 이동 합니다.**</span><span class="sxs-lookup"><span data-stu-id="66e1e-200">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="66e1e-201">일반적으로 꼭 짓 점 수는 픽셀 수 (720p는 921600 픽셀, 1080p는 2073600 픽셀 등) 보다 훨씬 작습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-201">Generally, the number of vertices is much smaller than the number of pixels (720p is 921,600 pixels, 1080p is 2,073,600 pixels, etc.)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="66e1e-202">GPU 단계 제거</span><span class="sxs-lookup"><span data-stu-id="66e1e-202">Remove GPU stages</span></span>

<span data-ttu-id="66e1e-203">사후 처리 효과는 비용이 많이 들고 응용 프로그램의 채우기 비율이 높아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-203">Post-processing effects can be very expensive and increase the fill rate of your application.</span></span> <span data-ttu-id="66e1e-204">여기에는 MSAA와 같은 앤티앨리어싱 기술이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-204">This includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="66e1e-205">HoloLens에서는 이러한 기술을 완전히 피하는 것이 좋으며 geometry, 선체 및 compute 셰이더와 같은 추가 셰이더 단계를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-205">On HoloLens, it is recommended to avoid these techniques entirely, as well as additional shader stages such as geometry, hull, and compute shaders.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="66e1e-206">메모리 권장 사항</span><span class="sxs-lookup"><span data-stu-id="66e1e-206">Memory recommendations</span></span>

<span data-ttu-id="66e1e-207">과도 한 메모리 할당 및 할당 취소 작업을 수행 하면 일관 되지 않은 성능, 고정 된 프레임 및 기타 나쁜 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-207">Excessive memory allocation and deallocation operations can result in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="66e1e-208">메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-208">It is especially important to understand memory considerations when developing in Unity, since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="66e1e-209">개체 풀링</span><span class="sxs-lookup"><span data-stu-id="66e1e-209">Object pooling</span></span>

<span data-ttu-id="66e1e-210">개체 풀링은 연속 할당 및 개체 할당 해제 비용을 줄이는 인기 있는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-210">Object pooling is a popular technique to reduce the cost of continuous allocations and deallocations of objects.</span></span> <span data-ttu-id="66e1e-211">이 작업을 수행 하려면 시간이 지남에 따라 개체를 지속적으로 생성 및 제거 하는 대신 동일한 개체의 대량 풀을 할당 하 고이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-211">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="66e1e-212">개체 풀은 앱을 실행 하는 동안 변수 수명이 있는 다시 사용할 수 있는 구성 요소에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e1e-212">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="66e1e-213">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66e1e-213">See also</span></span>
- [<span data-ttu-id="66e1e-214">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="66e1e-214">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
- [<span data-ttu-id="66e1e-215">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="66e1e-215">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
- [<span data-ttu-id="66e1e-216">3D 모델 최적화</span><span class="sxs-lookup"><span data-stu-id="66e1e-216">Optimize 3D models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="66e1e-217">실시간 3D 모델 변환 및 최적화를 위한 모범 사례</span><span class="sxs-lookup"><span data-stu-id="66e1e-217">Best practices for converting and optimizing real-time 3D Models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

