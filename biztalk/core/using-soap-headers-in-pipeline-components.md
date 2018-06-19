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
# <a name="using-soap-headers-in-pipeline-components"></a><span data-ttu-id="ffea8-102">管線元件中使用 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="ffea8-102">Using SOAP Headers in Pipeline Components</span></span>
<span data-ttu-id="ffea8-103">若要存取管線元件中的 SOAP 標頭內容屬性，您使用內容屬性名稱和目標命名空間的組合中所述[協調流程中使用 SOAP 標頭](../core/using-soap-headers-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="ffea8-103">To access the SOAP header context properties in pipeline components, you use a combination of the context property name and target namespace as discussed in [Using SOAP Headers in Orchestrations](../core/using-soap-headers-in-orchestrations.md).</span></span>  
  
 <span data-ttu-id="ffea8-104">下列程式碼範例會設定要求 SOAP 標頭屬性名稱的傳送管線元件中**OrigDest**:</span><span class="sxs-lookup"><span data-stu-id="ffea8-104">The following code example sets the request SOAP header in a send pipeline component for a property name **OrigDest**:</span></span>  
  
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
  
 <span data-ttu-id="ffea8-105">如需管線元件的詳細資訊，請參閱[開發自訂管線元件](../core/developing-custom-pipeline-components.md)。</span><span class="sxs-lookup"><span data-stu-id="ffea8-105">For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffea8-106">當您從協調流程使用 (呼叫) Web 服務時，SOAP 配接器只支援通過型接收和傳送管線。</span><span class="sxs-lookup"><span data-stu-id="ffea8-106">When you consume (call) Web services from an orchestration, the SOAP adapter only supports pass-through style receive and send pipelines.</span></span> <span data-ttu-id="ffea8-107">您可以使用自訂管線，但它不能包含可修改訊息內文部分的元件。</span><span class="sxs-lookup"><span data-stu-id="ffea8-107">You can use a custom pipeline, but it cannot contain components that modify the body parts of the message.</span></span> <span data-ttu-id="ffea8-108">這些元件包括「XML 組合器」、「XML 解譯器」和「XML 驗證器」元件。</span><span class="sxs-lookup"><span data-stu-id="ffea8-108">These components include the XML Assembler, XML Disassembler, and XML Validator components.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffea8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffea8-109">See Also</span></span>  
 <span data-ttu-id="ffea8-110">[預設管線](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="ffea8-110">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 [<span data-ttu-id="ffea8-111">SOAP 標頭與已使用的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="ffea8-111">SOAP Headers with Consumed Web Services</span></span>](../core/soap-headers-with-consumed-web-services.md)