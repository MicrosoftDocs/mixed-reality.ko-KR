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
# <a name="qr-code-tracking"></a><span data-ttu-id="96f2b-104">QR 코드 추적</span><span class="sxs-lookup"><span data-stu-id="96f2b-104">QR code tracking</span></span>

<span data-ttu-id="96f2b-105">QR 코드 추적은 Windows Mixed Reality driver for 모던 (VR) 헤드셋에서 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="96f2b-106">헤드셋은 헤드셋 드라이버에서 QR 코드 추적기를 사용 하도록 설정 하 여 QR 코드를 검색 하 고 관심 있는 앱에 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="96f2b-107">이 기능은 [Windows 10 10 월 2018 업데이트 (RS5 라고도 함)](release-notes-october-2018.md)에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="96f2b-108">이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="96f2b-109">개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="96f2b-110">장치 지원</span><span class="sxs-lookup"><span data-stu-id="96f2b-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="96f2b-111"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="96f2b-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="96f2b-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="96f2b-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="96f2b-113"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="96f2b-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="96f2b-114">QR 코드 추적</span><span class="sxs-lookup"><span data-stu-id="96f2b-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="96f2b-115">❌</span><span class="sxs-lookup"><span data-stu-id="96f2b-115">❌</span></span></td>
        <td><span data-ttu-id="96f2b-116">✔️</span><span class="sxs-lookup"><span data-stu-id="96f2b-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="96f2b-117">헤드셋에서 QR 코드 추적 사용 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="96f2b-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="96f2b-118">참고: 이 섹션은 [Windows 10 10 월 2018 업데이트 (RS5 라고도 함)](release-notes-october-2018.md)에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="96f2b-119">19h1 빌드에서는이 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="96f2b-120">QR 코드 추적을 활용 하는 혼합 현실 앱을 개발 하 든, 이러한 앱 중 하나의 고객 인지 여부에 관계 없이 헤드셋의 드라이버에서 QR 코드 추적을 수동으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="96f2b-121">모던 (VR) 헤드셋에 대 한 **QR 코드 추적을 설정** 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="96f2b-122">PC에서 혼합 현실 포털 앱을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="96f2b-123">PC에서 헤드셋을 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="96f2b-124">명령 프롬프트에서 다음 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="96f2b-125">PC에 헤드셋을 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="96f2b-126">모던 (VR) 헤드셋에 대 한 **QR 코드 추적을 해제** 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="96f2b-127">PC에서 혼합 현실 포털 앱을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="96f2b-128">PC에서 헤드셋을 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="96f2b-129">명령 프롬프트에서 다음 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="96f2b-130">PC에 헤드셋을 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="96f2b-131">그러면 검색 된 QR 코드 "비 과정이"이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="96f2b-132">인쇄 코드</span><span class="sxs-lookup"><span data-stu-id="96f2b-132">Printing codes</span></span>

