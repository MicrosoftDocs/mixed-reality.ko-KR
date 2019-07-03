---
title: MR Learning ASA 모듈 HoloLens 2 Azure 공간 앵커
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: f8a52660fe05b6ed4508321ed246b8e299b75bca
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523337"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. 저장, 검색 및 공유 Azure 공간 앵커

이 자습서에서는에서는 HoloLens 2의 디스크에 우리의 앵커 정보를 저장 하 여 여러 앱 세션에서이 Azure 공간 앵커를 저장 하는 방법을 알아봅니다. 또한 다중 장치 앵커 맞춤에 대 한 다른 장치에이 앵커 정보를 공유 하는 방법을 배웁니다.

## <a name="objectives"></a>목표

* 저장 하 고 응용 프로그램 세션 간에 유지에 HoloLens 2 로컬 디스크에서 Azure 공간 앵커 정보를 검색 하는 방법을 알아봅니다

* 다중 장치 시나리오에서 사용자 간에 Azure 공간 앵커 정보를 공유 하는 방법 알아보기

  

## <a name="instructions"></a>지침

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>디스크에 앵커 ID 저장-응용 프로그램 세션 간에 Azure 앵커를 유지 합니다.

1. 검색 하 고 SaveAnchorToDisk prefab 장면에 추가 합니다. 여기에 두 개의 단추, HoloLens 2 디스크 및 디스크에서 모든 Id를 검색 하는 것에 대 한 다른 모든 사용 가능한 Azure 앵커 Id를 저장 하기 위한 단추가 하나 포함 됩니다.

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. 아래 지침에 따라 각 단추 구성
   - SaveToDisk 라는 단추의 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 SaveAzureAnchorIDToDisk() 메서드를 할당 합니다.
   
     > 참고: 다른 단추는 장면에서 겹치는 일부 단추가 나타납니다. 자유롭게 단추의 위치를 조정할 수 있습니다.
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - GetFromDisk 라는 단추의 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 LoadAzureAnchorIDsFromDisk() 메서드를 할당 합니다.

3. 장치에 업데이트 된 응용 프로그램을 빌드하려면 Tutoiral 1에서 지침을 따릅니다. Azure 앵커 만들기 단추를 누르면 이전 단원에서 수행한 것 처럼 지금 저장 수 Azure 앵커 ID를 디스크에 저장 디스크 단추를 눌러 합니다.

4. 응용 프로그램을 다시 로드 앵커 ID 키를 눌러 Azure 세션을 시작 디스크에 저장 하는 ID와 연결 된 앵커를 찾으려고 Azure 앵커 찾을 키를 누릅니다. 장면 전체 이제 맞추려면 위치를 위치에 저장 앵커 이전!

### <a name="share-azure-anchors-between-multiple-devices"></a>여러 장치 간에 Azure 앵커를 공유 합니다.

이 섹션에서는 여러 장치 간에 Azure 앵커 ID를 공유 하는 방법을 알아보겠습니다. 이렇게 하면 Azure는 동일한 앵커 ID를 쿼리 하는 여러 장치는 고정된 홀로그램 및 백그라운드에서 부분적으로 정렬 될 수 있습니다. (여러 장치 간에 같은 물리적 위치에 동일한 홀로그램 표시) 하는 공간 맞춤은 HoloLens 2에서 공유 키를 로컬 환경입니다. 자습서는 Azure 공간 앵커 공유 환경에 설명 된 메서드를 포함 하 여 장치 간의 azure Id에 관한 정보를 전송 하는 방법은 여러 가지 (할 일: 링크를 추가 합니다.) 이 예제에서는 업로드 및 장치 간에 앵커 Id를 다운로드 하는 간단한 웹 서비스를 사용 합니다.

