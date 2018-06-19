---
title: 叢集資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b68bc3f-c0c4-4050-8ca3-df6dd1927637
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e978c66f903049e566c25f9baf727b6621cbbf2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009471"
---
# <a name="clustering-the-biztalk-server-databases"></a>叢集 BizTalk Server 資料庫
若 BizTalk Server 資料庫變成無法使用，則 BizTalk Server 環境將無法正確運作。 若要提供高可用性，您可以為 BizTalk Server 資料庫建立 Microsoft SQL Server 叢集，如下圖所示。  
  
 ![BizTalk Server 資料庫層](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 若要為 BizTalk Server 資料庫建立高度可用的解決方案，您必須擁有至少兩部執行 SQL Server 的電腦以及在叢集中的共用磁碟陣列。  
  
## <a name="clustering-options"></a>叢集選項  
 為您的企業需求決定 BizTalk Server 資料庫的最佳叢集組態。 以下是一串選項：  
  
-   **主動/被動**。 BizTalk Server 資料庫的高可用性通常包含兩個或多個設定為主動/被動伺服器叢集組態的資料庫電腦。 這些電腦會共用一般磁碟資源 (例如 RAID 1 + 0 SCSI 磁碟陣列或儲存區域網路)，並使用 Windows 叢集提供備份備援和容錯功能。  
  
-   **主動/主動**。 Windows 叢集和 SQL Server 可讓您執行 SQL Server 以主動/主動模式叢集的每個節點其中是 「 作用中 」 且正在執行一個以上的 SQL Server 執行個體。 比方說，這樣可讓您有另一個節點上的一個節點和所有其他 BizTalk Server 資料庫上的 MessageBox 資料庫。 這可讓您以最大化叢集硬體的使用方式，但應該小心使用主動/主動 SQL Server 設定。  
  
     可以每個節點同時處理負載的所有 SQL Server 執行個體期間 SQL Server 叢集節點容錯移轉狀況？ 有足夠的 CPU 資源嗎？ 是否有足夠的記憶體？ 網路頻寬呢？ 如何磁碟 I/O 競爭？  
  
     這些只是部分必須回答才能判斷是否適合您的 BizTalk 應用程式的主動/主動 SQL Server 叢集的問題。 確定有一個節點無法處理所有的 SQL Server 執行個體在容錯移轉案例中，如果另一個方法是使用主動/主動/被動叢集。  
  
-   **主動/主動/被動**。 執行階段程序會寫入 BizTalk 管理資料庫、MessageBox 資料庫、追蹤 Analysis Services 資料庫、BAM 分析資料庫、BAM 星狀結構描述資料庫、BAM 主要匯入資料庫以及 BAM 封存資料庫。 因此，若發生嚴重損毀，這些資料庫就顯得特別重要，而且在決定要叢集哪些資料庫時必須有較高的優先順序。 只有使用者或工具會寫入其他資料庫。 MessageBox 資料庫中，您可以考慮主動/主動/被動或主動/主動/主動/被動組態，以減少所需的硬體。  
  
> [!NOTE]  
>  SQL Server Standard Edition 支援 2 個節點的容錯移轉叢集。 如果您決定使用 SQL Server 上的主動/主動/被動組態，您必須使用 Enterprise Edition。  
  
## <a name="procedures-for-clustering-the-databases"></a>叢集資料庫的程序  
 請確定您符合下列必要條件，再啟動叢集 BizTalk Server 資料庫。  
  
-   當您為 BizTalk Server 環境建立網域群組時，您必須建立全域網域帳戶。  
  
-   安裝及設定 BizTalk Server 之前，請設定 SQL Server 叢集。 請參閱[Windows Server 容錯移轉叢集 (WSFC) 與 SQL Server](https://docs.microsoft.com/sql/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server)或[Alwayson 容錯移轉叢集執行個體 (SQL Server)](https://docs.microsoft.com/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server)。  
  
-   若您也要叢集主要密碼伺服器，請先設定該伺服器。 請參閱[主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)。  
  
#### <a name="run-biztalk-configuration"></a>執行 BizTalk 組態  
  
1.  在執行階段伺服器上安裝 BizTalk Server。  
  
2. 開啟 [BizTalk Server 組態]。  
  
3.  若要套用自訂組態，請參閱[匯入和匯出 BizTalk Server 組態](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)。 若要指定 SQL Server 叢集的 BizTalk Server 資料庫輸入中的 SQL Server 叢集的名稱**資料庫**的組態對話方塊。  
  
4.  完成 BizTalk Server 組態使用[自訂組態](../install-and-config-guides/configure-biztalk-server.md)。
  
 如需叢集化 BizTalk Server 資料庫的詳細資訊，請參閱[改善在 BizTalk Server 中使用 Windows Server 2008 容錯移轉叢集或 Windows Server 2003 伺服器叢集的容錯功能](https://www.microsoft.com/download/details.aspx?id=2290)。  
  
## <a name="behavior-of-biztalk-host-instances-during-sql-server-failover"></a>SQL Server 容錯移轉期間的 BizTalk 主控件執行個體的行為  
 如需有關行為 BizTalk 主控件執行個體的 SQL Server 容錯移轉期間，請參閱[行為的 BizTalk Server 主控件執行個體在 SQL Server 容錯移轉期間](../core/behavior-of-biztalk-server-host-instances-during-sql-server-failover.md)。  
  
## <a name="using-sql-server-database-mirroring"></a>使用 SQL Server 資料庫鏡像  
 如需使用相對於 BizTalk Server 資料庫叢集的 SQL Server 資料庫鏡像的詳細資訊，請參閱[SQL Server 資料庫鏡像磁碟區陰影複製服務和 AlwaysOn](../core/sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson.md)。  
  
## <a name="see-also"></a>請參閱  
 [向外擴充 BizTalk Server 資料庫](../technical-guides/scaling-out-the-biztalk-server-databases.md)