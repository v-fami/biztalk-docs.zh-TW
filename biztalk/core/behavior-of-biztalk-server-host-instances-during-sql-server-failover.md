---
title: "SQL Server 容錯移轉期間的 BizTalk Server 主控件執行個體的行為 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5642417-d27f-4539-a369-5fa11bec4a4f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f244ce0fe00fe05f73db5f43ec867254b7a61fb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="behavior-of-biztalk-server-host-instances-during-sql-server-failover"></a>SQL Server 容錯移轉期間的 BizTalk Server 主控件執行個體行為
如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的叢集執行個體發生容錯移轉，儲存在 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 叢集執行個體上的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫將暫時無法使用。 本節記錄當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫無法使用時，與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 關聯的主控件執行個體行為。  
  
## <a name="behavior-of-in-process-host-instances-during-sql-server-failover"></a>SQL Server 容錯移轉期間的內含式主控件執行個體行為  
 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫無法使用，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件的內含式執行個體就會被回收，直到還原 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的連線為止。 一旦 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫的連線還原，文件處理就會繼續正常執行。  
  
## <a name="behavior-of-isolated-host-instances-during-sql-server-failover"></a>SQL Server 容錯移轉期間的外掛式主控件執行個體行為  
 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫無法使用，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件的外掛式執行個體就會暫停，且會在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式記錄檔中產生類似以下的錯誤：  
  
```  
All receive locations are being temporarily disabled because either   
the MessageBox or Configuration database is not available.   
When these databases become available, the receive locations will be automatically enabled.  
```  
  
 一旦 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫的連線還原，類似以下的告知性訊息就會寫入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式記錄檔中，且文件處理會繼續正常執行：  
  
```  
All receive locations are being enabled because both the MessageBox and Configuration databases are back online.  
```  
  
## <a name="see-also"></a>另請參閱  
 [主機](../core/hosts.md)