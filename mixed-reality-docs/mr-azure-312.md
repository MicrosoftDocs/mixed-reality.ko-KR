---
title: MR 및 Azure 312-Bot 통합
description: 만들고 Microsoft Bot Framework v4를 사용 하 여 봇, 배포 하는 방법을 알아보려면이 과정을 완료 하 고 혼합된 현실 응용 프로그램에서 통신 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 컴퓨터 비전, hololens, vr 몰입도 microsoft bot framework v4, web app 봇, bot framework, microsoft bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604982"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

# <a name="mr-and-azure-312-bot-integration"></a>MR 및 Azure 312: 봇 통합

이 과정을 만들고 Microsoft Bot Framework V4를 사용 하는 봇 배포 및 Windows Mixed Reality 응용 프로그램을 통해 통신 하는 방법을 배웁니다. 

![](images/AzureLabs-Lab312-00.png)

합니다 **Microsoft Bot Framework V4** 개발자 도구를 확장 하 고 확장 가능한 봇 빌드를 제공 하도록 설계 Api 집합을 응용 프로그램입니다. 자세한 내용은 참조는 [Microsoft Bot Framework 페이지](https://dev.botframework.com/) 또는 [V4 Git 리포지토리](https://github.com/Microsoft/botbuilder-dotnet/wiki)합니다.

이 과정을 완료 한 후 다음을 수행 하는 일을 할 수 있는 Windows Mixed Reality 응용 프로그램을 빌드한 됩니다.

1. 사용 하 여는 **탭 제스처** 봇에 사용자 음성에 대 한 수신 대기를 시작 합니다.
2. 사용자가 내용이 포함 되어 있었습니다, 봇 응답을 제공 하려고 합니다.
3. 봇 회신 Unity 장면에서 봇, 가까이 배치한 텍스트로 표시 합니다.

응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다. 이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다. 혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 312: 봇 통합</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정 HoloLens에 주로 중점을 두고, 하는 동안 Windows Mixed Reality 몰입 형 (VR) 헤드셋을이 과정에서 배운 적용할 수 있습니다. 몰입 형 (VR) 헤드셋에 액세스할 수 있는 카메라 없기 때문에 PC에 연결 하는 외부 카메라를 해야 합니다. 과정을 따라가려면 정보 몰입 형 (VR) 헤드셋을 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.

## <a name="prerequisites"></a>사전 요구 사항

> [!NOTE]
> 이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다. 또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다. 내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.

다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.

- 개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용
- [Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여](install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여
- Azure Bot 검색 및 Azure에 대 한 인터넷 액세스. 자세한 내용은 [이 링크를 따르세요](https://dev.botframework.com/)합니다.

### <a name="before-you-start"></a>시작하기 전 주의 사항

1.  이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).
2.  설정 하 고 여 HoloLens를 테스트 합니다. 에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다. 
3.  (때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다. 

보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.

센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.

## <a name="chapter-1--create-the-bot-application"></a>1 장-봇 응용 프로그램 만들기

첫 번째 단계 봇을 로컬 ASP.Net Core 웹 응용 프로그램을 만드는 것입니다. 완료 하 고 테스트 후 Azure 포털에 게시 합니다.

1.  Visual Studio를 엽니다. 새 프로젝트를 만듭니다 **ASP NET Core 웹 응용 프로그램** (있습니다 아래 하위 섹션에서는.NET Core) 프로젝트 형식으로 호출 **MyBot**합니다. **확인**을 클릭합니다.

2.  선택 표시 되는 창의 **빈**합니다. 또한 대상 설정 되어 있는지 확인 **ASP NET Core 2.0** 인증으로 설정 됩니다 **인증 안 함**합니다. **확인**을 클릭합니다.  

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-01.png)

3.  솔루션이 열립니다. 솔루션을 마우스 오른쪽 단추로 클릭 **Mybot** 에 **솔루션 탐색기** 클릭 **솔루션용 NuGet 패키지 관리**합니다. 

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-02.png)

4.  에 **찾아보기** 탭에서 검색할 **Microsoft.Bot.Builder.Integration.AspNet.Core** (했는지 **시험판 포함** 확인). 패키지 버전을 선택 **4.0.1-preview**, 프로젝트 상자 눈금. 클릭 **설치**합니다. 이제에 필요한 라이브러리를 설치 합니다 **Bot Framework v4**합니다. NuGet 페이지를 닫습니다.

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-03.png)

