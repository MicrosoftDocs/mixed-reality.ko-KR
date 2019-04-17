---
title: MR 공간 230-공간 매핑
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 공간 매핑 개념의 자세한 연습을 코딩이 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, academy, 자습서, 공간 매핑, 화면 재구성, 메시
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600925"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR 공간 230: 공간 매핑

[공간 매핑](spatial-mapping.md) 홀로그램 환경에 대 한 강의 하 여 실제 및 가상 세계를 함께 결합 합니다. MR 공간 230 (프로젝트 Planetarium)에서는 것에 대해 설명 하는 방법.

* 개발 컴퓨터에는 HoloLens에서 환경 및 전송 데이터를 검색 합니다.
* 셰이더를 탐색 하 고, 공간 시각화에 사용 하는 방법을 알아봅니다.
* 대화방 메시 메시 처리를 사용 하 여 간단한 평면으로 분해 합니다.
* 학습 한 배치 기술 만으로는 [MR 기본 사항 101](holograms-101.md)를 홀로그램 환경에 배치할 수 있는지에 대 한 피드백을 제공 합니다.
* 폐색 효과 탐색 실제 개체 뒤에 홀로그램 때 볼 수 있도록 계속이 레이 투시 능력이 사용 하 여!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 공간 230: 공간 매핑</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.
* 기본적인 C# 기능을 프로그래밍 합니다.
* 완료 해야 [MR 기본 사항 101](holograms-101.md)합니다.
* HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.

### <a name="project-files"></a>프로젝트 파일

* 다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) 프로젝트에서 필요 합니다. Unity 2017.2 이상이 필요합니다.
  * Unity 5.6 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)합니다.
  * Unity 5.5 지원 해야 하는 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)합니다.
  * Unity 5.4 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)합니다.
* 취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.

>[!NOTE]
>을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)합니다.

### <a name="notes"></a>참고

* "사용할 수 없게 해야 하는 Visual Studio에서에서" 내 코드만 사용 (*unchecked*) 도구 > 옵션 > 디버깅 코드에서 중단점을 적중 하려면.

## <a name="unity-setup"></a>Unity 설치

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* 시작 **Unity**합니다.
* 선택 **새로 만들기** 새 프로젝트를 만듭니다.
* 프로젝트 이름을 **Planetarium**합니다.
* 있는지 확인 합니다 **3D** 설정을 선택 합니다.
* 클릭 **프로젝트를 만들**합니다.
* Unity이 시작 되 면 이동할 **편집 > 프로젝트 설정 > 플레이어**합니다.
* 에 **검사기** 패널을 찾고 선택 녹색 **Windows 스토어** 아이콘입니다.
* 확장 **기타 설정을**합니다.
* 에 **렌더링** 섹션을 확인 합니다 **가상 현실 지원** 옵션입니다.
* 확인 **Windows Holographic** 목록에 표시 됩니다 **가상 현실 Sdk**합니다. 그렇지 않은 경우 선택 합니다 **+** 목록의 맨 아래에 있는 단추를 선택 **Windows Holographic**합니다.
* 확장 **게시 설정**합니다.
* 에 **기능** 섹션에서 다음 설정을 확인 합니다.
    * InternetClientServer
    * PrivateNetworkClientServer
    * 마이크
    * SpatialPerception
