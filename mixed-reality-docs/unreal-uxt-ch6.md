---
title: 6. 패키징 후 디바이스 또는 에뮬레이터에 배포
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 튜토리얼의 6부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519972"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. 패키징 후 디바이스 또는 에뮬레이터에 배포

이 섹션에서는 HoloLens 2 디바이스 또는 에뮬레이터에서 실행되도록 앱을 준비하는 단계를 안내합니다. 디바이스가 있는 경우 컴퓨터에서 디바이스로 스트리밍하거나 앱을 패키징하여 디바이스에서 직접 실행할 수 있습니다. 디바이스가 없는 경우 에뮬레이터에서 실행되도록 앱을 패키징해야 합니다. 

## <a name="objectives"></a>목표

* [디바이스 전용] 홀로그램 앱 원격 기능을 통해 HoloLens 2에 앱 스트리밍
* HoloLens 2 디바이스 또는 에뮬레이터에 앱 패키지 및 배포

## <a name="device-only-stream"></a>[디바이스 전용] 스트림

1.  HoloLens 2의 Microsoft Store에서 **홀로그램 원격 플레이어**를 설치하고 앱 실행

2.  **편집 > 프로젝트 설정**으로 이동합니다. 홀로그램 원격 섹션에서 원격 기능을 사용하는 확인란을 선택하고 편집기를 다시 시작합니다.

3.  디바이스의 IP 주소를 입력하고 연결을 클릭합니다.

4.  연결되면 UE4 편집기에서 재생 단추 오른쪽에 있는 드롭다운 화살표를 클릭하고 VR 미리 보기를 선택합니다.

## <a name="package-and-deploy-your-app"></a>앱 패키징 및 배포 

>[!NOTE]
>HoloLens용 Unreal 앱을 처음으로 패키징하는 경우 Epic Launcher에서 지원 파일을 다운로드해야 합니다. 이렇게 하려면 Epic Games Launcher에서 **라이브러리** 탭으로 이동합니다. **실행** 옆의 드롭다운 화살표를 선택하고 **옵션**을 선택합니다. **대상 플랫폼**에서 **HoloLens 2**를 선택하고 **적용**을 클릭합니다. 
>![프로젝트 설정 - 설명](images/unreal-uxt/6-installationoptions.PNG)

1.  **편집 > 프로젝트 설정**으로 이동합니다. **프로젝트 > 설명 > 정보 > 프로젝트 이름**에서 프로젝트 이름을 부여합니다. **프로젝트 > 설명 > 게시자 > 회사 고유 이름**에서 “CN={INSERT COMPANY NAME}”을 입력합니다. 이들 필드 중 하나를 비워 두면 오류가 발생 합니다. 

![프로젝트 설정 - 설명](images/unreal-uxt/6-cn.PNG)

2.  **플랫폼 > HoloLens**에서 대상으로 지정할 에뮬레이션 및/또는 디바이스를 선택합니다.

3.  **패키징** 섹션에서 **서명 인증서** 옆에 있는 **새로 생성** 단추를 클릭하여 새 서명 인증서를 생성합니다. 주 창으로 돌아갑니다.

![프로젝트 설정 - 플랫폼 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  **파일 > 패키지 프로젝트**으로 이동하여 **HoloLens**를 선택합니다. 새 폴더를 만들어 패키지를 저장하고 **폴더 선택**을 선택합니다. 

5.  앱이 성공적으로 패키지된 후 **Windows Device Portal**을 열고 **보기 > 앱**으로 이동한 다음, **앱 배포** 섹션을 찾습니다.

6.  **찾아보기 ...** 를 클릭하여 **ChessApp.appxbundle** 파일로 이동합니다. **열기**를 클릭합니다. 

    * 디바이스에 앱을 처음 설치하는 경우**프레임워크 패키지를 선택하도록 허용** 옆의 확인란을 선택합니다. 다음 대화 상자에서 적절한 VCLibs appx 파일(디바이스의 경우 arm64, 에뮬레이터의 경우 x64)을 포함합니다. 

7.  **설치**를 클릭합니다.

이 자습서를 완료한 것을 축하합니다!  