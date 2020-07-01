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
# <a name="performance-recommendations-for-unity"></a>Unity에 대한 성능 추천 사항

이 문서에서는 [혼합 현실에 대한 성능 추천 사항](understanding-performance-for-mixed-reality.md)에 요약된 설명을 기반으로 하지만, Unity 엔진 환경과 관련된 학습에 집중하고 있습니다.

## <a name="use-recommended-unity-project-settings"></a>권장 Unity 프로젝트 설정 사용

Unity에서 혼합 현실 앱의 성능을 최적화할 때 가장 중요한 첫 번째 단계는 [Unity 권장 환경 설정](recommended-settings-for-unity.md)을 사용하는 것입니다. 해당 문서에는 성능이 뛰어난 Mixed Reality 앱을 빌드하는 데 가장 중요한 장면 구성에 대한 일부 내용이 나와 있습니다. 아래에서는 이러한 추천 설정 중 일부를 강조하고 있습니다.

## <a name="how-to-profile-with-unity"></a>Unity를 사용하여 프로파일링하는 방법

Unity는 기본적으로 **[Unity 프로파일러](https://docs.unity3d.com/Manual/Profiler.html)** 를 제공하며, 이는 특정 앱에 대한 중요한 성능 인사이트를 수집할 수 있는 유용한 리소스입니다. 편집기 내에서 프로파일러를 실행할 수 있지만, 이러한 메트릭은 실제 런타임 환경을 나타내지 않으므로 해당 메트릭의 결과는 신중하게 사용해야 합니다. 가장 정확하고 실행 가능한 인사이트를 얻으려면 디바이스에서 실행하는 동안 애플리케이션을 원격으로 프로파일링하는 것이 좋습니다. 또한 Unity의 [프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html)도 매우 강력하고 인사이트를 제공하는 도구입니다.

Unity는 다음 항목에 대한 유용한 문서를 제공합니다.
1) [Unity 프로파일러를 UWP 애플리케이션에 원격으로 연결](https://docs.unity3d.com/Manual/windowsstore-profiler.html)하는 방법
2) [Unity 프로파일러를 사용하여 성능 문제를 효과적으로 진단](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)하는 방법

>[!NOTE]
> Unity 프로파일러가 연결되고 GPU 프로파일러가 추가되면(오른쪽 위 모서리의 *프로파일러 추가* 참조) 프로파일러 가운데에서 CPU 및 GPU 각각에 소요되는 시간을 확인할 수 있습니다. 애플리케이션이 CPU 또는 GPU에 바인딩되어 있는 경우 개발자는 이를 통해 근사값을 빠르게 얻을 수 있습니다.
>
> ![Unity CPU 및 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 성능 추천 사항

아래 내용은 특히 Unity 및 C# 개발을 대상으로 하는 자세한 성능 사례에 대해 설명합니다.

#### <a name="cache-references"></a>캐시 참조

초기화 시 모든 관련 구성 요소 및 GameObject에 대한 참조를 캐시하는 것이 좋습니다. 이는 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 와 같은 반복 함수 호출이 포인터를 저장하는 메모리 비용보다 훨씬 더 비싸기 때문입니다. 또한 이는 매우 일반적으로 사용되는 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)에도 적용됩니다. *Camera.main*은 실제로 아래의 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 만 사용합니다. 이는 *"MainCamera"* 태그를 사용하여 장면 그래프에서 카메라 개체를 검색하지만 많은 비용이 들어갑니다.

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
> GetComponent(문자열) 사용 방지 <br/>
> *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 를 사용하는 경우 몇 가지 오버로드가 있습니다. 항상 형식 기반 구현을 사용하고, 문자열 기반 검색 오버로드를 사용하지 않는 것이 중요합니다. 장면에서 문자열로 검색하는 경우 Type을 기준으로 검색하는 것보다 훨씬 더 비쌉니다. <br/>
> (좋음) GetComponent(Type 형식) 구성 요소 <br/>
> (좋음) T GetComponent\<T>() <br/>
> (나쁨) GetComponent(문자열)> 구성 요소 <br/>