* 로 **편집 > 프로젝트 설정 > 품질**
* 에 **검사기** Windows 스토어 아이콘 선택에서 '기본' 행 아래에 있는 검은색 드롭다운 화살표를 클릭 한 기본 설정을 변경 **가장 빠름**합니다.
* 로 이동 **자산 > 패키지 가져오기 > 사용자 지정 패키지**합니다.
* 로 이동 합니다 **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** 폴더입니다.
* 클릭할 **Planetarium.unitypackage**합니다.
* **열기**를 클릭합니다.
* **Unity 패키지 가져오기** 창이 표시 됩니다를 클릭 합니다 **가져오기** 단추.
* 이 프로젝트를 완료 해야 하는 자산을 모두 가져오려면 Unity 될 때까지 기다립니다.
* 에 **계층 구조** 패널에서 삭제 합니다 **주 카메라**합니다.
* 에 **프로젝트** 패널 **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** 폴더를 찾기는 **주 카메라** 개체입니다.
* 끌어서 놓기는 **주 카메라** 으로 prefab 합니다 **계층** 패널입니다.
* 에 **계층** 패널에서 삭제 합니다 **Directional Light** 개체입니다.
* 에 **프로젝트** 패널 **홀로그램** 폴더를 찾습니다는 **커서** 개체입니다.
* 끌어서 놓기 합니다 **커서** 으로 prefab 합니다 **계층**합니다.
* 에 **계층** 패널을 선택 합니다 **커서** 개체.
* 에 **검사기** 패널을 클릭 합니다 **계층** 드롭다운을 선택 **계층 편집...** .
* 이름을 **사용자 계층 31** 으로 "**SpatialMapping**"입니다.
* 새 장면을 저장 합니다. **파일 >으로 장면 저장...**
* 클릭 **새 폴더** 는 폴더의 이름을 **장면**합니다.
* 파일 이름을 "**Planetarium**"에 저장 된 **장면** 폴더입니다.

## <a name="chapter-1---scanning"></a>1 장-검색

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Objectives**
* SurfaceObserver 및 설정을 미치는 경험 하는 방법 및 성능에 알아봅니다.
* 사용자 공간 메시를 수집 하는 환경을 검색 공간을 만듭니다.

**지침**
* 에 **프로젝트** 패널 **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** 폴더를 찾을 합니다 **SpatialMapping** prefab 합니다.
* 끌어서 놓기 합니다 **SpatialMapping** 으로 prefab 합니다 **계층** 패널입니다.

**빌드 및 배포 (1 부)**
* Unity에서 선택 **파일 > 빌드 설정**합니다.
* 클릭 **열려 장면 추가** 추가할 합니다 **Planetarium** 빌드 장면입니다.
* 선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 클릭 **플랫폼 전환**합니다.
* 설정 **SDK** 하 **유니버설 10** 하 고 **UWP 빌드 형식** 에 **D3D**합니다.
* 확인할 **Unity C# 프로젝트**합니다.
* **빌드**를 클릭합니다.
* 만들기는 **새 폴더** 이름을 "App"입니다.
* 한 번 클릭 합니다 **앱** 폴더입니다.
* 키를 눌러 합니다 **폴더 선택** 단추입니다.
* Unity 완료 되 면 빌드 파일 탐색기 창이 표시 됩니다.
* 두 번 클릭 합니다 **앱** 폴더를 엽니다.
* 두 번 클릭 **Planetarium.sln** Visual Studio에서 프로젝트를 로드 합니다.
* Visual Studio에서 최상위 도구 모음을 사용 하도록 구성을 변경 하려면 **릴리스**합니다.
* 플랫폼을 변경 **x86**합니다.
* ' Localmachine ' 오른쪽에 드롭다운 화살표를 클릭 하 고 선택 **원격 컴퓨터**합니다.
* 입력 [장치의 IP 주소](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) 주소 필드 및 인증 모드를 변경할 **유니버설 (암호화 되지 않은 프로토콜)** 합니다.
* 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.
* 조사식 합니다 **출력** 빌드에 대 한 Visual Studio에서 패널 및 상태를 배포 합니다.
* 앱에 배포한 전시실 방법을 설명 합니다. 흑백 와이어 프레임 메시를 다루지 주변 화면을 볼 수 있습니다.
* 환경을 검색 합니다. 벽, 최대값이, 바닥 확인 해야 합니다.

**빌드 및 배포 (2 부)**

이제 어떻게 공간 매핑 수 성능에 영향을 살펴보겠습니다.
* Unity에서 선택 **창 > Profiler**합니다.
* 클릭 **Profiler 추가 > GPU**합니다.
* 클릭 **활성 Profiler > <Enter IP>** 합니다.
* 입력 된 **IP 주소** 여 HoloLens의 합니다.
* **연결**을 클릭합니다.
* GPU에서 프레임을 렌더링 하는 데 걸리는 시간 (밀리초)의 수를 확인 합니다.
* 장치에서 실행에서 응용 프로그램을 중지 합니다.
* Visual Studio로 돌아가서 연 **SpatialMappingObserver.cs**합니다. 어셈블리-CSharp (유니버설 Windows) 프로젝트의 HoloToolkit\SpatialMapping 폴더에서 찾을 있습니다.
* 찾을 합니다 **Awake()** 함수 및 코드의 다음 줄을 추가 합니다. **TrianglesPerCubicMeter = 1200;**
* 장치 프로젝트를 다시 배포 차례로 **프로파일러를 다시 연결**합니다. 프레임을 렌더링 하는 밀리초 수의 변경 내용을 확인 합니다.
* 장치에서 실행에서 응용 프로그램을 중지 합니다.

