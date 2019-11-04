---
title: MR 및 Azure 312-봇 통합
description: 이 과정을 완료 하 여 Microsoft 봇 Framework v4를 사용 하는 bot을 만들어 배포 하 고 혼합 현실 응용 프로그램에서 통신 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 컴퓨터 비전, hololens, 모던, vr, microsoft 봇 framework v4, 웹 앱 봇, 봇 프레임 워크, microsoft 봇
ms.openlocfilehash: dc428f01a8333bf812fe03c59a46b7a2fa20df83
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438489"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-and-azure-312-bot-integration"></a>MR 및 Azure 312: 봇 통합

이 과정에서는 Microsoft 봇 Framework V4를 사용 하 여 봇을 만들어 배포 하 고 Windows Mixed Reality 응용 프로그램을 통해 통신 하는 방법에 대해 설명 합니다. 

![](images/AzureLabs-Lab312-00.png)

**Microsoft Bot Framework V4** 는 개발자에 게 확장 가능 하 고 확장 가능한 봇 응용 프로그램을 빌드할 수 있는 도구를 제공 하도록 설계 된 api 집합입니다. 자세한 내용은 [Microsoft 봇 Framework 페이지](https://dev.botframework.com/) 또는 [V4 Git 리포지토리](https://github.com/Microsoft/botbuilder-dotnet/wiki)를 참조 하세요.

이 과정을 완료 한 후 다음을 수행할 수 있는 Windows Mixed Reality 응용 프로그램을 작성 합니다.

1. **탭 제스처** 를 사용 하 여 사용자 의견을 수신 하는 봇을 시작 합니다.
2. 사용자가 무언가를 말하면 봇은 응답을 제공 하려고 합니다.
3. Unity 장면에서 봇 근처에 있는 텍스트로 인공 지능 회신을 표시 합니다.

응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다. 이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다. 이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 312: 봇 통합</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서 주로 HoloLens에 초점을 맞춘 반면,이 과정에서 배운 내용을 Windows Mixed Reality 모던 (VR) 헤드셋에도 적용할 수 있습니다. 모던 (VR) 헤드셋은 액세스할 수 있는 카메라를 포함 하지 않으므로 PC에 연결 된 외부 카메라가 필요 합니다. 이 과정을 진행 하면서 모던 (VR) 헤드셋을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다. [도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- 모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC
- [개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)
- Azure 및 Azure Bot 검색을 위한 인터넷 액세스. 자세한 내용은 [다음 링크](https://dev.botframework.com/)를 참조 하세요.

### <a name="before-you-start"></a>시작하기 전 확인 사항

1.  이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
2.  HoloLens를 설정 하 고 테스트 합니다. HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다. 
3.  새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음). 

보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens-2)대 한 다음 링크를 참조 하세요.

센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.

## <a name="chapter-1--create-the-bot-application"></a>1 장-Bot 응용 프로그램 만들기

첫 번째 단계는 bot을 로컬 ASP.Net Core 웹 응용 프로그램으로 만드는 것입니다. 이를 완료 하 고 테스트 한 후에는 Azure Portal에 게시 합니다.

1.  Visual Studio를 엽니다. 새 프로젝트를 만들고, 프로젝트 형식으로 **ASP NET Core 웹 응용 프로그램** 을 선택 하 고 (하위 섹션 .net core 아래에서 찾을 수 있습니다.) **mybot**를 호출 합니다. **확인**을 클릭합니다.

2.  표시 되는 창에서 **비어 있음**을 선택 합니다. 또한 대상이 **ASP NET Core 2.0** 로 설정 되 고 인증이 **인증 없음**으로 설정 되어 있는지 확인 합니다. **확인**을 클릭합니다.  

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-01.png)

3.  이제 솔루션이 열립니다. **솔루션 탐색기** 에서 솔루션 **mybot** 을 마우스 오른쪽 단추로 클릭 하 고 **솔루션용 NuGet 패키지 관리**를 클릭 합니다. 

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-02.png)

4.  **찾아보기** 탭에서 **Microsoft** . m a. a. m a. i. 패키지 버전 **4.0.1-미리 보기**를 선택 하 고 프로젝트 상자를 선택 합니다. 그런 다음 **설치**를 클릭 합니다. 이제 **Bot Framework v4**에 필요한 라이브러리를 설치 했습니다. NuGet 페이지를 닫습니다.

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-03.png)