#### <a name="avoid-expensive-operations"></a>비용이 많이 드는 작업 방지

1) **[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq) 사용 방지**

    LINQ는 매우 깔끔하고 쉽게 읽고 쓸 수 있지만, 일반적으로 알고리즘을 수동으로 작성하는 것보다 훨씬 더 많은 계산, 특히 더 많은 메모리 할당이 필요합니다.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **일반 Unity API**

    일부 Unity API는 유용하지만 실행 비용이 매우 많이 들 수 있습니다. 이러한 API 중 대부분은 전체 장면 그래프에서 일치하는 몇 가지 GameObject 목록을 찾습니다. 일반적으로 런타임에 참조를 추적하기 위해 참조를 캐시하거나 해당 GameObject에 대한 관리자 구성 요소를 구현하여 이러한 작업을 방지할 수 있습니다.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 및 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 는 반드시 제거해야 합니다. 이러한 함수는 직접 함수 호출보다 1,000배 더 느릴 수 있습니다.

3) **boxing에 주의**

    [boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)은 C# 언어 및 런타임의 핵심 개념입니다. 이는 char, int, bool 등과 같은 값 형식 변수를 참조 형식 변수로 래핑하는 프로세스입니다. 값 형식 변수가 "boxing"되면 관리형 힙에 저장된 System.Object 내부에 래핑됩니다. 이에 따라 메모리가 할당되며, 결국에는 삭제 시 가비지 수집기에서 처리해야 합니다. 이러한 할당 및 할당 취소는 성능 비용을 발생시키며, 많은 시나리오에서 필요하지 않거나 비용이 더 저렴한 대안으로 쉽게 대체할 수 있습니다.

    개발에서 가장 일반적인 boxing 형태 중 하나는 [nullable 값 형식](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)을 사용하는 것입니다. 특히 작업에서 값을 가져오는 데 실패하는 경우 함수에서 일반적으로 값 형식으로 null을 반환하려고 시도할 수 있습니다. 이 방법의 잠재적인 문제는 이제 할당이 힙에서 발생하므로 나중에 가비지를 수집해야 한다는 것입니다.

    **C#의 boxing 예제**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **nullable 값 형식을 통한 문제가 있는 boxing의 예제**

    다음 코드에서는 Unity 프로젝트에서 만들 수 있는 더미 파티클 클래스를 보여 줍니다. `TryGetSpeed()`를 호출하면 개체가 힙에 할당되며, 나중에 가비지를 수집해야 합니다. 이 예제는 한 장면에 1,000개 이상의 파티클이 있을 수 있으므로 특히 문제가 되며, 각각 현재 속도를 요구하고 있습니다. 따라서 1,000개의 개체가 할당되고, 결과적으로 모든 프레임에서 할당을 취소하여 성능이 크게 저하됩니다. 오류를 나타내기 위해 -1과 같은 음수 값을 반환하도록 함수를 다시 작성하면 이 문제가 방지되고 메모리가 스택에서 유지됩니다.

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

#### <a name="repeating-code-paths"></a>반복 코드 경로

초당 여러 번 실행되는 Unity 콜백 반복 함수(예: Update) 및/또는 프레임은 매우 신중하게 작성해야 합니다. 여기서 비용이 많이 드는 작업은 성능에 크고 일관된 영향을 미칠 수 있습니다.

1) **빈 콜백 함수**

    아래 코드는 애플리케이션에 남겨 두는 것이 무해한 것처럼 보일 수 있지만, 특히 모든 Unity 스크립트가 이 코드 블록을 사용하여 자동으로 초기화되므로 이러한 빈 콜백은 실제로 매우 비쌀 수 있습니다. Unity는 UnityEngine 코드와 애플리케이션 코드 간에 비관리/관리 코드 경계를 넘나들며 작동합니다. 이 브리지를 통해 컨텍스트를 전환하는 것은 실행하는 작업이 없더라도 비용이 매우 많이 듭니다. 반복되는 빈 Unity 콜백이 있는 구성 요소가 포함된 100개의 GameObject가 앱에 있는 경우 특히 문제가 됩니다.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update()는 이 성능 문제의 가장 일반적인 증상이지만 다른 Unity 콜백(예: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage() 등)은 나쁘지 않은 경우에도 마찬가지로 나쁠 수 있습니다. 

