---
title: MR 학습 자료 모듈 소개
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 2fe07efe87086e9a8c06e1953fcef8544b03c80a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829877"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="ee369-104">모듈 개요 MR 학습 자료 및 목표</span><span class="sxs-lookup"><span data-stu-id="ee369-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="ee369-105">장치 지원</span><span class="sxs-lookup"><span data-stu-id="ee369-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ee369-106"><strong>과정</strong></span><span class="sxs-lookup"><span data-stu-id="ee369-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="ee369-107"><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></span><span class="sxs-lookup"><span data-stu-id="ee369-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="ee369-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="ee369-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="ee369-109"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="ee369-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="ee369-110">❌</span><span class="sxs-lookup"><span data-stu-id="ee369-110">❌</span></span></td>
        <td><span data-ttu-id="ee369-111">✔️</span><span class="sxs-lookup"><span data-stu-id="ee369-111">✔️</span></span></td>
        <td><span data-ttu-id="ee369-112">❌</span><span class="sxs-lookup"><span data-stu-id="ee369-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="ee369-113">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="ee369-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ee369-114">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ee369-114">Prerequisites</span></span>

* <span data-ttu-id="ee369-115">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구 설치](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="ee369-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="ee369-116">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="ee369-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="ee369-117">기본적인 C# 기능을 프로그래밍 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee369-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="ee369-118">HoloLens 2 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.</span><span class="sxs-lookup"><span data-stu-id="ee369-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
