---
title: Unity에 대 한 성능 권장 사항
description: 혼합된 현실 앱을 사용 하 여 성능 향상을 위해 unity 관련 팁.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 그래픽, cpu, gpu, hololens, 가비지 컬렉션, 렌더링
ms.openlocfilehash: 37eac566a0315009330ac7fee96edd82348d6ba3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604912"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="13ab4-104">Unity에 대 한 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="13ab4-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="13ab4-105">이 문서에 설명 된 설명을 기반 [혼합된 현실에 대 한 성능 권장 사항](understanding-performance-for-mixed-reality.md) Unity 엔진 환경에 특정 학습에 중점을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

<span data-ttu-id="13ab4-106">개발자의 검토는 좋습니다 이기도 합니다 [Unity 아티클에 대 한 환경 설정을 권장](Recommended-settings-for-unity.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-106">It is also highly advisable that developers review the [recommended environment settings for Unity article](Recommended-settings-for-unity.md).</span></span> <span data-ttu-id="13ab4-107">이 문서에 가장 중요 한 장면 구성의 일부를 사용 하 여 콘텐츠와 관련해 서 성능이 혼합 현실 앱 빌드</span><span class="sxs-lookup"><span data-stu-id="13ab4-107">This article has content with some of the most important scene configurations in regards to building performant Mixed Reality apps.</span></span> <span data-ttu-id="13ab4-108">권장 되는 이러한 설정 중 일부는 아래 강조 표시 된도 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-108">Some of these recommended settings are highlighted below as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="13ab4-109">Unity를 사용 하 여 프로 파일링 하는 방법</span><span class="sxs-lookup"><span data-stu-id="13ab4-109">How to profile with Unity</span></span>

<span data-ttu-id="13ab4-110">Unity를 제공 합니다 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 특정 앱에 대 한 중요 한 성능 정보를 수집할 수 있는 훌륭한 리소스는 기본 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-110">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="13ab4-111">하나는 프로파일러-편집기에서 실행할 수 있지만 이러한 메트릭을 true 런타임 환경을 나타내지 않으면 및 따라서이 결과로 사용할지 신중 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-111">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="13ab4-112">좋습니다 원격으로 프로필에 가장 정확 하 고 실행 가능한 정보에 대 한 장치에서 실행 되는 동안 응용 프로그램.</span><span class="sxs-lookup"><span data-stu-id="13ab4-112">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="13ab4-113">또한 Unity [프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html) 는 매우 강력 하 고 활용에 대 한 정보 도구 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-113">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)  is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="13ab4-114">Unity에 대 한 유용한 설명서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-114">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="13ab4-115">연결 하는 방법의 [Unity 프로파일러 UWP 응용 프로그램에 원격으로](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="13ab4-115">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="13ab4-116">하는 방법을 효과적으로 [Unity Profiler를 사용 하 여 성능 문제 진단](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="13ab4-116">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="13ab4-117">연결 된 Unity Profiler를 사용 하 여 및 GPU 프로파일러를 추가한 후 (참조 *Profiler 추가* 오른쪽 위 모서리에서), 얼마나 많은 시간이 소요 되는지 CPU 및 GPU에서 각각 프로파일러 중간 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-117">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="13ab4-118">이렇게 하면 개발자가 응용 프로그램 CPU 또는 GPU 경계가 지정 된 경우 빠른 근사값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-118">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 및 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="13ab4-120">CPU 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="13ab4-120">CPU performance recommendations</span></span>

<span data-ttu-id="13ab4-121">아래의 콘텐츠 특히 Unity를 대상으로 하는 자세한 심층 분석 성능 사례를 다룹니다 & C# 개발 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-121">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="13ab4-122">참조를 캐시</span><span class="sxs-lookup"><span data-stu-id="13ab4-122">Cache references</span></span>

<span data-ttu-id="13ab4-123">초기화 시 모든 관련 구성 요소 및 Gameobject에 참조를 캐시 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-123">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="13ab4-124">와 같은 함수 호출을 반복 하기 때문에 이것이 *[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 는 비용에 대 한 포인터를 저장 하는 메모리를 기준으로 훨씬 더 비쌉니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-124">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="13ab4-125">이에 적용 됩니다 하는 매우, 정기적으로 사용 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-125">This also applies to to the very, regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="13ab4-126">*Camera.main* 사용 하 여 실제로 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 더 포함 하는 카메라 개체에 대 한 장면 그래프를 검색 하는 아래를 *"MainCamera"*  태그입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-126">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] <span data-ttu-id="13ab4-127">Avoid GetComponent(string)</span><span class="sxs-lookup"><span data-stu-id="13ab4-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="13ab4-128">사용 하는 경우  *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, 몇 가지 다른 오버 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="13ab4-129">형식 기반 구현 및 되지 문자열 기반 검색 오버 로드를 사용 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-129">It is important to always use the Type based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="13ab4-130">장면에 대 한 문자열에서 검색 하는 것은 비용 유형별 검색 보다 훨씬 더 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="13ab4-131">(좋음) 구성 요소 GetComponent (형식)</span><span class="sxs-lookup"><span data-stu-id="13ab4-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="13ab4-132">(Good) T GetComponent\<T>()</span><span class="sxs-lookup"><span data-stu-id="13ab4-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="13ab4-133">(불량) 구성 요소 GetComponent(string) ></span><span class="sxs-lookup"><span data-stu-id="13ab4-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="13ab4-134">비용이 많이 드는 작업 방지</span><span class="sxs-lookup"><span data-stu-id="13ab4-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="13ab4-135">**사용 하지 않도록 [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="13ab4-135">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="13ab4-136">LINQ는 매우 명확 하 고 쉽게 읽기 및 쓰기 수를 사용할 수 있지만 일반적으로 훨씬 더 많은 계산 및 수동으로 알고리즘 작성 보다 특히 더 많은 메모리를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-136">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="13ab4-137">**일반적인 Unity Api**</span><span class="sxs-lookup"><span data-stu-id="13ab4-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="13ab4-138">특정 Unity Api 유용할 수 있습니다 실행 하는 데 비용이 많이 드는.</span><span class="sxs-lookup"><span data-stu-id="13ab4-138">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="13ab4-139">이들 중 대부분 Gameobject 일부 일치 하는 목록에 대 한 전체 장면 그래프를 검색 하는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="13ab4-140">일반적으로 참조를 캐싱 하거나 런타임에 대 한 참조를 추적 하려면 해당 Gameobject에 대 한 관리자 구성 요소를 구현 하 여 이러한 작업을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="13ab4-141">*[Sendmessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)*  하 고 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 중심지 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="13ab4-142">이러한 함수는 1000 배 직접적인 함수 호출에 비해 느리게 순서 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="13ab4-143">**Boxing에 주의 하세요.**</span><span class="sxs-lookup"><span data-stu-id="13ab4-143">**Beware of boxing**</span></span>

    <span data-ttu-id="13ab4-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) 는의 핵심 개념을 C# 언어 및 런타임입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="13ab4-145">참조 형식의 변수를 char, int, bool 등 값 형식 변수를 래핑하는 프로세스는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-145">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="13ab4-146">값 형식 변수는 "boxed", 관리 되는 힙에 저장 되어 있는 System.Object 내부 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-146">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="13ab4-147">따라서 메모리를 할당 및 삭제 하는 경우에 결국 가비지 수집기에서 처리 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-147">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="13ab4-148">이러한 할당 및 할당 취소 성능 비용이 발생 하 고 대부분의 시나리오에서 필요 하지 않습니다 또는 대신 비용이 저렴으로 쉽게 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

#### <a name="repeating-code-paths"></a><span data-ttu-id="13ab4-149">코드 경로 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-149">Repeating code paths</span></span>

<span data-ttu-id="13ab4-150">모든 반복 Unity 콜백 함수 (즉</span><span class="sxs-lookup"><span data-stu-id="13ab4-150">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="13ab4-151">업데이트) 초당 여러 번 실행 되는 및/또는 프레임을 매우 신중 하 게 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-151">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="13ab4-152">여기에 비용이 많이 드는 작업 성능에 큰 하 고 일관 된 영향을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-152">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="13ab4-153">**빈 콜백 함수**</span><span class="sxs-lookup"><span data-stu-id="13ab4-153">**Empty callback functions**</span></span>

    <span data-ttu-id="13ab4-154">아래 코드는 모든 Unity 스크립트 자동 초기화가 코드 블록을 사용 하 여 이후 특히 응용 프로그램에서 그대로 보일 수 있지만 비어 있는 이러한 콜백을 실제로 매우 많은 비용이 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-154">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="13ab4-155">Unity는 UnityEngine 코드 응용 프로그램 코드와 관리 되지 않는/관리 코드 경계를 통해 앞뒤로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-155">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="13ab4-156">이 브리지를 전환 하는 컨텍스트를 실행 하는 것이 없을 경우에 상당히 듭니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-156">Context switching over this bridge is fairly expensive even if there is nothing to execute.</span></span> <span data-ttu-id="13ab4-157">이 앱에 빈 반복 Unity 콜백 되는 구성 요소를 사용 하 여 Gameobject의 있으며 경우에 특히 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-157">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="13ab4-158">Update ()이 성능 문제의 가장 일반적인 특성 이지만 다음과 같은 다른 반복 Unity 콜백에 하지 나쁜 경우 불량 동일 하 게 될 수 있습니다. FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span><span class="sxs-lookup"><span data-stu-id="13ab4-158">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks such as the following can be equally as bad if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="13ab4-159">**작업을 한 번 실행 하는 중 무엇을 선호할 프레임당**</span><span class="sxs-lookup"><span data-stu-id="13ab4-159">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="13ab4-160">다음과 같은 Unity Api는 많은 Holographic 앱에 대 한 일반적인 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-160">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="13ab4-161">항상 가능 하지 않지만 결과 이러한 함수를 한 번 매우 일반적으로 계산할 수 있습니다 하 고 결과 지정된 된 프레임에 대 한 응용 프로그램에서 다시 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-161">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="13ab4-162">a) 일반적으로 것이 좋습니다는 전용 Singleton 클래스 또는 장면에 프로그램 게이즈 Raycast를 처리 한 다음 다른 모든 장면 구성 요소를 각각 사용 하 여 반복 되 고 기본적으로 동일한 Raycast 작업 하는 대신에이 결과 다시 사용 하는 서비스 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-162">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="13ab4-163">물론, 일부 응용 프로그램에서는 다른 원본에서 또는 다른 raycasts [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-163">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="13ab4-164">b)에서 update ()와 같은 반복 Unity 콜백에서 GetComponent() 작업 방지 [캐싱을 참조](#cache-references) start () 또는 Awake()</span><span class="sxs-lookup"><span data-stu-id="13ab4-164">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="13ab4-165">c)는 초기화 및 사용 가능한 경우 모든 개체를 인스턴스화하는 것이 좋습니다 [개체 풀링을](#object-pooling) 재활용 및 다시 Gameobject를 사용 하 여 전체 응용 프로그램의 런타임</span><span class="sxs-lookup"><span data-stu-id="13ab4-165">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="13ab4-166">**인터페이스 및 가상 구문을 방지합니다**</span><span class="sxs-lookup"><span data-stu-id="13ab4-166">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="13ab4-167">인터페이스 및 직접 개체를 통해 함수 호출을 실행 하거나 가상 함수를 호출 종종 수 직접 구문 또는 직접 함수 호출을 활용 하 여 보다 훨씬 더 비쌉니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-167">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="13ab4-168">가상 함수 또는 인터페이스 필요가 없는 경우을 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-168">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="13ab4-169">그러나 이러한 접근 방식을 위한 성능 저하가 일반적으로 절충 만한 개발 공동 작업, 코드 가독성 및 코드 유지 관리를 단순화 활용 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="13ab4-169">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span> 

4) <span data-ttu-id="13ab4-170">**값으로 전달 구조체 방지**</span><span class="sxs-lookup"><span data-stu-id="13ab4-170">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="13ab4-171">클래스와 달리 구조체는 값 형식 및 해당 내용을 새로 만든된 인스턴스에 복사 되므로 함수에 직접 전달 되 면 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-171">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="13ab4-172">이 복사본 비용 스택에 추가 메모리와 CPU를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-172">This copy adds CPU cost as well as additional memory on the stack.</span></span> <span data-ttu-id="13ab4-173">작은 구조체에 대 한 효과가 일반적으로 매우 최소화 하 고 있으므로 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-173">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="13ab4-174">함수는 반복적으로 프레임 마다 호출에 대 한 뿐만 아니라 큰 구조체를 수행 하는 함수, 함수 정의 참조로 전달 하려면 가능한 경우 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-174">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="13ab4-175">자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="13ab4-175">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="13ab4-176">기타</span><span class="sxs-lookup"><span data-stu-id="13ab4-176">Miscellaneous</span></span>

1) <span data-ttu-id="13ab4-177">**물리학**</span><span class="sxs-lookup"><span data-stu-id="13ab4-177">**Physics**</span></span>

    <span data-ttu-id="13ab4-178">a) 일반적으로 물리학을 개선 하기 위해 쉬운 물리학 또는 초당 반복 횟수에 소요 된 시간의 양을 제한 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-178">a) Generally, easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="13ab4-179">물론,이 시뮬레이션 정확도를 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-179">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="13ab4-180">참조 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) Unity에서</span><span class="sxs-lookup"><span data-stu-id="13ab4-180">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="13ab4-181">b) 유형의 colliders Unity에서 광범위 하 게 다른 성능 특징을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-181">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="13ab4-182">아래와 같은 순서로 왼쪽에서 오른쪽으로 가장 성능이 뛰어난 colliders에 대부분의 고성능 colliders를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-182">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="13ab4-183">기본 colliders 보다 훨씬 더 비쌉니다는 메시 Colliders를 방지 하려면 가장 중요 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-183">It is most important to avoid Mesh Colliders which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="13ab4-184">참조 [Unity 물리학 모범 사례](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) 자세한 내용을 보려면</span><span class="sxs-lookup"><span data-stu-id="13ab4-184">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="13ab4-185">**애니메이션**</span><span class="sxs-lookup"><span data-stu-id="13ab4-185">**Animations**</span></span>

    <span data-ttu-id="13ab4-186">애니메이터 구성 요소를 사용 하지 않도록 설정 하 여 유휴 애니메이션을 사용 하지 않도록 설정 (게임 개체를 사용 하지 않도록 설정 하지 않습니다 동일한 효과가).</span><span class="sxs-lookup"><span data-stu-id="13ab4-186">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="13ab4-187">디자인 패턴을 애니메이터 동일한 항목 값을 설정 하는 루프에 위치 하는 위치를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-187">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="13ab4-188">응용 프로그램에 영향을 주지이 기술의 경우 상당한 오버 헤드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-188">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="13ab4-189">여기에서 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="13ab4-189">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="13ab4-190">**복잡 한 알고리즘**</span><span class="sxs-lookup"><span data-stu-id="13ab4-190">**Complex algorithms**</span></span>

    <span data-ttu-id="13ab4-191">응용 프로그램 역 운동학, 경로 찾기 등과 같은 복잡 한 알고리즘을 사용 하는 경우 간단 하거나 성능에 대 한 관련 설정을 조정 확인</span><span class="sxs-lookup"><span data-stu-id="13ab4-191">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="13ab4-192">CPU-GPU 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="13ab4-192">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="13ab4-193">CPU-GPU 성능으로 제공 되는 일반적으로 **그리기 호출** 그래픽 카드에 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-193">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="13ab4-194">성능 향상을 위해 그리기 호출 해야 전략적 **a) 감소** 또는 **b) 재구성** 최적의 결과 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-194">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="13ab4-195">자체 그리기 호출의 리소스를 많이 사용 되므로 감소 하는 데 필요한 전체 작업을 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-195">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="13ab4-196">또한 비용이 많이 드는 유효성 검사를 요구 하는 그리기 호출 간에 변경 내용 및 그래픽 드라이버의 변환 단계 상태 및 상태 변경 (즉, 제한에 대 한 그리기 호출 응용 프로그램의 구조 즉,</span><span class="sxs-lookup"><span data-stu-id="13ab4-196">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes(i.e</span></span> <span data-ttu-id="13ab4-197">다른 자료 등)에 성능을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-197">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="13ab4-198">Unity 개요를 제공 합니다. 해당 플랫폼에 대 한 그리기 호출을 일괄 처리 설명 하는 훌륭한 기사를 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-198">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="13ab4-199">Unity 그리기 호출 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="13ab4-199">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="13ab4-200">단일 패스 인스턴스화된 렌더링</span><span class="sxs-lookup"><span data-stu-id="13ab4-200">Single pass instanced rendering</span></span>

