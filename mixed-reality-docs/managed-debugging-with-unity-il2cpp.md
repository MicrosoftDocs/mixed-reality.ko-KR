---
title: 관리 되는 Unity IL2CPP를 사용 하 여 디버깅
description: 이 문서에서는 Unity IL2CPP UWP 프로젝트에서 관리 되는 디버거를 실행 하는 방법에 설명 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: unity에 visual studio, 디버깅, il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148858"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>관리 되는 Unity IL2CPP를 사용 하 여 디버깅

Unity IL2CPP UWP 빌드에 관리 되는 디버거를 연결 하려면 다음이 단계를 따릅니다. 이 가이드는 HoloLens 및 HoloLens 2에 대 한 원래 개발 되었습니다.

1. 했는지 **InternetClientServer** 하 고 **PrivateNetworkClientServer** Unity UWP 게시 설정 기능에서 체크 인 됩니다.

    ![UWP 설정 기능 게시](images/il2cpp-debugging-capabilities.png)

1. Unity UWP 빌드 설정을 구성 합니다.
    - 개발 빌드
    - 스크립트 디버깅
    - 관리 되는 디버거 (선택 사항)에 대 한 대기

    ![UWP 빌드 설정](images/il2cpp-debugging-build.png)

1. Unity에서 빌드하십시오.
1. 빌드하고 Visual Studio 솔루션에서 장치에 배포 합니다. 사용 하 여 작성 해야 합니다 **디버그** 또는 **릴리스** 구성 합니다. 합니다 **마스터** 구성 Unity 프로파일러를 사용 하지 않도록 설정 하 고 최적의 디버깅 하지 못할 수 있습니다. 필요에 따라 확인 **인터넷 (클라이언트 및 서버)** 하 고 **개인 네트워크 (클라이언트 및 서버)** 솔루션에서 Package.appxmanifest에 기능 목록에서.
1. 장치에서 앱을 시작 합니다. 장치가 PC와 동일한 네트워크에 연결 되어 있는지 확인 합니다.
1. 장치 했는지 **아닙니다** USB 통해 PC에 연결 합니다.
1. Unity에서 확인 하 고 편집할 수 있는 스크립트를 두 번 클릭할 때 생성 되는 Visual Studio 솔루션으로 이동 하면 C# 스크립트입니다.
1. 디버그-> Unity 디버거를 연결 합니다.

    ![Unity 디버거 연결](images/il2cpp-debugging-attach.png)

1. 목록에서 장치를 선택 하 고 연결 하려면 "확인"을 클릭 합니다.

    ![장치 목록](images/il2cpp-debugging-machines.png)
