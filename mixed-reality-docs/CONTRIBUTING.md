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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="1f2e3-103">Windows Mixed Reality 개발자 설명서에 기여</span><span class="sxs-lookup"><span data-stu-id="1f2e3-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="1f2e3-104">시작 합니다 [Windows Mixed Reality 개발자 설명서에 대 한 공용 리포지토리](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="1f2e3-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="1f2e3-105">만들기 또는 편집이 리포지토리의 모든 문서 **공개적으로 표시 됩니다.**</span><span class="sxs-lookup"><span data-stu-id="1f2e3-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="1f2e3-106">Windows Mixed Reality docs (Markdig 기능)와 GitHub 지원 Markdown을 사용 하는 docs.microsoft.com 플랫폼에서 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="1f2e3-107">에 표시 되는 서식이 지정 되 고 스타일이 지정 된 페이지에이 리포지토리에서 편집 내용을 설정 기본적 https://docs.microsoft.com/windows/mixed-reality합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="1f2e3-108">이 페이지 기본 단계 및 영향을 주는에 대 한 지침 뿐만 아니라 Markdown 기본 사항에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="1f2e3-109">작성 글을 주셔서 감사 합니다!</span><span class="sxs-lookup"><span data-stu-id="1f2e3-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1f2e3-110">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="1f2e3-110">Before you start</span></span>

