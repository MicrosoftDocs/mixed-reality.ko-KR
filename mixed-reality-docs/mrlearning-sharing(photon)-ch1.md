---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523294"
---
#  <a name="setting-up-photon-unity-networking"></a>Photon Unity 네트워킹 설정

이 자습서에서는 Unity 프로젝트로 Photon Unity 네트워킹 (예제)를 가져와서 공유 환경을 만들기 위한 준비 방법에 알아봅니다. Photon 몇 가지 네트워킹 옵션 혼합 현실 개발자에 게 사용할 수 있는 공유 환경을 만들 수 중 하나입니다. 에서는 Photon 계정을 만들려면 Photon을 가져오고 선택적 로컬 서버를 만드는 방법 설명

목표:

* Photon 계정을 만드는 방법 알아보기

* 찾기 및 Photon Unity 네트워킹을 가져오는 방법 알아보기

* 로컬 Photon 서버 설정

  

### <a name="setting-up-photon"></a>Photon 설정

1. 설정 된 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) 계정. Photon 등록 페이지를 클릭 하 여 이동할 [이 링크](https://dashboard.photonengine.com/en-US/Account/SignUp)합니다. 계정을 만들려면 등록 페이지의 지침을 따릅니다. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 새 앱 단추 만들기를 클릭 하 여 응용 프로그램 ID를 만듭니다.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Photon 예제 Photon 형식 아래에서 드롭다운 메뉴에서 선택 합니다. 그런 다음 이름을 지정 합니다. 이 예에서는 라는 HoloLensPhotonProject 합니다. 완료 되 면 만들기 단추를 클릭 합니다.

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 작업이 완료 되 면 응용 프로그램 페이지로 돌아가서 아래 그림과 같은 결과가 표시 됩니다. 응용 프로그램 ID를 클릭 하 고 복사 합니다. 붙여넣기가 쉽게 액세스할 수 있는 곳입니다.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 새 unity 프로젝트를 만들고 HLSharingProject 라는 이름을 지정 합니다. 새 Unity 프로젝트를 만드는 방법에 대 한 자세한 내용은를 참조 하십시오 [자료 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)합니다. 

6. 아래 이미지에 나와 있는 것 처럼 자산 저장소 탭의 프로젝트 로드 되 면 클릭 합니다. 검색 결과에서 그런 다음 아래 이미지에서 강조 표시 하 고 검색 상자에 예제를 입력 한 Photon 예제 2-빈도 선택"자산입니다. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. 다운로드 하 고 다운로드 및 가져오기 단추를 눌러이 자산을 가져옵니다.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon 가져오기 프로세스가 완료 되 면 예제 마법사가 나타납니다. 4 단계에서 응용 프로그램 ID (해야 하는 클립보드에)를 수행 하 고 AppID 상자에 붙여넣습니다. 설치 프로젝트 단추를 누릅니다. 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Photon AppID를 성공적으로 추가한 후 이동할 PhotonUnityNetworking->-> 리소스에는 자산에 PhotonServerSettings-> 합니다. 옵션을 사용 하 여 이름 서버를 선택 하 고 우리에 게 고정 된 지역 또는 yourPphoton 서비스 지역 설정 합니다.

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>축하합니다.

성공적으로 Photon 계정을 만들지, 로컬 Photon 서버를 설정 했으며 Unity에 예제를 가져옵니다. 다음 단계는 프로젝트를 설정 하 고 여러 사용자가 작업을 볼 수 있도록 한 다음 다른 사용자와 연결을 허용 하는 것입니다. 

[다음 자습서의 경우: Unity 개발을 위한 준비](mrlearning-sharing(photon)-ch2.md)

