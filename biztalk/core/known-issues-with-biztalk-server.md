---
title: BizTalk Server 的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1aa5fb60-e8db-4cd2-88be-3c71b7b1d44d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ab3522254ea7cd965ed1b9172de2c382d214fb6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014455"
---
# <a name="known-issues-with-biztalk-server"></a><span data-ttu-id="3de12-102">使用 BizTalk Server 的已知的問題</span><span class="sxs-lookup"><span data-stu-id="3de12-102">Known Issues with BizTalk Server</span></span>
<span data-ttu-id="3de12-103">本主題列出一些 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的已知問題。</span><span class="sxs-lookup"><span data-stu-id="3de12-103">This topic lists some known issues with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="dtc-firewall-rules"></a><span data-ttu-id="3de12-104">DTC 防火牆規則</span><span class="sxs-lookup"><span data-stu-id="3de12-104">DTC Firewall Rules</span></span>  
 <span data-ttu-id="3de12-105">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同的電腦時，分散式交易協調器 (MS DTC) 會處理電腦間的交易。</span><span class="sxs-lookup"><span data-stu-id="3de12-105">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers.</span></span> <span data-ttu-id="3de12-106">如此一來，在上啟用 DTC 連接埠，在您的防火牆規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="3de12-106">As a result, enable the DTC ports within your firewall rules on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers.</span></span>  
  
 <span data-ttu-id="3de12-107">設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，DTC 連接埠不在防火牆中啟用時，可能會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="3de12-107">When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the following errors can occur when the DTC ports are not enabled in the firewall:</span></span>  
  
 <span data-ttu-id="3de12-108">**在資料庫建立; 期間，發生 WMI 錯誤嘗試復原和刪除建立不完整的資料庫 'SQLServerName\BizTalkMsgBoxDb'**</span><span class="sxs-lookup"><span data-stu-id="3de12-108">**WMI Error occurred during database creation; attempt to rollback and delete the partially created database'SQLServerName\BizTalkMsgBoxDb'**</span></span>  
  
 <span data-ttu-id="3de12-109">**產生 WMI 錯誤描述： 類型 'System.EnterpriseServices.TransactionProxyException' 擲回的例外狀況。**</span><span class="sxs-lookup"><span data-stu-id="3de12-109">**WMI error description is generated: Exception of type 'System.EnterpriseServices.TransactionProxyException' was thrown.**</span></span>  
  
 <span data-ttu-id="3de12-110">下列連結提供詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="3de12-110">The following links provide more information:</span></span>  
  
 [<span data-ttu-id="3de12-111">管理伺服器的連接埠</span><span class="sxs-lookup"><span data-stu-id="3de12-111">Ports for the Administration Server</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=275568)  
  
 [<span data-ttu-id="3de12-112">BizTalk Server 2013 和 2013 R2 的後續安裝步驟</span><span class="sxs-lookup"><span data-stu-id="3de12-112">Post-installation Steps for BizTalk Server 2013 and 2013 R2</span></span>](../install-and-config-guides/post-installation-steps-for-biztalk-server-2013-and-2013-r2.md)  
  
##  <a name="BKMK_BAM"></a> <span data-ttu-id="3de12-113">商務活動監控</span><span class="sxs-lookup"><span data-stu-id="3de12-113">Business Activity Monitoring</span></span>  
 <span data-ttu-id="3de12-114">本節列出商務活動監控 (BAM) 模組的已知的問題。</span><span class="sxs-lookup"><span data-stu-id="3de12-114">This section lists the known issues with the Business Activity Monitoring (BAM) module.</span></span>  
  
### <a name="bam-definition-deployment-fails-due-to-a-sql-login-error"></a><span data-ttu-id="3de12-115">BAM 定義部署失敗，因為 SQL 登入錯誤</span><span class="sxs-lookup"><span data-stu-id="3de12-115">BAM definition deployment fails due to a SQL login error</span></span>  
 <span data-ttu-id="3de12-116">在部署 BAM 定義，此作業可能會因為登入錯誤，錯誤碼為 42000。</span><span class="sxs-lookup"><span data-stu-id="3de12-116">While deploying BAM definition, the operation might fail due to a login error with error code 42000.</span></span>  
  
