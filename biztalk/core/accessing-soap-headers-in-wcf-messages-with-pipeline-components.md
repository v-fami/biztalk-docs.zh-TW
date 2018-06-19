---
title: 存取 WCF 訊息的管線元件中的 SOAP 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, WCF services
- WCF services, pipeline components
- pipeline components, SOAP headers
- SOAP headers, pipeline components
- WCF services, SOAP headers
- SOAP headers, WCF messages
ms.assetid: 5e24afa3-b2e6-472e-8890-a47b59573304
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf8bc9c2c17172cb29ee75bfbfc4aaee841848fa
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965100"
---
# <a name="accessing-soap-headers-in-wcf-messages-with-pipeline-components"></a>使用管線元件存取 WCF 訊息中的 SOAP 標頭
若要存取 SOAP 標頭搭配 WCF 配接器管線元件中，您可以使用內容屬性名稱的組合**InboundHeaders**，和目標命名空間**http://schemas.microsoft.com/BizTalk/2006/01/配接器/WCF-內容**。 WCF 配接器複製到輸入訊息中的自訂 SOAP 標頭和標準 SOAP 標頭**InboundHeaders**屬性。 WCF 配接器也可讓您以程式設計方式選取您想要升級或以程式設計的方式寫入內容屬性的屬性。 請參閱[SOAP 標頭與已發佈 WCF 服務](../core/soap-headers-with-published-wcf-services.md)如需詳細資訊。  
  
 內容屬性中所包含的值是包含 XML 資料字串\<**標頭**\>根項目，並傳入的 SOAP 標頭複製成為子項目的\< **標頭**\>項目。 使用 WCF 配接器存取 SOAP 標頭如何的相關資訊，請參閱 SDK 範例 「 使用自訂 SOAP 標頭與 WCF 配接器 >，網址[http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。  
  
 下列程式碼的自訂管線元件的接收管線元件中取得要求 SOAP 標頭**InboundHeaders**屬性：  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
   {  
   string stringVar = inmsg.Context.Read("InboundHeaders",    "http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties").ToString();  
   }  
   catch (Exception ex)  
   {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
   }  
return inmsg;  
}  
```  
  
 如需管線元件的詳細資訊，請參閱[開發自訂管線元件](../core/developing-custom-pipeline-components.md)。  
  
## <a name="see-also"></a>請參閱  
 [存取 WCF 訊息與協調流程中的 SOAP 標頭](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md)   
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [SOAP 標頭與使用 WCF 服務](../core/soap-headers-with-consumed-wcf-services.md)