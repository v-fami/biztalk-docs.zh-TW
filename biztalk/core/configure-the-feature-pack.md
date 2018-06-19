---
title: 設定此功能套件 |Microsoft 文件
description: 安裝和設定功能組件 1、 和功能套件 2。 請參閱新的功能清單，包括 API 管理中，team services 部署，Azure 的新配接器、 備份及多個 BizTalk Server 2016 中
ms.custom: ''
ms.date: 11/22/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1027bfa6-49b9-4f58-a2e2-3e0ae2fc3bf3
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b4164cf1f1355ab9a0d2f350aa5b3b5ce411e0
ms.sourcegitcommit: f4c0d7bc4b617688c643101a34062db90014851a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2017
ms.locfileid: "25550757"
---
# <a name="configure-the-feature-pack"></a><span data-ttu-id="5ab6f-104">設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="5ab6f-104">Configure the feature pack</span></span>

## <a name="overview"></a><span data-ttu-id="5ab6f-105">概觀</span><span class="sxs-lookup"><span data-stu-id="5ab6f-105">Overview</span></span>

[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5ab6f-106">您可以使用 feature pack 來提供增強功能、 功能和更緊密地與 Azure 整合。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-106"> uses feature packs to provide improvements, features, and closer integration with Azure.</span></span> <span data-ttu-id="5ab6f-107">這些功能的組件可以擴充主要區域，例如部署、 安全性、 分析、 執行階段中，與備份中的功能。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-107">These feature packs extend functionality in key areas, such as deployment, security, analytics, runtime, and backup.</span></span> 

> [!NOTE]
> <span data-ttu-id="5ab6f-108">Feature pack 可用與 Enterprise 和 Developer edition 搭配[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]時：</span><span class="sxs-lookup"><span data-stu-id="5ab6f-108">The feature packs are available with the Enterprise and Developer editions of [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] when:</span></span> 
> 
> - <span data-ttu-id="5ab6f-109">搭配軟體保證 (SA)，或</span><span class="sxs-lookup"><span data-stu-id="5ab6f-109">Used with Software Assurance (SA), OR</span></span>
> - <span data-ttu-id="5ab6f-110">執行[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]在 Azure 中使用 Enterprise 合約</span><span class="sxs-lookup"><span data-stu-id="5ab6f-110">Running [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in Azure using an Enterprise Agreement</span></span>
> 
> <span data-ttu-id="5ab6f-111">Feature pack 不適用於任何其他[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]edition 或任何其他[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-111">The feature packs are not available for any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] edition, or any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version.</span></span> 

## <a name="download-and-install"></a><span data-ttu-id="5ab6f-112">下載並安裝</span><span class="sxs-lookup"><span data-stu-id="5ab6f-112">Download and install</span></span>

<span data-ttu-id="5ab6f-113">Feature pack 是累計的。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-113">The feature packs are cumulative.</span></span> <span data-ttu-id="5ab6f-114">因此當您安裝功能套件 2，您也得到的功能和更新 feature pack 1。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-114">So when you install feature pack 2, you also get the features and updates in feature pack 1.</span></span>

* <span data-ttu-id="5ab6f-115">下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)][功能套件 2](https://aka.ms/bts2016fp2)。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-115">Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2).</span></span>

* <span data-ttu-id="5ab6f-116">下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)][功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-116">Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100).</span></span>

#### <a name="install"></a><span data-ttu-id="5ab6f-117">Install</span><span class="sxs-lookup"><span data-stu-id="5ab6f-117">Install</span></span>

1. <span data-ttu-id="5ab6f-118">以系統管理員身分執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-118">Run setup as administrator.</span></span>
2. <span data-ttu-id="5ab6f-119">在**歡迎使用**，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-119">In **Welcome**, select **Next**.</span></span> 
3. <span data-ttu-id="5ab6f-120">接受授權合約，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-120">Accept the license agreement, and select **Next**.</span></span> 
4. <span data-ttu-id="5ab6f-121">繼續安裝作業。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-121">Continue with the installation.</span></span> <span data-ttu-id="5ab6f-122">在安裝期間，數個命令視窗可能會開啟和關閉。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-122">During the install, several command windows may open and close.</span></span> <span data-ttu-id="5ab6f-123">完成時，系統會提示您**完成**。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-123">When complete, you are prompted to **Finish**.</span></span>

<span data-ttu-id="5ab6f-124">安裝程式記錄檔中建立`C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-124">A setup log is created in `C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`.</span></span>

>[!TIP]
> <span data-ttu-id="5ab6f-125">如需完整安裝的詳細指引，請參閱[Feature Pack 的逐步安裝](https://blog.sandro-pereira.com/2017/04/27/microsoft-biztalk-server-2016-feature-pack-1-step-by-step-installation/)部落格文章。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-125">For comprehensive guidance on the installation, see the [Feature Pack step-by-step installation](https://blog.sandro-pereira.com/2017/04/27/microsoft-biztalk-server-2016-feature-pack-1-step-by-step-installation/) blog post.</span></span>

## <a name="feature-pack-2-updates"></a><span data-ttu-id="5ab6f-126">功能 Pack 2 更新</span><span class="sxs-lookup"><span data-stu-id="5ab6f-126">Feature Pack 2 updates</span></span>

#### <a name="expose-soap-endpoints-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[<span data-ttu-id="5ab6f-127">公開 SOAP 端點，使用 API 管理</span><span class="sxs-lookup"><span data-stu-id="5ab6f-127">Expose SOAP endpoints with API Management</span></span>](../core/connect-to-azure-api-management.md)

<span data-ttu-id="5ab6f-128">擴充功能組件 1 所做的 API 管理整合，您現在可以公開 Wcf-basichttp 接收位置使用 BizTalk Server 管理主控台的 SOAP 端點。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-128">Expanding on the API management integration made with Feature Pack 1, you can now expose a WCF-BasicHTTP receive location as a SOAP endpoint using the BizTalk Server Administration console.</span></span> 

#### <a name="use-the-event-hub-adapterevent-hubs-adaptermd"></a>[<span data-ttu-id="5ab6f-129">使用事件中心配接器</span><span class="sxs-lookup"><span data-stu-id="5ab6f-129">Use the Event Hub adapter</span></span>](event-hubs-adapter.md)

<span data-ttu-id="5ab6f-130">從 BizTalk 傳送訊息至 Azure 事件中樞，並從 Azure 事件中心接收訊息至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-130">Send messages from BizTalk to Azure Event Hubs, and receive messages from Azure Event Hubs to BizTalk Server.</span></span> <span data-ttu-id="5ab6f-131">當您設定傳輸屬性時，您可以輕鬆地登入您的 Azure 帳戶，並自動選取 您的 Azure 事件中樞命名空間和事件中心。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-131">When you configure the transport properties, you can easily sign in to your Azure account, and automatically select your Azure Event Hubs namespace, and Event Hub.</span></span>

#### <a name="backup-to-azure-blob-accountcorehow-to-configure-the-backup-biztalk-server-jobmd"></a>[<span data-ttu-id="5ab6f-132">備份至 Azure blob 帳戶</span><span class="sxs-lookup"><span data-stu-id="5ab6f-132">Backup to Azure blob account</span></span>](../core/how-to-configure-the-backup-biztalk-server-job.md)
<span data-ttu-id="5ab6f-133">「 備份 BizTalk Server 」 工作會備份 BizTalk 資料庫和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-133">The Backup BizTalk Server job backs up the BizTalk databases and log files.</span></span> <span data-ttu-id="5ab6f-134">當您設定此 SQL Agent 作業時，您可以輸入的工作屬性內的 Azure blob 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-134">When you configure this SQL Agent job, you can enter an Azure blob storage account within the job properties.</span></span> <span data-ttu-id="5ab6f-135">這可讓您備份您的資料，而不是使用本機實體磁碟的另一個選項。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-135">This gives you another option to backup your data, instead of using a local physical disk.</span></span> 

#### <a name="multi-machine-deployment-using-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[<span data-ttu-id="5ab6f-136">使用 VSTS 多電腦部署</span><span class="sxs-lookup"><span data-stu-id="5ab6f-136">Multi-machine deployment using VSTS</span></span>](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)
<span data-ttu-id="5ab6f-137">使用部署群組，您可以部署多個 BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-137">Using deployment groups, you can deploy your applications to multiple BizTalk Servers.</span></span> <span data-ttu-id="5ab6f-138">您也可以設定在應用程式專案中，應用程式名稱，並輸入您的管理伺服器安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-138">You can also set the application name within the application project, and install your application by entering your management server.</span></span>

<span data-ttu-id="5ab6f-139">[部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index)這在 VSTS 中的完成方式提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-139">[Deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) provides more details on how this is done in VSTS.</span></span>  

#### <a name="use-service-bus-premiumcoresb-messaging-adaptermd"></a>[<span data-ttu-id="5ab6f-140">使用服務匯流排 Premium</span><span class="sxs-lookup"><span data-stu-id="5ab6f-140">Use Service Bus Premium</span></span>](../core/sb-messaging-adapter.md)

<span data-ttu-id="5ab6f-141">服務匯流排配接器支援服務匯流排 Premium，包括將訊息傳送至資料分割的佇列和主題。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-141">The Service Bus adapter supports Service Bus Premium, including sending messages to partitioned queues and topics.</span></span> <span data-ttu-id="5ab6f-142">[服務匯流排 Premium 和 Standard 傳訊層](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging)有關服務匯流排的高階詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-142">[Service Bus Premium and Standard messaging tiers](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging) details more about Service Bus Premium.</span></span> 

#### <a name="use-named-instances-with-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[<span data-ttu-id="5ab6f-143">使用 Application Insights 中使用具名執行個體</span><span class="sxs-lookup"><span data-stu-id="5ab6f-143">Use named instances with Application Insights</span></span>](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)
<span data-ttu-id="5ab6f-144">當您啟用分析，並輸入 Application Insights 金鑰時，您可能會收到錯誤：</span><span class="sxs-lookup"><span data-stu-id="5ab6f-144">When you enable Analytics, and enter the Application Insights key, you may get error:</span></span> 

```
Group settings were not applied. (A database failure occurred due to database connectivity problems.)
```

<span data-ttu-id="5ab6f-145">會發生這種情況是當您使用 SQL 具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-145">This happens when you use SQL named instances.</span></span> <span data-ttu-id="5ab6f-146">這是在此功能套件; 中修正您可以使用 SQL 的預設執行個體，而且 SQL 具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-146">This is fixed in this feature pack; you can use SQL default instances, and SQL named instances.</span></span> 

#### <a name="tls-12-support"></a><span data-ttu-id="5ab6f-147">TLS 1.2 支援</span><span class="sxs-lookup"><span data-stu-id="5ab6f-147">TLS 1.2 support</span></span>

<span data-ttu-id="5ab6f-148">在 BizTalk Server 中，包括所有介面卡和所有加速器，則完全支援 TLS 1.2。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-148">TLS 1.2 is fully supported in BizTalk Server, including all the adapters and all the accelerators.</span></span> <span data-ttu-id="5ab6f-149">您可以停用 SSL、 TLS 1.0 和 BizTalk Server 上的 TLS 1.1。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-149">You can disable SSL, TLS 1.0, and TLS 1.1 on the BizTalk Server.</span></span> 

<span data-ttu-id="5ab6f-150">索引鍵的資訊：</span><span class="sxs-lookup"><span data-stu-id="5ab6f-150">Key information:</span></span> 

* <span data-ttu-id="5ab6f-151">任何外部系統溝通 BizTalk 也需要支援 TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="5ab6f-151">Any external systems communicating with BizTalk also need to support TLS 1.2</span></span>
* <span data-ttu-id="5ab6f-152">任何自訂程式碼，例如運算質，可能需要更新為支援 TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="5ab6f-152">Any custom code, such as functoids, may need to be updated to support TLS 1.2</span></span>

<span data-ttu-id="5ab6f-153">[TLS/SSL 通訊協定的描述](https://support.microsoft.com/kb/3155464)描述如何設定 TLS 1.2 環境。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-153">[Description of the TLS/SSL protocol](https://support.microsoft.com/kb/3155464) describes how to setup a TLS 1.2 environment.</span></span> 

#### <a name="use-latest-newtonsoft-json"></a><span data-ttu-id="5ab6f-154">使用最新 Newtonsoft JSON</span><span class="sxs-lookup"><span data-stu-id="5ab6f-154">Use latest Newtonsoft JSON</span></span> 
<span data-ttu-id="5ab6f-155">Newtonsoft 是適用於.NET 的 JSON 架構。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-155">Newtonsoft is a JSON framework for .NET.</span></span> <span data-ttu-id="5ab6f-156">此功能套件，在支援版本 10.0.3 則會包含項目。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-156">In this feature pack, support for version 10.0.3 is included.</span></span> <span data-ttu-id="5ab6f-157">[下載 v。10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3)直接從 NuGet。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-157">[Download v. 10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3) directly from NuGet.</span></span> 


## <a name="feature-pack-1-updates"></a><span data-ttu-id="5ab6f-158">功能 Pack 1 更新</span><span class="sxs-lookup"><span data-stu-id="5ab6f-158">Feature Pack 1 updates</span></span>

#### <a name="send-tracking-data-to-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[<span data-ttu-id="5ab6f-159">將追蹤資料傳送至 Application Insights</span><span class="sxs-lookup"><span data-stu-id="5ab6f-159">Send tracking data to Application Insights</span></span>](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)

<span data-ttu-id="5ab6f-160">將追蹤資料傳送到 Azure Application Insights 以使用其功能，例如分析、 機器學習、 診斷與多個。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-160">Send tracking data to Azure Application Insights to use its features, such as analytics, machine learning, diagnostics, and more.</span></span> 

#### <a name="configure-the-operational-data-feed-using-power-bicoreconfigure-the-operational-data-feed-for-power-bi-with-biztalk-servermd"></a>[<span data-ttu-id="5ab6f-161">設定操作資料摘要使用 Power BI</span><span class="sxs-lookup"><span data-stu-id="5ab6f-161">Configure the operational data feed using Power BI</span></span>](../core/configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md)

<span data-ttu-id="5ab6f-162">將追蹤資料傳送到 Power BI 使用 oData。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-162">Send tracking data to Power BI using oData.</span></span> <span data-ttu-id="5ab6f-163">例如，從您的連接埠和協調流程取得追蹤資料的視覺表示法。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-163">For example, get a visual representation of your tracking data from your ports and orchestrations.</span></span> 

#### <a name="connect-to-the-management-rest-apis-in-biztalkcoreinstall-and-configure-the-management-rest-apis-in-biztalk-servermd"></a>[<span data-ttu-id="5ab6f-164">連線到管理 REST Api，在 BizTalk 中</span><span class="sxs-lookup"><span data-stu-id="5ab6f-164">Connect to the management REST APIs in BizTalk</span></span>](../core/install-and-configure-the-management-rest-apis-in-biztalk-server.md)

<span data-ttu-id="5ab6f-165">使用 REST Api 用來從遠端管理您的 BizTalk 成品，包括合約、 擱置的執行個體、 取消登錄協調流程、 等等。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-165">Use REST APIs to remotely manage your BizTalk artifacts, including agreements, suspended instances, unenlisted orchestrations, and more.</span></span>

#### <a name="configure-advanced-schedulingcoreconfigure-the-time-zone-and-recurrence-scheduling-in-biztalk-servermd"></a>[<span data-ttu-id="5ab6f-166">設定進階排程</span><span class="sxs-lookup"><span data-stu-id="5ab6f-166">Configure advanced scheduling</span></span>](../core/configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server.md)

<span data-ttu-id="5ab6f-167">啟用進階排程在您的接收位置。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-167">Enable advanced scheduling in your receive locations.</span></span> <span data-ttu-id="5ab6f-168">例如，設定時區，或設定的特定日期上特定月份循環服務窗口。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-168">For example, set the timezone, or set a recurrence service window for a specific day on a specific month.</span></span>

#### <a name="configure-automatic-deployments-with-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[<span data-ttu-id="5ab6f-169">利用 VSTS 設定自動部署</span><span class="sxs-lookup"><span data-stu-id="5ab6f-169">Configure automatic deployments with VSTS</span></span>](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  

<span data-ttu-id="5ab6f-170">若要自動部署您的解決方案，使用 Visual Studio Team Services (VSTS) 或更新現有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-170">Use Visual Studio Team Services (VSTS) to automatically deploy your solutions, or update existing applications.</span></span> <span data-ttu-id="5ab6f-171">與上安裝代理程式通訊的 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-171">VSTS communicates with an agent installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

#### <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-servercoreconnect-to-sql-server-always-encrypted-columns-with-biztalk-servermd"></a>[<span data-ttu-id="5ab6f-172">連接至 BizTalk Server 與 SQL Server 永遠加密的資料行</span><span class="sxs-lookup"><span data-stu-id="5ab6f-172">Connect to SQL Server Always Encrypted columns with BizTalk Server</span></span>](../core/connect-to-sql-server-always-encrypted-columns-with-biztalk-server.md)  

<span data-ttu-id="5ab6f-173">使用 WCF-SQL 配接器，來查詢從 SQL Server 中的永遠加密資料庫加密的資料行。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-173">Use the WCF-SQL adapter to query encrypted columns from an Always Encrypted database in SQL Server.</span></span>

#### <a name="integrate-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[<span data-ttu-id="5ab6f-174">使用 API 管理整合</span><span class="sxs-lookup"><span data-stu-id="5ab6f-174">Integrate with API Management</span></span>](../core/connect-to-azure-api-management.md)

<span data-ttu-id="5ab6f-175">在 Azure API 管理服務中，您可以建立和公開的 WSDL，API 和使用的 BizTalk SOAP 端點的 URI。</span><span class="sxs-lookup"><span data-stu-id="5ab6f-175">Within your Azure API management service, you can create and expose an API as WSDL, and use the URI to a BizTalk SOAP endpoint.</span></span>  