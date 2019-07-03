---
title: MR 학습 자료 모듈 소개
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 389a23129d4dfc5819cdc45d071b678e3792089d
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523158"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="23465-104">1. 개요 및 목표</span><span class="sxs-lookup"><span data-stu-id="23465-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="23465-105">장치 지원</span><span class="sxs-lookup"><span data-stu-id="23465-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="23465-106"><strong>과정</strong></span><span class="sxs-lookup"><span data-stu-id="23465-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="23465-107"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="23465-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="23465-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="23465-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="23465-109"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="23465-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="23465-110">❌</span><span class="sxs-lookup"><span data-stu-id="23465-110">❌</span></span></td>
        <td><span data-ttu-id="23465-111">✔️</span><span class="sxs-lookup"><span data-stu-id="23465-111">✔️</span></span></td>
        <td><span data-ttu-id="23465-112">❌</span><span class="sxs-lookup"><span data-stu-id="23465-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="23465-113">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="23465-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="23465-114">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="23465-114">Prerequisites</span></span>

* <span data-ttu-id="23465-115">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구 설치](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="23465-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="23465-116">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="23465-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="23465-117">기본적인 C# 기능을 프로그래밍 합니다.</span><span class="sxs-lookup"><span data-stu-id="23465-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="23465-118">HoloLens 2 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.</span><span class="sxs-lookup"><span data-stu-id="23465-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
