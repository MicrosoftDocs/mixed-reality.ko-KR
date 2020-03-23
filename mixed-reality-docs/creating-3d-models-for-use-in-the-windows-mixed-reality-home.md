---
title: 홈에서 사용할 3D 모델 만들기
description: Windows Mixed Reality 홈에서 HoloLens 및 모던 (VR) 헤드셋 모두에 사용할 수 있는 Asset 요구 사항 및 3D 모델 제작 지침
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, 모델링, 모델링 지침, 자산 요구 사항, 제작 지침, 시작 관리자, 3D 시작 관리자, 질감, 재질, 복잡도, 삼각형, 메시, 다각형, polycount, 제한
ms.openlocfilehash: 536fd9bc2002d679ee3bf73d5c906b84c51e5d46
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375630"
---
# <a name="create-3d-models-for-use-in-the-home"></a>홈에서 사용할 3D 모델 만들기

[Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 은 사용자가 응용 프로그램을 시작 하기 전에 수행 하는 시작 지점입니다. Windows Mixed Reality 헤드셋의 응용 프로그램을 디자인 하 여 [3d 모델을 앱 시작 관리자로](implementing-3d-app-launchers.md) 활용 하 고 [3d 딥 링크를 앱 내에서 windows Mixed reality 홈에 배치할](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) 수 있습니다. 이 문서에서는 Windows Mixed Reality 홈과 호환 되는 3D 모델을 만드는 방법에 대 한 지침을 설명 합니다.

## <a name="asset-requirements-overview"></a>자산 요구 사항 개요
Windows Mixed Reality의 3D 모델을 만들 때 모든 자산이 충족 해야 하는 몇 가지 요구 사항이 있습니다. 
1. [내보내기](#exporting-models) -자산은 .bb 파일 형식으로 배달 되어야 합니다 (이진 글 tf).
2. [모델링](#modeling-guidelines) -자산은 10k 삼각형 미만 이어야 하 고, 64 개 미만의 노드 및 32 submeshes LOD를 포함 해야 합니다.
3. [재질](#material-guidelines) -질감은 4096 x 4096 보다 클 수 없으며, 가장 작은 밉 지도는 두 차원에서 4 보다 크지 않아야 합니다.
4. [애니메이션](#animation-guidelines) -애니메이션은 30 fps (36000 키 프레임)에서 20 분 보다 길 수 없으며, < = 8192 모핑 대상 꼭 짓 점을 포함 해야 합니다.
5. [최적화](#optimizations) - [Windowsmrassetconverter](https://github.com/Microsoft/glTF-Toolkit/releases)를 사용 하 여 자산을 최적화 해야 합니다. 이는 **WINDOWS Os 버전 < = 1709에 필요** 하며 windows os 버전 > = 1803에 권장 됩니다.

이 문서의 나머지 부분에는 이러한 요구 사항에 대 한 자세한 개요와 모델이 Windows Mixed Reality 홈에서 잘 작동 하도록 하기 위한 추가 지침이 포함 되어 있습니다. 

## <a name="detailed-guidance"></a>자세한 지침

### <a name="exporting-models"></a>모델 내보내기

Windows Mixed Reality 홈에는 포함 된 이미지와 이진 데이터를 포함 하는 .bb 파일 형식을 사용 하 여 3D 자산이 제공 될 것으로 예상 됩니다. 글 2는 Khronos 그룹에서 유지 관리 되는 3D 자산 배달에 대 한 무료 무료 오픈 표준 인 글 지에 대 한 이진 버전입니다. 인 글 Tf는 상호 운용할 수 있는 3D 콘텐츠에 대 한 업계 표준으로 진화 하므로 Microsoft는 Windows 앱과 환경에서 형식을 지원 합니다. [지원 되는 내보내기 및 변환기의 목록을](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) 찾을 수 있는 경우, 이전에는 글 tf 자산을 만들지 않은 경우 github 작업 그룹 github 페이지에서 찾을 수 있습니다.  

### <a name="modeling-guidelines"></a>모델링 지침

Windows에서는 혼합 현실 홈 환경과의 호환성을 보장 하기 위해 다음 모델링 지침을 사용 하 여 자산을 생성할 것으로 예상 합니다. 선택한 프로그램에서 모델링할 때 다음 권장 사항 및 제한 사항에 유의 하세요.
1. 위쪽 축을 "Y"로 설정 해야 합니다.
2. 자산은 양의 Z 축에 "전달" 해야 합니다.
3. 모든 자산은 장면 원점 (0, 0, 0)의 그라운드 평면에서 빌드되어야 합니다.
4. 자산을 전 세계 규모에서 작성할 수 있도록 작업 단위를 미터 및 자산으로 설정 해야 합니다.
5. 모든 메시를 결합할 필요는 없지만 리소스 제한 장치를 대상으로 하는 경우에는 권장 됩니다.
6. 모든 메시는 전체 자산에 대해 1 개의 질감 집합만 사용 하 여 1 개의 재질을 공유 해야 합니다.
7. UVs는 0-1 공간의 사각형 정렬로 배치 되어야 합니다. 질감이 허용 되지만 바둑판식으로 배열 하지 않습니다.
8. 다중 UVs는 지원 되지 않습니다.
9. 양면 자료는 지원 되지 않습니다.

### <a name="triangle-counts-and-levels-of-detail-lods"></a>삼각형 개수 및 세부 정보 수준 (LODs)

Windows Mixed Reality 홈에서는 1만 삼각형이 넘는 모델을 지원 하지 않습니다. 이 개수를 초과 하지 않도록 내보내기 전에 메시를 삼각 측량 것이 좋습니다. 또한 Windows MR은 성능 및 고화질 환경을 보장 하기 위해 선택적 geometry (세부 정보)를 지원 합니다. [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) 는 세 가지 버전의 모델을 단일 .bb 모델에 결합 하는 데 도움이 됩니다. Windows는 모델이 차지 하 고 있는 화면 크기에 따라 표시할 LOD를 결정 합니다. 3 개의 LOD 수준만 지원 되는 권장 삼각형 개수는 다음과 같습니다.
<br>

|  LOD 수준  |  권장 삼각형 수  |  최대 삼각형 수 | 
|------|------|------|
|  LOD 0 |  1만 |  1만 | 
|  LOD 1 |  5000  |  1만 | 
|  LOD 2 |  2500  |  1만 | 

### <a name="node-counts-and-submesh-limits"></a>노드 개수 및 하위 메시에 대해 제한
Windows Mixed Reality 홈에서는 64 개 이상의 노드가 있는 모델이 나 LOD 당 32 submeshes을 지원 하지 않습니다. 노드는 장면에서 개체를 [정의 하는 개념입니다.](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) Submeshes는 개체에서 망상의 [기본 형식](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) 배열에 정의 되어 있습니다. 

|  기능 |  설명  |  최대 지원 | 설명서 |
|------|------|------|------|
|  노드 |  개체의 개체 |  LOD 당 64 | [여기](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  모든 망상의 기본 형식 합계 |  LOD 당 32 | [여기](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>재질 지침

이 경우에는 .PBR 금속 황삭 워크플로를 사용 하 여 질감을 준비 해야 합니다. 먼저 Albedo, Normal, 폐색, 금속 및 황삭를 비롯 한 전체 질감 집합을 만듭니다. Windows Mixed Reality는 해상도가 4096x4096 인 질감을 지원 하지만 512x512에서 작성 하는 것이 좋습니다. 또한 아래에 설명 된 내보내기 단계에서 질감에 적용 되는 압축 형식에 대 한 요구 사항은 4의 배수로 해상도에 따라 질감이 작성 되어야 합니다. 마지막으로, 밉 맵 또는 질감을 생성할 때 가장 낮은 밉는 최대 4x4 여야 합니다.
<br>

|  권장 텍스처 크기  |  최대 질감 크기 | 가장 낮은 밉
|----|----|----|
|  512x512  |  4096x4096 | 최대 4x4|

### <a name="albedo-base-color-map"></a>Albedo (기본 색) 맵

조명 정보가 없는 Raw 색입니다. 또한이 지도에는 금속 (금속 지도에 흰색) 및 insulator (금속성 지도의 검정)에 대 한 reflectance 및 확산 정보가 각각 포함 되어 있습니다.

### <a name="normal"></a>일반

탄젠트 공간 법선 지도

### <a name="roughness-map"></a>황삭 지도

개체의 마이크로 표면에 대해 설명 합니다. 흰색 1.0은 황삭 검정 0.0입니다. 이 맵은 가장 많은 문자 (예: 긁힘, 지문, 얼룩, 창 등)를 정확히 설명 하는 자산을 제공 합니다.

### <a name="ambient-occlusion-map"></a>앰비언트 폐색 map

반사를 차단 하는 폐색 조명의 영역을 나타내는 값 눈금 맵

### <a name="metallic-map"></a>금속 지도

항목이 금속 인지 여부를 셰이더에 알립니다. Raw 메탈 = 1.0 흰색 미 설치 = 0.0 black. 먼지와 같이 raw 금속을 덮고 있는 항목을 나타내는 회색 값을 변환할 수 있지만 일반적으로이 맵은 검정과 흰색 이어야 합니다.

## <a name="optimizations"></a>강력한

Windows Mixed Reality 홈은 사용자 지정 확장 프로그램을 사용 하 여 정의 된 핵심 글 트 Tf 사양 위에 일련의 최적화를 제공 합니다. 이러한 최적화는 Windows 버전 < = 1709에 필요 하며 최신 버전의 Windows에서 권장 됩니다. [GitHub에서 제공 되는 Windows Mixed Reality 자산 변환기](https://github.com/Microsoft/glTF-Toolkit/releases)를 사용 하 여 모든 글 2.0 모델을 쉽게 최적화할 수 있습니다. 이 도구는 아래 지정 된 대로 올바른 질감 압축 및 최적화를 수행 합니다. 일반적인 사용을 위해 WindowsMRAssetConverter를 사용 하는 것이 좋습니다. 그러나 환경을 보다 세부적으로 제어 해야 하 고 사용자 고유의 최적화 파이프라인을 빌드 하려는 경우 아래 상세 사양을 참조할 수 있습니다.  

### <a name="materials"></a>자재

혼합 현실 환경에서 자산 로드 시간을 개선 하기 위해 Windows MR은이 섹션에 정의 된 질감 압축 체계에 따라 압축 된 DDS 질감 렌더링을 지원 합니다. DDS 질감이 [MSFT_texture_dds 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)을 사용 하 여 참조 됩니다. 텍스처를 압축 하는 것이 좋습니다. 

#### <a name="hololens"></a>HoloLens

HoloLens 기반 혼합 현실에서는 다음 압축 사양을 사용 하 여 2 질감 설정을 사용 하 여 질감이 압축 될 것으로 간주 합니다.
<br>

|  인 글 Tf 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 녹색 (G), 파랑 (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  보통 (RG), 황삭 (B), 금속 (A) | 


DDS 텍스처를 압축 하는 경우 각 맵에 다음과 같은 압축이 필요 합니다.
<br>

|  질감  |  예상 압축 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>모던 (VR) 헤드셋

모던 (VR) 헤드셋을 위한 PC 기반 Windows 혼합 현실 환경에서는 다음 압축 사양을 사용 하 여 3 질감 설정을 사용 하 여 질감을 압축할 것으로 간주 합니다.

##### <a name="windows-os--1803"></a>Windows OS > = 1803

<br>

|  인 글 Tf 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 녹색 (G), 파랑 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  폐색 (R), 황삭 (G), 금속 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  보통 (RG) | 

DDS 텍스처를 압축 하는 경우 각 맵에 다음과 같은 압축이 필요 합니다.
<br>

|  질감  |  예상 압축 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS < = 1709
<br>

|  인 글 Tf 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 녹색 (G), 파랑 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  황삭 (R), 금속 (G), 폐색 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  보통 (RG) | 

DDS 텍스처를 압축 하는 경우 각 맵에 다음과 같은 압축이 필요 합니다.
<br>

|  질감  |  예상 압축 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>메시 LODs 추가

Windows MR은 geometry 노드 LODs를 사용 하 여 화면 검사에 따라 다양 한 세부 수준으로 3D 모델을 렌더링 합니다. 이 기능은 기술적으로 필수는 아니지만 모든 자산에 대해 적극 권장 됩니다. 현재 Windows에서 3 가지 세부 수준을 지원 합니다. 기본 LOD는 최고 품질을 나타내는 0입니다. 다른 LODs는 순차적으로 번호가 매겨집니다. 예를 들어 1, 2 및 점진적으로 품질이 낮아집니다. [Windows Mixed Reality 자산 변환기](https://github.com/Microsoft/glTF-Toolkit/releases) 는 여러 가지 영향을 받는 tf 모델을 수락 하 고 유효한 LOD 수준의 단일 자산에 병합 하 여이 LOD 사양을 충족 하는 자산 생성을 지원 합니다. 다음 표에서는 예상 되는 LOD 순서 지정 및 삼각형 대상에 대해 간략하게 설명 합니다.
<br>

|  LOD 수준  |  권장 삼각형 수  |  최대 삼각형 수 | 
|-------|-------|-------|
|  LOD 0 |  1만 |  1만 | 
|  LOD 1 |  5000  |  1만 | 
|  LOD 2 |  2500  |  1만 | 

LODs를 사용 하는 경우 항상 3 LOD 수준을 지정 합니다. LOD 시스템이 누락 된 LOD 수준으로 전환 될 때 LODs가 누락 되 면 모델이 예기치 않게 렌더링 되지 않습니다. 글 Tf 2.0은 현재 핵심 사양의 일부로 LODs를 지원 하지 않습니다. 따라서 LODs는 [MSFT_LOD 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)을 사용 하 여 정의 해야 합니다.

### <a name="screen-coverage"></a>화면 검사

LODs는 각 LOD에 설정 된 화면 범위 값으로 구동 되는 시스템에 따라 Windows Mixed Reality에 표시 됩니다. 현재 화면 공간을 더 많이 사용 하는 개체는 더 높은 LOD 수준에 표시 됩니다. 화면 검사는 핵심 글 글 2.0 사양의 일부가 아니므로 [MSFT_lod 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)의 "스페셜" 섹션에서 MSFT_ScreenCoverage을 사용 하 여 지정 해야 합니다.
<br>

|  LOD 수준  |  권장 범위  |  기본 범위 | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  .5 | 
|  LOD 1 |  50%-20% 미만  |  .2 | 
|  LOD 2 |  20%-1% 미만  |  .01 | 
|  LOD 4  |  1% 미만  |  - | 

## <a name="animation-guidelines"></a>애니메이션 지침

> [!NOTE]
> 이 기능은 [Windows 10 4 월 2018 업데이트](release-notes-april-2018.md)의 일부로 추가 되었습니다. 이전 버전의 Windows에서는 이러한 애니메이션이 재생 되지 않지만이 문서의 지침에 따라 작성 된 경우에도 계속 로드 됩니다.  

혼합 현실 홈은 HoloLens 및 몰입 형 (VR) 헤드셋에서 애니메이션 된 인 글 하는 개체를 지원 합니다. 모델에 대 한 애니메이션을 트리거하려면 애니메이션 맵 확장을 지 원하는 Tf 형식으로 사용 해야 합니다. 이 확장을 사용 하면 전 세계 사용자를 기준으로 하 여 인 사이트에서 애니메이션을 트리거할 수 있습니다. 예를 들어, 사용자가 개체에 가까이 있거나 보는 동안 애니메이션을 트리거할 수 있습니다. Tf 개체에 애니메이션이 있지만 트리거를 정의 하지 않으면 애니메이션이 재생 되지 않습니다. 다음 섹션에서는 이러한 트리거를 애니메이션 된 모든 개체에 추가 하는 한 가지 워크플로를 설명 합니다.

### <a name="tools"></a>도구
먼저, 다음 도구가 아직 없는 경우 다운로드 합니다. 이러한 도구를 사용 하면 쉽게 모든 프로그램을 열고, 미리 보고, 변경 하 고,
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Visual Studio Code에 대 한 글 서 용 Tf 도구](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>모델 열기 및 미리 보기
먼저 파일을 편집기 창으로 끌어 VSCode에서 글 글 Tf 모델을 엽니다. .glTF 파일 대신 .glb가 있는 경우 다운로드한 glTF 도구 추가기능을 사용하여 VSCode로 가져올 수 있습니다. "보기-> 명령 팔레트"로 이동 하 여 명령 팔레트에 "글 제 Tf"를 입력 하 고 "글 제 Tf"를 선택 합니다. 을 (를) 사용 하 여을 가져올 수 있는 파일 선택기를 표시 하는 &에서 가져옵니다. 

인 글 어 어 모델을 열면 편집기 창에 JSON이 표시 됩니다. 파일 이름을 마우스 오른쪽 단추로 클릭 하 고 "글 Tf:를 선택 하 여 라이브 3D 뷰어에서 모델을 미리 볼 수도 있습니다. 3D 모델 미리 보기 "명령 바로 가기 메뉴를 마우스 오른쪽 단추로 클릭 합니다. 

### <a name="adding-the-triggers"></a>트리거 추가
애니메이션 트리거는 애니메이션 맵 확장을 사용 하 여 글 지 Tf 모델 JSON에 추가 됩니다. 애니메이션 맵 확장은 [GitHub에서](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 공개적으로 설명 됩니다 (참고: 이는 초안 확장입니다. 모델에 확장을 추가 하려면 편집기에서 인 글 Tf 파일의 끝으로 스크롤하고 "extensionsUsed" 및 "extensions" 블록을 파일에 추가 합니다 (아직 없는 경우). "ExtensionsUsed" 섹션에서 "EXT_animation_map" 확장에 대 한 참조를 추가 하 고 "extensions" 블록에 모델의 애니메이션에 대 한 매핑을 추가 합니다.

[사양에 설명 된](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 것 처럼 애니메이션 인덱스의 배열인 "애니메이션" 목록에서 "의미 체계" 문자열을 사용 하 여 애니메이션을 트리거하는 항목을 정의 합니다. 아래 예제에서는 사용자가 개체에서 gazing 때 애니메이션을 재생 하도록 지정 했습니다.

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
* "항상": 애니메이션을 지속적으로 반복
* "보관": 전체 기간 동안 반복 되는 개체는 grabbed입니다.
* "응시": 개체를 조회 하는 동안 루프가 반복 됩니다.
* "근접": 뷰어가 개체 근처에 있는 동안 반복 됩니다.
* "가리키기": 사용자가 개체를 가리키는 동안 반복 됩니다.

### <a name="saving-and-exporting"></a>저장 및 내보내기
글 어 어 모델을 변경한 후에는 해당 모델을 직접 나 편집기에서 파일 이름을 마우스 오른쪽 단추로 클릭 하 고 "글 어:를 선택할 수 있습니다. 대신 글 b (이진 파일)로 내보내. 

### <a name="restrictions"></a>Restrictions
애니메이션은 20 분 보다 길면 안 되며 36000 개 보다 많은 키 프레임을 포함할 수 없습니다 (20 분 (30FPS)). 또한 모핑 대상 기반 애니메이션을 사용 하는 경우 8192 모핑 대상 꼭 짓 점을 초과 하지 않습니다. 이러한 횟수를 초과 하면 Windows Mixed Reality 홈에서 애니메이션 자산이 지원 되지 않습니다. 

|기능|최대값|
|-----|-----|
|Duration|20분|
|키프레임에서|36,000| 
|모핑 대상 꼭 짓 점|8192|

## <a name="gltf-implementation-notes"></a>글 서 Tf 구현 참고 사항
Windows MR은 음수 눈금을 사용 하는 기 하 도형 이동을 지원 하지 않습니다. 배율이 음수인 기 하 도형은 시각적 아티팩트가 될 가능성이 높습니다.

Windows MR에서 렌더링 되는 장면 특성을 사용 하 여 글 글 Tf 자산은 기본 장면을 가리켜야 합니다. 또한 [windows 10 4 월 2018 업데이트](release-notes-april-2018.md) 이전의 Windows MR 글 tf 로더는 접근자를 **요구** 합니다.
* Min 및 max 값이 있어야 합니다.
* 스칼라 형식은 componentType UNSIGNED_SHORT (5123) 또는 UNSIGNED_INT (5125) 여야 합니다.
* VEC2 및 VEC3 형식은 componentType FLOAT 여야 합니다 (5126).

다음 재질 속성은 core로 된 Tf 2.0 사양에서 사용 되지만 반드시 필요한 것은 아닙니다.
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: Dds에 저장 된 질감을 가리켜야 합니다.
* emissiveTexture: Dds에 저장 된 질감을 가리켜야 합니다.
* emissiveFactor
* alphaMode

다음 재질 속성은 코어 사양에서 무시 됩니다.
* 모든 다중 UVs
* metalRoughnessTexture: 아래에 정의 된 Microsoft 최적화 된 질감 압축을 대신 사용 해야 합니다.
* normalTexture: 아래에 정의 된 Microsoft 최적화 된 질감 압축을 대신 사용 해야 합니다.
* normalScale
* occlusionTexture: 아래에 정의 된 Microsoft 최적화 된 질감 압축을 대신 사용 해야 합니다.
* occlusionStrength

Windows MR은 기본 모드 선 및 요소를 지원 하지 않습니다. 

단일 UV vertex 특성만 지원 됩니다.

## <a name="additional-resources"></a>추가 자료
* [글 내보내기 및 변환기](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [글 Tf Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [글 Tf 2.0 사양](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft 글 Tf LOD 확장 사양](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC 혼합 현실 질감 압축 확장 사양](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens 혼합 현실 질감 압축 확장 사양](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 질감 및 Tf 확장 사양](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>참고 항목

* [3D 앱 시작 관리자(UWP 앱) 구현](implementing-3d-app-launchers.md)
* [3D 앱 시작 관리자(Win32 앱) 구현](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