<span data-ttu-id="13ab4-201">Unity에서 단일 패스 Instanced 렌더링 하나 인스턴스화된 그리기 호출까지 줄여야 각 눈에 대 한 그리기 호출을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-201">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="13ab4-202">두 그리기 호출 간에 캐시 일관성, 인해도 GPU에서 성능 향상도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-202">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="13ab4-203">Unity 프로젝트에서이 기능을 사용 하도록 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="13ab4-203">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="13ab4-204">오픈 **플레이어 xr 하이 설정을** (이동 **편집** > **프로젝트 설정** > **Player**  >  **Xr 하이 설정을**)</span><span class="sxs-lookup"><span data-stu-id="13ab4-204">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="13ab4-205">선택 **단일 전달 인스턴스화된** 에서 합니다 **스테레오 렌더링 메서드** 드롭 다운 메뉴 (**지원 되는 가상 현실** 확인란을 선택 해야 합니다)</span><span class="sxs-lookup"><span data-stu-id="13ab4-205">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="13ab4-206">이 렌더링 방법 세부 정보에 대 한 Unity에서 다음 문서를 읽어봅니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-206">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="13ab4-207">고급 스테레오 렌더링 AR 및 VR 성능을 최대화 하는 방법</span><span class="sxs-lookup"><span data-stu-id="13ab4-207">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="13ab4-208">단일 패스 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="13ab4-208">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="13ab4-209">개발자가 기존 사용자 지정 셰이더 용으로 작성 되지가 이미 있으면 단일 전달 렌더링 인스턴스화된 다음 한 가지 일반적인 문제가 발생 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="13ab4-209">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="13ab4-210">개발자는이 기능을 사용 하도록 설정한 후 일부 Gameobject만 렌더링 한 눈에 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-210">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="13ab4-211">사용자 지정 셰이더를 연결된에 대 한 적절 한 속성을 없기 때문에 이것이 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="13ab4-211">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="13ab4-212">참조 [단일 전달 스테레오에 대 한 렌더링 HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) 이 문제를 해결 하는 방법에 대 한 Unity에서</span><span class="sxs-lookup"><span data-stu-id="13ab4-212">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="13ab4-213">정적 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="13ab4-213">Static batching</span></span>