**저장 하 고 Unity에서 로드**

마지막으로, 보겠습니다 저장이 대화방 메시 하 고 Unity로 로드 합니다.
* Visual Studio로 돌아가서 및 제거는 **TrianglesPerCubicMeter** 에서 추가한 줄 합니다 **Awake()** 함수에서 이전 섹션 중입니다.
* 장치에 프로젝트를 다시 배포 합니다. 에서는 이제 실행 해야 **500** 평방 미터당 삼각형입니다.
* 브라우저를 열고로 이동 하 여 HoloLens IPAddress에를 입력 합니다 **Windows Device Portal**합니다.
* 선택 된 **3D 뷰** 왼쪽된 패널의 옵션입니다.
* 아래 **재구성 노출** 선택 합니다 **업데이트** 단추입니다.
* 표시 창에 표시 하 여 HoloLens에서 검색 한 영역을 시청 하세요.
* 키를 눌러에 공간 검색을 저장 하는 **저장** 단추.
* 오픈 프로그램 **다운로드** 저장된 공간이 모델을 찾을 폴더 **SRMesh.obj**합니다.
* 복사본 **SRMesh.obj** 에 **자산** Unity 프로젝트의 폴더입니다.
* Unity에서 선택 합니다 **SpatialMapping** 개체를 **계층** 패널입니다.
* 찾을 합니다 **개체 화면 관찰자 (스크립트)** 구성 요소입니다.
* 오른쪽에 원을 클릭 합니다 **방 모델** 속성입니다.
* 찾기 및 선택 합니다 **SRMesh** 개체 및 다음 창을 닫습니다.
* 되어 있는지 확인 합니다 **방 모델** 속성에는 **검사기** 패널으로 설정 되었습니다 **SRMesh**.
* 키를 눌러 합니다 **재생** 단추 Unity의 미리 보기 모드로 전환 합니다.
* Unity에서 사용할 수 있도록 SpatialMapping 구성 요소 저장된 공간이 모델에서는 메시를 로드 합니다.
* 전환할 **장면** 와이어 프레임 셰이더와 표시 공간 모델의 모든 표시 되도록 보기.
* 키를 눌러 합니다 **재생** 하려면 단추를 다시 미리 보기 모드를 종료 합니다.

**참고:** Unity에서 미리 보기 모드를 시작 하는 다음에 저장 된 대화방 메시 기본적으로 로드 됩니다.

## <a name="chapter-2---visualization"></a>2 장-시각화

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Objectives**
* 셰이더의 기본 사항을 알아봅니다.
* 환경을 시각화 합니다.

**지침**
* Unity의 **계층 구조** 패널을 선택 합니다 **SpatialMapping** 개체입니다.
* 에 **검사기** 패널에서 찾을 합니다 **공간 매핑 관리자 (스크립트)** 구성 요소입니다.
* 오른쪽에 원을 클릭 합니다 **표면 재질** 속성입니다.
* 찾기 및 선택 합니다 **BlueLinesOnWalls** material 및는 창 닫습니다.
* 에 **프로젝트** 패널 **셰이더** 폴더를 두 번 클릭 **BlueLinesOnWalls** 를 Visual Studio에서 셰이더를 엽니다.
* 이 간단한 픽셀 (조각 꼭 짓 점) 다음 작업을 수행 하는 셰이더:
    1. 세계 좌표 공간을 꼭 짓 점을 위치를 변환합니다.
    2. 꼭 짓 점이 픽셀에 세로 인지 확인 하려면 normal을 확인 합니다.
    3. 렌더링 된 픽셀의 색을 설정합니다.

