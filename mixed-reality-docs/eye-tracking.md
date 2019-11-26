---
title: 시선 추적
description: HoloLens 2 allows for a new level of context and human understanding within the holographic experience by providing developers with the ability to use information about what the user is looking at.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Eye tracking, mixed reality, input, eye-gaze, calibration
ms.openlocfilehash: 1f3699330fb4879258693b6959724441bd838d98
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491146"
---
# <a name="eye-tracking-on-hololens-2"></a>HoloLens 2의 시선 추적

![Eye tracking demo in MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 allows for a new level of context and human understanding within the holographic experience by providing developers with the ability to use information about what the user is looking at. This page explains how developers can benefit from eye tracking for various use cases, as well as what to look for when designing eye-gaze-based user interactions. 

Eye tracking API has been designed with a user’s privacy in mind, avoiding passing any identifiable information, particularly any biometrics. For eye-tracking capable applications, the user needs to grant app permission to use eye tracking information. 


### <a name="device-support"></a>장치 지원
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Feature</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
</tr>
<tr>
     <td>Eye-gaze</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="calibration"></a>Calibration 
For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](calibration.md) for which the user has to look at a set of holographic targets. This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time. 

Eye tracking should work for most users, but there are rare cases in which a user might not be able to calibrate successfully. Calibration might fail for various reasons, including but not limited to: 
* The user previously opted out of the calibration process
* The user got distracted and didn't follow the calibration targets
* The user has certain types of contact lenses and glasses which the system doesn't yet support 
* The user has certain eye physiology, eye conditions or had eye surgery which the system doesn't yet support  
* External factors inhibiting reliable eye tracking such as smudges on the HoloLens visor or eyeglasses, intense direct sunlight and occlusions due to hair in front of the eyes

Developers should make sure to provide adequate support for users for whom eye tracking data may not be available (who are not able to calibrate successfully). We have provided recommendations for fallback solutions in the section at the bottom of this page. 

To learn more about the calibration and about how to ensure a smooth experience, please check our [eye tracking user calibration](calibration.md) page.

<br>

