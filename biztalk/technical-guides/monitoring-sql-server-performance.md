---
title: 監視 SQL Server 效能 |Microsoft 文件
description: 監控 BizTalk Server 資料庫時使用 效能工具，活動監視器和資料收集
ms.custom: ''
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 020fa764-968e-467c-b146-d069f5606a0f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e4f9db738298ec2a242350faae3ba5bc9da1c92
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007895"
---
# <a name="monitor-sql-server-performance"></a>監視 SQL Server 效能
SQL Server 提供數個工具，用於監視 SQL Server 中的事件，以及用來微調實體資料庫設計。 [效能監視和微調工具](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools)描述這些工具。 
  
BizTalk Server 是需要大量資料庫的程序。 當 BizTalk Server 效能問題進行疑難排解，可能很有幫助也請檢查 SQL Server 效能。 下列工具可協助。  
  
## <a name="sql-server-activity-monitor"></a>SQL Server 活動監視器  
SQL Server 活動監視器 」 提供 SQL Server 處理序以及這些處理序如何影響目前的 SQL Server 執行個體的相關資訊。 如需詳細資訊，請參閱[活動監視器](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor)，和[如何： 開啟活動監視器 (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio)。 
  
## <a name="sql-serverdata-collection"></a>SQL ServerData 集合  
SQL Server 提供您可以使用來取得及儲存從數個來源蒐集資料的資料收集器。 資料收集器可讓您使用資料收集容器，可讓您決定的範圍與執行 SQL Server 的電腦上的資料收集的頻率。 請參閱[資料收集](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection)。
  
## <a name="see-also"></a>請參閱  
 [最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)