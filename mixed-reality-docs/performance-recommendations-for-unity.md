---
title: Unity에 대 한 성능 권장 사항
description: 혼합 현실 앱을 사용 하 여 성능을 향상 시킬 수 있는 Unity 관련 팁입니다.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 그래픽, cpu, gpu, 렌더링, 가비지 수집, hololens
ms.openlocfilehash: 6507667904cfa26dfad1ccf1402cc75f14386609
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003202"
---
# <a name="performance-recommendations-for-unity"></a>Unity에 대 한 성능 권장 사항

이 문서는 [혼합 현실에 대 한 성능 권장 사항](understanding-performance-for-mixed-reality.md) 에 설명 된 토론을 기반으로 하지만 Unity 엔진 환경과 관련 된 학습에 중점을 집중 합니다.

또한 개발자는 [Unity의 권장 환경 설정 문서](Recommended-settings-for-unity.md)를 검토 하는 것이 좋습니다. 이 문서에는 고성능 혼합 현실 앱을 빌드하기 위한 가장 중요 한 장면 구성의 일부 내용이 포함 되어 있습니다. 이러한 권장 설정 중 일부는 아래에도 표시 됩니다.

## <a name="how-to-profile-with-unity"></a>Unity를 사용 하 여 프로 파일링 하는 방법

Unity는 특정 앱에 대 한 중요 한 성능 정보를 수집 하는 데 유용한 리소스인 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 를 기본 제공 합니다. 편집기에서 프로파일러를 실행할 수는 있지만 이러한 메트릭은 진정한 런타임 환경을 나타내지 않으므로이에 대 한 결과는 신중 하 게 사용 해야 합니다. 가장 정확 하 고 실행 가능한 정보를 얻기 위해 장치에서 실행 되는 동안 응용 프로그램을 원격으로 프로 파일링 하는 것이 좋습니다. 또한 Unity의 [프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html) 는 활용할 수 있는 매우 강력 하 고 통찰력 있는 도구 이기도 합니다.

Unity는 다음에 대 한 유용한 설명서를 제공 합니다.
1) [Unity 프로파일러를 UWP 응용 프로그램에 원격](https://docs.unity3d.com/Manual/windowsstore-profiler.html) 으로 연결 하는 방법
2) [Unity Profiler를 사용 하 여 성능 문제](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window) 를 효과적으로 진단 하는 방법

