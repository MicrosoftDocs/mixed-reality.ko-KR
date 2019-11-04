---
title: Unity를 사용 하 여 관리 되는 디버깅 IL2CPP
description: 이 문서에서는 Unity IL2CPP UWP 프로젝트에서 관리 되는 디버거를 실행 하는 방법을 설명 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, 디버깅, il2cpp
ms.openlocfilehash: fd09c3ca1bd410c56e46eb8e8815742f87482d08
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439634"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Unity를 사용 하 여 관리 되는 디버깅 IL2CPP

다음 단계를 수행 하 여 관리 되는 디버거를 Unity IL2CPP UWP 빌드에 연결 합니다. 이 가이드는 원래 HoloLens 및 HoloLens 2 용으로 개발 되었습니다.

1. [멀티 캐스트](https://en.wikipedia.org/wiki/Multicast)를 지 원하는 네트워크에 있어야 합니다.
1. UWP 게시 설정 기능의 Unity에서 **Internetclientserver** 및 **PrivateNetworkClientServer** 가 선택 되어 있는지 확인 합니다.

    ![UWP 게시 설정 기능](images/il2cpp-debugging-capabilities.png)

1. Unity UWP 빌드 설정 구성:
    - 개발 빌드
    - 스크립트 디버깅
    - 관리 되는 디버거 대기 (옵션)

    ![UWP 빌드 설정](images/il2cpp-debugging-build.png)

1. Unity에서 빌드합니다.
1. Visual Studio 솔루션에서 장치에 빌드 및 배포 합니다. **디버그** 또는 **릴리스** 구성을 사용 하 여 빌드해야 합니다. **마스터** 구성은 Unity 프로파일러를 사용 하지 않도록 설정 하 고 최적의 디버깅을 방지할 수 있습니다. 필요한 경우 솔루션에서 appxmanifest.xml의 기능 목록에 있는 **인터넷 (클라이언트 & 서버)** 및 **개인 네트워크 (클라이언트 & 서버)** 를 확인 합니다.
1. 장치에서 앱을 시작 합니다. 장치가 PC와 동일한 네트워크에 연결 되어 있는지 확인 합니다.
1. 장치가 USB를 통해 PC에 연결 **되지** 않았는지 확인 합니다.
1. C# 스크립트를 보고 편집할 수 있는 Unity에서 스크립트를 두 번 클릭 하면 생성 된 Visual Studio 솔루션으로 이동 합니다.
1. 디버그 > Unity 디버거를 연결 합니다.

    ![Unity 디버거 연결](images/il2cpp-debugging-attach.png)

1. 목록에서 장치를 선택 하 고 "확인"을 클릭 하 여 연결 합니다.

    ![장치 목록](images/il2cpp-debugging-machines.png)
