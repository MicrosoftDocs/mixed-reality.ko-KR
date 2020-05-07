---
title: 장면 이해
description: HoloLens의 장면 이해 기능 소개
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity
ms.openlocfilehash: 615da20df95f4a435216457e8b9f16bb7d7d069b
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604964"
---
# <a name="scene-understanding"></a>장면 이해

장면 이해는 environmentally 인식 응용 프로그램을 쉽게 개발할 수 있도록 설계 된 구조적인 고급 환경 표현을 포함 하는 혼합 현실 개발자를 제공 합니다. 장면 이해는 매우 정확한 구조화 되지 않은 [공간 매핑과](spatial-mapping.md) 새로운 AI 기반 런타임과 같이 기존의 혼합 현실 런타임의 강력한 기능을 결합 하 여이를 수행 합니다. 이러한 기술을 결합 하 여 장면 이해는 Unity 또는 ARKit/Arkit와 같은 프레임 워크에서 사용한 것과 유사한 3D 환경의 표현을 생성 합니다. 장면 이해 진입점은 새 장면을 계산 하기 위해 응용 프로그램에서 호출 하는 장면 관찰자로 시작 합니다. 현재이 기술은 세 가지 고유 하지만 관련 된 개체 범주를 생성할 수 있습니다. 간소화 된 watertight 환경 메시를 사용 하 여 Quads를 호출 하는 배치에 대해 복잡 한 평면 영역을 유추 하 고, 노출 된 Quads/Watertight 데이터에 맞는 [공간 매핑](spatial-mapping.md) 메시의 스냅숏을 만들 수 있습니다.

![공간 매핑 메시, 레이블이 지정 된 평면 표면, watertight 메시](images/SUScenarios.png)

이 문서는 시나리오 개요를 제공 하 고 장면 이해 및 공간 매핑 공유의 관계를 명확 하 게 설명 하기 위한 것입니다.

## <a name="developing-with-scene-understanding"></a>장면 이해로 개발

이 문서에서는 런타임 및 개념을 이해 하는 데만 사용 됩니다. 장면 이해를 통해 개발 하는 방법에 대 한 설명서를 찾으려는 경우 다음에 관심이 있을 수 있습니다.

[장면 이해 SDK 개요](scene-understanding-SDK.md)

샘플 GitHub 사이트에서 장면 이해 샘플 앱을 다운로드할 수 있습니다.

