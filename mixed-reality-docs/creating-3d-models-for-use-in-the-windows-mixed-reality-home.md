---
title: 집에서 사용할 3D 모델 만들기
description: 자산 요구 사항 및 HoloLens와 몰입 형 (VR) 헤드셋 홈 Windows Mixed Reality에 사용할 3D 모델에 대 한 지침을 작성 합니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 모델링 지침 자산 요구 사항, 지침, 표시 아이콘, 3D 표시 아이콘, 질감, 자료, 복잡성, 삼각형, 메시, 다각형, polycount, 제작 3D 모델링 제한
ms.openlocfilehash: 73af40cf2915742cab612625c8243a36ee74d748
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692288"
---
# <a name="create-3d-models-for-use-in-the-home"></a>집에서 사용할 3D 모델 만들기

합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 출발점 응용 프로그램을 시작 하기 전에 사용자가 이동 하는 위치입니다. Windows Mixed Reality 헤드셋 활용 하 여 응용 프로그램을 디자인할 수 있습니다는 [는 앱 시작 관리자를 사용 하 여 3D 모델](implementing-3d-app-launchers.md) 하 고 허용 [홈 Windows Mixed Reality 넣을 3D 딥 링크](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) 에서 앱 내에서. 이 문서에서는 Windows Mixed Reality 홈 호환 3D 모델을 만들기 위한 지침을 설명 합니다.

