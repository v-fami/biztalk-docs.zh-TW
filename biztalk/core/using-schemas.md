---
title: "使用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- pipeline components [custom], code samples
- pipeline components [custom], schemas
ms.assetid: 07e60532-1032-422d-865e-0bd65c45dab6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a7cb71319fef61d3b6cb854b04b41e3815a6129
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-schemas"></a><span data-ttu-id="2fb10-102">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="2fb10-102">Using Schemas</span></span>
<span data-ttu-id="2fb10-103">本節包含與使用結構描述有關之一般工作的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="2fb10-103">This section contains code examples for common tasks associated with using schemas.</span></span>  
  
## <a name="using-xsd-schemas"></a><span data-ttu-id="2fb10-104">使用 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="2fb10-104">Using XSD schemas</span></span>  
 <span data-ttu-id="2fb10-105">`IDocumentSpec Interface`介面代表 XML 結構描述定義語言 (XSD) 結構描述所定義的文件圖形; XSD 的最上層元素的圖形的根項目。</span><span class="sxs-lookup"><span data-stu-id="2fb10-105">The `IDocumentSpec Interface` interface represents a document shape defined by an XML Schema definition language (XSD) schema; the shape is rooted by a top-level element of the XSD.</span></span> <span data-ttu-id="2fb10-106">結構描述會安裝之後，可以擷取由呼叫`IPipelineContext.GetDocumentSpecByType Method`或`IPipelineContext.GetDocumentSpecByName Method`方法**IPipelineContext**介面。</span><span class="sxs-lookup"><span data-stu-id="2fb10-106">After the schema is installed, it can be retrieved by calling the `IPipelineContext.GetDocumentSpecByType Method` or `IPipelineContext.GetDocumentSpecByName Method` methods in the **IPipelineContext** interface.</span></span>  
  
```  
IDocumentSpec docspec = pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## <a name="using-xsd-flat-file-schemas"></a><span data-ttu-id="2fb10-107">使用 XSD 一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="2fb10-107">Using XSD flat file schemas</span></span>  
 <span data-ttu-id="2fb10-108">這兩個**GetDocumentSpecByType**和**GetDocumentSpecByName**方法會傳回**IDocumentSpec**介面。</span><span class="sxs-lookup"><span data-stu-id="2fb10-108">Both the **GetDocumentSpecByType** and **GetDocumentSpecByName** methods return the **IDocumentSpec** interface.</span></span> <span data-ttu-id="2fb10-109">如果結構描述是實際的一般檔案結構描述 （一個具有其他一般檔案專屬附註），您可以類型轉換**IDocumentSpec**到**IFFDocumentSpec**和初始化剖析和序列化從該處的順序。</span><span class="sxs-lookup"><span data-stu-id="2fb10-109">If the schema is actually a flat file schema (one that has additional flat file-specific annotations), you can typecast the **IDocumentSpec** into **IFFDocumentSpec** and initiate parsing and serializing sequences from there.</span></span>  
  
```  
IFFDocumentSpec docspec = (IFFDocumentSpec) pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fb10-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fb10-110">See Also</span></span>  

[<span data-ttu-id="2fb10-111">使用剖析和序列化引擎</span><span class="sxs-lookup"><span data-stu-id="2fb10-111">Using the Parsing and Serializing Engines</span></span>](../core/using-the-parsing-and-serializing-engines.md)