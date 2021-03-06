---
title: 사례 연구-HoloTour
description: HoloTour for Microsoft HoloLens는 전 세계의 아이콘 위치에 대 한 모던 3D 개인 둘러보기를 제공 합니다. 이 사례 연구에서는 HoloTour에 사용 되는 콘텐츠를 캡처하고 만드는 과정을 안내 합니다.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed 현실
ms.openlocfilehash: 59c3dffd48009aa792643ea27b59f8f6f85b64d7
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278191"
---
# <a name="case-study---holotour"></a>사례 연구-HoloTour

HoloTour for Microsoft HoloLens는 전 세계의 아이콘 위치에 대 한 모던 3D 개인 둘러보기를 제공 합니다. 이 프로젝트에서 작업 하는 디자이너, 아티스트, 생산자, 오디오 디자이너 및 개발자가 발견 되 면 잘 알려진 위치에 대 한 convincingly 실제 3D 렌더링을 만드는 것은 독창적인 및 기술적 wizardry의 고유한 blend를 사용 합니다. 이 사례 연구에서는 HoloTour에 사용 되는 콘텐츠를 캡처하고 만드는 과정을 안내 합니다.

## <a name="the-tech"></a>기술

HoloTour를 사용 하 여 사용자는 자신의 거실에서 바로, 페루의 Machu 좋아요, 현대 [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) 의 [유적](https://en.wikipedia.org/wiki/Machu_Picchu) 등 세계에서 가장 놀라운 대상 중 일부를 방문할 수 있게 되었습니다. Microsoft 팀은 "HoloTour"에 대 한 목표를 달성 했습니다. 사진이 나 비디오 이상의 환경을 제공 해야 합니다. HoloLens의 고유한 표시, 추적 및 오디오 기술을 활용 하 여 다른 위치로 사용자를 거의 전송할 수 있습니다. 방문한 모든 위치의 위권, 사운드 및 3 차원 기 하 도형을 캡처하고 앱 내에서 다시 만들어야 합니다.

이렇게 하려면 방향성 오디오 캡처가 있는 360 ° 카메라 rig가 필요 합니다. 중철 아티팩트를 최소화 하기 위해 장면이 HoloLens에서 재생 될 때 선명 하 게 보이도록 카메라를 가까이 배치 해야 하기 때문에 매우 높은 해상도로 캡처해야 했습니다. 수평 뿐만 아니라 위와 아래에 있는 전체 구면 적용을 원했습니다. 또한 rig는 전 세계 전체를 사용할 수 있도록 이식 가능 해야 합니다. 제공 되는 무료 옵션을 평가 하 고 해결, 비용 또는 크기 때문에 비전을 실현할 만큼 충분 하지 않은 것으로 인식 했습니다. 요구를 충족 하는 카메라 rig를 찾을 수 없는 경우에는 직접 구축 해야 합니다.

### <a name="building-the-rig"></a>Rig 빌드

집어넣었을, Velcro, 덕트 테이프 및 14 GoPro 카메라에서 만든 첫 번째 버전은 매우. 낮은 종료 솔루션에서 사용자 지정 제조 된 rig까지 모든 항목을 검토 한 후에는 GoPro 카메라가 작고 경제적 이며 사용 하기 쉬운 메모리 저장소가 있기 때문에 궁극적으로 가장 적합 한 옵션 이었습니다. 작은 폼 팩터는 카메라를 긴밀 하 게 가깝게 두는 것이 가능 하기 때문에 특히, 카메라 간의 거리가 작을수록 중철 아티팩트가 작아집니다. 고유한 카메라 정렬을 통해 카메라를 지능적으로 정렬 하 고 중철 프로세스 중에 일부 아티팩트를 원활 하 게 조정할 수 있도록 전체 구 범위 *와* 충분 한 중복을 얻을 수 있었습니다.

HoloLens의 [공간 음향](spatial-sound.md) 기능을 활용 하는 것은 convincingly 실제 몰입 형 환경을 만드는 데 매우 중요 합니다. Tripod 카메라 아래에 4 개의 마이크 배열을 사용 했습니다 .이는 카메라 위치에서 4 방향으로 소리를 캡처하여 장면에서 공간 소리를 만들 수 있는 충분 한 정보를 제공 합니다.

![360 ° 카메라 rig는이 filming 외부에 있습니다.](images/camera-pantheon-200px.png)

360 ° 카메라 rig는이 filming 외부에 있습니다. 


Homemade rig는 시애틀 근처의 Rattlesnake로 이동 하 여 하이킹 맨 위에 있는 장면 캡처를 통해 테스트 했습니다. 결과는 현재 HoloTour에 표시 되는 위치 보다 훨씬 더 간단 하지만, 의도 한 대로 rig 디자인이 충분 하다는 것을 확신 했습니다.

Microsoft에서는 Velcro 및 집어넣었을에서 3D로 인쇄 된 카메라 하우징로 업그레이드 하 고, GoPro 카메라에 대 한 외부 배터리 팩을 구입 하 여 배터리 관리를 간소화 합니다. 그런 다음 더 광범위 한 테스트를 수행 하 여 샌프란시스코와 아이콘 골든 성문 브리지의 작은 투어를 만들어 샌프란시스코로 이동 했습니다. 이 카메라 rig는 HoloTour에서 방문 하는 위치의 대부분의 캡처에 사용 됩니다.

![360 ° 카메라 rig filming Machu](images/camera-machu-pichu-500px.png)

360 ° 카메라 rig filming Machu 

## <a name="behind-the-scenes"></a>백그라운드 작업

Filming 하기 전에 가상 둘러보기에 포함 하려는 위치를 파악 해야 했습니다. 로마는 처음에는 제공 하고자 하는 첫 번째 위치이 고,이 위치를 사용 하 여 scouting를 미리 수행 하기로 결정 했습니다. 사용자가 고려 하 고 있는 사이트에 대 한 사용자의 방문을 위해 아티스트, 디자이너 및 생산자를 비롯 한 6 명의 팀을 보냈습니다. Filming에 대 한 나머지는 여행에 대 한 9 일 – 2.5입니다. (Machu에 대 한 microsoft는 정찰을 수행 하지 않도록 하 고, 미리 연구 하 여 filming에 대 한 몇 일의 버퍼를 예약 했습니다.)

로마에서 팀은 각 영역에 대 한 사진을 받고 관심 있는 팩트와 관심 있는 팩트와 crowds 또는 제한으로 인해 각 지점으로 이동 하는 것과 같은 실질적인 사항을 고려 하는 것이 좋습니다. 이는 휴가 처럼 들리지만 많은 작업을 수행 합니다. 매일 아침에 시작 된 일은 저녁까지 중단 되지 않습니다. 매일 밤에는 팀을 위해 시애틀에 다시 검토를 위해 푸티지가 업로드 되었습니다. 

![로마의 캡처 crew.](images/holotour-filming-crew-rome-500px.jpg) 

로마의 캡처 crew. 


정찰 병이 완료 된 후에는 실제 filming에 대 한 최종 요금제를 만들었습니다. 이 작업을 수행 하려면 영화에 대 한 자세한 목록, 날짜 및 시간을 입력 해야 합니다. 매일 해외 마다 비용이 많이 들기 때문에 이러한 여행을 효율적으로 수행 해야 합니다. 일출 전부터 전까지 모든 날에 사용할 수 있도록 로마에서 가이드와 처리기를 예약 했습니다. 정말 좋은 느낌을 얻기 위해 최상의 푸티지를 제공 해야 합니다.

### <a name="capturing-the-video"></a>비디오 캡처

캡처 중 몇 가지 간단한 작업을 수행 하면 사후 처리를 훨씬 더 쉽게 수행할 수 있습니다. 예를 들어 여러 카메라의 이미지를 함께 연결할 때마다 각 카메라에 약간 다른 보기가 있으므로 시각적 아티팩트가 발생 합니다. 더 가까이 있는 개체는 카메라에 대 한 것 이며, 뷰 간의 차이가 클수록 중철 아티팩트가 커집니다. 문제를 시각화 하는 쉬운 방법은 다음과 같습니다. 얼굴 앞에서 엄지 단추를 누르고 한 눈에 볼 수 있습니다. 이제 눈동자를 전환 합니다. 배경을 기준으로 이동 하는 것이 표시 됩니다. 얼굴에서 멀리 떨어진 곳을 보유 하 고 실험을 반복 하는 경우 엄지 단추는 아래로 이동 하는 것 처럼 보입니다. 이러한 분명 한 이동은 직면 한 중철 문제와 비슷합니다. 카메라와 마찬가지로 눈에는 거의 거리가 구분 되어 있으므로 정확히 동일한 이미지가 표시 되지 않습니다.

사후 처리에서이를 해결 하는 것 보다 filming 하는 동안에는 최악의 아티팩트를 방지 하는 것이 더 쉬울 것 이기 때문에, 사용자와 카메라에서 멀리 떨어져 있는 항목을 유지 하려고 시도 했습니다. 카메라에 대 한 큰 선택을 유지 하는 것은 가장 큰 문제 중 하나 이며, 이러한 문제를 해결 하기 위해 창조적으로 노력 해야 했습니다. 로컬 가이드를 사용 하는 것은 crowds를 관리 하는 데 큰 도움이 되었지만 기호 (간혹 작은 원추 또는 bean)를 사용 하 여 filming 공간을 매우 효율적으로 표시 하는 것이 좋습니다. 가장 좋은 캡처를 얻는 가장 좋은 방법은 대부분의 사용자가 표시 하기 전에 아침에 매우 빨리 도착 하는 것입니다.

일부 다른 유용한 캡처 기술은 기존 필름 관행에서 바로 제공 됩니다. 예를 들어 모든 카메라에서 색 수정 카드를 사용 하 고 나중에 필요할 수 있는 텍스처 및 개체에 대 한 참조 사진을 캡처 했습니다. 

![색 수정 카드를 표시 하는 Machu의 대략적인 잘라내기입니다.](images/rough-cut-machu-picchu-500px.png)

중철 하기 전에 푸티지에 대 한 대략적인 잘림입니다.

### <a name="processing-the-video"></a>비디오 처리

360 ° 콘텐츠 캡처는 첫 번째 단계입니다. HoloTour에 표시 되는 최종 자산으로 캡처된 원시 카메라 푸티지를 변환 하려면 많은 처리가 필요 합니다. 이전 집에는 14 개의 다른 카메라 피드에서 비디오를 촬영 하 고 최소한의 아티팩트를 갖춘 단일 연속 비디오로 전환 해야 했습니다. Microsoft의 예술 팀은 캡처된 푸티지를 결합 하 고 폴란드어 위해 많은 도구를 사용 했으며 최대한 많은 처리를 최적화 하기 위해 파이프라인을 개발 했습니다. 푸티지를 함께 연결 되어 하 고, 색을 수정한 후, 복잡 한 요소와 아티팩트를 제거 하거나, 수명 및 동작의 보조 포켓을 추가 하는 것이 좋습니다.

![중철 하기 전에 푸티지에 대 한 대략적인 잘림입니다.](images/rough-cut-pantheon-500px.png)

중철 하기 전에 푸티지에 대 한 대략적인 잘림입니다. 


비디오를 결합 하기 위해 [Ptgui](https://www.ptgui.com/) 라는 도구를 사용 하 여 처리 파이프라인에 통합 했습니다. 사후 처리의 일환으로 비디오에서 아직 프레임을 추출 하 고 해당 프레임 중 하나에 적합 한 중철 패턴을 찾았습니다. 그런 다음 해당 패턴을 작성 한 사용자 지정 플러그 인에 적용 했습니다. 그러면 After Effects에서 합성 하는 동안 비디오 아티스트가 중철 패턴을 직접 미세 조정 하 고 조정할 수 있습니다. 

![연결 되어을 보여 주는 PTGui의 스크린샷.](images/stitching-tool-pantheon-500px.png)

연결 되어을 보여 주는 PTGui의 스크린샷. 


### <a name="video-playback"></a>비디오 재생

푸티지의 처리가 완료 된 후에는 원활한 비디오가 있지만 8K 해상도를 상당히 합니다. 비디오를 디코딩하는 데는 비용이 많이 들고, 8K 비디오를 처리할 수 있는 컴퓨터가 거의 없기 때문에 다음 과제는 HoloLens에서이 비디오를 다시 재생 하는 방법을 찾을 수 있습니다. 사용자가 전체 비디오를 보는 것과 같은 느낌을 주는 동시에 디코딩 비용을 방지 하기 위해 다양 한 전략을 개발 했습니다.

가장 쉬운 최적화는 크게 변경 되지 않는 비디오의 일부를 디코딩하는 것을 방지 하는 것입니다. 동작이 거의 또는 전혀 없는 각 장면의 영역을 식별 하는 도구를 작성 했습니다. 이러한 지역에는 각 프레임의 비디오를 디코딩하는 대신 정적 이미지를 표시 합니다. 이러한 작업을 가능 하 게 하기 위해 큰 비디오를 훨씬 더 작은 청크로 나눕니다.

또한 디코딩 한 모든 픽셀이 가장 효과적으로 사용 되었는지 확인할 수 있습니다. 비디오 크기를 낮추는 압축 기술로 실험. 프로젝션 되는 기 하 도형의 다각형에 따라 비디오 영역을 분할 합니다. 다른 polygon의 양에 따라 UVs를 조정 하 고 비디오를 다시 압축 했습니다. 이 작업의 결과는 단일 8k 비디오로 시작 되는 항목이 장면에 올바르게 다시 프로젝션 될 때까지 거의 이해할 수 없는 여러 청크로 설정 된 것입니다. 질감 매핑 및 UV 압축을 이해 하는 게임 개발자의 경우이는 잘 느껴질 것입니다. 

![최적화 전에 표시 되는의 전체 뷰입니다.](images/pantheon-before-optimization-500px.png) 

최적화 전에 표시 되는의 전체 뷰입니다. 


![비디오 재생을 위해 처리 된의 오른쪽 절반입니다.](images/pantheon-process-video-playback-500px.png) 

비디오 재생을 위해 처리 된의 오른쪽 절반입니다. 


![최적화 및 압축 후의 단일 비디오 영역 예제입니다.](images/single-video-region-after-optimization-500px.png) 

최적화 및 압축 후의 단일 비디오 영역 예제입니다. 


자주 보고 하지 않는 비디오를 디코딩하는 것을 방지 하기 위해 사용 하는 또 다른 트릭을 사용 했습니다. HoloTour 중에는 지정 된 순간에 전체 장면의 일부만 볼 수 있습니다. 시야 (시야) 내에서 또는 그 밖의 경우에만 비디오를 디코딩합니다. 머리를 회전할 때 현재 FOV에 있는 비디오의 영역을 재생 하 고 더 이상 없는 비디오의 재생을 중지 하기 시작 합니다. 대부분의 사람들은 이러한 상황이 발생 하는 것을 볼 수 있지만 신속 하 게 전환 하는 경우 비디오를 시작 하는 데 두 번째 시간이 소요 되는 것을 볼 수 있습니다. 그 후에는 고정 이미지가 표시 되 고 일단 준비 되 면 비디오를 다시 페이드 아웃 합니다.

이 전략을 활용 하기 위해 광범위 한 비디오 재생 시스템을 개발 했습니다. 비디오 전환을 매우 효율적으로 수행 하기 위해 낮은 수준의 재생 코드를 최적화 했습니다. 또한 언제 든 지 비디오로 신속 하 게 전환할 수 있도록 비디오를 특별 한 방식으로 인코딩해야 했습니다. 이 재생 파이프라인은 개발 시간이 상당히 많기 때문에 단계에서 구현 했습니다. 효율적이 지는 않지만 디자이너 및 음악가는 환경에서 작업 하는 데 사용할 수 있는 간단한 시스템으로 시작 했으며, 최종 품질 막대에서 제공 하도록 허용 하는 더 강력한 재생 시스템으로 천천히 개선 되었습니다. 이 최종 시스템에는 장면 내에서 비디오를 설정 하 고 재생 엔진을 모니터링 하기 위해 Unity 내에서 만든 사용자 지정 도구가 있습니다.

### <a name="recreating-near-space-objects-in-3d"></a>3D에서 공간 근처의 개체 다시 만들기

비디오는 HoloTour에 표시 되는 대부분의 기능을 구성 하지만, Piazza Navona의 그리기, 판 외부의 분수 또는 항공 장면에 대해 사용자가 제공 하는 핫 공기 풍선을 비롯 하 여 가까이에 표시 되는 많은 3D 개체가 있습니다. 이러한 3D 개체는 인간 깊이 인식을 매우 유용 하지만 멀리 떨어져 있지 않기 때문에 중요 합니다. 거리에 비디오를 사용할 수 있지만 사용자가 공간을 중심으로 이동할 수 있도록 하 고, 주변 개체에는 깊이가 필요 합니다. 이 기술은 자연 기록 박물관에서 볼 수 있는 것과 유사 합니다. diorama는 실제 landscaping, 식물 및 동물 specimens를 전경으로 포함 하지만 백그라운드에서 영리 마스킹된 무광택 그리기로 recedes 합니다.

일부 개체는 환경을 개선 하기 위해 만들고 장면에 추가 된 3D 자산입니다. Filmed 때 그리기 및 핫 공기 풍선이 표시 되지 않기 때문에이 범주에 속합니다. 게임 자산과 마찬가지로 팀의 3D 음악가에 의해 생성 되 고 적절 하 게 텍스처 됩니다. 이러한 항목은 어디에서 든 지 가까이에 놓고 게임 엔진은 3D 개체로 표시 되도록 두 HoloLens 표시로 렌더링할 수 있습니다.

외부에 있는 분수와 같은 기타 자산은 비디오를 촬영 하는 위치에 존재 하는 실제 개체 이지만 비디오에서 3D로 이러한 개체를 가져오기 위해 몇 가지 작업을 수행 해야 합니다.

먼저 각 개체에 대 한 추가 정보가 필요 합니다. Filming에 대 한 위치에 있는 동안 팀은 이러한 개체의 많은 참조 푸티지를 캡처 했으므로 텍스처를 정확 하 게 다시 만들 수 있는 충분 한 상세 이미지가 있습니다. 또한 수십 개의 2D 이미지에서 3D 모델을 생성 하는 [photogrammetry](https://en.wikipedia.org/wiki/Photogrammetry) 검색을 수행 하 여 완전 한 규모에서 개체의 대략적인 모델을 제공 합니다.

푸티지를 처리할 때 나중에 3D 표현으로 교체 되는 개체는 비디오에서 제거 됩니다. 3D 자산은 photogrammetry 모델을 기반으로 하지만 아티스트에서 정리 하 고 간소화 합니다. 일부 개체의 경우에는 분수의 워터 무늬와 같은 비디오의 일부를 사용할 수 있지만 대부분의 분수는 이제 사용자가 깊이를 잘 알 수 있고 경험을 위해 제한 된 공간을 탐색할 수 있는 3D 개체입니다. 이 처럼 공간에 가까운 개체가 있으면 현실감의 의미에 크게 추가 되며 가상 위치의 사용자를 파악 하는 데 도움이 됩니다. 

![분수를 제거 하 여 푸티지를 제거 합니다. 3D 자산으로 대체 됩니다.](images/object-removal-pantheon-500px.png)

분수를 제거 하 여 푸티지를 제거 합니다. 3D 자산으로 대체 됩니다.


## <a name="final-thoughts"></a>최종 생각

여기에서 설명 하는 것 보다 더 많은 콘텐츠를 만들 수 있습니다. 몇 가지 장면을 사용 합니다. 즉, 핫 비행기 풍선을 타는 것을 비롯 하 여 "불가능 한 큐브 뷰"를 호출 하 고, Colosseum에 대 한 글이 싸 워 하 여 더 독창적인 방법을 사용 했습니다. 향후 사례 연구에서 이러한 사항을 해결 합니다.

프로덕션 중에 발생 한 몇 가지 큰 문제에 대 한 솔루션을 공유 하는 것이 다른 개발자에 게 유용 하 고, 이러한 기술 중 일부를 사용 하 여 HoloLens를 위한 고유한 몰입 형 환경을 만드는 것이 좋습니다. (이 경우 [HoloLens 앱 개발 포럼](https://forums.hololens.com/)에서 공유 하 고 있는지 확인 하세요.)

## <a name="about-the-authors"></a>작성자 정보

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> 는 HoloTour에서 작업 하는 것을 고려 하 여 카메라 rig 및 비디오 재생에 대해 자세히 살펴본 선임 개발자입니다.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> 는 로마를 통한 이동이 가능한 한 이상 인지 한 비디오 음악가입니다.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> 는 나중에 다시 방문 하는 경우에도 방문 하는 모든 대상의 soundscape를 경험할 수 있도록 하는 오디오 디자이너입니다.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis 스타 이너</b> 는 위치를 연구 하 고 scouted 하 고, 여행 계획을 작성 하 고, 사이트에서 지시 된 filming를 담당 하는 디자인 감독</td>
</tr>
</table>



## <a name="see-also"></a>참고 항목
* [비디오: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
