---
title: 멀티모달 상호 작용 개요
description: 멀티모달 상호 작용에 대한 개요
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, 응시, 응시 타기팅, 상호 작용, 디자인, HoloLens, MMR, 멀티모달
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516017"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="40803-104">직관적인 상호 작용 소개</span><span class="sxs-lookup"><span data-stu-id="40803-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="40803-105">간단하고 직관적인 상호 작용이라는 철학은 혼합 현실 플랫폼 전반에 얽혀 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="40803-106">애플리케이션 디자이너와 개발자가 고객에게 쉽고 직관적인 상호 작용을 제공할 수 있도록 하는 3단계를 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="40803-107">첫째, 손 추적, 시선 추적 및 자연어와 같은 놀라운 센서와 입력 기술을 완벽한 멀티모달 상호 작용 모델로 결합했습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="40803-108">조사에 따르면, 단일 입력 보다는 다원적인 설계와 개발이 직관적인 환경을 만드는 열쇠라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="40803-109">둘째, 여러 디바이스(HoloLens 2, HoloLens (1세대) 또는 HoloLens 및 VR)를 대상으로 하는 개발자가 많다는 점을 파악했습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="40803-110">따라서, 상호 작용 모델이 여러 디바이스에서 작동하도록 설계하고 있습니다(입력 기술이 디바이스마다 다를 수 있음).</span><span class="sxs-lookup"><span data-stu-id="40803-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="40803-111">예를 들어, 6DOF 컨트롤러가 포함된 Windows 몰입형 헤드셋과의 원거리 상호 작용 및 HoloLens 2의 원거리 상호 작용은 둘 다 동일한 어포던스와 패턴을 사용하여 디바이스 간에 애플리케이션을 쉽게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="40803-112">이러한 기능은 개발자와 디자이너에게 편리할 뿐만 아니라 최종 사용자에게는 당연하게 받아들여 집니다.</span><span class="sxs-lookup"><span data-stu-id="40803-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="40803-113">마지막으로, MR에서 효과적이고 매력적이며 신비한 수천 가지의 상호 작용이 가능하다는 것을 알고 있지만, 사용자의 성공과 편리한 환경을 위해서는 애플리케이션에 의도적으로 단일 상호 작용 모델을 사용하는 것이 가장 좋다는 것을 파악했습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="40803-114">따라서, 이 상호 작용 지침에는 다음 세 가지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="40803-115">이 지침은 세 가지 기본 상호 작용 모델 및 각각에 필요한 구성 요소와 패턴을 중심으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="40803-116">플랫폼에 제공되는 기타 혜택에 대한 추가 지침이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="40803-117">시나리오에 적합한 상호 작용 모델을 선택하는 데 참고할 수 있는 지침이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="40803-118">멀티모달 상호 작용 모델</span><span class="sxs-lookup"><span data-stu-id="40803-118">Multimodal interaction models</span></span>

