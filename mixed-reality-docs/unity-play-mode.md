---
title: Unity 재생 모드
description: Unity 편집기에서 재생 모드를 사용 하 여 앱을 배포 하지 않고 장치에서 변경 내용을 미리 봅니다.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, remoting, holographic remoting, holographic 원격 플레이어
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548720"
---
# <a name="unity-play-mode"></a>Unity 재생 모드

Unity 프로젝트에서 빠르게 작업 하는 방법은 "재생 모드"를 사용 하는 것입니다. 그러면 PC의 Unity 편집기에서 로컬로 앱이 실행 됩니다. Unity는 Holographic 원격 기능을 사용 하 여 실제 HoloLens 장치에서 콘텐츠를 빠르게 미리 볼 수 있는 방법을 제공 합니다.

## <a name="unity-play-mode-with-holographic-remoting"></a>Holographic 원격을 사용 하는 Unity 재생 모드

Holographic Remoting을 사용 하면 PC의 Unity 편집기에서 실행 되는 동안 HoloLens에서 앱을 경험해 볼 수 있습니다. 응시, 제스처, 음성 및 공간 매핑 입력은 HoloLens에서 PC로 전송 됩니다. 그러면 렌더링 된 프레임이 HoloLens로 다시 전송 됩니다. 이 방법은 전체 프로젝트를 빌드하고 배포 하지 않고도 신속 하 게 앱을 디버그할 수 있는 좋은 방법입니다.
1. HoloLens에서 **Microsoft Store** 로 이동 하 여 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치 합니다.
2. HoloLens에서 **Holographic Remoting Player** 앱을 시작 합니다.
3. Unity에서 **창** 메뉴로 이동 하 여 **Holographic 에뮬레이션**을 선택 합니다.
4. **에뮬레이션 모드** 를 **원격에서 장치로**설정 합니다.
5. **원격 컴퓨터**의 경우 HOLOLENS의 IP 주소를 입력 합니다.
6. **연결**을 클릭합니다. **연결 상태가** **연결 됨** 으로 변경 되 고 HoloLens에서 화면이 비어 있는 것을 볼 수 있습니다.
7. 재생 모드를 시작 하 고 HoloLens에서 앱을 경험 하려면 **재생** 단추를 클릭 합니다.

Holographic Remoting을 사용 하려면 고속 PC 및 Wi-fi 연결이 필요 합니다. 자세한 내용은 [Holographic Remoting Player](holographic-remoting-player.md) 를 참조 하세요.

최상의 결과를 위해 앱이 [포커스 지점을](focus-point-in-unity.md)적절히 설정 하는지 확인 합니다. 이렇게 하면 Holographic는 무선 연결의 대기 시간에 맞게 장면을 최적으로 조정 하는 데 도움이 됩니다.

## <a name="see-also"></a>관련 항목
* [홀로그램 원격 플레이어](holographic-remoting-player.md)
