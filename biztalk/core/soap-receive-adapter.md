---
title: SOAP 接收配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP adapters, receive adapters
- receive adapters, SOAP adapters
ms.assetid: bb968fa8-0515-4f3a-bb39-9effb83e960c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06fac19580d6083ed1b0d4be315d3285acf14fcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278390"
---
# <a name="soap-receive-adapter"></a><span data-ttu-id="58b79-102">SOAP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="58b79-102">SOAP Receive Adapter</span></span>
<span data-ttu-id="58b79-103">您可以使用 SOAP 接收配接器來接收 Web 服務要求。</span><span class="sxs-lookup"><span data-stu-id="58b79-103">You use the SOAP receive adapter to receive Web service requests.</span></span> <span data-ttu-id="58b79-104">SOAP 接收配接器會建立 BizTalk 訊息物件，並將關聯的屬性升級為訊息內容。</span><span class="sxs-lookup"><span data-stu-id="58b79-104">The SOAP receive adapter creates a BizTalk Message object, and promotes the associated properties to the message context.</span></span>  
  
 <span data-ttu-id="58b79-105">SOAP 接收配接器 URI 必須聯結至一或多個 BizTalk 協調流程或結構描述已經發行為 web 服務與**BizTalk Web 服務發佈精靈**。</span><span class="sxs-lookup"><span data-stu-id="58b79-105">A SOAP receive adapter URI must correlate to one or more BizTalk orchestrations or schemas that have been published as a web service with the **BizTalk Web Services Publishing Wizard**.</span></span> <span data-ttu-id="58b79-106">已發佈的 Web 服務會公開一或多個 Web 方法，這些方法都與 BizTalk 組件中的一或多個 BizTalk Server 協調流程或結構描述相互關聯。</span><span class="sxs-lookup"><span data-stu-id="58b79-106">The published web service exposes one or more web methods which correlate to one or more BizTalk Server orchestrations or schemas in a BizTalk assembly.</span></span> <span data-ttu-id="58b79-107">實際上，已發佈的 Web 服務是做為 BizTalk 協調流程或結構描述的伺服器 Proxy，在用戶端與 BizTalk 協調流程或結構描述之間轉寄要求和回應。</span><span class="sxs-lookup"><span data-stu-id="58b79-107">In effect, the published web service acts as a server proxy for the BizTalk orchestration(s) or schema(s) and forwards requests and responses between the client and the BizTalk orchestration(s) or schema(s).</span></span> <span data-ttu-id="58b79-108">如需有關發佈 BizTalk 協調流程或結構描述為 web 服務，請參閱[發佈 Web 服務](../core/publishing-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="58b79-108">For more information about publishing BizTalk orchestrations or schemas as web services see [Publishing Web Services](../core/publishing-web-services.md).</span></span>  
  
 <span data-ttu-id="58b79-109">使用 SOAP 配接器的接收位置可以設定為單向或要求回應 (雙向)。</span><span class="sxs-lookup"><span data-stu-id="58b79-109">A receive location that uses the SOAP adapter can be configured as one-way or request response (two way).</span></span> <span data-ttu-id="58b79-110">當單向接收位置設定為使用 SOAP 配接器時，相關聯的 Web 服務會叫用接收埠所繫結的 BizTalk 組件，並將要求狀態傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="58b79-110">When a one-way receive location is configured to use the SOAP adapter, the associated web service invokes the BizTalk assembly bound to the receive port, and returns the status of the request to the client.</span></span> <span data-ttu-id="58b79-111">當要求回應 (雙向) 接收位置設定為使用 SOAP 配接器時，相關聯的 Web 服務會叫用接收埠所繫結的 BizTalk 組件，並將回應文件傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="58b79-111">When a request response (two way) receive location is configured to use the SOAP Adapter, the associated web service invokes the BizTalk assembly bound to the receive port, and returns a response document to the client.</span></span> <span data-ttu-id="58b79-112">如需有關要求回應訊息，請參閱[要求-回應傳訊](../core/request-response-messaging.md)。</span><span class="sxs-lookup"><span data-stu-id="58b79-112">For more information about request response messaging see [Request-Response Messaging](../core/request-response-messaging.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b79-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58b79-113">See Also</span></span>  
 <span data-ttu-id="58b79-114">[什麼是 SOAP 配接器？](../core/what-is-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="58b79-114">[What Is the SOAP Adapter?](../core/what-is-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="58b79-115">SOAP 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="58b79-115">SOAP Adapter Security Recommendations</span></span>](../core/soap-adapter-security-recommendations.md)