---
title: Unity 재생 모드
description: Unity 편집기에서 재생 모드를 사용 하 여 앱을 배포 하지 않고 장치에서 변경 내용을 미리 봅니다.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 원격, holographic remoting, holographic 원격 플레이어
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597825"
---
# <a name="unity-play-mode"></a>Unity 재생 모드

Unity 프로젝트에서 작동 하는 빠른 방법을 "재생 모드"를 사용 하는 것입니다. 이 앱에서 로컬로 실행 Unity 편집기에서 PC. Unity Holographic 원격을 사용 하 여 실제 HoloLens 장치에서 콘텐츠 미리 보기에 빠른 방법을 제공 합니다.

## <a name="unity-play-mode-with-holographic-remoting"></a>Holographic Remoting 사용 하 여 unity 재생 모드

Holographic Remoting을 사용 하 여 PC에 Unity 편집기에서 실행 되는 동안는 HoloLens에 앱을 경험할 수 있습니다. 에 HoloLens 게이즈, 제스처, 음성 및 공간 매핑 입력 사용자 PC에 보내집니다. 렌더링 된 프레임에 HoloLens로 다시 전송 됩니다. 이것이 신속 하 게 빌드하고 전체 프로젝트를 배포 하지 않고 앱을 디버그 하는 좋은 방법입니다.
1. 에 HoloLens로 이동 합니다 **Microsoft Store** 하 고 설치를 **[Holographic 원격 플레이어](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱.
2. 에 HoloLens에서 시작 합니다 **Holographic 원격 플레이어** 앱.
3. Unity로 이동 합니다 **창을** 메뉴를 선택 **Holographic 에뮬레이션**합니다.
4. 설정할 **에뮬레이션 모드** 하 **장치에 원격**합니다.
5. 에 대 한 **원격 컴퓨터**, 프로그램 HoloLens의 IP 주소를 입력 합니다.
6. **연결**을 클릭합니다. 표시 되어야 **연결 상태** 변경 **연결 됨** 이동는 HoloLens에 빈 화면을 표시 합니다.
7. 클릭 합니다 **재생** 단추 재생 모드를 시작 하 여 HoloLens에 앱을 경험 합니다.

Holographic Remoting 빠른 PC 및 Wi-fi 연결에 필요합니다. 참조 [Holographic 원격 플레이어](holographic-remoting-player.md) 전체 세부 정보에 대 한 합니다.

최상의 결과 앱이 올바르게 설정 되었는지 확인 합니다 [지점 집중](focus-point-in-unity.md)합니다. 이렇게 하면 장면 무선 연결의 대기 시간을 가장 잘 맞게 Holographic Remoting 수 있습니다.

## <a name="see-also"></a>관련 항목
* [Holographic Remoting 플레이어](holographic-remoting-player.md)
