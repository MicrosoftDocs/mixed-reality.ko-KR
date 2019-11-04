---
title: Unity에 대 한 성능 권장 사항
description: 혼합 현실 앱을 사용 하 여 성능을 향상 시킬 수 있는 Unity 관련 팁입니다.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 그래픽, cpu, gpu, 렌더링, 가비지 수집, hololens
ms.openlocfilehash: 724ec24408e70360fda07c59a4ca2ffc30b49c1f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438122"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="05971-104">Unity에 대 한 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="05971-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="05971-105">이 문서는 [혼합 현실에 대 한 성능 권장 사항](understanding-performance-for-mixed-reality.md) 에 설명 된 토론을 기반으로 하지만 Unity 엔진 환경과 관련 된 학습에 중점을 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

<span data-ttu-id="05971-106">또한 개발자는 [Unity의 권장 환경 설정 문서](Recommended-settings-for-unity.md)를 검토 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-106">It is also highly advisable that developers review the [recommended environment settings for Unity article](Recommended-settings-for-unity.md).</span></span> <span data-ttu-id="05971-107">이 문서에는 고성능 혼합 현실 앱을 빌드하는 것과 관련 하 여 가장 중요 한 장면 구성의 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-107">This article has content with some of the most important scene configurations in regards to building performant Mixed Reality apps.</span></span> <span data-ttu-id="05971-108">이러한 권장 설정 중 일부는 아래에도 강조 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-108">Some of these recommended settings are highlighted below as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="05971-109">Unity를 사용 하 여 프로 파일링 하는 방법</span><span class="sxs-lookup"><span data-stu-id="05971-109">How to profile with Unity</span></span>

<span data-ttu-id="05971-110">Unity는 특정 앱에 대 한 중요 한 성능 정보를 수집 하는 데 유용한 리소스인 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 를 기본 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-110">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="05971-111">편집기에서 프로파일러를 실행할 수는 있지만 이러한 메트릭은 진정한 런타임 환경을 나타내지 않으므로이에 대 한 결과는 신중 하 게 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-111">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="05971-112">가장 정확 하 고 실행 가능한 정보를 얻기 위해 장치에서 실행 되는 동안 응용 프로그램을 원격으로 프로 파일링 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-112">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="05971-113">또한 Unity의 [프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html) 는 활용할 수 있는 매우 강력 하 고 통찰력 있는 도구 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-113">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)  is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="05971-114">Unity는 다음에 대 한 유용한 설명서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-114">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="05971-115">[Unity 프로파일러를 UWP 응용 프로그램에 원격](https://docs.unity3d.com/Manual/windowsstore-profiler.html) 으로 연결 하는 방법</span><span class="sxs-lookup"><span data-stu-id="05971-115">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="05971-116">[Unity Profiler를 사용 하 여 성능 문제](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window) 를 효과적으로 진단 하는 방법</span><span class="sxs-lookup"><span data-stu-id="05971-116">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="05971-117">Unity 프로파일러를 연결 하 고 GPU 프로파일러를 추가한 후 (오른쪽 위 모서리의 *프로파일러 추가* 참조) 프로파일러 중에 CPU & gpu에서 각각 얼마나 많은 시간이 소요 되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-117">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="05971-118">이를 통해 개발자는 응용 프로그램이 CPU 또는 GPU 바인딩된 경우 빠른 근사값을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-118">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 및 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="05971-120">CPU 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="05971-120">CPU performance recommendations</span></span>

<span data-ttu-id="05971-121">아래 내용은 특히 Unity & C# 개발을 대상으로 하는 자세한 성능 관행을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-121">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="05971-122">캐시 참조</span><span class="sxs-lookup"><span data-stu-id="05971-122">Cache references</span></span>

