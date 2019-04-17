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
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="d3cef-104">HoloLens에 Wi-fi에 연결</span><span class="sxs-lookup"><span data-stu-id="d3cef-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="d3cef-105">HoloLens 802.11ac는 포함-2 Wi-fi 라디오 x 지 원하는 경우 2입니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="d3cef-106">HoloLens Wi-fi 네트워크에 연결 하는 것을 Windows 10 데스크톱 또는 모바일 장치 Wi-fi 네트워크에 연결 하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens Wi-fi 설정](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="d3cef-108">HoloLens에 Wi-fi 네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="d3cef-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="d3cef-109">[블 룸](gestures.md#bloom) 에 **시작** 메뉴.</span><span class="sxs-lookup"><span data-stu-id="d3cef-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="d3cef-110">선택는 **설정** 또는 시작에서 앱을 **모든 앱** 시작 메뉴의 오른쪽에는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="d3cef-111">합니다 **설정을** 앱 사용자 앞에 자동 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="d3cef-112">선택 **네트워크 및 인터넷**합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="d3cef-113">Wi-Fi가 켜져 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="d3cef-114">목록에서 Wi-fi 네트워크를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="d3cef-115">(필요한 경우) Wi-fi 네트워크 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="d3cef-116">HoloLens에서 Wi-fi를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="d3cef-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="d3cef-117">설정 앱을 사용 하 여 HoloLens에</span><span class="sxs-lookup"><span data-stu-id="d3cef-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="d3cef-118">[블 룸](gestures.md#bloom) 에 **시작** 메뉴.</span><span class="sxs-lookup"><span data-stu-id="d3cef-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="d3cef-119">선택는 **설정** 또는 시작에서 앱을 **모든 앱** 시작 메뉴의 오른쪽에는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="d3cef-120">합니다 **설정을** 앱 사용자 앞에 자동 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="d3cef-121">선택 **네트워크 및 인터넷**합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="d3cef-122">"Off" 위치로 이동 하려면 Wi-fi 슬라이더 스위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="d3cef-123">Wi-fi 라디오 RF 구성 요소를 해제 되 고 HoloLens에 모든 Wi-fi 기능을 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="d3cef-124">HoloLens 자동으로 로드할 수 없습니다 하 [공간](environment-considerations-for-hololens.md#spaces) Wi-fi 라디오 사용을 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#spaces) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="d3cef-125">슬라이더 스위치 Wi-fi 라디오 설정 하 고 Microsoft HoloLens Wi-fi 기능을 복원 하려면 "On" 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="d3cef-126">선택한 Wi-fi 라디오 상태 ("설정"의 "끄기"로) 재부팅 간에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="d3cef-127">Wi-fi 네트워크에 연결 된 확인 방법</span><span class="sxs-lookup"><span data-stu-id="d3cef-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="d3cef-128">[블 룸](gestures.md#bloom) 불러오려면 합니다 **시작** 메뉴.</span><span class="sxs-lookup"><span data-stu-id="d3cef-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="d3cef-129">위쪽 Wi-fi 상태에 대 한 시작 메뉴의 왼쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="d3cef-130">상태의 Wi-fi 및 연결된 된 네트워크의 SSID 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="d3cef-131">Wi-fi 네트워크에 HoloLens의 IP 주소를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="d3cef-132">설정 앱을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="d3cef-132">Using the Settings app</span></span>

1. <span data-ttu-id="d3cef-133">[블 룸](gestures.md#bloom) 에 **시작** 메뉴.</span><span class="sxs-lookup"><span data-stu-id="d3cef-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="d3cef-134">선택는 **설정** 또는 시작에서 앱을 **모든 앱** 시작 메뉴의 오른쪽에는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="d3cef-135">합니다 **설정을** 앱 사용자 앞에 자동 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="d3cef-136">선택 **네트워크 및 인터넷**합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="d3cef-137">선택한 사용 가능한 Wi-fi 네트워크 목록 아래까지 아래로 스크롤하고 **하드웨어 속성**합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Wi-fi 설정에서 하드웨어 속성](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="d3cef-139">IP 주소 옆에 나타납니다 **IPv4 주소**합니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="d3cef-140">Cortana를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="d3cef-140">Using Cortana</span></span>

<span data-ttu-id="d3cef-141">예를 들어 "*Hey Cortana, 내 IP 주소는 무엇 인가요?*"</span><span class="sxs-lookup"><span data-stu-id="d3cef-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="d3cef-142">및 Cortana에서 표시 하 고 IP 주소 아웃 읽이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="d3cef-143">Windows Device Portal 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="d3cef-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="d3cef-144">엽니다는 [장치 포털](using-the-windows-device-portal.md#networking) PC에서 웹 브라우저에서.</span><span class="sxs-lookup"><span data-stu-id="d3cef-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="d3cef-145">로 이동 합니다 **네트워킹** 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="d3cef-146">IP 주소 및 기타 네트워크 정보 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="d3cef-147">복사 및 붙여넣기 개발 PC의 IP 주소에 대 한이 방법을 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3cef-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
