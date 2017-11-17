---
title: "BizTalk Server 的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1aa5fb60-e8db-4cd2-88be-3c71b7b1d44d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b7998225af7ca598d4df5b4fd98f2826edce3a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-biztalk-server"></a><span data-ttu-id="fef0c-102">BizTalk Server 的已知的問題</span><span class="sxs-lookup"><span data-stu-id="fef0c-102">Known Issues with BizTalk Server</span></span>
<span data-ttu-id="fef0c-103">本主題列出一些 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的已知問題。</span><span class="sxs-lookup"><span data-stu-id="fef0c-103">This topic lists some known issues with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="dtc-firewall-rules"></a><span data-ttu-id="fef0c-104">DTC 防火牆規則</span><span class="sxs-lookup"><span data-stu-id="fef0c-104">DTC Firewall Rules</span></span>  
 <span data-ttu-id="fef0c-105">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同的電腦時，分散式交易協調器 (MS DTC) 會處理電腦間的交易。</span><span class="sxs-lookup"><span data-stu-id="fef0c-105">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers.</span></span> <span data-ttu-id="fef0c-106">如此一來，在上啟用防火牆規則內的 DTC 通訊埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="fef0c-106">As a result, enable the DTC ports within your firewall rules on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers.</span></span>  
  
 <span data-ttu-id="fef0c-107">設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，未在防火牆中啟用的 DTC 通訊埠時，可能會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="fef0c-107">When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the following errors can occur when the DTC ports are not enabled in the firewall:</span></span>  
  
 <span data-ttu-id="fef0c-108">**資料庫建立; 發生 WMI 錯誤嘗試回復，並刪除部分建立的資料庫 'SQLServerName\BizTalkMsgBoxDb'**</span><span class="sxs-lookup"><span data-stu-id="fef0c-108">**WMI Error occurred during database creation; attempt to rollback and delete the partially created database'SQLServerName\BizTalkMsgBoxDb'**</span></span>  
  
 <span data-ttu-id="fef0c-109">**產生 WMI 錯誤描述： 類型 'System.EnterpriseServices.TransactionProxyException' 擲回的例外狀況。**</span><span class="sxs-lookup"><span data-stu-id="fef0c-109">**WMI error description is generated: Exception of type 'System.EnterpriseServices.TransactionProxyException' was thrown.**</span></span>  
  
 <span data-ttu-id="fef0c-110">下列連結提供詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="fef0c-110">The following links provide more information:</span></span>  
  
 [<span data-ttu-id="fef0c-111">管理伺服器的連接埠</span><span class="sxs-lookup"><span data-stu-id="fef0c-111">Ports for the Administration Server</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=275568)  
  
 [<span data-ttu-id="fef0c-112">BizTalk Server 2013 和 2013 R2 的後續安裝步驟</span><span class="sxs-lookup"><span data-stu-id="fef0c-112">Post-installation Steps for BizTalk Server 2013 and 2013 R2</span></span>](../install-and-config-guides/post-installation-steps-for-biztalk-server-2013-and-2013-r2.md)  
  
##  <span data-ttu-id="fef0c-113"><a name="BKMK_BAM"></a>商務活動監控</span><span class="sxs-lookup"><span data-stu-id="fef0c-113"><a name="BKMK_BAM"></a> Business Activity Monitoring</span></span>  
 <span data-ttu-id="fef0c-114">此區段會列出與商務活動監控 (BAM) 模組的已知的問題。</span><span class="sxs-lookup"><span data-stu-id="fef0c-114">This section lists the known issues with the Business Activity Monitoring (BAM) module.</span></span>  
  
### <a name="bam-definition-deployment-fails-due-to-a-sql-login-error"></a><span data-ttu-id="fef0c-115">BAM 定義部署失敗，因為發生 SQL 登入錯誤</span><span class="sxs-lookup"><span data-stu-id="fef0c-115">BAM definition deployment fails due to a SQL login error</span></span>  
 <span data-ttu-id="fef0c-116">同時部署 BAM 定義，此作業可能會因為登入錯誤，錯誤碼為 42000。</span><span class="sxs-lookup"><span data-stu-id="fef0c-116">While deploying BAM definition, the operation might fail due to a login error with error code 42000.</span></span>  
  
