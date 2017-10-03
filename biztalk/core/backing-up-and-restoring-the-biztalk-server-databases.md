---
title: "備份和還原 BizTalk Server 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- backing up, transaction logs
- maintaining, restoring
- restoring, BizTalk Server
- maintaining, backing up
- transaction logs
ms.assetid: 7c08ce19-614c-4728-8dde-c40d4052339e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44bbb9316f1d036551acba5441424bcce65c2549
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-the-biztalk-server-databases"></a>備份和還原 BizTalk Server 資料庫
本節提供有關如何備份和還原 BizTalk Server 資料庫的資訊。 您應該遵循本節中的程序，以確保在發生硬體失敗時有能力還原前後一致的 BizTalk Server 環境。 BizTalk Server 會跨資料庫執行分散式交易，因此備份然後還原所有資料庫很重要。  
  
 BizTalk Server 需要使用完整資料庫備份和記錄備份並搭配交易式記錄標示的自訂備份程序。 此程序的相關資訊，請參閱[標示的交易、 完整備份和記錄檔備份](../core/marked-transactions-full-backups-and-log-backups.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [檢查清單： 備份和還原 BizTalk Server 資料庫](../core/checklist-back-up-and-restore-biztalk-server-databases.md)  
  
-   [備份和還原資料庫的最佳作法](../core/best-practices-for-backing-up-and-restoring-databases.md)  
  
-   [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)  
  
-   [備份和還原 BAM](../core/backing-up-and-restoring-bam.md)  
  
-   [解決資料遺失](../core/resolving-data-loss.md)  
  
-   [備份和還原的相關進階的資訊](../core/advanced-information-about-backup-and-restore1.md)