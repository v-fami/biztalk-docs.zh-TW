---
title: "使用 [群組中樞] 頁面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50693ccc-a3b2-4ad0-9a05-d60dab404a07
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e035a363b71b70db390d88a8b0e32e2e9b531d92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-group-hub-page"></a>使用群組中樞頁面
選取**BizTalk 群組**在 BizTalk Server 管理主控台中，節點會顯示 [BizTalk Server 群組中樞] 頁面詳細資料窗格中。 [BizTalk Server 群組中樞] 頁面分為三個區段，會提供 BizTalk Server 系統狀況的整體檢視。  
  
-   **設定概觀**區段中，位於 [群組中樞] 頁面的上半部顯示主控件執行個體，應用程式的狀態，表示 BizTalk 群組的整體健全狀況和配接器處理常式中設定此群組中。  
  
-   **進行中的工作**和**擱置的項目**區段則位於 [群組中樞] 頁面的中間。  
  
    -   **進行中的工作**區段會顯示執行中服務執行個體、 凍結的協調流程、 正在重試與閒置的連接埠、 準備就緒的服務執行個體和已排程的服務執行個體。  
  
    -   **擱置的項目**區段會顯示已擱置的服務執行個體，並可繼續和不可繼續的執行個體的數目。  
  
-   **分組已擱置服務執行個體**區段會顯示依應用程式、 服務名稱、 錯誤碼和 URI 分組的已擱置的服務執行個體。  
  
    > [!NOTE]
    >  在 [群組中樞] 頁面中列出的數字只是近似的計數。 例如下, 顯示的數字**執行服務執行個體**或**已擱置服務執行個體**可能不等於執行中服務執行個體或已擱置的服務執行個體的總數因為正在產生 [中樞] 頁面上的各種統計資料時，無法變更系統的狀態。  
  
-   **追蹤服務執行個體**和**追蹤訊息事件**區段訊息事件和狀態的服務執行個體的最大相符項目上執行查詢 = 50。  
  
    -   **追蹤服務執行個體**查詢會搜尋搜尋受到追蹤的服務執行個體。  
  
    -   **已完成執行個體**查詢會搜尋搜尋受到追蹤的服務執行個體等於完成狀態。  
  
    -   **終止執行個體**查詢會搜尋搜尋受到追蹤的服務執行個體的狀態等於終止。  
  
    -   **追蹤訊息事件**查詢搜尋的追蹤的訊息事件。  
  
    -   **傳輸失敗事件**查詢搜尋的傳輸失敗的事件類型的追蹤的訊息事件。  
  
-   **EDI 狀態報告**和**EDIINT 狀態報告**區段，位於 群組中樞 頁面底部會顯示有關 EDI 交換的四個報表和相關 AS2 交換的其中一個： EDI 交換和相互關聯的 ACK 狀態報表、 批次狀態報告中，交換彙總報告、 交易集彙總報告和 AS2 訊息和相互關聯的 MDN 狀態報告。 如需有關這些報表的詳細資訊，請參閱[EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)。  
  
    > [!NOTE]
    >  如果此 BizTalk 群組設定 EDI/AS2 功能，則只會顯示 EDI 和 EDIINT 狀態報告的區段。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [服務執行個體狀態](../core/service-instance-states.md)  
  
-   [調查協調流程、 連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)  
  
-   [使用管理主控台查詢索引標籤](../core/using-the-administration-console-query-tab.md)  
  
-   [檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [健全狀況與活動追蹤](../core/health-and-activity-tracking.md)