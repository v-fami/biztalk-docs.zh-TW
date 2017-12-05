---
title: "訊息分隔符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, events
- messages, XML messages
- events
- delimiters
- messages, delimiters
- flat files
- XML messages
- messages, flat files
ms.assetid: d25bf6db-5512-4c82-be0e-00da024c55d1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e25e4fad2eb9e32c87f8a395bd924fc4a1f2eb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="message-delimiters"></a>訊息的分隔符號
HL7 標準所定義的訊息事件的形式如下：  
  
-   **一般檔案**。 HL7 版本 2.4 及更早版本所定義的訊息事件的一般檔案形式。  
  
-   **XML**。 HL7 版本 2.XML 和第 3 版所定義的訊息事件 XML 檔案的形式。  
  
 標準 HL7 未遵循位置的格式，因為它會使用分隔符號來定義區段、 欄位、 元件和子元件層級的一般檔案。 下表列出由 HL7 一般檔案的預設分隔符號。  
  
|分隔符號|值|使用方式|  
|---------------|-----------|-----------|  
|區段結束字元|\<cr\>|所傳回的歸位字元會終止區段記錄。 您無法變更此值。|  
|欄位的分隔符號|&#124;|縱線字元分隔的區段內的兩個相鄰的資料欄位。 此字元，也會將從第一個資料欄位中每個區段的區段識別碼。|  
|元件分隔符號|^|Hat 字元會分隔相鄰資料的元件 HL7 標準所允許的欄位。|  
|子元件分隔符號|&|& 符號字元會分隔相鄰資料子元件 HL7 標準所允許的欄位。 如果有任何子元件，您就可以省略這個字元。|  
|重複分隔符號|~|波狀符號字元分隔的欄位中的子元件或元件多個項目允許 HL7 標準。|  
|逸出字元|\|與 ST、 TX 或全文檢索資料類型，符合任何欄位或 ED 資料類型的資料 （第四個） 元件，您可以使用逸出字元。 如果沒有逸出字元存在訊息中，您可以省略這個字元。 不過，您必須包括它如果您使用的訊息中的子元件。|  
  
## <a name="see-also"></a>請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)