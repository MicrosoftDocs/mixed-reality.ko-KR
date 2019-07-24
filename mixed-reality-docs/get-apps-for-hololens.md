---
title: HoloLens 용 앱 가져오기
description: Microsoft Store 및 테스트용 로드를 통해 HoloLens 용 앱을 설치 하는 방법을 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 테스트용으로 로드, side load, 테스트용 로드, 스토어, uwp, 앱, 설치
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522542"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="5f8a8-104">HoloLens 용 앱 가져오기</span><span class="sxs-lookup"><span data-stu-id="5f8a8-104">Get apps for HoloLens</span></span>

<span data-ttu-id="5f8a8-105">Windows 10 장치는 hololens를 위해 특별히 빌드된 새로운 앱 뿐만 아니라 앱 스토어에서 많은 기존 UWP 응용 프로그램을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="5f8a8-106">이러한 앱을 기반으로 자신의 앱 또는 친구의 앱을 [개발](development-overview.md) 하 고 설치 하는 것도 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="5f8a8-107">앱 설치</span><span class="sxs-lookup"><span data-stu-id="5f8a8-107">Installing Apps</span></span>

<span data-ttu-id="5f8a8-108">HoloLens에 새 앱을 설치 하는 방법에는 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="5f8a8-109">기본 방법은 Windows 스토어에서 새 응용 프로그램을 설치 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="5f8a8-110">그러나 장치 포털을 사용 하거나 Visual Studio에서 배포 하 여 응용 프로그램을 직접 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="5f8a8-111">Microsoft Store에서</span><span class="sxs-lookup"><span data-stu-id="5f8a8-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="5f8a8-112">[블 룸](gestures.md#bloom) 제스처를 수행 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="5f8a8-113">스토어 앱을 선택 하 고 탭 하 여이 타일을 전 세계에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="5f8a8-114">스토어 앱이 열리면 검색 표시줄을 사용 하 여 원하는 응용 프로그램을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="5f8a8-115">응용 프로그램의 페이지에서 **가져오기** 또는 **설치** 를 선택 합니다 (구매가 필요할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="5f8a8-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="5f8a8-116">장치 포털을 사용 하 여 응용 프로그램 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="5f8a8-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="5f8a8-117">[장치 포털](using-the-windows-device-portal.md) 에서 대상 HoloLens로의 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="5f8a8-118">왼쪽 탐색 영역에서 **앱** 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="5f8a8-119">**앱 패키지** 아래에서 응용 프로그램과 연결 된 .appx 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="5f8a8-120">연결 된 종속성 및 인증서 파일을 모두 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="5f8a8-121">**찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-121">Click **Go**.</span></span>

<span data-ttu-id="5f8a8-122">![Microsoft HoloLens의 Windows 장치 포털에서 앱 양식 설치](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="5f8a8-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="5f8a8-123">Windows 장치 포털을 사용 하 여 HoloLens에 앱 설치</span><span class="sxs-lookup"><span data-stu-id="5f8a8-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="5f8a8-124">Microsoft Visual Studio 2015에서 배포</span><span class="sxs-lookup"><span data-stu-id="5f8a8-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="5f8a8-125">앱의 Visual Studio 솔루션 (.sln 파일)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="5f8a8-126">프로젝트의 **속성** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="5f8a8-127">다음 빌드 구성을 선택 합니다. Master/x86/원격 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="5f8a8-128">원격 컴퓨터를 선택 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="5f8a8-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="5f8a8-129">주소가 HoloLens의 WiFi IP 주소를 가리키는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="5f8a8-130">인증을 유니버설 (암호화 되지 않은 프로토콜)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="5f8a8-131">솔루션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-131">Build your solution.</span></span>
6. <span data-ttu-id="5f8a8-132">**원격 컴퓨터** 단추를 클릭 하 여 개발 PC에서 HoloLens에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="5f8a8-133">HoloLens에 기존 빌드가 이미 있는 경우 예를 선택 하 여이 최신 버전을 다시 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="5f8a8-134">![Visual Studio에서 Microsoft HoloLens로 앱에 대 한 원격 컴퓨터 배포](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="5f8a8-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="5f8a8-135">응용 프로그램이 설치 되 고 HoloLens에 자동 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f8a8-135">The application will install and auto launch on your HoloLens.</span></span>