```  
...  
Deploying Activity... Done.   
Deploying View... ERROR: The BAM deployment failed.   
Server: The current operation was cancelled because another operation in the transaction failed.   
OLE DB error: OLE DB or ODBC error: Login failed for user <username>.; 42000.   
…  
```  
  
 <span data-ttu-id="3de12-117">若要修正此問題，請確定 SQL Analysis Service 登入帳戶對與 BAM 相關的所有資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="3de12-117">To fix this issue, make sure the SQL Analysis Service logon account has permissions on all databases related to BAM.</span></span>  
  
### <a name="bam-configuration-might-result-in-warnings-related-to-the-bam-analysis-logon-account"></a><span data-ttu-id="3de12-118">BAM 組態可能會導致 BAM 分析的登入帳戶相關的警告</span><span class="sxs-lookup"><span data-stu-id="3de12-118">BAM configuration might result in warnings related to the BAM Analysis logon account</span></span>  
 <span data-ttu-id="3de12-119">BAM 組態會加入至 BAM，若要能夠存取相關的所有資料庫中的 BAM 分析登入帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="3de12-119">BAM configuration adds the permissions for BAM Analysis logon account in all the databases related to BAM to be able to access them.</span></span> <span data-ttu-id="3de12-120">不過，組態可能會無法執行這項操作，並提供警告，若不符合任何下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="3de12-120">However, the configuration might fail to do so and give a warning if any of the following prerequisites is not met:</span></span>  
  
- <span data-ttu-id="3de12-121">執行 BAM 組態的使用者應該安裝分析服務的電腦上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="3de12-121">The user under which the BAM configuration is run should be an administrator on the computer where Analysis Service is installed.</span></span>  
  
- <span data-ttu-id="3de12-122">在該電腦上必須允許通過防火牆的遠端管理。</span><span class="sxs-lookup"><span data-stu-id="3de12-122">Remote administration through firewall must be allowed on that computer.</span></span>  
  
- <span data-ttu-id="3de12-123">BAM 分析登入帳戶是否與 BAM 相關的資料庫安裝所在的 SQL Server 的系統管理員，您也可能會收到警告。</span><span class="sxs-lookup"><span data-stu-id="3de12-123">You might also get a warning if the BAM Analysis logon account is an administrator for the SQL Server where the BAM-related databases are installed.</span></span> <span data-ttu-id="3de12-124">您可以略過警告，並往前移動。</span><span class="sxs-lookup"><span data-stu-id="3de12-124">You can ignore the warning and move ahead.</span></span>  
  
  <span data-ttu-id="3de12-125">**因應措施**– 您必須與 BAM 相關的所有資料庫上手動新增 BAM 分析登入帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="3de12-125">**Workaround** – You must manually add the permission for the BAM Analysis logon account on all databases related to BAM.</span></span>  
  
### <a name="bam-portal-compatibility-with-internet-explorer-10"></a><span data-ttu-id="3de12-126">BAM 入口網站的相容性標記與 Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="3de12-126">BAM Portal Compatibility with Internet Explorer 10</span></span>  
 <span data-ttu-id="3de12-127">若要使用 Internet Explorer 10 中的 BAM 入口網站，您一律必須使用瀏覽器相容性模式中。</span><span class="sxs-lookup"><span data-stu-id="3de12-127">To use the BAM Portal with Internet Explorer 10, you must always use the browser in Compatibility mode.</span></span>  
  