<span data-ttu-id="40803-119">현재까지의 연구 및 고객과의 작업을 기반으로, 대다수의 혼합 현실 환경에 적합한 세 가지 주요 상호 작용 모델이 파악되었습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="40803-120">여러 가지 면에서 상호 작용 모델은 사용자의 흐름을 완료하기 위한 멘탈 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-120">In many ways, the interaction model is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="40803-121">각 상호 작용 모델은 고객의 요구에 맞게 최적화되어 있으며 각 모델은 편리하고 강력하며 사용하기에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="40803-122">아래 차트는 간략한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="40803-123">각 상호 작용 모델 사용에 대한 자세한 정보는 아래 페이지에서 이미지와 코드 샘플로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="40803-124"><strong>모델</strong></span><span class="sxs-lookup"><span data-stu-id="40803-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="40803-125"><strong>예제 시나리오</strong></span><span class="sxs-lookup"><span data-stu-id="40803-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="40803-126"><strong>적합</strong></span><span class="sxs-lookup"><span data-stu-id="40803-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="40803-127"><strong>하드웨어</strong></span><span class="sxs-lookup"><span data-stu-id="40803-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="40803-128"><a href="hands-and-tools.md">실습 및 모션 컨트롤러</a></span><span class="sxs-lookup"><span data-stu-id="40803-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="40803-129">3D 공간 환경, 예: 공간 레이아웃 및 디자인, 컨텐츠 조작 또는 시뮬레이션.</span><span class="sxs-lookup"><span data-stu-id="40803-129">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="40803-130">새로운 사용자에게 음성, 시선 추적 또는 헤드 게이즈(head-gaze)와 함께 사용하면 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-130">Great for new users, coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="40803-131">학습 기간이 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-131">Low learning curve.</span></span> <span data-ttu-id="40803-132">손 추적 및 6 DoF 컨트롤러에서 UX가 일관적입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span></td>
        <td><span data-ttu-id="40803-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="40803-133">HoloLens 2</span></span><br><span data-ttu-id="40803-134">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="40803-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="40803-135"><a href="hands-free.md">핸즈프리</a></span><span class="sxs-lookup"><span data-stu-id="40803-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="40803-136">현장 학습, 유지 보수와 같이 사용자의 손을 다른 일에 사용하고 있는 상황에 맞는 환경.</span><span class="sxs-lookup"><span data-stu-id="40803-136">Contextual experiences where a user's hands are occupied, e.g. on-the-job learning, maintenance.</span></span></td>
        <td><span data-ttu-id="40803-137">어느 정도 학습이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-137">Some learning required.</span></span> <span data-ttu-id="40803-138">손을 사용할 수 없는 경우, 음성 및 자연어와 조화를 잘 이룹니다.</span><span class="sxs-lookup"><span data-stu-id="40803-138">If hands are unavailable pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="40803-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="40803-139">HoloLens 2</span></span><br><span data-ttu-id="40803-140">HoloLens(1세대)</span><span class="sxs-lookup"><span data-stu-id="40803-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="40803-141">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="40803-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="40803-142"><a href="gaze-and-commit.md">헤드 게이즈 및 커밋</a></span><span class="sxs-lookup"><span data-stu-id="40803-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="40803-143">클릭 사용 환경, 예: 3D 프레젠테이션, 데모.</span><span class="sxs-lookup"><span data-stu-id="40803-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="40803-144">모바일이 아닌 HMD에 대한 교육이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="40803-145">액세스 가능한 컨트롤러에 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-145">Best for accessible controllers.</span></span> <span data-ttu-id="40803-146">HoloLens(1세대)에 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="40803-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="40803-147">HoloLens 2</span></span><br><span data-ttu-id="40803-148">HoloLens(1세대)</span><span class="sxs-lookup"><span data-stu-id="40803-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="40803-149">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="40803-149">Immersive headsets</span></span><br><span data-ttu-id="40803-150">모바일 AR</span><span class="sxs-lookup"><span data-stu-id="40803-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="40803-151">환경에서 상호 작용에 문제가 없도록 하는 가장 좋은 방법은 단일 모델에 대한 지침을 처음부터 끝까지 따르는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-151">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="40803-152">디자인 및 개발 속도를 높일 수 있도록, 각 모델에 대한 자세한 내용과 이미지 및 코드 샘플 링크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-152">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="40803-153">하지만 먼저, 아래 섹션에서는 이러한 상호 작용 모델 중 하나를 선택하고 구현하는 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-153">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="40803-154">이 페이지를 끝까지 마치면 다음 사항에 대한 지침을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="40803-155">고객을 위한 상호 작용 모델 선택</span><span class="sxs-lookup"><span data-stu-id="40803-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="40803-156">상호 작용 모델 지침 사용</span><span class="sxs-lookup"><span data-stu-id="40803-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="40803-157">상호 작용 모델 간 전환</span><span class="sxs-lookup"><span data-stu-id="40803-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="40803-158">다음 단계 디자인</span><span class="sxs-lookup"><span data-stu-id="40803-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="40803-159">고객을 위한 상호 작용 모델 선택</span><span class="sxs-lookup"><span data-stu-id="40803-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="40803-160">대부분의 경우, 개발자와 작성자는 사용자에게 제공하려는 상호 작용 환경의 종류에 대한 아이디어를 이미 염두에 두고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-160">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="40803-161">고객 중심의 설계 방식을 권장하기 위해, 아래 지침에 따라 고객에게 최적화된 상호 작용 모델을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-161">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="40803-162">이 지침을 따르는 이유</span><span class="sxs-lookup"><span data-stu-id="40803-162">Why follow this guidance?</span></span>

* <span data-ttu-id="40803-163">상호 작용 모델은 신체적 노력과 인지적 노력, 직관성 및 학습 가능성과 같은 객관적이고 주관적인 기준에 따라 테스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-163">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="40803-164">상호 작용이 다르기 때문에, 시각 및 오디오 어포던스 및 개체 동작 역시 상호 작용 모델 간에 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-164">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="40803-165">여러 상호 작용 모델의 파트를 함께 결합하면 어포던스 사이에 경쟁(예: 동시 핸드 레이(hand ray)와 헤드 게이즈(head-gaze) 커서)이 발생할 위험이 있으며, 사용자에게 혼란을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-165">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which can overwhelm and confuse users.</span></span>

