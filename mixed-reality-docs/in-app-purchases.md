---
title: 앱에서 바로 구매
description: 앱 내 구매는 혼합 현실 앱에서 지원 되지만 몇 가지 작업을 설정 해야 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 앱에서 바로 구매, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515296"
---
# <a name="in-app-purchases"></a>앱에서 바로 구매

앱 내 구매는 HoloLens에서 지원 되지만 몇 가지 작업을 설정 해야 합니다.

앱 구매 기능에서을 활용 하려면 다음을 수행 해야 합니다.
* 슬레이트로 표시할 XAML [2d 뷰](app-views.md) 만들기
* 이로 전환 하 여 배치를 활성화 하면 몰입 형 보기가 남습니다.
* API: wait [Currentapp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_) 를 호출 합니다.

이 API는 앱 내 구매 이름, 설명 및 가격을 표시 하는 stock Windows OS 팝업을 표시 합니다. 그러면 사용자가 구매 옵션을 선택할 수 있습니다. 작업이 완료 되 면 앱은 사용자가 [몰입 형 보기로](app-views.md)다시 전환할 수 있도록 UI를 제공 해야 합니다.

데스크톱 기반 Windows Mixed Reality 모던 헤드셋을 대상으로 하는 앱의 경우 RequestProductPurchaseAsync API를 호출 하기 전에 XAML 뷰로 수동으로 전환할 필요가 없습니다.
