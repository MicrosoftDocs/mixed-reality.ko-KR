---
title: 4. 대화형 장면 만들기
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서 시리즈 4/6부
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: a9de5755ab86c96322a8d50fecd7ba2cdea866d3
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330220"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="2b923-104">4. 대화형 장면 만들기</span><span class="sxs-lookup"><span data-stu-id="2b923-104">4. Making your scene interactive</span></span>

## <a name="overview"></a><span data-ttu-id="2b923-105">개요</span><span class="sxs-lookup"><span data-stu-id="2b923-105">Overview</span></span>

<span data-ttu-id="2b923-106">이전 자습서에서는 ARSession, 폰 및 Game 모드를 추가하여 체스 앱에 대한 혼합 현실 설정을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-106">In the previous tutorial you added an ARSession, Pawn, and Game Mode to complete the mixed reality setup for the chess app.</span></span> <span data-ttu-id="2b923-107">이 섹션에서는 조작 장면을 만들 수 있는 도구를 제공하는 오픈 소스 [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)의 사용에 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-107">This section focuses on using the open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) plugin, which provides tools to make the scene interactive.</span></span> <span data-ttu-id="2b923-108">이 섹션의 끝부분에서는 사용자 입력을 통해 체스 말을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-108">By the end of this section you'll be able to move the chess pieces with user input.</span></span> 

## <a name="objectives"></a><span data-ttu-id="2b923-109">목표</span><span class="sxs-lookup"><span data-stu-id="2b923-109">Objectives</span></span>

* <span data-ttu-id="2b923-110">Mixed Reality Toolkit UX Tools 플러그 인 다운로드</span><span class="sxs-lookup"><span data-stu-id="2b923-110">Downloading the Mixed Reality Toolkit UX Tools plugin</span></span> 
* <span data-ttu-id="2b923-111">손가락 끝에 손 조작 행위자 추가</span><span class="sxs-lookup"><span data-stu-id="2b923-111">Adding Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="2b923-112">장면의 개체에 조작자 만들기 및 추가</span><span class="sxs-lookup"><span data-stu-id="2b923-112">Creating and adding Manipulators to objects in the scene</span></span>
* <span data-ttu-id="2b923-113">입력 시뮬레이션을 사용하여 프로젝트의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="2b923-113">Using input simulation to validate the project</span></span>

## <a name="downloading-the-mrtk-ux-tools-plugin"></a><span data-ttu-id="2b923-114">MRTK UX Tools 플러그 인 다운로드</span><span class="sxs-lookup"><span data-stu-id="2b923-114">Downloading the MRTK UX Tools plugin</span></span>
<span data-ttu-id="2b923-115">사용자 입력 작업을 시작하기 전에 프로젝트에 플러그 인을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-115">Before you start working with user input, you'll need to add the plugin to the project.</span></span>

1.  <span data-ttu-id="2b923-116">[GitHub 리포지토리](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)에서 최신 MRTK UX Tools 플러그 인을 복제하거나 다운로드하고 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-116">Clone or download the latest MRTK UX Tools plugin from the [GitHub repository](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) and unzip the file.</span></span>

2.  <span data-ttu-id="2b923-117">프로젝트 루트 폴더에 이름이 **Plugins**인 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-117">Create a new folder called **Plugins** in the root folder of the project.</span></span> <span data-ttu-id="2b923-118">압축을 푼 UXTools 플러그 인을 이 폴더에 복사하고 Unreal 편집기를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-118">Copy the unzipped UXTools plugin into this folder and restart the Unreal editor.</span></span> 

![프로젝트 플러그 인 폴더 만들기](images/unreal-uxt/4-plugins.PNG)

3.  <span data-ttu-id="2b923-120">UXTools 플러그 인에는 **Pointers**, **Input Simulation**, **Simple Button** 등의 하위 폴더가 있는 Content 폴더와, 함수로 구분된 C++ Classes 폴더가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-120">The UXTools plugin has a Content folder with subfolders for **Pointers**, **Input Simulation**, and **Simple Button**, as well as a C++ Classes folder separated by function.</span></span>  

> [!NOTE]
> <span data-ttu-id="2b923-121">**콘텐츠 브라우저**에 **UXTools 콘텐츠** 섹션이 표시되지 않는 경우 **보기 옵션 > 플러그 인 콘텐츠**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-121">If you don’t see the **UXTools Content** section in the **Content Browser**, click **View Options > Show Plugin Content**.</span></span> 

![플러그 인 콘텐츠 표시](images/unreal-uxt/4-showplugincontent.PNG)

