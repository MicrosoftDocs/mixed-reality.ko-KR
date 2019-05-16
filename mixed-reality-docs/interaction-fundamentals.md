---
title: 조직의 다중 모달 방식 상호 작용 개요
description: 조직의 다중 모달 방식 상호 작용의 개요
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, 게이즈 게이즈 상호 작용을 대상으로 디자인, hololens, MMR, multimodal
ms.openlocfilehash: 771ebe44dc984c9d4550638bef405810d86b8d69
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730829"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="470e9-104">소개 instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="470e9-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="470e9-105">Microsoft 혼합 현실 (MMR) 플랫폼 전체에서 소프트웨어에는 하드웨어에서 간단 하 고 instinctual 상호 작용의 원리 연결 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality (MMR) platform, from hardware to software.</span></span>

<span data-ttu-id="470e9-106">이러한 instinctual 상호 작용에는 모든 사용 가능한 입력 등과 같은 기술을 추적 내부 스케일 아웃, 직접 추적, 시선 추적, 자연어를 원활 하 게 조직의 다중 모달 방식 상호 작용 모델의 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-106">These instinctual interactions utilize all available input technologies, including inside-out tracking, hand tracking, eye tracking, and natural language, in seamless multimodal interaction models.</span></span> <span data-ttu-id="470e9-107">디자인 및 개발이 연구에 기초한 multimodals, 단일 입력 하지 기반 이며 중요 한 이런 환경을 만들 때.</span><span class="sxs-lookup"><span data-stu-id="470e9-107">Based on our research, designing and developing multimodals, and not based on single inputs, is critical when creating instinctive experiences.</span></span>

<span data-ttu-id="470e9-108">장치 유형에 서 Instinctual 상호 작용 모델은 또한 자연스럽 게 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-108">The Instinctual Interaction models also naturally align across device types.</span></span>  <span data-ttu-id="470e9-109">예를 들어 먼 상호는 몰입 형 헤드셋에 자유롭게 (DoF) 컨트롤러의 6도 및 HoloLens 2에서 먼 상호 작용 동일한 affordances, 패턴 및 동작을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-109">For example, far interaction on an immersive headset with a 6 degrees of freedom (DoF) controller and far interaction on a HoloLens 2 use the same affordances, patterns, and behaviors.</span></span>  <span data-ttu-id="470e9-110">뿐만 아니라이 편리 개발자 및 디자이너, 하지만 최종 사용자에 게 자연스럽 게 받아들이며에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-110">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span>


<span data-ttu-id="470e9-111">마지막으로, 효율적이 고 흥미로운 수천 개의 마법의 상호 작용 MR에서 가능한 개는 의도적으로 사용 하는 단일 상호 작용 모델의 종단 간 인식 하는 동안 응용 프로그램은 가장 좋은 방법은 사용자가 성공적으로 확인 하 고 훌륭한 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-111">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="470e9-112">이 위해 다음 세 가지가 상호 작용 지침에 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-112">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="470e9-113">에서는 세 가지 기본 상호 작용 모델 및 구성 요소와 각각에 대해 필요한 패턴을 기반으로 한이 지침을 구조화 했습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-113">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="470e9-114">플랫폼 제공 하는 기타 혜택에 대 한 추가 지침 포함 했습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-114">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="470e9-115">시나리오에 대 한 적절 한 상호 작용 모델을 선택 하는 데 유용한 지침 포함 했습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-115">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="470e9-116">조직의 다중 모달 방식 상호 작용 모델</span><span class="sxs-lookup"><span data-stu-id="470e9-116">Multimodal interaction models</span></span>

<span data-ttu-id="470e9-117">이 연구 및 고객 날짜를 사용 하 여 작업에 따라 3 가지 기본 상호 작용 모델 대부분의 혼합 현실 환경에 맞게을 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-117">Based on our research and work with customers to date, we've discovered three primary interaction models that suit the majority of Mixed Reality experiences.</span></span>  

