---
title: HoloLens에 Wi-fi에 연결
description: HoloLens 사용 하 여 무선 인터넷 연결 하는 방법 및 장치의 IP 주소를 식별 하는 방법에 대 한 지침입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, 무선 인터넷, ip, ip 주소
ms.openlocfilehash: 0440c3dad48d73db51e7d730e79d6eb1e74a5694
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604110"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>HoloLens에 Wi-fi에 연결

HoloLens 802.11ac는 포함-2 Wi-fi 라디오 x 지 원하는 경우 2입니다. HoloLens Wi-fi 네트워크에 연결 하는 것을 Windows 10 데스크톱 또는 모바일 장치 Wi-fi 네트워크에 연결 하는 것과 비슷합니다.

![HoloLens Wi-fi 설정](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>HoloLens에 Wi-fi 네트워크에 연결

1. [블 룸](gestures.md#bloom) 에 **시작** 메뉴.
2. 선택는 **설정** 또는 시작에서 앱을 **모든 앱** 시작 메뉴의 오른쪽에는 목록입니다.
3. 합니다 **설정을** 앱 사용자 앞에 자동 배치 됩니다.
4. 선택 **네트워크 및 인터넷**합니다.
5. Wi-Fi가 켜져 있는지 확인합니다.
6. 목록에서 Wi-fi 네트워크를 선택 합니다.
7. (필요한 경우) Wi-fi 네트워크 암호를 입력 합니다.

## <a name="disabling-wi-fi-on-hololens"></a>HoloLens에서 Wi-fi를 사용 하지 않도록 설정

### <a name="using-the-settings-app-on-hololens"></a>설정 앱을 사용 하 여 HoloLens에

1. [블 룸](gestures.md#bloom) 에 **시작** 메뉴.
2. 선택는 **설정** 또는 시작에서 앱을 **모든 앱** 시작 메뉴의 오른쪽에는 목록입니다.
3. 합니다 **설정을** 앱 사용자 앞에 자동 배치 됩니다.
4. 선택 **네트워크 및 인터넷**합니다.
5. "Off" 위치로 이동 하려면 Wi-fi 슬라이더 스위치를 선택 합니다. Wi-fi 라디오 RF 구성 요소를 해제 되 고 HoloLens에 모든 Wi-fi 기능을 사용 하지 않도록 설정 됩니다. 

    >[!WARNING]
    >HoloLens 자동으로 로드할 수 없습니다 하 [공간](environment-considerations-for-hololens.md#spaces) Wi-fi 라디오 사용을 하지 않도록 설정 합니다.
    
6. 슬라이더 스위치 Wi-fi 라디오 설정 하 고 Microsoft HoloLens Wi-fi 기능을 복원 하려면 "On" 위치로 이동 합니다. 선택한 Wi-fi 라디오 상태 ("설정"의 "끄기"로) 재부팅 간에 유지 됩니다.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Wi-fi 네트워크에 연결 된 확인 방법

1. [블 룸](gestures.md#bloom) 불러오려면 합니다 **시작** 메뉴.
2. 위쪽 Wi-fi 상태에 대 한 시작 메뉴의 왼쪽입니다. 상태의 Wi-fi 및 연결된 된 네트워크의 SSID 표시 됩니다.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Wi-fi 네트워크에 HoloLens의 IP 주소를 식별합니다.

### <a name="using-the-settings-app"></a>설정 앱을 사용 하 여

1. [블 룸](gestures.md#bloom) 에 **시작** 메뉴.
2. 선택는 **설정** 또는 시작에서 앱을 **모든 앱** 시작 메뉴의 오른쪽에는 목록입니다.
3. 합니다 **설정을** 앱 사용자 앞에 자동 배치 됩니다.
4. 선택 **네트워크 및 인터넷**합니다.
5. 선택한 사용 가능한 Wi-fi 네트워크 목록 아래까지 아래로 스크롤하고 **하드웨어 속성**합니다.

    ![Wi-fi 설정에서 하드웨어 속성](images/wifi-hololens-hwdetails.jpg)

IP 주소 옆에 나타납니다 **IPv4 주소**합니다.

### <a name="using-cortana"></a>Cortana를 사용 하 여

예를 들어 "*Hey Cortana, 내 IP 주소는 무엇 인가요?*" 및 Cortana에서 표시 하 고 IP 주소 아웃 읽이 됩니다.

### <a name="using-windows-device-portal"></a>Windows Device Portal 사용 하 여

1. 엽니다는 [장치 포털](using-the-windows-device-portal.md#networking) PC에서 웹 브라우저에서.
2. 로 이동 합니다 **네트워킹** 섹션입니다.

IP 주소 및 기타 네트워크 정보 표시 됩니다. 복사 및 붙여넣기 개발 PC의 IP 주소에 대 한이 방법을 사용 하면 됩니다.
