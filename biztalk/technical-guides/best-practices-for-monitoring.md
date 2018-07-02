---
title: 監視的最佳作法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5b180e2-bdd3-4081-9531-d96be7dabe1a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bfb2b5575fe46c1104ddc6b852695fb777275ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981655"
---
# <a name="best-practices-for-monitoring"></a><span data-ttu-id="22864-102">監視的最佳做法</span><span class="sxs-lookup"><span data-stu-id="22864-102">Best Practices for Monitoring</span></span>
<span data-ttu-id="22864-103">本主題提供監視您的 Microsoft BizTalk Server 環境和應用程式的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="22864-103">This topic provides best practices for monitoring your Microsoft BizTalk Server environment and applications.</span></span>  
  
 <span data-ttu-id="22864-104">**建立，然後再實作您的 BizTalk 應用程式和基礎結構的監視計劃**</span><span class="sxs-lookup"><span data-stu-id="22864-104">**Create and then implement a monitoring plan for your BizTalk applications and infrastructure**</span></span>  
  
- <span data-ttu-id="22864-105">閱讀本指南，以確保更完整的監視解決方案中監視的主題。</span><span class="sxs-lookup"><span data-stu-id="22864-105">Read the monitoring topics in this guide to ensure a more complete monitoring solution.</span></span> <span data-ttu-id="22864-106">要考慮的因素包括：</span><span class="sxs-lookup"><span data-stu-id="22864-106">Factors to consider include the following:</span></span>  
  
  -   <span data-ttu-id="22864-107">將由誰執行每日、 每週、 每月，以及所需的監視工作？</span><span class="sxs-lookup"><span data-stu-id="22864-107">Who will perform the daily, weekly, monthly, and as needed monitoring tasks?</span></span>  
  
  -   <span data-ttu-id="22864-108">有人會通知的事件、 擱置的訊息或 其他系統或應用程式的失敗？</span><span class="sxs-lookup"><span data-stu-id="22864-108">Is someone notified of events, suspended messages, or other system or application failures?</span></span>  
  
  -   <span data-ttu-id="22864-109">經過篩選，或指定較低的優先順序，則是 「 預期 」 的例外狀況？</span><span class="sxs-lookup"><span data-stu-id="22864-109">Are "expected" exceptions filtered or given a lower priority?</span></span>  
  
  -   <span data-ttu-id="22864-110">是所有的主控件執行個體的監視，以確保它們會繼續執行？</span><span class="sxs-lookup"><span data-stu-id="22864-110">Are all host instances monitored to ensure they continue running?</span></span>  
  
  -   <span data-ttu-id="22864-111">所有的自訂服務、 自訂事件記錄檔和監視的自訂資料庫？</span><span class="sxs-lookup"><span data-stu-id="22864-111">Are all custom services, custom event logs, and custom databases monitored?</span></span>  
  
  -   <span data-ttu-id="22864-112">是 SQL Server 電腦和 BizTalk Server SQL 代理程式監視的作業？</span><span class="sxs-lookup"><span data-stu-id="22864-112">Are the SQL Server computers and the BizTalk Server SQL agent jobs monitored?</span></span>  
  
  <span data-ttu-id="22864-113">**可能的話，請安裝監視的應用程式，例如[!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)]才能自動監視您的 BizTalk Server 應用程式和基礎結構**</span><span class="sxs-lookup"><span data-stu-id="22864-113">**If possible, install a monitoring application such as [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] in order to automate the monitoring of your BizTalk Server applications and infrastructure**</span></span>  
  
