---
title: 1. 시작
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서 시리즈 1/6부
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 39e4e7218341dcc69eacf01f43b5e0721e76031b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720379"
---
# <a name="1-getting-started"></a>1. 시작

여기서는 혼합 현실을 처음 사용하거나 익숙한 사용자 모두를 위해 [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) 및 [Unreal Engine](https://www.unrealengine.com/en-US/)을 시작하는 출발점을 제시합니다. 이 자습서 시리즈에서는 [Unreal용 Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unreal)의 일부인 [UX Tools 플러그 인](https://github.com/microsoft/MixedReality-UXTools-Unreal)을 사용하여 대화형 체스 앱을 빌드하는 방법을 단계별로 안내합니다. 플러그 인은 코드, 청사진 및 예제를 통해 프로젝트에 일반 UX 기능을 추가하는 데 도움이 됩니다. 

![뷰포트에서 장면 종료](images/unreal-uxt/5-endscene.PNG)

시리즈를 마치면 다음에 대한 실습 경험을 갖게 됩니다.
* 새 프로젝트 시작
* 혼합 현실 설정
* 사용자 입력 작업
* 단추 추가
* 에뮬레이터 또는 디바이스에서 재생

궁금한 점은 [Unreal 개발 개요](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)를 확인하세요.

## <a name="prerequisites"></a>필수 구성 요소
진행하기 전에 다음 요구 사항에 부합하는지 확인합니다.
* Windows 10 1809 이상
* Windows 10 SDK 10.0.18362.0 이상
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 이상
* [개발용으로 구성된](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 디바이스 또는 에뮬레이터
* Visual Studio 2019(아래 워크로드 포함)

### <a name="installing-visual-studio-2019"></a>Visual Studio 2019 설치
마지막 단계는 다음과 같이 Visual Studio를 설정하는 것입니다.
1. 최신 버전의 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)를 다운로드합니다.
2. 다음 [워크로드](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads)를 설치합니다.
    * C++를 사용한 데스크톱 개발
    * .NET 데스크톱 개발
    * 유니버설 Windows 플랫폼 개발

3. 다음 [구성 요소](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components)를 설치합니다.
    * 컴파일러, 빌드 도구 및 런타임 > MSVC v142 - VS 2019 C++ ARM64 빌드 도구(최신 버전)

간단하죠. 이제 체스 앱 프로젝트를 시작할 준비가 되었습니다.

[다음 섹션: 2. 프로젝트 및 첫 번째 애플리케이션 초기화](unreal-uxt-ch2.md)