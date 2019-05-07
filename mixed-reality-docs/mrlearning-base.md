---
title: MR 학습 자료 모듈 소개
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 80b9b8d7cd3659c9cc20824114cdedc05eae8a85
ms.sourcegitcommit: 45a0a7d5ce45440b251293a0380ad5b722dbbad3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64933650"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="f6ef4-104">모듈 개요 MR 학습 자료 및 목표</span><span class="sxs-lookup"><span data-stu-id="f6ef4-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="f6ef4-105">장치 지원</span><span class="sxs-lookup"><span data-stu-id="f6ef4-105">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f6ef4-106">과정</span><span class="sxs-lookup"><span data-stu-id="f6ef4-106">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f6ef4-107"><a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></span><span class="sxs-lookup"><span data-stu-id="f6ef4-107"><a href="hololens-hardware-details.md">HoloLens (1st Gen)</a></span></span></th><th style="width:150px"> <span data-ttu-id="f6ef4-108"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="f6ef4-108"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th><th style="width:150px"> <span data-ttu-id="f6ef4-109"><a href="https://www.microsoft.com/en-us/hololens/hardware">HoloLens 2</a></span><span class="sxs-lookup"><span data-stu-id="f6ef4-109"><a href="https://www.microsoft.com/en-us/hololens/hardware">HoloLens 2</a></span></span></th>
</tr><tr>
<td></td><td style="text-align: center;"> </td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="f6ef4-110">✔️</span><span class="sxs-lookup"><span data-stu-id="f6ef4-110">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="f6ef4-111">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="f6ef4-111">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f6ef4-112">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f6ef4-112">Prerequisites</span></span>

* <span data-ttu-id="f6ef4-113">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구 설치](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="f6ef4-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="f6ef4-114">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="f6ef4-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="f6ef4-115">기본적인 C# 기능을 프로그래밍 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ef4-115">Some basic C# programming ability.</span></span>
* <span data-ttu-id="f6ef4-116">HoloLens 2 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ef4-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
