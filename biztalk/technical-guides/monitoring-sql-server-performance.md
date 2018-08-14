---
title: 監視 SQL Server 效能 |Microsoft Docs
description: 監視 BizTalk Server 資料庫使用的效能工具、 活動監視器和資料收集
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
ms.openlocfilehash: 730896dc1cf0a465f68965f812da7311dd8664ab
ms.sourcegitcommit: ed9590dbcd97c12a1fe5ce2cdf8d826492cccdff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39640114"
---
# <a name="monitor-sql-server-performance"></a>監視 SQL Server 效能
SQL Server 提供數個工具，用於監視 SQL Server 中的事件，以及用來微調實體資料庫設計。 [效能監視和微調工具](https://docs.microsoft.com/sql/relational-databases/performance/performance-monitoring-and-tuning-tools)描述這些工具。 
  
BizTalk Server 會是需要大量資料庫的程序。 BizTalk Server 效能問題進行疑難排解時, 很有幫助也請檢查 SQL Server 效能。 下列工具可以幫助。  
  
## <a name="sql-server-activity-monitor"></a>SQL Server 活動監視器  
SQL Server 活動監視器 」 提供 SQL Server 處理序以及這些處理序如何影響目前的執行個體的 SQL Server 的相關資訊。 如需詳細資訊，請參閱 <<c0> [ 活動監視器](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor)，並[如何： 開啟活動監視器 (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio)。 
  
## <a name="sql-serverdata-collection"></a>SQL ServerData 集合  
SQL Server 提供資料收集器，您可以使用它來取得及儲存從數個來源收集的資料。 資料收集器可讓您使用資料收集容器，可讓您決定的範圍與執行 SQL Server 的電腦上的資料收集的頻率。 請參閱[資料收集](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection)。
  
## <a name="see-also"></a>另請參閱  
 [最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)
