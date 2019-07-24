---
title: HoloLens의 계정
description: HoloLens에서 사용자 계정을 설정 하 고 관리 하는 방법입니다.
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 사용자, 계정, aad, adfs, microsoft 계정, msa, 자격 증명
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516819"
---
# <a name="accounts-on-hololens"></a>HoloLens의 계정

초기 HoloLens를 설정 하는 동안 사용자는 장치에서 사용 하려는 계정으로 로그인 해야 합니다. 이 계정은 소비자 Microsoft 계정 또는 Azure Active Directory (AAD) 또는 Active Directory Federation Services (ADFS)에서 구성 된 엔터프라이즈 계정일 수 있습니다.

설치 하는 동안이 계정에 로그인 하면 사용자가 로그인 하는 데 사용할 수 있는 장치에 사용자 프로필이 생성 되며 모든 앱에서 해당 데이터를 저장 합니다. 이 동일한 계정은 Windows 계정 관리자 Api를 통해 Edge 또는 Skype와 같은 앱에 대 한 Single Sign-on도 제공 합니다.

또한 장치에서 엔터프라이즈 또는 조직 계정에 로그인 하는 경우 IT 관리자가 구성한 경우 MDM (모바일 장치 관리) 정책을 적용할 수도 있습니다.

장치가 다시 시작 되거나 대기 상태에서 다시 시작 될 때마다이 계정에 대 한 자격 증명을 사용 하 여 다시 로그인 합니다. 설정에서 명시적인 로그인을 적용 하는 옵션을 사용 하도록 설정한 경우 사용자가 자격 증명을 다시 입력 해야 합니다. OS 업데이트를 받아서 적용 한 후 장치가 다시 시작 될 때마다 명시적인 로그인이 필요 합니다.

## <a name="multi-user-support"></a>다중 사용자 지원

>[!NOTE]
>다중 사용자 지원 [에는 비즈니스용 Windows Holographic](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) 기능이 필요 하므로 상용 Suite가 필요 합니다.

[Windows 10 4 월 2018 업데이트](release-notes-april-2018.md)부터 HoloLens는 동일한 AAD 테 넌 트 내에서 여러 사용자를 지원 합니다. 이를 사용 하려면 먼저 조직에 속한 계정으로 장치를 설정 해야 합니다. 이후에는 동일한 테 넌 트의 다른 사용자가 로그인 화면에서 장치에 로그인 하거나 시작 패널에서 사용자 타일을 눌러 기존 사용자를 로그 아웃할 수 있습니다. 

장치에 설치 된 앱은 다른 모든 사용자가 사용할 수 있지만 각 사용자는 자신의 앱 데이터 및 기본 설정을 갖습니다. 앱을 제거 하면 다른 모든 사용자도 제거 됩니다. 

설정 > 계정 > 다른 사용자로 이동 하 여 장치에서 장치 사용자를 제거 하 여 공간을 회수할 수 있습니다. 그러면 장치에서 다른 모든 사용자의 앱 데이터도 제거 됩니다. 

## <a name="linked-accounts"></a>연결 된 계정

단일 장치 계정 내에서 사용자는 앱 내에서 더 쉽게 액세스할 수 있도록 추가 웹 계정 자격 증명을 연결 하거나 (예: 스토어) 개인 및 회사 리소스에 대 한 액세스를 결합할 수 있습니다. 이러한 방식으로 추가 계정에 로그인 하면 이미지 또는 다운로드와 같이 장치에서 만들어진 사용자 데이터를 구분 하지 않습니다. 계정이 장치에 연결 되 면 앱은 각 앱에 개별적으로 로그인 할 필요가 없도록 사용자의 사용 권한으로 앱을 사용할 수 있습니다.

## <a name="using-single-sign-on-within-an-app"></a>앱 내에서 single sign-on 사용

앱 개발자는 다른 Windows 장치와 마찬가지로 [Windows 계정 관리자 api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)를 사용 하 여 HoloLens에 연결 된 id를 사용 하는 이점을 활용할 수 있습니다. 이러한 Api에 대 한 일부 코드 샘플은 [여기](http://go.microsoft.com/fwlink/p/?LinkId=620621)에서 사용할 수 있습니다.

앱에서 인증 토큰을 요청할 때 계정 정보, 2 단계 인증 등에 대 한 사용자 동의를 요청 하는 등 발생할 수 있는 모든 계정 인터럽트가 처리 되어야 합니다.

앱에 이전에 연결 되지 않은 특정 계정 유형이 필요한 경우 앱에서 사용자에 게 사용자에 게 메시지를 추가 하 라는 메시지를 표시 하도록 요청할 수 있습니다. 그러면 계정 설정 창이 앱의 모달 자식으로 시작 됩니다. 2D 앱의 경우이 창은 앱의 중앙에서 직접 렌더링 하 고 Unity 앱의 경우이 창을 holographic 앱에서 잠깐 이동 하 여이 자식 창을 렌더링할 수 있습니다. 이 창에서 명령 및 동작을 사용자 지정 하는 방법은 [여기](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)에 설명 되어 있습니다.

## <a name="enterprise-and-other-authentication"></a>엔터프라이즈 및 기타 인증

앱에서 NTLM, 기본 또는 Kerberos와 같은 다른 형식의 인증을 사용 하는 경우 [Windows 자격 증명 UI](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) 를 사용 하 여 사용자의 자격 증명을 수집, 처리 및 저장할 수 있습니다. 이러한 자격 증명을 수집 하는 사용자 환경은 다른 클라우드 기반 계정 인터럽트와 매우 비슷하며, 2D 앱 위에 자식 앱으로 표시 되거나, UI를 표시 하기 위해 Unity 앱을 잠깐 일시 중단 합니다.

## <a name="deprecated-apis"></a>사용 되지 않는 Api

Desktop에서 HoloLens를 개발할 때의 한 가지 차이점은 [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API는 완전히 지원 되지 않는다는 것입니다. 기본 계정이 양호 하면 토큰을 반환 하지만 위에 설명 된 것과 같은 인터럽트는 사용자에 대 한 UI를 표시 하지 않으며 계정을 올바르게 인증 하지 못합니다.

