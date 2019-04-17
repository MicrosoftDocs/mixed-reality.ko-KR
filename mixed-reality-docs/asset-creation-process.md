---
title: 자산 생성 프로세스
description: 혼합된 현실 환경에 대 한 자산을 만드는 방법에 대 한 지침입니다.
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: 자산, 만들기, 프로세스, 예산, 다각형, 텍스처, 셰이더, 성능
ms.openlocfilehash: cec689ab4d44591d2d3e84679c3fe51dba161bc5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604712"
---
# <a name="asset-creation-process"></a>자산 생성 프로세스

Windows Mixed Reality 수십 년 DirectX에 대 한 투자를 기반으로 합니다. 즉, 모든 환경 및 기술을 개발자 3D 구축 그래픽 계속 HoloLens를 사용 하 여 유용할 수 있습니다.

프로젝트에 대해 만든 자산 다양 한 형태와 forms로 제공 됩니다. 일련의 질감/이미지, 오디오, 비디오, 구성 될 수 있습니다 3D 모델 및 애니메이션 합니다. 에서는 프로젝트의 다양 한 유형의 사용 되는 자산을 만드는 데 사용할 수 있는 모든 도구를 시작할 수 없습니다. 이 문서에 대 한 3D 자산 생성 방법에는 살펴볼 것입니다.

