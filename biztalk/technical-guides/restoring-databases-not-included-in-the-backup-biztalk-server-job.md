---
title: "還原資料庫不包含在備份 BizTalk Server 作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7141980-d4a6-4409-be9b-c94a7f733376
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3277886207e04a30fec8bb61f29b5fe8c5ec3545
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-databases-not-included-in-the-backup-biztalk-server-job"></a><span data-ttu-id="5968b-102">還原資料庫不包含在備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="5968b-102">Restoring Databases Not Included in the Backup BizTalk Server Job</span></span>
<span data-ttu-id="5968b-103">本節說明如何還原資料庫的整體的 BizTalk 解決方案的一部分，但不由 「 備份 BizTalk Server 」 工作備份。</span><span class="sxs-lookup"><span data-stu-id="5968b-103">This section describes how to restore databases that are part of the overall BizTalk solution but are not backed up by the Backup BizTalk Server job.</span></span> <span data-ttu-id="5968b-104">BizTalk 解決方案的一部分的所有資料庫會被都備份可以使用備份 BizTalk Server 作業，但下列除外：</span><span class="sxs-lookup"><span data-stu-id="5968b-104">All databases that are part of a BizTalk solution will be backed up by using the Backup BizTalk Server job except for the following:</span></span>  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]<span data-ttu-id="5968b-105">Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="5968b-105"> Analysis Services databases</span></span>  
  
-   <span data-ttu-id="5968b-106">當 BAM 啟用及設定使用 BM.exe BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="5968b-106">BAM databases when BAM is enabled and configured using BM.exe</span></span>  
  
 <span data-ttu-id="5968b-107">本節也說明如何還原上面所列的資料庫之後更新資料庫參考，並包含解析不完整的 BAM 活動執行個體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5968b-107">This section also describes how to update database references after restoring the databases listed above and includes information about resolving incomplete BAM activity instances.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5968b-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="5968b-108">In This Section</span></span>  
  
-   [<span data-ttu-id="5968b-109">還原 Analysis Services 和支援的資料庫</span><span class="sxs-lookup"><span data-stu-id="5968b-109">Restoring Analysis Services and Supporting Databases</span></span>](../technical-guides/restoring-analysis-services-and-supporting-databases.md)  
  
-   [<span data-ttu-id="5968b-110">更新資料庫參考</span><span class="sxs-lookup"><span data-stu-id="5968b-110">Updating Database References</span></span>](../technical-guides/updating-database-references.md)  
  
-   [<span data-ttu-id="5968b-111">如何解決不完整的 BAM 活動執行個體</span><span class="sxs-lookup"><span data-stu-id="5968b-111">How to Resolve Incomplete BAM Activity Instances</span></span>](../technical-guides/how-to-resolve-incomplete-bam-activity-instances.md)