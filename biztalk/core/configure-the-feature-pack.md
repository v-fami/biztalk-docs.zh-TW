---
title: 設定 feature pack |Microsoft Docs
description: 安裝並設定功能套件 1，功能套件 2。 請參閱新的功能清單，包括 API 管理、 team services 部署，Azure 的新配接器、 備份和 BizTalk Server 2016 中的其他資訊
ms.custom: ''
ms.date: 06/26/2018
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
ms.openlocfilehash: 210089dc225d85271a8c8fdc426d2ca68bf353e1
ms.sourcegitcommit: 080224caa88f9935b5b13fa035d372f8964d2e52
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957866"
---
# <a name="configure-the-feature-pack"></a><span data-ttu-id="bf20c-104">設定 feature pack</span><span class="sxs-lookup"><span data-stu-id="bf20c-104">Configure the feature pack</span></span>

## <a name="overview"></a><span data-ttu-id="bf20c-105">概觀</span><span class="sxs-lookup"><span data-stu-id="bf20c-105">Overview</span></span>

[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bf20c-106"> 您可以使用 feature pack 來提供增強功能、 功能及更緊密地整合與 Azure。</span><span class="sxs-lookup"><span data-stu-id="bf20c-106"> uses feature packs to provide improvements, features, and closer integration with Azure.</span></span> <span data-ttu-id="bf20c-107">這些功能的組件擴充中重要的領域，例如部署、 安全性、 分析、 執行階段、 維護、 標準的合規性，以及混合式整合的功能。</span><span class="sxs-lookup"><span data-stu-id="bf20c-107">These feature packs extend functionality in key areas, such as deployment, security, analytics, runtime, maintainance, standard compliance, and hybrid integration.</span></span> 

> [!NOTE]
> <span data-ttu-id="bf20c-108">Feature pack 所提供的 Enterprise 和 Developer edition[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]時：</span><span class="sxs-lookup"><span data-stu-id="bf20c-108">The feature packs are available with the Enterprise and Developer editions of [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] when:</span></span> 
> 
> - <span data-ttu-id="bf20c-109">使用具備軟體保證 (SA)，或</span><span class="sxs-lookup"><span data-stu-id="bf20c-109">Used with Software Assurance (SA), OR</span></span>
> - <span data-ttu-id="bf20c-110">執行[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]在 Azure 中使用 Enterprise 合約</span><span class="sxs-lookup"><span data-stu-id="bf20c-110">Running [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in Azure using an Enterprise Agreement</span></span>
> 
> <span data-ttu-id="bf20c-111">Feature pack 不適用於任何其他[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]edition （標準版與 Branch 版），或任何其他[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本 (2013 R2、 2013、 2010，依此類推)。</span><span class="sxs-lookup"><span data-stu-id="bf20c-111">The feature packs are not available for any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] edition (Standard and Branch editions), or any other [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] version (2013 R2, 2013, 2010, and so on).</span></span> 

## <a name="download-and-install"></a><span data-ttu-id="bf20c-112">下載並安裝</span><span class="sxs-lookup"><span data-stu-id="bf20c-112">Download and install</span></span>

<span data-ttu-id="bf20c-113">Feature pack 是累計的。</span><span class="sxs-lookup"><span data-stu-id="bf20c-113">The feature packs are cumulative.</span></span> <span data-ttu-id="bf20c-114">因此當您安裝 feature pack 3，也會取得的功能和更新在 feature pack 2 和 1。</span><span class="sxs-lookup"><span data-stu-id="bf20c-114">So when you install feature pack 3, you also get the features and updates in feature packs 2 and 1.</span></span> <span data-ttu-id="bf20c-115">您也可以取得最新的累計更新。</span><span class="sxs-lookup"><span data-stu-id="bf20c-115">You also get the latest cumulative updates.</span></span>

* <span data-ttu-id="bf20c-116">下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 3](https://aka.ms/bts2016fp3)。</span><span class="sxs-lookup"><span data-stu-id="bf20c-116">Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 3](https://aka.ms/bts2016fp3).</span></span>

* <span data-ttu-id="bf20c-117">下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2)。</span><span class="sxs-lookup"><span data-stu-id="bf20c-117">Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2).</span></span>

