---
title: MR Learning ASA 모듈 2 HoloLens에 Azure 공간 앵커
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327098"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (수정 나 잘못 된 경우)

이 단원에서는 

목표:

* 에 대해 알아봅니다 ___ 하는 방법

* 에 대해 알아봅니다 ___ 하는 방법

  

## <a name="instructions"></a>지침

### <a name="setting-up-photon"></a>Photon 설정

1. 설정 된 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정. 이 전자 메일 imputing 및 몇 가지 확인 단계를 거치지 구성 됩니다.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. 등록 하면 Sdk 클릭 합니다. 해당 페이지에 있는 경우 "서버" 클릭 하 고 "자체 호스트 합니다." 라는 있는지 확인 아래로 스크롤한 다음 하 고 "server" 두 번째 이미지 아래에 표시 된 대로 클릭 합니다.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. "추가 정보입니다." 레이블이 지정 된을 표시할 입력란에 일으키는 계속 해 서 읽어야 합니다. 완료 되 면 다운로드 하는 것 "downloadSDK" 옆에 있는 링크를 클릭 합니다.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. 다운로드가 완료 되 면 폴더를 두 번 클릭 합니다.  SDK 폴더를 표시 합니다. 파일 탐색기 열리면 SDK 폴더를 복사 합니다.
   
   - 다음 단계 '서버입니다.' 라는 새 폴더를 만들고 windows c: 드라이브를 이동 하는 것
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - 이제 폴더를 열고 앞에서 복사한 SDK 폴더에 붙여 넣습니다.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. 완료 되 면 SDK 폴더를 열고 "배포" 다음 "bin_Win64 가"로 이동 하 고 "photon 컨트롤입니다."를 두 번 클릭


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> 참고: 대부분의 프로그램 정보 (아래 이미지에 표시) 하는 대로 IP 주소에 대 한 질문이 나 다른 비슷한 질문이 있으면 도구 모음에서 찾을 수 있습니다.
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. 서버를 설정 및 시작 했으므로 Photon 웹 사이트로 다시 이동 하 고 (아래 이미지에서는 boxed) 프로필 아이콘을 클릭 하 고 "응용 프로그램입니다."를 선택
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. "새 앱 만들기" 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - "Photon 형식입니다." 아래에 있는 드롭다운 메뉴에서 "Photon 실행" 선택 다음 (것을 기억해) 이름을 지정 합니다. 이 예에서는 이라는 "HoloLensPhotonProject." 완료 되 면 "만들기"를 클릭

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. 작업이 완료 되 면 응용 프로그램 페이지로 돌아가서 아래 그림과 같은 결과가 표시 됩니다. 앱 ID를 클릭 하 고 복사 합니다. 붙여넣기가 쉽게 액세스할 수 있는 곳입니다.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. 새 unity 프로젝트를 만듭니다. Unity 허브를 열고 "new." 클릭 이름을 "HLSharingProject." 클릭 한 다음 만듭니다. 

   > 참고: 이 로드 하려면 최대 2 분 컴퓨터 속도에 따라를 걸릴 수 있습니다.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> 참고: "위치" 옵션을 변경 하 여 컴퓨터에서 프로젝트를 저장할 위치를 선택 합니다. 기억 하 고 쉽게 액세스 하는 저장 합니다.

10. 프로젝트 로드 되 면 클릭 "자산 저장소"입니다. 그런 다음 아래 그림과에서 같이 검색 상자에 "예제"를 입력 하 고 "Photon 예제 2 무료" 자산을 선택 합니다. 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. 다운로드 및 가져오기!
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Unity 프로젝트 설정** 

