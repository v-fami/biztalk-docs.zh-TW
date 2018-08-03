---
title: 發佈具有 SOAP 標頭的 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, code samples
- SOAP headers, pipelines
- SOAP headers, BizTalk Web Services Publishing Wizard
- pipelines, SOAP headers
- orchestrations, SOAP headers
ms.assetid: c362caff-b75f-4c1b-9013-d2b9c74f5c65
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7baf6af0e4505e448a854fe6def372614bfdaa49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269022"
---
# <a name="publishing-web-services-with-soap-headers"></a><span data-ttu-id="0b84f-102">發佈具有 SOAP 標頭的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="0b84f-102">Publishing Web Services with SOAP Headers</span></span>
<span data-ttu-id="0b84f-103">當您執行「BizTalk Web 服務發佈精靈」時，可以將 SOAP 標頭加入至 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="0b84f-103">You add SOAP headers to your Web services when you run the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="0b84f-104">當您發佈可支援 SOAP 標頭的 Web 服務時，標頭會變成包含 SOAP 標頭字串表示的內容屬性，提供給協調流程和管線元件使用。</span><span class="sxs-lookup"><span data-stu-id="0b84f-104">When you publish a Web service that supports SOAP headers, the headers become available to orchestrations and pipeline components as context properties that contain string representations of the SOAP headers.</span></span>  
  
## <a name="defined-soap-headers"></a><span data-ttu-id="0b84f-105">已定義的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="0b84f-105">Defined SOAP headers</span></span>  
 <span data-ttu-id="0b84f-106">當您使用精靈加入已定義的 SOAP 標頭時，精靈會使用對應至 SOAP 標頭之根項目的名稱，建立內容屬性。</span><span class="sxs-lookup"><span data-stu-id="0b84f-106">When you add a defined SOAP header using the wizard, the wizard creates a context property with a name that corresponds to the root element of the SOAP header.</span></span> <span data-ttu-id="0b84f-107">所有已定義的 SOAP 標頭內容屬性具有命名空間**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**。</span><span class="sxs-lookup"><span data-stu-id="0b84f-107">All defined SOAP header context properties have the namespace **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**.</span></span> <span data-ttu-id="0b84f-108">當 SOAP 配接器將 SOAP 要求轉換為 BizTalk 訊息時，它會建立一個 SOAP 標頭內容屬性。</span><span class="sxs-lookup"><span data-stu-id="0b84f-108">When the SOAP adapter converts the SOAP request to a BizTalk message, it creates one SOAP header context property.</span></span>  
  
 <span data-ttu-id="0b84f-109">下列範例示範簡單的 SOAP 要求：</span><span class="sxs-lookup"><span data-stu-id="0b84f-109">The following example shows a simple SOAP request:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
       <soap:Header>  
             <OrigDest xmlns="http://SOAPHeaderWS.ItemAvailability">  
                    <Origination>Work</Origination>  
                    <Destination>Home</Destination>  
             </OrigDest>  
       </soap:Header>  
       <soap:Body>  
  
       </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="0b84f-110">對於簡單的 SOAP 要求，SOAP 配接器建立 BizTalk 訊息一個 SOAP 標頭內容屬性**OrigDest**和字串。</span><span class="sxs-lookup"><span data-stu-id="0b84f-110">For the simple SOAP request, the SOAP adapter created a BizTalk message with one SOAP header context property **OrigDest** and the string.</span></span>  
  
 <span data-ttu-id="0b84f-111">下列範例會顯示 SOAP 配接器建立的字串：</span><span class="sxs-lookup"><span data-stu-id="0b84f-111">The following example shows the string created by the SOAP adapter:</span></span>  
  
```  
"<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader"><Origination xmlns="">Home</Origination><Destination xmlns="">Work</Destination> </OrigDest>"  
```  
  
## <a name="unknown-soap-headers"></a><span data-ttu-id="0b84f-112">未知的 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="0b84f-112">Unknown SOAP headers</span></span>  
 <span data-ttu-id="0b84f-113">如果您選擇支援未知的 SOAP 標頭，在精靈中，精靈會建立內容屬性名稱**UnknownHeaders**和命名空間**http://schemas.microsoft.com/BizTalk/2003/soap-properties**.</span><span class="sxs-lookup"><span data-stu-id="0b84f-113">If you choose to support unknown SOAP headers in the wizard, the wizard creates a context property with the name **UnknownHeaders** and the namespace **http://schemas.microsoft.com/BizTalk/2003/soap-properties**.</span></span> <span data-ttu-id="0b84f-114">**UnknownHeaders**內容屬性包含所有已接收的未知 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="0b84f-114">The **UnknownHeaders** context property contains all of the received unknown SOAP headers.</span></span>  
  
 <span data-ttu-id="0b84f-115">例如，如果您收到未知的 SOAP 標頭的根元素名稱，與**CustomerGroup**、 **UnknownHeaders**內容屬性包含字串：</span><span class="sxs-lookup"><span data-stu-id="0b84f-115">For example, if you receive an unknown SOAP header with the root element name, **CustomerGroup**, the **UnknownHeaders** context property contains the string:</span></span>  
  
```  
"<?xml version="1.0" encoding="utf-16"?><UnknownHeaders><CustomerGroup xmlns="http://SOAPHeaderWS/CustomerGroup"><Id xmlns="">My Customer</Id>  
</CustomerGroup></UnknownHeaders>"  
```  
  
 <span data-ttu-id="0b84f-116">如需有關加入已定義 SOAP 標頭或支援未知的 SOAP 標頭，請參閱[協調流程發佈為 Web 服務](../core/publishing-an-orchestration-as-a-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0b84f-116">For more information about adding defined SOAP headers or supporting unknown SOAP headers, see [Publishing an Orchestration as a Web Service](../core/publishing-an-orchestration-as-a-web-service.md).</span></span> <span data-ttu-id="0b84f-117">另請參閱[發佈為 Web 服務的結構描述](../core/publishing-schemas-as-a-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0b84f-117">Also see [Publishing Schemas as a Web Service](../core/publishing-schemas-as-a-web-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b84f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b84f-118">See Also</span></span>  
 [<span data-ttu-id="0b84f-119">SOAP 標頭與已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="0b84f-119">SOAP Headers with Published Web Services</span></span>](../core/soap-headers-with-published-web-services.md)