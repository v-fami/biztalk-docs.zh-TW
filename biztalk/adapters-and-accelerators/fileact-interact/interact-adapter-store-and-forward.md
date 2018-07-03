---
title: InterAct 配接器儲存和轉寄 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d596780a-085d-48db-be44-a3ae58f591d0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f3ce047de1c926e6e144b1351954774c1d3edb5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022588"
---
# <a name="interact-adapter-store-and-forward"></a>InterAct 配接器儲存和轉寄
在存放區中，並正向 (SnF) 模式中，訊息傳遞給佇列在傳送時，會從目的地佇列擷取。 使用時 SnF，回應來自 SWIFTNet SnF 本身並不包含任何來自回應者的意見反應。  
  
 訊息和檔案可以路由傳送到佇列有相同的彈性，為訊息路由傳送至伺服器處理序時未使用 SnF。 此定義位於 MRR （內 SWIFTNet)。 它是接收者必須決定哪一個佇列中訊息或檔案會成為寄件者傳送後。 將訊息或檔案放在佇列中由 SnF 傳遞模式 （在 RequestControl) 的訊息加上旗標。  
  
 從佇列擷取訊息可能會發生兩種不同模式的詳細資訊，視應用程式的設計工具所做的選擇而定。 推送和提取，就會呼叫這些模式。  
  
 使用推播模式時，將訊息傳遞計劃會位於使用 SWIFTNet SnF。 訊息然後 「 從推播 」 SWIFTNet SnF，而且會收到由應用程式伺服器上 SWIFTNet 連結。 伺服器應用程式必須確保訊息是 safestored 再回應以確認。 此通知指示 SWIFTNet SnF 已收到訊息的方式。 通知不包含任何其他額外的 「 商業 」 邏輯。  
  
## <a name="queues-in-swiftnet"></a>SWIFTNet 中的佇列  
 佇列包含訊息和傳送的傳送者傳遞至指定的收件者的檔案。 佇列也包含 SWIFTNet SnF 所產生的傳遞告知。  
  
 佇列所定義且由接收者的組織設定。 在使用者的要求，實際建立佇列是由 SWIFT。 寄件者不知道在其中訊息最後將的佇列的相關的任何項目。 這是接收者的完全掌控。  
  
 Queue 的視窗大小屬性控制 SWIFTNet SnF 擷取而不需要通知佇列的訊息的數目上限。 接收者仍然必須確認訊息之前的視窗中的位置便會釋放。  
  
### <a name="delivery-into-a-queue"></a>傳遞到佇列  
 使用儲存和轉送服務的接收者會判斷哪一個佇列會用來儲存所儲存和轉送模式中傳送的訊息。  
  
 傳遞通知會放入寄件者機構，以傳送訊息的傳遞狀態通知寄件者的佇列。 這是可設定與傳送配接器屬性。  
  
## <a name="sessions"></a>工作階段  
 取得佇列時, 啟動工作階段。 Sw:SnFSessionId 會傳回每個訊息，由 SWIFTNet SnF 傳遞。 Sw:SnFSessionId 包含佇列名稱、 工作階段模式： 推送及工作階段數目。 工作階段數目會遞增每個工作階段。 以下是範例：  
  
 **\<Sw:SnFSessionId\>bankwxyz_applicq1:p:000458\</Sw:SnFSessionId\>**  
  
 "p"表示推入工作階段。 工作階段可以也會顯示為保留項目佇列的授權者。 後續的訊息需要相同的授權者通知。  
  
 傳送訊息到儲存和轉送時，工作階段不適用。  
  
### <a name="push-session-snf"></a>Push 工作階段 SnF  
 SnF 順序的假設如下：  
  
- 用戶端處理序已完成其工作，並可以立即終止。 若要這樣做，開啟 安全性內容必須先清除上發出 SwSec:DestroyContextRequest。 之後 Sw:TermRequest，程序可能 exit （）。  
  
- 另一個用戶端已啟動。 初始化步驟會與第一個用戶端相同。 佇列的版本是執行以做為輸入的基本型別 Sw:ReleaseSnFQueueRequest SwCall。  
  
   SWIFTNet 會停止從佇列的訊息傳遞，因為它已順利處理佇列的版本。  
  
  伺服器會處理一個要求時。 SWIFTNet SnF 提供數個移出佇列的要求。 伺服器回應，或發生逾時之前，這些會緩衝中的網路和 SWIFTNet 連結。  
  
  可以，某些要求已被送達，但尚未認可之前釋出佇列。 SWIFTNet SnF 不會處理這些訊息的任何詳細通知，直到佇列被釋放為止。 這些訊息將會在後續的工作階段重新傳遞。  
  
  伺服器應用程式仍會回應之後，用戶端發出發行該佇列，但通常這不會發生這個狀況，從佇列傳遞的要求正通知是否，它會保留給本機的實作。  
  
## <a name="see-also"></a>另請參閱  
 [InterAct 配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [商務交換的 interAct 配接器訊息](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [InterAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [InterAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [InterAct 配接器不可否認性](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)