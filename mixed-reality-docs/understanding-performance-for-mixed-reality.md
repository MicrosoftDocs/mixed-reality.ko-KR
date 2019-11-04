---
title: 혼합 현실 성능 이해
description: Windows Mixed Reality 앱 성능을 최적화 하는 방법에 대 한 고급 항목 및 세부 정보
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 성능, 최적화, CPU, GPU
ms.openlocfilehash: 7d8a0c95d59ec7e42e11bc1e1b6b40c702e01529
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438238"
---
# <a name="understanding-performance-for-mixed-reality"></a>혼합 현실 성능 이해

이 문서에서는 혼합 현실 앱의 성능에 대 한 중요 한 개념을 소개 합니다.  최적의 프레임 속도에서 응용 프로그램이 실행 되지 않으면 사용자 환경이 크게 저하 될 수 있습니다. Holograms가 불안정 하 게 표시 되 고 환경에 대 한 헤드 추적이 부정확 하 게 표시 되어 사용자에 게 잘못 된 환경을 제공 합니다. 성능은 혼합 현실 개발의 경우 첫 번째 클래스 기능으로 간주 되어야 하며,이는 폴란드어 작업이 아닙니다.

각 대상 플랫폼에 대 한 성능의 프레임 속도 값은 아래에 나열 되어 있습니다.

| 플랫폼 | 대상 프레임 율 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality 울트라 Pc](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pc](immersive-headset-hardware-details.md) | 60 FPS |

아래 프레임 워크는 대상 프레임 속도 적중에 대 한 모범 사례를 간략하게 설명 합니다. Unity에서 개발 하는 경우 unity 환경에서 프레임 속도를 측정 하 고 개선 하는 방법에 대 한 팁은 [unity의 성능 권장 사항 문서](performance-recommendations-for-unity.md) 를 참조 하세요.

## <a name="understanding-performance-bottlenecks"></a>성능 병목 상태 이해

앱에 실적이 떨어지는 프레임 속도가 있는 경우 첫 번째 단계는 응용 프로그램의 계산 집약적 위치를 분석 하 고 이해 하는 것입니다. 장면을 렌더링 하는 작업을 담당 하는 두 가지 기본 프로세서는 CPU와 GPU입니다. 이러한 각 항목은 혼합 현실 앱의 다양 한 측면을 처리 합니다. 병목 현상이 발생할 수 있는 세 가지 주요 위치는 다음과 같습니다. 

1. **앱 스레드-CPU** -이 스레드는 응용 프로그램 논리를 담당 합니다. 여기에는 입력, 애니메이션, 물리 및 기타 응용 프로그램 논리가 포함 됩니다.
2. **CPU에 스레드 CPU 렌더링** -이 스레드는 gpu에 그리기 호출을 전송 하는 일을 담당 합니다. 응용 프로그램에서 큐브나 모델 등의 개체를 렌더링 하려는 경우이 스레드는 이러한 작업을 수행 하기 위해 GPU에 요청을 보냅니다.
3. **GPU** -이 프로세서는 가장 일반적으로 응용 프로그램의 그래픽 파이프라인을 처리 하 여 3d 데이터 (모델, 질감 등)를 픽셀로 변환 합니다. 궁극적으로 장치 화면에 제출할 2D 이미지를 생성 합니다.

![프레임 수명](images/lifetime-of-a-frame.png)

일반적으로 HoloLens 응용 프로그램은 GPU에 바인딩되므로 항상 그렇지는 않습니다. 아래 도구와 기술을 사용 하 여 특정 앱의 병목 현상이 발생 하는 위치를 파악할 수 있습니다.

## <a name="how-to-analyze-your-application"></a>응용 프로그램을 분석 하는 방법

혼합 현실 응용 프로그램의 성능 프로필을 이해 하는 데 사용할 수 있는 많은 도구가 있습니다. 이를 통해 병목 상태를 해결할 수 있는 위치와 이유를 찾을 수 있습니다.

