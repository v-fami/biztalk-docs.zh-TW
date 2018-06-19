---
title: 系統管理維護 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67cdf9d7-5448-40c5-8c5f-eae0e281d22c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed53236352831d3ae920263d57b89ed4789be0ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299734"
---
# <a name="administrative-maintenance"></a><span data-ttu-id="f5b18-102">系統管理的維護</span><span class="sxs-lookup"><span data-stu-id="f5b18-102">Administrative Maintenance</span></span>
<span data-ttu-id="f5b18-103">本節提供有關管理問題的解決方式的資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。</span><span class="sxs-lookup"><span data-stu-id="f5b18-103">This section provides information about how you can resolve administration issues with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span> <span data-ttu-id="f5b18-104">這些問題可能會發現在會執行例行的維護工作檢查[常式維護檢查清單](../technical-guides/routine-maintenance-checklists.md)> 一節。</span><span class="sxs-lookup"><span data-stu-id="f5b18-104">These issues may be discovered by the routine maintenance checks that are performed in the [Routine Maintenance Checklists](../technical-guides/routine-maintenance-checklists.md) section.</span></span>  
  
 <span data-ttu-id="f5b18-105">除了本節中的主題，這份文件中的其他主題會處理管理問題。</span><span class="sxs-lookup"><span data-stu-id="f5b18-105">In addition to the topics in this section, other topics in this document address administration issues.</span></span> <span data-ttu-id="f5b18-106">這些主題會列出相關的下列章節中。</span><span class="sxs-lookup"><span data-stu-id="f5b18-106">These topics are listed in Related Sections below.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5b18-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="f5b18-107">In This Section</span></span>  
  
-   [<span data-ttu-id="f5b18-108">系統管理的維護最佳作法</span><span class="sxs-lookup"><span data-stu-id="f5b18-108">Best Practices for Administrative Maintenance</span></span>](../technical-guides/best-practices-for-administrative-maintenance.md)  
  
-   [<span data-ttu-id="f5b18-109">如何啟動 SQL Server 代理程式</span><span class="sxs-lookup"><span data-stu-id="f5b18-109">How to Start the SQL Server Agent</span></span>](../technical-guides/how-to-start-the-sql-server-agent.md)  
  
-   [<span data-ttu-id="f5b18-110">如何排程備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="f5b18-110">How to Schedule a Backup BizTalk Server Job</span></span>](../technical-guides/how-to-schedule-a-backup-biztalk-server-job.md)  
  
-   [<span data-ttu-id="f5b18-111">如何設定備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="f5b18-111">How to Configure a Backup BizTalk Server Job</span></span>](../technical-guides/how-to-configure-a-backup-biztalk-server-job.md)  
  
## <a name="related-sections"></a><span data-ttu-id="f5b18-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="f5b18-112">Related Sections</span></span>  
  
-   <span data-ttu-id="f5b18-113">如需確保[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]上執行代理程式服務[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，並確定所有的 BizTalk 相關 SQL Server 作業正常運作，請參閱[監視 SQL Server Agent 作業](../technical-guides/monitoring-sql-server-agent-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-113">For information about ensuring that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent service is running on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and ensuring that all BizTalk related SQL Server jobs are working properly, see [Monitoring SQL Server Agent Jobs](../technical-guides/monitoring-sql-server-agent-jobs.md).</span></span>  
  
-   <span data-ttu-id="f5b18-114">BizTalk 應用程式或成品使用 BTSTask 命令列工具移除的相關資訊，請參閱 [RemoveApp 命令]，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkID=154687](http://go.microsoft.com/fwlink/?LinkID=154687)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-114">For information about removing a BizTalk application or artifact using the BTSTask command-line tool, see "RemoveApp Command" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkID=154687](http://go.microsoft.com/fwlink/?LinkID=154687).</span></span>  
  
-   <span data-ttu-id="f5b18-115">從 BizTalk Server 管理主控台或 BTSTask 命令列工具使用的應用程式移除成品的詳細資訊，請參閱 「 如何移除成品從應用程式 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/ 嗎？LinkID = 154688](http://go.microsoft.com/fwlink/?LinkID=154688)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-115">For information about removing an artifact from an application using either the BizTalk Server Administration console or the BTSTask command-line tool, see "How to Remove an Artifact from an Application" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkID=154688](http://go.microsoft.com/fwlink/?LinkID=154688).</span></span>  
  
-   <span data-ttu-id="f5b18-116">驗證 BizTalk 管理主控台中的組態相關資訊，請參閱 「 使用 BizTalk Server 管理主控台 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkID=154689](http://go.microsoft.com/fwlink/?LinkID=154689)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-116">For information about verifying the configuration in the BizTalk Administration Console, see "Using the BizTalk Server Administration Console" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkID=154689](http://go.microsoft.com/fwlink/?LinkID=154689).</span></span>  
  
-   <span data-ttu-id="f5b18-117">驗證 BTSNTSvc.exe.config 檔案相關資訊，請參閱 「 BTSNTSvc.exe.config 檔"[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkID=154690](http://go.microsoft.com/fwlink/?LinkID=154690)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-117">For information about verifying the BTSNTSvc.exe.config file, see "BTSNTSvc.exe.config File" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkID=154690](http://go.microsoft.com/fwlink/?LinkID=154690).</span></span>  
  
-   <span data-ttu-id="f5b18-118">如需驗證 BizTalk 相關的登錄機碼，請參閱 「 Windows 登錄資訊適用於進階使用者 」 中 「 Microsoft 說明及支援 」 網站，網址[http://go.microsoft.com/fwlink/?LinkId=155583](http://go.microsoft.com/fwlink/?LinkId=155583)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-118">For information about verifying the BizTalk related registry keys, see "Windows registry information for advanced users" in the Microsoft Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=155583](http://go.microsoft.com/fwlink/?LinkId=155583).</span></span>  
  
-   <span data-ttu-id="f5b18-119">執行 BizTalk 最佳做法分析程式的相關資訊，請參閱 「 BizTalk Server Best Practices Analyzer 」 位於 Microsoft 下載中心[http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-119">For information about running the BizTalk Best Practices Analyzer, see "BizTalk Server Best Practices Analyzer" in the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317).</span></span>  
  
-   <span data-ttu-id="f5b18-120">維護 BAM 資料庫的相關資訊，請參閱 < 管理 BAM 資料庫 >，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId=155584](http://go.microsoft.com/fwlink/?LinkId=155584)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-120">For information about maintaining BAM databases, see "Managing BAM Databases" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=155584](http://go.microsoft.com/fwlink/?LinkId=155584).</span></span>  
  
-   <span data-ttu-id="f5b18-121">如需確保安裝最新的 service pack 和 hotfix，請參閱 Microsoft Update 網站，在[http://go.microsoft.com/fwlink/?LinkID=47813](http://go.microsoft.com/fwlink/?LinkID=47813)。</span><span class="sxs-lookup"><span data-stu-id="f5b18-121">For information about ensuring that the latest service packs and hotfixes are installed, see the Microsoft Update Web site at [http://go.microsoft.com/fwlink/?LinkID=47813](http://go.microsoft.com/fwlink/?LinkID=47813).</span></span>