5.  **솔루션 탐색기** 에서 *프로젝트* **mybot**을 마우스 오른쪽 단추로 클릭 하 고 **|** **클래스** **추가** 를 클릭 합니다.

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-04.png)

6.  클래스 이름을 **Mybot** 로 설정 하 고 **추가**를 클릭 합니다.

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-05.png)

7.  이전 지점을 반복 하 여 **ConversationContext**라는 다른 클래스를 만듭니다. 

8.  **솔루션 탐색기** 에서 **wwwroot** 를 마우스 오른쪽 단추로 클릭 하 고 **|** **새 항목** **추가** 를 클릭 합니다. **HTML 페이지** 를 선택 합니다 .이 페이지는 하위 섹션 웹에서 찾을 수 있습니다. 파일 이름을 **html.actionlink**로 합니다. **추가**를 클릭합니다.

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-06.png)

9.  **솔루션 탐색기** 의 클래스/개체 목록은 아래 이미지와 같습니다.

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-07.png)

10. **ConversationContext** 클래스를 두 번 클릭 합니다. 이 클래스는 봇에서 대화의 컨텍스트를 유지 하는 데 사용 하는 변수를 보유 합니다. 이러한 대화 컨텍스트 값은이 클래스의 인스턴스에서 유지 관리 됩니다. **Mybot** 클래스의 인스턴스는 활동이 수신 될 때마다 새로 고쳐집니다. 클래스에 다음 코드를 추가 합니다.

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. **Mybot** 클래스를 두 번 클릭 합니다. 이 클래스는 고객의 들어오는 활동에 의해 호출 되는 처리기를 호스팅합니다. 이 클래스에서는 봇과 고객 간에 대화를 빌드하는 데 사용 되는 코드를 추가 합니다. 앞에서 설명한 것 처럼이 클래스의 인스턴스는 활동이 수신 될 때마다 초기화 됩니다. 이 클래스에 다음 코드를 추가 합니다.

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. **Startup** 클래스를 두 번 클릭 합니다. 이 클래스는 bot를 초기화 합니다. 클래스에 다음 코드를 추가 합니다.

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. **프로그램** 클래스 파일을 열고 코드의 코드가 다음과 같은지 확인 합니다.

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. 변경 내용을 저장 하려면 Visual Studio 맨 위에 있는 도구 모음에서 **파일** > **모두 저장**으로 이동 합니다.

## <a name="chapter-2---create-the-azure-bot-service"></a>2 장-Azure Bot Service 만들기

이제 bot에 대 한 코드를 빌드 했으므로 Azure Portal에서 *웹 앱 봇* 서비스의 인스턴스에 게시 해야 합니다. 이 장에서는 Azure에서 봇 서비스를 만들고 구성 하는 방법을 보여 주고 코드를 게시 합니다.

1.  먼저 Azure Portal (https://portal.azure.com) 에 로그인 합니다. 

    1. 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

2.  로그인 되 면 왼쪽 위 모서리에서 **리소스 만들기** 를 클릭 하 고 *웹 앱 봇*을 검색 한 다음 **Enter 키**를 누릅니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-08.png)
 
3.  새 페이지에는 *웹 앱 봇* 서비스에 대 한 설명이 제공 됩니다. 이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-09.png)
 
4.  **만들기**를 클릭 하면 다음을 클릭 합니다.

    1. 이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.
    2. **구독**을 선택 합니다.
    3. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

        > Azure 리소스 그룹에 대 한 자세한 내용은 [다음 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) 를 참조 하세요.

    4. 새 리소스 그룹을 만드는 경우 리소스 그룹의 위치를 확인 합니다. 위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.
    5. 적절 한 **가격 책정 계층** 을 선택 합니다. *웹 앱 봇* 서비스를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.
    6. **앱 이름은** *봇 이름과*동일 하 게 남겨둘 수 있습니다. 
    7. *Bot 템플릿을* **Basic (C#)** 으로 그대로 둡니다.
    8. 계정에 대해 *App service 계획/위치* 를 자동으로 채워야 합니다.
    9. Bot을 호스트 하는 데 사용할 **Azure Storage** 를 설정 합니다. 아직 없는 경우 여기에서 만들 수 있습니다.
    10. 또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.
    11. 만들기를 클릭 합니다.
 
        ![Azure Bot Service 만들기](images/AzureLabs-Lab312-10.png)

5.  **만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

6.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-11.png) 
 
