---
title: HoloLens 학습을 위한 Azure 공간 앵커 (HoloLens) 2
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
# <a name="photon-correct-me-if-im-wrong"></a>Photon (잘못 된 경우 문제 해결)

이 단원에서는 

목표로

* __________________________________________________________________________

* ______________________________________________________________________

  

## <a name="instructions"></a>지침

### <a name="setting-up-photon"></a>Photon 설정

1. [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정을 설정 합니다. 이 작업은 전자 메일을 채우기 하 고 몇 가지 확인 단계를 진행 하는 것으로 구성 됩니다.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. 등록 하면 Sdk를 클릭 합니다. 해당 페이지를 클릭 한 후 "서버"를 클릭 하 고 "자체 호스팅" 이라는 메시지가 표시 되는지 확인 합니다. 아래 두 번째 이미지에 표시 된 대로 아래로 스크롤하여 "서버"를 클릭 합니다.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. 그러면 텍스트 상자가 "읽기" 라는 레이블이 표시 됩니다. 계속 해 서 읽어 보세요. 완료 되 면 "downloadSDK" 옆의 링크를 클릭 하 여 다운로드 합니다.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. 다운로드가 완료 되 면 폴더를 두 번 클릭 합니다.  SDK 폴더를 노출 하는 파일 탐색기가 열리면 SDK 폴더를 복사 합니다.
   
   - 다음 단계는 windows C: 드라이브로 이동 하 고 ' server ' 라는 새 폴더를 만드는 것입니다.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - 이제 폴더를 열고 이전에 복사한 SDK 폴더를 붙여넣습니다.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. 이 작업이 완료 되 면 SDK 폴더를 열고 "deploy", "bin_Win64"로 이동한 다음 "photon control"을 두 번 클릭 합니다.


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> 참고: IP 주소 또는 기타 유사한 질문에 대 한 질문이 있는 경우 도구 모음에서 대부분의 정보를 찾을 수 있습니다 (아래 이미지 참조).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. 서버를 설정 하 고 시작 했으므로 이제 Photon 웹 사이트로 돌아가서 프로필 아이콘 (아래 이미지에서 boxed)을 클릭 하 고 "응용 프로그램"을 선택 합니다.
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. "새 앱 만들기" 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - "Photon type." 아래의 드롭다운 메뉴에서 "Photon 실행"을 선택 합니다. 그런 다음 이름을 지정 합니다 (기억할 항목). 이 예제에서는 이름이 "HoloLensPhotonProject"로 지정 되었습니다. 완료 되 면 "만들기"를 클릭 합니다.

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. 작업이 완료 되 면 응용 프로그램 페이지로 돌아가 아래 그림과 유사한 내용이 표시 되어야 합니다. 앱 ID를 클릭 하 고 복사 합니다. 쉽게 액세스할 수 있는 위치에 붙여 넣을 수 있습니다.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. 새 unity 프로젝트를 만듭니다. Unity 허브를 열고 "새로 만들기"를 클릭 합니다. 이름을 "HLSharingProject"로 합니다. 그런 다음 만들기를 클릭 합니다. 

   > 두고 컴퓨터 속도에 따라 로드 하는 데 최대 2 분이 걸릴 수 있습니다.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> 참고: "위치" 옵션을 변경 하 여 컴퓨터에 프로젝트를 저장할 위치를 선택 합니다. 저장 하 고 쉽게 액세스할 수 있는 위치에 저장 합니다.

10. 프로젝트가 로드 되 면 "자산 저장소"를 클릭 합니다. 그런 다음 아래 이미지에 표시 된 검색 상자에 "THIS"를 입력 하 고 "Photon THIS-2 FREE" 자산을 선택 합니다. 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. 다운로드 하 여 가져오세요.
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Unity 프로젝트 설정** 

11. 여기를 클릭 하 여 Unity에서 Photon를 설정 하는 데 필요한 새 자산을 다운로드 [합니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. Unity에서 자산 메뉴를 클릭 하 고 "자산 가져오기"를 선택한 다음 "사용자 지정 자산"을 클릭 합니다.

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. 1 단계에서 제공한 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다. Unity에 가져오기 단추가 표시 되 면 클릭 합니다.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> 참고: 패키지를 다운로드 하는 위치는 어디에 위치 합니다. 위의 이미지는 패키지를 찾을 위치를 표시 된다 하지 않습니다.

14. 새 장면을 만듭니다 .이 작업은 control/command + N을 사용 하거나 "파일"을 클릭 하 고 "새 장면"을 선택 하 여 수행할 수 있습니다. 장면을 "HLSharedProjectMain"로 저장 합니다.

> 참고: 아래 이미지와 비슷한 팝업을 받을 수 있습니다. 지금은 "아니요"를 클릭 하면 됩니다.
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. "Mixed Reality Toolkit"에서 "장면에 추가 및 구성"을 클릭 합니다.

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. 완료 되 면 프로필을 사용자 지정할 수 있는 새 구성 파일이 표시 됩니다. "복사 및 사용자 지정"을 클릭 합니다.

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. 아래로 스크롤하여 "진단 시스템 사용"을 선택 취소 합니다. 이를 통해이 프로젝트를 쉽게 설정할 수 있습니다.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. 빌드 설정을 엽니다 (컨트롤 + shift + B). 프로그램이 현재 "PC, Mac 및 Linux 독립 실행형" 플랫폼에서 설정 되어 있는지 확인 합니다. 이 프로젝트의 경우 플랫폼을 "유니버설 windows 플랫폼"으로 설정 합니다. 이를 선택 하 고 "플랫폼 전환"을 클릭 합니다.

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. 완료 되 면 "열려 있는 장면 추가" 라는 상자를 클릭 합니다. 이제 검사기 패널로 이동 하 여 아래 이미지에 표시 된 것 처럼 "가상 현실 지원"의 오른쪽에 있는 확인란이 선택 되어 있는지 확인 합니다. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> 두고 또한 "장면/HLSharedProjectMain" 옆의 확인란도 선택 되어 있는지 확인 합니다.

20. 검사기 패널의 "게시 설정" 아래에서 "기능"으로 스크롤하고 다음 확인란만 표시 되어 있는지 확인 합니다.

- 인터넷 클라이언트
- 인터넷 클라이언트 서버
- 개인 네트워크 클라이언트 서버
- 카메라/웹캠
- 마이크

21. 12 단계와 마찬가지로 다음 단계는 [여기]를 다운로드할 수 있는 "2 단원" 라는 다른 사용자 지정 패키지를 가져오는 것입니다. [2 단원. unitypackage 링크를 여기로 이동] 해당 패키지를 가져옵니다.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. 이제 프로젝트 패널에서 "prefabs" 폴더로 이동 합니다. 다음 몇 단계에서 장면에 몇 가지 prefabs를 구현 합니다. "Prefabs" 폴더에서 prefab "DebugWindow"를 클릭 하 고 계층으로 끕니다. 완료 되 면 프로젝트를 저장 합니다 (파일, 저장 또는 컨트롤 + S 클릭).

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> 두고 Prefab를 클릭 하면 TMP Essentials에 대 한 정보를 요청 하는 팝업이 표시 될 수 있습니다. 필요에 따라 "TMP Essentials 가져오기"를 클릭 합니다.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**여러 사용자 연결**

23. 22 단계와 마찬가지로 프로젝트 패널의 "prefabs" 폴더에서 다음 단계는 "NetworkLobby" prefab을 계층에 끌어서 놓는 것입니다. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. 부모 prefab "NetworkLobby"를 열면 자식 prefab "Networklobby"이 표시 됩니다. 선택 된 상태에서 검사기 패널로 이동 하 고 "구성 요소 추가"를 클릭 합니다. "PhotonView"를 검색 하 고 구성 요소를 추가 합니다.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. 계층 구조에 비어 있는 게임 개체를 새로 만듭니다 (계층을 마우스 오른쪽 단추로 클릭 하 고 "빈" 선택). 위치 지정이 x = 0, y = 0, z = 0으로 설정 되어 있는지 확인 하 고 개체 이름을 "PhotonUser"로 지정 합니다.

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>축하합니다.



