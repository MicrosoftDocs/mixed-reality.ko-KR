---
title: 상호 작용 기본 사항
description: HoloLens에서 환경을 구축한 대로 (첫 번째 gen) HoloLens 2 및 몰입 형 헤드셋을 공유 하는 데 유용 알게 몇 가지 작업을 기록 시작 했습니다.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합 현실을, 상호 작용 디자인
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597550"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="8ca12-104">상호 작용 기본 사항</span><span class="sxs-lookup"><span data-stu-id="8ca12-104">Interaction fundamentals</span></span>

<span data-ttu-id="8ca12-105">HoloLens 및 몰입 형 헤드셋 환경을 구축한으로 공유 하는 데 유용 알게 몇 가지 작업을 기록 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="8ca12-106">이러한 혼합된 현실 상호 작용 디자인을 위한 기본적인 빌딩 블록으로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="8ca12-107">장치 지원</span><span class="sxs-lookup"><span data-stu-id="8ca12-107">Device support</span></span>

<span data-ttu-id="8ca12-108">에 적용 되는 상호 작용 디자인 문서를 사용할 수 있는 장치 유형 또는 형식의 개요는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="8ca12-109"><strong>입력</strong></span><span class="sxs-lookup"><span data-stu-id="8ca12-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="8ca12-110"><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8ca12-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="8ca12-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8ca12-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="8ca12-112"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="8ca12-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="8ca12-113"><a href="gestures.md">명확 하 고 실습</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="8ca12-114">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="8ca12-115"><a href="gaze-targeting.md">모니터링 대상</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="8ca12-116">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="8ca12-117"><a href="gaze-targeting.md">대상으로 응시</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-118">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-119">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-120">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8ca12-121"><a href="gestures.md">제스처</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-122">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-123">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="8ca12-124"><a href="voice-design.md">음성 디자인</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-125">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-126">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8ca12-128">게임 패드</span><span class="sxs-lookup"><span data-stu-id="8ca12-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-129">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-130">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-131">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="8ca12-132"><a href="motion-controllers.md">컨트롤러 동작</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="8ca12-133">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="8ca12-134"><strong>인식 및 공간 기능</strong></span><span class="sxs-lookup"><span data-stu-id="8ca12-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="8ca12-135"><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8ca12-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="8ca12-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8ca12-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="8ca12-137"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="8ca12-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="8ca12-138"><a href="spatial-sound-design.md">공간 적절 하 게 디자인</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-139">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-140">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-141">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8ca12-142"><a href="spatial-mapping-design.md">공간 매핑 디자인</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-143">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-144">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="8ca12-145"><a href="hologram.md">홀로그램</a></span><span class="sxs-lookup"><span data-stu-id="8ca12-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-146">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="8ca12-147">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca12-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="8ca12-148">사용자가 카메라</span><span class="sxs-lookup"><span data-stu-id="8ca12-148">The user is the camera</span></span>

![사용자가 카메라](images/useriscamera-640px.jpg)

