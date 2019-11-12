---
title: Azure Speech Services 자습서-2. 로컬 음성-텍스트 번역을 위한 오프 라인 모드 추가
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 962d7d4750cf59fe56de4af9088c90e8ecd0aa16
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913214"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="4bd81-105">2. 로컬 음성-텍스트 번역을 위한 오프 라인 모드 추가</span><span class="sxs-lookup"><span data-stu-id="4bd81-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="4bd81-106">이 자습서에서는 Azure 서비스에 연결할 수 없는 경우 로컬 음성-텍스트 변환을 수행할 수 있도록 하는 오프 라인 모드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="4bd81-107">또한 연결 되지 않은 상태를 *시뮬레이션* 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="4bd81-108">지침</span><span class="sxs-lookup"><span data-stu-id="4bd81-108">Instructions</span></span>

1. <span data-ttu-id="4bd81-109">계층에서 Lunarcom_Base 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-109">Select the Lunarcom_Base object in the hierarchy.</span></span>

2. <span data-ttu-id="4bd81-110">검사기 패널에서 구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-110">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="4bd81-111">Lunarcom 오프 라인 인식을 검색 하 고 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-111">Search for and select the Lunarcom Offline Recognition.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. <span data-ttu-id="4bd81-113">LunarcomOfflineRecognizer의 드롭다운을 클릭 하 고 사용을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-113">Click the drop-down in the LunarcomOfflineRecognizer and select Enabled.</span></span> <span data-ttu-id="4bd81-114">이 프로그램은 사용자가 연결 되지 않은 것 처럼 작동 하는 프로젝트를 프로그램 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-114">This programs the project to act like the user doesn't have a connection.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. <span data-ttu-id="4bd81-116">Unity 편집기에서 Play를 누르고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-116">Press Play in Unity Editor, and test it.</span></span> <span data-ttu-id="4bd81-117">장면의 왼쪽 아래 모서리에 있는 마이크를 누르고 말하기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-117">Press the microphone in the bottom-left corner in the scene and begin speaking.</span></span>

    >[!NOTE]
    ><span data-ttu-id="4bd81-118">오프 라인 상태 이기 때문에 절전 모드 해제 단어 기능이 사용 하지 않도록 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-118">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="4bd81-119">오프 라인에서 음성이 인식 될 때마다 마이크를 물리적으로 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-119">You'll need to physically click the microphone every time you wish to have your speech recognized when offline.</span></span>

    <span data-ttu-id="4bd81-120">다음은 장면이 표시 되는 모양의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-120">Below is an example of what your scene could look like.</span></span>

    ![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="4bd81-122">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-122">Congratulations</span></span>

<span data-ttu-id="4bd81-123">오프 라인 모드를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-123">The offline mode has been enabled.</span></span> <span data-ttu-id="4bd81-124">이제 오프 라인 상태인 경우에도 음성 SDK를 사용 하 여 프로젝트에 대 한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd81-124">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span>

[<span data-ttu-id="4bd81-125">다음 자습서: 3. Azure Cognitive Services speech translation 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="4bd81-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