5.  마우스 오른쪽 단추로 클릭 하 *프로젝트*, **MyBot**에서 합니다 **솔루션 탐색기** 을 클릭할 **추가** **|** **클래스**합니다.

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-04.png)

6.  클래스의 이름을 **MyBot** 를 클릭 **추가**합니다.

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-05.png)

7.  라는 다른 클래스를 만들려면 이전 점이 반복 **ConversationContext**합니다. 

8.  마우스 오른쪽 단추로 클릭 **wwwroot** 에 **솔루션 탐색기** 클릭 **추가** **|** **새항목**. 선택 **HTML 페이지** (알 수 있을 것 하위 섹션에서는 웹에서). 파일 이름을 **default.html**합니다. **추가**를 클릭합니다.

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-06.png)

9.  클래스의 목록은 개체 / 합니다 **솔루션 탐색기** 아래 이미지와 같습니다.

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-07.png)

10. 두 번 클릭 합니다 **ConversationContext** 클래스입니다. 이 클래스는 봇 대화 컨텍스트를 유지 하기 위해 사용 하는 변수를 보유 하는 일을 담당 합니다. 때문에 이러한 대화 컨텍스트 값은이 클래스의 인스턴스에서 유지 관리의 모든 인스턴스를 **MyBot** 클래스 활동 수신 될 때마다 새로 고쳐집니다. 클래스에 다음 코드를 추가 합니다.

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

11. 두 번 클릭 합니다 **MyBot** 클래스입니다. 이 클래스는 고객 으로부터 받는 모든 활동에 의해 호출 처리기를 호스팅합니다. 이 클래스에서 봇와 고객 간의 대화를 빌드하는 데 사용 하는 코드를 추가 합니다. 앞에서 설명한 대로이 클래스의 인스턴스는 활동 수신 될 때마다 초기화 됩니다. 이 클래스에 다음 코드를 추가 합니다.

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

12. 두 번 클릭 합니다 **시작** 클래스입니다. 이 클래스는 봇을 초기화 합니다. 클래스에 다음 코드를 추가 합니다.

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

13. 엽니다는 **프로그램** 클래스 파일 및 해당 코드를 다음과 같이 같은지 확인 합니다.

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

14. 로를 위해 변경 내용을 저장 해야 **파일** > **모두 저장**, Visual Studio의 맨 위에 있는 도구 모음에서.

## <a name="chapter-2---create-the-azure-bot-service"></a>-2 장 Azure Bot Service 만들기

인스턴스를 게시 해야 하는 코드 봇에 빌드 합니다 *Web App 봇* Azure Portal에서 서비스 합니다. 이 장에서 만들 azure Bot Service를 구성 하 고 다음 코드를 게시 하는 방법을 보여 줍니다.

1.  먼저 Azure Portal에 로그인 (https://portal.azure.com)합니다. 

    1. Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다. 클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.

2.  일단 로그인 하면 클릭할 **리소스 만들기** 왼쪽 위에서 모서리 및 검색 *Web App 봇*를 클릭 하 고 **Enter**합니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-08.png)
 
3.  새 페이지에 대 한 설명을 제공 합니다는 *Web App 봇* 서비스입니다. 선택이 페이지의 왼쪽 아래에 있는 합니다 **만들기** 이 연결 서비스를 만들려면 단추입니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-09.png)
 
