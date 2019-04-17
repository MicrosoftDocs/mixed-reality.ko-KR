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
# <a name="unity-play-mode"></a><span data-ttu-id="67d97-104">Unity 재생 모드</span><span class="sxs-lookup"><span data-stu-id="67d97-104">Unity Play Mode</span></span>

<span data-ttu-id="67d97-105">Unity 프로젝트에서 작동 하는 빠른 방법을 "재생 모드"를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="67d97-106">이 앱에서 로컬로 실행 Unity 편집기에서 PC.</span><span class="sxs-lookup"><span data-stu-id="67d97-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="67d97-107">Unity Holographic 원격을 사용 하 여 실제 HoloLens 장치에서 콘텐츠 미리 보기에 빠른 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="67d97-108">Holographic Remoting 사용 하 여 unity 재생 모드</span><span class="sxs-lookup"><span data-stu-id="67d97-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="67d97-109">Holographic Remoting을 사용 하 여 PC에 Unity 편집기에서 실행 되는 동안는 HoloLens에 앱을 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="67d97-110">에 HoloLens 게이즈, 제스처, 음성 및 공간 매핑 입력 사용자 PC에 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="67d97-111">렌더링 된 프레임에 HoloLens로 다시 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="67d97-112">이것이 신속 하 게 빌드하고 전체 프로젝트를 배포 하지 않고 앱을 디버그 하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="67d97-113">에 HoloLens로 이동 합니다 **Microsoft Store** 하 고 설치를 **[Holographic 원격 플레이어](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱.</span><span class="sxs-lookup"><span data-stu-id="67d97-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="67d97-114">에 HoloLens에서 시작 합니다 **Holographic 원격 플레이어** 앱.</span><span class="sxs-lookup"><span data-stu-id="67d97-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="67d97-115">Unity로 이동 합니다 **창을** 메뉴를 선택 **Holographic 에뮬레이션**합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="67d97-116">설정할 **에뮬레이션 모드** 하 **장치에 원격**합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="67d97-117">에 대 한 **원격 컴퓨터**, 프로그램 HoloLens의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="67d97-118">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-118">Click **Connect**.</span></span> <span data-ttu-id="67d97-119">표시 되어야 **연결 상태** 변경 **연결 됨** 이동는 HoloLens에 빈 화면을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="67d97-120">클릭 합니다 **재생** 단추 재생 모드를 시작 하 여 HoloLens에 앱을 경험 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="67d97-121">Holographic Remoting 빠른 PC 및 Wi-fi 연결에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="67d97-122">참조 [Holographic 원격 플레이어](holographic-remoting-player.md) 전체 세부 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="67d97-123">최상의 결과 앱이 올바르게 설정 되었는지 확인 합니다 [지점 집중](focus-point-in-unity.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="67d97-124">이렇게 하면 장면 무선 연결의 대기 시간을 가장 잘 맞게 Holographic Remoting 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67d97-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="67d97-125">관련 항목</span><span class="sxs-lookup"><span data-stu-id="67d97-125">See Also</span></span>
* [<span data-ttu-id="67d97-126">Holographic Remoting 플레이어</span><span class="sxs-lookup"><span data-stu-id="67d97-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
