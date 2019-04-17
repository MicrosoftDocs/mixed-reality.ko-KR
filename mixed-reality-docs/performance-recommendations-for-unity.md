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
# <a name="performance-recommendations-for-unity"></a>Unity에 대 한 성능 권장 사항

이 문서에 설명 된 설명을 기반 [혼합된 현실에 대 한 성능 권장 사항](understanding-performance-for-mixed-reality.md) Unity 엔진 환경에 특정 학습에 중점을 둡니다.

개발자의 검토는 좋습니다 이기도 합니다 [Unity 아티클에 대 한 환경 설정을 권장](Recommended-settings-for-unity.md)합니다. 이 문서에 가장 중요 한 장면 구성의 일부를 사용 하 여 콘텐츠와 관련해 서 성능이 혼합 현실 앱 빌드 권장 되는 이러한 설정 중 일부는 아래 강조 표시 된도 합니다.

## <a name="how-to-profile-with-unity"></a>Unity를 사용 하 여 프로 파일링 하는 방법

Unity를 제공 합니다 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 특정 앱에 대 한 중요 한 성능 정보를 수집할 수 있는 훌륭한 리소스는 기본 제공 합니다. 하나는 프로파일러-편집기에서 실행할 수 있지만 이러한 메트릭을 true 런타임 환경을 나타내지 않으면 및 따라서이 결과로 사용할지 신중 하 게 합니다. 좋습니다 원격으로 프로필에 가장 정확 하 고 실행 가능한 정보에 대 한 장치에서 실행 되는 동안 응용 프로그램. 또한 Unity [프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html) 는 매우 강력 하 고 활용에 대 한 정보 도구 이기도 합니다.

