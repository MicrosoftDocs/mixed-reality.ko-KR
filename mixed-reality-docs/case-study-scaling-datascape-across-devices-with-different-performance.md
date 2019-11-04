---
title: 사례 연구-다양 한 성능으로 장치에서 고가는 크기 조정
description: 이 사례 연구는 다양 한 성능 기능을 갖춘 다양 한 장치에서 매력적인 환경을 제공 하기 위해 Microsoft 개발자가 어떻게 강화 카보베르데 앱을 최적화 하는 방법에 대 한 통찰력을 제공 합니다.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 모던 헤드셋, 성능 최적화, VR, 사례 연구
ms.openlocfilehash: 05f97188c81d85685540be998111ecfc47d9ef9c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436508"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>사례 연구-다양 한 성능으로 장치에서 고가는 크기 조정

가 중 카보베르데는 Microsoft에서 내부적으로 개발 된 Windows Mixed Reality 응용 프로그램으로,이를 통해 지형 데이터 위에 날씨 데이터를 표시 하는 데 중점을 두었습니다. 응용 프로그램은 사용자가 holographic 데이터 시각화를 사용 하 여 혼합 현실에서 데이터를 검색 하는 것을 얻을 수 있는 고유한 통찰력을 탐색 합니다.

뛰어난 카보베르데의 경우 Microsoft HoloLens에서 Windows Mixed Reality 몰입 형 헤드셋에 이르는 다양 한 하드웨어 기능을 갖춘 다양 한 플랫폼을 대상으로 하 고, 저전력 Pc에서 고성능 GPU를 사용 하는 최신 Pc로 다양 한 플랫폼을 대상으로 하고자 했습니다. 주요 과제는 높은 프레임 속도로 실행 되는 동안 다른 그래픽 기능을 무분별 하는 장치에서 시각적으로 눈에 띄는 장면을 렌더링 하는 것 이었습니다.

이 사례 연구에서는 몇 가지 GPU 집약적 시스템을 만드는 데 사용 되는 프로세스와 기술을 단계별로 안내 하 여 발생 한 문제와 극복 했습니다 방법을 설명 합니다.

## <a name="transparency-and-overdraw"></a>투명도 및 과도 한 그리기

투명도는 GPU에 비용이 많이 들 수 있으므로 주 렌더링 겪던 투명도를 처리 합니다.

깊이 버퍼에 쓰는 동안 단색 기 하 도형을 뒤로 렌더링 하 여 해당 픽셀 뒤에 있는 이후의 픽셀을 모두 중지할 수 있습니다. 이렇게 하면 숨겨진 픽셀이 픽셀 셰이더를 실행 하는 것을 방지 하 여 프로세스 속도를 크게 향상 시킬 수 있습니다. 기 하 도형이 최적으로 정렬 된 경우 화면에서 각 픽셀은 한 번만 그려집니다.

투명 한 기 하 도형을 앞으로 다시 정렬 하 고 픽셀 셰이더의 출력을 화면에 있는 현재 픽셀에 혼합 해야 합니다. 이로 인해 화면에 각 픽셀이 프레임 당 여러 번 그려집니다 (과다 그리기 라고 함).

HoloLens 및 메인스트림 Pc의 경우 화면을 몇 번만 채울 수 있으므로 투명 하 게 렌더링 하는 문제가 발생할 수 있습니다.

## <a name="introduction-to-datascape-scene-components"></a>이상 카보베르데 구성 요소 소개

장면에는 세 가지 주요 구성 요소가 있습니다. **UI, 지도**및 **날씨**입니다. 날씨 효과에는 얻을 수 있는 모든 GPU 시간이 필요 하기 때문에, 과도 한 그리기를 줄이는 방식으로 UI 및 지형을 의도적으로 설계 되었습니다.

UI를 여러 번 다시 작성 하 여 생성 되는 오버 그리기의 양을 최소화 합니다. 빛나는 단추 및 지도 개요와 같은 구성 요소를 위해 투명 한 아트를 서로 겹치지 않고 보다 복잡 한 기 하 도형의 측면에서 erred.

