---
title: 規劃您的平台容錯 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- MessageBox database, fault tolerance
- clustering, fault tolerance
- SQL Server RAID
- databases [BAM], fault tolerance
- BizTalk Server, planning
- fault tolerance
- clustering, fail-overs
- planning, fault tolerance
- Primary Import database [BAM]
- BizTalk Server, backing up
- fault tolerance, planning
- planning, BizTalk Server
- Primary Import database [BAM], fault tolerance
- fail-over clustering
ms.assetid: 512ed6b8-db1e-434a-8009-63e952cf5500
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32cb8913ff48ed954e6e57140417966846641f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265022"
---
# <a name="planning-your-platform-for-fault-tolerance"></a>規劃您的平台的容錯功能
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是建立在 Microsoft Windows 與 Microsoft SQL Server 平台上。 BizTalk Server 從嚴重損毀存留或復原的能力有賴於基礎平台的存留或復原的能力。  
  
 對於「商務活動監控」(BAM) 資料庫和 MessageBox 資料庫，建議您執行以下動作：  
  
-   設定 SQL Server Enterprise Edition 中所提供的容錯移轉叢集。 容錯移轉叢集可讓 SQL Server 從失敗的伺服器將 SQL Server 執行個體的處理自動切換至工作伺服器。  
  
     「BAM 主要匯入」資料庫收集事件資料。 在嚴重損毀的事件中，從上次備份寫入「BAM 主要匯入」資料庫中的資料會遺失。 因為不可能重新產生遺失的事件，所以在「BAM 主要匯入」資料庫上啟用容錯移轉叢集顯得特別重要。  
  
-   使用 SQL Server RAID (獨立磁碟冗餘陣列)，特別是針對 MessageBox 資料庫與「BAM 主要匯入」資料庫。  
  
 使用下列資源設計具有容錯功能的 Windows 與 SQL Server 部署。 請用一些時間瞭解硬體與伺服器備援技術，例如叢集和磁碟鏡像，以防止服務中斷和資料遺失。  
  
-   [技術白皮書： 高可用性 — 永遠在技術上](http://go.microsoft.com/fwlink/?LinkId=130376)  
  
     「 高可用性-永遠在線技術 」 白皮書描述 SQL Server 2008 中的可用的高可用性功能。  
  
-   [高可用性解決方案概觀](http://go.microsoft.com/fwlink/?LinkId=130377)  
  
     介紹幾個改善伺服器或資料庫可用性的 SQL Server 2008 高可用性解決方案。  
  
-   [第 15 章-高可用性的選項，SQL Server Resource Kit](http://go.microsoft.com/fwlink/?LinkId=24431)  
  
     《Microsoft SQL Server Resource Kit》涵蓋廣泛的管理和部署規劃區域。 第 15 章涵蓋容錯和修復的規劃。  
  
-   [Windows 部署服務逐步指南](http://go.microsoft.com/fwlink/?LinkId=130379)  
  
     包含如何使用 Windows Server 2008 中的 Windows 部署服務角色的逐步指引。  
  
-   [Windows Server 2003 Deployment Kit: Planning Server Deployments](http://go.microsoft.com/fwlink/?LinkId=24433)。  
  
     本書提供規劃伺服器儲存的資訊，以及設計和部署檔案伺服器、列印伺服器以及中大型組織的終端機伺服器之資訊。  
  
     您也可使用本書中的指導方針來規劃遠端伺服器管理、設計和部署伺服器叢集、以及設計和部署「網路負載平衡叢集」，以最大化伺服器的可用性和擴充性。  
  
## <a name="backing-up-your-platform"></a>備份平台  
 在您設定系統後，請為伺服器準備完整備份，這樣您才可以在發生資料遺失事件時快速還原完全相同的伺服器。  
  
 若要備份平台，請為以下每個技術執行記錄的備份程序：  
  
-   Microsoft Windows Server Standard、Enterprise 或 Datacenter Edition  
  
-   Internet Information Services (IIS)  
  
-   Microsoft SQL Server  
  
-   Windows SharePoint Services (由 Windows SharePoint Services 配接器所使用)。  
  
 請遵循 「 備份 BizTalk Server 」 可在 「 BizTalk Server 作業指南 》 中的建議[檢查清單： 提高可用性與災害復原](http://go.microsoft.com/fwlink/?LinkId=130498)。  
  
 完整地測試備份和還原程序，並將它們放在安全的遠端位置中。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)