<span data-ttu-id="1f2e3-111">해야 하면 이미 계정이 없는 경우 [GitHub 계정을 만듭니다](https://github.com/join)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="1f2e3-112">가 Microsoft 직원인 경우 GitHub 계정에 Microsoft 별칭에 연결 합니다 [Microsoft 오픈 소스 포털](https://repos.opensource.microsoft.com/)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="1f2e3-113">조인 합니다 **"Microsoft"** 하 고 **"MicrosoftDocs"** 조직).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="1f2e3-114">GitHub 계정에 설정 하는 경우 이러한 보안 예방 조치를 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="1f2e3-115">만들기는 [Github 계정에 대 한 강력한 암호](https://github.com/settings/admin)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="1f2e3-116">사용 하도록 설정 [2 단계 인증](https://github.com/settings/two_factor_authentication/configure)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="1f2e3-117">저장 하 [복구 코드](https://github.com/settings/auth/recovery-codes) 안전한 곳에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="1f2e3-118">업데이트 프로그램 [공개 프로필 설정은](https://github.com/settings/profile)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="1f2e3-119">사용자 이름을 설정 하 고 설정을 고려 하 *공용 메일* 를 *내 전자 메일 주소를 표시 안 함*합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="1f2e3-120">사용자가 참여 하는 문서 페이지의 축소판 그림과 같이 프로필 사진을 업로드 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="1f2e3-121">명령줄 워크플로 사용 하려는 경우를 설정 하십시오 [Windows 용 Git 자격 증명 관리자](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) 기 고물 할 때마다 암호를 입력 하지 않아도 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="1f2e3-122">다음이 단계를 수행 하는 것이 중요 합니다 게시 시스템은 GitHub에 연결 하 고 작성자 또는 참여자 GitHub 별칭을 사용 하 여 각 문서에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="1f2e3-123">기존 문서 편집</span><span class="sxs-lookup"><span data-stu-id="1f2e3-123">Editing an existing article</span></span>

<span data-ttu-id="1f2e3-124">에 대 한 업데이트를 위해 다음 워크플로를 사용 *기존 아티클을* 웹 브라우저에서 GitHub를 통해:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="1f2e3-125">"혼합 현실-문서" 폴더에서 편집 하려는 문서를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="1f2e3-126">오른쪽 위에 있는 편집 단추 (연필 아이콘)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="1f2e3-127">자동으로 '마스터' 분기를 삭제할 수 있는 분기를 분기는이 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![문서를 편집 합니다.](images/editpage.png)
3. <span data-ttu-id="1f2e3-129">문서의 콘텐츠를 편집 (참고 ["Markdown 기본 사항"](#markdown-basics) 아래 지침에 대 한).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="1f2e3-130">각 문서의 맨 위에 있는 관련 메타 데이터를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="1f2e3-131">제목: 문서를 보고 하는 경우 브라우저 탭에 표시 되는 페이지 제목입니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="1f2e3-132">하지 않는 한 제목을 변경 하지 않아야 SEO 및 인덱싱에 대 한이 사용 되는, (있지만 이것이 덜 중요 한 문서 공개 되기 전에) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="1f2e3-133">description: 간략 한 설명은 항목의 콘텐츠를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="1f2e3-134">이 따른 SEO 및 검색에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="1f2e3-135">작성자: 페이지의 기본 소유자 라면 여기 GitHub 별칭을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="1f2e3-136">ms.author: 페이지의 기본 소유자 인 경우 추가 Microsoft 별칭 여기 (필요가 @microsoft.com, 별칭만).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="1f2e3-137">ms.date: 문법, 서식 지정, 설명이 같은 수정 하지 않고 페이지에서 주요 콘텐츠를 추가 하거나 맞춤법 검사 하는 경우 날짜를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="1f2e3-138">키워드: 키워드는 SEO (검색 엔진 최적화)에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="1f2e3-139">쉼표 및 공백을 구분 하 여, 문서 (하지만 마지막 키워드 목록에 다음 문장 부호 없는); 관련 된 키워드 추가 다른 곳에서 관리 되는 것, 모든 문서에 적용 되는 전역 키워드를 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="1f2e3-140">문서 편집을 완료 한 경우 아래로 스크롤하여을 클릭 합니다 **파일 변경 내용 제안** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="1f2e3-141">다음 페이지에서 클릭 **끌어오기 요청 만들기** 'master'. 자동으로 만들어진 분기 병합</span><span class="sxs-lookup"><span data-stu-id="1f2e3-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="1f2e3-142">편집 하려면 다음 문서에 대 한 위의 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="1f2e3-143">새 문서 만들기</span><span class="sxs-lookup"><span data-stu-id="1f2e3-143">Creating a new article</span></span>

<span data-ttu-id="1f2e3-144">다음 워크플로를 사용 하 여 *새 문서를 만들* 웹 브라우저에서 GitHub 통해 설명서 리포지토리에서:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="1f2e3-145">MicrosoftDocs/혼합 현실 '마스터' 분기는 분기를 만듭니다 (사용 하는 **포크** 오른쪽 위에 있는 단추).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![마스터 분기를 포크 합니다.](images/forkbranch.png)
2. <span data-ttu-id="1f2e3-147">"혼합 현실-문서" 폴더를 클릭 합니다 **새 파일 만들기** 오른쪽 위에 있는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="1f2e3-148">아티클에 대 한 페이지 이름을 만듭니다 (하이픈을 사용 하 여 공백 대신 및 문장 부호 또는 아포스트로피 사용 하지 마세요) 및 ".md"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![새 페이지를 이름을 지정 합니다.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="1f2e3-150">"혼합 현실-문서" 폴더 내에서 새 항목을 만드는 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="1f2e3-151">확인 하 여이 확인할 수 있습니다 "혼합 현실-문서 / /" 새 파일 이름 줄에서.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="1f2e3-152">새 페이지의 맨 위에 있는 다음 메타 데이터 블록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="1f2e3-153">지침에 따라 관련 메타 데이터 필드를 입력 합니다 [위의 섹션](#editing-an-existing-article)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="1f2e3-154">쓰기 문서 콘텐츠를 사용 하 여 [Markdown 기본 사항](#markdown-basics)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="1f2e3-155">추가 된 `## See also` 다른 관련 된 문서에 대 한 링크를 사용 하 여 문서의 맨 아래에 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="1f2e3-156">완료 되 면, 클릭 **커밋 새 파일**합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="1f2e3-157">클릭 **새 끌어오기 요청** MicrosoftDocs/혼합 현실 '마스터' 분기의 '마스터' 분기 병합 및 (화살표는 올바른 방법은 가리키고 있는지 확인).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![MicrosoftDocs/혼합 현실에 포크에서 끌어오기 요청 만들기](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="1f2e3-159">Markdown 기본 사항</span><span class="sxs-lookup"><span data-stu-id="1f2e3-159">Markdown basics</span></span>

<span data-ttu-id="1f2e3-160">다음 리소스를 사용 하는 Markdown 언어를 사용 하 여 문서를 편집 하는 방법을 알아봅니다 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="1f2e3-161">Markdown 기본 사항</span><span class="sxs-lookup"><span data-stu-id="1f2e3-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="1f2e3-162">Markdown에서-요약 참조 포스터</span><span class="sxs-lookup"><span data-stu-id="1f2e3-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="1f2e3-163">Docs.microsoft.com 용 Markdown 작성을 위한 추가 리소스</span><span class="sxs-lookup"><span data-stu-id="1f2e3-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="1f2e3-164">테이블 추가</span><span class="sxs-lookup"><span data-stu-id="1f2e3-164">Adding tables</span></span>

<span data-ttu-id="1f2e3-165">방법은 docs.microsoft.com 스타일 테이블이 없기 테두리 또는 사용자 지정 스타일을 인라인 CSS를 시도 하는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="1f2e3-166">짧은 기간에 대해 작동 하는 것이 나타납니다. 하지만 결국 플랫폼에서는 테이블에서 외부 스타일을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="1f2e3-167">따라서 미리 계획 하 고 테이블을 단순하게 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="1f2e3-168">[Markdown 테이블을 더 쉽게 하는 사이트 같습니다](http://www.tablesgenerator.com/markdown_tables)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="1f2e3-169">합니다 [Visual Studio Code 용 Docs Markdown 확장](https://docs.microsoft.com/teamblog/docs-extension) 사용 하는 경우 사용 하면 쉽게 생성 테이블도 [Visual Studio Code (아래 참조)](#using-visual-studio-code) 설명서를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="1f2e3-170">이미지 추가</span><span class="sxs-lookup"><span data-stu-id="1f2e3-170">Adding images</span></span>

<span data-ttu-id="1f2e3-171">리포지토리에서 "혼합 현실-docs/이미지" 폴더에 이미지를 업로드 하 고 해당 문서의 적절히 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="1f2e3-172">이미지는 자동으로 표시에서 큰, 즉이 문서의 전체 너비를 드리겠습니다 이미지 큰 경우.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="1f2e3-173">따라서 미리 업로드 하기 전에 이미지를 크기 조정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="1f2e3-174">크기를 지정 해야 위로 또는 아래로 있으면 조밀한 스크린샷 또는 스크린샷의 분수 각각 있지만 700 600 픽셀, 권장 되는 너비가입니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1f2e3-175">만 병합 하기 전에 분기 된 리포지토리에 이미지를 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="1f2e3-176">따라서 문서에 이미지를 추가 하려는 경우 해야 [Visual Studio Code를 사용 하 여](#using-visual-studio-code) 먼저 포크의 "이미지" 폴더에 이미지를 추가 하려면 웹 브라우저에서 다음을 수행한 있는지 확인:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="1f2e3-177">MicrosoftDocs/혼합 현실 리포지토리를 포크 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="1f2e3-178">포크에서 문서를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="1f2e3-179">포크에서 "혼합 현실-docs/이미지" 폴더에 문서에서 참조 하는 이미지를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="1f2e3-180">생성을 **끌어오기 요청** 포크 MicrosoftDocs/혼합 현실 '마스터' 분기에 병합 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="1f2e3-181">사용자 고유의 분기 된 리포지토리를 설정 하는 방법에 알아보려면 지침을 따르세요 [새 아티클을 만들](#creating-a-new-article)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="1f2e3-182">작업 미리 보기</span><span class="sxs-lookup"><span data-stu-id="1f2e3-182">Previewing your work</span></span>

<span data-ttu-id="1f2e3-183">웹 브라우저를 통해 GitHub에서 편집 하는 동안 클릭 수를 **미리 보기** 커밋하기 전에 작업 미리 보기 페이지의 위쪽 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="1f2e3-184">Microsoft 직원 에게만 제공 되 review.docs.microsoft.com 대 한 변경 내용을 미리 보기</span><span class="sxs-lookup"><span data-stu-id="1f2e3-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="1f2e3-185">Microsoft 직원이: 설명서 모양을에서 공용 이동 하기 전에 볼 수 '마스터' 분기에 병합 된 글을 면 https://review.docs.microsoft.com/windows/mixed-reality?branch=master (왼쪽된 열에서 목차를 사용 하 여 문서 찾기).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="1f2e3-186">데스크톱 클라이언트를 사용 하 여 편집 및 브라우저에서 편집</span><span class="sxs-lookup"><span data-stu-id="1f2e3-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="1f2e3-187">그러나 빠르게 변경 하는 가장 쉬운 방법은 브라우저에서 편집이, 몇 가지 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="1f2e3-188">맞춤법 검사를 활용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-188">You don't get spell-check.</span></span>
- <span data-ttu-id="1f2e3-189">모든 스마트 링크 (해야 수동으로 문서 파일 이름 입력) 다른 문서에 활용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="1f2e3-190">업로드 하 고 이미지를 참조 번거로울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="1f2e3-191">와 같은 데스크톱 클라이언트를 사용 하 여 좋습니다 하지 이러한 문제를 사용 하 여 처리 대신 하는 경우 [Visual Studio Code](https://code.visualstudio.com/) 담아 [유용한 확장](#useful-extensions) 설명서에 기여 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="1f2e3-192">Visual Studio Code를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="1f2e3-192">Using Visual Studio Code</span></span>

<span data-ttu-id="1f2e3-193">나열 된 이유로 [위에](#editing-in-the-browser-vs-editing-with-a-desktop-client), 데스크톱 클라이언트를 사용 하 여 웹 브라우저를 대신 문서를 편집 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="1f2e3-194">사용 하는 것이 좋습니다 [Visual Studio Code](https://code.visualstudio.com/)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="1f2e3-195">설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="1f2e3-195">Setup</span></span>

<span data-ttu-id="1f2e3-196">이 리포지토리를 사용 하려면 Visual Studio Code를 구성 하려면 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="1f2e3-197">웹 브라우저:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-197">In a web browser:</span></span>
    1. <span data-ttu-id="1f2e3-198">설치할 [PC에 대 한 Git](https://git-scm.com/downloads)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="1f2e3-199">설치할 [Visual Studio Code](https://code.visualstudio.com/)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="1f2e3-200">[분기 MicrosoftDocs/혼합 현실](#creating-a-new-article) 아직 없는 경우.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="1f2e3-201">포크, 포크에서 클릭 **복제 또는 다운로드** URL을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="1f2e3-202">Visual Studio Code에서 포크의 로컬 클론을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="1f2e3-203">**뷰** 메뉴에서 **명령 팔레트**합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="1f2e3-204">형식 "Git:Clone."</span><span class="sxs-lookup"><span data-stu-id="1f2e3-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="1f2e3-205">방금 복사한 URL을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="1f2e3-206">PC에서 복제본을 저장할 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="1f2e3-207">클릭 **열고 리포지토리** 팝업에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="1f2e3-208">문서를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-208">Editing documentation</span></span>

<span data-ttu-id="1f2e3-209">다음 워크플로 사용 하 여 Visual Studio Code를 사용 하 여 문서를 변경 하려면:</span><span class="sxs-lookup"><span data-stu-id="1f2e3-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="1f2e3-210">에 대 한 모든 지침 [편집](#editing-an-existing-article) 하 고 [만들기](#creating-a-new-article) 문서 및 [Markdown 편집의 기본 사항을](#markdown-basics), 위의 경우에 Visual Studio Code를 사용 하 여 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="1f2e3-211">복제 된 포크 공식 리포지토리를 사용 하 여 최신 상태 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="1f2e3-212">웹 브라우저에서 포크에 MicrosoftDocs/혼합 현실 'master'에서 다른 참여자의 최근 변경 내용을 동기화 하려면 끌어오기 요청 만들기 (화살표가 올바른 방법으로 있는지 확인).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![포크에 MicrosoftDocs/혼합 현실에서 변경 내용을 동기화](images/sync_repos.PNG)
   2. <span data-ttu-id="1f2e3-214">Visual Studio Code에서 로컬 클론으로 새롭게 업데이트 된 분기를 동기화 할 동기화 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![동기화 단추를 클릭 합니다.](images/sync_clone.png)
2. <span data-ttu-id="1f2e3-216">만들거나 Visual Studio Code를 사용 하 여 복제 된 리포지토리에서 문서를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="1f2e3-217">(이미지 "이미지" 폴더에 필요한 경우 추가) 하는 하나 이상의 문서를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="1f2e3-218">**저장할** 변경 **탐색기**합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-218">**Save** changes in **Explorer**.</span></span>
      
      ![탐색기에서 "모든 저장" 선택](images/explorer_save.png)
   3. <span data-ttu-id="1f2e3-220">**모두 커밋** 변경 **소스 제어** (메시지가 표시 되 면 커밋 메시지 쓰기).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      !["모두 커밋" 소스 제어에서 선택](images/source_control_commit.png)
   4. <span data-ttu-id="1f2e3-222">클릭 합니다 **동기화** (GitHub의 분기) 원본에 변경 내용을 다시 동기화 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![동기화 단추를 클릭 합니다.](images/sync_back.png)
3. <span data-ttu-id="1f2e3-224">웹 브라우저에서 MicrosoftDocs/혼합 현실 'master' 돌아가기 포크에 새로운 변경 내용을 동기화 하려면 끌어오기 요청 만들기 (화살표는 올바른 방법은 가리키고 있는지 확인).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![MicrosoftDocs/혼합 현실에 포크에서 끌어오기 요청 만들기](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="1f2e3-226">유용한 확장</span><span class="sxs-lookup"><span data-stu-id="1f2e3-226">Useful extensions</span></span>

<span data-ttu-id="1f2e3-227">다음 Visual Studio Code 확장 설명서를 편집할 때 매우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="1f2e3-228">[Visual Studio Code 용 docs Markdown 확장](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -사용 **Alt + M** 문서 작성 등의 옵션 메뉴를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="1f2e3-229">검색 및 참조 이미지를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="1f2e3-230">목록, 테이블, 같은 서식 지정 및 docs 특정 설명을 추가 `>[!NOTE]`합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="1f2e3-231">검색 하 고 내부 링크와 책갈피 (페이지 내에서 특정 섹션에 대 한 링크)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="1f2e3-232">서식 오류가 강조 표시 됩니다 (자세한 내용은 오류 위로 마우스를 가져가서).</span><span class="sxs-lookup"><span data-stu-id="1f2e3-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="1f2e3-233">[맞춤법 검사기 코드](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -맞춤법이 틀린된 단어 밑줄이 표시 됩니다; 그리고 변경 또는 사전에 저장 하려면 맞춤법이 틀린된 단어를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e3-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
