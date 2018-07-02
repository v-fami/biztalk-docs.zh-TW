---
title: 規劃高 Availability2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65271fd5-5294-406f-87f8-3aa394c235a2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac94e56775badc3aa610505ad1fb441f85e9262e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988503"
---
# <a name="planning-for-high-availability"></a>高可用性的規劃
BizTalk Server 的高可用性著重於復原可能中斷 BizTalk Server 部署中的可用性的功能性元件。  
  
 若要示範 BizTalk Server 中的高可用性，您有會導致失敗，並測量 recovery 中的產品的有效性。 高可用性的 BizTalk Server 部署可以讓錯誤和失敗外部應用程式和系統，並確保所有服務會都持續最少中斷的情況下正確運作。  
  
 設計 BizTalk Server 部署，提供高可用性，牽涉到在應用程式整合或商務程序整合案例中實作每個功能元件的備援。 BizTalk Server 會簡化這些案例的實作在概念上分隔的資料*主機*所處理的資料。 A*主機*是 BizTalk 的邏輯容器項目，例如協調流程、 傳送處理常式和接收處理常式。 您建立*主控件執行個體*並將它們指派給主機。 主控件執行個體是特定伺服器上主控件的實體表示法。 它是 BizTalk Server 服務程序呼叫 BTSNTSvc.exe 或另一個處理序，比方說，IIS 處理序。 BizTalk Server 中包含執行多個，因此提供高可用性*主控件執行個體*和叢集 BizTalk Server 資料庫，如下所示：  
  
- **為 BizTalk 主控件的架構**。 BizTalk Server 可讓您分開主機並執行多個主控件執行個體，以提供高可用性的索引鍵的函式，例如接收訊息、 處理協調流程和傳送訊息。 這些主機不需要任何其他叢集或負載平衡機制，因為 BizTalk Server 會自動將工作負載分散在多部電腦透過主控件執行個體。 不過，會裝載 HTTP 與 SOAP 配接器需要負載平衡機制，例如網路負載平衡 (NLB) 以提供高可用性，並執行 FTP 接收處理常式的主控件、 MSMQ、 POP3、 SQL 和 SAP 需要執行的接收處理常式叢集提供高可用性機制。  
  
  > [!NOTE]  
  >  您一律必須叢集化 SAP 接收配接器，以容納兩階段交易認可案例。  
  
- **BizTalk Server 資料庫的架構**。 BizTalk Server 資料庫的高可用性組態通常包含設定為主動/被動伺服器叢集組態的兩個或多個 SQL Server 資料庫電腦。 這些電腦會共用一般磁碟資源 (例如 RAID 1 + 0 SCSI 磁碟陣列或存放區域網路) 並使用 Windows 容錯移轉叢集提供備份備援和容錯。  
  
  另一個 BizTalk 功能元件，是高可用性的關鍵是主要密碼伺服器。 BizTalk Server 依賴這項服務取得加密金鑰。  
  
  本節提供如何解決這些類別中的高可用性的相關資訊。 因為 BizTalk Server 高可用性解決方案建置在 Windows 和 SQL Server，請確定具有高可用性部署這些產品，然後再設定 BizTalk Server 的主機。 以下連結包括為這些基礎產品提供高可用性的資訊：  
  
- **高可用性解決方案 (SQL Server)] (https://docs.microsoft.com/sql/sql-server/failover-clusters/high-availability-solutions-sql-server)**  
  
- **[Windows Server 叢集的容錯移轉](https://docs.microsoft.com/windows-server/failover-clustering/failover-clustering-overview)**
  
## <a name="understanding-the-impact-of-a-component-failure"></a>了解元件失敗的影響  
 下表列出的元件和 BizTalk Server 環境以及對 BizTalk Server 環境的影響的相依性，如果元件或相依性失敗。 決定是否要加入叢集的元件或相依性時，您應該考慮可能失敗的範圍。  
  
|元件或相依性|失敗的範圍|  
|-----------------------------|----------------------|  
|[SQL Server]|全系統。 如果 SQL Server 無法然後 BizTalk Server 將無法處理文件。|  
|主要密碼伺服器|全系統。 如果主要密碼伺服器失敗然後 BizTalk Server 將無法處理文件。 <br/>**注意：** 如果主要密碼伺服器失敗，BizTalk 群組中的每個 BizTalk server 將繼續使用快取於記憶體中複本的主要密碼，直到重新啟動 BizTalk server 上的企業 SSO 服務。 在 BizTalk 伺服器上重新啟動 「 企業單一登入 」 服務時，然後從記憶體釋放主要祕密的快取的副本，並 BizTalk server 必須能夠連絡以取得主要祕密的另一份主要密碼伺服器。 不重新啟動的企業單一登入服務的 BizTalk server 群組中如果主要密碼伺服器失敗，而且您想要繼續處理文件的 BizTalk server。|  
|MSDTC|伺服器。 如果 MSDTC 失敗需要交易支援的伺服器上的任何元件將會失敗。 <br/>**注意：** SQL 伺服器和主要密碼伺服器是在 MSDTC 交易支援相依項目，因為失敗的範圍會變成全系統的 SQL 伺服器或主要密碼伺服器上的 MSDTC 時。 在執行階段作業期間，SQL Server 與主要密碼伺服器進行通訊時，BizTalk Server 需要交易支援。|  
|BizTalk 主控件執行個體|伺服器。 裝載 BizTalk 主控件執行個體中的任何元件將無法參與文件處理，如果主控件執行個體失敗。|  
|Microsoft Message Queuing (MSMQ)|伺服器。 如果 MSMQ 失敗然後任何相依於 MSMQ 服務，例如 MSMQ 配接器的文件處理就會停止在伺服器上。|  
|檔案系統|伺服器。 如果檔案系統失敗則取決於檔案系統，例如 File 配接器，任何文件處理就會停止在伺服器上。|  
  
 若要能夠更有效地管理高可用性的 BizTalk Server 系統，您必須充分了解 BizTalk 堆疊： Windows Server，DC （DNS、 DHCP）、 BizTalk Server、 SQL Server、 IIS 伺服器、 檔案伺服器、 MSMQ 伺服器、 外部應用程式。 本節著重於 BizTalk Server 和相依的 SQL Server 電腦的高可用性。  
  
## <a name="biztalk-server-high-availability-examples"></a>BizTalk Server 高可用性的範例  
 如需範例案例在 Microsoft BizTalk Server 可透過向外擴充的主機層的高可用性，請參閱[BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md)。
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 主控件的的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [資料庫的高可用性](../technical-guides/high-availability-for-databases.md)   
 [主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [檢查清單：利用災害復原功能提高可用性](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)