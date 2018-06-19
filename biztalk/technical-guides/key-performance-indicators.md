---
title: 關鍵效能指標 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 298d639a-7adf-4f04-b097-a17f4c77ee50
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a03bf76c725f22567d5e884ca22e3a862b15ce3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298286"
---
# <a name="key-performance-indicators"></a>關鍵效能指標
本主題提供使用下列的擴充方法時，觀察到 BizTalk Server 產品小組的測試結果：  
  
-   關鍵效能指標 (Kpi) 的數目增加時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試中，只有一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫已設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試僅著重於增加更多的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
-   Kpi 的數目增加時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所使用的 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試僅著重於增加更多的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
-   Kpi 的兩者數目增加時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所使用的 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試以測量的新增影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
## <a name="analysis-of-key-performance-indicators"></a>分析的關鍵效能指標  
  
### <a name="messaging-scenario-biztalk-server-scale-out--biztalk-and-sql-kpi"></a>傳訊案例中，BizTalk Server 向外延展 – BizTalk 和 SQL KPI  
 新增第二部電腦，執行 BizTalk Server 不會對整體產能顯示重大的影響。  在 BizTalk 伺服器的 CPU 上負載降低 25%。 適用於 SQL Server CPU 投資可增加從 59%59.8%第二個執行 BizTalk Server 的電腦新增至 BizTalk Server 群組。 超過這個時間點，沒有進一步的效能優勢已獲得藉由增加 BizTalk 處理伺服器的數目。  
  
 每個 BizTalk 主控件執行個體，定期輪詢 MessageBox 中適當的佇列。 主控件佇列參考的任何訊息實際上儲存在 MessageBox 中的資料表的共用集內。 新增更多的電腦執行 BizTalk Server 時，會卸除輸送量，常見原因，是針對共用 MessageBox 資料庫中資料表的活動太多。 將這些資料表指派給特定的檔案群組，可以建立專用的 I/O 路徑，SQL Server 的這些資料表。  
  
 [最佳化檔案群組 Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md)提供如何將資料表指派給特定的檔案群組的指引。 包含在指令碼[BizTalk Server MessageBox 資料庫檔案群組 SQL 指令碼](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)的指南會告訴您如何完成這。 之後散發 MessageBox 物件跨多個檔案群組，並套用所有其他 SQL 相關的最佳化之後，才能考慮向外的延展到多個 MessageBox 設定。  
  
 **BizTalk Server 和 SQL Server CPU 使用率百分比**  
  
 ![&#45;SingleMsgBox](../technical-guides/media/m-singlemsgbox.gif "M SingleMsgBox")  
  
### <a name="messaging-scenario-biztalk-server-and-sql-server-scale-out--biztalk-and-sql-kpi"></a>傳訊案例中，BizTalk Server 和 SQL Server 向外延展 – BizTalk 和 SQL KPI  
 執行此測試以判斷的向外擴充 SQL Server 層藉由新增四個 MessageBox 資料庫效能。 在此案例中，新增兩個執行 BizTalk Server 的電腦啟用 2,790 每秒的訊息的最大持續輸送量。 使用單一 MessageBox 時，這是 118%高於才能取得的最大輸送量。 超過這個時間點，以類似的方式，單一 MessageBox 案例的效能降低將更多的處理能力加入至 BizTalk Server 層。  
  
 索引鍵的傳訊案例的測試結果是，向外延展 BizTalk Server 是有效的技術，來提高整體輸送量，如果 SQL Server 上的競爭不是瓶頸。 如果 MessageBox 資料庫變成的爭用點，請先套用中詳述的最佳化[最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)，特別是在檔案群組最佳化指令碼中所述[BizTalk ServerMessageBox 資料庫檔案群組的 SQL 指令碼](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)散發 I/O 負載。 如果您仍然無法達到您所需的輸送量，您應該考慮橫向擴充，新增多個 MessageBox 資料庫。  
  
 **BizTalk Server 和 SQL Server CPU 使用率百分比**  
  
 ![&#45;MultipleMsgBox](../technical-guides/media/m-multiplemsgbox.gif "M MultipleMsgBox")  
  
### <a name="orchestration-scenario-biztalk-server-scale-out--sql-server-and-biztalk-server-kpi"></a>協調流程案例中，BizTalk Server 向外延展 – SQL Server 和 BizTalk Server KPI  
 新增第二部電腦，執行 BizTalk Server 不會對整體產能顯示重大的影響。 在 BizTalk 伺服器的 CPU 上的負載減少 23%。 適用於 SQL Server CPU 會增加從 66.5%68.5%加入執行 BizTalk Server 的其他電腦時。  
  
 **BizTalk Server 和 SQL Server CPU 使用率百分比**  
  
 ![&#45;SingleMsgBox](../technical-guides/media/o-singlemsgbox.gif "O SingleMsgBox")  
  
### <a name="orchestration-scenario-biztalk-server-and-sql-server-scale-out--sql-server-and-biztalk-server-kpi"></a>協調流程案例中，BizTalk Server 和 SQL Server 向外延展 – SQL Server 和 BizTalk Server KPI  
 執行此測試以判斷的向外擴充 BizTalk Server 和 SQL Server 層藉由新增更多的電腦執行 BizTalk Server 和協調流程案例的多個 MessageBox 資料庫效能。 在此案例中，新增兩個執行 BizTalk Server 的電腦啟用每秒 1,487 協調流程的最大持續的輸送量。 這是 116%高於最大的才能取得結果，針對單一 MessageBox。 向外延展至不同的 SQL Server 電腦上的四個 MessageBox 資料庫，可容納增加的輸送量，由於額外的處理能力，並且能夠將資料庫負載分散到多個 MessageBox 資料庫。 這種做法也減輕爭用共用在資料表上，這是在單一環境中，MessageBox 是效能瓶頸。 與傳訊案例中，增加的 MessageBox 資料庫數目，以及散發這些專用的 SQL 執行個體之間能夠新增至 BizTalk Server 群組的數個 BizTalk Server 電腦。  
  
 **BizTalk Server 和 SQL Server CPU 使用率百分比**  
  
 ![&#45;MultipleMsgBox](../technical-guides/media/o-multiplemsgbox.gif "O MultipleMsgBox")  
  
## <a name="see-also"></a>另請參閱  
 [調整實際執行 BizTalk Server 環境](../technical-guides/scaling-a-production-biztalk-server-environment.md)