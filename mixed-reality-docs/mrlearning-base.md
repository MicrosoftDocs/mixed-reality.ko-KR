---
title: 시작 자습서-1. 개요 및 목표
description: 이 과정에서는 혼합 현실 응용 프로그램 내에서 Azure 얼굴 인식을 구현 하는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: dbae7545edb6515b5cf148fbbfb6652595d2fc0d
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129264"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="c7402-105">1. 개요 및 목표</span><span class="sxs-lookup"><span data-stu-id="c7402-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="c7402-106">장치 지원</span><span class="sxs-lookup"><span data-stu-id="c7402-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c7402-107"><strong>과정</strong></span><span class="sxs-lookup"><span data-stu-id="c7402-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="c7402-108"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c7402-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c7402-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="c7402-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="c7402-110"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="c7402-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="c7402-111">✔️</span><span class="sxs-lookup"><span data-stu-id="c7402-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c7402-112">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="c7402-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c7402-113">필수 조건</span><span class="sxs-lookup"><span data-stu-id="c7402-113">Prerequisites</span></span>

* <span data-ttu-id="c7402-114">올바른 [도구로](install-the-tools.md) 구성 된 WINDOWS 10 PC</span><span class="sxs-lookup"><span data-stu-id="c7402-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="c7402-115">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="c7402-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="c7402-116">몇 가지 C# 기본 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="c7402-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="c7402-117">[개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode) HoloLens 2 장치</span><span class="sxs-lookup"><span data-stu-id="c7402-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="c7402-118">Unity 2019.2가 설치 되 고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가 된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 허브</a></span><span class="sxs-lookup"><span data-stu-id="c7402-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7402-119">이 자습서 시리즈의 권장 Unity 버전은 Unity 2019.2. X입니다.</span><span class="sxs-lookup"><span data-stu-id="c7402-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="c7402-120">이렇게 하면 위에 연결 된 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항이 나 권장 사항이 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7402-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="c7402-121">다음 단원: 2. 프로젝트 및 첫 번째 응용 프로그램 초기화</span><span class="sxs-lookup"><span data-stu-id="c7402-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
