---
title: Unity 및 Visual Studio를 사용 하 여 작업에 대 한 모범 사례
description: 팁과 요령을 Unity 및 Visual Studio를 사용 하 여 혼합된 현실 응용 프로그램을 만드는 워크플로 간소화 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: visual studio, HoloLens, 몰입 형 헤드셋을 unity 배포
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604105"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Unity 및 Visual Studio를 사용 하 여 작업에 대 한 모범 사례

Unity를 사용한 혼합된 현실 응용 프로그램을 만드는 개발자를 위한 Unity 및 Visual Studio는 몰입 형 헤드셋 및/또는 HoloLens에 배포 되는 응용 프로그램 패키지를 만들 수 사이 전환 해야 합니다. 기본적으로 Visual Studio의 두 인스턴스는 필요한 (Unity 스크립트를 수정 하려면 1) 및 디버그 장치를 배포 하는 것입니다. 단일 Visual Studio 인스턴스를 사용 하 여 개발 있으며 Unity 프로젝트 내보내기 빈도가 감소 디버깅 환경을 개선 하는 다음 절차입니다.

## <a name="improving-iteration-time"></a>반복 시간 개선

Unity 및 Visual Studio를 사용 하 여 작업 하는 경우 일반적인 워크플로 문제는 여러 windows의 Visual Studio 열기 및 지속적으로 반복 하는 Visual Studio와 Unity 간에 전환 해야 하는 것입니다.
1. **Unity** -장면을 수정 하 고 Visual Studio 솔루션 내보내기
2. **Visual Studio (1)** -스크립트를 수정 합니다.
3. **Visual Studio (2)** -빌드하고 Unity 배포 내보낸 장치에 Visual Studio 솔루션

다행히 Visual Studio의 단일 인스턴스를 간소화 하 고 Unity에서 내보내기를 자주 수행에서 줄일 수가 있습니다.

때 [Unity에서 프로젝트를 내보내는](exporting-and-building-a-unity-visual-studio-solution.md)를 확인 합니다 **Unity C# 프로젝트** "파일 > 빌드 설정" 메뉴에서 확인란을 선택 합니다. 이제 Unity에서 내보낸 프로젝트에 프로젝트의 모든 C# 스크립트 및 몇 가지 이점이 있습니다.
* 스크립트를 작성 하 고 프로젝트를 빌드/배포에 대 한 Visual Studio의 동일한 인스턴스를 사용 합니다.
* 장면에는 Unity 편집기에서 변경 된 경우에 Unity에서 내보내기 스크립트의 내용을 변경할 수 있습니다 Visual Studio에서 다시 내보내지 않고 합니다.

사용 하 여 **Unity C# 프로젝트** 설정에 각 프로그램의 인스턴스가 하나만 열 수 해야 합니다.
1. **Unity** -장면을 수정 하 고 Visual Studio 솔루션 내보내기
2. **Visual Studio** -빌드 및 배포 Unity 장치에 Visual Studio 솔루션을 내보낸 다음 스크립트를 수정 하기 위한

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

다운로드 [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)

**Visual Studio Tools for Unity의 이점**
* 변수와 복잡 한 식을 평가 하는 중단점을 배치 하 여 Visual Studio에서 Unity 편집기에서 play 모드를 디버그 합니다.
* Unity 프로젝트 탐색기를 사용 하 여 Unity를 표시 하는 것과 동일한 계층을 사용 하 여 스크립트를 찾으려고 합니다.
* 직접 Visual Studio 내의 Unity 콘솔을 가져옵니다.
* 마법사를 사용 하 여 신속 하 게 만들거나 스크립트로 이동 합니다.

## <a name="expose-c-class-variables-for-easy-tuning"></a>표시 C# 쉽게 조정에 대 한 변수 클래스

클래스 변수를 노출 하는 방법은 두 가지가 있습니다. 이렇게 하려면 개인 변수를 [SerializeField] 특성을 추가 하는 것이 좋습니다. 따라서 편집기에서 액세스할 수 있지만 하지 프로그래밍 방식으로 노출 하도록 합니다.  확인 하려면 다른 옵션은 C# 편집기 UI에서에서이 노출 하려면 클래스 변수를 public입니다. 

두 가지 방법을 모두 사용 하면 편집기에서 재생 하는 동안 변수를 쉽게 조정할 수 있습니다. 이 상호 작용 정비공 속성을 조정 하는 데 특히 유용 합니다.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK 또는 Unity 업그레이드 후 UWP Visual Studio 솔루션을 다시 생성

새 Windows SDK 또는 Unity 엔진을 업그레이드 한 후 UWP Visual Studio 솔루션을 소스 제어에 체크 인 날짜 지 남 가져올 수 있습니다. Unity에서 새 UWP 솔루션을 빌드하고 다음 체크 인 된 솔루션으로 모든 차이점을 병합 하 여 업그레이드 후 해결할 수 있습니다.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>변경 내용이 쉽게 비교에 대 한 텍스트 형식으로 자산 사용

자산을 텍스트 형식으로 저장 쉽게 Visual Studio에서 콘텐츠 변경 내용이 차이 검토 합니다. 변경 하 여 "> 프로젝트 설정 > 편집기 편집"이을 사용할 수 있습니다 **Asset Serialization** 모드 **Force Text**합니다. 그러나 텍스트 자산 파일 변경 내용을 병합 하는 것은 오류가 발생 하기 쉬운 및 권장 되는 것이 좋습니다 소스 제어 시스템에서 이진 단독 체크 아웃을 사용 하도록 설정 합니다.
