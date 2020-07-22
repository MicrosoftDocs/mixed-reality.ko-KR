---
title: Unreal의 스트리밍
description: Unreal에서 HoloLens 2로 스트림하는 방법에 대한 지침입니다.
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 스트리밍, PC, 홀로그램 앱 원격, 홀로그램 원격 플레이어, 설명서
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: d25efbcf83e45749cc4eb8b99581b71105c59c9d
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303534"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="26def-104">Unreal의 스트리밍</span><span class="sxs-lookup"><span data-stu-id="26def-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="26def-105">개요</span><span class="sxs-lookup"><span data-stu-id="26def-105">Overview</span></span>
<span data-ttu-id="26def-106">PC에서 HoloLens로 스트림하는 경우 다음과 같은 두 가지 주요 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26def-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="26def-107">혼합 현실 앱에서 PC의 계산 능력을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26def-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="26def-108">개발 반복 시간을 단축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26def-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="26def-109">시작하려면 [홀로그램 원격 플레이어](holographic-remoting-player.md)를 HoloLens 디바이스에 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-109">To get started, you'll need to download the [Holographic Remoting Player](holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="26def-110">이렇게 하면 앱에서 다음 원본에 있는 HoloLens의 원격 플레이어에 직접 스트림할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26def-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="26def-111">Unreal Engine 편집기</span><span class="sxs-lookup"><span data-stu-id="26def-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="26def-112">패키지된 Windows 실행 파일</span><span class="sxs-lookup"><span data-stu-id="26def-112">A packaged Windows executable</span></span> 

<span data-ttu-id="26def-113">스트림할 때 디바이스에서 애플리케이션을 실행할 때와 동일한 대부분의 HoloLens 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26def-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="26def-114">여기에는 [손 관절 추적](unreal-hand-tracking.md)(HoloLens 2에 있는 경우), [공간 매핑](unreal-spatial-mapping.md) 및 [공간 앵커](unreal-spatial-anchors.md)가 포함되지만 이 [제한 사항 목록](holographic-remoting-troubleshooting.md)에 있는 기능은 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="26def-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="26def-115">스트리밍 품질은 Wi-Fi 네트워크의 강도에 따라 크게 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="26def-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="26def-116">모든 기능은 홀로그램 원격 플레이어에 대해 자동으로 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="26def-116">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="26def-117">디바이스에서 실행되는 경우를 제외하고 사용자 권한(예: 시선 추적)을 사용해야 하는 기능을 찾는 경우 프로젝트 설정에서 적절한 기능을 사용하도록 설정했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-117">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="26def-118">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="26def-118">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="26def-119"><strong>원본</strong></span><span class="sxs-lookup"><span data-stu-id="26def-119"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="26def-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1세대</strong></a></span><span class="sxs-lookup"><span data-stu-id="26def-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="26def-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="26def-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="26def-122"><strong>몰입형 헤드셋</strong></span><span class="sxs-lookup"><span data-stu-id="26def-122"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="26def-123">Unreal 편집기</span><span class="sxs-lookup"><span data-stu-id="26def-123">Unreal editor</span></span></td>
        <td><span data-ttu-id="26def-124">✔️</span><span class="sxs-lookup"><span data-stu-id="26def-124">✔️</span></span></td>
        <td><span data-ttu-id="26def-125">✔️</span><span class="sxs-lookup"><span data-stu-id="26def-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="26def-126">Windows 패키지</span><span class="sxs-lookup"><span data-stu-id="26def-126">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="26def-127">✔️</span><span class="sxs-lookup"><span data-stu-id="26def-127">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="26def-128">Unreal 편집기에서 스트리밍</span><span class="sxs-lookup"><span data-stu-id="26def-128">Streaming from the Unreal editor</span></span>

<span data-ttu-id="26def-129">개발자는 Unreal 편집기에서 HoloLens 디바이스로 스트림하는 경우 테스트할 때 큰 이점을 제공한다는 것을 알 수 있습니다. 즉, 업데이트를 시도하기 전에 앱이 빌드 및 배포될 때까지 더 이상 기다릴 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26def-129">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="26def-130">Unreal 시작 자습서 시리즈의 마지막 섹션에서 [Unreal 편집기에서 스트림하는 방법](unreal-uxt-ch6.md#device-only-streaming)에 대한 자세한 지침을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26def-130">You can find detailed instructions on [streaming from the Unreal editor](unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="26def-131">패키지된 Windows 실행 파일에서 스트리밍</span><span class="sxs-lookup"><span data-stu-id="26def-131">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="26def-132">Unreal 4.25.1부터 다음 단계에 따라 앱을 패키지된 Windows 실행 파일에서 HoloLens 2 디바이스에 스트림할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26def-132">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="26def-133">편집기 메뉴에서 **파일 > 패키지 프로젝트 > Windows**로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-133">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="26def-134">패키지를 저장할 위치를 선택하고, **폴더 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-134">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="26def-135">패키지가 빌드되면 HoloLens 2에서 **홀로그램 원격 플레이어**를 열고 IP 주소를 적어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="26def-135">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="26def-136">**홀로그램 원격 플레이어**를 열어 놓은 채 명령줄 프롬프트를 사용하여 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-136">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="26def-137">cd를 사용하여 패키지를 저장한 로컬 디렉터리로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-137">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="26def-138">```<App Name>.exe -vr -HoloLensRemoting=<IP Address>``` 명령을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="26def-138">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="26def-139">프로젝트 설정의 애플리케이션 이름을 사용하여 Windows 패키지를 자동으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-139">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="26def-140">몇 가지 이유로 인해 이러한 이름이 다른 경우 명령 프롬프트에서 Windows 실행 파일 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-140">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="26def-141">Enter 키를 누르면 애플리케이션에서 스트리밍을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="26def-141">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="26def-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26def-142">See also</span></span>
* [<span data-ttu-id="26def-143">홀로그램 원격 버전 기록</span><span class="sxs-lookup"><span data-stu-id="26def-143">Holographic remoting version history</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="26def-144">사용자 지정 홀로그램 원격 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="26def-144">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="26def-145">홀로그램 원격을 사용하여 보안 연결 설정</span><span class="sxs-lookup"><span data-stu-id="26def-145">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
