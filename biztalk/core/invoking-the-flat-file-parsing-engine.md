---
title: "叫用一般檔案剖析引擎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- IFFDocumentSpec interface
- pipeline components [custom], flat file documents
- pipeline components [custom], engines
ms.assetid: 9c5d325e-2fae-4291-af13-3fb06657ec0e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90108ff2ade354c51f87499a388ae54135f14c7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoking-the-flat-file-parsing-engine"></a><span data-ttu-id="54596-102">叫用一般檔案剖析引擎</span><span class="sxs-lookup"><span data-stu-id="54596-102">Invoking the Flat File Parsing Engine</span></span>
<span data-ttu-id="54596-103">一般檔案剖析引擎，可以藉由呼叫叫用**剖析**方法**IFFDocumentSpec**介面，接著類型轉換從`IDocumentSpec Interface`擷取自**接著此**。</span><span class="sxs-lookup"><span data-stu-id="54596-103">The flat file parsing engine can be invoked by calling the **Parse** method of the **IFFDocumentSpec** interface, which in turn is typecast from the `IDocumentSpec Interface` retrieved from the **PipelineContext**.</span></span> <span data-ttu-id="54596-104">因為**XmlReader**從傳回**剖析**方法可讓用戶端一次擷取一個節點，這是自訂此剖析器的好機會。</span><span class="sxs-lookup"><span data-stu-id="54596-104">Because the **XmlReader** returned from the **Parse** method allows clients to retrieve one node at a time, this is a good opportunity to customize the parser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54596-105">範例</span><span class="sxs-lookup"><span data-stu-id="54596-105">Example</span></span>  
  
```  
XmlReader xr = docspec.Parse(new DataReader());  
while (xr.Read())  
{  
   switch(xr.NodeType)  
   {  
      case XmlNodeType.Element :  
         // Customize the element  
         //   
         break;  
      case XmlNodeType.Attribute :  
         // Customize the attribute  
         //   
         break;  
      // Customize other types of nodes  
      //   
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="54596-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54596-106">See Also</span></span>  
 [<span data-ttu-id="54596-107">使用一般檔案剖析引擎</span><span class="sxs-lookup"><span data-stu-id="54596-107">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)