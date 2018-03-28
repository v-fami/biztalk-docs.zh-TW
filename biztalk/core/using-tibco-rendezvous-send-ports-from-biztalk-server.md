---
title: 使用 TIBCO Rendezvous 傳送埠從 BizTalk Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 950c4c367fe053195ba14029405f5015381fc6be
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="using-tibco-rendezvous-send-ports"></a><span data-ttu-id="fedd6-102">使用 TIBCO Rendezvous 傳送埠</span><span class="sxs-lookup"><span data-stu-id="fedd6-102">Using TIBCO Rendezvous Send Ports</span></span>
<span data-ttu-id="fedd6-103">傳輸埠可傳送任何種類的訊息。</span><span class="sxs-lookup"><span data-stu-id="fedd6-103">A transmit port can send any kind of message.</span></span> <span data-ttu-id="fedd6-104">當 BizTalk Server 透過 Microsoft BizTalk Adapter for TIBCO Rendezvous 傳送訊息時，配接器會依據訊息內容屬性值產生訊息，或是使用預設值並傳送到指定的主體。</span><span class="sxs-lookup"><span data-stu-id="fedd6-104">When BizTalk Server sends a message through Microsoft BizTalk Adapter for TIBCO Rendezvous, the adapter generates the message based on message context properties values, or it uses the default and sends it to the specified subject.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fedd6-105">依據 TIBCO Rendezvous 文件，不得在傳輸主體名稱中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="fedd6-105">According to the TIBCO Rendezvous documentation, wildcard characters are not supported in transmit subject names.</span></span>  
  
## <a name="message-handling"></a><span data-ttu-id="fedd6-106">訊息處理</span><span class="sxs-lookup"><span data-stu-id="fedd6-106">Message Handling</span></span>  
 <span data-ttu-id="fedd6-107">配接器會維護狀態，並依據該狀態處理內送的 BizTalk Server 訊息。</span><span class="sxs-lookup"><span data-stu-id="fedd6-107">The adapter maintains a state and handles incoming BizTalk Server messages accordingly.</span></span>  
  
-   <span data-ttu-id="fedd6-108">如果訊息因為傳輸失敗而無法傳送，會指示 BizTalk Server 稍後重新提交。</span><span class="sxs-lookup"><span data-stu-id="fedd6-108">If a message cannot be sent because of transport failure, BizTalk Server is instructed to resubmit later.</span></span>  
  
-   <span data-ttu-id="fedd6-109">如果訊息因為配接器仍在初始化而無法傳送，會將 BizTalk Server 訊息排入佇列。</span><span class="sxs-lookup"><span data-stu-id="fedd6-109">If a message cannot be sent because the adapter is still initializing, the BizTalk Server message is queued.</span></span> <span data-ttu-id="fedd6-110">如果初始化失敗，會指示 BizTalk Server 稍後重新提交。</span><span class="sxs-lookup"><span data-stu-id="fedd6-110">If initialization fails, BizTalk Server is instructed to resubmit later.</span></span>  
  
