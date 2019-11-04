---
title: 사례 연구-HoloSketch, 공간 레이아웃 및 HoloLens 용 UX 스케치 앱 빌드
description: HoloSketch는 holographic 환경을 빌드하는 데 도움이 되는 장치 상의 공간 레이아웃 및 UX 스케치 도구입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, 스케치, 앱
ms.openlocfilehash: d6d22aae7709bcc1a33b142a100d1a0f9645d3cc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436948"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>사례 연구-HoloSketch, 공간 레이아웃 및 HoloLens 용 UX 스케치 앱 빌드

HoloSketch는 holographic 환경을 빌드하는 데 도움이 되는 장치 상의 공간 레이아웃 및 UX 스케치 도구입니다. HoloSketch는 쌍을 이루는 Bluetooth 키보드 및 마우스 뿐만 아니라 제스처 및 음성 명령에서 작동 합니다. HoloSketch의 목적은 신속한 시각화 및 반복을 위한 간단한 UX 레이아웃 도구를 제공 하는 것입니다.

![HoloSketch: HoloLens 용 공간 레이아웃 및 UX 스케치 앱입니다.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: HoloLens 용 공간 레이아웃 및 UX 스케치 앱*

빠른 시각화 및 반복을 위한 간단한 UX 레이아웃 도구를 ![합니다.](images/holosketch-image-02.png)<br>
*빠른 시각화 및 반복을 위한 간단한 UX 레이아웃 도구입니다.*

## <a name="features"></a>기능

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>빠른 연구 및 규모 프로토타입 작성을 위한 기본 형식

![기본 도형 사용](images/holosketch-primitives-giphy.gif)

빠른 massing 연구 및 확장 프로토타입 작성을 위해 기본 셰이프를 사용 합니다.

### <a name="import-objects-through-onedrive"></a>OneDrive를 통해 개체 가져오기

![개체 가져오기](images/holosketch-importobjects-giphy.gif)

OneDrive를 통해 혼합 된 현실 공간으로 PNG/JPG 이미지 또는 3D FBX 개체 (Unity에서 패키징 필요)를 가져옵니다.

### <a name="manipulate-objects"></a>개체 조작

![개체 조작](images/manipulate-objects-640px.jpg)

익숙한 3D 개체 인터페이스를 사용 하 여 개체 (이동/회전/배율)를 조작 합니다.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, 마우스/키보드, 제스처 및 음성 명령

![Bluetooth 지원](images/supports-bluetooth-640px.jpg)

HoloSketch는 Bluetooth 마우스/키보드, 제스처 및 음성 명령을 지원 합니다.

## <a name="background"></a>백그라운드

### <a name="importance-of-experiencing-your-design-in-the-device"></a>장치에서 디자인이 발생 하는 중요성

HoloLens를 설계할 때 장치에서 디자인을 경험 하는 것이 중요 합니다. 혼합 현실 앱 디자인에서 가장 큰 문제 중 하나는 특히 기존 2D 스케치를 통해 규모, 위치 및 깊이를 이해 하기 어려운 것입니다.

### <a name="cost-of-2d-based-communication"></a>2D 기반 통신 비용

UX 흐름과 시나리오를 다른 사용자에 게 효과적으로 전달 하기 위해 디자이너는 Illustrator, Photoshop 및 PowerPoint와 같은 기존 2D 도구를 사용 하 여 자산을 만드는 데 많은 시간이 소요 될 수 있습니다. 이러한 2D 디자인은 종종 3D로 변환 하는 데 추가 작업이 필요 합니다. 일부 아이디어는 2D에서 3D로의 변환에서 손실 됩니다.

### <a name="complex-deployment-process"></a>복잡 한 배포 프로세스

혼합 현실는 미국에 대 한 새로운 캔버스 이므로 특성에 따라 다양 한 디자인 반복과 평가판 및 오류가 수반 됩니다. Unity 및 Visual Studio와 같은 도구를 잘 모르는 디자이너의 경우 HoloLens에 추가 하는 것은 쉽지 않습니다. 일반적으로 장치에서 2D/3D 아트 워크를 확인 하려면 아래 프로세스를 진행 해야 합니다. 이는 아이디어 및 시나리오를 신속 하 게 반복 하는 디자이너에 게 큰 장벽 이었습니다.

![복잡 한 배포 프로세스](images/holosketch-image-03-1000px.png)<br>
*배포 프로세스*

### <a name="simplified-process-with-holosketch"></a>HoloSketch를 사용한 간소화 된 프로세스

HoloSketch를 사용 하 여 개발 도구 및 장치 포털 페어링을 포함 하지 않고이 프로세스를 간소화 하려고 했습니다. OneDrive를 사용 하 여 사용자는 2D/3D 자산을 HoloLens에 쉽게 배치할 수 있습니다.

HoloSketch](images/holosketch-image-04-1000px.png) ![간소화 된 프로세스<br>
*HoloSketch를 사용한 간소화 된 프로세스*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>3 차원 디자인 고려 및 솔루션을 장려 합니다.

이 도구를 통해 디자이너는 진정한 3 차원 공간에서 솔루션을 탐색 하 고 2D로는 중단 하지 않을 수 있습니다. HoloLens의 경우 배경이 실제 세계 이기 때문에 UI에 대 한 3D 배경을 만드는 방법에 대해 생각해 서는 안 됩니다. HoloSketch은 디자이너에서 HoloLens의 3D 디자인을 쉽게 탐색 하는 방법을 엽니다.

## <a name="get-started"></a>시작하기를

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>2D 이미지 (JPG/PNG)를 HoloSketch로 가져오는 방법

* ' Documents/HoloSketch ' OneDrive 폴더에 JPG/PNG 이미지를 업로드 합니다.
* HoloSketch의 OneDrive 메뉴에서 이미지를 선택 하 고 환경에 저장할 수 있습니다.

2D 이미지를 가져오는 ![](images/import-2d-images-1000px.jpg)<br>
*OneDrive를 통해 이미지 및 3D 개체 가져오기*

### <a name="how-to-import-3d-objects-into-holosketch"></a>HoloSketch에 3D 개체를 가져오는 방법

OneDrive 폴더에 업로드 하기 전에 다음 단계에 따라 3D 개체를 Unity 자산 번들로 패키지 하세요. 이 프로세스를 사용 하 여 Maya, 시네마 4D 및 Microsoft Paint 3D와 같은 3D 소프트웨어에서 FBX/OBJ 파일을 가져올 수 있습니다.

>[!IMPORTANT]
>현재 asset 번들 만들기는 Unity 버전 5.4.5 f1에서 지원 됩니다.

1. Unity 프로젝트 [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)를 다운로드 하 여 엽니다. 이 Unity 프로젝트에는 번들 자산 생성에 대 한 스크립트가 포함 되어 있습니다.
2. 새 GameObject을 만듭니다.
3. 내용에 따라 GameObject의 이름을로 설정 합니다.
4. 검사기 패널에서 ' 구성 요소 추가 '를 클릭 하 고 ' Box Collider '를 추가 합니다. 

   ![검사기 패널에서 ' 구성 요소 추가 '를 클릭 하 고 ' Box Collider '를 추가 합니다.](images/holosketch-10a-assetbundles-1000px.png)
   
   ![검사기 패널에서 ' 구성 요소 추가 '를 클릭 하 고 ' Box Collider '를 추가 #2](images/holosketch-10b-assetbundles-1000px.png)

5. 3D FBX 파일을 프로젝트 패널로 끌어 파일을 가져옵니다.
6. 개체를 **새 GameObject**의 계층 패널로 끕니다.

   ![새 GameObject의 계층 패널로 개체를 끌어 옵니다.](images/holosketch-12-assetbundles-1000px.png)

7. 개체와 일치 하지 않는 경우 collider dimension을 조정 합니다. 개체를 **Z 축**표면으로 회전 합니다.

   ![개체와 일치 하지 않는 경우에는 collider dimension을 조정 합니다.](images/holosketch-13-assetbundles-1000px.png)

8. 계층 패널에서 프로젝트 패널로 개체를 끌어 **prefab**.
9. 검사기 패널의 아래쪽에서 드롭다운을 클릭 하 고 새 고유 이름을 만들고 할당 합니다. 아래 예제에서는 AssetBundle 이름에 대해 ' brownchair '을 추가 하 고 할당 하는 방법을 보여 줍니다. 

   ![검사기 패널의 아래쪽에서 드롭다운을 클릭 하 고 새 고유 이름을 할당 합니다.](images/holosketch-14-assetbundles-1000px.png)

10. 모델 개체에 대 한 미리 보기 이미지를 준비 합니다. 
   이미지를 프로젝트 패널로 끌어와 개체에 사용 되는 이름을 할당 ![합니다.](images/holosketch-15-assetbundles-1000px.png)

11. Unity 프로젝트의 ' Asset ' 폴더 아래에 ' Assetbundles ' 이라는 폴더를 만듭니다.

12. 자산 메뉴에서 ' AssetBundles 빌드 '를 선택 하 여 파일을 생성 합니다. 
   자산 메뉴에서 ![' AssetBundles 빌드 '를 선택 하 여 파일을 생성 합니다.](images/holosketch-15a-assetbundles.png)


13. **생성 된 파일을 OneDrive의/Files/Documents/HoloSketch 폴더에 업로드 합니다.** Asset_unique_name 파일만 업로드 합니다. 매니페스트 파일이 나 AssetBundles 파일을 업로드할 필요가 없습니다. <br>
파일/문서/HoloSketch/폴더 ![](images/holosketch-onedriveupload-1000px.png)
에 파일을 추가 ![HoloSketch의 OneDrive 메뉴에 3D 개체가 추가 된 것을 볼 수](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>개체를 조작 하는 방법

HoloSketch는 3D 소프트웨어에서 널리 사용 되는 기존 인터페이스를 지원 합니다. 제스처와 마우스를 사용 하 여 개체를 이동, 회전, 크기를 조정할 수 있습니다. 음성 또는 키보드를 사용 하 여 여러 모드 간을 빠르게 전환할 수 있습니다.

### <a name="object-manipulation-modes"></a>개체 조작 모드

개체를 조작 하는 방법 ![](images/holosketch-image-06-1000px.png)<br>
*개체를 조작 하는 방법*

### <a name="contextual-and-tool-belt-menus"></a>상황별 및 도구 벨트 메뉴

**상황에 맞는 메뉴 사용**

두 번 탭 하 여 상황에 맞는 메뉴를 엽니다. 

메뉴 항목:
* **레이아웃 화면:** 이는 여러 개체를 레이아웃 하 고 그룹으로 관리할 수 있는 3D 그리드 시스템입니다. 레이아웃 화면에서 두 번 탭 하 여 개체를 추가 합니다.
* **기본 형식:** Massing 연구에는 큐브, 구, 실린더 및 원추를 사용 합니다.
* **OneDrive:** OneDrive 메뉴를 열어 개체를 가져옵니다.
* **도움말:** 도움말 화면을 표시 합니다.

상황에 맞는 메뉴를 ![](images/holosketch-image-07.png)<br>
*상황에 맞는 메뉴*

**도구 벨트 메뉴 사용**

이동, 회전, 크기 조정, 저장 및 로드 장면을 도구 벨트 메뉴에서 사용할 수 있습니다. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>키보드, 제스처 및 음성 명령 사용

키보드, 제스처 및 음성 명령 ![](images/holosketch-image-08-1000px.png)<br>
*키보드, 제스처 및 음성 명령*

## <a name="download-the-app"></a>앱 다운로드

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Microsoft Store
에서 무료로 HoloSketch 앱을 다운로드 하 여 설치</a> 합니다.</td>
</tr>
</table>

## <a name="known-issues"></a>알려진 문제
* 현재 자산 번들 만들기는 **Unity 버전 5.4.5 f1** 에서 지원 됩니다.
* OneDrive의 데이터 양에 따라 OneDrive 콘텐츠를 로드 하는 동안 앱이 중지 된 것 처럼 보일 수 있습니다.
* 현재 저장 및 로드 기능은 기본 개체만 지원 합니다.
* 상황에 맞는 메뉴에서 텍스트, 소리, 비디오 및 사진 메뉴를 사용할 수 없습니다.
* 도구 벨트 메뉴의 재생 단추를 클릭 하면 조작 gizmo 그리려면 지워집니다.

## <a name="sharing-your-sketches"></a>스케치 공유

' 안녕하세요 Cortana, 녹화 시작/중지 ' 라고 말하여 HoloLens의 비디오 녹화 기능을 사용할 수 있습니다. 볼륨 위쪽/아래쪽 키를 함께 사용 하 여 스케치를 그림으로 만듭니다.

## <a name="about-the-authors"></a>작성자 정보

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>동 Yoon 공원</b><br>UX 디자이너 @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>개발자 @Microsoft</td>
</tr>
</table> 
