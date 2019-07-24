---
title: 시작
description: 이 가이드에서는 혼합 현실 개발을 시작 하 고 실행 하는 가장 빠른 방법을 간략하게 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 시작 하기, 기본 사항, HoloLens, 모던 헤드셋, ar, vr, unity, visual studio, 빠른 시작, 방법
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873965"
---
# <a name="get-started"></a>시작

혼합 현실 개발을 시작 합니다. MR을 처음 접하는 경우이 가이드는 가능한 한 빨리 시작 및 실행 하기 위한 허브입니다. PC를 개발용으로 설정 하 고, 장치를 준비 하 고, MR 개발 프로세스를 가속화 하는 도구를 설치 하는 데 도움이 됩니다. 

## <a name="intro-to-mixed-reality"></a>혼합 현실 소개

"혼합 현실" 이란 무엇 이며, 확장 된 현실 (AR) 및 가상 현실 (VR)과의 관계에 대 한 몇 가지 질문이 있을 수 있습니다. 간단히 말해서 혼합 현실은 디지털 세계와 물리적 세계를 혼합 하는 것 이므로, 디지털 콘텐츠가 실제 세계에 배치 되는 모든 확장 현실에서 실제 세계에 거의 완전히 적용 되는 모든 항목을 포함 하는 스펙트럼입니다. 디지털로 대체 되었습니다. 

![HoloLens 및 몰입 형 (VR) 헤드셋을 모두 지 원하는 혼합 현실 앱의 예](images/mr-island.png)<br>
*혼합 현실 앱은 HoloLens 및 몰입 형 (VR) 헤드셋을 모두 지원할 수 있습니다.*

Windows Mixed Reality를 단일 개발 플랫폼으로 만들었으며 MR 스펙트럼을 처리할 수 있는 도구 집합을 만들었으며 현재 동일한 스펙트럼을 다루는 두 가지 장치 유형을 지원 합니다. [Microsoft HoloLens](https://www.microsoft.com/hololens), 세계 최초의 자체 포함 된 holographic 헤드셋, 강력한 가상 현실 환경을 위해 PC에 연결 하는 [Windows Mixed Reality 모던 헤드셋 및 동작 컨트롤러](https://www.microsoft.com/windows/windows-mixed-reality)입니다. [혼합 현실?]의 정의를 확인할 수 있습니다. (관심이 있는 경우 보다 철저 한 답을 위한 문서입니다.

## <a name="choose-your-development-path"></a>개발 경로 선택

혼합 현실 앱을 개발 하는 가장 쉬운 방법은 게임 개발에 자주 사용 되는 강력 하 고 인기 있는 미들웨어 도구인 [Unity](https://unity3d.com)를 사용 하는 것입니다. 사용자 지정 엔진을 사용 하려는 경우 [DirectX에 대해 빌드할](directx-development-overview.md)수도 있지만 대부분의 MR 개발자는 게임 및 앱에 Unity를 사용 합니다. Unity를 사용 하면 HoloLens, 모던 (VR) 헤드셋 또는 둘 다를 대상으로 하는 혼합 현실 앱을 만들 수 있습니다.

## <a name="prepare-your-pc-and-devices-for-development"></a>개발을 위한 PC 및 장치 준비

HoloLens, 모던 (VR) 헤드셋 또는 둘 다를 대상으로 하는 혼합 현실 앱을 빌드하 든 관계 없이 일반적인 도구 및 Api 집합을 사용 하 게 됩니다. 또한 사용자의 PC가 개발 하는 데 충분 한지 확인 해야 합니다. 

>[!NOTE]
>개발 PC 사양, 지원 되는 각 소프트웨어 도구 버전 및 관련 설정 또는 구성 메모에 대 한 권장 사항은 [도구 설치](install-the-tools.md) 문서에서 찾을 수 있습니다. 아래 도구를 설치 하기 전에 해당 문서를 검토 하십시오.

설치할 도구:
* [Unity](https://store.unity.com/download)
* [Visual Studio (Windows 10 SDK 포함)](https://developer.microsoft.com/windows/downloads)
* [Unity 용 혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

또한 [대상 장치를 개발자 모드로 전환 하 고 대상 장치에 앱을 배포 하기 위해 Visual Studio를 구성](using-visual-studio.md)하려고 합니다.

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Unity 용 Mixed Reality 도구 키트에 대 한 참고 사항

![Unity 용 MRTK](images/mrtkandunity.png)<br>

***YOYO 그 이유를 이야기 하 고, MRTK-UNITY가 정말 놀라운 것으로 생각 하는 이유를 모두 제공 하 고:)***

Mixed Reality Toolkit은 Microsoft HoloLens 및 Windows Mixed Reality 헤드셋을 대상으로 하는 응용 프로그램의 개발을 가속화 하기 위한 스크립트 및 구성 요소의 모음입니다. 이 프로젝트는 혼합 현실 애플리케이션을 만들기 위한 진입 장벽을 낮추고 커뮤니티에 다시 기여하는 것을 목표로 합니다.

## <a name="start-your-first-mr-project"></a>첫 번째 MR 프로젝트 시작

이제 PC와 장치가 설정 되었으므로 Unity에서 첫 번째 혼합 현실 프로젝트를 만들 준비가 되었습니다. 첫 번째 mr 아카데미 과정, [MR 기본 사항 100을 따릅니다. Unity](holograms-100.md)를 시작 하면 혼합 현실 헤드셋에서 큐브를 실행 하 고 실행 하 게 됩니다.

![혼합 현실 Unity 프로젝트의 큐브 스크린샷](images/mr-cube.PNG)<br>
*Unity의 첫 번째 혼합 현실 프로젝트-hello 세계!*

## <a name="learn-more-and-get-help"></a>자세한 정보 및 도움말 보기

첫 번째 MR 프로젝트를 성공적으로 만들었으므로 이제 더 많은 작업이 필요할 수 있습니다. 도움이 되는 몇 가지 리소스는 다음과 같습니다.
* [혼합 현실 개발자 설명서](mixed-reality.md) -이미 여기에 있지만 기술 문서, 디자인 지침, 샘플 프로젝트 및 사례 연구를 비롯 하 여 체크 아웃할 수 있는 많은 작업이 있습니다.
* [혼합 현실 자습서](tutorials.md) -프로젝트를 설정 하 고, 핵심 mr 빌딩 블록을 구현 하 고, Azure cloud SERVICES를 MR 앱에 통합 하는 것과 관련 된 자습서를 함께 수행 합니다.
* [Unity에 대해 알아보기](https://unity3d.com/learn) -unity의 웹 사이트에서는 모든 학습 단계에서 작성자를 위한 자습서, 프로젝트 및 라이브 학습 세션을 제공 합니다.

이러한 유용한 커뮤니티 리소스에서 도움을 받을 수도 있습니다.
* [혼합 현실 개발자 포럼](https://forums.hololens.com/) -혼합 현실 개발자를 위한 공식 포럼에서 질문을 하 고 답변할 뿐만 아니라 Microsoft에서 직접 MR 개발 뉴스를 읽을 수 있습니다.
* [HoloDevelopers 여유 시간 채널](https://holodevelopersslack.azurewebsites.net/) -가장 강력 하 고 resourceful 외부 혼합 현실 개발자 채널 여기에서 개발자는 유용 하 고 유용 합니다.
* [Unity 포럼](https://forum.unity3d.com/) -unity의 공식 포럼.
