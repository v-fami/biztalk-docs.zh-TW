---
title: HTTP 配接器屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AffiliateApplicationName property [HTTP adapters]
- Certificate property [HTTP adapters]
- Password property [HTTP adapters]
- HTTP adapters, properties
- InboundHttpHeaders property [HTTP adapters]
- UseHandlerProxySettings property [HTTP adapters]
- configuring [HTTP adapters], properties
- schemas, HTTP adapters
- RequestTimeout property [HTTP adapters]
- ProxyPassword property [HTTP adapters]
- UseSSO property [HTTP adapters]
- HTTP adapters, schemas
- AuthenticationScheme property [HTTP adapters]
- ProxyName property [HTTP adapters]
- ProxyPort property [HTTP adapters]
- UseProxy property [HTTP adapters]
- configuring [HTTP adapters], schemas
- ContentType property [HTTP adapters]
- MaxRedirects property [HTTP adapters]
- ProxyUsername property [HTTP adapters]
- UserName property, HTTP adapters
ms.assetid: c9b50a82-8cb1-4521-9cf3-5fd77a3531e1
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 416ad39e804a4907dc39c7cef941e9a1bb57d3dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257422"
---
# <a name="http-adapter-property-schema-and-properties"></a>HTTP 配接器屬性結構描述和屬性
下表列出 HTTP 配接器屬性結構描述中的屬性。  
  
 **命名空間：** http://schemas.microsoft.com/BizTalk/2003/http-properties  
  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|**ProxyName**|xs:string|指定 Proxy 伺服器名稱。|  
|**ProxyPort**|xs:int|指定 Proxy 伺服器連接埠。|  
|**UseHandlerProxySettings**|xs:boolean|指定 HTTP 傳送埠是否要對處理常式使用 Proxy 組態。|  
|**UseProxy**|xs:boolean|指定 HTTP 配接器是否使用 Proxy 伺服器。|  
|**RequestTimeout**|xs:int|等待伺服器回應的逾時期間。 若此屬性設定為零 (0)，則系統會根據要求訊息的大小來計算逾時。|  
|**使用者名稱**|xs:string|要提供給伺服器驗證的使用者名稱。|  
|**密碼**|xs:string|要提供給伺服器驗證的使用者密碼。|  
|**ProxyUsername**|xs:string|指定要用於 Proxy 伺服器驗證的使用者名稱。|  
|**ProxyPassword**|xs:string|指定要用於 Proxy 伺服器驗證的使用者密碼。|  
|**MaxRedirects**|xs:int|HTTP 配接器重新導向要求的次數上限。|  
|**ContentType**|xs:string|要求訊息的內容類型。|  
|**AuthenticationScheme**|xs:string|與目的地伺服器搭配使用的驗證類型。|  
|**[MSSQLSERVER 的通訊協定內容]**|xs:string|用戶端 SSL 憑證指紋。|  
|**UseSSO**|xs:boolean|指定 HTTP 傳送埠是否要使用 SSO。|  
|**AffiliateApplicationName**|xs:string|SSO 使用之分支機構應用程式的名稱。|  
|**InboundHttpHeaders**|xs:string|包含來自輸入 HTTP 要求的 HTTP 標頭。|  
|**SubmissionHandle**|xs:string|包含要求訊息的 BizTalk Server 相互關聯 Token (GUID)。|  
|**EnableChunkedEncoding**|xs:boolean|指定 HTTP 配接器是否會使用區塊編碼。|  
|**UserHttpHeaders**|xs:string|包含 HTTP 要求或回應訊息中內含的自訂標頭<br /><br /> 值**UserHttpHeaders**屬性必須具有下列格式：<br /><br /> `Header1: value\r\nHeader2: value\r\n`<br /><br /> **請注意**放置冒號 （:） 和標頭的值之間的空格字元 （）。 空白標頭將會篩除項目。可以使用空值。<br /><br /> 您可以修改下列五個標準 HTTP 標頭使用**UserHttpHeaders**屬性：<br /><br /> 接受<br /><br /> -查閱者<br /><br /> -預期<br /><br /> -如果-修改-自<br /><br /> -使用者代理程式|  
  
## <a name="see-also"></a>另請參閱  
 [設定 HTTP 配接器](../core/configuring-the-http-adapter.md)