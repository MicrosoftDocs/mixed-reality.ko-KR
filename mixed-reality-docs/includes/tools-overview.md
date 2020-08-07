# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. 최신 버전 다운로드

새 프로젝트를 시작할 때 사용하기 가장 좋은 버전은 [Unity LTS(장기 지원)](https://unity3d.com/unity/qa/lts-releases) 스트림이며, 이것을 최신 개정판으로 업데이트하여 안정적인 최신 수정 프로그램을 선택하는 것이 좋습니다. 
* 현재 추천 사항은 아래의 MRTK v2에 필요한 LTS 빌드인 **Unity 2019**를 사용하는 것입니다.
* 특정 이유로 인해 다른 Unity 버전을 사용해야 하는 경우 Unity는 서로 다른 버전을 함께 설치하도록 지원합니다.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. MRTK(Mixed Reality Toolkit) 가져오기
![MRTK](../images/UX/MRTK_UX_Hero.png)

MRTK([Mixed Reality Toolkit](../mrtk-getting-started.md))는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다. MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. 도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity(GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Unity에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.

#### <a name="other-tools-optional"></a>기타 도구 [선택 사항]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Mixed Reality 개발용 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다. 또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다. 일부 도구는 이전 운영 체제에서 지원되지 않습니다. 

> [!NOTE]
> HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다. 필요에 따라 아래 요구 사항을 충족해야 합니다.

#### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 둘 다에 대한 시스템 요구 사항을 충족하는지 확인합니다. [HoloLens 에뮬레이터](../using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.

HoloLens 에뮬레이터를 시작하려면 [HoloLens 에뮬레이터 사용](../using-the-hololens-emulator.md)을 참조하세요.

HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.

#### <a name="immersive-vr-headset-requirements"></a>몰입형 (VR) 헤드셋 요구 사항

>[!NOTE]
>다음 지침은 몰입형(VR) 헤드셋 *개발 PC*에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.

>[!WARNING]
>이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양*을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.

몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.

현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.

<table>
<tr>
<th></th><th> 최소값</th><th> 권장</th>
</tr><tr>
<td> 프로세서</td><td> <b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</td><td> <b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</td>
</tr><tr>
<td> GPU</td><td> <b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td><td><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td>
</tr><tr>
<td> GPU 드라이버 WDDM 버전</td><td colspan="2"> WDDM 2.2 드라이버</td>
</tr><tr>
<td> 열 디자인 전원</td><td colspan="2"> 15W 이상</td>
</tr><tr>
<td> 그래픽 디스플레이 포트</td><td colspan="2"> 헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</td>
</tr><tr>
<td> 디스플레이 해상도</td><td colspan="2"> 해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</td>
</tr><tr>
<td> 메모리</td><td> 8GB&#160;RAM 이상</td><td> 16GB RAM 이상</td>
</tr><tr>
<td> 스토리지</td><td colspan="2"> &gt;10GB의 추가 사용 가능 공간</td>
</tr><tr>
<td> USB 포트</td><td colspan="2"> 헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0(액세서리 연결용)</td>
</tr>
</table>

### <a name="whats-next"></a>다음 작업

> [!div class="nextstepaction"]
> [Unity 경험 시작](../unity-development-overview.md)

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. 최신 버전 다운로드

HoloLens에 기본 제공되는 지원 기능을 최대한 활용하려면 [Unreal Engine 버전 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 이상을 설치하는 것이 좋습니다.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. MRTK(Mixed Reality Toolkit) 가져오기
![MRTK](../images/UX/MRTK_UX_Hero.png)

MRTK(Mixed Reality Toolkit)는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다. MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. 도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal(GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Unreal에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.

#### <a name="other-tools-optional"></a>기타 도구 [선택 사항]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. 혼합 현실 개발용 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다. 또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다. 일부 도구는 이전 운영 체제에서 지원되지 않습니다. 

> [!NOTE]
> HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다. 필요에 따라 아래 요구 사항을 충족해야 합니다.

#### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위해 개발 PC를 설정할 때 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다. [HoloLens 에뮬레이터](../using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.

HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.

#### <a name="immersive-vr-headset-requirements"></a>몰입형 (VR) 헤드셋 요구 사항

>[!NOTE]
>다음 지침은 몰입형(VR) 헤드셋 *개발 PC*에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.

>[!WARNING]
>이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양*을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.

몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.

현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.

<table>
<tr>
<th></th><th> 최소값</th><th> 권장</th>
</tr><tr>
<td> 프로세서</td><td> <b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</td><td> <b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</td>
</tr><tr>
<td> GPU</td><td> <b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td><td><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td>
</tr><tr>
<td> GPU 드라이버 WDDM 버전</td><td colspan="2"> WDDM 2.2 드라이버</td>
</tr><tr>
<td> 열 디자인 전원</td><td colspan="2"> 15W 이상</td>
</tr><tr>
<td> 그래픽 디스플레이 포트</td><td colspan="2"> 헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</td>
</tr><tr>
<td> 디스플레이 해상도</td><td colspan="2"> 해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</td>
</tr><tr>
<td> 메모리</td><td> 8GB&#160;RAM 이상</td><td> 16GB RAM 이상</td>
</tr><tr>
<td> 스토리지</td><td colspan="2"> &gt;10GB의 추가 사용 가능 공간</td>
</tr><tr>
<td> USB 포트</td><td colspan="2"> 헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0(액세서리 연결용)</td>
</tr>
</table>

### <a name="whats-next"></a>다음 작업

> [!div class="nextstepaction"]
> [Unreal 경험 시작](../unreal-development-overview.md)

# <a name="native-openxr"></a>[네이티브(OpenXR)](#tab/native)

 ![네이티브 앱 개발](../images/native_logo_banner.png)

네이티브 OpenXR 개발의 경우 다운로드할 엔진이 없습니다. 개발을 시작하는 데 필요한 모든 것은 [OpenXR 시작](../openxr-getting-started.md) 문서에서 찾을 수 있습니다.

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. 혼합 현실 개발용 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다. 또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다. 일부 도구는 이전 운영 체제에서 지원되지 않습니다.

#### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다. [HoloLens 에뮬레이터](../using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.

HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.

> [!NOTE]
> HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다. 필요에 따라 아래 요구 사항을 충족해야 합니다.

#### <a name="immersive-vr-headset-requirements"></a>몰입형 (VR) 헤드셋 요구 사항

>[!NOTE]
>다음 지침은 몰입형(VR) 헤드셋 *개발 PC*에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.

>[!WARNING]
>이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양*을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.

몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.

현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.

<table>
<tr>
<th></th><th> 최소값</th><th> 권장</th>
</tr><tr>
<td> 프로세서</td><td> <b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</td><td> <b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</td>
</tr><tr>
<td> GPU</td><td> <b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td><td><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td>
</tr><tr>
<td> GPU 드라이버 WDDM 버전</td><td colspan="2"> WDDM 2.2 드라이버</td>
</tr><tr>
<td> 열 디자인 전원</td><td colspan="2"> 15W 이상</td>
</tr><tr>
<td> 그래픽 디스플레이 포트</td><td colspan="2"> 헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</td>
</tr><tr>
<td> 디스플레이 해상도</td><td colspan="2"> 해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</td>
</tr><tr>
<td> 메모리</td><td> 8GB&#160;RAM 이상</td><td> 16GB RAM 이상</td>
</tr><tr>
<td> 스토리지</td><td colspan="2"> &gt;10GB의 추가 사용 가능 공간</td>
</tr><tr>
<td> USB 포트</td><td colspan="2"> 헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0(액세서리 연결용)</td>
</tr>
</table>

### <a name="whats-next"></a>다음 작업

> [!div class="nextstepaction"]
> [기본 경험 시작](../directx-development-overview.md)