* <span data-ttu-id="bf20c-118">下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100)。</span><span class="sxs-lookup"><span data-stu-id="bf20c-118">Download the [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100).</span></span>

#### <a name="install"></a><span data-ttu-id="bf20c-119">安裝</span><span class="sxs-lookup"><span data-stu-id="bf20c-119">Install</span></span>

1. <span data-ttu-id="bf20c-120">以系統管理員身分執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="bf20c-120">Run setup as administrator.</span></span>
2. <span data-ttu-id="bf20c-121">在 [**歡迎**，選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bf20c-121">In **Welcome**, select **Next**.</span></span> 
3. <span data-ttu-id="bf20c-122">接受授權合約，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="bf20c-122">Accept the license agreement, and select **Next**.</span></span> 
4. <span data-ttu-id="bf20c-123">繼續安裝作業。</span><span class="sxs-lookup"><span data-stu-id="bf20c-123">Continue with the installation.</span></span> <span data-ttu-id="bf20c-124">安裝過程中，可能會開啟數個命令視窗，並將其關閉中。</span><span class="sxs-lookup"><span data-stu-id="bf20c-124">During the install, several command windows may open and close.</span></span> <span data-ttu-id="bf20c-125">完成時，系統會提示您**完成**。</span><span class="sxs-lookup"><span data-stu-id="bf20c-125">When complete, you are prompted to **Finish**.</span></span>

<span data-ttu-id="bf20c-126">安裝程式記錄檔中建立`C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`。</span><span class="sxs-lookup"><span data-stu-id="bf20c-126">A setup log is created in `C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`.</span></span>

>[!TIP]
> <span data-ttu-id="bf20c-127">如需完整安裝的詳細指引，請參閱[BizTalk Server 2016 功能套件 3年︰ 逐步安裝](https://blog.sandro-pereira.com/2018/06/26/biztalk-server-2016-feature-pack-3/)部落格文章。</span><span class="sxs-lookup"><span data-stu-id="bf20c-127">For comprehensive guidance on the installation, see the [BizTalk Server 2016 Feature Pack 3: step-by-step installation](https://blog.sandro-pereira.com/2018/06/26/biztalk-server-2016-feature-pack-3/) blog post.</span></span>

## <a name="feature-pack-3-updates"></a><span data-ttu-id="bf20c-128">功能 Pack 3 更新</span><span class="sxs-lookup"><span data-stu-id="bf20c-128">Feature Pack 3 updates</span></span>

<span data-ttu-id="bf20c-129">**Office 365 配接器**</span><span class="sxs-lookup"><span data-stu-id="bf20c-129">**Office 365 Adapters**</span></span>


<span data-ttu-id="bf20c-130">Microsoft Office 365 是雲端架構的訂用帳戶服務，結合最佳的人們工具現在的運作。</span><span class="sxs-lookup"><span data-stu-id="bf20c-130">Microsoft Office 365 is a cloud-based subscription service that brings together the best tools for the way people work today.</span></span> <span data-ttu-id="bf20c-131">Office 365 內建藉由結合同級產品中的應用程式，例如 Excel 和 Outlook，OneDrive 和 Microsoft Teams 等的功能強大的雲端服務，可讓任何人建立並共用任何地方在任何裝置上。</span><span class="sxs-lookup"><span data-stu-id="bf20c-131">By combining best-in-class apps like Excel and Outlook with powerful cloud services like OneDrive and Microsoft Teams, Office 365 lets anyone create and share anywhere on any device.</span></span>

<span data-ttu-id="bf20c-132">適用於 Office 365 的 Microsoft BizTalk Server 配接器可讓 IT 專業人員和企業開發人員與 BizTalk Server 2016 為基礎的新方案整合 Outlook 郵件、 連絡人和排程。</span><span class="sxs-lookup"><span data-stu-id="bf20c-132">Microsoft BizTalk Server adapters for Office 365 enable IT professionals and enterprise developers to integrate Outlook mail, contacts, and schedules with new solutions based on BizTalk Server 2016.</span></span>

#### <a name="office-365-mail-adapteroffice365-mail-adaptermd"></a>[<span data-ttu-id="bf20c-133">Office 365 郵件配接器</span><span class="sxs-lookup"><span data-stu-id="bf20c-133">Office 365 Mail adapter</span></span>](office365-mail-adapter.md)
<span data-ttu-id="bf20c-134">您可以使用 BizTalk Adapter for Office 365 電子郵件，來讀取、 標示為已讀取或刪除 Outlook 電子郵件訊息，透過單向的 BizTalk Server 接收位置。</span><span class="sxs-lookup"><span data-stu-id="bf20c-134">Using the BizTalk Adapter for Office 365 Mail, you can read, mark as read or delete Outlook e-mail messages through one-way BizTalk Server receive locations.</span></span> <span data-ttu-id="bf20c-135">使用此配接器，您可以撰寫電子郵件訊息，包括設定訊息的優先權，透過單向靜態或動態 BizTalk Server 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="bf20c-135">Using this adapter, you can write e-mail message, including setting message priority, through one-way static or dynamic BizTalk Server send ports.</span></span>

#### <a name="office-365-calendar-adapteroffice365-calendar-adaptermd"></a>[<span data-ttu-id="bf20c-136">Office 365 行事曆配接器</span><span class="sxs-lookup"><span data-stu-id="bf20c-136">Office 365 Calendar adapter</span></span>](office365-calendar-adapter.md)
<span data-ttu-id="bf20c-137">使用 BizTalk Adapter for Office 365 行事曆，您可以取得未來的行事曆事件透過單向的 BizTalk Server 接收位置。</span><span class="sxs-lookup"><span data-stu-id="bf20c-137">Using the BizTalk Adapter for Office 365 Calendar, you can get future calendar events through one-way BizTalk Server receive locations.</span></span> <span data-ttu-id="bf20c-138">您可以使用此配接器，來建立行事曆事件和輸入必要和選擇性出席者，透過單向靜態或動態的 BizTalk Server 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="bf20c-138">Using this adapter, you can create calendar events, and enter required and optional attendees, through one-way static or dynamic BizTalk Server send ports.</span></span>

#### <a name="office-365-contact-adapteroffice365-contact-adaptermd"></a>[<span data-ttu-id="bf20c-139">Office 365 連絡人配接器</span><span class="sxs-lookup"><span data-stu-id="bf20c-139">Office 365 Contact adapter</span></span>](office365-contact-adapter.md)
<span data-ttu-id="bf20c-140">使用 BizTalk Adapter for Office 365 連絡人，您可以建立的連絡人，並輸入所有的設定，透過單向靜態或動態的 BizTalk Server 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="bf20c-140">Using the BizTalk Adapter for Office 365 Contact, you can create contacts, and enter all settings, through one-way static or dynamic BizTalk Server send ports.</span></span>

## <a name="feature-pack-2-updates"></a><span data-ttu-id="bf20c-141">功能 Pack 2 更新</span><span class="sxs-lookup"><span data-stu-id="bf20c-141">Feature Pack 2 updates</span></span>

#### <a name="expose-soap-endpoints-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[<span data-ttu-id="bf20c-142">公開 SOAP 端點，使用 API 管理</span><span class="sxs-lookup"><span data-stu-id="bf20c-142">Expose SOAP endpoints with API Management</span></span>](../core/connect-to-azure-api-management.md)

<span data-ttu-id="bf20c-143">展開含 Feature Pack 1 所做的 API 管理整合，您現在可以公開 Wcf-basichttp 接收位置做為使用 BizTalk Server 管理主控台的 SOAP 端點。</span><span class="sxs-lookup"><span data-stu-id="bf20c-143">Expanding on the API management integration made with Feature Pack 1, you can now expose a WCF-BasicHTTP receive location as a SOAP endpoint using the BizTalk Server Administration console.</span></span> 

#### <a name="use-the-event-hub-adapterevent-hubs-adaptermd"></a>[<span data-ttu-id="bf20c-144">使用事件中樞配接器</span><span class="sxs-lookup"><span data-stu-id="bf20c-144">Use the Event Hub adapter</span></span>](event-hubs-adapter.md)

<span data-ttu-id="bf20c-145">從 BizTalk 將訊息傳送至 Azure 事件中樞，並從 Azure 事件中樞接收訊息，BizTalk server。</span><span class="sxs-lookup"><span data-stu-id="bf20c-145">Send messages from BizTalk to Azure Event Hubs, and receive messages from Azure Event Hubs to BizTalk Server.</span></span> <span data-ttu-id="bf20c-146">當您設定傳輸屬性時，您可以輕鬆地登入您的 Azure 帳戶，並自動選取 您的 Azure 事件中樞命名空間和事件中樞。</span><span class="sxs-lookup"><span data-stu-id="bf20c-146">When you configure the transport properties, you can easily sign in to your Azure account, and automatically select your Azure Event Hubs namespace, and Event Hub.</span></span>

#### <a name="backup-to-azure-blob-accountcorehow-to-configure-the-backup-biztalk-server-jobmd"></a>[<span data-ttu-id="bf20c-147">備份至 Azure blob 帳戶</span><span class="sxs-lookup"><span data-stu-id="bf20c-147">Backup to Azure blob account</span></span>](../core/how-to-configure-the-backup-biztalk-server-job.md)
<span data-ttu-id="bf20c-148">「 備份 BizTalk Server 」 工作會備份 BizTalk 資料庫和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bf20c-148">The Backup BizTalk Server job backs up the BizTalk databases and log files.</span></span> <span data-ttu-id="bf20c-149">當您設定這個 SQL Agent 作業時，您可以輸入 Azure blob 儲存體帳戶內的工作屬性。</span><span class="sxs-lookup"><span data-stu-id="bf20c-149">When you configure this SQL Agent job, you can enter an Azure blob storage account within the job properties.</span></span> <span data-ttu-id="bf20c-150">這可讓您以備份您的資料，而不是使用本機的實體磁碟的另一個選項。</span><span class="sxs-lookup"><span data-stu-id="bf20c-150">This gives you another option to backup your data, instead of using a local physical disk.</span></span> 

#### <a name="multi-machine-deployment-using-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[<span data-ttu-id="bf20c-151">使用 VSTS 的多電腦部署</span><span class="sxs-lookup"><span data-stu-id="bf20c-151">Multi-machine deployment using VSTS</span></span>](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)
<span data-ttu-id="bf20c-152">您可以使用部署群組，來部署您的應用程式的多個 BizTalk 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bf20c-152">Using deployment groups, you can deploy your applications to multiple BizTalk Servers.</span></span> <span data-ttu-id="bf20c-153">您也可以設定在應用程式專案中，應用程式名稱，並輸入您的管理伺服器來安裝您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf20c-153">You can also set the application name within the application project, and install your application by entering your management server.</span></span>

<span data-ttu-id="bf20c-154">[部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index)如何做到這點在 VSTS 中提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bf20c-154">[Deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) provides more details on how this is done in VSTS.</span></span>  

#### <a name="use-service-bus-premiumcoresb-messaging-adaptermd"></a>[<span data-ttu-id="bf20c-155">使用服務匯流排進階版</span><span class="sxs-lookup"><span data-stu-id="bf20c-155">Use Service Bus Premium</span></span>](../core/sb-messaging-adapter.md)

<span data-ttu-id="bf20c-156">服務匯流排配接器支援服務匯流排進階層，包括將訊息傳送至資料分割的佇列和主題。</span><span class="sxs-lookup"><span data-stu-id="bf20c-156">The Service Bus adapter supports Service Bus Premium, including sending messages to partitioned queues and topics.</span></span> <span data-ttu-id="bf20c-157">[服務匯流排進階和標準傳訊層級](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging)詳細說明有關服務匯流排進階詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bf20c-157">[Service Bus Premium and Standard messaging tiers](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging) details more about Service Bus Premium.</span></span> 

#### <a name="use-named-instances-with-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[<span data-ttu-id="bf20c-158">使用 Application Insights 中使用具名執行個體</span><span class="sxs-lookup"><span data-stu-id="bf20c-158">Use named instances with Application Insights</span></span>](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)
<span data-ttu-id="bf20c-159">當您啟用分析，並輸入 Application Insights 金鑰時，您可能會收到錯誤：</span><span class="sxs-lookup"><span data-stu-id="bf20c-159">When you enable Analytics, and enter the Application Insights key, you may get error:</span></span> 

```
Group settings were not applied. (A database failure occurred due to database connectivity problems.)
```

<span data-ttu-id="bf20c-160">會發生這種情況是當您使用具名執行個體的 SQL。</span><span class="sxs-lookup"><span data-stu-id="bf20c-160">This happens when you use SQL named instances.</span></span> <span data-ttu-id="bf20c-161">此問題已在此功能套件;您可以使用 SQL 的預設執行個體，和 SQL 具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="bf20c-161">This is fixed in this feature pack; you can use SQL default instances, and SQL named instances.</span></span> 

#### <a name="tls-12-support"></a><span data-ttu-id="bf20c-162">TLS 1.2 支援</span><span class="sxs-lookup"><span data-stu-id="bf20c-162">TLS 1.2 support</span></span>

<span data-ttu-id="bf20c-163">在 BizTalk Server 中，包括所有配接器和所有加速器完全支援 TLS 1.2。</span><span class="sxs-lookup"><span data-stu-id="bf20c-163">TLS 1.2 is fully supported in BizTalk Server, including all the adapters and all the accelerators.</span></span> <span data-ttu-id="bf20c-164">您可以停用 SSL、 TLS 1.0 及 BizTalk Server 上的 TLS 1.1。</span><span class="sxs-lookup"><span data-stu-id="bf20c-164">You can disable SSL, TLS 1.0, and TLS 1.1 on the BizTalk Server.</span></span> 

<span data-ttu-id="bf20c-165">重要資訊：</span><span class="sxs-lookup"><span data-stu-id="bf20c-165">Key information:</span></span> 

* <span data-ttu-id="bf20c-166">也與 BizTalk 通訊的任何外部系統必須支援 TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="bf20c-166">Any external systems communicating with BizTalk also need to support TLS 1.2</span></span>
* <span data-ttu-id="bf20c-167">任何自訂程式碼，例如運算質，可能需要更新為支援 TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="bf20c-167">Any custom code, such as functoids, may need to be updated to support TLS 1.2</span></span>

<span data-ttu-id="bf20c-168">[TLS/SSL 通訊協定描述](https://support.microsoft.com/kb/3155464)描述如何設定 TLS 1.2 的環境。</span><span class="sxs-lookup"><span data-stu-id="bf20c-168">[Description of the TLS/SSL protocol](https://support.microsoft.com/kb/3155464) describes how to setup a TLS 1.2 environment.</span></span> 

#### <a name="use-latest-newtonsoft-json"></a><span data-ttu-id="bf20c-169">使用最新的 Newtonsoft JSON</span><span class="sxs-lookup"><span data-stu-id="bf20c-169">Use latest Newtonsoft JSON</span></span> 
<span data-ttu-id="bf20c-170">Newtonsoft 是適用於.NET 的 JSON 架構。</span><span class="sxs-lookup"><span data-stu-id="bf20c-170">Newtonsoft is a JSON framework for .NET.</span></span> <span data-ttu-id="bf20c-171">此功能組件中，在支援版本 10.0.3 則會包含項目。</span><span class="sxs-lookup"><span data-stu-id="bf20c-171">In this feature pack, support for version 10.0.3 is included.</span></span> <span data-ttu-id="bf20c-172">[下載 v。10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3)直接從 NuGet。</span><span class="sxs-lookup"><span data-stu-id="bf20c-172">[Download v. 10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3) directly from NuGet.</span></span> 


## <a name="feature-pack-1-updates"></a><span data-ttu-id="bf20c-173">功能 Pack 1 更新</span><span class="sxs-lookup"><span data-stu-id="bf20c-173">Feature Pack 1 updates</span></span>

#### <a name="send-tracking-data-to-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[<span data-ttu-id="bf20c-174">將追蹤資料傳送至 Application Insights</span><span class="sxs-lookup"><span data-stu-id="bf20c-174">Send tracking data to Application Insights</span></span>](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)

<span data-ttu-id="bf20c-175">將追蹤資料傳送至 Azure Application Insights，以使用其功能，例如分析、 機器學習服務、 診斷和更多功能。</span><span class="sxs-lookup"><span data-stu-id="bf20c-175">Send tracking data to Azure Application Insights to use its features, such as analytics, machine learning, diagnostics, and more.</span></span> 

#### <a name="configure-the-operational-data-feed-using-power-bicoreconfigure-the-operational-data-feed-for-power-bi-with-biztalk-servermd"></a>[<span data-ttu-id="bf20c-176">設定操作資料摘要使用 Power BI</span><span class="sxs-lookup"><span data-stu-id="bf20c-176">Configure the operational data feed using Power BI</span></span>](../core/configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md)

<span data-ttu-id="bf20c-177">將追蹤資料傳送至 Power BI 使用 oData。</span><span class="sxs-lookup"><span data-stu-id="bf20c-177">Send tracking data to Power BI using oData.</span></span> <span data-ttu-id="bf20c-178">例如，從您的連接埠和協調流程取得追蹤資料的視覺表示法。</span><span class="sxs-lookup"><span data-stu-id="bf20c-178">For example, get a visual representation of your tracking data from your ports and orchestrations.</span></span> 

#### <a name="connect-to-the-management-rest-apis-in-biztalkcoreinstall-and-configure-the-management-rest-apis-in-biztalk-servermd"></a>[<span data-ttu-id="bf20c-179">連線到管理 BizTalk 中的 REST Api</span><span class="sxs-lookup"><span data-stu-id="bf20c-179">Connect to the management REST APIs in BizTalk</span></span>](../core/install-and-configure-the-management-rest-apis-in-biztalk-server.md)

<span data-ttu-id="bf20c-180">使用 REST Api，以從遠端管理您的 BizTalk 成品，包括合約、 擱置的執行個體、 取消登錄協調流程等等。</span><span class="sxs-lookup"><span data-stu-id="bf20c-180">Use REST APIs to remotely manage your BizTalk artifacts, including agreements, suspended instances, unenlisted orchestrations, and more.</span></span>

#### <a name="configure-advanced-schedulingcoreconfigure-the-time-zone-and-recurrence-scheduling-in-biztalk-servermd"></a>[<span data-ttu-id="bf20c-181">設定進階排程</span><span class="sxs-lookup"><span data-stu-id="bf20c-181">Configure advanced scheduling</span></span>](../core/configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server.md)

<span data-ttu-id="bf20c-182">啟用進階排程在您的接收位置。</span><span class="sxs-lookup"><span data-stu-id="bf20c-182">Enable advanced scheduling in your receive locations.</span></span> <span data-ttu-id="bf20c-183">例如，設定時區，或設定在特定月份的特定日期的循環服務窗口。</span><span class="sxs-lookup"><span data-stu-id="bf20c-183">For example, set the timezone, or set a recurrence service window for a specific day on a specific month.</span></span>

#### <a name="configure-automatic-deployments-with-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[<span data-ttu-id="bf20c-184">使用 VSTS 設定自動部署</span><span class="sxs-lookup"><span data-stu-id="bf20c-184">Configure automatic deployments with VSTS</span></span>](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  

<span data-ttu-id="bf20c-185">若要自動部署您的解決方案，使用 Visual Studio Team Services (VSTS) 或更新現有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf20c-185">Use Visual Studio Team Services (VSTS) to automatically deploy your solutions, or update existing applications.</span></span> <span data-ttu-id="bf20c-186">與安裝代理程式通訊的 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf20c-186">VSTS communicates with an agent installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

#### <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-servercoreconnect-to-sql-server-always-encrypted-columns-with-biztalk-servermd"></a>[<span data-ttu-id="bf20c-187">連接至 SQL Server Always Encrypted 資料行，與 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bf20c-187">Connect to SQL Server Always Encrypted columns with BizTalk Server</span></span>](../core/connect-to-sql-server-always-encrypted-columns-with-biztalk-server.md)  

<span data-ttu-id="bf20c-188">若要查詢加密資料行，從 SQL Server 的 Always Encrypted 資料庫使用 WCF-SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="bf20c-188">Use the WCF-SQL adapter to query encrypted columns from an Always Encrypted database in SQL Server.</span></span>

#### <a name="integrate-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[<span data-ttu-id="bf20c-189">與 API 管理整合</span><span class="sxs-lookup"><span data-stu-id="bf20c-189">Integrate with API Management</span></span>](../core/connect-to-azure-api-management.md)

<span data-ttu-id="bf20c-190">在 Azure API 管理服務中，您可以建立並公開 API 的 WSDL，並使用 BizTalk SOAP 端點的 URI。</span><span class="sxs-lookup"><span data-stu-id="bf20c-190">Within your Azure API management service, you can create and expose an API as WSDL, and use the URI to a BizTalk SOAP endpoint.</span></span>  
