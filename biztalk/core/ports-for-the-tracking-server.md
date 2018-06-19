---
title: 追蹤伺服器的連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracking server
- ports, tracking server
ms.assetid: 4b4913a4-7d8d-4fd0-a116-ba868c4ad7da
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 975f5e42c800a6d4ae4015108afa2650b2c7f626
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266350"
---
# <a name="ports-for-the-tracking-server"></a>追蹤伺服器的連接埠
如需保護 BizTalk Server 部署安全的完整資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下表列出您必須為追蹤伺服器設定的連接埠，以存取它們所需的服務。 您需要開啟連接埠的防火牆，視目的地伺服器在架構中的位置而不同。 您必須為輸入與輸出流量開啟這些連接埠。  
  
|服務或應用程式內容|目的地伺服器|目的地服務|通訊埠|通訊協定|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|登入使用者|BizTalk 管理資料庫|SQL Server|1433|TCP|建立和設定 BizTalk 管理資料庫|  
|登入使用者|BizTalk 管理資料庫|DTC|135|TCP|用於更新和擷取資料庫資訊的 SQL Server 交易連線|  
|登入使用者|BizTalk 管理資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|SSO 資料庫|SQL Server|1433|TCP|供 SSO 服務連線到 SSO 資料庫|  
|登入使用者|BAM 主要匯入資料庫|SQL Server|1433|TCP|驗證 BAM 主要匯入資料庫。 追蹤主控件會在執行階段連線到此資料庫。|  
|登入使用者|BAM 星狀結構描述資料庫|SQL Server|1433||更新和擷取資料庫的資訊。 **注意：** 追蹤主控件執行 BizTalk 組態管理員，從這台伺服器建立新的 BizTalk 群組時，才會連接到此資料庫。|  
|登入使用者|BAM 分析資料庫|OLAP|445|TCP|在遠端電腦建立 OLAP 資料檔案 (.mdb)。 **注意：** 追蹤主控件執行 BizTalk 組態管理員，從這台伺服器建立新的 BizTalk 群組時，才會連接到此資料庫。|  
|登入使用者|BAM 分析資料庫|OLAP|2383 (SQL Server 2005 Analysis Services)||若要建立和設定 BAM 分析資料庫**附註：** 追蹤主控件執行 BizTalk 組態管理員，從這台伺服器建立新的 BizTalk 群組時，才會連接到此資料庫。|  
|登入使用者|BAM 分析資料庫|OLAP|2725|TCP|擷取資料以進行分析 （樞紐分析表報表）**附註：** 追蹤主控件執行 BizTalk 組態管理員，從這台伺服器建立新的 BizTalk 群組時，才會連接到此資料庫。|  
|登入使用者|追蹤資料庫|SQL Server|1433|TCP|更新和擷取資料庫的資訊|  
|登入使用者|MessageBox 資料庫|SQL|1433|TCP|更新和擷取資料庫的資訊|  
|登入使用者|MessageBox 資料庫|DTC|135|TCO|SQL Server 交易連線|  
|登入使用者|MessageBox 資料庫|DTC|50000-50200||次要 RPC 連接埠|  
|登入使用者|BAM 封存資料庫|SQL Server|1433|TCP|若要更新，並從資料庫擷取資訊**附註：** 追蹤主控件執行 BizTalk 組態管理員，從這台伺服器建立新的 BizTalk 群組時，才會連接到此資料庫。|  
|SSO 服務帳戶|SSO 資料庫|SQL Server|1433|TCP|更新和擷取資料庫的資訊|  
|SSO 服務帳戶|主要密碼伺服器|主要密碼服務|135|TCP|供 SSO 服務連接到主要密碼伺服器的 SQL Server 交易連線|  
|SSO 服務帳戶|主要密碼伺服器|次要 RPC|50000-50200|TCP|供 SSO 服務連線到主要密碼伺服器的次要 RPC 連接埠|  
  
## <a name="see-also"></a>另請參閱  
 [伺服器命名慣例](../core/server-naming-conventions.md)   
 [訊息與執行個體資料追蹤的安全性考量](../core/security-considerations-for-message-and-instance-data-tracking.md)   
 [具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md)   
 [必要的連接埠，以便讓 BizTalk Server](../core/required-ports-for-biztalk-server.md)   
 [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)