```  
...  
Deploying Activity... Done.   
Deploying View... ERROR: The BAM deployment failed.   
Server: The current operation was cancelled because another operation in the transaction failed.   
OLE DB error: OLE DB or ODBC error: Login failed for user <username>.; 42000.   
…  
```  
  
 <span data-ttu-id="fef0c-117">若要修正此問題，請確定 SQL Analysis Service 登入帳戶對與 BAM 相關的所有資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="fef0c-117">To fix this issue, make sure the SQL Analysis Service logon account has permissions on all databases related to BAM.</span></span>  
  
### <a name="bam-configuration-might-result-in-warnings-related-to-the-bam-analysis-logon-account"></a><span data-ttu-id="fef0c-118">BAM 組態可能會導致 BAM 分析的登入帳戶相關的警告</span><span class="sxs-lookup"><span data-stu-id="fef0c-118">BAM configuration might result in warnings related to the BAM Analysis logon account</span></span>  
 <span data-ttu-id="fef0c-119">BAM 組態會加入 BAM 分析登入帳戶的權限可以存取它們的 BAM 相關的所有資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fef0c-119">BAM configuration adds the permissions for BAM Analysis logon account in all the databases related to BAM to be able to access them.</span></span> <span data-ttu-id="fef0c-120">不過，設定可能會失敗，並發出警告，如果不符合任何下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="fef0c-120">However, the configuration might fail to do so and give a warning if any of the following prerequisites is not met:</span></span>  
  
-   <span data-ttu-id="fef0c-121">使用者執行 BAM 組態應該安裝 Analysis Services 的電腦上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="fef0c-121">The user under which the BAM configuration is run should be an administrator on the computer where Analysis Service is installed.</span></span>  
  
-   <span data-ttu-id="fef0c-122">必須允許通過防火牆的遠端管理該電腦上。</span><span class="sxs-lookup"><span data-stu-id="fef0c-122">Remote administration through firewall must be allowed on that computer.</span></span>  
  
-   <span data-ttu-id="fef0c-123">BAM 分析登入帳戶是否與 BAM 相關的資料庫安裝所在的 SQL Server 的系統管理員，您也可能會收到警告。</span><span class="sxs-lookup"><span data-stu-id="fef0c-123">You might also get a warning if the BAM Analysis logon account is an administrator for the SQL Server where the BAM-related databases are installed.</span></span> <span data-ttu-id="fef0c-124">您可以忽略此警告，並往前移動。</span><span class="sxs-lookup"><span data-stu-id="fef0c-124">You can ignore the warning and move ahead.</span></span>  
  
 <span data-ttu-id="fef0c-125">**因應措施**– 您必須手動將 BAM 分析登入帳戶的權限與 BAM 相關的所有資料庫上。</span><span class="sxs-lookup"><span data-stu-id="fef0c-125">**Workaround** – You must manually add the permission for the BAM Analysis logon account on all databases related to BAM.</span></span>  
  
### <a name="bam-portal-compatibility-with-internet-explorer-10"></a><span data-ttu-id="fef0c-126">Internet Explorer 10 與 BAM 入口網站的相容性</span><span class="sxs-lookup"><span data-stu-id="fef0c-126">BAM Portal Compatibility with Internet Explorer 10</span></span>  
 <span data-ttu-id="fef0c-127">若要使用 Internet Explorer 10 中的 BAM 入口網站，您一律必須使用瀏覽器相容性模式中。</span><span class="sxs-lookup"><span data-stu-id="fef0c-127">To use the BAM Portal with Internet Explorer 10, you must always use the browser in Compatibility mode.</span></span>  
  