## <a name="asset-requirements-overview"></a>자산 요구 사항 개요
Windows Mixed Reality에 대 한 3D 모델을 만들 때 모든 자산을 충족 해야 하는 몇 가지 요구 사항이 있습니다. 
1. [내보내기](#exporting-models) -.glb 파일 형식 (이진 glTF) 자산을 배달 되어야 합니다
2. [모델링](#modeling-guidelines) -자산 해야 10 보다 작은 k 삼각형 수, 최대 64 개의 노드가 있고 LOD 당 32 submeshes
3. [자료](#material-guidelines) -질감 4096x4096 보다 클 수 없습니다 하 고 가장 작은 mip 맵 하거나 차원에서 4 개 이하의 해야 합니다.
4. [애니메이션](#animation-guidelines) -애니메이션 30FPS에서 20 분 보다 길 수 없습니다 (36,000 키프레임)이 있어야 하 고 < = 8192 morph 대상 꼭 짓 점
5. [최적화](#optimizations) -를 사용 하 여 자산을 최적화 해야 합니다 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)합니다. 이것이 **Windows OS 버전에 필요한 < 1709 =** Windows OS 버전에서 권장 및 > = 1803

이 문서의 나머지 부분에서는 이러한 요구 사항 뿐만 아니라 추가 지침 모델 홈 Windows Mixed Reality 잘 작동 하도록의 자세한 개요를 포함 합니다. 

## <a name="detailed-guidance"></a>자세한 지침

### <a name="exporting-models"></a>모델 내보내기

Windows Mixed Reality 홈.glb 파일 형식을 사용 하 여 포함 된 이미지 및 이진 데이터를 사용 하 여 3D 자산을 예상 합니다. Glb 사용료를 지불 인 glTF 형식의 이진 버전이 Khronos 그룹에 의해 유지 관리 하는 3D 자산 배달에 대 한 무료 개방형 표준입니다. Windows 앱 및 환경에서 형식에 대 한 Microsoft의 지원 됩니다 glTF 업계 상호 운용 가능한 3D 콘텐츠에 대 한 표준으로 발전 합니다. 찾으려면 먼저 glTF 자산을 만들지 않은 경우는 [지원 되는 내보내기 도구 목록과 변환기](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) glTF 작업 그룹 github 페이지입니다.  

### <a name="modeling-guidelines"></a>모델링 지침

Windows 홈 혼합 현실 환경 호환성을 위해 다음 모델링 지침에 따라 생성 되는 자산에 필요 합니다. 선택한 프로그램에서 모델링을 수행할 때 다음 권장 사항 및 제한 사항을 염두에:
1. 최대 축 "Y"로 설정 해야 합니다.
2. 자산 양의 Z 축 방향으로 "forward" 발생 해야 합니다.
3. 장면 원점 (0,0,0)에서 처음부터 평면상의 모든 자산을 빌드해야
4. 작업 단위에 설정할 미터와 자산을 전 세계 규모의 자산을 작성할 수 있습니다.
5. 모든 메시 결합할 필요가 없지만 경우 리소스가 제한 된 장치를 대상으로 하는 것이 좋습니다.
6. 모든 메시 전체 자산에 사용 되는 설정 하는 1 개의 질감을 사용 하 여 1 자료를 공유 해야
7. 0-1에서 사각형 배열에서 UVs 배치 해야 공간입니다. 허용 되는 있지만 바둑판식 배열 질감을 방지 합니다.
8. 다중 UVs 지원 되지 않습니다.
9. Double 양면된 자료는 지원 되지 않습니다.

### <a name="triangle-counts-and-levels-of-detail-lods"></a>삼각형 개수 및 세부 (단계 Lod) 수준

Windows Mixed Reality 홈 10,000 개 보다 많은 삼각형을 사용 하 여 모델을 지원 하지 않습니다. 프로그램 메시 이러한 수행이 수를 초과 하지 않는지 확인 하려면 내보내기 전에 삼각 측량 하는 것이 좋습니다. 또한 Windows MR 선택적 기 하 도형 수준의 성능 및 고품질 환경 되도록 세부 단계 (Lod)를 지원 합니다. [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) 3 버전 모델의 단일.glb 모델로 결합 하는 데 도움이 됩니다. Windows는 LOD 표시할 모델을 차지 하는 실제 화면 크기에 따라 결정 합니다. 3 개의 LOD 수준 삼각형 수를 권장 되는 다음을 사용 하 여 지원 됩니다.
<br>

|  LOD 수준  |  권장 되는 삼각형 수  |  최대 삼각형 수 | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>노드 수 및 표시 된 하위 메시에 제한
Windows Mixed Reality 홈 64 개 노드 또는 LOD 당 32 submeshes를 사용 하 여 모델을 지원 하지 않습니다. 노드는 개념은 [glTF 사양](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) 장면에 개체를 정의 하는 합니다. Submeshes 배열에 정의 된 [기본형](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) 개체에 메시에 서입니다. 

|  기능 |  설명  |  최대 지원 | 설명서 |
|------|------|------|------|
|  노드 |  GlTF 장면에 개체 |  LOD 별로 64 개 | [여기](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  기본 형식에서 모든 메시의 합계 |  LOD 당 32 | [여기](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>재질 지침

PBR 금속 거친 워크플로 사용 하 여 질감을 준비 해야 합니다. Albedo "," Normal "," 폐색 "," 금속, "및" 거친을 포함 하 여 질감의 전체 집합을 만들어 시작 합니다. 해당 권장 하지만 4096x4096 512 x 512의 저자는 해상도 사용 하 여 Windows Mixed Reality 지원 텍스처 최대입니다. 또한 아래에 설명 된 내보내기 단계에서 질감을 적용할 압축 형식에 대 한 요구 사항 이므로 질감 4의 배수로 해상도에서 작성 해야 합니다. 마지막으로, 경우 gerating mip 맵 또는 질감 가장 낮은 mip 최대 4 x 4 이어야 합니다.
<br>

|  권장 되는 질감 크기  |  최대 질감 크기 | 가장 낮은 Mip
|----|----|----|
|  512x512  |  4096x4096 | 최대 4 x 4|

### <a name="albedo-base-color-map"></a>(기본 색) albedo 맵

조명 정보 없이 원시 색입니다. 이 또한 맵에 금속 (금속성 맵에서 흰색) 및 (금속성 구조의 검정) 절연체 표면에 확산 정보와 반사율 각각 있습니다.

### <a name="normal"></a>보통

탄젠트 공간 일반 맵

### <a name="roughness-map"></a>거친 맵

개체의 microsurface를 설명합니다. 흰색 1.0은 대략적인은 검정 0.0 부드러운입니다. 이 맵에 가장 많은 문자를 노출 하는 진정한에 설명 된 대로 예: 흠집 자산, 지문, 긁혔거나, grime 등을 제공 합니다.

### <a name="ambient-occlusion-map"></a>앰비언트 폐색 맵

폐색 빛 반사를 차단 하는 영역을 보여 주는 값 확장 맵

### <a name="metallic-map"></a>금속성 맵

항목 인지 metal 셰이더를 지시 합니다. 원시 금속 흰색 1.0 비 금속 = = 0.0 검은색입니다. 더 트 바이크와 같은 원시 체제 미 설치 컴퓨터를 다루는 특징을 나타내기 위해 회색 전환 값이 있을 수 있지만 일반적이 맵에 흑백만 있어야 합니다.

## <a name="optimizations"></a>최적화

Windows Mixed Reality 홈 일련의 사용자 지정 확장을 사용 하 여 정의 하는 핵심 glTF 사양 기반 최적화를 제공 합니다. 이러한 최적화는 Windows 버전에 필요한 < = 1709 및 최신 버전의 Windows에서 것이 좋습니다. 사용 하 여 모든 glTF 2.0 모델을 쉽게 최적화할 수 있습니다 합니다 [Windows 혼합 현실 자산 변환기 GitHub에서 사용할 수 있는](https://github.com/Microsoft/glTF-Toolkit/releases)합니다. 이 도구는 올바른 질감 압축 및 아래에 지정 된 최적화를 수행 합니다. 일반 용도 WindowsMRAssetConverter를 사용 하 여 권장 되지만 환경 보다 자세히 제어 해야 하 고 최적화 하는 파이프라인을 빌드 하려는 경우 다음 참조할 수 있습니다 아래 자세한 사양입니다.  

### <a name="materials"></a>자료

자산 로드 혼합 현실 환경 Windows MR에서에서 시간을 개선 하기 위해이 섹션에 정의 된 스키마를 압축 하는 질감에 따라 압축 하는 압축 된 DDS 질감 렌더링을 지원 합니다. DDS 질감은 사용 하 여 참조 되는 [MSFT_texture_dds 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)합니다. 질감 압축은 것이 좋습니다. 

#### <a name="hololens"></a>HoloLens

혼합된 현실 HoloLens 기반 환경을 질감 압축 사양을 사용 하 여 2 질감 설치 프로그램을 사용 하 여 압축을 예상 합니다.
<br>

|  glTF 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 초록 (R) 파랑 (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  보통 (RG), (B)를 거친 금속 (A) | 


DDS 질감을 압축 하는 경우 각 맵에서 다음 압축 될 수 있습니다.
<br>

|  질감  |  압축 예상된 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>몰입 형 (VR) 헤드셋

Windows Mixed Reality 환경을 몰입 형 (VR) 헤드셋 PC 기반 질감 압축 사양을 사용 하 여 질감 3 설치 프로그램을 사용 하 여 압축 예상:

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  glTF 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 초록 (R) 파랑 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R)를 거친 (G) 금속 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  보통 (RG) | 

DDS 질감을 압축 하는 경우 각 맵에서 다음 압축 될 수 있습니다.
<br>

|  질감  |  압축 예상된 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  glTF 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 초록 (R) 파랑 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Roughness (R), 금속 (G), 폐색 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  보통 (RG) | 

DDS 질감을 압축 하는 경우 각 맵에서 다음 압축 될 수 있습니다.
<br>

|  질감  |  압축 예상된 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>추가 메시 LODs

Windows MR 기 하 도형 노드 LODs를 사용 하 여 3D 모델에 다른 수준의 세부 정보 화면 검사에 따라 렌더링. 이 기능은 기술적으로 필수는 동안 모든 자산에 대 한는 것이 좋습니다. 현재 Windows 3 수준의 세부 정보를 지원합니다. LOD 기본값인 최고 품질을 나타내는 0입니다. 다른 LODs 예: 1, 2 및 get 점진적으로 낮은 품질에서 순차적으로 번호가 지정 됩니다. 합니다 [Windows Mixed Reality 자산 변환기](https://github.com/Microsoft/glTF-Toolkit/releases) 여러 glTF 모델을 수락 하 고 유효한 LOD 수준 사용 하 여 단일 자산에 병합 하 여이 LOD 사양을 충족 하는 자산 생성을 지원 합니다. 다음 표에서 예상된 LOD 순서 및 삼각형 목표를 설명합니다.
<br>

|  LOD 수준  |  권장 되는 삼각형 수  |  최대 삼각형 수 | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

LODs를 항상 사용 하는 경우에 3 LOD 수준을 지정 합니다. LODs 누락 된 모델에 누락 된 LOD 수준 LOD 시스템 스위치로 예기치 않게 렌더링 되지 발생 합니다. 2.0 glTF 현재 지원 하지 않습니다 LODs core 사양의 일부분으로 합니다. LODs 따라서 정의 되어야 합니다는 [MSFT_LOD 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)합니다.

### <a name="screen-coverage"></a>화면 검사

LODs는 Windows Mixed Reality 각 LOD 설정 화면 검사 값에 의해 구동 시스템을 기반으로 표시 됩니다. 화면 공간의 큰 부분이 현재 사용 되는 개체는 더 높은 세밀도 수준에 표시 됩니다. 화면 검사 core glTF 2.0 사양의 일부 아니며 MSFT_ScreenCoverage의 "기타" 섹션에서 사용 하 여 지정 해야 합니다 [MSFT_lod 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)합니다.
<br>

|  LOD 수준  |  권장 되는 범위  |  기본 범위 | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  .5 | 
|  LOD 1 |  아래에서 50%-20%  |  .2 | 
|  LOD 2 |  아래에 있는 20% 1%  |  .01 | 
|  LOD 4  |  아래에서 1%  |  - | 

## <a name="animation-guidelines"></a>애니메이션 지침

> [!NOTE]
> 이 기능은의 일부로 추가 되었습니다 [Windows 10 2018 년 4 월 업데이트](release-notes-april-2018.md)합니다. 그러나 이러한 애니메이션의 재생 되지 것입니다 Windows의 이전 버전에서는 여전히 로드이 문서의 지침에 따라 작성 하는 경우.  

혼합된 현실 홈 HoloLens 및 몰입 형 (VR) 헤드셋 애니메이션된 glTF 개체를 지원합니다. 모델에서 애니메이션 트리거 하려는 경우에 glTF 형식에 애니메이션 맵 확장을 사용 해야 합니다. 이 확장을 사용 하면 전 세계의 사용자 현재 상태에 따라 glTF 모델에서 애니메이션 트리거, 사용자에서 검색 하는 동안 또는 개체에 가까운 경우 애니메이션을 예를 들어 트리거를 수행할 수 있습니다. GlTF 개체에 애니메이션 트리거를 정의 하지 않는 경우 애니메이션 다시 재생 되지 않습니다. 아래 섹션에서는 모든 애니메이션된 glTF 개체를이 트리거를 추가 하기 위한 하나의 워크플로 설명 합니다.

### <a name="tools"></a>도구
먼저 이미 이러한 권한이 없는 경우에 다음 도구를 다운로드 합니다. 이러한 도구는 쉽게 glTF 모델을 열고, 미리, 변경 및 glTF 또는.glb 다시 저장 합니다.
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Visual Studio Code 용 glTF 도구](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>열고 모델을 미리 보기
편집기 창에.glTF 파일을 끌어 VSCode에서 glTF 모델을 열어 시작 합니다. .glTF 대신.glb 있다면 파일에 다운로드 한 glTF 도구 추가 기능을 사용 하 여 VSCode를 가져올 수 있습니다. "보기-> 명령 팔레트"로 이동 하 고 그런 다음 명령 팔레트에서 "glTF"를 입력 하기 시작 하 고 선택 "glTF: 에서 가져오기 glb "를 사용 하 여.glb 가져올 파일 선택 상자가 표시 됩니다. 

GlTF 모델 연 후에 JSON 편집기 창에 표시 됩니다. 참고를 사용 하 여 라이브 3D 뷰어에서 모델을 미리 볼 수는 파일 이름을 마우스 오른쪽 단추로 클릭 하 고 선택 하 여는 "glTF: 3D 모델을 미리 보기"명령 바로 가기를 마우스 오른쪽 단추로 클릭 합니다. 

### <a name="adding-the-triggers"></a>트리거 추가
애니메이션 트리거 glTF 모델 애니메이션 맵 확장을 사용 하 여 JSON에 추가 됩니다. 애니메이션 맵 확장은 공개적으로 문서화 [여기 GitHub에서](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (참고: 이 초안 확장). 모델 편집기에서 glTF 파일의 끝에만 스크롤에 확장을 추가 및 아직 없는 경우 파일에 "extensionsUsed" 및 "extensions" 블록을 추가 합니다. "ExtensionsUsed" 섹션에서는 "EXT_animation_map" 확장에 대 한 참조를 추가 하 고 "extensions" 블록의 모델의 애니메이션에 매핑을 추가 됩니다.

설명 했 듯이 [사양에](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 애니메이션은 애니메이션 인덱스의 배열 하는 "애니메이션" 목록에서 "의미 체계" 문자열을 사용 하 여 트리거를 정의 합니다. 아래 예제에서는 지정 했기 때문에 사용자 개체에서 gazing는 동안 재생할 애니메이션 합니다.

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
다음 애니메이션 트리거 의미 체계는 Windows Mixed Reality 홈에서 지원 됩니다.  
* "ALWAYS": 지속적으로 애니메이션 반복
* "HELD": 전체 기간 동안 반복 개체 놓은 합니다.
* "GAZE": 개체를 조회 하는 동안 반복
* "근접성": 뷰어는 개체에 가까이 있는 반복
* "가리키고" 있습니다. 사용자가 개체를 가리키는 동안 반복

### <a name="saving-and-exporting"></a>저장 및 내보내기
한 번 glTF로 직접 저장할 수 있습니다 glTF 모델 변경 내용을 만들었습니다 또는 마우스 오른쪽 단추로 클릭할 수 선택한 편집기에서 파일의 이름을 "glTF: GLB (이진 파일)로 내보내기 "를.glb을 대신 내보내려면 합니다. 

### <a name="restrictions"></a>Restrictions
애니메이션 20 분 보다 길 수 없습니다 및 이상 36,000 키프레임을 (30FPS에서 20 분)을 포함할 수 없습니다. 또한 morph 대상 기반을 사용 하는 경우 애니메이션을 초과 하지 8192 morph 대상 꼭 짓 점 미만입니다. 이러한 개수는 차이로 애니메이션이 적용 된 자산을 Windows Mixed Reality 집에서 지원 되지 않는 수를 초과 합니다. 

|기능|최대값|
|-----|-----|
|Duration|20분|
|키 프레임|36,000| 
|Morph 대상 꼭 짓 점|8192|

## <a name="gltf-implementation-notes"></a>glTF 구현 참고 사항
Windows MR 뒤집기 기 하 도형 음수 눈금을 사용 하 여 지원 하지 않습니다. 음수 눈금은 발생 visual 아티팩트를 사용 하 여 기 하 도형입니다.

GlTF 자산 장면 특성을 사용 하 여 Windows MR에서 렌더링할 기본 장면을를 가리켜야 합니다. 또한 Windows MR glTF 로더를 이전 합니다 [Windows 10 2018 년 4 월 업데이트](release-notes-april-2018.md) **필요** 접근자:
* 최소 및 최대 값이 있어야 합니다.
* 스칼라 형식 componentType UNSIGNED_SHORT (5123) 또는 UNSIGNED_INT (5125) 이어야 합니다.
* 형식 v e c 2 및 VEC3 componentType FLOAT (5126) 이어야 합니다.

다음과 같은 재질 핵심 glTF 2.0 사양에서 사용 되지만 필요 하지 않습니다.
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: Dds에 저장 된 질감을 가리켜야 합니다.
* emissiveTexture: Dds에 저장 된 질감을 가리켜야 합니다.
* emissiveFactor
* alphaMode

다음 material 속성은 핵심 사양에서 무시 됩니다.
* 모든 다중 UVs
* metalRoughnessTexture: 아래에 정의 된 액세스에 최적화 된 Microsoft 질감 압축을 대신 사용 해야 합니다.
* normalTexture: 아래에 정의 된 액세스에 최적화 된 Microsoft 질감 압축을 대신 사용 해야 합니다.
* normalScale
* occlusionTexture: 아래에 정의 된 액세스에 최적화 된 Microsoft 질감 압축을 대신 사용 해야 합니다.
* occlusionStrength

기본 모드 선 및 점의 Windows MR 지원 하지 않습니다. 

UV 꼭 짓 점 특성이 한 개만 지원 됩니다.

## <a name="additional-resources"></a>추가 자료
* [glTF 내보내기 도구 및 변환기](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF 도구 키트](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 사양](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD 확장 사양](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [혼합 현실 질감 압축 확장 사양 PC](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens 혼합 현실 질감 압축 확장 사양](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 질감 glTF 확장 사양](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>참조

* [3D 앱 시작 관리자(UWP 앱) 구현](implementing-3d-app-launchers.md)
* [3D 앱 시작 관리자(Win32 앱) 구현](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
