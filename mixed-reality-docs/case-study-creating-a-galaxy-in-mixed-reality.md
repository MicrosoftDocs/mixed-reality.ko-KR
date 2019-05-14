---
title: 사례 연구-는 galaxy 혼합된 현실에서 만들기
description: Microsoft HoloLens 배송 전에 요청한 개발자 커뮤니티 응용 프로그램이 어떤 바란다고 새 장치에 대 한 빌드 숙련된 된 내부 팀을 참조 하세요. 5,000 개가 넘는 아이디어 공유 된 했는데 24 시간제 Twitter 폴링 이후 우승자 "Galaxy 탐색기." 라는 개념
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy 탐색기, HoloLens, Windows Mixed Reality 사례 연구 아이디어 공유
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604832"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>사례 연구-는 galaxy 혼합된 현실에서 만들기

Microsoft HoloLens 배송 전에 요청한 개발자 커뮤니티 응용 프로그램이 어떤 바란다고 새 장치에 대 한 빌드 숙련된 된 내부 팀을 참조 하세요. 5,000 개가 넘는 아이디어를 공유 하 고 24 시간제 Twitter 폴링 이후 우승자를 호출 하는 개념 [Galaxy 탐색기](galaxy-explorer.md)합니다.

Andy Zibits, 프로젝트를 최신 잠재 고객 및 팀의 그래픽 엔지니어 Karim Luccin, 아트 및 Galaxy 탐색기에서 Milky 방법은 galaxy 정확 하 고, 대화형 표현을 생성 하는 엔지니어링 간의 공동 노력에 알아봅니다.

## <a name="the-tech"></a>기술 지원 담당자

