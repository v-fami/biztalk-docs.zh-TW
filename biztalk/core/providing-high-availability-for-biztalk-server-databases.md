---
title: "BizTalk Server 資料庫提供高可用性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clustering, SQL Servers
- databases, architecture
- SQL Server, clustering
- servers, clustering
- databases, high availability
- architecture
- databases, clustering
- BizTalk Server, architecture
- Windows clustering
- high availability, databases
- clustering, databases
- data, persistence
- SQL Server Analysis Services
ms.assetid: 47fbc402-9e46-41dd-bc12-d1cde1982576
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3648a8f6d48bbfd6cf67995e1d314511b70db7bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="providing-high-availability-for-biztalk-server-databases"></a>為 BizTalk Server 資料庫提供高可用性
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 高度依賴 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 以保存資料。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中所有其他元件和主控件在整合不同的商業應用程式的程序中都有特定的角色 (例如，接收、處理或路由訊息)，但是資料庫電腦會擷取此工作並將它保存到磁碟中。  
  
 若要提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，來設定執行 SQL Server 建立伺服器叢集的兩個資料庫電腦使用 Windows Server 容錯移轉叢集。 伺服器叢集會為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫提供備援和容錯。 不像載入平衡叢集是以一組電腦一起運作以增加可用性和延展性，伺服器叢集通常包含兩個一組的主動/被動組態的資料庫電腦，如此，其中一部電腦即可為另一部電腦提供備份資源。  
  
 下圖顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫層透過主動/被動伺服器叢集提供高可用性。  
  
 ![BizTalk Server 資料庫層](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 若主動資料庫電腦發生錯誤或失敗，則被動電腦會變成主動並掌控資料庫資源，直到失敗的電腦修復為止。 資料庫服務會容錯移轉，並將資料連接還原至新的作用中電腦，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式繼續運作。  
  
 如需安裝的資料庫資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[BizTalk Server 中的資料庫](../core/databases-in-biztalk-server.md)。  
  
 如需備份您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [向外延展資料庫](../core/scaled-out-databases.md)  
  
-   [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)  
  
-   [SQL Server 容錯移轉期間的 BizTalk Server 主控件執行個體的行為](../core/behavior-of-biztalk-server-host-instances-during-sql-server-failover.md)  
  
-   [SQL Server 資料庫鏡像磁碟區陰影複製服務和 AlwaysOn](../core/sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson.md)  
  
## <a name="see-also"></a>另請參閱  
 [為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md)   
 [BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md)