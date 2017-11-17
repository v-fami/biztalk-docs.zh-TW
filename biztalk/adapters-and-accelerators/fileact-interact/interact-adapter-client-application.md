---
title: "InterAct 配接器用戶端應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdab4624-0fc2-42a3-9867-8f77e144b40c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dac8f459799f59b63976c29f4a87dfe22b56e7ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-client-application"></a><span data-ttu-id="12a35-102">InterAct 配接器用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="12a35-102">InterAct Adapter Client Application</span></span>
<span data-ttu-id="12a35-103">互動配接器用戶端應用程式要求訊息是從用戶端應用程式用戶端 SWIFTNet 連結 (SNL) 傳遞的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="12a35-103">InterAct adapter client application request messages are XML documents passed from the client application to the client-side SWIFTNet Link (SNL).</span></span> <span data-ttu-id="12a35-104">為用戶端上執行基本的 SWIFTNet 要求/回應的第一個部分，會發生此類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="12a35-104">Messages of this type occur as the first part of the SWIFTNet Request/Response primitives exercised on the client side.</span></span>  
  
 <span data-ttu-id="12a35-105">本主題描述 SwInt:ExchangeRequest 訊息。</span><span class="sxs-lookup"><span data-stu-id="12a35-105">This topic describes the SwInt:ExchangeRequest message.</span></span> <span data-ttu-id="12a35-106">它用於 「 同步 」 SWIFTNet 用戶端呼叫。</span><span class="sxs-lookup"><span data-stu-id="12a35-106">It is used for “synchronous” client-side calls to SWIFTNet.</span></span> <span data-ttu-id="12a35-107">在此情況下，「 同步 」 表示函式呼叫中封鎖用戶端應用程式，強制等候從伺服器端應用程式收到的回應。</span><span class="sxs-lookup"><span data-stu-id="12a35-107">In this context, “synchronous” means that the function call blocks the client application, forcing it to wait until the Response is received from the server-side application.</span></span> <span data-ttu-id="12a35-108">（或者，或者，就會發生錯誤狀況和該錯誤會回報給用戶端。）</span><span class="sxs-lookup"><span data-stu-id="12a35-108">(Or, alternatively, an error condition occurs and that error is reported back to the client.)</span></span>  
  
 <span data-ttu-id="12a35-109">密碼編譯的區塊 (SwSec:Crypto)，如果有的話，包含訊息簽署及/或驗證處理的結果。</span><span class="sxs-lookup"><span data-stu-id="12a35-109">The cryptographic blocks (SwSec:Crypto), if they exist, contain the results of message signing and/or verification processing.</span></span> <span data-ttu-id="12a35-110">此外，在特定的處理階段，它們可能會包含直接 SNL 所要執行的密碼編譯處理的指示。</span><span class="sxs-lookup"><span data-stu-id="12a35-110">Also, at certain processing stages, they may contain instructions that direct cryptographic processing that is to be performed by the SNL.</span></span>  
  
## <a name="interact-adapter-payload-format"></a><span data-ttu-id="12a35-111">互動配接器裝載格式</span><span class="sxs-lookup"><span data-stu-id="12a35-111">InterAct Adapter Payload Format</span></span>  
 <span data-ttu-id="12a35-112">要求承載包含獨特的商務訊息。</span><span class="sxs-lookup"><span data-stu-id="12a35-112">The Request Payload contains the substance of the business message.</span></span> <span data-ttu-id="12a35-113">裝載的結構必須符合格式正確的 XML （這只是表示裝載不會中斷 XML 剖析，但是在這種情況，它沒有使用 XML 文件結構） 的需求。</span><span class="sxs-lookup"><span data-stu-id="12a35-113">The structure of the payload must conform to the requirements of well-formed XML (this simply means that the payload does not break the XML parsing, but as such, it does not have to use the XML document structure).</span></span> <span data-ttu-id="12a35-114">如果套用 SWIFTNet 訊息驗證，則還有承載必須遵守其他結構化的需求。</span><span class="sxs-lookup"><span data-stu-id="12a35-114">If SWIFTNet Message Validation is applied, then there are other structural requirements to which the payload must conform.</span></span> <span data-ttu-id="12a35-115">除了，裝載結構和內容取決於商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="12a35-115">Aside from that, the payload structure and contents are determined by the business application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a35-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12a35-116">See Also</span></span>  
 <span data-ttu-id="12a35-117">[互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="12a35-117">[InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="12a35-118">[InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span><span class="sxs-lookup"><span data-stu-id="12a35-118">[InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span></span>  
 <span data-ttu-id="12a35-119">[配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span><span class="sxs-lookup"><span data-stu-id="12a35-119">[InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span></span>  
 <span data-ttu-id="12a35-120">[InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span><span class="sxs-lookup"><span data-stu-id="12a35-120">[InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span></span>  
 <span data-ttu-id="12a35-121">[配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="12a35-121">[InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="12a35-122">[互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="12a35-122">[InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="12a35-123">[互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span><span class="sxs-lookup"><span data-stu-id="12a35-123">[InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span></span>  
 <span data-ttu-id="12a35-124">[互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="12a35-124">[InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span></span>  
 [<span data-ttu-id="12a35-125">互動配接器不可否認性</span><span class="sxs-lookup"><span data-stu-id="12a35-125">InterAct Adapter Non-Repudiation</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)