### <a name="receiving-notification-e-mails-even-after-the-alert-host-service-is-stopped"></a><span data-ttu-id="fef0c-128">接收通知電子郵件，即使警示的主機服務已停止</span><span class="sxs-lookup"><span data-stu-id="fef0c-128">Receiving notification e-mails even after the Alert Host service is stopped</span></span>  
 <span data-ttu-id="fef0c-129">如果您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，如果您想要使用 BAM 警示，您必須在 SQL Server 中設定 Database Mail 功能。</span><span class="sxs-lookup"><span data-stu-id="fef0c-129">If you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], you must configure the Database Mail feature in SQL Server if you want to use BAM Alerts.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fef0c-130">Database Mail 功能搭配使用警示的主機服務，來傳送通知的警示。</span><span class="sxs-lookup"><span data-stu-id="fef0c-130"> uses an Alert Host service in conjunction with the Database Mail feature to send notification alerts.</span></span> <span data-ttu-id="fef0c-131">警示的主機服務之後處理通知, 傳遞通知的工作負載中 SQL Server Database Mail 元件。</span><span class="sxs-lookup"><span data-stu-id="fef0c-131">The Alert Host service, after processing the notifications, passes on the notification workload to the Database Mail component in SQL Server.</span></span> <span data-ttu-id="fef0c-132">因此，即使您停止警示的主機服務時，可能仍可使用幾個警示的主機服務，但不是由 Database Mail 元件已處理的事件通知。</span><span class="sxs-lookup"><span data-stu-id="fef0c-132">So, even if you stop the Alert Host service, you might still get a few notifications for events that were processed by the Alert Host service but not by the Database Mail component.</span></span>  
  
### <a name="configuring-tracing-for-bam-alerts"></a><span data-ttu-id="fef0c-133">設定 BAM 警示的追蹤</span><span class="sxs-lookup"><span data-stu-id="fef0c-133">Configuring tracing for BAM Alerts</span></span>  
 <span data-ttu-id="fef0c-134">如果您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，而且您想要啟用 BAM 警示的診斷追蹤，您必須藉由建立 BAM 警示主機組態檔執行。</span><span class="sxs-lookup"><span data-stu-id="fef0c-134">If you are using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], and you want to enable diagnostic tracing for BAM Alerts, you must do so by creating a config file for the BAM Alerts host.</span></span> <span data-ttu-id="fef0c-135">您必須為檔案名稱**BAMAlerts.exe.config**並將它複製到相同的位置與 EXE (**BAMAlerts.exe**)，這是在 \Program Files\Microsoft BizTalk Server\Tracking\\。</span><span class="sxs-lookup"><span data-stu-id="fef0c-135">You must name the file as **BAMAlerts.exe.config** and copy it to the same location as the EXE (**BAMAlerts.exe**), which is at \Program Files\Microsoft BizTalk Server\Tracking\\.</span></span>  
  
 <span data-ttu-id="fef0c-136">範例組態檔看起來如下。</span><span class="sxs-lookup"><span data-stu-id="fef0c-136">A sample config file looks like the following.</span></span> <span data-ttu-id="fef0c-137">這個檔案會記錄**資訊**層級的事件檢視器的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fef0c-137">This file logs **Information** level details to the Event Viewer.</span></span>  
  
