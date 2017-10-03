---
title: "監視 SQL Server Agent 作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60d0a377-c86d-429b-9e48-c37bd5b0f912
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 489e9e8e8b5bf5b00125036d71ff5fa0f37f3545
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-server-agent-jobs"></a>監視 SQL Server Agent 作業
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含多項 SQL Server Agent 作業，可執行重要功能以維持伺服器運作正常且狀況良好。 您應該監視這些作業的狀況，確保它們在沒有錯誤的情況下執行。  
  
## <a name="guidelines-for-monitoring-the-sql-server-agent-jobs"></a>監視 SQL Server Agent 作業的指導方針  
 以下是用於監視作業的指導方針：  
  
-   **確認 SQL Server Agent 服務正在執行**  
  
-   **確認 BizTalk Server 所安裝的 SQL Server Agent 作業已啟用且正在執行成功**  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Server Agent 作業很重要： 如果它們未執行，一段時間，將會降低系統效能。  
  
-   **確認 BizTalk Server SQL Server Agent 作業所完成及時**  
  
     設定 Microsoft System Center Operations Manager 監視作業。  
  
     您應留意某些工作特定的排程：  
  
    -   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作預設會持續執行。 監視軟體，應該考量此排程，而不會產生警告。  
  
    -   未啟用 MessageBox_Message_Cleanup_BizTalkMsgBoxDb 作業或排程，但它由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作啟動每隔 10 秒。 因此，此作業應該不啟用、 排程，或手動啟動。  
  
-   **確認已正確設定 SQL Server Agent 服務的啟動類型**  
  
     確認 SQL Server Agent 服務已設定使用**Startuptype**的**自動**除非 SQL Server Agent 服務已設定為 Windows Server 叢集上叢集資源。 如果 SQL Server Agent 服務設定為叢集資源，則您應該設定**Startuptype**為**手動**因為服務會管理叢集服務。  
  
## <a name="additional-resources"></a>其他資源  
  
-   如需有關監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL Agent 作業，請參閱[監視 SQL Server Agent 作業和資料庫](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)。  
  
-   如需隨附於 SQL Server Agent 作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]看到[[資料庫結構與工作]](http://go.microsoft.com/fwlink/?LinkID=153451) (http://go.microsoft.com/fwlink/?LinkID=153451)。