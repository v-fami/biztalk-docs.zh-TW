---
title: "關於工作階段 Management1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1848619-d97a-4f1e-ba94-59861bd7aedf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 336deb34e5587e64c5177cd0a439c756cf0f2b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="about-session-management"></a>關於工作階段管理
Microsoft BizTalk Adapter for JD Edwards OneWorld 建立連線工作階段，以傳送呼叫給 JD Edwards OneWorld 伺服器。 當呼叫終止時，工作階段會放在集區中，供後續呼叫重複使用。 配接器會建立多個連線工作階段，以處理對 JD Edwards OneWorld 伺服器的並行呼叫。 集區會定期清除，以移除不再需要的工作階段。  
  
 Microsoft BizTalk Adapter for JD Edwards OneWorld 提供兩個訊息內容屬性來控制，必須發生呼叫相同的工作階段內。  
  
|名稱|類型|預設值|  
|----------|----------|-------------|  
|JDE.SessionID|int|0|  
|JDE.ReserveSession|boolean|false|  
  
 如果商務功能只需呼叫 JD Edwards OneWorld 伺服器一單一工作階段管理。 配接器可以取用任何可用的工作階段，而且工作階段仍然可供任何後續呼叫使用。 在這種情況下，您可以忽略訊息內容屬性，因為預設值都適用。  
  
 有些 JD Edwards OneWorld 功能需要多次呼叫 JD Edwards OneWorld 伺服器，例如在建立 SalesOrder 時。 第一次呼叫 BeginDoc 時，會建立空白 SalesOrder。 接著，對 EditLine 的每個後續呼叫都會在 SalesOrder 中加入一個明細項目。 最後，對 EndDoc 的呼叫會關閉 SalesOrder。  
  
```  
BeginDoc  
   EditLine  
   EditLine  
   ...  
EndDoc  
```  
  
 若要成功，單一 SalesOrder 的所有呼叫都必須在相同的工作階段傳送。 若要執行這項操作，請指派訊息內容屬性，以指示配接器如何處理工作階段。 對於 SalesOrder 範例，下列值會指派給訊息內容屬性，以處理 JD OneWorld 工作階段：  
  
|函數|SessionID|ReserveSession|  
|--------------|---------------|--------------------|  
|BeginDoc|0|true|  
|EditLine|從 BeginDoc 回覆複製|true|  
|EditLine|從 BeginDoc 回覆複製|true|  
|EndDoc|從 BeginDoc 回覆複製|false|  
  
-   對於第一個呼叫，配接器可以自由選取任何可用的工作階段 (因為 SessionID 是零)。  
  
-   配接器會傳回 BeginDoc 回覆中所使用的 SessionID。  
  
-   ReserveSession 屬性會告知配接器保留此工作階段，以供明確要求此工作階段的後續呼叫使用。 其他呼叫都會刻意重複使用此工作階段，因為它是保留的工作階段。  
  
-   藉由將 SessionID 設定為 BeginDoc 中所傳回的值，後續呼叫便可以要求此工作階段。  
  
-   ReserveSession 屬性設定為 true (至少直到一系列呼叫中的最後一個呼叫為止)。  
  
-   最後一個呼叫會將 ReserveSession 設定為 false，讓任何後續呼叫都可以使用工作階段。 不過，協調流程可以選擇保留工作階段給更多呼叫使用。  
  
 如果有一段時間工作階段未使用，集區會對此工作階段進行記憶體回收，即使此工作階段仍然因為錯誤而遭保留也一樣。  
  
 如需訊息內容屬性的詳細資料，請參閱 BizTalk Server 文件。  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息內容屬性](../core/using-message-context-properties2.md)   
 [如何指派訊息內容屬性值](../core/how-to-assign-message-context-property-values2.md)   
 [教學課程： 使用 BizTalk Adapter for JD Edwards OneWorld](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld.md)