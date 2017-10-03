---
title: "規劃高 Availability2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65271fd5-5294-406f-87f8-3aa394c235a2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 310414b094b7175c6b07fc92697b460e6dd2a830
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-high-availability"></a>高可用性的規劃
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的高可用性著重於復原可能中斷 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署可用性的功能性元件。  
  
 若要示範中的高可用性[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，您有會導致失敗，並測量產品效能中復原。 高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署可以讓錯誤和失敗外部應用程式和系統，並確保所有的服務繼續正常的干擾。  
  
 設計[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]提供高可用性部署需要實作應用程式處理序整合整合或商務案例中每個功能元件的複本。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]在概念上分隔的資料可簡化這些案例的實作*主機*所處理的資料。 A*主機*是 BizTalk 的邏輯容器項目，例如協調流程、 傳送處理常式和接收處理常式。 您建立*主控件執行個體*並將它們指派給主機。 主控件執行個體是特定伺服器上主控件的實體表示法。 它可能是[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]BTSNTSvc.exe 或另一個處理序呼叫的服務處理程序，例如，IIS 處理。 因此提供的高可用性[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]牽涉到執行多個*主控件執行個體*和叢集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，如下所示：  
  
-   **BizTalk 主控件的架構**。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]可讓您將主控件分開並執行以提供高可用性的索引鍵的函式，例如接收訊息、 處理協調流程和傳送訊息的多個主控件執行個體。 這些主控件不需要任何其他叢集或負載平衡機制，因為 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 會透過主控件執行個體在多部電腦之間自動分散工作負載。 不過，裝載 HTTP 與 SOAP 配接器需要負載平衡機制，例如網路負載平衡 (NLB) 以提供高可用性，並執行 ftp 接收處理常式的主控件、 MSMQ、 POP3、 SQL 和 SAP 需要執行的接收處理常式叢集以提供高可用性機制。  
  
    > [!NOTE]  
    >  您必須一律叢集 SAP 接收配接器，以容納兩階段認可案例。  
  
-   **BizTalk Server 資料庫的架構**。 高可用性組態[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]資料庫通常包含兩個或多個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫設定為主動/被動伺服器叢集組態中的電腦。 這些電腦會共用一般磁碟資源 (例如 RAID 1 + 0 SCSI 磁碟陣列或存放區域網路)，並使用 Windows 容錯移轉叢集提供備份備援和容錯功能。  
  
 主要密碼伺服器的另一個重要的高可用性 BizTalk 功能元件。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]依賴此服務，以取得加密金鑰。  
  
 本節提供如何處理每個類別中的高可用性的相關資訊。 因為[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]建置高可用性方案[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，請確定具備高可用性部署這些產品，然後再設定主控件[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。 以下連結包括為這些基礎產品提供高可用性的資訊：  
  
-   **技術白皮書： 高可用性 — 永遠在技術**位於[http://go.microsoft.com/fwlink/?LinkId=156812](http://go.microsoft.com/fwlink/?LinkId=156812)。  
  
-   取得在 Windows Server 2008 的問題疑難排解的詳細資訊[Windows Server 2008 部署、 管理和疑難排解頁面](http://go.microsoft.com/fwlink/?LinkId=156813)(http://go.microsoft.com/fwlink/?LinkId=156813)。  
  
-   取得可用性和延展性的詳細資訊，在 Windows Server 2008 中[可用性和延展性](http://go.microsoft.com/fwlink/?LinkId=156814)(http://go.microsoft.com/fwlink/?LinkId=156814)。  
  
-   請參閱**高可用性**區段[Windows Server 2008 R2 文件和白皮書頁面](http://go.microsoft.com/fwlink/?LinkId=157760)(http://go.microsoft.com/fwlink/?LinkId=157760)。  
  
## <a name="understanding-the-impact-of-a-component-failure"></a>了解元件故障的影響  
 下表列出的元件和相依性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境及對影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，如果元件或相依性失敗。 決定是否要加入叢集的元件或相依性時，您應該考慮可能失敗的範圍。  
  
|元件或相依性|失敗的範圍|  
|-----------------------------|----------------------|  
|[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]|全系統。 如果[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]然後失敗[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法處理文件。|  
|主要密碼伺服器|全系統。 如果主要密碼伺服器失敗然後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法處理文件。 **注意：**如果主要密碼伺服器失敗，BizTalk 群組中的每個 BizTalk server 將會繼續使用快取的記憶體中複本的主要密碼，直到重新啟動 BizTalk server 上的企業 SSO 服務。 企業 SSO 服務重新啟動 BizTalk 伺服器上，然後從記憶體釋放主要密碼的快取的副本和 BizTalk server 必須能夠連絡主要密碼伺服器取得主要密碼的另一個複本。 並不需要重新啟動 BizTalk 伺服器上的企業單一登入服務群組中如果主要密碼伺服器失敗，而且您想要繼續處理文件的 BizTalk 伺服器。|  
|MSDTC|伺服器。 如果 MSDTC 失敗需要交易支援，伺服器上的任何元件將會失敗。 **注意：**因為[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和主要密碼伺服器是依存於 MSDTC 交易支援，失敗的範圍將會變成全系統，如果 SQL server 或主要密碼伺服器上的 MSDTC 失敗。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與通訊時，需要交易支援[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和主要密碼伺服器在執行階段作業。|  
|BizTalk 主控件執行個體|伺服器。 在 BizTalk 主控件執行個體中的任何元件將無法參與文件處理，如果主控件執行個體失敗。|  
|Microsoft Message Queuing (MSMQ)|伺服器。 如果 MSMQ 失敗然後相依於 MSMQ 服務，例如 MSMQ 配接器，任何文件處理就會停止在伺服器上。|  
|檔案系統|伺服器。 如果檔案系統接著任何文件處理失敗，取決於檔案系統中，例如 File 配接器，就會停止在伺服器上。|  
  
 若要能夠管理更容易高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統，您必須充分了解 BizTalk 堆疊： [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]，DC （DNS、 DHCP） [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]， [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，IIS 伺服器、 檔案伺服器、 MSMQ 伺服器、 外部應用程式。 本節著重於高可用性的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]及相關[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
## <a name="biztalk-server-high-availability-examples"></a>BizTalk Server 高可用性的範例  
 在 Microsoft 的範例實例的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，透過向外擴充的主控件層提供高可用性，請參閱[BizTalk Server 高可用性實例範例](http://go.microsoft.com/fwlink/?LinkId=156815)(http://go.microsoft.com/fwlink/?LinkId=156815)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [資料庫的高可用性](../technical-guides/high-availability-for-databases.md)   
 [主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)