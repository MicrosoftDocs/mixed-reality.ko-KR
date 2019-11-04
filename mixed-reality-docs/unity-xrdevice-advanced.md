---
title: Unity의 혼합 현실 네이티브 개체
description: Unity에서 기본 Holographic 네이티브 개체에 대 한 액세스를 가져옵니다.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity, mixed reality, 네이티브, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 975775f64a19fe5fff4bc395a3e954cbf529dfa9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437339"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Unity의 혼합 현실 네이티브 개체

[HolographicSpace 가져오기](getting-a-holographicspace.md) 는 모든 혼합 현실 앱이 카메라 데이터 및 렌더링 프레임 수신을 시작 하기 전에 수행 하는 작업입니다. Unity에서 엔진은 렌더링 루프의 일부로 내부적으로 Holographic 개체 및 업데이트를 처리 하는 이러한 단계를 처리 합니다.

그러나 고급 시나리오에서는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> 및 current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>와 같은 기본 네이티브 개체에 대 한 액세스 권한을 얻어야 할 수 있습니다. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XRDevice</a> 는 이러한 네이티브 개체에 대 한 액세스를 제공 합니다.

## <a name="xrdevice"></a>XRDevice 

**네임 스페이스:** *UNITYENGINE. XR*<br>
**유형:** *xrdevice*

*Xrdevice* 유형을 사용 하면 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> 메서드를 사용 하 여 기본 네이티브 개체에 액세스할 수 있습니다. GetNativePtr 반환 되는 항목은 플랫폼 마다 다릅니다. 유니버설 Windows 플랫폼에서 Windows Mixed Reality XR SDK를 대상으로 지정 하는 경우 GetNativePtr는 다음 구조에 대 한 포인터 (IntPtr)를 반환 합니다. 

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
Marshal.sizeof와 marshal.ptrtostructure 메서드를 사용 하 여 HolographicFrameNativeData로 변환할 수 있습니다.
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** 은 길이가 MaxNumberOfCameras와 같은 unmanagedtype.lpwstr ByValArray으로 마샬링되는 IntPtr의 배열입니다.* 

### <a name="unmarshaling-native-pointers"></a>네이티브 포인터 역마샬링

[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) 를 사용 하는 경우 `FromNativePtr()` 메서드를 사용 하 여 네이티브 포인터에서 관리 되는 개체를 생성할 수 있습니다.

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

그렇지 않으면 `Marshal.GetObjectForIUnknown()`를 사용 하 여 원하는 형식으로 캐스팅 합니다.

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a>좌표계 간 변환

Unity는 왼손 좌표계를 사용 하는 반면 Windows 인식 Api는 오른손 좌표계를 사용 합니다. 이러한 두 가지 규칙을 변환 하기 위해 다음 도우미를 사용할 수 있습니다.

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a>HolographicFrame 네이티브 데이터 사용

> [!NOTE]
> HolographicFrameNativeData를 통해 수신 된 네이티브 개체의 상태를 변경 하면 예기치 않은 동작 및 렌더링 아티팩트가 발생할 수 있습니다. 특히 Unity에서 동일한 상태를 갖는 이유가 있을 수 있습니다.  예를 들어 HolographicFrame를 호출 하면 안 됩니다. UpdateCurrentPrediction를 호출 하면 안 됩니다. 그렇지 않으면 Unity가 해당 프레임으로 렌더링 하는 포즈 예측이 Windows에서 기대 하는 포즈와 동기화 되지 않아 [홀로그램 안정성이](hologram-stability.md)감소 합니다.

네이티브 인터페이스에 대 한 액세스가 네이티브 플러그 인 또는 C# 코드에서 렌더링 또는 디버깅 목적으로 필요한 경우 HolographicFrameNativeData의 데이터를 사용할 수 있습니다. 

HolographicFrameNativeData를 사용 하 여 photon time에 대 한 현재 프레임의 예측을 가져오는 방법의 예는 다음과 같습니다. 
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

## <a name="see-also"></a>참고 항목
* [HoloLens용 Unity 앱에서 Windows 네임스페이스 사용](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX의 렌더링](rendering-in-directx.md)
