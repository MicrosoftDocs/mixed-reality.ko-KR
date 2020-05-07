---
title: 음성 입력
description: 음성 입력을 사용 하는 방법을 설명 합니다.
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835323"
---
# <a name="voice-input"></a><span data-ttu-id="f857b-104">음성 입력</span><span class="sxs-lookup"><span data-stu-id="f857b-104">Voice Input</span></span>

<span data-ttu-id="f857b-105">HoloLens에서 음성 인식을 사용 하도록 설정 하려면 개발자가 프로젝트 설정 > Platform > HoloLens > 기능에서 사용 하지 않는 편집기에서 "마이크"를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="f857b-106">또한 장치는 설정 > 개인 정보 > 음성에서 음성 인식을 사용 하도록 설정 하 고 영어를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Windows 음성 인식 설정](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="f857b-108">가능한 최상의 서비스 품질을 위해 온라인 음성 인식을 사용 하도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="f857b-109">HoloLens의 음성 인식에 대 한 기술 세부 정보는 여기를 참조 [하세요](voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="f857b-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="f857b-110">그러면 응용 프로그램이 처음 시작 될 때 마이크를 사용 하도록 설정 하는 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="f857b-111">사용자가 예를 선택 하면 응용 프로그램이 음성 입력을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="f857b-112">음성 입력에는 특별 한 Windows Mixed Reality API가 필요 하지 않으며, 대신 기존 Unreal Engine 4 입력 매핑 API를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="f857b-113">입력 API를 사용 하는 방법에 대 한 자세한 내용은 [여기](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f857b-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="f857b-114">음성 매핑이 엔진 – 아래 작업 및 축 매핑의 바인딩 섹션에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![UE4 엔진 입력 설정은](images/unreal/engine-input.png)
 
<span data-ttu-id="f857b-116">다음은 "점프" 전 세계 모니터링을 추가 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="f857b-117">모든 영어 단어 또는 짧은 문장을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="f857b-118">프로젝트 설정을 통해 음성 매핑을 추가한 후에는 다음 예제와 같이 개발자가 표준 Unreal 논리를 사용 하 여 입력을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f857b-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![음성에 대 한 간단한 작업](images/unreal/input-action-bp.png)
