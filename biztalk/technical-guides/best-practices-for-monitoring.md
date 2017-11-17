---
title: "監視的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5b180e2-bdd3-4081-9531-d96be7dabe1a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d520026b9037f10f2ed20f52a366b1ff9d3183a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-monitoring"></a><span data-ttu-id="c3dbd-102">監視的最佳作法</span><span class="sxs-lookup"><span data-stu-id="c3dbd-102">Best Practices for Monitoring</span></span>
<span data-ttu-id="c3dbd-103">本主題提供的監視您的 Microsoft 最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境和應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-103">This topic provides best practices for monitoring your Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment and applications.</span></span>  
  
 <span data-ttu-id="c3dbd-104">**建立，然後實作您的 BizTalk 應用程式和基礎結構的監視計劃**</span><span class="sxs-lookup"><span data-stu-id="c3dbd-104">**Create and then implement a monitoring plan for your BizTalk applications and infrastructure**</span></span>  
  
-   <span data-ttu-id="c3dbd-105">閱讀本指南，以確保更完整的監視解決方案的監視。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-105">Read the monitoring topics in this guide to ensure a more complete monitoring solution.</span></span> <span data-ttu-id="c3dbd-106">要考慮的因素包括：</span><span class="sxs-lookup"><span data-stu-id="c3dbd-106">Factors to consider include the following:</span></span>  
  
    -   <span data-ttu-id="c3dbd-107">誰可以執行每日、 每週、 每月，以及所需的監視工作？</span><span class="sxs-lookup"><span data-stu-id="c3dbd-107">Who will perform the daily, weekly, monthly, and as needed monitoring tasks?</span></span>  
  
    -   <span data-ttu-id="c3dbd-108">有人會通知的事件、 擱置的訊息或其他系統或應用程式失敗？</span><span class="sxs-lookup"><span data-stu-id="c3dbd-108">Is someone notified of events, suspended messages, or other system or application failures?</span></span>  
  
    -   <span data-ttu-id="c3dbd-109">為 「 預期 」 例外狀況篩選或指定較低的優先權？</span><span class="sxs-lookup"><span data-stu-id="c3dbd-109">Are "expected" exceptions filtered or given a lower priority?</span></span>  
  
    -   <span data-ttu-id="c3dbd-110">是所有的主控件執行個體的監視，以確保它們會繼續執行？</span><span class="sxs-lookup"><span data-stu-id="c3dbd-110">Are all host instances monitored to ensure they continue running?</span></span>  
  
    -   <span data-ttu-id="c3dbd-111">所有的自訂服務、 自訂的事件記錄檔和監視的自訂資料庫？</span><span class="sxs-lookup"><span data-stu-id="c3dbd-111">Are all custom services, custom event logs, and custom databases monitored?</span></span>  
  
    -   <span data-ttu-id="c3dbd-112">SQL Server 電腦和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]監視 SQL agent 作業嗎？</span><span class="sxs-lookup"><span data-stu-id="c3dbd-112">Are the SQL Server computers and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL agent jobs monitored?</span></span>  
  
 <span data-ttu-id="c3dbd-113">**可能的話，請安裝監視的應用程式，例如[!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)]才能自動監視您的 BizTalk Server 應用程式和基礎結構**</span><span class="sxs-lookup"><span data-stu-id="c3dbd-113">**If possible, install a monitoring application such as [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] in order to automate the monitoring of your BizTalk Server applications and infrastructure**</span></span>  
  