- <span data-ttu-id="22864-114">使用 Microsoft System Center Operations Manager 是慣用的方法，如自動監視，因為 BizTalk Server 管理組件會提供 BizTalk Server 中的數百個內建規則。</span><span class="sxs-lookup"><span data-stu-id="22864-114">Using Microsoft System Center Operations Manager is the preferred approach for automated monitoring because the BizTalk Server management packs provide hundreds of built-in rules for BizTalk Server.</span></span>  
  
   <span data-ttu-id="22864-115">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="22864-115">For more information, see the following resources:</span></span>  
  
  -   <span data-ttu-id="22864-116">[適用於 System Center Operations Manager 2007 的 Microsoft BizTalk Server 管理封包](http://go.microsoft.com/fwlink/?LinkID=190339)(http://go.microsoft.com/fwlink/?LinkID=190339)。</span><span class="sxs-lookup"><span data-stu-id="22864-116">[Microsoft BizTalk Server Management Pack for System Center Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=190339) (http://go.microsoft.com/fwlink/?LinkID=190339).</span></span>  
  
  -   <span data-ttu-id="22864-117">[如何匯入 Operations Manager 2007 中的管理組件](http://go.microsoft.com/fwlink/?LinkID=98348)(http://go.microsoft.com/fwlink/?LinkID=98348)</span><span class="sxs-lookup"><span data-stu-id="22864-117">[How to Import a Management Pack in Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=98348) (http://go.microsoft.com/fwlink/?LinkID=98348)</span></span>  
  
  -   [<span data-ttu-id="22864-118">如何標示 BizTalk Server 資料庫以進行自訂監視</span><span class="sxs-lookup"><span data-stu-id="22864-118">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
  <span data-ttu-id="22864-119">**執行 BizTalk Server Best Practices Analyzer**</span><span class="sxs-lookup"><span data-stu-id="22864-119">**Run the BizTalk Server Best Practices Analyzer**</span></span>  
  
- <span data-ttu-id="22864-120">BizTalk Server Best Practices Analyzer 會檢查 BizTalk Server 部署，並產生一份最佳實務標準相關的問題。</span><span class="sxs-lookup"><span data-stu-id="22864-120">The BizTalk Server Best Practices Analyzer examines a BizTalk Server deployment and generates a list of issues pertaining to best practices standards.</span></span> <span data-ttu-id="22864-121">工具會執行組態層級驗證，以從不同的資訊來源，例如 Windows Management Instrumentation (WMI) 類別、 SQL Server 資料庫和登錄項目收集資料。</span><span class="sxs-lookup"><span data-stu-id="22864-121">The tool performs configuration-level verification by gathering data from different information sources, such as Windows Management Instrumentation (WMI) classes, SQL Server databases, and registry entries.</span></span> <span data-ttu-id="22864-122">資料然後用以評估部署組態。</span><span class="sxs-lookup"><span data-stu-id="22864-122">The data is then used to evaluate the deployment configuration.</span></span> <span data-ttu-id="22864-123">此工具會讀取和只會報告和不會修改任何系統的設定，並不是自我調整的工具。</span><span class="sxs-lookup"><span data-stu-id="22864-123">The tool reads and reports only and does not modify any system settings, and is not a self-tuning tool.</span></span>  
  
   <span data-ttu-id="22864-124">您可以下載 BizTalk Server Best Practices Analyzer 在[ http://go.microsoft.com/fwlink/?LinkId=83317 ](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317)。</span><span class="sxs-lookup"><span data-stu-id="22864-124">You can download the BizTalk Server Best Practices Analyzer at [http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317).</span></span>  
  
  <span data-ttu-id="22864-125">**執行記錄檔的效能分析工具 (PAL)**</span><span class="sxs-lookup"><span data-stu-id="22864-125">**Run the Performance Analysis of Logs tool (PAL)**</span></span>  
  
- <span data-ttu-id="22864-126">PAL 是可在免費下載[ https://github.com/clinthuffman/PAL ](https://github.com/clinthuffman/PAL)。</span><span class="sxs-lookup"><span data-stu-id="22864-126">PAL is available as a free download at [https://github.com/clinthuffman/PAL](https://github.com/clinthuffman/PAL).</span></span> <span data-ttu-id="22864-127">重要的安裝資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="22864-127">For important installation information, see [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).</span></span>  
  
  <span data-ttu-id="22864-128">**執行記錄檔剖析器**</span><span class="sxs-lookup"><span data-stu-id="22864-128">**Run Log Parser**</span></span>  
  
- <span data-ttu-id="22864-129">記錄檔剖析器是功能強大、 用途廣泛的工具，提供通用查詢存取以文字為基礎的資料，例如記錄檔、 XML 檔案、 CSV 檔案，以及索引鍵的資料來源上 Windows® 作業系統，例如事件記錄檔、 登錄、 檔案系統和 ActiveDirectory®。</span><span class="sxs-lookup"><span data-stu-id="22864-129">Log Parser is a powerful, versatile tool that provides universal query access to text-based data such as log files, XML files and CSV files, as well as key data sources on the Windows® operating system such as the Event Log, the Registry, the file system, and Active Directory®.</span></span> <span data-ttu-id="22864-130">若要使用此工具來查詢大量的記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="22864-130">You may want to use this tool to query a significant amount of logging information.</span></span> <span data-ttu-id="22864-131">您可以下載 Log Parser 工具 [http://go.microsoft.com/fwlink/?LinkID=85574](http://go.microsoft.com/fwlink/?LinkID=85574)</span><span class="sxs-lookup"><span data-stu-id="22864-131">You can download the Log Parser tool at [http://go.microsoft.com/fwlink/?LinkID=85574](http://go.microsoft.com/fwlink/?LinkID=85574)</span></span>  
  
  <span data-ttu-id="22864-132">**執行 BizTalk MsgBoxViewer 工具**</span><span class="sxs-lookup"><span data-stu-id="22864-132">**Run the BizTalk MsgBoxViewer Tool**</span></span>  
  
  <span data-ttu-id="22864-133">執行[BizTalk MsgBoxViewer 工具](http://go.microsoft.com/fwlink/?LinkId=151930)苀[ http://go.microsoft.com/fwlink/?LinkId=151930 ](http://go.microsoft.com/fwlink/?LinkId=151930)。</span><span class="sxs-lookup"><span data-stu-id="22864-133">Run the [BizTalk MsgBoxViewer tool](http://go.microsoft.com/fwlink/?LinkId=151930) available from [http://go.microsoft.com/fwlink/?LinkId=151930](http://go.microsoft.com/fwlink/?LinkId=151930).</span></span> <span data-ttu-id="22864-134">這項工具會分析 BizTalk MessageBox 和其他資料庫，並產生包含警告的 HTML 報告與資料庫相關的任何，和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="22864-134">This tool analyzes the BizTalk MessageBox and other databases and generates an HTML report containing warnings, if any, and other information related to the databases.</span></span> <span data-ttu-id="22864-135">您也可以儲存供稍後使用的報表。</span><span class="sxs-lookup"><span data-stu-id="22864-135">You can also save the reports for later use.</span></span> <span data-ttu-id="22864-136">與 BizTalk 應用程式的問題進行疑難排解時，這些報表可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="22864-136">These reports might be useful when troubleshooting issues with the BizTalk application.</span></span>  
  
  <span data-ttu-id="22864-137">如果 BizTalk MsgBoxViewer 工具會識別任何問題，執行[結束字元 工具](http://go.microsoft.com/fwlink/?LinkId=151931)網址[ http://go.microsoft.com/fwlink/?LinkId=151931 ](http://go.microsoft.com/fwlink/?LinkId=151931)。</span><span class="sxs-lookup"><span data-stu-id="22864-137">If the BizTalk MsgBoxViewer tool identifies any issues, run the [Terminator tool](http://go.microsoft.com/fwlink/?LinkId=151931) available at [http://go.microsoft.com/fwlink/?LinkId=151931](http://go.microsoft.com/fwlink/?LinkId=151931).</span></span> <span data-ttu-id="22864-138">這項工具可讓使用者輕鬆地解決 BizTalk MsgBoxViewer 工具所識別的任何問題。</span><span class="sxs-lookup"><span data-stu-id="22864-138">This tool enables users to easily resolve any issues identified by the BizTalk MsgBoxViewer tool.</span></span> <span data-ttu-id="22864-139">如需結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[若要解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。</span><span class="sxs-lookup"><span data-stu-id="22864-139">For more information about how the Terminator tool integrates with the BizTalk MsgBoxViewer tool, see [Using BizTalk Terminator to resolve issues identified by BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=151932) (http://go.microsoft.com/fwlink/?LinkId=151932).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22864-140">Microsoft 不支援使用這些工具，Microsoft 不保證這些程式的適用性。</span><span class="sxs-lookup"><span data-stu-id="22864-140">Use of these tools is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of these programs.</span></span> <span data-ttu-id="22864-141">請自行承擔使用這些程式的一切風險。</span><span class="sxs-lookup"><span data-stu-id="22864-141">Use of these programs is entirely at your own risk.</span></span>  
  
 <span data-ttu-id="22864-142">**請監視優先順序**</span><span class="sxs-lookup"><span data-stu-id="22864-142">**Make monitoring a priority**</span></span>  
  
-   <span data-ttu-id="22864-143">不斷監控 BizTalk Server 應用程式和基礎結構的務必維護狀況良好的環境。</span><span class="sxs-lookup"><span data-stu-id="22864-143">Consistent monitoring of BizTalk Server applications and infrastructure is essential to maintaining a healthy environment.</span></span>  
  
-   <span data-ttu-id="22864-144">定期評估，並調整您的監視工具，經過一段時間，以及您的 BizTalk Server 應用程式和基礎結構變更。</span><span class="sxs-lookup"><span data-stu-id="22864-144">Regularly evaluate and adjust your monitoring tools over time and as your BizTalk Server applications and infrastructure change.</span></span>