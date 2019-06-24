---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327464"
---
# <a name="setting-up-photon"></a>Photon 설정

이 단원에서는에서는 Unity 프로젝트로 Photon Unity 네트워킹 (예제)를 가져와서 공유 환경을 만들기 위한 준비 하는 방법을 배웁니다. Photon 몇 가지 네트워킹 옵션 혼합 현실 개발자에 게 사용할 수 있는 공유 환경을 만들 수 중 하나입니다. 에서는 Photon 계정을 만들려면 Photon을 가져오고 선택적 로컬 서버를 만드는 방법 설명

목표:

* Photon 계정을 만드는 방법에 알아봅니다.

* 찾기 및 Photon Unity 네트워킹을 가져오는 방법 알아보기

* 로컬 Photon 서버 설정

  

### <a name="setting-up-photon"></a>Photon 설정

1. 설정 된 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정. Photon 등록 페이지를 클릭 하 여 이동할 [이 링크](https://dashboard.photonengine.com/en-US/Account/SignUp)합니다. 계정을 만들려면 등록 페이지의 지침을 따릅니다. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. 등록 하면 Sdk 클릭 합니다. 해당 페이지에 있는 경우 "서버" 클릭 하 고 "자체 호스트 합니다." 라는 있는지 확인 아래로 스크롤한 다음 하 고 "server" 두 번째 이미지 아래에 표시 된 대로 클릭 합니다.

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. "추가 정보입니다." 레이블이 지정 된을 표시할 입력란에 일으키는 계속 해 서 읽어야 합니다. 완료 되 면 다운로드 하는 것 "downloadSDK" 옆에 있는 링크를 클릭 합니다.


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. 다운로드가 완료 되 면 폴더를 두 번 클릭 합니다.  SDK 폴더를 표시 합니다. 파일 탐색기 열리면 SDK 폴더를 복사 합니다.
   
   - 다음 단계 '서버입니다.' 라는 새 폴더를 만들고 windows c: 드라이브를 이동 하는 것
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - 이제 폴더를 열고 앞에서 복사한 SDK 폴더에 붙여 넣습니다.
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. 완료 되 면 SDK 폴더를 열고 "배포" 다음 "bin_Win64 가"로 이동 하 고 "photon 컨트롤입니다."를 두 번 클릭


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> 참고: 대부분의 프로그램 정보 (아래 이미지에 표시) 하는 대로 IP 주소에 대 한 질문이 나 다른 비슷한 질문이 있으면 도구 모음에서 찾을 수 있습니다.
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. 서버를 설정 및 시작 했으므로 Photon 웹 사이트로 다시 이동 하 고 여전히 등록 되어 있는지 확인 (또는 다시에 로그인 하지 않은 경우) (아래 이미지의 오른쪽 위 모서리의 boxed) 프로필 아이콘을 클릭 하 고 "응용 프로그램입니다."를 선택 합니다.
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. "새 앱 만들기" 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - "Photon 형식입니다." 아래에 있는 드롭다운 메뉴에서 "Photon 예제"를 선택 합니다. 그런 다음 이름을,이 예에서 "HoloLensPhotonProject." 라는 것 완료 되 면 "만들기" 단추를 클릭 합니다.

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. 작업이 완료 되 면 응용 프로그램 페이지로 돌아가서 아래 그림과 같은 결과가 표시 됩니다. 앱 ID를 클릭 하 고 복사 합니다. 붙여넣기가 쉽게 액세스할 수 있는 곳입니다.  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. 새 unity 프로젝트를 만들고 이름을 "HLSharingProject." 새 Unity 프로젝트를 만드는 방법에 대 한 자세한 내용은를 참조 하십시오 [자료 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)합니다. 


10. 아래 이미지에 표시 된 대로 "자산 저장소" 탭의 프로젝트 로드 되 면 클릭 합니다. 그런 다음 아래 이미지에서 강조 표시 하 고 검색 상자에 "예제"를 입력 하 고 검색 결과에서 "Photon 예제 2 무료" 자산을 선택 합니다. 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. 다운로드 하 고 있는 "다운로드" 및 "가져오기" 단추를 눌러이 자산을 가져옵니다.
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>축하합니다.

성공적으로 Photon 계정을 만들지, 로컬 Photon 서버를 설정 했으며 Unity에 예제를 가져옵니다. 다음 단계는 프로젝트를 설정 하 고 여러 사용자가 작업을 볼 수 있도록 한 다음 다른 사용자와 연결을 허용 하는 것입니다. 

[다음 단원: Sharing(Photon) 단원 2](mrlearning-sharing(photon)-ch2.md)