Unity에 대 한 유용한 설명서를 제공합니다.
1) 연결 하는 방법의 [Unity 프로파일러 UWP 응용 프로그램에 원격으로](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) 하는 방법을 효과적으로 [Unity Profiler를 사용 하 여 성능 문제 진단](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> 연결 된 Unity Profiler를 사용 하 여 및 GPU 프로파일러를 추가한 후 (참조 *Profiler 추가* 오른쪽 위 모서리에서), 얼마나 많은 시간이 소요 되는지 CPU 및 GPU에서 각각 프로파일러 중간 볼 수 있습니다. 이렇게 하면 개발자가 응용 프로그램 CPU 또는 GPU 경계가 지정 된 경우 빠른 근사값을 가져올 수 있습니다.
>
> ![Unity CPU 및 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 성능 권장 사항

아래의 콘텐츠 특히 Unity를 대상으로 하는 자세한 심층 분석 성능 사례를 다룹니다 & C# 개발 합니다.

#### <a name="cache-references"></a>참조를 캐시

초기화 시 모든 관련 구성 요소 및 Gameobject에 참조를 캐시 하는 것이 좋습니다. 와 같은 함수 호출을 반복 하기 때문에 이것이 *[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 는 비용에 대 한 포인터를 저장 하는 메모리를 기준으로 훨씬 더 비쌉니다. 이에 적용 됩니다 하는 매우, 정기적으로 사용 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)합니다. *Camera.main* 사용 하 여 실제로 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 더 포함 하는 카메라 개체에 대 한 장면 그래프를 검색 하는 아래를 *"MainCamera"*  태그입니다.

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

>[!NOTE] Avoid GetComponent(string) <br/>
> 사용 하는 경우  *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, 몇 가지 다른 오버 로드 합니다. 형식 기반 구현 및 되지 문자열 기반 검색 오버 로드를 사용 하는 것이 반드시 합니다. 장면에 대 한 문자열에서 검색 하는 것은 비용 유형별 검색 보다 훨씬 더 합니다. <br/>
> (좋음) 구성 요소 GetComponent (형식) <br/>
> (Good) T GetComponent\<T>() <br/>
> (불량) 구성 요소 GetComponent(string) > <br/>

#### <a name="avoid-expensive-operations"></a>비용이 많이 드는 작업 방지

1) **사용 하지 않도록 [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    LINQ는 매우 명확 하 고 쉽게 읽기 및 쓰기 수를 사용할 수 있지만 일반적으로 훨씬 더 많은 계산 및 수동으로 알고리즘 작성 보다 특히 더 많은 메모리를 할당 해야 합니다.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **일반적인 Unity Api**

    특정 Unity Api 유용할 수 있습니다 실행 하는 데 비용이 많이 드는. 이들 중 대부분 Gameobject 일부 일치 하는 목록에 대 한 전체 장면 그래프를 검색 하는 작업이 포함 됩니다. 일반적으로 참조를 캐싱 하거나 런타임에 대 한 참조를 추적 하려면 해당 Gameobject에 대 한 관리자 구성 요소를 구현 하 여 이러한 작업을 방지할 수 있습니다.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[Sendmessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)*  하 고 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 중심지 제거 해야 합니다. 이러한 함수는 1000 배 직접적인 함수 호출에 비해 느리게 순서 수 있습니다.

3) **Boxing에 주의 하세요.**

    [Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) 는의 핵심 개념을 C# 언어 및 런타임입니다. 참조 형식의 변수를 char, int, bool 등 값 형식 변수를 래핑하는 프로세스는 것입니다. 값 형식 변수는 "boxed", 관리 되는 힙에 저장 되어 있는 System.Object 내부 래핑됩니다. 따라서 메모리를 할당 및 삭제 하는 경우에 결국 가비지 수집기에서 처리 되어야 합니다. 이러한 할당 및 할당 취소 성능 비용이 발생 하 고 대부분의 시나리오에서 필요 하지 않습니다 또는 대신 비용이 저렴으로 쉽게 바꿀 수 있습니다.

#### <a name="repeating-code-paths"></a>코드 경로 반복합니다.

모든 반복 Unity 콜백 함수 (즉 업데이트) 초당 여러 번 실행 되는 및/또는 프레임을 매우 신중 하 게 작성 해야 합니다. 여기에 비용이 많이 드는 작업 성능에 큰 하 고 일관 된 영향을 해야 합니다.

1) **빈 콜백 함수**

    아래 코드는 모든 Unity 스크립트 자동 초기화가 코드 블록을 사용 하 여 이후 특히 응용 프로그램에서 그대로 보일 수 있지만 비어 있는 이러한 콜백을 실제로 매우 많은 비용이 소요 될 수 있습니다. Unity는 UnityEngine 코드 응용 프로그램 코드와 관리 되지 않는/관리 코드 경계를 통해 앞뒤로 작동합니다. 이 브리지를 전환 하는 컨텍스트를 실행 하는 것이 없을 경우에 상당히 듭니다. 이 앱에 빈 반복 Unity 콜백 되는 구성 요소를 사용 하 여 Gameobject의 있으며 경우에 특히 문제가 됩니다.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update ()이 성능 문제의 가장 일반적인 특성 이지만 다음과 같은 다른 반복 Unity 콜백에 하지 나쁜 경우 불량 동일 하 게 될 수 있습니다. FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc. 

2) **작업을 한 번 실행 하는 중 무엇을 선호할 프레임당**

    다음과 같은 Unity Api는 많은 Holographic 앱에 대 한 일반적인 작업입니다. 항상 가능 하지 않지만 결과 이러한 함수를 한 번 매우 일반적으로 계산할 수 있습니다 하 고 결과 지정된 된 프레임에 대 한 응용 프로그램에서 다시 사용 합니다.

    a) 일반적으로 것이 좋습니다는 전용 Singleton 클래스 또는 장면에 프로그램 게이즈 Raycast를 처리 한 다음 다른 모든 장면 구성 요소를 각각 사용 하 여 반복 되 고 기본적으로 동일한 Raycast 작업 하는 대신에이 결과 다시 사용 하는 서비스 구성 요소입니다. 물론, 일부 응용 프로그램에서는 다른 원본에서 또는 다른 raycasts [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)합니다.

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b)에서 update ()와 같은 반복 Unity 콜백에서 GetComponent() 작업 방지 [캐싱을 참조](#cache-references) start () 또는 Awake()

        UnityEngine.Object.GetComponent()

    c)는 초기화 및 사용 가능한 경우 모든 개체를 인스턴스화하는 것이 좋습니다 [개체 풀링을](#object-pooling) 재활용 및 다시 Gameobject를 사용 하 여 전체 응용 프로그램의 런타임

        UnityEngine.Object.Instantiate()

3) **인터페이스 및 가상 구문을 방지합니다**

    인터페이스 및 직접 개체를 통해 함수 호출을 실행 하거나 가상 함수를 호출 종종 수 직접 구문 또는 직접 함수 호출을 활용 하 여 보다 훨씬 더 비쌉니다. 가상 함수 또는 인터페이스 필요가 없는 경우을 제거 해야 합니다. 그러나 이러한 접근 방식을 위한 성능 저하가 일반적으로 절충 만한 개발 공동 작업, 코드 가독성 및 코드 유지 관리를 단순화 활용 하는 경우. 

