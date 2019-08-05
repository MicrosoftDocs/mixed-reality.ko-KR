---
title: HoloLens 용 Galaxy 탐색기 만들기 2
description: HoloLens의 Galaxy 탐색기를 업데이트 하는 방법 2를 시작 합니다. 원래 Galaxy 탐색기와 마찬가지로 팀은 GitHub의 프로젝트를 열어 커뮤니티에 모든 권한이 있는지 확인 합니다.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy 탐색기, 사례 연구, 프로젝트, 샘플
ms.openlocfilehash: 1e04b27ff0382d87f8e6a15ae2b7b2284fa020e6
ms.sourcegitcommit: be3631932ea1c88ac3ad8b2390c98c5a6e8b93ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2019
ms.locfileid: "68776427"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>HoloLens 용 Galaxy 탐색기 만들기 2

HoloLens의 Galaxy 탐색기를 업데이트 하는 방법 2를 시작 합니다. [Galaxy 탐색기] (https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy 탐색기") 는 원래 아이디어 프로그램 공유를 통해 HoloLens (첫 번째 gen) 용 오픈 소스 응용 프로그램으로 개발 되었으며, 많은 사람들이 보유 하 고 있는 첫 번째 혼합 현실 환경 중 하나입니다. 이제 [HoloLens 2의 새롭고 흥미로운 기능](https://www.microsoft.com/hololens/hardware)을 위해 업데이트 하 고 있습니다.

[Microsoft Mixed Reality 스튜디오](galaxy-explorer-update.md#mixed-reality-studios)중 하나로, 일반적으로 상용 성적 솔루션을 개발 하 고 창의적인 개발 프로세스 전체에서 대상 플랫폼에 대 한 테스트를 & 개발 하 고 있습니다. 이제 HoloLens 2 장치에 아직 액세스할 수 없지만 Galaxy 탐색기에 대 한 업데이트를 시작 하는 것이 좋습니다. Microsoft는이 프로젝트에 대해 우리와 커뮤니티에서 사용할 수 있게 되는 프레임 워크 및 도구 (예: [Mrtk v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html))를 형성 하 고 있습니다.

원래 Galaxy 탐색기와 마찬가지로 [팀](galaxy-explorer-update.md#meet-the-team) 은 [GitHub의 프로젝트를 열어](https://github.com/Microsoft/GalaxyExplorer) 커뮤니티에 모든 권한이 있는지 확인 합니다. 또한 MRTK v1에서 MRTK v 2로 포팅 하는 방법, HoloLens 2에서 제공 되는 새로운 기능을 기반으로 하 여 환경을 개선 하는 방법, 그리고 Galaxy 탐색기가 다중 플랫폼 환경. 따라서 HoloLens에서 Galaxy 탐색기를 보고 있든 (첫 번째 gen), HoloLens 2, Windows Mixed Reality 헤드셋 또는 Windows 10 desktop 중 어디에 있든 간에 편안 하 게 편안 하 게 경험 하 고 경험을 최대한 활용 하고자 합니다.

이 페이지는 프로젝트를 진행할 때 확장 되며, 프로젝트에 대 한 참가자의 의견을 제공 하기 위해 더 자세한 문서, 코드, 디자인 아티팩트의, 추가 MRTK v2 설명서 등에 연결 합니다.

## <a name="unveiling-the-new-logo"></a>새 로고 예상치

새 Galaxy 탐색기 로고의 미리 보기를 사용해 보세요. Milky 방식을 통해 원래 로고에 대 한 정보를 지불 하는 동안 실제 시각화를 설계 하 고 최신 느낌을 제공 하기 위해 입력 체계를 업데이트 했습니다. 로고에는 새 아이콘 중 하나를 살펴볼 수 있습니다.

![새 Galaxy 탐색기 로고](images/ge-update-app-icon.png)

로고의 디자인과 입력 체계는 전체 환경에서 UI 요소의 전체 모양과 느낌에 대 한 톤을 설정 합니다. 

## <a name="thinking-about-interactions"></a>상호 작용 고려

독창적인 스튜디오는 Galaxy Explorer를 HoloLens 2로 이식할 수 있는 권한에 대 한 ecstatic입니다. 처음에는 새로운 장치에 대 한 축 하 드립니다. 그리고 혼합 현실 역량을 상상력으로 제한 한다는 것을 보여 줍니다.

HoloLens 2를 사용 하면 사용자가 자연 스러운 방식으로 holograms을 터치, 판단 및 이동할 수 있습니다. 실제 개체와 같이 응답 합니다. 완전 한 트레일러 식 모델은 사용자가 자연스럽 게 작업할 수 있기 때문에 놀라운 역할을 합니다. 예를 들어 모든 사용자가 컵을 약간 다르게 선택 하 고 특정 한 방법을 적용 하는 대신, HoloLens 2를 사용 하 여 작업을 수행할 수 있습니다.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

이는 첫 번째 세대 HoloLens 장치에서 공기 탭 기반 인터페이스를 크게 변경 하는 것입니다. 사용자는 먼 거리에서 holograms와 상호 작용 하는 대신 "사용자가 가까이와 개인"을 가져올 수 있습니다. 기존 환경을 HoloLens 2로 포팅 하거나 새로운 환경을 계획할 때 holograms의 직접 조작을 이해 하는 것이 중요 합니다.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>직접 조작과 공간의 넓은 거리 비교

이는 전 세계에 연락 하 고 전 세계에 보관할 수 있는 마법의 경험입니다. 이 방법의 과제는 태양계의 크기 이며 매우 다양 합니다. 사용자는 각 행성에 근접 하 여 상호 작용할 수 있도록 방 주위를 탐색 해야 합니다.

사용자가 더 멀리 떨어져 있는 개체와 상호 작용할 수 있도록 하기 위해 MRTK는 사용자의 팜 중심에서 제공 되는 손 광선을 제공 하 여 손 모양 확장으로 작동 합니다. 도넛 모양의 커서는 광선이 대상 개체와 교차 하는 위치를 나타내기 위해 광선 끝에 연결 됩니다. 그런 다음, 커서가 닿는 개체는 손에서 제스처 명령을 받을 수 있습니다. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

원래 버전의 Galaxy 탐색기에서 사용자는 응시 커서를 사용 하 여 전 세계를 대상으로 하 고, 무선 탭을 사용 하 여 더 가까이 호출 합니다. HoloLens 2로 환경을 이식 하는 가장 쉬운 방법은이 동작을 수행 하 고 핸드 레이를 사용 하 여 행성을 선택 하는 것입니다. 이 기능이 작동 하는 동안 더 많은 정보를 남겨 주세요.

### <a name="back-to-the-drawing-board"></a>그리기 보드로 돌아가기

기존 상호 작용을 기반으로 구축 될 수 있는 항목을 ideate 했습니다. 생각은 다음과 같습니다. HoloLens 2를 사용 하면 사용자가 실제적이 고 현실적인 방법으로 holograms와 상호 작용할 수 있지만 실제 정의는 아닙니다. 따라서 사용자에 대 한 상호 작용이 타당 실제 개체를 사용 하 여 상호 작용을 가능 하 게 하는 것은 중요 하지 않으며 가능 합니다.

Telekinesis을 기반으로 하는 한 가지 개념은 개체를 조작할 수 있는 강력한 기능입니다. 일반적으로는 슈퍼 영웅 영화에서 볼 수 있으며, 사람들은 자신의 마음에 도달 하 여 개체를 오픈 손 모양으로 호출 합니다. 아이디어를 자세히 살펴보고 개념의 작동 방식에 대 한 빠른 스케치를 제공 합니다.

![강제 잡기 상호 작용에 대 한 개념](images/ge-update-interactions-concept-force-grab.png)

사용자는 대상 피드백을 제공 하는 전 세계의 광선을 가리킵니다. 그런 다음 사용자가 자신의 오픈 손을 확장 하 게 되 면 전 세계에 가까이 있을 때까지 전 세계를 통해 사용자에 게 이동 합니다. 따라서 상호 작용에 대 한 이름: 강제 잡기. 사용자가 해당 지구를 사용 하 여 지구를 푸시하 면 해당 궤도로 다시 돌아옵니다.

### <a name="force-grab-prototyping"></a>강제 잡기 프로토타입

그런 다음 개념을 테스트 하기 위해 여러 프로토타입을 만들었습니다. 상호 작용의 전체적인 느낌 호출 된 개체가 사용자 앞에서 중지 되거나 배치 될 때까지 손을 사용 해야 하나요? 호출 된 개체의 크기를 변경 해야 합니까? 아니면 크기를 조정 해야 하나요?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>응용 프로그램에 대 한 강제 잡기 구현

행성에 대해 강제 잡기를 시도 하면 태양계의 소수 자릿수를 변경 해야 했습니다. 사용자가 이해 하 고 탐색할 수 있을 때까지 태양계를 정확 하 고 중간 크기로 표현 하는 것은 어려운 일입니다. 그러나 정확 하 고 작은 크기의 표현이 너무 작아 쉽게 선택할 수 없습니다. 결과적으로 행성의 크기와 태양 개의 개체 간 간격은 상대 정확도를 유지 하면서 보통 크기의 공간 내에서 편안 하 게 설계 되었습니다.

개발 스 프린트의 이후 단계를 진행 하는 동안 동료 MSFT Mixed Reality 전문가에 게 사내를 사용 하는 것이 충분 하기 때문에 전문 테스터로 서 입력을 받고 강제로 잡기 상호 작용에 대 한 빠른 반복을 수행할 수 있습니다.

![의 Kam에서 Galaxy 탐색기의 미리 보기 빌드 테스트](images/ge-update-user-testing.png)

그림: 의 Kam, 선임 디자인 리드, Galaxy 탐색기의 작업 진행 상황을 테스트 합니다.

### <a name="adding-affordances-for-targeting"></a>대상 지정을 위한 affordances 추가

HoloLens 2를 실험 새 상호 작용이 자연스럽 고 직관적 이더라도 holograms는 가중치 또는 tactile sensations 없이 동일 하 게 유지 된다는 것을 알게 되었습니다. Holograms는 사용자가 개체와 상호 작용할 때 수신 하는 데 사용 하는 자연 스러운 피드백을 제공 하지 않으므로 만들어야 합니다.

사용자가 상호 작용의 다양 한 단계를 위해 사용자에 게 제공 되는 시각적 및 오디오 피드백 및 강제 잡기 메커니즘이 Galaxy 탐색기와 상호 작용 하는 중심 이므로 많은 반복이 발생 했습니다. 목표는 각 상호 작용 단계에 대 한 오디오 및 시각적 피드백의 적절 한 균형을 찾는 것입니다. 즉, 의도 한 개체에 초점을 맞춘 후 사용자에 게 호출 하 고 릴리스 합니다. HoloLens (첫 번째 gen)에 사용 된 것 보다 훨씬 더 많은 오디오 및 시각적 피드백을 사용 하 여 더 많은 오디오 및 시각적 피드백이 필요 합니다.

![행성의 시각적 affordances](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>강제 잡기에 affordances 추가
 
Audio 및 visual affordances를 사용 하는 기본 강제 잡기 메커니즘이 있으면 더 많은 사용자에 게 더 많은 행성을 선택 하는 방법을 살펴보았습니다. 해결 해야 할 두 가지 주요 사항은 다음과 같습니다. 양력 시스템은 3D 이동 인터페이스 이므로 사용자가 개체를 일관 되 게 대상으로 하는 방법을 배울 수 있는 복잡성이 추가 되었습니다. 이는 손을 빛이 매우 빠르기 때문에 개체를 선택 하 여 사용자를 매우 빠르게 이동 하는 것입니다.

대 접근 솔루션을 사용 하 여이에 대해 노력 했습니다. 첫 번째 방법은 매우 직관적입니다. 행성이 사용자에 게 보다 자연스럽 게 접근 하도록 선택 프로세스의 속도를 낮춥니다. 속도가 조정 된 후에는 오디오 및 시각적 affordances을 다시 방문 하 여 사용자에 게 추적 된 지구로 오디오 피드백을 추가 해야 했습니다.

솔루션의 두 번째 부분에서는 전체 강제 잡기 작업을 시각화 하는 것이 매우 중요 합니다. 손 모양 광선이 연결 된 후 대상 개체를 향해 이동 하는 굵은 선을 시각화 하 고 개체를 사용자와 같은 올가미로 다시 가져옵니다. 

![강제 잡기를 위한 시각적 "올가미" affordances](images/ge-update-lasso-affordances.png)

마지막으로, 행성이 사용자의 응시 및 손 광선을 대상으로 하는 데 충분 한 크기를 갖도록 양력 시스템의 규모를 최적화 했습니다. 

이러한 세 가지 향상 된 기능을 통해 사용자는 정확한 선택을 하 고 직관적인 방식으로 행성을 호출할 수 있습니다. 전반적으로 최종 강제 잡기의 효과는 태양계에서 더 몰입 형이 고 대화형 환경입니다.

## <a name="spotlight-on-jupiter"></a>Jupiter의 스포트라이트

Milky 방식의 태양계를 만드는 것은 humbling 환경 이었습니다. 특히 Jupiter의 고유한 특성은 behold에 대 한 시야를 만듭니다. 가스의 가장 크고 광범위 한 조합 이며 다른 모든 행성 보다 많은 질량을 포함 합니다. Turbulence 및 클라우드 dynamics의 가장 큰 크기 및 mesmerizing 밴드는 특별 한 꾸밈 주의를 prefect 합니다.

### <a name="geometry-and-meshes"></a>기 하 도형 및 망

가스의 Jupiter 외부 셸은 gaseous 계층으로 구성 됩니다. 고속 회전 속도, 내부 열 교환 및 Coriolis의 조합으로 인해 swirling cloud 벨트 및 vortices로 형성 되는 다채로운 계층 및 스트림이 생성 됩니다. 이러한 복잡 한 장점 캡처는 태양계를 만드는 데 중요 했습니다.

사전 계산 스트림을 사용 하 여 유체 시뮬레이션 및 애니메이션 텍스처와 같은 시각화 기법을 사용 하는 것이 더 확실 하지 않습니다. 동시에 발생 하는 다른 모든 것과 함께이를 시뮬레이션 하는 데 필요한 컴퓨팅 성능은 성능에 상당한 영향을 미칠 수 있습니다. 

![Jupiter 개체 개요](images/ge-update-jupiter-shells-complete.jpg)

다음 방법은 순환 메시의 컴포지션에 컴파일된 대기 이동의 특정 측면을 처리 하는 투명 한 질감 계층으로 구성 된 ' 스모크 및 미러링 ' 솔루션 이었습니다.

아래 이미지에서는 왼쪽의 내부 셸을 볼 수 있습니다. 이 matt 계층은 클라우드를 구성 하는 여러 계층 간의 작은 간격을 방지 하기 위해 컴포지션에 배경을 제공 했습니다. 계층의 저속 회전으로 인해 계층 전체에서 visual unity를 빌드하는 데 도움이 되도록 더 빠른 이동 밴드 사이에 시각적 버퍼로 제공 됩니다.

모델에 대 한이 앵커를 설정한 후에는 아래에 표시 된 중간 및 오른쪽 메시에서 이동 하는 클라우드 계층이 투영 됩니다.

![셸이 분리 된 Jupiter 개체 개요](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>질감

기존 질감이 세 부분으로 구성 된 질감 아틀라스로 분리 되었습니다. 상단 세 번째는 시차 효과를 제공 하기 위해 간격이 포함 된 클라우드 계층을 호스트 하 고, 가운데 섹션에는 빠른 이동 외부 스트림을 포함 하 고, 세 번째는 느린 내부 기본 계층을 포함 합니다.

특성에 적합 한 빨간색도 다양 한 이동 부분으로 분리 된 다음, 다른 경우에는 질감의 보이지 않는 영역에 삽입 되었습니다. 이러한 구성 요소는 아래 이미지의 가운데 섹션에서 빨강-toned speckles로 볼 수 있습니다.

각 밴드는 특정 방향과 속도를 가지 므로 각 메시에 개별적으로 질감을 적용 했습니다. 그러면 메시는 전체 표면에 애니메이션 효과를 concentrically 수 있는 공통 중심 및 피벗 점입니다.

![Jupiter 질감 개요](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>회전 및 질감 동작

이제 Jupiter의 시각적 컴퍼지션을 설정 했으므로 회전 및 궤도 속도가 적절히 계산 되어 적용 되었는지 확인 해야 했습니다. Jupiter가 전체 회전을 완료 하는 데 약 9 시간이 걸립니다. 이는 차등 회전으로 인 한 정의의 문제입니다. 따라서 적도 스트림이 ' 마스터 스트림 '으로 설정 되어 전체 회전에 대해 3600 프레임을 차지 합니다. 600, 900, 1200, 1800 등의 초기 위치를 일치 시키기 위해 다른 모든 계층에는 3600의 요소로 회전 속도가 필요 합니다.

![Jupiter shell 질감](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>멋진 빨간색 스폿

개별적으로 회전 하는 스트림은 좋은 시각적 느낌을 제공 하지만, 근접 범위에서 관찰 될 때 세부 정보는 부족 합니다.

가장 눈에 띄는 부분은 Jupiter의 훌륭한 레드를 위한 것 이므로이를 소개 하는 메시 및 질감 집합을 만들었습니다.
 
Jupiter의 밴드와 유사한 메커니즘을 사용 했습니다. 즉, 회전 하는 부분의 집합이 서로 위에 구성 되어 있고, ' 마스터 계층 ' 아래에도 그룹화 되어 있으므로 나머지는 이동 속도에 관계 없이 위치를 유지할 수 있습니다.

메시를 설정 하 고 설정 하면 stormy 소용돌이의 여러 계층이 적용 되 고 각 디스크는 개별적으로 애니메이션 효과를 준 다음 가운데에 세로로 애니메이션 효과를 준 후에는 바깥쪽으로 이동 하는 동안 점차 속도가 빨라집니다.

![Jupiter 뛰어난 레드 스폿 메시](images/ge-update-great-red-spot-mesh.jpg)

또한 컴포지션에는 다른 모든 메시와 동일한 피벗이 있었으며 원래 y-축 (!)에서 회전에 자유롭게 애니메이션 효과를 주는 데 사용할 수 있습니다. 3600 프레임은 기본 속도로, 각 계층에는 회전 기간을 포함 하는 요소가 있습니다.

![Jupiter 멋진 빨강 스폿 텍스처](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Unity에서 바로 가져오기

Unity에서 구현할 때 유의 해야 할 몇 가지 중요 한 사항이 있습니다.

Unity는 많은 투명 계층 집합을 처리할 때 쉽게 혼동 됩니다. 이 솔루션은 각 망상의 질감 재질을 복제 하 고 내부에서 바깥쪽으로 오름차순 렌더링 큐 값을 각 재질에 적용 하는 것 이었습니다.

그 결과 내부 셸에서는 렌더링 큐 값이 3000 (기본값)이 고, 나중에 정적 레드 toned 외부에서 3005 값을 가지 며, fast 흰색 외부 클라우드에 3010이 있습니다. 이 모델에서 값이 3025로 완료 되 면 빨간색 (내부에서 외부 계층으로 진행)이 완료 됩니다.

![Jupiter final 개체](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>최종 접촉

텍스처 된 Jupiter 계층은 처음에 설정 되었으며 구현에 충분 하지 않은 것으로 입증 되었습니다.

원래 행성 표준 셰이더 (및 모든 변형)는 MRTK 표준 셰이더가 지원 하지 않는 SunLightReceiver 스크립트를 통해 해당 조명 정보를 받습니다.

전 세계 표준 셰이더는 투명지를 사용 하는 질감 맵을 지원 하지 않으므로 셰이더를 교체 하는 것은 솔루션이 아닙니다. Jupiter 빌드를 의도 한 대로 수행 하기 위해이 셰이더를 편집 했습니다.

마지막으로, 소스 Blend를 10으로 설정 하 고 대상 Blend를 5로 설정 하 여 알파 혼합을 설정 해야 했습니다.

![Jupiter Unity 속성](images/ge-update-jupiter-unity-render-queue.jpg)

Galaxy 탐색기에서 Jupiter의 최종 렌더링을 확인할 수 있습니다.

## <a name="meet-the-team"></a>팀 충족 

혼합 현실 스튜디오 팀은 디자이너, 3D 아티스트, UX 전문가, 개발자, 프로그램 관리자 및 스튜디오 헤드로 구성 됩니다. 우리는 전 세계에서 벨기에, 캐나다, 독일, 이스라엘, 일본, 영국 및 미국. Microsoft는 다양 한 배경에서 제공 되는 여러 전문 분야 팀입니다. 게임-기존 및 비 주사위, 디지털 마케팅, 의료 및 과학을 모두 제공 합니다.

HoloLens 2 용 Galaxy 탐색기를 만들고 HoloLens (첫 번째 gen), VR 및 데스크톱 버전을 업데이트 합니다. 

![Galaxy 탐색기 팀](images/ge-update-team-image.png)

위에서 왼쪽에서 오른쪽으로: Artemis Tsouflidou (Developer), Angie Teickner (비주얼 디자이너), David Janer (UX 디자이너), 김 미 숙 Garrett (배달 & 프로덕션 리드), Yasushi Zonno (Creative 리드), Eline Ledent (개발자) 및 이혜준 Turner (선임 개발자).
왼쪽에서 오른쪽으로: Amit에서 (Technical 음악가), Martin Wettig (3D 음악가) 및 Dik Songuer (스튜디오 헤드).
추천 안 함: Tim Gerken (Tech 리드) 및 Oscar Salandin (비주얼 디자이너).

## <a name="additional-information"></a>추가 정보

### <a name="mixed-reality-studios"></a>혼합 현실 스튜디오

미국, 유럽 및 아시아 태평양에서 거주 하는 Microsoft Mixed Reality 스튜디오 팀은 사용자 환경 디자인, holographic 컴퓨팅, AR/VR 기술 및 3D 개발의 전문가입니다. 3D 자산 만들기, DirectX, Unity, Unreal 등을 포함 합니다. 고객이 조직 전체에 측정 가능한 영향을 만들 수 있도록 하는 동시에 원하는 미래를 구상 하 고 설계, 빌드 및 제공 하는 데 도움이 됩니다. 스튜디오는 엔터프라이즈 응용 프로그램 통합, 도입, 운영 및 지원에 대 한 22000 이상의 Microsoft 서비스 전문가와 긴밀 하 게 협력 합니다.
