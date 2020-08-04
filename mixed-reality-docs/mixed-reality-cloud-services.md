---
layout: LandingPage
title: 혼합 현실 클라우드 서비스
description: 혼합 현실 클라우드 서비스 리소스
author: hferrone
ms.author: v-haferr
ms.date: 06/5/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, 개발, 개발, HoloLens, 클라우드 서비스
ms.openlocfilehash: 26c5f91eab2b39fbd809010ab0ac738d81dff854
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390220"
---
# <a name="cloud-services"></a>클라우드 서비스

## <a name="overview"></a>개요

**Azure Remote Rendering** 및 **Azure Spatial Anchors**와 같은 Mixed Reality 클라우드 서비스는 개발자가 다양한 플랫폼에서 매력적인 몰입형 경험을 빌드할 수 있도록 도와줍니다. 이러한 서비스를 사용하면 사용자 환경의 컨텍스트에서 3D 학습, 예측 장비 유지 관리 및 디자인 검토를 위한 애플리케이션을 만들 때 공간 인식을 프로젝트에 통합할 수 있습니다.

또한 Mixed Reality 우산에 속하지는 않지만 기존 프로젝트에 쉽게 추가할 수 있는 다른 Azure 서비스가 있습니다. Unity용으로 개발하는 경우, 시작하는 데 도움이 되는 다양한 [자습서](#standalone-services)가 이 페이지의 맨 아래에 나열되어 있습니다.

## <a name="mixed-reality-services"></a>Mixed Reality 서비스

### <a name="azure-remote-rendering"></a>Azure Remote Rendering
[Azure Remote Rendering](https://docs.microsoft.com/azure/remote-rendering)(ARR)은 매우 복잡한 3D 모델을 실시간으로 렌더링하는 데 사용할 수 있는 서비스입니다. ARR은 현재 공개 미리 보기로 제공됩니다. 이는 HoloLens 2 또는 Windows 데스크톱 PC를 대상으로 하는 Unity 또는 Native C++ 프로젝트에 추가할 수 있습니다.

![Unity 쇼케이스 앱에서 Azure Remote Rendering의 예](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors
[Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors)(ASA)는 공간적으로 인식되는 혼합 현실 애플리케이션을 빌드할 수 있는 플랫폼 간 서비스입니다. Azure Spatial Anchors를 사용하면 실제 규모로 여러 디바이스에서 홀로그램 콘텐츠를 매핑, 유지 및 공유할 수 있습니다.

![Azure Spatial Anchors의 예](images/persistence.gif)

서비스는 다양한 환경에서 개발될 수 있으며, 대규모 디바이스 및 플랫폼 그룹에 배포할 수 있습니다. 이를 통해 다음과 같은 사용 가능한 플랫폼 목록에 대해 특별히 허가됩니다.
* HoloLens용 Unity
* iOS용 Unity
* Android용 Unity
* 네이티브 iOS
* 네이티브 Android
* C++/WinRT 및 HoloLens용 DirectX
* iOS용 Xamarin
* Android용 Xamarin

## <a name="standalone-services"></a>독립 실행형 서비스
아래에 나열된 독립 실행형 서비스는 Mixed Reality에는 적용되지 않지만, 다양한 개발 컨텍스트에서 유용하게 사용할 수 있습니다. Unity에서 개발하는 경우 이러한 각 서비스를 새로운 프로젝트 또는 기존 프로젝트에 통합할 수 있습니다.

### <a name="device-support"></a>디바이스 지원
<table>
    <tr>
        <td><strong>Azure Cloud Service</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens 1세대</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td><a href="mr-azure-301.md">언어 번역</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302.md">컴퓨터 비전</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302b.md">사용자 지정 비전</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-303.md">디바이스 간 알림</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-304.md">얼굴 인식</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-305.md">함수 및 스토리지</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-306.md">비디오 스트리밍</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-307.md">기계 학습</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-308.md">함수 및 스토리지</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-309.md">애플리케이션 인사이트</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-310.md">개체 감지</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-312.md">봇 통합</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>
