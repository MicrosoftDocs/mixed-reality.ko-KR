---
title: Holographic 원격을 사용 하 여 보안 연결 설정
description: 이 페이지에서는 Holographic Remoting을 사용할 때 암호화 된 보안 연결을 설정 하는 방법을 설명 합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278231"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a><span data-ttu-id="6ae71-104">Holographic 원격을 사용 하 여 보안 연결 설정</span><span class="sxs-lookup"><span data-stu-id="6ae71-104">Establishing a secure connection with Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="6ae71-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="6ae71-106">이 페이지에서는 Holographic Remoting을 사용할 때 암호화 된 보안 연결을 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-106">This page explains how to establish a secure encrypted connection when using Holographic Remoting.</span></span>

<span data-ttu-id="6ae71-107">개방형 WiFi 또는 인터넷과 같은 안전 하지 않은 네트워크를 통해 HoloLens 2로 콘텐츠를 스트리밍하는 경우 암호화 된 연결을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-107">When streaming content to HoloLens 2 over a insecure Network such as an open WiFi or the internet it is highly recommended to use an encrypted connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="6ae71-108">암호화 된 연결을 사용 하는 신뢰할 수 있는 로컬 WiFi를 사용 하는 경우에도 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-108">Even when using a trusted local WiFi using an encrypted connection should be considered.</span></span>

<span data-ttu-id="6ae71-109">암호화 된 연결을 사용할 수 있으려면 [사용자 지정 플레이어](holographic-remoting-create-player.md) 와 [사용자 지정 원격 앱](holographic-remoting-create-host.md)을 모두 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-109">To be able to use a encrypted connection you will need to implement both a [custom player](holographic-remoting-create-player.md) and a [custom remote app](holographic-remoting-create-host.md).</span></span>

<span data-ttu-id="6ae71-110">기본 플랫폼 TLS 구현을 사용 하 여 암호화를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-110">The encryption is achieved by using the underlying platforms TLS implementation.</span></span>

## <a name="basics-of-an-encrypted-connection"></a><span data-ttu-id="6ae71-111">암호화 된 연결의 기본 사항</span><span class="sxs-lookup"><span data-stu-id="6ae71-111">Basics of an encrypted connection</span></span>

<span data-ttu-id="6ae71-112">인증서 교환을 허용 하려면 다음 개체를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-112">The following objects need to be implemented to allow for a certificate exchange.</span></span>

>[!TIP]
><span data-ttu-id="6ae71-113">WinRT 인터페이스 구현은/Winrt. 사용 C++하 여 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-113">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="6ae71-114">[/Sd를 사용 C++하는 작성자 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 장에서는이에 대해 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-114">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="6ae71-115">NuGet 패키지 내의 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```에는 보안 연결과 관련 된 API에 대 한 자세한 설명서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-115">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

1) <span data-ttu-id="6ae71-116">```ICertificate``` 인터페이스를 구현 해야 하는 인증서 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-116">A certificate object, which needs to implement the ```ICertificate``` interface.</span></span>

    * <span data-ttu-id="6ae71-117">```GetCertificatePfx``` 메서드를 통해 pfx 인증서의 이진 콘텐츠를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-117">Return the binary contents of the pfx certificate through the ```GetCertificatePfx``` method.</span></span> <span data-ttu-id="6ae71-118">.Pfx 파일의 이진 콘텐츠와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-118">Same as the binary contents of a .pfx file.</span></span>
    * <span data-ttu-id="6ae71-119">```GetSubjectName```를 통해 인증서 주체 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-119">Return the certificate subject name through ```GetSubjectName```.</span></span>
    * <span data-ttu-id="6ae71-120">```GetPfxPassword```를 통해 pfx 암호를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-120">Return the pfx password through ```GetPfxPassword```.</span></span> <span data-ttu-id="6ae71-121">보호 되지 않는 pfx에 대해 빈 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-121">Return an empty string for an unprotected pfx.</span></span>

2) <span data-ttu-id="6ae71-122">```GetCertificate``` 메서드를 통해 요청 될 때 인증서를 제공 하는 ```ICertificateProvider``` 인터페이스를 구현 하는 인증서 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-122">A certificate provider implementing the ```ICertificateProvider``` interface which provides a certificate when asked through the ```GetCertificate``` method.</span></span>

3) <span data-ttu-id="6ae71-123">```ICertificateValidator``` 인터페이스를 구현 하는 인증서 유효성 검사기입니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-123">A certificate validator implementing the ```ICertificateValidator``` interface.</span></span> <span data-ttu-id="6ae71-124">해당 작업은 들어오는 인증서를 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-124">Its task is to verify incoming certificates.</span></span>
    * <span data-ttu-id="6ae71-125">```PerformSystemValidation``` 메서드는 기본 플랫폼에서 들어오는 인증서 체인의 유효성을 검사 해야 하는 경우 ```true```을 반환 합니다. 그렇지 않으면 ```false``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-125">The ```PerformSystemValidation``` method should return ```true``` when the underlying platform should validate the incoming certificate chain, ```false``` otherwise.</span></span>
    * <span data-ttu-id="6ae71-126">```ValidateCertificate```는 인증서의 유효성 검사를 요청 하기 위해 클라이언트 컨텍스트에서 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-126">```ValidateCertificate``` is called by the client context to request validation of a certificate.</span></span> <span data-ttu-id="6ae71-127">이 메서드는 인증서 체인 (주체 인증서가 있는 첫 번째 인증서 포함), 연결이 설정 되는 서버의 이름 및 해지 검사 강제 적용 여부를 수락 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-127">This method accepts the certificate chain (with the first certificate being the subject certificate), the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="6ae71-128">기본 시스템에서 유효성 검사를 요청한 경우 시스템 유효성 검사 결과가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-128">The system validation result will be provided if validation by the underlying system has been requested.</span></span> <span data-ttu-id="6ae71-129">적절 한 결과 나 ```Cancel``` 유효성 검사를 취소 하는 ```CertificateValidated```를 계속 처리 하려면 전달 된 ```ICertificateValidationCallback```에서 유효성 검사를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-129">To continue processing either ```CertificateValidated``` with the appropriate result or ```Cancel``` to cancel validation needs to be called on the passed ```ICertificateValidationCallback```.</span></span>

