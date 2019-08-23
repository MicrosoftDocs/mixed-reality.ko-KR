---
title: 혼합 현실 성능 이해
description: Windows Mixed Reality 앱 성능을 최적화 하는 방법에 대 한 고급 항목 및 세부 정보
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 성능, 최적화, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548836"
---
# <a name="understanding-performance-for-mixed-reality"></a>혼합 현실 성능 이해

이 문서에서는 혼합 현실 앱의 성능에 대 한 중요 한 가져가지 소개 합니다.  최적의 프레임 속도에서 응용 프로그램이 실행 되지 않으면 사용자 환경이 크게 저하 될 수 있습니다. Holograms가 불안정 하 게 표시 되 고 환경에 대 한 헤드 추적이 부정확 하 게 표시 되어 사용자에 게 잘못 된 환경을 제공 합니다. 실제로 성능은 혼합 현실 개발을 위한 첫 번째 클래스 기능으로 간주 되어야 하며,이는 안정화 된 주기 작업이 아닙니다.

검토를 위해 각 대상 플랫폼에 대 한 성능의 프레임 속도 값이 아래에 나열 됩니다.

| 플랫폼 | 대상 프레임 율 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality 울트라 Pc](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pc](immersive-headset-hardware-details.md) | 60 FPS |

아래 프레임 워크는 대상 프레임 속도에 대 한 모범 사례 및 사항을 이해에 대 한 일반적인 개요를 제공 합니다. 자세히 알아보려면 [Unity의 성능 권장 사항 문서](performance-recommendations-for-unity.md)를 참조 하세요. 특히이 관련 문서에서는 unity Windows Mixed Reality 앱에서의 프레임 속도를 측정 하는 방법 및 Unity 환경에서 성능을 개선 하기 위해 수행할 단계에 대해 설명 합니다.

## <a name="understanding-performance-bottlenecks"></a>성능 병목 상태 이해

앱에 실적이 떨어지는 프레임 속도가 있는 경우 첫 번째 단계는 응용 프로그램의 계산 집약적 위치를 분석 하 고 이해 하는 것입니다. 장면을 렌더링 하는 작업을 담당 하는 두 가지 기본 프로세서는 CPU와 GPU입니다. 이러한 두 구성 요소는 혼합 현실 앱의 서로 다른 작업 및 단계를 처리 합니다. 병목 현상이 발생할 수 있는 세 가지 주요 위치가 있습니다. 

1. **앱 스레드-CPU** -이 스레드는 응용 프로그램 논리를 담당 합니다. 여기에는 입력, 애니메이션, 물리 및 기타 앱 논리/상태 처리가 포함 됩니다.
2. **CPU에 스레드 CPU 렌더링** -이 스레드는 gpu에 그리기 호출을 전송 하는 일을 담당 합니다. 응용 프로그램에서 큐브나 모델 등의 개체를 렌더링 하려는 경우이 스레드에서는 렌더링을 위해 최적화 된 아키텍처가 포함 된 요청을 GPU에 전송 하 여 이러한 작업을 수행 합니다.
3. **GPU** - 
    이 프로세서는 주로 3d 데이터 (모델, 질감 등)를 픽셀로 변환 하 고 궁극적으로 장치 화면에 제출할 2d 이미지를 생성 하는 응용 프로그램의 그래픽 파이프라인을 처리 합니다.

![프레임 수명](images/lifetime-of-a-frame.png)

일반적으로 HoloLens 응용 프로그램은 GPU 경계가 됩니다. 그러나이는 모든 응용 프로그램에 적용 되지 않으며, 따라서 아래 & 기술을 사용 하 여 특정 앱에 대 한 사항을 파악 하는 것이 좋습니다.

## <a name="how-to-analyze-your-application"></a>응용 프로그램을 분석 하는 방법

혼합 현실 응용 프로그램의 성능 프로필을 이해할 수 있는 개발자로 서의 많은 도구가 있습니다. 이러한 기능을 사용 하면 병목 현상이 있는 위치를 대상으로 하는 대상과 해당 나타나고을 디버그 하는 방법을 모두 사용할 수 있습니다.

