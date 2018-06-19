---
title: 資料庫的高可用性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63813d87-1ce4-4645-bb2a-d55e413fcace
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24e17afbf9e33f3e12553d7ded5068370d8ca085
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009359"
---
# <a name="high-availability-for-databases"></a>資料庫的高可用性
BizTalk Server 高度依賴 SQL Server 資料存放區和資料持續性。 在 BizTalk Server 中所有其他元件和主控件在整合不同的商業應用程式的程序中都有特定的角色 (例如，接收、處理或路由訊息)，但是資料庫電腦會擷取此工作並將它保存到磁碟中。 例如，當 BizTalk Server 接收內送訊息，接收主控件它保存到 MessageBox 資料庫之前其他主控件擷取協調流程處理和傳送的訊息。 如果您的 BizTalk 方案包含協調流程，BizTalk Server 會將訊息路由的主控件執行商務程序 （處理主控件），並在協調流程完成之後，將訊息儲存到 MessageBox 資料庫。 傳送主控件接著會從資料庫擷取訊息，再透過適當的傳送配接器將它傳送到外部應用程式。  
  
 若要為 BizTalk Server 資料庫提供高可用性，使用 Windows 叢集來設定兩個或多個執行 SQL Server 建立伺服器叢集的電腦。 這個伺服器叢集提供備援和容錯功能，BizTalk Server 資料庫。 不像載入平衡叢集是以一組電腦一起運作以增加可用性和延展性，伺服器叢集通常包含兩個一組的主動/被動組態的資料庫電腦，如此，其中一部電腦即可為另一部電腦提供備份資源。  
  
 下圖顯示 BizTalk Server 資料庫層透過主動/被動伺服器叢集提供高可用性。  
  
 ![BizTalk Server 資料庫層](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 若主動資料庫電腦發生錯誤或失敗，則被動電腦會變成主動並掌控資料庫資源，直到失敗的電腦修復為止。 資料庫服務會容錯移轉將資料連接還原至新的作用中電腦並讓 BizTalk 應用程式繼續運作。  
  
## <a name="biztalk-server-databases"></a>BizTalk Server 資料庫  
 Microsoft BizTalk Server 會在 SQL Server 中安裝數個資料庫。 下表顯示 BizTalk Server 資料庫的一般使用特性。  
  
|資料庫|預設資料庫名稱|使用特性|  
|--------------|---------------------------|---------------------------|  
|管理資料庫|BizTalkMgmtDb|此資料庫控制代碼低使用量讀取和寫入作業。|  
|MessageBox 資料庫|BizTalkMsgBoxDb|此資料庫控制代碼高使用量讀取和寫入作業。|  
|追蹤資料庫|BizTalkDTADb|這個資料庫負責處理可能高使用量寫入作業，您可以設定為要追蹤的資料數量而定，和低使用量讀取作業。|  
|SSO 資料庫|SSODB|此資料庫控制代碼低使用量讀取和寫入作業。|  
|BAM 分析資料庫|BAMAnalysis|此 SQL Server Analysis Services 資料庫處理可能高使用量的讀取和寫入作業，根據監視執行的層級。|  
|BAM 星狀結構描述資料庫|BAMStarSchema|此 SQL Server Analysis Services 資料庫處理可能高使用量的讀取和寫入作業，根據監視執行的層級。|  
|BAM 主要匯入資料庫|BAMPrimaryImport|此 SQL Server Analysis Services 資料庫處理可能高使用量的讀取和寫入作業，根據監視執行的層級。|  
|BAM 封存資料庫|BAMArchive|此 SQL Server Analysis Services 資料庫處理可能高使用量的讀取和寫入作業，根據監視執行的層級。|  
|規則引擎資料庫|BizTalkRuleEngineDb|這個資料庫會處理潛在的低使用量讀取和寫入作業，除非您更新的規則。|  
|追蹤 Analysis Services 資料庫|BizTalkAnalysisDb|此 SQL Server Analysis Services 資料庫高使用量讀取和寫入作業的控制代碼。|  
  
 BizTalk Server 執行階段作業通常會使用前四個的資料庫 （管理資料庫、 MessageBox 資料庫、 追蹤資料庫以及 SSO 資料庫）。 根據這些資料庫上的流量，您可以將它們放在個別執行 SQL Server 的電腦上。 視您所使用的 BizTalk Server 功能而定，您可能有資料表中部分或全部的其他資料庫。 您可以向外延展，並視需要叢集這些資料庫。  
  
 請確定您遵循優良的 SQL Server 部署作法，例如每個資料庫使用不同的磁碟。  
  
 BizTalk Server 資料庫中，我們建議您下列：  
  
-   **設定容錯移轉叢集**。 容錯移轉叢集可讓 SQL Server 會自動切換 SQL server 從失敗的伺服器正常運作的伺服器執行個體處理。  
  
     「BAM 主要匯入」資料庫收集事件資料。 在嚴重損毀的事件中，從上次備份寫入「BAM 主要匯入」資料庫中的資料會遺失。 沒有任何方法來重新產生遺失的事件，因為它是特別重要，您會啟用容錯移轉叢集上 BAM 主要匯入資料庫。  
  
-   **使用 SQL Server RAID 1 + 0 （獨立磁碟備援陣列）**，特別是針對 MessageBox 資料庫和 BAM 主要匯入資料庫。  
  
 如需 BizTalk Server 資料庫備份的詳細資訊，請參閱[災害復原的最佳作法](../technical-guides/best-practices-for-disaster-recovery.md)。  
  
> [!NOTE]  
>  Microsoft SQL Server 提供一種軟體解決方案，稱為 「 資料庫鏡像增加資料庫的可用機率。 使用 SQL Server 資料庫鏡像目前不支援的解決方案，可確保 Microsoft BizTalk Server 資料庫的高可用性，因為維護 BizTalk Server 資料庫中的交易一致性的潛在問題。  
>   
>  如需有關資料庫鏡像和 SQL Server 中的跨資料庫交易的詳細資訊，請參閱[交易的可用性群組和資料庫鏡像](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring)。 BizTalk Server 資料庫應該安裝在 SQL Server 叢集，以確保高可用性和災害復原用途應該利用記錄傳送。  
>   
>  如需記錄傳送的詳細資訊，請參閱[什麼是 BizTalk Server 記錄傳送嗎？](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [叢集 BizTalk Server 資料庫](../technical-guides/clustering-the-biztalk-server-databases2.md)  
  
-   [向外擴充 BizTalk Server 資料庫](../technical-guides/scaling-out-the-biztalk-server-databases.md)  
  
## <a name="see-also"></a>請參閱  
 [高可用性規劃](../technical-guides/planning-for-high-availability2.md)   
 [BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [災害復原](../technical-guides/disaster-recovery.md)