## <a name="message-generation"></a><span data-ttu-id="fedd6-111">訊息產生</span><span class="sxs-lookup"><span data-stu-id="fedd6-111">Message Generation</span></span>  
 <span data-ttu-id="fedd6-112">使用傳輸配接器時，BizTalk Adapter for TIBCO Rendezvous 會忽略訊息目標命名空間與根元素。</span><span class="sxs-lookup"><span data-stu-id="fedd6-112">With the transmit adapter, BizTalk Adapter for TIBCO Rendezvous ignores the message target namespace and root element.</span></span> <span data-ttu-id="fedd6-113">如果配接器傳送訊息，會依原狀傳送內容。</span><span class="sxs-lookup"><span data-stu-id="fedd6-113">If the adapter sends messages, it sends the payload as is.</span></span> <span data-ttu-id="fedd6-114">如果配接器產生結構化的 TIBCO Rendezvous 訊息，則會忽略根元素的名稱 (訊息沒有名稱)。</span><span class="sxs-lookup"><span data-stu-id="fedd6-114">If the adapter generates a structured TIBCO Rendezvous message, the name of the root element is ignored (a message does not have a name).</span></span> <span data-ttu-id="fedd6-115">在任何情況下，配接器在發佈訊息時均會使用內容屬性尋找要使用的主體。</span><span class="sxs-lookup"><span data-stu-id="fedd6-115">In every case, the adapter uses a context property to find which subject to use when publishing the message.</span></span>  
  
 <span data-ttu-id="fedd6-116">如需詳細資訊，請參閱[BizTalk Server 訊息內容屬性 （傳送處理常式）](../core/biztalk-server-message-context-properties-send-handlers.md)和[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)。</span><span class="sxs-lookup"><span data-stu-id="fedd6-116">For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md) and [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span></span>  

## <a name="using-biztalk-to-send-messages"></a><span data-ttu-id="fedd6-117">使用 BizTalk 傳送訊息</span><span class="sxs-lookup"><span data-stu-id="fedd6-117">Using BizTalk to Send Messages</span></span>
<span data-ttu-id="fedd6-118">Microsoft BizTalk Adapter for TIBCO Rendezvous 使用非同步 API (Transport.Send)。</span><span class="sxs-lookup"><span data-stu-id="fedd6-118">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the asynchronous API (Transport.Send).</span></span> <span data-ttu-id="fedd6-119">您可以使用訊息內容屬性指定配接器傳送的訊息種類：</span><span class="sxs-lookup"><span data-stu-id="fedd6-119">You can specify what kind of message the adapter sends using a message context property:</span></span>  
  
-   <span data-ttu-id="fedd6-120">**結構化**︰ 配接器會產生 TIBRVMSG_MSG 結構化的訊息，BizTalk Server 收到 XML 資料為基礎。</span><span class="sxs-lookup"><span data-stu-id="fedd6-120">**Structured**: The adapter generates a TIBRVMSG_MSG structured message, based on the XML data received from BizTalk Server.</span></span> <span data-ttu-id="fedd6-121">(\*)</span><span class="sxs-lookup"><span data-stu-id="fedd6-121">(\*)</span></span>  
  
 <span data-ttu-id="fedd6-122">如果 BizTalk Server 傳送的訊息中有欄位名稱超過 127 個字元，BizTalk Adapter for TIBCO Rendezvous 會將名稱截斷至 TIBCO Rendezvous 的欄位名稱大小上限 (即 127)。</span><span class="sxs-lookup"><span data-stu-id="fedd6-122">If BizTalk Server sends a message with fields that have names longer than 127 characters, BizTalk Adapter for TIBCO Rendezvous truncates the names to the maximum field name size for TIBCO Rendezvous, which is 127.</span></span>  
  
 <span data-ttu-id="fedd6-123">如果提供 `reply subject name` 屬性，會用來設定 TIBCO Rendezvous 訊息的回覆主旨。</span><span class="sxs-lookup"><span data-stu-id="fedd6-123">If a `reply subject name` property is provided, it is used to set the reply subject on the TIBCO Rendezvous message.</span></span> <span data-ttu-id="fedd6-124">這是假設接收埠設為接聽回覆並將它轉寄至 BizTalk Server，或一些其他的 TIBCO Rendezvous 程式會處理回覆。</span><span class="sxs-lookup"><span data-stu-id="fedd6-124">It is assumed that either a receive port is set to listen for the reply and forward it to BizTalk Server, or some other TIBCO Rendezvous program is taking care of the reply.</span></span>  
  
 <span data-ttu-id="fedd6-125">服務、精靈與網路這三者構成傳輸組態。</span><span class="sxs-lookup"><span data-stu-id="fedd6-125">The triplet (service, daemon, network) makes up the transport configuration.</span></span> <span data-ttu-id="fedd6-126">傳輸組態空白 (預設值) 時，則會透過預設的傳輸物件傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="fedd6-126">An empty (default) transport configuration results in a message being sent through the default transport object.</span></span>  
  
 <span data-ttu-id="fedd6-127">如果未指定字碼頁，配接器會使用 UTF-8 編碼 (字碼頁 65001)。</span><span class="sxs-lookup"><span data-stu-id="fedd6-127">If the code page is left unspecified, the adapter uses UTF-8 encoding (code page 65001).</span></span> <span data-ttu-id="fedd6-128">傳輸器端不支援認證訊息。</span><span class="sxs-lookup"><span data-stu-id="fedd6-128">Certified Messages are not supported on the transmitter side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fedd6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fedd6-129">See Also</span></span>  
 <span data-ttu-id="fedd6-130">[建立傳送埠](../core/creating-send-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="fedd6-130">[Creating Send Ports](../core/creating-send-ports2.md) </span></span>  
 [<span data-ttu-id="fedd6-131">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="fedd6-131">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)