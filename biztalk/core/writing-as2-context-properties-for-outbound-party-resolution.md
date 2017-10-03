---
title: "撰寫 AS2 內容屬性的輸出合作對象解析 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 808d63d9-076d-4eed-8420-aee12b130fee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c89804c42554825e387d01ff592e3a628e8225b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="writing-as2-context-properties-for-outbound-party-resolution"></a>撰寫 AS2 內容屬性以執行輸出合作對象解析
透過 AS2To 內容屬性或 `Http.UserHttpHeaders` 內容屬性中的 AS2To 屬性，便可以執行輸出 AS2 訊息的協議解析。 不過，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在收到 AS2 訊息時，並不會將 AS2To 屬性寫至內容。 如果您想對 AS2To 或 UserHttpHeaders 內容屬性執行協議解析，必須撰寫自訂協調流程或自訂管線元件。 只有在傳送埠未連結至協議時，才需要這麼做。  
  
 若是自訂協調流程，您可以使用下列程式碼，將 AS2-To 附加至現有 `Http.UserHttpHeaders` 內容屬性的開頭：  
  
```  
Message_1(Http.UserHttpHeaders) = “AS2-To: MyPartner\r\n” + Message_1(Http.UserHttpHeaders);  
```  
  
 若是自訂管線元件，則可以使用下列程式碼，將 AS2-To 附加至現有 `Http.UserHttpHeaders` 內容屬性的開頭。 您必須先將 AS2-To 附加至 `Http.UserHttpHeaders` 內容屬性，As2Encoder 元件才能處理訊息。  
  
```  
string strName="UserHttpHeaders";  
string strValue = "AS2-To: MyPartner\r\n" + (string)baseMessage.Context.Read(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties");  
baseMessage.Context.Write(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties", strValue);  
```  
  
 如需有關升級`EDIIntAS.AS2To`屬性或`BTS.UseHttpHeaders`屬性至內容，請參閱中的 「 升級 AS2 標頭內容屬性 」[透過 FILE 傳送埠傳送 AS2 訊息](../core/sending-an-as2-message-over-a-file-send-port.md)。  
  
 您可以加入要寫入 http 標頭的自訂管線元件的程式碼。UserHttpHeaders 內容屬性至訊息，請參閱[透過 FILE 傳送埠傳送 AS2 訊息](../core/sending-an-as2-message-over-a-file-send-port.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)