<span data-ttu-id="96f2b-133">가장 먼저, QR 코드 [의 사양](https://www.qrcode.com/en/howto/code.html) 에는 "qr 코드 기호 영역에 여백 또는" 자동 영역 "이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="96f2b-134">여백은 아무것도 인쇄 되지 않는 기호 주위의 선명한 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="96f2b-135">QR 코드에는 기호의 전체에 4 차원 여백이 필요 합니다. "</span><span class="sxs-lookup"><span data-stu-id="96f2b-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="96f2b-136">이 경우 모듈 크기의 4 배 (코드에서 단일 검정 사각형)의 너비를 모두 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="96f2b-137">사양 페이지에는 QR 코드를 인쇄 하는 방법에 대 한 조언을 포함 하 고 특정 크기의 QR 코드를 만드는 데 필요한 영역을 파악 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="96f2b-138">현재 QR 코드 감지 품질은 다양 한 조명 및 배경에 취약 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="96f2b-139">이를 공격 하려면 조명을 확인 하 고 적절 한 코드를 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="96f2b-140">특히 밝은 조명이 있는 장면에서 회색 배경의 검정색 코드를 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="96f2b-141">낮은 밝은 장면에서 흰색의 검은색은 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="96f2b-142">마찬가지로, 코드에 대 한 배경이 특히 어두운 경우 검색 속도가 낮은 경우 회색 코드를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="96f2b-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="96f2b-143">그렇지 않으면 배경이 더 가벼운 경우 일반 코드가 정상적으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="96f2b-144">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="96f2b-144">QRTracking API</span></span>

<span data-ttu-id="96f2b-145">QRTracking 플러그 인은 QR 코드 추적을 위한 Api를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="96f2b-146">플러그 인을 사용 하려면 *Qrcodestrackerplugin* 네임 스페이스에서 다음 형식을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="96f2b-147">Unity에서 QR 코드 추적 구현</span><span class="sxs-lookup"><span data-stu-id="96f2b-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="96f2b-148">MRTK의 샘플 Unity 장면 (혼합 현실 도구 키트)</span><span class="sxs-lookup"><span data-stu-id="96f2b-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="96f2b-149">Mixed Reality Toolkit [GitHub 사이트](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)에서 QR 추적 API를 사용 하는 방법에 대 한 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="96f2b-150">MRTK는 QR 추적 사용을 simpilify 하는 데 필요한 스크립트를 구현 했습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="96f2b-151">QR 추적 앱을 개발 하는 데 필요한 모든 자산은 "QRTracker" 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="96f2b-152">두 가지 장면이 있습니다. 첫 번째는 QR 코드의 세부 정보를 검색 된 것으로 표시 하는 샘플 이며, 두 번째는 QR 코드에 연결 된 좌표계를 사용 하 여 holograms를 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="96f2b-153">Qrscanner를 사용 하는 데 필요한 모든 스크립트를 장면에 추가 하는 "QRScanner" prefab 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="96f2b-154">스크립트 QRCodeManager는 QRCode API를 구현 하는 단일 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="96f2b-155">이를 장면에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-155">This needs to be added to your scene.</span></span> <span data-ttu-id="96f2b-156">"AttachToQRCode" 스크립트를 사용 하 여 QR 코드 좌표계 좌표계에 holograms를 연결 하면이 스크립트를 holograms에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="96f2b-157">"SpatialGraphCoordinateSystem"는 QRCode 좌표계를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="96f2b-158">이러한 스크립트는 프로젝트 장면에서 있는 그대로 사용 하거나 위에서 설명한 대로 플러그 인을 사용 하 여 직접 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="96f2b-159">MRTK 없이 Unity에서 QR 코드 추적 구현</span><span class="sxs-lookup"><span data-stu-id="96f2b-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="96f2b-160">MRTK에 대 한 종속성 없이 Unity에서 QR 추적 API를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="96f2b-161">API를 사용 하려면 다음 지침을 사용 하 여 프로젝트를 준비 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="96f2b-162">다음 이름을 사용 하 여 unity 프로젝트의 자산 폴더에 새 폴더를 만듭니다. "플러그 인"</span><span class="sxs-lookup"><span data-stu-id="96f2b-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="96f2b-163">[이 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) 의 필요한 모든 파일을 방금 만든 로컬 "플러그 인" 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="96f2b-164">[Mrtk scripts 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) 에서 QR 추적 스크립트를 사용 하거나 직접 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="96f2b-165">참고: 이러한 플러그 인은 [Windows 10 10 월 2018 업데이트 (RS5 라고도 함)](release-notes-october-2018.md) 빌드에만 해당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="96f2b-166">플러그 인은 다음 windows 릴리스로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="96f2b-167">현재 플러그 인은 실험적 이며 이후 버전의 windows에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="96f2b-168">다음 windows 릴리스에서 사용할 수 있는 새 플러그 인이 게시 되며, 이전에는 호환 되지 않으며 RS5에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="96f2b-169">DirectX에서 QR 코드 추적 구현</span><span class="sxs-lookup"><span data-stu-id="96f2b-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="96f2b-170">Visual Studio에서 QRTrackingPlugin을 사용 하려면 winmd에 QRTrackingPlugin의 참조를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="96f2b-171">[지원 되는 플랫폼에 필요한 파일은 여기](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="96f2b-172">좌표계 가져오기</span><span class="sxs-lookup"><span data-stu-id="96f2b-172">Getting a coordinate system</span></span>

<span data-ttu-id="96f2b-173">왼쪽 상단에 있는 빠른 검색 사각형의 왼쪽 위 모퉁이에 있는 QR 코드와 맞춘 오른쪽 좌표계를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="96f2b-174">좌표계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-174">The coordinate system is shown below.</span></span> <span data-ttu-id="96f2b-175">Z 축은 용지를 가리키지만 (표시 되지 않음) Unity에서 z 축은 종이와 왼손으로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="96f2b-176">표시 된 대로 정렬 된 SpatialCoordinateSystem가 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="96f2b-177">이 좌표계는 API *Windows::P erception:: 공간::P review:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*를 사용 하 여 플랫폼에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![QR 코드 좌표계](images/Qr-coordinatesystem.png) 

<span data-ttu-id="96f2b-179">QRCode ^ Code 개체에서 다음 코드는 사각형을 만들어 QR 좌표계에 배치 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="96f2b-180">실제 크기를 사용 하 여 QR 사각형을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="96f2b-181">좌표계를 사용 하 여 QR 코드를 그리거나 위치에 holograms을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="96f2b-182">*Qrcodestrackerplugin:: QRCodeAddedHandler* 은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="96f2b-183">문제 해결 및 FAQ</span><span class="sxs-lookup"><span data-stu-id="96f2b-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="96f2b-184">**일반 문제 해결**</span><span class="sxs-lookup"><span data-stu-id="96f2b-184">**General troubleshooting**</span></span>

* <span data-ttu-id="96f2b-185">PC에서 Windows 10 10 월 2018 업데이트를 실행 하 고 있나요?</span><span class="sxs-lookup"><span data-stu-id="96f2b-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="96f2b-186">Reg 키를 설정 했습니까?</span><span class="sxs-lookup"><span data-stu-id="96f2b-186">Have you set the reg key?</span></span> <span data-ttu-id="96f2b-187">장치를 나중에 다시 시작 했습니까?</span><span class="sxs-lookup"><span data-stu-id="96f2b-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="96f2b-188">QR 코드 버전이 지원 되는 버전 인가요?</span><span class="sxs-lookup"><span data-stu-id="96f2b-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="96f2b-189">현재 API는 최대 QR 코드 버전 20을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="96f2b-190">일반적인 사용을 위해 버전 5를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="96f2b-191">QR 코드에 충분히 가까이 있나요?</span><span class="sxs-lookup"><span data-stu-id="96f2b-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="96f2b-192">카메라가 QR 코드에 가까울수록 API에서 지원할 수 있는 QR 코드 버전이 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="96f2b-193">**QR 코드를 검색 하려면 어떻게 해야 하나요?**</span><span class="sxs-lookup"><span data-stu-id="96f2b-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="96f2b-194">이는 QR 코드의 크기와 버전이 무엇 인지에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="96f2b-195">5 cm에서 25cm 면에서 다양 한 버전 1 QR 코드의 경우 최소 검색 거리가 0.15 미터에서 0.5 미터 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="96f2b-196">이에 대 한 가장 멀리 떨어진 것은 더 작은 QR 코드 대상에 대 한 약 0.3 미터에서 더 큰 값의 1.4 미터까지 이동 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="96f2b-197">보다 큰 QR 코드의 경우에는 다음을 예측할 수 있습니다. 크기에 대 한 검색 거리가 선형적으로 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="96f2b-198">Tracker는 5cm 보다 작은 QR 코드에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="96f2b-199">**로고가 포함 된 QR 코드를 사용 하 시겠습니까?**</span><span class="sxs-lookup"><span data-stu-id="96f2b-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="96f2b-200">로고가 포함 된 QR 코드는 테스트 되지 않았으며 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="96f2b-201">**앱에서 QR 코드의 선택을 취소 하 여 유지 하지 않는 어떻게 할까요? 있나요?**</span><span class="sxs-lookup"><span data-stu-id="96f2b-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="96f2b-202">QR 코드는 부팅 세션 에서만 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="96f2b-203">다시 부팅 하거나 드라이버를 다시 시작 하면 다음 번에 새 개체로 표시 되 고 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="96f2b-204">QR 코드 기록은 드라이버 세션의 시스템 수준에서 저장 되지만, 원하는 경우 특정 타임 스탬프 보다 오래 된 QR 코드를 무시 하도록 앱을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="96f2b-205">현재 API는 여러 앱이 데이터에 관심이 있을 수 있으므로 QR 코드 기록 지우기를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="96f2b-206">**RS5 및 이후 버전에 대 한 플러그 인은 호환 되지 않습니다** . RS5 버전의 플러그 인은 RS5에 대해서만 작동 하며 이후 버전에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="96f2b-207">Expermental 플러그 인이 실제 플러그 인으로 바뀌고 이후 버전의 windows에서 사용할 수 있는 플러그 인이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f2b-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
