---
title: 사용자 지정 홈 환경 추가
description: 제공 하는 Windows Mixed Reality 홈 환경 외에도 만들고 고유한를 사용 하 여 실험할 수 있습니다.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 홈, 사용자 지정 환경, 위치, cliff 집, skyloft, 사용자 만들기
ms.openlocfilehash: d0cdb878f1994cb5f898f06b98d74dee3dd4fdf1
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024533"
---
# <a name="add-custom-home-environments"></a>사용자 지정 홈 환경 추가

>[!NOTE]
>이 실험적 기능입니다. 체험해 보세요를 즐겁게 하며 모든 항목이 예상 대로 제대로 작동 하지 않더라도 놀라지 마세요. 이 기능과 되므로 사용에 대 한 관심의 실행 가능성을 평가 하는 것에 알려주세요 환경을 (및 발견 한 모든 버그)에 [개발자 포럼](https://forums.hololens.com/categories/custom-home-environments)합니다.

로 시작 합니다 [Windows 10 2018 년 4 월 업데이트](#release-notes-april-2018.md),으로 사용할 사용자 지정 환경 위치 선택 (시작 메뉴)를 추가할 수 있는 실험적인 기능을 활성화 했습니다는 [Windows Mixed Reality 홈](#navigating-the-windows-mixed-reality-home.md). Windows Mixed Reality Cliff 집 고 Skyloft 집으로 선택할 수 있는 두 가지 기본 환경에 있습니다. 사용자 지정 환경 만들기를 사용 하면 사용자 고유의 만들기를 사용 하 여 해당 목록을 확장 수 있습니다. 진행 중인이 사용할 수 있는 초기 상태 평가 창작자, 개발자의 관심 분야의 종류를 만들고 다른 제작 도구를 사용 하 여 작동 방식을 이해를 참조 하세요.

해당 텔레포트 보면 사용자 지정 환경을 사용 하는 경우 앱과 상호 작용 하 고 홀로그램 배치 Skyloft 고 Cliff 집에서와 마찬가지로 작동 합니다. 소설 환경에서 웹 사이트를 탐색 하거나 홀로그램 혁신적인 도시를 채울 수 있습니다-가능성은 무한!

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>사용자 지정 홈 환경</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>샘플 환경을 시도

사용자 지정 홈 환경의 창조적 가능성 중 일부를 보여 주는 샘플 환경을 만들었습니다. 작업을 수행 하려면 다음이 단계를 수행 합니다.
1. [예제 판타지 섬 환경 다운로드](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (링크가 자동 압축 풀기 실행 파일을 가리키는).

    ![소설을 섬 샘플 환경](images/FantasyLand.jpg)<br>
    *소설을 섬 샘플 환경*<br>

2. 실행 합니다 **Fantasy_Island.exe** 방금 다운로드 한 파일입니다.

    > [!NOTE]
    > (다음과 같은)는 웹에서 다운로드.exe 파일을 실행 하려고 하면 "Windows PC를 보호 하는 데 사용" 팝업을 발생할 수 있습니다. Fantasy_Island.exe이이 팝업에서를 실행 하려면 **자세한 내용은** 차례로 **실행**합니다. 이 보안 설정은 있으므로 신뢰 하지 않을 파일을 다운로드 하는 것을 방지 하기 것만이 옵션 선택 하십시오이 파일의 원본을 신뢰 하는 경우.

3. 오픈 **파일 탐색기** 주소 표시줄에 다음을 붙여 넣는 방법으로 환경 폴더로 이동 하 고: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`합니다.
4. 이 폴더에 다운로드 한 샘플 환경을 복사 합니다.
5. 다시 시작 **혼합 현실 포털**합니다. 이 위치 선택에서 환경 목록을 새로 고칩니다.
6. 헤드셋에 배치 합니다. 집에서 했으면 엽니다는 **시작 메뉴** 컨트롤러 단추는 Windows를 사용 하 여 합니다.
7. 선택 된 **자릿수** 홈 환경을 선택에 대 한 고정 된 앱 목록 위의 아이콘입니다.
8. 위치 목록에서 다운로드 한 판타지 섬 환경을 찾을 수 있습니다. 선택 **판타지 섬** 새 사용자 지정 홈 환경 입력!

## <a name="creating-your-own-custom-environment"></a>사용자 고유의 사용자 지정 환경 만들기

이 샘플 환경을 사용 하는 것 외에도 소프트웨어를 편집 하면 즐겨 찾는 3D를 사용 하 여 사용자 고유의 사용자 지정 환경을 내보낼 수 있습니다. 

### <a name="modeling-guidelines"></a>모델링 지침

환경을 모델링 하는 경우 다음 권장 사항에 유의 해야 합니다. 이렇게 하면 올바른 방향 believably 규모 환경에서 사용자 생성을 확인 하는 데 도움이 됩니다.

1. 사용자는 원점을 원하는 생성 위치 0,0,0 따라서 가운데에 배치 됩니다.
2. 작업 단위는 전 세계 규모의 자산을 작성할 수 있습니다 있도록 미터제로 설정 되어야 합니다.
3. 최대 축 "Y"로 설정 해야 합니다.
4. 자산 양의 Z 축 방향으로 "forward" 발생 해야 합니다.
5. 모든 메시를 결합할 필요는 없지만 리소스가 제한 된 장치를 대상으로 하는 경우 것이 좋습니다.

### <a name="exporting-your-environment"></a>환경 내보내기

Windows Mixed Reality 환경에 대 한 자산 배달 형식으로 이진 glTF (.glb)에 의존합니다. glTF는 사용료를 지불 Khronos 그룹에 의해 유지 관리 하는 3D 자산 배달에 대 한 무료 개방형 표준입니다. Windows 앱 및 환경에서 형식에 대 한 Microsoft의 지원 됩니다 glTF 업계 상호 운용 가능한 3D 콘텐츠에 대 한 표준으로 발전 합니다.

사용자 지정 홈 환경으로 사용할 자산을 내보내는 첫 번째 단계는 glTF 2.0 모델을 생성 합니다. GlTF 작업 그룹은 유지 관리를 [지원 되는 내보내기 도구 목록과 변환기](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) glTF 2.0 모델을 만듭니다. 시작 하려면이 페이지에 나열 된 프로그램 중 하나를 사용 하 여 만들고 glTF 2.0 모델 내보내기 또는 지원 되는 변환기 중 하나를 사용 하 여 기존 모델을 변환 합니다.

또한 체크 아웃 [유용한 기사의](https://www.khronos.org/blog/art-pipeline-for-gltf) Blender와 3DS glTF 모델 내보내기에 대 한 최신 워크플로 간략하게 제공 하는 직접 Max입니다. 

### <a name="environment-limits"></a>환경 제한

모든 환경에는 < 256 mb 여야 합니다. 256 mb 보다 큰 환경 로드 하 고 사용자와 관련 된 기본 skybox를 사용 하 여 빈 세계는 대체 되지 것입니다. 모델을 만들 때이 파일 크기 제한을 염두에서 하세요 유지 합니다. 또한 아래 설명 된 대로 WindowsMRAssetConverter를 사용 하 여 사용자 환경 최적화 하려는 경우 최적화 프로그램이 더 큰 파일 크기를 갖지만 더 빠르게 로드 하는 질감을 만듭니다 질감 크기를 증가 인식 해야 합니다. 

### <a name="optimizing-your-environment"></a>사용자 환경 최적화

Windows Mixed Reality를 다양 한 환경의 부하 시간을 크게 줄일 수 있는 선택적 최적화를 지원 합니다. 이 경우에 따라은 로드 하는 동안 시간 초과 많은 질감을 사용 하 여 환경에 특히 중요 수 있습니다. 그러나 적거나 저해상도 질감을 사용 하 여 소규모 환경의 않습니다 항상 필요한, 일반적으로 모든 자산에 대해이 단계가 좋습니다. 

이 과정을 더 쉽게 만들었습니다 합니다 [Windows 혼합 현실 자산 변환기 (GitHub에서 사용 가능)](https://github.com/Microsoft/glTF-Toolkit/releases) 프로그램 최적화를 수행 합니다. 이 도구는 추가 질감 압축, 압축 및 아래쪽 크기 조정 확인을 수행 하 여 모든 표준 2.0 glTF 또는.glb을 최적화 하기 위해 Microsoft glTF 도구 키트에서 사용할 수 있는 유틸리티 집합을 사용 합니다. 

변환기는 현재 다양 한 최적화가 정확한 동작을 조정 하는 플래그를 지원 합니다. 최상의 결과 위해 다음 플래그를 사용 하 여 실행을 사용 하는 것이 좋습니다.

Flag|권장된 값|설명
---|---|---
-max-texture-size|1024 또는 2048| 질감의 품질을 개선 하기 위해이 조정, 기본값은 512 x 512입니다. 더 큰 값을 환경 파일 크기를 크게 영향을 참고 따라서 염두 256mb 제한
-최소 버전|1803|사용자 지정 환경 버전의 windows 에서만 지원 됩니다 > 1803 =. 이 플래그는 이전 버전의 질감을 제거 하 고 최종 자산의 파일 크기를 줄이기

예를 들어 다음과 같은 가치를 제공해야 합니다.

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>테스트 환경

최종.glb 환경을 만든 후 헤드셋에서 테스트할 준비가 되었습니다. 2 단계에서 시작 합니다 ["샘플 환경을 동안"](#trying-a-sample-environment) 홈 혼합된 현실으로 사용자 지정 환경을 사용 하는 섹션입니다. 

## <a name="feedback"></a>사용자 의견

이 실험적 기능을 평가 하는 것을 하는 동안 사용자 지정 환경에서 발생할 수 있는 버그를 사용 하는 방법을 학습에 관심이 및 원하는 기능입니다. 만들기 및 사용자 지정 홈 환경에서 사용에 대 한 모든 의견을 [개발자 포럼](https://forums.hololens.com/categories/custom-home-environments)합니다.

## <a name="troubleshooting-and-tips"></a>문제 해결 및 팁

### <a name="how-do-i-change-the-name-of-the-environment"></a>환경의 이름을 변경 하려면 어떻게 해야 합니까?

환경 폴더에 파일 이름은 위치 선택에서 사용 됩니다. 환경의 이름을 변경 하려면 단순히 환경 이름 바꾸기 파일 이름, 다시 시작 후 혼합 현실 포털 합니다.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>위치 선택 내에서 사용자 지정 환경을 어떻게 제거 합니까?

사용자 지정 환경을 제거 하려면 PC의 환경 폴더를 엽니다 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 환경을 삭제 하 고 있습니다. 혼합 현실 포털을 다시 시작 하면이 환경 위치 선택에서 더 이상 표시 됩니다. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>내 즐겨 찾는 사용자 지정 환경 기본값으로 하는 방법

현재 기본 환경을 변경할 수 없습니다. 혼합 현실 포털을 다시 시작할 때마다 Cliff 집 환경에 반환 되는 합니다. 

### <a name="i-spawn-into-a-blank-space"></a>빈 공간에 생성 하나요

Windows Mixed Reality [256mb를 초과 하는 환경을 지원 하지 않습니다](#environment-limits)합니다. Environment이이 제한을 초과 하는 경우 모델이 없는 빈 하늘 상자에서 이동 합니다.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>내 환경에 로드 하는 데 시간이 오래 걸리는

선택적 최적화를 더 빠르게 로드 되도록 환경에 추가할 수 있습니다. 참조 ["환경의 최적화"](#optimizing-your-environment) 세부 정보에 대 한 합니다.

### <a name="the-scale-of-my-environment-is-incorrect"></a>내 환경의 규모 올바르지 않습니다.

Windows Mixed Reality 환경을 로드할 때 glTF 단위 1 미터를 변환 합니다. 환경을 로드는 예기치 않은 확장을 다시 확인 되도록에 내보내기 하는 경우 1 미터 규모로 모델링 합니다. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>내 환경에서 생성 위치가 잘못 되었습니다.

기본 생성 위치는 환경의 0,0,0에 있습니다. 해당 현재 불가능 환경의 원하는 생성 시점에 배치 하 여 원본과 내보내 생성 시점을 수정 해야 하므로이 위치를 사용자 지정할 수 있습니다.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>오디오 환경의 올바른 보인다는 것

사용자 지정 환경을 만들면 사용자가 만든 실제 공간 일치 하지 않는 소음 렌더링 시뮬레이션을 사용 됩니다. Sound 잘못 된 방향에서 가져올 수 있습니다 및 들리지만 muffled 합니다. 

## <a name="see-also"></a>참조
* [Windows 혼합 현실 자산 변환기 (github)](https://github.com/Microsoft/glTF-Toolkit/releases)

