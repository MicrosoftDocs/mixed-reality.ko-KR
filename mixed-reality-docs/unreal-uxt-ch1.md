---
title: 1. 시작
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 튜토리얼의 1부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840132"
---
# <a name="1-getting-started"></a><span data-ttu-id="c02aa-104">1. 시작</span><span class="sxs-lookup"><span data-stu-id="c02aa-104">1. Getting started</span></span>

<span data-ttu-id="c02aa-105">Unreal Engine 4를 사용하여 대화형 HoloLens 2 체스 앱을 빌드하는 방법을 보여 주는 단계별 자습서입니다.</span><span class="sxs-lookup"><span data-stu-id="c02aa-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="c02aa-106">또한 개발 속도를 높이기 위해 Mixed Reality Toolkit의 UX Tools 플러그인을 사용하는 방법도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c02aa-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="c02aa-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c02aa-107">Prerequisites</span></span>

* <span data-ttu-id="c02aa-108">Windows 10 1809 이상</span><span class="sxs-lookup"><span data-stu-id="c02aa-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="c02aa-109">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="c02aa-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="c02aa-110">Unreal Engine 4.25 이상</span><span class="sxs-lookup"><span data-stu-id="c02aa-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="c02aa-111">[개발용으로 구성된](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 디바이스 또는 에뮬레이터</span><span class="sxs-lookup"><span data-stu-id="c02aa-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="c02aa-112">Visual Studio 2019(아래 워크로드 및 구성 요소 포함)</span><span class="sxs-lookup"><span data-stu-id="c02aa-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="c02aa-113">Visual Studio 2019, 워크로드 및 구성 요소 설치</span><span class="sxs-lookup"><span data-stu-id="c02aa-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="c02aa-114">최신 버전 Visual Studio 2019 설치 및/또는 업데이트</span><span class="sxs-lookup"><span data-stu-id="c02aa-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="c02aa-115">Visual Studio 2019 다운로드</span><span class="sxs-lookup"><span data-stu-id="c02aa-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="c02aa-116">다음 워크로드를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c02aa-116">Install the following workloads:</span></span>
* <span data-ttu-id="c02aa-117">C++를 사용한 데스크톱 개발</span><span class="sxs-lookup"><span data-stu-id="c02aa-117">Desktop development with C++</span></span>
* <span data-ttu-id="c02aa-118">.NET 데스크톱 개발</span><span class="sxs-lookup"><span data-stu-id="c02aa-118">.NET desktop development</span></span>
* <span data-ttu-id="c02aa-119">유니버설 Windows 플랫폼 개발</span><span class="sxs-lookup"><span data-stu-id="c02aa-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="c02aa-120">다음 개별 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c02aa-120">Install the following individual components:</span></span>
* <span data-ttu-id="c02aa-121">컴파일러, 빌드 도구 및 런타임 > MSVC v142 - VS 2019 C++ ARM64 빌드 도구(최신 버전)</span><span class="sxs-lookup"><span data-stu-id="c02aa-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="c02aa-122">다음 섹션: 2. 프로젝트 및 첫 번째 애플리케이션 초기화</span><span class="sxs-lookup"><span data-stu-id="c02aa-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)