[장면 이해 샘플](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

장치를 사용 하지 않고 장면 이해를 시도 하기 위해 샘플 장면에 액세스 하려는 경우 샘플 자산 폴더에는 장면이 있습니다.

[장면 이해 샘플 장면](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK)

장면 이해를 위해 개발 하는 방법 또는 장면 이해의 작동 방식에 대 한 자세한 내용 및 개발 방법에 대 한 자세한 내용을 보려면 [장면 이해 SDK 개요](scene-understanding-SDK.md) 설명서를 참조 하세요.


### <a name="sample"></a>샘플


## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 gen)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>장면 이해</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>일반 시나리오

![일반적인 공간 매핑 사용 시나리오의 그림: 배치, 폐색, 물리 및 탐색](images/sm-concepts-1000px.png)<br>
*일반적인 공간 매핑 사용 시나리오: 배치, 폐색, 물리 및 탐색.*

<br>

환경 인식 응용 프로그램 (배치, 폐색, 물리 등)에 대 한 핵심 시나리오의 대부분은 공간 매핑과 장면 이해를 통해 주소를 지정할 수 있으며,이 섹션에서는 이러한 차이를 강조 표시 합니다. 장면 이해와 공간 매핑의 핵심 차이점은 최대 정확성과 구조 및 단순성의 대기 시간에 대 한 균형입니다. 응용 프로그램에 사용자만 액세스할 수 있는 가장 낮은 대기 시간 및 메시 삼각형이 필요한 경우 공간 매핑을 직접 사용 합니다. 더 높은 수준의 처리를 수행 하는 경우 기능 상위 집합을 제공 해야 하므로 장면 이해 모델로 전환 하는 것을 고려할 수 있습니다. 장면 이해는 해당 표현의 일부로 공간 매핑 메시의 스냅숏을 제공 하므로 항상 가장 완전 하 고 정확한 공간 매핑 데이터에 액세스할 수 있습니다.

다음 섹션에서는 새 장면 이해 SDK의 컨텍스트에서 핵심 공간 매핑 시나리오를 다시 방문 합니다.

### <a name="placement"></a>배치

장면 이해에서는 배치 시나리오를 간소화 하기 위해 특별히 설계 된 새 구문을 제공 합니다. 장면은 holograms을 배치할 수 있는 플랫 표면을 설명 하는 SceneQuads 라는 기본 형식을 계산할 수 있습니다. SceneQuads는 특별히 배치를 중심으로 디자인 되었으며 2D 표면을 설명 하 고 해당 화면에 배치 하기 위한 API를 제공 합니다. 이전에는 삼각형 메시를 사용 하 여 배치를 수행할 때 쿼드의 모든 영역을 검색 하 고 구멍 채우기/사후 처리를 수행 하 여 개체 배치를 위한 좋은 위치를 확인 해야 했습니다. 장면 이해 런타임은 스캔 되지 않은 쿼드 영역을 유추 하 고 표면의 일부가 아닌 쿼드 영역을 무효화 하는 데 사용할 수 있으므로 Quads에는 항상 필요 하지 않습니다.

:::row:::
    :::column:::
       ![유추를 사용 하지 않도록 설정 하 고, 스캔 한 영역에 대 한 배치 영역을 SceneQuads 합니다.](images/SUQuads.png)<br>
       **이미지 #1** -유추가 사용 하지 않도록 설정 된 SceneQuads, 스캔 한 영역에 대 한 배치 영역 캡처
    :::column-end:::
        :::column:::
       ![유추를 사용 하도록 설정 하면 배치가 더 이상 스캔 된 영역으로 제한 되지 않습니다.](images/SUWatertight.png)<br>
        **이미지 #2** -유추를 사용 하도록 설정 하면 배치가 더 이상 스캔 된 영역으로 제한 되지 않습니다.
    :::column-end:::
:::row-end:::

<br>


응용 프로그램에서 2D 또는 3D holograms를 환경의 고정 구조에 배치 하려는 경우 배치를 위한 SceneQuads의 단순성과 편의성은 [공간 매핑](spatial-mapping.md) 메시에서이 정보를 계산 하는 것 보다 좋습니다. 이 항목에 대 한 자세한 내용은 참조 [장면 이해 SDK 참조](scene-understanding-SDK.md) 를 참조 하세요.

**참고** 공간 매핑 메시에 의존 하는 레거시 배치 코드의 경우 EnableWorldMesh 설정을 설정 하 여 SceneQuads와 함께 공간 매핑 메시를 계산할 수 있습니다. 장면 이해 API가 응용 프로그램의 대기 시간 요구 사항에 맞지 않는 경우 [공간 매핑 api](spatial-mapping.md#placement)를 계속 사용 하는 것이 좋습니다.

### <a name="occlusion"></a>폐색

[공간 매핑 폐색](spatial-mapping.md#occlusion) 환경의 실시간 상태를 캡처하는 가장 낮은 방법으로 유지 됩니다. 이는 매우 동적인 장면에서 폐색을 제공 하는 데 유용할 수 있지만 여러 가지 이유로 폐색에 대 한 장면 이해를 고려할 수 있습니다. 장면 이해로 생성 된 공간 매핑 메시를 사용 하는 경우 로컬 캐시에 저장 되지 않으므로 인식 Api에서 사용할 수 없는 공간 매핑에서 데이터를 요청할 수 있습니다. Watertight 메시와 함께 폐색에 대 한 공간 매핑을 사용 하면 특히 스캔 되지 않은 대화방 구조를 완료 하는 추가 값이 제공 됩니다.

요구 사항에 따라 장면 이해의 대기 시간이 길어질 수 있는 경우, 응용 프로그램 개발자는 장면 이해 watertight 메시를 사용 하 고 한꺼번에의 공간 매핑 메시를 평면 표현과 함께 사용 하는 것을 고려해 야 합니다. 이렇게 하면 간소화 된 watertight 폐색이 가장 현실적인 폐색 지도를 제공 하는 보다 정교한 nonplanar 기 하 도형으로 결혼 하는 "세계 최고의" 시나리오를 제공 합니다.

### <a name="physics"></a>물리

장면 이해는 공간 매핑 메시가 적용 하는 물리의 많은 제한 사항을 해결 하기 위해 의미 체계를 사용 하 여 공간을 분해 하는 watertight 메시를 생성 합니다. Watertight 구조체를 사용 하면 물리학 광선 캐스팅이 항상 적중 되며, 의미 체계 분해를 통해 실내 탐색을 위한 탐색 메시를 보다 간단 하 게 생성할 수 있습니다. [폐색](#occlusion)에 대 한 섹션에 설명 된 대로 EnableSceneObjectMeshes 및 EnableWorldMesh를 사용 하 여 장면을 만들면 실제로 완전히 완료 된 메시가 생성 됩니다. 환경 메쉬의 watertight 속성은 적중 테스트가 적중 하는 표면에 도달 하지 않도록 방지 하 고 메시 데이터를 사용 하면 물리학가 방 구조만이 아니라 장면의 모든 개체와 상호 작용 하 게 됩니다.

### <a name="navigation"></a>탐색

의미 체계 클래스로 분해 된 평면 메시는 탐색 및 경로 계획에 이상적인 구문이 며 [공간 매핑 탐색](spatial-mapping.md#navigation) 개요에 설명 된 많은 문제를 감속 합니다. 장면에서 계산 되는 SceneMesh 개체는 이미 표면 유형에 의해 구성 되어 있지 않습니다. 탐색-메시 생성은 사용할 수 있는 서피스로 제한 됩니다. 구조는 간단 하기 때문에 Unity와 같은 3d 엔진의 동적 탐색-메시 생성은 실시간 요구 사항에 따라 realistic 됩니다.

정확한 탐색을 생성 하는 메시는 현재 사후 처리가 필요 합니다. 즉, 탐색이 복잡 한/테이블을 통해 전달 되지 않도록 응용 프로그램이 바닥에 계속 occluders 야 합니다. 이를 수행 하는 가장 정확한 방법은 장면이 EnableWorldMesh 플래그를 사용 하 여 계산 되는 경우 제공 되는 세계 메시 데이터를 프로젝션 하는 것입니다.

### <a name="visualization"></a>시각화

[공간 매핑 시각화](spatial-mapping.md#visualization) 를 사용 하 여 환경에 대 한 실시간 피드백을 제공할 수 있지만, 평면 및 watertight 개체의 단순성은 더 많은 성능과 시각적 품질을 제공 합니다. 공간 매핑을 사용 하 여 설명 하는 그림자 프로젝션 및 접지 기술은 Quads 또는 planar watertight 메시에서 제공 되는 평면 표면에서 투영 된 경우 더 보기 편 수 있습니다. 이는 장면에서 유추할 수 있는 팩트 때문에 철저 한 사전 검사가 최적이 아닌 환경/시나리오에서 특히 중요 합니다.

또한 공간 매핑에서 반환 된 총 표면 수는 내부 공간 캐시에 의해 제한 되는 반면 장면 이해의 공간 매핑 메시 버전은 캐시 되지 않은 공간 매핑 데이터에 액세스할 수 있습니다. 이로 인해 시각화 또는 추가 메시 처리를 위해 장면 이해는 단일 공간 보다 큰 공간에 대 한 메시 표현을 캡처하는 데 더 적합 합니다. EnableWorldMesh를 사용 하 여 반환 되는 세계 메시는 전체에 걸쳐 일관 된 세부 수준을 가지 며,이는 와이어 프레임으로 렌더링 되는 경우 더 많은 보기 편 시각화를 생성할 수 있습니다.

### <a name="see-also"></a>참고 항목

* [장면 이해 SDK](scene-understanding-SDK.md)
* [공간 매핑](spatial-mapping.md)
