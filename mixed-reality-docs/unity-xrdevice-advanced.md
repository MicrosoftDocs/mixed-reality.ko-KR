---
title: Unity에서 혼합된 현실 네이티브 개체
description: Unity의 기본 Holographic 네이티브 개체에 대 한 액세스를 가져옵니다.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: 혼합 현실, 네이티브, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr unity
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942099"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Unity에서 혼합된 현실 네이티브 개체

[가져오기는 HolographicSpace](getting-a-holographicspace.md) 모든 혼합 현실 앱은 카메라 데이터를 수신 하 고 렌더링을 시작 하기 전에 새로운 프레임은입니다. Unity에서 엔진이 처리는 이러한 단계를 Holographic 개체를 처리 하 고 해당 렌더링 루프의 일부로 내부적으로 업데이트 합니다.

그러나 고급 시나리오에서는 해야와 같은 기본 네이티브 개체에 액세스 하는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> 및 현재 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>합니다. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> 는 이러한 네이티브 개체에 대 한 액세스를 제공 하는 것입니다.

## <a name="xrdevice"></a>XRDevice 

**Namespace:** *UnityEngine.XR*<br>
**형식:** *XRDevice*

합니다 *XRDevice* 유형을 사용 하 여 기본 네이티브 개체에 액세스할 수 있습니다 합니다 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> 메서드. 여러 플랫폼 간에 다릅니다 GetNativePtr 반환 합니다. XRDevice.GetNativePtr 유니버설 Windows 플랫폼에서 Windows Mixed Reality xr 하이 SDK를 대상으로 할 때, 다음 구조에 대 한 포인터 (IntPtr)를 반환 합니다. 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
Marshal.PtrToStructure 메서드를 사용 하 여 HolographicFrameNativeData를 변환할 수 있습니다.
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** IntPtr MaxNumberOfCameras 같음 길이가 UnmanagedType.ByValArray 마샬링될 배열의* 


### <a name="using-holographicframenativedata"></a>HolographicFrameNativeData를 사용 하 여

> [!NOTE]
> HolographicFrameNativeData 통해 수신 하는 네이티브 개체의 상태를 변경 하면 발생할 수 있습니다 예측할 수 없는 동작 및 렌더링 아티팩트를 특히 Unity는 또한 동일한 해당 상태에 대 한 이유입니다.  예를 들어 HolographicFrame.UpdateCurrentPrediction를 호출 하지 않아야. 그러지 않으면 Unity 프레임을 사용 하 여 렌더링 하는 자세 예측을 줄일 수 있는 Windows 예상 하는 자세와 동기화 됩니다 [홀로그램 안정성](hologram-stability.md).

네이티브 인터페이스에 대 한 액세스에 필요한 경우 렌더링 또는 네이티브에 플러그 인에서 디버깅용 HolographicFrameNativeData에서 데이터를 사용할 수 있습니다 또는 C# 코드입니다. 

Photon 시간에 대 한 현재 프레임의 예측을 가져오려면 HolographicFrameNativeData를 사용 하는 방법의 예는 다음과 같습니다. 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a>관련 항목
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX의 렌더링](rendering-in-directx.md)