4.  클릭 한 후 **만들기**:

    1. 원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.
    2. 선택 된 **구독**합니다.
    3. 선택 된 **리소스 그룹** 하거나 새로 만듭니다. 리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다. 좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).

        > 추가 하려는 경우 Azure 리소스 그룹에 대 한 [이 링크를 따르세요.](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹의 위치를 결정 합니다. 위치는 응용 프로그램은 실행할 지역의 것이 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.
    5. 선택 된 **가격 책정 계층** 첫 번째 경우, 적절 한 시간 만들기는 *Web App 봇* 서비스, 무료 계층 (F0 라는)를 사용할 수 있어야
    6. **앱 이름** 방금에 남겨둘 수와 동일 합니다 *봇 이름*합니다. 
    7. 유지 된 *Bot 템플릿을* 으로 **기본 (C#)** 합니다.
    8. *App service 계획/위치* 계정에 대해 자동으로 채워진 었어야 합니다.
    9. 설정 합니다 **Azure Storage** 봇을 호스트할 사용 하려고 합니다. 없다면 이미, 여기서 만들 수 있습니다.
    10. 이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.
    11. 만들기를 클릭 합니다.
 
        ![Azure Bot Service 만들기](images/AzureLabs-Lab312-10.png)

5.  클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.

6.  서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-11.png) 
 
7.  새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다. 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-12.png)
 
8. 클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다. 새 Azure 서비스에 연결 됩니다. 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-13.png)
 
9.  라는 기능을 설치 해야 하는 시점 **직접 회선** 클라이언트 응용 프로그램이이 Bot 서비스와 통신할 수 있도록 합니다. 클릭할 **채널**, 그런 다음는 **추천된 채널 추가** 섹션을 클릭 **구성 직접 회선 채널**합니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-14.png)

10. 이 페이지에서 찾을 수 있습니다 합니다 **비밀 키** 클라이언트 앱 봇으로 인증할 수 있도록 합니다. 클릭 합니다 **표시** 단추 및 프로젝트에서 나중에이 필요 하므로 하나 표시 키의 복사본을 만듭니다. 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>– 3 장 봇을 Azure Web App 봇 서비스에 게시

이제 서비스 준비 되 면 새로 만든된 웹 앱 봇 서비스에 이전에 작성 하는 봇 코드를 게시 해야 합니다.

> [!NOTE] 
> 봇 솔루션에 변경 될 때마다 Azure 서비스에 봇을 게시 해야 / c o d.

1.  이전에 만든 Visual Studio 솔루션으로 돌아갑니다. 
2.  마우스 오른쪽 단추로 클릭 하 **MyBot** 프로젝트를 합니다 **솔루션 탐색기**, 클릭 **게시**합니다.

    ![봇 Azure Web App 봇 서비스에 게시](images/AzureLabs-Lab312-16.png)

3.  에 *게시 대상 선택* 페이지에서 **App Service**, 한 다음 **기존 항목 선택**, 마지막 클릭 **프로필 만들기** (해야 할 수 있습니다 옆에 있는 드롭다운 화살표를 클릭 합니다 *게시* 단추에 표시 되지 않는 경우).

    ![봇 Azure Web App 봇 서비스에 게시](images/AzureLabs-Lab312-17.png)

4. 하면 로그인 하지 않은 아직 Microsoft 계정으로, 다음 작업을 수행 해야 합니다.
5. 에 **게시** 동일 하 게 설정 해야 하는 것이 보면 페이지 **구독** 에 사용 하는 합니다 *Web App 봇* 서비스 만들기. 설정한 합니다 **보기** 으로 **리소스 그룹** 드롭다운 폴더 구조 목록에서 선택 합니다 **리소스 그룹** 이전에 만든 합니다. **확인**을 클릭합니다. 

    ![봇 Azure Web App 봇 서비스에 게시](images/AzureLabs-Lab312-18.png)

6.  클릭 합니다 **게시** 단추 및 봇에 게시 될 때까지 기다립니다 (몇 분 정도 걸릴 수 있습니다).

    ![봇 Azure Web App 봇 서비스에 게시](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>4 장-Unity 프로젝트 설정

다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.

1.  오픈 *Unity* 누릅니다 **새로 만들기**합니다. 

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-20.png)

