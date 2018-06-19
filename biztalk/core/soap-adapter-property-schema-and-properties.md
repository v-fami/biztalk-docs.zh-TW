---
title: SOAP 配接器屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ProxyUsername property [SOAP adapters]
- ClientConnectionTimeout property [SOAP adapters]
- SOAP adapters, properties
- ProxyAddress property [SOAP adapters]
- UserDefined property [SOAP adapters]
- AssemblyName property [SOAP adapters]
- ClientCertificate property [SOAP adapters]
- AffiliateApplicationName property [SOAP adapters]
- schemas, SOAP adapters
- AuthenticationScheme property [SOAP adapters]
- UserName property, SOAP adapters
- UseProxy property [SOAP adapters]
- Password property [SOAP adapters]
- configuring [SOAP adapters], schemas
- UnknownHeaders property [SOAP adapters]
- configuring [SOAP adapters], properties
- UseSoap12 property [SOAP adapters]
- UseHandlerSetting property [SOAP adapters]
- SOAP adapters, schemas
- ProxyPassword property [SOAP adapters]
- UseSSO property [SOAP adapters]
- MethodName property [SOAP adapters]
- ProxyPort property [SOAP adapters]
ms.assetid: b471cf4b-2d87-4aa2-ae4a-f48517fd4c94
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a24a9ccfc3a07abe925761fe2d6886646981be9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277510"
---
# <a name="soap-adapter-property-schema-and-properties"></a>SOAP 配接器屬性結構描述和屬性
下表列出 SOAP 配接器屬性結構描述中的屬性。  
  
 **命名空間：** http://schemas.microsoft.com/BizTalk/2003/soap-properties  
  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|**AssemblyName**|xs:string|識別要載入和執行的 .NET 類型與組件。|  
|**MethodName**|xs:string|識別在 .NET 組件上要叫用的目標方法。|  
|**使用者名稱**|xs:string|要提供給伺服器驗證的使用者名稱。|  
|**密碼**|xs:string|要提供給伺服器驗證的使用者密碼。|  
|**ClientCertificate**|xs:string|用戶端 SSL 憑證的指紋。|  
|**UseProxy**|xs:Boolean|指定 SOAP 配接器是否要使用 Proxy 伺服器。|  
|**ProxyAddress**|xs:string|指定 Proxy 伺服器位址。|  
|**ProxyPort**|xs:int|指定 Proxy 伺服器連接埠。|  
|**ProxyUsername**|xs:string|指定要用於 Proxy 伺服器驗證的使用者名稱。|  
|**ProxyPassword**|xs:string|指定要用於 Proxy 伺服器驗證的使用者密碼。|  
|**UnknownHeaders**|xs:string|指定未知 SOAP 標頭的序列化清單。|  
|**AffiliateApplicationName**|xs:string|定義 SSO 使用之分支機構應用程式的名稱。|  
|**AuthenticationScheme**|xs:string|指定要提供給目的地伺服器的驗證類型。|  
|**UseSSO**|xs:boolean|指定 SOAP 配接器是否對傳送埠使用 SSO。|  
|**UseHandlerSetting**|xs:boolean|指定 SOAP 傳送埠是否要對處理常式使用 Proxy 組態。|  
|**ClientConnectionTimeout**|xs:int|指定等待伺服器回應的逾時期間。 若設定為零 (0)，則系統會根據要求訊息的大小來計算逾時。|  
|**UserDefined**|xs:string|定義使用者定義類別。|  
|**UseSoap12**|xs:boolean|指定是否產生支援 SOAP 1.2 通訊協定的 Proxy 程式碼。|  
  
## <a name="see-also"></a>另請參閱  
 [設定 SOAP 配接器](../core/configuring-the-soap-adapter.md)