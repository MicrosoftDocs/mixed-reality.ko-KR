---
title: Holographic DirectX 앱에서 XAML 사용
description: 2D XAML 뷰 및 DirectX 앱 및 XAML 뷰 및 몰입 형 뷰 모두 효율적으로 사용 하는 방법의 몰입 형 뷰 간의 전환의 영향에 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 관리, xaml, 키보드, 연습에서는 windows 혼합된 현실 등 UWP 앱에서 볼 DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598685"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Holographic DirectX 앱에서 XAML 사용

이 항목에서는 전환의 영향을 설명 합니다. [2D XAML 뷰 및 몰입 형 뷰](app-views.md) DirectX 앱 및 XAML 뷰 및 몰입 형 뷰 모두 효율적으로 사용 하는 방법입니다.

## <a name="xaml-view-switching-overview"></a>개요를 전환 하는 XAML 보기

HoloLens에서 2D XAML 뷰를 나중에 표시 될 수 있는 일반적으로 몰입 형 앱을 해당 XAML 뷰를 먼저 초기화 하 고 즉시 여기에서 몰입 형 뷰를 전환 해야 합니다. 즉, 앱 작업을 수행 하려면 먼저 XAML 로드 됩니다. 결과적으로, 시작 시간을 조금 향상 되 고 XAML을 계속 백그라운드;에 있는 동안 앱 프로세스에서 메모리 공간을 차지 시작 지연 시간 및 사용 현황은 어떤 앱에 따라 달라 집니다 메모리의 양을 기본 뷰로 전환 하기 전에 XAML을 사용 하 여 수행 합니다. 아무 일도 하지 몰입 형 보기 시작 점을 제외 하면 처음에는 코드에 XAML 시작에서 하는 경우에 영향을 부 있어야 합니다. 또한 사용자 holographic 렌더링, 몰입도 높은 뷰로 직접 수행 되므로 해당 렌더링에 대 한 XAML 관련 제한을 요청할지를 방지 합니다.

CPU와 GPU에 대 한 메모리 사용량을 계산 하는 참고 합니다. Direct3D 11 가상 그래픽 메모리 스왑할 수 있지만 XAML GPU 리소스의 일부 또는 전부를 스왑할 못할 것 이며 눈에 띄는 성능 저하가 있을 수 있습니다. 어느 방법이 든 모든 XAML 기능을 로드 하지 있습니다 하지 필요한 앱에 대 한 더 많은 공간을 둡니다를 더 나은 환경을 제공 합니다.

## <a name="xaml-view-switching-workflow"></a>워크플로 전환 하는 XAML 보기

몰입 형 모드에 XAML에서 직접이 되는 앱에 대 한 워크플로 다음과 같이 합니다.
* 앱이 2D XAML 보기에서 시작 합니다.
* 앱의 XAML 시작 시퀀스는 현재 시스템 holographic 렌더링을 지원 하는지 검색 합니다.
* 그렇다면 앱 몰입 형 뷰를 만들고 바로 앞으로 제공 합니다. XAML 로드 필요 하지 않은 항목에 대 한 모든 렌더링 클래스 및 XAML 보기에서 로드 하는 자산을 포함 하 여 Windows Mixed Reality 장치에서 생략 됩니다. 앱을 사용 하는 XAML 키보드 입력에 대 한 경우 해당 입력된 페이지도 만들어야 합니다.
* 그러지 않으면 XAML 뷰 비즈니스 평소 처럼 계속할 수 있습니다.

## <a name="tip-for-rendering-graphics-across-both-views"></a>두 보기에서 그래픽 렌더링에 대 한 팁

앱을 Windows Mixed Reality의 XAML 뷰에 대 한 DirectX에서 어느 정도의 렌더링을 구현 하는 경우 가장 좋은 두 보기를 사용 하 여 사용할 수 있는 하나의 렌더러를 만드는 것입니다. 렌더러 뷰 모두에서 액세스할 수 있는 하나의 인스턴스가 있어야 합니다. 및 2D 및 holographic 렌더링 간을 전환할 수 있어야 합니다. 로드 시간, 메모리 영향 및 보기를 전환할 때 교환할 리소스의 크기를 줄입니다 GPU 자산만 한 번만 로드 됩니다 이런 방식으로이.
