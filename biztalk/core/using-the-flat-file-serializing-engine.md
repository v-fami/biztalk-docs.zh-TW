---
title: "使用一般檔案序列化引擎 |Microsoft 文件"
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
ms.assetid: 0a519f0f-392b-4fa3-ab08-f09012d033af
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4f39f42c3513932b54a92946e448d821ee362a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-flat-file-serializing-engine"></a><span data-ttu-id="7c3ed-102">使用一般檔案序列化引擎</span><span class="sxs-lookup"><span data-stu-id="7c3ed-102">Using the Flat File Serializing Engine</span></span>
<span data-ttu-id="7c3ed-103">一般檔案序列化引擎會叫用呼叫**序列化**方法**IFFDocumentSpec**介面。</span><span class="sxs-lookup"><span data-stu-id="7c3ed-103">The flat file serializing engine is invoked by calling the **Serialize** method of the **IFFDocumentSpec** interface.</span></span> <span data-ttu-id="7c3ed-104">提供自訂**XmlReader**為方法的引數，您可以控制取得序列化的最終資料。</span><span class="sxs-lookup"><span data-stu-id="7c3ed-104">By providing a customized **XmlReader** as the argument to the method, you can control the final data that gets serialized.</span></span> <span data-ttu-id="7c3ed-105">資料可以是任何格式，也可能只是衍生自 XmlDocument 而建立的讀取器。</span><span class="sxs-lookup"><span data-stu-id="7c3ed-105">Data could be in any format, or could simply be a reader created of off an XmlDocument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c3ed-106">範例</span><span class="sxs-lookup"><span data-stu-id="7c3ed-106">Example</span></span>  
  
```  
Stream stm = docspec.Serialize(new MyXmlReader(originalXmlReader), Encoding.Unicode);  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c3ed-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c3ed-107">See Also</span></span>  
 <span data-ttu-id="7c3ed-108">[Microsoft.BizTalk.Component.Interop.IFFDocumentSpec](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.iffdocumentspec.aspx) </span><span class="sxs-lookup"><span data-stu-id="7c3ed-108">[Microsoft.BizTalk.Component.Interop.IFFDocumentSpec](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.iffdocumentspec.aspx) </span></span>  
 [<span data-ttu-id="7c3ed-109">使用一般檔案剖析引擎</span><span class="sxs-lookup"><span data-stu-id="7c3ed-109">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)