```  
<configuration>  
  <system.diagnostics>  
    <switches>  
      <add name="LogEventProvider" value="Info"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
##  <span data-ttu-id="fef0c-138"><a name="BKMK_Upgrade"></a>使用 BizTalk Server 與 SQL Server 2012 時問題</span><span class="sxs-lookup"><span data-stu-id="fef0c-138"><a name="BKMK_Upgrade"></a> Issues While Using BizTalk Server with SQL Server 2012</span></span>  
 <span data-ttu-id="fef0c-139">同時使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]您可以設定**遠端登入逾時**SQL Server 中的值為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="fef0c-139">While using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] you can set the **Remote Login Timeout** value in SQL Server to 20 seconds.</span></span> <span data-ttu-id="fef0c-140">如果您不要這樣做，您可能會遇到負荷過重的狀況中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fef0c-140">If you don’t do so, you might encounter errors in stress conditions.</span></span> <span data-ttu-id="fef0c-141">如需有關如何在中設定的遠端登入逾時值指示[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，請參閱[http://msdn.microsoft.com/library/ms175136.aspx](http://msdn.microsoft.com/library/ms175136.aspx)</span><span class="sxs-lookup"><span data-stu-id="fef0c-141">For instructions on how to set the Remote Login Timeout value in [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], see [http://msdn.microsoft.com/library/ms175136.aspx](http://msdn.microsoft.com/library/ms175136.aspx)</span></span>  
  
##  <span data-ttu-id="fef0c-142"><a name="BKMK_Adapters"></a>配接器問題</span><span class="sxs-lookup"><span data-stu-id="fef0c-142"><a name="BKMK_Adapters"></a> Issues with Adapters</span></span>  
 <span data-ttu-id="fef0c-143">此區段會列出的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。</span><span class="sxs-lookup"><span data-stu-id="fef0c-143">This section lists the known issues with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.</span></span>  
  
### <a name="dynamic-port-may-fail-while-using-the-windows-sharepoint-services-wss-adapter"></a><span data-ttu-id="fef0c-144">動態連接埠可能會使用 Windows SharePoint Services (WSS) 配接器時失敗</span><span class="sxs-lookup"><span data-stu-id="fef0c-144">Dynamic port may fail while using the Windows SharePoint Services (WSS) adapter</span></span>  
 <span data-ttu-id="fef0c-145">使用 WSS 配接器的動態連接埠可能會失敗，發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="fef0c-145">A dynamic port using the WSS adapter may fail with the following error:</span></span>  
  
```  
Error details: The Windows SharePoint Services site was not found. The URL "http://server:443/site" points to a SharePoint object for which there is no Windows SharePoint Services site.  
```  
  
 <span data-ttu-id="fef0c-146">**因應措施**:</span><span class="sxs-lookup"><span data-stu-id="fef0c-146">**Workarounds**:</span></span>  
  
-   <span data-ttu-id="fef0c-147">在連接埠組態中，對於此站台 URL，包括連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="fef0c-147">In the port configuration, for the site URL, include the port number as well.</span></span> <span data-ttu-id="fef0c-148">例如， `http://server:80/site`。</span><span class="sxs-lookup"><span data-stu-id="fef0c-148">For example, `http://server:80/site`.</span></span>  
  
-   <span data-ttu-id="fef0c-149">啟用**Windows Identity Foundation 3.5**功能。</span><span class="sxs-lookup"><span data-stu-id="fef0c-149">Enable the **Windows Identity Foundation 3.5** feature.</span></span>  
  
-   <span data-ttu-id="fef0c-150">確認執行 BizTalk 主控件的帳戶具有存取 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="fef0c-150">Confirm the account running the BizTalk host has access to SharePoint.</span></span>  
  
### <a name="adapters-available-with-biztalk-adapter-pack-cannot-be-administered-on-a-computer-that-only-has-biztalk-server-administration-component-installed"></a><span data-ttu-id="fef0c-151">使用 BizTalk Adapter Pack 配接器無法管理只具有 BizTalk Server 管理元件安裝在電腦上</span><span class="sxs-lookup"><span data-stu-id="fef0c-151">Adapters available with BizTalk Adapter Pack cannot be administered on a computer that only has BizTalk Server Administration component installed</span></span>  
 <span data-ttu-id="fef0c-152">如果您有只在電腦上安裝 BizTalk Adapter Pack[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中安裝，安裝 BizTalk Adapter Pack 的一部分的介面卡沒有可用當您建立傳送埠或接收位置。</span><span class="sxs-lookup"><span data-stu-id="fef0c-152">If you have BizTalk Adapter Pack installed on a computer that only has the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console installed, the adapters installed as part of the BizTalk Adapter Pack are not available when you create a send port or receive location.</span></span> <span data-ttu-id="fef0c-153">這是因為這些配接器對在同一部電腦上安裝 BizTalk 執行階段有相依性。</span><span class="sxs-lookup"><span data-stu-id="fef0c-153">This is because these adapters have a dependency on the BizTalk Runtime to be installed on the same computer.</span></span>  
  
 <span data-ttu-id="fef0c-154">因應措施 – 安裝 BizTalk Server 執行階段有配接器組件和 BizTalk Server 管理元件安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="fef0c-154">Workaround – Install the BizTalk Server runtime on the computer that has the Adapter Pack and the BizTalk Server Administration component installed.</span></span> <span data-ttu-id="fef0c-155">您不需要該電腦上設定 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="fef0c-155">You need not configure BizTalk Server on that computer.</span></span>  
  
## <a name="other-issues"></a><span data-ttu-id="fef0c-156">其他問題</span><span class="sxs-lookup"><span data-stu-id="fef0c-156">Other Issues</span></span>  
  
### <a name="setupbat-for-biztalk-server-samples-runs-with-a-32-bit-command-prompt"></a><span data-ttu-id="fef0c-157">Setup.bat，以便讓 BizTalk Server 範例與 32 位元命令提示字元執行</span><span class="sxs-lookup"><span data-stu-id="fef0c-157">Setup.bat for BizTalk Server Samples Runs with a 32-bit Command Prompt</span></span>  
 <span data-ttu-id="fef0c-158">如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]隨附於此版本的範例，您必須只從 32 位元命令提示字元執行隨附的 setup.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="fef0c-158">For the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] samples shipped with this release, you must run the accompanying setup.bat files only from a 32-bit command prompt.</span></span> <span data-ttu-id="fef0c-159">64 位元命令提示字元執行批次檔，可能會導致失敗。</span><span class="sxs-lookup"><span data-stu-id="fef0c-159">Running the batch files from a 64-bit command prompt might result in a failure.</span></span>  
  
