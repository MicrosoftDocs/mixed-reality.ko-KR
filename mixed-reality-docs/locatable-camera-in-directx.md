---
title: DirectX의 과정이 카메라
description: HoloLens 앱에서 POV (지점 관점) 카메라를 사용 하는 방법을 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 과정이 카메라, 관점, POV, un, media foundation, MF, 사용자 지정 싱크, 연습, 샘플 코드
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516861"
---
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="acbd7-104">DirectX의 과정이 카메라</span><span class="sxs-lookup"><span data-stu-id="acbd7-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="acbd7-105">이 항목에서는 실제 세계에서 생성 된 이미지를 찾을 수 있는 프레임 메타 데이터를 포함 하 여 DirectX 앱에서 [카메라](locatable-camera.md) 에 액세스 하도록 [미디어 파운데이션](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) 파이프라인을 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="acbd7-106">Windows Media Capture 및 미디어 파운데이션 개발: IMFAttributes</span><span class="sxs-lookup"><span data-stu-id="acbd7-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="acbd7-107">각 이미지 프레임에는 두 가지 중요 한 변환 뿐만 아니라 [좌표계도 포함 됩니다](locatable-camera.md#images-with-coordinate-systems) .</span><span class="sxs-lookup"><span data-stu-id="acbd7-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="acbd7-108">"보기" 변환은 제공 된 좌표계에서 카메라로 매핑되고 "프로젝션"은 카메라에서 이미지의 픽셀로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="acbd7-109">좌표계 및 2 변환은 미디어 파운데이션의 [Imfattributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)를 통해 모든 이미지 프레임에 메타 데이터로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="acbd7-110">MF 사용자 지정 싱크로 특성 읽기 및 프로젝션을 수행 하는 샘플 사용</span><span class="sxs-lookup"><span data-stu-id="acbd7-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="acbd7-111">사용자 지정 MF 싱크 스트림 ([Imfstreamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx))에서 샘플 특성이 포함 된 [imfsample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) 을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="acbd7-112">다음 미디어 확장은 WinRT 기반 코드에 대해 정의 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="acbd7-113">WinRT Api에서는 이러한 특성에 액세스할 수 없지만 [Imftransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (효과) 또는 [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) 및 [Imfstreamsink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (사용자 지정 싱크에 대 한)의 미디어 확장 구현이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="acbd7-114">[Imftransform::P rocessinput ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[imftransform::P rocessoutput (](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) ) 또는 [imfstreamsink::P rocesssample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)에서이 확장의 샘플을 처리 하는 경우이 샘플과 같은 특성을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

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

<span data-ttu-id="acbd7-115">카메라에서 질감에 액세스 하려면 카메라 프레임 질감을 만드는 동일한 D3D 장치가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="acbd7-116">이 D3D 장치는 캡처 파이프라인에서 [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="acbd7-117">미디어 캡처에서 DXGI 장치 관리자를 가져오기 위해 [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) 및 [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) 인터페이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

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

<span data-ttu-id="acbd7-118">Windows Mixed Reality 앱에 대 한 선택적 입력 방법으로 마우스 및 키보드 입력을 사용 하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="acbd7-119">이는 HoloLens와 같은 장치에 대 한 유용한 디버깅 기능이 될 수도 있으며, Pc에 연결 된 모던 헤드셋에서 실행 되는 혼합 현실 앱에서 사용자 입력에 적합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acbd7-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
