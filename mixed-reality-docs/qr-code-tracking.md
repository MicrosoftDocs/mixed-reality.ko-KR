---
title: QR 코드 추적
description: Windows Mixed Reality 몰입 형 (VR) 헤드셋에 대 한 추적 QR 코드를 설정 하는 방법을 알아보고 VR 앱에서 기능을 구현 합니다.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr lbe, 위치 기반 엔터테인먼트, vr 아케이드 아케이드, 몰입도 qr, qr 코드
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829980"
---
# <a name="qr-code-tracking"></a>QR 코드 추적

QR 코드를 추적 (VR) 헤드셋 몰입 형 Windows Mixed Reality 드라이버에 구현 됩니다. 헤드셋 드라이버에서 QR 코드 추적기를 사용 하 여 헤드셋 QR 코드를 검색 하 고 원하는 앱에 보고 됩니다. 이 기능은 에서만 사용할 수의 합니다 [Windows 10 년 10 월 2018 Update (라고도: RS5)](release-notes-october-2018.md)합니다.

>[!NOTE]
>이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).  개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>QR 코드 추적</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>설정 및 해제 QR 코드 헤드셋에 대 한 추적
참고: 이 섹션에만 유효 [Windows 10 년 10 월 2018 Update (라고도: RS5)](release-notes-october-2018.md)합니다. 19 h 1 빌드에서 이렇게 않아도 됩니다.
추적, QR 코드를 활용 하는 혼합된 현실 앱을 개발 하 든 이러한 앱 중 하나는 고객 QR 코드 헤드셋의 드라이버에서 추적을 수동으로 설정 해야 합니다.

순서 대로 **QR 코드 추적을 켤** 몰입 형 헤드셋 (VR)에 대 한 합니다.

1. PC에서 혼합된 현실 포털 앱을 닫습니다.
2. PC에서 헤드셋을 분리 합니다.
3. 명령 프롬프트에서 다음 스크립트를 실행 합니다.<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. 사용자 PC에 헤드셋 다시 연결 합니다.

순서 대로 **QR 코드 추적을 해제** 몰입 형 헤드셋 (VR)에 대 한 합니다.

1. PC에서 혼합된 현실 포털 앱을 닫습니다.
2. PC에서 헤드셋을 분리 합니다.
3. 명령 프롬프트에서 다음 스크립트를 실행 합니다.<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. 사용자 PC에 헤드셋 다시 연결 합니다. 이렇게 하면 모든 검색 된 QR 코드 "비-과정이."

## <a name="printing-codes"></a>코드 인쇄

무엇을 [QR 코드에 대 한 사양](https://www.qrcode.com/en/howto/code.html) 라는 "QR 코드 기호 영역 여백 또는"자동 영역 "을 사용할 수 있도록 주위에 필요 합니다. 여백에 아무것도 출력 되지 기호 관련 일반 영역입니다. QR 코드를 실행 하려면 기호의 모든 면에서 4 모듈 넓은 여백. " 이 너비를 4 번 모듈-코드에서 검은색 사각형 한 크기의 모든 측면에 해야 합니다. 사양 페이지 QR 코드를 인쇄 하 고 특정 크기의 QR 코드를 확인 하는 데 필요한 영역을 파악 하는 방법에 대 한 조언을 포함 합니다.

현재 QR 코드 검색 품질 다양 한 조명 및 배경 하기 쉽습니다. 이 해결 하 여 조명을 기록한 적절 한 코드를 인쇄 합니다. 특히 밝은 조명을 사용 하 여 장면에는 회색 배경에 검정 코드를 인쇄 합니다. 아래는 조명이 장면 black 흰색 작동 합니다. 마찬가지로 코드에 배경이 특히 어두운 색 이면 그래도 회색 코드에 검은색 검색 속도가 낮은 경우. 이 고, 그렇지 배경 인 밝은 일반 코드를 정상적으로 작동 합니다.

## <a name="qrtracking-api"></a>QRTracking API

QRTracking 플러그 인 QR 코드를 추적 하기 위한 Api를 노출 합니다. 플러그 인을 사용 하려면에서 다음 형식을 사용 해야 합니다 *QRCodesTrackerPlugin* 네임 스페이스입니다.

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a>Unity에서 추적 되는 QR 코드를 구현 합니다.

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>샘플 MRTK (혼합 현실 도구 키트)의 Unity 장면

혼합 현실 도구 키트의 QR 추적 API를 사용 하는 방법에 대 한 예제를 찾을 수 있습니다 [GitHub 사이트](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)합니다.

MRTK 사용 현황 추적 QR simpilify에 필요한 스크립트를 구현 했습니다. QR 추적 앱을 개발 하는 데 필요한 모든 자산 "QRTracker" 폴더에 있습니다. 두 장면 가지: 첫 번째는 단순히 감지 된와 두 번째 홀로그램 표시할 QR 코드를 연결할 좌표계를 사용 하는 방법에 설명 QR 코드의 세부 정보를 표시 하는 샘플입니다.
prefab "QRScanner" QRCodes 데 장면에 필요한 모든 스크립트를 추가 하는 경우 QRCodeManager 스크립트는 QRCode API를 구현 하는 단일 클래스입니다. 이 장면에 추가 해야 합니다. 스크립트 "AttachToQRCode" 홀로그램 QR 코드 좌표 시스템에 연결 하는,이 스크립트는 사용자 제공 중 하나에 추가할 수 있습니다. "SpatialGraphCoordinateSystem" QRCode 좌표계를 사용 하는 방법을 보여 줍니다. 으로 이러한 스크립트를 사용할 수 있습니다-는 프로젝트에서 장면을 하거나 작성할 수 직접 사용 하 여 플러그 인을 위에 설명 된 대로 합니다.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>QR 코드 MRTK 없이 Unity에서 추적 구현

Unity에서 MRTK에 의존 하지 않고 QR 추적 API를 사용할 수도 있습니다. API를 사용 하려면 다음 명령 사용 하 여 프로젝트를 준비 해야 합니다.

1. 이름 사용 하 여 unity 프로젝트의 자산 폴더에 새 폴더를 만듭니다. "플러그 인"입니다.
2. 필요한 모든 파일을 복사 [이 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) 방금 만든 로컬 "플러그 인" 폴더에 있습니다.
3. QR 추적에서 스크립트를 사용할 수는 [MRTK scripts 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) 하거나 직접 작성 합니다.
참고: 이러한 플러그 인은 동안만 [Windows 10 년 10 월 2018 Update (RS5이 라고도 함)](release-notes-october-2018.md) 작성 합니다. 다음 windows 릴리스를 사용 하 여 플러그 인 업데이트 됩니다. 현재 플러그 인은 실험적 했으며 이후 버전의 windows에 대 한 작동 하지 않습니다. 다음 windows 버전에서 사용할 수 있는 새 플러그 인을 게시할 수는 고 됩니다 이전 버전과 호환 가능 하며 RS5 작동 하지 것입니다).