<span data-ttu-id="40803-166">다음은 각 상호 작용 모델에 대해 어포던스 및 동작을 최적화하는 방법에 대한 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="40803-167">새로운 사용자가 "시스템이 작동하는지 어떻게 알 수 있나요? 내가 무엇을 할 수 있는지 어떻게 알 수 있나요? 내가 방금 한 일이 이해되었는지 어떻게 알 수 있나요?" 등과 유사한 질문을 하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="40803-168"><strong>모델</strong></span><span class="sxs-lookup"><span data-stu-id="40803-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="40803-169"><strong>작동하는지 어떻게 알 수 있나요?</strong></span><span class="sxs-lookup"><span data-stu-id="40803-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="40803-170"><strong>내가 무엇을 할 수 있는지 어떻게 알 수 있나요?</strong></span><span class="sxs-lookup"><span data-stu-id="40803-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="40803-171"><strong>내가 방금 한 일을 어떻게 알 수 있나요?</strong></span><span class="sxs-lookup"><span data-stu-id="40803-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="40803-172"><a href="hands-and-tools.md">실습 및 모션 컨트롤러</a></span><span class="sxs-lookup"><span data-stu-id="40803-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="40803-173">손 메시가 보입니다. 손가락 끝 어포던스 또는 손/컨트롤러 레이가 보입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-173">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="40803-174">내 손이 가까이 있으면 잡을 수 있는 핸들이나 테두리 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="40803-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="40803-175">가청음이 들리고 잡았다 놓을 수 있는 애니메이션이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="40803-176"><a href="gaze-and-commit.md">헤드 게이즈 및 커밋</a></span><span class="sxs-lookup"><span data-stu-id="40803-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="40803-177">내 시야의 가운데에 커서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="40803-178">헤드 게이즈(head-gaze) 커서가 특정 개체 위에 있으면 상태가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="40803-179">내가 행동을 하면 시각 및 청각 확인이 보이고 들립니다.</span><span class="sxs-lookup"><span data-stu-id="40803-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="40803-180"><a href="hands-free.md">핸즈프리(헤드 게이즈(head-gaze) 및 드웰(dwell))</a></span><span class="sxs-lookup"><span data-stu-id="40803-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="40803-181">내 시야의 가운데에 커서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="40803-182">상호 작용이 가능한 개체에 드웰(dwell)하면 진행률 표시기가 보입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="40803-183">내가 행동을 하면 시각 및 청각 확인이 보이고 들립니다.</span><span class="sxs-lookup"><span data-stu-id="40803-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="40803-184"><a href="hands-free.md">핸즈프리(음성 명령)</a></span><span class="sxs-lookup"><span data-stu-id="40803-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="40803-185">시스템이 무엇을 들었는지 보여주는 듣기 표시기와 자막이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="40803-186">음성 프롬프트와 힌트가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-186">I get voice prompts and hints.</span></span>  <span data-ttu-id="40803-187">"뭐라고 해야 하나요?"라고 말하면 피드백이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-187">When I say "what can I say?"</span></span> <span data-ttu-id="40803-188">피드백이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="40803-189">명령을 하면 시각 및 청각 확인이 보이고 들리거나 필요할 때 명확성 UX가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="40803-190">다음은 상호 작용 모델을 선택하는 데 도움이 되는 질문입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="40803-191">Q:  사용자가 홀로그램을 터치하고 정밀한 홀로그램 조작을 수행하기를 원하나요?</span><span class="sxs-lookup"><span data-stu-id="40803-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="40803-192">A:  만약 그렇다면, 손이나 모션 컨트롤러로 정밀 타기팅 및 조작을 위한 손 및 도구 상호 작용 모델을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="40803-192">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="40803-193">Q:  사용자가 실제 업무에서 손이 자유로워야 하나요?</span><span class="sxs-lookup"><span data-stu-id="40803-193">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="40803-194">A:  만약 그렇다면, 응시 기반 및 음성 기반 상호 작용을 통해 유용한 핸즈프리 환경을 제공하는 핸즈프리 상호 작용 모델을 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="40803-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="40803-195">Q:  사용자가 혼합 현실 애플리케이션의 상호 작용을 학습할 시간이 있나요? 또는 가장 낮은 학습 곡선과의 상호 작용이 사용자에게 필요한가요?</span><span class="sxs-lookup"><span data-stu-id="40803-195">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="40803-196">A:  사용자가 손을 사용하여 상호 작용을 할 수만 있다면, 가장 낮은 학습 곡선과 가장 직관적인 상호 작용을 위한 손과 도구 모델이 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-196">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="40803-197">Q:  사용자가 가리키기 및 조작을 위해 모션 컨트롤러를 사용하나요?</span><span class="sxs-lookup"><span data-stu-id="40803-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="40803-198">A:  손 및 도구 모델에는 모션 컨트롤러를 사용하는 유용한 경험을 위한 모든 지침이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40803-198">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="40803-199">Q:  사용자가 접근성 컨트롤러나 일반적인 Bluetooth 컨트롤러(예: 클리커)를 사용하나요?</span><span class="sxs-lookup"><span data-stu-id="40803-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="40803-200">A:  모든 비 추적 컨트롤러에 대해서는 헤드 게이즈(head-gaze) 및 커밋 모델을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-200">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="40803-201">사용자가 간단하나 "대상 및 커밋" 기법으로 전체 환경을 탐색할 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="40803-202">Q: 사용자가 UI 컨트롤의 밀집된 레이아웃을 탐색하는 것과는 대조적으로, "클릭"(예: 3D 슬라이드 쇼와 같은 환경)을 통한 환경에서 작업을 수행하나요?</span><span class="sxs-lookup"><span data-stu-id="40803-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="40803-203">A:  사용자가 UI를 많이 제어할 필요가 없는 경우에는, 헤드 게이즈(head-gaze) 및 커밋에 학습이 가능한 옵션이 제공되기 때문에 사용자가 타기팅을 염려할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="40803-204">Q:  사용자가 HoloLens(1세대)와 HoloLens 2/Windows 몰입형(VR 헤드셋)을 둘 다 사용하나요?</span><span class="sxs-lookup"><span data-stu-id="40803-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="40803-205">A:  헤드 게이즈(head-gaze) 및 커밋은 HoloLens(1세대)를 위한 상호 작용 모델이기 때문에, HoloLens(1세대)를 지원하는 작성자는 사용자가 HoloLens(1세대) 헤드셋에서 경험할 수 있는 기능이나 모드에 대해 헤드 게이즈(head-gaze) 및 커밋을 사용할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="40803-206">여러 HoloLens 세대를 위한 원활한 환경을 만드는 방법에 대한 자세한 내용은 *상호 작용 모델 전환*에 대한 다음 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40803-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="40803-207">Q: 주로 한 곳에서 일하는 사용자에 비해 일반적으로 이동이 많은(넓은 공간을 사용하거나 공간 사이를 이동) 사용자는 어떤가요?</span><span class="sxs-lookup"><span data-stu-id="40803-207">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="40803-208">A:  이러한 사용자에게는 모든 사용자 상호 작용 모델이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="40803-209">앱 디자인에 관련된 자세한 지침은 [서비스 예정](index.md#news-and-notes)입니다.</span><span class="sxs-lookup"><span data-stu-id="40803-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="40803-210">상호 작용 모델 전환</span><span class="sxs-lookup"><span data-stu-id="40803-210">Transition interaction models</span></span>
<span data-ttu-id="40803-211">둘 이상의 상호 작용 모델을 활용해야 하는 사용 사례의 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-211">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="40803-212">예를 들어, 앱의 '만들기 흐름'에는 손 및 모션 컨트롤러 상호 작용 모델이 사용되지만 현장 기술자에게는 핸즈프리 모드를 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="40803-212">For example, your app's "creation flow" utilizes the Hands and motion controllers interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="40803-213">환경에 다수의 상호 작용 모델이 필요한 경우, 한 모델에서 다른 모델로 전환하는 데 어려움을 겪는 최종 사용자가 많은 것을 파악했습니다. 특히 혼합 현실을 처음 접하는 사용자가 어려움을 겪습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-213">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="40803-214">디자이너와 개발자가 MR에서 어려울 수 있는 선택을 할 수 있도록 여러 상호 작용 모델 사용에 대한 자세한 지침을 제공하기 위해 노력하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40803-214">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="40803-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40803-215">See also</span></span>
* [<span data-ttu-id="40803-216">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="40803-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="40803-217">헤드 게이즈 및 유지</span><span class="sxs-lookup"><span data-stu-id="40803-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="40803-218">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="40803-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="40803-219">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="40803-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="40803-220">제스처</span><span class="sxs-lookup"><span data-stu-id="40803-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="40803-221">음성 명령</span><span class="sxs-lookup"><span data-stu-id="40803-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="40803-222">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="40803-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="40803-223">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="40803-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="40803-224">공간 매핑 디자인</span><span class="sxs-lookup"><span data-stu-id="40803-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="40803-225">편안함</span><span class="sxs-lookup"><span data-stu-id="40803-225">Comfort</span></span>](comfort.md)