11. 클릭 하 여 Unity의 Photon을 설정 하는 데 필요한 새 자산을 다운로드 [여기 있습니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. Unity에서 자산 메뉴 및 가져오기 자산을 "클릭"자산에 사용자 지정 합니다."

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. 1 단계에서 제공 된 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다. 가져오기 단추에 표시 되 면 Unity 되 면 클릭 합니다.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> 참고: 찾을 있는 됩니다 패키지를 다운로드 하는 위치입니다. 위의 이미지에서 패키지를 찾을 수 있습니다 표시 되지 않습니다.

14. 새 장면을 만드는 (컨트롤을 사용 하 여 / 명령 + 수 N 또는 "file"을 클릭 하 고 "새 장면을."를 선택 하 여). 장면 "HLSharedProjectMain."로 저장

> 참고: 아래 이미지와 비슷한 팝업이 표시 될 수 있습니다. 이제 클릭 "아니요"입니다.
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. "혼합 현실 Toolkit" 클릭 "장면에 추가 및 구성"에서

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. 완료 되 면 새 구성 파일을 나타납니다 프로필에 맞게 선택할 수 있도록 합니다. "복사 및 사용자 지정 합니다."를 클릭 합니다.

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. 아래로 스크롤하여 "진단 시스템을 사용 합니다." 선택을 취소합니다 이 쉽게이 프로젝트를 설정 합니다.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. 빌드 설정 (control + shift + B)를 엽니다. 프로그램 "PC, Mac 및 Linux 독립 실행형" 플랫폼에서 현재 설정 되어 있는지 확인 합니다. 이 프로젝트에 플랫폼 "유니버설 windows 플랫폼입니다."으로 설정 선택 하 고 "플랫폼 전환 합니다." 클릭

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. 완료 되 면 "open 장면을 추가 합니다." 라는 상자를 클릭 이제 검사기 패널로 이동 하 고 (아래 이미지에 표시 된)으로 "지원 되는 가상 reality"의 오른쪽에 확인란을 했는지 확인 됩니다. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> 참고: 또한 "장면/HLSharedProjectMain" 옆의 확인란도 선택 되어 있는지 확인 합니다.

20. 아래 검사기 패널에서 "게시 설정" "기능"까지 아래로 스크롤하여 다음 확인란만 표시 되는지 확인 합니다.

- 인터넷 클라이언트
- 인터넷 클라이언트 서버
- 개인 네트워크 클라이언트 서버
- camera/webcam
- 마이크

21. 12 단계와 마찬가지로 다음 단계는 "2 단원" [여기]. 다운로드할 수 있습니다를 호출 하는 다른 사용자 지정 패키지를 가져올 것 [lesson2.unitypackage 링크 위치] 해당 패키지를 가져옵니다.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. 이제 프로젝트 패널에서 이동 "prefabs" 폴더에 다음 몇 단계에서 구현 장면에 몇 가지 prefabs 하므로 합니다. "Prefabs" 폴더에서 클릭 하 고 prefab, "DebugWindow" 계층으로 끌어 옵니다. 완료 되 면 프로젝트를 저장 합니다 (클릭 파일을 다음 저장 또는 컨트롤 + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> 참고: 클릭 하면 prefab, TMP Essentials에 대 한 요청을 표시 하는 팝업을 볼 수 있습니다. 필요한 경우는 "가져오기 TMP Essentials"를 클릭 합니다.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**여러 사용자를 연결합니다.**

23. 프로젝트 패널에서 "prefabs" 폴더에 22 단계와 같이 다음 단계에서 끌어서 놓기 "NetworkLobby" prefab 계층에는입니다. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. 자식 prefab, "NetworkRoom." 표시 "NetworkLobby," 부모 prefab을 열어야 하는 경우 검사기 패널로 이동 하 고 "구성 요소를 추가 합니다."를 클릭 후 선택 "PhotonView"를 검색 하 고 구성 요소를 추가 합니다.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. 계층 구조 (계층 및 "empty" 선택에서 마우스 오른쪽 단추로 클릭)에서 새 빈 게임 개체를 만듭니다. 위치를 x로 설정 해야 = 0, y = 0, z = 0 및 "PhotonUser." 개체 이름

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>축하합니다.



