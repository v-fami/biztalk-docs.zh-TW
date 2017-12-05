---
title: "WCF 訊息與協調流程中使用 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, SOAP headers [WCF services]
- WCF services, orchestrations
- WCF services, SOAP headers
ms.assetid: 31c01e35-a2a6-4ea9-bdf4-6d4311268dbe
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e8248ec62e75a058566eefef1942e1f82061dbb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="using-soap-headers-in-wcf-messages-with-orchestrations"></a>在協調流程使用 WCF 訊息中的 SOAP 標頭
若要傳送外寄 WCF 訊息自訂 SOAP 標頭在協調流程中，您可以使用內容屬性， **WCF。OutboundCustomHeaders**。 WCF 配接器傳送自訂 SOAP 標頭結合的標準 SOAP 標頭，WCF 基礎結構會使用適用於 Web 服務標準，例如 Ws-addressing、 Ws-security 和 Ws-atomictransaction。 當您使用**OutboundCustomHeaders**屬性，屬性必須有\<**標頭**\>元素是根項目。 所有自訂 SOAP 標頭必須置於\<**標頭**\>項目。 如果自訂 SOAP 標頭值為空字串，您必須指派\<**標頭**\>\</**標頭**\>或\<**標頭**/ \>至**OutboundCustomHeaders**屬性。  
  
 針對協調流程，SOAP 標頭內容屬性會設為包含 XML 資料的字串。 使用 BizTalk 運算式編輯器 中設定這些字串**訊息指派**或**運算式**圖形。 如需如何搭配 WCF 配接器使用 SOAP 標頭的詳細資訊，請參閱 SDK 範例，使用自訂 SOAP 標頭搭配 WCF 配接器，從[http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。  
  
 下列範例 (擷取自「訊息指派」或「運算式」圖形) 說明設定內容屬性的字串：  
  
```  
outboundMessageInstance(WCF.OutboundCustomHeaders) = "<headers><Origination>Home</Origination><Destination>Work</Destination></headers>"  
```  
  
## <a name="creating-an-xmldocument-to-set-context-properties"></a>建立 XmlDocument 來設定內容屬性  
 您可以設定**WCF。OutboundCustomHeaders**內容屬性，藉由建立**XmlDocument**和寫入的字串值**XmlDocument**內容屬性。 宣告類型的變數**XMLDocument**並指派 XML 資料。  
  
 下列範例說明如何宣告類型的變數**XMLDocument**並指派 XML 資料：  
  
```  
xmlDoc.LoadXml("<headers><Origination>Home</Origination><Destination>Work</Destination></headers>");  
```  
  
 下列範例說明如何設定內容屬性：  
  
```  
RequestMessageInstance(WCF.OutboundCustomHeaders) = xmlDoc.OuterXml;  
```  
  
 如需有關如何使用 BizTalk 運算式編輯器的詳細資訊，請參閱[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)。 如需有關呼叫[!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)]類別，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
## <a name="see-also"></a>請參閱  
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [SOAP 標頭與使用的 WCF 服務](../core/soap-headers-with-consumed-wcf-services.md)   
 [SOAP 標頭與已發佈的 WCF 服務](../core/soap-headers-with-published-wcf-services.md)