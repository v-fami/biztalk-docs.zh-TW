---
title: 關鍵效能指標 |Microsoft Docs
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
ms.openlocfilehash: f808299dd0df0c47b169a831a7f09b33e59dc799
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966135"
---
# <a name="key-performance-indicators"></a>關鍵效能指標
本主題提供使用下列的向外延展方法時，所觀察到 BizTalk Server 產品小組的測試結果：  
  
- 關鍵效能指標 (Kpi)，當增加的數目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試中，只有一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫設有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試著重於增加更多的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
- Kpi 的數目增加時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所使用的 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試著重於增加更多的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
- Kpi 時增加兩者的數字[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦並[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所使用的 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這些測試會測量的新增影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦並[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
## <a name="analysis-of-key-performance-indicators"></a>分析的關鍵效能指標  
  
### <a name="messaging-scenario-biztalk-server-scale-out--biztalk-and-sql-kpi"></a>傳訊案例中，BizTalk Server 向外延展 – BizTalk 和 SQL KPI  
 新增第二部電腦，執行 BizTalk Server 不會顯示的整體輸送量很重要的影響。  在 BizTalk Server CPU 負載降低 25%。 適用於 SQL Server CPU 稍微增加從 59%至 59.8%時執行 BizTalk Server 的第二部電腦新增至 BizTalk Server 群組。 超過此時間點，已不獲得任何進一步的效能益處增加 BizTalk 處理伺服器的數目。  
  
 每個 BizTalk 主控件執行個體，定期輪詢 MessageBox 中適當的佇列。 參考在主控件佇列的任何訊息實際上儲存在 MessageBox 中的資料表的共用集內。 新增更多執行 BizTalk Server 的電腦時，會卸除的輸送量，常見的原因會是針對 MessageBox 資料庫中的共用資料表的活動太多。 將這些資料表指派給特定的檔案群組，可以建立專用的 I/O 路徑，SQL Server 的這些資料表。  
  
 [最佳化檔案群組的資料庫 2](../technical-guides/optimizing-filegroups-for-the-databases2.md)提供如何將資料表指派給特定的檔案群組的指引。 包含在指令碼[BizTalk Server MessageBox 資料庫檔案群組 SQL 指令碼](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)的指南會告訴您如何完成這。 向外的延展至多個 MessageBox 組態只應該視為之後跨多個檔案群組，並套用所有其他 SQL 相關的最佳化之後，散發 MessageBox 物件。  
  
 **BizTalk Server 和 SQL Server CPU 使用率百分比**  
  
 ![M&#45;SingleMsgBox](../technical-guides/media/m-singlemsgbox.gif "M SingleMsgBox")  
  
### <a name="messaging-scenario-biztalk-server-and-sql-server-scale-out--biztalk-and-sql-kpi"></a>傳訊案例中，BizTalk Server 和 SQL Server 向外延展 – BizTalk 和 SQL KPI  
 若要判斷擴充藉由新增四個 MessageBox 資料庫的 SQL Server 層的效率執行這項測試。 在此案例中，新增最多兩個執行 BizTalk Server 的電腦啟用 2,790 每秒的訊息的最大持續輸送量。 使用單一 MessageBox 時，這會是 118%超過最大取得輸送量。 超過此時間點，以類似的方式，單一 MessageBox 案例的效能降低將更多處理能力新增至 BizTalk Server 層。  
  
 從傳訊案例的測試索引鍵的結果是，向外擴充 BizTalk Server 是有效的技術，以增加整體輸送量，如果 SQL Server 上的競爭不是瓶頸。 如果 MessageBox 資料庫會變成的爭用點，請先套用所述的最佳化[最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)，特別是檔案群組最佳化指令碼中所述[BizTalk ServerMessageBox 資料庫檔案群組 SQL 指令碼](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)將 I/O 負載。 如果您仍然無法達到您所需的輸送量時，您應該考慮藉由新增更多的 MessageBox 資料庫向外延展。  
  
 **BizTalk Server 和 SQL Server CPU 使用率百分比**  
  
 ![M&#45;MultipleMsgBox](../technical-guides/media/m-multiplemsgbox.gif "M MultipleMsgBox")  
  
### <a name="orchestration-scenario-biztalk-server-scale-out--sql-server-and-biztalk-server-kpi"></a>協調流程案例中，BizTalk Server 向外延展 – SQL Server 和 BizTalk Server KPI  
 新增第二部電腦，執行 BizTalk Server 不會顯示的整體輸送量很重要的影響。 BizTalk Server CPU 的負載減少 23%。 適用於 SQL Server CPU 會增加 66.5%68.5%新增額外的電腦執行 BizTalk Server 時。  
  
 **BizTalk Server 和 SQL Server CPU 使用率百分比**  
  
 ![O&#45;SingleMsgBox](../technical-guides/media/o-singlemsgbox.gif "O SingleMsgBox")  
  
### <a name="orchestration-scenario-biztalk-server-and-sql-server-scale-out--sql-server-and-biztalk-server-kpi"></a>協調流程案例中，BizTalk Server 和 SQL Server 向外延展 – SQL Server 和 BizTalk Server KPI  
 執行此測試以判斷藉由新增更多的電腦執行 BizTalk Server 協調流程案例的多個 MessageBox 資料庫向外擴充 BizTalk Server 和 SQL Server 的層的效率。 在此案例中，新增最多兩個執行 BizTalk Server 的電腦啟用每秒的 1,487 協調流程的最大持續的輸送量。 這是 116%高於最大的單一 MessageBox 取得結果。 向外延展至不同的 SQL Server 電腦上的四個 MessageBox 資料庫，可容納增加的輸送量，因為額外的處理能力，以及資料庫的負載分配給多個 MessageBox 資料庫。 這種做法也減輕了爭用共用在資料表上，這是單一 MessageBox 環境中的瓶頸。 如同傳訊案例中，增加的 MessageBox 資料庫數目，以及散發這些在專用的 SQL 執行個體，可讓新增至 BizTalk Server 群組的數個 BizTalk Server 電腦。  
  
 **BizTalk Server 和 SQL Server CPU 使用率百分比**  
  
 ![O&#45;MultipleMsgBox](../technical-guides/media/o-multiplemsgbox.gif "O MultipleMsgBox")  
  
## <a name="see-also"></a>另請參閱  
 [調整生產 BizTalk Server 環境](../technical-guides/scaling-a-production-biztalk-server-environment.md)