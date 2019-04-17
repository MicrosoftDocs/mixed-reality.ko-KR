---
title: 혼합된 현실에 대 한 성능 이해
description: Windows 혼합 현실 앱에 대 한 성능 최적화에 고급 항목 및 세부 정보
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: 혼합 현실, 혼합된 현실, 가상 현실, VR, MR, 성능, 최적화, CPU, GPU Windows
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603289"
---
# <a name="understanding-performance-for-mixed-reality"></a>혼합된 현실에 대 한 성능 이해

이 문서는 혼합 현실 앱에 대 한 성능의 중요성을 합리화를 소개 합니다.  응용 프로그램이 최적의 프레임 속도로 실행 되지 않는 경우 사용자 환경은 크게 저하 될 수 있습니다. 홀로그램 불안정 나타나고 환경의 헤드 추적 앞에 잘못 된 환경에서 사용자를 정확 하 게 됩니다. 실제로 성능 혼합 현실 개발 및 없습니다 안정화를 주기 작업의 끝에 대 한 첫 번째 클래스 기능으로 간주 해야 합니다.

검토를 위해 각 대상 플랫폼에 대 한 고성능 프레임 속도 값은 다음과 같습니다.

| 플랫폼 | 대상 프레임 속도 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra Pc](immersive-headset-hardware-details.md) | 90 FPS |
| [혼합 현실 Pc Windows](immersive-headset-hardware-details.md) | 60 FPS |

모범 사례에 대 한 일반적인 개요를 제공 하는 다음 프레임 워크 및 프레임 속도 대상에 도달 하는 쪽으로 이해 합니다. 파일 추가 세부 정보를 읽는 것이 좋습니다 합니다 [Unity 문서에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)합니다. 특히 관련 된이 문서에서는 성능 향상을 위해 Unity 환경에서 수행 하는 단계 뿐만 Unity Windows Mixed Reality 앱에서 프레임 속도 측정 하는 방법을 설명 합니다.

## <a name="understanding-performance-bottlenecks"></a>성능 병목 현상을 이해

앱이를 줄이는데 framerate를 하는 경우 분석 하 고 응용 프로그램 기법은 아닙니다 이해는 첫 번째 단계가입니다. 장면 렌더링 하는 작업을 담당 기본 프로세서 두 가지: CPU와 GPU 합니다. 각 이러한 두 구성 요소에는 다양 한 작업 및 혼합 현실 앱 단계의 처리 합니다. 세 가지 주요 위치는 병목 현상이 발생할 수 있는 합니다. 

1. **앱 스레드가-CPU** -이 스레드는 사용자 앱 논리를 담당 합니다. 여기에 입력, 애니메이션, 물리, 및 다른 응용 프로그램 논리 상태 처리
2. **렌더링 스레드-CPU gpu** -이 스레드는 GPU에 그리기 호출을 제출 하는 일을 담당 합니다. 앱에서 큐브 또는 모델과 같은 개체를 렌더링 하려는 경우이 스레드가 GPU 렌더링에 대 한 액세스에 최적화 된 아키텍처에는 이러한 작업을 수행 하는 요청을 보냅니다.
3. **GPU** - 
    이 프로세서는 가장 일반적으로 픽셀 (모델, 질감, 등) 3D 데이터 변환 및 궁극적으로 장치의 화면에 전송할 2D 이미지를 생성 하도록 응용 프로그램의 그래픽 파이프라인을 처리 합니다.

![프레임의 수명](images/lifetime-of-a-frame.png)

일반적으로 HoloLens 응용 프로그램에 GPU 제한 됩니다. 그러나 모든 응용 프로그램에서 true 유지 하지 않으면이 있으며 따라서 도구 및 기술을 아래 ground-특정 앱에 대 한 진실 하는 데 좋습니다.

## <a name="how-to-analyze-your-application"></a>응용 프로그램을 분석 하는 방법

혼합 현실 응용 프로그램의 성능 프로필을 이해 하는 개발자로 서 사용할 수 있는 많은 도구가 있습니다. 이 수 해야 하는 병목 현상 및 어떻게 이러한 자체 디버그할 수를 나타내는 모두 대상으로 합니다.

