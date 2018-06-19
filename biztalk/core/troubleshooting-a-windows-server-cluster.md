---
title: 疑難排解 Windows Server 叢集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 283cf4cd-ce40-48b7-8549-9ab17d7d2c34
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da1159bafc42f6cfbf47621e3b846764e50e5267
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279958"
---
# <a name="troubleshooting-a-windows-server-cluster"></a>疑難排解 Windows Server 叢集
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援 Windows Server 叢集的使用，以提供主控件叢集的支援、提供企業單一登入 (SSO) 主要密碼的高可用性，並提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的高可用性。 本主題提供一些在 Windows Server 叢集環境中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的一般指導方針，並討論在 Windows Server 叢集環境中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時可能會發生的一些已知問題。  
  
## <a name="general-guidelines"></a>一般指導方針  
 請依照這些一般指導方針來最大化 Windows Server 叢集的產能，並且疑難排解可能會影響到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 Windows Server 叢集問題。  
  
1.  完成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]證明概念與 Windows Server 叢集虛擬的伺服器環境中的工作。  
  
     **適用於 Windows Server 2008 HYPER-V 角色可用來建立虛擬的伺服器環境。**  
  
    -   關於 Windows Server 2008 HYPER-V 的詳細資訊，請參閱 「 虛擬化與合併 >，網址[http://go.microsoft.com/fwlink/?LinkID=121187](http://go.microsoft.com/fwlink/?LinkID=121187)。  
  
    -   如需有關優點的運用提供與 HYPER-V 虛擬化技術的深入資訊，請參閱 「 進階虛擬化優點的 Windows Server 2008 版本的 Enterprise 」 可以從下載技術白皮書[http://go.microsoft.com/fwlink/?LinkId=123530](http://go.microsoft.com/fwlink/?LinkId=123530)。  
  
    -   使用 HYPER-V 建立的 Windows Server 2008 叢集的步驟時使用[http://go.microsoft.com/fwlink/?LinkId=129680](http://go.microsoft.com/fwlink/?LinkId=129680)。  
  
     執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]證明概念與 Windows Server 叢集虛擬的伺服器環境中的工作，可提供絕佳的彈性，並使用遠少於比所需的 Windows Server 叢集的硬體資源。 如果使用這項做法，請對在主機電腦上同時執行的每部虛擬機器，都配置至少 512 MB 的記憶體，並對主機作業系統配置額外的 512 MB 記憶體。 例如，針對使用五部虛擬機器之 Windows Server 叢集 (兩個 BizTalk Server 叢集節點、兩個 Microsoft SQL Server 叢集節點和一個網域控制站) 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案，您應該規劃將 3 GB 的記憶體安裝在主機電腦上。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]概念證明環境需要超過 2 GB 的記憶體，請考慮 （HYPER-V 角色所需） 在主機電腦上安裝 64 位元版本的 Windows，以確保所有已安裝的記憶體是由主機作業系統可存取。  
  
## <a name="troubleshooting-resources"></a>疑難排解資源  
 **疑難排解 Windows Server 2008 容錯移轉叢集的資源**  
  
-   檢閱[容錯移轉叢集驗證及疑難排解 Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=129729) Microsoft TechNet 網站上的 TechNet 網路廣播。 這個網路廣播說明如何疑難排解容錯移轉叢集驗證及疑難排解 Windows Server 2008。  
  
-   如需有關如何分析問題與 Windows Server 2008 容錯移轉叢集的詳細資訊，請檢閱本主題[檢視事件和記錄檔，容錯移轉叢集](http://go.microsoft.com/fwlink/?LinkId=129730)Microsoft TechNet 網站上。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="any-attempt-to-bring-a-clustered-msdtc-resource-online-fails-which-causes-dependent-biztalk-server-services-to-fail"></a>嘗試將叢集的 MSDTC 資源連到線上結果失敗，進而造成相依的 BizTalk Server 服務失敗  
  
##### <a name="problem"></a>問題  
 叢集的分散式交易協調器 (MSDTC) 資源無法上線**上線**選項在叢集系統管理員，這會導致[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]依賴 MSDTC 的執行階段作業失敗的交易支援。  
  
##### <a name="cause"></a>原因  
 叢集 MSDTC 資源失敗可能因為下列數種原因而發生：  
  
-   沒有以正確的「磁碟」和「網路名稱」資源相依性設定叢集 MSDTC 資源，或是資源相依性失敗。  
  
-   權限問題阻止叢集 MSDTC 資源啟動。  
  
##### <a name="resolution"></a>解決方案  
 **完成 Windows Server 2008 叢集上的下列步驟：**  
  
-   請依照[檢查清單： Windows Server 2008 容錯移轉叢集中建立 MS DTC 資源](http://go.microsoft.com/fwlink/?LinkId=129677)Windows Server 2008 容錯移轉叢集上建立一或多個叢集的 MSDTC 資源。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)   
 [BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md)   
 [高可用性 SSO 安裝選項](../core/high-availability-sso-installation-options.md)