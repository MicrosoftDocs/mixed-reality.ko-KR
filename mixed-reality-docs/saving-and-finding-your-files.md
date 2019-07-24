---
title: 파일 저장 및 찾기
description: HoloLens에서 파일을 찾고 저장 하 고 공유 하는 방법입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 방법, 파일 선택, 파일, 사진, 비디오, 그림, OneDrive, 저장소, 파일 탐색기
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524607"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="8bc15-104">파일 저장 및 찾기</span><span class="sxs-lookup"><span data-stu-id="8bc15-104">Saving and finding your files</span></span>

<span data-ttu-id="8bc15-105">파일은 다른 Windows 10 데스크톱 및 모바일 장치와 비슷한 방식으로 저장 및 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="8bc15-106">파일 탐색기 앱을 사용 하 여 로컬 폴더에 액세스</span><span class="sxs-lookup"><span data-stu-id="8bc15-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="8bc15-107">앱 자체 저장소 내에서</span><span class="sxs-lookup"><span data-stu-id="8bc15-107">Within an app's own storage</span></span>
* <span data-ttu-id="8bc15-108">특수 한 알려진 폴더 (예: 비디오 또는 음악 라이브러리)</span><span class="sxs-lookup"><span data-stu-id="8bc15-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="8bc15-109">앱 및 파일 선택 (예: OneDrive)을 포함 하는 저장소 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="8bc15-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="8bc15-110">MTP (미디어 전송 프로토콜) 지원을 통해 USB를 통해 HoloLens에 연결 된 데스크톱 PC 사용</span><span class="sxs-lookup"><span data-stu-id="8bc15-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="8bc15-111">파일 탐색기</span><span class="sxs-lookup"><span data-stu-id="8bc15-111">File Explorer</span></span>

<span data-ttu-id="8bc15-112">파일 탐색기 앱을 사용 하 여 HoloLens 내에서 파일을 이동 하 고 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="8bc15-113">파일 탐색기에 파일이 표시 되지 않으면 "최근" 필터가 활성화 되어 있을 수 있습니다 (왼쪽 창에 클록 아이콘이 강조 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="8bc15-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="8bc15-114">이 문제를 해결 하려면 왼쪽 창 (시계 아이콘 아래)에서 **이 장치** 문서 아이콘을 선택 하거나 메뉴를 열고 **이 장치**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="8bc15-115">앱 내의 파일</span><span class="sxs-lookup"><span data-stu-id="8bc15-115">Files within an app</span></span>

<span data-ttu-id="8bc15-116">응용 프로그램이 장치에 파일을 저장 하는 경우 해당 응용 프로그램을 사용 하 여 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="8bc15-117">내 사진/동영상은 어디에 있나요?</span><span class="sxs-lookup"><span data-stu-id="8bc15-117">Where are my photos/videos?</span></span>

<span data-ttu-id="8bc15-118">[혼합 현실 캡처](mixed-reality-capture.md) 사진과 비디오는 장치의 카메라 롤 폴더에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="8bc15-119">이러한 [앱은 사진 앱](see-your-photos.md#photos-app)을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="8bc15-120">사진 앱을 사용 하 여 사진과 비디오를 OneDrive에 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="8bc15-121">[Windows 장치 포털](using-the-windows-device-portal.md#mixed-reality-capture)의 혼합 현실 캡처 페이지를 통해 사진과 비디오에 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="8bc15-122">다른 앱에서 파일 요청</span><span class="sxs-lookup"><span data-stu-id="8bc15-122">Requesting files from another app</span></span>

<span data-ttu-id="8bc15-123">응용 프로그램은 파일 [선택기](app-model.md#file-pickers)를 통해 파일을 저장 하거나 다른 앱에서 파일을 열도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="8bc15-124">알려진 폴더</span><span class="sxs-lookup"><span data-stu-id="8bc15-124">Known folders</span></span>

<span data-ttu-id="8bc15-125">HoloLens는 앱이 액세스 권한을 요청할 수 있는 많은 [알려진 폴더](app-model.md#known-folders) 를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="8bc15-126">서비스의 파일</span><span class="sxs-lookup"><span data-stu-id="8bc15-126">Files in a service</span></span>

<span data-ttu-id="8bc15-127">서비스에 파일을 저장 하거나 액세스 하려면 서비스와 연결 된 앱을 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="8bc15-128">OneDrive에서 파일에 파일을 저장 하 고이 파일에 액세스 하려면 [onedrive 앱](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)을 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="8bc15-129">MTP (미디어 전송 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="8bc15-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="8bc15-130">다른 모바일 장치와 마찬가지로, HoloLens를 데스크톱 PC에 연결 하 고, PC에서 파일 탐색기를 열어 간편 하 게 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="8bc15-131">되었을</span><span class="sxs-lookup"><span data-stu-id="8bc15-131">Clarifications</span></span>

* <span data-ttu-id="8bc15-132">HoloLens는 외부 하드 드라이브 또는 SD 카드에 연결 하는 기능을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="8bc15-133">[Hololens 용 Windows 10 4 월 2018 업데이트 (RS4)](release-notes-april-2018.md)를 기준으로 hololens는 장치에서 파일을 저장 하 고 관리 하는 파일 탐색기를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="8bc15-134">파일 탐색기를 추가 하면 파일 선택기를 선택할 수 있습니다. 예를 들어 파일을 장치 또는 OneDrive에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc15-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