응용 프로그램에 대 한 심층 프로 파일링 정보를 얻을 수 있는 몇 가지 일반적인 도구는 다음과 같습니다.
- [Intel 그래픽 성능 분석기](https://software.intel.com/gpa)
- [Visual Studio 그래픽 디버거](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity 프로파일러](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>모든 환경에서 프로 파일링 하는 방법

응용 프로그램에서 GPU가 바인딩되어 있는지 아니면 CPU에 바인딩되어 있는지를 확인 하는 한 가지 방법은 렌더링 대상 출력의 해상도를 낮추는 것입니다. 계산 되는 픽셀 수를 줄이면 GPU 부하가 감소 합니다. 장치는 작은 질감으로 렌더링 된 다음 위쪽의 샘플을 통해 최종 이미지를 표시 합니다.

렌더링 해상도를 줄이고 나면 다음을 수행 합니다.
1) 응용 프로그램 프레임 속도가 **늘어나면** **GPU가 바인딩될** 가능성이 높습니다.
1) 응용 프로그램 프레임 속도가 **변경 되지**않은 경우 **CPU 바인딩될** 가능성이 높습니다.

>[!NOTE]
>Unity는 *[Xrsettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 통해 런타임에 응용 프로그램의 렌더링 대상 해상도를 쉽게 수정할 수 있는 기능을 제공 합니다. 장치에 표시 되는 최종 이미지의 해상도는 고정 되어 있습니다. 플랫폼은 디스플레이에서 렌더링 하기 위한 더 높은 해상도 이미지를 빌드하기 위해 낮은 해상도 출력을 샘플링 합니다. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>응용 프로그램을 개선 하는 방법

### <a name="cpu-performance-recommendations"></a>CPU 성능 권장 사항

일반적으로 CPU의 혼합 현실 응용 프로그램에서 대부분의 작업은 장면의 "시뮬레이션"을 수행 하 고 응용 프로그램 논리를 처리 하는 작업을 포함 합니다. 다음 영역은 일반적으로 최적화를 대상으로 합니다.

- 애니메이션
- 물리
- 메모리 할당
- 복합 알고리즘 (예: 역 기구학, 경로 찾기)

### <a name="gpu-performance-recommendations"></a>GPU 성능 권장 사항

#### <a name="understanding-bandwidth-vs-fill-rate"></a>대역폭 및 채우기 빈도 이해
GPU에서 프레임을 렌더링 하는 경우 응용 프로그램은 일반적으로 메모리 대역폭이 나 채우기 속도로 바인딩됩니다.

- **메모리 대역폭** 은 GPU에서 메모리를 통해 수행할 수 있는 읽기 및 쓰기의 률입니다.
    - 대역폭 제한을 확인 하려면 질감 품질을 줄이고 프레임 속도가 개선 되었는지 확인 합니다.
    - Unity에서는 **편집** > **프로젝트 설정** >  **[품질 설정](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 에서 **질감 품질** 을 변경 하 여이 작업을 수행할 수 있습니다.
- **채우기 비율은** GPU에서 초당 그릴 수 있는 픽셀을 나타냅니다.
    - 채우기 속도 제한을 파악 하려면 디스플레이 해상도를 낮추고 프레임 속도가 개선 되었는지 확인 합니다. 
    - Unity에서는 *[Xrsettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 통해이 작업을 수행할 수 있습니다.

메모리 대역폭은 일반적으로 다음 중 하나에 대 한 최적화를 포함 합니다.
1) 텍스처 해상도 줄이기
2) 질감 (법선, 반사 등)을 덜 활용 합니다.

채우기 비율은 최종 렌더링 된 픽셀에 대해 계산 되어야 하는 작업의 수를 줄이는 데 중점을 두었습니다. 여기에는 축소가 포함 됩니다.
1) 렌더링/처리할 개체 수
2) 셰이더 당 작업 수
3) 최종 결과 (기 하 도형 셰이더, 사후 처리 효과 등)에 대 한 GPU 스테이지 수
4) 렌더링할 픽셀 수 (해상도 표시)

