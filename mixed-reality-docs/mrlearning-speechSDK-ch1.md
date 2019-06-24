# <a name="speech-sdk-learning-module"></a>Speech SDK 학습 모듈

이 자습서에서는 Azure Cognitive Services 음성 SDK는 HoloLens 2를 사용 하 여 사용을 탐색 하는 혼합 현실 응용 프로그램을 만들게 됩니다. 이 자습서 시리즈를 사용 하 여 완료 되 면 장치의 마이크를 사용 하 여 실시간으로 텍스트를 음성 기록, 사용자 음성을 다른 언어로 번역 및 Speech SDK를 사용 하 여 음성 명령을 인식 하도록 의도 기능을 활용 하는 일을 할 수는 인공 지능 합니다.

목표:

- HoloLens 2 응용 프로그램에 Azure Speech SDK를 통합 하는 방법에 알아봅니다.
- 음성 명령을 사용 하는 방법 알아보기
- 음성-텍스트 기능을 사용 하는 방법 알아보기

## <a name="instructions"></a>지침

### <a name="getting-started"></a>시작하기

1. Unity를 시작 하 고 새 프로젝트를 만듭니다. 프로젝트 이름을 "Speech SDK 학습 모듈입니다."를 입력 합니다. 프로젝트를 저장 하는 위치에 대 한 위치를 선택 합니다. "프로젝트 만들기." 클릭

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> 참고: 위의 이미지에 표시 된 대로 템플릿에 "3D에서"로 설정 되어 있는지 확인 합니다.