4) **값으로 전달 구조체 방지**

    클래스와 달리 구조체는 값 형식 및 해당 내용을 새로 만든된 인스턴스에 복사 되므로 함수에 직접 전달 되 면 합니다. 이 복사본 비용 스택에 추가 메모리와 CPU를 추가 합니다. 작은 구조체에 대 한 효과가 일반적으로 매우 최소화 하 고 있으므로 허용 됩니다. 함수는 반복적으로 프레임 마다 호출에 대 한 뿐만 아니라 큰 구조체를 수행 하는 함수, 함수 정의 참조로 전달 하려면 가능한 경우 수정 합니다. [자세히 알아보기](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>기타

1) **물리학**

    a) 일반적으로 물리학을 개선 하기 위해 쉬운 물리학 또는 초당 반복 횟수에 소요 된 시간의 양을 제한 하는 것입니다. 물론,이 시뮬레이션 정확도를 줄어듭니다. 참조 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) Unity에서

    b) 유형의 colliders Unity에서 광범위 하 게 다른 성능 특징을 갖습니다. 아래와 같은 순서로 왼쪽에서 오른쪽으로 가장 성능이 뛰어난 colliders에 대부분의 고성능 colliders를 나열합니다. 기본 colliders 보다 훨씬 더 비쌉니다는 메시 Colliders를 방지 하려면 가장 중요 한 것입니다.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    참조 [Unity 물리학 모범 사례](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) 자세한 내용을 보려면

2) **애니메이션**

    애니메이터 구성 요소를 사용 하지 않도록 설정 하 여 유휴 애니메이션을 사용 하지 않도록 설정 (게임 개체를 사용 하지 않도록 설정 하지 않습니다 동일한 효과가). 디자인 패턴을 애니메이터 동일한 항목 값을 설정 하는 루프에 위치 하는 위치를 방지 합니다. 응용 프로그램에 영향을 주지이 기술의 경우 상당한 오버 헤드가 있습니다. [여기에서 알아보세요.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **복잡 한 알고리즘**

    응용 프로그램 역 운동학, 경로 찾기 등과 같은 복잡 한 알고리즘을 사용 하는 경우 간단 하거나 성능에 대 한 관련 설정을 조정 확인

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU-GPU 성능 권장 사항

CPU-GPU 성능으로 제공 되는 일반적으로 **그리기 호출** 그래픽 카드에 제출 합니다. 성능 향상을 위해 그리기 호출 해야 전략적 **a) 감소** 또는 **b) 재구성** 최적의 결과 합니다. 자체 그리기 호출의 리소스를 많이 사용 되므로 감소 하는 데 필요한 전체 작업을 축소 됩니다. 또한 비용이 많이 드는 유효성 검사를 요구 하는 그리기 호출 간에 변경 내용 및 그래픽 드라이버의 변환 단계 상태 및 상태 변경 (즉, 제한에 대 한 그리기 호출 응용 프로그램의 구조 즉, 다른 자료 등)에 성능을 높일 수 있습니다.