1. 계층에 ShareAnchor prefab을 추가 합니다. 이 prefab 장면;에 두 개의 새 단추를 추가합니다. 앵커 ID 정보 및 다운로드에 대 한 다른 업로드에 대 한 ID 정보를 고정 합니다. 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. 아래 지침에 따라 각 단추 구성

   - SendSharedAnchor, 라는 단추 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 ShareAnchor() 메서드를 할당 합니다.

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - GetSharedAnchor, 라는 단추 클릭 이벤트 트리거 뿐만 아니라 단추 누름 이벤트 트리거 아래에서 새 이벤트를 만듭니다. 빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 GetSharedAzureAnchor() 메서드를 할당 합니다.

3. 지침을 따릅니다 [자습서 1](mrlearning-base-ch1.md)합니다. 장치에 업데이트 된 응용 프로그램을 빌드하려면. Azure 앵커 만들기 단추를 누르면 이전 단원에서와 같이 공유할 수 있습니다 이제 다른 장치에 Azure 앵커 ID는 다른 장치에 공유 단추를 눌러.

   > 참고: 선택 하 고 부모 앵커 부모 앵커 스크립트까지 아래로 스크롤합니다. 공유 하는 본인을 공유 하면 알 수 있도록 공용 공유 pin 고유 인지 확인 합니다. 이렇게 하면 올바른 Azure 앵커를 공유 하는 확인 되므로 해당 Azure 앵커를 공유 하는 사용자 수천 개가 될 수 있습니다.

4. 다른 HoloLens 2 장치에 있는 경우 응용 프로그램을 시작 하 고 Azure 세션을 시작 합니다. 공유 앵커 ID 가져오기 단추를 누르고 디스크에 저장 하는 ID와 연결 된 앵커를 찾으려고 Azure 앵커 찾기 단추를 누릅니다. 장면 전체 위치에 이제 맞추려면 where에서 다른 HoloLens 2 장치에 배치 된 경우. 만 있는 경우 하나의 HoloLens 2, 아직 기능 테스트 응용 프로그램을 다시 시작 하 여 Azure 세션을 시작 하 고 "공유 앵커 ID 가져오기" 단추를 누릅니다 있습니다 앵커를 찾으려고 Azure 앵커 찾을 단추와 연결 된 디스크에 저장 하는 ID입니다. 장면 전체 이제 맞추려면 위치를 위치에 저장 앵커 이전!

## <a name="congratulations"></a>축하합니다.
이 단원의 HoloLens 2에서 로컬 디스크로 Azure 공간 앵커 ID를 저장 하 여 응용 프로그램 다시 시작 하 고 응용 프로그램 세션 간에 Azure 공간 앵커를 유지 하는 방법을 알아보았습니다. 또한 Azure 공간 앵커를 공유 하는 기본 다중 사용자, 정적 홀로그램 환경에 대 한 여러 장치 간에 공유 하는 방법을 배웠습니다.

공유 모듈의 마지막 단원 중 완전 한 대화형 로컬 공유 환경의 일부분으로 Azure 공간 앵커를 구현 하는 방법을 알아보겠습니다. 로컬 공유 경험을 각 사용자에 대해 동기화 된 3D 개체 위치, 회전 및 비율, 식별자와 같은 기능이 포함 될 수 있습니다 및 응용 프로그램 상태를 공유 합니다. 모든 사용자가 물리적으로 동일한 위치에서 가상 개체를 볼 수 있는 일반적인 앵커를 사용 하 여 각 참가자를 제공 하 여 이러한 공유 시나리오를 개선 하는 azure 공간 앵커 합니다. 다양 한 장치 플랫폼, HoloLens, Android 및 iOS 장치를 비롯 한 마찬가지입니다. 공유 경험을 개발 하는 방법에 알아보려면 공유 모듈의 모든 단원을 완료 합니다.

다음 단원에서는 실시간 피드백을 사용 하 여 사용자에 게 제공 하는 방법을 배웁니다. 이 피드백에는 앵커 생성, 환경 이해도 품질 및 Azure 세션 상태에 대 한 정보가 포함 됩니다. 피드백을 하지 않고 사용자가 모를 수 있습니다 앵커를 Azure에 업로드 했습니다. 되었는지 앵커 생성 또는 현재 상태에 대 한 충분 한 환경의 품질 인지.

[다음 단원: ASA 자습서 3](mrlearning-asa-ch3.md)

