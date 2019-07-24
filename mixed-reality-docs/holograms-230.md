---
title: MR 공간 230-공간 매핑
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 공간 매핑 개념에 대 한 자세한 내용을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 공간 매핑, 표면 재구성, 메시
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993557"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR 공간 230: 공간 매핑

[공간 매핑은](spatial-mapping.md) 환경에 대 한 holograms을 교육 하 여 실제 세계와 가상 세계를 함께 결합 합니다. MR 공간 230 (Project Planetarium)에서 다음을 수행 하는 방법을 알아봅니다.

* 환경을 검색 하 고 HoloLens에서 개발 컴퓨터로 데이터를 전송 합니다.
* 셰이더를 탐색 하 고 공간을 시각화 하는 데 사용 하는 방법을 알아보세요.
* 메시 처리를 사용 하 여 대화방 메시를 간단한 평면으로 나눕니다.
* [MR 기본 사항 101](holograms-101.md)에서 배운 배치 기술 외에도, 환경에서 홀로그램을 배치할 수 있는 위치에 대 한 피드백을 제공 하세요.
* 폐색 효과를 탐색 하 여 홀로그램이 실제 개체 뒤에 있을 때 x-레이 비전을 사용 하 여 볼 수 있습니다.

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 공간 230: 공간 매핑</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.
* 몇 가지 C# 기본적인 프로그래밍 기능.
* [MR 기본 101](holograms-101.md)를 완료 해야 합니다.
* [개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
  * Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)를 사용 하세요.
  * Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)를 사용 하세요.
  * Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)를 사용 하세요.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)있습니다.

### <a name="notes"></a>참고

* Visual Studio의 "내 코드만 사용"은 코드에서 중단점을 적중 하기 위해 디버깅 > 도구 > 옵션에서 비활성화 (*선택 취소*) 해야 합니다.

## <a name="unity-setup"></a>Unity 설치

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* **Unity**를 시작 합니다.
* 새로 만들기 **를 선택 하** 여 새 프로젝트를 만듭니다.
* 프로젝트 이름을 **Planetarium**로 합니다.
* **3d** 설정이 선택 되어 있는지 확인 합니다.
* **Create Project**를 클릭합니다.
* Unity가 시작 되 면 **편집 > 프로젝트 설정 > 플레이어**로 이동 합니다.
* **검사기** 패널에서 녹색 **Windows 스토어** 아이콘을 찾아 선택 합니다.
* **기타 설정**을 확장 합니다.
* **렌더링** 섹션에서 **가상 현실 지원** 옵션을 선택 합니다.
* **Windows Holographic** 가 **가상 현실 sdk**목록에 나타나는지 확인 합니다. 그렇지 않은 경우 목록 아래쪽 **+** 의 단추를 선택 하 고 **Windows Holographic**를 선택 합니다.
* **게시 설정**을 확장 합니다.
* **기능** 섹션에서 다음 설정을 확인 합니다.
    * InternetClientServer
    * PrivateNetworkClientServer
    * 마이크
    * SpatialPerception
* **편집 > 프로젝트 설정 > 품질** 로 이동 합니다.
* **검사기** 패널의 Windows 스토어 아이콘에서 ' default ' 행 아래의 검은색 드롭다운 화살표를 선택 하 고 기본 설정을 **매우 낮음**으로 변경 합니다.
* **자산 > 가져오기 패키지 > 사용자 지정 패키지**로 이동 합니다.
* **. ..\Holographicacademy-holograms-230-SpatialMapping\Starting** 폴더로 이동 합니다.
* **Planetarium. unitypackage**를 클릭 합니다.
* **열기**를 클릭합니다.
* **Unity 패키지 가져오기** 창이 표시 되 면 **가져오기** 단추를 클릭 합니다.
* Unity가이 프로젝트를 완료 하는 데 필요한 모든 자산을 가져올 때까지 기다립니다.
* **계층** 패널에서 **주 카메라**를 삭제 합니다.
* **프로젝트** 패널의 **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** 폴더에서 **주 카메라** 개체를 찾습니다.
* **주 카메라** Prefab을 **계층** 패널로 끌어다 놓습니다.
* **계층** 패널에서 **방향 광원** 개체를 삭제 합니다.
* **프로젝트** 패널의 **Holograms** 폴더에서 **Cursor** 개체를 찾습니다.
* **커서** Prefab을 **계층**으로 끌어 & 놓습니다.
* **계층** 패널에서 **Cursor** 개체를 선택 합니다.
* **검사기** 패널에서 **계층** 드롭다운을 클릭 하 고 **계층 편집 ...** 을 선택 합니다.
* **사용자 계층 31** 의 이름을 "**SpatialMapping**"로 합니다.
* 새 장면 저장: **파일 > 다른 이름으로 장면 저장 ...**
* **새 폴더** 를 클릭 하 고 폴더 이름을 **장면**으로 합니다.
* 파일 이름을 "**Planetarium**"로 하 고 해당 파일을 **백그라운드** 폴더에 저장 합니다.

