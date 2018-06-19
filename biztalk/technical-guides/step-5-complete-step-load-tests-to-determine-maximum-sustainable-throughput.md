---
title: 步驟 5： 執行步驟負載模式測試，來判斷最大持續輸送量 |Microsoft 文件
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
ms.openlocfilehash: 8f9794634b5a782ef6d9bce4e819e759fd47ba1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302638"
---
# <a name="step-5-perform-step-load-pattern-tests-to-determine-maximum-sustainable-throughput"></a>步驟 5： 執行步驟負載模式測試，來判斷最大持續輸送量
判斷最大持續輸送量 (MST) 在 BizTalk Server 方案中使用 Visual Studio 負載測試的最簡單方法是執行的步驟負載模式和比較總每秒處理的文件每秒接收的文件總數. 只要每秒處理的平均總文件是大於或等於測試期間每秒接收的平均總文件，則負載會被視為持續性。 如果平均每秒接收的文件總數第二個大於測試期間每秒處理的平均總文件，則負載不會被視為持續性，而且這會由對應的成長中的值總合Biztalk: Message Box: General Counters\Spool Size 計數器。 經過一段時間，當 BizTalk Server 應用程式會收到比它可以處理的文件，未處理的文件將會累積在 MessageBox 資料庫中，將最終誘使節流狀況，並大幅降低的效能BizTalk Server 應用程式。  
  
## <a name="configure-the-load-test-with-a-step-load-pattern-appropriate-for-your-application"></a>使用步驟負載模式適用於您的應用程式設定負載測試  
 遵循本主題中的步驟[步驟 3： 建立負載測試來執行多個單元測試同時](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md)建立負載測試時，會使用步驟負載模式。 影響能夠及時處理文件的 BizTalk Server 應用程式的能力的因素包括：  
  
-   **BizTalk Server 群組中的電腦數目**-其他 BizTalk 伺服器提供額外的處理能力。  
  
-   **正在處理的訊息大小**-較大的訊息需要額外的處理資源。  
  
-   **文件對應的量執行**-對應需要額外的處理資源。  
  
-   **接收管線或傳送管線的應用程式所需**。 -複雜管線需要額外的處理資源。  
  
-   **配接器和/或 BizTalk Server 應用程式所使用的快速鍵**– 某些配接器和/或加速器需要比其他更多的處理資源。  
  
-   **郵件追蹤所需數量**– 已耗用大量資源的訊息追蹤。  
  
-   **數目與複雜度的 BizTalk Server 應用程式中執行的協調流程**– 協調流程可以是非常耗用資源。  
  
 在設定步驟負載模式測試時，修改為指定的值**啟動使用者計數**和**最大使用者計數**，確保指定可輕鬆地開始執行使用者計數的訊息數目由 BizTalk Server 應用程式容錯移轉時間和同樣地，指定最大使用者計數的訊息數目大於： BizTalk Server 應用程式可以處理一段時間。 請參閱[加入負載測試，並設定負載測試情節、 計數器集合和回合設定](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_StepLoadTest)編輯負載測試的負載模式設定的相關資訊。  
  
## <a name="ensure-that-the-correct-test-settings-are-used-for-the-step-pattern-load-test"></a>確定正確的測試設定會用於步驟模式負載測試  
 設定要使用的負載測試**測試設定**您在建立[方案以執行測試和從遠端收集資料以加入測試設定檔](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_TestSettings)。  
  
## <a name="configure-the-load-test-with-the-appropriate-performance-counters-and-run-the-step-pattern-load-test"></a>設定負載測試與適當的效能計數器，然後執行步驟模式負載測試  
 請依照[加入自訂計數器集合會以量值 BizTalk Server 關鍵效能指標 (KPI)](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_BTSCounters)新增必要的 BizTalk Server 效能計數器可以用來測量的 BizTalk Server 效能應用程式，並判斷點，BizTalk Server 應用程式已不再能夠保持載入測試代理程式所建立的訊息負載。 這會透過增加 [biztalk: Message Box: General Counters\Spool Size] 計數器的值所偵測到的多工緩衝處理資料表中的訊息待處理項目的累算總合。 如果這個計數器的值開始大幅增加您有可能超過 MST 的 BizTalk Server 應用程式。 一旦您已決定 BizTalk Server 應用程式在不再能夠處理許多訊息時接收，請記下的文件 received/Sec 當發生這種情況的訊息數目。 請務必記下此值，因為主題[步驟 6： 執行常數負載模式測試，以確認最大持續輸送量](../technical-guides/step-6-complete-load-pattern-tests-to-verify-maximum-sustainable-throughput.md)將說明如何執行 [常數的使用者計數] 值的固定模式負載測試這是稍微小於最大持續性文件數/秒值。 這是為了確認 BizTalk Server 應用程式能夠處理一段時間的訊息數量。 若要檢視的計數器集合的值，第一次啟動負載測試，以滑鼠右鍵按一下測試名稱 (例如 BTS_Messaging_Step)，，然後按一下**執行測試**功能表選項。 效能計數器會初始化並開始負載測試之後，Visual Studio 會自動將焦點切換至 [圖形] 視窗可讓您同時顯示 1 4 圖形。 如果您主要是想要在中，只能檢視關鍵效能指標中所定義[加入自訂計數器集合會以量值 BizTalk Server 關鍵效能指標 (KPI)](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_BTSCounters)，按一下 **面板**下拉式清單從 [負載測試] 功能表，並選取的選項**一個面板**。 然後按一下 下拉式清單頂端的圖表，然後選取**關鍵指標**即時顯示關鍵效能指標的值。  
  
> [!NOTE]  
>  因為某些預設計數器的值將會顯示在**關鍵指標**圖形，因為您可能會想要顯示計數器數值，您可以加入自訂計數器集合，您可能需要以手動方式刪除每個顯示在計數器**關鍵指標**圖，並以手動方式將計數器加入從自訂計數器集。 比方說，有提供的話，您會想要至少將計數器新增下表來判斷 BizTalk Server 環境，以及處理負載，以及找出任何瓶頸可能會發生您圖形：  
  
|計數器類別|計數器|執行個體|電腦|  
|----------------------|-------------|--------------|--------------|  
|BizTalk:Message Box：一般計數器|多工緩衝處理大小|*BizTalk Server Messagebox 資料庫*:*裝載 BizTalk Server Messagebox 資料庫的 SQL Server 執行個體*|安裝任何 BizTalk Server 群組中，使用 BizTalk Server 管理主控台。|  
|BizTalk:傳訊|接收文件數/秒|RxHost （或接收主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #1*|  
|BizTalk:傳訊|接收文件數/秒|RxHost （或接收主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #2*|  
|BizTalk:傳訊|接收文件數/秒|RxHost （或接收主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #n*|  
|BizTalk:傳訊|處理文件數/秒|TxHost （或傳送主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #1*|  
|BizTalk:傳訊|處理文件數/秒|TxHost （或傳送主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #2*|  
|BizTalk:傳訊|處理文件數/秒|TxHost （或傳送主控件的名稱）|*BizTalk Server 群組中的 BizTalk Server 電腦 #n*|  
|處理器|% 處理器時間|_Total|*BizTalk Server 群組中的 BizTalk Server 電腦 #1*|  
|處理器|% 處理器時間|_Total|*BizTalk Server 群組中的 BizTalk Server 電腦 #2*|  
|處理器|% 處理器時間|_Total|*BizTalk Server 群組中的 BizTalk Server 電腦 #n*|  
|處理器|% 處理器時間|_Total|*裝載 BizTalk Server 資料庫的 SQL Server 執行個體*|