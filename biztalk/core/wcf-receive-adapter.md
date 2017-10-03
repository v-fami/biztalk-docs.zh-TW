---
title: "WCF 接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, headers
- receive adapters, Web service headers
- SOAP messages, extracting information
- SOAP messages, WCF adapters
- WCF adapters, receive adapters
- messages, SOAP
- receive adapters, WCF adapters
- Web services, headers
- headers [messages]
- SOAP messages, receive adapters
ms.assetid: 6b3d5df1-5d9d-4240-a98f-ea29c3272e38
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb8ea12087b5884370edce13f3ddc6fd6853c7d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-receive-adapter"></a>WCF 接收配接器
WCF 接收配接器可讓您接收 WCF 服務要求。  
  
## <a name="extracting-the-biztalk-message-body-from-the-soap-message"></a>從 SOAP 訊息擷取 BizTalk 訊息內文  
 使用下列其中一種選項，便可從 SOAP 訊息擷取輸入 BizTalk 訊息內文：  
  
-   擷取 SOAP Body 元素的內容  
  
-   擷取整個 SOAP Envelope  
  
-   使用 XPath 運算式以擷取 SOAP Envelope 內元素的內容  
  
 您可以在傳輸屬性對話方塊中設定這些選項。  
  
#### <a name="extract-the-content-of-the-soap-body-element"></a>擷取 SOAP Body 元素的內容  
 若是選取這個選項，SOAP Body 元素的內部內容就會讀取自 SOAP 訊息，並且放入 BizTalk 訊息的內文部分。  
  
#### <a name="extract-the-entire-soap-envelope"></a>擷取整個 SOAP Envelope  
 若是選取這個選項，包括標記的整個 SOAP Envelope 就會放入 BizTalk 訊息的內文部分。  
  
#### <a name="extract-the-content-of-the-element-by-using-an-xpath-expression"></a>使用 XPath 運算式以擷取元素的內容  
 若是選取這個選項，由 XPath 運算式所找出 SOAP Body 內元素的內部內容就會放入 BizTalk 訊息的內文部分。 內文元素中的其他資料則會略過。 您也必須指定節點編碼 -- 例如，XML、Base64、Hex 或 String 編碼。  
  
> [!NOTE]
>  若是選取 XML 編碼，XML 本文內元素的外部內容就會由 XPath 運算式所找出，並放入 BizTalk 訊息的內文部分。  
  
## <a name="handling-web-services-headers"></a>處理 Web 服務標頭  
 接收配接器會將標準 Web 服務標頭的子集升級到 BizTalk 訊息內容，以利根據這些標頭的值來輕鬆進行存取和路由。 下表列出將由接收配接器儲存到訊息內容的屬性。 在下列命名空間下定義的屬性： http://www.w3.org/2005/addressing 及 http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties。  
  
|標頭|BizTalk 屬性名稱|是否有提升？|  
|------------|---------------------------|------------------|  
|動作|動作|是|  
|MessageID|MessageID|否|  
|若要|若要|是|  
|ReplyTo/Address|ReplyTo|是|  
|From/Address|來源|是|  
|Sequence/Identifier|SequenceId|是|  
|Sequence/MessageNumber|SequenceNumber|是|  
|Sequence/LastMessage|SequenceLastMessage|是|  
|\<在 soap: Header >|InboundHeaders|否|  
  
## <a name="see-also"></a>另請參閱  
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [WCF 傳送配接器](../core/wcf-send-adapter.md)   
 [WCF 配接器有哪些？](../core/what-are-the-wcf-adapters.md)