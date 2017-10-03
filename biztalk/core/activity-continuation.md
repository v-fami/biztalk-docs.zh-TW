---
title: "活動接續 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- continuation tokens
- activities [BAM], code samples
- activities [BAM], continuation tokens
- continuations, activities [BAM]
- code samples, activities [BAM]
ms.assetid: 47d91ae6-77c1-4efb-940f-a7b3a325e5bd
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7568da0647ae9847c3de2d060d75a53466b9709
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="activity-continuation"></a>活動接續
BAM 活動 (也稱為商務活動) 可以跨越多個異質應用程式 (例如，從某個管線進入兩個協調流程，再到某個商務營運系統應用程式，然後到另一個管線)。 BAM 基礎結構可讓開發人員概念與多個應用程式的事件相互關聯 」*接續*，」 所示，如下圖。  
  
 ![](../core/media/ebiz-prog-bam-fig4-app-scopes-cont-tokens.gif "ebiz_prog_bam_fig4_app_scopes_cont_tokens")  

## <a name="applications"></a>應用程式  
 活動的第一個階段發生於 Sales (銷售) 應用程式，第二個階段則發生於 Packaging & Assembly (包裝和組裝) 應用程式，最後由 Shipping (送貨) 應用程式提供送貨進度。 每個應用程式使用不同的識別碼，目前的工作單位： 訂單號碼 (PO)、 銷售訂單號碼 (SO) 和送貨單號碼 (UPS)。 若要將兩個不同應用程式的事件相互關聯，您必須：  
  
-   識別接續 Token，這是兩個應用程式都能使用的唯一資料片段 (例如，彼此交換的訊息部分)。  
  
-   在第一個應用程式中呼叫 EnableContinuation，並傳遞接續 Token 和目前的 ActivityID。  
  
-   請勿在第二個應用程式中呼叫 BeginActivity。  
  
-   在第二個應用程式中使用接續 Token 代替 ActivityID，引發所有後續事件。  
  
 下列程式碼範例示範如何在三個應用程式之間使用活動接續：  
  
 **訂單應用程式**  
  
```  
string oID="PO#123";  
string soID="SO#265";  
es.BeginActivity("PurchaseOrder",poID);  
es.UpdateActivity("PurchaseOrder",poID,  
    "POReceived",DateTime.UtcNow,  
    "POAmount",100,  
"CustomerCity","Seattle");  
es.EnableContinuation(  
   "PurchaseOrder",poId,soID);  
es.EndActivity("PurchaseOrder",poID);  
```  
  
 **履行應用程式**  
  
```  
string soID="SO#265";  
string upsID="UPS#97892";  
es.UpdateActivity("PurchaseOrder",soID,  
    "POApproved",DateTime.UtcNow,  
    "ProductName","ProductA");  
es.EnableContinuation(  
   "PurchaseOrder",soID,upsID);  
es.EndActivity("PurchaseOrder",soID);  
```  
  
 **傳送應用程式**  
  
```  
string upsID="UPS#97892"  
es.UpdateActivity("PurchaseOrder", upsID,  
"POShipped",DateTime.UtcNow);  
es.EndActivity("PurchaseOrder",upsID)  
  
```  
  
 請依循下列指導方針，在程式碼中使用活動接續：  
  
-   除非使用者必須將不同應用程式的工作視為相同活動的一部分，否則切勿使用接續。 如果每個應用程式的工作對使用者而言是各有其意義的活動，每個應用程式均應使用不同的活動，然後建立活動關係。  
  
-   如果應用程式的工作單位並非一對一關係，則可使用活動關係但不應使用接續，例如，一張銷售訂單有數個送貨地點時。  
  
-   若以同步方式將資料傳送至 BAM (使用 DirectEventStream)，且 ActivityID 傳遞至所有參與的元件，就不需要使用接續。  
  
-   若以非同步方式將資料傳送至 BAM (使用 BufferedEventStream 或透過協調流程)，則即使 ActivityID 傳遞至所有元件，仍然必須使用接續。 在此情況下，每個應用程式必須使用不同的 ActivityID，所以請用唯一字串做為字首 (例如，加上應用程式名稱)。 需要這麼做是因為，不同的應用程式可能以隨機順序將資料送達 BAM，而 BAM 必須隱藏失序的事件以確保查詢和彙總結果正確。  
  
-   使用接續的應用程式不需要重新撰寫就能交換更多資料。  
  
## <a name="see-also"></a>另請參閱  
  
 [BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md)   
 [BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)   
 [BAM 端對端 （BizTalk Server 範例）](../core/bam-end-to-end-biztalk-server-sample.md)