2) **프레임당 한 번 실행되도록 하는 작업**

    다음 Unity API는 많은 홀로그램 앱의 일반적인 작업입니다. 이러한 함수의 결과는 항상 가능한 것은 아니지만 일반적으로 한 번 계산될 수 있으며, 지정된 프레임에 대해 애플리케이션 전체에서 다시 사용할 수 있습니다.

    a) 일반적으로 각 구성 요소에서 반복적이고 본질적으로 동일한 Raycast 작업을 수행하는 대신, 장면에서 Raycast를 응시하도록 처리한 다음, 이 결과를 다른 모든 장면 구성 요소에서 다시 사용하는 전용 Singleton 클래스 또는 서비스를 사용하는 것이 좋습니다. 물론 일부 애플리케이션에는 다른 원본 또는 다른 [LayerMask](https://docs.unity3d.com/ScriptReference/LayerMask.html)에 대한 Raycast가 필요할 수 있습니다.

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) Start() 또는 Awake()에서 [캐싱 참조](#cache-references)를 통해 Update()와 같은 반복적인 Unity 콜백에서 GetComponent() 작업을 사용하도록 방지합니다.

        UnityEngine.Object.GetComponent()

    c) 가능한 경우 초기화 시 모든 개체를 인스턴스화하고 [개체 풀링](#object-pooling)을 사용하여 애플리케이션의 런타임 전체에서 GameObject를 재활용하고 다시 사용하는 것이 좋습니다.

        UnityEngine.Object.Instantiate()

3) **인터페이스 및 가상 구문 사용 방지**

    직접 개체보다 인터페이스를 통해 함수 호출을 호출하거나 가상 함수를 호출하는 경우 종종 직접 구문 또는 직접 함수 호출을 활용하는 것보다 훨씬 더 비쌀 수 있습니다. 가상 함수 또는 인터페이스가 필요하지 않은 경우 이를 제거해야 합니다. 그러나 이러한 방법의 성능 결과는 이를 활용하여 개발 협업, 코드 가독성 및 코드 유지 관리가 간소화되는 경우 일반적으로 절충할 만한 가치가 있습니다.

    일반적으로 이 멤버를 덮어쓸 필요가 있는 경우에만 필드 및 함수를 가상으로 표시하는 것이 좋습니다. `UpdateUI()` 메서드와 같이 프레임당 여러 번 또는 한 번 호출되는 빈도가 높은 코드 경로에서는 특히 주의해야 합니다.

4) **값으로 구조체 전달 방지**

    클래스와 달리 구조체는 값 형식이며, 함수에 직접 전달되면 해당 내용이 새로 만든 인스턴스에 복사됩니다. 이 복사본으로 인해 CPU 비용과 스택의 추가 메모리가 추가됩니다. 작은 구조체의 경우 효과가 매우 작으므로 일반적으로 허용됩니다. 그러나 모든 프레임을 반복적으로 호출하는 함수와 큰 구조체를 사용하는 함수의 경우 가능하면 함수 정의를 참조로 전달하도록 수정합니다. [여기서 자세히 알아보세요.](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>기타

1) **Physics**

    a) 일반적으로 물리학을 향상시키는 가장 쉬운 방법은 Physics에 소요되는 시간 또는 초당 반복 횟수를 제한하는 것입니다. 물론 이렇게 하면 시뮬레이션 정확도가 떨어집니다. Unity의 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)를 참조하세요.

    b) Unity의 collider 형식에는 매우 다양한 성능 특징이 있습니다. 아래 순서는 왼쪽에는 성능이 가장 높은 collider, 오른쪽에는 성능이 가장 낮은 collider의 순서로 나열되어 있습니다. 기본 collider보다 실질적으로 더 비싼 Mesh collider를 사용하지 않도록 방지하는 것이 가장 중요합니다.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    자세한 내용은 [Unity Physics 모범 사례](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)를 참조하세요.

