---
title: "互動配接器儲存與轉送 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d596780a-085d-48db-be44-a3ae58f591d0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c7aff0b2421a19f5fe84ee914c4f9d2bd7ef04e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="interact-adapter-store-and-forward"></a>配接器儲存與轉送互動
在存放區和順向 (SnF) 模式中，訊息傳送至佇列在傳送時，會從目的地佇列擷取。 使用時 SnF，回應來自 SWIFTNet SnF 本身，並不包含任何來自回應者的意見反應。  
  
 訊息和檔案可以路由傳送到佇列為訊息路由傳送至伺服器處理序，不使用 SnF 時相同的彈性。 這個定義是 MRR （內 SWIFTNet) 內。 所以接收者必須決定哪些佇列中的訊息或檔案將會傳送寄件者之後。 將訊息或檔案放在佇列是由 SnF 傳遞模式 （在 RequestControl) 的訊息加上旗標。  
  
 從佇列擷取訊息可能會發生兩個不同的模式，視應用程式的設計工具所做的選擇而定。 這些模式稱為發送和提取。  
  
 使用推入模式時，將訊息傳遞 initiative 位於與 SWIFTNet SnF。 然後 「 推送 」 從 SWIFTNet SnF 訊息，並收到由應用程式伺服器上 SWIFTNet 連結。 請確認訊息 safestored 然後通知以回應對伺服器應用程式。 此通知指示 SWIFTNet SnF 已收到訊息。 通知不包含任何額外的"business"邏輯。  
  
## <a name="queues-in-swiftnet"></a>SWIFTNet 中的佇列  
 佇列包含訊息和寄件者傳送到傳遞至指定的收件者的檔案。 佇列也包含由 SWIFTNet SnF 產生傳遞通知。  
  
 佇列定義和接收者的組織所設定。 佇列的實際建立方式是 SWIFT 之使用者的要求。 寄件者不知道在其中訊息最終將的佇列的相關的任何項目。 這是完全受控制的收件者。  
  
 佇列視窗大小屬性控制 SWIFTNet SnF 擷取從佇列中未認可的訊息的數目上限。 收件者還是必須確認訊息之前釋放 視窗中的位置。  
  
### <a name="delivery-into-a-queue"></a>傳遞至佇列  
 使用儲存和轉送服務的收件者會決定的佇列會用來儲存所儲存和轉送模式中傳送的訊息。  
  
 傳遞通知會放在寄件者機構，以傳送訊息的傳遞狀態通知寄件者的佇列。 這是可設定與傳送配接器屬性。  
  
## <a name="sessions"></a>工作階段  
 取得佇列，會啟動工作階段。 Sw:SnFSessionId 會傳回每個訊息，由 SWIFTNet SnF。 Sw:SnFSessionId 包含佇列名稱的工作階段模式： 推入，以及工作階段數目。 工作階段數目會遞增每個工作階段。 範例如下：  
  
 **\<Sw:SnFSessionId\>bankwxyz_applicq1:p:000458\</Sw:SnFSessionId\>**  
  
 "p"指出推入工作階段。 工作階段也是視為佇列的保留由授權者。 後續的訊息必須由相同的授權者認可。  
  
 傳送訊息至儲存和轉送時，工作階段不適用。  
  
### <a name="push-session-snf"></a>推入工作階段 SnF  
 SnF 順序會假設下列：  
  
-   用戶端處理序已完成其工作，並可立即終止。 若要這樣做，開啟 安全性內容必須先清除上發出 SwSec:DestroyContextRequest。 Sw:TermRequest 之後, 處理程序可能 exit （）。  
  
-   另一個用戶端已啟動。 初始設定步驟都與第一個用戶端相同。 佇列的版本是執行以做為基本輸入 Sw:ReleaseSnFQueueRequest SwCall。  
  
     SWIFTNet 停止從佇列的訊息傳遞，因為它已順利處理佇列的版本。  
  
 伺服器會處理一個要求時。 SWIFTNet SnF 提供幾個佇列的要求。 伺服器的回應，或發生逾時之前，這些會緩衝網路和 SWIFTNet 連結中。  
  
 有可能，有些要求了已被傳遞，但尚未認可之前釋出佇列。 SWIFTNet SnF 不會處理這些訊息的任何多個通知，直到釋放佇列為止。 這些訊息將會重新傳遞後續的工作階段中。  
  
 伺服器應用程式仍會以正值通知之後，用戶端發出發行該佇列，但通常這不會發生此情況，系統會從佇列傳送的要求回應是否會維持到本機的實作。  
  
## <a name="see-also"></a>請參閱  
 [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [InterAct 配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)