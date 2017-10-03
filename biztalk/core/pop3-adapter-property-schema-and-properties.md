---
title: "POP3 配接器屬性結構描述和屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, POP3 adapters
- Subject properties [POP3 adapters]
- Date properties [POP3 adapters]
- From properties [POP3 adapters]
- To properties [POP3 adapters]
- POP3 adapters, properties
- configuring [POP3 adapters], schemas
- configuring [POP3 adapters], properties
- CC properties [POP3 adapters]
- Headers properties [POP3 adapters]
- ReplyTo properties [POP3 adapters]
- DispositionNotificationTo properties [POP3 adapters]
ms.assetid: 7a10ae1f-dbcf-4c05-9a50-2503895960f9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b976aba7161272ebdc65da2b5bcd2067c8cd3a5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter-property-schema-and-properties"></a>POP3 配接器屬性結構描述和屬性
下表列出 POP3 配接器屬性結構描述中的屬性。  
  
 **命名空間：** http://schemas.microsoft.com/BizTalk/2003/pop3-properties  
  
|**名稱**|**型別**|**說明**|  
|--------------|--------------|---------------------|  
|**主旨**|xs:string|指定的內容放在**主旨**訊息標頭|  
|**來源**|xs:string|指定放在電子郵件地址**從**標頭欄位的電子郵件訊息。|  
|**若要**|xs:string|指定的電子郵件地址或多個放**至**標頭欄位的電子郵件訊息。|  
|**ReplyTo**|xs:string|指定放在電子郵件地址**ReplyTo**標頭欄位的電子郵件訊息。|  
|**[副本]**|xs:string|指定的電子郵件地址或多個放**CC**標頭欄位的電子郵件訊息。|  
|**日期**|xs:string|指定的內容放在**日期**標頭欄位的電子郵件訊息。|  
|**DispositionNotificationTo**|xs:string|指定的內容放在**DispositionNotificationTo**標頭欄位的電子郵件訊息。|  
|**標頭**|xs:string|指定電子郵件訊息所有標頭欄位的內容。|  
  
## <a name="see-also"></a>另請參閱  
 [設定 POP3 配接器](../core/configuring-the-pop3-adapter.md)