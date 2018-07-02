---
title: 叢集主要密碼伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14aa3622-8462-4ed9-abde-40090d4f96ff
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c19702cfa7179399ee89f6799b65f1d2cec27a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977295"
---
# <a name="clustering-the-master-secret-server"></a>叢集主要密碼伺服器
BizTalk Server 應用程式服務會維護硬式編碼相依性會隨企業單一登入 (SSO) 服務時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 SSO 服務必須能夠與啟動主要密碼伺服器進行通訊。 我們建議您在主要密碼伺服器提供容錯功能的主要密碼伺服器上叢集化 SSO 服務。 如需詳細資訊，請參閱 <<c0> [ 高可用性 SSO 安裝選項](http://go.microsoft.com/fwlink/?LinkId=156838)(<http://go.microsoft.com/fwlink/?LinkId=156838>) 在 BizTalk Server 說明中。  
  
## <a name="preparing-for-clustering-the-master-secret-server"></a>正在準備叢集主要密碼伺服器  
  
### <a name="deciding-whether-to-use-a-dedicated-cluster-or-the-sql-server-cluster"></a>決定是否要使用專用的叢集或 SQL Server 叢集  
 叢集硬體很昂貴。 若要減少高度可用的方案的硬體資源，可以將主要密碼伺服器新增為叢集資源，您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫叢集。 如果您使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫叢集，建議您不要讓主要密碼伺服器與 MessageBox 資料庫相同的作用中節點上。 MessageBox 資料庫會比其他資料庫通常較忙碌。 即使主要密碼伺服器不會消耗許多硬體資源，最好是將它移至不同的使用中叢集節點中，從 [作用中的 MessageBox 資料庫] 節點。  
  
### <a name="clustering-the-sso-database"></a>叢集 SSO 資料庫  
 主要密碼伺服器會取決於 SSO 資料庫。 若要建置高可用性 SSO，您必須叢集化 SSO 資料庫。 如需叢集化 BizTalk 資料庫的詳細資訊，請參閱[叢集 BizTalk Server 資料庫 2](../technical-guides/clustering-the-biztalk-server-databases2.md)。  
  
### <a name="creating-domain-groups-and-accounts"></a>建立網域群組和帳戶  
 您需要設定下列網域群組和帳戶，再叢集主要密碼伺服器：  
  
-   以 SSO 系統管理員和 SSO 分支機構系統管理員的名稱建立網域群組。 若要建立叢集 「 企業單一登入 」 服務執行個體，您必須建立 「 SSO 系統管理員 」 和 「 SSO 分支機構系統管理員群組做為網域群組。  
  
-   建立或指定的 SSO 系統管理員網域群組成員的網域帳戶。 每個節點上的「企業單一登入」服務會設定為以此網域帳戶的身分登入。 這個帳戶必須在叢集中的每個節點上的 「 以服務方式登入 」 權限。 此帳戶必須也授與完全控制叢集存取權。  
  
## <a name="clustering-the-master-secret-server"></a>叢集主要密碼伺服器  
 以下是供叢集化主要密碼伺服器的基本步驟：  
  
1. 安裝及設定企業單一登入叢集節點上。  
  
2. 建立叢集化 「 企業單一登入資源和相依的資源。  
  
3. 還原第二個叢集節點上的主要密碼。 如果您將主要密碼伺服器移到叢集時，您必須還原主要祕密，第一個叢集節點上。  
  
4. 將包含 SSO 服務、 線上叢集群組。  
  
5. 更新 「 管理 」 資料庫中的主要祕密名稱。  
  
   如需叢集主要密碼伺服器的詳細步驟，請參閱[如何叢集化主要密碼伺服器](http://go.microsoft.com/fwlink/?LinkId=156839)(<http://go.microsoft.com/fwlink/?LinkId=156839>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
## <a name="see-also"></a>另請參閱  
 [手動指定新的主要密碼伺服器](../technical-guides/designating-a-new-master-secret-server-manually.md)