---
title: 자산 생성 프로세스
description: 혼합 현실 환경에 대 한 자산을 만드는 방법에 대 한 지침입니다.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 자산, 생성, 프로세스, 예산, 다각형, 질감, 셰이더, 성능
ms.openlocfilehash: fb8266a018e11a8fb944819a0cac5ace38f2cb25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437008"
---
# <a name="asset-creation-process"></a>자산 생성 프로세스

Windows Mixed Reality는 Microsoft에서 DirectX로 만든 수십 년의 투자를 기반으로 합니다. 즉, 개발자가 3D 그래픽을 빌드하는 데 사용 하는 모든 경험과 기술은 HoloLens에서 계속 가치가 있습니다.

프로젝트에 대해 생성 하는 자산은 많은 모양과 양식으로 제공 됩니다. 이러한 이미지는 일련의 질감/이미지, 오디오, 비디오, 3D 모델 및 애니메이션으로 구성 될 수 있습니다. 프로젝트에서 사용 되는 다양 한 종류의 자산을 만드는 데 사용할 수 있는 모든 도구를 시작할 수 없습니다. 이 문서에서는 3D 자산 생성 방법에 초점을 둡니다.

![개념, 생성, 통합 및 반복 흐름](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*개념, 생성, 통합 및 반복 흐름*

## <a name="things-to-consider"></a>고려 사항

원하는 경험을 살펴보면 최상의 환경을 만들기 위해 사용할 수 있는 **예산** 으로 생각 하면 됩니다. 자산에 사용 되는 **다각형** 의 수 나 **재료의 유형** 에 대 한 하드 제한이 필요 하지는 않지만 예산 면에서 더 많이 사용 됩니다.

사용자 환경에 대 한 예제 예산은 다음과 같습니다. 성능은 일반적으로 단일 실패 지점이 아니라 천 단위 컷으로 인 한 것입니다.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>가치</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 메모리</th>
</tr><tr>
<td> 다각형</td><td> 0</td><td> 5</td><td> 5-10</td>
</tr><tr>
<td> 텍스처</td><td> 5</td><td> 15</td><td>25%</td>
</tr><tr>
<td> 셰이더</td><td> 15</td><td> 35%</td><td> 0</td>
</tr><tr>
<td> <b>움직임</b></td><td></td><td></td><td></td>
</tr><tr>
<td> 물리</td><td> 5</td><td> 15</td><td> 0</td>
</tr><tr>
<td> 실시간 조명</td><td> 5-10</td><td> 0</td><td> 0</td>
</tr><tr>
<td> 미디어 (오디오/비디오)</td><td> -</td><td> 15</td><td> 25%</td>
</tr><tr>
<td> 스크립트/논리</td><td> 25%</td><td> 0</td><td> 5</td>
</tr><tr>
<td> 일반 오버 헤드</td><td> 5</td><td> 5</td><td> 5</td>
</tr><tr>
<td> <b>개수</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**총 자산 수**
* 장면에 활성 상태인 자산이 몇 개입니까?

**자산의 복잡성**
* 삼각형/polygon은 몇 개입니까?
* 셰이더는 얼마나 복잡 한가요? Mixed Reality 도구 키트를 사용 하는 경우 [혼합 현실 도구 키트 표준 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 를 사용 하 여 셰이더 복잡성을 줄이는 것이 좋습니다.

개발자와 아티스트는 모두 장치와 그래픽 엔진의 기능을 고려해 야 합니다. Microsoft HoloLens에는 장치에 모든 컴퓨팅 및 그래픽이 내장 되어 있습니다. 개발자가 모바일 플랫폼에서 찾을 수 있는 기능을 공유 합니다.

자산에 대 한 생성 프로세스는 [holographic 장치 또는 몰입 형 장치](mixed-reality.md#the-mixed-reality-spectrum)에 대 한 환경을 대상으로 하는지 여부에 관계 없이 동일 합니다. 가장 중요 한 점은 위에서 언급 한 것과 같이 크기를 조정 하는 것입니다 .이는 혼합 현실에서 실제 세계를 볼 수 있기 때문에 환경에 따라 올바른 규모를 유지 해야 한다는 것입니다. 

## <a name="authoring-assets"></a>자산 제작

프로젝트에 대 한 자산을 가져오는 방법으로 시작 합니다.
1. 자산 만들기 (제작 도구 및 개체 캡처)
2. 자산 구입 (온라인으로 자산 구입)
3. 자산 포팅 (기존 자산 가져오기)
4. 자산 아웃소싱 (타사에서 자산 가져오기)

### <a name="creating-assets"></a>자산 만들기

**작성 도구**<br>
먼저 다양 한 방법으로 고유한 자산을 만들 수 있습니다. 3D 아티스트는 여러 응용 프로그램 및 도구를 사용 하 여 **메시**, **질감**및 **재질**로 구성 된 모델을 만듭니다. 그런 다음 응용 프로그램에서 사용 하는 그래픽 엔진 (예:)에서 가져오거나 사용할 수 있는 파일 형식으로 저장 됩니다 **. FBX** 또는 **입니다. OBJ**. 선택한 그래픽 엔진에서 지원 되는 모델을 생성 하는 모든 도구는 **HoloLens**에서 작동 합니다. 3D 아티스트 중에는 [Autodesk의 Maya](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 를 사용 하도록 선택 하 고,이를 사용 하 여 자산이 생성 되는 방식을 변환할 수 있습니다. 신속 하 게 작업 하려면 Windows와 함께 제공 되는 [3D 작성기](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 를 사용 하 여 내보낼 수도 있습니다. 응용 프로그램에서 사용할 OBJ입니다.

**개체 캡처**<br>
3D에서 개체를 캡처하는 옵션도 있습니다. 3D로 inanimate 개체를 캡처하고 디지털 콘텐츠 생성 소프트웨어를 사용 하 여 편집 하는 것은 3D 인쇄로 점점 더 인기 있습니다. **Kinect 2** 센서 및 [3d 작성기](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 를 사용 하 여 캡처 기능을 사용 하 여 실제 개체에서 자산을 만들 수 있습니다. 이는 함께 연결 하는 여러 이미지를 처리 하 고 메시와 질감을 사용 하 여 **photogrammetry** 와 동일한 작업을 수행 하는 [도구 모음](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) 이기도 합니다.

### <a name="purchasing-assets"></a>자산 구매

또 다른 뛰어난 옵션은 사용자 환경에 대 한 자산을 구입 하는 것입니다. [Unity Asset Store](https://www.assetstore.unity3d.com/) 또는 [TurboSquid](https://www.turbosquid.com/) 와 같은 서비스를 통해 사용할 수 있는 자산이 있습니다.

타사에서 자산을 구입 하는 경우 항상 다음을 확인 해야 합니다.
* **Poly 수는 무엇 인가요?**
  * 예산 내에 적합 한가요?
* **모델에 대 한 세부 정보 (LODs)가 있나요?**
  * 모델에 대 한 세부 정보를 사용 하 여 성능에 대 한 모델 세부 정보를 확장할 수 있습니다.
* **원본 파일을 사용할 수 있나요?**
  * 일반적으로 [Unity Asset Store](https://www.assetstore.unity3d.com/) 에는 포함 되지 않지만 항상 [TurboSquid](https://www.turbosquid.com/)와 같은 서비스에 포함 됩니다.
  * 원본 파일이 없으면 자산을 수정할 수 없습니다.
  * 제공 된 소스 파일을 3D 도구에서 가져올 수 있는지 확인 합니다.
* **수신 하는 내용 파악**
  * 애니메이션이 제공 되나요?
  * 구매 중인 자산의 콘텐츠 목록을 확인 하세요.

### <a name="porting-assets"></a>자산 포팅

일부 경우에는 원래 다른 장치와 다른 앱을 위해 빌드된 기존 자산을 전달 하 게 됩니다. 대부분의 경우 이러한 자산은 앱에서 사용 하는 그래픽 엔진과 호환 되는 형식으로 변환할 수 있습니다.

HoloLens 응용 프로그램에서 사용할 자산을 이식 하는 경우 다음을 요청 합니다.
* **직접 가져올 수도 있고 다른 형식으로 변환 해야 하나요?** 사용 중인 그래픽 엔진을 사용 하 여 가져오는 형식을 확인 합니다.
* **호환 되는 형식으로 변환 하는 것이 손실 되는 경우** 경우에 따라 세부 정보를 분실 하거나 가져오면 3D authoring tool에서 정리 해야 하는 아티팩트가 발생할 수 있습니다.
* **자산의 삼각형/다각형 수는 무엇 인가요?** 응용 프로그램의 예산에 따라 [Simplygon](https://www.simplygon.com/) 또는 유사한 도구를 사용 하 여 원래 자산의 decimate (procedurally 또는 수동 감소)를 응용 프로그램 예산에 맞게 설정할 수 있습니다.

### <a name="outsourcing-assets"></a>자산 아웃소싱

팀에서 만드는 것 보다 더 많은 자산이 필요한 대규모 프로젝트의 또 다른 옵션은 자산 생성을 아웃소싱 하는 것입니다. 아웃소싱 프로세스에는 자산을 전문적으로 활용 하는 올바른 스튜디오 또는 에이전시를 찾는 과정이 포함 됩니다. 이 옵션은 비용이 가장 많이 드는 옵션 일 수 있지만 가장 유연 하 게 얻을 수 있습니다.
* **요청 하는 내용을 명확 하 게 정의**
  * 최대한 많은 세부 정보 제공
  * Front, side 및 back 개념 이미지
  * 컨텍스트에서 자산을 보여 주는 참조 아트
  * 개체의 눈금 (일반적으로 센티미터 단위로 지정)
* **예산 제공**
  * Poly count 범위
  * 질감 수
  * 셰이더 유형 (Unity 및 HoloLens의 경우 항상 먼저 모바일 셰이더로 기본 지정 해야 함)
* **비용 이해**
  * 변경 요청에 대 한 아웃소싱 정책은 무엇 인가요?

아웃소싱은 프로젝트 타임 라인에 따라 매우 잘 작동 하지만, 처음으로 필요한 자산을 얻을 수 있도록 더 많은 감독이 필요 합니다.