<span data-ttu-id="8ca12-150">항상 해당 실제 및 가상 환경에 대 한 이동 사용자 관점에 대 한 디자인에 대 한 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="8ca12-151">**몇 가지 질문**</span><span class="sxs-lookup"><span data-stu-id="8ca12-151">**Some questions to ask**</span></span>
* <span data-ttu-id="8ca12-152">이 사용자 앉아 안락, 준비, 이거나 환경을 사용 하는 동안 walking?</span><span class="sxs-lookup"><span data-stu-id="8ca12-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="8ca12-153">다른 위치로 콘텐츠 조정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8ca12-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="8ca12-154">사용자 조정할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="8ca12-154">Can the user adjust it?</span></span>
* <span data-ttu-id="8ca12-155">사용자 앱을 사용 하 여 편리 하 게 되나요?</span><span class="sxs-lookup"><span data-stu-id="8ca12-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="8ca12-156">**모범 사례**</span><span class="sxs-lookup"><span data-stu-id="8ca12-156">**Best practices**</span></span>
* <span data-ttu-id="8ca12-157">사용자가 카메라와 움직임을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="8ca12-158">이러한 드라이브 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-158">Let them drive.</span></span>
* <span data-ttu-id="8ca12-159">사실상 사용자를 전송 해야 할 경우 vestibular 뜨거움 관련 된 문제에 중요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="8ca12-160">사용 하 여 더 짧은 애니메이션</span><span class="sxs-lookup"><span data-stu-id="8ca12-160">Use shorter animations</span></span>
* <span data-ttu-id="8ca12-161">왼쪽/오른쪽 아래로에서 애니메이션을 적용 하거나 Z 대신 페이드</span><span class="sxs-lookup"><span data-stu-id="8ca12-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="8ca12-162">타이밍 속도가 저하</span><span class="sxs-lookup"><span data-stu-id="8ca12-162">Slow down timing</span></span>
* <span data-ttu-id="8ca12-163">사용자가 백그라운드에서 전 세계를 참조 하도록 허용</span><span class="sxs-lookup"><span data-stu-id="8ca12-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="8ca12-164">**피해 야 할 사항**</span><span class="sxs-lookup"><span data-stu-id="8ca12-164">**What to avoid**</span></span>
* <span data-ttu-id="8ca12-165">카메라 흔들기 하지 않거나 3DOF에 의도적으로 잠글 (만 방향, 변환이 수행 되지 않음) 불편 한 사용자가 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="8ca12-166">갑작스러운 이동 되지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-166">No abrupt movement.</span></span> <span data-ttu-id="8ca12-167">사용자의 콘텐츠를 표시 해야 할 경우 느린와 원활 하 게 쪽으로 이동 하 최대 편안 함에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="8ca12-168">사용자가 반응 하에서 제공 하는 큰 메뉴 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="8ca12-169">가속화 또는 사용자의 카메라를 설정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8ca12-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="8ca12-170">사용자는 가속 (angular 및 변환)에 민감합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="8ca12-171">사용자의 관점을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-171">Leverage the user's perspective</span></span>