응용 프로그램에 대 한 심층 프로 파일링 정보를 얻는 인기 있는 강력한 도구 목록입니다.
- [Intel 그래픽 성능 분석기](https://software.intel.com/gpa)
- [Visual Studio 그래픽 디버거](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity 프로파일러](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 프레임 디버거](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>모든 환경에서 프로 파일링 하는 방법

응용 프로그램에서 GPU 제한 또는 CPU가 제한 되어 있는지 신속 하 게 확인 하는 간단한 테스트가 있습니다. 렌더링 대상 출력의 해상도를 낮추면 이미지를 렌더링 하기 위해 GPU에서 수행 해야 하는 작업의 수가 감소 합니다. 뷰포트 크기 조정 (동적 해상도 크기 조정)은 더 작은 렌더링 대상에 이미지를 렌더링 하는 방법으로, 출력 장치에서 표시할 수 있습니다. 최종 이미지를 표시 하기 위해 더 작은 픽셀 집합에서 장치를 위로 샘플링 합니다.

렌더링 해상도를 줄이고 나면 다음을 수행 합니다.
1) 응용 프로그램의 프레임 속도가 **늘어나면** **GPU 경계가** 발생할 수 있습니다.
1) 응용 프로그램 프레임 속도가 **변경 되지**않은 경우 **CPU 제한** 가능성이 있습니다.

>[!NOTE]
>Unity는 *[Xrsettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 통해 런타임에 응용 프로그램의 렌더링 대상 해상도를 쉽게 수정할 수 있는 기능을 제공 합니다. 장치에 표시 되는 최종 이미지의 해상도는 고정 되어 있습니다. 플랫폼은 디스플레이에서 렌더링 하기 위한 더 높은 해상도 이미지를 빌드하기 위해 낮은 해상도 출력을 샘플링 합니다. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>응용 프로그램을 개선 하는 방법

### <a name="cpu-performance-recommendations"></a>CPU 성능 권장 사항

일반적으로 CPU의 혼합 현실 응용 프로그램에서 대부분의 작업은 장면의 "시뮬레이션"을 수행 하 고 광범위 한 고유 응용 프로그램 논리를 처리 하는 작업을 포함 합니다. 따라서 일반적으로 다음 영역은 최적화를 대상으로 합니다.

- 애니메이션
- 물리학 단순화
- 메모리 할당
- 복합 알고리즘 (예: 역 기구학, 경로 찾기)

### <a name="gpu-performance-recommendations"></a>GPU 성능 권장 사항

#### <a name="understanding-bandwidth-vs-fill-rate"></a>대역폭과 채우기 빈도 이해
GPU에서 프레임을 렌더링 하는 경우 응용 프로그램은 일반적으로 메모리 대역폭이 나 채우기 속도로 제한 됩니다.

- **메모리 대역폭** 은 GPU에서 메모리를 통해 수행할 수 있는 읽기 및 쓰기의 률입니다.
    - 대역폭 제한을 파악 하려면 질감 품질을 줄이고 프레임 속도가 개선 되었는지 확인 합니다.
    - Unity에서는 > **프로젝트 설정** >  **[품질설정](https://docs.unity3d.com/Manual/class-QualitySettings.html)** **편집**에서 **질감 품질** 을 변경 하 여이 작업을 수행할 수 있습니다.
- **채우기 속도** 는 GPU에서 초당 그릴 수 있는 렌더링 된 픽셀의 처리량을 나타냅니다.
    - 채우기 속도 제한을 파악 하려면 디스플레이 해상도를 낮추고 프레임 속도가 개선 되었는지 확인 합니다. 
    - Unity에서는 *[Xrsettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 속성을 통해이 작업을 수행할 수 있습니다.

메모리 대역폭은 일반적으로 다음에 대 한 최적화를 포함 합니다.
1) 텍스처 해상도 줄이기
2) less 텍스처를 활용 합니다 (즉, 수직, 반사 등)

채우기 비율은 주로 렌더링 된 최종 픽셀에 대해 계산 되어야 하는 작업의 수를 줄이는 데 중점을 두었습니다. 이에 대 한 예는 일반적으로 줄어듭니다.
1) 렌더링/처리할 개체 수
2) 셰이더 당 작업 수
3) 최종 결과에 대 한 GPU 단계 수 (기 하 도형 셰이더, 처리 후 효과 등)
4) 렌더링할 픽셀 수 (즉, 디스플레이 해상도)

#### <a name="reduce-poly-count"></a>Poly 수 줄이기
다각형 수가 높을수록 GPU에 대 한 작업이 더 많이 발생 하 고 장면의 다각형 수가 줄어들기 때문에 해당 기 하 도형 렌더링 시간이 줄어듭니다. 계속 해 서 비용이 들 수 있는 기 하 도형에 음영을 적용 하는 것과 관련 된 다른 요인이 있습니다. 하지만 polygon 수는 장면을 렌더링 하는 데 드는 비용을 결정 하는 기본 메트릭입니다.