<span data-ttu-id="13ab4-214">Unity는 GPU 그리기 호출을 줄이기 위해 많은 정적 개체를 일괄 처리 수입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-214">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="13ab4-215">대부분 사용할 수 있는 정적 일괄 처리 [렌더러](https://docs.unity3d.com/ScriptReference/Renderer.html) Unity의 개체는 **1)-동일한 자료를 공유 하는 중** 하 고 **2)는 모두로 표시 *정적***  ( Unity에서 개체를 선택 하 고 위에 있는 확인란을 클릭 하 고 관리자의 오른쪽).</span><span class="sxs-lookup"><span data-stu-id="13ab4-215">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="13ab4-216">로 표시 된 Gameobject *정적* 응용 프로그램의 런타임 전체에서 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-216">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="13ab4-217">따라서 정적 일괄 처리 거의 모든 개체 이동, 확장 등 배치할 해야 하는 HoloLens에 활용 하기 어려울 수 있습니다. 몰입 형 헤드셋에 대 한 정적 일괄 처리 수 그리기 호출을 크게 줄일 수 및 성능을 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-217">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="13ab4-218">읽기 *정적 일괄 처리* 아래에서 [그리기 호출 Unity에서 일괄 처리를](https://docs.unity3d.com/Manual/DrawCallBatching.html) 대 한 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-218">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="13ab4-219">동적 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="13ab4-219">Dynamic batching</span></span>

