---
title: Unreal의 HoloLens 사진/비디오 카메라
description: Unreal에서 HoloLens 사진/비디오 카메라 사용 가이드
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 카메라, PV 카메라, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451338"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="a86a0-104">Unreal의 HoloLens 사진/비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="a86a0-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="a86a0-105">HoloLens에는 MRC(혼합 현실 캡처)에서 사용하며 앱에서 실세계 시각적 개체에 액세스하는 데 사용하는 PV(사진/비디오) 카메라가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-105">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="a86a0-106">MRC용 PV 카메라에서 렌더링</span><span class="sxs-lookup"><span data-stu-id="a86a0-106">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="a86a0-107">여기에는 **Unreal Engine 4.25** 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-107">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="a86a0-108">시스템 및 사용자 지정 MRC 레코더는 몰입형 앱에서 렌더링한 홀로그램과 PV 카메라를 결합하여 혼합 현실 캡처를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-108">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="a86a0-109">기본적으로 혼합 현실 캡처는 오른쪽 눈의 홀로그램 출력을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-109">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="a86a0-110">몰입 형 앱이 [PV 카메라에서 렌더링](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)하도록 선택한 경우 해당 항목을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-110">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="a86a0-111">이를 통해 MRC 영상에서 실제 세계와 홀로그램의 매핑이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-111">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="a86a0-112">PV 카메라에서 렌더링하도록 옵트인하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-112">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="a86a0-113">**SetEnabledMixedRealityCamera** 및 **ResizeMixedRealityCamera** 호출</span><span class="sxs-lookup"><span data-stu-id="a86a0-113">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="a86a0-114">**크기 X** 및 **크기 Y** 값을 사용하여 비디오 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-114">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![세 번째 카메라](images/unreal-camera-3rd.PNG)

<span data-ttu-id="a86a0-116">그러면 Unreal은 PV 카메라의 관점에서 렌더링하는 MRC의 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-116">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="a86a0-117">[혼합 현실 캡처](mixed-reality-capture.md)가 트리거된 경우에만 앱이 사진/비디오 카메라의 관점에서 렌더링하도록 요청됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-117">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="a86a0-118">PV 카메라 사용</span><span class="sxs-lookup"><span data-stu-id="a86a0-118">Using the PV Camera</span></span>

<span data-ttu-id="a86a0-119">웹캠 질감을 게임에서 런타임에 검색할 수 있지만 편집기의 **편집 > 프로젝트 설정**에서 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-119">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="a86a0-120">**플랫폼 > HoloLens > 기능**으로 이동하여 **웹캠**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-120">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="a86a0-121">**StartCameraCapture** 함수를 사용하여 런타임에 웹캠을 사용하고 **StopCameraCapture** 함수를 사용하여 기록을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-121">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Camera 시작 중지](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="a86a0-123">이미지 렌더링</span><span class="sxs-lookup"><span data-stu-id="a86a0-123">Rendering an image</span></span>
<span data-ttu-id="a86a0-124">카메라 이미지를 렌더링하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-124">To render the camera image:</span></span>
1. <span data-ttu-id="a86a0-125">프로젝트의 재질을 기반으로 동적 재질 인스턴스를 만듭니다. 아래 스크린샷에서 이름이 **PVCamMat**입니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-125">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="a86a0-126">동적 재질 인스턴스를 **재질 인스턴스 동적 개체 참조** 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-126">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="a86a0-127">카메라 피드를 렌더링하는 장면의 개체 재질을 이 새로운 동적 재질 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-127">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="a86a0-128">카메라 이미지를 재질에 바인딩하는 데 사용할 타이머를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-128">Start a timer that will be used to bind the camera image to the material.</span></span> 

![카메라 렌더링](images/unreal-camera-render.PNG)

4. <span data-ttu-id="a86a0-130">이 타이머에 대한 새로운 기능을 만들고(이 경우 **MaterialTimer**), **GetARCameraImage**를 호출하여 웹캠에서 질감을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-130">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="a86a0-131">이 질감이 유효한 경우 음영의 질감 매개 변수를 이 이미지로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-131">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="a86a0-132">그렇지 않으면 재질 타이머를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-132">Otherwise, start the material timer again.</span></span> 

![카메라 텍스처](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="a86a0-134">재질에 색 항목에 바인딩된 **SetTextureParameterValue**의 이름과 일치하는 매개 변수가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-134">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="a86a0-135">매개 변수가 없으면 카메라 이미지를 제대로 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-135">Without this, the camera image can't be properly displayed.</span></span>

![카메라 텍스처](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="a86a0-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a86a0-137">See also</span></span>
* [<span data-ttu-id="a86a0-138">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="a86a0-138">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="a86a0-139">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="a86a0-139">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