### <a name="run-setup-as-administrator"></a><span data-ttu-id="fef0c-160">以系統管理員身分執行安裝程式</span><span class="sxs-lookup"><span data-stu-id="fef0c-160">Run setup as Administrator</span></span>  
 <span data-ttu-id="fef0c-161">安裝時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，使用**系統管理員身分執行**選項。</span><span class="sxs-lookup"><span data-stu-id="fef0c-161">When installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], use the **Run as Administrator** option.</span></span> <span data-ttu-id="fef0c-162">否則，可能會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="fef0c-162">Otherwise, the following errors may occur:</span></span>  
  
 <span data-ttu-id="fef0c-163">內部錯誤 2761年。</span><span class="sxs-lookup"><span data-stu-id="fef0c-163">Internal Error 2761.</span></span> <span data-ttu-id="fef0c-164">傳回碼： 1</span><span class="sxs-lookup"><span data-stu-id="fef0c-164">Return Code: 1</span></span>  
  
 <span data-ttu-id="fef0c-165">MSI 安裝傳回 1603-安裝時發生嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="fef0c-165">MSI installation returned 1603 - Fatal error during installation.</span></span>  
  
### <a name="using-certificates-with-1024-key-for-encoding-and-signing-results-in-failure-of-mime-smime-decoding"></a><span data-ttu-id="fef0c-166">具有 1024年索引鍵使用憑證來進行編碼，並簽署產生的 MIME SMIME 解碼失敗</span><span class="sxs-lookup"><span data-stu-id="fef0c-166">Using certificates with 1024 key for encoding and signing results in failure of MIME-SMIME decoding</span></span>  
 <span data-ttu-id="fef0c-167">在 Windows 8 上加密並以 1024年的索引鍵使用憑證來簽署訊息時 MIME SMIME 解碼失敗中驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="fef0c-167">On Windows 8, when a message is encrypted and signed using certificates with 1024 key, MIME-SMIME decoding fails in authenticating the message.</span></span> <span data-ttu-id="fef0c-168">若要避免這個問題，您可以使用憑證具有 2048年索引鍵。</span><span class="sxs-lookup"><span data-stu-id="fef0c-168">To avoid this issue, you can use certificates with 2048 key.</span></span>  
  
### <a name="uddi-resolver-with-esb-toolkit-gives-a-serialization-error"></a><span data-ttu-id="fef0c-169">UDDI 解析程式使用 ESB Toolkit 提供序列化錯誤</span><span class="sxs-lookup"><span data-stu-id="fef0c-169">UDDI resolver with ESB Toolkit gives a Serialization error</span></span>  
 <span data-ttu-id="fef0c-170">使用 UDDI 時[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]時查閱繫結的詳細資訊，您可能會遇到 XML 序列化錯誤。</span><span class="sxs-lookup"><span data-stu-id="fef0c-170">While using UDDI with the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] you might encounter an XML serialization error when looking up the binding details.</span></span> <span data-ttu-id="fef0c-171">如果未指定繫結索引鍵，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="fef0c-171">This error occurs if the binding key is not specified.</span></span>  
  
