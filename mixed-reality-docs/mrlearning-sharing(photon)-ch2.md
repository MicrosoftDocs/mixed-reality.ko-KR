---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327117"
---
# <a name="getting-unity-ready-for-development"></a>**Unity 개발을 위한 준비** 

이 단원에서는 준비, 혼합 현실 도구 키트를 가져오기 하 고, 빌드 설정을 구성 하 고,이 장면 준비를 포함 하 여 앱 개발을 위해 Unity를 구성 하는 방법을 배웁니다.

목표:

- 앱 개발에 대 한 Unity를 구성 합니다.

- Mixed Reality Toolkit 가져오기

- 프로젝트 장면 준비

### <a name="instructions"></a>지침

1. 다운로드 하 고 클릭 하 여 혼합 현실 Toolkit unity 패키지를 저장 [여기 있습니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)
2. Unity에서 자산 메뉴 및 "패키지 가져오기," 선택 클릭 "사용자 지정 패키지입니다."

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 1 단계에서 제공 된 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다. Unity에서 가져오기 팝업 창이 표시 되 면 가져오기를 시작 하려면 [가져오기] 단추를 클릭 합니다. 가져오기는 MRTK 몇 분 정도 걸릴 수 있습니다.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 참고: 파일을 저장 한 로컬 폴더에 다운로드 한 패키지가 됩니다. 위의 이미지에서 패키지를 찾을 수 있습니다 표시 되지 않습니다.

4. (이 가능 "file"을 클릭 하 고 "새 장면을"를 선택 하 여) 새 장면을 만듭니다. 장면 "HLSharedProjectMain."로 저장

> 참고: 아래 이미지와 비슷하게 보이는 팝업을 나타날 수 있습니다. 이제 클릭 "아니요"
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. "혼합 현실 Toolkit" 클릭 "장면에 추가 및 구성"에서

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 완료 되 면 새 구성 파일을 나타납니다 프로필에 맞게 선택할 수 있도록 합니다. "복사 및 사용자 지정 합니다."를 클릭 합니다.

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. 아래로 스크롤하여 "사용" 진단 시스템 진단 창을 숨기려면 싶다면의 선택을 취소 합니다. 진단 창이 성능을 모니터링 하려면 앱 개발 동안 사용 하도록 설정 하 고 프로덕션 또는 응용 프로그램 데모 중 해제 상태로 유지 하는 것이 좋습니다.

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. 컨트롤 + shift + B를 눌러 또는 파일로 이동 하 여 빌드 설정 > 빌드 설정 합니다. 프로그램 "PC, Mac 및 Linux 독립 실행형" 플랫폼에서 현재 설정 되어 있는지 확인 합니다. HoloLens 2 개발을 위한 플랫폼 "유니버설 Windows 플랫폼"으로 설정 선택 하 고 "플랫폼 전환 합니다." 클릭

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. 완료 되 면 "open 장면을 추가 합니다." 라는 상자를 클릭 이제 검사기 패널로 이동 하 고 (아래 이미지에 표시 된)으로 "지원 되는 가상 reality"의 오른쪽에 확인란을 했는지 확인 됩니다. 또한 아래 이미지에 표시 된 대로 "장면/HLSharedProjectMain" 옆의 확인란 선택도 되어 있는지 확인 합니다.

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. 검사기 패널 스크롤합니다 "기능" 섹션에서 "게시 설정" 하 고 다음 확인란 표시 되는지 확인 합니다.
    - 인터넷 클라이언트
       
       - 인터넷 클라이언트 서버
       
       - 개인 네트워크 클라이언트 서버
   
       - camera/webcam

       - 마이크
   
   11. "2 단원" 다운로드할 수 있는 다음 호출에서는 사용자 지정 패키지를 가져옵니다. TODO: 자산 팩에 대 한 링크를 제공 합니다.
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. 이제 프로젝트 패널에서 이동 "prefabs" 폴더에 다음 몇 단계에서 구현 장면에 몇 가지 prefabs 하므로 합니다. "Prefabs" 폴더에서 클릭 하 고 prefab, "DebugWindow" 계층으로 끌어 옵니다. 완료 되 면 프로젝트를 저장 합니다 (파일을 저장 한 다음 클릭 또는 컨트롤 + S를 눌러)
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > 참고: 클릭 하면 prefab, TMP Essentials에 대 한 요청을 표시 하는 팝업을 볼 수 있습니다. 필요한 경우는 "가져오기 TMP Essentials"를 클릭 합니다. 이 팝업이 나타나면 해야를 prefab 계층 구조에서 삭제를 다시 잠재적인 텍스트 관련 오류를 방지 하려면 계층으로 끕니다.
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>축하합니다.

Unity 프로젝트 Photon 준비가 완료 되었습니다! 앞 단원에서는이 장면 및 전체 공유 경험을 위해 Unity 프로젝트에 빌드 해 보겠습니다.

[다음 단원: Sharing(Photon) 단원 3](mrlearning-sharing(photon)-ch3.md)

