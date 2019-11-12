---
title: 다중 사용자 기능 자습서-2. Unity를 개발할 준비 하는 중
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 91935cb5b465e51d3948f68b818f93ba52b215f1
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914414"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Unity를 개발할 준비 하는 중 


이 자습서에서는 혼합 현실 도구 키트 가져오기, 빌드 설정 구성 및 장면 준비를 포함 하 여 응용 프로그램 개발을 위해 Unity를 준비 하 고 구성 하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

- 응용 프로그램 개발을 위한 Unity 구성

- Mixed Reality Toolkit 가져오기

- 프로젝트 장면 준비

## <a name="instructions"></a>지침

1. 여기를 클릭 하 여 Mixed Reality Toolkit Foundation unity 패키지를 다운로드 하 고 저장 합니다 [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)

2. Unity에서 자산 메뉴를 클릭 하 고 패키지 가져오기를 선택한 다음 사용자 지정 패키지를 클릭 합니다.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 1 단계에서 제공한 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다. Unity에 가져오기 팝업 창이 표시 되 면 가져오기 단추를 클릭 하 여 MRTK 가져오기를 시작 합니다. 몇 분 정도 걸릴 수 있습니다.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 참고: 다운로드 한 패키지는 파일을 저장 한 로컬 폴더에 있습니다. 위의 이미지는 패키지를 찾을 위치를 표시 된다 하지 않습니다.

4. 새 장면을 만듭니다. 파일을 클릭 하 고 새 장면을 선택 하 여이 작업을 수행할 수 있습니다. HLSharedProjectMain로 저장 합니다.

> 참고: 아래 이미지와 비슷한 팝업을 받을 수 있습니다. 지금은 아니요를 클릭 합니다.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Mixed Reality Toolkit에서 장면에 추가 및 구성을 클릭 합니다.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 완료 되 면 프로필을 사용자 지정할 수 있는 새 구성 파일이 표시 됩니다. 

![Module2Chapter1step4im](images/Module2Chapter1step4im.PNG)

7. 계층에서 혼합-현실 도구 키트 (MRTK)를 선택 합니다. 검사기 패널에서 Mixed Reality Toolkit 스크립트를 찾아 아래 그림에 표시 된 것 처럼 "& 사용자 지정 복사" 단추를 누릅니다.  이 작업 뒤에 pop가 나타나고 팝업 메뉴에서 복제 옵션을 선택 합니다.

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

7. 아래로 스크롤하여 진단 창을 숨기려면 진단 시스템 사용을 선택 취소 합니다. 응용 프로그램을 개발 하는 동안 진단 창을 사용 하도록 설정 하 여 성능을 모니터링 한 다음 프로덕션 또는 응용 프로그램 데모 중에 사용 하지 않도록 설정 하는 것이 좋습니다. 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Ctrl + shift + B를 누르거나 파일 > 빌드 설정으로 이동 하 여 빌드 설정을 엽니다. 프로그램은 현재 PC, Mac 및 Linux 독립 실행형 플랫폼 아래에 설정 되어 있습니다. HoloLens 2 개발의 경우 플랫폼을 유니버설 Windows 플랫폼로 설정 합니다. 선택한 후 플랫폼 전환을 클릭 합니다.

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 완료 되 면 열려 있는 장면 추가 라는 상자를 클릭 합니다. 이제 검사기 패널로 이동 하 여 지원 되는 가상 현실 오른쪽에 있는 확인란이 선택 되어 있는지 확인 합니다 (아래 이미지에 표시 됨). 또한 아래 이미지에 나와 있는 것 처럼 장면/HLSharedProjectMain 옆의 확인란도 선택 되어 있는지 확인 합니다.

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. 검사기 패널의 게시 설정 섹션에서 기능으로 스크롤하고 다음 확인란이 표시 되어 있는지 확인 합니다.

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. 여기에서 다운로드할 수 있는 SharingAssetCollection 이라는 사용자 지정 패키지를 가져옵니다 [.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. 프로젝트 패널에서 Prefabs 폴더로 이동 합니다. 다음 단계에서는 장면에 몇 가지 prefabs을 구현 합니다. Prefabs 폴더에서 prefab, 디버그 창을 클릭 하 여 계층으로 끕니다. 완료 되 면 파일을 클릭 한 다음 저장을 클릭 하거나 ctrl + S를 눌러 프로젝트를 저장 합니다.

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 참고: prefab를 클릭 하면 TMP Essentials에 대 한 정보를 요청 하는 팝업이 표시 될 수 있습니다. 필요에 따라 TMP Essentials 가져오기를 클릭 합니다. 이 팝업이 표시 되 면 계층 구조에서 prefab을 삭제 하 고 텍스트 관련 오류 발생을 방지 하기 위해 계층으로 다시 끌어 야 할 수 있습니다.
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>축하합니다.

이제 Unity 프로젝트를 Photon 준비가 되었습니다. 향후 자습서에서는이 장면 및 Unity 프로젝트를 전체 공유 환경에 구축 합니다.

[다음 자습서: 3. 여러 사용자 연결](mrlearning-sharing(photon)-ch3.md)

