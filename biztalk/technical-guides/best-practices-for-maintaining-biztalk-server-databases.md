---
title: 維護 BizTalk Server 資料庫的最佳作法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93333f41-ee83-4b64-b381-66584a7d5551
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b1d8f03201b04a3be1f7908eaf7e763a4ade226
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981247"
---
# <a name="best-practices-for-maintaining-biztalk-server-databases"></a><span data-ttu-id="080ef-102">維護 BizTalk Server 資料庫的最佳做法</span><span class="sxs-lookup"><span data-stu-id="080ef-102">Best Practices for Maintaining BizTalk Server Databases</span></span>
<span data-ttu-id="080ef-103">本主題列出維護的一些最佳做法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="080ef-103">This topic lists some best practices for maintaining [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
- <span data-ttu-id="080ef-104">請確定 SQL Server Agent 正在執行的 SQL Server 上。</span><span class="sxs-lookup"><span data-stu-id="080ef-104">Make sure the SQL Server Agent is running on the SQL Server.</span></span> <span data-ttu-id="080ef-105">SQL Server Agent 停止時，無法執行負責維護資料庫的內建 BizTalk SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="080ef-105">When the SQL Server Agent is stopped, the built-in BizTalk SQL Server Agent jobs that are responsible for database maintenance cannot run.</span></span> <span data-ttu-id="080ef-106">這個行為會導致資料庫成長，這種成長，可能會造成效能問題。</span><span class="sxs-lookup"><span data-stu-id="080ef-106">This behavior causes database growth, and this growth may cause performance issues.</span></span> <span data-ttu-id="080ef-107">如需監視 SQL Server Agent 作業的詳細資訊，請參閱[監視 SQL Server Agent 作業](../technical-guides/monitoring-sql-server-agent-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="080ef-107">For information about monitoring SQL Server Agent Jobs see [Monitoring SQL Server Agent Jobs](../technical-guides/monitoring-sql-server-agent-jobs.md).</span></span>  
  
- <span data-ttu-id="080ef-108">請確定 SQL Server LDF 和 MDF 檔案是位在不同的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="080ef-108">Make sure the SQL Server LDF and MDF files are on separate drives.</span></span> <span data-ttu-id="080ef-109">具有相同的磁碟機上 BizTalkMsgBoxDb 和 BizTalkDTADb 資料庫的 LDF 和 MDF 檔案，可能會導致磁碟爭用情況。</span><span class="sxs-lookup"><span data-stu-id="080ef-109">Having the LDF and MDF files for the BizTalkMsgBoxDb and BizTalkDTADb databases on the same drive may result in disk contention.</span></span>  
  
- <span data-ttu-id="080ef-110">請勿啟用訊息內文追蹤，如果不需要。</span><span class="sxs-lookup"><span data-stu-id="080ef-110">Do not enable message body tracking, if not required.</span></span> <span data-ttu-id="080ef-111">通常，您可能要啟用訊息內文追蹤，而您會開發和疑難排解解決方案。</span><span class="sxs-lookup"><span data-stu-id="080ef-111">Frequently, you may want to enable message body tracking while you develop and troubleshoot a solution.</span></span> <span data-ttu-id="080ef-112">如果是的話，請確定您停用訊息內文追蹤完成時。</span><span class="sxs-lookup"><span data-stu-id="080ef-112">If so, make sure you disable message body tracking when you are done.</span></span> <span data-ttu-id="080ef-113">如果您保留訊息內文追蹤，啟用 BizTalk Server 資料庫成長。</span><span class="sxs-lookup"><span data-stu-id="080ef-113">If you keep message body tracking enabled, the BizTalk Server databases grow.</span></span> <span data-ttu-id="080ef-114">如果您有要求您啟用訊息內文追蹤的商務需求，請確認**TrackedMessages_Copy_BizTalkMsgBoxDb**並**DTA 清除與封存**執行 SQL Server Agent 作業已成功。</span><span class="sxs-lookup"><span data-stu-id="080ef-114">If you have a business need that requires you to enable message body tracking, confirm that the **TrackedMessages_Copy_BizTalkMsgBoxDb** and **DTA Purge and Archive** SQL Server Agent jobs are running successfully.</span></span>  
  
- <span data-ttu-id="080ef-115">一般而言，較小的交易記錄檔會導致更好的效能。</span><span class="sxs-lookup"><span data-stu-id="080ef-115">Typically, smaller transaction logs cause better performance.</span></span> <span data-ttu-id="080ef-116">若要保持較小的交易記錄檔，設定**備份 BizTalk Server**更常執行的 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="080ef-116">To keep the transaction logs smaller, configure the **Backup BizTalk Server** SQL Server Agent job to run more frequently.</span></span> <span data-ttu-id="080ef-117">如需詳細資訊，請參閱 < [BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkId=153594)(http://go.microsoft.com/fwlink/?LinkId=153594)。</span><span class="sxs-lookup"><span data-stu-id="080ef-117">For more information, see the [BizTalk Server Database Optimization white paper](http://go.microsoft.com/fwlink/?LinkId=153594) (http://go.microsoft.com/fwlink/?LinkId=153594).</span></span>  
  
- <span data-ttu-id="080ef-118">使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]要評估現有的 Best Practices Analyzer (BPA)[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。</span><span class="sxs-lookup"><span data-stu-id="080ef-118">Use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Best Practices Analyzer (BPA) to evaluate an existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span> <span data-ttu-id="080ef-119">BPA 會執行許多資料庫相關的檢查。</span><span class="sxs-lookup"><span data-stu-id="080ef-119">The BPA performs numerous database-related checks.</span></span> <span data-ttu-id="080ef-120">您可以下載從 BizTalk Server Best Practices Analyzer 工具[BizTalk Server Best Practices Analyzer 工具](http://go.microsoft.com/fwlink/?LinkId=83317)(<http://go.microsoft.com/fwlink/?LinkId=83317>)。</span><span class="sxs-lookup"><span data-stu-id="080ef-120">You can download the BizTalk Server Best Practices Analyzer tool from [BizTalk Server Best Practices Analyzer tool](http://go.microsoft.com/fwlink/?LinkId=83317) (<http://go.microsoft.com/fwlink/?LinkId=83317>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="080ef-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="080ef-121">See Also</span></span>  
 <span data-ttu-id="080ef-122">[檢查清單： 維護和疑難排解 BizTalk Server 資料庫](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="080ef-122">[Checklist: Maintaining and Troubleshooting BizTalk Server Databases](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md) </span></span>  
 [<span data-ttu-id="080ef-123">日益成長的 BizTalk Server 資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="080ef-123">Large-growing BizTalk Server Database Tables</span></span>](../technical-guides/large-growing-biztalk-server-database-tables.md)