<span data-ttu-id="470e9-118">이러한 상호 작용 모델 해당 흐름을 완료 하는 것에 대 한 사용자의 멘 탈 모델 이라고 생각 됩니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-118">Think of these interaction models as the user's mental model for completing their flows.</span></span>

<span data-ttu-id="470e9-119">이러한 상호 작용 모델의 각 강력 하 고 고유한 권한을 사용할 수 있는 편리한 이며 모든 고객의 요구 사항 집합에 대해 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-119">Each of these interaction models is convenient, powerful, and usable in its own right, and all are optimized for a set of customer needs.</span></span> <span data-ttu-id="470e9-120">아래, 시나리오, 예제 및 각 상호 작용 모델의 이점에 대 한 차트를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-120">View the chart below, for scenarios, examples, and benefits of each interaction model.</span></span>  

<span data-ttu-id="470e9-121">**Model**</span><span class="sxs-lookup"><span data-stu-id="470e9-121">**Model**</span></span> | <span data-ttu-id="470e9-122">**[실습 및 도구](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)**</span><span class="sxs-lookup"><span data-stu-id="470e9-122">**[Hands and Tools](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)**</span></span> | <span data-ttu-id="470e9-123">**[핸 즈 프리](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)**</span><span class="sxs-lookup"><span data-stu-id="470e9-123">**[Hands free](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)**</span></span> | <span data-ttu-id="470e9-124">**[응시 및 커밋](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**</span><span class="sxs-lookup"><span data-stu-id="470e9-124">**[Gaze and Commit](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**</span></span>
|--------- | --------------| ------------| ---------|
<span data-ttu-id="470e9-125">**예제 시나리오**</span><span class="sxs-lookup"><span data-stu-id="470e9-125">**Example Scenarios**</span></span> | <span data-ttu-id="470e9-126">예를 들어 공간 레이아웃과 디자인을 3D 공간 환경이 콘텐츠 조작 또는 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="470e9-126">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation</span></span> | <span data-ttu-id="470e9-127">여기서 사용자의 손에 꽉 찼을, 예: the 작업 학습, 유지 관리 하는 상황에 맞는 환경</span><span class="sxs-lookup"><span data-stu-id="470e9-127">Contextual experiences where a user's hands are occupied, e.g. on the-job learning, maintenance</span></span>| <span data-ttu-id="470e9-128">클릭 광고 환경을, 3D 프레젠테이션, 데모 예:</span><span class="sxs-lookup"><span data-stu-id="470e9-128">Click-through experiences, e.g. 3D presentations, demos</span></span>
<span data-ttu-id="470e9-129">**Fit**</span><span class="sxs-lookup"><span data-stu-id="470e9-129">**Fit**</span></span> | <span data-ttu-id="470e9-130">새 사용자를 결합 된 wit 음성에 대 한 멋진 시각 추적 또는 헤드 응시 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-130">Great for new users, coupled wit voice, eye tracking or head gaze.</span></span> <span data-ttu-id="470e9-131">낮은 학습 곡선입니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-131">Low learning curve.</span></span> <span data-ttu-id="470e9-132">직접 추적 및 6 DoF 컨트롤러 간에 일관 된 UX 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span> | <span data-ttu-id="470e9-133">일부 학습 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-133">Some learning required.</span></span> <span data-ttu-id="470e9-134">음성 및 자연어 쌍을 사용할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="470e9-134">If hands are unavailable pairs well with voice and natural language</span></span> | <span data-ttu-id="470e9-135">Mobile에는 없지만 HMDs에서 학습에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-135">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="470e9-136">액세스할 수 있는 컨트롤러 HoloLens에 가장 적합 (첫 번째 범용)</span><span class="sxs-lookup"><span data-stu-id="470e9-136">Best for accessible controllers Best for HoloLens (1st gen)</span></span> |
<span data-ttu-id="470e9-137">**하드웨어**</span><span class="sxs-lookup"><span data-stu-id="470e9-137">**Hardware**</span></span> | <span data-ttu-id="470e9-138">HoloLens 2 몰입 형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="470e9-138">HoloLens 2 Immersive headsets</span></span> | <span data-ttu-id="470e9-139">HoloLens 2 HoloLens (첫 번째 gen) 몰입 형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="470e9-139">HoloLens 2 HoloLens (1st gen) Immersive headsets</span></span> | <span data-ttu-id="470e9-140">HoloLens 2 몰입 형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="470e9-140">HoloLens 2 Immersive headsets</span></span> | <span data-ttu-id="470e9-141">HoloLens 2 HoloLens (첫 번째 gen) 몰입 형 헤드셋 Mobile AR</span><span class="sxs-lookup"><span data-stu-id="470e9-141">HoloLens 2 HoloLens (1st gen) Immersive headsets Mobile AR</span></span> |

<span data-ttu-id="470e9-142">각 상호 작용 모델에서 원활 하 게 함께 사용 하는 모든 사용 가능한 입력에 대 한 자세한 내용은 다음에 오는 페이지, 그림 및 샘플 콘텐츠는 Unity MRTK에서 링크 켜져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-142">Detailed information for using all available inputs seamlessly together in each interaction model is on the pages that follow, as well as illustrations and links to sample content from our Unity MRTK.</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="470e9-143">고객을 위해 상호 작용 모델을 선택</span><span class="sxs-lookup"><span data-stu-id="470e9-143">Choose an interaction model for your customer</span></span>


<span data-ttu-id="470e9-144">대부분의 경우 개발자와 작성자도 이미 몇 가지 아이디어 상호 작용 경험 하도록 사용자에 게 원하는 유형의 염두 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-144">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="470e9-145">고객 중심 접근 방법을 디자인 하는 것이 좋습니다, 아래 지침을 따르도록를 좋습니다 고객을 위해 최적화 된 상호 작용 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-145">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="470e9-146">이 지침을 수행 하는 이유</span><span class="sxs-lookup"><span data-stu-id="470e9-146">Why follow this guidance?</span></span>

* <span data-ttu-id="470e9-147">상호 작용 모델은 목표와 실제 및 cognitive 노력, 사용 편이성을 learnability 등 주관적인 기준에 대 한 테스트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-147">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="470e9-148">상호 작용 다르므로 visual 및 오디오 affordances 동작과 개체 상호 작용 모델 간에 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-148">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="470e9-149">여러 상호 작용 모델의 파트를 결합 위험 등 동시 직접 광선 헤드 게이즈 커서를 압도 하 고 사용자를 혼동 하는 경쟁 affordances 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-149">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="470e9-150">Affordances 동작과 각 상호 작용 모델에 대해 최적화 된 방법의 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-150">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="470e9-151">종종 볼 새 사용자로도 비슷한 질문이 같은 "시스템 작동을 알고 수행 하는 방법을 어떻게 알 수 있습니까 수행할 수 있는 작업을 어떻게 알 수 있습니까 방금 수행한 이해 하는 경우 및?"</span><span class="sxs-lookup"><span data-stu-id="470e9-151">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="470e9-152"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="470e9-152"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="470e9-153"><strong>어떻게이 작업은?</strong></span><span class="sxs-lookup"><span data-stu-id="470e9-153"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="470e9-154"><strong>수행할 수 있습니다 어떻게 알 수 있나요?</strong></span><span class="sxs-lookup"><span data-stu-id="470e9-154"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="470e9-155"><strong>방금 필자 어떻게 알 수 있나요?</strong></span><span class="sxs-lookup"><span data-stu-id="470e9-155"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="470e9-156"><a href="hands-and-tools.md">실습 및 도구</a></span><span class="sxs-lookup"><span data-stu-id="470e9-156"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="470e9-157">메시 손 모양 표시, 손끝 유도성 또는 직접 표시 / 컨트롤러 광선 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-157">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="470e9-158">Grabbable 핸들이 나 손을 때 표시 경계 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-158">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="470e9-159">청각적 들릴 했으며 잡기 릴리스에 애니메이션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="470e9-159">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="470e9-160"><a href="gaze-and-commit.md">헤드 게이즈 및 커밋</a></span><span class="sxs-lookup"><span data-stu-id="470e9-160"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="470e9-161">보기 내 필드의 가운데에 커서를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-161">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="470e9-162">특정 개체에 대해 작업 하는 경우 헤드 게이즈 커서 변경 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-162">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="470e9-163">I/I 조치를 취할 때 시청각 확인을 들.</span><span class="sxs-lookup"><span data-stu-id="470e9-163">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="470e9-164"><a href="hands-free.md">핸 즈 (헤드 게이즈 및 유지)</a></span><span class="sxs-lookup"><span data-stu-id="470e9-164"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="470e9-165">보기 내 필드의 가운데에 커서를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-165">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="470e9-166">부분 있습니까 상호 작용할 수 없는 개체에 고민 하는 경우 진행률 표시기가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-166">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="470e9-167">I/I 조치를 취할 때 시청각 확인을 들.</span><span class="sxs-lookup"><span data-stu-id="470e9-167">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="470e9-168"><a href="hands-free.md">핸 즈 프리 (음성 명령 실행)</a></span><span class="sxs-lookup"><span data-stu-id="470e9-168"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="470e9-169">수신 대기 표시기 및 캡션을 시스템 들어 본 적 표시 하는 것이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-169">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="470e9-170">내가 음성 안내 및 힌트.</span><span class="sxs-lookup"><span data-stu-id="470e9-170">I get voice prompts and hints.</span></span>  <span data-ttu-id="470e9-171">"어떤 말할 수 있는" 말하는 경우</span><span class="sxs-lookup"><span data-stu-id="470e9-171">When I say "what can I say?"</span></span> <span data-ttu-id="470e9-172">사용자 의견을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-172">I see feedback.</span></span></td>
        <td><span data-ttu-id="470e9-173">I/명령을 제공 하거나 필요할 때 UX 명확성을 가져올 때 시청각 확인을 듣고 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-173">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="470e9-174">찾았습니다. 도움말 팀 선택 상호 작용 모델을 질문에는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-174">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="470e9-175">Q:  사용자에 게 홀로그램 touch 및 전체 자릿수 holographic 조작을 수행 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="470e9-175">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="470e9-176">A:  만약 그렇다면 전체 자릿수가 대상 지정 및 실습 또는 동작 컨트롤러를 사용 하 여 조작에 대 한 실습 및 도구 상호 작용 모델 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-176">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="470e9-177">Q:  내 사용자가 실제 작업에 대 한 무료가 바늘을 유지 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="470e9-177">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="470e9-178">A:  그렇다면 살펴보겠습니다 핸 즈 프리 상호 작용 하는 모델을 응시 및 음성 기반 상호 작용을 통해 유용한 핸 즈 프리 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-178">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="470e9-179">Q:  내 사용자가 혼합된 현실 응용 프로그램에 대 한 상호 작용을 배울 시간이 없거나 필요도 가장 낮은 학습 곡선을 사용 하 여 상호 작용 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="470e9-179">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="470e9-180">A:  사용자 상호 작용에 대 한 대응을 사용할 수 없게 되는 가장 낮은 학습 곡선 및 가장 직관적인 상호 작용에 대 한 실습 및 도구 모델을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-180">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="470e9-181">Q:  내 사용자가 가리키는 및 조작에 대 한 동작 컨트롤러를 사용 합니까?</span><span class="sxs-lookup"><span data-stu-id="470e9-181">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="470e9-182">A:  실습 및 도구 모델 동작 컨트롤러 환경을 개선에 대 한 모든 지침을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-182">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="470e9-183">Q:  내 사용자는 내게 필요한 옵션 컨트롤러나를 clicker 같은 일반적인 Bluetooth 컨트롤러를 사용 하려면?</span><span class="sxs-lookup"><span data-stu-id="470e9-183">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="470e9-184">A:  모든 비 추적 컨트롤러에 대 한 헤드 게이즈 모델과 커밋 모델을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-184">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="470e9-185">간단한 "대상 및 커밋" 정비공을 사용 하 여 전체 환경을 통과 하는 사용자를 허용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-185">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="470e9-186">Q: 내 사용자만 진행 마세요 환경을 통해 "를 클릭 하 여" (예를 들어 환경의 3d 슬라이드쇼), UI 컨트롤의 짙은 레이아웃을 탐색 하는 대신?</span><span class="sxs-lookup"><span data-stu-id="470e9-186">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="470e9-187">A:  사용자 UI 많은 제어 하지 않아도, 헤드 게이즈 및 커밋 사용자를 대상으로 하는 방법에 대 한 걱정 없는 수행 learnable 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-187">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="470e9-188">Q:  내 사용자가 모두 HoloLens 사용 (첫 번째 gen) 및 HoloLens 2 / Windows 몰입 형 (VR 헤드셋)</span><span class="sxs-lookup"><span data-stu-id="470e9-188">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="470e9-189">A:  헤드 게이즈 및 커밋에 HoloLens에 대 한 상호 작용 모델 이므로 (첫 번째 gen) 좋습니다 HoloLens를 지 원하는 작성자 (첫 번째 gen) Head 게이즈를 사용 하 고 모든 기능 또는 사용자는 HoloLens에 발생할 수 있는 모드에 대 한 커밋을 (첫 번째 gen) 헤드셋 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-189">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="470e9-190">아래 다음 섹션을 참조 하십시오 온 *상호 작용 모델을 전환* 여러 HoloLens 세대에 대 한 뛰어난 환경을 만들기 위해 세부 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-190">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="470e9-191">Q: (많은 공간을 다루는 또는 공간 간에 이동), 일반적으로 모바일 사용자에 게 어떤 작업에 대 한 단일 공간에서 작동 하는 사용자와?</span><span class="sxs-lookup"><span data-stu-id="470e9-191">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="470e9-192">A:  이러한 사용자에 대 한 상호 작용 모델의 모든 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-192">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="470e9-193">앱 디자인에 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-193">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="470e9-194">전환 상호 작용 모델</span><span class="sxs-lookup"><span data-stu-id="470e9-194">Transition interaction models</span></span>
<span data-ttu-id="470e9-195">둘 이상의 상호 작용 모델을 활용 하는 사용 사례에 필요할 수 있습니다 위치 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-195">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="470e9-196">예를 들어 흐름 앱의 "만들기" 실습 및 도구 상호 작용 모델을 활용 하지만 핸 즈 프리 모드 적용 되어 현장 기술자를 사용 하려는.</span><span class="sxs-lookup"><span data-stu-id="470e9-196">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="470e9-197">환경을 여러 상호 작용 모델에 필요 하 고, 많은 최종 사용자가 특히 최종 사용자가 접하는 MR-다른 모델에서 전환 하는 데 문제가 발생할 수 있습니다를 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-197">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="470e9-198">가이드 디자이너 및 MR의 어려울 수 있는 선택 항목을 통해 개발자를 위해 여러 상호 작용 모델을 사용 하기 위한 자세한 지침에 최선을 다하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="470e9-198">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="470e9-199">참조</span><span class="sxs-lookup"><span data-stu-id="470e9-199">See also</span></span>
* [<span data-ttu-id="470e9-200">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="470e9-200">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="470e9-201">직접 조작</span><span class="sxs-lookup"><span data-stu-id="470e9-201">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="470e9-202">지점 및 커밋</span><span class="sxs-lookup"><span data-stu-id="470e9-202">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="470e9-203">응시 대상 지정</span><span class="sxs-lookup"><span data-stu-id="470e9-203">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="470e9-204">제스처</span><span class="sxs-lookup"><span data-stu-id="470e9-204">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="470e9-205">음성 디자인</span><span class="sxs-lookup"><span data-stu-id="470e9-205">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="470e9-206">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="470e9-206">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="470e9-207">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="470e9-207">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="470e9-208">공간 매핑 디자인</span><span class="sxs-lookup"><span data-stu-id="470e9-208">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="470e9-209">편안함</span><span class="sxs-lookup"><span data-stu-id="470e9-209">Comfort</span></span>](comfort.md)