#### <a name="limit-overdraw"></a>과도 한 그리기 제한

여러 개체가 렌더링 되지만 화면에 표시 되지 않는 경우에는 일반적으로 더 가까운 occluding 개체에 의해 숨겨질 때 발생 합니다. 여러 방 및 기 하 도형을 포함 하는 벽을 살펴보겠습니다. 모든 기 하 도형은 렌더링을 위해 처리 되지만, 불투명 벽만이 다른 모든 콘텐츠의 보기를 occludes 렌더링 해야 합니다. 이로 인해 현재 뷰에 불필요 한 작업이 필요 하지 않습니다.

#### <a name="shaders"></a>셰이더

셰이더는 GPU에서 실행 되는 작은 프로그램으로, 일반적으로 렌더링에서 다음과 같은 두 가지 중요 한 단계를 결정 합니다.
1) 화면에 그려야 하는 개체의 꼭지점과 화면 공간 (예: 꼭 짓 점 셰이더)
    - 꼭 짓 점 셰이더는 일반적으로 모든 GameObject에 대 한 꼭 짓 점 마다 실행 됩니다.
2) 이러한 픽셀의 색을 결정 하는 방법 (즉, 픽셀 셰이더)
    - 픽셀 셰이더는 장치에 대해 렌더링 되는 질감에 대해 픽셀 단위로 실행 됩니다.

일반적으로 셰이더는 많은 변환 및 조명 계산을 수행 합니다. 복합 조명 모델, 그림자 및 기타 작업은 환상적인 결과를 생성할 수 있지만 가격과 함께 제공 됩니다. 셰이더에서 계산 된 작업의 수를 줄이면 프레임 당 GPU에 의해 수행 되는 데 필요한 전체 작업을 크게 줄일 수 있습니다.

##### <a name="shader-coding-recommendations"></a>셰이더 코딩 권장 사항

- 가능 하면 항상 이중 선형 필터링 사용
- 곱하기 및 추가를 동시에 수행 하기 위해 MAD 내장 함수를 사용 하도록 식 다시 정렬
- CPU에서 최대한 Precalculate 하 고 재질에 상수로 전달 합니다.
- **픽셀 셰이더의 작업을 꼭 짓 점 셰이더로 이동 합니다.**
    - 일반적으로 꼭지점의 # < < 픽셀 (즉, 720p = = 921600 픽셀, 1080p = = 2073600 픽셀 등)

#### <a name="remove-gpu-stages"></a>GPU 단계 제거
사후 처리 효과는 매우 비쌉니다. 일반적으로 응용 프로그램의 채우기 비율이 저하 될 수 있습니다. 여기에는 MSAA와 같은 앤티앨리어싱 기술도 포함 됩니다. HoloLens에서는 이러한 기술을 완전히 방지 하는 것이 좋습니다. 또한 가능 하면 geometry, 선체 및 compute 셰이더와 같은 추가 셰이더 단계를 피해 야 합니다.

## <a name="memory-recommendations"></a>메모리 권장 사항
과도 한 메모리 할당 & 할당 취소 작업은 holographic 응용 프로그램에 부정적인 영향을 줄 수 있으므로 성능, 고정 된 프레임 및 기타 부정적 동작이 일치 하지 않을 수 있습니다. 메모리 관리는 가비지 수집기에 의해 제어 되므로 Unity에서 개발할 때 메모리 고려 사항을 이해 하는 것이 특히 중요 합니다.

#### <a name="object-pooling"></a>개체 풀링

개체 풀링은 연속 & 할당의 비용을 줄이고 개체 할당을 취소 하는 인기 있는 기술입니다. 이 작업을 수행 하려면 시간이 지남에 따라 개체를 지속적으로 생성 및 제거 하는 대신 동일한 개체의 대량 풀을 할당 하 고이 풀에서 사용 가능한 비활성 인스턴스를 다시 사용 합니다. 개체 풀은 앱을 실행 하는 동안 변수 수명이 있는 다시 사용할 수 있는 구성 요소에 적합 합니다.

## <a name="see-also"></a>참조
- [Unity의 권장 성능](performance-recommendations-for-unity.md)
- [Unity 권장 설정](recommended-settings-for-unity.md)
