---
title: 영향을 주는 지침
description: Windows Mixed Reality 설명서에 기여 하는 방법입니다.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604652"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Windows Mixed Reality 개발자 설명서에 기여

시작 합니다 [Windows Mixed Reality 개발자 설명서에 대 한 공용 리포지토리](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)! 만들기 또는 편집이 리포지토리의 모든 문서 **공개적으로 표시 됩니다.** 

Windows Mixed Reality docs (Markdig 기능)와 GitHub 지원 Markdown을 사용 하는 docs.microsoft.com 플랫폼에서 됩니다. 에 표시 되는 서식이 지정 되 고 스타일이 지정 된 페이지에이 리포지토리에서 편집 내용을 설정 기본적 https://docs.microsoft.com/windows/mixed-reality합니다. 

이 페이지 기본 단계 및 영향을 주는에 대 한 지침 뿐만 아니라 Markdown 기본 사항에 연결 합니다. 작성 글을 주셔서 감사 합니다!

## <a name="before-you-start"></a>시작하기 전 주의 사항

해야 하면 이미 계정이 없는 경우 [GitHub 계정을 만듭니다](https://github.com/join)합니다.

>[!NOTE]
>가 Microsoft 직원인 경우 GitHub 계정에 Microsoft 별칭에 연결 합니다 [Microsoft 오픈 소스 포털](https://repos.opensource.microsoft.com/)합니다. 조인 합니다 **"Microsoft"** 하 고 **"MicrosoftDocs"** 조직).

GitHub 계정에 설정 하는 경우 이러한 보안 예방 조치를 좋습니다.
- 만들기는 [Github 계정에 대 한 강력한 암호](https://github.com/settings/admin)합니다.
- 사용 하도록 설정 [2 단계 인증](https://github.com/settings/two_factor_authentication/configure)합니다.
- 저장 하 [복구 코드](https://github.com/settings/auth/recovery-codes) 안전한 곳에 있습니다.
- 업데이트 프로그램 [공개 프로필 설정은](https://github.com/settings/profile)합니다.
   - 사용자 이름을 설정 하 고 설정을 고려 하 *공용 메일* 를 *내 전자 메일 주소를 표시 안 함*합니다.
   - 사용자가 참여 하는 문서 페이지의 축소판 그림과 같이 프로필 사진을 업로드 것이 좋습니다.
- 명령줄 워크플로 사용 하려는 경우를 설정 하십시오 [Windows 용 Git 자격 증명 관리자](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) 기 고물 할 때마다 암호를 입력 하지 않아도 되도록 합니다.

다음이 단계를 수행 하는 것이 중요 합니다 게시 시스템은 GitHub에 연결 하 고 작성자 또는 참여자 GitHub 별칭을 사용 하 여 각 문서에 나열 됩니다.

## <a name="editing-an-existing-article"></a>기존 문서 편집

에 대 한 업데이트를 위해 다음 워크플로를 사용 *기존 아티클을* 웹 브라우저에서 GitHub를 통해:

1. "혼합 현실-문서" 폴더에서 편집 하려는 문서를 탐색 합니다.
2. 오른쪽 위에 있는 편집 단추 (연필 아이콘)를 선택 합니다. 자동으로 '마스터' 분기를 삭제할 수 있는 분기를 분기는이 합니다.

   ![문서를 편집 합니다.](images/editpage.png)
3. 문서의 콘텐츠를 편집 (참고 ["Markdown 기본 사항"](#markdown-basics) 아래 지침에 대 한).
4. 각 문서의 맨 위에 있는 관련 메타 데이터를 업데이트 합니다.
   * 제목: 문서를 보고 하는 경우 브라우저 탭에 표시 되는 페이지 제목입니다. 하지 않는 한 제목을 변경 하지 않아야 SEO 및 인덱싱에 대 한이 사용 되는, (있지만 이것이 덜 중요 한 문서 공개 되기 전에) 필요 합니다.
   * description: 간략 한 설명은 항목의 콘텐츠를 작성 합니다. 이 따른 SEO 및 검색에 도움이 됩니다.
   * 작성자: 페이지의 기본 소유자 라면 여기 GitHub 별칭을 추가 합니다.
   * ms.author: 페이지의 기본 소유자 인 경우 추가 Microsoft 별칭 여기 (필요가 @microsoft.com, 별칭만).
   * ms.date: 문법, 서식 지정, 설명이 같은 수정 하지 않고 페이지에서 주요 콘텐츠를 추가 하거나 맞춤법 검사 하는 경우 날짜를 업데이트 합니다.
   * 키워드: 키워드는 SEO (검색 엔진 최적화)에 도움이 됩니다. 쉼표 및 공백을 구분 하 여, 문서 (하지만 마지막 키워드 목록에 다음 문장 부호 없는); 관련 된 키워드 추가 다른 곳에서 관리 되는 것, 모든 문서에 적용 되는 전역 키워드를 추가할 필요가 없습니다. 
5. 문서 편집을 완료 한 경우 아래로 스크롤하여을 클릭 합니다 **파일 변경 내용 제안** 단추입니다.
6. 다음 페이지에서 클릭 **끌어오기 요청 만들기** 'master'. 자동으로 만들어진 분기 병합
7. 편집 하려면 다음 문서에 대 한 위의 단계를 반복 합니다.

## <a name="creating-a-new-article"></a>새 문서 만들기

다음 워크플로를 사용 하 여 *새 문서를 만들* 웹 브라우저에서 GitHub 통해 설명서 리포지토리에서:

1. MicrosoftDocs/혼합 현실 '마스터' 분기는 분기를 만듭니다 (사용 하는 **포크** 오른쪽 위에 있는 단추).

   ![마스터 분기를 포크 합니다.](images/forkbranch.png)
2. "혼합 현실-문서" 폴더를 클릭 합니다 **새 파일 만들기** 오른쪽 위에 있는 단추입니다.
3. 아티클에 대 한 페이지 이름을 만듭니다 (하이픈을 사용 하 여 공백 대신 및 문장 부호 또는 아포스트로피 사용 하지 마세요) 및 ".md"를 추가 합니다.

   ![새 페이지를 이름을 지정 합니다.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >"혼합 현실-문서" 폴더 내에서 새 항목을 만드는 하는지 확인 합니다. 확인 하 여이 확인할 수 있습니다 "혼합 현실-문서 / /" 새 파일 이름 줄에서.

4. 새 페이지의 맨 위에 있는 다음 메타 데이터 블록을 추가 합니다.

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. 지침에 따라 관련 메타 데이터 필드를 입력 합니다 [위의 섹션](#editing-an-existing-article)합니다.
6. 쓰기 문서 콘텐츠를 사용 하 여 [Markdown 기본 사항](#markdown-basics)합니다.
7. 추가 된 `## See also` 다른 관련 된 문서에 대 한 링크를 사용 하 여 문서의 맨 아래에 섹션입니다.
8. 완료 되 면, 클릭 **커밋 새 파일**합니다.
9. 클릭 **새 끌어오기 요청** MicrosoftDocs/혼합 현실 '마스터' 분기의 '마스터' 분기 병합 및 (화살표는 올바른 방법은 가리키고 있는지 확인).

   ![MicrosoftDocs/혼합 현실에 포크에서 끌어오기 요청 만들기](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Markdown 기본 사항

다음 리소스를 사용 하는 Markdown 언어를 사용 하 여 문서를 편집 하는 방법을 알아봅니다 도움이 됩니다.

- [Markdown 기본 사항](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown에서-요약 참조 포스터](images/MarkdownPoster.pdf)
- [Docs.microsoft.com 용 Markdown 작성을 위한 추가 리소스](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>테이블 추가

방법은 docs.microsoft.com 스타일 테이블이 없기 테두리 또는 사용자 지정 스타일을 인라인 CSS를 시도 하는 경우에 합니다. 짧은 기간에 대해 작동 하는 것이 나타납니다. 하지만 결국 플랫폼에서는 테이블에서 외부 스타일을 제거 합니다. 따라서 미리 계획 하 고 테이블을 단순하게 유지 합니다. [Markdown 테이블을 더 쉽게 하는 사이트 같습니다](http://www.tablesgenerator.com/markdown_tables)합니다.

합니다 [Visual Studio Code 용 Docs Markdown 확장](https://docs.microsoft.com/teamblog/docs-extension) 사용 하는 경우 사용 하면 쉽게 생성 테이블도 [Visual Studio Code (아래 참조)](#using-visual-studio-code) 설명서를 편집할 수 있습니다.

### <a name="adding-images"></a>이미지 추가

리포지토리에서 "혼합 현실-docs/이미지" 폴더에 이미지를 업로드 하 고 해당 문서의 적절히 참조 해야 합니다. 이미지는 자동으로 표시에서 큰, 즉이 문서의 전체 너비를 드리겠습니다 이미지 큰 경우. 따라서 미리 업로드 하기 전에 이미지를 크기 조정 하는 것이 좋습니다. 크기를 지정 해야 위로 또는 아래로 있으면 조밀한 스크린샷 또는 스크린샷의 분수 각각 있지만 700 600 픽셀, 권장 되는 너비가입니다.

>[!IMPORTANT]
>만 병합 하기 전에 분기 된 리포지토리에 이미지를 업로드할 수 있습니다. 따라서 문서에 이미지를 추가 하려는 경우 해야 [Visual Studio Code를 사용 하 여](#using-visual-studio-code) 먼저 포크의 "이미지" 폴더에 이미지를 추가 하려면 웹 브라우저에서 다음을 수행한 있는지 확인:
>
>1. MicrosoftDocs/혼합 현실 리포지토리를 포크 합니다.
>2. 포크에서 문서를 편집 합니다.
>3. 포크에서 "혼합 현실-docs/이미지" 폴더에 문서에서 참조 하는 이미지를 업로드 합니다.
>4. 생성을 **끌어오기 요청** 포크 MicrosoftDocs/혼합 현실 '마스터' 분기에 병합 합니다.
>
>사용자 고유의 분기 된 리포지토리를 설정 하는 방법에 알아보려면 지침을 따르세요 [새 아티클을 만들](#creating-a-new-article)합니다.

## <a name="previewing-your-work"></a>작업 미리 보기

웹 브라우저를 통해 GitHub에서 편집 하는 동안 클릭 수를 **미리 보기** 커밋하기 전에 작업 미리 보기 페이지의 위쪽 탭 합니다. 

>[!NOTE]
>Microsoft 직원 에게만 제공 되 review.docs.microsoft.com 대 한 변경 내용을 미리 보기

Microsoft 직원이: 설명서 모양을에서 공용 이동 하기 전에 볼 수 '마스터' 분기에 병합 된 글을 면 https://review.docs.microsoft.com/windows/mixed-reality?branch=master (왼쪽된 열에서 목차를 사용 하 여 문서 찾기).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>데스크톱 클라이언트를 사용 하 여 편집 및 브라우저에서 편집

그러나 빠르게 변경 하는 가장 쉬운 방법은 브라우저에서 편집이, 몇 가지 단점이 있습니다.

- 맞춤법 검사를 활용할 수 없습니다.
- 모든 스마트 링크 (해야 수동으로 문서 파일 이름 입력) 다른 문서에 활용할 수 없습니다.
- 업로드 하 고 이미지를 참조 번거로울 수 있습니다.

와 같은 데스크톱 클라이언트를 사용 하 여 좋습니다 하지 이러한 문제를 사용 하 여 처리 대신 하는 경우 [Visual Studio Code](https://code.visualstudio.com/) 담아 [유용한 확장](#useful-extensions) 설명서에 기여 하 합니다.

## <a name="using-visual-studio-code"></a>Visual Studio Code를 사용 하 여

나열 된 이유로 [위에](#editing-in-the-browser-vs-editing-with-a-desktop-client), 데스크톱 클라이언트를 사용 하 여 웹 브라우저를 대신 문서를 편집 하는 것이 좋습니다. 사용 하는 것이 좋습니다 [Visual Studio Code](https://code.visualstudio.com/)합니다.

### <a name="setup"></a>설치 프로그램

이 리포지토리를 사용 하려면 Visual Studio Code를 구성 하려면 다음이 단계를 수행 합니다.

1. 웹 브라우저:
    1. 설치할 [PC에 대 한 Git](https://git-scm.com/downloads)합니다.
    2. 설치할 [Visual Studio Code](https://code.visualstudio.com/)합니다.
    3. [분기 MicrosoftDocs/혼합 현실](#creating-a-new-article) 아직 없는 경우.
    4. 포크, 포크에서 클릭 **복제 또는 다운로드** URL을 복사 합니다.
2. Visual Studio Code에서 포크의 로컬 클론을 만듭니다.
    1. **뷰** 메뉴에서 **명령 팔레트**합니다.
    2. 형식 "Git:Clone."
    3. 방금 복사한 URL을 붙여넣습니다.
    4. PC에서 복제본을 저장할 위치를 선택 합니다.
    5. 클릭 **열고 리포지토리** 팝업에서 합니다.

### <a name="editing-documentation"></a>문서를 편집합니다.

다음 워크플로 사용 하 여 Visual Studio Code를 사용 하 여 문서를 변경 하려면:

>[!NOTE]
>에 대 한 모든 지침 [편집](#editing-an-existing-article) 하 고 [만들기](#creating-a-new-article) 문서 및 [Markdown 편집의 기본 사항을](#markdown-basics), 위의 경우에 Visual Studio Code를 사용 하 여 적용 됩니다.

1. 복제 된 포크 공식 리포지토리를 사용 하 여 최신 상태 인지 확인 합니다.
   1. 웹 브라우저에서 포크에 MicrosoftDocs/혼합 현실 'master'에서 다른 참여자의 최근 변경 내용을 동기화 하려면 끌어오기 요청 만들기 (화살표가 올바른 방법으로 있는지 확인).
      
      ![포크에 MicrosoftDocs/혼합 현실에서 변경 내용을 동기화](images/sync_repos.PNG)
   2. Visual Studio Code에서 로컬 클론으로 새롭게 업데이트 된 분기를 동기화 할 동기화 단추를 클릭 합니다.
      
      ![동기화 단추를 클릭 합니다.](images/sync_clone.png)
2. 만들거나 Visual Studio Code를 사용 하 여 복제 된 리포지토리에서 문서를 편집 합니다.
   1. (이미지 "이미지" 폴더에 필요한 경우 추가) 하는 하나 이상의 문서를 편집 합니다.
   2. **저장할** 변경 **탐색기**합니다.
      
      ![탐색기에서 "모든 저장" 선택](images/explorer_save.png)
   3. **모두 커밋** 변경 **소스 제어** (메시지가 표시 되 면 커밋 메시지 쓰기).
      
      !["모두 커밋" 소스 제어에서 선택](images/source_control_commit.png)
   4. 클릭 합니다 **동기화** (GitHub의 분기) 원본에 변경 내용을 다시 동기화 하는 단추입니다.
      
      ![동기화 단추를 클릭 합니다.](images/sync_back.png)
3. 웹 브라우저에서 MicrosoftDocs/혼합 현실 'master' 돌아가기 포크에 새로운 변경 내용을 동기화 하려면 끌어오기 요청 만들기 (화살표는 올바른 방법은 가리키고 있는지 확인).

   ![MicrosoftDocs/혼합 현실에 포크에서 끌어오기 요청 만들기](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>유용한 확장

다음 Visual Studio Code 확장 설명서를 편집할 때 매우 유용 합니다.

- [Visual Studio Code 용 docs Markdown 확장](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -사용 **Alt + M** 문서 작성 등의 옵션 메뉴를 표시 합니다.
   - 검색 및 참조 이미지를 업로드 합니다.
   - 목록, 테이블, 같은 서식 지정 및 docs 특정 설명을 추가 `>[!NOTE]`합니다.
   - 검색 하 고 내부 링크와 책갈피 (페이지 내에서 특정 섹션에 대 한 링크)를 참조 합니다.
   - 서식 오류가 강조 표시 됩니다 (자세한 내용은 오류 위로 마우스를 가져가서).
- [맞춤법 검사기 코드](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -맞춤법이 틀린된 단어 밑줄이 표시 됩니다; 그리고 변경 또는 사전에 저장 하려면 맞춤법이 틀린된 단어를 마우스 오른쪽 단추로 클릭 합니다.