**빌드 및 배포**
* Unity 및 키를 눌러 돌아갑니다 **재생** 미리 보기 모드로 전환 합니다.
* 파란색 선은 (저장 된 검색 데이터에서 자동으로 로드)는 공간이 메시의 모든 세로 화면에 렌더링 됩니다.
* 으로 전환 합니다 **장면** 탭 대화방의 보기를 조정 하 여 전체 공간 메시 Unity에 표시 되는 방식을 참조 하세요.
* 에 **프로젝트** 패널에서 찾을 **자료** 폴더를 선택 합니다 **BlueLinesOnWalls** 자료입니다.
* 일부 속성을 수정 하 고 Unity 편집기에서 변경 내용을 표시 하는 방법을 참조 하세요.
    * 에 **검사기** 패널을 조정 합니다 **LineScale** 두꺼운 두께 표시 하는 줄을 확인 하는 값.
    * 에 **검사기** 패널을 조정 합니다 **LinesPerMeter** 각 담 벼 락에 표시 된 줄 수를 변경 하려면 값.
* 클릭 **재생** 미리 보기 모드를 종료 하는 다시 합니다.
* 작성 하는 HoloLens에 배포 및 실제 화면에 렌더링 하는 셰이더 어떻게 표시 되는지 확인 합니다.

Unity는 훌륭한 자료, 미리 보기의 이지만 항상 장치에서 체크 아웃 렌더링 하는 것이 좋습니다.

## <a name="chapter-3---processing"></a>3 장-처리

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Objectives**
* 응용 프로그램에서 사용 하기 위해 공간 매핑 데이터를 처리 하는 방법에 알아봅니다.
* 평면을 검색 하 고 삼각형을 제거할 공간 매핑 데이터를 분석 합니다.
* 홀로그램 배치에 대해 평면을 사용 합니다.

**지침**
* Unity의 **프로젝트** 패널 **홀로그램** 폴더를 찾을 합니다 **SpatialProcessing** 개체입니다.
* 끌어서 놓기 합니다 **SpatialProcessing** 개체를 **계층** 패널입니다.

SpatialProcessing prefab 공간 매핑 데이터를 처리 하는 것에 대 한 구성 요소를 포함 합니다. **SurfaceMeshesToPlanes.cs** 찾아 평면 공간 매핑 데이터를 기반으로 생성 됩니다. 바닥, 벽, 최대값이 나타내는 평면 응용 프로그램에서 사용 됩니다. 이 prefab도 포함 되어 있습니다 **RemoveSurfaceVertices.cs** 공간 매핑 메시에 서 꼭 짓 점을 제거할 수는 있습니다. 이 메시에 구멍을 생성 하거나 (평면 사용할 수 있으므로 대신) 더 이상 필요 없는 과도 한 삼각형을 제거 하도록 사용할 수 없습니다.
* Unity의 **프로젝트** 패널 **홀로그램** 폴더를 찾을 합니다 **SpaceCollection** 개체입니다.
* 끌어서 놓기 합니다 **SpaceCollection** 개체를 **계층** 패널입니다.
* 에 **계층** 패널을 선택 합니다 **SpatialProcessing** 개체.
* 에 **검사기** 패널에서 찾을 합니다 **재생 공간 관리자 (스크립트)** 구성 요소입니다.
* 두 번 클릭 **PlaySpaceManager.cs** Visual Studio에서 엽니다.

PlaySpaceManager.cs 응용 프로그램별 코드를 포함합니다. 이 스크립트는 다음 동작을 사용 하도록 설정 하려면 기능을 추가 됩니다.
1. 검색 시간 제한 (10 초)를 초과 하는 후 공간 매핑을 데이터 수집을 중지 합니다.
2. 공간 매핑 데이터를 처리 합니다.
    1. SurfaceMeshesToPlanes 평면 (벽, 층, 최대값이 등)으로 전 세계의 간단한 표현을 만드는 데 사용 합니다.
    2. 평면 경계 내에 속하는 노출 삼각형 제거할 RemoveSurfaceVertices를 사용 합니다.
3. 전 세계에서 홀로그램의 컬렉션을 생성 하 고 벽 및 층 평면 사용자 근처에 배치 합니다.

