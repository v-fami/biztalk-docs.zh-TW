---
title: "使用 TIBCO Rendezvous 傳送埠從 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, handling
- message handling
- BizTalk Server, using send ports from
- send ports, using from BizTalk Server
- messages, generating
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04e11657e8e15ac0739124178e85f0c7c5c0a70e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-tibco-rendezvous-send-ports-from-biztalk-server"></a><span data-ttu-id="fbddc-102">從 BizTalk Server 使用 TIBCO Rendezvous 傳送埠</span><span class="sxs-lookup"><span data-stu-id="fbddc-102">Using TIBCO Rendezvous Send Ports from BizTalk Server</span></span>
<span data-ttu-id="fbddc-103">傳輸埠可傳送任何種類的訊息。</span><span class="sxs-lookup"><span data-stu-id="fbddc-103">A transmit port can send any kind of message.</span></span> <span data-ttu-id="fbddc-104">當 BizTalk Server 透過 Microsoft BizTalk Adapter for TIBCO Rendezvous 傳送訊息時，配接器會依據訊息內容屬性值產生訊息，或是使用預設值並傳送到指定的主體。</span><span class="sxs-lookup"><span data-stu-id="fbddc-104">When BizTalk Server sends a message through Microsoft BizTalk Adapter for TIBCO Rendezvous, the adapter generates the message based on message context properties values, or it uses the default and sends it to the specified subject.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbddc-105">依據 TIBCO Rendezvous 文件，不得在傳輸主體名稱中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="fbddc-105">According to the TIBCO Rendezvous documentation, wildcard characters are not supported in transmit subject names.</span></span>  
  
## <a name="message-handling"></a><span data-ttu-id="fbddc-106">訊息處理</span><span class="sxs-lookup"><span data-stu-id="fbddc-106">Message Handling</span></span>  
 <span data-ttu-id="fbddc-107">配接器會維護狀態，並依據該狀態處理內送的 BizTalk Server 訊息。</span><span class="sxs-lookup"><span data-stu-id="fbddc-107">The adapter maintains a state and handles incoming BizTalk Server messages accordingly.</span></span>  
  
-   <span data-ttu-id="fbddc-108">如果訊息因為傳輸失敗而無法傳送，會指示 BizTalk Server 稍後重新提交。</span><span class="sxs-lookup"><span data-stu-id="fbddc-108">If a message cannot be sent because of transport failure, BizTalk Server is instructed to resubmit later.</span></span>  
  
-   <span data-ttu-id="fbddc-109">如果訊息因為配接器仍在初始化而無法傳送，會將 BizTalk Server 訊息排入佇列。</span><span class="sxs-lookup"><span data-stu-id="fbddc-109">If a message cannot be sent because the adapter is still initializing, the BizTalk Server message is queued.</span></span> <span data-ttu-id="fbddc-110">如果初始化失敗，會指示 BizTalk Server 稍後重新提交。</span><span class="sxs-lookup"><span data-stu-id="fbddc-110">If initialization fails, BizTalk Server is instructed to resubmit later.</span></span>  
  
## <a name="message-generation"></a><span data-ttu-id="fbddc-111">訊息產生</span><span class="sxs-lookup"><span data-stu-id="fbddc-111">Message Generation</span></span>  
 <span data-ttu-id="fbddc-112">使用傳輸配接器時，BizTalk Adapter for TIBCO Rendezvous 會忽略訊息目標命名空間與根元素。</span><span class="sxs-lookup"><span data-stu-id="fbddc-112">With the transmit adapter, BizTalk Adapter for TIBCO Rendezvous ignores the message target namespace and root element.</span></span> <span data-ttu-id="fbddc-113">如果配接器傳送訊息，會依原狀傳送內容。</span><span class="sxs-lookup"><span data-stu-id="fbddc-113">If the adapter sends messages, it sends the payload as is.</span></span> <span data-ttu-id="fbddc-114">如果配接器產生結構化的 TIBCO Rendezvous 訊息，則會忽略根元素的名稱 (訊息沒有名稱)。</span><span class="sxs-lookup"><span data-stu-id="fbddc-114">If the adapter generates a structured TIBCO Rendezvous message, the name of the root element is ignored (a message does not have a name).</span></span> <span data-ttu-id="fbddc-115">在任何情況下，配接器在發佈訊息時均會使用內容屬性尋找要使用的主體。</span><span class="sxs-lookup"><span data-stu-id="fbddc-115">In every case, the adapter uses a context property to find which subject to use when publishing the message.</span></span>  
  
 <span data-ttu-id="fbddc-116">如需詳細資訊，請參閱[BizTalk Server 訊息內容屬性 （傳送處理常式）](../core/biztalk-server-message-context-properties-send-handlers.md)和[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)。</span><span class="sxs-lookup"><span data-stu-id="fbddc-116">For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md) and [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbddc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbddc-117">See Also</span></span>  
 <span data-ttu-id="fbddc-118">[建立傳送埠](../core/creating-send-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="fbddc-118">[Creating Send Ports](../core/creating-send-ports2.md) </span></span>  
 [<span data-ttu-id="fbddc-119">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="fbddc-119">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)