7.  알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-12.png)
 
8. 알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 새 Azure 서비스 인스턴스로 이동 됩니다. 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-13.png)
 
9.  이 시점에서 클라이언트 응용 프로그램이이 Bot 서비스와 통신할 수 있도록 **Direct Line** 이라는 기능을 설정 해야 합니다. **채널**을 클릭 한 다음, **추천 채널 추가** 섹션에서 **직접 선 채널 구성**을 클릭 합니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-14.png)

10. 이 페이지에서는 클라이언트 앱에서 봇으로 인증할 수 있는 **비밀 키** 를 찾을 수 있습니다. **표시** 단추를 클릭 하 고, 프로젝트에서 나중에 필요 하므로 표시 된 키 중 하나를 복사 합니다. 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>3 장 – Azure 웹 앱 봇 서비스에 봇 게시

이제 서비스가 준비 되었으므로 새로 만든 웹 앱 봇 서비스에 이전에 빌드한 봇 코드를 게시 해야 합니다.

> [!NOTE] 
> Bot 솔루션/코드를 변경할 때마다 Azure 서비스에 봇을 게시 해야 합니다.

1.  이전에 만든 Visual Studio 솔루션으로 돌아갑니다. 
2.  **솔루션 탐색기**에서 **mybot** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **게시**를 클릭 합니다.

    ![Azure 웹 앱 봇 서비스에 봇 게시](images/AzureLabs-Lab312-16.png)

3.  *게시 대상 선택* 페이지에서 **App Service**를 클릭 한 다음 기존 프로필 만들기를 **선택**합니다. 마지막으로 **프로필 만들기** 를 클릭 합니다 (표시 되지 않는 경우 *게시* 단추와 함께 드롭다운 화살표를 클릭 해야 할 수 있음).

    ![Azure 웹 앱 봇 서비스에 봇 게시](images/AzureLabs-Lab312-17.png)

4. Microsoft 계정에 아직 로그인 하지 않은 경우 여기에서 작업을 수행 해야 합니다.
5. **게시** 페이지에서 *웹 앱 봇* 서비스 생성에 사용한 것과 동일한 **구독** 을 설정 해야 합니다. 그런 다음 **보기** 를 **리소스 그룹** 으로 설정 하 고 드롭다운 폴더 구조에서 이전에 만든 **리소스 그룹** 을 선택 합니다. **확인**을 클릭합니다. 

    ![Azure 웹 앱 봇 서비스에 봇 게시](images/AzureLabs-Lab312-18.png)

6.  이제 **게시** 단추를 클릭 하 고 봇이 게시 될 때까지 기다립니다 (몇 분 정도 걸릴 수 있음).

    ![Azure 웹 앱 봇 서비스에 봇 게시](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>4 장-Unity 프로젝트 설정

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

1.  *Unity* 를 열고 **새로 만들기**를 클릭 합니다. 

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-20.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. **HoloLens 봇**을 삽입 합니다. 프로젝트 템플릿이 **3d**로 설정 되었는지 확인 합니다. 위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다. 그런 다음 **프로젝트 만들기**를 클릭 합니다.

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-21.png)

3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다. **> 기본 설정 편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-22.png)

4.  그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 **유니버설 Windows 플랫폼**을 선택한 후 **플랫폼 전환** 단추를 클릭 하 여 선택 항목을 적용 합니다.

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-23.png)

5.  아직 **파일 > 빌드 설정을** 사용 하 고 있는지 확인 합니다.

    1.  **대상 장치가** **HoloLens** 로 설정 됨

        > 모던 헤드셋의 경우 **대상 장치** 를 *모든 장치로*설정 합니다.

    2.  **빌드 형식이** **D3D** 로 설정 됩니다.

    3.  **SDK** 가 **최신 설치** 로 설정 됨

    4.  **Visual Studio 버전이** **최신 설치** 로 설정 됨

    5.  **빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨

    6.  장면을 저장 하 고 빌드에 추가 합니다. 

        1. 이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다. 저장 창이 표시 됩니다.
        
            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-24.png)

        2. 이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음

             ![Unity 프로젝트 설정](images/AzureLabs-Lab312-25.png)

        3. 새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **BotScene**를 입력 하 고 **저장**을 클릭 합니다.

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-26.png)

    7. **빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.