>[!NOTE]
> Unity 프로파일러를 연결 하 고 GPU 프로파일러를 추가한 후 (오른쪽 위 모서리의 *프로파일러 추가* 참조) 프로파일러 중에 CPU & gpu에서 각각 얼마나 많은 시간이 소요 되는지 확인할 수 있습니다. 이를 통해 개발자는 응용 프로그램이 CPU 또는 GPU 바인딩된 경우 빠른 근사값을 얻을 수 있습니다.
>
> ![Unity CPU 및 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 성능 권장 사항

아래 내용은 특히 Unity & C# 개발을 대상으로 하는 자세한 성능 관행을 설명 합니다.

#### <a name="cache-references"></a>캐시 참조

모든 관련 구성 요소에 대 한 참조와 초기화 시 Gameobject를 캐시 하는 것이 가장 좋습니다. 이는 *[Getcomponent\<t > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 와 같은 반복 함수 호출이 포인터를 저장 하는 메모리 비용에 비해 훨씬 더 비쌉니다. 이는 정기적으로 사용 되는 [카메라 주](https://docs.unity3d.com/ScriptReference/Camera-main.html)에도 적용 됩니다. FindGameObjectsWithTag는 실제로 *"maincamera"* 태그가 있는 카메라 개체에 대 한 장면 그래프를 검색 하는 저렴 *[()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 를 사용 *합니다.*

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
> GetComponent (string) 사용 안 합니다. <br/>
> *[Getcomponent ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 를 사용 하는 경우 몇 가지 오버 로드가 있습니다. 항상 형식 기반 구현을 사용 하 고 문자열 기반 검색 오버 로드를 사용 하지 않는 것이 중요 합니다. 장면에서 문자열로 검색 하는 것은 유형별로 검색 하는 것 보다 훨씬 더 비쌉니다. <br/>
> 좋음 구성 요소 GetComponent (Type 유형) <br/>
> 좋음 T GetComponent\<T > () <br/>
> 올바르지 구성 요소 GetComponent (문자열) > <br/>

#### <a name="avoid-expensive-operations"></a>비용이 많이 드는 작업 방지

1) **[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq) 사용 방지**

    LINQ는 매우 깔끔하고 쉽게 읽고 쓸 수 있지만 일반적으로 알고리즘을 수동으로 작성 하는 것 보다 훨씬 더 많은 계산과 특히 더 많은 메모리 할당이 필요 합니다.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **Common Unity Api**

    유용 하지만 특정 Unity Api를 실행 하는 데 비용이 많이 들 수 있습니다. 이러한 항목 중 대부분은 일부 일치 하는 Gameobject 목록에 대 한 전체 장면 그래프 검색을 포함 합니다. 이러한 작업은 일반적으로 참조를 캐시 하거나 런타임에 참조를 추적 하는 Gameobject에 대 한 관리자 구성 요소를 구현 하 여 피할 수 있습니다.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 및 *[BroadcastMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 는 모든 비용으로 제거 되어야 합니다. 이러한 함수는 직접 함수 호출 보다 100% 더 느릴 수 있습니다.

3) **Boxing 유의**

    [Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) 은 C# 언어 및 런타임의 핵심 개념입니다. Char, int, bool 등의 값 형식 변수를 참조 형식 변수로 래핑하는 프로세스입니다. 값으로 형식화 된 변수가 "boxed" 이면 관리 되는 힙에 저장 된 System.object의 내부에 래핑됩니다. 따라서 가비지 수집기에서 메모리를 할당 하 고 결국 삭제를 처리 해야 합니다. 이러한 할당과 할당 해제는 성능 비용을 초래 하 고 많은 시나리오에서 불필요 하거나 더 저렴 한 방법으로 쉽게 바꿀 수 있습니다.

    개발에서 boxing의 가장 일반적인 형태 중 하나는 [nullable 값 형식을](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)사용 하는 것입니다. 일반적으로 함수에서 값 형식에 대해 null을 반환할 수 있기를 원합니다. 특히 작업에서 값을 가져오려고 하면 오류가 발생할 수 있습니다. 이 방법의 잠재적인 문제는 이제 힙에서 할당이 발생 하므로 나중에 가비지를 수집 해야 한다는 것입니다.

    **의 boxing 예C#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **Nullable 값 형식을 통한 문제 boxing의 예**

    이 코드는 Unity 프로젝트에서 만들 수 있는 더미 파티클 클래스를 보여 줍니다. `TryGetSpeed()`를 호출 하면 힙에 대 한 개체 할당이 발생 하며,이는 나중에 가비지 수집 해야 합니다. 이 예제는 특히 현재 속도를 요청 하는 장면에 1000 개 이상의 파티클이 있을 수 있기 때문에 문제가 발생 합니다. 따라서 1000 개의 개체가 할당 되 고 그에 따라 모든 프레임에서 할당을 취소 하 여 성능이 크게 저하 됩니다. 오류를 나타내기 위해-1과 같은 음수 값을 반환 하는 함수를 다시 작성 하면이 문제를 방지 하 고 스택에 메모리를 유지 합니다.

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

반복 Unity 콜백 함수 (즉, 초당 여러 번 실행 되는 업데이트) 및/또는 프레임을 매우 신중 하 게 작성 해야 합니다. 여기에서 비용이 많이 드는 작업은 성능에 크게 영향을 미칠 수 있습니다.

1) **빈 콜백 함수**

    아래 코드는 응용 프로그램에 남겨 두는 것 처럼 보일 수 있지만, 특히 모든 Unity 스크립트는이 코드 블록을 사용 하 여 자동으로 초기화 되기 때문에 이러한 빈 콜백은 실제로 매우 많은 비용이 소요 될 수 있습니다. Unity는 UnityEngine 코드와 응용 프로그램 코드 간에 관리 되지 않는/관리 코드 경계를 앞뒤로 작동 합니다. 이 브리지를 통해 컨텍스트를 전환 하는 것은 실행 하는 작업이 없는 경우에도 매우 비용이 많이 듭니다. 이는 응용 프로그램에 비어 있는 반복 Unity 콜백이 있는 구성 요소가 있는 100 개의 Gameobject 있는 경우 특히 문제가 됩니다.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update ()는이 성능 문제를 가장 일반적으로 노력, 다음과 같은 기타 반복 Unity 콜백이 잘못 된 경우 (예: FixedUpdate (), Behaviour (), OnPostRender ", OnPreRender (), OnRenderImage () 등)와 동일 합니다. 

2) **프레임당 한 번 실행 되도록 하는 작업**

    다음 Unity Api는 많은 Holographic 앱에 대 한 일반적인 작업입니다. 항상 가능한 것은 아니지만 이러한 함수의 결과는 일반적으로 한 번 계산 되 고 결과는 지정 된 프레임에 대 한 응용 프로그램 전체에서 다시 사용 될 수 있습니다.

    a) 일반적으로 반복 되 고 본질적으로 동일한 Raycast 작업을 수행 하는 대신 다른 모든 장면 구성 요소에서이 결과를 다시 사용 하는 전용 Singleton 클래스 또는 서비스를 사용 하는 것이 좋습니다. 구성 요소. 물론 일부 응용 프로그램의 경우 다른 원본 또는 다른 [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)에 대 한 raycasts를 요구할 수 있습니다.

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) Start () 또는 s a s n ()에서 [참조를 캐싱하여](#cache-references) Update ()와 같은 반복 Unity 콜백에서 getcomponent () 작업을 수행 하지 않습니다.

        UnityEngine.Object.GetComponent()

    c) 응용 프로그램의 전체 런타임에 Gameobject를 초기화 하 고 다시 사용 하기 위해 [개체 풀링을](#object-pooling) 사용 하 여 모든 개체를 인스턴스화하는 것이 좋습니다.

        UnityEngine.Object.Instantiate()

3) **인터페이스 및 가상 구문 방지**

    인터페이스를 통해 함수 호출을 호출 하거나 직접 개체를 호출 하거나 가상 함수를 호출 하는 것이 직접 구문 또는 직접 함수 호출을 활용 하는 것 보다 훨씬 더 비쌉니다. 가상 함수 또는 인터페이스가 필요 하지 않은 경우 제거 해야 합니다. 그러나 이러한 접근 방식에 대 한 성능 저하는 일반적으로 개발 공동 작업, 코드 가독성 및 코드 유지 관리를 간소화 하는 것입니다.

    일반적으로이 멤버를 덮어써야 하는 것으로 예상 되는 것이 확실 하지 않으면 필드 및 함수를 가상으로 표시 하지 않는 것이 좋습니다. 프레임 당 여러 번 또는 `UpdateUI()` 메서드와 같이 프레임당 한 번 호출 되는 빈도가 높은 코드 경로에 특히 주의 해야 합니다.

