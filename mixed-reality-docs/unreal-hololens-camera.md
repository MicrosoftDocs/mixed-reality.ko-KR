---
title: Unreal의 HoloLens 카메라
description: Unreal에서 HoloLens 카메라 사용 가이드
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 카메라, 세 번째 카메라, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840122"
---
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="c563c-104">Unreal의 HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="c563c-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="c563c-105">세 번째 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="c563c-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="c563c-106">세 번째 카메라 MRC(Mixed Reality Capture)는 아이 텍스처 관점이 아닌 HoloLens 바이저의 카메라 관점에서 혼합 현실 캡처를 렌더링하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="c563c-107">이를 통해 MRC 영상에서 실제 세계와 홀로그램의 매핑이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="c563c-108">세 번째 카메라 MRC 사용을 선택하려면 원하는 비디오 크기로 SetEnabledMixedRealityCamera 및 ResizeMixedRealityCamera를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![세 번째 카메라](images/unreal-camera-3rd.PNG)

<span data-ttu-id="c563c-110">그런 다음 HoloLens 디바이스 포털에서 MRC 비디오를 녹화합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="c563c-111">PV 카메라</span><span class="sxs-lookup"><span data-stu-id="c563c-111">PV Camera</span></span>

<span data-ttu-id="c563c-112">런타임 시 게임에서 웹캠 텍스처를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="c563c-113">HoloLens에서 웹캠 텍스처를 가져오려면 먼저 프로젝트 설정> 플랫폼> HoloLens> 기능의 Unreal 에디터에서 "웹캠" 기능이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="c563c-114">StartCameraCapture 함수를 사용하여 런타임 시 웹캠 사용을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="c563c-115">StopCameraCapture 함수를 사용하여 캡처를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-115">Stop capturing with the StopCameraCapture function.</span></span> 

![Camera 시작 중지](images/unreal-camera-startstop.PNG)

<span data-ttu-id="c563c-117">카메라 이미지를 렌더링하려면 먼저 프로젝트의 재질을 기반으로 하는 동적 재질 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="c563c-118">이 경우 PVCamMat 이라는 재질을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="c563c-119">이를 Material Instance Dynamic Object Reference 유형의 변수에 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="c563c-120">그런 다음 장면에서 카메라 피드를 이 새로운 동적 재질 인스턴스에 렌더링할 개체의 재질을 설정하고 카메라 이미지를 재료에 바인딩하는 데 사용할 타이머를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![카메라 렌더링](images/unreal-camera-render.PNG)

<span data-ttu-id="c563c-122">이 타이머에 대한 새로운 기능을 만들고(이 경우 MaterialTimer), GetARCameraImage를 호출하여 웹캠에서 텍스처를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="c563c-123">이 텍스처가 유효한 경우 셰이더의 텍스처 파라미터를 이 이미지에 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="c563c-124">그렇지 않으면 재질 타이머를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-124">Otherwise, start the material timer again.</span></span> 

![카메라 텍스처](images/unreal-camera-texture.PNG)

<span data-ttu-id="c563c-126">카메라 이미지를 올바르게 표시하려면 재질에 SetTextureParameterValue의 이름과 일치하는 매개 변수가 색상 항목에 바인딩되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c563c-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![카메라 텍스처](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="c563c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c563c-128">See also</span></span>
* [<span data-ttu-id="c563c-129">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="c563c-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="c563c-130">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="c563c-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
