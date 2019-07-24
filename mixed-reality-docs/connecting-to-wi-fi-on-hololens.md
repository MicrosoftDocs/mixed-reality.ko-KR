---
title: HoloLens에서 Wi-fi에 연결
description: HoloLens를 사용 하 여 무선 인터넷에 연결 하는 방법 및 장치의 IP 주소를 식별 하는 방법에 대 한 지침입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, 무선, 인터넷, ip, ip 주소
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670113"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>HoloLens에서 Wi-fi에 연결

HoloLens는 802.11 ac 지원, 2x2 Wi-fi 라디오를 포함 합니다. HoloLens를 Wi-fi 네트워크에 연결 하는 것은 Windows 10 데스크톱 또는 모바일 장치를 Wi-fi 네트워크에 연결 하는 것과 비슷합니다.

![HoloLens Wi-fi 설정](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>HoloLens에서 Wi-fi 네트워크에 연결

1. **시작** 메뉴로 [블 룸](gestures.md#bloom) .
2. 시작 메뉴의 오른쪽에 있는 **모든 앱** 목록 또는 시작에서 **설정** 앱을 선택 합니다.
3. **설정** 앱이 사용자의 앞에 자동으로 배치 됩니다.
4. **네트워크 & 인터넷**을 선택 합니다.
5. Wi-Fi가 켜져 있는지 확인합니다.
6. 목록에서 Wi-fi 네트워크를 선택 합니다.
7. 필요한 경우 Wi-fi 네트워크 암호를 입력 합니다.

## <a name="disabling-wi-fi-on-hololens"></a>HoloLens에서 Wi-fi를 사용 하지 않도록 설정

### <a name="using-the-settings-app-on-hololens"></a>HoloLens에서 설정 앱 사용

1. **시작** 메뉴로 [블 룸](gestures.md#bloom) .
2. 시작 메뉴의 오른쪽에 있는 **모든 앱** 목록 또는 시작에서 **설정** 앱을 선택 합니다.
3. **설정** 앱이 사용자의 앞에 자동으로 배치 됩니다.
4. **네트워크 & 인터넷**을 선택 합니다.
5. Wi-fi 슬라이더 스위치를 선택 하 여 "꺼짐" 위치로 이동 합니다. 그러면 Wi-fi 라디오의 RF 구성 요소가 꺼지고 HoloLens에서 모든 Wi-fi 기능을 사용 하지 않도록 설정 됩니다. 

    >[!WARNING]
    >Wi-fi 라디오를 사용 하지 않도록 설정 하면 HoloLens에서 자동으로 [공백을](environment-considerations-for-hololens.md#WiFi fingerprint considerations) 로드할 수 없습니다.
    
6. 슬라이더 스위치를 "켜기" 위치로 이동 하 여 Wi-fi 라디오를 켜고 Microsoft HoloLens에서 Wi-fi 기능을 복원 합니다. 선택한 Wi-fi 라디오 상태 ("꺼짐"의 "꺼짐")는 다시 부팅 하는 동안 유지 됩니다.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Wi-fi 네트워크에 연결 되어 있는지 확인 하는 방법

1. **시작** 메뉴를 [블 룸](gestures.md#bloom) .
2. 시작 메뉴의 왼쪽 위에서 Wi-fi 상태를 확인 합니다. Wi-fi의 상태와 연결 된 네트워크의 SSID가 표시 됩니다.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Wi-fi 네트워크에서 HoloLens의 IP 주소를 식별 하는 중

### <a name="using-the-settings-app"></a>설정 앱 사용

1. **시작** 메뉴로 [블 룸](gestures.md#bloom) .
2. 시작 메뉴의 오른쪽에 있는 **모든 앱** 목록 또는 시작에서 **설정** 앱을 선택 합니다.
3. **설정** 앱이 사용자의 앞에 자동으로 배치 됩니다.
4. **네트워크 & 인터넷**을 선택 합니다.
5. 사용 가능한 Wi-fi 네트워크 목록 아래까지 아래로 스크롤하고 **하드웨어 속성**을 선택 합니다.

    ![Wi-fi 설정의 하드웨어 속성](images/wifi-hololens-hwdetails.jpg)

IP 주소는 **IPv4 주소**옆에 표시 됩니다.

### <a name="using-cortana"></a>Cortana 사용

"*Cortana, 내 IP 주소는 무엇입니까?* " 라고 표시 됩니다. Cortana는 IP 주소를 표시 하 고 읽습니다.

### <a name="using-windows-device-portal"></a>Windows 장치 포털 사용

1. PC의 웹 브라우저에서 [장치 포털](using-the-windows-device-portal.md#networking) 을 엽니다.
2. **네트워킹** 섹션으로 이동 합니다.

IP 주소와 기타 네트워크 정보가 표시 됩니다. 이 방법을 사용 하면 개발 PC에서 IP 주소를 간편 하 게 복사 하 고 붙여넣을 수 있습니다.
