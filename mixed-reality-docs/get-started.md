---
title: 시작
description: 이 가이드에는 혼합된 현실 개발을 사용 하 여 즉시 가동 및 실행 하는 가장 빠른 방법은 간략하게 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 시작, 기초, HoloLens, 몰입 형 헤드셋, ar, vr, unity, visual studio, 빠른 시작 하는 방법
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873965"
---
# <a name="get-started"></a>시작

혼합된 현실 개발을 시작 합니다! MR 접하는 경우이 가이드는 시작 하려면 허브 및 최대한 빨리 실행 됩니다. 개발에 대 한 사용자 PC의 집합을 시작, 장치, 준비 및 MR 개발 프로세스를 신속 하 게 하는 도구를 설치 하 게 도울 것입니다. 

## <a name="intro-to-mixed-reality"></a>혼합된 현실에 대 한 소개

"Mixed reality"가 뭐 냐고요 및 연결 증강된 현실 (AR) 하는 방법에 대 한 몇 가지 질문을 해야 하 고 가상 현실 (VR). 즉, 혼합된 현실은 확대 된 현실에서 모든 항목을 다루는 스펙트럼 이므로 디지털 세계와 실제 세계의 혼합 현실 세계에 거의 완전히 인 가상 현실에 실제 세계에서 디지털 콘텐츠 위치 디지털 바뀝니다. 

![HoloLens 및 몰입 형 (VR) 헤드셋을 지 원하는 혼합된 현실 앱의 예제](images/mr-island.png)<br>
*HoloLens 및 몰입 형 (VR) 헤드셋 혼합된 현실 앱 수 있습니다.*

Windows Mixed Reality MR 스펙트럼을 처리할 수 있는 도구 집합을 단일 개발 플랫폼으로 만든 및 현재 동일한 스펙트럼을 포괄 하는 두 개의 장치 유형을 지원: [Microsoft HoloLens](https://www.microsoft.com/hololens), 전 세계의 첫 번째 독립적인된 holographic 헤드셋, 및 [Windows Mixed Reality 몰입 형 헤드셋 및 동작 컨트롤러](https://www.microsoft.com/windows/windows-mixed-reality), 강력한 가상 현실 환경에 대 한 PC에 연결 합니다. 이 내용을 확인할 수 있습니다 [혼합 현실?] (문서를 보다 정확 하 게 응답 하려는 경우입니다.

## <a name="choose-your-development-path"></a>배포 경로 선택 합니다.

혼합된 현실 앱을 개발 하는 가장 쉬운 방법은 사용 하 여 [Unity](https://unity3d.com), 게임 개발에 대 한 자주 사용 되는 미들웨어를 강력 하 고 인기 있는 도구입니다. 사용자 지정 엔진을 사용 하려는 경우 수도 있습니다 [DirectX에 대 한 빌드](directx-development-overview.md), 하지만 대부분의 MR 개발자가 게임 및 앱에 대 한 Unity를 사용 합니다. Unity를 사용 하 여 HoloLens, (VR) 헤드셋 몰입 형, 또는 둘 다를 대상으로 하는 혼합된 현실 앱을 만들 수 있습니다.

## <a name="prepare-your-pc-and-devices-for-development"></a>PC 및 장치 개발을 위한 준비

HoloLens, (VR) 헤드셋 몰입 형, 또는 둘 다를 대상으로 하는 혼합된 현실 앱을 빌드하는 지 여부를 일반적인 도구와 Api 집합을 사용할 것입니다. 또한 PC 개발을 충분히 강력한 인지 확인 합니다. 

>[!NOTE]
>권장 되는 개발 PC 사양에서 지원 되는 버전의 각 소프트웨어 도구 및 관련 설정 또는 구성에서 각각에 대 한 정보를 찾을 수 있습니다 합니다 [도구를 설치](install-the-tools.md) 문서. 아래 도구를 설치 하기 전에 해당 문서를 검토 하세요.

설치 하는 도구:
* [Unity](https://store.unity.com/download)
* [Visual Studio (windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [Unity 용 혼합된 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

또한 하려는 [대상 장치의 개발자 모드로 설정 하 고 대상 장치에 앱을 배포 하기 위한 Visual Studio 구성](using-visual-studio.md)합니다.

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>혼합 현실 용 도구 키트에 Unity에 대 한 메모

![Unity에 대 한 MRTK](images/mrtkandunity.png)<br>

***YOYO이 구체화 후 왜 MRTK UNITY 정말 대단한 있고 모든 멋진 내부:) 모든 사람에 게***

혼합 현실 도구 키트는 스크립트 컬렉션 구성 요소를 하며 Microsoft HoloLens 및 Windows Mixed Reality 헤드셋을 대상으로 하는 응용 프로그램의 개발을 가속화 하세요. 프로젝트는 장벽이 혼합된 현실 응용 프로그램을 만들고 우리가 증가 함에 따라 커뮤니티에 다시 기여에 항목을 줄이는 목표로 합니다.

## <a name="start-your-first-mr-project"></a>첫 번째 MR 프로젝트 시작

이제는 PC와 장치 설정 되 면 Unity에서 첫 번째 혼합된 현실 프로젝트를 만들 준비가 되었습니다. 첫 번째 MR academy 과정을 따르려면 [MR 기본 사항 100: Unity를 사용 하 여 시작](holograms-100.md), 혼합된 현실 헤드셋에서 실행 되 고 큐브 엔드에서 해야 합니다.

![혼합된 현실 Unity 프로젝트의 큐브 스크린 샷](images/mr-cube.PNG)<br>
*첫 번째 혼합된 현실 프로젝트에 Unity-hello world!*

## <a name="learn-more-and-get-help"></a>자세히 알아보고 도움말을 보려면

첫 번째 MR 프로젝트를 성공적으로 만든 했으므로 자세한 아마도 배고픈 완료 되었습니다! 해야 하는 데 도움이 되는 일부 리소스는 다음과 같습니다.
* [혼합 현실 개발자 설명서](mixed-reality.md) -아직 여기 이지만 등 많은 기술 문서, 디자인 지침, 샘플 프로젝트 및 사례 연구를 포함 하 여 확인 합니다.
* [혼합 현실 자습서](tutorials.md) -핵심 MR 구성 요소를 구현 하는 데 프로젝트 설정에서 모든 내용을 다루는 자습서를 따라, MR 앱에 클라우드 서비스에 Azure를 통합 합니다.
* [Unity에 알아봅니다](https://unity3d.com/learn) -Unity의 웹 사이트가 학습 과정의 모든 단계에서 작성자에 대 한 자습서, 프로젝트 및 라이브 교육 세션 제공 합니다.

또한 이러한 유용한 커뮤니티 리소스에서 도움말을 얻을 수 있습니다.
* [혼합 현실을 개발자 포럼](https://forums.hololens.com/) -요청 및 질문에 답변으로 Microsoft에서 직접 MR 개발 뉴스 읽기 혼합된 현실 개발자를 위한 공식 포럼입니다.
* [HoloDevelopers Slack 채널](https://holodevelopersslack.azurewebsites.net/) -가장 강력 하 고 략이 외부 혼합 현실 관련 개발자 채널은 여기에 개발자 지식 및 유용 합니다.
* [Unity 포럼](https://forum.unity3d.com/) -Unity의 공식 포럼입니다.
