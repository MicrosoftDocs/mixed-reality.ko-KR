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
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="88e9c-104">Unity의 혼합 현실 네이티브 개체</span><span class="sxs-lookup"><span data-stu-id="88e9c-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="88e9c-105">[HolographicSpace 가져오기](getting-a-holographicspace.md) 는 모든 혼합 현실 앱이 카메라 데이터 및 렌더링 프레임 수신을 시작 하기 전에 수행 하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="88e9c-106">Unity에서 엔진은 렌더링 루프의 일부로 내부적으로 Holographic 개체 및 업데이트를 처리 하는 이러한 단계를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="88e9c-107">그러나 고급 시나리오에서는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> 및 current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>와 같은 기본 네이티브 개체에 대 한 액세스 권한을 얻어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="88e9c-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XRDevice</a> 는 이러한 네이티브 개체에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="88e9c-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="88e9c-109">XRDevice</span></span> 

<span data-ttu-id="88e9c-110">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="88e9c-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="88e9c-111">**유형:** *xrdevice*</span><span class="sxs-lookup"><span data-stu-id="88e9c-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="88e9c-112">*Xrdevice* 유형을 사용 하면 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> 메서드를 사용 하 여 기본 네이티브 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="88e9c-113">GetNativePtr 반환 되는 항목은 플랫폼 마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="88e9c-114">유니버설 Windows 플랫폼에서 Windows Mixed Reality XR SDK를 대상으로 지정 하는 경우 GetNativePtr는 다음 구조에 대 한 포인터 (IntPtr)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="88e9c-115">Marshal.sizeof와 marshal.ptrtostructure 메서드를 사용 하 여 HolographicFrameNativeData로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="88e9c-116">***IHolographicCameraPtr** 은 길이가 MaxNumberOfCameras와 같은 unmanagedtype.lpwstr ByValArray으로 마샬링되는 IntPtr의 배열입니다.*</span><span class="sxs-lookup"><span data-stu-id="88e9c-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="88e9c-117">네이티브 포인터 역마샬링</span><span class="sxs-lookup"><span data-stu-id="88e9c-117">Unmarshaling native pointers</span></span>

<span data-ttu-id="88e9c-118">[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) 를 사용 하는 경우 `FromNativePtr()` 메서드를 사용 하 여 네이티브 포인터에서 관리 되는 개체를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-118">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

<span data-ttu-id="88e9c-119">그렇지 않으면 `Marshal.GetObjectForIUnknown()`를 사용 하 여 원하는 형식으로 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-119">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the desired type:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="88e9c-120">좌표계 간 변환</span><span class="sxs-lookup"><span data-stu-id="88e9c-120">Converting between coordinate systems</span></span>

<span data-ttu-id="88e9c-121">Unity는 왼손 좌표계를 사용 하는 반면 Windows 인식 Api는 오른손 좌표계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-121">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="88e9c-122">이러한 두 가지 규칙을 변환 하기 위해 다음 도우미를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-122">To convert between these two conventions, you can use the following helpers:</span></span>

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

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="88e9c-123">HolographicFrame 네이티브 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="88e9c-123">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="88e9c-124">HolographicFrameNativeData를 통해 수신 된 네이티브 개체의 상태를 변경 하면 예기치 않은 동작 및 렌더링 아티팩트가 발생할 수 있습니다. 특히 Unity에서 동일한 상태를 갖는 이유가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-124">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="88e9c-125">예를 들어 HolographicFrame를 호출 하면 안 됩니다. UpdateCurrentPrediction를 호출 하면 안 됩니다. 그렇지 않으면 Unity가 해당 프레임으로 렌더링 하는 포즈 예측이 Windows에서 기대 하는 포즈와 동기화 되지 않아 [홀로그램 안정성이](hologram-stability.md)감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-125">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="88e9c-126">네이티브 인터페이스에 대 한 액세스가 네이티브 플러그 인 또는 C# 코드에서 렌더링 또는 디버깅 목적으로 필요한 경우 HolographicFrameNativeData의 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-126">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="88e9c-127">HolographicFrameNativeData를 사용 하 여 photon time에 대 한 현재 프레임의 예측을 가져오는 방법의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88e9c-127">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="88e9c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88e9c-128">See Also</span></span>
* [<span data-ttu-id="88e9c-129">HoloLens용 Unity 앱에서 Windows 네임스페이스 사용</span><span class="sxs-lookup"><span data-stu-id="88e9c-129">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="88e9c-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="88e9c-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="88e9c-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="88e9c-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="88e9c-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="88e9c-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="88e9c-133">DirectX의 렌더링</span><span class="sxs-lookup"><span data-stu-id="88e9c-133">Rendering in DirectX</span></span>](rendering-in-directx.md)