4) **값으로 구조체 전달 방지**

    클래스와 달리 구조체는 값 형식이 며 함수로 직접 전달 될 때 해당 내용이 새로 만든 인스턴스에 복사 됩니다. 이 복사본은 CPU 비용 뿐만 아니라 스택에 추가 메모리를 추가 합니다. 작은 구조체의 경우 효과는 일반적으로 매우 미미 하므로 허용할 수 있습니다. 그러나 모든 프레임을 반복 해 서 호출 하는 함수 뿐만 아니라 대량 구조체를 가져오는 함수도 가능 하면 함수 정의를 참조로 전달 하도록 수정 합니다. [여기를 참조하세요](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method).

#### <a name="miscellaneous"></a>기타

1) **물리**

    a) 일반적으로 물리를 개선 하는 가장 쉬운 방법은 물리학에 소요 되는 시간 또는 초당 반복 횟수를 제한 하는 것입니다. 물론이로 인해 시뮬레이션 정확도가 줄어듭니다. Unity에서 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) 를 참조 하세요.

    b) Unity의 colliders 형식에는 다양 한 성능 특징이 있습니다. 아래 주문에서는 가장 성능이 가장 뛰어난 colliders을 왼쪽에서 오른쪽으로 가장 낮은 colliders 나열 합니다. 기본 Colliders 보다 비용이 많이 드는 메시 Colliders을 방지 하는 것이 가장 중요 합니다.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    자세한 내용은 [Unity 물리학 모범 사례](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) 를 참조 하세요.

