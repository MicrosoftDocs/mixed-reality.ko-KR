---
title: 다중 사용자 기능 자습서-1. Photon Unity 네트워킹 설정
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 57a23e34404e4bff653d74b7f6afc65adff8b19c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334335"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Photon Unity 네트워킹 설정

## <a name="overview"></a>개요

이 자습서에서는 THIS (Photon Unity 네트워킹)를 Unity 프로젝트로 가져와 공유 환경을 만들기 위해 준비 하는 방법에 대해 설명 합니다. Photon는 혼합 현실 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다. Photon 계정을 만들고, Photon를 가져오고, 선택적 로컬 서버를 만드는 방법에 대해 알아봅니다.

## <a name="objectives"></a>목표

* Photon 계정을 만드는 방법 알아보기
* Photon Unity 네트워킹을 찾고 가져오는 방법 알아보기
* 로컬 Photon 서버 설정

## <a name="prerequisites"></a>전제 조건

>[!TIP]
>초보자를 위한 [자습서](mrlearning-base.md) 시리즈를 아직 완료 하지 않은 경우 해당 자습서를 먼저 완료 하는 것이 좋습니다.

* 올바른 [도구로](install-the-tools.md) 구성 된 WINDOWS 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 C# 기본 프로그래밍 기능
* [개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode) HoloLens 2 장치

>[!IMPORTANT]
>이 자습서 시리즈에는 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> 이 필요 하며 권장 버전은 unity 2019.1.14입니다. 이렇게 하면 위에 연결 된 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항이 나 권장 사항이 대체 됩니다.

## <a name="setting-up-photon"></a>Photon 설정

1. [Photon](https://dashboard.photonengine.com//Account/SignUp) 계정을 설정 합니다. [이 링크](https://dashboard.photonengine.com//Account/SignUp)를 클릭 하 여 Photon 등록 페이지로 이동 합니다. 등록 페이지의 지침에 따라 계정을 만듭니다.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 새 앱 만들기 단추를 클릭 하 여 응용 프로그램 ID를 만듭니다.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. 드롭다운 메뉴의 Photon 형식에서 Photon THIS을 선택 합니다. 그런 다음 이름을 지정 합니다. 이 예제에서는 HoloLensPhotonProject 라는 이름을 지정 했습니다. 완료 되 면 만들기 단추를 클릭 합니다.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 응용 프로그램 페이지로 돌아가 아래 그림과 유사한 내용이 표시 되어야 합니다. 응용 프로그램 ID를 클릭 하 고 복사 합니다. 쉽게 액세스할 수 있는 위치에 붙여 넣습니다.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 새 unity 프로젝트를 만들고 이름을 HLSharingProject로 만듭니다. 새 Unity 프로젝트를 만드는 방법에 대 한 지침은 [기본 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)을 참조 하세요. 

6. 프로젝트가 로드 되 면 아래 그림에 표시 된 것 처럼 자산 저장소 탭을 클릭 합니다. 그런 다음 아래 이미지에 강조 표시 된 검색 상자에 THIS를 입력 하 고 검색 결과에서 Photon THIS 2-FREE "자산을 선택 합니다.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. 다운로드 및 가져오기 단추를 눌러이 자산을 다운로드 하 고 가져옵니다.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon 가져오기 프로세스가 완료 되 면 This 마법사가 나타납니다. 4 단계에서 응용 프로그램 ID (클립보드에 있어야 함)를 사용 하 여 AppID 상자에 붙여넣은 다음 프로젝트 설치 단추를 누릅니다.

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. AppID를 성공적으로 추가한 후 Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings (자산)로 이동 합니다. 이름 서버 사용 옵션을 선택 하 고 고정 지역을 US 또는 photon 서비스 지역으로 설정 합니다.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>축하합니다.

Photon 계정을 성공적으로 만들고, 로컬 Photon 서버를 설정 하 고, THIS를 Unity로 가져왔습니다. 다음 단계는 여러 사용자가 작업을 볼 수 있도록 프로젝트를 설정 하 고 다른 사용자와의 연결을 허용 하는 것입니다.

[다음 자습서: 2. Unity를 개발할 준비 하는 중](mrlearning-sharing(photon)-ch2.md)