응용 프로그램에 대 한 심층 프로 파일링 정보는 데 널리 사용 되 고 강력한 도구 목록입니다.
- [Intel 그래픽 성능 분석기](https://software.intel.com/gpa)
- [Visual Studio 그래픽 디버거](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>모든 환경에서 프로 파일링 하는 방법

간단한 테스트를 신속 하 게 GPU 제한 가능성이 있는지를 확인 또는 CPU 바인딩된 응용 프로그램에 있습니다. 렌더링 대상 출력의 해상도 낮추면 적은 픽셀을 계산 하는 하며 따라서 더 적은 작업 GPU의 이미지를 렌더링 하기 위해 수행 합니다. (동적 확인 배율) 크기 조정 뷰포트는 작은 이미지를 렌더링 하는 방법 렌더링 대상 출력 장치의 표시 수 있습니다. 장치는 최대-샘플 최종 이미지를 표시 하는 픽셀의 더 작은 집합입니다.

경우 렌더링 해상도 낮추면 후:
1) 응용 프로그램 framerate **증가**, 될 가능성이 다음 **GPU 제한**
1) 응용 프로그램 framerate **변경 되지 않은**, 될 가능성이 다음 **CPU 제한**

>[!NOTE]
>Unity를 통해 런타임에 응용 프로그램의 렌더링 대상 해상도 쉽게 수정할 수는 기능을 제공 합니다 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성입니다. 장치에 표시 된 최종 이미지에 고정된 확인 합니다. 플랫폼 출력 표시에 렌더링 하기 위한 더 높은 해상도 이미지를 빌드하는 더 낮은 해상도 샘플링 됩니다. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>응용 프로그램을 개선 하는 방법

### <a name="cpu-performance-recommendations"></a>CPU 성능 권장 사항

일반적으로 CPU에서 혼합된 현실 응용 프로그램에서 대부분의 작업에는 장면 "시뮬레이션"를 수행 하 고 광범위 한 고유한 응용 프로그램 논리를 처리할 포함 됩니다. 따라서 다음과 같은 영역 일반적으로 최적화에 대 한 대상입니다.

- 애니메이션
- 물리학 간소화
- 메모리 할당
- 복잡 한 알고리즘 (즉 역 운동학, 경로 찾기)

### <a name="gpu-performance-recommendations"></a>GPU 성능 권장 사항

#### <a name="understanding-bandwidth-vs-fill-rate"></a>이해 대역폭 vs 채우기 속도
GPU에서 프레임을 렌더링 하는 경우 응용 프로그램은 일반적으로 메모리 대역폭 또는 채우기 비율에 따라 제한 중 하나입니다.

- **메모리 대역폭** 읽기 속도 및 GPU 메모리에서 수행할 수 있는 쓰기
    - 대역폭 제한을 식별 하려면 질감 줄이고 framerate 개선 하는 경우를 확인 합니다.
    - Unity에서이 가능 바꿔서 **질감** 에 **편집** > **프로젝트 설정**  >   **[ 품질 설정을](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 합니다.
- **채우기 비율** GPU에서 초당 그릴 수 있는 렌더링 된 픽셀의 처리량을 가리킵니다.
    - 채우기 속도 제한을 식별 하려면 디스플레이 해상도 감소 하 고 framerate 개선 하는 경우를 확인 합니다. 
    - Unity를 통해 수행할 수 있습니다 합니다 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성

메모리 대역폭을 최적화를 일반적으로
1) 질감 해상도 감소
2) (즉, 적은 질감을 활용 정규 분포 반사, 등)

채우기 속도 주로 최종 렌더링 된 픽셀에 대 한 계산 해야 하는 작업 수가 줄어듭니다. 이 예제에서는 일반적으로 줄이는 나뉩니다.
1) 렌더링/프로세스에는 개체 수
2) 셰이더 초당 작업 수
3) 최종 결과 (기 하 도형 셰이더를 사후 처리 효과, 등)에 GPU 단계 수
4) (즉, 렌더링 하는 픽셀 수 디스플레이 해상도)

