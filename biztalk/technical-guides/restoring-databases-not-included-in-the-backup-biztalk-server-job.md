---
title: 還原資料庫不包含在 「 備份 BizTalk Server 」 工作中 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7141980-d4a6-4409-be9b-c94a7f733376
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b24b0815c5948bac86dc3c614d05eb87d0684bdb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999247"
---
# <a name="restoring-databases-not-included-in-the-backup-biztalk-server-job"></a>還原資料庫不包含在備份 BizTalk Server 作業
本節說明如何還原資料庫整體的 BizTalk 解決方案的一部分，但不會由 「 備份 BizTalk Server 」 工作備份。 BizTalk 解決方案的一部分的所有資料庫會藉由使用 「 備份 BizTalk Server 」 作業，但不包括下列都備份：  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services 資料庫  
  
- 當您啟用 BAM，並使用 BM.exe 設定的 BAM 資料庫  
  
  本節也說明如何還原上面所列的資料庫之後更新資料庫參考，並包含解析未完成的 BAM 活動執行個體的相關資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [還原 Analysis Services 和支援資料庫](../technical-guides/restoring-analysis-services-and-supporting-databases.md)  
  
-   [更新資料庫參考](../technical-guides/updating-database-references.md)  
  
-   [如何解析未完成的 BAM 活動執行個體](../technical-guides/how-to-resolve-incomplete-bam-activity-instances.md)