2) **애니메이션**

    Animator 구성 요소를 사용하지 않도록 설정하여 유휴 애니메이션을 사용하지 않도록 설정합니다(게임 개체를 사용하지 않도록 설정하면 동일한 효과가 없음). 애니메이터가 동일한 값으로 설정하는 반복에 있는 디자인 패턴을 사용하지 않도록 방지합니다. 이 기술에는 애플리케이션에 영향을 주지 않지만 상당한 오버헤드가 있습니다. [여기서 자세히 알아보세요.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **복잡한 알고리즘**

    애플리케이션에서 역운동학, 경로 찾기 등과 같은 복잡한 알고리즘을 사용하는 경우 더 간단한 방법을 찾거나 해당 성능과 관련된 설정을 조정합니다.

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU-GPU 성능 추천 사항

일반적으로 CPU-GPU 성능은 결국에는 그래픽 카드에 제출되는 **그리기 호출**이 됩니다. 성능을 향상시키려면 최적의 결과를 얻을 수 있도록 그리기 호출을 전략적으로 **a) 줄이거나** **b) 재구성**해야 합니다. 그리기 호출 자체는 리소스를 많이 사용하므로 이러한 호출을 줄이면 필요한 전체 작업을 줄일 수 있습니다. 또한 그리기 호출 간의 상태 변경은 그래픽 드라이버에서 비용이 많이 드는 유효성 검사 및 변환 단계가 필요하므로 상태 변경(즉, 다른 재질 등)을 제한하도록 애플리케이션의 그리기 호출을 재구성하면 성능이 향상될 수 있습니다.

Unity에는 개요를 제공하고 플랫폼에 대한 그리기 호출 일괄 처리를 자세히 살펴볼 수 있는 유용한 문서가 있습니다.
- [Unity 그리기 호출 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>인스턴스화된 단일 패스 렌더링

Unity에서 인스턴스화된 단일 패스 렌더링을 사용하면 각 눈에 대한 그리기 호출을 하나의 인스턴스화된 그리기 호출로 줄일 수 있습니다. 두 그리기 호출 간의 캐시 일관성으로 인해 GPU에서도 성능이 약간 향상됩니다.

Unity 프로젝트에서 이 기능을 사용하도록 설정하려면 다음을 수행합니다.
1)  **플레이어 XR 설정**을 엽니다(**편집** > **프로젝트 설정** > **플레이어** > **XR 설정**으로 차례로 이동).
2) **스테레오 렌더링 방법** 드롭다운 메뉴에서 **단일 패스 인스턴스화됨**을 선택합니다(**가상 현실 지원됨** 확인란을 선택해야 함).

이 렌더링 방법에 대한 자세한 내용은 Unity에서 다음 문서를 참조하세요.
- [고급 스테레오 렌더링을 사용하여 AR 및 VR 성능을 최대화하는 방법](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [단일 패스 인스턴스화](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 인스턴스화된 단일 패스 렌더링의 일반적인 문제 중 하나는 개발자에게 인스턴스화에 맞게 작성되지 않은 기존 사용자 지정 셰이더가 이미 있는 경우에 발생합니다. 이 기능을 사용하도록 설정하면 개발자가 일부 GameObject를 한쪽 눈에만 렌더링한다는 것을 알 수 있습니다. 이는 인스턴스화에 적절한 속성이 연결된 사용자 지정 셰이더에 없기 때문입니다.
>
> 이 문제를 해결하는 방법은 Unity의 [HoloLens에 대한 단일 패스 스테레오 렌더링](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)을 참조하세요.

#### <a name="static-batching"></a>정적 일괄 처리

Unity는 많은 정적 개체를 일괄 처리하여 GPU에 대한 그리기 호출을 줄일 수 있습니다. 정적 일괄 처리는 **1) 동일한 재질을 공유**하고 **2) 모두 *Static*으로 표시**되는 Unity의 [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) 개체 대부분에서 작동합니다(Unity에서 개체를 선택하고 검사기 오른쪽 위의 확인란을 클릭함). *Static*으로 표시된 GameObject는 애플리케이션의 런타임 전체에서 이동할 수 없습니다. 따라서 정적 일괄 처리는 거의 모든 개체를 배치, 이동, 크기 조정해야 하는 HoloLens에서 활용하기가 어려울 수 있습니다. 몰입형 헤드셋의 경우 정적 일괄 처리를 통해 그리기 호출을 크게 줄여 성능을 향상시킬 수 있습니다.