### <a name="the-itinerary-designer-for-esb-toolkit"></a><span data-ttu-id="fef0c-172">ESB Toolkit 路線設計工具</span><span class="sxs-lookup"><span data-stu-id="fef0c-172">The itinerary designer for ESB Toolkit</span></span>  
 <span data-ttu-id="fef0c-173">路線設計工具的[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]屬於現在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="fef0c-173">The itinerary designer for the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] is now part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation media.</span></span> <span data-ttu-id="fef0c-174">您可以找到媒體的根資料夾在路線設計工具中，名稱`Microsoft.Practices.Services.Itinerary.DslPackage.vsix`。</span><span class="sxs-lookup"><span data-stu-id="fef0c-174">You can find the itinerary designer at the root folder of the media and has the name `Microsoft.Practices.Services.Itinerary.DslPackage.vsix`.</span></span> <span data-ttu-id="fef0c-175">較舊版本，此檔案時可用的安裝位置[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]，這通常是 \Program Files\Microsoft [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fef0c-175">Earlier, this file was available at the location where you install the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)], which typically is \Program Files\Microsoft [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].</span></span>  
  
### <a name="edi"></a><span data-ttu-id="fef0c-176">EDI</span><span class="sxs-lookup"><span data-stu-id="fef0c-176">EDI</span></span>  
 <span data-ttu-id="fef0c-177">EDI 批次處理正在使用中。</span><span class="sxs-lookup"><span data-stu-id="fef0c-177">EDI Batching is being used.</span></span> <span data-ttu-id="fef0c-178">使用阿拉伯曆或阿拉伯文本機設定時，協調流程會暫停，發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="fef0c-178">When using an Arabic calendar or Arabic local settings, the orchestration suspends with the following error:</span></span>  
  
 <span data-ttu-id="fef0c-179">**錯誤碼： 0xC0C01B52 （協調流程引擎錯誤） 的錯誤描述： 凍結期間暫停由於持續性失敗。**</span><span class="sxs-lookup"><span data-stu-id="fef0c-179">**Error Code: 0xC0C01B52 (Orchestration Engine Error)Error Description: Suspend due to persistence failure during dehydration.**</span></span> <span data-ttu-id="fef0c-180">阿拉伯文西曆支援日期*04/30/1900 00.00.00*至*05/13/2029年 23:59:59*。</span><span class="sxs-lookup"><span data-stu-id="fef0c-180">Arabic Gregorian supports dates from *04/30/1900 00.00.00* to *05/13/2029 23:59:59*.</span></span>  
  
 <span data-ttu-id="fef0c-181">若要解決這個問題，請輸入有效阿拉伯文結束日期。</span><span class="sxs-lookup"><span data-stu-id="fef0c-181">To resolve this behavior, enter a valid Arabic end date.</span></span>  
  
### <a name="enterprise-single-sign-on"></a><span data-ttu-id="fef0c-182">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fef0c-182">Enterprise Single Sign-On</span></span>  
 <span data-ttu-id="fef0c-183">當您安裝企業單一登入 (ESSO)，或當您重新啟動 ESSO 服務時，您可能會看到下列錯誤記錄到事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="fef0c-183">When you install Enterprise Single Sign-On (ESSO) or when you restart the ESSO service you might see the following error logged in the Event Viewer.</span></span>  
  
 <span data-ttu-id="fef0c-184">**無法載入 \Program Files\Common Files\Enterprise 單一登 On\SSOPSServer.dll 錯誤碼： 0x8007007E，找不到指定的模組。**</span><span class="sxs-lookup"><span data-stu-id="fef0c-184">**Failed to load \Program Files\Common Files\Enterprise Single Sign-On\SSOPSServer.dll Error code: 0x8007007E, The specified module could not be found.**</span></span> <span data-ttu-id="fef0c-185">您可以放心忽略這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="fef0c-185">You can safely ignore this error.</span></span>