<span data-ttu-id="2b923-123">플러그 인이 무사히 설치되면 직접 조작 행위자부터, 제공하는 도구를 사용할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-123">With the plugin safely installed, you're ready to start using the tools it has to offer, starting with hand interaction actors.</span></span>

## <a name="spawning-hand-interaction-actors"></a><span data-ttu-id="2b923-124">손 조작 행위자 생성</span><span class="sxs-lookup"><span data-stu-id="2b923-124">Spawning Hand Interaction Actors</span></span>
<span data-ttu-id="2b923-125">UX 요소에서의 손 조작은 인접 및 원거리 조작을 위한 포인터와 시각적 개체를 만들어 구동하는 손 조작 행위자를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-125">Hand interaction with UX elements is performed with Hand Interaction Actors, which create and drive the pointers and visuals for near and far interactions.</span></span>
- <span data-ttu-id="2b923-126">*인접 조작*은 집게와 엄지 손가락으로 요소를 집어서, 또는 손끝으로 찔러서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-126">*Near interactions* are performed by pinching elements between index finger and thumb or by poking them with a fingertip.</span></span> 
- <span data-ttu-id="2b923-127">*원거리 조작*은 요소에 있는 가상 손으로부터 나가는 광선을 가리키고 검지와 엄지를 한꺼번에 눌러서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-127">*Far interactions* are performed by pointing a ray from the virtual hand at an element and pressing index and thumb together.</span></span>

<span data-ttu-id="2b923-128">여기서는 **MRPawn**에 손 상호 작용 행위자를 추가하면 다음 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-128">In our case, adding a Hand Interaction Actor to **MRPawn** will:</span></span>
- <span data-ttu-id="2b923-129">폰의 집게 손가락 끝에 커서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-129">Add a cursor to the tips of the Pawn’s index fingers.</span></span>
- <span data-ttu-id="2b923-130">폰을 통해 조작할 수 있는 관절식 손 입력 이벤트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-130">Provide articulated hand input events that can be manipulated through the Pawn.</span></span>
- <span data-ttu-id="2b923-131">가상 손의 손바닥에서부터 나오는 손 광선을 통해 원거리 조작 입력 이벤트를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-131">Allow far interaction input events through hand rays extending from the palms of the virtual hands.</span></span>

<span data-ttu-id="2b923-132">이러한 콘셉트 홈을 구동하려면 계속하기 전에 [설명서](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md)의 손 조작 부분을 읽어 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-132">In order to drive these concepts home, you're encouraged to read through the [documentation](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md) on hand interactions before continuing.</span></span> 

<span data-ttu-id="2b923-133">준비되면 **MRPawn** 청사진을 열고 **이벤트 그래프**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-133">Once you're ready, open the **MRPawn** Blueprint and go to the **Event Graph**.</span></span> 

1. <span data-ttu-id="2b923-134">**Event BeginPlay**에서 실행 핀을 끌어다 놓아 새 노드를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-134">Drag and release the execution pin from **Event BeginPlay** to place a new node.</span></span> 
    * <span data-ttu-id="2b923-135">**클래스에서 행위자 생성**을 선택하고 **클래스** 핀 옆에 있는 드롭다운을 클릭한 다음, **Uxt 손 조작 행위자**를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-135">Select **Spawn Actor from Class**, click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span> 

2. <span data-ttu-id="2b923-136">**SpawnActor Uxt 손 조작** 노드에서 실행 핀을 끌어다 놓고 **Uxt 손 조작 행위자** 클래스에서 **손 설정** 함수를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-136">Drag and release the execution pin from the **SpawnActor Uxt Hand Interaction** node and search for the **Set Hand** function in the **Uxt Hand Interaction Actor** class.</span></span> 
    * <span data-ttu-id="2b923-137">**SpawnActor** 노드의 **반환 값**을 **손 설정** 노드의 **대상 핀**에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-137">Connect the **SpawnActor** node’s **Return Value** to the **Target** pin of the **Set Hand** node.</span></span> <span data-ttu-id="2b923-138">이렇게 하면 손 조작 행위자의 손이 **왼쪽**으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-138">This sets the hand of the Hand Interaction Actor to **Left**.</span></span> 

3. <span data-ttu-id="2b923-139">두 번째 **Uxt 손 조작 행위자**를 생성합니다. 이번에는 손을 **오른쪽**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-139">Spawn a second **Uxt Hand Interaction Actor**, this time setting the hand to **Right**.</span></span> <span data-ttu-id="2b923-140">이벤트가 시작되면 각각의 손에 Uxt 손 조작 행위자가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-140">When the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span> 

<span data-ttu-id="2b923-141">**이벤트 그래프**는 다음 스크린샷과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-141">Your **Event Graph** should match the following screenshot:</span></span>

