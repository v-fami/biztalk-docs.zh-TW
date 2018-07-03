---
title: Continuation 和 ContinuationID 節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- continuation tokens
- Continuation nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- BAM, correlating activities
- activities, linking
- activities, continuation tokens
- ContinuationID nodes [Tracking Profile Editor]
ms.assetid: aa050660-66f7-4084-b6bf-b9319ce625af
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f8baf50c8384d939ba477abf1d33f4553d4fa4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021121"
---
# <a name="continuation-and-continuationid-nodes"></a>Continuation 和 ContinuationID 節點
接續提供有關下列資訊的 BAM 基礎結構指導：  
  
- 預期的事件發生順序  
  
- 處理唯一識別碼任何變更的方法，此識別碼與事件項目相互關聯  
  
  換句話說，接續會定義這項資訊在活動參與者之間的傳輸。 在下列情況中會發生傳輸：  
  
- 從活動開始到結束期間，ActivityID 有所變更。 舉例來說，假設您有兩個相關的訊息，例如訂單編號與銷售訂單編號。 各自都有指定的唯一編號，例如訂單編號是 123456，銷售訂單編號是 987654。 您可以使用接續使訂單編號與銷售訂單兩者的唯一識別碼相等，如此，無論哪個唯一識別碼與內送事件相關聯，都可以使事件與常用活動相互關聯。  
  
- 您從一個執行階段環境轉換到另一個執行階段環境。 例如，假設有一個應用程式提供訂單到 BizTalk Server 傳訊管線，然後叫用協調流程，與協調流程，然後將控制權傳給傳送出貨通知的應用程式，在您有兩個環境轉換： 從傳訊管線轉換協調流程和協調流程到傳訊管線。  
  
  當選取用於接續的屬性時，請記得一個要點，就是必須從相同的內容對應這些屬性。  
  
  例如，如果您有屬性 Message.InterchangeID 和 servicecontext.InterchangeID，則您似乎可以使用 InterchangeID 來建立接續。 但是，如果訊息來自於不同的內容，您將無法使用 InterchangeID (或其他屬性) 來可靠地建立接續。  
  
## <a name="working-with-continuation-nodes"></a>使用 Continuation 節點  
 Continuation 節點含有指示唯一執行個體識別碼，也稱為的資料項目*接續 token*。 利用接續 Token，開發人員就可以使用 ContinuationID 節點與其他活動連結。  
  
 三種使用 Continuation 和 ContinuationID 節點的基本實例：  
  
- 協調流程到協調流程  
  
- 協調流程到 BizTalk 解決方案  
  
- BizTalk 解決方案到協調流程  
  
  在協調流程實例中，TPE 必須定義 Continuation 節點和 ContinuationID 節點，並且這兩個節點的名稱必須相同，BAM 才能使活動相互關聯。  
  
  在協調流程到 BizTalk 解決方案的實例中，您會使用 TPE 定義 Continuation 節點，而開發人員會建立使用 BAM API 的解決方案來處理接續的目的部分。  
  
  在 BizTalk 解決方案到協調流程的實例中，開發人員會使用 BAM API 提供接續組的起源，而且您會使用 TPE 定義 ContinuationID 節點。  
  
> [!NOTE]
>  雙向連接埠可以在任何一個方向運作，也就是說，攔截通過連接埠的資料可能需要啟用接續 (視 BizTalk 解決方案的行為而定)。 舉例來說，如果活動在任一方向記錄 BizTalk Server 傳訊連接埠啟動的 PortEndTime (如果項目的名稱依序是 MessageReceived 和 MessageSent)，您就必須在這兩者之間建立接續。 只要有一個以上的事件資料流提供給 BAM 活動，並且每個實作碰觸點都有不同的事件資料流 (例如 BTS 內送訊息、BTS 外寄訊息、協調流程、自訂應用程式與 Web 服務)，就需要使用接續。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立接續](../core/how-to-create-a-continuation.md)   
 [TPE 活動檢視節點](../core/tpe-activity-view-nodes.md)