---
title: MRTK 패키지
description: 이 문서에서는 Microsoft 혼합 현실 Toollkit를 구성 하는 패키지를 설명 합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality를 MRTK, 패키지, 구성 요소
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604642"
---
# <a name="mrtk-packages"></a><span data-ttu-id="4aebf-104">MRTK 패키지</span><span class="sxs-lookup"><span data-stu-id="4aebf-104">MRTK packages</span></span>

<span data-ttu-id="4aebf-105">혼합 현실 도구 키트 (MRTK)은 구성 요소화 된 방식으로 혼합 현실 하드웨어 및 플랫폼에 대 한 지원을 제공 하 여 플랫폼 간 혼합 현실 응용 프로그램 개발을 사용 하도록 설정 하는 패키지의 컬렉션.</span><span class="sxs-lookup"><span data-stu-id="4aebf-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms in a componentized manner.</span></span>

<span data-ttu-id="4aebf-106">범주 MRTK 패키지에는 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-106">There are three categories of MRTK packages:</span></span> 

* [<span data-ttu-id="4aebf-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="4aebf-107">Foundation</span></span>](#foundation-packages)
* [<span data-ttu-id="4aebf-108">확장명</span><span class="sxs-lookup"><span data-stu-id="4aebf-108">Extension</span></span>](#extension-packages)
* [<span data-ttu-id="4aebf-109">실험적</span><span class="sxs-lookup"><span data-stu-id="4aebf-109">Experimental</span></span>](#experimental-packages)

## <a name="foundation-packages"></a><span data-ttu-id="4aebf-110">Foundation 패키지</span><span class="sxs-lookup"><span data-stu-id="4aebf-110">Foundation Packages</span></span>

<span data-ttu-id="4aebf-111">혼합 현실 Toolkit Foundation에는 혼합 현실 플랫폼 간에 공통 기능을 활용 하 여 응용 프로그램을 사용 하는 패키지의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-111">The Mixed Reality Toolkit Foundation is the set of packages that enable your application to leverage common functionality across Mixed Reality Platforms.</span></span> <span data-ttu-id="4aebf-112">이러한 패키지 해제 되며 소스 코드에서 Microsoft에서 지원 합니다 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) github 분기 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-112">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

![MRTK Foundation 패키지](images/mrtk-foundation.jpg)

<span data-ttu-id="4aebf-114">*혼합된 현실 Toolkit Foundation 패키지*</span><span class="sxs-lookup"><span data-stu-id="4aebf-114">*Mixed Reality Toolkit Foundation packages*</span></span>

<span data-ttu-id="4aebf-115">MRTK Foundation의 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-115">The MRTK Foundation is comprised of:</span></span>

* [<span data-ttu-id="4aebf-116">Core 패키지</span><span class="sxs-lookup"><span data-stu-id="4aebf-116">Core Package</span></span>](#core-package)
* [<span data-ttu-id="4aebf-117">플랫폼 공급자</span><span class="sxs-lookup"><span data-stu-id="4aebf-117">Platform Providers</span></span>](#platform-providers)
* [<span data-ttu-id="4aebf-118">시스템 서비스</span><span class="sxs-lookup"><span data-stu-id="4aebf-118">System Services</span></span>](#system-services)
* [<span data-ttu-id="4aebf-119">기능 자산</span><span class="sxs-lookup"><span data-stu-id="4aebf-119">Feature Assets</span></span>](#feature-assets)

<span data-ttu-id="4aebf-120">다음 섹션에서는 각 범주에는 패키지의 형식을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-120">The following sections describe the types of packages in each category.</span></span>

### <a name="core-package"></a><span data-ttu-id="4aebf-121">Core 패키지</span><span class="sxs-lookup"><span data-stu-id="4aebf-121">Core Package</span></span>

<span data-ttu-id="4aebf-122">Core 패키지는 _필요한_ 구성 요소 모든 MRTK foundation 패키지에서 종속성으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-122">The core package is a _required_ component and is taken as a dependency by all MRTK foundation packages.</span></span>

<span data-ttu-id="4aebf-123">MRTK Core 패키지에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-123">The MRTK Core package includes:</span></span>

* [<span data-ttu-id="4aebf-124">공용 인터페이스, 클래스 및 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="4aebf-124">Common interfaces, classes and data types</span></span>](#common-interfaces-clases-and-data-types)
* [<span data-ttu-id="4aebf-125">MixedRealityToolkit 장면 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4aebf-125">MixedRealityToolkit scene component</span></span>](#mixedrealitytoolkit-scene-component)
* [<span data-ttu-id="4aebf-126">MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="4aebf-126">MRTK Standard Shader</span></span>](#mrtk-standard-shader)
* [<span data-ttu-id="4aebf-127">Unity 입력된 공급자</span><span class="sxs-lookup"><span data-stu-id="4aebf-127">Unity Input Provider</span></span>](#unity-input-provider)
* [<span data-ttu-id="4aebf-128">패키지 관리</span><span class="sxs-lookup"><span data-stu-id="4aebf-128">Package Management</span></span>](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a><span data-ttu-id="4aebf-129">공용 인터페이스, 클래스 및 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="4aebf-129">Common interfaces, classes and data types</span></span>

<span data-ttu-id="4aebf-130">혼합 현실 Toolkit 코어 패키지는 모든 공용 인터페이스, 클래스 및 다른 모든 구성 요소에서 사용 되는 데이터 형식에 대 한 정의 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-130">The Mixed Reality Toolkit Core package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="4aebf-131">응용 프로그램 플랫폼에서 가장 높은 호환성 수준을 사용 하도록 정의 된 인터페이스를 통해서만 MRTK 구성 요소를 액세스 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-131">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

#### <a name="mixedrealitytoolkit-scene-component"></a><span data-ttu-id="4aebf-132">MixedRealityToolkit 장면 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4aebf-132">MixedRealityToolkit scene component</span></span>

<span data-ttu-id="4aebf-133">MixedRealityToolkit 장면 구성 요소는 혼합 현실 도구 키트에 대 한 단일, 중앙 집중식 리소스 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-133">The MixedRealityToolkit scene component is the single, centralized resource manager for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="4aebf-134">이 구성 요소를 로드 하 고 및 플랫폼 및 서비스 모듈의 수명 관리, 해당 구성 설정에 액세스 하려면 시스템에 대 한 리소스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-134">This component loads and manages the lifespan of the platform and service modules and provides resources for the systems to access their configuration settings.</span></span> 

#### <a name="mrtk-standard-shader"></a><span data-ttu-id="4aebf-135">MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="4aebf-135">MRTK Standard Shader</span></span>

<span data-ttu-id="4aebf-136">MRTK 표준 셰이더는 MRTK에서 제공 되는 자료의 거의 모든 기초를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-136">The MRTK Standard Shader provides the basis for virtually all of the materials provided by the MRTK.</span></span> <span data-ttu-id="4aebf-137">이 셰이더는 매우 유연 하 고 다양 한 MRTK는 지원 되는 플랫폼에 대 한 최적화.</span><span class="sxs-lookup"><span data-stu-id="4aebf-137">This shader is extremely flexible and optimized for the variety of platforms on which MRTK is supported.</span></span> <span data-ttu-id="4aebf-138">것 _항상_ MRTK 표준 셰이더를 사용 하 여 최적의 성능을 위해 응용 프로그램의 자료는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-138">It is _highly_ recommended that your application's materials use the MRTK standard shader for optimal performance.</span></span>

#### <a name="unity-input-provider"></a><span data-ttu-id="4aebf-139">Unity 입력된 공급자</span><span class="sxs-lookup"><span data-stu-id="4aebf-139">Unity Input Provider</span></span>

<span data-ttu-id="4aebf-140">Unity 입력 공급자 3D 공간 마우스 게임 컨트롤러, 터치 스크린 등 일반적인 입력된 장치에 대 한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-140">The Unity Input Provider provides access to common input devices such as game controllers, touch screens and a 3D spatial mouse.</span></span>

#### <a name="package-management"></a><span data-ttu-id="4aebf-141">패키지 관리</span><span class="sxs-lookup"><span data-stu-id="4aebf-141">Package Management</span></span>

<span data-ttu-id="4aebf-142">_서비스 예정_</span><span class="sxs-lookup"><span data-stu-id="4aebf-142">_Coming soon_</span></span>

<span data-ttu-id="4aebf-143">혼합 현실 Toolkit Core 패키지를 검색 하 고 선택적 foundation, 확장 및 실험적 MRTK 패키지 관리에 대 한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-143">The Mixed Reality Toolkit Core package provides support for discovering and managing the optional foundation, extension and experimental MRTK packages.</span></span>

### <a name="platform-providers"></a><span data-ttu-id="4aebf-144">플랫폼 공급자</span><span class="sxs-lookup"><span data-stu-id="4aebf-144">Platform Providers</span></span>

<span data-ttu-id="4aebf-145">MRTK 플랫폼 공급자 패키지는 대상 혼합 현실 하드웨어 혼합 현실 Toolkit 및 플랫폼 기능을 사용 하도록 설정 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-145">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="4aebf-146">지원 되는 플랫폼은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-146">Supported platforms include:</span></span>

* [<span data-ttu-id="4aebf-147">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4aebf-147">Windows Mixed Reality</span></span>](#windows-mixed-reality)
* [<span data-ttu-id="4aebf-148">OpenVR</span><span class="sxs-lookup"><span data-stu-id="4aebf-148">OpenVR</span></span>](#openvr)
* [<span data-ttu-id="4aebf-149">Windows 음성</span><span class="sxs-lookup"><span data-stu-id="4aebf-149">Windows Voice</span></span>](#windows-voice)

#### <a name="windows-mixed-reality"></a><span data-ttu-id="4aebf-150">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4aebf-150">Windows Mixed Reality</span></span>

<span data-ttu-id="4aebf-151">Windows Mixed Reality 패키지는 Microsoft HoloLens 및 혼합 현실 몰입 Windows 장치에 대 한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-151">The Windows Mixed Reality package provides support for Microsoft HoloLens and Windows Mixed Reality Immersive devices.</span></span> <span data-ttu-id="4aebf-152">패키지에는 전체 플랫폼 지원이 포함 되어 있습니다. 포함 하 여:</span><span class="sxs-lookup"><span data-stu-id="4aebf-152">The package contains full platform support, including:</span></span>

* <span data-ttu-id="4aebf-153">대상으로 응시</span><span class="sxs-lookup"><span data-stu-id="4aebf-153">Gaze targeting</span></span>
* <span data-ttu-id="4aebf-154">제스처</span><span class="sxs-lookup"><span data-stu-id="4aebf-154">Gestures</span></span>
* <span data-ttu-id="4aebf-155">Windows Mixed Reality 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="4aebf-155">Windows Mixed Reality Motion controllers</span></span>
* <span data-ttu-id="4aebf-156">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="4aebf-156">Spatial Mapping</span></span>

#### <a name="openvr"></a><span data-ttu-id="4aebf-157">OpenVR</span><span class="sxs-lookup"><span data-stu-id="4aebf-157">OpenVR</span></span>

<span data-ttu-id="4aebf-158">OpenVR 패키지 OpenVR 플랫폼을 사용 하 여 장치에 대 한 지원 하드웨어 및 플랫폼을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-158">The OpenVR package provides hardware and platform support for devices using the OpenVR platform.</span></span>

#### <a name="windows-voice"></a><span data-ttu-id="4aebf-159">Windows 음성</span><span class="sxs-lookup"><span data-stu-id="4aebf-159">Windows Voice</span></span>

<span data-ttu-id="4aebf-160">Windows 음성 패키지는 Microsoft Windows 10 장치에서 키워드 인식과 받아쓰기 기능에 대 한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-160">The Windows Voice package provides support for keyword recognition and dictation functionality on Microsoft Windows 10 devices.</span></span>

### <a name="system-services"></a><span data-ttu-id="4aebf-161">시스템 서비스</span><span class="sxs-lookup"><span data-stu-id="4aebf-161">System Services</span></span>

<span data-ttu-id="4aebf-162">핵심 플랫폼 서비스는 시스템 서비스 패키지에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-162">Core platform services are provided in system service packages.</span></span> <span data-ttu-id="4aebf-163">이러한 패키지에 정의 된 시스템 서비스 인터페이스, 혼합 현실 도구 키트의 기본 구현을 포함 합니다 [core](#core-package) 패키지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-163">These packages contain the Mixed Reality Toolkit's default implementations of the system service interfaces, defined in the [core](#core-package) package.</span></span>

<span data-ttu-id="4aebf-164">MRTK foundation에는 다음 시스템 서비스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-164">The MRTK foundation includes the following system services:</span></span>

* [<span data-ttu-id="4aebf-165">경계 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-165">Boundary System</span></span>](#boundary-system)
* [<span data-ttu-id="4aebf-166">진단 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-166">Diagnostic System</span></span>](#diagnostic-system)
* [<span data-ttu-id="4aebf-167">입력된 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-167">Input System</span></span>](#input-system)
* [<span data-ttu-id="4aebf-168">공간 인식 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-168">Spatial Awareness System</span></span>](#spatial-awareness-system)
* [<span data-ttu-id="4aebf-169">텔레포트 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-169">Teleport System</span></span>](#teleport-system)

#### <a name="boundary-system"></a><span data-ttu-id="4aebf-170">경계 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-170">Boundary System</span></span>

<span data-ttu-id="4aebf-171">가상 현실에 대 한 데이터를 제공 하는 MRTK 경계 시스템 playspace입니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-171">The MRTK Boundary System provides data about the to virtual reality playspace.</span></span> <span data-ttu-id="4aebf-172">사용자가 경계를 구성 하는 시스템에서는 시스템 floor 평면, 사각형 playspace, 추적된 영역 등을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-172">On systems for which the user has configured the boundary, the system can provide a floor plane, rectangular playspace, tracked area, and more.</span></span>

#### <a name="diagnostic-system"></a><span data-ttu-id="4aebf-173">진단 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-173">Diagnostic System</span></span>

<span data-ttu-id="4aebf-174">MRTK 진단 시스템에 응용 프로그램 환경에서 실시간 성능 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-174">The MRTK Diagnostic System provides real-time performance data within your application experience.</span></span> <span data-ttu-id="4aebf-175">Glace에서 응용 프로그램을 사용 하 여 프레임 속도, 프로세서 시간 및 기타 주요 성능 메트릭을 볼 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-175">At a glace, you will be able to view frame rate, processor time and other key performance metrics as you use your application.</span></span>

#### <a name="input-system"></a><span data-ttu-id="4aebf-176">입력된 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-176">Input System</span></span>

<span data-ttu-id="4aebf-177">MRTK 입력 시스템 응용 프로그램이 사용자 동작을 지정 하 고 가장 적합 한 단추 및 대상 컨트롤러의 축에 이러한 작업을 할당 하 여 플랫폼 간 방식으로 입력을 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-177">The MRTK Input Systems enables applications to access input in a cross platform manner by specifying user actions and assigning those actions to the most appropriate buttons and axes on target controllers.</span></span>

#### <a name="spatial-awareness-system"></a><span data-ttu-id="4aebf-178">공간 인식 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-178">Spatial Awareness System</span></span>

<span data-ttu-id="4aebf-179">MRTK 공간 인식 시스템 Microsoft HoloLens 같은 장치에서 실제 환경 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-179">The MRTK Spatial Awareness System enables access to real-world environmental data from devices such as the Microsoft HoloLens.</span></span>

#### <a name="teleport-system"></a><span data-ttu-id="4aebf-180">텔레포트 시스템</span><span class="sxs-lookup"><span data-stu-id="4aebf-180">Teleport System</span></span>

<span data-ttu-id="4aebf-181">MRTK 텔레포트 시스템에 가상 현실 locomotion 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-181">The MRTK Teleport System provides virtual reality locomotion support.</span></span>

### <a name="feature-assets"></a><span data-ttu-id="4aebf-182">기능 자산</span><span class="sxs-lookup"><span data-stu-id="4aebf-182">Feature Assets</span></span>

<span data-ttu-id="4aebf-183">기능 자산은 스크립트 및 Unity 자산으로 제공 되는 관련 기능의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-183">Feature Assets are collections of related functionality delivered as Unity assets and scripts.</span></span> <span data-ttu-id="4aebf-184">이러한 기능 중 일부는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-184">Some of these features include:</span></span>

* <span data-ttu-id="4aebf-185">사용자 인터페이스 컨트롤</span><span class="sxs-lookup"><span data-stu-id="4aebf-185">User Interface Controls</span></span>
* <span data-ttu-id="4aebf-186">표준 자산</span><span class="sxs-lookup"><span data-stu-id="4aebf-186">Standard Assets</span></span>
* <span data-ttu-id="4aebf-187">more</span><span class="sxs-lookup"><span data-stu-id="4aebf-187">more</span></span>

## <a name="extension-packages"></a><span data-ttu-id="4aebf-188">확장 패키지</span><span class="sxs-lookup"><span data-stu-id="4aebf-188">Extension Packages</span></span>

<span data-ttu-id="4aebf-189">MRTK 확장 패키지는 확장 하 고 혼합 현실 도구 키트의 기능을 향상 시키는 Microsoft 및 커뮤니티에서 작성 하는 패키지의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-189">MRTK Extension packages are a collection of packages written by Microsoft and the Community that extend and enhance the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="4aebf-190">확장 작성자가 필요한 종속성을 상태, 혼합 현실 도구 키트와 호환 패키지로 표시 및 라이선스 제공 되며 문을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-190">Extension authors will state any required dependencies, mark the package as compatible with the Mixed Reality Toolkit and provide licensing and support statements.</span></span>

<span data-ttu-id="4aebf-191">확장 패키지에는 새로운 기능과 새로운 플랫폼 지원을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-191">Extension packages may provide new features and new platform support.</span></span> <span data-ttu-id="4aebf-192">시간이 지남에 따라 확장, 지원 및 작성자의 승인을 사용 하 여 마이그레이션될 수 있으므로 MRTK 기반 이때는 해제 되며 Microsoft 지원에 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-192">Over time, extensions may, with the assistance and approval of the authors, be migrated into the MRTK Foundation at which time they will be released and supported by Microsoft.</span></span>

![MRTK 확장 패키지](images/mrtk-extensions.jpg)

<span data-ttu-id="4aebf-194">*혼합된 현실 Toolkit 확장 패키지*</span><span class="sxs-lookup"><span data-stu-id="4aebf-194">*Mixed Reality Toolkit Extension packages*</span></span>

## <a name="experimental-packages"></a><span data-ttu-id="4aebf-195">실험적 패키지</span><span class="sxs-lookup"><span data-stu-id="4aebf-195">Experimental Packages</span></span>

<span data-ttu-id="4aebf-196">실험적 패키지에는 흥미로운 새로운 아이디어, 비행 프로토타입 기능 및 시험판 버전을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-196">Experimental packages provide the ability to flight prototype features, pre-releases and exciting new ideas.</span></span> <span data-ttu-id="4aebf-197">가장 실험적 패키지의 목표는 새로운 고 고객의 관심 계기입니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-197">The goal of most experimental packages is to try something new and to gauge customer interest.</span></span> <span data-ttu-id="4aebf-198">많은 있지만 모든 실험적 패키지 수 확장으로 다시 출시 된 프로토타입 및 테스트 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-198">Many, though not all, experimental packages will be re-released as extensions once the prototyping and testing phase completes.</span></span>

![MRTK 실험적 패키지](images/mrtk-experimental.jpg)

<span data-ttu-id="4aebf-200">*혼합된 현실 Toolkit 실험적 패키지*</span><span class="sxs-lookup"><span data-stu-id="4aebf-200">*Mixed Reality Toolkit Experimental packages*</span></span>

## <a name="conclusion"></a><span data-ttu-id="4aebf-201">결론</span><span class="sxs-lookup"><span data-stu-id="4aebf-201">Conclusion</span></span>

<span data-ttu-id="4aebf-202">혼합 현실 Toolkit 패키지 및 패키지 관리 시스템은 입자 불필요 한 구성 요소 프로젝트에 포함 되도록 요구 하지 않고 환경에 기능을 작성 하기 위한 명확 하 고 간단한 방법을 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-202">The Mixed Reality Toolkit packages and package management system are designed to enable a clean and simple method for you to additively build features into your experiences without requiring unnecessary components to be included into the project.</span></span>

<span data-ttu-id="4aebf-203">시간이 지남에 따라 패키지 관리 지원은 추가 하 고 혼합 현실 도구 키트 내에서 강화 합니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-203">Over time, package management support will be added and enhanced within the Mixed Reality Toolkit.</span></span> <span data-ttu-id="4aebf-204">피드백 했거나 참여 하려는 경우를 방문 하십시오 합니다 [혼합 현실 Toolkit 프로젝트](https://github.com/Microsoft/MixedRealityToolkit-Unity) github입니다.</span><span class="sxs-lookup"><span data-stu-id="4aebf-204">If you have feedback or wish to get involved, please visit the [Mixed Reality Toolkit project](https://github.com/Microsoft/MixedRealityToolkit-Unity) on GitHub.</span></span> 

## <a name="see-also"></a><span data-ttu-id="4aebf-205">참조</span><span class="sxs-lookup"><span data-stu-id="4aebf-205">See also</span></span>

* [<span data-ttu-id="4aebf-206">MixedRealityToolkit-Unity (GitHub)</span><span class="sxs-lookup"><span data-stu-id="4aebf-206">MixedRealityToolkit-Unity (GitHub)</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

