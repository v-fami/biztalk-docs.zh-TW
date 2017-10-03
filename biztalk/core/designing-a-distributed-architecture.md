---
title: "設計分散式的架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clustering, SQL Servers
- SQL Server, clustering
ms.assetid: 8a8f1710-4d53-42bf-b5e5-2be3b43813b4
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 156c7107abfd0fd140a5e7b07f06d00eabf7c961
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="designing-a-distributed-architecture"></a>設計分散式架構
完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 主題中所提供的架構[大型分散式架構](../core/large-distributed-architecture.md)解決了許多 BizTalk 環境是易受攻擊的潛在安全性威脅。 在設計您的架構時，安全性在優先權清單上應該有高優先權，但是在分散式環境中還有其他考量，像是高可用性、延展性及效能。 本節提供設計 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 架構時您可以考量的其他選項。  
  
## <a name="domains"></a>定義域  
 若公司大多數是執行外部式網際網路的通訊，則可以從公司網域移除內部網路服務。 相反地，若您使用 BizTalk Server 來連接透過內部網路連線的其他應用程式或商務夥伴，則可以移除周邊網路。 如果您的公司網際網路和內部網路對向通訊的夥伴數目很少，您可以考慮將內部網路服務與周邊網路結合。  
  
 若您要使資料網域中處理伺服器與 SQL Server 之間的通訊延遲降到最低，而且內部網路中像是網路探查、竄改封包，以及主控件安全防護等安全性問題不是考量重點時，則可以移除處理與資料網域之間的防火牆，並且合併這些網域。 建議您使用「網際網路通訊協定安全性」(IPSec) 或「安全通訊端層」(SSL) 來保護伺服器之間傳輸的資料。  
  
## <a name="sql-server-clustering"></a>SQL Server 叢集  
 雖然本節並未詳細描述，但是我們仍強烈建議將您的資料庫組成叢集，以獲得容錯移轉保護。 如需有關 SQL Server 2008 容錯移轉叢集的詳細資訊，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkId=131016](http://go.microsoft.com/fwlink/?LinkId=131016)。  
  
## <a name="messagebox-database"></a>MessageBox 資料庫  
 依據貴公司的訊息傳輸量需求，可能需要新增 (或移除) MessageBox 資料庫。 如需多個 messagebox 的詳細資訊，請參閱[Scaled-Out 資料庫](../core/scaled-out-databases.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設計安全架構](../core/designing-a-secure-architecture.md)   
 [高可用性規劃](../core/planning-for-high-availability3.md)   
 [持續性效能的規劃](../core/planning-for-sustained-performance.md)   
 [設計 BizTalk Server 的系統架構](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)