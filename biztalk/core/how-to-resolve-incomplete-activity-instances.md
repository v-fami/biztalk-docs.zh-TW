---
title: 解析未完成的活動執行個體 |Microsoft 文件
description: BAM 活動執行個體之後備份 BAMPrimaryImport 資料庫，BizTalk Server 中保持作用中狀態
ms.custom: ''
ms.date: 01/17/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8adbcb66-58ad-42c5-ba16-7dc07572099e
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 616ba096062da7ede8d78122e5a6faaca2befdc4
ms.sourcegitcommit: 20d33d8b74bf129a8d1a506ac4a1ad960184966d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2018
ms.locfileid: "27873414"
---
# <a name="resolve-incomplete-bam-activity-instances---biztalk-server"></a><span data-ttu-id="40467-103">解析不完整的 BAM 活動執行個體-BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="40467-103">Resolve incomplete BAM activity instances - BizTalk Server</span></span>
<span data-ttu-id="40467-104">BAM 將未完成的活動執行個體的資料儲存在特殊 *作用中執行個體* BAMPrimaryImport 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="40467-104">BAM stores data for incomplete activity instances in a special *active instance* table in the BAMPrimaryImport database.</span></span>  
  
 <span data-ttu-id="40467-105">如果部分執行個體記錄 BAMPrimaryImport 資料庫上次備份前開始但完成備份之後，這些執行個體記錄會保留在作用中執行個體資料表。</span><span class="sxs-lookup"><span data-stu-id="40467-105">If some instance records were started before the last backup of the BAMPrimaryImport database but completed after the backup, those instance records remain in an active instance table.</span></span> <span data-ttu-id="40467-106">這是因為 BAMPrimaryImport 資料庫還原後，這些執行個體的完成記錄會遺失。</span><span class="sxs-lookup"><span data-stu-id="40467-106">This is because after the BAMPrimaryImport database is restored, the completion records for these instances are lost.</span></span>  
  
 <span data-ttu-id="40467-107">雖然作用中執行個體資料表的記錄不會讓 BAM 運作失常，我們仍建議您將這些記錄標示為「已完成」，再將它們移出作用中執行個體資料表。</span><span class="sxs-lookup"><span data-stu-id="40467-107">Although the records in the active instance table do not prevent BAM from functioning properly, we recommend that you mark these records as "completed," and then move them out of the active instance table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="40467-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="40467-108">Prerequisites</span></span>  
<span data-ttu-id="40467-109">BizTalk Server 系統管理員群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="40467-109">Sign in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="create-a-list-of-incomplete-activityids"></a><span data-ttu-id="40467-110">建立未完成 Activityid 的清單</span><span class="sxs-lookup"><span data-stu-id="40467-110">Create a list of incomplete ActivityIDs</span></span> 
  
1.  <span data-ttu-id="40467-111">針對 BAMPrimaryImport 資料庫執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="40467-111">Run the following query against the BAMPrimaryImport database:</span></span>  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  <span data-ttu-id="40467-112">如果外部系統的資料顯示活動執行個體實際上已完成，請執行下列查詢以手動完成此執行個體：</span><span class="sxs-lookup"><span data-stu-id="40467-112">If data from external systems indicates that the activity instance is in fact completed, run the following query to manually complete the instance:</span></span>  
  
    ```  
    begin transaction
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    commit transaction
    ```  
  
> [!NOTE]
>  <span data-ttu-id="40467-113">您可以遵循相同的程序完成接續活動取代`ActivityID`與`ContinuationID`。</span><span class="sxs-lookup"><span data-stu-id="40467-113">You can follow the same process to complete a continuation activity by replacing `ActivityID` with `ContinuationID`.</span></span>  
> 
>  <span data-ttu-id="40467-114">如果主要追蹤具有任何作用中的接續追蹤，它會處於作用中直到完成接續追蹤為止。</span><span class="sxs-lookup"><span data-stu-id="40467-114">If the main trace has any active continuation traces, it remains active until the continuation traces are completed.</span></span>  

## <a name="remove-incomplete-instances"></a><span data-ttu-id="40467-115">移除未完成的執行個體</span><span class="sxs-lookup"><span data-stu-id="40467-115">Remove incomplete instances</span></span>
<span data-ttu-id="40467-116">您也可以使用自訂的 SQL 指令碼 BAMPrimaryImport 資料庫中移除未完成的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="40467-116">You can also remove incomplete activity instances from the BAMPrimaryImport database using a custom SQL script.</span></span> <span data-ttu-id="40467-117">請參閱[移除未完成的活動執行個體](how-to-remove-incomplete-activity-instances.md)範例。</span><span class="sxs-lookup"><span data-stu-id="40467-117">See [Remove incomplete activity instances](how-to-remove-incomplete-activity-instances.md) for a sample.</span></span>

## <a name="see-also"></a><span data-ttu-id="40467-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40467-118">See Also</span></span>  
 [<span data-ttu-id="40467-119">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="40467-119">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)
