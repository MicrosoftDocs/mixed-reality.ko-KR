---
title: QR 코드 추적
description: Windows Mixed Reality 모던 (VR) 헤드셋에 대 한 QR 코드 추적을 설정 하 고 VR 앱에서 기능을 구현 하는 방법을 알아봅니다.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr, lbe, 위치 기반 엔터테인먼트, vr 아케이드, 아케이드, 모던, qr, qr 코드
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829980"
---
# <a name="qr-code-tracking"></a>QR 코드 추적

QR 코드 추적은 Windows Mixed Reality driver for 모던 (VR) 헤드셋에서 구현 됩니다. 헤드셋은 헤드셋 드라이버에서 QR 코드 추적기를 사용 하도록 설정 하 여 QR 코드를 검색 하 고 관심 있는 앱에 보고 합니다. 이 기능은 [Windows 10 10 월 2018 업데이트 (RS5 라고도 함)](release-notes-october-2018.md)에서만 사용할 수 있습니다.

>[!NOTE]
>이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.  개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>QR 코드 추적</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>헤드셋에서 QR 코드 추적 사용 및 사용 안 함
참고: 이 섹션은 [Windows 10 10 월 2018 업데이트 (RS5 라고도 함)](release-notes-october-2018.md)에만 유효 합니다. 19h1 빌드에서는이 작업을 수행할 필요가 없습니다.
QR 코드 추적을 활용 하는 혼합 현실 앱을 개발 하 든, 이러한 앱 중 하나의 고객 인지 여부에 관계 없이 헤드셋의 드라이버에서 QR 코드 추적을 수동으로 설정 해야 합니다.

모던 (VR) 헤드셋에 대 한 **QR 코드 추적을 설정** 하려면 다음을 수행 합니다.

1. PC에서 혼합 현실 포털 앱을 닫습니다.
2. PC에서 헤드셋을 분리 합니다.
3. 명령 프롬프트에서 다음 스크립트를 실행 합니다.<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. PC에 헤드셋을 다시 연결 합니다.

모던 (VR) 헤드셋에 대 한 **QR 코드 추적을 해제** 하려면 다음을 수행 합니다.

1. PC에서 혼합 현실 포털 앱을 닫습니다.
2. PC에서 헤드셋을 분리 합니다.
3. 명령 프롬프트에서 다음 스크립트를 실행 합니다.<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. PC에 헤드셋을 다시 연결 합니다. 그러면 검색 된 QR 코드 "비 과정이"이 생성 됩니다.

## <a name="printing-codes"></a>인쇄 코드

