---
title: 如何備份 BAM 分析和追蹤 Analysis Server 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, DTS packages
- backing up [BAM], Tracking Analysis Server database
- backing up [BAM], OLAP cubes
- backing up [BAM], DTS packages
- purging, OLAP cubes
- Analysis database [BAM], backing up
- scheduling, BAM backups
- backing up [BAM], Analysis database
- OLAP cubes, purging
- backing up, BAM
- backing up [BAM], database order
- DTS packages, backing up
- backing up [BAM], Star Schema database
- backing up [BAM], scheduling
- Tracking Analysis Server database [BAM], backing up
- Star Schema database [BAM], backing up
ms.assetid: d39e3491-ab54-44f2-990a-7b8ee86f0501
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: effa2f5787f04493713ea6972562fe768081f4bc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970268"
---
# <a name="how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases"></a><span data-ttu-id="a2924-102">如何備份 BAM 分析和追蹤 Analysis Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="a2924-102">How to Back Up the BAM Analysis and Tracking Analysis Server Databases</span></span>
<span data-ttu-id="a2924-103">商務活動監控 (BAM) 分析資料庫和追蹤 Analysis Server 資料庫會將內容儲存在 SQL Server Analysis Services Cube 中。</span><span class="sxs-lookup"><span data-stu-id="a2924-103">The Business Activity Monitoring (BAM) Analysis database and the Tracking Analysis Server database store content in SQL Server Analysis Services cubes.</span></span> <span data-ttu-id="a2924-104">「備份 BizTalk Server」工作不會備份這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="a2924-104">The Backup BizTalk Server job does not back up these databases.</span></span> <span data-ttu-id="a2924-105">相反的，若要備份這些資料庫，您必須使用 SQL Server 分析管理員。</span><span class="sxs-lookup"><span data-stu-id="a2924-105">Instead, to backup these databases, you must use SQL Server Analysis Manager.</span></span>  
  
 <span data-ttu-id="a2924-106">備份這些資料庫之後，您可能需要清除 OLAP Cube。</span><span class="sxs-lookup"><span data-stu-id="a2924-106">After you back up these databases, you may want to purge the OLAP cubes.</span></span> <span data-ttu-id="a2924-107">清除 OLAP Cube 時，您也必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a2924-107">When you purge the OLAP cubes, you must also perform the following steps:</span></span>  
  
1.  <span data-ttu-id="a2924-108">清除 OLAP Cube 之前，請先在 BAMStarSchema 資料庫中，截斷您要清除之 Cube 的事實資料表。</span><span class="sxs-lookup"><span data-stu-id="a2924-108">Before you purge the OLAP cubes, in the BAMStarSchema database, truncate the fact table(s) for the cube you want to purge.</span></span> <span data-ttu-id="a2924-109">資料表命名慣例為"bam_*\<CubeName\>*_Facts"。</span><span class="sxs-lookup"><span data-stu-id="a2924-109">The table naming convention is "bam_*\<CubeName\>*_Facts".</span></span>  
  
2.  <span data-ttu-id="a2924-110">清除 OLAP Cube 之後，您必須完整地處理作用中、已完成和虛擬的 Cube。</span><span class="sxs-lookup"><span data-stu-id="a2924-110">After you purge the OLAP cubes, you must fully process active, completed, and virtual cubes.</span></span>  
  
 <span data-ttu-id="a2924-111">如需有關備份分析資料庫的指示，請參閱《SQL Server 線上叢書》中的＜封存 Analysis Services 資料庫＞。</span><span class="sxs-lookup"><span data-stu-id="a2924-111">For instructions about backing up the analysis databases, see "Archiving an Analysis Services Database" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a2924-112">**排程 BAM 資料庫的備份**</span><span class="sxs-lookup"><span data-stu-id="a2924-112">**Scheduling backups for the BAM databases**</span></span>  
  
 <span data-ttu-id="a2924-113">如果您使用 BAM，請確認在備份封裝依排程執行時，沒有 BAM Cube 程序或資料維護 Data Transformation Services (DTS) 封裝在執行。</span><span class="sxs-lookup"><span data-stu-id="a2924-113">If you are using BAM, verify that neither the BAM cube process nor data maintenance Data Transformation Services (DTS) packages are running when the backup package is scheduled to run.</span></span>  
  
 <span data-ttu-id="a2924-114">若要確保所有的 BAM 資料庫中都有一致的結構描述，請在每次部署或解除部署 BAM 活動時，備份 BAM 資料庫和 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="a2924-114">To ensure consistent schema across all BAM databases, back up the BAM databases and DTS packages each time you deploy or undeploy a BAM activity.</span></span>  
  
 <span data-ttu-id="a2924-115">在每次部署或解除部署 BAM 檢視時，備份 BAM 分析資料庫與 BAMStarSchema 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a2924-115">Back up the BAM Analysis database and BAMStarSchema database each time you deploy or undeploy a BAM view.</span></span>  
  
 <span data-ttu-id="a2924-116">依下列順序備份 BAM 資料庫：</span><span class="sxs-lookup"><span data-stu-id="a2924-116">Back up the BAM databases in the following order:</span></span>  
  
1.  <span data-ttu-id="a2924-117">執行「備份 BizTalk Server」作業以備份 BAMPrimaryImport 資料庫和其他 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a2924-117">Run the Backup BizTalk Server job to back up the BAMPrimaryImport database and your other BizTalk Server databases.</span></span>  
  
2.  <span data-ttu-id="a2924-118">針對所有活動執行 BAM 資料維護 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="a2924-118">Run the BAM data maintenance DTS package for all activities.</span></span>  
  
     <span data-ttu-id="a2924-119">將這些步驟併入 DTS 封裝，並排程封裝以定期執行。</span><span class="sxs-lookup"><span data-stu-id="a2924-119">Incorporate these steps into a DTS package, and schedule the package to run on a regular basis.</span></span> <span data-ttu-id="a2924-120">若要確保資料完整性，請確定在此備份封裝依排程執行時，沒有其他 BAM Cube 或資料維護 DTS 封裝在執行。</span><span class="sxs-lookup"><span data-stu-id="a2924-120">To ensure data integrity, make sure no other BAM cubing or data maintenance DTS packages run when this backup package is scheduled to run.</span></span>  
  
     <span data-ttu-id="a2924-121">為了確保可以在 BAMArchive 資料庫失敗時復原完整的封存資料，請在複製資料分割到 BAMArchive 資料庫之後，但是要在從 BAMPrimaryImport 資料庫刪除資料分割之前，備份 BAMArchive 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a2924-121">To ensure that you can recover a complete set of archived data if the BAMArchive database fails, back up the BAMArchive database after you copy the partition into the BAMArchive database, but before you delete the partition from the BAMPrimaryImport database.</span></span> <span data-ttu-id="a2924-122">如果要這樣做，請修改每個活動的資料維護 DTS 封裝，以在 DTS 封裝中的最後一個步驟「結束封存」之前插入備份 BAMArchive 資料庫的步驟。</span><span class="sxs-lookup"><span data-stu-id="a2924-122">To do this, modify the data maintenance DTS package for each activity to insert a step to back up the BAMArchive database before the last step in the DTS package, "End Archiving."</span></span>  
  
3.  <span data-ttu-id="a2924-123">備份 BAMAnalysis 資料庫，然後備份 BAMStarSchema 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a2924-123">Back up the BAMAnalysis database, and then the BAMStarSchema database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2924-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2924-124">See Also</span></span>  
 [<span data-ttu-id="a2924-125">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="a2924-125">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)