### <a name="receiving-notification-e-mails-even-after-the-alert-host-service-is-stopped"></a><span data-ttu-id="3de12-128">接收通知電子郵件，即使警示的主機服務已停止</span><span class="sxs-lookup"><span data-stu-id="3de12-128">Receiving notification e-mails even after the Alert Host service is stopped</span></span>  
 <span data-ttu-id="3de12-129">如果您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，如果您想要使用 BAM 警示，您必須在 SQL Server 中設定 Database Mail 功能。</span><span class="sxs-lookup"><span data-stu-id="3de12-129">If you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], you must configure the Database Mail feature in SQL Server if you want to use BAM Alerts.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3de12-130"> 使用與 Database Mail 功能搭配使用的警示的主機服務，來傳送通知的警示。</span><span class="sxs-lookup"><span data-stu-id="3de12-130"> uses an Alert Host service in conjunction with the Database Mail feature to send notification alerts.</span></span> <span data-ttu-id="3de12-131">警示的主機服務，在處理通知之後，傳遞通知的工作負載在 SQL Server Database Mail 元件。</span><span class="sxs-lookup"><span data-stu-id="3de12-131">The Alert Host service, after processing the notifications, passes on the notification workload to the Database Mail component in SQL Server.</span></span> <span data-ttu-id="3de12-132">因此，即使您停止警示的主機服務時，您仍可能會收到幾個警示的主機服務，但不是由 Database Mail 元件已處理的事件通知。</span><span class="sxs-lookup"><span data-stu-id="3de12-132">So, even if you stop the Alert Host service, you might still get a few notifications for events that were processed by the Alert Host service but not by the Database Mail component.</span></span>  
  
### <a name="configuring-tracing-for-bam-alerts"></a><span data-ttu-id="3de12-133">設定 BAM 警示的追蹤</span><span class="sxs-lookup"><span data-stu-id="3de12-133">Configuring tracing for BAM Alerts</span></span>  
 <span data-ttu-id="3de12-134">如果您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，和您想要啟用 BAM 警示的診斷追蹤，您必須藉由建立 BAM 警示主機的組態檔。</span><span class="sxs-lookup"><span data-stu-id="3de12-134">If you are using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], and you want to enable diagnostic tracing for BAM Alerts, you must do so by creating a config file for the BAM Alerts host.</span></span> <span data-ttu-id="3de12-135">您必須為檔案名稱**BAMAlerts.exe.config**並將它複製到相同的位置與 EXE (**BAMAlerts.exe**)，其位於 \Program Files\Microsoft BizTalk Server\Tracking\\。</span><span class="sxs-lookup"><span data-stu-id="3de12-135">You must name the file as **BAMAlerts.exe.config** and copy it to the same location as the EXE (**BAMAlerts.exe**), which is at \Program Files\Microsoft BizTalk Server\Tracking\\.</span></span>  
  
 <span data-ttu-id="3de12-136">範例組態檔看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="3de12-136">A sample config file looks like the following.</span></span> <span data-ttu-id="3de12-137">此檔案會記錄**資訊**層級的事件檢視器的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3de12-137">This file logs **Information** level details to the Event Viewer.</span></span>  
  