2. 다운로드 합니다 [혼합 현실 Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity 패키지를 PC의 폴더에 저장 합니다. Unity 프로젝트에 패키지를 가져옵니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 참조 하십시오 [기본 모듈입니다. 1 단원](mrlearning-base-ch1.md)합니다. 

3. 다운로드 하 여 Azure를 가져와야 [Speech SDK](https://aka.ms/csspeech/unitypackage) Unity 자산 패키지에 대 한 합니다. "자산을" 선택 "패키지 가져오기," 다음 "사용자 지정 패키지 있습니다."를 선택를 클릭 하 여 Speech SDK 패키지 가져오기 이전에 다운로드 한 Speech SDK 패키지를 검색 하 여 가져오기 프로세스를 시작 하려면 엽니다. 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. 다음 팝업 창에서 "가져오기" Speech SDK 패키지 가져오기를 시작 하려면 클릭 합니다. 아래 이미지에 나와 있는 것 처럼 모든 항목을 확인을 확인 합니다.

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. 다운로드 합니다 [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) 자산 패키지 있습니다. Lunarcom 자산 패키지는 실제로 Azure의 Speech SDK 사용을 보여 주기 위해 자산 및이 단원 시리즈에 대 한 개발 하는 스크립트 컬렉션입니다. 음성 명령을 터미널은 궁극적으로 개발 음력 모듈 어셈블리 환경과 상호 연결 되는 것은 [자료 모듈 자습서입니다.](mrlearning-base-ch6.md)
6. 혼합 현실 Toolkit 및 Speech SDK를 가져오는 데 비슷한 단계를 수행 하 여 Unity 프로젝트에 Lunarcom 자산 패키지를 가져옵니다.
7. 혼합된 현실 도구 키트 (MRTK)를 구성 합니다. 이 작업을 수행 하 여 창의 위쪽에서 "혼합 현실 Toolkit" 패널에서 클릭 한 다음 "장면 및 구성에 추가 합니다."를 선택

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. 장면은 이제 몇 가지 새 항목에는 MRTK에서 있습니다. "File"을 클릭 하 여 다른 이름으로 장면 저장 "다른 이름으로 저장"을 "SpeechScene" 장면 이름을 합니다. 

   > 참고: MRTK 프로젝트에 추가한 후 "실행" 모드로 전환 되지 않는 장면에 있는 재생 단추를 누르기를 Unity를 다시 시작 해야 합니다. 

9. 계층에서 선택한 "MixedRealityToolkit" 개체를 사용 하 여 검사기 패널에서 "복사 및 사용자 지정"을 클릭 합니다.

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. 또한 (계층에서 선택한 "MixedRealityToolkit" 개체)와 검사기 창에서 "사용 진단 System."는 오른쪽에 있는 확인란의 선택을 취소 하 여 진단 시스템 해제

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. 프로젝트 패널에서 "Lunarcom" 폴더를 확장 하 고 "Lunarcom_Base" prefab 계층으로 끕니다.

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. 계층의 "Lunarcom_Base" 개체를 선택 하 고 위치 x로 설정 되어 있는지 확인 합니다. = 0, y = 0 및 z = 0, x로 회전 뿐만 아니라 = 0, y = 0 및 z = 0. 눈금이 줄어 설정 x 0.008, = y 0.008, 및 z = = 0.01 합니다.

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. "구성 요소 추가" 클릭 합니다. 검색 하 고 "LunarcomController."를 선택 합니다. 이 스크립트는 6 단계에서에서 가져온 Lunarcom 자산 팩에 포함 됩니다.

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. 앱에서 Azure Cognitive Services에 연결 하려면 입력할 "구독 키" 라고도 "API 키" Speech Service에 대 한 합니다. 지침을 따르세요 [이 링크](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) 무료 구독 키를 확보 합니다. 구독 키를 가져온 후 입력 [관리자] 패널에 있는 "LunarcomController" 구성 "음성 서비스 API 키" 필드에 아래 그림과에서 같이 합니다.

15. 등록할 때 "LunarcomController" 구성 요소 검사기 패널에서 "음성 서비스 지역" 필드에 구독 키에 대 한 선택한 영역을 입력 합니다.

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. 계층의 왼쪽에 있는 화살표를 클릭 하 여 "Lunarcom_Base" 개체를 차례로 확장 한 후 아래 그림과에서 같이 "터미널" 해당 자식 개체에 대해 동일한 작업을 수행 합니다.

17. "Lunarcom_Base"를 선택한 상태에서 누르고 아래 이미지에 표시 된 대로 검사기 창에서 "Lunarcom" 계층 구조에서에서 텍스트를 "출력 텍스트" 슬롯 "LunarcomController" 구성 요소를 끕니다.
18. 이제 "터미널" 슬롯에 "Light 컨트롤러 연결" 슬롯 "Light 연결" 개체 "터미널" 개체를 사용 하 여 동일한 작업을 수행 합니다.

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. [관리자] 패널에서 "LunarcomController" 스크립트 "Lunarcom 단추" 섹션 옆의 화살표를 클릭 하 고 3으로 크기를 변경 또는 Return 키를 눌러 합니다. 이렇게 하면 세 개의 새로운 "Element" 필드 표시 합니다.

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. 계층에서 옆에 있는 화살표를 클릭 하 여 "Lunarcom 단추"를 확장 하 고 "LunarcomController" 구성 요소에서 각각의 요소 0, 1 및 2 참조로 Mic, 위성, 및 Rocket gameobject를 끌어 위와 동일한 프로세스를 사용 하 여 검사기 패널입니다. 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. 계층에서 "Lunarcom_Base" 개체를 선택 합니다. 검사기 창에서 "추가 구성 요소"를 클릭 합니다. 검색 하 고 "LunarcomWakeWordRecognizer."를 선택 합니다.

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. "Wake 단어" 슬롯에서 "Activate 터미널." 입력 또한 "해제 단어" 슬롯에서 "해제 터미널." 입력

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a>축하합니다.

Azure에서 구동 응용 프로그램에서 음성 인식 기능을 설정한! 모든 기능이 제대로 작동 하도록 응용 프로그램을 실행 합니다. 절전 모드 해제 마디 22, "활성화 터미널." 단계에서 입력 시작 그런 다음 음성 인식 시작 말하기를 시작 하는 마이크 단추를 선택 합니다. 당신은 말하면서 터미널에서 감정과 단어가 표시 됩니다. 음성 인식 하지 않도록 마이크 단추를 두 번 누릅니다. "해제 터미널" Lunarcom 터미널을 숨기려면 가정해 보겠습니다. 다음 단원에서는 Azure의 speech SDK HoloLens 2가 오프 라인으로 인해 사용할 수 없는 위치 하는 상황에 대 한 장치 기반 음성 인식을 사용 하 여 동적으로 전환 하는 방법을 알아보겠습니다.

[다음 단원: Speech SDK 단원 2](mrlearning-speechSDK-ch2.md)

