---
title: 使用具有 SOAP 標頭的 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP headers, consuming
- Web services, consuming
- Web services, SOAP headers
- SOAP headers, Web services
ms.assetid: c2dfe7d8-e2f0-4bc6-b79c-354d06a7ffd6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45a3efa628e435092505fdc3884704baa15be34c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237806"
---
# <a name="consuming-web-services-with-soap-headers"></a><span data-ttu-id="1830a-102">使用具有 SOAP 標頭的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="1830a-102">Consuming Web Services with SOAP Headers</span></span>
<span data-ttu-id="1830a-103">在您使用具有已定義之 SOAP 標頭的 Web 服務之後，這些標頭會變成協調流程和管線元件可以使用的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="1830a-103">After you consume a Web service with defined SOAP headers, these headers become available to your orchestrations and pipeline components as context properties.</span></span> <span data-ttu-id="1830a-104">這些內容屬性包含 SOAP 標頭的字串表示法。</span><span class="sxs-lookup"><span data-stu-id="1830a-104">These context properties contain string representations of the SOAP headers.</span></span> <span data-ttu-id="1830a-105">對於 Web 服務中每個已定義的 SOAP 標頭，您可以使用對應至 SOAP 標頭根項目的名稱，建立內容屬性。</span><span class="sxs-lookup"><span data-stu-id="1830a-105">For each defined SOAP header in the Web service, you can create a context property by using the name that corresponds to the root element of the SOAP header.</span></span> <span data-ttu-id="1830a-106">所有已定義的 SOAP 標頭內容屬性位於**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**命名空間。</span><span class="sxs-lookup"><span data-stu-id="1830a-106">All defined SOAP header context properties are in the **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader** namespace.</span></span>  
  
 <span data-ttu-id="1830a-107">下列範例示範如何建立 SOAP 標頭內容屬性**OrigDest**使用中的 SOAP 標頭範例[與取用 Web 服務的 SOAP 標頭](../core/soap-headers-with-consumed-web-services.md):</span><span class="sxs-lookup"><span data-stu-id="1830a-107">The following example shows how to create a SOAP header context property **OrigDest** using the SOAP header example in [SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md):</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns=" http://SOAPHeaderWS.ItemAvailability">  
   <Origination xmlns="">Home</Origination>  
      <Destination xmlns="">Work</Destination>  
</OrigDest>  
```  
  
 <span data-ttu-id="1830a-108">回應 SOAP 標頭也包含已定義之 SOAP 標頭的字串表示法。</span><span class="sxs-lookup"><span data-stu-id="1830a-108">Response SOAP headers also contain string representations of the defined SOAP header.</span></span> <span data-ttu-id="1830a-109">其值與建立要求 SOAP 標頭類似。</span><span class="sxs-lookup"><span data-stu-id="1830a-109">The values are similar to creating a request SOAP header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1830a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1830a-110">See Also</span></span>  
 [<span data-ttu-id="1830a-111">SOAP 標頭與已使用的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="1830a-111">SOAP Headers with Consumed Web Services</span></span>](../core/soap-headers-with-consumed-web-services.md)