## <a name="implementing-qr-code-tracking-in-directx"></a>QR 코드 DirectX에서 추적 구현

Visual Studio에서의 QRTrackingPlugin를 사용 하는.winmd를 QRTrackingPlugin의 참조를 추가할 해야 합니다. 찾을 수 있습니다 합니다 [여기에 지원 되는 플랫폼에 필요한 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)합니다.

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a>좌표계를 시작합니다.

왼쪽 상단에 있는 빠른 검색 사각형의 왼쪽된 위 모퉁이에서 QR 코드를 사용 하 여 정렬 오른쪽 좌표 시스템을 정의 합니다. 좌표계는 다음과 같습니다. Z 축 (표시 되지 않음) 백서를 가리키고 이지만 Unity의 z 축 용지 부족 및 왼쪽.

SpatialCoordinateSystem 표시 된 대로 정렬 되는 정의 되어 있습니다. 이 좌표 시스템 API를 사용 하 여 플랫폼에서 가져올 수 있습니다 *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*합니다.

![QR 코드 좌표계](images/Qr-coordinatesystem.png) 

QRCode에서 ^ 코드 개체에 다음 코드는 사각형을 만들고 QR 좌표계에 배치 하는 방법을 보여줍니다.

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

QR 사각형을 만드는 실제 크기를 사용할 수 있습니다.

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

QR 코드를 그리거나 홀로그램 위치에 연결 하는 좌표계를 사용할 수 있습니다.

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

모두 하 *QRCodesTrackerPlugin::QRCodeAddedHandler* 다음과 같을 수 있습니다.

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a>문제 해결 및 FAQ

**일반적인 문제 해결**

* Windows 실행 PC는 10 년 10 월 2018 업데이트?
* 레지스트리 키를 설정한? 나중에 장치를 다시 시작 하 시겠습니까?
* QR 코드 버전을 지원 되는 버전은? QR 코드 버전 20까지 현재 API 지원 합니다. 버전 5를 사용 하 여 일반적으로 사용 하는 것이 좋습니다. 
* QR 코드를 닫을 수는? 카메라를 QR 코드에 가까울수록, 높을수록 QR 코드 버전이 API를 지원할 수 있습니다.  

**얼마나 근접 하 고 검색을 위해 QR 코드를 하나요?**

QR 코드의 크기에 따라 달라 집니다이 되며 또한 버전. 25 cm 양쪽으로 5 cm 양쪽에서 다양 한 버전 1 QR 코드에 대 한 최소 감지 거리는 0.5 미터제로 바뀌는 0.15 미터에서 범위입니다. 검색할 수 있습니다 이러한 합니다 멀리 떨어진 작은 QR 코드의 대상에 대 한 약 0.3 미터에서로 이동 클수록 1.4 기준은 합니다. QR 코드를 보다 더 큰에 대 한 다음을 예측할 수 있습니다. 크기에 대 한 감지 거리 연속적으로 늘어납니다. 우리의 추적기 작동 하지 않습니다 양쪽을 사용 하 여 QR 코드를 사용 하 여 5 cm 보다 작습니다.

**로고 작업을 사용 하 여 QR 코드?**

로고를 사용 하 여 QR 코드는 테스트 되지 않았습니다 하 고 현재 지원 되지 않습니다.

**지우는 방법 QR 코드 내 앱에서 유지 되지 됩니다 있도록?**

* QR 코드는 부트 세션에만 유지 됩니다. 수 다시 부팅, 드라이버를 다시 시작 되 면 이러한 완료 되며 새 개체가 다음 시간으로 검색 합니다.
* QR 코드 기록 드라이버 세션에서 시스템 수준에서 저장 됩니다 있지만 원하는 경우 특정 타임 스탬프 보다 오래 된 QR 코드를 무시 하도록 앱을 구성할 수 있습니다. 현재 API를 여러 앱 데이터에서 필요한 대로 지우기 QR 코드 기록을 지원지 않습니다.

**RS5 및 이후 버전에 대 한 플러그 인 시험판 호환 되지** RS5 플러그 인의 RS5 버전 에서만 작동 하며 이후 버전에 대 한 작동 하지 것입니다. Expermental 플러그 인 실제 플러그 인을 사용 하 여 대체 됩니다 하 고 사용할 수 있다는 이후 버전의 windows 것 이어야 합니다.
