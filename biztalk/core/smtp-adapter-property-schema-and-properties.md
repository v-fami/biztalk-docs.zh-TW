---
title: "SMTP 配接器屬性結構描述和屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserName property, SMTP adapters
- EmailBodyTextCharset property [SMTP adapters]
- configuring [SMTP adapters], properties
- Subject property [SMTP adapters]
- EmailBodyFileCharset property [SMTP adapters]
- Attachments property [SMTP adapters]
- SMTP adapters, schemas
- EmailBodyText property [SMTP adapters]
- configuring [SMTP adapters], schemas
- CC property [SMTP adapters]
- ReadReceipt property [SMTP adapters]
- Password property [SMTP adapters]
- ReplyBy property [SMTP adapters]
- DeliveryReceipt property [SMTP adapters]
- SMTP adapters, properties
- SMTPAuthenticate property [SMTP adapters]
- EmailBodyFile property [SMTP adapters]
- schemas, SMTP adapters
- SMTPHost property [SMTP adapters]
- From property [SMTP adapters]
- MessagePartsAttachments property [SMTP adapters]
ms.assetid: 6d062fb6-d728-4525-8f0d-bd3f0f8ff7ca
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09f7dfa67bfad53e43a4a6678ff6ad67705e0e27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter-property-schema-and-properties"></a>SMTP 配接器屬性結構描述和屬性
下表列出 SMTP 配接器屬性結構描述中的屬性。  
  
 **命名空間：** http://schemas.microsoft.com/BizTalk/2003/smtp-properties  
  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|**使用者名稱**|xs:string|指定要用於 SMTP 伺服器驗證的使用者名稱。|  
|**密碼**|xs:string|指定要用於 SMTP 伺服器驗證的密碼。|  
|**SMTPHost**|xs:string|指定傳送訊息時要使用的 SMTP 伺服器名稱。|  
|**來源**|xs:string|指定要置於 SMTP 電子郵件地址**從**標頭。|  
|**[副本]**|xs:string|指定傳送訊息副本的電子郵件地址。|  
|**主旨**|xs:string|指定訊息的主旨標題。|  
|**SMTPAuthenticate**|xs:int|指定要用於 SMTP 伺服器的驗證類型。|  
|**ReadReceipt**|xs:boolean|指定是否在訊息被讀取時傳送確認電子郵件訊息。|  
|**DeliveryReceipt**|xs:boolean|指定傳遞訊息之後是否傳送確認電子郵件訊息。|  
|**EmailBodyText**|xs:string|指定傳送的電子郵件內文所使用的文字。|  
|**EmailBodyTextCharset**|xs:string|指定要用於編碼傳送之電子郵件內文的字元集**EmailBodyText**選項使用。 SMTP 配接器會將轉換**EmailBodyText**設定所指定的字元**EmailBodyTextCharset**。|  
|**EmailBodyFile**|xs:string|指定將用於傳送的電子郵件內文的檔案內容，以及檔案的完整路徑。 在執行階段，SMTP 配接器的主控件必須可以存取此路徑。|  
|**EmailBodyFileCharset**|xs:string|指定要用於編碼傳送之電子郵件內文的字元集**EmailBodyFile**屬性設定。 SMTP 配接器不會在檔案執行任何轉換；檔案必須已經使用此字元集編碼。 若檔案有一個「位元順序標記」(Byte-Order-Mark，BOM)，SMTP 配接器會移除它。|  
|**附加檔案**|xs:string|指定要附加一或多個檔案至電子郵件訊息，以及檔案的完整路徑。 在執行階段，SMTP 配接器的主控件必須可以存取指定的一或多個路徑。|  
|**MessagePartsAttachments**|xs:unsignedInt|指定如何將 BizTalk 訊息部分附加到電子郵件訊息。|  
|**ReplyBy**|xs:dateTime|指定的 dateTime 值**回覆給**外寄電子郵件訊息中的標頭。|  
  
## <a name="see-also"></a>另請參閱  
 [設定 SMTP 配接器](../core/configuring-the-smtp-adapter.md)