Unity 개요를 제공 합니다. 해당 플랫폼에 대 한 그리기 호출을 일괄 처리 설명 하는 훌륭한 기사를 있습니다.
- [Unity 그리기 호출 일괄 처리](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>단일 패스 인스턴스화된 렌더링

Unity에서 단일 패스 Instanced 렌더링 하나 인스턴스화된 그리기 호출까지 줄여야 각 눈에 대 한 그리기 호출을 허용 합니다. 두 그리기 호출 간에 캐시 일관성, 인해도 GPU에서 성능 향상도 않습니다.

Unity 프로젝트에서이 기능을 사용 하도록 설정 하려면
1)  오픈 **플레이어 xr 하이 설정을** (이동 **편집** > **프로젝트 설정** > **Player**  >  **Xr 하이 설정을**)
2) 선택 **단일 전달 인스턴스화된** 에서 합니다 **스테레오 렌더링 메서드** 드롭 다운 메뉴 (**지원 되는 가상 현실** 확인란을 선택 해야 합니다)

이 렌더링 방법 세부 정보에 대 한 Unity에서 다음 문서를 읽어봅니다.
- [고급 스테레오 렌더링 AR 및 VR 성능을 최대화 하는 방법](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [단일 패스 인스턴스 만들기](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 개발자가 기존 사용자 지정 셰이더 용으로 작성 되지가 이미 있으면 단일 전달 렌더링 인스턴스화된 다음 한 가지 일반적인 문제가 발생 인스턴스. 개발자는이 기능을 사용 하도록 설정한 후 일부 Gameobject만 렌더링 한 눈에 알 수 있습니다. 사용자 지정 셰이더를 연결된에 대 한 적절 한 속성을 없기 때문에 이것이 인스턴스.
>
> 참조 [단일 전달 스테레오에 대 한 렌더링 HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) 이 문제를 해결 하는 방법에 대 한 Unity에서

#### <a name="static-batching"></a>정적 일괄 처리

Unity는 GPU 그리기 호출을 줄이기 위해 많은 정적 개체를 일괄 처리 수입니다. 대부분 사용할 수 있는 정적 일괄 처리 [렌더러](https://docs.unity3d.com/ScriptReference/Renderer.html) Unity의 개체는 **1)-동일한 자료를 공유 하는 중** 하 고 **2)는 모두로 표시 *정적***  ( Unity에서 개체를 선택 하 고 위에 있는 확인란을 클릭 하 고 관리자의 오른쪽). 로 표시 된 Gameobject *정적* 응용 프로그램의 런타임 전체에서 이동할 수 없습니다. 따라서 정적 일괄 처리 거의 모든 개체 이동, 확장 등 배치할 해야 하는 HoloLens에 활용 하기 어려울 수 있습니다. 몰입 형 헤드셋에 대 한 정적 일괄 처리 수 그리기 호출을 크게 줄일 수 및 성능을 개선 합니다.

읽기 *정적 일괄 처리* 아래에서 [그리기 호출 Unity에서 일괄 처리를](https://docs.unity3d.com/Manual/DrawCallBatching.html) 대 한 자세한 내용은 합니다.

#### <a name="dynamic-batching"></a>동적 일괄 처리

개체를 표시 하는 문제가 있는 이므로 *정적* HoloLens 개발을 위한 동적 일괄 처리 수는이 보완 하는 데 유용한 도구 기능 부족 합니다. 수는 물론, 몰입 형 헤드셋도에 유용 합니다. Unity에서 일괄 처리를 동적 어려울 수 있습니다 하지만 Gameobject 해야 하기 때문에 사용할 수 있도록 **a) 공유 같은 자료가** 하 고 **b) 긴 목록을 다른 조건 충족**.

읽기 *동적 일괄 처리* 아래에서 [그리기 호출 Unity에서 일괄 처리를](https://docs.unity3d.com/Manual/DrawCallBatching.html) 전체 목록입니다. 가장 일반적으로 Gameobject 연결된 메시 데이터 300 개 꼭 짓 점 수 있기 때문에 동적으로 일괄 처리할 수 없게 됩니다.

#### <a name="other-techniques"></a>기타 기술

일괄 처리 여러 Gameobject가 동일한 자료를 공유할 수 있는 경우만 발생할 수 있습니다. 일반적으로 해당 해당 자료에 대 한 고유 질감 할 Gameobject 필요할 경우이 차단 됩니다. 일반적으로 하나의 큰 질감 이라고 하는 방법이 질감 결합 [질감 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)합니다.

또한 것 가능 하 고 적절 한 경우 하나의 GameObject 메시를 결합 하는 것이 일반적으로 좋습니다. Unity에서 각 렌더러를 갖게 하나 렌더러에서 결합 된 메시를 제출 및 그리기 호출에 연결 합니다. 

>[!NOTE]
> 런타임 시 Renderer.material의 속성을 수정 자료의 복사본 만들기를 따라서 손상 될 일괄 처리 합니다. Renderer.sharedMaterial를 사용 하 여 Gameobject 간에 공유 material 속성을 수정 합니다.

## <a name="gpu-performance-recommendations"></a>GPU 성능 권장 사항

자세한 내용은 [Unity에서 그래픽 렌더링 최적화](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

#### <a name="reduce-poly-count"></a>예: poly 수 축소

일반적으로 다각형 수가으로 감소
1) 장면에서 개체 제거
2) 특정된 메시에 대 한 다각형 줄어듭니다 자산 부분 제거
3) 구현 된 [세부 정보 수준 (LOD) 시스템](https://docs.unity3d.com/Manual/LevelOfDetail.html) 멀리 동일한 기 하 도형의 다각형 낮은 버전을 사용 하 여 개체를 렌더링 하는 응용 프로그램에

#### <a name="limit-overdraw"></a>제한 overdraw

Unity에서 표시할 수 있습니다 하나로 전환 하 여 overdraw가 장면에 대 한 합니다 [ **그리기 모드 메뉴** ](https://docs.unity3d.com/Manual/ViewModes.html) 의 왼쪽된 위 모퉁이에 **장면 보기로** 선택 하 고 **Overdraw** .

일반적으로 overdraw GPU에 전송 되기 전에 미리 개체를 선별 하 여 완화할 수 있습니다. 구현 세부 정보를 제공 하는 unity [폐색 고르기](https://docs.unity3d.com/Manual/OcclusionCulling.html) 해당 엔진에 대 한 합니다.

#### <a name="understanding-shaders-in-unity"></a>Unity에서 이해 셰이더

성능에서 셰이더를 비교할 쉽게 근사치가 각 작업의 평균 수를 확인 하기 위해 런타임 시 실행 합니다. 이 Unity의 매우 쉽게 수행할 수 있습니다.

1) 셰이더 자산을 선택 하거나, 재질을 선택한 다음 검사기 창의 오른쪽 위 모서리에서 기어 아이콘을 선택 하 고 다음 **"셰이더 선택"**

    ![Unity에서 셰이더를 선택 합니다.](images/Select-shader-unity.png)
2) 선택한 셰이더 자산을 클릭 합니다 **"컴파일 및 코드를 표시"** 검사기 창 아래의 단추

    ![Unity에서 셰이더 코드 컴파일](images/compile-shader-code-unity.PNG)

3) 컴파일 후 확인 결과에 통계 섹션에 대 한 꼭 짓 점 및 픽셀 셰이더에 대 한 다른 작업의 수를 사용 하 여 (참고: 픽셀 셰이더는 종종 라고도 조각 셰이더)

    ![Unity 표준 셰이더 작업](images/unity-standard-shader-compilation.png)

##### <a name="unity-standard-shader-alternatives"></a>Unity 표준 셰이더 대안

실제로 기반된 렌더링 (PBR) 또는 다른 고품질 셰이더를 사용 하는 대신 확인는 뛰어난 성능을 활용 하 고 저렴 한 셰이더입니다. [혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity) 제공을 [표준 셰이더](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader) 혼합된 현실 프로젝트에 대 한 최적화 되었습니다.

Unity는 표준 Unity 셰이더에 켜지, 활성화 하는 꼭 짓 점, 훨씬 더 빠르게 비교 하는 간소화 된 셰이더 확산, 및 기타 옵션 또한 제공 합니다. 참조 [사용 및 기본 제공 셰이더 성능](https://docs.unity3d.com/Manual/shader-Performance.html) 좀 더 자세한 내용은 합니다.

## <a name="memory-recommendations"></a>메모리 권장 사항

과도 한 메모리 할당 및 할당 취소 작업에는 일관 되지 않은 성능, 고정 된 프레임 및 기타 나쁜 동작의 결과 holographic 응용 프로그램에 부정적인 영향을 있을 수 있습니다. 특히 메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 반드시 합니다.

#### <a name="garbage-collection"></a>가비지 수집

Holographic 앱 GC는 더 이상 범위에서 실행 하는 동안 개체를 분석 하기 활성화 되 고 해당 메모리를 다시 사용할 수 있는 만들 수 있도록 해제 해야 하는 경우 가비지 수집기 (GC) 처리 계산 시간을 잃게 됩니다. 상수 할당 및 할당 취소가 가비지 수집기가 성능 저하의 원인이 되므로 및 사용자 환경을 더 자주 실행 하려면 일반적으로 해야 합니다.

Unity는 가비지 수집기의 작동 방식을 자세히 설명 하는 뛰어난 페이지 및 메모리 관리와 관련해 서에서 더 효율적인 코드를 작성 하기 위한 팁을 제공 합니다.
- [Unity 게임에서 가비지 수집을 최적화](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

과도 한 가비지 수집을 발생 시키는 가장 일반적인 사례 중 하나가 Unity 개발의 클래스 및 구성 요소에 대 한 참조가 캐시 되지 않습니다. 모든 참조 start () 또는 Awake() 중 캡처된 있고 LateUpdate() update () 등 나중의 함수에서 다시 사용 합니다.

기타 빠른 팁:
- 사용 된 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 동적으로 런타임 시 복잡 한 문자열을 작성 하는 클래스
- 더 이상 필요 없는 앱의 모든 빌드 버전에서 계속 실행 될 때 Debug.Log() 호출 제거
- Holographic 앱에는 일반적으로 메모리가 많이 필요한 경우에 호출 해 보십시오 [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) 같은 단계를 로드 하는 동안 로드를 제공 하는 경우 또는 전환 화면

#### <a name="object-pooling"></a>개체 풀링

개체 풀링은 연속 할당의 비용 및 개체의 할당 취소를 위해 널리 사용 되는 기술입니다. 이 동일한 개체의 대형 풀을 할당 하 고 다시 지속적으로 생성 하 고 시간이 지남에 따라 개체를 제거 하는 대신이 풀에서 비활성, 사용 가능한 인스턴스를 사용 하 여 이루어집니다. 개체 풀은 앱 중 변수 수명에 있는 다시 사용 가능한 구성 요소에 적합 합니다.

- [개체 풀링 Unity의 자습서](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>시작 성능

더 작은 장면으로 시작 하는 앱을 사용 하 여 고려해 야 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 장면의 나머지 부분을 로드 합니다. 이렇게 하면 최대한 빨리 대화형 상태를 얻기 위해 응용 프로그램. 인식 하는 있을 수 있습니다.는 CPU 사용량이 엄청나게 급증 동안 새 장면을 활성화 되 고 있으며 렌더링 된 내용을 끊길 수 있습니다. 있는지 또는 다른 점이 있다면 수 있습니다. 이 문제를 해결 하는 하나 방법은 로드 되 고 장면 AsyncOperation.allowSceneActivation 속성을 false로 설정 하려면 장면 로드을 검정으로, 화면의 선택을 취소 한 다음 다시 장면 정품 인증을 완료 하려면 true로 설정 될 때까지 기다리는 것입니다.

기억 시작 화면이 로드 되는 동안 holographic 시작 화면이 사용자에 게 표시 됩니다.

## <a name="see-also"></a>참조
- [Unity 게임 그래픽 렌더링 최적화](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Unity 게임에서 가비지 수집을 최적화](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [물리학 모범 사례 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [스크립트 [Unity] 최적화](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