```  
<configuration>  
  <system.diagnostics>  
    <switches>  
      <add name="LogEventProvider" value="Info"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
##  <a name="BKMK_Upgrade"></a> <span data-ttu-id="3de12-138">使用 BizTalk Server 與 SQL Server 2012 時的問題</span><span class="sxs-lookup"><span data-stu-id="3de12-138">Issues While Using BizTalk Server with SQL Server 2012</span></span>  
 <span data-ttu-id="3de12-139">在使用時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]具有[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]您可以設定**遠端登入逾時**SQL Server 中的值為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="3de12-139">While using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] you can set the **Remote Login Timeout** value in SQL Server to 20 seconds.</span></span> <span data-ttu-id="3de12-140">如果您不這樣做，您可能會遇到負荷過重的狀況中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3de12-140">If you don’t do so, you might encounter errors in stress conditions.</span></span> <span data-ttu-id="3de12-141">如需有關如何在中設定的遠端登入逾時值[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，請參閱 [http://msdn.microsoft.com/library/ms175136.aspx](http://msdn.microsoft.com/library/ms175136.aspx)</span><span class="sxs-lookup"><span data-stu-id="3de12-141">For instructions on how to set the Remote Login Timeout value in [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], see [http://msdn.microsoft.com/library/ms175136.aspx](http://msdn.microsoft.com/library/ms175136.aspx)</span></span>  
  
##  <a name="BKMK_Adapters"></a> <span data-ttu-id="3de12-142">配接器問題</span><span class="sxs-lookup"><span data-stu-id="3de12-142">Issues with Adapters</span></span>  
 <span data-ttu-id="3de12-143">此區段會列出已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。</span><span class="sxs-lookup"><span data-stu-id="3de12-143">This section lists the known issues with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.</span></span>  
  
### <a name="dynamic-port-may-fail-while-using-the-windows-sharepoint-services-wss-adapter"></a><span data-ttu-id="3de12-144">使用 Windows SharePoint Services (WSS) 配接器時的動態連接埠可能會失敗</span><span class="sxs-lookup"><span data-stu-id="3de12-144">Dynamic port may fail while using the Windows SharePoint Services (WSS) adapter</span></span>  
 <span data-ttu-id="3de12-145">使用 WSS 配接器的動態連接埠可能會失敗，發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="3de12-145">A dynamic port using the WSS adapter may fail with the following error:</span></span>  
  
```  
Error details: The Windows SharePoint Services site was not found. The URL "http://server:443/site" points to a SharePoint object for which there is no Windows SharePoint Services site.  
```  
  
 <span data-ttu-id="3de12-146">**因應措施**:</span><span class="sxs-lookup"><span data-stu-id="3de12-146">**Workarounds**:</span></span>  
  
-   <span data-ttu-id="3de12-147">在 連接埠組態的 網站 url，包括連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="3de12-147">In the port configuration, for the site URL, include the port number as well.</span></span> <span data-ttu-id="3de12-148">例如， `http://server:80/site`。</span><span class="sxs-lookup"><span data-stu-id="3de12-148">For example, `http://server:80/site`.</span></span>  
  
-   <span data-ttu-id="3de12-149">啟用**Windows Identity Foundation 3.5**功能。</span><span class="sxs-lookup"><span data-stu-id="3de12-149">Enable the **Windows Identity Foundation 3.5** feature.</span></span>  
  
-   <span data-ttu-id="3de12-150">確認執行 BizTalk 主控件的帳戶具有 SharePoint 的存取。</span><span class="sxs-lookup"><span data-stu-id="3de12-150">Confirm the account running the BizTalk host has access to SharePoint.</span></span>  
  
### <a name="adapters-available-with-biztalk-adapter-pack-cannot-be-administered-on-a-computer-that-only-has-biztalk-server-administration-component-installed"></a><span data-ttu-id="3de12-151">使用 BizTalk Adapter Pack 配接器無法管理只具有 [已安裝的 BizTalk Server 管理] 元件的電腦上</span><span class="sxs-lookup"><span data-stu-id="3de12-151">Adapters available with BizTalk Adapter Pack cannot be administered on a computer that only has BizTalk Server Administration component installed</span></span>  
 <span data-ttu-id="3de12-152">如果您有只在電腦上安裝 BizTalk Adapter Pack[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝的管理主控台，做為 BizTalk Adapter Pack 的一部分安裝的配接器不提供當您建立傳送埠或接收位置。</span><span class="sxs-lookup"><span data-stu-id="3de12-152">If you have BizTalk Adapter Pack installed on a computer that only has the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console installed, the adapters installed as part of the BizTalk Adapter Pack are not available when you create a send port or receive location.</span></span> <span data-ttu-id="3de12-153">這是因為這些配接器會對同一部電腦上安裝 BizTalk 執行階段中的相依性。</span><span class="sxs-lookup"><span data-stu-id="3de12-153">This is because these adapters have a dependency on the BizTalk Runtime to be installed on the same computer.</span></span>  
  
 <span data-ttu-id="3de12-154">因應措施 – 安裝 BizTalk Server 執行階段有配接器組件和 BizTalk Server 管理元件安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="3de12-154">Workaround – Install the BizTalk Server runtime on the computer that has the Adapter Pack and the BizTalk Server Administration component installed.</span></span> <span data-ttu-id="3de12-155">您不需要在該電腦上設定 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="3de12-155">You need not configure BizTalk Server on that computer.</span></span>  
  
## <a name="other-issues"></a><span data-ttu-id="3de12-156">其他問題</span><span class="sxs-lookup"><span data-stu-id="3de12-156">Other Issues</span></span>  
  
### <a name="setupbat-for-biztalk-server-samples-runs-with-a-32-bit-command-prompt"></a><span data-ttu-id="3de12-157">Setup.bat，以便讓 BizTalk Server 範例與 32 位元命令提示字元執行</span><span class="sxs-lookup"><span data-stu-id="3de12-157">Setup.bat for BizTalk Server Samples Runs with a 32-bit Command Prompt</span></span>  
 <span data-ttu-id="3de12-158">針對[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]隨附此版本的範例，您必須只從 32 位元命令提示字元執行隨附的 setup.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="3de12-158">For the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] samples shipped with this release, you must run the accompanying setup.bat files only from a 32-bit command prompt.</span></span> <span data-ttu-id="3de12-159">從 64 位元命令提示字元中執行批次檔，可能會導致失敗。</span><span class="sxs-lookup"><span data-stu-id="3de12-159">Running the batch files from a 64-bit command prompt might result in a failure.</span></span>  
  
