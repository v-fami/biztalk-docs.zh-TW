---
title: 步驟 5： 執行步驟負載模式測試，以判斷最大持續輸送量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8056ced6-1f04-4be2-878a-48a427a93dad
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 223d8e444bbfc05960f2266e0c23eb0f1a90d9ee
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987567"
---
# <a name="step-5-perform-step-load-pattern-tests-to-determine-maximum-sustainable-throughput"></a>步驟 5： 執行步驟負載模式測試，以判斷最大持續輸送量
決定最大持續輸送量 (MST) 的 BizTalk Server 解決方案使用 Visual Studio 負載測試的最簡單方法是執行的步驟負載模式，並比較總計每秒處理的文件每秒接收的文件總數. 只要每秒處理的平均總文件是大於或等於接收測試期間每秒的平均總文件，則負載視為持續性。 如果平均每接收文件總數第二個大於測試期間每秒處理的平均總文件則負載不會被視為持續性，而且這會由對應的成長中的值總合Biztalk: Message Box: General Counters\Spool Size 計數器中。 經過一段時間，當 BizTalk Server 應用程式收到比它可以處理更多的文件時，未處理的文件將會累積在 MessageBox 資料庫中，將最後引發節流狀況，並大幅降低的效能BizTalk Server 應用程式。  
  
## <a name="configure-the-load-test-with-a-step-load-pattern-appropriate-for-your-application"></a>使用步驟負載模式適用於您的應用程式中設定負載測試  
 請依照下列主題中的步驟[步驟 3： 建立負載測試來執行多個單元測試同時](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md)建立負載測試使用步驟負載模式。 影響 neodpověděl včas 處理文件的 BizTalk Server 應用程式的能力的因素包括：  
  
- **BizTalk Server 群組中的電腦數目**-其他 BizTalk 伺服器提供額外的處理能力。  
  
- **正在處理的訊息大小**位較大的訊息需要額外的處理資源。  
  
- **文件對應的量執行**-對應需要額外的處理資源。  
  
- **接收管線或傳送管線的應用程式所需**。 -複雜的管線會需要額外的處理資源。  
  
- **配接器和/或 BizTalk Server 應用程式所使用的加速器**– 某些配接器和/或加速器需要比其他的更多處理資源。  
  
- **訊息追蹤所需的數量**– 訊息追蹤會耗用大量資源。  
  
- **數目和複雜度的 BizTalk Server 應用程式中執行的協調流程**-協調流程可以是非常耗用資源。  
  
  當設定步驟負載模式測試，修改指定的值**啟動使用者計數**並**最大使用者計數**以確保啟動使用者計數，可以輕鬆地針對指定的訊息數目由 BizTalk Server 段時間，並同樣地，指定最大使用者計數的訊息數目的應用程式會是多個 BizTalk Server 應用程式可以處理一段時間。 請參閱[新增負載測試，並設定負載測試情節、 計數器集合和回合設定](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_StepLoadTest)編輯負載測試的負載模式設定的相關資訊。  
  
## <a name="ensure-that-the-correct-test-settings-are-used-for-the-step-pattern-load-test"></a>確保使用正確的測試設定為步驟模式的負載測試  
 設定要使用的負載測試**測試設定**中建立[方案以執行測試和從遠端收集資料以加入測試設定檔](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_TestSettings)。  
  
## <a name="configure-the-load-test-with-the-appropriate-performance-counters-and-run-the-step-pattern-load-test"></a>設定負載測試與適當的效能計數器，然後執行步驟模式負載測試  
 請依照下列中的步驟[新增自訂計數器集合以量值 BizTalk Server 關鍵效能指標 (KPI)](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_BTSCounters)新增必要的 BizTalk Server 效能計數器來測量的 BizTalk Server 效能應用程式，並判斷何時 BizTalk Server 應用程式已不再能夠保持載入的測試代理程式所建立的訊息負載。 這會由 [biztalk: Message Box: General Counters\Spool Size] 計數器的值增加所見的多工緩衝處理資料表中的訊息待處理項目累算總合。 如果這個計數器的值開始大幅增加您有可能超過 MST 的 BizTalk Server 應用程式。 一旦您已經決定的 BizTalk Server 應用程式已不再能夠處理許多訊息，它會接收，記下的文件 received/Sec 當發生這種情況的訊息數目。 請務必記下此值，因為主題[步驟 6： 執行常數負載模式測試，來確認最大持續輸送量](../technical-guides/step-6-complete-load-pattern-tests-to-verify-maximum-sustainable-throughput.md)將說明如何執行與常數使用者計數 值的常數模式負載測試這是有點小於最大持續性文件數/秒值。 這是為了確認 BizTalk Server 應用程式是可經過一段時間處理的訊息數量。 若要檢視的計數器集合的值，第一次啟動負載測試，以滑鼠右鍵按一下測試名稱 (例如 BTS_Messaging_Step)，，然後按一下**執行測試**功能表選項。 效能計數器會初始化和負載測試開始之後，Visual Studio 會自動將焦點切換到圖形視窗可讓您同時顯示 1 4 的圖形。 如果您是主要想要只檢視 關鍵效能指標，如同[新增自訂計數器集合以量值 BizTalk Server 關鍵效能指標 (KPI)](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_BTSCounters)，按一下**面板**下拉式清單從 [負載測試] 功能表，然後選取的選項**一個面板**。 然後按一下頂端的圖表，然後選取下拉式清單**關鍵指標**即時顯示關鍵效能指標的值。  
  
> [!NOTE]  
>  因為某些預設計數器的值將會顯示在**關鍵指標**圖形，並因為您可能會想要顯示您加入至自訂計數器集合的計數器值，您可能想要以手動方式刪除每個啟動在顯示的計數器**關鍵指標**圖形，然後從您的自訂計數器集手動新增計數器。 比方說，有提供的話，您會想要新增至少計數器下表中至您的圖形，來決定 BizTalk Server 環境如何處理負載，以及可能會發生任何瓶頸的位置：  
  
|計數器分類|計數器|執行個體|電腦|  
|----------------------|-------------|--------------|--------------|  
|BizTalk:Message Box：一般計數器|多工緩衝處理大小|*BizTalk Server Messagebox 資料庫*:*裝載 BizTalk Server Messagebox 資料庫的 SQL Server 執行個體*|使用 BizTalk Server 管理主控台的 在群組中任何 BizTalk Server 安裝。|  
|BizTalk:傳訊|接收文件數/秒|RxHost （或接收主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #1*|  
|BizTalk:傳訊|接收文件數/秒|RxHost （或接收主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #2*|  
|BizTalk:傳訊|接收文件數/秒|RxHost （或接收主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #n*|  
|BizTalk:傳訊|處理文件數/秒|把 TxHost （或傳送主控件名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #1*|  
|BizTalk:傳訊|處理文件數/秒|把 TxHost （或傳送主控件名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #2*|  
|BizTalk:傳訊|處理文件數/秒|把 TxHost （或傳送主控件名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #n*|  
|處理器|% 處理器時間|_Total|*BizTalk Server 群組中的 BizTalk Server 電腦 #1*|  
|處理器|% 處理器時間|_Total|*BizTalk Server 群組中的 BizTalk Server 電腦 #2*|  
|處理器|% 處理器時間|_Total|*BizTalk Server 群組中的 BizTalk Server 電腦 #n*|  
|處理器|% 處理器時間|_Total|*裝載 BizTalk Server 資料庫的 SQL Server 執行個體*|