![UXT 손 조작 행위자 생성](images/unreal-uxt/4-spawnactor.PNG)

<span data-ttu-id="2b923-143">Uxt 손 조작 행위자에는 소유자와 최초 변환 위치가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-143">Both Uxt Hand Interaction Actors need owners and initial transform locations.</span></span> <span data-ttu-id="2b923-144">손 조작 행위자는 표시되는 즉시 가상 손으로 이동하므로(이 동작이 UX Tools 플러그 인에 포함됨) 최초 변환은 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-144">The initial transform  doesn’t matter since the Hand Interaction Actors will jump to the virtual hands as soon as they're visible (this behavior is included in the UX Tools plugin).</span></span> <span data-ttu-id="2b923-145">그러나 컴파일러 오류를 방지하려면 `SpawnActor` 함수에 변환 입력이 필요하므로 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-145">However, the `SpawnActor` function requires a Transform input to avoid a compiler error, so you'll use the default values.</span></span> 

1. <span data-ttu-id="2b923-146">**변환 생성** 핀 중 하나를 끌어다 놓아 새 노드를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-146">Drag and release the pin off one of the **Spawn Transform** pins to place a new node.</span></span> 
    * <span data-ttu-id="2b923-147">**변환** 노드를 검색한 다음, **반환 값**을 다른 손의 **변환 생성**으로 끌어 **SpawnActor** 노드가 모두 연결되게 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-147">Search for the **Make Transform** node, then drag the **Return Value** to the other hand’s **Spawn Transform** so that both **SpawnActor** nodes are connected.</span></span> 

3.  <span data-ttu-id="2b923-148">두 **SpawnActor** 노드의 하단에서 **아래쪽 화살표**를 클릭하여 **소유자** 핀을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-148">Click the **down arrow** at the bottom of both **SpawnActor** nodes to reveal the **Owner** pin.</span></span>    
    * <span data-ttu-id="2b923-149">**소유자** 핀 중 하나를 새 노드로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-149">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span> 
    * <span data-ttu-id="2b923-150">**자체**를 검색하고 **자체에 참조 가져오기** 변수를 선택한 다음, **자체** 개체 참조 노드와 다른 손 조작 행위자의 **소유자** 핀 사이에 링크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-150">Search for **self** and select the **Get a reference to self** variable, then create a link between the **Self** object reference node and the other Hand Interaction Actor’s **Owner** pin.</span></span> 
    * <span data-ttu-id="2b923-151">**컴파일**하고, **저장**하고, 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-151">**Compile**, **save**, and return to the Main window.</span></span> 

<span data-ttu-id="2b923-152">연결이 다음 스크린샷과 일치하는지 확인합니다. 그러나 노드 주변을 자유롭게 끌어 청사진의 가독성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-152">Make sure the connections match the following screenshot, but feel free to drag around nodes to make your Blueprint more readable</span></span>

![UXT 손 조작 행위자 설정 완료](images/unreal-uxt/4-fingerptrs.PNG) 

<span data-ttu-id="2b923-154">MRTK UX Tools 플러그 인에서 제공하는 손 조작 행위자에 대한 자세한 내용은 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-154">You can find more information about the Hand Interaction Actor provided in the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html).</span></span>

<span data-ttu-id="2b923-155">이제 프로젝트의 가상 손이 개체를 선택할 수 있게 되었지만 아직은 조작하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-155">Now the virtual hands in the project have a way of selecting objects, but they still can't manipulate them.</span></span> <span data-ttu-id="2b923-156">앱을 테스트 하기 전의 마지막 작업은 장면의 행위자에 조작자 구성 요소를 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-156">Your last task before testing the app is to add Manipulator components to the actors in the scene.</span></span>

## <a name="attaching-manipulators"></a><span data-ttu-id="2b923-157">조작자 연결</span><span class="sxs-lookup"><span data-stu-id="2b923-157">Attaching Manipulators</span></span>

<span data-ttu-id="2b923-158">조작자는 관절식 손 입력에 응답하고 잡기, 회전 및 전환이 가능한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-158">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated.</span></span> <span data-ttu-id="2b923-159">조작자의 변환을 행위자의 변환에 적용하면 직접 행위자 조작이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-159">Applying the Manipulator’s transform to an Actors transform allows direct Actor manipulation.</span></span> 

1. <span data-ttu-id="2b923-160">**Board** 블루프린트에서 **구성 요소 추가**를 클릭하고 **구성 요소** 패널에서 **Uxt 일반 조작자**를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-160">Open the **Board** blueprint, click **Add Component** and search for **Uxt Generic Manipulator** in the **Components** panel.</span></span>