-   <span data-ttu-id="c3dbd-114">使用 Microsoft System Center Operations Manager 是慣用的方法，自動監視，因為 BizTalk Server 管理組件提供數百個內建規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-114">Using Microsoft System Center Operations Manager is the preferred approach for automated monitoring because the BizTalk Server management packs provide hundreds of built-in rules for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
     <span data-ttu-id="c3dbd-115">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="c3dbd-115">For more information, see the following resources:</span></span>  
  
    -   <span data-ttu-id="c3dbd-116">[System Center Operations Manager 2007 的 Microsoft BizTalk Server 管理組件](http://go.microsoft.com/fwlink/?LinkID=190339)(http://go.microsoft.com/fwlink/?LinkID=190339)。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-116">[Microsoft BizTalk Server Management Pack for System Center Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=190339) (http://go.microsoft.com/fwlink/?LinkID=190339).</span></span>  
  
    -   <span data-ttu-id="c3dbd-117">[如何匯入 Operations Manager 2007 中的管理組件](http://go.microsoft.com/fwlink/?LinkID=98348)(http://go.microsoft.com/fwlink/?LinkID=98348)</span><span class="sxs-lookup"><span data-stu-id="c3dbd-117">[How to Import a Management Pack in Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=98348) (http://go.microsoft.com/fwlink/?LinkID=98348)</span></span>  
  
    -   [<span data-ttu-id="c3dbd-118">如何將 BizTalk Server 資料庫標示為的自訂監視</span><span class="sxs-lookup"><span data-stu-id="c3dbd-118">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
 <span data-ttu-id="c3dbd-119">**執行 BizTalk Server Best Practices Analyzer**</span><span class="sxs-lookup"><span data-stu-id="c3dbd-119">**Run the BizTalk Server Best Practices Analyzer**</span></span>  
  
-   <span data-ttu-id="c3dbd-120">BizTalk Server Best Practices Analyzer 會檢查[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署，並且產生與最佳做法標準相關問題的清單。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-120">The BizTalk Server Best Practices Analyzer examines a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment and generates a list of issues pertaining to best practices standards.</span></span> <span data-ttu-id="c3dbd-121">工具會執行組態層級驗證，以從不同的資訊來源，例如 Windows Management Instrumentation (WMI) 類別、 SQL Server 資料庫和登錄項目收集資料。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-121">The tool performs configuration-level verification by gathering data from different information sources, such as Windows Management Instrumentation (WMI) classes, SQL Server databases, and registry entries.</span></span> <span data-ttu-id="c3dbd-122">將資料再用於評估的部署組態。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-122">The data is then used to evaluate the deployment configuration.</span></span> <span data-ttu-id="c3dbd-123">工具讀取然後只會報告不會修改任何系統設定，並不是自我調整工具。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-123">The tool reads and reports only and does not modify any system settings, and is not a self-tuning tool.</span></span>  
  
     <span data-ttu-id="c3dbd-124">您可以下載 BizTalk Server Best Practices Analyzer 在[http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317)。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-124">You can download the BizTalk Server Best Practices Analyzer at [http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317).</span></span>  
  
 <span data-ttu-id="c3dbd-125">**執行記錄檔的效能分析工具 (PAL)**</span><span class="sxs-lookup"><span data-stu-id="c3dbd-125">**Run the Performance Analysis of Logs tool (PAL)**</span></span>  
  
-   <span data-ttu-id="c3dbd-126">PAL 是在免費下載[http://go.microsoft.com/fwlink/LinkID=98098](http://go.microsoft.com/fwlink/?LinkID=98098)。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-126">PAL is available as a free download at [http://go.microsoft.com/fwlink/LinkID=98098](http://go.microsoft.com/fwlink/?LinkID=98098).</span></span> <span data-ttu-id="c3dbd-127">重要的安裝資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-127">For important installation information, see [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).</span></span>  
  
 <span data-ttu-id="c3dbd-128">**執行記錄檔剖析器**</span><span class="sxs-lookup"><span data-stu-id="c3dbd-128">**Run Log Parser**</span></span>  
  
-   <span data-ttu-id="c3dbd-129">記錄檔剖析器是功能強大、 靈活的工具，提供通用的查詢文字為基礎的資料，例如記錄檔、 XML 檔案和 CSV 檔案，以及索引鍵的資料來源來存取 Windows® 作業系統，例如事件記錄檔、 登錄、 檔案系統和作用中Directory®。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-129">Log Parser is a powerful, versatile tool that provides universal query access to text-based data such as log files, XML files and CSV files, as well as key data sources on the Windows® operating system such as the Event Log, the Registry, the file system, and Active Directory®.</span></span> <span data-ttu-id="c3dbd-130">若要使用此工具來查詢大量的記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-130">You may want to use this tool to query a significant amount of logging information.</span></span> <span data-ttu-id="c3dbd-131">您可以下載記錄檔剖析器工具在[http://go.microsoft.com/fwlink/?LinkID=85574](http://go.microsoft.com/fwlink/?LinkID=85574)</span><span class="sxs-lookup"><span data-stu-id="c3dbd-131">You can download the Log Parser tool at [http://go.microsoft.com/fwlink/?LinkID=85574](http://go.microsoft.com/fwlink/?LinkID=85574)</span></span>  
  
 <span data-ttu-id="c3dbd-132">**執行 BizTalk MsgBoxViewer 工具**</span><span class="sxs-lookup"><span data-stu-id="c3dbd-132">**Run the BizTalk MsgBoxViewer Tool**</span></span>  
  
 <span data-ttu-id="c3dbd-133">執行[BizTalk MsgBoxViewer 工具](http://go.microsoft.com/fwlink/?LinkId=151930)可從[http://go.microsoft.com/fwlink/?LinkId=151930](http://go.microsoft.com/fwlink/?LinkId=151930)。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-133">Run the [BizTalk MsgBoxViewer tool](http://go.microsoft.com/fwlink/?LinkId=151930) available from [http://go.microsoft.com/fwlink/?LinkId=151930](http://go.microsoft.com/fwlink/?LinkId=151930).</span></span> <span data-ttu-id="c3dbd-134">此工具會分析 BizTalk MessageBox 資料庫與其他資料庫，並會產生 HTML 報表包含警告，如果與資料庫相關的任何，和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-134">This tool analyzes the BizTalk MessageBox and other databases and generates an HTML report containing warnings, if any, and other information related to the databases.</span></span> <span data-ttu-id="c3dbd-135">您也可以儲存供稍後使用的報表。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-135">You can also save the reports for later use.</span></span> <span data-ttu-id="c3dbd-136">與 BizTalk 應用程式的問題進行疑難排解時，這些報表可能會有用。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-136">These reports might be useful when troubleshooting issues with the BizTalk application.</span></span>  
  
 <span data-ttu-id="c3dbd-137">如果 BizTalk MsgBoxViewer 工具識別任何問題，請執行[結束字元工具](http://go.microsoft.com/fwlink/?LinkId=151931)位於[http://go.microsoft.com/fwlink/?LinkId=151931](http://go.microsoft.com/fwlink/?LinkId=151931)。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-137">If the BizTalk MsgBoxViewer tool identifies any issues, run the [Terminator tool](http://go.microsoft.com/fwlink/?LinkId=151931) available at [http://go.microsoft.com/fwlink/?LinkId=151931](http://go.microsoft.com/fwlink/?LinkId=151931).</span></span> <span data-ttu-id="c3dbd-138">此工具可讓使用者輕鬆地解決 BizTalk MsgBoxViewer 工具所識別的任何問題。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-138">This tool enables users to easily resolve any issues identified by the BizTalk MsgBoxViewer tool.</span></span> <span data-ttu-id="c3dbd-139">如需結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-139">For more information about how the Terminator tool integrates with the BizTalk MsgBoxViewer tool, see [Using BizTalk Terminator to resolve issues identified by BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=151932) (http://go.microsoft.com/fwlink/?LinkId=151932).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3dbd-140">使用這些工具不支援的 Microsoft，Microsoft 並不保證這些程式的適用性。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-140">Use of these tools is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of these programs.</span></span> <span data-ttu-id="c3dbd-141">請自行承擔使用這些程式的一切風險。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-141">Use of these programs is entirely at your own risk.</span></span>  
  
 <span data-ttu-id="c3dbd-142">**請監視優先順序**</span><span class="sxs-lookup"><span data-stu-id="c3dbd-142">**Make monitoring a priority**</span></span>  
  
-   <span data-ttu-id="c3dbd-143">一致監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構是重要的維護狀況良好的環境。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-143">Consistent monitoring of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications and infrastructure is essential to maintaining a healthy environment.</span></span>  
  
-   <span data-ttu-id="c3dbd-144">定期評估，並調整您的監視工具經過一段時間，以及您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構變更。</span><span class="sxs-lookup"><span data-stu-id="c3dbd-144">Regularly evaluate and adjust your monitoring tools over time and as your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications and infrastructure change.</span></span>