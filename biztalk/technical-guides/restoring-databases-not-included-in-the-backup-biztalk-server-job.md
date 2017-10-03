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
# <a name="restoring-databases-not-included-in-the-backup-biztalk-server-job"></a>還原資料庫不包含在備份 BizTalk Server 作業
本節說明如何還原資料庫的整體的 BizTalk 解決方案的一部分，但不由 「 備份 BizTalk Server 」 工作備份。 BizTalk 解決方案的一部分的所有資料庫會被都備份可以使用備份 BizTalk Server 作業，但下列除外：  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫  
  
-   當 BAM 啟用及設定使用 BM.exe BAM 資料庫  
  
 本節也說明如何還原上面所列的資料庫之後更新資料庫參考，並包含解析不完整的 BAM 活動執行個體的相關資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [還原 Analysis Services 和支援的資料庫](../technical-guides/restoring-analysis-services-and-supporting-databases.md)  
  
-   [更新資料庫參考](../technical-guides/updating-database-references.md)  
  
-   [如何解決不完整的 BAM 活動執行個體](../technical-guides/how-to-resolve-incomplete-bam-activity-instances.md)