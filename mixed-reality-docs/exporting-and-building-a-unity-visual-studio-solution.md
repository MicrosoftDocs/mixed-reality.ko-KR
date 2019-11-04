---
title: Unity Visual Studio 솔루션 내보내기 및 빌드
description: 이 문서에서는 Visual Studio에서 빌드 및 배포할 수 있도록 Unity에서 혼합 현실 프로젝트를 내보내는 방법을 간략하게 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, 내보내기, 빌드, 배포
ms.openlocfilehash: 752a9dd002d27d24d9b80a1a97cb07a44237b9e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435568"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Unity Visual Studio 솔루션 내보내기 및 빌드

응용 프로그램에서 시스템 키보드를 사용 하지 않으려는 경우 응용 프로그램에서 메모리를 약간 줄이고 시작 시간을 약간 단축 하므로 *D3D* 를 사용 하는 것이 좋습니다. 프로젝트에서 TouchScreenKeyboard API를 사용 하 여 시스템 키보드를 사용 하는 경우 *XAML*로 내보내야 합니다.

## <a name="how-to-export-from-unity"></a>Unity에서 내보내는 방법

Unity 빌드 설정 ![](images/unitybuildsettings-300px.png)<br>
*Unity 빌드 설정*

1. Unity에서 프로젝트를 내보낼 준비가 되 면 **파일** 메뉴를 열고 **빌드 설정** ...을 선택 합니다.
2. 열려 있는 장면 **추가** 를 클릭 하 여 빌드에 장면을 추가 합니다.
3. **빌드 설정** 대화 상자에서 다음 옵션을 선택 하 여 HoloLens를 내보냅니다.
   * **Platform:** *유니버설 Windows 플랫폼* 하 고 선택 항목을 적용 하려면 **스위치 플랫폼** 을 선택 해야 합니다.
   * **SDK:** *Universal 10*.
   * **UWP 빌드 형식:** *D3D*입니다.
4. **선택 사항**: **Unity C# 프로젝트:** 선택 됨.

>[!NOTE]
>이 확인란을 선택 하면 다음 작업을 수행할 수 있습니다.
>* Visual Studio 원격 디버거에서 앱을 디버그 합니다.
>* WinRT Api 용 IntelliSense를 C# 사용 하는 동안 Unity 프로젝트의 스크립트를 편집 합니다.

5. **빌드 설정 ...** 창에서 **플레이어 설정 ...** 을 엽니다.
6. 유니버설 Windows 플랫폼 탭 **에 대 한 설정을** 선택 합니다.
7. **XR 설정** 그룹을 확장 합니다.
8. **XR 설정** 섹션에서 **가상 현실 지원** 확인란을 선택 하 여 새 **가상 현실 장치** 목록을 추가 하 고 **"Windows Mixed Reality"** 가 지원 되는 장치로 나열 되는지 확인 합니다.
9. **빌드 설정** 대화 상자로 돌아갑니다.
10. **빌드**를 선택 합니다.
11. 표시 되는 Windows 탐색기 대화 상자에서 Unity의 빌드 출력을 보관할 새 폴더를 만듭니다. 일반적으로 "App" 폴더의 이름을로 합니다.
12. 새로 만든 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.
13. Unity가 빌드를 완료 하면 Windows 탐색기 창이 프로젝트 루트 디렉터리에 열립니다. 새로 만든 폴더로 이동 합니다.
14. 이 폴더 내에 있는 생성 된 Visual Studio 솔루션 파일을 엽니다.

## <a name="when-to-re-export-from-unity"></a>Unity에서 다시 내보내는 경우

Unity에서 앱C# 을 내보낼 때 "프로젝트" 확인란을 선택 하면 모든 Unity 스크립트 파일이 포함 된 Visual Studio 솔루션이 만들어집니다. 이를 통해 Unity에서 다시 내보내지 않고 스크립트를 반복할 수 있습니다. 그러나 스크립트의 내용만 변경 하지 않는 프로젝트를 변경 하려는 경우에는 Unity에서 다시 내보내야 합니다. Unity에서 다시 내보내는 데 필요한 몇 가지 예는 다음과 같습니다.
* 프로젝트 탭에서 자산을 추가 하거나 제거 합니다.
* Inspector 탭에서 값을 변경 합니다.
* 계층 탭에서 개체를 추가 하거나 제거 합니다.
* Unity 프로젝트 설정을 변경 합니다.

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Unity Visual Studio 솔루션 빌드 및 배포

응용 프로그램 빌드 및 배포의 나머지 부분은 [Visual Studio](using-visual-studio.md)에서 발생 합니다. Unity 빌드 구성을 지정 해야 합니다. Unity의 명명 규칙은 Visual Studio에서 일반적으로 사용 하는 것과 다를 수 있습니다.

|  구성  |  설명 | 
|----------|----------|
|  디버그  |  모든 최적화를 해제 하 고 프로파일러를 사용 하도록 설정 합니다. 스크립트를 디버깅 하는 데 사용 됩니다. | 
|  마스터  |  모든 최적화를 사용 하도록 설정 하 고 프로파일러를 사용 하지 않습니다. 스토어에 앱을 제출 하는 데 사용 됩니다. | 
|  릴리스  |  모든 최적화를 설정 하 고 프로파일러를 사용 하도록 설정 합니다. 앱 성능을 평가 하는 데 사용 됩니다. | 

위의 목록은 Visual Studio 프로젝트를 생성 해야 하는 일반적인 트리거의 하위 집합입니다. 일반적으로 Visual Studio 내에서 .cs 파일을 편집 하는 경우 Unity 내에서 프로젝트를 다시 생성할 필요가 없습니다.

## <a name="troubleshooting"></a>문제 해결

Visual Studio 프로젝트에서 .cs 파일에 대 한 편집 내용이 인식 되지 않는 것을 발견 한 경우 Unity의 빌드 메뉴에서 C# VS 프로젝트를 생성할 때 "unity 프로젝트"가 선택 되어 있는지 확인 합니다.