## <a name="available-eye-tracking-data"></a>Available eye tracking data
Before going into detail about specific use cases for eye-gaze input, we want to briefly point out the capabilities that the HoloLens 2 [Eye Tracking API](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose) provides. Developers get access to a single eye-gaze ray (gaze origin and direction) at approximately _30 FPS (30 Hz)_ .
For more detailed information about how to access eye tracking data, please refer to our developer guides for using [eye-gaze in DirectX](gaze-in-directx.md) and [eye-gaze in Unity](https://aka.ms/mrtk-eyes).

The predicted eye-gaze is approximately within 1.5 degrees in visual angle around the actual target (see the illustration below). As slight imprecisions are expected, developers should plan for some margin around this lower-bound value (e.g., 2.0-3.0 degrees may result in a much more comfortable experience). We will discuss how to address the selection of small targets in more detail below. 시선 추적이 정확히 작동하려면 각 사용자가 시선 추적 사용자 보정을 진행해야 합니다. 

![2m 거리에서 최적 대상 크기](images/gazetargeting-size-1000px.jpg)<br>
*Optimal target size at a 2-meter distance*

<br>

## <a name="use-cases"></a>사용 사례
시선 추적을 사용하여 애플리케이션에서는 사용자가 실시간으로 보는 곳을 추적할 수 있습니다. The following use cases describe some interactions that are possible with eye tracking on HoloLens 2 in mixed reality.
Please note that these use cases are not yet part of the Holographic Shell experience (i.e., the interface that you see when you start up your HoloLens 2).
You can try some of them in the [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html), which provides several interesting and powerful examples for using eye tracking, such as quick and effortless eye-supported target selections, as well as automatically scrolling through text based on what the user looks at. 

### <a name="user-intent"></a>사용자 의도    
Information about where and what a user looks at provides a powerful **context for other inputs**, such as voice, hands and controllers.
이러한 컨텍스트를 다양한 작업에서 사용할 수 있습니다.
For example, this can range from quickly and effortlessly **targeting** across the scene by simply looking at a hologram and saying *"select"* (also see [gaze and commit](gaze-and-commit.md)) or *"put this..."* , then looking over to where the user wants to place the hologram and say *"...there"* . 이에 대한 예는 [Mixed Reality Toolkit - 시선 지원 대상 선택](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) 및 [Mixed Reality Toolkit - 시선 지원 대상 위치 지정](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html)에서 찾을 수 있습니다.

Additionally, an example for user intent might include using information about what users look at to enhance engagement with embodied virtual agents and interactive holograms. For instance, virtual agents might adapt available options and their behavior, based on currently viewed content. 

### <a name="implicit-actions"></a>암시적 작업
암시적 작업의 범주는 사용자 의도와 밀접하게 관련되어 있습니다.
The idea is that holograms or user interface elements react in an instinctual way that may not even feel like the user is interacting with the system at all, but rather that the system and the user are in sync. One example is **eye-gaze-based auto scroll** where the user can read a long text which automatically starts scrolling once the user gets to the bottom of the textbox to keep the user in the flow of reading, without lifting a finger.  
A key aspect of this is that the scrolling speed adapts to the reading speed of the user.
Another example is **eye-supported zoom and pan** where the user can feel like diving exactly toward what he or she is focused on. Triggering and controlling zoom speed can be controlled by voice or hand input, which is important for providing the user with the feeling of control while avoiding being overwhelmed. We will talk about these design considerations in more detail below. Once zoomed in, the user can smoothly follow, for example, the course of a street to explore his or her neighborhood by simply using their eye-gaze.
이러한 유형의 상호 작용을 나타내는 데모 예제는 [Mixed Reality Toolkit - 시선 지원 탐색](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) 샘플에서 찾을 수 있습니다.

_암시적 작업_의 추가 사용 사례로는 다음이 포함될 수 있습니다.
- **Smart notifications:** Ever get annoyed by notifications popping up right where you are looking? Taking into account what a user is paying attention to, you can make this experience better by offsetting notifications from where the user is currently gazing. This limits distractions and automatically dismisses them once the user is finished reading. 
- **Attentive holograms:** Holograms that subtly react when being gazed upon. This can range from slightly glowing UI elements, a slowly blooming flower to a virtual dog starting to look back at the user and wagging its tail. This interaction might provide an interesting sense of connectivity and satisfaction in your application.

### <a name="attention-tracking"></a>주의 추적   
Information on where or what users look at can be an immensely powerful tool. It can help assess usability of designs and identify problems in workflows to make them more efficient.
Eye tracking visualization and analytics are a common practice in various application areas. With HoloLens 2, we provide a new dimension to this understanding as 3D holograms can be placed in real-world contexts and assessed accordingly. The [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) provides basic examples for logging and loading eye tracking data and how to visualize them.
Microsoft is dedicated to facilitating innovation while ensuring that users have an informed and transparent experience with how their eye tracking information is used.  We will work with our developers and UX teams to provide guidance for third parties to ensure that experiences are centered around the user.  


이 영역의 다른 응용 분야로 다음이 포함될 수 있습니다. 
-   **Remote eye-gaze visualization:** Remote eye-gaze visualizations: Visualize what remote collaborators are looking at, to be able to provide immediate feedback and facilitate more accurate information processing.
-   **User research studies:** Attention tracking can help researchers get more insights into how users perceive and engage with the natural environment, without interfering, to design more instinctual human-computer-interactions. Eye tracking can provide information that is not directly articulated by participants in the study, which otherwise might be easily missed by the researcher. 
-   **Training and performance monitoring:** Practice and optimize the execution of tasks by identifying bottlenecks more effectively in the execution flow. Eye tracking can provide natural, real-time and objective information to help improve training, productivity, and safety in the workplace. 
-   **Design evaluations, marketing and consumer research:** Eye tracking enables commercial companies to perform marketing and consumer studies in real-world environments or analyze what captures a user’s attention to improve product or space design. 

### <a name="additional-use-cases"></a>추가 사용 사례
- **Gaming:** Ever wanted to have superpowers? 여기서 그 기회를 얻을 수 있습니다. You can levitate holograms by staring at them. Shoot laser beams from your eyes - try it out in [RoboRaid for HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j).
Turn enemies into stone or freeze them. X-광선을 사용해서 건물을 투시하세요. 상상하는 만큼 이루어집니다.
Beware of not overwhelming the user though - to find out more, check out our [eye-gaze-based input design guidelines](eye-gaze-interaction.md).

- **Expressive avatars:** Eye tracking aids in more expressive 3D avatars by using live eye tracking data to animate the avatar's eyes that indicate what the user is looking at. 

- **Text entry:** Eye tracking can be used as an alternative for low-effort text entry, especially when speech or hands are inconvenient to use. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Using eye-gaze for interaction
Building an interaction that takes advantage of fast-moving eye targeting can be challenging.
On the one hand, the eyes move so fast that you need to be careful on how to use eye-gaze input, because otherwise users may find the experience overwhelming or distracting. On the other hand, you can also create truly magical experiences that will excite your users! To help you, check out our overview of key advantages, challenges and design recommendations for [eye-gaze for interaction](eye-gaze-interaction.md). 
 
## <a name="fallback-solutions-when-eye-tracking-is-not-available"></a>Fallback solutions when eye tracking is not available

In rare cases, eye tracking data might not be available.
This can be due to different reasons from which the most common are listed below:
* The system failed to [calibrate the user](calibration.md).
* The user skipped the [calibration](calibration.md).   
* The user is calibrated, but decided to not give permission to your app to use their eye tracking data.    
* The user has unique eyeglasses or some eye condition that the system does not yet support.    
* External factors inhibiting reliable eye tracking such as smudges on the HoloLens visor or eyeglasses, intense direct sunlight and occlusions due to hair in front of the eyes.   

Hence, developers should ensure that there is appropriate fallback support for these users. On the [Eye Tracking in DirectX](gaze-in-directx.md#fallback-when-eye-tracking-is-not-available) page, we explain the APIs required to detect whether eye tracking data is available. 

While some users may have consciously decided to revoke access to their eye tracking data and are ok with the trade-off of an inferior user experience to the privacy of not providing access to their eye tracking data, in some cases this may be unintentional.  
Hence, if your app uses eye tracking, and this is an important part of the experience, we recommend clearly communicating this to the user.     
Kindly informing the user why eye tracking is critical for your application (maybe even listing some enhanced features) to experience the full potential of your application, can help the user to better understand what they are giving up.   
Help the user identify why eye tracking may not be working (based on the above checks) and offer some suggestions to quickly troubleshoot potential issues.     
For example, if you can detect that the system supports eye tracking, the user is calibrated and has even given their permission, yet no eye tracking data is received, then this may point to some other issues such as smudges or the eyes being occluded.    
Please note that there are rare cases of users for whom eye tracking may simply not work.   
Hence, please be respectful of that by allowing to dismiss or even disable reminders for enabling eye tracking in your app.

### <a name="fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Fallback for apps using eye-gaze as a primary input pointer
If your app uses eye-gaze as a pointer input to quickly select holograms across the scene, yet eye tracking data is unavailable, we recommend falling back to head-gaze and start showing the head-gaze cursor. We recommend using a timeout (e.g., 500–1500 ms) to determine whether to switch or not. This action prevents cursors from appearing every time the system may briefly lose tracking due to fast eye motions or winks and blinks. If you are a Unity developer, the automatic fallback to head-gaze is already handled in the Mixed Reality Toolkit. If you are a DirectX developer, you need to handle this switch yourself.

### <a name="fallback-for-other-eye-tracking-specific-applications"></a>Fallback for other eye-tracking-specific applications
Your app may use eye-gaze in a unique way that is tailored specifically to the eyes. For example, animating an avatar’s eyes or for eye-based attention heatmaps relying on precise information about visual attention. In this case, there is no clear fallback. If eye tracking is not available, these capabilities may simply need to be disabled.
Again, we recommend to clearly communicate this to the user who may be unaware that the capability is not working.

<br>

This page has hopefully provided you with a good overview to get you started understanding the role of eye tracking and eye-gaze input for HoloLens 2. To get started developing, check out our information on the role of [eye-gaze for interacting with holograms](eye-gaze-interaction.md), [eye-gaze in Unity](https://aka.ms/mrtk-eyes) and [eye-gaze in DirectX](gaze-in-directx.md).


## <a name="see-also"></a>참고 항목
* [조정](calibration.md)
* [편안함](comfort.md)
* [시선 응시 기반 상호 작용](eye-gaze-interaction.md)
* [Eye-gaze in DirectX](gaze-in-directx.md)
* [Eye-gaze in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [응시 및 커밋](gaze-and-commit.md)
* [음성 입력 ](voice-design.md)


