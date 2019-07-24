---
title: 깊이 카메라 백서-ISSCC 2018
description: Azure 용 Project Kinect 및 HoloLens의 다음 버전에서 활용 되는 깊이 카메라에 대해 설명 하는 기술 백서입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: 이벤트, iscc, 컴퓨터 비전, 연구, kinect, hololens, 깊이, tof
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516873"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="f1fe9-104">깊이 카메라 백서-ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="f1fe9-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="f1fe9-105">**제목과** 1Mpixel 65nm BSI 320MHz μm TOF Image 센서 3.5 Global 셔터 픽셀과 아날로그 범주화</span><span class="sxs-lookup"><span data-stu-id="f1fe9-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="f1fe9-106">**추가한** Cyrus S Bamji, 스와티어 Mehta, Barry Thompson, 발표자 Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, 있는지 McCauley, 리치 Mustansir, Mukadam Iskender, Agi, Shaun McCarthy Zhanping Xu, Travis Perry, William Qian, Vei-한자 변경 (, Prabhu Adepu, Gazi 알리, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="f1fe9-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="f1fe9-107">**ISSCC 2018에 표시 되 고 ISSCC 도씩 게시 됩니다. 유형. 용지, 2018 년 2 월**</span><span class="sxs-lookup"><span data-stu-id="f1fe9-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="f1fe9-108">3\.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-108">C.</span></span> <span data-ttu-id="f1fe9-109">Bamji et al., "1Mpixel 65nm BSI 320MHz Demodulated TOF Image 센서 (3.5 μm Global 셔터 픽셀 및 아날로그 범주화," ISSCC 도씩)</span><span class="sxs-lookup"><span data-stu-id="f1fe9-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="f1fe9-110">유형.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-110">Tech.</span></span> <span data-ttu-id="f1fe9-111">용지, pp. 94-95, 2 월 2018.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="f1fe9-112">IEEE 탐색 링크: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="f1fe9-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="f1fe9-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-113">© 2018 IEEE.</span></span> <span data-ttu-id="f1fe9-114">이 자료의 개인적인 사용은 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="f1fe9-115">다른 모든 용도에 대해 IEEE에서 사용 권한을 취득 해야 합니다. 예를 들어 광고 또는 판촉 목적을 위해이 자료를 reprinting/다시 게시 하거나, 새 집합적 작업을 만들거나, 서버 또는 목록에 대 한 재판매 또는 재배포를 위한 것입니다. 다른 작업에서이 작업의 저작권 구성 요소를 다시 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fe9-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="f1fe9-116">**백서**</span><span class="sxs-lookup"><span data-stu-id="f1fe9-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="f1fe9-117">![백서 미리 보기](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="f1fe9-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="f1fe9-118">다운로드 깊이 카메라 백서</span><span class="sxs-lookup"><span data-stu-id="f1fe9-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