### <a name="run-setup-as-administrator"></a><span data-ttu-id="3de12-160">以系統管理員身分執行安裝程式</span><span class="sxs-lookup"><span data-stu-id="3de12-160">Run setup as Administrator</span></span>  
 <span data-ttu-id="3de12-161">安裝時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，使用**系統管理員身分執行**選項。</span><span class="sxs-lookup"><span data-stu-id="3de12-161">When installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], use the **Run as Administrator** option.</span></span> <span data-ttu-id="3de12-162">否則，可能會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="3de12-162">Otherwise, the following errors may occur:</span></span>  
  
 <span data-ttu-id="3de12-163">內部錯誤 2761年。</span><span class="sxs-lookup"><span data-stu-id="3de12-163">Internal Error 2761.</span></span> <span data-ttu-id="3de12-164">傳回碼： 1</span><span class="sxs-lookup"><span data-stu-id="3de12-164">Return Code: 1</span></span>  
  
 <span data-ttu-id="3de12-165">MSI 安裝傳回 1603-安裝時發生嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="3de12-165">MSI installation returned 1603 - Fatal error during installation.</span></span>  
  
### <a name="using-certificates-with-1024-key-for-encoding-and-signing-results-in-failure-of-mime-smime-decoding"></a><span data-ttu-id="3de12-166">使用 1024年索引鍵中的憑證，用於編碼和簽署的 MIME SMIME 解碼失敗結果</span><span class="sxs-lookup"><span data-stu-id="3de12-166">Using certificates with 1024 key for encoding and signing results in failure of MIME-SMIME decoding</span></span>  
 <span data-ttu-id="3de12-167">在 Windows 8 中，當訊息使用加密與簽署憑證以 1024年金鑰 MIME SMIME 解碼失敗驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="3de12-167">On Windows 8, when a message is encrypted and signed using certificates with 1024 key, MIME-SMIME decoding fails in authenticating the message.</span></span> <span data-ttu-id="3de12-168">若要避免這個問題，您可以使用以 2048年金鑰的憑證。</span><span class="sxs-lookup"><span data-stu-id="3de12-168">To avoid this issue, you can use certificates with 2048 key.</span></span>  
  
### <a name="uddi-resolver-with-esb-toolkit-gives-a-serialization-error"></a><span data-ttu-id="3de12-169">使用 ESB 工具組的 UDDI 解析程式可讓序列化錯誤</span><span class="sxs-lookup"><span data-stu-id="3de12-169">UDDI resolver with ESB Toolkit gives a Serialization error</span></span>  
 <span data-ttu-id="3de12-170">同時使用 UDDI[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]查閱繫結詳細資料時，可能會遇到的 XML 序列化錯誤。</span><span class="sxs-lookup"><span data-stu-id="3de12-170">While using UDDI with the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] you might encounter an XML serialization error when looking up the binding details.</span></span> <span data-ttu-id="3de12-171">如果未指定繫結索引鍵，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="3de12-171">This error occurs if the binding key is not specified.</span></span>  
  
