# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>HoloLens 용 Galaxy 탐색기 만들기 2

HoloLens의 Galaxy 탐색기를 업데이트 하는 방법 2를 시작 합니다. [Galaxy 탐색기] (https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy 탐색기") 는 원래 아이디어 프로그램 공유를 통해 HoloLens (첫 번째 gen) 용 오픈 소스 응용 프로그램으로 개발 되었으며, 많은 사람들이 보유 하 고 있는 첫 번째 혼합 현실 환경 중 하나입니다. 이제 [HoloLens 2의 새롭고 흥미로운 기능](https://www.microsoft.com/hololens/hardware)을 위해 업데이트 하 고 있습니다.

Microsoft Mixed Reality 스튜디오 (1) 중 하나로 서 일반적으로 상용 성적 솔루션을 개발 하 고 창의적인 개발 프로세스 전체에서 대상 플랫폼에 대 한 테스트를 & 개발 하 고 있습니다. 이제 HoloLens 2 장치에 아직 액세스할 수 없지만 Galaxy 탐색기에 대 한 업데이트를 시작 하는 것이 좋습니다. Microsoft는이 프로젝트에 대해 우리와 커뮤니티에서 사용할 수 있게 되는 프레임 워크 및 도구 (예: [Mrtk v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html))를 형성 하 고 있습니다.

원래 Galaxy 탐색기와 마찬가지로, [GitHub에서 프로젝트를 열어](https://github.com/Microsoft/GalaxyExplorer) 커뮤니티에 모든 권한이 있는지 확인 하 게 됩니다. 또한 MRTK v1에서 MRTK v 2로 포팅 하는 방법, HoloLens 2에서 제공 되는 새로운 기능을 기반으로 하 여 환경을 개선 하는 방법, 그리고 Galaxy 탐색기가 다중 플랫폼 환경. 따라서 HoloLens에서 Galaxy 탐색기를 보고 있든 (첫 번째 gen), HoloLens 2, Windows Mixed Reality 헤드셋 또는 Windows 10 desktop 중 어디에 있든 간에 편안 하 게 편안 하 게 경험 하 고 경험을 최대한 활용 하고자 합니다.

이 페이지는 프로젝트를 진행할 때 확장 되며, 프로젝트에 대 한 참가자의 의견을 제공 하기 위해 더 자세한 문서, 코드, 디자인 아티팩트의, 추가 MRTK v2 설명서 등에 연결 합니다.



(1) Microsoft Mixed Reality 스튜디오 팀-미국, 유럽 및 아시아 태평양-태평양-사용자 환경 디자인, holographic 컴퓨팅, AR/VR 기술 및 3D 개발의 전문가입니다. 3D 자산 만들기, DirectX, Unity, Unreal 등을 포함 합니다. 고객이 조직 전체에 측정 가능한 영향을 만들 수 있도록 하는 동시에 원하는 미래를 구상 하 고 설계, 빌드 및 제공 하는 데 도움이 됩니다. 스튜디오는 엔터프라이즈 응용 프로그램 통합, 도입, 운영 및 지원에 대 한 22000 이상의 Microsoft 서비스 전문가와 긴밀 하 게 협력 합니다.
