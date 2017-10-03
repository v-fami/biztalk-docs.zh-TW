---
title: "WCF 訊息的管線元件中使用 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, SOAP headers
- SOAP headers, pipeline components
- SOAP headers, WCF services
- WCF services, SOAP headers
ms.assetid: b02f2913-4948-4de9-bc59-73bab40aa1a0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf40cf5a81188dae0174199f16229daf61115796
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers-in-wcf-messages-with-pipeline-components"></a>搭配管線元件使用 WCF 訊息中的 SOAP 標頭
您可以在管線元件中搭配 WCF 配接器設定自訂 SOAP 標頭。 您可以使用內容屬性名稱的組合**OutboundCustomHeaders**，和目標命名空間**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**。 當您使用**OutboundCustomHeaders**屬性，屬性必須有\<**標頭**> 元素是根項目。 所有自訂 SOAP 標頭必須置於\<**標頭**> 項目。 如果自訂 SOAP 標頭值為空字串，您必須指派\<**標頭**>\</**標頭**> 或\< **標頭**/ > 若要**OutboundCustomHeaders**屬性。 如需如何搭配 WCF 配接器使用 SOAP 標頭的詳細資訊，請參閱 SDK 範例，使用自訂 SOAP 標頭搭配 WCF 配接器，從[http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。  
  
 下列程式碼範例在名為屬性的傳送管線元件中設定自訂 SOAP 標頭**OutboundCustomHeaders**:  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
      {  
       string stringVar = "<headers>  
             <Origination>Home</Origination>  
             <Destination>Work</Destination>  
          </headers>";  
inmsg.Context.Write("OutboundCustomHeaders","http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties", stringVar);  
      }  
   catch (Exception ex)  
      {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
      }  
return inmsg;  
}  
```  
  
 如需管線元件的詳細資訊，請參閱[開發自訂管線元件](../core/developing-custom-pipeline-components.md)。  
  
> [!NOTE]
>  不可設定 WCF 基礎結構用於 Web 服務標準的標準 SOAP 標頭，例如 WS-Addressing、WS-Security 和 WS-AtomicTransaction。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 訊息與協調流程中使用 SOAP 標頭](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md)   
 [SOAP 標頭與使用的 WCF 服務](../core/soap-headers-with-consumed-wcf-services.md)   
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [SOAP 標頭與已發佈的 WCF 服務](../core/soap-headers-with-published-wcf-services.md)