![개념, 생성, 통합 및 반복 흐름](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*개념, 생성, 통합 및 반복 흐름*

## <a name="things-to-consider"></a>고려 사항

경우를 만들려고 하는 경험을 살펴보면으로 생각할를 **예산** 최상의 환경을 만들기 위해 소비할 수 있는 합니다. 수에 반드시 하드 제한 없는 **다각형** 또는 **재질 형식 중** 자산 균형점을 찾아야 예산된 집합 보다 에서만 사용 합니다.

환경에 대 한 예에서는 예산은 다음과 같습니다. 성능 아니며 일반적으로 실패 하지만 사망 se 당는 천 절단 하 여 단일 지점
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>자산</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 메모리</th>
</tr><tr>
<td> 다각형</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> 텍스처</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> 셰이더</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> 물리학</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> 실시간 조명</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> 미디어 (오디오/동영상)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> 스크립트/논리</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> 일반 오버 헤드</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>총</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**총 자산**
* 얼마나 많은 자산은 장면에서 활성화?

**자산의 복잡성**
* 얼마나 많은 삼각형 / 다각형?
* 셰이더 얼마나 복잡 기능

개발자 및 아티스트가 장치와 그래픽 엔진의 기능을 고려해 야 합니다. Microsoft HoloLens는 모든 계산 및 그래픽 장치에 기본 제공 합니다. 모바일 플랫폼에서 개발자는 찾기 기능을 공유 합니다.

자산에 대 한 만들기 프로세스에 대 한 환경을 대상으로 하는 여부에 관계 없이 동일를 [holographic 장치 또는 몰입 형 장치](mixed-reality.md#the-mixed-reality-spectrum)합니다. 기본 점은 실제 경험을 기반으로 올바른 눈금을 유지 해야 하는 혼합된 현실에서 볼 수 있으므로 크기 조정 뿐만 아니라 위에서 설명한 것 처럼 장치 기능이 있습니다. 

## <a name="authoring-assets"></a>제작 자산

프로젝트에 대 한 자산을 창출 하는 방법부터 살펴보겠습니다.
1. 자산 (제작 도구 및 개체 캡처) 만들기
2. 자산 (구입 자산 온라인) 구입
3. 포팅 자산 (기존 자산을 수행 합니다.)
4. 아웃소싱 자산 (타사에서 자산 가져오기)

### <a name="creating-assets"></a>자산 만들기

**제작 도구**<br>
먼저 다양 한 가지 방법으로 사용자 고유의 자산을 만들 수 있습니다. 으로 구성 된 모델을 만드는 다양 한 응용 프로그램 및 도구를 사용 하는 3D 아티스트 **메시**, **질감**, 및 **자료**합니다. 와 같은 앱에서 사용 되는 그래픽 엔진에서 사용 하거나 가져올 수 있는 파일 형식으로 저장 됩니다이 **합니다. FBX** 또는 **합니다. OBJ**합니다. 선택한 그래픽 엔진을 지 원하는 모델을 생성 하는 모든 도구 작동 **HoloLens**합니다. 3D artist 간에 많은 사용 하기로 [의 Autodesk Maya에서 HoloLens를 사용할 수 있는 자체](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 변환할 방법은 자산 생성 됩니다. 빠른 작업 참여 하려는 경우 사용할 수도 있습니다 [3D 작성기](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 내보내려면 Windows 함께 제공 되는 합니다. 응용 프로그램에서 사용 하기 위해 OBJ 합니다.

**개체 캡처**<br>
3d에서 개체를 캡처할 옵션 이기도 합니다. 3d에서 inanimate 개체를 캡처 및 디지털 콘텐츠 제작과 소프트웨어를 사용 하 여 편집 하는 3D 인쇄 증가 함에 따라 점차 인기를 더해가는입니다. 사용 하는 **Kinect 2** 센서 및 [3D 작성기](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 캡처 기능을 사용 하 여 실제 개체에서 자산을 만듭니다. 도를 [도구 모음](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) 동일한 작업을 수행 하 **photogrammetry** 다양 한 이미지를 함께 연결 및 메시 질감을 처리 하 여 합니다.

### <a name="purchasing-assets"></a>자산을 구매

또 다른 뛰어난 옵션 환경에 대 한 자산을 구입 하는 것입니다. 밖에도 자산의 서비스를 통해 사용 가능한 예는 [Unity 자산 스토어](https://www.assetstore.unity3d.com/) 또는 [TurboSquid](http://www.turbosquid.com/) 특히 합니다.

타사에서 자산을 구입한 경우 항상 다음을 확인 하려면:
* **예: poly 수 란?**
  * 예산 내에서 그 크기는?
* **모델에 대 한 (단계 Lod) 세부 수준을 있습니까?**
  * 수준의 모델의 세부 정보를 사용 하면 성능에 대 한 모델의 세부 정보를 확장할 수 있습니다.
* **소스 파일 사용 가능한 기능**
  * 일반적으로 사용 하 여 포함 되지 [Unity 자산 스토어](https://www.assetstore.unity3d.com/) 와 같은 서비스를 사용 하 여 항상 포함 되지만 [TurboSquid](http://www.turbosquid.com/)합니다.
  * 원본 파일 없이 자산을 수정할 수 없습니다.
  * 3D 도구에서 제공 된 소스 파일을 가져올 수 있는지 확인 합니다.
* **그 결과 알으십시오**
  * 애니메이션 제공 됩니다.
  * 구매 중인 자산 콘텐츠 목록을 확인 해야 합니다.

### <a name="porting-assets"></a>자산에 이식

일부 경우에 다른 장치 및 다른 앱에 대 한 원래 작성 된 기존 자산 전달 됩니다. 대부분의 경우에서 이러한 자산을 해당 앱을 사용 하는 그래픽 엔진 호환 형식으로 변환할 수 있습니다.

HoloLens 응용 프로그램에서 사용 하는 자산을 이식 하는 경우 다음에 대해 질문 합니다.
* **직접 가져올 수 있습니다 또는 다른 형식으로 변환 해야 합니까?** 사용 하는 그래픽 엔진을 사용 하 여 가져오는 형식을 확인 합니다.
* **호환 형식으로 변환 하는 경우 아무 것도 손실 됩니다.** 경우에 따라 세부 정보는 손실 될 수 있습니다 또는 가져오기 도구를 제작의 3d에서 정리 해야 하는 아티팩트를 발생할 수 있습니다.
* **삼각형 란 다각형 자산에 대 한 개수 /?** 하는 응용 프로그램에 대 한 예산에 따라 [Simplygon](https://www.simplygon.com/) 또는 유사한 도구 데시메이트하기 (절차에 따라 또는 수동으로 예: poly 수를 축소 함) 응용 프로그램 예산에 맞게 원래 자산입니다.

### <a name="outsourcing-assets"></a>아웃소싱 자산

팀 보다 자세한 자산을 필요로 하는 대규모 프로젝트에 대 한 또 다른 옵션은 자산 만들기를 아웃소싱하는 데는 만들려는 장착 합니다. 아웃소싱 과정 아웃소싱 자산에 오른쪽 studio 또는 전문으로 하는 에이전시를 찾습니다. 가장 비용이 많이 드는 옵션 수는 있지만 수도 얻게에 가장 유연한이 있습니다.
* **명확 하 게 요청 하는 정의**
  * 최대한 많은 세부 정보를 제공 합니다.
  * 쪽 앞면과 뒷면 개념 이미지
  * 컨텍스트에서 참조 아트 보여 주는 자산
  * (일반적으로 센티미터 단위로 지정) 하는 개체의 크기 조정
* **예산 범위를 제공 합니다.**
  * 예: poly 수 범위
  * 텍스처 수
  * 셰이더 (에 대 한 Unity 및 HoloLens 먼저 모바일 셰이더를를 항상 기본 해야)의 형식
* **비용을 이해**
  * 변경 요청에 대 한 아웃소싱 정책은 무엇 인가요?

아웃소싱이 프로젝트 타임 라인에 따라 매우 잘 가능 하지만 자세한 감독 처음 해야 올바른 자산을 얻을 수 있도록 보장 하기 위해 필요 합니다.
