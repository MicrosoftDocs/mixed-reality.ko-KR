---
title: Unreal에서 입력 응시
description: Unreal에서 응시 입력을 사용 하는 방법을 설명 합니다.
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens, 눈동자 추적
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835629"
---
# <a name="gaze-input"></a><span data-ttu-id="f5a38-104">응시 입력</span><span class="sxs-lookup"><span data-stu-id="f5a38-104">Gaze Input</span></span>

<span data-ttu-id="f5a38-105">Windows Mixed Reality 플러그인은 응시 입력에 특별 한 함수를 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-105">The Windows Mixed Reality plugin doesn’t provide any special functions for the gaze input.</span></span> <span data-ttu-id="f5a38-106">모든 것은 표준 Unreal API를 통해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-106">Everything works though the standard Unreal API.</span></span>

[<span data-ttu-id="f5a38-107">헤드 응시 API</span><span class="sxs-lookup"><span data-stu-id="f5a38-107">Head gaze API</span></span>](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a><span data-ttu-id="f5a38-108">시선 추적</span><span class="sxs-lookup"><span data-stu-id="f5a38-108">Eye tracking</span></span>

<span data-ttu-id="f5a38-109">아이 추적 API를 사용 하기 위해 개발자는 HoloLens 프로젝트 설정에서 "응시 입력" 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-109">To use the eye tracking API, developers should enable the “Gaze Input” capability in their HoloLens project settings.</span></span> <span data-ttu-id="f5a38-110">응용 프로그램이 시작 되 면 사용자에 게 다음과 같은 동의 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-110">When the application starts, user will see the following consent prompt</span></span>

![눈 입력 권한](images/unreal/eye-input-permissions.png)
 
<span data-ttu-id="f5a38-112">사용자가 권한을 부여 하는 경우 응용 프로그램은 눈동자 입력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-112">If the user gives their permission, the application will get eye gaze input.</span></span> 

<span data-ttu-id="f5a38-113">Unreal의 눈 추적 API는 [여기](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html) 에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-113">Unreal’s eye tracking API is documented is [here](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span></span>

<span data-ttu-id="f5a38-114">눈 추적의 기술적인 세부 정보는 [여기](eye-tracking.md) 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-114">The technical details of eye tracking are [here](eye-tracking.md)</span></span>

<span data-ttu-id="f5a38-115">특히 Unreal의 경우 HoloLens 눈 추적에는 두 눈에 모두 단일 응시 레이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-115">Note that specifically for Unreal, HoloLens eye tracking has a single gaze ray for both eyes.</span></span> <span data-ttu-id="f5a38-116">HoloLens는 stereoscopic 눈 추적을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5a38-116">HoloLens doesn’t provide stereoscopic eye tracking.</span></span>
