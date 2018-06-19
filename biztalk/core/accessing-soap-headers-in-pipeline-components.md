---
title: 存取管線元件中的 SOAP 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP headers, pipelines
- SOAP headers, properties
- pipelines, SOAP headers
ms.assetid: a2fb074e-0fde-487e-a6ec-7e2b543b7c8b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e484b221df54f00b02f20ef89466fed6b99cd69d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225094"
---
# <a name="accessing-soap-headers-in-pipeline-components"></a><span data-ttu-id="13e2c-102">存取管線元件中的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="13e2c-102">Accessing SOAP Headers in Pipeline Components</span></span>
<span data-ttu-id="13e2c-103">您可以存取管線元件中的 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="13e2c-103">You can access SOAP header context properties in pipeline components.</span></span> <span data-ttu-id="13e2c-104">您可以使用內容屬性名稱和目標命名空間的組合**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**。</span><span class="sxs-lookup"><span data-stu-id="13e2c-104">You use a combination of the context property name and the target namespace **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**.</span></span>  
  
 <span data-ttu-id="13e2c-105">下列程式碼範例的接收管線元件中取得要求 SOAP 標頭屬性**OrigDest**:</span><span class="sxs-lookup"><span data-stu-id="13e2c-105">The following code example gets the request SOAP header in a receive pipeline component for the property **OrigDest**:</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
   {  
   string stringVar = inmsg.Context.Read("OrigDest",    "http://schemas.microsoft.com/BizTalk/2003/SOAPHeader").ToString();  
   }  
   catch (Exception ex)  
   {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
   }  
return inmsg;  
}  
```  
  
 <span data-ttu-id="13e2c-106">如需管線元件的詳細資訊，請參閱[開發自訂管線元件](../core/developing-custom-pipeline-components.md)。</span><span class="sxs-lookup"><span data-stu-id="13e2c-106">For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e2c-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13e2c-107">See Also</span></span>  
 [<span data-ttu-id="13e2c-108">SOAP 標頭與已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="13e2c-108">SOAP Headers with Published Web Services</span></span>](../core/soap-headers-with-published-web-services.md)