2) **애니메이션**

    애니메이터 구성 요소를 사용 하지 않도록 설정 하 여 유휴 상태의 애니메이션을 사용 하지 않도록 설정 (게임 개체를 사용 하지 않도록 설정 해도 동일한 효과가 없음 값을 동일한 값으로 설정 하는 반복에서 애니메이터를 사용 하는 디자인 패턴을 피합니다. 응용 프로그램에 영향을 주지 않고이 기술에 대 한 상당한 오버 헤드가 발생 합니다. [자세한 내용은 여기를 참조 하세요.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **복잡 한 알고리즘**

    응용 프로그램에서 역 기구학, 경로 찾기 등의 복잡 한 알고리즘을 사용 하는 경우 더 간단한 접근 방식을 찾거나 성능에 대 한 관련 설정을 조정 합니다.

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU 대 GPU 성능 권장 사항

일반적으로 CPU 대 GPU 성능은 그래픽 카드에 제출 된 **그리기 호출** 에 도달 합니다. 성능을 향상 시키려면 최적의 결과를 위해 그리기 호출을 전략적 **a로 축소** 하거나 **b) 재구성** 해야 합니다. 그리기 호출 자체는 리소스를 많이 사용 하므로 이러한 호출을 줄이면 필요한 전체 작업을 줄일 수 있습니다. 그리고 그리기 호출 사이에 상태를 변경 하려면 그래픽 드라이버에서 비용이 많이 드는 유효성 검사 및 변환 단계가 필요 하므로 상태 변경을 제한 하기 위해 응용 프로그램의 그리기 호출을 재구성 해야 합니다. 즉, 다른 자료 등)를 통해 성능을 향상 시킬 수 있습니다.

Unity에는 플랫폼에 대 한 일괄 처리 그리기 호출에 대 한 개요 및 다이브을 제공 하는 유용한 문서가 있습니다.
- [Unity 호출 일괄 처리 그리기](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>단일 패스 인스턴스화된 렌더링

Unity에서 단일 패스 인스턴스화된 렌더링을 사용 하면 각 눈동자에 대 한 그리기 호출을 하나의 인스턴스화된 그리기 호출로 줄일 수 있습니다. 두 그리기 호출 사이의 캐시 일관성으로 인해 GPU 에서도 약간의 성능도 향상 되었습니다.

Unity 프로젝트에서이 기능을 사용 하도록 설정 하려면
1)  **플레이어 XR 설정** 열기 ( **편집** > **프로젝트 설정** > **플레이어** > **XR 설정**으로 이동)
2) **스테레오 렌더링 방법** 드롭다운 메뉴에서 **단일 패스 인스턴스** 를 선택 합니다 (**가상 현실 지원 됨** 확인란을 선택 해야 함).

