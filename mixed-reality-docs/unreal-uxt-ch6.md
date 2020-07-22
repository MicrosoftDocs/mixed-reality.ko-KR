---
title: 6. 패키징 후 디바이스 또는 에뮬레이터에 배포
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서 시리즈 6/6부
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: c49e2a69cb97a996da4bf601a105c2176ccf267f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303544"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. 패키징 후 디바이스 또는 에뮬레이터에 배포

## <a name="overview"></a>개요

이전 자습서에서는 체스 말을 원래 위치로 다시 설정하는 간단한 단추를 추가했습니다. 이 마지막 섹션에서는 HoloLens 2 또는 에뮬레이터에서 앱을 실행할 수 있게 준비합니다. HoloLens 2가 있는 경우 컴퓨터에서 스트리밍하거나 앱을 패키징하여 디바이스에서 직접 실행할 수 있습니다. 디바이스가 없는 경우 에뮬레이터에서 실행되도록 앱을 패키징합니다. 이 섹션을 마치면 재생할 수 있는 혼합 현실 앱이 배포되며 조작과 UI가 완성됩니다.

## <a name="objectives"></a>목표

* [디바이스 전용] 홀로그램 앱 원격 기능을 통해 HoloLens 2에 스트리밍
* HoloLens 2 디바이스 또는 에뮬레이터에 앱 패키징 및 배포

## <a name="device-only-streaming"></a>[디바이스 전용] 스트리밍
이 경우 [홀로그램 원격 기능](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting)은 채널을 전환하는 것이 아니라 PC나 독립 실행형 UWP 디바이스에서 HoloLens 2로 데이터를 스트리밍합니다. 이 작업에서는 원격 호스트 앱이 HoloLens로부터 입력 데이터 스트림을 받고 가상 몰입형 보기에서 콘텐츠를 렌더링하며 다시 Wi-Fi를 통해 콘텐츠 프레임을 HoloLens로 돌려 보냅니다. 스트리밍에서는 사용자가 원격 몰입형 보기를 기존 데스크톱 PC 소프트웨어에 추가할 수 있고 다른 시스템 리소스에 액세스할 수 있습니다. 

체스 앱에 이 경로를 적용하려면 다음 몇 가지가 필요합니다.

1.  Microsoft Store에서 HoloLens 2에 **Holographic Remoting Player**를 설치하고 앱을 실행합니다. 앱에 표시되는 IP 주소를 확인합니다.

2.  Unreal 편집기로 돌아가서 **편집 > 프로젝트 설정**으로 이동하고 **홀로그램 원격** 섹션에서 **원격 사용**을 선택합니다.

3.  편집기를 다시 시작한 다음, 디바이스 IP 주소(Holographic Remoting Player 앱에 표시됨)를 입력한 다음, **연결**을 클릭합니다.

연결되면 **재생** 단추 오른쪽의 드롭다운 화살표를 클릭하여 **VR 미리 보기**를 선택합니다. 그러면 HoloLens 헤드셋으로 스트리밍되는 VR 미리 보기 창에 앱이 실행됩니다. 

## <a name="packaging-and-deploying-the-app-via-device-portal"></a>디바이스 포털을 통해 앱 패키징 및 배포

>[!NOTE]
>HoloLens용 Unreal 앱을 처음으로 패키징하는 경우 Epic Launcher에서 지원 파일을 다운로드해야 합니다. 
>- Epic Games 시작 관리자에서 **라이브러리** 탭으로 이동한 다음, **시작** 옆의 드롭다운 화살표를 선택하고 **옵션**을 클릭합니다. 
>- **대상 플랫폼**에서 **HoloLens 2**를 선택하고 **적용**을 클릭합니다. 
>![프로젝트 설정 - 설명](images/unreal-uxt/6-installationoptions.PNG)

1.  **편집 > 프로젝트 설정**으로 이동합니다. 
    * **프로젝트 > 설명 > 정보 > 프로젝트 이름**에서 프로젝트 이름을 추가합니다. 
    * **프로젝트 > 설명 > 게시자 > 회사 고유 이름** 아래에서 **CN=YourCompanyName**을 추가합니다.

> [!IMPORTANT]
> 이러한 필드 중 하나를 비워 두면 3단계에서 새 인증서를 생성하려고 할 때 오류가 발생합니다. 

> [!IMPORTANT]
> 게시자의 이름은 [LADPv3 고유 이름 형식](https://www.ietf.org/rfc/rfc2253.txt)이어야 합니다. 패키지할 때 잘못된 형식의 게시자 이름으로 인해 "서명 키를 찾을 수 없습니다. 앱에 디지털 서명할 수 없습니다."라는 오류가 발생합니다.

![프로젝트 설정 - 설명](images/unreal-uxt/6-cn.PNG)

2.  **플랫폼 > HoloLens**에서 **HoloLens 에뮬레이션에 대해 빌드** 및/또는 **HoloLens 디바이스에 대해 빌드**를 사용하도록 설정합니다.

3.  **서명 인증서** 옆의 **패키징** 섹션에서 **새로 생성**을 클릭합니다.

> [!IMPORTANT]
> 이미 생성된 인증서를 사용하는 경우 인증서의 게시자 이름은 애플리케이션의 게시자 이름과 동일해야 합니다. 그렇지 않으면 "서명 키를 찾을 수 없습니다. 앱에 디지털 서명할 수 없습니다."라는 오류로 인해 path\filename 파일을 삭제하지 못했습니다.

![프로젝트 설정 - 플랫폼 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. 프라이빗 키 암호를 만들라는 메시지가 표시되면 테스트 목적으로 **없음**을 클릭합니다.

![새 인증서 생성](images/unreal-uxt/6-private-key-testing.png)

5. **파일 > 패키지 프로젝트**으로 이동하여 **HoloLens**를 선택합니다. 
    * 새 폴더를 만들어 패키지를 저장하고 **폴더 선택**을 선택합니다. 

6.  앱 패키징 후 [Windows 장치 포털](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)을 열고 **보기 > 앱**으로 이동한 다음, **앱 배포** 섹션을 찾습니다.

7.  **찾아보기...** 를 클릭하고 **ChessApp.appxbundle** 파일로 이동한 다음, **열기**를 클릭합니다. 

    * 디바이스에 앱을 처음 설치하는 경우 **프레임워크 패키지를 선택하도록 허용** 옆의 확인란을 선택합니다. 
    * 다음 대화 상자에서 적절한 **VCLibs** 및 **appx** 파일을 포함합니다(디바이스에는 arm64, 에뮬레이터에는 x64). 이 항목은 패키지를 저장한 폴더 안의 **HoloLens** 아래에 있습니다.

8.  **설치**를 클릭합니다.
    * 이제 **모든 앱**으로 이동하고 새로 설치된 앱을 탭하여 실행하거나 **Windows 장치 포털**에서 직접 앱을 시작할 수 있습니다. 

축하합니다! HoloLens 혼합 현실 애플리케이션이 완료되어 진행할 준비가 되었습니다. 그러나 모두 끝난 것은 아닙니다. MRTK에는 공간 매핑, 응시, 음성 입력을 비롯하여 QR 코드에 이르기까지, 프로젝트에 추가할 수 있는 무수한 독립 실행형 기능이 있습니다. 이러한 기능에 대한 자세한 내용은 [Unreal 개발 개요](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)에서 확인할 수 있습니다.