6. *빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다. 

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-27.png)

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. **기타 설정** 탭에서 다음을 수행 합니다.

        1. **Scripting Runtime 버전** 은 **실험적 (NET 4.6 동급)** 이어야 합니다. 이를 변경 하려면 편집기를 다시 시작 해야 합니다.
        2. **Scripting 백엔드** 는 **.net** 이어야 합니다.
        3. **API 호환성 수준은** **.net 4.6** 이어야 합니다.

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-28.png)
      
    2. **게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.

        - **InternetClient**
        - **마이크로**

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-29.png)

    3. 패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.

        ![Unity 프로젝트 설정](images/AzureLabs-Lab312-30.png)

8.  *빌드 설정* 으로 돌아가서 _Unity C#_  프로젝트가 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).


## <a name="chapter-5--camera-setup"></a>5 장-카메라 설정

> [!IMPORTANT]
> 이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [312이 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)를 다운로드 하 고 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 다음을 [계속 진행 합니다. 7 장](#chapter-8--create-the-botobjects-class).

1.  *계층 패널*에서 **기본 카메라**를 선택 합니다. 
2.  선택한 후에는 *검사기 패널*에서 **주 카메라** 의 모든 구성 요소를 볼 수 있습니다.

    1. **카메라 개체** 의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).
    2. 기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).
    3. **변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.
    4. **Clear Flags** 를 **Solid 색**으로 설정 합니다.
    5. 카메라 구성 요소의 **배경색** 을 **검은색, 알파 0 (16 진수 코드: #00000000)** 으로 설정 합니다.

    ![카메라 설정](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>6 장 – Newtonsoft.json 라이브러리 가져오기

받아서 봇 서비스로 전송 되는 개체를 deserialize 하 고 serialize 할 수 있도록 **newtonsoft.json** 라이브러리를 다운로드 해야 합니다. [여기에서 올바른 Unity 폴더 구조를 사용 하 여 이미 구성 된 호환 버전](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)을 찾을 수 있습니다. 

Newtonsoft.json 라이브러리를 프로젝트로 가져오려면이 과정에서 제공 되는 Unity 패키지를 사용 합니다.

1.   >  > **패키지 가져오기** **사용자 지정 패키지** 메뉴 옵션의 **자산** 을 사용 하 여 *unitypackage* 을 Unity에 추가 합니다.

    ![Newtonsoft.json 라이브러리 가져오기](images/AzureLabs-Lab312-34.png)

2.  표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** 을 포함 하 여 모든 항목을 선택 했는지 확인 합니다.

    ![Newtonsoft.json 라이브러리 가져오기](images/AzureLabs-Lab312-35.png)

3.  **가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.

4.  프로젝트 뷰에서 **플러그** 인의 **newtonsoft.json** 폴더로 이동 하 고 newtonsoft.json 플러그 인을 선택 합니다.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Newtonsoft.json 플러그 인을 선택한 상태에서 **모든 플랫폼이** 선택 **취소**되어 있는지 확인 한 다음 **WSAPlayer** 도 **선택 취소**되어 있는지 확인 하 고 **적용**을 클릭 합니다. 이는 파일이 올바르게 구성 되었는지 확인 하기 위한 것입니다.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > 이러한 플러그 인을 표시 하면 Unity 편집기 에서만 사용 하도록 구성 됩니다. WSA 폴더에는 프로젝트를 Unity에서 내보낸 후에 사용 되는 다른 집합이 있습니다.

6.  다음으로 **newtonsoft.json** 폴더 내에서 **WSA** 폴더를 열어야 합니다. 방금 구성한 파일의 복사본이 표시 됩니다. 파일을 선택 하 고 검사기에서 다음을 확인 합니다.
    -   **모든 플랫폼이** **선택 취소** 되어 있음 
    -   **WSAPlayer** 만 **선택** 됩니다.
    -   **Dont 프로세스** 를 **선택 했습니다** .

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>7 장-BotTag 만들기

1.  **BotTag**라는 새 **Tag** 개체를 만듭니다. 장면에서 주 카메라를 선택 합니다. 검사기 패널에서 태그 드롭다운 메뉴를 클릭 합니다. **태그 추가**를 클릭 합니다.

    ![카메라 설정](images/AzureLabs-Lab312-32.png)
 
2.  **+** 기호를 클릭 합니다. 새 **태그** 의 이름을 **BotTag**, *Save*로 합니다.

    ![카메라 설정](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **BotTag** 를 기본 카메라에 적용 **하지 마십시오** . 실수로이 작업을 수행한 경우 주 카메라 태그를 *Maincamera*로 다시 변경 해야 합니다.

## <a name="chapter-8--create-the-botobjects-class"></a>8 장 – BotObjects 클래스 만들기

만들어야 하는 첫 번째 스크립트는 **BotObjects** 클래스입니다 .이 클래스는 일련의 다른 클래스 개체를 동일한 스크립트 내에 저장 하 고 장면의 다른 스크립트에서 액세스할 수 있도록 만들어지는 빈 클래스입니다.

이 클래스를 만드는 것은 전적으로 아키텍처를 선택 하는 것입니다. 이러한 개체는이 과정의 뒷부분에서 만들 Bot 스크립트에서 호스팅될 수 있습니다.

이 클래스를 만들려면: 

1.  *프로젝트 패널*을 마우스 오른쪽 단추로 클릭 하 고 **> 폴더를 만듭니다**. 폴더 이름을 **스크립트**로 합니다. 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab312-36.png)

2.  **Scripts** 폴더를 두 번 클릭 하 여 엽니다. 그런 다음 해당 폴더 내에서를 마우스 오른쪽 단추로 클릭 하 고  **C# > 스크립트 만들기**를 선택 합니다. 스크립트 이름을 **BotObjects**로 합니다. 

3.  새 **BotObjects** 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.

4.  스크립트의 내용을 삭제 하 고 다음 코드로 바꿉니다.

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  *Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-9--create-the-gazeinput-class"></a>9 장 – GazeInput 클래스 만들기

만들려는 다음 클래스는 **GazeInput** 클래스입니다. 이 클래스는 다음을 담당 합니다.

- 플레이어의 *응시* 를 나타내는 커서를 만듭니다.
- 플레이어를 응시 하 고 검색 된 개체에 대 한 참조를 보유 하는 개체를 검색 합니다.

이 클래스를 만들려면: 

1.  이전에 만든 **스크립트** 폴더로 이동 합니다. 
2.  폴더 내부를 마우스 오른쪽 단추로 클릭 하 **> C# 스크립트를 만듭니다**. **GazeInput**스크립트를 호출 합니다. 
3.  새 **GazeInput** 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.
4.  클래스 이름 바로 위에 다음 줄을 삽입 합니다.

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  그런 다음 **GazeInput** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  **Start ()** 메서드에 대 한 코드를 추가 해야 합니다. 클래스가 초기화 될 때 호출 됩니다.

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  응시 커서를 인스턴스화하고 설정 하는 메서드를 구현 합니다. 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  기본 카메라에서 Raycast를 설정 하 고 현재 포커스가 있는 개체를 추적 하는 메서드를 구현 합니다.

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  *Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-10--create-the-bot-class"></a>10 장 – Bot 클래스 만들기

지금 만들려는 스크립트를 **봇**이라고 합니다. 이 클래스는 응용 프로그램의 핵심 클래스 이며 다음을 저장 합니다. 

- 웹 앱 봇 자격 증명
- 사용자 음성 명령을 수집 하는 메서드
- 웹 앱 봇에서 대화를 시작 하는 데 필요한 방법 
- 웹 앱 봇에 메시지를 보내는 데 필요한 방법 

Bot Service로 메시지를 보내기 위해 **SendMessageToBot ()** 코 루틴는 사용자가 보낸 데이터로 bot Framework에서 인식 하는 개체인 활동을 빌드합니다. 
 
이 클래스를 만들려면: 

1. **Scripts** 폴더를 두 번 클릭 하 여 엽니다. 
2. **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다. 스크립트의 이름을 **Bot**로 합니다. 
3. 새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
4. **Bot** 클래스의 위쪽에서 다음과 같이 네임 스페이스를 업데이트 합니다.

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. **Bot** 클래스 내에서 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > **BotSecret** 변수에 **봇 비밀 키** 를 삽입 했는지 확인 합니다. 이 과정의 시작 부분에 있는  **[2 장](#chapter-2---create-the-azure-bot-service), 10 단계**에서 **봇 비밀 키** 를 적어 두는 것을 볼 수 있습니다.

7. 이제 해제 **()** 및 **Start ()** 에 대 한 코드를 추가 해야 합니다. 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. 음성 캡처가 시작 되 고 끝날 때 음성 라이브러리에서 호출 하는 두 처리기를 추가 합니다. *DictationRecognizer* 사용자가 말하기를 중지 하면 자동으로 사용자 음성 캡처가 중지 됩니다.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. 다음 처리기는 사용자 음성 입력의 결과를 수집 하 고 웹 앱 봇 서비스에 메시지를 전송 하는 것을 담당 하는 코 루틴을 호출 합니다.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. 다음 코 루틴는 Bot를 사용 하 여 대화를 시작 하기 위해 호출 됩니다. 대화 호출이 완료 되 면 활동을 **SendMessageToCoroutine ()** 를 호출 하는 일련의 매개 변수를 전달 하 여 해당 활동을 빈 메시지로 전달 하 게 됩니다. 이 작업은 봇 서비스에 대화를 시작 하 라는 메시지를 표시 하기 위해 수행 됩니다.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. 다음 코 루틴는 Bot 서비스로 보낼 활동을 빌드하기 위해 호출 됩니다. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. 다음 코 루틴는 작업을 Bot Service로 보낸 후 응답을 요청 하기 위해 호출 됩니다. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. 이 클래스에 추가할 마지막 메서드는 장면에 메시지를 표시 하는 데 필요 합니다.

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > Unity 편집기 콘솔에 **SceneOrganiser** 클래스 누락에 대 한 오류가 표시 될 수 있습니다. 자습서의 뒷부분에서이 클래스를 만들 때이 메시지는 무시 합니다.

14.  *Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-11--create-the-interactions-class"></a>11 장-상호 작용 클래스 만들기

지금 만들 클래스를 **상호 작용**이라고 합니다. 이 클래스는 사용자의 HoloLens 탭 입력을 검색 하는 데 사용 됩니다. 

장면에서 *봇* 개체를 확인 하는 동안 사용자를 누르면 봇이 음성 입력을 수신할 준비가 되 면 봇 개체가 색을 **빨강** 으로 변경 하 고 음성 입력 수신 대기를 시작 합니다. 

이 클래스는 **GazeInput** 클래스에서 상속 하므로 **base**를 사용 하는 것으로 표시 된 해당 클래스에서 **Start ()** 메서드 및 변수를 참조할 수 있습니다. 
 
이 클래스를 만들려면:

1.  **Scripts** 폴더를 두 번 클릭 하 여 엽니다. 
2.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다. 스크립트 **상호 작용**의 이름을로 합니다. 
3.  새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
4.  **상호 작용** 클래스의 위쪽에서 네임 스페이스와 클래스 상속을 다음과 같이 업데이트 합니다.

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  **상호 작용** 클래스 내에서 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  그런 다음 **Start ()** 메서드를 추가 합니다.

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  사용자가 HoloLens 카메라 앞에서 탭 제스처를 수행할 때 트리거되는 처리기를 추가 합니다.

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. *Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>12 장 – SceneOrganiser 클래스 만들기

이 랩에서 필요한 마지막 클래스를 **SceneOrganiser**라고 합니다. 이 클래스는 기본 카메라에 구성 요소 및 스크립트를 추가 하 고 장면에 적절 한 개체를 만들어 프로그래밍 방식으로 장면을 설정 합니다.
 
이 클래스를 만들려면:

1.  **Scripts** 폴더를 두 번 클릭 하 여 엽니다. 
2.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다. 스크립트 이름을 **SceneOrganiser**로 합니다. 
3.  새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
4.  **SceneOrganiser** 클래스 내에서 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  그런 다음, no **()** 및 **Start ()** 메서드를 추가 합니다.

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  장면에서 봇 개체를 만들고 매개 변수 및 구성 요소를 설정 하는 다음 메서드를 추가 합니다.

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  다음 메서드를 추가 하 여 화면에 UI 개체를 만들고 봇의 응답을 나타냅니다.

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  *Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.
9.  Unity 편집기에서 **SceneOrganiser** 스크립트를 Scripts 폴더에서 주 카메라로 끌어 옵니다. 이제 아래 이미지에 표시 된 것 처럼 장면 Organiser 구성 요소가 기본 카메라 개체에 표시 됩니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>13 장 – 빌드하기 전

응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 HoloLens에 테스트용으로 로드 해야 합니다.
이렇게 하려면 먼저 다음을 확인 해야 합니다.

-   [**4 장**](#chapter-4--set-up-the-unity-project) 에서 설명한 모든 설정이 올바르게 설정 됩니다. 
-   **SceneOrganiser** 스크립트는 **주 카메라** 개체에 연결 됩니다. 
-   **Bot** 클래스에서 **봇 비밀 키** 를 **botSecret** 변수에 삽입 했는지 확인 합니다.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>14 장 – 테스트용으로 로드에 빌드 및

이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.

1.  **빌드 설정**, **파일 > 빌드 설정**으로 이동 합니다.
2.  **빌드 설정** 창에서 **빌드**를 클릭 합니다.

    ![Unity에서 앱 빌드](images/AzureLabs-Lab312-38.png)

3.  아직 없는 경우 tick **Unity C# 프로젝트**입니다.
4.  **빌드**를 클릭합니다. Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 **파일 탐색기** 창을 시작 합니다. 이제 해당 폴더를 만들고 이름을 **App**으로 만듭니다. 그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다. 
5.  Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다. 
6.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)

## <a name="chapter-15--deploy-to-hololens"></a>15 장 – HoloLens에 배포

HoloLens에 배포 하려면:

1.  HoloLens의 IP 주소 (원격 배포의 경우)가 필요 하 고 HoloLens가 **개발자 모드**에 있는지 확인 합니다. 이렇게 하려면 다음을 수행합니다.

    1. HoloLens를 입고 하는 동안 **설정을**엽니다.
    2. **네트워크 & 인터넷 > wi-fi > 고급 옵션** 으로 이동 합니다.
    3. **IPv4** 주소를 적어둡니다.
    4. 그런 다음 **설정**으로 다시 이동한 다음 **개발자를 위한 & 보안 >를 업데이트** 합니다. 
    5. 에서 개발자 모드를 설정 합니다.

2.  새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.
3.  **솔루션 구성** 에서 **디버그**를 선택 합니다.
4.  **솔루션 플랫폼**에서 **X86**, **원격 컴퓨터**를 선택 합니다. 

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab312-39.png)
 
5.  **빌드 메뉴로** 이동 하 여 **솔루션 배포**를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.
6.  이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되어 시작할 준비가 되었습니다!

    > [!NOTE]
    > 모던 헤드셋에 배포 하려면 **솔루션 플랫폼** 을 *로컬 컴퓨터*로 설정 하 고 **구성을** *디버그*로 설정 하 고 *x 86* 을 **플랫폼**으로 설정 합니다. 그런 다음 **빌드 메뉴**를 사용 하 여 *솔루션 배포*를 선택 하 여 로컬 컴퓨터에 배포 합니다. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>16 장-HoloLens에서 응용 프로그램 사용

- 응용 프로그램을 시작 하면 그 앞에 파란색 구로 봇이 표시 됩니다.

- 구에 gazing 하는 동안 **탭 제스처** 를 사용 하 여 대화를 시작 합니다. 
 
- 대화가 시작 될 때까지 기다립니다 (UI가 발생 하면 메시지 표시). 봇에서 소개 메시지를 받은 후 봇에서 다시 탭 하 여 빨간색으로 바뀌고 음성 듣기를 시작 합니다. 

- 통신을 중지 하면 응용 프로그램이 봇으로 메시지를 보내고 UI에 표시 되는 응답을 즉시 받게 됩니다. 

- 프로세스를 반복 하 여 봇에 더 많은 메시지를 보냅니다 (메시지를 send 할 때마다 탭 해야).

이 대화에서는 봇이 정보 (사용자 이름)를 유지할 수 있는 방법을 보여 주며, 알려진 정보 (예: 보충 항목)도 제공 합니다.

#### <a name="some-questions-to-ask-the-bot"></a>Bot 질문:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>완료 된 웹 앱 봇 (v4) 응용 프로그램

축 하 합니다. Azure 웹 앱 봇, Microsoft 봇 Framework v4를 활용 하는 혼합 현실 앱을 빌드 했습니다.

![최종 제품](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

이 랩에서 대화 구조는 매우 기본적인 것입니다. Microsoft LUIS를 사용 하 여 인공 자연어 이해 기능을 제공 합니다.

### <a name="exercise-2"></a>연습 2

이 예제에서는 대화를 종료 하 고 새 대화를 다시 시작 하는 것을 포함 하지 않습니다. Bot 기능을 완전 하 게 만들려면 대화에 대 한 클로저를 구현 해 보세요.