<span data-ttu-id="6ae71-130">또한 보안 토큰을 교환할 수 있도록 다음 개체를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-130">Furthermore, to allow for the exchange of a secure token the following objects need to be implemented.</span></span>

1) <span data-ttu-id="6ae71-131">```IAuthenticationProvider``` 인터페이스를 구현 하는 인증 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-131">An authentication provider implementing the ```IAuthenticationProvider``` interface.</span></span> <span data-ttu-id="6ae71-132">클라이언트 인증에 대 한 토큰을 요청 하기 위해 클라이언트 컨텍스트에서 해당 ```GetToken``` 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-132">Its ```GetToken``` method is called by the client context to request a token for client authentication.</span></span> <span data-ttu-id="6ae71-133">```TokenReceived``` 하 여 인증 토큰을 제공 하 고 연결 프로세스를 계속 하거나 ```Cancel``` 취소 하려면 전달 된 ```IAuthenticationProviderCallback```에서 프로세스를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-133">To continue either ```TokenReceived``` to provide the authentication token and continue the connection process or ```Cancel``` to cancel the process needs to be called on the passed ```IAuthenticationProviderCallback```.</span></span>
2) <span data-ttu-id="6ae71-134">```IAuthenticationReceiver``` 인터페이스를 구현 하는 인증 수신자입니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-134">An authentication receiver implementing the ```IAuthenticationReceiver``` interface.</span></span> <span data-ttu-id="6ae71-135">해당 작업은 들어오는 토큰의 유효성을 검사 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-135">Its task is to validate incoming tokens.</span></span>
    * <span data-ttu-id="6ae71-136">```GetRealm``` 메서드는 인증 영역 이름을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-136">The ```GetRealm``` method should return the name of the authentication realm.</span></span>
    * <span data-ttu-id="6ae71-137">클라이언트 인증 토큰의 유효성 검사를 요청 하기 위해 서버 네트워크 컨텍스트에서 ```ValidateToken``` 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-137">The ```ValidateToken``` method is called by the server network context to request validation of a client authentication token.</span></span> <span data-ttu-id="6ae71-138">계속 하려면 유효성 검사를 완료 하기 위해 ```ValidationCompleted```를 호출 하거나 클라이언트 연결을 거부 ```Cancel``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-138">To continue either call ```ValidationCompleted``` to signal completion of the validation or ```Cancel``` to reject the client connection..</span></span> <span data-ttu-id="6ae71-139">```ValidationCompleted```에 전달 된 유효성 검사 결과에 따라 클라이언트 연결이 허가 되거나 거부 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-139">The client connection will be admitted or rejected based on the validation result passed to ```ValidationCompleted```.</span></span> 

<span data-ttu-id="6ae71-140">이러한 개체가 구현 되 면 원격 컨텍스트 및 플레이어 컨텍스트를 각각 ```Connect``` 대신 ```Listen``` 및 ```ConnectSecure``` 대신 ```ListenSecure``` 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-140">Once these objects are implemented ```ListenSecure``` needs to be called instead of ```Listen``` and ```ConnectSecure``` instead of ```Connect``` on the remote context and player context respectively.</span></span> <span data-ttu-id="6ae71-141">```ListenSecure```에는 ```Listen```에 대 한 추가 인증서 공급자 및 인증 수신기가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-141">```ListenSecure``` requires an additional certificate provider and authentication receiver over ```Listen```.</span></span> <span data-ttu-id="6ae71-142">```ConnectSecure```에는 ```Connect```에 대 한 추가 인증 공급자 및 인증서 유효성 검사기가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae71-142">```ConnectSecure``` requires an additional authentication provider and certificate validator over ```Connect```.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ae71-143">관련 항목</span><span class="sxs-lookup"><span data-stu-id="6ae71-143">See Also</span></span>
* [<span data-ttu-id="6ae71-144">Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="6ae71-144">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="6ae71-145">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="6ae71-145">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="6ae71-146">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="6ae71-146">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="6ae71-147">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="6ae71-147">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="6ae71-148">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="6ae71-148">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
