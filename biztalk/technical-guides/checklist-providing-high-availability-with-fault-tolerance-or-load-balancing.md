---
title: "檢查清單： 提供高可用性容錯或負載平衡 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c93cfc3-05b2-43ad-b0a9-b7f0d2596113
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72976dba4ed30ad6747d2d6175702110fe9730a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-providing-high-availability-with-fault-tolerance-or-load-balancing"></a>檢查清單： 提供高可用性與容錯或負載平衡
本主題列出您應該先完成設定容錯和/或負載平衡元件的實際執行的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，以提供高可用性。 這些元件的容錯組態可讓系統持續運作的特定元件失敗時。  
  
|步驟|參考|  
|-----------|---------------|  
|建立多個 BizTalk 主控件執行個體，並實作主控件叢集支援這些介面卡需要它。|[BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)|  
|設定高可用性的追蹤主控件。|[BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)|  
|設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上的叢集資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]位於 Windows server 叢集執行個體。|[資料庫的高可用性](../technical-guides/high-availability-for-databases.md)|  
|設定高可用性的追蹤主控件。 請確認至少 N + 1 個主機的執行個體啟用其中 N 是 BizTalk 群組中的 MessageBox 資料庫數目追蹤。|若要啟用追蹤的主機，請選取 **允許主控件追蹤**上**主控件屬性**對話方塊可從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需設定主機內容的詳細資訊，請參閱主題[如何修改主機內容](http://go.microsoft.com/fwlink/?LinkId=154359)(http://go.microsoft.com/fwlink/?LinkId=154359)。|  
|練習定期執行，以確保容錯移轉功能的資料庫容錯移轉。|應該直接指派此的責任，以確保這會對以一致的方式。|  
|請確定有足夠的處理能力和被動叢集節點上的記憶體，若要啟用多個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在容錯移轉案例中同時執行的執行個體。|如果兩個 SQL 執行個體經常會使用超過 50%的個別叢集節點上的資源，然後當兩個執行個體容錯移轉至單一節點，每個執行個體則會造成效能降低的問題。 因此，測試應該執行以確保單一叢集節點都能夠處理負載，直到失敗的節點恢復上線。 如果單一節點無法處理負載的兩個 SQL 執行個體然後考慮新增其他叢集節點，若要實作主動/主動/被動叢集拓撲。|  
|實作存放區域網路 (SAN) 來保存[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 **注意：**的話，請設定 SAN 磁碟使用 RAID 1 + 0 （等量磁碟區鏡像組） 的最大效能和高可用性的拓撲。|在[「 BizTalk Server 資料庫最佳化白皮書"](http://go.microsoft.com/fwlink/?linkid=104427) (http://go.microsoft.com/fwlink/?linkid=104427)，請參閱底下 「 效能微調 」 「 磁碟基礎結構 」 一節。|  
|使用 Windows 叢集來叢集化企業單一登入 (SSO) 主要密碼伺服器。|[主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)**附註：**執行未叢集化 SSO 服務執行的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]除非您叢集化 SSO 與 BizTalk 主控件相同的叢集群組中。 如需有關叢集化 SSO 服務和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相同叢集群組中的主應用程式請參閱[如何叢集 SSO 和 BizTalk 主控件相同的叢集群組中](http://go.microsoft.com/fwlink/?LinkId=154367)(http://go.microsoft.com/fwlink/?LinkId=154367)。|  
|備份企業單一登入 (SSO) 主要密碼。|請參閱[如何備份主要密碼](http://go.microsoft.com/fwlink/?LinkID=151395)(http://go.microsoft.com/fwlink/?LinkID=151395)。|  
|設定網際網路資訊服務 (IIS) Web 伺服器外掛式主控的件執行個體和 BAM 入口網站網頁，才能使用網路負載平衡 (NLB) 或其他負載平衡裝置提供高可用性。|**適用於 Windows Server 2008**： 請參閱[網路負載平衡部署指南 》](http://go.microsoft.com/fwlink/?LinkId=153139) (http://go.microsoft.com/fwlink/?LinkId=153139)。|  
  
## <a name="see-also"></a>另請參閱  
 [提供高可用性](../technical-guides/providing-high-availability.md)