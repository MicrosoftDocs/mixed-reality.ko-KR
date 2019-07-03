# <a name="getting-unity-ready-for-development"></a>Unity 개발을 위한 준비 

이 자습서에서는 준비 하 고 응용 프로그램 개발, 혼합 현실 도구 키트 가져오기, 빌드 설정을 구성 하 고이 장면 준비를 포함 하 여 Unity를 구성 하는 방법을 알아봅니다.

목표:

- 응용 프로그램 개발에 대 한 Unity를 구성 합니다.

- Mixed Reality Toolkit 가져오기

- 프로젝트 장면 준비

### <a name="instructions"></a>지침

1. 다운로드 하 고 클릭 하 여 혼합 현실 Toolkit unity 패키지를 저장 [여기 있습니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. Unity에서 패키지 가져오기 자산 메뉴를 클릭 하 고 선택한 사용자 지정 패키지에 클릭 합니다.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 1 단계에서 제공 된 링크에서 방금 다운로드 한 Unity 패키지를 선택 합니다. Unity에서 가져오기 팝업 창이 표시 되 면 가져오기를 시작 하려면 [가져오기] 단추를 클릭 합니다. 가져오기는 MRTK 몇 분 정도 걸릴 수 있습니다.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 참고: 다운로드 한 패키지 파일을 저장 한 로컬 폴더에 있습니다. 위의 이미지에서 패키지를 찾을 수 있습니다 표시 되지 않습니다.

4. 새 장면을 만듭니다. 이 수 하면 파일을 클릭 하 고 새 장면을 선택 하 여 "). 장면 HLSharedProjectMain로 저장 합니다.

> 참고: 아래 이미지와 비슷하게 보이는 팝업을 나타날 수 있습니다. 이제 클릭 아니요.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. 혼합 현실 도구 키트에서 장면 및 구성에 추가 클릭 합니다.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 완료 되 면 새 구성 파일을 표시, 프로필을 사용자 지정할 수 있는 옵션이 제공 됩니다. 복사를 클릭 하 고 사용자 지정 합니다.

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. 아래로 스크롤하여 진단 창 숨기려는 경우 Siagnostics 사용 시스템의 선택을 취소 합니다. 진단 창이 성능을 모니터링 하려면 응용 프로그램 개발 중 사용 하도록 설정 하 고 프로덕션 또는 응용 프로그램 데모 중 해제 상태로 유지 하는 것이 좋습니다. 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. 열린 컨트롤 + shift + B를 누르거나 파일을 이동 하 여 빌드 설정-> 빌드 설정 합니다. 프로그램이 독립 실행형 PC, Mac 및 Linux 플랫폼에서 현재 설정 되어 있는지 확인 합니다. HoloLens 2 개발에 대 한 유니버설 Windows 플랫폼으로 플랫폼을 설정 합니다. 선택 하 고 플랫폼 전환을 클릭 합니다.![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 완료 되 면 상자를 열고 백그라운드에서 추가 클릭 합니다. 이제 검사기 패널로 이동 하 고 가상 현실 지원 (아래 이미지에 표시 됨)는 오른쪽에 있는 확인란이 선택 되어 있는지 확인 합니다. 또한 아래 이미지에 표시 된 대로 장면을/HLSharedProjectMain 옆의 확인란도 선택 되어 있는지 확인 합니다.![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. 검사기 창에서 게시 설정 섹션에서 기능을 스크롤하고 다음 확인란 표시 되는지 확인 합니다.![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. 다운로드할 수 있는 SharingAssetCollection 라는 사용자 지정 패키지를 가져올 [여기.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. 프로젝트 패널에서 Prefabs 폴더로 이동 합니다. 다음 몇 단계에서 몇 가지 prefabs 장면에 구현할 수 있습니다. Prefabs 폴더에서 클릭 하 고 계층 안으로 DebugWindow prefab을 끕니다. 완료 되 면 clckin 파일에서 프로젝트를 저장 한 다음 저장 하거나 컨트롤 + S를 누릅니다.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 참고: 클릭 하면 prefab, TMP Essentials에 대 한 요청을 표시 하는 팝업을 볼 수 있습니다. 필요에 따라 가져오기 TMP Essentials를 클릭 합니다. 이 팝업이 나타나면 해야를 prefab 계층 구조에서 삭제를 다시 잠재적인 텍스트 관련 오류를 방지 하려면 계층으로 끕니다.
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>축하합니다.

Unity 프로젝트 Photon 준비가 되었습니다. 향후 자습서에서는이 장면 및 전체 공유 경험을 위해 Unity 프로젝트에 빌드 해 보겠습니다.

[다음 자습서의 경우: 여러 사용자를 연결합니다.](mrlearning-sharing(photon)-ch3.md)

