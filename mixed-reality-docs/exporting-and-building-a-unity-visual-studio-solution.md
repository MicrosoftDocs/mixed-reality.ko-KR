---
title: 내보내기 및 Unity Visual Studio 솔루션 빌드
description: 이 문서 작성 하 고 Visual Studio에서 배포할 수 있도록 Unity에서 혼합된 현실 프로젝트 내보내기 설명 합니다.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: visual studio unity 내보내기, 빌드, 배포
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603697"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>내보내기 및 Unity Visual Studio 솔루션 빌드

권장 사항은 사용 하는 것에 시스템 키보드를 사용 하 여 응용 프로그램에서 하지, *D3D* 응용 프로그램은 약간 적은 메모리를 사용 하 고 시작 시간이 약간 더 빠릅니다. 프로젝트에서 TouchScreenKeyboard API를 사용 하 여 시스템 키보드를 사용 하는, 경우로 내보내려면 *XAML*합니다.

## <a name="how-to-export-from-unity"></a>Unity에서 내보내는 방법

![Unity 빌드 설정](images/unitybuildsettings-300px.png)<br>
*Unity 빌드 설정*

1. Unity에서 프로젝트를 내보낼 준비가 되었을 때 엽니다는 **파일** 선택한 메뉴 **빌드 설정...**
2. 클릭 **열기 장면 추가** 빌드에 장면 추가 합니다.
3. 에 **빌드 설정** 대화 상자에서 HoloLens에 대 한 내보내려면 다음 옵션을 선택 합니다.
   * **플랫폼:** *유니버설 Windows 플랫폼* 를 선택 해야 **플랫폼 전환** 적용 하려면 선택 항목에 대 한 합니다.
   * **SDK:** *유니버설 10*합니다.
   * **UWP 빌드 유형:** *D3D*.
4. **선택적**: **Unity C# 프로젝트:** 이 옵션을 선택 합니다.

>[!NOTE]
>이 확인란을 선택 수 있습니다.
>* Visual Studio 원격 디버거에서 앱을 디버그 합니다.
>* Unity에서 스크립트를 편집 C# WinRT Api에 대 한 IntelliSense를 사용 하는 동안 프로젝트입니다.

5. **빌드 설정...**  창을 열려면 **플레이어 설정...**
6. 선택 된 **유니버설 Windows 플랫폼에 대 한 설정을** 탭 합니다.
7. 확장 된 **xr 하이 설정을** 그룹입니다.
8. 에 **xr 하이 설정** 섹션을 확인 합니다 **가상 현실 지원** 새 추가 하려면이 확인란을 **가상 현실 장치용** 나열 하 고 확인 **"Windows 혼합 Reality"** 지원 되는 장치로 나열 됩니다.
9. 반환 합니다 **빌드 설정** 대화 합니다.
10. 선택 **빌드**합니다.
11. 표시 되는 Windows 탐색기 대화 상자에서 Unity의 빌드 출력을 포함할 새 폴더를 만듭니다. 일반적으로 "App" 폴더를 이름을합니다.
12. 새로 만든된 폴더를 선택 하 고 클릭 **폴더 선택**합니다.
13. Unity 빌드 완료 되 면 프로젝트 루트 디렉터리는 Windows 탐색기 창이 열립니다. 새로 만든 폴더로 이동 합니다.
14. 이 폴더 안에 있는 생성 된 Visual Studio 솔루션 파일을 엽니다.

## <a name="when-to-re-export-from-unity"></a>Unity에서 다시 내보내야 하는 경우

확인 된 "C# 프로젝트"에 모든 Unity 스크립트 파일을 포함 하는 Unity에서 앱을 내보내는 만들 때 Visual Studio 솔루션을 하는 확인란을 선택 합니다. 이 옵션을 사용 하면 스크립트에서 Unity를 다시 내보내지 않고 반복할 수 있습니다. 그러나 스크립트의 내용을 변경 하지는 프로젝트에 변경 하려는 경우에 Unity에서 다시 내보낼 해야 합니다. Unity에서 다시 내보내야 하는 시간의 몇 가지 예는:
* 추가 하거나 프로젝트 탭에서 자산을 제거 합니다.
* 관리자 탭에서 모든 값을 변경할 수 있습니다.
* 추가 하거나 계층 구조 탭에서 개체를 제거 합니다.
* Unity 프로젝트 설정을 변경 하기

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Unity Visual Studio 솔루션을 구축 및 배포

앱 빌드 및 배포의 나머지 부분에서 발생 [Visual Studio](using-visual-studio.md)합니다. Unity 빌드 구성을 지정 해야 합니다. Unity의 명명 규칙에서 무엇을 하 고 일반적으로 하는 데 Visual Studio에서 다를 수 있습니다.

|  Configuration  |  설명 | 
|----------|----------|
|  디버그  |  모든 최적화 해제 및 프로파일러 사용 됩니다. 스크립트를 디버그 하는 데 사용 합니다. | 
|  마스터  |  모든 최적화 켜져 있고 프로파일러를 사용 하지 않도록 설정 합니다. 앱 스토어에 제출 하는 데 사용 합니다. | 
|  릴리스  |  모든 최적화가 설정 하 고 프로파일러 활성화 됩니다. 앱 성능을 평가 하는 데 사용 합니다. | 

Note 위의 목록은 Visual Studio 프로젝트를 생성 해야 하는 일반적인 트리거의 하위 집합입니다. 일반적으로 Visual Studio 내에서.cs 파일을 편집 하는 프로젝트에서 Unity 내에서 다시 생성할 필요가 없습니다.

## <a name="troubleshooting"></a>문제 해결

Visual Studio 프로젝트의.cs 파일을 편집 하지 인식 되는 경우를 확인 하는 "Unity C# 프로젝트" VS 프로젝트 Unity의 빌드 메뉴에서 생성 하는 경우 확인 됩니다.