Map의 경우 그림자 및 복잡 한 조명과 같은 표준 Unity 기능을 제거 하 여 간단한 단일 sun 조명 모델과 사용자 지정 안개 계산으로 대체 하는 사용자 지정 셰이더를 사용 했습니다. 이로 인해 간단한 픽셀 셰이더가 생성 되 고 GPU 사이클이 해제 됩니다.

하드웨어에 따라 변경 내용이 필요 하지 않은 예산으로 렌더링 하기 위해 UI와 지도를 모두 얻기 위해 관리 했습니다. 그러나 특히 클라우드 렌더링에서 날씨 시각화는 더 많은 과제를 증명 했습니다.

## <a name="background-on-cloud-data"></a>클라우드 데이터의 배경

클라우드 데이터는 NOAA 서버 (https://nomads.ncep.noaa.gov/) 에서 다운로드 되었으며, 각각 클라우드의 위쪽 및 아래쪽 높이와 표의 각 셀에 대 한 클라우드의 밀도를 포함 하는 세 개의 고유한 2D 계층으로 제공 됩니다. 데이터는 각 구성 요소가 질감의 빨강, 녹색 및 파랑 구성 요소에 저장 된 클라우드 정보 질감으로 처리 되어 GPU에 쉽게 액세스할 수 있습니다.

## <a name="geometry-clouds"></a>기 하 도형 클라우드

더 적은 수의 컴퓨터에서 클라우드를 렌더링할 수 있도록 하려면 솔리드 geometry를 사용 하 여 과도 한 그리기를 최소화 하는 방법으로 시작 하기로 결정 했습니다.

먼저 꼭지점 마다 클라우드 정보 질감의 반지름을 사용 하 여 각 계층에 대해 solid heightmap 메시를 생성 하 고 셰이프를 생성 하 여 클라우드를 생성 했습니다. 기 하 도형 셰이더를 사용 하 여 클라우드를 생성 하는 클라우드의 위쪽과 아래쪽에서 꼭 짓 점을 생성 했습니다. 질감에서 밀도 값을 사용 하 여 더 많은 조밀한 클라우드의 경우 더 진한 색으로 클라우드를 색으로 바꿉니다.

**꼭 짓 점 만들기에 대 한 셰이더:**

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

실제 데이터에 대 한 자세한 정보를 얻기 위해 작은 소음 패턴이 도입 되었습니다. 라운드 클라우드 가장자리를 생성 하기 위해 보간된 반지름 값이 0에 가까운 값을 삭제 하는 임계값에 도달할 때 픽셀 셰이더의 픽셀을 클리핑 했습니다.

![기 하 도형 클라우드](images/datascape-geometry-clouds-700px.jpg)

클라우드는 솔리드 기 하 도형 이므로 더 높은 속도의 지도 픽셀을 숨겨 프레임 속도를 높이는 데 사용할 수 있습니다. 이 솔루션은 견고한 기 하 도형 렌더링 방식 때문에 HoloLens 뿐만 아니라 최소 사양에서 하이엔드 그래픽 카드로 모든 그래픽 카드에서 효과적으로 실행 되었습니다.

## <a name="solid-particle-clouds"></a>단색 파티클 클라우드

이제 클라우드 데이터를 적절 하 게 표현 하는 백업 솔루션이 있지만,이는 "wow" 요소에 대 한 비트 lackluster, 고급 컴퓨터에 대 한 대규모 느낌이 전달 되지 않았습니다.

다음 단계는 약 10만 파티클을 사용 하 여 클라우드를 만들어 더 유기적 및 대규모 모양을 생성 하는 것입니다.

파티클을 계속 해 서 오름차순으로 정렬 하는 경우 이전에 렌더링 된 입자 뒤의 픽셀에 대 한 깊이 버퍼 고르기을 활용 하 여 오버 그리기를 줄일 수 있습니다. 또한 파티클 기반 솔루션을 사용 하 여 다른 하드웨어를 대상으로 하는 데 사용 되는 파티클의 양을 변경할 수 있습니다. 그러나 모든 픽셀은 여전히 깊이 테스트를 거쳐야 하므로 약간의 추가 오버 헤드가 발생 합니다.

첫 번째는 시작 시 경험 중심 지점을 중심으로 파티클 위치를 만들었습니다. 입자를 중심 주위에 더 조밀 거리에 분산 합니다. 가장 가까운 입자가 가장 먼저 렌더링 되도록 모든 입자를 중심에서 뒤로 미리 정렬 했습니다.

계산 셰이더는 각 파티클을 올바른 높이로 배치 하 고 밀도에 따라 색을 조정 하는 클라우드 정보 질감을 샘플링 합니다.

이 경우에는 모든 파티클에서 파티클 데이터를 유지할 수 있도록 각 파티클을 렌더링 하기 위해 *Drawprocedural* 을 사용 했습니다.

각 파티클에는 높이와 반지름이 모두 포함 됩니다. 높이는 클라우드 정보 질감에서 샘플링 된 클라우드 데이터를 기반으로 하며, 반지름은 가장 가까운 인접 항목에 가로 거리를 저장 하도록 계산 되는 초기 분포를 기반으로 합니다. Quads는이 데이터를 사용 하 여 높이를 기준으로 하 여 사용자가 가로 방향으로 표시 하 고, 높이가 표시 되 고, 사용자가 하향식으로 볼 때 이웃 영역 사이에 영역이 적용 되도록 합니다.

![파티클 모양](images/particle-shape-700px.png)

**분포를 보여 주는 셰이더 코드:**

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

파티클을 front로 정렬 하 고 단색 스타일 셰이더를 사용 하 여 투명 픽셀을 클리핑 하기 때문에이 기술은 놀라운 양의 파티클을 처리 하 여 더 높은 수준의 시스템 에서도 과도 한 오버 그리기를 방지 합니다.

## <a name="transparent-particle-clouds"></a>투명 파티클 클라우드

솔리드 파티클은 클라우드의 셰이프에 좋은 유기적 느낌을 제공 하지만 클라우드의 fluffiness을 판매 하는 데 필요한 사항이 있습니다. 투명도를 도입할 수 있는 고급 그래픽 카드에 대 한 사용자 지정 솔루션을 사용해 보았습니다.

이렇게 하려면 파티클의 초기 정렬 순서를 전환 하 고 질감 알파를 사용 하도록 셰이더를 변경 하기만 하면 됩니다.

![Fluffy 클라우드](images/fluffy-clouds-700px.jpg)

수백 번의 화면에서 각 픽셀을 렌더링 하므로 가장 어려운 컴퓨터에도 너무 많은 것으로 판명 되었습니다.

## <a name="render-off-screen-with-lower-resolution"></a>해상도가 낮은 화면에서 렌더링

클라우드에서 렌더링 되는 픽셀 수를 줄이기 위해 화면에 비해 사분기 해상도 버퍼로 렌더링 하기 시작 하 고 모든 파티클이 그려진 후 최종 결과를 화면에 다시 스트레치 합니다. 약 4 배 속도를 제공 했지만 몇 가지 주의 사항이 있습니다.

**화면 밖에 렌더링 하기 위한 코드:**

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

첫째, 화면 외부 버퍼로 렌더링할 때 주 장면에서 모든 깊이 정보를 손실 하 여 산악 산 위에서의 파티클 렌더링을 생성 합니다.

두 번째로, 버퍼를 스트레치 하는 것은 해결 방법이 눈에 띄는 클라우드의 가장자리에도 아티팩트를 도입 했습니다. 다음 두 섹션에서는 이러한 문제를 해결 하는 방법에 대해 설명 합니다.

## <a name="particle-depth-buffer"></a>파티클 깊이 버퍼

산 또는 개체가 산의 입자를 다룰 수 있는 세계 기 하 도형에 입자를 공존할 수 있도록 하기 위해 화면 외부 버퍼를 주 장면의 기 하 도형을 포함 하는 깊이 버퍼로 채웁니다. 이러한 깊이 있는 버퍼를 생성 하기 위해 두 번째 카메라를 만들었으므로 솔리드 기 하 도형 및 장면의 깊이가 렌더링 됩니다.

그런 다음 클라우드의 픽셀 셰이더에 새 텍스처를 사용 하 여 픽셀을 려 합니다. 동일한 질감을 사용 하 여 클라우드 픽셀 뒤의 기 하 도형에 대 한 거리를 계산 했습니다. 이제이 거리를 사용 하 여 픽셀의 알파에 적용 하는 경우, 이제는 지역에 근접 하 고 파티클 및 지형을 만족 하는 하드 컷을 제거 하 여 클라우드의 효과를 줄일 수 있었습니다.

![지형으로 혼합 되는 클라우드](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>가장자리를 선명 하 게

확장 된 클라우드는 파티클의 중앙에서 일반적인 크기의 클라우드와 거의 동일 하 게 보이지만, 겹쳐진 위치는 클라우드 가장자리에서 일부 아티팩트를 보여 주었습니다. 그렇지 않으면 선명한 가장자리가 흐리게 표시 되 고 카메라를 이동할 때 별칭 효과가 도입 됩니다.

이는 화면 밖의 버퍼에서 간단한 셰이더를 실행 하 여 대비에 큰 변화가 발생 한 위치 (1)를 확인 하 여이를 해결 했습니다. 큰 변화를 가진 픽셀을 새 스텐실 버퍼 (2)에 배치 합니다. 그런 다음 스텐실 버퍼를 사용 하 여 화면에 오프 화면 버퍼를 다시 적용할 때 이러한 높은 대비 영역을 마스크 하 여 클라우드 (3)의 구멍이 발생 하 게 합니다.

그런 다음 전체 화면 모드에서 모든 파티클을 다시 렌더링 했지만 이번에는 스텐실 버퍼를 사용 하 여 가장자리를 제외한 모든 항목을 마스크 하 여 최소한의 픽셀 집합 (4)을 사용 했습니다. 파티클에 대해 명령 버퍼를 이미 만들었기 때문에 새 카메라로 다시 렌더링 하기만 하면 됩니다.

![클라우드 가장자리 렌더링 진행](images/cloud-steps-1-4-700px.jpg)

최종 결과는 클라우드의 저렴 한 센터 섹션과 선명한 가장자리가 되었습니다.

이는 전체 화면에서 모든 입자를 렌더링 하는 것 보다 훨씬 빠르기는 하지만 스텐실 버퍼에 대 한 픽셀 테스트와 관련 된 비용이 여전히 남아 있으므로 엄청난 양의 과도 한 그리기는 여전히 비용으로 제공 됩니다.

## <a name="culling-particles"></a>고르기 파티클

바람 효과를 위해 계산 셰이더에 긴 삼각형 스트립을 생성 하 여 전 세계에서 많은 바람의 wisps을 생성 했습니다. Skinny 스트립으로 인해 윈드 효과가 가득 차서 채우기 비율이 크게 지는 않지만 수많은 꼭 짓 점 셰이더를 생성 하 여 꼭 짓 점 셰이더를 많이 로드 합니다.

그릴 바람 스트립의 하위 집합을 제공 하기 위해 계산 셰이더에 추가 버퍼를 도입 했습니다. 계산 셰이더의 몇 가지 간단한 뷰 고르기 논리를 사용 하 여 스트립이 카메라 보기 외부에 있는지 확인 하 고 푸시 버퍼에 추가 되지 않도록 할 수 있습니다. 이렇게 하면 스트립의 양이 현저 하 게 감소 하 여 GPU에서 필요한 주기가 확보 됩니다.

**추가 버퍼를 보여 주는 코드:**

*셰이더 계산:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#code*

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

클라우드 파티클에서 동일한 기법을 사용 하려고 했습니다. 여기서는 계산 셰이더에 추려내 표시 되는 파티클만 푸시합니다. 이 기법은 가장 큰 병목 현상이 화면에 렌더링 되는 픽셀 크기이 고 꼭 짓 점을 계산 하는 비용이 아니라 GPU에 거의 저장 되지 않았습니다.

이 방법의 다른 문제는 파티클을 계산 하 여 병렬 처리 된 특성으로 인해 추가 버퍼가 임의의 순서로 채워지기 때문에 정렬 된 입자가 정렬 되지 않아 클라우드 파티클이 깜박거리는 것입니다.

푸시 버퍼를 정렬 하는 기술이 있지만 고르기 파티클에서 제공 되는 제한 된 양은 추가 정렬을 사용 하 여 상쇄 될 가능성이 높기 때문에 이러한 최적화를 활용 하지 않기로 결정 했습니다.

## <a name="adaptive-rendering"></a>적응 렌더링

Cloudy vs와 같이 다양 한 렌더링 조건이 있는 앱에서 안정적인 프레임 속도를 보장 하기 위해 앱에 적응 렌더링을 도입 했습니다.

적응 렌더링의 첫 번째 단계는 GPU를 측정 하는 것입니다. 이를 위해 사용자 지정 코드를 렌더링 된 프레임의 시작과 끝에 있는 GPU 명령 버퍼에 삽입 하 여 왼쪽 및 오른쪽 시각 화면 시간을 모두 캡처합니다.

렌더링 하는 데 걸린 시간을 측정 하 여 원하는 새로 고침 비율과 비교 하면 얼마나 가까이 프레임을 삭제 하는 것이 합리적입니다.

프레임을 놓을 때 보다 빠르게 보이도록 렌더링을 조정 합니다. 한 가지 간단한 방법은 화면에서 뷰포트 크기를 변경 하는 것입니다. 렌더링 되는 데 필요한 픽셀 수를 줄일 수 있습니다.

*XR* 를 사용 하 여 시스템에서 대상 뷰포트를 축소 하 고 결과를 화면에 맞게 자동으로 확장 합니다. 세계 기 하 도형에서는 규모의 작은 변화가 거의 눈에 띄지 않으며, 배율 인수 0.7에는 렌더링 해야 하는 픽셀의 절반이 필요 합니다.

![70% 배율, 1/2 픽셀](images/datascape-scaling-700px.jpg)

프레임을 삭제 하려고 하는 것을 감지 하면 크기를 고정 된 수 만큼 줄이고 빠르게 다시 실행 하는 경우 다시 증가 합니다.

시작할 때 하드웨어의 그래픽 기능을 기반으로 사용할 클라우드 기술을 결정 했지만, 시스템에서 오랜 시간 동안 해상도를 유지 하지 못하도록 GPU 측정의 데이터를 기반으로 할 수 있습니다. 그러나이는 시간이 없는 것입니다.  을 탐색 합니다.

## <a name="final-thoughts"></a>최종 생각

다양 한 하드웨어를 대상으로 하는 것은 어려운 일 이며 몇 가지 계획이 필요 합니다.

낮은 수준의 컴퓨터를 대상으로 지정 하 여 문제 공간을 파악 하 고 모든 컴퓨터에서 실행 되는 백업 솔루션을 개발 하는 것이 좋습니다. 픽셀은 가장 귀중 한 리소스 이기 때문에 채우기 빈도를 염두에 두면 솔루션을 디자인 하세요. 투명도에 대 한 대상 솔리드 기 하 도형입니다.

그러면 백업 솔루션을 사용 하 여 높은 수준의 컴퓨터에 대해 더 복잡 하 게 계층화를 시작 하거나 백업 솔루션의 해상도를 향상 시킬 수 있습니다.

최악의 시나리오에 맞게 디자인 하 고 많은 상황에서 적응 렌더링을 사용 하는 것이 좋습니다.

## <a name="about-the-authors"></a>작성자 정보

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>소프트웨어 엔지니어 @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>소프트웨어 엔지니어 @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>참고 항목
* [혼합 현실 성능 이해](understanding-performance-for-mixed-reality.md)
* [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)

 
