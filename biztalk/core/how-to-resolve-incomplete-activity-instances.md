---
title: "解析未完成的活動執行個體 |Microsoft 文件"
description: "BAM 活動執行個體之後備份 BAMPrimaryImport 資料庫，BizTalk Server 中保持作用中狀態"
ms.custom: 
ms.date: 01/17/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8adbcb66-58ad-42c5-ba16-7dc07572099e
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 616ba096062da7ede8d78122e5a6faaca2befdc4
ms.sourcegitcommit: 20d33d8b74bf129a8d1a506ac4a1ad960184966d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2018
---
# <a name="resolve-incomplete-bam-activity-instances---biztalk-server"></a>解析不完整的 BAM 活動執行個體-BizTalk Server
BAM 將未完成的活動執行個體的資料儲存在特殊 *作用中執行個體* BAMPrimaryImport 資料庫中的資料表。  
  
 如果部分執行個體記錄 BAMPrimaryImport 資料庫上次備份前開始但完成備份之後，這些執行個體記錄會保留在作用中執行個體資料表。 這是因為 BAMPrimaryImport 資料庫還原後，這些執行個體的完成記錄會遺失。  
  
 雖然作用中執行個體資料表的記錄不會讓 BAM 運作失常，我們仍建議您將這些記錄標示為「已完成」，再將它們移出作用中執行個體資料表。  
  
## <a name="prerequisites"></a>필수 구성 요소  
BizTalk Server 系統管理員群組的成員身分登入。  
  
## <a name="create-a-list-of-incomplete-activityids"></a>建立未完成 Activityid 的清單 
  
1.  針對 BAMPrimaryImport 資料庫執行下列查詢：  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  如果外部系統的資料顯示活動執行個體實際上已完成，請執行下列查詢以手動完成此執行個體：  
  
    ```  
    begin transaction
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    commit transaction
    ```  
  
> [!NOTE]
>  您可以遵循相同的程序完成接續活動取代`ActivityID`與`ContinuationID`。  
> 
>  如果主要追蹤具有任何作用中的接續追蹤，它會處於作用中直到完成接續追蹤為止。  

## <a name="remove-incomplete-instances"></a>移除未完成的執行個體
您也可以使用自訂的 SQL 指令碼 BAMPrimaryImport 資料庫中移除未完成的活動執行個體。 請參閱[移除未完成的活動執行個體](how-to-remove-incomplete-activity-instances.md)範例。

## <a name="see-also"></a>另請參閱  
 [備份和還原 BAM](../core/backing-up-and-restoring-bam.md)