<span data-ttu-id="05971-123">모든 관련 구성 요소에 대 한 참조와 초기화 시 Gameobject를 캐시 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-123">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="05971-124">이는 *[Getcomponent\<t > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 와 같은 반복 함수 호출이 포인터를 저장 하는 메모리 비용에 비해 훨씬 더 비쌉니다.</span><span class="sxs-lookup"><span data-stu-id="05971-124">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="05971-125">이는 정기적으로 사용 되는 가장 많이 사용 되는 [카메라 주](https://docs.unity3d.com/ScriptReference/Camera-main.html)에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-125">This also applies to to the very, regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="05971-126">FindGameObjectsWithTag *는 실제로 저렴* 가 *"maincamera"* 태그가 있는 카메라 개체에 대 한 장면 그래프를 검색 하는 *[()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-126">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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

>[!NOTE] 
> <span data-ttu-id="05971-127">GetComponent (string) 사용 안 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="05971-128">*[Getcomponent ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 를 사용 하는 경우 몇 가지 오버 로드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="05971-129">항상 형식 기반 구현을 사용 하 고 문자열 기반 검색 오버 로드를 사용 하지 않는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-129">It is important to always use the Type based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="05971-130">장면에서 문자열로 검색 하는 것은 유형별로 검색 하는 것 보다 훨씬 더 비쌉니다.</span><span class="sxs-lookup"><span data-stu-id="05971-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="05971-131">좋음 구성 요소 GetComponent (Type 유형)</span><span class="sxs-lookup"><span data-stu-id="05971-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="05971-132">좋음 T GetComponent\<T > ()</span><span class="sxs-lookup"><span data-stu-id="05971-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="05971-133">올바르지 구성 요소 GetComponent (문자열) ></span><span class="sxs-lookup"><span data-stu-id="05971-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="05971-134">비용이 많이 드는 작업 방지</span><span class="sxs-lookup"><span data-stu-id="05971-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="05971-135">**[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq) 사용 방지**</span><span class="sxs-lookup"><span data-stu-id="05971-135">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="05971-136">LINQ는 매우 깔끔하고 쉽게 읽고 쓸 수 있지만 일반적으로 알고리즘을 수동으로 작성 하는 것 보다 훨씬 더 많은 계산과 특히 더 많은 메모리 할당이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-136">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="05971-137">**Common Unity Api**</span><span class="sxs-lookup"><span data-stu-id="05971-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="05971-138">유용 하지만 특정 Unity Api를 실행 하는 데 비용이 많이 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-138">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="05971-139">이러한 항목 중 대부분은 일부 일치 하는 Gameobject 목록에 대 한 전체 장면 그래프 검색을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="05971-140">이러한 작업은 일반적으로 참조를 캐시 하거나 런타임에 참조를 추적 하는 Gameobject에 대 한 관리자 구성 요소를 구현 하 여 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="05971-141">*[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 및 *[BroadcastMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 는 모든 비용으로 제거 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="05971-142">이러한 함수는 직접 함수 호출 보다 100% 더 느릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="05971-143">**Boxing 유의**</span><span class="sxs-lookup"><span data-stu-id="05971-143">**Beware of boxing**</span></span>

    <span data-ttu-id="05971-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) 은 C# 언어 및 런타임의 핵심 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="05971-145">Char, int, bool 등의 값 형식 변수를 참조 형식 변수로 래핑하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-145">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="05971-146">값으로 형식화 된 변수가 "boxed" 이면 관리 되는 힙에 저장 된 System.object의 내부에 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-146">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="05971-147">따라서 가비지 수집기에서 메모리를 할당 하 고 결국 삭제를 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-147">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="05971-148">이러한 할당과 할당 해제는 성능 비용을 초래 하 고 많은 시나리오에서 불필요 하거나 더 저렴 한 방법으로 쉽게 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="05971-149">개발에서 boxing의 가장 일반적인 형태 중 하나는 [nullable 값 형식을](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-149">One of the most common forms of boxing in development is the use of [nullable value types](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/).</span></span> <span data-ttu-id="05971-150">일반적으로 작업에서 값을 가져오려고 할 때 오류가 발생 하는 경우 함수에서 값 형식에 대해 null을 반환할 수 있기를 원합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-150">It is common to want to be able to return null for a value type in a function especially when the operation may fail trying to get the value.</span></span> <span data-ttu-id="05971-151">이 방법의 잠재적인 문제는 이제 힙에서 할당이 발생 하므로 나중에 가비지를 수집 해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-151">The potential problem with this approach is that allocation now occur on the heap and consequently need to be garbage collected later.</span></span>

    <span data-ttu-id="05971-152">**의 boxing 예C#**</span><span class="sxs-lookup"><span data-stu-id="05971-152">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    <span data-ttu-id="05971-153">**Nullable 값 형식을 통한 문제 boxing의 예**</span><span class="sxs-lookup"><span data-stu-id="05971-153">**Example of problematic boxing via nullable value types**</span></span>

    <span data-ttu-id="05971-154">이 코드는 Unity 프로젝트에서 만들 수 있는 더미 파티클 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="05971-154">This code demonstrates a dummy particle class that one may create in a Unity project.</span></span> <span data-ttu-id="05971-155">`TryGetSpeed()`를 호출 하면 힙에 대 한 개체 할당이 발생 하며,이는 나중에 가비지 수집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-155">A call to `TryGetSpeed()` will cause object allocation on the heap which will need to be garbage collected at a later point in time.</span></span> <span data-ttu-id="05971-156">이 예제는 특히 현재 속도를 요청 하는 장면에 1000 개 이상의 파티클이 있을 수 있기 때문에 문제가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-156">This example is particularly problematic as there may be 1000+ or many more particles in a scene, each being asked for their current speed.</span></span> <span data-ttu-id="05971-157">따라서 1000 개의 개체가 할당 되 고 결과적으로 성능이 크게 저하 되는 모든 프레임을 할당 취소 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-157">Thus, 1000's of objects would be allocated and consequently de-allocated every frame which would greatly diminish performance.</span></span> <span data-ttu-id="05971-158">오류를 나타내기 위해-1과 같은 음수 값을 반환 하는 함수를 다시 작성 하면이 문제를 방지 하 고 스택에 메모리를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-158">Re-writing the function to return a negative value such as -1 to indicate a failure would avoid this issue and keep memory on the stack.</span></span>

    ```csharp
        public class MyParticle
        {
            // Example of function returning nullable value type
            public int? TryGetSpeed()
            {
                // Returns current speed int value or null if fails
            }
        }
    ```

#### <a name="repeating-code-paths"></a><span data-ttu-id="05971-159">반복 코드 경로</span><span class="sxs-lookup"><span data-stu-id="05971-159">Repeating code paths</span></span>

<span data-ttu-id="05971-160">반복 Unity 콜백 함수 (즉,</span><span class="sxs-lookup"><span data-stu-id="05971-160">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="05971-161">초당 여러 번 실행 되는 업데이트) 및/또는 프레임을 매우 신중 하 게 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-161">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="05971-162">여기에서 비용이 많이 드는 작업은 성능에 크게 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-162">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="05971-163">**빈 콜백 함수**</span><span class="sxs-lookup"><span data-stu-id="05971-163">**Empty callback functions**</span></span>

    <span data-ttu-id="05971-164">아래 코드는 응용 프로그램에 남겨 두는 것 처럼 보일 수 있지만, 특히 모든 Unity 스크립트는이 코드 블록을 사용 하 여 자동으로 초기화 되기 때문에 이러한 빈 콜백은 실제로 매우 많은 비용이 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-164">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="05971-165">Unity는 UnityEngine 코드와 응용 프로그램 코드 간에 관리 되지 않는/관리 코드 경계를 앞뒤로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-165">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="05971-166">이 브리지를 통해 컨텍스트를 전환 하는 것은 실행할 작업이 없는 경우에도 매우 비용이 많이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="05971-166">Context switching over this bridge is fairly expensive even if there is nothing to execute.</span></span> <span data-ttu-id="05971-167">이는 응용 프로그램에 비어 있는 반복 Unity 콜백이 있는 구성 요소가 있는 100 개의 Gameobject 있는 경우 특히 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-167">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="05971-168">Update ()는이 성능 문제의 가장 일반적인 노력 이지만, 다음과 같은 다른 반복 Unity 콜백은 FixedUpdate (), Behaviour (), OnPostRender ", OnPreRender (), OnRenderImage () 등의 경우와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-168">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks such as the following can be equally as bad if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="05971-169">**프레임당 한 번 실행 되도록 하는 작업**</span><span class="sxs-lookup"><span data-stu-id="05971-169">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="05971-170">다음 Unity Api는 많은 Holographic 앱에 대 한 일반적인 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-170">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="05971-171">항상 가능한 것은 아니지만 이러한 함수의 결과는 일반적으로 한 번 계산 되 고 결과는 지정 된 프레임에 대 한 응용 프로그램 전체에서 다시 사용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-171">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="05971-172">a) 일반적으로 반복 되 고 본질적으로 동일한 Raycast 작업을 수행 하는 대신 다른 모든 장면 구성 요소에서이 결과를 다시 사용 하는 전용 Singleton 클래스 또는 서비스를 사용 하는 것이 좋습니다. 구성 요소.</span><span class="sxs-lookup"><span data-stu-id="05971-172">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="05971-173">물론 일부 응용 프로그램의 경우 다른 원본 또는 다른 [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)에 대 한 raycasts를 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-173">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="05971-174">b) Start () 또는 s a s n ()에서 [참조를 캐싱하여](#cache-references) Update ()와 같은 반복 Unity 콜백에서 getcomponent () 작업을 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-174">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="05971-175">c) 응용 프로그램의 전체 런타임에 Gameobject를 초기화 하 고 다시 사용 하기 위해 [개체 풀링을](#object-pooling) 사용 하 여 모든 개체를 인스턴스화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-175">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="05971-176">**인터페이스 및 가상 구문 방지**</span><span class="sxs-lookup"><span data-stu-id="05971-176">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="05971-177">인터페이스를 통해 함수 호출을 호출 하거나 직접 개체를 호출 하거나 가상 함수를 호출 하는 것이 직접 구문 또는 직접 함수 호출을 활용 하는 것 보다 훨씬 더 비쌉니다.</span><span class="sxs-lookup"><span data-stu-id="05971-177">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="05971-178">가상 함수 또는 인터페이스가 필요 하지 않은 경우 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-178">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="05971-179">그러나 이러한 접근 방식에 대 한 성능 저하는 일반적으로 개발 공동 작업, 코드 가독성 및 코드 유지 관리를 간소화 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-179">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="05971-180">일반적으로이 멤버를 덮어써야 하는 것으로 예상 되는 것이 확실 하지 않으면 필드 및 함수를 가상으로 표시 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-180">Generally, the recommendation is to not mark fields and functions as virtual unless there is a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="05971-181">프레임 당 여러 번 또는 `UpdateUI()` 메서드와 같이 프레임당 한 번 호출 되는 빈도가 높은 코드 경로에 특히 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-181">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="05971-182">**값으로 구조체 전달 방지**</span><span class="sxs-lookup"><span data-stu-id="05971-182">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="05971-183">클래스와 달리 구조체는 값 형식이 며 함수로 직접 전달 될 때 해당 내용이 새로 만든 인스턴스에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-183">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="05971-184">이 복사본은 CPU 비용 뿐만 아니라 스택에 추가 메모리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-184">This copy adds CPU cost as well as additional memory on the stack.</span></span> <span data-ttu-id="05971-185">작은 구조체의 경우 효과는 일반적으로 매우 미미 하므로 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-185">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="05971-186">그러나 모든 프레임을 반복 해 서 호출 하는 함수 뿐만 아니라 대량 구조체를 가져오는 함수도 가능 하면 함수 정의를 참조로 전달 하도록 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-186">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="05971-187">여기에서 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="05971-187">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="05971-188">기타</span><span class="sxs-lookup"><span data-stu-id="05971-188">Miscellaneous</span></span>

1) <span data-ttu-id="05971-189">**물리**</span><span class="sxs-lookup"><span data-stu-id="05971-189">**Physics**</span></span>

    <span data-ttu-id="05971-190">a) 일반적으로 물리를 개선 하는 가장 쉬운 방법은 물리학에 소요 되는 시간 또는 초당 반복 횟수를 제한 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-190">a) Generally, easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="05971-191">물론이로 인해 시뮬레이션 정확도가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="05971-191">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="05971-192">Unity에서 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05971-192">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="05971-193">b) Unity의 colliders 형식에는 다양 한 성능 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-193">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="05971-194">아래 주문에서는 가장 성능이 가장 뛰어난 colliders을 왼쪽에서 오른쪽으로 가장 낮은 colliders 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-194">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="05971-195">기본 Colliders 보다 비용이 많이 드는 메시 Colliders을 방지 하는 것이 가장 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-195">It is most important to avoid Mesh Colliders which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="05971-196">자세한 내용은 [Unity 물리학 모범 사례](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05971-196">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="05971-197">**애니메이션이**</span><span class="sxs-lookup"><span data-stu-id="05971-197">**Animations**</span></span>

    <span data-ttu-id="05971-198">애니메이터 구성 요소를 사용 하지 않도록 설정 하 여 유휴 상태의 애니메이션을 사용 하지 않도록 설정 (게임 개체를 사용 하지 않도록 설정 해도 동일한 효과가 없음</span><span class="sxs-lookup"><span data-stu-id="05971-198">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="05971-199">값을 동일한 값으로 설정 하는 반복에서 애니메이터를 사용 하는 디자인 패턴을 피합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-199">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="05971-200">응용 프로그램에 영향을 주지 않고이 기술에 대 한 상당한 오버 헤드가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-200">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="05971-201">자세한 내용은 여기를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05971-201">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="05971-202">**복잡 한 알고리즘**</span><span class="sxs-lookup"><span data-stu-id="05971-202">**Complex algorithms**</span></span>

    <span data-ttu-id="05971-203">응용 프로그램에서 역 기구학, 경로 찾기 등의 복잡 한 알고리즘을 사용 하는 경우 더 간단한 접근 방식을 찾거나 성능에 대 한 관련 설정을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-203">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="05971-204">CPU 대 GPU 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="05971-204">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="05971-205">일반적으로 CPU 대 GPU 성능은 그래픽 카드에 제출 된 **그리기 호출** 에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-205">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="05971-206">성능을 향상 시키려면 최적의 결과를 위해 그리기 호출을 전략적 **a로 축소** 하거나 **b) 재구성** 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-206">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="05971-207">그리기 호출 자체는 리소스를 많이 사용 하므로 이러한 호출을 줄이면 필요한 전체 작업을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-207">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="05971-208">그리고 그리기 호출 사이에 상태를 변경 하려면 그래픽 드라이버에서 비용이 많이 드는 유효성 검사 및 변환 단계가 필요 하므로 상태 변경을 제한 하기 위해 응용 프로그램의 그리기 호출을 재구성 해야 합니다. 즉,</span><span class="sxs-lookup"><span data-stu-id="05971-208">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes(i.e</span></span> <span data-ttu-id="05971-209">다른 자료 등)를 통해 성능을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-209">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="05971-210">Unity에는 플랫폼에 대 한 일괄 처리 그리기 호출에 대 한 개요 및 다이브을 제공 하는 유용한 문서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-210">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="05971-211">Unity 호출 일괄 처리 그리기</span><span class="sxs-lookup"><span data-stu-id="05971-211">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="05971-212">단일 패스 인스턴스화된 렌더링</span><span class="sxs-lookup"><span data-stu-id="05971-212">Single pass instanced rendering</span></span>

