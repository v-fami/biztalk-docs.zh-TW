---
title: "存取 WCF 訊息與協調流程中的 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, SOAP headers [WCF services]
- orchestrations, WCF services
- WCF services, SOAP headers
- SOAP headers, WCF messages
ms.assetid: fe02fb02-18d6-4fc6-89e0-b06bdbfa5cb4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bfd1dd4e09071c3d7bcccf28878f19e13acad8a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="accessing-soap-headers-in-wcf-messages-with-orchestrations"></a>使用協調流程存取 WCF 訊息中的 SOAP 標頭
若要存取的協調流程中的內送 WCF 訊息的 SOAP 標頭值，您可以使用內容屬性**WCF。InboundHeaders**。 WCF 配接器複製到輸入訊息中的自訂 SOAP 標頭和標準 SOAP 標頭**WCF。InboundHeaders**屬性。 您也可以使用 WCF 配接器，選取要以程式設計方式升級至或寫入至內容屬性的屬性。 請參閱[SOAP 標頭與已發佈 WCF 服務](../core/soap-headers-with-published-wcf-services.md)如需詳細資訊。  
  
 內容屬性中所包含的值是包含 XML 資料字串\<**標頭**\>根項目，並傳入的 SOAP 標頭複製成為子項目的\< **標頭**\>項目。 若要存取此資料最簡單的方式是使用 BizTalk 運算式編輯器，在**訊息指派**或**運算式**圖形中，將字串載入**XmlDocument**，並使用若要存取特定欄位的 XPath 查詢。 如需在 BizTalk 運算式編輯器 」 中建立 XML 文件的詳細資訊，請參閱[XLANG 的語言](../core/xlang-s-language.md)。  
  
 下列程式碼範例會取得要求 SOAP 標頭中**訊息指派**或**運算式**圖形**WCF。InboundHeaders**屬性：  
  
```  
stringVar = inboundMessageInstance(WCF.InboundHeaders);  
```  
  
 內容屬性與特定的訊息有關聯。 「傳訊引擎」不會將要求訊息中 SOAP 標頭的值自動對應至回應訊息。 在建立 WCF 服務的回應訊息時，您必須特別設定 SOAP 標頭值，透過**WCF。OutboundCustomHeaders**屬性。 下列命令是設定 SOAP 標頭內容屬性的最簡單的方法：  
  
```  
outboundMessageInstance(WCF.OutbounCustomHeaders) = "<headers><Origination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Home</Origination><Destination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Work</Destination></headers>"  
```  
  
 您也可以設定內容屬性，藉由建立**XmlDocument**和寫入的字串值**XmlDocument**內容屬性。  
  
 使用 WCF 配接器存取 SOAP 標頭如何的相關資訊，請參閱 SDK 範例 「 使用自訂 SOAP 標頭與 WCF 配接器 >，網址[http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。  
  
## <a name="see-also"></a>請參閱  
 [存取 WCF 訊息的管線元件中的 SOAP 標頭](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md)   
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [SOAP 標頭與使用 WCF 服務](../core/soap-headers-with-consumed-wcf-services.md)