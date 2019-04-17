---
title: HoloLens에서 계정
description: 설정 하 고 HoloLens에 사용자 계정을 관리 하는 방법입니다.
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 사용자, 계정, aad, adfs, microsoft 계정, msa, 자격 증명
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599830"
---
# <a name="accounts-on-hololens"></a>HoloLens에서 계정

초기 HoloLens 설치 하는 동안 사용자가 장치에서 사용 하려는 계정으로 로그인 해야 합니다. 이 계정은 소비자 Microsoft 계정 또는 Azure Active Directory (AAD) 또는 Active Directory Federation Services (ADFS)에서 구성 된 엔터프라이즈 계정 수 있습니다.

사용자를 사용할 수 있는 장치에서 사용자 프로필을 생성 설치 하는 동안이 계정에 로그인 합니다. 로그인 하 고 있는 모든 앱은 해당 데이터를 저장 하는 것에 대 한 합니다. 이 계정을 Edge 또는 Windows 계정 관리자 Api를 통해 Skype와 같은 앱에 대 한 Single Sign On도 제공합니다.

또한 기업 또는 장치에서 조직 계정에 로그인 하는 경우이 적용 될 수 모바일 장치 관리 (MDM) 정책을 IT 관리자가 구성 된 경우

장치 다시 시작 또는 대기 모드에서 다시 시작 될 때마다이 계정에 대 한 자격 증명을 로그인에 다시 사용 됩니다. 명시적 로그인 적용 옵션 설정에서 활성화 되어, 사용자가 자격 증명 다시 입력 해야 합니다. 장치가 수신 하 고 OS 업데이트를 적용 한 후 다시 시작 되 면 언제 든 지는 명시적 로그인이 필요 합니다.

## <a name="multi-user-support"></a>다중 사용자 지원

>[!NOTE]
>이 다중 사용자 지원 필요는 Commercial Suite를 [Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) 기능입니다.

로 시작 합니다 [Windows 10 2018 년 4 월 업데이트](release-notes-april-2018.md), HoloLens 동일한 AAD 테 넌 트 내에서 여러 사용자를 지원 합니다. 이 사용 하려면 조직에 속해 있는 계정으로 처음으로 장치 설정 해야 합니다. 이후에 동일한 테 넌 트에서 다른 사용자가 기존 사용자 로그 아웃 시작 패널의 사용자 타일을 탭 하거나 로그인 화면에서 장치에 로그인 됩니다. 

장치에 설치 하는 앱을 다른 모든 사용자에 게 사용할 수 있지만 각각 자신의 앱 데이터 및 기본 설정을 갖게 됩니다. 앱 제거도 제거 됩니다 다른 모든 사용자에 대 한 하지만. 

설정으로 이동 하 여 공간을 확보 하려면 장치에서 장치 사용자를 제거할 수 있습니다 > 계정 > 다른 사용자입니다. 다른 사용자의 앱 데이터의 모든 장치에서 제거 됩니다이 있습니다. 

## <a name="linked-accounts"></a>연결 된 계정

사용자는 단일 장치 계정 내에서 추가 웹 계정 자격 증명 (예: 저장소)는 앱 내에서 쉽게 액세스 하기 위해 연결할 수 있습니다 또는 Windows의 데스크톱 버전 유사한 개인 및 회사 리소스에 대 한 액세스를 결합 합니다. 이러한 방식으로 추가 계정에 로그인 이미지와 같은 장치에서 만든 사용자 데이터를 구분 하지 않습니다 또는 다운로드 합니다. 앱 계정을 장치에 연결 되 면 가능 개별적으로 각 앱에 로그인 할 필요를 줄이기 위해 사용자의 권한으로 사용 합니다.

## <a name="using-single-sign-on-within-an-app"></a>앱 내에서 single sign-on 사용

앱 개발자는 연결 된 id를 사용 하 여 HoloLens에 이점이 걸리므로 합니다 [Windows 계정 관리자 Api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx), 동일한 방식으로 다른 Windows 장치에서. 이러한 Api에 대 한 몇 가지 코드 샘플이 제공 됩니다 [여기](http://go.microsoft.com/fwlink/p/?LinkId=620621)합니다.

계정 정보에 대 한 동의 요청 하는 사용자와 같은 발생할 수 있는 모든 계정 인터럽트, 앱에서 인증 토큰을 요청 하는 경우 2 단계 인증 등을 처리 해야 합니다.

앱에서 이전에 연결 되지 않은 하는 특정 계정 형식에 필요한 경우 하나를 추가 하려면 사용자 메시지를 표시 하려면 앱에 요청할 수 있습니다. 이렇게 하면 앱의 모달 자식 항목으로 시작 계정 설정 창이 트리거됩니다. 2D 앱의 경우이 창을 센터 앱 및 Unity 앱을 통해 직접 렌더링 됩니다, 그리고 간단 하 게 이렇게 holographic 앱에서 사용자가 자식 창을 렌더링할 수 있도록 합니다. 명령 및이 창에 대 한 작업을 사용자 지정 설명 [여기](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)합니다.

## <a name="enterprise-and-other-authentication"></a>엔터프라이즈 및 기타 인증

앱이 실행 하면 경우 다른 유형의 인증을 사용 하 여, 예: NTLM, Basic 또는 Kerberos를 사용할 수 있습니다 [Windows 자격 증명 UI](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) 수집, 처리 및 사용자의 자격 증명을 저장 합니다. 이러한 자격 증명을 수집 하는 것에 대 한 사용자 환경을 다른 클라우드 기반 계정을 인터럽트에 매우 비슷합니다 및 2D 앱을 기반으로 자식 앱으로 표시 또는 간단 하 게 UI를 표시 하려면 Unity 앱을 일시 중단 됩니다.

## <a name="deprecated-apis"></a>사용 되지 않는 Api

데스크톱에서 HoloLens에 개발을 위한 한 가지 차이점 [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API 완전히 지원 되지 않습니다. 와 같은 중단 기본 계정이 올바른-고정 하는 경우 토큰을 반환 하지만 사용자에 대 한 모든 UI를 표시 하지 않습니다 위에 설명 된 내용과 및 계정이 올바르게 인증 되지 않습니다.