<span data-ttu-id="05971-213">Unity에서 단일 패스 인스턴스화된 렌더링을 사용 하면 각 눈동자에 대 한 그리기 호출을 하나의 인스턴스화된 그리기 호출로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-213">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="05971-214">두 그리기 호출 사이의 캐시 일관성으로 인해 GPU 에서도 약간의 성능도 향상 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-214">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="05971-215">Unity 프로젝트에서이 기능을 사용 하도록 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="05971-215">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="05971-216">**플레이어 XR 설정** 열기 ( **편집** > **프로젝트 설정** > **플레이어** > **XR 설정**으로 이동)</span><span class="sxs-lookup"><span data-stu-id="05971-216">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="05971-217">**스테레오 렌더링 방법** 드롭다운 메뉴에서 **단일 패스 인스턴스** 를 선택 합니다 (**가상 현실 지원 됨** 확인란을 선택 해야 함).</span><span class="sxs-lookup"><span data-stu-id="05971-217">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="05971-218">이 렌더링 방법에 대 한 자세한 내용은 Unity에서 다음 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05971-218">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="05971-219">고급 스테레오 렌더링을 사용 하 여 AR 및 VR 성능을 최대화 하는 방법</span><span class="sxs-lookup"><span data-stu-id="05971-219">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="05971-220">단일 패스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="05971-220">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="05971-221">단일 패스 인스턴스화된 렌더링의 일반적인 문제 중 하나는 개발자에 게 인스턴스에 대해 작성 되지 않은 기존 사용자 지정 셰이더가 이미 있는 경우 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-221">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="05971-222">이 기능을 사용 하도록 설정한 후 개발자는 일부 Gameobject 한 눈에만 렌더링 되는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-222">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="05971-223">이는 연결 된 사용자 지정 셰이더가 인스턴스에 적합 한 속성을 포함 하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-223">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="05971-224">이 문제를 해결 하는 방법에 대해서는 Unity의 [HoloLens에 대 한 단일 패스 스테레오 렌더링](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05971-224">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="05971-225">정적 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="05971-225">Static batching</span></span>

<span data-ttu-id="05971-226">Unity는 많은 정적 개체를 일괄 처리 하 여 GPU에 대 한 그리기 호출을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-226">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="05971-227">정적 일괄 처리는 **1) 동일한 자료를 공유** 하 고 **2) 모두 *정적* 으로 표시** 되는 unity의 대부분 [렌더러](https://docs.unity3d.com/ScriptReference/Renderer.html) 개체에 대해 작동 합니다. unity에서 개체를 선택 하 고 검사기의 오른쪽 위에 있는 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-227">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="05971-228">*Static* 으로 표시 된 gameobject는 응용 프로그램의 런타임 전체에서 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-228">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="05971-229">따라서 정적 일괄 처리는 거의 모든 개체를 배치 하 고 이동 하거나 크기를 조정 해야 하는 HoloLens에서 활용 하기 어려울 수 있습니다. 모던 헤드셋의 경우 정적 일괄 처리는 그리기 호출을 크게 줄일 수 있으므로 성능을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-229">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="05971-230">자세한 내용은 [Unity에서 그리기 호출 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html) 에서 *정적 일괄 처리* 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05971-230">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="05971-231">동적 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="05971-231">Dynamic batching</span></span>

<span data-ttu-id="05971-232">개체를 HoloLens 개발에 대 한 *정적* 으로 표시 하는 데 문제가 있기 때문에 동적 일괄 처리는 이러한 부족 한 기능을 보정 하는 데 유용한 도구 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-232">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="05971-233">물론 모던 헤드셋 에서도 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-233">Of course, it is can also be useful on immersive headsets as well.</span></span> <span data-ttu-id="05971-234">Unity의 동적 일괄 처리 **는 gameobject가 동일한 자료를 공유** 하 고 **b) 다른 조건의 긴 목록을 충족**하기 때문에를 사용 하도록 설정 하는 것이 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-234">Dynamic batching in Unity can be difficult though to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="05971-235">전체 목록에 대 한 [Unity의 그리기 호출 일괄](https://docs.unity3d.com/Manual/DrawCallBatching.html) 처리에서 *동적 일괄 처리* 를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-235">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="05971-236">가장 일반적으로 Gameobject는 연결 된 메시 데이터가 300 꼭 짓 점이 될 수 있으므로 동적으로 일괄 처리할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-236">Most commonly, GameObjects become invalid to be batched dynamically because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="05971-237">기타 기술</span><span class="sxs-lookup"><span data-stu-id="05971-237">Other techniques</span></span>

