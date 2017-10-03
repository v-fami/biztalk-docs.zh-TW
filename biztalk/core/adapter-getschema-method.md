---
title: "配接器 GetSchema 方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c83340c-a775-435c-9633-3a692611e99e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c40e698b3c373aa4e10a8de2362650a42e71a1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-getschema-method"></a><span data-ttu-id="47e45-102">配接器 GetSchema 方法</span><span class="sxs-lookup"><span data-stu-id="47e45-102">Adapter GetSchema Method</span></span>
<span data-ttu-id="47e45-103">假設參考的 WSDL 檔案只包含結構描述參考，而不包含內嵌的結構描述。</span><span class="sxs-lookup"><span data-stu-id="47e45-103">Suppose the referenced WSDL file contains only schema references and does not contain embedded schemas.</span></span> <span data-ttu-id="47e45-104">在此情況下，您使用**GetSchema**方法**IAdapterConfig**載入從 WSDL 檔案內所參考的結構描述的介面。</span><span class="sxs-lookup"><span data-stu-id="47e45-104">In this case, you use the **GetSchema** method of the **IAdapterConfig** interface to load a schema referenced from within a WSDL file.</span></span>  
  
 <span data-ttu-id="47e45-105">在 file 配接器範例中，修改中的程式碼**GetSchema** AdapterManagement.cs 傳回未包含在 WSDL 檔案的任何外部 XSD 檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="47e45-105">In the file adapter sample, modify the code in the **GetSchema** method of AdapterManagement.cs to return any external XSD files that are not included with the WSDL files.</span></span>  
  
 <span data-ttu-id="47e45-106">下列程式碼取自**GetSchema** AdapterManagement.cs 檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="47e45-106">The following code is from the **GetSchema** method of the AdapterManagement.cs file.</span></span> <span data-ttu-id="47e45-107">由於 Service1.wsdl 檔案包含內嵌的結構描述，它會在此傳回 null。</span><span class="sxs-lookup"><span data-stu-id="47e45-107">It returns null here because the Service1.wsdl file contains embedded schemas.</span></span> <span data-ttu-id="47e45-108">如果情況並非如此，便需要傳回對應於 XSD 結構描述檔案的字串。</span><span class="sxs-lookup"><span data-stu-id="47e45-108">If that were not the case, a string corresponding to an XSD schema file would need to be returned.</span></span>  
  
```  
/// <summary>  
        /// Acquire externally referenced xsd's  
        /// </summary>  
        /// <param name="xsdLocation">Location of schema</param>  
        /// <param name="xsdNamespace">Namespace</param>  
        /// <param name="XSDFileName">Schmea file name (return)</param>  
        /// <returns>Outcome of acquisition</returns>  
        public Result GetSchema(string xsdLocation,  
                                string xsdNamespace,  
                        out string xsdSchema)   
      {  
            xsdSchema = null;  
            return Result.Continue;  
        }  
```