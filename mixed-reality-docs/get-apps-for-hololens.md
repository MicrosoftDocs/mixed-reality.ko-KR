---
title: HoloLens에 앱을 다운로드 합니다.
description: HoloLens, 테스트용으로 로드 및 Microsoft Store 통해 둘 다에 대 한 앱 설치를 설명합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 테스트용으로 로드, 테스트용 로드, 테스트용으로 로드, 저장소, uwp, 앱 설치
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597555"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="70b5d-104">HoloLens에 앱을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-104">Get apps for HoloLens</span></span>

<span data-ttu-id="70b5d-105">Windows 10 장치로 HoloLens HoloLens 위해 특별히 구축 된 새로운 앱 뿐만 아니라 앱 스토어에서 많은 기존 UWP 응용 프로그램을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="70b5d-106">이 기반으로 하려는 [개발](development-overview.md) 앱 또는 친구의 설치 및!</span><span class="sxs-lookup"><span data-stu-id="70b5d-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="70b5d-107">앱 설치</span><span class="sxs-lookup"><span data-stu-id="70b5d-107">Installing Apps</span></span>

<span data-ttu-id="70b5d-108">에 HoloLens에 새 앱을 설치 하는 방법은 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="70b5d-109">기본 방법은 새 응용 프로그램을 Windows 스토어에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="70b5d-110">장치 포털을 사용 하 여 사용자 고유의 응용 프로그램도 설치할 수는 있지만 또는 Visual Studio에서 배포 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="70b5d-111">Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="70b5d-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="70b5d-112">수행을 [블 룸](gestures.md#bloom) 제스처를 열려면 합니다 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="70b5d-113">스토어 앱을 선택 하 고 전 세계에이 타일을 배치할 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="70b5d-114">스토어 앱이 열리면 원하는 모든 응용 프로그램에 대 한 검색할 검색 표시줄을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="70b5d-115">선택 **가져옵니다** 또는 **설치** 응용 프로그램의 페이지 (제품을 구매 해야 할 수도 있습니다).</span><span class="sxs-lookup"><span data-stu-id="70b5d-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="70b5d-116">장치 포털을 사용 하 여 응용 프로그램 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="70b5d-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="70b5d-117">연결을 설정 [장치 포털](using-the-windows-device-portal.md) HoloLens 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="70b5d-118">로 이동 합니다 **앱** 왼쪽된 탐색 창에서 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="70b5d-119">아래 **앱 패키지** 응용 프로그램과 연결 된.appx 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="70b5d-120">연결 된 모든 종속성 및 인증서 파일을 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="70b5d-121">클릭 **이동**합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-121">Click **Go**.</span></span>

<span data-ttu-id="70b5d-122">![Windows Device Portal Microsoft HoloLens 앱 형식 설치](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="70b5d-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="70b5d-123">Windows Device Portal 사용 하 여 HoloLens에 앱을 설치 하려면</span><span class="sxs-lookup"><span data-stu-id="70b5d-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="70b5d-124">Microsoft Visual Studio 2015에서 배포</span><span class="sxs-lookup"><span data-stu-id="70b5d-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="70b5d-125">앱의 Visual Studio 솔루션 (.sln 파일)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="70b5d-126">프로젝트를 엽니다 **속성** 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="70b5d-127">다음 빌드 구성을 선택 합니다. 마스터/x86/원격 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="70b5d-128">원격 컴퓨터 선택 하면:</span><span class="sxs-lookup"><span data-stu-id="70b5d-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="70b5d-129">해야 주소 지점 HoloLens' WiFi IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="70b5d-130">유니버설 (암호화 되지 않은 프로토콜)로 인증을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="70b5d-131">솔루션을 빌드하십시오.</span><span class="sxs-lookup"><span data-stu-id="70b5d-131">Build your solution.</span></span>
6. <span data-ttu-id="70b5d-132">클릭 합니다 **원격 컴퓨터** 에 HoloLens 개발 PC에서에서 앱을 배포 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="70b5d-133">이미 있는 경우 기존 빌드에는 HoloLens, 다시이 최신 버전을 설치 하려면 예 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="70b5d-134">![Visual Studio에서 Microsoft HoloLens 앱에 대 한 원격 컴퓨터에 배포](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="70b5d-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="70b5d-135">응용 프로그램 설치를 자동으로 여 HoloLens에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="70b5d-135">The application will install and auto launch on your HoloLens.</span></span>
