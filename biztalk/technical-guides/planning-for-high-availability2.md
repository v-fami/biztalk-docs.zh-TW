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
ms.openlocfilehash: f9b5ff05391eed424e7b910296cc5aa801f8cab1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-high-availability"></a>高可用性的規劃
BizTalk Server 的高可用性著重於復原可能中斷 BizTalk Server 部署中的可用性的功能性元件。  
  
 為了示範如何在 BizTalk Server 的高可用性，您有會導致失敗和量值的修復的產品的效能。 高可用性的 BizTalk Server 部署可以讓錯誤和失敗外部應用程式和系統，並可確保所有的服務繼續正常的干擾。  
  
 設計可提供高可用性的 BizTalk Server 部署，牽涉到整合應用程式或商務程序整合案例中實作的每個功能元件的備援性。 BizTalk Server 可簡化這些案例的實作在概念上分隔資料從*主機*所處理的資料。 A*主機*是 BizTalk 的邏輯容器項目，例如協調流程、 傳送處理常式和接收處理常式。 您建立*主控件執行個體*並將它們指派給主機。 主控件執行個體是特定伺服器上主控件的實體表示法。 它是 BizTalk Server 服務程序呼叫 BTSNTSvc.exe 或另一個處理序，例如，在 IIS 處理序。 因此，BizTalk Server 涉及執行多個，提供高可用性*主控件執行個體*和叢集 BizTalk Server 資料庫，如下所示：  
  
-   **BizTalk 主控件的架構**。 BizTalk Server 可讓您將主控件分開並執行以提供高可用性的索引鍵的函式，例如接收訊息、 處理協調流程和傳送訊息的多個主控件執行個體。 這些主機不需要因為 BizTalk Server 會自動分散工作負載，透過主控件執行個體的多部電腦上任何其他叢集或負載平衡機制。 不過，裝載 HTTP 與 SOAP 配接器需要負載平衡機制，例如網路負載平衡 (NLB) 以提供高可用性，並執行 ftp 接收處理常式的主控件、 MSMQ、 POP3、 SQL 和 SAP 需要執行的接收處理常式叢集以提供高可用性機制。  
  
    > [!NOTE]  
    >  您必須一律叢集 SAP 接收配接器，以容納兩階段認可案例。  
  
-   **BizTalk Server 資料庫的架構**。 設定為主動/被動伺服器叢集組態的兩個或多個 SQL Server 資料庫電腦通常包含 BizTalk Server 資料庫的高可用性組態。 這些電腦會共用一般磁碟資源 (例如 RAID 1 + 0 SCSI 磁碟陣列或存放區域網路)，並使用 Windows 容錯移轉叢集提供備份備援和容錯功能。  
  
 主要密碼伺服器的另一個重要的高可用性 BizTalk 功能元件。 BizTalk Server 依賴此服務，以取得加密金鑰。  
  
 本節提供如何處理每個類別中的高可用性的相關資訊。 因為 BizTalk Server 高可用性解決方案建置在 Windows 和 SQL Server，請確定具備高可用性部署這些產品，然後再設定 BizTalk Server 的主機。 以下連結包括為這些基礎產品提供高可用性的資訊：  
  
-   **高可用性解決方案 (SQL Server)] (https://docs.microsoft.com/sql/sql-server/failover-clusters/high-availability-solutions-sql-server)**  
  
-   **[容錯移轉叢集的 Windows Server](https://docs.microsoft.com/windows-server/failover-clustering/failover-clustering-overview)**
  
## <a name="understanding-the-impact-of-a-component-failure"></a>了解元件故障的影響  
 下表列出的元件和 BizTalk Server 環境，以及對 BizTalk Server 環境的影響的相依性，如果元件或相依性失敗。 決定是否要加入叢集的元件或相依性時，您應該考慮可能失敗的範圍。  
  
|元件或相依性|失敗的範圍|  
|-----------------------------|----------------------|  
|SQL Server|全系統。 如果 SQL Server 無法再 BizTalk Server 將無法處理文件。|  
|主要密碼伺服器|全系統。 如果主要密碼伺服器失敗然後 BizTalk Server 將無法處理文件。 <br/>**注意：**如果主要密碼伺服器失敗，BizTalk 群組中的每個 BizTalk server 將會繼續使用快取的記憶體中複本的主要密碼，直到重新啟動 BizTalk server 上的企業 SSO 服務。 企業 SSO 服務重新啟動 BizTalk 伺服器上，然後從記憶體釋放主要密碼的快取的副本和 BizTalk server 必須能夠連絡主要密碼伺服器取得主要密碼的另一個複本。 並不需要重新啟動 BizTalk 伺服器上的企業單一登入服務群組中如果主要密碼伺服器失敗，而且您想要繼續處理文件的 BizTalk 伺服器。|  
|MSDTC|伺服器。 如果 MSDTC 失敗需要交易支援，伺服器上的任何元件將會失敗。 <br/>**注意：**如果 SQL server 或主要密碼伺服器上的 MSDTC 失敗 SQL Server 和主要密碼伺服器有相依於 MSDTC 交易支援，因為失敗的範圍將會變成全系統。 在執行階段作業期間與 SQL Server 和主要密碼伺服器進行通訊時，BizTalk Server 需要交易支援。|  
|BizTalk 主控件執行個體|伺服器。 在 BizTalk 主控件執行個體中的任何元件將無法參與文件處理，如果主控件執行個體失敗。|  
|Microsoft Message Queuing (MSMQ)|伺服器。 如果 MSMQ 失敗然後相依於 MSMQ 服務，例如 MSMQ 配接器，任何文件處理就會停止在伺服器上。|  
|檔案系統|伺服器。 如果檔案系統接著任何文件處理失敗，取決於檔案系統中，例如 File 配接器，就會停止在伺服器上。|  
  
 若要能管理高可用性的 BizTalk Server 系統更容易，您必須充分了解 BizTalk 堆疊： Windows Server、 DC （DNS、 DHCP）、 BizTalk Server、 SQL Server、 IIS 伺服器、 檔案伺服器、 MSMQ 伺服器、 外部應用程式。 本節著重於 BizTalk Server 和相依的 SQL Server 電腦的高可用性。  
  
## <a name="biztalk-server-high-availability-examples"></a>BizTalk Server 高可用性的範例  
 如範例的案例中 Microsoft BizTalk Server 中透過向外擴充的主控件層提供高可用性，請參閱[BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md)。
  
## <a name="see-also"></a>請參閱  
 [BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [資料庫的高可用性](../technical-guides/high-availability-for-databases.md)   
 [主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [檢查清單：利用災害復原功能提高可用性](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)