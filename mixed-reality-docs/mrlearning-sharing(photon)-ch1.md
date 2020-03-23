---
title: 다중 사용자 기능 자습서 - 1. Photon Unity 네트워킹 설정
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031336"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Photon Unity 네트워킹 설정

## <a name="overview"></a>개요

이 자습서에서는 PUN(Photon Unity 네트워킹)을 Unity 프로젝트로 가져와서 공유 환경을 만들기 위해 준비하는 방법에 대해 알아봅니다. Photon은 Mixed Reality 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다. Photon 계정을 만들고, Photon을 가져오고, 필요에 따라 로컬 서버를 만드는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* Photon 계정을 만드는 방법 알아보기
* Photon Unity 네트워킹을 찾고 가져오는 방법 알아보기
* 로컬 Photon 서버 설정

## <a name="prerequisites"></a>필수 구성 요소

>[!TIP]
>[시작 자습서](mrlearning-base.md) 및 [Azure Spatial Anchors 시작 자습서](mrlearning-asa-ch1.md) 시리즈를 아직 시작하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.

* 올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC
* Windows 10 SDK 10.0.18362.0 이상
* 몇 가지 기본 C# 프로그래밍 기능
* [개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스

>[!IMPORTANT]
> 이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다. 이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.

## <a name="setting-up-photon"></a>Photon 설정

1. [Photon](https://dashboard.photonengine.com//Account/SignUp) 계정을 설정합니다. [이 링크](https://dashboard.photonengine.com//Account/SignUp)를 클릭하여 Photon 가입 페이지로 이동합니다. 가입 페이지의 지침에 따라 계정을 만듭니다.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. [새 앱 만들기] 단추를 클릭하여 애플리케이션 ID를 만듭니다.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. [Photon 유형] 아래의 드롭다운 메뉴에서 Photon PUN을 선택합니다. 그런 다음, 이름을 지정합니다. 이 예에서는 HoloLensPhotonProject라는 이름을 지정했습니다. 완료되면 [만들기] 단추를 클릭 합니다.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 애플리케이션 페이지로 돌아가면 아래 그림과 비슷하게 표시됩니다. 애플리케이션 ID를 클릭하여 복사합니다. 이를 쉽게 액세스할 수 있는 위치에 붙여넣습니다.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 새 Unity 프로젝트를 만들고, HLSharingProject라는 이름을 지정합니다. 새 Unity 프로젝트를 만드는 방법에 대한 지침은 [기본 모듈의 "Unity 프로젝트 만들기" 섹션](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)을 참조하세요. 

6. 프로젝트가 로드되면 아래 이미지와 같이 [자산 저장소] 탭을 클릭합니다. 그런 다음, 아래 이미지에서 강조 표시된 검색 상자에서 PUN을 입력하고, 검색 결과에서 "Photon PUN 2 - FREE" 자산을 선택합니다.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. [다운로드] 및 [가져오기] 단추를 눌러 이 자산을 다운로드하고 가져옵니다.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon에서 가져오기 프로세스가 완료되면 Pun 마법사가 표시됩니다. 4단계에서 애플리케이션 ID(클립보드에 있음)를 가져와서 AppID 상자에 붙여넣고 [프로젝트 설정] 단추를 누릅니다.

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. AppID가 성공적으로 추가되면 Assets에서 Photon->PhotonUnityNetworking->Resources->PhotonServerSettings으로 차례로 이동합니다. [이름 서버 사용] 옵션을 선택하고, 고정 지역을 미국 또는 Photon 서비스 지역으로 설정합니다.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>축하합니다.

Photon 계정을 성공적으로 만들고, 로컬 Photon 서버를 설정하고, PUN을 Unity로 가져왔습니다. 다음 단계는 여러 사용자가 작업을 볼 수 있도록 프로젝트를 설정하고 다른 사용자와의 연결을 허용하는 것입니다.

[다음 자습서: 2. Unity 개발 준비](mrlearning-sharing(photon)-ch2.md)
