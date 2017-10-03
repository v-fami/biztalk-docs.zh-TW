---
title: "管理 BAM 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], databases
- databases [BAM], managing
- databases, BAM
ms.assetid: ce3c472e-2da1-4d67-816a-befe4ded20d9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dbe8cdb2c7806ab62b67db80c4741d64560fba9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-bam-databases"></a>管理 BAM 資料庫
系統管理員會使用 BAM 管理公用程式 (bm.exe) 安裝、管理和更新 BAM 資料庫。 本節將說明如何使用 BAM 管理公用程式，執行下表所述的一般 BAM 資料庫系統管理員工作。  
  
 如需備份和還原 BAM 資料庫的資訊，請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。  
  
|資料庫|預設資料庫名稱|Description|  
|--------------|---------------------------|-----------------|  
|BAM 主要匯入資料庫|BAMPrimaryImport|BAM 會在其中收集原始追蹤資料。|  
|BAM Notification Services 應用程式資料庫|BAMAlertsApplication|包含 BAM 通知的警示資訊。 例如，當您使用 BAM 入口網站建立警示時，就會在資料庫中插入項目以指定與警示相關的條件和事件，以及警示的其他支援資料項目。|  
|BAM Notification Services 執行個體資料庫|BAMAlertsNSMain|包含指定通知服務如何連接至 BAM 所監控系統的執行個體資訊。|  
|BAM 星狀結構描述資料庫|BAMStarSchema|包含臨時資料表以及量值和維度資料表。|  
|BAM 分析資料庫|BAMAnalysis|含有可供線上及離線分析使用的 BAM OLAP Cube。|  
|BAM 封存資料庫|BAMArchive|封存舊的商務活動資料。 您可以建立 BAM 封存資料庫，將 BAM 主要匯入資料庫中商務活動資料的累積量降到最低。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [封存主要匯入資料庫資料](../core/archiving-primary-import-database-data.md)  
  
-   [在封存資料庫中建立資料分割的檢視](../core/creating-a-partitioned-view-in-the-archiving-database.md)  
  
-   [排程 SQL Server Integration Services 封裝](../core/scheduling-sql-server-integration-services-packages.md)  
  
-   [如何設定 BAM 資料庫使用 BAM 管理公用程式](../core/how-to-set-up-the-bam-databases-using-the-bam-management-utility.md)  
  
-   [如何擷取 BAM 組態檔使用 BAM 管理公用程式](../core/how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility.md)  
  
-   [如何更新 BAM 組態使用 BAM 管理公用程式](../core/how-to-update-the-bam-configuration-using-the-bam-management-utility.md)  
  
-   [如何參考其他 BAM 主要匯入資料庫](../core/how-to-reference-additional-bam-primary-import-databases.md)  
  
-   [如何停用 BAM 主要匯入資料庫參考](../core/how-to-disable-a-bam-primary-import-database-reference.md)  
  
-   [如何列出所有被參考資料庫](../core/how-to-list-all-referenced-databases.md)  
  
-   [如何移除未完成的活動執行個體](../core/how-to-remove-incomplete-activity-instances.md)  
  
-   [如何更新 BAM 管理公用程式組態之後備份與還原](../core/update-the-bam-management-utility-configuration-after-a-backup-and-restore.md)  
  
-   [如何整合 BAM 與 SQL Server Reporting Services](../core/how-to-integrate-bam-with-sql-server-reporting-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM](../core/managing-bam.md)