### <a name="the-itinerary-designer-for-esb-toolkit"></a><span data-ttu-id="3de12-172">ESB 工具組在路線設計工具</span><span class="sxs-lookup"><span data-stu-id="3de12-172">The itinerary designer for ESB Toolkit</span></span>  
 <span data-ttu-id="3de12-173">路線設計工具[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]目前是[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="3de12-173">The itinerary designer for the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] is now part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation media.</span></span> <span data-ttu-id="3de12-174">您可以找到路線設計工具，在媒體的根資料夾，並具有名稱`Microsoft.Practices.Services.Itinerary.DslPackage.vsix`。</span><span class="sxs-lookup"><span data-stu-id="3de12-174">You can find the itinerary designer at the root folder of the media and has the name `Microsoft.Practices.Services.Itinerary.DslPackage.vsix`.</span></span> <span data-ttu-id="3de12-175">更早版本，此檔案時可用的安裝位置[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]，這通常是 \Program Files\Microsoft [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3de12-175">Earlier, this file was available at the location where you install the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)], which typically is \Program Files\Microsoft [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].</span></span>  
  
### <a name="edi"></a><span data-ttu-id="3de12-176">EDI</span><span class="sxs-lookup"><span data-stu-id="3de12-176">EDI</span></span>  
 <span data-ttu-id="3de12-177">正在使用 EDI 批次處理。</span><span class="sxs-lookup"><span data-stu-id="3de12-177">EDI Batching is being used.</span></span> <span data-ttu-id="3de12-178">使用阿拉伯曆或阿拉伯文的本機設定時，協調流程會暫停，發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="3de12-178">When using an Arabic calendar or Arabic local settings, the orchestration suspends with the following error:</span></span>  
  
 <span data-ttu-id="3de12-179">**錯誤碼： 0xC0C01B52 （協調流程引擎錯誤） 的錯誤描述： 凍結期間因為持續性失敗而暫停。**</span><span class="sxs-lookup"><span data-stu-id="3de12-179">**Error Code: 0xC0C01B52 (Orchestration Engine Error)Error Description: Suspend due to persistence failure during dehydration.**</span></span> <span data-ttu-id="3de12-180">阿拉伯文西曆支援從*04/30/1900 00.00.00*要*05/13/2029年 23:59:59*。</span><span class="sxs-lookup"><span data-stu-id="3de12-180">Arabic Gregorian supports dates from *04/30/1900 00.00.00* to *05/13/2029 23:59:59*.</span></span>  
  
 <span data-ttu-id="3de12-181">若要解決此問題，請輸入有效的阿拉伯文結束日期。</span><span class="sxs-lookup"><span data-stu-id="3de12-181">To resolve this behavior, enter a valid Arabic end date.</span></span>  
  
### <a name="enterprise-single-sign-on"></a><span data-ttu-id="3de12-182">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="3de12-182">Enterprise Single Sign-On</span></span>  
 <span data-ttu-id="3de12-183">當您安裝企業單一登入 (ESSO)，或當您重新啟動 ESSO 服務時，您可能會看到下列錯誤記錄到事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="3de12-183">When you install Enterprise Single Sign-On (ESSO) or when you restart the ESSO service you might see the following error logged in the Event Viewer.</span></span>  
  
 <span data-ttu-id="3de12-184">**無法載入 \Program Files\Common Files\Enterprise 單一登 On\SSOPSServer.dll 錯誤程式碼： 0x8007007E，找不到指定的模組。**</span><span class="sxs-lookup"><span data-stu-id="3de12-184">**Failed to load \Program Files\Common Files\Enterprise Single Sign-On\SSOPSServer.dll Error code: 0x8007007E, The specified module could not be found.**</span></span> <span data-ttu-id="3de12-185">您可以放心忽略此錯誤。</span><span class="sxs-lookup"><span data-stu-id="3de12-185">You can safely ignore this error.</span></span>