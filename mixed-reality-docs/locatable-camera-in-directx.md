---
title: DirectX에서 찾을 수 있는 카메라
description: HoloLens 앱에서의 관점 (있는) 카메라를 사용 하는 방법에 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 찾을 수 있는 카메라, 관점, unporoject, media foundation MF 있는, 사용자 지정 싱크, 연습, 샘플 코드
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602085"
---
# <a name="locatable-camera-in-directx"></a>DirectX에서 찾을 수 있는 카메라

이 항목에서는 설정 하는 방법에 설명 합니다는 [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) 에 액세스 하려면 파이프라인는 [카메라](locatable-camera.md) DirectX 앱에서 이미지를 찾을 수 있도록 프레임 메타 데이터를 포함 하 여 생성 된 실제 환경에서.

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows 미디어 캡처 및 Media Foundation 개발: IMFAttributes

각 이미지 프레임 [좌표 시스템을 포함](locatable-camera.md#images-with-coordinate-systems) , 두 가지 중요 한 변환 뿐만 아니라 합니다. "View" 카메라에 제공 된 좌표계에서 지도 및 이미지의 픽셀을 "프로젝션" 지도 카메라를 변환합니다. 좌표계 및 2 변환 메타 데이터로 Media Foundation을 통해 모든 이미지 프레임에 포함 된 [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)합니다.

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>MF 사용자 지정 싱크를 사용 하 여 특성을 읽고 프로젝션을 수행 하는 샘플 사용

사용자 지정 MF 싱크 스트림을에서 ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx))을 얻게 됩니다 [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) 샘플 특성을 사용 하 여:

다음 MediaExtensions WinRT 기반 코드에 대 한 정의 되어야 합니다.

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

WinRT Api에서 이러한 특성에 액세스할 수 없습니다 하지만 미디어 확장 구현 해야 [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (대 한 영향을 주지) 또는 [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) 하 고 [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) ( 사용자 지정 싱크). 처리 하는 경우이 확장 프로그램의 샘플 중 하나에 [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) 또는 [IMFStreamSink::ProcessSample() ](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx),이 샘플과 같은 특성을 쿼리할 수 있습니다.

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

질감에서 카메라에 액세스 하려면 동일한 D3D 장치 카메라 프레임 질감을 만드는 해야 합니다. 이 D3D 장치가 [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) 캡처 파이프라인. 미디어 캡처를 사용할 수에서 DXGI 장치 관리자를 가져오려는 [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) 하 고 [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) 인터페이스입니다.

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

마우스 및 키보드 입력 Windows Mixed Reality 앱에 대 한 입력된 메서드를 선택적으로 사용할 수 있습니다. 이 HoloLens, 같은 장치에 대 한 뛰어난 디버깅 기능을 수도 있습니다 및 Pc에 연결 하는 몰입 형 헤드셋에서 실행 되는 혼합된 현실 앱에서 사용자 입력이 바람직 할 수 있습니다.