이 렌더링 방법에 대 한 자세한 내용은 Unity에서 다음 문서를 참조 하세요.
- [고급 스테레오 렌더링을 사용 하 여 AR 및 VR 성능을 최대화 하는 방법](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [단일 패스 인스턴스](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 단일 패스 인스턴스화된 렌더링의 일반적인 문제 중 하나는 개발자에 게 인스턴스에 대해 작성 되지 않은 기존 사용자 지정 셰이더가 이미 있는 경우 발생 합니다. 이 기능을 사용 하도록 설정한 후 개발자는 일부 Gameobject 한 눈에만 렌더링 되는 것을 알 수 있습니다. 이는 연결 된 사용자 지정 셰이더가 인스턴스에 적합 한 속성을 포함 하지 않기 때문입니다.
>
> 이 문제를 해결 하는 방법에 대해서는 Unity의 [HoloLens에 대 한 단일 패스 스테레오 렌더링](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) 을 참조 하세요.

#### <a name="static-batching"></a>정적 일괄 처리

Unity는 많은 정적 개체를 일괄 처리 하 여 GPU에 대 한 그리기 호출을 줄일 수 있습니다. 정적 일괄 처리는 **1) 동일한 자료를 공유** 하 고 **2) 모두 *정적* 으로 표시** 되는 unity의 대부분 [렌더러](https://docs.unity3d.com/ScriptReference/Renderer.html) 개체에 대해 작동 합니다. unity에서 개체를 선택 하 고 검사기의 오른쪽 위에 있는 확인란을 클릭 합니다. *Static* 으로 표시 된 gameobject는 응용 프로그램의 런타임 전체에서 이동할 수 없습니다. 따라서 정적 일괄 처리는 거의 모든 개체를 배치 하 고 이동 하거나 크기를 조정 해야 하는 HoloLens에서 활용 하기 어려울 수 있습니다. 모던 헤드셋의 경우 정적 일괄 처리는 그리기 호출을 크게 줄일 수 있으므로 성능을 향상 시킬 수 있습니다.

자세한 내용은 [Unity에서 그리기 호출 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html) 에서 *정적 일괄 처리* 를 참조 하세요.

#### <a name="dynamic-batching"></a>동적 일괄 처리

개체를 HoloLens 개발에 대 한 *정적* 으로 표시 하는 데 문제가 있기 때문에 동적 일괄 처리는 이러한 부족 한 기능을 보정 하는 데 유용한 도구 일 수 있습니다. 물론 모던 헤드셋 에서도 유용할 수 있습니다. 그러나 Unity의 동적 일괄 처리 **는 gameobject가 동일한 자료를 공유** 하 고 **b) 다른 기준의 긴 목록을 충족**하기 때문에 사용 하기 어려울 수 있습니다.

