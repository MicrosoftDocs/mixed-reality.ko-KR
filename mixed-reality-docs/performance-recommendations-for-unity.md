---
title: Unity에 대한 성능 추천 사항
description: 혼합 현실 앱을 사용하여 성능을 향상시킬 수 있는 Unity 관련 팁입니다.
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 그래픽, CPU, GPU, 렌더링, 가비지 컬렉션, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c6c68a6dd6e8ba59bee983e158e210aed27d2b17
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216244"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="0b5f7-104">Unity에 대한 성능 추천 사항</span><span class="sxs-lookup"><span data-stu-id="0b5f7-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="0b5f7-105">이 문서에서는 [혼합 현실에 대한 성능 추천 사항](understanding-performance-for-mixed-reality.md)에 요약된 설명을 기반으로 하지만, Unity 엔진 환경과 관련된 학습에 집중하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

## <a name="use-recommended-unity-project-settings"></a><span data-ttu-id="0b5f7-106">권장 Unity 프로젝트 설정 사용</span><span class="sxs-lookup"><span data-stu-id="0b5f7-106">Use recommended Unity project settings</span></span>

<span data-ttu-id="0b5f7-107">Unity에서 혼합 현실 앱의 성능을 최적화할 때 가장 중요한 첫 번째 단계는 [Unity 권장 환경 설정](recommended-settings-for-unity.md)을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-107">The most important first step when optimizing performance of mixed reality apps in Unity is to be sure you are using the [recommended environment settings for Unity](recommended-settings-for-unity.md).</span></span> <span data-ttu-id="0b5f7-108">해당 문서에는 성능이 뛰어난 Mixed Reality 앱을 빌드하는 데 가장 중요한 장면 구성에 대한 일부 내용이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-108">That article contains content with some of the most important scene configurations for building performant Mixed Reality apps.</span></span> <span data-ttu-id="0b5f7-109">아래에서는 이러한 추천 설정 중 일부를 강조하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-109">Some of these recommended settings are highlighted below, as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="0b5f7-110">Unity를 사용하여 프로파일링하는 방법</span><span class="sxs-lookup"><span data-stu-id="0b5f7-110">How to profile with Unity</span></span>

