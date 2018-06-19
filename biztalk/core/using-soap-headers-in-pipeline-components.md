---
title: 管線元件中使用 SOAP 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP headers, code samples
- SOAP headers, creating
- SOAP headers, pipelines
- SOAP headers, properties
- pipelines, SOAP headers
- Web services, SOAP headers
- creating, SOAP headers
ms.assetid: 5b4a8902-e8f5-44a4-88f7-17f47a9deecd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c11b74aafe53150ced42d0c53a2e19a2c5080fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287270"
---
# <a name="using-soap-headers-in-pipeline-components"></a>管線元件中使用 SOAP 標頭
若要存取管線元件中的 SOAP 標頭內容屬性，您使用內容屬性名稱和目標命名空間的組合中所述[協調流程中使用 SOAP 標頭](../core/using-soap-headers-in-orchestrations.md)。  
  
 下列程式碼範例會設定要求 SOAP 標頭屬性名稱的傳送管線元件中**OrigDest**:  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
      {  
       string stringVar = "<?xml version=\"1.0\"?>  
          <OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">  
             <Origination>Home</Origination>  
             <Destination>Work</Destination>  
          </OrigDest>";  
inmsg.Context.Write("OrigDest","http://schemas.microsoft.com/BizTalk/2003/SOAPHeader", stringVar);  
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
>  當您從協調流程使用 (呼叫) Web 服務時，SOAP 配接器只支援通過型接收和傳送管線。 您可以使用自訂管線，但它不能包含可修改訊息內文部分的元件。 這些元件包括「XML 組合器」、「XML 解譯器」和「XML 驗證器」元件。  
  
## <a name="see-also"></a>另請參閱  
 [預設管線](../core/default-pipelines.md)   
 [SOAP 標頭與已使用的 Web 服務](../core/soap-headers-with-consumed-web-services.md)