자세한 내용은 [Unity의 그리기 호출 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)에서 *정적 일괄 처리*를 참조하세요.

#### <a name="dynamic-batching"></a>동적 일괄 처리

HoloLens 개발에 대해 개체를 *Static*으로 표시하는 것은 문제가 있으므로 동적 일괄 처리는 이러한 부족한 기능을 보완하는 훌륭한 도구가 될 수 있습니다. 물론, 그것은 또한 몰입형 헤드셋에도 유용할 수 있습니다. 그러나 GameObject는 **a) 동일한 Material을 공유**하고 **b) 다른 기준의 긴 목록을 충족**해야 하므로 Unity에서 동적 일괄 처리를 사용하도록 설정하기는 어려울 수 있습니다.

자세한 내용은 [Unity의 그리기 호출 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)에서 *동적 일괄 처리*를 참조하세요. 가장 일반적으로 연결된 메시 데이터에는 꼭짓점이 300개 이하이므로 GameObject는 동적으로 일괄 처리할 수 없습니다.

#### <a name="other-techniques"></a>기타 기술

여러 GameObject에서 동일한 재질을 공유할 수 있는 경우에만 일괄 처리를 수행할 수 있습니다. 일반적으로 GameObject에는 각 Material에 고유한 질감이 있어야 하므로 이 기술이 차단됩니다. Texture를 하나의 큰 Texture로 결합하는 것이 일반적이며, 이를 [질감 아틀라싱(Texture Atlasing)](https://en.wikipedia.org/wiki/Texture_atlas)이라고 합니다.

또한 일반적으로 메시를 가능하고 합리적인 하나의 GameObject에 결합하는 것이 좋습니다. 하나의 Renderer 아래에 결합된 메시를 제출하는 것과 비교하여 Unity의 각 Renderer에는 연결된 그리기 호출이 있습니다.

>[!NOTE]
> 런타임에 Renderer.material의 속성을 수정하면 Material의 복사본이 만들어지고 이로 인해 일괄 처리가 중단될 수 있습니다. Renderer.sharedMaterial을 사용하여 GameObject에서 공유 재질 속성을 수정합니다.

## <a name="gpu-performance-recommendations"></a>GPU 성능 추천 사항

[Unity에서 그래픽 렌더링을 최적화하는 방법](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)에 대해 자세히 알아보세요.

### <a name="optimize-depth-buffer-sharing"></a>깊이 버퍼 공유 최적화

일반적으로 **플레이어 XR 설정** 아래에서 **깊이 버퍼 공유**를 사용하도록 설정하여 [홀로그램 안정성](Hologram-stability.md)을 최적화하는 것이 좋습니다. 그러나 이 설정을 사용하여 깊이 기반 후기 단계 리프로젝션을 사용하도록 설정할 경우 **24비트 깊이 형식** 대신 **16비트 깊이 형식**을 선택하는 것이 좋습니다. 16비트 깊이 버퍼는 깊이 버퍼 트래픽과 관련된 대역폭(이에 따라 전력)을 크게 줄입니다. 이는 전력 감소와 성능 향상 모두에서 큰 결과를 얻을 수 있습니다. 그러나 *16비트 깊이 형식*을 사용하면 두 측면에서 모두 부정적인 결과가 발생할 수 있습니다.

**Z-Fighting**

깊이 범위 충실도가 낮아지면 24비트보다 16비트에서 [z-fighting](https://en.wikipedia.org/wiki/Z-fighting)이 발생할 가능성이 높아집니다. 이러한 아티팩트를 방지하려면 정밀도를 낮추도록 [Unity 카메라](https://docs.unity3d.com/Manual/class-Camera.html)의 근거리/원거리 클립 평면을 수정합니다. HoloLens 기반 애플리케이션의 경우 일반적으로 Unity 기본값인 1,000m 대신 50m의 원거리 클립 평면을 사용하여 z-fighting을 제거할 수 있습니다.

**사용하지 않도록 설정된 스텐실 버퍼**

Unity에서 [16비트 깊이의 렌더링 질감](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)을 만드는 경우 스텐실 버퍼가 만들어지지 않습니다. Unity 설명서에 따라 24비트 깊이 형식을 선택하면 24비트 z 버퍼와 [8비트 스텐실 버퍼](https://docs.unity3d.com/Manual/SL-Stencil.html) 가 만들어집니다(32비트가 디바이스에 적용되는 경우이며, 일반적으로 HoloLens와 동일한 경우임).

### <a name="avoid-full-screen-effects"></a>전체 화면 효과 사용 방지

각 프레임의 크기에서 수백만 개의 작업을 요구하므로 전체 화면에서 작동하는 기술에는 비용이 많이 들 수 있습니다. 따라서 앤티 앨리어싱, 블룸 등과 같은 [후 처리 효과](https://docs.unity3d.com/Manual/PostProcessingOverview.html)를 사용하지 않도록 방지하는 것이 좋습니다.

### <a name="optimal-lighting-settings"></a>최적 조명 설정

Unity의 [실시간 글로벌 조명](https://docs.unity3d.com/Manual/GIIntro.html)은 뛰어난 시각적 결과를 제공할 수 있지만 상당히 비싼 조명 계산이 수반됩니다. **창** > **렌더링** > **조명 설정** > **실시간 글로벌 조명** 선택 취소를 통해 모든 Unity 장면 파일에 대해 실시간 글로벌 조명을 사용하지 않도록 설정하는 것이 좋습니다.

또한 이 기술은 Unity 장면에 비용이 많이 드는 GPU 패스를 추가하므로 모든 섀도 캐스팅을 사용하지 않도록 설정하는 것이 좋습니다. 섀도는 조명별로 사용하지 않도록 설정할 수 있지만 품질 설정을 통해 전체적으로 제어할 수도 있습니다.

**편집** > **프로젝트 설정**을 선택한 다음, **품질** 범주를 선택하고, UWP 플랫폼에 대해 **낮은 품질**을 선택합니다. **섀도** 속성을 **섀도 사용 안 함**으로 설정할 수도 있습니다.

Unity의 모델에서 굽기 조명을 사용하는 것이 좋습니다.

### <a name="reduce-poly-count"></a>다각형 수 감소

다각형 수는 일반적으로 다음 방법 중 하나를 사용하여 줄어듭니다.
1) 장면에서 개체 제거
2) 지정된 메시의 다각형 수를 줄이는 자산 부분 제거
3) 동일한 기하 도형의 낮은 다각형 버전을 사용하여 멀리 떨어진 개체를 렌더링하는 애플리케이션에 [LOD(세부 정보 수준) 시스템](https://docs.unity3d.com/Manual/LevelOfDetail.html) 구현

### <a name="understanding-shaders-in-unity"></a>Unity의 셰이더에 대한 이해

성능에서 셰이더를 쉽게 비교할 수 있는 대략적인 방법은 런타임에서 각각 실행되는 평균 작업 수를 식별하는 것입니다. 이 작업은 Unity에서 쉽게 수행할 수 있습니다.

1) 셰이더 자산을 선택하거나 재질을 선택한 다음, 검사기 창의 오른쪽 위 모서리에서 기어 아이콘을 선택한 다음, **"셰이더 선택"** 을 선택합니다.

    ![Unity에서 셰이더 선택](images/Select-shader-unity.png)
2) 셰이더 자산을 선택한 상태에서 검사기 창 아래쪽에서 **"코드 컴파일 및 표시"** 단추를 클릭합니다.

    ![Unity에서 셰이더 코드 컴파일](images/compile-shader-code-unity.PNG)

3) 컴파일되면 꼭짓점 및 픽셀 셰이더 모두에 대한 다양한 작업 수가 포함된 결과에서 통계 섹션을 찾습니다(참고: 픽셀 셰이더는 종종 조각 셰이더라고도 함).

    ![Unity 표준 셰이더 작업](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>픽셀 셰이더 최적화

위의 방법을 사용하여 컴파일된 통계 결과를 살펴보면 일반적으로 [조각 셰이더](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)에서 평균적으로 [꼭짓점 셰이더](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)보다 더 많은 작업을 실행합니다. 픽셀 셰이더라고도 하는 조각 셰이더는 화면 출력에서 픽셀 단위로 실행되지만, 꼭짓점 셰이더는 화면에 그려지는 모든 메시의 꼭짓점 단위로만 실행됩니다. 

따라서 모든 조명 계산으로 인해 조각 셰이더에는 꼭짓점 셰이더보다 더 많은 명령이 포함될 뿐만 아니라, 조각 셰이더가 거의 항상 더 큰 데이터 세트에서 실행됩니다. 예를 들어 화면 출력이 2,000 x 2,000 이미지인 경우 조각 셰이더는 2,000 * 2,000 = 4,000,000회 실행될 수 있습니다. 두 눈을 렌더링하는 경우 두 개의 화면이 있으므로 이 횟수가 두 배가 됩니다. 혼합 현실 애플리케이션에서 여러 패스, 전체 화면 후 처리 효과 또는 동일한 픽셀에 여러 메시 렌더링을 수행하는 경우 이 횟수는 크게 늘어납니다. 

따라서 조각 셰이더의 작업 수를 줄이면 일반적으로 꼭짓점 셰이더의 최적화에 비해 훨씬 더 큰 성능 향상을 달성할 수 있습니다.

#### <a name="unity-standard-shader-alternatives"></a>Unity 표준 셰이더 대안

PBR(물리적 기반 렌더링) 또는 다른 고품질 셰이더를 사용하는 대신, 성능이 더 뛰어나고 저렴한 셰이더를 활용하는 방법을 살펴봅니다. [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)는 혼합 현실 프로젝트에 최적화된 [MRTK 표준 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)를 제공합니다.

또한 Unity는 Unity 표준 셰이더에 비해 훨씬 빠른 unlit(꺼짐), vertex lit(꼭짓점 깜박임), diffuse(확산) 및 간소화된 다른 셰이더 옵션을 제공합니다. 자세한 내용은 [기본 제공 셰이더 사용 및 성능](https://docs.unity3d.com/Manual/shader-Performance.html)을 참조하세요.

#### <a name="shader-preloading"></a>셰이더 미리 로드

*셰이더 미리 로드* 및 기타 트릭을 사용하여 [셰이더 로드 시간](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)을 최적화합니다. 특히 셰이더 미리 로드는 런타임 셰이더 컴파일로 인해 길이 조정이 표시되지 않음을 의미합니다.

### <a name="limit-overdraw"></a>과도한 그리기 제한

Unity에서 **장면 보기**의 왼쪽 위 모서리에서 [**그리기 모드 메뉴**](https://docs.unity3d.com/Manual/ViewModes.html)를 전환하고 **과도한 그리기**를 선택하여 해당 장면에 대한 과도한 그리기를 표시할 수 있습니다.

일반적으로 과도한 그리기는 GPU로 보내기 전에 개체를 미리 선별하여 완화할 수 있습니다. Unity는 [폐색 선별 기능](https://docs.unity3d.com/Manual/OcclusionCulling.html)을 해당 엔진에 구현하는 방법에 대한 자세한 정보를 제공합니다.

## <a name="memory-recommendations"></a>메모리 추천 사항

과도한 메모리 할당 및 할당 취소 작업은 홀로그램 애플리케이션에 부정적인 영향을 줄 수 있으므로 일관성 없는 성능, 고정된 프레임 및 기타 부정적인 동작이 발생할 수 있습니다. 메모리 관리는 가비지 수집기를 통해 제어되므로 Unity에서 개발하는 경우 메모리 고려 사항을 이해하는 것이 특히 중요합니다.

#### <a name="garbage-collection"></a>가비지 컬렉션

실행 중에 더 이상 범위에 있지 않은 개체를 분석하기 위해 GC를 활성화하고 메모리를 해제해야 할 때 홀로그램 앱에서 GC(가비지 수집기)에 대한 처리 컴퓨팅 시간을 상실하여 다시 사용할 수 있도록 설정할 수 있습니다. 지속적인 할당 및 할당 취소는 일반적으로 가비지 수집기를 더 자주 실행해야 하므로 성능과 사용자 환경이 저하됩니다.

Unity는 가비지 수집기의 작동 방식 및 메모리 관리와 관련된 더 효율적인 코드를 작성하기 위한 팁을 자세히 설명하는 매우 유용한 페이지를 제공합니다.
- [Unity 게임에서 가비지 컬렉션 최적화](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

과도한 가비지 컬렉션으로 이어지는 가장 일반적인 사례 중 하나는 Unity 개발에서 구성 요소 및 클래스에 대한 참조를 캐시하지 않는 것입니다. 모든 참조는 Start() 또는 Awake() 중에 캡처되고, Update() 또는 LateUpdate()와 같은 이후 함수에서 다시 사용되어야 합니다.

기타 빠른 팁:
- 런타임에 복잡한 문자열을 동적으로 빌드하려면 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 클래스를 사용합니다.
- 앱의 모든 빌드 버전에서 계속 실행되므로 더 이상 필요하지 않은 Debug.Log()에 대한 호출을 제거합니다.
- 홀로그램 앱에 일반적으로 많은 메모리가 필요한 경우 로드 또는 전환 화면을 표시할 때와 같이 로드 단계 중에 [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)를 호출하는 것이 좋습니다.

#### <a name="object-pooling"></a>개체 풀링

개체 풀링은 개체의 지속적인 할당 및 할당 취소에 드는 비용을 줄이는 데 널리 사용되는 기술입니다. 이 작업을 수행하려면 시간이 지남에 따라 개체를 지속적으로 만들고 삭제하는 대신, 동일한 개체의 대량 풀을 할당하고 이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용합니다. 개체 풀은 앱 중에 수명이 가변적인 다시 사용할 수 있는 구성 요소에 적합합니다.

- [Unity의 개체 풀링 자습서](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>시작 성능

앱을 더 작은 장면으로 시작한 다음, *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 를 사용하여 나머지 장면을 로드하는 것이 좋습니다. 이렇게 하면 앱이 최대한 빨리 대화형 상태로 전환될 수 있습니다. 새 장면이 활성화되는 동안 높은 CPU 스파이크가 발생할 수 있으며 렌더링된 콘텐츠가 끊기거나 길이가 조정될 수 있습니다. 이 문제를 해결하는 한 가지 방법은 로드되는 장면에서 AsyncOperation.allowSceneActivation 속성을 "false"로 설정하고, 장면이 로드될 때까지 기다리고, 화면을 검은색으로 지운 다음, "true"로 다시 설정하여 장면 활성화를 완료하는 것입니다.

시작 장면을 로드하는 동안 사용자에게 홀로그램 시작 화면이 표시됩니다.

## <a name="see-also"></a>참고 항목
- [Unity 게임에서 그래픽 렌더링 최적화](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Unity 게임에서 가비지 컬렉션 최적화](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Physics 모범 사례[Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [스크립트 최적화[Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
