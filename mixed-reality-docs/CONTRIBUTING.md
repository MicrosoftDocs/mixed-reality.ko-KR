---
title: 영향을 주는 지침
description: Windows Mixed Reality 설명서에 기여 하는 방법입니다.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516253"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="183fa-103">Windows Mixed Reality 개발자 설명서에 기여</span><span class="sxs-lookup"><span data-stu-id="183fa-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="183fa-104">[Windows Mixed Reality 개발자 설명서에 대 한 공용 리포지토리](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="183fa-105">이 리포지토리에서 만들거나 편집 하는 모든 문서는 **공용에 표시 됩니다.**</span><span class="sxs-lookup"><span data-stu-id="183fa-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="183fa-106">Windows Mixed Reality 문서는 이제 GitHub-flavored Markdown (Markdig 기능 포함)를 사용 하는 docs.microsoft.com 플랫폼에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="183fa-107">기본적으로이 리포지토리에서 편집 하는 콘텐츠는에 https://docs.microsoft.com/windows/mixed-reality 표시 되는 서식이 지정 되 고 스타일이 지정 된 페이지로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="183fa-108">이 페이지에서는 Markdown 기본 사항에 대 한 링크 뿐만 아니라 기여에 대 한 기본 단계 및 지침을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="183fa-109">기여를 주셔서 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="183fa-110">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="183fa-110">Before you start</span></span>

<span data-ttu-id="183fa-111">아직 없는 경우 [GitHub 계정을 만들어야](https://github.com/join)합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="183fa-112">Microsoft 직원 인 경우 microsoft [오픈 소스 포털](https://repos.opensource.microsoft.com/)의 microsoft 별칭에 GitHub 계정을 연결 하세요.</span><span class="sxs-lookup"><span data-stu-id="183fa-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="183fa-113">**"Microsoft"** 및 **"MicrosoftDocs"** 조직에 참여 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="183fa-114">GitHub 계정을 설정할 때 다음과 같은 보안 예방 조치를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="183fa-115">[Github 계정에 대 한 강력한 암호](https://github.com/settings/admin)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="183fa-116">[2 단계 인증](https://github.com/settings/two_factor_authentication/configure)을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="183fa-117">[복구 코드](https://github.com/settings/auth/recovery-codes) 를 안전한 장소에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="183fa-118">[공개 프로필 설정을](https://github.com/settings/profile)업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="183fa-119">사용자의 이름을 설정 하 고 *전자 메일 주소를 표시 하지 않도록* *공용 전자 메일* 을 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="183fa-120">사용자가 참여 하는 문서 페이지에 미리 보기가 표시 되므로 프로필 그림을 업로드 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="183fa-121">명령줄 워크플로를 사용 하려는 경우 기여를 할 때마다 암호를 입력할 필요가 없도록 [Windows 용 Git 자격 증명 관리자](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) 를 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="183fa-122">이러한 단계를 수행 하는 것이 중요 합니다. 게시 시스템이 GitHub에 연결 되어 있으므로 GitHub 별칭을 사용 하 여 각 아티클에 작성자 또는 참가자로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="183fa-123">기존 문서 편집</span><span class="sxs-lookup"><span data-stu-id="183fa-123">Editing an existing article</span></span>

<span data-ttu-id="183fa-124">웹 브라우저에서 GitHub를 통해 *기존 문서* 를 업데이트 하려면 다음 워크플로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="183fa-125">"Mixed reality-docs" 폴더에서 편집 하려는 문서로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="183fa-126">오른쪽 위에 있는 편집 단추 (연필 아이콘)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="183fa-127">이렇게 하면 ' master ' 분기에서 삭제 가능한 분기가 자동으로 분기 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![문서를 편집 합니다.](images/editpage.png)
3. <span data-ttu-id="183fa-129">문서의 내용을 편집 합니다 (지침은 아래의 ["Markdown 기본 사항"](#markdown-basics) 참조).</span><span class="sxs-lookup"><span data-stu-id="183fa-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="183fa-130">각 아티클의 위쪽에서 메타 데이터를 관련 항목으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="183fa-131">제목과 문서를 볼 때 브라우저 탭에 표시 되는 페이지 제목입니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="183fa-132">이는 SEO 및 인덱싱에 사용 되므로 필요 하지 않은 경우에는 제목을 변경 하지 않아야 합니다. 단, 설명서를 공개 하기 전에는이 작업이 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="183fa-133">한 문서 내용에 대 한 간략 한 설명을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="183fa-134">이는 SEO 및 검색을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="183fa-135">자신이 페이지의 주 소유자 인 경우 여기에 GitHub 별칭을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="183fa-136">ms author: 페이지의 주 소유자 인 경우 여기에 Microsoft 별칭을 추가 합니다 (필요 @microsoft.com하지 않음, 별칭만).</span><span class="sxs-lookup"><span data-stu-id="183fa-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="183fa-137">ms. 날짜: 주요 콘텐츠를 페이지에 추가 하는 경우에는 날짜를 업데이트 합니다. 자세한 내용은 설명, 서식 지정, 문법 또는 맞춤법과 같은 수정 사항은 업데이트 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="183fa-138">어 SEO의 키워드 지원 (검색 엔진 최적화).</span><span class="sxs-lookup"><span data-stu-id="183fa-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="183fa-139">문서와 관련 된 키워드를 쉼표와 공백으로 구분 하 여 추가 합니다 (목록에서 마지막 키워드 뒤에 문장 부호는 없음). 모든 문서에 적용 되는 전역 키워드는 다른 곳에서 관리 되므로 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="183fa-140">문서 편집을 완료 한 후 아래로 스크롤하여 **파일 변경 내용 제안** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="183fa-141">다음 페이지에서 **끌어오기 요청 만들기** 를 클릭 하 여 자동으로 만들어진 분기를 ' 마스터 '에 병합 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="183fa-142">편집 하려는 다음 문서에 대해 위의 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="183fa-143">새 문서 만들기</span><span class="sxs-lookup"><span data-stu-id="183fa-143">Creating a new article</span></span>

<span data-ttu-id="183fa-144">웹 브라우저에서 GitHub를 통해 설명서 리포지토리에서 *새 문서를 만들려면* 다음 워크플로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="183fa-145">오른쪽 위에 있는 **포크** 단추를 사용 하 여 MicrosoftDocs/mixed reality ' master ' 분기에서 포크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![마스터 분기를 포크 합니다.](images/forkbranch.png)
2. <span data-ttu-id="183fa-147">"Mixed reality-docs" 폴더의 오른쪽 위에 있는 **새 파일 만들기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="183fa-148">문서에 대 한 페이지 이름 (공백 대신 하이픈을 사용 하 고 구두점 또는 아포스트로피를 사용 하지 않음)을 만든 후 ".ma"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![새 페이지의 이름을로 합니다.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="183fa-150">"Mixed reality-docs" 폴더 내에서 새 문서를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="183fa-151">새 파일 이름 줄에서 "/mixed-reality-docs/"를 확인 하 여이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="183fa-152">새 페이지 위쪽에 다음 메타 데이터 블록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="183fa-153">[위의 섹션](#editing-an-existing-article)에 설명 된 지침에 따라 관련 메타 데이터 필드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="183fa-154">[Markdown 기본 사항을](#markdown-basics)사용 하 여 문서 콘텐츠를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="183fa-155">문서의 맨 `## See also` 아래에 있는 섹션을 다른 관련 문서에 대 한 링크와 함께 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="183fa-156">완료 되 면 **새 파일 커밋**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="183fa-157">**새 끌어오기 요청** 을 클릭 하 고 분기의 ' 마스터 ' 분기를 MicrosoftDocs/mixed-현실 ' master '에 병합 합니다. 화살표가 올바른 방법을 가리키고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![포크에서 MicrosoftDocs/mixed reality로 끌어오기 요청 만들기](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="183fa-159">Markdown 기본 사항</span><span class="sxs-lookup"><span data-stu-id="183fa-159">Markdown basics</span></span>

<span data-ttu-id="183fa-160">다음 리소스는 Markdown 언어를 사용 하 여 문서를 편집 하는 방법을 배우는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="183fa-161">Markdown 기본 사항</span><span class="sxs-lookup"><span data-stu-id="183fa-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="183fa-162">한눈에 Markdown 참조 포스터</span><span class="sxs-lookup"><span data-stu-id="183fa-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="183fa-163">Docs.microsoft.com에 대 한 Markdown 쓰기에 대 한 추가 리소스</span><span class="sxs-lookup"><span data-stu-id="183fa-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="183fa-164">테이블 추가</span><span class="sxs-lookup"><span data-stu-id="183fa-164">Adding tables</span></span>

<span data-ttu-id="183fa-165">스타일 docs.microsoft.com 스타일을 지정 하는 방식 때문에 인라인 CSS를 시도 하더라도 테두리나 사용자 지정 스타일은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="183fa-166">짧은 시간 동안 작동 하는 것 처럼 보이지만 결국 플랫폼은 테이블에서 스타일을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="183fa-167">따라서 미리 계획 하 고 테이블을 단순하게 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="183fa-168">[Markdown 테이블을 쉽게 만들 수 있는 사이트는 다음과 같습니다](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="183fa-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="183fa-169">[Visual Studio Code에 대 한 Docs Markdown 확장](https://docs.microsoft.com/teamblog/docs-extension) 은 [Visual Studio Code (아래 참조)](#using-visual-studio-code) 를 사용 하 여 문서를 편집 하는 경우에도 테이블을 쉽게 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="183fa-170">이미지 추가</span><span class="sxs-lookup"><span data-stu-id="183fa-170">Adding images</span></span>

<span data-ttu-id="183fa-171">리포지토리의 "mixed reality-docs/images" 폴더에 이미지를 업로드 한 다음 문서에서 적절 하 게 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="183fa-172">이미지가 자동으로 전체 크기로 표시 됩니다. 즉, 이미지가 크면 아티클의 전체 너비를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="183fa-173">따라서 이미지를 업로드 하기 전에 미리 크기를 조정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="183fa-174">권장 되는 너비는 600 픽셀에서 700 픽셀 사이 이지만, 조밀한 스크린샷 또는 스크린 샷의 분수 인 경우 크기를 조정 하거나 축소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="183fa-175">병합 하기 전에 분기 리포지토리에만 이미지를 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="183fa-176">따라서 문서에 이미지를 추가 하려면 먼저 [Visual Studio Code를 사용](#using-visual-studio-code) 하 여 포크의 "images" 폴더에 이미지를 추가 하거나 웹 브라우저에서 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="183fa-177">MicrosoftDocs/mixed reality 리포지토리를 분기 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="183fa-178">포크에서 문서를 편집 했습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="183fa-179">문서에서 참조 하는 이미지를 포크의 "mixed reality-docs/images" 폴더에 업로드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="183fa-180">분기를 MicrosoftDocs/mixed-현실 ' master ' 분기에 병합 하는 **끌어오기 요청** 을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="183fa-181">사용자 고유의 분기 리포지토리를 설정 하는 방법을 알아보려면 [새 문서 만들기](#creating-a-new-article)에 대 한 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="183fa-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="183fa-182">작업 미리 보기</span><span class="sxs-lookup"><span data-stu-id="183fa-182">Previewing your work</span></span>

<span data-ttu-id="183fa-183">웹 브라우저를 통해 GitHub에서 편집 하는 동안 페이지 위쪽의 **미리 보기** 탭을 클릭 하 여 커밋하기 전에 작업을 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="183fa-184">Microsoft 직원만 review.docs.microsoft.com에서 변경 내용을 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="183fa-185">Microsoft 직원: 기여를 ' 마스터 ' 분기에 병합 한 후에는에서 https://review.docs.microsoft.com/windows/mixed-reality?branch=master 공개 되기 전에 설명서의 모양을 확인할 수 있습니다 (왼쪽 열의 목차를 사용 하 여 문서 찾기).</span><span class="sxs-lookup"><span data-stu-id="183fa-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="183fa-186">브라우저에서 편집 및 데스크톱 클라이언트를 사용 하 여 편집</span><span class="sxs-lookup"><span data-stu-id="183fa-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="183fa-187">브라우저에서 편집은 빠른 변경을 수행 하는 가장 쉬운 방법 이지만 다음과 같은 몇 가지 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="183fa-188">맞춤법 검사를 받을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-188">You don't get spell-check.</span></span>
- <span data-ttu-id="183fa-189">다른 문서에 대 한 스마트 링크를 얻을 수 없습니다 (문서의 파일 이름을 직접 입력 해야 함).</span><span class="sxs-lookup"><span data-stu-id="183fa-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="183fa-190">이미지를 업로드 하 고 참조 하는 것이 더 나을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="183fa-191">이러한 문제를 해결 하는 것이 아닌 경우 설명서에 기여 하는 데 도움이 되는 몇 가지 [유용한 확장과](#useful-extensions) 함께 [Visual Studio Code](https://code.visualstudio.com/) 와 같은 데스크톱 클라이언트를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="183fa-192">Visual Studio Code 사용</span><span class="sxs-lookup"><span data-stu-id="183fa-192">Using Visual Studio Code</span></span>

<span data-ttu-id="183fa-193">[위에](#editing-in-the-browser-vs-editing-with-a-desktop-client)나열 된 이유 때문에 웹 브라우저가 아닌 데스크톱 클라이언트를 사용 하 여 문서를 편집 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="183fa-194">[Visual Studio Code](https://code.visualstudio.com/)를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="183fa-195">설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="183fa-195">Setup</span></span>

<span data-ttu-id="183fa-196">이 리포지토리를 사용 하도록 Visual Studio Code를 구성 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="183fa-197">웹 브라우저에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-197">In a web browser:</span></span>
    1. <span data-ttu-id="183fa-198">[PC 용 Git를](https://git-scm.com/downloads)설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="183fa-199">[Visual Studio Code](https://code.visualstudio.com/)를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="183fa-200">[분기 MicrosoftDocs/mixed-현실](#creating-a-new-article) . 아직 없는 경우.</span><span class="sxs-lookup"><span data-stu-id="183fa-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="183fa-201">포크에서 **복제 또는 다운로드** 를 클릭 하 고 URL을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="183fa-202">Visual Studio Code에서 포크의 로컬 클론을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="183fa-203">**보기** 메뉴에서 **명령 팔레트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="183fa-204">"Git: Clone"을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="183fa-205">방금 복사한 URL을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="183fa-206">PC에서 클론을 저장할 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="183fa-207">팝업에서 **리포지토리 열기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="183fa-208">문서 편집</span><span class="sxs-lookup"><span data-stu-id="183fa-208">Editing documentation</span></span>

<span data-ttu-id="183fa-209">Visual Studio Code를 사용 하 여 설명서를 변경 하려면 다음 워크플로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="183fa-210">Visual Studio Code 사용 하는 경우에는 문서 [편집](#editing-an-existing-article) 및 [만들기](#creating-a-new-article) 에 대 한 모든 지침과 위에서 [Markdown 편집의 기본](#markdown-basics)사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="183fa-211">복제 된 분기가 공식 리포지토리를 사용 하 여 최신 상태 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="183fa-212">웹 브라우저에서 끌어오기 요청을 만들어 MicrosoftDocs/mixed reality의 다른 참가자의 최근 변경 내용을 포크에 동기화 합니다. 화살표가 올바른 방법을 가리키고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![MicrosoftDocs/mixed-현실에서 포크로 변경 내용 동기화](images/sync_repos.PNG)
   2. <span data-ttu-id="183fa-214">Visual Studio Code에서 동기화 단추를 클릭 하 여 새로 업데이트 된 포크를 로컬 클론에 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![동기화 단추를 클릭 합니다.](images/sync_clone.png)
2. <span data-ttu-id="183fa-216">Visual Studio Code를 사용 하 여 복제 된 리포지토리에서 문서를 만들거나 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="183fa-217">하나 이상의 문서 (필요한 경우 "images" 폴더에 이미지 추가)를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="183fa-218">**탐색기**에서 변경 내용을 **저장** 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-218">**Save** changes in **Explorer**.</span></span>
      
      ![탐색기에서 "모두 저장"을 선택 합니다.](images/explorer_save.png)
   3. <span data-ttu-id="183fa-220">**소스 제어** 의 모든 변경 내용 **커밋** (메시지가 표시 되 면 쓰기 커밋 메시지).</span><span class="sxs-lookup"><span data-stu-id="183fa-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![소스 제어에서 "모두 커밋"을 선택 합니다.](images/source_control_commit.png)
   4. <span data-ttu-id="183fa-222">**동기화** 단추를 클릭 하 여 변경 내용을 다시 원본 (GitHub의 포크)으로 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![동기화 단추를 클릭 합니다.](images/sync_back.png)
3. <span data-ttu-id="183fa-224">웹 브라우저에서 끌어오기 요청을 만들어 분기의 새 변경 내용을 MicrosoftDocs/mixed-현실 ' master '로 다시 동기화 합니다. 화살표가 올바른 방법을 가리키고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![포크에서 MicrosoftDocs/mixed reality로 끌어오기 요청 만들기](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="183fa-226">유용한 확장</span><span class="sxs-lookup"><span data-stu-id="183fa-226">Useful extensions</span></span>

<span data-ttu-id="183fa-227">다음 Visual Studio Code 확장은 설명서를 편집할 때 매우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="183fa-228">[Visual Studio Code 용 Docs Markdown 확장](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - **Alt + M** 을 사용 하 여 다음과 같은 docs 제작 옵션 메뉴를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="183fa-229">업로드 한 이미지를 검색 하 고 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="183fa-230">목록과 같이 `>[!NOTE]`목록, 테이블 및 문서 특정 호출 등의 서식을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="183fa-231">내부 링크와 책갈피를 검색 하 고 참조 합니다 (페이지 내의 특정 섹션에 대 한 링크).</span><span class="sxs-lookup"><span data-stu-id="183fa-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="183fa-232">서식 지정 오류가 강조 표시 됩니다. 자세한 내용은 오류를 마우스로 가리키십시오.</span><span class="sxs-lookup"><span data-stu-id="183fa-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="183fa-233">[코드 맞춤법 검사기](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -철자가 잘못 된 단어에는 밑줄이 그어집니다. 철자가 잘못 된 단어를 마우스 오른쪽 단추로 클릭 하 여 변경 하거나 사전에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="183fa-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