2.  이제 Unity 프로젝트 이름을 제공 해야 합니다. 삽입 **Hololens Bot**합니다. 프로젝트 템플릿은 설정 되어 있는지 확인 **3D**합니다. 설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다). 그런 다음 클릭 **프로젝트 만들기**합니다.

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-21.png)

3.  Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다. 로 이동 **편집 > 기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다. 변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다. 닫기 합니다 **기본 설정** 창입니다.

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-22.png)

4.  이동한 다음 **파일 > 빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환** 선택 항목을 적용 하려면 단추.

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-23.png)

5.  여전히 **파일 > 빌드 설정** 되어 있는지 확인 합니다.

    1.  **장치를 대상** 로 설정 된 **Hololens**

        > 몰입 형 헤드셋, 설정 **대상 장치** 하 *모든 장치*합니다.

    2.  **빌드 형식** 로 설정 된 **D3D**

    3.  **SDK** 로 설정 된 **가장 최근에 설치 된**

    4.  **Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**

    5.  **빌드 및 실행** 로 설정 된 **로컬 컴퓨터**

    6.  장면 저장 하 고 빌드에 추가 합니다. 

        1. 선택 하 여이 작업을 수행할 **열고 장면 추가**합니다. 창 저장 나타납니다.
        
            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-24.png)

        2. 새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.

             ![Unity 프로젝트 설정](images/AzureLabs-Lab312-25.png)

        3. 새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **BotScene**, 클릭 **저장**합니다.

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-26.png)

    7. 설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.

6. 에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한. 

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-27.png)

7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. 에 **기타 설정** 탭:

        1. **스크립팅 런타임 버전** 있어야 **실험적 (NET 4.6 동등)**; 편집기를 다시 시작이를 변경 해야 합니다.
        2. **백 엔드를 스크립팅** 있어야 **.NET**
        3. **API 호환성 수준** 있어야 **.NET 4.6**

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-28.png)
      
    2. 내 합니다 **게시 설정** 탭의 **기능**, 확인:

        - **InternetClient**
        - **Microphone**

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-29.png)

    3. 패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.

        ![Unity 프로젝트 설정](images/AzureLabs-Lab312-30.png)

8.  년대 *빌드 설정* _Unity C#_  프로젝트는 더 이상 회색으로;이 옆의 확인란을 선택 합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).


## <a name="chapter-5--camera-setup"></a>5 장-카메라 설정

