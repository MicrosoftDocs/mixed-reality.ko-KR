---
title: 사례 연구-빌드 HoloSketch, 공간 레이아웃 및 HoloLens에 앱을 스케치 UX
description: HoloSketch는 장치의 공간 레이아웃 및 UX holographic 환경을 구축 하는 데는 HoloLens에 대 한 도구를 스케치 합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, 스케치, 앱
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600135"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>사례 연구-빌드 HoloSketch, 공간 레이아웃 및 HoloLens에 앱을 스케치 UX

HoloSketch는 장치의 공간 레이아웃 및 UX holographic 환경을 구축 하는 데는 HoloLens에 대 한 도구를 스케치 합니다. HoloSketch 페어링된 Bluetooth 키보드 및 마우스와 제스처 및 음성 명령을 사용 하 여 작동합니다. HoloSketch의 목적은 신속 하 게 시각화 및 반복에 대 한 간단한 UX 레이아웃 도구를 제공 하는 것입니다.

![HoloSketch: 공간 레이아웃 및 UX HoloLens에 앱을 스케치 합니다.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: 공간 레이아웃 및 HoloLens에 앱을 스케치 UX*

![신속 하 게 시각화 및 반복에 대 한 간단한 UX 레이아웃 도구입니다.](images/holosketch-image-02.png)<br>
*신속 하 게 시각화 및 반복에 대 한 간단한 UX 레이아웃 도구*

## <a name="features"></a>기능

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>빠른 연구 및 프로토타입 확장에 대 한 기본 형식

![기본 셰이프를 사용 하 여](images/holosketch-primitives-giphy.gif)

빠른 결집할 연구 및 프로토타입 확장에 대 한 기본 셰이프를 사용 합니다.

### <a name="import-objects-through-onedrive"></a>OneDrive 통해 개체 가져오기

![개체 가져오기](images/holosketch-importobjects-giphy.gif)

PNG/JPG 이미지 또는 3D FBX 개체 가져오기 (Unity에서 패키징 필요) OneDrive 통해 혼합된 현실 공간으로 합니다.

### <a name="manipulate-objects"></a>개체를 조작 합니다.

![개체를 조작합니다.](images/manipulate-objects-640px.jpg)

친숙 한 3D 개체 인터페이스를 사용 하 여 개체 (이동/회전/배율)를 조작 합니다.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, 마우스/키보드, 제스처 및 음성 명령

![Bluetooth를 지원합니다.](images/supports-bluetooth-640px.jpg)

HoloSketch는 Bluetooth 마우스/키보드, 제스처 및 음성 명령을 지원합니다.

## <a name="background"></a>배경

### <a name="importance-of-experiencing-your-design-in-the-device"></a>발생 하는 장치에서 디자인의 중요성

HoloLens에 대 한 무언가 설계 하는 경우 장치에서 디자인을 것입니다. 혼합된 현실 앱 디자인의 가장 큰 과제 중 하나는 확장성, 위치 및 깊이의 의미를 일반적인 2D 스케치 특히 통과 하기 어렵다는 것입니다.

### <a name="cost-of-2d-based-communication"></a>2D의 비용 기반 통신

UX 흐름과 다른 사람에 게는 시나리오와 효과적으로 통신 하려면 디자이너 Illustrator, Photoshop 및 PowerPoint와 같은 기존 2D 도구를 사용 하 여 자산을 만드는 시간이 많이 소비 끝날 수도 있습니다. 이러한 2D 디자인으로 변환 하기 위해 추가적인 작업이 필요한 경우가 많습니다 3D 넣습니다. 몇 가지 아이디어는 3D로 2D에서이 변환에서 손실 됩니다.

### <a name="complex-deployment-process"></a>복잡 한 배포 프로세스

혼합된 현실에 새 캔버스 이므로 기본적으로 디자인 반복 및 시행 착오 많은 수행 해야 합니다. Unity 및 Visual Studio와 같은 도구를 사용 하 여 모르는 디자이너에 대 한 쉽습니다 하지 HoloLens에 함께 무언가 배치 합니다. 일반적으로 장치에서 2D/3D 아트 워크를 보려면 아래 프로세스를 진행 해야 합니다. 이것은 신속 하 게 아이디어와 시나리오에서 반복 하는 디자이너에 대 한 큰 장애물입니다.

![복잡 한 배포 프로세스](images/holosketch-image-03-1000px.png)<br>
*배포 프로세스*

### <a name="simplified-process-with-holosketch"></a>HoloSketch 사용 하 여 간소화 된 프로세스

HoloSketch를 사용 하 여 개발 도구 및 포털 쌍 장치를 통하지 않고이 프로세스를 단순화 하려고 했습니다. OneDrive를 사용 하 여, 사용자는 HoloLens에 2D/3D 자산을 쉽게 배치 수 합니다.

![HoloSketch 사용 하 여 간소화 된 프로세스](images/holosketch-image-04-1000px.png)<br>
*HoloSketch 사용 하 여 간소화 된 프로세스*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>3 차원 디자인 사고 및 솔루션을 장려

이 도구는 디자이너 수 있도록 솔루션을 진정으로 3 차원 공간에서 탐색 및 2D에 빠지지 않았는지 라고 생각 합니다. 백그라운드 Hololens의 경우 실제 이므로 해당 UI에 대 한 3D 배경이 만들기에 대 한 생각 필요가 없습니다. HoloSketch는 디자이너가 Hololens에서 3D 디자인을 쉽게 탐색할 수 있는 방법을 열립니다.

## <a name="get-started"></a>시작

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>HoloSketch 2D 이미지 (JPG/PNG)을 가져오는 방법

* ' 문서/HoloSketch ' OneDrive 폴더에 JPG/PNG 이미지를 업로드 합니다.
* HoloSketch에서 OneDrive 메뉴에서 선택 하 고 환경에서 이미지를 배치 하는 일을 할 수 있습니다.

![2D 이미지 가져오기](images/import-2d-images-1000px.jpg)<br>
*이미지 및 OneDrive 통해 3D 개체 가져오기*

### <a name="how-to-import-3d-objects-into-holosketch"></a>HoloSketch 3D 개체를 가져오는 방법

OneDrive 폴더에 업로드 하기 전에 Unity 자산 묶음으로 3D 개체를 패키지 하려면 다음 단계를 따르세요. 이 프로세스를 사용 하 여 Microsoft 그림판 3D, Maya 및 배급사 4d 등 3D 소프트웨어에서 FBX/OBJ 파일을 가져올 수 있습니다.

>[!IMPORTANT]
>현재 버전 5.4.5f1 Unity 사용 하 여 자산 번들 만들기가 지원 됩니다.

1. 다운로드 하 고 Unity 프로젝트를 엽니다 ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)합니다. 이 Unity 프로젝트 번들 자산 생성을 위한 스크립트를 포함합니다.
2. 새 GameObject를 만듭니다.
3. 내용에 따라 GameObject 이름을 지정 합니다.
4. 검사기 창에서 ' 구성 요소 추가 '를 클릭 하 고 ' 상자 Collider'를 추가 합니다. 

   ![검사기 창에서 ' 구성 요소 추가 '를 클릭 하 고 ' 상자 Collider' 추가](images/holosketch-10a-assetbundles-1000px.png)
   
   ![검사기 창에서 ' 구성 요소 추가 '를 클릭 하 고 ' 상자 Collider' # 2를 추가 합니다.](images/holosketch-10b-assetbundles-1000px.png)

5. 프로젝트 패널에 끌어와 3D FBX 파일을 가져옵니다.
6. 계층 패널에 개체를 끌어 **아래에 새 GameObject**합니다.

   ![아래에 새 GameObject 계층 패널에 개체를 끌어 놓습니다.](images/holosketch-12-assetbundles-1000px.png)

7. 개체는 일치 하지 않는 경우에 collider 차원을 조정 합니다. 얼굴 개체를 회전 **z 축**합니다.

   ![개체는 일치 하지 않는 경우 collider 크기를 조정 합니다.](images/holosketch-13-assetbundles-1000px.png)

8. 계층 구조 창에서 [프로젝트] 패널에 개체를 끌어서 **prefab 있도록**입니다.
9. [관리자] 패널의 아래쪽에 드롭다운, 만들기 및 새 고유 이름을 할당 합니다. 아래 예제에서는 추가 하 고 'brownchair' AssetBundle 이름에 대 한 할당을 보여 줍니다. 

   ![[관리자] 패널의 아래쪽에 드롭다운을 클릭 하 고 새 고유 이름을 할당 합니다.](images/holosketch-14-assetbundles-1000px.png)

10. 모델 개체에 대 한 축소판 이미지를 준비 합니다. 
   ![프로젝트 패널에 이미지를 끌어서 개체에 사용 된 이름을 할당 합니다.](images/holosketch-15-assetbundles-1000px.png)

11. Unity 프로젝트의 '자산' 폴더 아래에 있는 'Assetbundles' 라는 폴더를 만듭니다.

12. [자산] 메뉴에서 파일을 생성 하려면 ' AssetBundles 빌드 '를 선택 합니다. 
   ![[자산] 메뉴에서 파일을 생성 하려면 ' AssetBundles 빌드 '를 선택 합니다.](images/holosketch-15a-assetbundles.png)


13. **OneDrive에서 /Files/Documents/HoloSketch 폴더에 생성된 된 파일을 업로드 합니다.** Asset_unique_name 파일만을 업로드 합니다. 매니페스트 파일 또는 AssetBundles 파일을 업로드할 필요가 없습니다. <br>
![파일/문서/HoloSketch에 파일 추가/폴더](images/holosketch-onedriveupload-1000px.png)
![HoloSketch의 OneDrive 메뉴에 추가 된 3D 개체를 보면](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>개체를 조작 하는 방법

HoloSketch 3D 소프트웨어에서 널리 사용 되는 기존 인터페이스를 지원 합니다. 이동을 사용 지정, 회전, 제스처 및 마우스를 사용 하 여 개체를 확장 합니다. 음성 또는 키보드를 사용 하 여 서로 다른 모드 간에 빠르게 전환할 수 있습니다.

### <a name="object-manipulation-modes"></a>개체 조작 모드

![개체를 조작 하는 방법](images/holosketch-image-06-1000px.png)<br>
*개체를 조작 하는 방법*

### <a name="contextual-and-tool-belt-menus"></a>상황별 및 도구 벨트 메뉴

**상황에 맞는 메뉴를 사용 하 여**

상황에 맞는 메뉴를 열려면 double 어 탭 합니다. 

메뉴 항목:
* **레이아웃 화면:** 3D 그리드 시스템 레이아웃을 수행할 수 있는 여러 개체 이며 그룹으로 관리 합니다. 개체를 추가할 레이아웃 화면의 double 어-탭 합니다.
* **기본 형식:** 큐브, 구, 실린더 및 콘을 연구 결집할 사용 합니다.
* **OneDrive:** 개체를 가져오려면 OneDrive 메뉴를 엽니다.
* **도움말:** 도움말 화면을 표시 합니다.

![상황에 맞는 메뉴](images/holosketch-image-07.png)<br>
*상황에 맞는 메뉴*

**도구 벨트 메뉴를 사용 하 여**

이동, 회전, 크기 조정, 저장 및 로드 장면 도구 벨트 메뉴에서 사용할 수 있습니다. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>키보드, 제스처 및 음성 명령을 사용 하 여

![키보드, 제스처 및 음성 명령](images/holosketch-image-08-1000px.png)<br>
*키보드, 제스처 및 음성 명령*

## <a name="download-the-app"></a>앱 다운로드

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">다운로드 하 고 HoloSketch 앱을 무료로 Microsoft Store 설치</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>알려진 문제
* 사용 하 여 자산 번들 만들기는 현재 **Unity 버전 5.4.5f1 합니다.**
* OneDrive의 데이터 양에 따라 앱 OneDrive 콘텐츠를 로드 하는 동안 중지 된 것 처럼 나타날 수 있습니다.
* 현재, 저장 및 로드 기능은 기본 개체 지원
* 메뉴 텍스트, 사운드, 비디오 및 사진 상황에 맞는 메뉴에서 사용할 수 없습니다.
* Play 단추 메뉴의 도구 벨트 조작 gizmo를 지웁니다.

## <a name="sharing-your-sketches"></a>프로그램 스케치를 공유합니다.

HoloLens의 비디오 기록을 기능을 사용 하면 하면 ' Hey Cortana 시작/중지 기록 '. 볼륨 위쪽/아래쪽에 스케치 사진을 찍은 함께 키를 누릅니다.

## <a name="about-the-authors"></a>저자 소개

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>했어요 Yoon Park</b><br>UX 디자이너 @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>개발자 @Microsoft</td>
</tr>
</table> 