PlaySpaceManager.cs, 표시 코딩 연습을 완료 하거나 아래에서 완성 된 솔루션을 사용 하 여 스크립트를 바꿉니다.

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
* 키를 눌러는 HoloLens를 배포 하기 전에 합니다 **재생** 재생 모드로 전환 하는 Unity에서 단추입니다.
* 대화방 메시 파일에서 로드 되 면 처리 공간 매핑 메시에 서 시작 하기 전에 10 초 기다립니다.
* 처리가 완료 되 면 바닥, 벽, ceiling, 등을 나타내는 평면 나타납니다.
* 결국 평면 중 발견 된 하나의 태양계 floor 카메라 근처의 테이블에 표시를 표시 합니다.
* 두 가지 포스터는 너무 벽 카메라 근처에 표시 됩니다. 으로 전환 합니다 **장면** 탭에 표시 되지 않는 경우 **게임** 모드입니다.
* 키를 눌러 합니다 **재생** 다시 모드를 종료 하려면 play 단추입니다.
* 빌드 및 HoloLens, 평소 대로 배포 합니다.
* 검색 및 완료 공간 매핑 데이터의 처리를 기다립니다.
* 평면에 표시 되 면 전 세계에서 태양계 및 포스터를 찾으려고 시도 합니다.

## <a name="chapter-4---placement"></a>4 장-배치

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Objectives**
* 홀로그램 화면에 맞는 경우를 결정 합니다.
* 화면에서를 홀로그램/없는 경우 사용자에 게 피드백을 제공 합니다.

**지침**
* Unity의 **계층 구조** 패널을 선택 합니다 **SpatialProcessing** 개체입니다.
* 에 **검사기** 패널에서 찾을 합니다 **표면 메시를 평면 (스크립트)** 구성 요소입니다.
* 변경 된 **그리기 평면** 속성을 **Nothing** 선택을 취소 합니다.
* 변경 합니다 **그리는 평면** 속성을 **벽**벽 평면에만 렌더링 될 수 있도록 합니다.
* 에 **프로젝트** 패널 **스크립트** 폴더를 두 번 클릭 **Placeable.cs** Visual Studio에서 엽니다.

합니다 **Placeable** 스크립트가 평면 찾기 완료 된 후 만들어진 포스터 및 프로젝션 상자에 이미 연결 되어 있습니다. 수행 해야 하는 것은 일부 코드를 주석 처리를 제거 하 고이 스크립트는 다음을 수행:
1. 홀로그램 플레이어가 중심 경계 큐브의 네 모퉁이를 여는 화면에 맞도록 경우를 결정 합니다.
2. 플러시 보관 홀로그램에 대 한 충분 한 부드러운 인지 확인 하는 일반적인 화면을 확인 합니다.
3. 실제 크기로 배치 하는 동안 표시할 홀로그램 주위의 경계 큐브를 렌더링 합니다.
4. 아래/뒤 floor/벽에 배치 됩니다 여기서 표시할 홀로그램 섀도 캐스팅 합니다.
5. 그림자 빨강으로 렌더링할를 홀로그램 가능한 경우 녹색, 화면에 배치할 수 없습니다.
6. 선호도 노출 종류 (세로 또는 가로)에 맞춰 홀로그램 방향을 다시 지정 합니다.
7. 이동 또는 동작을 맞추기 방지 하기 위해 선택한 화면에서를 홀로그램을 원활 하 게 배치 합니다.

아래 코딩 연습에서 모든 코드 주석 처리를 제거 하거나이 완료 된 솔루션에서 사용 하 여 **Placeable.cs**:

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
* 검색 및 완료 공간 매핑 데이터의 처리를 기다립니다.
* 태양계에 표시 되 면 아래에 있는 프로젝션 상자 응시 고 해 선택 제스처를 수행 합니다. 프로젝션 확인란을 선택 하는 동안 경계 큐브 프로젝션 상자 주위에 표시 됩니다.
* 대화방의 다른 위치를 응시 이동을 이동 합니다. 프로젝션 상자에 응시를 따라야 합니다. 프로젝션 상자 아래의 그림자 색이 빨강으로 홀로그램 해당 화면에 배치할 수 없습니다. 프로젝션 상자 아래의 섀도 녹색 바뀌면 다른 선택 제스처를 수행 하 여를 홀로그램을 배치할 수 있습니다.
* 찾기 및 새 위치로 이동할 벽 holographic 포스터 중 하나를 선택 합니다. Floor 또는 한계 포스터를 배치할 수 없습니다 하 고 항상 각 옆면에 올바르게 방향 이동 살펴보세요.