[필자의 팀](galaxy-explorer.md#meet-the-team) 두 디자이너, 개발자 3, 4 아티스트, 생산자, 및 테스터를 하나를 수행 하는--6 주에 대해 알아보고 (광활) 및 우리의 Milky 방법은 Galaxy의 장점은 탐색 하 게 허용 하는 모든 기능을 갖춘 앱을 빌드할 수 있었습니다.

에 방문 하셔서 했습니다는 현실적인 보이는 galaxy 닫기에서 확대/축소 및 개별 별 참조 하는 일을 할 수는 사용자 위치 각각 자신의 궤적을 만들려면 하므로 사용자의 생활 공간에서 직접 3D 개체를 렌더링 하는 HoloLens의 기능을 최대한 활용 .

개발의 첫 번째 주에 개발할 수 있었습니다 몇 가지 목표 Milky 방법은 galaxy이 표현에 대 한 합니다. 깊이, 이동 및 대규모 느낌에 필요한 것-별 galaxy 도형을 만들어야 하는 데 도움이 되는 전체.

업데이트 해야 하는 단일 요소 수가 너무 많아 CPU를 사용 하 여 애니메이션 효과를 주는 HoloLens에 대해 프레임당 너무 큰 것이 별 수십억 있던는 애니메이션된 galaxy 만들기 문제가 였습니다. 솔루션 관련 기술 및 방법의 복잡 한 조합 합니다.

## <a name="behind-the-scenes"></a>백그라운드 작업

개별 별을 탐색할 수 있도록, 첫 번째 단계에서는 한 번에 렌더링 하는 얼마나 많은 파티클 파악 했습니다.

### <a name="rendering-particles"></a>파티클 렌더링

현재 Cpu 직렬 작업을 처리 하 고 몇 가지 병렬 작업을 한 번에 (코어 개수에 따라 있으면)까지 잘 되지만 Gpu 수천 개의 작업을 병렬로 처리에서 훨씬 더 효율적입니다. 그러나 일반적으로 CPU와 동일한 메모리를 공유 하지 않습니다, 때문에 CPU <> GPU 간의 데이터 교환 신속 하 게는 병목이 될 수 있습니다. 솔루션을 galaxy GPU에서 확인 하는 것 이었습니다 및 GPU에서 완전히 라이브 해야 합니다.

수천 개의 다양 한 패턴의 지점 입자를 사용 하 여 스트레스 테스트를 시작 했습니다. 이 옵션을 사용 하면 필드와 그렇지 않은 것을 확인 하려면 HoloLens galaxy 로그온 수 있었습니다.

### <a name="creating-the-position-of-the-stars"></a>별표 위치 만들기

이미 작성 했다고 우리 팀 멤버 중 하나를 C# 별 처음 위치에서 생성 하는 코드입니다. 별표 타원에 있고 해당 위치에서 설명할 수 있습니다 (**curveOffset**를 **ellipseSize**에 **상승**) 여기서 **curveOffset**ellipse에 따라 star의 각도 **ellipseSize** X 따라 타원의 차원이 Z, 및 권한 상승 galaxy 내 별의 적절 한 권한 상승 합니다. 따라서 버퍼를 만들 수 있습니다 ([Unity의 ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) 별 각 특성을 사용 하 여 초기화 됩니다을 환경의 나머지 부분에는 거주 GPU에 전송 합니다. 사용이 버퍼를 그릴 [Unity의 DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) 에서 허용 하는 셰이더 (GPU에서 코드)를 실행 중인 임의의 지점 집합 galaxy 나타내는 실제 메시를 하지 않고도:

**CPU:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

파티클 수천 개의 원시 순환 패턴을 사용 하 여 시작합니다. 이 통해 많은 입자를 관리 하 고 성능이 뛰어난 속도로 실행 수 있었습니다 있지만 없습니다 galaxy의 전체적인 모양을 만족 했던 증명 합니다. 모양 향상을 위해 다양 한 패턴 및 회전을 사용 하 여 파티클 시스템을 시도 했습니다. 얻었습니다 처음 유망한 파티클 성능과 수가 일관 된 특정 높게 유지 하지만 가운데 근처에 있는 중단 되는 모양을 별표 현실적인 아닌 외부적으로 내보내는 것 때문입니다. 허용 시간을 조작 하 고 있는 파티클 현실적으로 이동 하는 내보내기가 필요 반복 galaxy 중앙에 가깝게 적이 있습니다.

![다양 한 패턴 및 이러한 회전 파티클 시스템을 시도 했습니다.](images/galaxy-patterns-500px.png)

다양 한 패턴 및 이러한 회전 파티클 시스템을 시도 했습니다.

필자의 팀 않은 방식으로 은하계 함수에 대 한 몇 가지 연구 및 galaxy에 맞게 사용자 지정 파티클 시스템을 기반으로 하는 줄임표도 파티클을 설명할 수 있도록 했습니다 "[밀도 wave 이론](https://en.wikipedia.org/wiki/Density_wave_theory),"는 theorizes는의 arm을 galaxy은 더 높은 밀도 있지만 트래픽 걸림 같은 상수 flux 영역입니다. 것 안정적이 고, 단색 처럼 보이지만 별표 실제로 이동 하는 arm에서 들어오고 나가는 각각 해당 줄임표를 따라 이동 합니다. 이 시스템에서 파티클 되지에 있는 CPU-카드를 생성 하 고 전체 시스템 단순히 초기 상태 + 시간 이므로 GPU에서 모든 방향입니다. 이 같이 진행 합니다.

![GPU 렌더링 파티클 시스템의 진행](images/spiral-galaxy-arms-500px.jpg)

GPU 렌더링 파티클 시스템의 진행


충분 한 줄임표 회전로 추가 하 고는 은하계 폼 "arm" 별의 이동이 수렴 하기 시작 했습니다. 타원형 각 경로의 별표의 간격을 몇 가지 임의성을 지정 된 및 각 별 약간의 추가 위치 임의성을 가져왔습니다. 이 이동 및 arm에 대 한 별 모양의 양이 적고 자연 스러운 보이는 분포를 생성 합니다. 마지막으로, center에서의 거리에 따라 드라이브 색에 기능을 추가 했습니다.

### <a name="creating-the-motion-of-the-stars"></a>별표는 동작 만들기

일반 별 동작, 애니메이션을 각 프레임에 대 한 상수 각도 추가 하 고 해당 줄임표 상수 방사형 속도로 진행 별 필요 했습니다. 이 사용 하는 주된 이유 **curveOffset**합니다. 이 별 긴 가장자리의 줄임표를 더 빠르게 이동할 수 있지만 일반 동작 한다고 좋은 생각 한 대로 기술적으로 올바르지 않습니다.

![별은 가장자리 느리게 긴 호에서 더 빠르게 이동합니다.](images/ellipse-movement.jpg)

별은 가장자리 느리게 긴 호에서 더 빠르게 이동합니다.


사용 하 여 각 별모양으로 설명 완벽 하 게 됩니다 (**curveOffset**, **ellipseSize**, **권한 상승**, **Age**) 여기서 **Age** 장면 로드 된 이후 경과 된 총 시간의 누적 됩니다.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

이 덕분에 수십만 별 응용 프로그램의 시작 부분에 한 번 생성 하려면 다음 설정 된 곡선을 따라 별 서명된 집합을 애니메이션 효과가 적용 했습니다. GPU에서 모든 항목 이므로 시스템 cpu 비용 없이 병렬로 모든 별 애니메이트할 수 있습니다.

![모양 때 그리기 흰색 quads 다음과 같습니다.](images/drawing-white-quads-300px.jpg)

모양 때 그리기 흰색 quads 다음과 같습니다.



쿼드 각 얼굴 카메라를 만들려면 각 별모양 위치는 별모양 질감을 포함 하는 화면에서 2D 사각형에 변환할 기 하 도형 셰이더를 사용 했습니다.

![Quads 대신 다이아몬드입니다.](images/drawing-white-quads-300px.jpg)

Quads 대신 다이아몬드입니다.


에 방문 하셔서 overdraw (픽셀을 처리할 시간 수)를 제한 하기 때문에 가능한 만큼에서는 회전 우리의 quads 덜 중복 되어 있도록 합니다.

### <a name="adding-clouds"></a>클라우드를 추가합니다.

여러 가지 방법으로 입자를 사용 하 여 대규모 이해할-광선이 볼륨 내에서 클라우드를 시뮬레이션 하기 위해 최대한 많은 파티클 그리기 행진 합니다. 행진 하는 실시간 ray 되므로 너무 어렵고 비용이 많이 드는 작성자에 게 먼저 노력 게임의 렌더링 포리스트에 대해 메서드를 사용 하 여 가짜 시스템을 구축 하려는-많은 수의 카메라를 연결 하는 트리의 2D 이미지를 사용 하 여 합니다. 게임에서이 작업을 수행 했습니다 주위, 이러한 모든 이미지 저장 및 각 빌보드 카드에 대 한 런타임 시 회전 하는 카메라에서 렌더링 되는 트리의 질감이 보기 방향을 일치 하는 이미지를 선택 수 했습니다. 이 작동 하지 않습니다도 이미지를 제공 하는 경우. 왼쪽된 눈와 오른쪽 눈 차이 되도록 보입니다 flat 별칭을 지정 합니다. 그렇지 않으면 훨씬 더 높은 해상도 필요 또는 반복 합니다.

이 두 번째 시도에서 최대한 많은 파티클 것을 시도 합니다. 최상의 시각적 개체 입자 파티클 그린 하 고 이러한 장면에 추가 하기 전에 흐리게 표시 얻은 결과입니다. 해당 접근 방식 사용 하 여 일반적인 문제 된 얼마나 관련이 파티클 번을 그릴 수 있습니다 하 고 얼마나 60 fps를 유지 하면서 영역은 화면 표시 합니다. 이 클라우드 기분을 가져오기 결과 이미지가 흐리게 표시 하기가 매우 비용이 많이 드는 작업을 일반적으로 했습니다.

![질감 없이 2% 불투명도 사용 하 여 확인은 클라우드입니다.](images/clouds-without-texture-300px.jpg)

질감 없이 2% 불투명도 사용 하 여 확인은 클라우드입니다.



가산 성 되 고 많은 있다는 것을 서로 위에 몇 가지 quads 반복 해 서 같은 픽셀을 음영을 의미 합니다. Galaxy 센터에서 같은 픽셀 서로 위에 quads 수백 있으며 비용도 만만치 전체 화면을 완료 되 면이 있었습니다.

전체 화면 클라우드를 수행 하 고 흐리게 하 되었을 바람직하지 대신에 작업을 수행 하는 하드웨어를 사용 하기로 결정 했습니다.

### <a name="a-bit-of-context-first"></a>비트 컨텍스트의 우선

게임에서 질감을 사용 하는 경우 질감 크기는 거의 사용 하려는 영역을 일치 하지만 다른 종류의 질감 필터링 질감의 픽셀에서 원하는 색을 보간 하는 그래픽 카드를 가져오고을 사용할 수 있습니다 ([질감 필터링<c3/>).](https://msdn.microsoft.com/library/dn642451.aspx) 미국 관심 있는 필터링 [쌍선형 필터링](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) 는 가장 인접 한 항목 4를 사용 하 여 픽셀의 값을 계산 됩니다.

![필터링 하기 전에 원래](images/texture-1.png)

![필터링 후 발생 합니다.](images/texture-2.png)

이 속성을 사용는 질감 크지는 배 영역에 그릴 시도 될 때마다 해당 흐리게 결과 표시 합니다.

전체 화면에 렌더링에서는 다른 작업에 소요 될 수 있습니다 하는 데 귀중 한 밀리초를 모두 잃으면 서, 대신 작은 버전의 화면에 렌더링 합니다. 그런 다음이 질감을 복사 하 고 여러 번 2 배 확장,으로 니 전체 화면으로 프로세스에서 콘텐츠를 흐리게 표시 하는 동안.

![x3 고급 고해상도 돌아갑니다.](images/galaxy-resolutions-300px.png)

x3 고급 고해상도 돌아갑니다.



이 옵션을 사용 하면 원래 비용의 일부만 사용 하 여 클라우드 부분을 가져올 수 있었습니다. 클라우드에 전체 해상도에,만 것 그리기 1/64 픽셀 및만 stretch 텍스처 전체 해상도를 다시 추가 하는 대신 합니다.

![왼쪽을 높입니다 1에서 전체 해결; 8 일 / 및 오른쪽 높입니다 3을 사용 하 여 2의 제곱을 사용 합니다.](images/stars-upscaled-300px.jpg)

왼쪽을 높입니다 1에서 전체 해결; 8 일 / 및 오른쪽 높입니다 3을 사용 하 여 2의 제곱을 사용 합니다.


1에서 이동 하는 동안 해당 참고/64의 전체 크기를 그래픽 카드는를 사용 하 여 4 픽셀이 설치 프로그램에서 더 큰 영역을 음영을 적용 하 고 아티팩트를 표시 하려면 한꺼번에 크기 완전히 다르게 표시 됩니다.

그런 다음 작은 카드를 사용 하 여 고해상도 stars를 추가 했습니다 하는 경우 전체 galaxy를 가져옵니다.

![거의 전체 해상도 별표를 사용 하 여 galaxy 렌더링의 최종 결과](images/full-galaxy-500px.png)

셰이프를 오른쪽 트랙 있었습니다 되 면 클라우드, photoshop, 그리고 하 고 몇 가지 추가 색 추가 사용 하 여 임시 점 스와핑할의 계층을 추가 했습니다. 결과 Milky 방법은 Galaxy 우리의 아트 및 엔지니어링 팀 모두에 대 한 좋은 것 깊이, 볼륨 및 동작의 목표를 충족 하기-CPU에 부담이 초래 하지 않고 있습니다.

![3d에서는 최종 Milky 방법은 Galaxy 합니다.](images/final-galaxy-500px.jpg)

3d에서는 최종 Milky 방법은 Galaxy 합니다.


### <a name="more-to-explore"></a>추가로 살펴볼 내용

Galaxy 탐색기 앱에 대 한 코드를 오픈 소스를에 제공 했습니다 [GitHub](https://github.com/Microsoft/GalaxyExplorer) 개발자 작성할 수 있습니다.

Galaxy 탐색기에 대 한 개발 프로세스에 대해 자세히 알아보려면에 관심이 있으십니까? 이전 프로젝트에서 모든 업데이트를 확인 합니다 [Microsoft HoloLens YouTube 채널](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)합니다.

## <a name="about-the-authors"></a>저자 소개

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> 은 소프트웨어 엔지니어 이자 열성적인 멋진 시각적 개체입니다. Galaxy 탐색기에 대 한 그래픽 엔지니어 였습니다.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> Galaxy 탐색기에 대 한 3D 모델링 팀을 관리 하 고 더 많은 파티클에 대 한 느껴지거나 아트 잠재 고객 및 공간 열성적인 됩니다.</td>
</tr>
</table>


## <a name="see-also"></a>참조
* [GitHub에서 Galaxy 탐색기](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube의 Galaxy 탐색기 프로젝트 업데이트](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