가장 먼저, QR 코드 [의 사양](https://www.qrcode.com/en/howto/code.html) 에는 "qr 코드 기호 영역에 여백 또는" 자동 영역 "이 필요 합니다. 여백은 아무것도 인쇄 되지 않는 기호 주위의 선명한 영역입니다. QR 코드에는 기호의 전체에 4 차원 여백이 필요 합니다. " 이 경우 모듈 크기의 4 배 (코드에서 단일 검정 사각형)의 너비를 모두 포함 해야 합니다. 사양 페이지에는 QR 코드를 인쇄 하는 방법에 대 한 조언을 포함 하 고 특정 크기의 QR 코드를 만드는 데 필요한 영역을 파악 합니다.

현재 QR 코드 감지 품질은 다양 한 조명 및 배경에 취약 합니다. 이를 공격 하려면 조명을 확인 하 고 적절 한 코드를 인쇄 합니다. 특히 밝은 조명이 있는 장면에서 회색 배경의 검정색 코드를 인쇄 합니다. 낮은 밝은 장면에서 흰색의 검은색은 작동 합니다. 마찬가지로, 코드에 대 한 배경이 특히 어두운 경우 검색 속도가 낮은 경우 회색 코드를 사용해 보세요. 그렇지 않으면 배경이 더 가벼운 경우 일반 코드가 정상적으로 작동 합니다.

## <a name="qrtracking-api"></a>QRTracking API

QRTracking 플러그 인은 QR 코드 추적을 위한 Api를 노출 합니다. 플러그 인을 사용 하려면 *Qrcodestrackerplugin* 네임 스페이스에서 다음 형식을 사용 해야 합니다.

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Unity에서 QR 코드 추적 구현

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>MRTK의 샘플 Unity 장면 (혼합 현실 도구 키트)

Mixed Reality Toolkit [GitHub 사이트](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)에서 QR 추적 API를 사용 하는 방법에 대 한 예제를 찾을 수 있습니다.

MRTK는 QR 추적 사용을 simpilify 하는 데 필요한 스크립트를 구현 했습니다. QR 추적 앱을 개발 하는 데 필요한 모든 자산은 "QRTracker" 폴더에 있습니다. 두 가지 장면이 있습니다. 첫 번째는 QR 코드의 세부 정보를 검색 된 것으로 표시 하는 샘플 이며, 두 번째는 QR 코드에 연결 된 좌표계를 사용 하 여 holograms를 표시 하는 방법을 보여 줍니다.
Qrscanner를 사용 하는 데 필요한 모든 스크립트를 장면에 추가 하는 "QRScanner" prefab 있습니다. 스크립트 QRCodeManager는 QRCode API를 구현 하는 단일 클래스입니다. 이를 장면에 추가 해야 합니다. "AttachToQRCode" 스크립트를 사용 하 여 QR 코드 좌표계 좌표계에 holograms를 연결 하면이 스크립트를 holograms에 추가할 수 있습니다. "SpatialGraphCoordinateSystem"는 QRCode 좌표계를 사용 하는 방법을 보여 줍니다. 이러한 스크립트는 프로젝트 장면에서 있는 그대로 사용 하거나 위에서 설명한 대로 플러그 인을 사용 하 여 직접 작성할 수 있습니다.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>MRTK 없이 Unity에서 QR 코드 추적 구현

MRTK에 대 한 종속성 없이 Unity에서 QR 추적 API를 사용할 수도 있습니다. API를 사용 하려면 다음 지침을 사용 하 여 프로젝트를 준비 해야 합니다.

1. 다음 이름을 사용 하 여 unity 프로젝트의 자산 폴더에 새 폴더를 만듭니다. "플러그 인"
2. [이 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) 의 필요한 모든 파일을 방금 만든 로컬 "플러그 인" 폴더에 복사 합니다.
3. [Mrtk scripts 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) 에서 QR 추적 스크립트를 사용 하거나 직접 작성할 수 있습니다.
참고: 이러한 플러그 인은 [Windows 10 10 월 2018 업데이트 (RS5 라고도 함)](release-notes-october-2018.md) 빌드에만 해당 됩니다. 플러그 인은 다음 windows 릴리스로 업데이트 됩니다. 현재 플러그 인은 실험적 이며 이후 버전의 windows에서 작동 하지 않습니다. 다음 windows 릴리스에서 사용할 수 있는 새 플러그 인이 게시 되며, 이전에는 호환 되지 않으며 RS5에서 작동 하지 않습니다.

## <a name="implementing-qr-code-tracking-in-directx"></a>DirectX에서 QR 코드 추적 구현

Visual Studio에서 QRTrackingPlugin을 사용 하려면 winmd에 QRTrackingPlugin의 참조를 추가 해야 합니다. [지원 되는 플랫폼에 필요한 파일은 여기](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)에서 찾을 수 있습니다.

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

## <a name="getting-a-coordinate-system"></a>좌표계 가져오기

왼쪽 상단에 있는 빠른 검색 사각형의 왼쪽 위 모퉁이에 있는 QR 코드와 맞춘 오른쪽 좌표계를 정의 합니다. 좌표계는 다음과 같습니다. Z 축은 용지를 가리키지만 (표시 되지 않음) Unity에서 z 축은 종이와 왼손으로 진행 됩니다.

표시 된 대로 정렬 된 SpatialCoordinateSystem가 정의 됩니다. 이 좌표계는 API *Windows::P erception:: 공간::P review:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*를 사용 하 여 플랫폼에서 가져올 수 있습니다.

![QR 코드 좌표계](images/Qr-coordinatesystem.png) 

QRCode ^ Code 개체에서 다음 코드는 사각형을 만들어 QR 좌표계에 배치 하는 방법을 보여 줍니다.

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

실제 크기를 사용 하 여 QR 사각형을 만들 수 있습니다.

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

좌표계를 사용 하 여 QR 코드를 그리거나 위치에 holograms을 연결할 수 있습니다.

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

*Qrcodestrackerplugin:: QRCodeAddedHandler* 은 다음과 같습니다.

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

**일반 문제 해결**

* PC에서 Windows 10 10 월 2018 업데이트를 실행 하 고 있나요?
* Reg 키를 설정 했습니까? 장치를 나중에 다시 시작 했습니까?
* QR 코드 버전이 지원 되는 버전 인가요? 현재 API는 최대 QR 코드 버전 20을 지원 합니다. 일반적인 사용을 위해 버전 5를 사용 하는 것이 좋습니다. 
* QR 코드에 충분히 가까이 있나요? 카메라가 QR 코드에 가까울수록 API에서 지원할 수 있는 QR 코드 버전이 더 높습니다.  

**QR 코드를 검색 하려면 어떻게 해야 하나요?**

이는 QR 코드의 크기와 버전이 무엇 인지에 따라 달라 집니다. 5 cm에서 25cm 면에서 다양 한 버전 1 QR 코드의 경우 최소 검색 거리가 0.15 미터에서 0.5 미터 사이입니다. 이에 대 한 가장 멀리 떨어진 것은 더 작은 QR 코드 대상에 대 한 약 0.3 미터에서 더 큰 값의 1.4 미터까지 이동 하는 것입니다. 보다 큰 QR 코드의 경우에는 다음을 예측할 수 있습니다. 크기에 대 한 검색 거리가 선형적으로 늘어납니다. Tracker는 5cm 보다 작은 QR 코드에서 작동 하지 않습니다.

**로고가 포함 된 QR 코드를 사용 하 시겠습니까?**

로고가 포함 된 QR 코드는 테스트 되지 않았으며 현재 지원 되지 않습니다.

**앱에서 QR 코드의 선택을 취소 하 여 유지 하지 않는 어떻게 할까요? 있나요?**

* QR 코드는 부팅 세션 에서만 유지 됩니다. 다시 부팅 하거나 드라이버를 다시 시작 하면 다음 번에 새 개체로 표시 되 고 검색 됩니다.
* QR 코드 기록은 드라이버 세션의 시스템 수준에서 저장 되지만, 원하는 경우 특정 타임 스탬프 보다 오래 된 QR 코드를 무시 하도록 앱을 구성할 수 있습니다. 현재 API는 여러 앱이 데이터에 관심이 있을 수 있으므로 QR 코드 기록 지우기를 지원 합니다.

**RS5 및 이후 버전에 대 한 플러그 인은 호환 되지 않습니다** . RS5 버전의 플러그 인은 RS5에 대해서만 작동 하며 이후 버전에서는 작동 하지 않습니다. Expermental 플러그 인이 실제 플러그 인으로 바뀌고 이후 버전의 windows에서 사용할 수 있는 플러그 인이 있어야 합니다.
