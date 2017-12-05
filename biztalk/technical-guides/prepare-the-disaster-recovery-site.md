---
title: "準備災害復原站台 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b66f3c8-afe0-4ac0-b925-8f780d14bd4b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a60be6d04d0f73013f67c5fe8e5b0144357fd1f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="prepare-the-disaster-recovery-site"></a>準備災害復原站台
BizTalk Server 記錄傳送具有兩個支援的案例。 其中一個是記錄傳送的所有生產執行個體上的所有資料庫的位置[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]套用至單一災害復原執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 其他的案例是記錄的位置的每個實際執行個體的資料庫傳送[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]套用到對應的執行個體的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在災害復原站台。 請注意，它會完全支援有相同數目的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體在災害復原站台，因為沒有在生產環境中，但是在較少的實體伺服器上。 本節提供這些準備工作的指引。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [準備災害復原 SQL Server](../technical-guides/preparing-the-disaster-recovery-sql-servers.md)  
  
-   [備份 BAM 分析和追蹤 Analysis Server 資料庫](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)  
  
-   [準備災害復原 BizTalk Server](../technical-guides/preparing-the-disaster-recovery-biztalk-servers.md)  
  
-   [準備應用程式的災害復原](../technical-guides/preparing-applications-for-disaster-recovery.md)  
  
-   [如何還原主要密碼伺服器](../technical-guides/how-to-restore-the-master-secret-server.md)