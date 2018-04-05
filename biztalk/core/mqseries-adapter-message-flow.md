---
title: MQSeries 配接器訊息流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, message flow
ms.assetid: aa5c8523-afd6-4181-9c11-a150857a7790
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5df8549f99d376ea518b160ac1505aaac7feb5fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-message-flow"></a><span data-ttu-id="5f830-102">MQSeries 配接器訊息流程</span><span class="sxs-lookup"><span data-stu-id="5f830-102">MQSeries Adapter Message Flow</span></span>
<span data-ttu-id="5f830-103">來自 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的訊息會先傳到在 Windows 上執行的 MQSeries Server。</span><span class="sxs-lookup"><span data-stu-id="5f830-103">A message originating from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer is first passed to an MQSeries Server running on Windows.</span></span> <span data-ttu-id="5f830-104">在 Windows 上執行的 MQSeries Server 可以位於執行 BizTalk Server 的相同電腦上。</span><span class="sxs-lookup"><span data-stu-id="5f830-104">MQSeries Server running on Windows can be on the same computer as the one that runs BizTalk Server.</span></span> <span data-ttu-id="5f830-105">訊息透過 MQSeries Server for Windows 電腦路由到裝載於 UNIX 這類作業系統上的 MQSeries Server 主控件。</span><span class="sxs-lookup"><span data-stu-id="5f830-105">The message is routed through the MQSeries Server for Windows computer to an MQSeries Server host on an operating system such as UNIX.</span></span> <span data-ttu-id="5f830-106">然後應用程式從 MQSeries 佇列擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="5f830-106">An application then retrieves the message from the MQSeries queue.</span></span>  
  
 <span data-ttu-id="5f830-107">來自應用程式的訊息會先傳到 MQSeries Server 上的 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="5f830-107">A message originating from an application first goes to an MQSeries queue on MQSeries Server.</span></span> <span data-ttu-id="5f830-108">MQSeries Server 將訊息轉送到 MQSeries Server for Windows 電腦。</span><span class="sxs-lookup"><span data-stu-id="5f830-108">The MQSeries Server forwards the message to the MQSeries Server for Windows computer.</span></span> <span data-ttu-id="5f830-109">BizTalk Server 從 MQSeries Server for Windows 電腦接收訊息，然後轉送到適當的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f830-109">BizTalk Server receives the message from the MQSeries Server for Windows computer and forwards it to the appropriate application.</span></span>  
  
 <span data-ttu-id="5f830-110">MQSeries 配接器支援下列傳訊實例。</span><span class="sxs-lookup"><span data-stu-id="5f830-110">The MQSeries adapter supports the following messaging scenarios.</span></span>  
  
|<span data-ttu-id="5f830-111">**狀況**</span><span class="sxs-lookup"><span data-stu-id="5f830-111">**Scenario**</span></span>|<span data-ttu-id="5f830-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="5f830-112">**Description**</span></span>|  
|------------------|---------------------|  
|<span data-ttu-id="5f830-113">Receive</span><span class="sxs-lookup"><span data-stu-id="5f830-113">Receive</span></span>|<span data-ttu-id="5f830-114">配接器從 MQSeries Server 接收已傳送到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的訊息。</span><span class="sxs-lookup"><span data-stu-id="5f830-114">The adapter receives a message from MQSeries Server, which is passed to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
|<span data-ttu-id="5f830-115">傳送 (靜態單向連接埠)</span><span class="sxs-lookup"><span data-stu-id="5f830-115">Send (Static One-Way Port)</span></span>|<span data-ttu-id="5f830-116">配接器路由來自 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的訊息。</span><span class="sxs-lookup"><span data-stu-id="5f830-116">The adapter routes a message that originates from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
|<span data-ttu-id="5f830-117">動態傳送</span><span class="sxs-lookup"><span data-stu-id="5f830-117">Dynamic Send</span></span>|<span data-ttu-id="5f830-118">啟用應用程式在執行階段選取目的地位址 (URI)。</span><span class="sxs-lookup"><span data-stu-id="5f830-118">Enables the application to select a destination address (URI) at run time.</span></span>|  
|<span data-ttu-id="5f830-119">動態接收</span><span class="sxs-lookup"><span data-stu-id="5f830-119">Dynamic Receive</span></span>|<span data-ttu-id="5f830-120">讓應用程式在執行階段選取位址 (URI)，藉由設定**MQSeries.DynamicReceive**內容屬性**是**並指定動態接收位址。</span><span class="sxs-lookup"><span data-stu-id="5f830-120">Enables the application to select a source address (URI) at run time by setting the **MQSeries.DynamicReceive** context property to **Yes** and specifying the dynamic receive address.</span></span>|  
|<span data-ttu-id="5f830-121">Correlation</span><span class="sxs-lookup"><span data-stu-id="5f830-121">Correlation</span></span>|<span data-ttu-id="5f830-122">來自配接器的訊息與協調流程的特定執行個體相互關聯，可處理多個訊息類型。</span><span class="sxs-lookup"><span data-stu-id="5f830-122">Messages from the adapter are correlated with specific instances of an orchestration that can handle more than one type of message.</span></span><br /><br /> <span data-ttu-id="5f830-123">MQSeries Server 可以使用請求-回應來建立相互關聯識別項，或是 BizTalk Server 可以建立相互關聯識別項。</span><span class="sxs-lookup"><span data-stu-id="5f830-123">MQSeries Server can create the correlation identifier by using solicit-response, or BizTalk Server can create the correlation identifier.</span></span><br /><br /> <span data-ttu-id="5f830-124">如需有關相互關聯集的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 說明」。</span><span class="sxs-lookup"><span data-stu-id="5f830-124">For more information about correlation sets, see [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>|  
  
 <span data-ttu-id="5f830-125">如需有關在管線、協調流程和以內容為基礎的路由中使用連接埠與配接器的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 說明」。</span><span class="sxs-lookup"><span data-stu-id="5f830-125">For more information about using ports and adapters in pipelines, orchestrations, and content-based routing, see [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span> <span data-ttu-id="5f830-126">如需配接器中使用相互關聯識別項的詳細資訊，請參閱[相互關聯訊息使用要求-回覆](../core/correlating-messages-using-request-reply.md)。</span><span class="sxs-lookup"><span data-stu-id="5f830-126">For more information about using correlation identifiers in the adapter, see [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md).</span></span>  
  
 <span data-ttu-id="5f830-127">可用來篩選配接器中的標頭屬性的詳細資訊，請參閱[屬性相關的 BizTalk Server](../core/properties-related-to-biztalk-server.md)和[MQSeries 內容屬性](../core/mqseries-context-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5f830-127">For information about the header properties available for filtering in the adapter, see [Properties Related to BizTalk Server](../core/properties-related-to-biztalk-server.md) and [MQSeries Context Properties](../core/mqseries-context-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f830-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f830-128">See Also</span></span>  
 [<span data-ttu-id="5f830-129">使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="5f830-129">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)