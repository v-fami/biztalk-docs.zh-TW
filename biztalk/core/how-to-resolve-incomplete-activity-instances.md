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
# <a name="how-to-resolve-incomplete-activity-instances"></a>如何解析未完成的活動執行個體
BAM 會將未完成的活動執行個體的資料儲存在特殊*作用中執行個體*BAMPrimaryImport 資料庫中的資料表。  
  
 如果部分執行個體記錄已 BAMPrimaryImport 資料庫上次備份前開始，但在備份之後完成，這些執行個體記錄保留在作用中執行個體資料表。 這是因為還原 BAMPrimaryImport 資料庫之後，這些執行個體的完成記錄會遺失。  
  
 雖然作用中執行個體資料表的記錄不會讓 BAM 運作失常，我們仍建議您將這些記錄標示為「已完成」，再將它們移出作用中執行個體資料表。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這個程序。  
  
### <a name="to-generate-a-list-of-incomplete-activityids-for-an-activity"></a>產生活動的未完成 ActivityID 清單  
  
1.  針對 BAMPrimaryImport 資料庫執行下列查詢：  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  如果外部系統的資料顯示活動執行個體實際上已完成，請執行下列查詢以手動完成此執行個體：  
  
    ```  
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    ```  
  
> [!NOTE]
>  您可以使用 ContinuationID 來取代 ActivityID，再依照相同的程序完成接續活動。  
  
> [!NOTE]
>  如果主要追蹤具有任何作用中的接續追蹤，它會處於作用中直到完成接續追蹤為止。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BAM](../core/backing-up-and-restoring-bam.md)