---
title: Unity 및 Visual Studio 사용에 대 한 모범 사례
description: Unity 및 Visual Studio를 사용 하 여 혼합 현실 응용 프로그램을 만드는 워크플로를 간소화 하기 위한 팁과 요령.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 배포, unity, visual studio, HoloLens, HoloLens 2, 모던 헤드셋
ms.openlocfilehash: 4d145568190ea43cf2ec43442a1c3d5ca4d92251
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502634"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Unity 및 Visual Studio 사용에 대 한 모범 사례

Unity를 사용 하 여 혼합 현실 응용 프로그램을 만드는 개발자는 HoloLens 및/또는 모던 헤드셋에 배포 되는 응용 프로그램 패키지를 빌드하기 위해 Unity와 Visual Studio 사이를 전환 해야 합니다. 기본적으로 Visual Studio의 두 인스턴스가 필요 합니다. 하나는 Unity 스크립트를 수정 하 고 다른 하나는 장치에 배포 하 고 디버그 하는 데 필요 합니다. 다음 절차에서는 단일 Visual Studio 인스턴스를 사용 하는 개발을 허용 하 고 Unity 프로젝트를 내보내는 빈도를 줄이고 디버깅 환경을 향상 시킵니다.

## <a name="improving-iteration-time"></a>반복 시간 향상

Unity의 .NET scripting 백 엔드 지원은 Unity 2018에서 더 이상 사용 되지 않으며 Unity 2019 이상에서 제거 되었습니다. 따라서 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)로 전환 하는 것이 좋습니다. 그러나 Unity에서 Visual Studio로의 빌드 시간이 길어질 수 있습니다. 더 빠른 반복을 위해 최상의 컴파일 결과를 위해 환경을 설정 해야 합니다.

1) 매번 미리 작성 된 파일을 다시 사용 하 여 프로젝트를 동일한 디렉터리에 빌드하여 증분 빌드를 활용 합니다.
2) 프로젝트에 대 한 맬웨어 방지 소프트웨어 검색 사용 안 함 & 빌드 폴더
   - Windows 10 설정 앱에서 **바이러스 & 위협 방지** 를 엽니다.
   - **바이러스 & 위협 방지 설정** 에서 **설정 관리** 를 선택 합니다.
   - **제외** 섹션에서 **제외 추가 또는 제거** 를 선택 합니다.
   - **제외 추가** 를 클릭 하 고 Unity 프로젝트 코드 및 빌드 출력을 포함 하는 폴더를 선택 합니다.
3) 빌드에 SSD 활용

자세한 정보는 [IL2CPP에 대 한 빌드 시간 최적화](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 를 검토 하세요. 또한 [IL2CPP Scripting 백 엔드에서 디버깅](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)을 검토 합니다.

또한 [ *Unityscriptanalyzer* Visual Studio 확장](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)을 설치 하는 것이 좋습니다. 이 도구는 더 최적화 C# 된 방식으로 작성할 수 있는 코드에 대 한 Unity 스크립트를 분석 합니다.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

다운로드 [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)

**Visual Studio Tools for Unity의 이점**
* 중단점을 배치 하 고 변수와 복잡 한 식을 평가 하 여 Visual Studio에서 Unity의 편집기 내 재생 모드를 디버그 합니다.
* Unity 프로젝트 탐색기를 사용 하 여 Unity에서 표시 하는 것과 정확히 동일한 계층 구조를 사용 하 여 스크립트를 찾습니다.
* Visual Studio 내에서 직접 Unity 콘솔을 가져옵니다.
* 마법사를 사용 하 여 신속 하 게 스크립트를 만들거나 탐색할 수 있습니다.

## <a name="expose-c-class-variables-for-easy-tuning"></a>손쉬운 C# 조정을 위해 클래스 변수 노출

클래스 변수를 노출 하는 방법에는 두 가지가 있습니다. [SerializeField] 특성을 전용 변수에 추가 하는 것이 좋습니다. 이렇게 하면 편집기에서 액세스할 수 있지만 프로그래밍 방식으로 노출 되지는 않습니다.  다른 옵션은 클래스 변수를 C# public으로 설정 하 여 편집기 UI에서 노출 하는 것입니다. 

두 방법 모두 편집기에서 재생 하는 동안 변수를 쉽게 수정할 수 있습니다. 이 기능은 상호 작용 정비공 속성을 튜닝 하는 데 특히 유용 합니다.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK 또는 Unity 업그레이드 후 UWP Visual Studio 솔루션 다시 생성

UWP Visual Studio 솔루션을 소스 제어에 체크 인 하면 새 Windows SDK 또는 Unity 엔진으로 업그레이드 한 후에 만료 될 수 있습니다. 업그레이드 후 Unity에서 새 UWP 솔루션을 빌드하고 체크 인 된 솔루션에 모든 차이점을 병합 하 여이 문제를 해결할 수 있습니다.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>텍스트 형식 자산을 사용 하 여 콘텐츠 변경 내용 비교

자산을 텍스트 형식으로 저장 하면 Visual Studio에서 콘텐츠 변경 차이을 보다 쉽게 검토할 수 있습니다. **Asset Serialization** 모드를 **텍스트 강제 적용**으로 변경 하 여 "> 프로젝트 설정 편집 > 편집기"에서이 기능을 사용 하도록 설정할 수 있습니다. 그러나 텍스트 자산 파일 변경 내용을 병합 하는 것은 오류가 발생 하기 쉬우며 권장 되지 않으므로 소스 제어 시스템에서 단독 이진 체크 아웃을 사용 하도록 설정 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목
- [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [IL2CPP에 대 한 빌드 시간 최적화](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*Unityscriptanalyzer* Visual Studio 확장](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