전체 목록에 대 한 [Unity의 그리기 호출 일괄](https://docs.unity3d.com/Manual/DrawCallBatching.html) 처리에서 *동적 일괄 처리* 를 읽습니다. 가장 일반적으로 Gameobject는 연결 된 메시 데이터가 300 개의 꼭지점이 될 수 있으므로 동적으로 일괄 처리할 수 없게 됩니다.

#### <a name="other-techniques"></a>기타 기술

일괄 처리는 여러 Gameobject가 동일한 자료를 공유할 수 있는 경우에만 발생할 수 있습니다. 일반적으로 Gameobject가 해당 재질에 고유한 질감을 가질 필요에 의해 차단 됩니다. [질감 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)하는 메서드를 하나의 큰 질감으로 결합 하는 것이 일반적입니다.

또한 일반적으로 메시를 가능한 한 GameObject 결합 하는 것이 좋습니다. Unity의 각 렌더러는 연결 된 그리기 호출을 포함 하 고 하나의 렌더러에서 결합 된 메시를 제출 합니다.

>[!NOTE]
> 렌더러의 속성을 수정 하는 중입니다. 런타임에 재질은 재질의 복사본을 만들고 일괄 처리를 중단 시킬 수 있습니다. Gameobject에서 공유 재질 속성을 수정 하려면 렌더러를 사용 합니다.

## <a name="gpu-performance-recommendations"></a>GPU 성능 권장 사항

[Unity에서 그래픽 렌더링 최적화](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games) 에 대 한 자세한 정보

### <a name="optimize-depth-buffer-sharing"></a>깊이 버퍼 공유 최적화

일반적으로 **플레이어 XR 설정** 에서 **깊이 버퍼 공유** 를 사용 하도록 설정 하 여 [홀로그램 안정성](Hologram-stability.md)을 최적화 하는 것이 좋습니다. 그러나이 설정을 사용 하 여 깊이 기반 지연 단계를 사용 하도록 설정 하는 경우 **24 비트 깊이 형식**대신 **16 비트 깊이 형식을** 선택 하는 것이 좋습니다. 16 비트 깊이 버퍼는 깊이 버퍼 트래픽과 관련 된 대역폭 (그리고 그에 따라 전원)을 크게 감소 시킵니다. 이는 전력 감소 및 성능 향상에 모두 큰 승리를 가질 수 있습니다. 그러나 *16 비트 깊이 형식을*사용 하는 경우 두 가지 가능한 음수 결과가 있습니다.

**Z-싸 우**

축소 된 깊이 범위 충실도는 24 비트 보다 16 비트를 사용 하 여 [z](https://en.wikipedia.org/wiki/Z-fighting) 를 더 많이 교환할 수 있도록 합니다. 이러한 아티팩트를 방지 하려면 [Unity 카메라](https://docs.unity3d.com/Manual/class-Camera.html) 의 near/far 클립 평면을 수정 하 여 더 낮은 정밀도를 고려 합니다. HoloLens 기반 응용 프로그램의 경우 Unity 기본 1000m 대신 5천만 개의 먼 클립 평면은 일반적으로 z-싸 우를 제거할 수 있습니다.

**사용 하지 않도록 설정 된 스텐실 버퍼**

Unity에서 [16 비트 깊이의 렌더링 질감](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)을 만드는 경우 스텐실 버퍼가 생성 되지 않습니다. Unity 설명서 당 24 비트 깊이 형식을 선택 하면 24 비트 z 버퍼와 [8 비트 스텐실 버퍼] (https://docs.unity3d.com/Manual/SL-Stencil.html) (일반적으로 HoloLens와 같은 경우 장치에 32 비트가 적용 되는 경우)가 생성 됩니다.

### <a name="avoid-full-screen-effects"></a>전체 화면 효과 방지

전체 화면에서 작동 하는 기술은 모든 프레임의 크기가 수백만 작업 이므로 상당한 비용이 들 수 있습니다. 따라서 앤티앨리어스, 블 룸 등의 [사후 처리 효과](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 를 방지 하는 것이 좋습니다.

### <a name="optimal-lighting-settings"></a>최적의 조명 설정

Unity의 [실시간 글로벌](https://docs.unity3d.com/Manual/GIIntro.html) 조명은 뛰어난 시각적 결과를 제공할 수 있지만 상당한 비용이 드는 조명 계산을 포함 합니다. **창을** 통해 모든 Unity 장면 파일에 대해 실시간 글로벌 조명을 사용 하지 않도록 설정 하는 것이 좋습니다. > **렌더링** > **조명 설정을** 사용 하 여 **실시간 글로벌 조명을**선택 취소 >.

또한 모든 섀도 캐스팅을 사용 하지 않도록 설정 하는 것이 좋습니다 .이 경우에도 Unity 장면에 비용이 많이 드는 GPU 패스가 추가 됩니다. 그림자는 빛 당 사용 하지 않도록 설정할 수 있지만 품질 설정을 통해 전체적으로 제어할 수도 있습니다.

 > **프로젝트 설정을** **편집한** 다음 **품질** 범주를 선택 하 > UWP 플랫폼 **에 대해 저품질를 선택** 합니다. 그림자를 **사용 하지 않도록**설정 하려면 **shadows** 속성을 설정 하면 됩니다.

### <a name="reduce-poly-count"></a>Poly 수 줄이기

다각형 수는 일반적으로 다음 중 하나로 줄어듭니다.
1) 장면에서 개체 제거
2) 지정 된 메시의 다각형 수를 줄이는 Asset decimation
3) 응용 프로그램에 대 한 [세부 정보 (LOD) 시스템](https://docs.unity3d.com/Manual/LevelOfDetail.html) 을 구현 하 여 동일한 기 하 도형에 대 한 다각형 버전이 더 낮은 개체를 렌더링 합니다.

### <a name="understanding-shaders-in-unity"></a>Unity의 셰이더 이해

성능과 셰이더를 비교 하는 것은 각 런타임에 실행 되는 평균 작업 수를 식별 하는 것입니다. Unity에서이 작업을 쉽게 수행할 수 있습니다.

1) 셰이더 자산을 선택 하거나 재질을 선택 하 고, 검사기 창의 오른쪽 위 모퉁이에서 기어 아이콘, **"셰이더 선택"** 을 차례로 선택 합니다.

    ![Unity에서 셰이더 선택](images/Select-shader-unity.png)
2) 셰이더 자산을 선택 하 고 검사기 창에서 **"코드 컴파일 및 표시"** 단추를 클릭 합니다.

    ![Unity에서 셰이더 코드 컴파일](images/compile-shader-code-unity.PNG)

3) 컴파일한 후에는 꼭 짓 점 및 픽셀 셰이더 모두에 대해 다양 한 작업 수를 사용 하 여 결과에서 통계 섹션을 찾습니다 (참고: 픽셀 셰이더를 조각 셰이더 라고도 함).

    ![Unity 표준 셰이더 작업](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>픽셀 셰이더 최적화

위의 메서드를 사용 하 여 컴파일된 통계 결과를 살펴보면 [조각 셰이더가](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) 평균에서 [꼭 짓 점 셰이더](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)보다 더 많은 작업을 실행 합니다. 꼭 짓 점 셰이더 라고도 하는 조각 셰이더는 화면 출력에서 픽셀 단위로 실행 되는 반면 꼭 짓 점 셰이더는 화면에 그려지는 모든 망상의 꼭 짓 점 마다 실행 됩니다. 

따라서 조각 셰이더는 모든 조명 계산으로 인해 꼭 짓 점 셰이더 보다 더 많은 명령을 포함할 뿐만 아니라 조각 셰이더는 거의 항상 큰 데이터 집합에서 실행 됩니다. 예를 들어 화면 출력이 2k 이미지 인 경우 조각 셰이더는 2000 * 2000 = 400만 번 실행 될 수 있습니다. 두 개의 눈동자를 렌더링 하는 경우 두 개의 화면이 있으므로이 수는 두 배가 됩니다. 혼합 현실 응용 프로그램에 여러 번의 통과, 전체 화면 처리 효과가 있는 경우 또는 여러 메시를 동일한 픽셀로 렌더링 하는 경우이 숫자가 크게 증가 합니다. 

따라서 조각 셰이더의 작업 수를 줄이면 일반적으로 꼭 짓 점 셰이더의 최적화에 비해 훨씬 더 큰 성능 향상을 제공할 수 있습니다.

#### <a name="unity-standard-shader-alternatives"></a>Unity 표준 셰이더 대안

실제 기반 렌더링 (.PBR) 또는 다른 고품질 셰이더를 사용 하는 대신 보다 성능이 뛰어나고 저렴 한 셰이더를 활용 하는 방법을 살펴보세요. [Mixed Reality 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity) 는 혼합 현실 프로젝트에 최적화 된 [mrtk 표준 셰이더](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) 를 제공 합니다.

Unity는 Unity 표준 셰이더에 비해 훨씬 빠르게 unlit, 꼭 짓 점, 확산 및 기타 단순화 된 셰이더 옵션을 제공 합니다. 자세한 내용은 [기본 제공 셰이더의 사용 및 성능](https://docs.unity3d.com/Manual/shader-Performance.html) 을 참조 하세요.

#### <a name="shader-preloading"></a>셰이더 미리 로드

셰이더 *미리* 로드 및 기타 트릭을 사용 하 여 [셰이더 로드 시간](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)을 최적화 합니다. 특히 셰이더 미리 로드는 런타임 셰이더 컴파일 때문에 어떤 hitches 표시 되지 않음을 의미 합니다.

### <a name="limit-overdraw"></a>과도 한 그리기 제한

Unity에서 **장면 보기** 의 왼쪽 위 모퉁이에 있는 [**그리기 모드 메뉴**](https://docs.unity3d.com/Manual/ViewModes.html) 를 전환 하 고 **과도 한 그리기**를 선택 하 여 장면에 대해 과도 한 그리기를 표시할 수 있습니다.

일반적으로 과도 한 그리기는 GPU에 전송 되기 전에 미리 개체를 고르기 하 여 완화할 수 있습니다. Unity는 [폐색 고르기](https://docs.unity3d.com/Manual/OcclusionCulling.html) for engine 구현에 대 한 세부 정보를 제공 합니다.

## <a name="memory-recommendations"></a>메모리 권장 사항

과도 한 메모리 할당 & 할당 취소 작업은 holographic 응용 프로그램에 부정적인 영향을 줄 수 있으므로 일관성 없는 성능, 고정 된 프레임 및 기타 부정적 동작이 발생할 수 있습니다. 메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 특히 중요 합니다.

#### <a name="garbage-collection"></a>가비지 컬렉션

Holographic apps는 GC가 활성화 되어 실행 중에 더 이상 범위에 있지 않은 개체를 분석 하 고 해당 메모리를 해제 해야 하므로 다시 사용할 수 있도록 설정할 수 있습니다. 상수 할당 및 할당 취소를 사용 하려면 일반적으로 가비지 수집기가 더 자주 실행 되므로 성능 및 사용자 환경이 저하 됩니다.

Unity는 메모리 관리와 관련 하 여 보다 효율적인 코드를 작성 하기 위한 팁과 가비지 수집기의 작동 방식에 대해 자세히 설명 하는 뛰어난 페이지를 제공 합니다.
- [Unity 게임에서 가비지 수집 최적화](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

과도 한 가비지 수집을 수행 하는 가장 일반적인 방법 중 하나는 Unity 개발의 구성 요소 및 클래스에 대 한 참조를 캐싱하지 않는 것입니다. 모든 참조는 Start () 또는 해제 () 중에 캡처되고 업데이트 () 또는 Behaviour ()와 같은 이후 함수에서 다시 사용 되어야 합니다.

기타 빠른 팁:
- [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 클래스를 사용 하 여 런타임에 복잡 한 문자열을 동적으로 빌드합니다.
- 응용 프로그램의 모든 빌드 버전에서 계속 실행 되므로 더 이상 필요 하지 않은 경우 Debug ()에 대 한 호출을 제거 합니다.
- Holographic 앱이 일반적으로 많은 메모리를 요구 하는 경우 로드 또는 전환 화면을 발표할 때와 같은 단계를 로드 하는 동안 system.string [ _**()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) 을 호출 하는 것이 좋습니다.

#### <a name="object-pooling"></a>개체 풀링

개체 풀링은 연속 & 할당의 비용을 줄이고 개체 할당을 취소 하는 인기 있는 기술입니다. 이 작업을 수행 하려면 시간이 지남에 따라 개체를 지속적으로 생성 및 제거 하는 대신 동일한 개체의 대량 풀을 할당 하 고이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용 합니다. 개체 풀은 앱을 실행 하는 동안 변수 수명이 있는 다시 사용할 수 있는 구성 요소에 적합 합니다.

- [Unity의 개체 풀링 자습서](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>시작 성능

더 작은 장면으로 앱을 시작한 다음 *[SceneManager. LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 를 사용 하 여 나머지 장면을 로드 하는 것이 좋습니다. 이렇게 하면 앱이 최대한 빠르게 대화형 상태가 될 수 있습니다. 새 장면을 활성화 하 고 렌더링 된 모든 콘텐츠를 끊길 하거나 hitch 수 있는 동안에는 상당한 CPU 스파이크가 있을 수 있습니다. 이 문제를 해결 하는 한 가지 방법은 로드 되는 장면에서 allowSceneActivation 속성을 "false"로 설정 하 고, 장면이 로드 될 때까지 기다린 후 화면을 검은색으로 AsyncOperation, "true"로 다시 설정 하 여 장면 활성화를 완료 하는 것입니다.

시작 장면을 로드 하는 동안 사용자에 게 holographic 시작 화면이 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [Unity 게임에서 그래픽 렌더링 최적화](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Unity 게임에서 가비지 수집 최적화](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [물리학 모범 사례 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [스크립트 최적화 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
