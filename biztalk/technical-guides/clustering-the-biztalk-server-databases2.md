---
title: "叢集 BizTalk Server Databases2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b68bc3f-c0c4-4050-8ca3-df6dd1927637
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c84f8f6ef26c567a1bbac44df078f2df58ca9da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="clustering-the-biztalk-server-databases"></a>叢集 BizTalk Server 資料庫
如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫會變成無法使用，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境將無法正確運作。 若要提供高可用性，您可以建立 Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集以[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，如下圖所示。  
  
 ![BizTalk Server 資料庫層](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 若要建立的高可用性解決方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您必須擁有至少兩部電腦執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]與叢集中的共用的磁碟陣列。  
  
## <a name="clustering-options"></a>叢集選項  
 判斷的最佳叢集組態[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]針對商務需求的資料庫。 以下是一串選項：  
  
-   **主動/被動**。 高可用性的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫通常包含兩個或多個設定為主動/被動伺服器叢集組態的資料庫電腦。 這些電腦會共用一般磁碟資源 (例如 RAID 1 + 0 SCSI 磁碟陣列或儲存區域網路)，並使用 Windows 叢集提供備份備援和容錯功能。  
  
-   **主動/主動**。 Windows 叢集和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可讓您執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]以主動/主動模式叢集的每個節點其中是 「 作用中 」 且正在執行的一或多個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。 比方說，這樣可讓您有一個節點和所有其他 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]另一個節點上的資料庫。 這可讓您以最大化叢集硬體的使用方式，但主動/主動[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]組態應該小心使用。  
  
     可以每個節點同時處理所有的負載[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體期間[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]容錯移轉叢集節點的案例？ 有足夠的 CPU 資源嗎？ 是否有足夠的記憶體？ 網路頻寬呢？ 如何磁碟 I/O 競爭？  
  
     這些只是部分的問題時必須回答才能判斷主動/主動[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集是否適合您的 BizTalk 應用程式。 如果它由決定有一個節點無法處理所有[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]容錯移轉狀況中的執行個體，另一個方法是使用主動/主動/被動叢集。  
  
-   **主動/主動/被動**。 執行階段程序會寫入 BizTalk 管理資料庫、MessageBox 資料庫、追蹤 Analysis Services 資料庫、BAM 分析資料庫、BAM 星狀結構描述資料庫、BAM 主要匯入資料庫以及 BAM 封存資料庫。 因此，若發生嚴重損毀，這些資料庫就顯得特別重要，而且在決定要叢集哪些資料庫時必須有較高的優先順序。 只有使用者或工具會寫入其他資料庫。 MessageBox 資料庫中，您可以考慮主動/主動/被動或主動/主動/主動/被動組態，以減少所需的硬體。  
  
> [!NOTE]  
>  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]Standard Edition 支援 2 個節點的容錯移轉叢集。 如果您決定使用上的主動/主動/被動組態[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]或[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，您必須使用 Enterprise Edition [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
## <a name="procedures-for-clustering-the-databases"></a>叢集資料庫的程序  
 請確定您符合下列必要條件，再啟動叢集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
-   當您建立網域群組您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，您必須建立全域網域帳戶。  
  
-   設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集才能安裝及設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需有關叢集[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]，請參閱[Started with SQL Server 2008 R2 容錯移轉叢集](http://go.microsoft.com/fwlink/?LinkId=156820)(http://go.microsoft.com/fwlink/?LinkId=156820)。  
  
-   若您也要叢集主要密碼伺服器，請先設定該伺服器。 如需高可用性的企業單一登入，請參閱[主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)。  
  
#### <a name="to-run-the-biztalk-server-configuration-wizard"></a>若要執行 BizTalk Server 組態精靈  
  
1.  在執行階段伺服器上安裝 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
2.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態程式。 按一下**啟動**，指向 **程式**，指向  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下 **BizTalk Server 組態**。  
  
3.  若要套用自訂的設定，請遵循[使用自訂組態管理員](http://go.microsoft.com/fwlink/?LinkId=156822)(http://go.microsoft.com/fwlink/?LinkId=156822) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。 若要指定 SQL Server 叢集的 BizTalk Server 資料庫輸入中的 SQL Server 叢集的名稱**資料庫**的組態對話方塊。  
  
4.  完成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態設定中的指示[自訂組態](http://go.microsoft.com/fwlink/?LinkId=156823)(http://go.microsoft.com/fwlink/?LinkId=156823) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 如需有關叢集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[改善在 BizTalk Server 中使用 Windows Server 2008 容錯移轉叢集或 Windows Server 2003 伺服器叢集的容錯功能](http://go.microsoft.com/fwlink/?LinkId=156819)(http://go.microsoft.com/fwlink/?LinkId=156819)。  
  
## <a name="behavior-of-biztalk-host-instances-during-sql-server-failover"></a>SQL Server 容錯移轉期間的 BizTalk 主控件執行個體的行為  
 如需有關行為 BizTalk 主控件執行個體的 SQL Server 容錯移轉期間，請參閱[行為的 BizTalk Server 主控件執行個體在 SQL Server 容錯移轉期間](http://go.microsoft.com/fwlink/?LinkId=151287)(http://go.microsoft.com/fwlink/?LinkId=151287)。  
  
## <a name="using-sql-server-database-mirroring"></a>使用 SQL Server 資料庫鏡像  
 如需使用相對於 BizTalk Server 資料庫叢集的 SQL Server 資料庫鏡像的詳細資訊，請參閱[使用 SQL Server 資料庫鏡像或磁碟區陰影複製服務](http://go.microsoft.com/fwlink/?LinkId=151288)(http://go.microsoft.com/fwlink/?LinkId = 151288) 在 BizTalk Server 說明。  
  
## <a name="see-also"></a>另請參閱  
 [向外延展 BizTalk Server 資料庫](../technical-guides/scaling-out-the-biztalk-server-databases.md)