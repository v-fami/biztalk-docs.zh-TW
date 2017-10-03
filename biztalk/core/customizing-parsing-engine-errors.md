---
title: "自訂剖析引擎錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], errors
- pipeline components [custom], code samples
ms.assetid: d9a0060b-49c0-4690-956b-d31668f23c41
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d0bd99d1cad6703e16ba8536625539881ae4c0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="customizing-parsing-engine-errors"></a><span data-ttu-id="4d0f3-102">自訂剖析引擎錯誤</span><span class="sxs-lookup"><span data-stu-id="4d0f3-102">Customizing Parsing Engine Errors</span></span>
<span data-ttu-id="4d0f3-103">您可以使用剖析引擎註冊自己的錯誤處理回呼以處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d0f3-103">You can register your own error-handling callback with the parsing engine to handle errors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d0f3-104">範例</span><span class="sxs-lookup"><span data-stu-id="4d0f3-104">Example</span></span>  
  
```  
bool MyErrorHandler(ErrorContext ctx)  
{  
   // Handle the error  
   return true;  
   // true=continue parsing, false=stop  
}  
  
FFReader ffr = (FFReader)docspec.Parse(new DataReader());  
ffr.OnErrorEvent += MyErrorHandler;  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d0f3-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d0f3-105">See Also</span></span>  
 [<span data-ttu-id="4d0f3-106">使用一般檔案剖析引擎</span><span class="sxs-lookup"><span data-stu-id="4d0f3-106">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)