#### <a name="reduce-polygon-count"></a>다각형 수 줄이기
다각형 수가 높을수록 GPU에 대 한 작업이 더 많이 발생 합니다. 장면의 다각형 수를 줄이면 렌더링 시간이 줄어듭니다. 비용이 많이 들 수 있는 기 하 도형에 음영을 지정 하는 다른 요인이 있지만 polygon 수는 장면을 렌더링 하는 데 소요 되는 비용을 결정 하는 가장 간단한 메트릭입니다.

#### <a name="limit-overdraw"></a>과도 한 그리기 제한

Occluding 개체에 의해 숨겨질 때 여러 개체가 렌더링 되지만 화면에 표시 되지 않는 경우에는 높은 오버 그리기가 발생 합니다. 개체 뒤에 개체를 포함 하는 벽을 살펴보겠습니다. 모든 기 하 도형은 렌더링을 위해 처리 되지만 불투명 벽만 렌더링 해야 합니다. 이로 인해 불필요 한 작업이 수행 됩니다.

#### <a name="shaders"></a>셰이더

셰이더는 GPU에서 실행 되는 작은 프로그램으로, 렌더링에서 다음과 같은 두 가지 중요 한 단계를 수행 합니다.
1) 그려야 하는 꼭 짓 점 및 화면 공간에 있는 위치 결정 (꼭 짓 점 셰이더)
    - 꼭 짓 점 셰이더는 일반적으로 모든 메시에 대해 꼭 짓 점에 대해 실행 됩니다.
2) 각 픽셀의 색 확인 (픽셀 셰이더)
    - 픽셀 셰이더는 기 하 도형에 의해 렌더링 되는 질감에 대해 렌더링 되는 픽셀 마다 실행 됩니다.

일반적으로 셰이더는 많은 변환 및 조명 계산을 수행 합니다. 복합 조명 모델, 그림자 및 기타 작업은 환상적인 결과를 생성할 수 있지만 가격과 함께 제공 됩니다. 셰이더에서 계산 된 작업의 수를 줄이면 프레임 당 GPU에 필요한 작업을 크게 줄일 수 있습니다.

##### <a name="shader-coding-recommendations"></a>셰이더 코딩 권장 사항

- 가능 하면 이중 선형 필터링 사용
- 곱하기 및 추가를 동시에 수행 하기 위해 MAD 내장 함수를 사용 하도록 식 다시 정렬
- CPU에서 최대한 Precalculate 하 고 재질에 상수로 전달 합니다.
- **픽셀 셰이더의 작업을 꼭 짓 점 셰이더로 이동 합니다.**
    - 일반적으로 꼭 짓 점 수는 픽셀 수 (720p는 921600 픽셀, 1080p는 2073600 픽셀 등) 보다 훨씬 작습니다.

#### <a name="remove-gpu-stages"></a>GPU 단계 제거
사후 처리 효과는 비용이 많이 들고 응용 프로그램의 채우기 비율이 높아질 수 있습니다. 여기에는 MSAA와 같은 앤티앨리어싱 기술이 포함 됩니다. HoloLens에서는 이러한 기술을 완전히 피하는 것이 좋으며 geometry, 선체 및 compute 셰이더와 같은 추가 셰이더 단계를 사용 하는 것이 좋습니다.

## <a name="memory-recommendations"></a>메모리 권장 사항
과도 한 메모리 할당 및 할당 취소 작업을 수행 하면 일관 되지 않은 성능, 고정 된 프레임 및 기타 나쁜 동작이 발생할 수 있습니다. 메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 특히 중요 합니다.

#### <a name="object-pooling"></a>개체 풀링

개체 풀링은 연속 할당 및 개체 할당 해제 비용을 줄이는 인기 있는 기술입니다. 이 작업을 수행 하려면 시간이 지남에 따라 개체를 지속적으로 생성 및 제거 하는 대신 동일한 개체의 대량 풀을 할당 하 고이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용 합니다. 개체 풀은 앱을 실행 하는 동안 변수 수명이 있는 다시 사용할 수 있는 구성 요소에 적합 합니다.

## <a name="see-also"></a>참고 항목
- [Unity의 권장 성능](performance-recommendations-for-unity.md)
- [Unity 권장 설정](recommended-settings-for-unity.md)