![일반 조작자 추가](images/unreal-uxt/4-addmanip.PNG)

2. <span data-ttu-id="2b923-162">**세부 정보** 패널에서 **일반 조작자** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-162">Expand the **Generic Manipulator** section in the **Details** panel.</span></span> <span data-ttu-id="2b923-163">한손 또는 양손 조작, 회전 모드를 설정하고 여기서부터 다듬기를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-163">You can set one-handed or two-handed manipulation, rotation mode, and smoothing from here.</span></span> <span data-ttu-id="2b923-164">원하는 모두를 자유롭게 선택한 다음, 보드를 **컴파일**하고 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-164">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span> 

![모드 설정](images/unreal-uxt/4-setrotmode.PNG)

3. <span data-ttu-id="2b923-166">**WhiteKing** 행위자에 대해 위의 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-166">Repeat the steps above for the **WhiteKing** Actor.</span></span>

<span data-ttu-id="2b923-167">MRTK UX Tools 플러그 인에서 제공하는 조작자 구성 요소에 대한 자세한 내용은 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-167">You can find more information about the Manipulator Components provided in the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html).</span></span>

## <a name="testing-the-scene"></a><span data-ttu-id="2b923-168">장면 테스트</span><span class="sxs-lookup"><span data-stu-id="2b923-168">Testing the scene</span></span>
<span data-ttu-id="2b923-169">모든 것이 마무리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-169">Good news everyone!</span></span> <span data-ttu-id="2b923-170">이제 새 가상 손과 사용자 입력으로 앱을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-170">You're ready to test out the app with its new virtual hands and user input.</span></span> <span data-ttu-id="2b923-171">주 창에서 **재생**을 누르면 MRTK UX Tools 플러그 인에서 제공하는 두 개의 메시 손이 나타나고, 각 손바닥에서 손 광선이 나가는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-171">Press **Play** in the Main Window and you'll see two mesh hands provided by the MRTK UX Tools plugin with hand rays extending from each hand’s palm.</span></span> <span data-ttu-id="2b923-172">다음과 같이 손과 조작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-172">You can control the hands and their interactions as follows:</span></span>
- <span data-ttu-id="2b923-173">**왼쪽 Alt** 키를 누른 상태로 **왼손**을, **왼쪽 Shift** 키를 누른 상태로 **오른손**을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-173">Hold down the **left Alt** key to control the **left hand** and the **left Shift** key to control the **right hand**.</span></span> 
- <span data-ttu-id="2b923-174">마우스를 움직여 손을 움직이고 **마우스 휠**을 스크롤하여 손을 **앞으로** 또는 **뒤로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-174">Move your mouse to move the hand and scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span> 
- <span data-ttu-id="2b923-175">마우스 왼쪽 단추를 클릭하면 **손가락 모으기** 동작이 수행되고, 마우스 가운데 단추를 클릭하면 **찌르기** 동작이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-175">Click the left mouse button to **pinch**, click the middle mouse button to **poke**.</span></span> 

![뷰포트의 시뮬레이션된 손](images/unreal-uxt/4-handsim.PNG)

<span data-ttu-id="2b923-177">시뮬레이션된 손을 사용하여 백의 체스 킹을 집어서 움직여 본 후 다시 내려놓고 보드를 조작해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-177">Try using the simulated hands to pick up, move, and set down the white chess king and manipulate the board!</span></span> <span data-ttu-id="2b923-178">근거리 및 원거리 조작을 시험해 보세요. 체스 보드와 킹을 직접 잡을 수 있을 만큼 손이 가까워지면 손에서 나가는 손 광선이 사라지고 검지손가락 끝에 있는 손가락 커서로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-178">Experiment with both near and far interaction - notice that when your hands get close enough to grab the board and king directly, the hand ray disappears and is replaced with a finger cursor at the tip of the index finger.</span></span> 

<span data-ttu-id="2b923-179">MRTK UX Tools 플러그 인에서 제공하는 시뮬레이션된 손 기능에 대한 자세한 내용은 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-179">You can find more information about the simulated hands feature provided by the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html).</span></span>

<span data-ttu-id="2b923-180">이제 가상 손이 개체와 상호 작용할 수 있으므로 다음 자습서를 진행하여 사용자 인터페이스와 이벤트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b923-180">Now that your virtual hands can interact with objects, you're ready to move on to the next tutorial and add user interfaces and events.</span></span>

[<span data-ttu-id="2b923-181">다음 섹션: 5. 단추 추가 및 조각 위치 재설정</span><span class="sxs-lookup"><span data-stu-id="2b923-181">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
