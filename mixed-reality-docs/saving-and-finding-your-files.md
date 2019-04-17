---
title: 저장 하 고 파일을 찾는
description: 찾기, 저장 및 HoloLens에 파일을 공유 하는 방법.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 방법, 파일 선택기, 파일, 사진, 비디오, 그림, OneDrive, 저장소, 파일 탐색기
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602685"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="7a116-104">저장 하 고 파일을 찾는</span><span class="sxs-lookup"><span data-stu-id="7a116-104">Saving and finding your files</span></span>

<span data-ttu-id="7a116-105">파일 저장 및 다른 Windows 10 Desktop 및 모바일 장치에 비슷한 방식으로 관리할 수 있습니다:</span><span class="sxs-lookup"><span data-stu-id="7a116-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="7a116-106">파일 탐색기 앱을 사용 하 여 로컬 폴더에 액세스</span><span class="sxs-lookup"><span data-stu-id="7a116-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="7a116-107">앱 자체의 저장소를 내</span><span class="sxs-lookup"><span data-stu-id="7a116-107">Within an app's own storage</span></span>
* <span data-ttu-id="7a116-108">특수 한 알려진 폴더 (예: 비디오 또는 음악 라이브러리)</span><span class="sxs-lookup"><span data-stu-id="7a116-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="7a116-109">앱과 파일 선택 (예: OneDrive)을 포함 하는 저장소 서비스를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="7a116-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="7a116-110">MTP (미디어 전송 프로토콜) 지원을 통해 USB 통해 여 HoloLens에 연결 된 pc는 데스크톱 PC를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="7a116-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="7a116-111">파일 탐색기</span><span class="sxs-lookup"><span data-stu-id="7a116-111">File Explorer</span></span>

<span data-ttu-id="7a116-112">이동 및 HoloLens 내에서 파일을 삭제 하려면 파일 탐색기 앱을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="7a116-113">"최근" 필터를 찾을 수 없으면 파일 탐색기에서 파일을 활성화할 수 있습니다 (시계 아이콘은 왼쪽된 창에서 강조 표시).</span><span class="sxs-lookup"><span data-stu-id="7a116-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="7a116-114">이 해결 하려면 선택 합니다 **이 장치** (아래에 있는 시계 아이콘)을 왼쪽된 창에서 아이콘을 문서 또는 메뉴를 열고 선택 **이 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="7a116-115">앱 내에서 파일</span><span class="sxs-lookup"><span data-stu-id="7a116-115">Files within an app</span></span>

<span data-ttu-id="7a116-116">응용 프로그램 장치에서 파일을 저장 하는 경우 해당 응용 프로그램 액세스 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="7a116-117">내 사진/비디오 위치?</span><span class="sxs-lookup"><span data-stu-id="7a116-117">Where are my photos/videos?</span></span>

<span data-ttu-id="7a116-118">[혼합 현실 캡처](mixed-reality-capture.md) 사진 및 비디오 장치의 카메라 앨범 폴더에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="7a116-119">통해 액세스할 수 있습니다 이러한 합니다 [Photos 앱](see-your-photos.md#photos-app)합니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="7a116-120">사진 및 비디오 OneDrive 동기화 할 사진 앱을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="7a116-121">사진 및 동영상의 혼합 현실 캡처 페이지를 통해 액세스할 수도 있습니다는 [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)합니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="7a116-122">다른 앱에서 요청 파일</span><span class="sxs-lookup"><span data-stu-id="7a116-122">Requesting files from another app</span></span>

<span data-ttu-id="7a116-123">응용 프로그램을 통해 다른 앱에서 파일을 열거나 파일을 저장 하도록 요청할 수 있습니다 [선택기 파일](app-model.md#file-pickers)합니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="7a116-124">알려진된 폴더</span><span class="sxs-lookup"><span data-stu-id="7a116-124">Known folders</span></span>

<span data-ttu-id="7a116-125">많은 지원 하며, HoloLens [폴더를 알려진](app-model.md#known-folders) 앱에 대 한 액세스 권한을 요청할 수 있다는입니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="7a116-126">서비스에서 파일</span><span class="sxs-lookup"><span data-stu-id="7a116-126">Files in a service</span></span>

<span data-ttu-id="7a116-127">파일을 저장 합니다 (또는 파일에 액세스) 서비스를 서비스에 연결 된 앱 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="7a116-128">파일을 저장 하 고 OneDrive에서 파일에 액세스를 위해 설치 해야 합니다 [OneDrive 앱](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)합니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="7a116-129">MTP (미디어 전송 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="7a116-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="7a116-130">다른 모바일 장치와 마찬가지로 HoloLens 데스크톱 PC에 연결 하 고 쉽게 전송 HoloLens 라이브러리 (사진, 비디오, 문서)에 액세스 하려면 PC에서 파일 탐색기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="7a116-131">확인</span><span class="sxs-lookup"><span data-stu-id="7a116-131">Clarifications</span></span>

* <span data-ttu-id="7a116-132">HoloLens 외부 하드 드라이브나 SD 카드에 연결 하는 것을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="7a116-133">[Windows 10 2018 년 4 월 업데이트 (RS4) HoloLens에 대 한](release-notes-april-2018.md), HoloLens 저장 및 관리 장치에서 파일에 대 한 파일 탐색기를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="7a116-134">파일 탐색기의 추가 파일 선택기 (예를 들어 파일을 저장 하는 장치 또는 OneDrive)을 선택 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a116-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