<span data-ttu-id="0b5f7-111">Unity는 기본적으로 **[Unity 프로파일러](https://docs.unity3d.com/Manual/Profiler.html)** 를 제공하며, 이는 특정 앱에 대한 중요한 성능 인사이트를 수집할 수 있는 유용한 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-111">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in, which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="0b5f7-112">편집기 내에서 프로파일러를 실행할 수 있지만, 이러한 메트릭은 실제 런타임 환경을 나타내지 않으므로 해당 메트릭의 결과는 신중하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-112">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="0b5f7-113">가장 정확하고 실행 가능한 인사이트를 얻으려면 디바이스에서 실행하는 동안 애플리케이션을 원격으로 프로파일링하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-113">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="0b5f7-114">또한 Unity의 [프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html)도 매우 강력하고 인사이트를 제공하는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-114">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="0b5f7-115">Unity는 다음 항목에 대한 유용한 문서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-115">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="0b5f7-116">[Unity 프로파일러를 UWP 애플리케이션에 원격으로 연결](https://docs.unity3d.com/Manual/windowsstore-profiler.html)하는 방법</span><span class="sxs-lookup"><span data-stu-id="0b5f7-116">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="0b5f7-117">[Unity 프로파일러를 사용하여 성능 문제를 효과적으로 진단](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)하는 방법</span><span class="sxs-lookup"><span data-stu-id="0b5f7-117">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="0b5f7-118">Unity 프로파일러가 연결되고 GPU 프로파일러가 추가되면(오른쪽 위 모서리의 *프로파일러 추가* 참조) 프로파일러 가운데에서 CPU 및 GPU 각각에 소요되는 시간을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-118">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="0b5f7-119">애플리케이션이 CPU 또는 GPU에 바인딩되어 있는 경우 개발자는 이를 통해 근사값을 빠르게 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-119">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 및 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="0b5f7-121">CPU 성능 추천 사항</span><span class="sxs-lookup"><span data-stu-id="0b5f7-121">CPU performance recommendations</span></span>

<span data-ttu-id="0b5f7-122">아래 내용은 특히 Unity 및 C# 개발을 대상으로 하는 자세한 성능 사례에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-122">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="0b5f7-123">캐시 참조</span><span class="sxs-lookup"><span data-stu-id="0b5f7-123">Cache references</span></span>

<span data-ttu-id="0b5f7-124">초기화 시 모든 관련 구성 요소 및 GameObject에 대한 참조를 캐시하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-124">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="0b5f7-125">이는 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 와 같은 반복 함수 호출이 포인터를 저장하는 메모리 비용보다 훨씬 더 비싸기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-125">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="0b5f7-126">또한 이는 매우 일반적으로 사용되는 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-126">This also applies to to the very regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="0b5f7-127">*Camera.main*은 실제로 아래의 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 만 사용합니다. 이는 *"MainCamera"* 태그를 사용하여 장면 그래프에서 카메라 개체를 검색하지만 많은 비용이 들어갑니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-127">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath, which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="0b5f7-128">GetComponent(문자열) 사용 방지</span><span class="sxs-lookup"><span data-stu-id="0b5f7-128">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="0b5f7-129">*[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 를 사용하는 경우 몇 가지 오버로드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-129">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="0b5f7-130">항상 형식 기반 구현을 사용하고, 문자열 기반 검색 오버로드를 사용하지 않는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-130">It is important to always use the Type-based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="0b5f7-131">장면에서 문자열로 검색하는 경우 Type을 기준으로 검색하는 것보다 훨씬 더 비쌉니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-131">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="0b5f7-132">(좋음) GetComponent(Type 형식) 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0b5f7-132">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="0b5f7-133">(좋음) T GetComponent\<T>()</span><span class="sxs-lookup"><span data-stu-id="0b5f7-133">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="0b5f7-134">(나쁨) GetComponent(문자열)> 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0b5f7-134">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="0b5f7-135">비용이 많이 드는 작업 방지</span><span class="sxs-lookup"><span data-stu-id="0b5f7-135">Avoid expensive operations</span></span>

1) <span data-ttu-id="0b5f7-136">**[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq) 사용 방지**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-136">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="0b5f7-137">LINQ는 매우 깔끔하고 쉽게 읽고 쓸 수 있지만, 일반적으로 알고리즘을 수동으로 작성하는 것보다 훨씬 더 많은 계산, 특히 더 많은 메모리 할당이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-137">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="0b5f7-138">**일반 Unity API**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-138">**Common Unity APIs**</span></span>

    <span data-ttu-id="0b5f7-139">일부 Unity API는 유용하지만 실행 비용이 매우 많이 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-139">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="0b5f7-140">이러한 API 중 대부분은 전체 장면 그래프에서 일치하는 몇 가지 GameObject 목록을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-140">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="0b5f7-141">일반적으로 런타임에 참조를 추적하기 위해 참조를 캐시하거나 해당 GameObject에 대한 관리자 구성 요소를 구현하여 이러한 작업을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-141">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="0b5f7-142">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 및 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 는 반드시 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-142">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="0b5f7-143">이러한 함수는 직접 함수 호출보다 1,000배 더 느릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-143">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="0b5f7-144">**boxing에 주의**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-144">**Beware of boxing**</span></span>

    <span data-ttu-id="0b5f7-145">[boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)은 C# 언어 및 런타임의 핵심 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-145">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="0b5f7-146">이는 char, int, bool 등과 같은 값 형식 변수를 참조 형식 변수로 래핑하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-146">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="0b5f7-147">값 형식 변수가 "boxing"되면 관리형 힙에 저장된 System.Object 내부에 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-147">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="0b5f7-148">이에 따라 메모리가 할당되며, 결국에는 삭제 시 가비지 수집기에서 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-148">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="0b5f7-149">이러한 할당 및 할당 취소는 성능 비용을 발생시키며, 많은 시나리오에서 필요하지 않거나 비용이 더 저렴한 대안으로 쉽게 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-149">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="0b5f7-150">개발에서 가장 일반적인 boxing 형태 중 하나는 [nullable 값 형식](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-150">One of the most common forms of boxing in development is the use of [nullable value types](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/).</span></span> <span data-ttu-id="0b5f7-151">특히 작업에서 값을 가져오는 데 실패하는 경우 함수에서 일반적으로 값 형식으로 null을 반환하려고 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-151">It is common to want to be able to return null for a value type in a function, especially when the operation may fail trying to get the value.</span></span> <span data-ttu-id="0b5f7-152">이 방법의 잠재적인 문제는 이제 할당이 힙에서 발생하므로 나중에 가비지를 수집해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-152">The potential problem with this approach is that allocation now occurs on the heap and consequently needs to be garbage collected later.</span></span>

    <span data-ttu-id="0b5f7-153">**C#의 boxing 예제**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-153">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    <span data-ttu-id="0b5f7-154">**nullable 값 형식을 통한 문제가 있는 boxing의 예제**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-154">**Example of problematic boxing via nullable value types**</span></span>

    <span data-ttu-id="0b5f7-155">다음 코드에서는 Unity 프로젝트에서 만들 수 있는 더미 파티클 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-155">This code demonstrates a dummy particle class that one may create in a Unity project.</span></span> <span data-ttu-id="0b5f7-156">`TryGetSpeed()`를 호출하면 개체가 힙에 할당되며, 나중에 가비지를 수집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-156">A call to `TryGetSpeed()` will cause object allocation on the heap which will need to be garbage collected at a later point in time.</span></span> <span data-ttu-id="0b5f7-157">이 예제는 한 장면에 1,000개 이상의 파티클이 있을 수 있으므로 특히 문제가 되며, 각각 현재 속도를 요구하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-157">This example is particularly problematic as there may be 1000+ or many more particles in a scene, each being asked for their current speed.</span></span> <span data-ttu-id="0b5f7-158">따라서 1,000개의 개체가 할당되고, 결과적으로 모든 프레임에서 할당을 취소하여 성능이 크게 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-158">Thus, 1000's of objects would be allocated and consequently de-allocated every frame, which would greatly diminish performance.</span></span> <span data-ttu-id="0b5f7-159">오류를 나타내기 위해 -1과 같은 음수 값을 반환하도록 함수를 다시 작성하면 이 문제가 방지되고 메모리가 스택에서 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-159">Re-writing the function to return a negative value such as -1 to indicate a failure would avoid this issue and keep memory on the stack.</span></span>

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

#### <a name="repeating-code-paths"></a><span data-ttu-id="0b5f7-160">반복 코드 경로</span><span class="sxs-lookup"><span data-stu-id="0b5f7-160">Repeating code paths</span></span>

<span data-ttu-id="0b5f7-161">초당 여러 번 실행되는 Unity 콜백 반복 함수(예:</span><span class="sxs-lookup"><span data-stu-id="0b5f7-161">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="0b5f7-162">Update) 및/또는 프레임은 매우 신중하게 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-162">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="0b5f7-163">여기서 비용이 많이 드는 작업은 성능에 크고 일관된 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-163">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="0b5f7-164">**빈 콜백 함수**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-164">**Empty callback functions**</span></span>

    <span data-ttu-id="0b5f7-165">아래 코드는 애플리케이션에 남겨 두는 것이 무해한 것처럼 보일 수 있지만, 특히 모든 Unity 스크립트가 이 코드 블록을 사용하여 자동으로 초기화되므로 이러한 빈 콜백은 실제로 매우 비쌀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-165">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="0b5f7-166">Unity는 UnityEngine 코드와 애플리케이션 코드 간에 비관리/관리 코드 경계를 넘나들며 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-166">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="0b5f7-167">이 브리지를 통해 컨텍스트를 전환하는 것은 실행하는 작업이 없더라도 비용이 매우 많이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-167">Context switching over this bridge is fairly expensive, even if there is nothing to execute.</span></span> <span data-ttu-id="0b5f7-168">반복되는 빈 Unity 콜백이 있는 구성 요소가 포함된 100개의 GameObject가 앱에 있는 경우 특히 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-168">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="0b5f7-169">Update()는 이 성능 문제의 가장 일반적인 증상이지만 다른 Unity 콜백(예: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage() 등)은 나쁘지 않은 경우에도 마찬가지로 나쁠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-169">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks, such as the following can be equally as bad, if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="0b5f7-170">**프레임당 한 번 실행되도록 하는 작업**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-170">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="0b5f7-171">다음 Unity API는 많은 홀로그램 앱의 일반적인 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-171">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="0b5f7-172">이러한 함수의 결과는 항상 가능한 것은 아니지만 일반적으로 한 번 계산될 수 있으며, 지정된 프레임에 대해 애플리케이션 전체에서 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-172">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="0b5f7-173">a) 일반적으로 각 구성 요소에서 반복적이고 본질적으로 동일한 Raycast 작업을 수행하는 대신, 장면에서 Raycast를 응시하도록 처리한 다음, 이 결과를 다른 모든 장면 구성 요소에서 다시 사용하는 전용 Singleton 클래스 또는 서비스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-173">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="0b5f7-174">물론 일부 애플리케이션에는 다른 원본 또는 다른 [LayerMask](https://docs.unity3d.com/ScriptReference/LayerMask.html)에 대한 Raycast가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-174">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="0b5f7-175">b) Start() 또는 Awake()에서 [캐싱 참조](#cache-references)를 통해 Update()와 같은 반복적인 Unity 콜백에서 GetComponent() 작업을 사용하도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-175">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="0b5f7-176">c) 가능한 경우 초기화 시 모든 개체를 인스턴스화하고 [개체 풀링](#object-pooling)을 사용하여 애플리케이션의 런타임 전체에서 GameObject를 재활용하고 다시 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-176">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="0b5f7-177">**인터페이스 및 가상 구문 사용 방지**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-177">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="0b5f7-178">직접 개체보다 인터페이스를 통해 함수 호출을 호출하거나 가상 함수를 호출하는 경우 종종 직접 구문 또는 직접 함수 호출을 활용하는 것보다 훨씬 더 비쌀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-178">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="0b5f7-179">가상 함수 또는 인터페이스가 필요하지 않은 경우 이를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-179">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="0b5f7-180">그러나 이러한 방법의 성능 결과는 이를 활용하여 개발 협업, 코드 가독성 및 코드 유지 관리가 간소화되는 경우 일반적으로 절충할 만한 가치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-180">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="0b5f7-181">일반적으로 이 멤버를 덮어쓸 필요가 있는 경우에만 필드 및 함수를 가상으로 표시하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-181">Generally, the recommendation is to not mark fields and functions as virtual unless there is a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="0b5f7-182">`UpdateUI()` 메서드와 같이 프레임당 여러 번 또는 한 번 호출되는 빈도가 높은 코드 경로에서는 특히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-182">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="0b5f7-183">**값으로 구조체 전달 방지**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-183">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="0b5f7-184">클래스와 달리 구조체는 값 형식이며, 함수에 직접 전달되면 해당 내용이 새로 만든 인스턴스에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-184">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="0b5f7-185">이 복사본으로 인해 CPU 비용과 스택의 추가 메모리가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-185">This copy adds CPU cost, as well as additional memory on the stack.</span></span> <span data-ttu-id="0b5f7-186">작은 구조체의 경우 효과가 매우 작으므로 일반적으로 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-186">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="0b5f7-187">그러나 모든 프레임을 반복적으로 호출하는 함수와 큰 구조체를 사용하는 함수의 경우 가능하면 함수 정의를 참조로 전달하도록 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-187">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="0b5f7-188">여기서 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-188">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="0b5f7-189">기타</span><span class="sxs-lookup"><span data-stu-id="0b5f7-189">Miscellaneous</span></span>

1) <span data-ttu-id="0b5f7-190">**Physics**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-190">**Physics**</span></span>

    <span data-ttu-id="0b5f7-191">a) 일반적으로 물리학을 향상시키는 가장 쉬운 방법은 Physics에 소요되는 시간 또는 초당 반복 횟수를 제한하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-191">a) Generally, the easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="0b5f7-192">물론 이렇게 하면 시뮬레이션 정확도가 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-192">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="0b5f7-193">Unity의 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-193">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="0b5f7-194">b) Unity의 collider 형식에는 매우 다양한 성능 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-194">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="0b5f7-195">아래 순서는 왼쪽에는 성능이 가장 높은 collider, 오른쪽에는 성능이 가장 낮은 collider의 순서로 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-195">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="0b5f7-196">기본 collider보다 실질적으로 더 비싼 Mesh collider를 사용하지 않도록 방지하는 것이 가장 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-196">It is most important to avoid Mesh Colliders, which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="0b5f7-197">자세한 내용은 [Unity Physics 모범 사례](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-197">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="0b5f7-198">**애니메이션**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-198">**Animations**</span></span>

    <span data-ttu-id="0b5f7-199">Animator 구성 요소를 사용하지 않도록 설정하여 유휴 애니메이션을 사용하지 않도록 설정합니다(게임 개체를 사용하지 않도록 설정하면 동일한 효과가 없음).</span><span class="sxs-lookup"><span data-stu-id="0b5f7-199">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="0b5f7-200">애니메이터가 동일한 값으로 설정하는 반복에 있는 디자인 패턴을 사용하지 않도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-200">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="0b5f7-201">이 기술에는 애플리케이션에 영향을 주지 않지만 상당한 오버헤드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-201">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="0b5f7-202">여기서 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-202">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="0b5f7-203">**복잡한 알고리즘**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-203">**Complex algorithms**</span></span>

    <span data-ttu-id="0b5f7-204">애플리케이션에서 역운동학, 경로 찾기 등과 같은 복잡한 알고리즘을 사용하는 경우 더 간단한 방법을 찾거나 해당 성능과 관련된 설정을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-204">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="0b5f7-205">CPU-GPU 성능 추천 사항</span><span class="sxs-lookup"><span data-stu-id="0b5f7-205">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="0b5f7-206">일반적으로 CPU-GPU 성능은 결국에는 그래픽 카드에 제출되는 **그리기 호출**이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-206">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="0b5f7-207">성능을 향상시키려면 최적의 결과를 얻을 수 있도록 그리기 호출을 전략적으로 **a) 줄이거나** **b) 재구성**해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-207">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="0b5f7-208">그리기 호출 자체는 리소스를 많이 사용하므로 이러한 호출을 줄이면 필요한 전체 작업을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-208">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="0b5f7-209">또한 그리기 호출 간의 상태 변경은 그래픽 드라이버에서 비용이 많이 드는 유효성 검사 및 변환 단계가 필요하므로 상태 변경(즉,</span><span class="sxs-lookup"><span data-stu-id="0b5f7-209">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes (i.e</span></span> <span data-ttu-id="0b5f7-210">다른 재질 등)을 제한하도록 애플리케이션의 그리기 호출을 재구성하면 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-210">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="0b5f7-211">Unity에는 개요를 제공하고 플랫폼에 대한 그리기 호출 일괄 처리를 자세히 살펴볼 수 있는 유용한 문서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-211">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="0b5f7-212">Unity 그리기 호출 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="0b5f7-212">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="0b5f7-213">인스턴스화된 단일 패스 렌더링</span><span class="sxs-lookup"><span data-stu-id="0b5f7-213">Single pass instanced rendering</span></span>

<span data-ttu-id="0b5f7-214">Unity에서 인스턴스화된 단일 패스 렌더링을 사용하면 각 눈에 대한 그리기 호출을 하나의 인스턴스화된 그리기 호출로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-214">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="0b5f7-215">두 그리기 호출 간의 캐시 일관성으로 인해 GPU에서도 성능이 약간 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-215">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="0b5f7-216">Unity 프로젝트에서 이 기능을 사용하도록 설정하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-216">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="0b5f7-217">**플레이어 XR 설정**을 엽니다(**편집** > **프로젝트 설정** > **플레이어** > **XR 설정**으로 차례로 이동).</span><span class="sxs-lookup"><span data-stu-id="0b5f7-217">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="0b5f7-218">**스테레오 렌더링 방법** 드롭다운 메뉴에서 **단일 패스 인스턴스화됨**을 선택합니다(**가상 현실 지원됨** 확인란을 선택해야 함).</span><span class="sxs-lookup"><span data-stu-id="0b5f7-218">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="0b5f7-219">이 렌더링 방법에 대한 자세한 내용은 Unity에서 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-219">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="0b5f7-220">고급 스테레오 렌더링을 사용하여 AR 및 VR 성능을 최대화하는 방법</span><span class="sxs-lookup"><span data-stu-id="0b5f7-220">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="0b5f7-221">단일 패스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="0b5f7-221">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="0b5f7-222">인스턴스화된 단일 패스 렌더링의 일반적인 문제 중 하나는 개발자에게 인스턴스화에 맞게 작성되지 않은 기존 사용자 지정 셰이더가 이미 있는 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-222">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="0b5f7-223">이 기능을 사용하도록 설정하면 개발자가 일부 GameObject를 한쪽 눈에만 렌더링한다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-223">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="0b5f7-224">이는 인스턴스화에 적절한 속성이 연결된 사용자 지정 셰이더에 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-224">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="0b5f7-225">이 문제를 해결하는 방법은 Unity의 [HoloLens에 대한 단일 패스 스테레오 렌더링](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-225">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="0b5f7-226">정적 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="0b5f7-226">Static batching</span></span>

<span data-ttu-id="0b5f7-227">Unity는 많은 정적 개체를 일괄 처리하여 GPU에 대한 그리기 호출을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-227">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="0b5f7-228">정적 일괄 처리는 **1) 동일한 재질을 공유**하고 **2) 모두 *Static*으로 표시**되는 Unity의 [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) 개체 대부분에서 작동합니다(Unity에서 개체를 선택하고 검사기 오른쪽 위의 확인란을 클릭함).</span><span class="sxs-lookup"><span data-stu-id="0b5f7-228">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="0b5f7-229">*Static*으로 표시된 GameObject는 애플리케이션의 런타임 전체에서 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-229">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="0b5f7-230">따라서 정적 일괄 처리는 거의 모든 개체를 배치, 이동, 크기 조정해야 하는 HoloLens에서 활용하기가 어려울 수 있습니다. 몰입형 헤드셋의 경우 정적 일괄 처리를 통해 그리기 호출을 크게 줄여 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-230">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="0b5f7-231">자세한 내용은 [Unity의 그리기 호출 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)에서 *정적 일괄 처리*를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-231">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="0b5f7-232">동적 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="0b5f7-232">Dynamic batching</span></span>

<span data-ttu-id="0b5f7-233">HoloLens 개발에 대해 개체를 *Static*으로 표시하는 것은 문제가 있으므로 동적 일괄 처리는 이러한 부족한 기능을 보완하는 훌륭한 도구가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-233">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="0b5f7-234">물론, 그것은 또한 몰입형 헤드셋에도 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-234">Of course, it can also be useful on immersive headsets, as well.</span></span> <span data-ttu-id="0b5f7-235">그러나 GameObject는 **a) 동일한 Material을 공유**하고 **b) 다른 기준의 긴 목록을 충족**해야 하므로 Unity에서 동적 일괄 처리를 사용하도록 설정하기는 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-235">However, dynamic batching in Unity can be difficult to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="0b5f7-236">자세한 내용은 [Unity의 그리기 호출 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)에서 *동적 일괄 처리*를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-236">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="0b5f7-237">가장 일반적으로 연결된 메시 데이터에는 꼭짓점이 300개 이하이므로 GameObject는 동적으로 일괄 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-237">Most commonly, GameObjects become invalid to be batched dynamically, because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="0b5f7-238">기타 기술</span><span class="sxs-lookup"><span data-stu-id="0b5f7-238">Other techniques</span></span>

