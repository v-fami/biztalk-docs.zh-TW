---
title: "監視 SQL Server 效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020fa764-968e-467c-b146-d069f5606a0f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5abdc3054576e03f28967017767112cea652f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-server-performance"></a>監視 SQL Server 效能
[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供數個工具來監視事件中的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]以及用來微調實體資料庫設計。 主題會描述這些工具[效能監視和微調工具](http://go.microsoft.com/fwlink/?LinkId=146357)(http://go.microsoft.com/fwlink/?LinkId=146357) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。 用於特定工具的相關資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]下面提供效能監視和微調。  
  
## <a name="sql-server-performance-monitoring-tools"></a>SQL Server 效能監視工具  
 因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]這類資料庫密集處理序通常很有幫助，才能查看什麼 SQL Server 中進行疑難排解時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能問題。 本主題的其餘部分描述的效能監視工具，可檢閱上的即時和封存資料[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]。  
  
### <a name="sql-server-2008-r2-activity-monitor"></a>SQL Server 2008 R2 活動監視器  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]活動監視器提供下列相關資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]處理程序以及這些處理序如何影響目前的執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需有關[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]活動監視器，請參閱[活動監視器](http://go.microsoft.com/fwlink/?LinkId=146355)(http://go.microsoft.com/fwlink/?LinkId=146355) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。 如需有關如何開啟活動監視器的資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio，請參閱[如何： 開啟活動監視器 (SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。  
  
### <a name="sql-server-2008-r2-data-collection"></a>SQL Server 2008 R2 資料收集  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] 提供資料收集器，您可用它來取得及儲存從數個來源蒐集而來的資料。 資料收集器可讓您使用資料收集容器，而這些容器可讓您在執行 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] 的電腦上決定資料收集的範圍與頻率。 如需有關實作[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]資料收集，請參閱[資料收集](http://go.microsoft.com/fwlink/?LinkId=146356)(http://go.microsoft.com/fwlink/?LinkId=146356) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)