## <a name="chapter-1---scanning"></a>1 장-검색

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**목표로**
* SurfaceObserver 및 해당 설정이 경험 및 성능에 미치는 영향에 대해 알아봅니다.
* 회의실의 메시를 수집 하는 방 스캔 환경을 만듭니다.

**지침**
* **프로젝트** 패널 **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** 폴더에서 **SpatialMapping** prefab를 찾습니다.
* **SpatialMapping** Prefab를 **계층** 패널로 끌어 & 놓습니다.

**빌드 및 배포 (1 부)**
* Unity에서 **파일 > 빌드 설정**을 선택 합니다.
* 열려 있는 장면 **추가** 를 클릭 하 여 **Planetarium** 장면을 빌드에 추가 합니다.
* **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.
* **SDK** 를 **Universal 10** 및 **UWP 빌드 형식** 으로 **D3D**로 설정 합니다.
* **Unity C# 프로젝트**를 확인 합니다.
* **빌드**를 클릭합니다.
* "App" 이라는 **새 폴더** 를 만듭니다.
* 단일 **앱** 폴더를 클릭 합니다.
* **폴더 선택** 단추를 누릅니다.
* Unity 작성이 완료 되 면 파일 탐색기 창이 표시 됩니다.
* **앱** 폴더를 두 번 클릭 하 여 엽니다.
* **Planetarium** 을 두 번 클릭 하 여 Visual Studio에서 프로젝트를 로드 합니다.
* Visual Studio에서 맨 위 도구 모음을 사용 하 여 구성을 **릴리스**로 변경 합니다.
* 플랫폼을 **x 86**으로 변경 합니다.
* ' 로컬 컴퓨터 ' 오른쪽에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터**를 선택 합니다.
* 주소 필드에 [장치의 IP 주소](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 변경 합니다.
* **디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.
* Visual Studio에서 빌드 및 배포 상태에 대 한 **출력** 패널을 시청 합니다.
* 앱이 배포 된 후에는 공간을 탐색 합니다. 검은색 및 흰색 와이어 프레임 메시를 포함 하는 주변 서피스가 표시 됩니다.
* 주변을 검색 합니다. 벽, 최대값이 및 층을 확인 해야 합니다.

**빌드 및 배포 (2 부)**

이제 공간 매핑이 성능에 영향을 줄 수 있는 방법을 살펴보겠습니다.
* Unity에서 **Window > Profiler**를 선택 합니다.
* **> GPU 추가 Profiler**를 클릭 합니다.
* **활성 프로파일러 > <Enter IP>** 를 클릭 합니다.
* HoloLens의 **IP 주소** 를 입력 합니다.
* **연결**을 클릭합니다.
* GPU에서 프레임을 렌더링 하는 데 걸리는 시간 (밀리초)을 관찰 합니다.
* 장치에서 응용 프로그램이 실행 되는 것을 중지 합니다.
* Visual Studio로 돌아가서 **SpatialMappingObserver.cs**을 엽니다. 이 파일은 어셈블리-CSharp (유니버설 Windows) 프로젝트의 HoloToolkit\SpatialMapping 폴더에서 찾을 수 있습니다.
* **활성 ()** 함수를 찾고 다음 코드 줄을 추가 합니다. **TrianglesPerCubicMeter = 1200;**
* 장치에 프로젝트를 다시 배포 하 고 **프로파일러를 다시 연결**합니다. 프레임을 렌더링 하는 시간 (밀리초)의 변경 내용을 관찰 합니다.
* 장치에서 응용 프로그램이 실행 되는 것을 중지 합니다.

**Unity에서 저장 및 로드**

마지막으로 대화방 메시를 저장 하 고 Unity에 로드 하겠습니다.
* Visual Studio로 돌아가서 이전 섹션에서 **TrianglesPerCubicMeter** **()** 함수에 추가한 줄을 제거 합니다.
* 장치에 프로젝트를 다시 배포 합니다. 이제 입방 미터 당 **500** 삼각형으로 실행 해야 합니다.
* 브라우저를 열고 HoloLens IPAddress를 입력 하 여 **Windows 장치 포털로**이동 합니다.
* 왼쪽 패널에서 **3D 보기** 옵션을 선택 합니다.
* **표면 재구성** 아래에서 **업데이트** 단추를 선택 합니다.
* HoloLens에서 스캔 한 영역이 표시 창에 표시 되는지 확인 합니다.
* 회의실 검색을 저장 하려면 **저장** 단추를 누릅니다.
* **다운로드** 폴더를 열어서 저장 된 **대화방 모델을**찾습니다.
* **Srmesh. .obj** 를 Unity 프로젝트의 **자산** 폴더에 복사 합니다.
* Unity의 **계층** 패널에서 **SpatialMapping** 개체를 선택 합니다.
* **개체 표면 관찰자 (스크립트)** 구성 요소를 찾습니다.
* **방 모델** 속성의 오른쪽에 있는 원을 클릭 합니다.
* **Srmesh** 개체를 찾아 선택한 다음 창을 닫습니다.
* 이제 **검사기** 패널의 **Room 모델** 속성이 **srmesh**로 설정 되었는지 확인 합니다.
* **재생** 단추를 눌러 Unity의 미리 보기 모드를 입력 합니다.
* SpatialMapping 구성 요소는 저장 된 대화방 모델에서 메시를 로드 하므로 Unity에서 사용할 수 있습니다.
* **장면** 보기로 전환 하 여 와이어 프레임 셰이더에 표시 되는 모든 대화방 모델을 확인 합니다.
* **재생** 단추를 다시 클릭 하 여 미리 보기 모드를 종료 합니다.

**참고:** 다음 번에 Unity에서 미리 보기 모드를 입력 하면 기본적으로 저장 된 대화방 메쉬가 로드 됩니다.

## <a name="chapter-2---visualization"></a>2 장-시각화

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**목표로**
* 셰이더의 기본 사항에 대해 알아봅니다.
* 주변을 시각화 합니다.

**지침**
* Unity의 **계층 구조** 패널에서 **SpatialMapping** 개체를 선택 합니다.
* **검사기** 패널에서 **공간 매핑 관리자 (스크립트)** 구성 요소를 찾습니다.
* **표면 재질** 속성의 오른쪽에 있는 원을 클릭 합니다.
* **BlueLinesOnWalls** 재질을 찾아 선택 하 고 창을 닫습니다.
* **프로젝트** 패널 **셰이더** 폴더에서 **BlueLinesOnWalls** 를 두 번 클릭 하 여 Visual Studio에서 셰이더를 엽니다.
* 다음 작업을 수행 하는 간단한 픽셀 (꼭 짓 점-조각) 셰이더입니다.
    1. 꼭 짓 점 위치를 세계 공간으로 변환 합니다.
    2. 꼭 짓 점의 법선을 확인 하 여 픽셀이 세로 인지 확인 합니다.
    3. 렌더링할 픽셀의 색을 설정 합니다.

**빌드 및 배포**
* Unity로 돌아가서 **재생** 을 눌러 미리 보기 모드를 시작 합니다.
* 저장 된 검색 데이터에서 자동으로 로드 되는 실내 메시의 모든 세로 화면에서 파란색 선이 렌더링 됩니다.
* **장면** 탭으로 전환 하 여 대화방 보기를 조정 하 고 전체 대화방 메쉬가 Unity에 표시 되는 방식을 확인 합니다.
* **프로젝트** 패널에서 **재질** 폴더를 찾고 **BlueLinesOnWalls** 재질을 선택 합니다.
* 일부 속성을 수정 하 고 Unity 편집기에서 변경 내용이 표시 되는 방식을 확인 합니다.
    * **검사기** 패널에서 **LineScale** 값을 조정 하 여 선이 더 두껍게 표시 되도록 합니다.
    * **검사기** 패널에서 선 **per측정기** 값을 조정 하 여 각 벽에 표시 되는 줄 수를 변경 합니다.
* **재생** 을 다시 클릭 하 여 미리 보기 모드를 종료 합니다.
* HoloLens에 빌드 및 배포 하 고 실제 표면에 셰이더 렌더링이 어떻게 나타나는지 관찰 합니다.

Unity는 자료를 미리 보는 많은 작업을 수행 하지만 항상 장치에서 렌더링을 체크 아웃 하는 것이 좋습니다.

## <a name="chapter-3---processing"></a>3 장-처리

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**목표로**
* 응용 프로그램에서 사용할 공간 매핑 데이터를 처리 하는 방법을 알아봅니다.
* 공간 매핑 데이터를 분석 하 여 평면을 찾고 삼각형을 제거 합니다.
* 홀로그램 배치에 평면을 사용 합니다.

**지침**
* Unity의 **Project** panel **Holograms** 폴더에서 **SpatialProcessing** 개체를 찾습니다.
* **SpatialProcessing** 개체를 **계층** 패널로 끌어 & 놓습니다.

SpatialProcessing prefab에는 공간 매핑 데이터를 처리 하기 위한 구성 요소가 포함 되어 있습니다. **SurfaceMeshesToPlanes.cs** 는 공간 매핑 데이터를 기반으로 평면을 찾아서 생성 합니다. 우리는 응용 프로그램에서 비행기를 사용 하 여 벽, 층 및 최대값이을 나타냅니다. 이 prefab에는 공간 매핑 메시에서 꼭 짓 점을 제거할 수 있는 **RemoveSurfaceVertices.cs** 도 포함 됩니다. 이를 사용 하 여 메시에 구멍을 만들거나 더 이상 필요 하지 않은 불필요 한 삼각형 (평면을 대신 사용할 수 있음)을 제거할 수 있습니다.
* Unity의 **Project** panel **Holograms** 폴더에서 **SpaceCollection** 개체를 찾습니다.
* **SpaceCollection** 개체를 **계층** 패널로 끌어 놓습니다.
* **계층** 패널에서 **SpatialProcessing** 개체를 선택 합니다.
* **검사기** 패널에서 **재생 공간 관리자 (스크립트)** 구성 요소를 찾습니다.
* **PlaySpaceManager.cs** 를 두 번 클릭 하 여 Visual Studio에서 엽니다.

PlaySpaceManager.cs는 응용 프로그램 관련 코드를 포함 합니다. 이 스크립트에 기능을 추가 하 여 다음 동작을 사용 하도록 설정 합니다.
1. 검색 시간 제한 (10 초)을 초과 하 고 나면 공간 매핑 데이터 수집을 중지 합니다.
2. 공간 매핑 데이터를 처리 합니다.
    1. SurfaceMeshesToPlanes를 사용 하 여 평면 (벽, 층, 최대값이 등)을 보다 간단 하 게 표현할 수 있습니다.
    2. 평면 경계 내에 있는 표면 삼각형을 제거 하려면 RemoveSurfaceVertices를 사용 합니다.
3. 전 세계에서 holograms의 컬렉션을 생성 하 고 사용자 가까이에 벽 및 바닥 평면을 배치할 수 있습니다.

PlaySpaceManager.cs에 표시 된 코딩 연습을 완료 하거나 아래에서 완성 된 솔루션으로 스크립트를 바꿉니다.

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**빌드 및 배포**
* HoloLens에 배포 하기 전에 Unity의 **재생** 단추를 눌러 재생 모드로 전환 합니다.
* 파일에서 대화방 메시를 로드 한 후에는 공간 매핑 메시에서 처리가 시작 될 때까지 10 초 정도 기다립니다.
* 처리가 완료 되 면 비행기가 바닥, 벽, 천장 등을 나타내는 것 처럼 보입니다.
* 모든 비행기를 찾은 후에는 카메라 근처의 바닥에 표를 표시 하는 것을 볼 수 있습니다.
* 두 포스터는 카메라 근처의 벽에도 표시 됩니다. **게임** 모드에서 볼 수 없는 경우 **장면** 탭으로 전환 합니다.
* 재생 모드를 종료 하려면 **재생** 단추를 다시 누릅니다.
* 평소 처럼를 빌드하고 HoloLens에 배포 합니다.
* 공간 매핑 데이터의 검색 및 처리가 완료 될 때까지 기다립니다.
* 비행기가 표시 되 면 세계에서 태양계와 포스터를 찾으려고 시도 합니다.

## <a name="chapter-4---placement"></a>4 장-배치

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**목표로**
* 홀로그램이 표면에 맞는지 확인 합니다.
* 홀로그램을 화면에 맞출 수 없는 경우 사용자에 게 피드백을 제공 합니다.

**지침**
* Unity의 **계층 구조** 패널에서 **SpatialProcessing** 개체를 선택 합니다.
* **검사기** 패널에서 **평면 (스크립트) 구성 요소에 대 한 표면 메시** 를 찾습니다.
* **그리기 평면** 속성을 **없음** 으로 변경 하 여 선택을 취소 합니다.
* 벽 평면만 렌더링 되도록 **평면 그리기** 속성을 **벽**으로 변경 합니다.
* **프로젝트** 패널의 **Scripts** 폴더에서 **Placeable.cs** 를 두 번 클릭 하 여 Visual Studio에서 엽니다.

**동적 배치** 가능 스크립트는 평면 찾기가 완료 된 후 생성 된 포스터 및 프로젝션 상자에 이미 연결 되어 있습니다. 코드의 주석 처리를 제거 하기만 하면 됩니다 .이 스크립트는 다음을 수행 합니다.
1. 홀로그램의 중심에서 raycasting로 화면에 맞출 수 있는지 여부와 경계 큐브의 4 개 모퉁이를 확인 합니다.
2. 표면 법선을 확인 하 여 홀로그램을 가만히 놓을 수 있을 만큼 부드러운 지 확인 합니다.
3. 홀로그램 주위에 경계 큐브를 렌더링 하 여 배치 하는 동안 실제 크기를 표시 합니다.
4. 홀로그램 아래/뒤에 그림자를 캐스팅 하 여 바닥/벽에 배치 될 위치를 표시 합니다.
5. 홀로그램을 표면에 배치할 수 없는 경우 그림자를 빨간색으로 렌더링 하 고 가능 하면 녹색으로 렌더링 합니다.
6. 선호도가 있는 표면 유형 (수직 또는 수평)에 맞춰 홀로그램의 방향을 다시 조정 합니다.
7. 이동 또는 맞춤 동작을 방지 하기 위해 홀로그램을 선택한 화면에 원활 하 게 놓습니다.

아래 코딩 연습에서 모든 코드의 주석 처리를 제거 하거나 **Placeable.cs**에서이 완성 된 솔루션을 사용 합니다.

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**빌드 및 배포**
* 이전과 마찬가지로 프로젝트를 빌드하고 HoloLens에 배포 합니다.
* 공간 매핑 데이터의 검색 및 처리가 완료 될 때까지 기다립니다.
* 태양계가 표시 되 면 아래 투영 상자를 응시 하 고 선택 제스처를 수행 하 여 이동 합니다. 투영 상자를 선택 하는 동안에는 경계 큐브가 투영 상자 주위에 표시 됩니다.
* 머리를 이동 하 여 대화방의 다른 위치를 응시 합니다. 투영 상자는 응시 다음에와 야 합니다. 투영 상자 아래 그림자가 빨간색으로 바뀌고 해당 화면에 홀로그램을 놓을 수 없습니다. 투영 상자 아래의 그림자가 녹색으로 바뀌고 다른 선택 제스처를 수행 하 여 홀로그램을 놓을 수 있습니다.
* 벽에서 holographic 포스터 중 하나를 찾아 선택 하 여 새 위치로 이동 합니다. 바닥 또는 천장에 포스터를 배치할 수 없으며, 이동할 때 각 벽에 대해 올바르게 방향이 유지 됩니다.

## <a name="chapter-5---occlusion"></a>5 장-폐색

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**목표로**
* 홀로그램을 공간 매핑 메시로 폐색 여부를 확인 합니다.
* 흥미로운 효과를 얻기 위해 다른 폐색 기술을 적용 합니다.

**지침**

먼저 공간 매핑 메시가 실제 세계를 occluding 하지 않고 다른 holograms을 려 수 있도록 합니다.
* **계층** 패널에서 **SpatialProcessing** 개체를 선택 합니다.
* **검사기** 패널에서 **재생 공간 관리자 (스크립트)** 구성 요소를 찾습니다.
* **보조 재질** 속성의 오른쪽에 있는 원을 클릭 합니다.
* **폐색** 재질을 찾아 선택 하 고 창을 닫습니다.

다음으로 지구에 특별 한 동작을 추가 하 여 다른 홀로그램 (예: sun)에 의해 폐색 될 때마다 파란색 강조 표시를 하거나 공간 매핑 메시로 이동 합니다.
* **프로젝트** 패널의 **Holograms** 폴더에서 **SolarSystem** 개체를 확장 합니다.
* **지구**를 클릭 합니다.
* **검사기** 패널에서 지구 재질 (최하위 구성 요소)을 찾습니다.
* **셰이더 드롭다운에서**셰이더를 **사용자 지정 > OcclusionRim**로 변경 합니다. 그러면 다른 개체에 의해 폐색 될 때마다 지구 주위에 파란색 강조 표시가 렌더링 됩니다.

마지막으로, 태양계에서 행성에 대해 x-레이 비전 효과를 사용 하도록 설정 하겠습니다. 다음을 수행 하려면 **PlanetOcclusion.cs** (Scripts\SolarSystem 폴더에 있음)를 편집 해야 합니다.
1. SpatialMapping 계층 (방 메시 및 평면)에서 행성을 폐색 여부를 확인 합니다.
2. SpatialMapping 계층에 의해 폐색 될 때마다 전 세계의 와이어 프레임 표현을 표시 합니다.
3. SpatialMapping 계층에 의해 차단 되지 않는 행성의 와이어 프레임 표현을 숨깁니다.

PlanetOcclusion.cs의 코딩 연습을 수행 하거나 다음 솔루션을 사용 합니다.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**빌드 및 배포**
* 평소 처럼 응용 프로그램을 빌드하고 HoloLens에 배포 합니다.
* 공간 매핑 데이터의 스캔 및 처리가 완료 될 때까지 기다립니다 (벽에 파란색 선이 표시 되어야 함).
* 태양계의 투영 상자를 찾아 선택한 다음 벽 옆 또는 카운터 뒤에 있는 상자를 설정 합니다.
* 포스터 또는 프로젝션 상자에서 피어에 화면을 숨겨서 기본 폐색를 볼 수 있습니다.
* 지구를 찾아 다른 홀로그램 또는 표면 뒤에 있을 때마다 파란색 강조 표시 효과가 있어야 합니다.
* 벽 또는 방의 다른 표면 뒤에서 행성 이동을 시청 합니다. 이제 x 광선의 비전을 통해 와이어 프레임 구조를 볼 수 있습니다.

## <a name="the-end"></a>끝

축하합니다. 이제 MR 공간 230 **을 완료 했습니다. 공간 매핑입니다**.
* 환경을 검색 하 고 공간 매핑 데이터를 Unity로 로드 하는 방법을 알고 있습니다.
* 셰이더의 기본 사항과 자료를 사용 하 여 전 세계를 다시 시각화 하는 방법을 이해 하 고 있습니다.
* 평면을 찾고 메시에서 삼각형을 제거 하는 새로운 처리 기법을 배웠습니다.
* Holograms를 이동 하 고 적합 한 표면에 놓을 수 있었습니다.
* 다양 한 폐색 기술이 경험 했으며 x 광선의 기능을 asha.