<span data-ttu-id="8ca12-172">사용자는 몰입 형 및 holographic 장치에 표시를 통해 혼합된 현실 세계를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ca12-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="8ca12-173">HoloLens,이 표시 라고 합니다 [holographic 프레임](holographic-frame.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="8ca12-174">2D 개발에 자주 콘텐츠 및 설정을 쉽게 액세스할 수 있도록 화면 모서리에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="8ca12-175">그러나 holographic 앱에서 사용자 보기의 모서리에 있는 콘텐츠 않을 편리 하 게 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="8ca12-176">이 경우 holographic 프레임의 가운데에는 콘텐츠에 대 한 프라임 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="8ca12-177">사용자가 즉시 보기 이외의 개체나 중요 한 이벤트를 찾으려면의 안내를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="8ca12-178">화살표, 연한 내역, 문자 헤드 이동, 사고 거품, 포인터, 공간 소리 및 음성 안내 앱의 중요 한 내용을 안내 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="8ca12-179">사용자의 편안 하 게 화면 잠금 콘텐츠 하지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="8ca12-180">보기 콘텐츠를 유지 하는 경우 전 세계에 놓고 "tag-along" 시작 메뉴와 같은 콘텐츠를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="8ca12-181">사용자 관점 함께 끌어오는 콘텐츠 환경에서 자연스럽 게 느낄 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="8ca12-182">![프레임의 가장자리에 도달 하면 시작 메뉴가 따릅니다 사용자 보기](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8ca12-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="8ca12-183">*프레임의 가장자리에 도달 하면 시작 메뉴가 따릅니다 사용자 보기*</span><span class="sxs-lookup"><span data-stu-id="8ca12-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="8ca12-184">HoloLens에서 홀로그램 잘려 가져오려면 하지 되므로 holographic 프레임 내에 맞을 때 실제 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="8ca12-185">사용자는 프레임 내에서 홀로그램의 범위를 확인 하기 위해 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="8ca12-186">HoloLens, 사용자의 뷰 내에 주 작업에 집중을 유지 하 여 UI를 간소화 하기 위해 중요 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="8ca12-187">몰입 형 헤드셋 장치 보기 필드 내에서 영구적 가상 세계의 효과 유지 하기 위해 중요 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="8ca12-188">사용자 편안 함</span><span class="sxs-lookup"><span data-stu-id="8ca12-188">User comfort</span></span>

<span data-ttu-id="8ca12-189">최대 되도록 [쾌적](comfort.md) 표시 머리에 만들고 사람은 3D 도형 및 자연에서 개체의 상대 위치를 해석 하는 방법을 비슷한 방식으로 콘텐츠를 제공 하는 디자이너 및 개발자를 위한 중요 한 것 전 세계입니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="8ca12-190">실제 관점에서 arm의 목 fatiguing 동작이 필요 하지 않은 콘텐츠를 설계 해야 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="8ca12-191">HoloLens 또는 몰입 형 헤드셋 개발 인지 모두 눈에 대 한 시각적 개체를 렌더링 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="8ca12-192">한 눈에 헤 즈 업 디스플레이 렌더링만 어려울 수 있습니다 인터페이스 이해 사용자의 눈을 뇌 uneasiness 발생 하기.</span><span class="sxs-lookup"><span data-stu-id="8ca12-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="8ca12-193">사용자 경험 공유</span><span class="sxs-lookup"><span data-stu-id="8ca12-193">Share your experience</span></span>

<span data-ttu-id="8ca12-194">사용 하 여 [혼합 현실 캡처](mixed-reality-capture.md), 사진 또는 비디오 언제 든 지 해당 환경의 사용자 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="8ca12-195">스냅숏 또는 비디오를 권장 하려는 앱의 환경을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="8ca12-196">Windows Mixed Reality 홈의 기본 UI 요소를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="8ca12-197">Windows PC 환경을 바탕 화면에서 시작 하는 것 처럼 Windows Mixed Reality 홈으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="8ca12-198">합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 타고 이해 하 고 3D 위치를 탐색 하는 능력을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="8ca12-199">HoloLens를 사용 하 여 집에 실제 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="8ca12-200">몰입 형 헤드셋을 사용 하 여 집 가상 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="8ca12-201">집 여기서 사용할지 시작 메뉴를 열고 앱 및 콘텐츠를 배치할 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="8ca12-202">혼합된 현실 콘텐츠로 홈을 입력 하 고 동시에 여러 앱을 사용 하 여 멀티 태스크 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="8ca12-203">장치를 다시 시작 하는 경우에 집에 배치 작업을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ca12-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ca12-204">참조</span><span class="sxs-lookup"><span data-stu-id="8ca12-204">See also</span></span>
* [<span data-ttu-id="8ca12-205">대상으로 응시</span><span class="sxs-lookup"><span data-stu-id="8ca12-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="8ca12-206">제스처</span><span class="sxs-lookup"><span data-stu-id="8ca12-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="8ca12-207">음성 디자인</span><span class="sxs-lookup"><span data-stu-id="8ca12-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="8ca12-208">컨트롤러 동작</span><span class="sxs-lookup"><span data-stu-id="8ca12-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="8ca12-209">공간 적절 하 게 디자인</span><span class="sxs-lookup"><span data-stu-id="8ca12-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="8ca12-210">공간 매핑 디자인</span><span class="sxs-lookup"><span data-stu-id="8ca12-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="8ca12-211">Comfort</span><span class="sxs-lookup"><span data-stu-id="8ca12-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="8ca12-212">Windows Mixed Reality 홈 탐색</span><span class="sxs-lookup"><span data-stu-id="8ca12-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
