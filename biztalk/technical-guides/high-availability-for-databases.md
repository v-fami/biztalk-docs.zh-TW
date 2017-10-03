---
title: "資料庫的高可用性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63813d87-1ce4-4645-bb2a-d55e413fcace
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 415b1bbe86df1b7ee3feaeec13c889dfe2a4a902
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="high-availability-for-databases"></a>資料庫的高可用性
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]高度依賴[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料存放區和資料持續性。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中所有其他元件和主控件在整合不同的商業應用程式的程序中都有特定的角色 (例如，接收、處理或路由訊息)，但是資料庫電腦會擷取此工作並將它保存到磁碟中。 例如，當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收內送訊息時，在其他主控件擷取協調流程處理和傳送的訊息之前，接收主控件會將它保存到 MessageBox 資料庫。 如果您的 BizTalk 方案包含協調流程，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將訊息路由至主控件執行商務程序 （處理主控件），並在協調流程完成之後，將訊息儲存到 MessageBox 資料庫。 傳送主控件接著會從資料庫擷取訊息，再透過適當的傳送配接器將它傳送到外部應用程式。  
  
 若要提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請使用 Windows 叢集來設定兩個或多個執行的電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]建立伺服器叢集。 這個伺服器叢集會為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫提供備援和容錯。 不像載入平衡叢集是以一組電腦一起運作以增加可用性和延展性，伺服器叢集通常包含兩個一組的主動/被動組態的資料庫電腦，如此，其中一部電腦即可為另一部電腦提供備份資源。  
  
 下圖顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫層透過主動/被動伺服器叢集提供高可用性。  
  
 ![BizTalk Server 資料庫層](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 若主動資料庫電腦發生錯誤或失敗，則被動電腦會變成主動並掌控資料庫資源，直到失敗的電腦修復為止。 資料庫服務會容錯移轉將資料連接還原至新的作用中電腦並讓 BizTalk 應用程式繼續運作。  
  
## <a name="biztalk-server-databases"></a>BizTalk Server 資料庫  
 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝多個資料庫中的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 下表顯示一般使用特性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
|資料庫|預設資料庫名稱|使用特性|  
|--------------|---------------------------|---------------------------|  
|管理資料庫|BizTalkMgmtDb|此資料庫控制代碼低使用量讀取和寫入作業。|  
|MessageBox 資料庫|BizTalkMsgBoxDb|此資料庫控制代碼高使用量讀取和寫入作業。|  
|追蹤資料庫|BizTalkDTADb|這個資料庫負責處理可能高使用量寫入作業，您可以設定為要追蹤的資料數量而定，和低使用量讀取作業。|  
|SSO 資料庫|SSODB|此資料庫控制代碼低使用量讀取和寫入作業。|  
|BAM 分析資料庫|BAMAnalysis|這[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫控制代碼可能高使用量的讀取和寫入作業，根據監視執行的層級。|  
|BAM 星狀結構描述資料庫|BAMStarSchema|這[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫控制代碼可能高使用量的讀取和寫入作業，根據監視執行的層級。|  
|BAM 主要匯入資料庫|BAMPrimaryImport|這[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫控制代碼可能高使用量的讀取和寫入作業，根據監視執行的層級。|  
|BAM 封存資料庫|BAMArchive|這[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫控制代碼可能高使用量的讀取和寫入作業，根據監視執行的層級。|  
|規則引擎資料庫|BizTalkRuleEngineDb|這個資料庫會處理潛在的低使用量讀取和寫入作業，除非您更新的規則。|  
|追蹤 Analysis Services 資料庫|BizTalkAnalysisDb|這[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫控制代碼高使用量的讀取和寫入作業。|  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段作業通常會使用前四個的資料庫 （管理資料庫、 MessageBox 資料庫、 追蹤資料庫以及 SSO 資料庫）。 根據這些資料庫上的流量，您可以將它們放在個別執行的電腦上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 取決於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您使用的功能可能會在資料表中有部分或所有其他資料庫。 您可以向外延展，並視需要叢集這些資料庫。  
  
 請確定您遵循良好[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]部署做法，例如每個資料庫使用不同的磁碟。 如需有關[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]部署的最佳作法，請參閱[技術白皮書： 高可用性 — 永遠在技術](http://go.microsoft.com/fwlink/?LinkId=156812)(http://go.microsoft.com/fwlink/?LinkId=156812)。  
  
 如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，建議您執行下列動作：  
  
-   **設定容錯移轉叢集**。 容錯移轉叢集可讓[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]自動切換的執行個體的處理[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]從失敗的伺服器至伺服器可正常運作。  
  
     「BAM 主要匯入」資料庫收集事件資料。 在嚴重損毀的事件中，從上次備份寫入「BAM 主要匯入」資料庫中的資料會遺失。 沒有任何方法來重新產生遺失的事件，因為它是特別重要，您會啟用容錯移轉叢集上 BAM 主要匯入資料庫。  
  
-   **使用 SQL Server RAID 1 + 0 （獨立磁碟備援陣列）**，特別是針對 MessageBox 資料庫和 BAM 主要匯入資料庫。  
  
 如需備份您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[災害復原的最佳作法](../technical-guides/best-practices-for-disaster-recovery.md)。  
  
> [!NOTE]  
>  Microsoft[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]提供一種軟體解決方案，稱為 「 資料庫鏡像增加資料庫的可用機率。 使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫鏡像目前不支援的解決方案，可確保高可用性的 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]因為維護交易一致性的潛在問題的資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
>   
>  如需有關資料庫鏡像和跨資料庫交易中的[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，請參閱[http://go.microsoft.com/fwlink/?LinkId=87977](http://go.microsoft.com/fwlink/?LinkId=87977)。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫應該安裝在[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]應該利用進行災害復原的叢集，以確保高可用性和記錄傳送。  
>   
>  如需記錄傳送的詳細資訊，請參閱[什麼是 BizTalk Server 記錄傳送嗎？](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [叢集 BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md)  
  
-   [向外延展 BizTalk Server 資料庫](../technical-guides/scaling-out-the-biztalk-server-databases.md)  
  
## <a name="see-also"></a>另請參閱  
 [規劃高 Availability2](../technical-guides/planning-for-high-availability2.md)   
 [BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [嚴重損壞修復](../technical-guides/disaster-recovery.md)