---
title: "叢集主要密碼伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14aa3622-8462-4ed9-abde-40090d4f96ff
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674cbf64e11817c951d3841ebdc9f6ee979c0e8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="clustering-the-master-secret-server"></a>叢集主要密碼伺服器
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]應用程式服務會維護硬式編碼相依性會隨企業單一登入 (SSO) 服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 SSO 服務必須能夠與啟動主要密碼伺服器進行通訊。 我們建議您在主要密碼伺服器提供容錯功能的主要密碼伺服器上叢集化 SSO 服務。 如需詳細資訊，請參閱[高可用性 SSO 安裝選項](http://go.microsoft.com/fwlink/?LinkId=156838)(http://go.microsoft.com/fwlink/?LinkId=156838) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]幫助。  
  
## <a name="preparing-for-clustering-the-master-secret-server"></a>正在準備叢集主要密碼伺服器  
  
### <a name="deciding-whether-to-use-a-dedicated-cluster-or-the-sql-server-cluster"></a>決定是否要使用專用的叢集或 SQL Server 叢集  
 叢集硬體是高度耗費資源。 若要減少高度可用的方案的硬體資源，可將主要密碼伺服器新增為叢集資源，您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫叢集。 如果您使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫叢集上，建議您不要讓主要密碼伺服器上的 MessageBox 資料庫相同的作用中節點。 通常與其他資料庫忙碌 MessageBox 資料庫。 即使主要密碼伺服器不會使用許多硬體資源，最好是將它移至不同的使用中叢集節點中，從使用中的 MessageBox 資料庫節點。  
  
### <a name="clustering-the-sso-database"></a>叢集 SSO 資料庫  
 主要密碼伺服器的 SSO 資料庫而定。 若要建置高可用性 SSO，您必須叢集化 SSO 資料庫。 如需叢集化 BizTalk 資料庫的詳細資訊，請參閱[叢集 BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md)。  
  
### <a name="creating-domain-groups-and-accounts"></a>建立網域群組和帳戶  
 您需要設定下列網域群組和帳戶，再叢集主要密碼伺服器：  
  
-   SSO 系統管理員和 SSO 分支機構系統管理員的名稱建立網域群組。 若要建立企業單一登入服務的叢集執行個體，您必須建立 「 SSO 系統管理員 」 和 「 SSO 分支機構系統管理員群組做為網域群組。  
  
-   建立或指定的網域帳戶是 SSO 系統管理員的網域群組的成員。 每個節點上的「企業單一登入」服務會設定為以此網域帳戶的身分登入。 此帳戶必須具有 「 以服務方式登入 」 權限，叢集中的每個節點上。 此帳戶必須也授與完全控制叢集存取權。  
  
## <a name="clustering-the-master-secret-server"></a>叢集主要密碼伺服器  
 以下是供叢集化主要密碼伺服器的基本步驟：  
  
1.  安裝和設定叢集節點上的企業單一登入。  
  
2.  建立叢集化 「 企業單一登入資源和相依的資源。  
  
3.  還原第二個叢集節點上的主要密碼。 如果您將主要密碼伺服器移至叢集時，您必須還原第一個叢集節點上的主要密碼。  
  
4.  將包含 SSO 服務，線上叢集群組。  
  
5.  更新管理資料庫中的主要密碼的名稱。  
  
 如需叢集主要密碼伺服器的詳細步驟，請參閱[如何叢集化主要密碼伺服器](http://go.microsoft.com/fwlink/?LinkId=156839)(http://go.microsoft.com/fwlink/?LinkId=156839) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
## <a name="see-also"></a>另請參閱  
 [手動指定新的主要密碼伺服器](../technical-guides/designating-a-new-master-secret-server-manually.md)