<span data-ttu-id="13ab4-220">개체를 표시 하는 문제가 있는 이므로 *정적* HoloLens 개발을 위한 동적 일괄 처리 수는이 보완 하는 데 유용한 도구 기능 부족 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-220">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="13ab4-221">수는 물론, 몰입 형 헤드셋도에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-221">Of course, it is can also be useful on immersive headsets as well.</span></span> <span data-ttu-id="13ab4-222">Unity에서 일괄 처리를 동적 어려울 수 있습니다 하지만 Gameobject 해야 하기 때문에 사용할 수 있도록 **a) 공유 같은 자료가** 하 고 **b) 긴 목록을 다른 조건 충족**.</span><span class="sxs-lookup"><span data-stu-id="13ab4-222">Dynamic batching in Unity can be difficult though to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="13ab4-223">읽기 *동적 일괄 처리* 아래에서 [그리기 호출 Unity에서 일괄 처리를](https://docs.unity3d.com/Manual/DrawCallBatching.html) 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-223">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="13ab4-224">가장 일반적으로 Gameobject 연결된 메시 데이터 300 개 꼭 짓 점 수 있기 때문에 동적으로 일괄 처리할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-224">Most commonly, GameObjects become invalid to be batched dynamically because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="13ab4-225">기타 기술</span><span class="sxs-lookup"><span data-stu-id="13ab4-225">Other techniques</span></span>

<span data-ttu-id="13ab4-226">일괄 처리 여러 Gameobject가 동일한 자료를 공유할 수 있는 경우만 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-226">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="13ab4-227">일반적으로 해당 해당 자료에 대 한 고유 질감 할 Gameobject 필요할 경우이 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-227">Typically this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="13ab4-228">일반적으로 하나의 큰 질감 이라고 하는 방법이 질감 결합 [질감 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-228">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="13ab4-229">또한 것 가능 하 고 적절 한 경우 하나의 GameObject 메시를 결합 하는 것이 일반적으로 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-229">Further, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="13ab4-230">Unity에서 각 렌더러를 갖게 하나 렌더러에서 결합 된 메시를 제출 및 그리기 호출에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-230">Each Renderer in Unity will have it's associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span> 

>[!NOTE]
> <span data-ttu-id="13ab4-231">런타임 시 Renderer.material의 속성을 수정 자료의 복사본 만들기를 따라서 손상 될 일괄 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-231">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="13ab4-232">Renderer.sharedMaterial를 사용 하 여 Gameobject 간에 공유 material 속성을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-232">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="13ab4-233">GPU 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="13ab4-233">GPU performance recommendations</span></span>

<span data-ttu-id="13ab4-234">자세한 내용은 [Unity에서 그래픽 렌더링 최적화](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="13ab4-234">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

#### <a name="reduce-poly-count"></a><span data-ttu-id="13ab4-235">예: poly 수 축소</span><span class="sxs-lookup"><span data-stu-id="13ab4-235">Reduce poly count</span></span>

<span data-ttu-id="13ab4-236">일반적으로 다각형 수가으로 감소</span><span class="sxs-lookup"><span data-stu-id="13ab4-236">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="13ab4-237">장면에서 개체 제거</span><span class="sxs-lookup"><span data-stu-id="13ab4-237">Removing objects from a scene</span></span>
2) <span data-ttu-id="13ab4-238">특정된 메시에 대 한 다각형 줄어듭니다 자산 부분 제거</span><span class="sxs-lookup"><span data-stu-id="13ab4-238">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="13ab4-239">구현 된 [세부 정보 수준 (LOD) 시스템](https://docs.unity3d.com/Manual/LevelOfDetail.html) 멀리 동일한 기 하 도형의 다각형 낮은 버전을 사용 하 여 개체를 렌더링 하는 응용 프로그램에</span><span class="sxs-lookup"><span data-stu-id="13ab4-239">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="13ab4-240">제한 overdraw</span><span class="sxs-lookup"><span data-stu-id="13ab4-240">Limit overdraw</span></span>

<span data-ttu-id="13ab4-241">Unity에서 표시할 수 있습니다 하나로 전환 하 여 overdraw가 장면에 대 한 합니다 [ **그리기 모드 메뉴** ](https://docs.unity3d.com/Manual/ViewModes.html) 의 왼쪽된 위 모퉁이에 **장면 보기로** 선택 하 고 **Overdraw** .</span><span class="sxs-lookup"><span data-stu-id="13ab4-241">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="13ab4-242">일반적으로 overdraw GPU에 전송 되기 전에 미리 개체를 선별 하 여 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-242">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="13ab4-243">구현 세부 정보를 제공 하는 unity [폐색 고르기](https://docs.unity3d.com/Manual/OcclusionCulling.html) 해당 엔진에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-243">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

#### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="13ab4-244">Unity에서 이해 셰이더</span><span class="sxs-lookup"><span data-stu-id="13ab4-244">Understanding shaders in Unity</span></span>

<span data-ttu-id="13ab4-245">성능에서 셰이더를 비교할 쉽게 근사치가 각 작업의 평균 수를 확인 하기 위해 런타임 시 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-245">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="13ab4-246">이 Unity의 매우 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-246">This can be done fairly easily in Unity.</span></span>

1) <span data-ttu-id="13ab4-247">셰이더 자산을 선택 하거나, 재질을 선택한 다음 검사기 창의 오른쪽 위 모서리에서 기어 아이콘을 선택 하 고 다음 **"셰이더 선택"**</span><span class="sxs-lookup"><span data-stu-id="13ab4-247">Select your shader asset or select a material, then in top right corner of the inspector window, select the gear icon and then **"Select Shader"**</span></span>

    ![Unity에서 셰이더를 선택 합니다.](images/Select-shader-unity.png)
2) <span data-ttu-id="13ab4-249">선택한 셰이더 자산을 클릭 합니다 **"컴파일 및 코드를 표시"** 검사기 창 아래의 단추</span><span class="sxs-lookup"><span data-stu-id="13ab4-249">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![Unity에서 셰이더 코드 컴파일](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="13ab4-251">컴파일 후 확인 결과에 통계 섹션에 대 한 꼭 짓 점 및 픽셀 셰이더에 대 한 다른 작업의 수를 사용 하 여 (참고: 픽셀 셰이더는 종종 라고도 조각 셰이더)</span><span class="sxs-lookup"><span data-stu-id="13ab4-251">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 표준 셰이더 작업](images/unity-standard-shader-compilation.png)

##### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="13ab4-253">Unity 표준 셰이더 대안</span><span class="sxs-lookup"><span data-stu-id="13ab4-253">Unity Standard shader alternatives</span></span>

<span data-ttu-id="13ab4-254">실제로 기반된 렌더링 (PBR) 또는 다른 고품질 셰이더를 사용 하는 대신 확인는 뛰어난 성능을 활용 하 고 저렴 한 셰이더입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-254">Instead of using a physically based rendering (PBR) or other high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="13ab4-255">[혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity) 제공을 [표준 셰이더](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader) 혼합된 현실 프로젝트에 대 한 최적화 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-255">[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a [standard shader](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="13ab4-256">Unity는 표준 Unity 셰이더에 켜지, 활성화 하는 꼭 짓 점, 훨씬 더 빠르게 비교 하는 간소화 된 셰이더 확산, 및 기타 옵션 또한 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-256">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="13ab4-257">참조 [사용 및 기본 제공 셰이더 성능](https://docs.unity3d.com/Manual/shader-Performance.html) 좀 더 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-257">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="13ab4-258">메모리 권장 사항</span><span class="sxs-lookup"><span data-stu-id="13ab4-258">Memory recommendations</span></span>

<span data-ttu-id="13ab4-259">과도 한 메모리 할당 및 할당 취소 작업에는 일관 되지 않은 성능, 고정 된 프레임 및 기타 나쁜 동작의 결과 holographic 응용 프로그램에 부정적인 영향을 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-259">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="13ab4-260">특히 메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-260">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="13ab4-261">가비지 수집</span><span class="sxs-lookup"><span data-stu-id="13ab4-261">Garbage collection</span></span>

<span data-ttu-id="13ab4-262">Holographic 앱 GC는 더 이상 범위에서 실행 하는 동안 개체를 분석 하기 활성화 되 고 해당 메모리를 다시 사용할 수 있는 만들 수 있도록 해제 해야 하는 경우 가비지 수집기 (GC) 처리 계산 시간을 잃게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-262">Holographic apps will loose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released so it can be made available for re-use.</span></span> <span data-ttu-id="13ab4-263">상수 할당 및 할당 취소가 가비지 수집기가 성능 저하의 원인이 되므로 및 사용자 환경을 더 자주 실행 하려면 일반적으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-263">Constant allocations and de-allocations will generally require the garbage collector to run more frequently thus hurting performance and user experience.</span></span>

<span data-ttu-id="13ab4-264">Unity는 가비지 수집기의 작동 방식을 자세히 설명 하는 뛰어난 페이지 및 메모리 관리와 관련해 서에서 더 효율적인 코드를 작성 하기 위한 팁을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-264">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="13ab4-265">Unity 게임에서 가비지 수집을 최적화</span><span class="sxs-lookup"><span data-stu-id="13ab4-265">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="13ab4-266">과도 한 가비지 수집을 발생 시키는 가장 일반적인 사례 중 하나가 Unity 개발의 클래스 및 구성 요소에 대 한 참조가 캐시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-266">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="13ab4-267">모든 참조 start () 또는 Awake() 중 캡처된 있고 LateUpdate() update () 등 나중의 함수에서 다시 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-267">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="13ab4-268">기타 빠른 팁:</span><span class="sxs-lookup"><span data-stu-id="13ab4-268">Other quick tips:</span></span>
- <span data-ttu-id="13ab4-269">사용 된 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 동적으로 런타임 시 복잡 한 문자열을 작성 하는 클래스</span><span class="sxs-lookup"><span data-stu-id="13ab4-269">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="13ab4-270">더 이상 필요 없는 앱의 모든 빌드 버전에서 계속 실행 될 때 Debug.Log() 호출 제거</span><span class="sxs-lookup"><span data-stu-id="13ab4-270">Remove calls to Debug.Log() when no longer needed as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="13ab4-271">Holographic 앱에는 일반적으로 메모리가 많이 필요한 경우에 호출 해 보십시오 [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) 같은 단계를 로드 하는 동안 로드를 제공 하는 경우 또는 전환 화면</span><span class="sxs-lookup"><span data-stu-id="13ab4-271">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="13ab4-272">개체 풀링</span><span class="sxs-lookup"><span data-stu-id="13ab4-272">Object pooling</span></span>

<span data-ttu-id="13ab4-273">개체 풀링은 연속 할당의 비용 및 개체의 할당 취소를 위해 널리 사용 되는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-273">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="13ab4-274">이 동일한 개체의 대형 풀을 할당 하 고 다시 지속적으로 생성 하 고 시간이 지남에 따라 개체를 제거 하는 대신이 풀에서 비활성, 사용 가능한 인스턴스를 사용 하 여 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-274">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="13ab4-275">개체 풀은 앱 중 변수 수명에 있는 다시 사용 가능한 구성 요소에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-275">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="13ab4-276">개체 풀링 Unity의 자습서</span><span class="sxs-lookup"><span data-stu-id="13ab4-276">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="13ab4-277">시작 성능</span><span class="sxs-lookup"><span data-stu-id="13ab4-277">Startup performance</span></span>

<span data-ttu-id="13ab4-278">더 작은 장면으로 시작 하는 앱을 사용 하 여 고려해 야 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 장면의 나머지 부분을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-278">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="13ab4-279">이렇게 하면 최대한 빨리 대화형 상태를 얻기 위해 응용 프로그램.</span><span class="sxs-lookup"><span data-stu-id="13ab4-279">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="13ab4-280">인식 하는 있을 수 있습니다.는 CPU 사용량이 엄청나게 급증 동안 새 장면을 활성화 되 고 있으며 렌더링 된 내용을 끊길 수 있습니다. 있는지 또는 다른 점이 있다면 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-280">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="13ab4-281">이 문제를 해결 하는 하나 방법은 로드 되 고 장면 AsyncOperation.allowSceneActivation 속성을 false로 설정 하려면 장면 로드을 검정으로, 화면의 선택을 취소 한 다음 다시 장면 정품 인증을 완료 하려면 true로 설정 될 때까지 기다리는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-281">One way to work around this is to set the AsyncOperation.allowSceneActivation property to false on the scene being loaded, wait for the scene to load, clear the screen to black, and then set back to true to complete the scene activation.</span></span>

<span data-ttu-id="13ab4-282">기억 시작 화면이 로드 되는 동안 holographic 시작 화면이 사용자에 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13ab4-282">Remember that while the startup scene is loading the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="13ab4-283">참조</span><span class="sxs-lookup"><span data-stu-id="13ab4-283">See also</span></span>
- [<span data-ttu-id="13ab4-284">Unity 게임 그래픽 렌더링 최적화</span><span class="sxs-lookup"><span data-stu-id="13ab4-284">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="13ab4-285">Unity 게임에서 가비지 수집을 최적화</span><span class="sxs-lookup"><span data-stu-id="13ab4-285">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="13ab4-286">[물리학 모범 사례 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="13ab4-286">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="13ab4-287">[스크립트 [Unity] 최적화](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="13ab4-287">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
