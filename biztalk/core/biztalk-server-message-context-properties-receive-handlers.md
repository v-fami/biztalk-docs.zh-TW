---
title: TIBCO Rendezvous 接收訊息內容屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f47e2a0-6ac8-404a-bc0a-c7739911af74
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36f4de92dbe7c4c235a1c9ebd092b28b3a198c92
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014997"
---
# <a name="biztalk-server-message-context-properties-receive-handlers"></a>BizTalk Server 訊息內容屬性 （接收處理常式）
在執行階段，必須可從 BizTalk Server 協調流程存取的，除了有訊息內容以外，還有組成訊息的補充資訊。  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a>已升級為訊息內容屬性的 TIBCO RV 訊息資訊  
 下表列出這些補充資訊：  
  
|資料識別|型別|可路由傳送|接收位置|  
|-------------------------|----------|--------------|----------------------|  
|傳送主旨 [null]|string|是|告訴協調流程此訊息已傳送至哪個主旨。|  
|回覆主旨 [null]|string|是|告訴協調流程，如果有回覆的話，寄件者預期要讓回覆傳送至的位置。|  
|欄位計數 [唯讀]|不帶正負號的整數|否|較上層 訊息中的欄位數目 。 TIBCO RV 所提供的屬性。|  
|CM 寄件者名稱 [唯讀]|string|是|寄件者的 CM 對應名稱。|  
|CM 序號 [唯讀]|long|否|由傳送 TIBCO 傳輸物件指派的序號。|  
|CM 時間限制 [唯讀]|double|否|時間限制，過了此時間限制之後，傳送程式就不再預期其 CM 傳輸會認證訊息傳遞。|  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 中的訊息對應](../core/message-mapping-in-tibco-rendezvous.md)   
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)