<span data-ttu-id="0b5f7-239">여러 GameObject에서 동일한 재질을 공유할 수 있는 경우에만 일괄 처리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-239">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="0b5f7-240">일반적으로 GameObject에는 각 Material에 고유한 질감이 있어야 하므로 이 기술이 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-240">Typically, this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="0b5f7-241">Texture를 하나의 큰 Texture로 결합하는 것이 일반적이며, 이를 [질감 아틀라싱(Texture Atlasing)](https://en.wikipedia.org/wiki/Texture_atlas)이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-241">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="0b5f7-242">또한 일반적으로 메시를 가능하고 합리적인 하나의 GameObject에 결합하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-242">Furthermore, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="0b5f7-243">하나의 Renderer 아래에 결합된 메시를 제출하는 것과 비교하여 Unity의 각 Renderer에는 연결된 그리기 호출이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-243">Each Renderer in Unity will have its associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="0b5f7-244">런타임에 Renderer.material의 속성을 수정하면 Material의 복사본이 만들어지고 이로 인해 일괄 처리가 중단될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-244">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="0b5f7-245">Renderer.sharedMaterial을 사용하여 GameObject에서 공유 재질 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-245">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="0b5f7-246">GPU 성능 추천 사항</span><span class="sxs-lookup"><span data-stu-id="0b5f7-246">GPU performance recommendations</span></span>

<span data-ttu-id="0b5f7-247">[Unity에서 그래픽 렌더링을 최적화하는 방법](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-247">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="0b5f7-248">깊이 버퍼 공유 최적화</span><span class="sxs-lookup"><span data-stu-id="0b5f7-248">Optimize depth buffer sharing</span></span>

<span data-ttu-id="0b5f7-249">일반적으로 **플레이어 XR 설정** 아래에서 **깊이 버퍼 공유**를 사용하도록 설정하여 [홀로그램 안정성](Hologram-stability.md)을 최적화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-249">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="0b5f7-250">그러나 이 설정을 사용하여 깊이 기반 후기 단계 리프로젝션을 사용하도록 설정할 경우 **24비트 깊이 형식** 대신 **16비트 깊이 형식**을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-250">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="0b5f7-251">16비트 깊이 버퍼는 깊이 버퍼 트래픽과 관련된 대역폭(이에 따라 전력)을 크게 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-251">The 16-bit depth buffers will drastically reduce the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="0b5f7-252">이는 전력 감소와 성능 향상 모두에서 큰 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-252">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="0b5f7-253">그러나 *16비트 깊이 형식*을 사용하면 두 측면에서 모두 부정적인 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-253">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="0b5f7-254">**Z-Fighting**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-254">**Z-Fighting**</span></span>

<span data-ttu-id="0b5f7-255">깊이 범위 충실도가 낮아지면 24비트보다 16비트에서 [z-fighting](https://en.wikipedia.org/wiki/Z-fighting)이 발생할 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-255">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="0b5f7-256">이러한 아티팩트를 방지하려면 정밀도를 낮추도록 [Unity 카메라](https://docs.unity3d.com/Manual/class-Camera.html)의 근거리/원거리 클립 평면을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-256">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="0b5f7-257">HoloLens 기반 애플리케이션의 경우 일반적으로 Unity 기본값인 1,000m 대신 50m의 원거리 클립 평면을 사용하여 z-fighting을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-257">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="0b5f7-258">**사용하지 않도록 설정된 스텐실 버퍼**</span><span class="sxs-lookup"><span data-stu-id="0b5f7-258">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="0b5f7-259">Unity에서 [16비트 깊이의 렌더링 질감](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)을 만드는 경우 스텐실 버퍼가 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-259">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there is no stencil buffer created.</span></span> <span data-ttu-id="0b5f7-260">Unity 설명서에 따라 24비트 깊이 형식을 선택하면 24비트 z 버퍼와 [8비트 스텐실 버퍼](https://docs.unity3d.com/Manual/SL-Stencil.html) 가 만들어집니다(32비트가 디바이스에 적용되는 경우이며, 일반적으로 HoloLens와 동일한 경우임).</span><span class="sxs-lookup"><span data-stu-id="0b5f7-260">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer, as well as an [8-bit stencil buffer] (https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on a device, which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="0b5f7-261">전체 화면 효과 사용 방지</span><span class="sxs-lookup"><span data-stu-id="0b5f7-261">Avoid full-screen effects</span></span>

<span data-ttu-id="0b5f7-262">각 프레임의 크기에서 수백만 개의 작업을 요구하므로 전체 화면에서 작동하는 기술에는 비용이 많이 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-262">Techniques that operate on the full screen can be quite expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="0b5f7-263">따라서 앤티 앨리어싱, 블룸 등과 같은 [후 처리 효과](https://docs.unity3d.com/Manual/PostProcessingOverview.html)를 사용하지 않도록 방지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-263">Thus, it is recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="0b5f7-264">최적 조명 설정</span><span class="sxs-lookup"><span data-stu-id="0b5f7-264">Optimal lighting settings</span></span>

<span data-ttu-id="0b5f7-265">Unity의 [실시간 글로벌 조명](https://docs.unity3d.com/Manual/GIIntro.html)은 뛰어난 시각적 결과를 제공할 수 있지만 상당히 비싼 조명 계산이 수반됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-265">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide outstanding visual results but involves quite expensive lighting calculations.</span></span> <span data-ttu-id="0b5f7-266">**창** > **렌더링** > **조명 설정** > **실시간 글로벌 조명** 선택 취소를 통해 모든 Unity 장면 파일에 대해 실시간 글로벌 조명을 사용하지 않도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-266">It is recommended to disable Realtime Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="0b5f7-267">또한 이 기술은 Unity 장면에 비용이 많이 드는 GPU 패스를 추가하므로 모든 섀도 캐스팅을 사용하지 않도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-267">Furthermore, it is recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="0b5f7-268">섀도는 조명별로 사용하지 않도록 설정할 수 있지만 품질 설정을 통해 전체적으로 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-268">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="0b5f7-269">**편집** > **프로젝트 설정**을 선택한 다음, **품질** 범주를 선택하고, UWP 플랫폼에 대해 **낮은 품질**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-269">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="0b5f7-270">**섀도** 속성을 **섀도 사용 안 함**으로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-270">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

<span data-ttu-id="0b5f7-271">Unity의 모델에서 굽기 조명을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-271">It is recommended that you use baked lighting with your models in Unity.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="0b5f7-272">다각형 수 감소</span><span class="sxs-lookup"><span data-stu-id="0b5f7-272">Reduce poly count</span></span>

<span data-ttu-id="0b5f7-273">다각형 수는 일반적으로 다음 방법 중 하나를 사용하여 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-273">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="0b5f7-274">장면에서 개체 제거</span><span class="sxs-lookup"><span data-stu-id="0b5f7-274">Removing objects from a scene</span></span>
2) <span data-ttu-id="0b5f7-275">지정된 메시의 다각형 수를 줄이는 자산 부분 제거</span><span class="sxs-lookup"><span data-stu-id="0b5f7-275">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="0b5f7-276">동일한 기하 도형의 낮은 다각형 버전을 사용하여 멀리 떨어진 개체를 렌더링하는 애플리케이션에 [LOD(세부 정보 수준) 시스템](https://docs.unity3d.com/Manual/LevelOfDetail.html) 구현</span><span class="sxs-lookup"><span data-stu-id="0b5f7-276">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="0b5f7-277">Unity의 셰이더에 대한 이해</span><span class="sxs-lookup"><span data-stu-id="0b5f7-277">Understanding shaders in Unity</span></span>

<span data-ttu-id="0b5f7-278">성능에서 셰이더를 쉽게 비교할 수 있는 대략적인 방법은 런타임에서 각각 실행되는 평균 작업 수를 식별하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-278">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="0b5f7-279">이 작업은 Unity에서 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-279">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="0b5f7-280">셰이더 자산을 선택하거나 재질을 선택한 다음, 검사기 창의 오른쪽 위 모서리에서 기어 아이콘을 선택한 다음, **"셰이더 선택"** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-280">Select your shader asset or select a material, then in the top right corner of the inspector window, select the gear icon followed by **"Select Shader"**</span></span>

    ![Unity에서 셰이더 선택](images/Select-shader-unity.png)
2) <span data-ttu-id="0b5f7-282">셰이더 자산을 선택한 상태에서 검사기 창 아래쪽에서 **"코드 컴파일 및 표시"** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-282">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![Unity에서 셰이더 코드 컴파일](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="0b5f7-284">컴파일되면 꼭짓점 및 픽셀 셰이더 모두에 대한 다양한 작업 수가 포함된 결과에서 통계 섹션을 찾습니다(참고: 픽셀 셰이더는 종종 조각 셰이더라고도 함).</span><span class="sxs-lookup"><span data-stu-id="0b5f7-284">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 표준 셰이더 작업](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a><span data-ttu-id="0b5f7-286">픽셀 셰이더 최적화</span><span class="sxs-lookup"><span data-stu-id="0b5f7-286">Optimize pixel shaders</span></span>

<span data-ttu-id="0b5f7-287">위의 방법을 사용하여 컴파일된 통계 결과를 살펴보면 일반적으로 [조각 셰이더](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)에서 평균적으로 [꼭짓점 셰이더](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)보다 더 많은 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-287">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), on average.</span></span> <span data-ttu-id="0b5f7-288">픽셀 셰이더라고도 하는 조각 셰이더는 화면 출력에서 픽셀 단위로 실행되지만, 꼭짓점 셰이더는 화면에 그려지는 모든 메시의 꼭짓점 단위로만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-288">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="0b5f7-289">따라서 모든 조명 계산으로 인해 조각 셰이더에는 꼭짓점 셰이더보다 더 많은 명령이 포함될 뿐만 아니라, 조각 셰이더가 거의 항상 더 큰 데이터 세트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-289">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="0b5f7-290">예를 들어 화면 출력이 2,000 x 2,000 이미지인 경우 조각 셰이더는 2,000 \* 2,000 = 4,000,000회 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-290">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="0b5f7-291">두 눈을 렌더링하는 경우 두 개의 화면이 있으므로 이 횟수가 두 배가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-291">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="0b5f7-292">혼합 현실 애플리케이션에서 여러 패스, 전체 화면 후 처리 효과 또는 동일한 픽셀에 여러 메시 렌더링을 수행하는 경우 이 횟수는 크게 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-292">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="0b5f7-293">따라서 조각 셰이더의 작업 수를 줄이면 일반적으로 꼭짓점 셰이더의 최적화에 비해 훨씬 더 큰 성능 향상을 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-293">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="0b5f7-294">Unity 표준 셰이더 대안</span><span class="sxs-lookup"><span data-stu-id="0b5f7-294">Unity Standard shader alternatives</span></span>

<span data-ttu-id="0b5f7-295">PBR(물리적 기반 렌더링) 또는 다른 고품질 셰이더를 사용하는 대신, 성능이 더 뛰어나고 저렴한 셰이더를 활용하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-295">Instead of using a physically based rendering (PBR) or another high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="0b5f7-296">[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)는 혼합 현실 프로젝트에 최적화된 [MRTK 표준 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-296">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="0b5f7-297">또한 Unity는 Unity 표준 셰이더에 비해 훨씬 빠른 unlit(꺼짐), vertex lit(꼭짓점 깜박임), diffuse(확산) 및 간소화된 다른 셰이더 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-297">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="0b5f7-298">자세한 내용은 [기본 제공 셰이더 사용 및 성능](https://docs.unity3d.com/Manual/shader-Performance.html)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-298">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="0b5f7-299">셰이더 미리 로드</span><span class="sxs-lookup"><span data-stu-id="0b5f7-299">Shader preloading</span></span>

<span data-ttu-id="0b5f7-300">*셰이더 미리 로드* 및 기타 트릭을 사용하여 [셰이더 로드 시간](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)을 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-300">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="0b5f7-301">특히 셰이더 미리 로드는 런타임 셰이더 컴파일로 인해 길이 조정이 표시되지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-301">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="0b5f7-302">과도한 그리기 제한</span><span class="sxs-lookup"><span data-stu-id="0b5f7-302">Limit overdraw</span></span>

<span data-ttu-id="0b5f7-303">Unity에서 **장면 보기**의 왼쪽 위 모서리에서 [**그리기 모드 메뉴**](https://docs.unity3d.com/Manual/ViewModes.html)를 전환하고 **과도한 그리기**를 선택하여 해당 장면에 대한 과도한 그리기를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-303">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top-left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="0b5f7-304">일반적으로 과도한 그리기는 GPU로 보내기 전에 개체를 미리 선별하여 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-304">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="0b5f7-305">Unity는 [폐색 선별 기능](https://docs.unity3d.com/Manual/OcclusionCulling.html)을 해당 엔진에 구현하는 방법에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-305">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="0b5f7-306">메모리 추천 사항</span><span class="sxs-lookup"><span data-stu-id="0b5f7-306">Memory recommendations</span></span>

<span data-ttu-id="0b5f7-307">과도한 메모리 할당 및 할당 취소 작업은 홀로그램 애플리케이션에 부정적인 영향을 줄 수 있으므로 일관성 없는 성능, 고정된 프레임 및 기타 부정적인 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-307">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application, resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="0b5f7-308">메모리 관리는 가비지 수집기를 통해 제어되므로 Unity에서 개발하는 경우 메모리 고려 사항을 이해하는 것이 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-308">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="0b5f7-309">가비지 컬렉션</span><span class="sxs-lookup"><span data-stu-id="0b5f7-309">Garbage collection</span></span>

<span data-ttu-id="0b5f7-310">실행 중에 더 이상 범위에 있지 않은 개체를 분석하기 위해 GC를 활성화하고 메모리를 해제해야 할 때 홀로그램 앱에서 GC(가비지 수집기)에 대한 처리 컴퓨팅 시간을 상실하여 다시 사용할 수 있도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-310">Holographic apps will lose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released, so it can be made available for re-use.</span></span> <span data-ttu-id="0b5f7-311">지속적인 할당 및 할당 취소는 일반적으로 가비지 수집기를 더 자주 실행해야 하므로 성능과 사용자 환경이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-311">Constant allocations and de-allocations will generally require the garbage collector to run more frequently, thus hurting performance and user experience.</span></span>

<span data-ttu-id="0b5f7-312">Unity는 가비지 수집기의 작동 방식 및 메모리 관리와 관련된 더 효율적인 코드를 작성하기 위한 팁을 자세히 설명하는 매우 유용한 페이지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-312">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="0b5f7-313">Unity 게임에서 가비지 컬렉션 최적화</span><span class="sxs-lookup"><span data-stu-id="0b5f7-313">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="0b5f7-314">과도한 가비지 컬렉션으로 이어지는 가장 일반적인 사례 중 하나는 Unity 개발에서 구성 요소 및 클래스에 대한 참조를 캐시하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-314">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="0b5f7-315">모든 참조는 Start() 또는 Awake() 중에 캡처되고, Update() 또는 LateUpdate()와 같은 이후 함수에서 다시 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-315">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="0b5f7-316">기타 빠른 팁:</span><span class="sxs-lookup"><span data-stu-id="0b5f7-316">Other quick tips:</span></span>
- <span data-ttu-id="0b5f7-317">런타임에 복잡한 문자열을 동적으로 빌드하려면 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-317">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="0b5f7-318">앱의 모든 빌드 버전에서 계속 실행되므로 더 이상 필요하지 않은 Debug.Log()에 대한 호출을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-318">Remove calls to Debug.Log() when no longer needed, as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="0b5f7-319">홀로그램 앱에 일반적으로 많은 메모리가 필요한 경우 로드 또는 전환 화면을 표시할 때와 같이 로드 단계 중에 [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)를 호출하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-319">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="0b5f7-320">개체 풀링</span><span class="sxs-lookup"><span data-stu-id="0b5f7-320">Object pooling</span></span>

<span data-ttu-id="0b5f7-321">개체 풀링은 개체의 지속적인 할당 및 할당 취소에 드는 비용을 줄이는 데 널리 사용되는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-321">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="0b5f7-322">이 작업을 수행하려면 시간이 지남에 따라 개체를 지속적으로 만들고 삭제하는 대신, 동일한 개체의 대량 풀을 할당하고 이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-322">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="0b5f7-323">개체 풀은 앱 중에 수명이 가변적인 다시 사용할 수 있는 구성 요소에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-323">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="0b5f7-324">Unity의 개체 풀링 자습서</span><span class="sxs-lookup"><span data-stu-id="0b5f7-324">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="0b5f7-325">시작 성능</span><span class="sxs-lookup"><span data-stu-id="0b5f7-325">Startup performance</span></span>

<span data-ttu-id="0b5f7-326">앱을 더 작은 장면으로 시작한 다음, *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 를 사용하여 나머지 장면을 로드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-326">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="0b5f7-327">이렇게 하면 앱이 최대한 빨리 대화형 상태로 전환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-327">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="0b5f7-328">새 장면이 활성화되는 동안 높은 CPU 스파이크가 발생할 수 있으며 렌더링된 콘텐츠가 끊기거나 길이가 조정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-328">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="0b5f7-329">이 문제를 해결하는 한 가지 방법은 로드되는 장면에서 AsyncOperation.allowSceneActivation 속성을 "false"로 설정하고, 장면이 로드될 때까지 기다리고, 화면을 검은색으로 지운 다음, "true"로 다시 설정하여 장면 활성화를 완료하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-329">One way to work around this is to set the AsyncOperation.allowSceneActivation property to "false" on the scene being loaded, wait for the scene to load, clear the screen to black, and then set it back to "true" to complete the scene activation.</span></span>

<span data-ttu-id="0b5f7-330">시작 장면을 로드하는 동안 사용자에게 홀로그램 시작 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b5f7-330">Remember that while the startup scene is loading, the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b5f7-331">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b5f7-331">See also</span></span>
- [<span data-ttu-id="0b5f7-332">Unity 게임에서 그래픽 렌더링 최적화</span><span class="sxs-lookup"><span data-stu-id="0b5f7-332">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="0b5f7-333">Unity 게임에서 가비지 컬렉션 최적화</span><span class="sxs-lookup"><span data-stu-id="0b5f7-333">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="0b5f7-334">[Physics 모범 사례[Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="0b5f7-334">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="0b5f7-335">[스크립트 최적화[Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="0b5f7-335">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