#### <a name="reduce-poly-count"></a>예: poly 수 축소
다각형 높은 GPU에 대 한 자세한 작업의 결과 계산 하 고 해당 기 하 도형에 렌더링 하는 시간의 양을 장면에서 다각형의 수를 줄이면 줄어듭니다. 비용이 많이 드는 계속 될 수 있는 기 하 도형 음영으로 관련 된 기타 요인도 있습니다 이지만 다각형 수 결정 드는 장면을 렌더링 하는 기본 메트릭을 있습니다.

#### <a name="limit-overdraw"></a>제한 overdraw

높은 overdraw 여러 개체 렌더링 되지만 다른, 일반적으로 좀 더 자세히 occluding 개체로 숨김으로 화면에 출력 하지 때 발생 합니다. 여러 방 및 숨김 기 하 도형 있던 벽을 살펴보면 한다고 가정 합니다. 렌더링에 대 한 처리 된 기 하 도형의 모든 있지만 불투명 벽만 실제로 다른 모든 콘텐츠 보기 occludes 것으로 렌더링 해야 합니다. 이 인해 현재 뷰에 대 한 필요 하지 않은 불필요 한 작업입니다.

#### <a name="shaders"></a>셰이더

셰이더는 GPU에서 실행 되며 일반적으로 렌더링에 두 가지 중요 한 단계를 확인 하는 작은 프로그램:
1) 개체의 꼭 짓 점 있는 화면 공간 (즉, 화면에 그릴 꼭 짓 점 셰이더)
    - 모든 GameObject에 대 한 꼭 짓 점 꼭 짓 점 셰이더는 일반적으로 실행
2) (즉, 이러한 픽셀 색에 픽셀 셰이더)
    - 픽셀 셰이더 있는 장치에 대 한 렌더링 되는 질감에 대 한 픽셀 당 실행

일반적으로 셰이더는 대부분의 변환 및 조명 계산을 수행합니다. 복잡 한 조명 모델, 그림자, 및 기타 작업 훌륭한 결과 생성 하지만 가격이 함께 제공 됩니다. 셰이더 계산 되는 작업의 수를 줄이면 프레임당 GPU에서 완료 해야 하는 데 필요한 전체 작업을 크게 줄일 수 있습니다.

##### <a name="shader-coding-recommendations"></a>권장 사항 코딩 셰이더

- 쌍선형 필터링 사용
- 동시는 multiply 및 추가 작업을 수행 하려면 MAD 내장 함수를 사용 하는 식을 다시 정렬
- CPU에서 최대한 미리 계산 하 고 자료를 상수로 전달
- **꼭 짓 점 셰이더가 픽셀 셰이더에에서 이동 작업을 선호**
    - 일반적으로 꼭 짓 점 # << # 픽셀 (즉, 720p == 921,600 pixels, 1080p == 2,073,600 pixels, etc)

#### <a name="remove-gpu-stages"></a>GPU 단계를 제거 합니다.
효과 사후 처리 비용이 매우 많이 들 수 하 고 일반적으로 응용 프로그램의 채우기 비율을 차단할 수 있습니다. MSAA와 같은 앤티 앨리어싱을 기술도 포함 됩니다. HoloLens에서 이러한 기법을 완전히 방지 하는 것이 좋습니다. 또한 가능한 경우 기 하 도형, 헐, 계산 셰이더 등 추가 셰이더 단계를 피해 야 합니다.

## <a name="memory-recommendations"></a>메모리 권장 사항
과도 한 메모리 할당 및 할당 취소 작업에는 일관 되지 않은 성능, 고정 된 프레임 및 기타 나쁜 동작의 결과 holographic 응용 프로그램에 부정적인 영향을 있을 수 있습니다. 특히 메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 반드시 합니다.

#### <a name="object-pooling"></a>개체 풀링

개체 풀링은 연속 할당의 비용 및 개체의 할당 취소를 위해 널리 사용 되는 기술입니다. 이 동일한 개체의 대형 풀을 할당 하 고 다시 지속적으로 생성 하 고 시간이 지남에 따라 개체를 제거 하는 대신이 풀에서 비활성, 사용 가능한 인스턴스를 사용 하 여 이루어집니다. 개체 풀은 앱 중 변수 수명에 있는 다시 사용 가능한 구성 요소에 적합 합니다.

## <a name="see-also"></a>참조
- [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)
- [Unity에 대 한 권장된 설정](recommended-settings-for-unity.md)
