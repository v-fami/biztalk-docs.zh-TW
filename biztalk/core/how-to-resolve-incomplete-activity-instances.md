---
title: "如何解析未完成的活動執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances, incomplete [BAM]
- restoring, BAM
- Primary Import database [BAM], incomplete instances
- restoring [BAM], Primary Import database
- Primary Import database [BAM], restoring
- BAM, restoring
ms.assetid: 8adbcb66-58ad-42c5-ba16-7dc07572099e
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81df9ee8b004a2dbd4a672eecb4f34894421a432
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-resolve-incomplete-activity-instances"></a><span data-ttu-id="72746-102">如何解析未完成的活動執行個體</span><span class="sxs-lookup"><span data-stu-id="72746-102">How to Resolve Incomplete Activity Instances</span></span>
<span data-ttu-id="72746-103">BAM 會將未完成的活動執行個體的資料儲存在特殊*作用中執行個體*BAMPrimaryImport 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="72746-103">BAM stores data for incomplete activity instances in a special *active instance* table in the BAMPrimaryImport database.</span></span>  
  
 <span data-ttu-id="72746-104">如果部分執行個體記錄已 BAMPrimaryImport 資料庫上次備份前開始，但在備份之後完成，這些執行個體記錄保留在作用中執行個體資料表。</span><span class="sxs-lookup"><span data-stu-id="72746-104">If some instance records were started before the last backup of the BAMPrimaryImport database but completed after the backup, those instance records remain in an active instance table.</span></span> <span data-ttu-id="72746-105">這是因為還原 BAMPrimaryImport 資料庫之後，這些執行個體的完成記錄會遺失。</span><span class="sxs-lookup"><span data-stu-id="72746-105">This is because after the BAMPrimaryImport database is restored, the completion records for these instances are lost.</span></span>  
  
 <span data-ttu-id="72746-106">雖然作用中執行個體資料表的記錄不會讓 BAM 運作失常，我們仍建議您將這些記錄標示為「已完成」，再將它們移出作用中執行個體資料表。</span><span class="sxs-lookup"><span data-stu-id="72746-106">Although the records in the active instance table do not prevent BAM from functioning properly, we recommend that you mark these records as "completed," and then move them out of the active instance table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="72746-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="72746-107">Prerequisites</span></span>  
 <span data-ttu-id="72746-108">您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="72746-108">You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.</span></span>  
  
### <a name="to-generate-a-list-of-incomplete-activityids-for-an-activity"></a><span data-ttu-id="72746-109">產生活動的未完成 ActivityID 清單</span><span class="sxs-lookup"><span data-stu-id="72746-109">To generate a list of incomplete ActivityIDs for an activity</span></span>  
  
1.  <span data-ttu-id="72746-110">針對 BAMPrimaryImport 資料庫執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="72746-110">Run the following query against the BAMPrimaryImport database:</span></span>  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  <span data-ttu-id="72746-111">如果外部系統的資料顯示活動執行個體實際上已完成，請執行下列查詢以手動完成此執行個體：</span><span class="sxs-lookup"><span data-stu-id="72746-111">If data from external systems indicates that the activity instance is in fact completed, run the following query to manually complete the instance:</span></span>  
  
    ```  
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="72746-112">您可以使用 ContinuationID 來取代 ActivityID，再依照相同的程序完成接續活動。</span><span class="sxs-lookup"><span data-stu-id="72746-112">You can follow the same process to complete a continuation activity by replacing ActivityID with ContinuationID.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72746-113">如果主要追蹤具有任何作用中的接續追蹤，它會處於作用中直到完成接續追蹤為止。</span><span class="sxs-lookup"><span data-stu-id="72746-113">If the main trace has any active continuation traces, it remains active until the continuation traces are completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72746-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72746-114">See Also</span></span>  
 [<span data-ttu-id="72746-115">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="72746-115">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)