> [!IMPORTANT]
> 건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [Azure MR-312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)을 로프로젝트로가져올[ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 선택한 다음에서 계속 [7 장](#chapter-7-–-create-the-botobjects-class)합니다.

1.  에 *계층 패널*를 선택 합니다 **주 카메라**합니다. 
2.  선택한 후에의 모든 구성 요소를 볼 수는 합니다 **주 카메라** 에 *검사기 패널*합니다.

    1. 합니다 **카메라 개체** 이름은 **주 카메라** (맞춤법을 확인 합니다.)
    2. 주 카메라 **태그** 으로 설정 되어 있어야 **MainCamera** (맞춤법을 확인 합니다.)
    3. 있는지 확인 합니다 **변환 위치** 로 설정 된 **0, 0, 0**
    4. 설정 **플래그 지우기** 하 **단색**합니다.
    5. 설정 된 **백그라운드** 카메라 구성 요소의 색 **검정, 알파 0 (16 진수 코드: #00000000)**

    ![카메라 설정](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>6 장-Newtonsoft 라이브러리 가져오기

봇 서비스에 보내고 받은 개체를 serialize 및 deserialize 하는 데 다운로드 해야 합니다 **Newtonsoft** 라이브러리입니다. 찾을 수 있습니다는 [호환 되는 버전 여기 잘못 Unity 폴더 구조를 사용 하 여 이미 구성](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)합니다. 

Newtonsoft 라이브러리를 프로젝트로 가져오는이 과정을 통해 제공 된 Unity 패키지를 사용 합니다.

1.  추가 된 *.unitypackage* 사용 하 여 Unity에는 **자산** > **패키지 가져오기** > **사용자 지정 패키지** 메뉴 옵션입니다.

    ![Newtonsoft 라이브러리 가져오기](images/AzureLabs-Lab312-34.png)

2.  에 **Unity 패키지 가져오기** 표시 되는 상자에서 아래에 있는 포함 하 여 모든 것을 확인 **플러그 인** 을 선택 합니다.

    ![Newtonsoft 라이브러리 가져오기](images/AzureLabs-Lab312-35.png)

3.  클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.

4.  로 이동 합니다 **Newtonsoft** 아래에 폴더 **플러그 인** 프로젝트 보기를 Newtonsoft 플러그 인을 선택 합니다.

    ![](images/AzureLabs-Lab312-35b.png)

5.  선택한 Newtonsoft 플러그 인을 사용 하 여 있는지를 확인 **Any 플랫폼** 는 **unchecked**, 한지 확인 합니다 **WSAPlayer** 이기도 **검사 되지 않은**, 누른 **적용**합니다. 이 파일이 올바르게 구성 되어 있는지 확인 합니다.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > 이러한 플러그 인을 표시만 Unity 편집기에서 사용 되도록 구성 합니다. Unity에서 프로젝트를 내보낸 후 사용 되는 WSA 폴더에서 다른 집합을 있습니다.

6.  열어야 할 때 다음에 **WSA** 폴더 내에서 합니다 **Newtonsoft** 폴더입니다. 방금 구성한 동일한 파일의 복사본을 볼 수 있습니다. 파일을 선택 하 고 [관리자]에서 확인 하는
    -   **모든 플랫폼** 는 **선택 취소 되어 있음** 
    -   **만** **WSAPlayer** 는 **확인**
    -   **처리 하지 않음** 는 **확인**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>7 장 –는 BotTag 만들기

1.  새 **태그** 라는 개체 **BotTag**합니다. 주 카메라 장면에서 선택 합니다. 태그에 대 한 드롭다운 검사기 창에서 메뉴를 클릭 합니다. 클릭할 **태그를 추가**합니다.

    ![카메라 설정](images/AzureLabs-Lab312-32.png)
 
2.  클릭 합니다 **+** 기호입니다. 새 이름을 **태그** 으로 **BotTag**하십시오 *저장*합니다.

    ![카메라 설정](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **하지** 적용 된 **BotTag** 주 카메라입니다. 실수로 수행한 경우이 변경 해야 태그를 주 카메라 *MainCamera*합니다.

## <a name="chapter-8--create-the-botobjects-class"></a>8 장-BotObjects 클래스 만들기

생성 해야 하는 첫 번째 스크립트는 **BotObjects** 동일한 스크립트 내 일련의 다른 클래스 개체에 저장할 수 있도록 만들고 장면에서 다른 스크립트에서 액세스 하는 빈 클래스 클래스.

이 클래스의 생성은 순수 하 게 아키텍처, 이러한 개체는이 과정의 뒷부분에서 만들 봇 스크립트 대신 호스트 될 수 있습니다.

이 클래스를 만들려면: 

1.  마우스 오른쪽 단추로 클릭 합니다 *프로젝트 패널*, 한 다음 **만들기 > 폴더**합니다. 폴더의 이름을 **스크립트**합니다. 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab312-36.png)

2.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 해당 폴더를 마우스 오른쪽 단추로 선택 내에서 다음 **만들기 > C# 스크립트**합니다. 스크립트 이름을 **BotObjects**합니다. 

3.  새 두 번 클릭 **BotObjects** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.

4.  스크립트의 콘텐츠를 삭제 하 고 다음 코드로 바꿉니다.

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

6.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

## <a name="chapter-9--create-the-gazeinput-class"></a>9 장-GazeInput 클래스 만들기

다음 클래스를 만드는 것은 **GazeInput** 클래스입니다. 이 클래스는 담당 합니다.

- 커서를 만들기가 나타내는 합니다 *gaze* 플레이어의 합니다.
- 선수의 게이즈 발생 하는 개체를 검색 하 고 검색 된 개체에 대 한 참조를 보유 합니다.

이 클래스를 만들려면: 

1.  로 이동 합니다 **스크립트** 이전에 만든 폴더입니다. 
2.  폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다. 스크립트를 호출할 **GazeInput**합니다. 
3.  새 두 번 클릭 **GazeInput** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.
4.  클래스 이름에 바로 위에 다음 줄을 삽입 합니다.

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  다음 내에서 다음 변수를 추가 합니다 **GazeInput** 위의 클래스는 **start ()** 메서드:

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

6.  에 대 한 코드 **start ()** 메서드를 추가 해야 합니다. 이 클래스를 초기화할 때 호출 됩니다.

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

7.  인스턴스화를 응시 커서를 설정 하는 메서드를 구현 합니다. 

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

8.  주 카메라에서 Raycast 설정 및는 추적할 현재 포커스가 있는 개체는 메서드를 구현 합니다.

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
 
9.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

## <a name="chapter-10--create-the-bot-class"></a>10 장-Bot 클래스 만들기

이제 만들려는 하려는 스크립트를 호출 **Bot**합니다. 응용 프로그램의 핵심 클래스를 저장 합니다. 

- Web App 봇 자격 증명
- 사용자 음성 명령에서 수집 하는 메서드
- 웹 응용 프로그램 봇을 사용 하 여 대화를 시작 하는 데 필요한 메서드 
- 웹 응용 프로그램 봇을에 메시지를 보내는 데 필요한 메서드 

봇 서비스에 메시지를 보내도록 합니다 **SendMessageToBot()** 코 루틴에서 사용자가 보낸 데이터로 Bot Framework에서 인식 하는 개체인 활동을 빌드합니다. 
 
이 클래스를 만들려면: 

1. 두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 
2. 마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 **Bot**합니다. 
3. Visual Studio를 사용 하 여 열에 새 스크립트를 두 번 클릭 합니다.
4. 네임 스페이스의 맨 위에 있는 다음과 같을 수를 업데이트 합니다 **Bot** 클래스:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. 내부를 **Bot** 클래스에 다음 변수를 추가 합니다.

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
    > 삽입 해야 하 **Bot 비밀 키** 에 **botSecret** 변수입니다. 가 기록한 사용자 **Bot 비밀 키** 이 과정의 시작 부분에  **[2 장](#chapter-2---create-the-azure-bot-service), 10 단계**합니다.

7. 에 대 한 코드 **Awake()** 하 고 **start ()** 추가 해야 합니다. 

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

8. 음성 캡처를 시작 및 종료 하는 경우 음성 라이브러리에서 호출 되는 두 명의 처리기를 추가 합니다. 합니다 *DictationRecognizer* 말하기 중지할 때 사용자 음성 캡처 자동으로 중지 됩니다.

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

1. 다음 처리기는 사용자 음성 입력의 결과 수집 하 고 웹 앱 봇 서비스에 메시지를 보내는 코 루틴을 호출 합니다.

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

10. 봇에 사용 하 여 대화를 시작 하려면 다음 코 루틴 일 이라고 합니다. 대화 호출이 완료 되 면 호출을 확인할 수 있습니다 합니다 **SendMessageToCoroutine()** 는 일련의 빈 메시지로 Bot Service를 전송할 수 있도록 활동을 설정 하는 매개 변수를 전달 하 여 합니다. Bot Service와 관련 된 대화를 시작 하려면 프롬프트에 수행 됩니다.

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

11. Bot Service를 전송할 수 있도록 활동을 빌드한 다음 코 루틴 일 이라고 합니다. 

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

12. 봇 서비스에 활동을 보낸 후 응답을 요청 하려면 다음 코 루틴 일 이라고 합니다. 

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

13. 이 클래스에 추가할 마지막 메서드는 장면에서 메시지를 표시 해야 합니다.

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
    > Unity 편집기 콘솔 누락 하는 방법에 대 한 오류가 표시 될 수 있습니다 합니다 **SceneOrganiser** 클래스입니다. 자습서의 뒷부분에 나오는이 클래스를 만들기는이 메시지는 무시 합니다.

14.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

## <a name="chapter-11--create-the-interactions-class"></a>11 장-상호 작용 클래스 만들기

클래스를 만드는 것은 이제 라고 **상호 작용**합니다. 이 클래스는 사용자 로부터 HoloLens 탭 입력 검색할 사용 됩니다. 

확인 하는 동안 사용자가 누를 경우는 *Bot* 봇 장면에 개체는 음성 입력을 수신 하도록 준비, 봇 개체는 색을 변경 **빨간색** 음성 입력에 대 한 수신 대기를 시작 합니다. 

이 클래스에서 상속 된 **GazeInput** 클래스를 참조할 수는 **start ()** 메서드 및 변수를 사용 하 여 표시 되는 클래스에서 **기본**입니다. 
 
이 클래스를 만들려면:

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 
2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 **상호 작용**합니다. 
3.  Visual Studio를 사용 하 여 열에 새 스크립트를 두 번 클릭 합니다.
4.  네임 스페이스 및 클래스 상속의 맨 위에 있는 다음과 같을 수를 업데이트 합니다 **상호 작용** 클래스:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  내 합니다 **상호 작용** 클래스에 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  그런 다음 추가 합니다 **start ()** 메서드:

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

7.  사용자가 HoloLens 카메라 앞에 탭 제스처를 수행할 때 트리거되는 처리기 추가

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

8. 변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>12 장-SceneOrganiser 클래스 만들기

이 랩에 필요한 마지막 클래스 라고 **SceneOrganiser**합니다. 이 클래스는 장면에서 해당 개체를 만들고 주 카메라에 구성 요소 및 스크립트를 추가 하 여 장면 프로그래밍 방식으로 설정 합니다.
 
이 클래스를 만들려면:

1.  두 번 클릭 합니다 **스크립트** 폴더를 엽니다. 
2.  마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다. 스크립트 이름을 **SceneOrganiser**합니다. 
3.  Visual Studio를 사용 하 여 열에 새 스크립트를 두 번 클릭 합니다.
4.  내 합니다 **SceneOrganiser** 클래스에 다음 변수를 추가 합니다.

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

6.  다음 추가 합니다 **Awake()** 하 고 **start ()** 메서드:

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

7.  장면에서 봇 개체를 만들고 매개 변수 및 구성 요소 설정에 다음 메서드를 추가 합니다.

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

7.  봇의 응답을 나타내는 장면에서 UI 개체를 만드는 다음 메서드를 추가 합니다.

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

8.  변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.
9.  Unity 편집기에서 끌어 합니다 **SceneOrganiser** 주 카메라를 Scripts 폴더에서 스크립트입니다. 장면 Organiser 구성 요소 아래 그림과에서 같이 이제 주 카메라 개체에 나타납니다.

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>13 장-빌드하기 전에

응용 프로그램의 철저 한 테스트를 수행 하려면 해야 테스트용으로 로드 하 여 HoloLens에 있습니다.
를 수행 하기 전에 확인 합니다.

-   에 언급 된 모든 설정 합니다 [ **4 장** ](#Chapter-4-–-Set-up-the-unity-project) 올바르게 설정 됩니다. 
-   스크립트 **SceneOrganiser** 에 연결할 때 합니다 **주 카메라** 개체입니다. 
-   에 **Bot** 클래스를 넣었습니다 선택 되어 있는지 확인 합니다에 **봇 비밀 키** 에 **botSecret** 변수.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>14 장-빌드 및는 HoloLens에 테스트용으로 로드

이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.

1.  이동할 **빌드 설정**, **파일 > 빌드 설정...** .
2.  **빌드 설정** 창에서 클릭 **빌드**합니다.

    ![Unity에서 앱 빌드](images/AzureLabs-Lab312-38.png)

3.  경우에 눈금 **Unity C# 프로젝트**합니다.
4.  **빌드**를 클릭합니다. Unity가 시작 됩니다는 **파일 탐색기** 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다. 해당 폴더를 이제 만들고 이름을 **앱**합니다. 사용 하 여 다음 합니다 **앱** 폴더를 선택, 클릭 **폴더 선택**합니다. 
5.  Unity 프로젝트를 빌드할 예정 된 **앱** 폴더입니다. 
6.  한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.

## <a name="chapter-15--deploy-to-hololens"></a>HoloLens에 장 15-배포

HoloLens에 배포 합니다.

1.  (배포에 대 한 원격), 여 HoloLens의 IP 주소를 사용 해야 하 고 중인에 HoloLens 되도록 **개발자 모드**합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1. 에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.
    2. 로 **네트워크 및 인터넷 > Wi-fi > 고급 옵션**
    3. 참고 합니다 **IPv4** 주소입니다.
    4. 다음으로 다시 이동할 **설정을**, 다음 **업데이트 및 보안 > 개발자 용** 
    5. 개발자 모드를 설정 합니다.

2.  새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.
3.  에 **솔루션 구성** 선택 **디버그**합니다.
4.  에 **솔루션 플랫폼**를 선택 **x86**를 **원격 컴퓨터**합니다. 

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab312-39.png)
 
5.  로 이동 합니다 **빌드 메뉴** 클릭 **솔루션 배포**, 응용 프로그램에 HoloLens 테스트용으로 로드 하려면.
6.  앱에 HoloLens 시작할 준비가에 설치 된 앱 목록에 나타나야 합니다.

    > [!NOTE]
    > 몰입 형 헤드셋을 배포 하려면 설정 합니다 **솔루션 플랫폼** 를 *로컬 컴퓨터*, 설정 및를 **구성** 에 *디버그*, 를사용하여*x86* 으로 **플랫폼**합니다. 로컬 배포 후 컴퓨터를 사용 하 여는 **빌드 메뉴**을 선택 하면 *솔루션 배포*합니다. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>16 장-는 HoloLens에서 응용 프로그램을 사용 하 여

- 응용 프로그램을 시작한 후 사용자 앞에 파란색 구도 봇을 나타납니다.

- 사용 된 **탭 제스처** 대화를 시작 하 여 구를에서 gazing 되는 동안. 
 
- 대화를 시작 될 때까지 기다립니다 (UI는 메시지가 표시 되는 경우). 봇에서 소개 메시지를 받게 되 면 탭 다시 봇 빨간색 설정 하 고 의견을 듣기를 시작 하도록 합니다. 

- 통신을 중지 하면 응용 프로그램 봇에 메시지를 송신할 후 UI에 표시 되는 응답을 즉시 받습니다. 

- (해야 될 때마다 메시지 발신자를 누릅니다) 봇을 더 많은 메시지를 보낼 프로세스를 반복 합니다.

이 대화 봇 정보 (이름)을 유지할 수는 방법을 보여 줍니다 (예: 누적 되는 항목) 알려진된 정보를 제공 하는 동안.

#### <a name="some-questions-to-ask-the-bot"></a>봇에 몇 가지 질문 합니다.

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>완성 된 Web App 봇 (v4) 응용 프로그램

축 하의 Azure Web App 봇, Microsoft Bot Framework v4를 활용 하는 혼합된 현실 앱 빌드 했습니다.

![최종 제품](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

이 랩에서 대화 구조 매우 기본적인 기능입니다. Microsoft LUIS를 사용 하 여 봇에 자연어 이해 기능.

### <a name="exercise-2"></a>연습 2

이 예제에서는 대화를 종료 하 고 새 암호를 다시 시작 포함 되지 않습니다. 봇 기능 완료를 위해 대화에는 클로저를 구현 하려고 합니다.
