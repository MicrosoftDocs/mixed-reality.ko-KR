---
title: QR 코드 추적
description: HoloLens 2에서 QR 코드를 검색 하는 방법에 대해 알아봅니다.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: vr, lbe, 위치 기반 엔터테인먼트, vr 아케이드, 아케이드, 모던, qr, qr 코드, hololens2
ms.openlocfilehash: d51da88aa7bff1dc5c6d3068cb31793891c71e61
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566003"
---
# <a name="qr-code-tracking"></a>QR 코드 추적

HoloLens 2는 헤드셋 주위의 환경에서 QR 코드를 검색 하 여 각 코드의 실제 위치에서 좌표계를 설정할 수 있습니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>기능</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens(1세대)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> QR 코드 검색</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">참고 참조</td>
</tr>
</table>

>[!NOTE]
>데스크톱 Pc의 몰입 형 Windows Mixed Reality 헤드셋 지원은 현재 아래의 NuGet 패키지에서 지원 되지 않습니다.  데스크톱 지원에 대 한 추가 업데이트를 계속 해 서 조정 하세요.

## <a name="getting-the-qr-package"></a>QR 패키지 가져오기
[여기](https://github.com/dorreneb/mixed-reality/releases)에서 QR 코드 검색을 위한 NuGet 패키지를 다운로드할 수 있습니다.

이 패키지의 이후 버전은 공용 NuGet 패키지 리포지토리를 통해 사용할 수 있습니다.

## <a name="detecting-qr-codes"></a>QR 코드 검색

### <a name="adding-the-webcam-capability"></a>웹캠 기능 추가
QR 코드를 검색 하려면 매니페스트에 기능 `webcam` 을 추가 해야 합니다. 이 기능은 사용자 환경에서 검색 된 코드 내의 데이터에 중요 한 정보가 포함 될 수 있으므로 필요 합니다.

다음을 호출 `QRCodeWatcher.RequestAccessAsync()`하 여 사용 권한을 요청할 수 있습니다.

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

QRCodeWatcher 개체를 구성 하기 전에 사용 권한을 요청 해야 합니다.

QR 코드 검색 `webcam` 기능을 사용 하려면 장치의 추적 카메라를 사용 하 여 검색을 수행 합니다. 이를 통해 장치 사진/비디오 (PV) 카메라를 검색 하는 것과 비교 하 여 더 광범위 한 검색 FOV와 더 나은 배터리 수명을 제공 합니다.

### <a name="detecting-qr-codes-in-unity"></a>Unity에서 QR 코드 검색

MRTK에 대 한 종속성을 취하지 않고 Unity에서 QR 코드 검색 API를 사용할 수 있습니다. 이렇게 하려면 다음을 수행 해야 합니다.

1. 이름 *플러그*인을 사용 하 여 unity 프로젝트의 자산 폴더에 새 폴더를 만듭니다.
2. 이 폴더의 필요한 모든 파일을 방금 만든 로컬 "플러그 인" 폴더에 복사 합니다.

Holographic square와 연결 된 데이터 (예: GUID, 실제 크기, 타임 스탬프 및 디코딩된 데이터)를 표시 하는 샘플 Unity 앱이 있습니다. 이 앱은에서 https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes 찾을 수 있습니다.

### <a name="detecting-qr-codes-in-c"></a>에서 QR 코드 검색C++

>[!NOTE]
>이 C++ 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되는 C++것 처럼 C + 17-so-far working 규격 C++/winrt가 아닌/cx 사용을 보여 줍니다. 개념은 코드를 변환 해야 C++하지만/winrt 프로젝트에 대해 동일 합니다.

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>QR 코드의 좌표계 가져오기

검색 된 각 QR 코드는 아래와 같이 왼쪽 상단에 있는 빠른 검색 사각형의 왼쪽 위 모서리에 있는 QR 코드와 정렬 된 [공간 좌표계](coordinate-systems.md) 를 제공 합니다.  QR SDK를 직접 사용 하는 경우 Z 축이 문서를 가리키고 (표시 되지 않음) Unity 좌표로 변환 되 면 Z 축 지점은 용지에서 제외 되며 왼쪽으로 전달 됩니다.

QR 코드의 SpatialCoordinateSystem가 표시 됩니다. 이 좌표계는 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> 를 호출 하 고 코드의 SpatialGraphNodeId를 전달 하 여 플랫폼에서 가져올 수 있습니다.

![QR 코드 좌표계](images/Qr-coordinatesystem.png) 

QRCode 개체의 경우 다음 C++/cx 코드는 사각형을 만들고 QR 코드의 좌표계를 사용 하 여 삽입 하는 방법을 보여 줍니다.

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

실제 크기를 사용 하 여 QR 사각형을 만들 수 있습니다.

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

좌표계를 사용 하 여 QR 코드를 그리거나 위치에 holograms을 연결할 수 있습니다.

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

*Qrcodewatcher:: QRCodeAddedHandler* 은 다음과 같을 수 있습니다.

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
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

## <a name="best-practices-for-qr-code-detection"></a>QR 코드 검색에 대 한 모범 사례

### <a name="quiet-zones-around-qr-codes"></a>QR 코드 주위의 자동 영역

올바르게 읽도록 하려면 QR 코드에 코드의 모든 측면에 대 한 여백이 필요 합니다. 이 여백은 인쇄 된 콘텐츠를 포함 하지 않아야 하 고 4 개의 모듈 (코드의 검정 사각형 하나) 너비 여야 합니다. 

[QR](https://www.qrcode.com/en/howto/code.html) 사양은 자동 영역에 대 한 자세한 정보를 포함 합니다.

### <a name="lighting-and-backdrop"></a>조명 및 배경
QR 코드 검색 품질은 다양 한 조명 및 배경에 영향을 받습니다. 

특히 밝은 조명이 있는 장면에서 회색 배경의 검정색 코드를 인쇄 합니다. 그렇지 않으면 흰색 배경으로 검정색 QR 코드를 인쇄 합니다.

코드에 대 한 배경이 특히 어두운 경우 검색 속도가 낮은 경우 회색 코드에서 검정을 시도 합니다. 배경이 비교적 밝은 경우 일반 코드가 정상적으로 작동 해야 합니다.

### <a name="size-of-qr-codes"></a>QR 코드 크기
Windows Mixed Reality 장치는 각각 5cm 보다 작은 QR 코드에서 작동 하지 않습니다.

5-10 cm 길이 면에서 QR 코드의 경우에는 코드를 검색 하는 데 상당히 가까이 두어야 합니다. 이 크기의 코드를 검색 하는 데 더 많은 시간이 걸립니다. 

코드를 검색 하는 정확한 시간은 QR 코드의 크기 뿐만 아니라 코드에서 떨어져 있는 정도에 따라 달라 집니다. 코드에 가까이 이동 하면 크기와 관련 된 문제를 오프셋할 수 있습니다.

### <a name="distance-and-angular-position-from-the-qr-code"></a>QR 코드의 거리 및 각도 위치
추적 카메라는 특정 수준의 세부 정보만 검색할 수 있습니다. 매우 작은 코드의 경우에는 옆쪽을 따라 < 10cm-반드시 가까워야 합니다. 버전 1 QR 코드의 경우 10 ~ 25cm의 범위에서 최소 검색 거리가 0.15 미터에서 0.5 미터 사이입니다. 

크기에 대 한 검색 거리가 선형적으로 늘어납니다. 

QR 검색은 각도 + = 45deg의 범위에서 작동 합니다. 코드를 검색 하기 위한 적절 한 해결 방법이 있는지 확인 하는 것입니다.

### <a name="qr-codes-with-logos"></a>로고가 포함 된 QR 코드
로고가 포함 된 QR 코드는 테스트 되지 않았으며 현재 지원 되지 않습니다.

### <a name="managing-qr-code-data"></a>QR 코드 데이터 관리
Windows Mixed Reality 장치는 드라이버의 시스템 수준에서 QR 코드를 검색 합니다. 장치를 다시 부팅 하면 검색 된 QR 코드가 사라지고 다음 번에 새 개체로 다시 검색 됩니다.

특정 타임 스탬프 보다 오래 된 QR 코드를 무시 하도록 앱을 구성 하는 것이 좋습니다. 현재이 API는 QR 코드 기록 지우기를 지원 하지 않습니다.

## <a name="qr-api-reference"></a>QR API 참조

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>참조
* [좌표계](coordinate-systems.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>