## <a name="chapter-5---occlusion"></a>5 장-폐색

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Objectives**
* 공간 매핑 관계로 홀로그램 폐색는 경우를 결정 합니다.
* 재미 있는 달성 하기 위해 다른 폐색 기술을 적용할 효과입니다.

**지침**

먼저 실제 occluding 없이 다른 홀로그램 채워집니다에 공간 매핑 메시를 허용 하려는:
* 에 **계층** 패널을 선택 합니다 **SpatialProcessing** 개체.
* 에 **검사기** 패널에서 찾을 합니다 **재생 공간 관리자 (스크립트)** 구성 요소입니다.
* 오른쪽에 원을 클릭 합니다 **보조 자료** 속성입니다.
* 찾기 및 선택 합니다 **폐색** material 및는 창 닫습니다.

다음으로, 하겠습니다 지구, 특별 한 동작을 추가할 때마다 (예: 일요일), 다른 홀로그램 하거나 공간 매핑 메시 여 폐색 됩니다 파란색 강조 표시가 포함 되도록:
* 에 **프로젝트** 패널를 **홀로그램** 폴더를 확장 합니다 **SolarSystem** 개체.
* 클릭할 **지구**합니다.
* 에 **검사기** 패널에서 지구 자료 (아래 구성 요소)를 확인 합니다.
* 에 **셰이더 드롭다운**, 셰이더를 변경할 **사용자 지정 > OcclusionRim**합니다. 이 다른 개체에 의해 폐색는 때마다 지구 주변의 파란색 강조 표시를 렌더링 합니다.

마지막으로, 태양 시스템에서 행성에 대 한 x-레이 시각 효과 사용 하도록 설정 하는 예정입니다. 편집 해야 합니다 **PlanetOcclusion.cs** (Scripts\SolarSystem 폴더에 있음) 다음을 구현 하려면:
1. 전 세계 SpatialMapping 계층 (대화방 메시 및 비행기)에서 폐색는 경우를 결정 합니다.
2. SpatialMapping 계층에서 폐색는 때마다는 전 세계의 와이어 프레임 표현을 보여 줍니다.
3. SpatialMapping 계층에서 차단 되지 않는 경우에 전 세계의 와이어 프레임 표현을 숨깁니다.

PlanetOcclusion.cs의 코딩 연습을 따르거나 다음 솔루션을 사용 합니다.

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
* 빌드 및 HoloLens, 응용 프로그램을 평소 대로 배포 합니다.
* 검색 및 완료 되기를 공간 매핑 데이터의 처리를 위해 대기 (벽에 표시 되는 파란색 줄이 표시 됩니다).
* 찾을 태양계의 프로젝션 상자를 선택 하 고 카운터 빠르거나 벽 옆에 있는 상자를 설정 합니다.
* 기본 폐색 숨기기 포스터 또는 프로젝션 box에서 피어 링 하려면 화면 뒤에서 볼 수 있습니다.
* 지구를 찾고, 다른 홀로그램 또는 화면 뒤 만약 때마다 파란색 강조 표시가 적용 해야 합니다.
* 행성 벽 또는 단체 실에 다른 화면 뒤 나가면서를 시청 하세요. 이제 레이 투시 능력이 있고 해당 와이어 프레임 구조를 볼 수 있습니다.

## <a name="the-end"></a>끝

축하합니다. 이제 완료 **MR 공간 230: 공간 매핑**합니다.
* Unity에 환경 및 부하 공간 매핑 데이터를 검색 하는 방법을 알고 있습니다.
* 셰이더와 다시 전 세계를 시각화 자료를 사용할 수 있는 방법을의 기초를 이해 합니다.
* 평면을 찾고 삼각형 메시에서 제거 하기 위한 새 처리 기술을 배웠습니다.
* 이동 하 고 있는 것은 타당 표면 홀로그램 배치 수 있었습니다.
* 다른 폐색 기술을 발생 하 고 레이 투시 능력이의 강력한 성능을 활용!
