# <a name="2-getting-unity-ready-for-development"></a>2. Unity를 개발할 준비 하는 중 


이 자습서에서는 Mixed Reality Toolkit 가져오기, 빌드 설정 구성, 장면 준비를 포함 하 여 응용 프로그램 개발을 위해 Unity를 준비 하 고 구성 하는 방법에 대해 알아봅니다.

## <a name="objectives"></a>목표

- 응용 프로그램 개발을 위한 Unity 구성

- Mixed Reality Toolkit 가져오기

- 프로젝트 장면 준비

## <a name="instructions"></a>지침

1. 여기를 클릭 하 여 Mixed Reality Toolkit unity 패키지를 다운로드 하 고 저장 [합니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)

2. Unity에서 자산 메뉴를 클릭 하 고 패키지 가져오기를 선택한 다음 사용자 지정 패키지를 클릭 합니다.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 1 단계에서 제공한 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다. Unity에 가져오기 팝업 창이 표시 되 면 가져오기 단추를 클릭 하 여 가져오기를 시작 합니다. MRTK를 가져오는 데 몇 분 정도 걸릴 수 있습니다.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 참고: 다운로드 된 패키지는 파일을 저장 한 로컬 폴더에 있습니다. 위의 이미지는 패키지를 찾을 위치를 표시 된다 하지 않습니다.

4. 새 장면을 만듭니다. 이 작업은 파일을 클릭 하 고 새 장면을 선택 하 여 수행할 수 있습니다. 장면을 HLSharedProjectMain로 저장 합니다.

> 참고: 아래 이미지와 비슷한 팝업을 받을 수 있습니다. 지금은 아니요를 클릭 합니다.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Mixed Reality Toolkit에서 장면에 추가 및 구성을 클릭 합니다.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 완료 되 면 프로필을 사용자 지정할 수 있는 새 구성 파일이 표시 됩니다. 복사 및 사용자 지정을 클릭 합니다.

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. 아래로 스크롤하여 진단 창을 숨기려면 진단 시스템 사용을 선택 취소 합니다. 응용 프로그램 개발 중에 진단 창을 사용 하도록 설정 하 여 성능을 모니터링 하 고 프로덕션 또는 응용 프로그램 데모 중에 사용 하지 않도록 설정 하는 것이 좋습니다. 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Ctrl + shift + B를 누르거나 파일 > 빌드 설정으로 이동 하 여 빌드 설정을 엽니다. 프로그램은 현재 PC, Mac 및 Linux 독립 실행형 플랫폼 아래에 설정 되어 있습니다. HoloLens 2 개발의 경우 플랫폼을 유니버설 Windows 플랫폼로 설정 합니다. 선택한 후 플랫폼 전환을 클릭 합니다.

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 완료 되 면 열려 있는 장면 추가 라는 상자를 클릭 합니다. 이제 검사기 패널로 이동 하 여 지원 되는 가상 현실 오른쪽에 있는 확인란이 선택 되어 있는지 확인 합니다 (아래 이미지에 표시 됨). 또한 아래 그림에 표시 된 것 처럼 장면/HLSharedProjectMain 옆의 확인란도 선택 되어 있는지 확인 합니다.

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. 검사기 패널의 게시 설정 섹션에서 기능으로 스크롤하고 다음 확인란이 표시 되어 있는지 확인 합니다.

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. 여기에서 다운로드할 수 있는 SharingAssetCollection 이라는 사용자 지정 패키지를 가져옵니다 [.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. 프로젝트 패널에서 Prefabs 폴더로 이동 합니다. 다음 몇 단계에서 장면에 몇 가지 prefabs 구현 합니다. Prefabs 폴더에서 prefab, 디버그 창을 클릭 하 여 계층으로 끕니다. 완료 되 면 파일을 클릭 한 다음 저장을 클릭 하거나 ctrl + S를 눌러 프로젝트를 저장 합니다.

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 참고: Prefab를 클릭 하면 TMP Essentials에 대 한 정보를 요청 하는 팝업이 표시 될 수 있습니다. 필요에 따라 TMP Essentials 가져오기를 클릭 합니다. 이 팝업이 표시 되 면 계층 구조에서 prefab을 삭제 하 고 텍스트 관련 오류 발생을 방지 하기 위해 계층으로 다시 끌어 야 할 수 있습니다.
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>축하합니다.

이제 Unity 프로젝트를 Photon 준비가 되었습니다. 향후 자습서에서는이 장면 및 Unity 프로젝트를 전체 공유 환경에 구축 합니다.

[다음 자습서: 3. 여러 사용자 연결](mrlearning-sharing(photon)-ch3.md)