<span data-ttu-id="05971-238">일괄 처리는 여러 Gameobject가 동일한 자료를 공유할 수 있는 경우에만 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-238">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="05971-239">일반적으로이는 Gameobject가 해당 재질에 대해 고유한 질감을 가질 필요에 의해 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-239">Typically this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="05971-240">[질감 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)하는 메서드를 하나의 큰 질감으로 결합 하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-240">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="05971-241">또한 일반적으로 메시를 가능한 한 GameObject 결합 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-241">Further, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="05971-242">Unity의 각 렌더러는 연결 된 그리기 호출을 포함 하 고 하나의 렌더러에서 결합 된 메시를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-242">Each Renderer in Unity will have it's associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="05971-243">렌더러의 속성을 수정 하는 중입니다. 런타임에 재질은 재질의 복사본을 만들고 일괄 처리를 중단 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-243">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="05971-244">Gameobject에서 공유 재질 속성을 수정 하려면 렌더러를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-244">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="05971-245">GPU 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="05971-245">GPU performance recommendations</span></span>

<span data-ttu-id="05971-246">[Unity에서 그래픽 렌더링 최적화](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games) 에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="05971-246">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="05971-247">깊이 버퍼 공유 최적화</span><span class="sxs-lookup"><span data-stu-id="05971-247">Optimize depth buffer sharing</span></span>

