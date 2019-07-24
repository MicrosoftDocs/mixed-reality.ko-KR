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
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="26fd6-104">HoloLens에서 Wi-fi에 연결</span><span class="sxs-lookup"><span data-stu-id="26fd6-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="26fd6-105">HoloLens는 802.11 ac 지원, 2x2 Wi-fi 라디오를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="26fd6-106">HoloLens를 Wi-fi 네트워크에 연결 하는 것은 Windows 10 데스크톱 또는 모바일 장치를 Wi-fi 네트워크에 연결 하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens Wi-fi 설정](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="26fd6-108">HoloLens에서 Wi-fi 네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="26fd6-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="26fd6-109">**시작** 메뉴로 [블 룸](gestures.md#bloom) .</span><span class="sxs-lookup"><span data-stu-id="26fd6-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="26fd6-110">시작 메뉴의 오른쪽에 있는 **모든 앱** 목록 또는 시작에서 **설정** 앱을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="26fd6-111">**설정** 앱이 사용자의 앞에 자동으로 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="26fd6-112">**네트워크 & 인터넷**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="26fd6-113">Wi-Fi가 켜져 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="26fd6-114">목록에서 Wi-fi 네트워크를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="26fd6-115">필요한 경우 Wi-fi 네트워크 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="26fd6-116">HoloLens에서 Wi-fi를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="26fd6-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="26fd6-117">HoloLens에서 설정 앱 사용</span><span class="sxs-lookup"><span data-stu-id="26fd6-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="26fd6-118">**시작** 메뉴로 [블 룸](gestures.md#bloom) .</span><span class="sxs-lookup"><span data-stu-id="26fd6-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="26fd6-119">시작 메뉴의 오른쪽에 있는 **모든 앱** 목록 또는 시작에서 **설정** 앱을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="26fd6-120">**설정** 앱이 사용자의 앞에 자동으로 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="26fd6-121">**네트워크 & 인터넷**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="26fd6-122">Wi-fi 슬라이더 스위치를 선택 하 여 "꺼짐" 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="26fd6-123">그러면 Wi-fi 라디오의 RF 구성 요소가 꺼지고 HoloLens에서 모든 Wi-fi 기능을 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="26fd6-124">Wi-fi 라디오를 사용 하지 않도록 설정 하면 HoloLens에서 자동으로 [공백을](environment-considerations-for-hololens.md#WiFi fingerprint considerations) 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="26fd6-125">슬라이더 스위치를 "켜기" 위치로 이동 하 여 Wi-fi 라디오를 켜고 Microsoft HoloLens에서 Wi-fi 기능을 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="26fd6-126">선택한 Wi-fi 라디오 상태 ("꺼짐"의 "꺼짐")는 다시 부팅 하는 동안 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="26fd6-127">Wi-fi 네트워크에 연결 되어 있는지 확인 하는 방법</span><span class="sxs-lookup"><span data-stu-id="26fd6-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="26fd6-128">**시작** 메뉴를 [블 룸](gestures.md#bloom) .</span><span class="sxs-lookup"><span data-stu-id="26fd6-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="26fd6-129">시작 메뉴의 왼쪽 위에서 Wi-fi 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="26fd6-130">Wi-fi의 상태와 연결 된 네트워크의 SSID가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="26fd6-131">Wi-fi 네트워크에서 HoloLens의 IP 주소를 식별 하는 중</span><span class="sxs-lookup"><span data-stu-id="26fd6-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="26fd6-132">설정 앱 사용</span><span class="sxs-lookup"><span data-stu-id="26fd6-132">Using the Settings app</span></span>

1. <span data-ttu-id="26fd6-133">**시작** 메뉴로 [블 룸](gestures.md#bloom) .</span><span class="sxs-lookup"><span data-stu-id="26fd6-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="26fd6-134">시작 메뉴의 오른쪽에 있는 **모든 앱** 목록 또는 시작에서 **설정** 앱을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="26fd6-135">**설정** 앱이 사용자의 앞에 자동으로 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="26fd6-136">**네트워크 & 인터넷**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="26fd6-137">사용 가능한 Wi-fi 네트워크 목록 아래까지 아래로 스크롤하고 **하드웨어 속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Wi-fi 설정의 하드웨어 속성](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="26fd6-139">IP 주소는 **IPv4 주소**옆에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="26fd6-140">Cortana 사용</span><span class="sxs-lookup"><span data-stu-id="26fd6-140">Using Cortana</span></span>

<span data-ttu-id="26fd6-141">"*Cortana, 내 IP 주소는 무엇입니까?* " 라고 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="26fd6-142">Cortana는 IP 주소를 표시 하 고 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="26fd6-143">Windows 장치 포털 사용</span><span class="sxs-lookup"><span data-stu-id="26fd6-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="26fd6-144">PC의 웹 브라우저에서 [장치 포털](using-the-windows-device-portal.md#networking) 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="26fd6-145">**네트워킹** 섹션으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="26fd6-146">IP 주소와 기타 네트워크 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="26fd6-147">이 방법을 사용 하면 개발 PC에서 IP 주소를 간편 하 게 복사 하 고 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26fd6-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
