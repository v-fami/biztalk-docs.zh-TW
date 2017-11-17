---
title: "還原 Analysis Services 和支援的資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490ad0fb-7805-4ebc-9bc5-117d52d7c3a8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da16bde7b69071b71b794c4c46407feab3ef4512
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-analysis-services-and-supporting-databases"></a><span data-ttu-id="01ce8-102">還原 Analysis Services 和支援的資料庫</span><span class="sxs-lookup"><span data-stu-id="01ce8-102">Restoring Analysis Services and Supporting Databases</span></span>
<span data-ttu-id="01ce8-103">有兩個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫必須還原在嚴重損壞修復案例：</span><span class="sxs-lookup"><span data-stu-id="01ce8-103">There are two [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases that must be restored in a disaster recovery scenario:</span></span>  
  
-   <span data-ttu-id="01ce8-104">BAM 分析 (BAMAnalysis)</span><span class="sxs-lookup"><span data-stu-id="01ce8-104">BAM Analysis (BAMAnalysis)</span></span>  
  
-   <span data-ttu-id="01ce8-105">追蹤 Analysis Server (BizTalkAnalysisdb)</span><span class="sxs-lookup"><span data-stu-id="01ce8-105">Tracking Analysis Server (BizTalkAnalysisdb)</span></span>  
  
 <span data-ttu-id="01ce8-106">BAM[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫可能會備份為 「 備份 BizTalk Server 」 工作一部分如果 BAM 已啟用但尚未設定。</span><span class="sxs-lookup"><span data-stu-id="01ce8-106">The BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases may be backed up as part of the Backup BizTalk Server job if BAM is enabled but not configured.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01ce8-107">BAM 主要匯入永遠備份資料庫的 「 備份 BizTalk Server 」 工作一部分因為參與 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="01ce8-107">The BAM Primary Import database is always backed up as part of the Backup BizTalk Server job because it participates in DTC transactions.</span></span>  
  
 <span data-ttu-id="01ce8-108">下列 BAM 資料庫將會是 「 備份 BizTalk Server 」 工作的一部分，如果 BAM 已啟用但尚未設定：</span><span class="sxs-lookup"><span data-stu-id="01ce8-108">The following BAM databases will be part of the Backup BizTalk Server job if BAM is enabled but not configured:</span></span>  
  
-   <span data-ttu-id="01ce8-109">BAMStarSchema</span><span class="sxs-lookup"><span data-stu-id="01ce8-109">BAMStarSchema</span></span>  
  
-   <span data-ttu-id="01ce8-110">BAMArchive</span><span class="sxs-lookup"><span data-stu-id="01ce8-110">BAMArchive</span></span>  
  
 <span data-ttu-id="01ce8-111">請依照[如何還原資料庫中 「 備份 BizTalk Server 」 工作](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)来還原這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="01ce8-111">Follow the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md) to restore these databases.</span></span>  
  
 <span data-ttu-id="01ce8-112">**否則，**</span><span class="sxs-lookup"><span data-stu-id="01ce8-112">**Otherwise,**</span></span>  
 <span data-ttu-id="01ce8-113">**如果 BAM 已啟用，也會搭配 BM.exe 設定一組正確的 BAM 資料庫必須先為一組一起還原。**</span><span class="sxs-lookup"><span data-stu-id="01ce8-113">**if BAM is enabled and is also configured with BM.exe, the correct set of BAM databases must be restored together as a set.**</span></span> <span data-ttu-id="01ce8-114">若要確定會復原一組完整的封存資料，BAM 封存資料庫被備份資料分割會複製到 BAM 封存後，但從 BAM 主要匯入資料庫刪除資料分割。</span><span class="sxs-lookup"><span data-stu-id="01ce8-114">To ensure that a complete set of archived data is recovered, the BAM Archive database is backed up after the partition is copied into the BAM Archive, but before the partition is deleted from the BAM Primary Import database.</span></span> <span data-ttu-id="01ce8-115">這是由所插入的最後一個步驟 「 結束封存 」 之前，備份 BAM 封存資料庫的步驟，藉以修改每個活動的資料維護 SSIS 封裝執行</span><span class="sxs-lookup"><span data-stu-id="01ce8-115">This is performed by modifying the data maintenance SSIS package for each activity by inserting a step to back up the BAM Archive database before the last step "End Archiving."</span></span>  
  
 <span data-ttu-id="01ce8-116">BAM 資料庫的還原程序： 如果 x 的最後備份日期還原 BAM 主要匯入資料庫，還原 BAM 封存和 BAM 星狀結構描述資料庫對應的複本至最新的資料維護 SSIS 封裝時的日期x 的日期之前執行。</span><span class="sxs-lookup"><span data-stu-id="01ce8-116">The restore procedure for the BAM databases is: If the BAM Primary Import database is restored with the last backup date of x, restore the copies of the BAM Archive and BAM Star Schema databases that correspond to the latest date when the data maintenance SSIS package was run before the date of x.</span></span>  
  
 <span data-ttu-id="01ce8-117">識別一組正確的 BAM 資料庫之後，還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫中所述，使用標準程序[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫。</span><span class="sxs-lookup"><span data-stu-id="01ce8-117">After the correct set of BAM databases is identified, restore the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases using standard procedures as documented in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online for restoring [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ce8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01ce8-118">See Also</span></span>  
 [<span data-ttu-id="01ce8-119">備份 BAM 分析和追蹤 Analysis Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="01ce8-119">Backing Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)