<span data-ttu-id="05971-248">일반적으로 **플레이어 XR 설정** 에서 **깊이 버퍼 공유** 를 사용 하도록 설정 하 여 [홀로그램 안정성](Hologram-stability.md)을 최적화 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-248">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="05971-249">그러나이 설정을 사용 하 여 깊이 기반 지연 단계를 사용 하도록 설정 하는 경우 **24 비트 깊이 형식**대신 **16 비트 깊이 형식을** 선택 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-249">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="05971-250">16 비트 깊이 버퍼는 깊이 버퍼 트래픽과 관련 된 대역폭 (그리고 그에 따라 전원)을 크게 감소 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="05971-250">The 16-bit depth buffers will drastically reduces the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="05971-251">이는 전력 감소 및 성능 향상에 모두 큰 승리를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-251">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="05971-252">그러나 *16 비트 깊이 형식을*사용 하는 경우 두 가지 가능한 음수 결과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-252">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="05971-253">**Z-싸 우**</span><span class="sxs-lookup"><span data-stu-id="05971-253">**Z-Fighting**</span></span>

<span data-ttu-id="05971-254">축소 된 깊이 범위 충실도는 24 비트 보다 16 비트를 사용 하 여 [z](https://en.wikipedia.org/wiki/Z-fighting) 를 더 많이 교환할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-254">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="05971-255">이러한 아티팩트를 방지 하려면 [Unity 카메라](https://docs.unity3d.com/Manual/class-Camera.html) 의 near/far 클립 평면을 수정 하 여 더 낮은 정밀도를 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-255">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="05971-256">HoloLens 기반 응용 프로그램의 경우 Unity 기본 1000m 대신 5천만 개의 먼 클립 평면은 일반적으로 z-싸 우를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-256">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="05971-257">**사용 하지 않도록 설정 된 스텐실 버퍼**</span><span class="sxs-lookup"><span data-stu-id="05971-257">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="05971-258">Unity에서 [16 비트 깊이의 렌더링 질감](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)을 만드는 경우 스텐실 버퍼가 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-258">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there is no stencil buffer created.</span></span> <span data-ttu-id="05971-259">Unity 설명서 당 24 비트 깊이 형식을 선택 하면 24 비트 z 버퍼 뿐만 아니라 [8 비트 스텐실 버퍼](https://docs.unity3d.com/Manual/SL-Stencil.html) (일반적으로 HoloLens와 같은 경우에 32 비트를 장치에 적용할 수 있는 경우)가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-259">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer as well as an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on device which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="05971-260">전체 화면 효과 방지</span><span class="sxs-lookup"><span data-stu-id="05971-260">Avoid full-screen effects</span></span>

<span data-ttu-id="05971-261">전체 화면에서 작동 하는 기술은 모든 프레임의 크기가 수백만 작업 이므로 상당한 비용이 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-261">Techniques that operate on the full screen can be quite expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="05971-262">따라서 앤티앨리어스, 블 룸 등의 [사후 처리 효과](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 를 방지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-262">Thus, it is recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="05971-263">최적의 조명 설정</span><span class="sxs-lookup"><span data-stu-id="05971-263">Optimal lighting settings</span></span>

<span data-ttu-id="05971-264">Unity의 [실시간 글로벌 조명은 전 세계](https://docs.unity3d.com/Manual/GIIntro.html) 의 시각적 결과를 제공할 수 있지만 상당한 비용이 드는 조명 계산이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-264">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide oustanding visual results but involves quite expensive lighting calculations.</span></span> <span data-ttu-id="05971-265">**창을** 통해 모든 Unity 장면 파일에 대해 실시간 글로벌 조명을 사용 하지 않도록 설정 하는 것이 좋습니다. > **렌더링** > **조명 설정을** 사용 하 여 **실시간 글로벌 조명을**선택 취소 >.</span><span class="sxs-lookup"><span data-stu-id="05971-265">It is recommended to disable Realtime Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="05971-266">또한 모든 섀도 캐스팅을 사용 하지 않도록 설정 하는 것이 좋습니다 .이 경우에도 Unity 장면에 비용이 많이 드는 GPU 패스가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-266">Further, it is recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="05971-267">그림자는 빛 당 사용 하지 않도록 설정할 수 있지만 품질 설정을 통해 전체적으로 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-267">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="05971-268"> > **프로젝트 설정을** **편집한** 다음 **품질** 범주를 선택 하 > UWP 플랫폼 **에 대해 저품질를 선택** 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-268">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="05971-269">그림자를 **사용 하지 않도록**설정 하려면 **shadows** 속성을 설정 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-269">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="05971-270">Poly 수 줄이기</span><span class="sxs-lookup"><span data-stu-id="05971-270">Reduce poly count</span></span>

<span data-ttu-id="05971-271">다각형 수는 일반적으로 다음 중 하나로 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="05971-271">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="05971-272">장면에서 개체 제거</span><span class="sxs-lookup"><span data-stu-id="05971-272">Removing objects from a scene</span></span>
2) <span data-ttu-id="05971-273">지정 된 메시의 다각형 수를 줄이는 Asset decimation</span><span class="sxs-lookup"><span data-stu-id="05971-273">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="05971-274">응용 프로그램에 대 한 [세부 정보 (LOD) 시스템](https://docs.unity3d.com/Manual/LevelOfDetail.html) 을 구현 하 여 동일한 기 하 도형에 대 한 다각형 버전이 더 낮은 개체를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-274">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="05971-275">Unity의 셰이더 이해</span><span class="sxs-lookup"><span data-stu-id="05971-275">Understanding shaders in Unity</span></span>

<span data-ttu-id="05971-276">성능과 셰이더를 비교 하는 것은 각 런타임에 실행 되는 평균 작업 수를 식별 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-276">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="05971-277">Unity에서이 작업을 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-277">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="05971-278">셰이더 자산을 선택 하거나 재질을 선택 하 고 검사기 창의 오른쪽 위에 있는 기어 아이콘을 선택한 다음 **"셰이더 선택"** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-278">Select your shader asset or select a material, then in top right corner of the inspector window, select the gear icon and then **"Select Shader"**</span></span>

    ![Unity에서 셰이더 선택](images/Select-shader-unity.png)
2) <span data-ttu-id="05971-280">셰이더 자산을 선택 하 고 검사기 창에서 **"코드 컴파일 및 표시"** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-280">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![Unity에서 셰이더 코드 컴파일](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="05971-282">컴파일한 후에는 꼭 짓 점 및 픽셀 셰이더 모두에 대해 다양 한 작업 수를 사용 하 여 결과에서 통계 섹션을 찾습니다 (참고: 픽셀 셰이더를 조각 셰이더 라고도 함).</span><span class="sxs-lookup"><span data-stu-id="05971-282">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 표준 셰이더 작업](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a><span data-ttu-id="05971-284">공간 픽셀 셰이더</span><span class="sxs-lookup"><span data-stu-id="05971-284">Optmize pixel shaders</span></span>

<span data-ttu-id="05971-285">위의 메서드를 사용 하 여 컴파일된 통계 결과를 살펴보면 [조각 셰이더가](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) 일반적으로 평균에서 [꼭 짓 점 셰이더](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) 보다 많은 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-285">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) on average.</span></span> <span data-ttu-id="05971-286">꼭 짓 점 셰이더 라고도 하는 조각 셰이더는 화면 출력에서 픽셀 단위로 실행 되는 반면 꼭 짓 점 셰이더는 화면에 그려지는 모든 망상의 꼭 짓 점 마다 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-286">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="05971-287">따라서 조각 셰이더는 모든 조명 계산으로 인해 꼭 짓 점 셰이더 보다 더 많은 명령을 포함할 뿐만 아니라 조각 셰이더는 거의 항상 큰 데이터 집합에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-287">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="05971-288">예를 들어 화면 출력이 2k 이미지 인 경우 조각 셰이더는 2000 \* 2000 = 400만 번 실행 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-288">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="05971-289">두 개의 눈동자를 렌더링 하는 경우 두 개의 화면이 있으므로이 수는 두 배가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-289">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="05971-290">혼합 현실 응용 프로그램에 여러 번의 통과, 전체 화면 처리 효과가 있는 경우 또는 여러 메시를 동일한 픽셀로 렌더링 하는 경우이 숫자가 크게 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-290">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="05971-291">따라서 조각 셰이더의 작업 수를 줄이면 일반적으로 꼭 짓 점 셰이더의 최적화에 비해 훨씬 더 큰 성능 향상을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-291">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="05971-292">Unity 표준 셰이더 대안</span><span class="sxs-lookup"><span data-stu-id="05971-292">Unity Standard shader alternatives</span></span>

<span data-ttu-id="05971-293">실제 기반 렌더링 (.PBR) 또는 기타 고품질 셰이더를 사용 하는 대신 보다 성능이 뛰어나고 저렴 한 셰이더를 활용 하는 방법을 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="05971-293">Instead of using a physically based rendering (PBR) or other high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="05971-294">[Mixed Reality 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity) 는 혼합 현실 프로젝트에 최적화 된 [mrtk 표준 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) 를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-294">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="05971-295">Unity는 Unity 표준 셰이더에 비해 훨씬 빠르게 unlit, 꼭 짓 점, 확산 및 기타 단순화 된 셰이더 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-295">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="05971-296">자세한 내용은 [기본 제공 셰이더의 사용 및 성능](https://docs.unity3d.com/Manual/shader-Performance.html) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05971-296">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="05971-297">셰이더 미리 로드</span><span class="sxs-lookup"><span data-stu-id="05971-297">Shader preloading</span></span>

<span data-ttu-id="05971-298">셰이더 *미리* 로드 및 기타 트릭을 사용 하 여 [셰이더 로드 시간](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-298">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="05971-299">특히 셰이더 미리 로드는 런타임 셰이더 컴파일 때문에 어떤 hitches 표시 되지 않음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-299">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="05971-300">과도 한 그리기 제한</span><span class="sxs-lookup"><span data-stu-id="05971-300">Limit overdraw</span></span>

<span data-ttu-id="05971-301">Unity에서 **장면 보기** 의 왼쪽 위 모퉁이에 있는 [**그리기 모드 메뉴**](https://docs.unity3d.com/Manual/ViewModes.html) 를 전환 하 고 **과도 한 그리기**를 선택 하 여 장면에 대해 과도 한 그리기를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-301">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="05971-302">일반적으로 과도 한 그리기는 GPU에 전송 되기 전에 미리 개체를 고르기 하 여 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-302">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="05971-303">Unity는 [폐색 고르기](https://docs.unity3d.com/Manual/OcclusionCulling.html) for engine 구현에 대 한 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-303">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="05971-304">메모리 권장 사항</span><span class="sxs-lookup"><span data-stu-id="05971-304">Memory recommendations</span></span>

<span data-ttu-id="05971-305">과도 한 메모리 할당 & 할당 취소 작업은 holographic 응용 프로그램에 부정적인 영향을 줄 수 있으므로 성능, 고정 된 프레임 및 기타 부정적 동작이 일치 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-305">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="05971-306">메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-306">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="05971-307">가비지 수집</span><span class="sxs-lookup"><span data-stu-id="05971-307">Garbage collection</span></span>

<span data-ttu-id="05971-308">Holographic apps는 GC가 활성화 되어 실행 중에 더 이상 범위에 있지 않은 개체를 분석 하 여 다시 사용할 수 있도록 설정할 수 있도록 해당 메모리를 해제 해야 하는 경우 GC (가비지 수집기)에 대 한 계산 시간을 더 이상 처리 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-308">Holographic apps will loose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released so it can be made available for re-use.</span></span> <span data-ttu-id="05971-309">상수 할당 및 할당 취소는 일반적으로 가비지 수집기가 더 자주 실행 하 여 성능 및 사용자 환경을 저하 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-309">Constant allocations and de-allocations will generally require the garbage collector to run more frequently thus hurting performance and user experience.</span></span>

<span data-ttu-id="05971-310">Unity는 메모리 관리와 관련 하 여 보다 효율적인 코드를 작성 하기 위한 팁과 가비지 수집기의 작동 방식에 대해 자세히 설명 하는 뛰어난 페이지를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-310">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="05971-311">Unity 게임에서 가비지 수집 최적화</span><span class="sxs-lookup"><span data-stu-id="05971-311">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="05971-312">과도 한 가비지 수집을 수행 하는 가장 일반적인 방법 중 하나는 Unity 개발의 구성 요소 및 클래스에 대 한 참조를 캐싱하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-312">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="05971-313">모든 참조는 Start () 또는 해제 () 중에 캡처되고 업데이트 () 또는 Behaviour ()와 같은 이후 함수에서 다시 사용 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-313">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="05971-314">기타 빠른 팁:</span><span class="sxs-lookup"><span data-stu-id="05971-314">Other quick tips:</span></span>
- <span data-ttu-id="05971-315">[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 클래스를 사용 하 여 런타임에 복잡 한 문자열을 동적으로 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-315">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="05971-316">응용 프로그램의 모든 빌드 버전에서 계속 실행 되므로 더 이상 필요 하지 않은 경우 Debug () 호출을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-316">Remove calls to Debug.Log() when no longer needed as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="05971-317">Holographic 앱이 일반적으로 많은 메모리를 요구 하는 경우 로드 또는 전환 화면을 발표할 때와 같은 단계를 로드 하는 동안 system.string [ _**()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) 을 호출 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-317">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="05971-318">개체 풀링</span><span class="sxs-lookup"><span data-stu-id="05971-318">Object pooling</span></span>

<span data-ttu-id="05971-319">개체 풀링은 연속 & 할당의 비용을 줄이고 개체 할당을 취소 하는 인기 있는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-319">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="05971-320">이 작업을 수행 하려면 시간이 지남에 따라 개체를 지속적으로 생성 및 제거 하는 대신 동일한 개체의 대량 풀을 할당 하 고이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-320">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="05971-321">개체 풀은 앱을 실행 하는 동안 변수 수명이 있는 다시 사용할 수 있는 구성 요소에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="05971-321">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="05971-322">Unity의 개체 풀링 자습서</span><span class="sxs-lookup"><span data-stu-id="05971-322">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="05971-323">시작 성능</span><span class="sxs-lookup"><span data-stu-id="05971-323">Startup performance</span></span>

<span data-ttu-id="05971-324">더 작은 장면으로 앱을 시작한 다음 *[SceneManager. LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 를 사용 하 여 나머지 장면을 로드 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-324">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="05971-325">이렇게 하면 앱이 최대한 빠르게 대화형 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-325">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="05971-326">새 장면을 활성화 하 고 렌더링 된 모든 콘텐츠를 끊길 하거나 hitch 수 있는 동안에는 상당한 CPU 스파이크가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05971-326">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="05971-327">이 문제를 해결 하는 한 가지 방법은 로드 되는 장면에서 allowSceneActivation 속성을 false로 설정 하 고, 장면을 로드할 때까지 기다리거나, 화면을 검정으로 AsyncOperation, true로 다시 설정 하 여 장면 활성화를 완료 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05971-327">One way to work around this is to set the AsyncOperation.allowSceneActivation property to false on the scene being loaded, wait for the scene to load, clear the screen to black, and then set back to true to complete the scene activation.</span></span>

<span data-ttu-id="05971-328">시작 장면을 로드 하는 동안 holographic 시작 화면이 사용자에 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05971-328">Remember that while the startup scene is loading the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="05971-329">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05971-329">See also</span></span>
- [<span data-ttu-id="05971-330">Unity 게임에서 그래픽 렌더링 최적화</span><span class="sxs-lookup"><span data-stu-id="05971-330">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="05971-331">Unity 게임에서 가비지 수집 최적화</span><span class="sxs-lookup"><span data-stu-id="05971-331">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="05971-332">[물리학 모범 사례 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="05971-332">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="05971-333">[스크립트 최적화 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="05971-333">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
