---
title: 建立高可用性的 BizTalk Server 環境 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, high availability
- architecture, databases
- databases, architecture
- performance
- hosts, multiple
- hosts, architecture
- architecture, hosts
- databases, clustering
- high availability, designing
- BizTalk Server, architecture
- installation, planning
- clustering, databases
- installation, availability
ms.assetid: 758eb3bd-a25b-4863-a4ca-d7a1635f7542
caps.latest.revision: 54
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0db43b53e9229747172a203d3c7788997ecedbfb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981887"
---
# <a name="creating-a-highly-available-biztalk-server-environment"></a>建立高度可用的 BizTalk 伺服器環境
本節說明如何為資料和 Microsoft 中的通訊提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]整合不同的系統和應用程式時。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 分開處理資料，讓您以解決可用性問題擴充資料庫和裝載獨立的主機中的資料。  
  
## <a name="demonstrating-high-availability"></a>顯示高可用性  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的高可用性著重於復原可能中斷 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署可用性的功能性元件。  
  
 為了顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的高可用性，您必須套用失敗並評量產品在復原方面的有效性。 當有錯誤或失敗發生時，高度可用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署可以讓外部應用程式和系統幾乎感覺不到任何異狀，並且讓所有的服務能夠在最少中斷的情況下繼續正確運作。  
  
## <a name="designing-for-high-availability"></a>為高可用性所設計  
 設計[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供高可用性的部署牽涉到實作應用程式整合 」 或 「 商務程序整合案例中每個功能元件的備援機制。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在概念上區隔資料，與處理資料的主機，可簡化這些案例的實作。 因此，為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供高可用性，需要執行多個主控件執行個體並叢集 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫，如下所示：  
  
- **為 BizTalk 主控件的架構**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您分開主機並執行多個主控件執行個體，以提供高可用性的索引鍵的函式，例如接收訊息、 處理協調流程和傳送訊息。 這些主控件不需要任何其他叢集或負載平衡機制，因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會透過主控件執行個體在多部電腦之間自動分散工作負載。 不過，執行 HTTP 與 SOAP 配接器的接收處理常式之主控件需要負載平衡機制，例如「網路負載平衡」(NLB) 以提供高可用性。  
  
- **BizTalk Server 資料庫架構**的高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫通常包含兩個或多個設定為主動/被動伺服器叢集組態的資料庫電腦。 這些電腦可共用一般磁碟資源 (例如，RAID5 SCSI 磁碟陣列或儲存區域網路)，並使用 Windows 叢集提供備份備援和容錯。  
  
> [!NOTE]
>  高度可用的環境實際上就是多個電腦的環境。 在多個電腦的環境中設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，必須使用網域使用者群組和帳戶。  
  
 因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是建置在 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 或 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 與 Microsoft SQL Server 2008 上，請確定您在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的主控件之前，先將這些產品部署為具有高可用性。 以下連結包括為這些基礎產品提供高可用性的資訊：  
  
- **高度可用性 — 永遠在技術**，網址[ http://go.microsoft.com/fwlink/?LinkId=130376 ](http://go.microsoft.com/fwlink/?LinkId=130376)。  
  
   此白皮書描述 SQL Server 2008 提供的高度可用性功能。  
  
- **高可用性解決方案概觀**，網址[ http://go.microsoft.com/fwlink/?LinkId=130377 ](http://go.microsoft.com/fwlink/?LinkId=130377)。  
  
   介紹幾個改善伺服器或資料庫可用性的 SQL Server 2008 高可用性解決方案。  
  
- **Windows 部署服務逐步指南 》**，網址[ http://go.microsoft.com/fwlink/?LinkId=130379 ](http://go.microsoft.com/fwlink/?LinkId=130379)。  
  
   包含如何使用 Windows Server 2008 中的 Windows 部署服務角色的逐步指引。  
  
- **Windows Server 2003 Deployment Kit: Planning Server Deployments**，網址[ http://go.microsoft.com/fwlink/?LinkId=24433 ](http://go.microsoft.com/fwlink/?LinkId=24433)。  
  
   本書提供規劃伺服器儲存的資訊，以及設計和部署檔案伺服器、列印伺服器以及中大型組織的終端機伺服器之資訊。  
  
- **增加 BizTalk Server 的可用性**，網址[ http://go.microsoft.com/fwlink/?LinkId=130457 ](http://go.microsoft.com/fwlink/?LinkId=130457)。  
  
   一節[BizTalk Server 作業指南](http://go.microsoft.com/fwlink/?LinkId=130458)描述您可以增加的可用性方式您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md)  
  
-   [為 BizTalk Server 資料庫提供高可用性](../core/providing-high-availability-for-biztalk-server-databases.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md)   
 [使用 Windows Server 叢集為 BizTalk Server Hosts2 提供高可用性](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)