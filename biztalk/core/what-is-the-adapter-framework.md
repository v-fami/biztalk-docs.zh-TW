---
title: 何謂配接器架構？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd1e2fd7-4e77-49c4-839d-c2bf16b10ba2
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7efa468cd21720ae04dc34197f790863fadaeb91
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995943"
---
# <a name="what-is-the-adapter-framework"></a><span data-ttu-id="228cb-103">何謂配接器架構？</span><span class="sxs-lookup"><span data-stu-id="228cb-103">What Is the Adapter Framework?</span></span>
<span data-ttu-id="228cb-104">BizTalk 配接器架構提供穩定、開放的機制，讓所有的配接器都能從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳訊引擎實作或存取工作。</span><span class="sxs-lookup"><span data-stu-id="228cb-104">The BizTalk Adapter Framework offers a stable, open mechanism for all adapters to implement or access work from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messaging Engine.</span></span> <span data-ttu-id="228cb-105">介面中所述**Microsoft.BizTalk.Adapter.Framework**命名空間啟用配接器能夠提供方法來修改組態屬性頁。</span><span class="sxs-lookup"><span data-stu-id="228cb-105">The interfaces described in the **Microsoft.BizTalk.Adapter.Framework** namespace enable adapters to provide a means to modify configuration property pages.</span></span> <span data-ttu-id="228cb-106">這種方法也可以將服務和結構描述匯入到 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="228cb-106">It also is a means to import services and schemas into the BizTalk project.</span></span>  
  
 <span data-ttu-id="228cb-107">下圖顯示配接器和配接器架構如何共同運作，以便將應用程式連線至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="228cb-107">The following figure shows how an adapter and the Adapter Framework work together to connect your application to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="228cb-108">![配接器架構](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")</span><span class="sxs-lookup"><span data-stu-id="228cb-108">![The adapter framework](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")</span></span>  
  
 <span data-ttu-id="228cb-109">下列步驟說明圖中顯示的一連串步驟：</span><span class="sxs-lookup"><span data-stu-id="228cb-109">The following steps describe the sequence of steps shown in this figure:</span></span>  
  
1. <span data-ttu-id="228cb-110">資料是從接收位置接收，該位置在指定的位址聆聽特定通訊協定的訊息。</span><span class="sxs-lookup"><span data-stu-id="228cb-110">Data is received from a receive location that is listening for messages with a certain protocol at a specified address.</span></span> <span data-ttu-id="228cb-111">接收位置與配接器和接收管線相關聯。</span><span class="sxs-lookup"><span data-stu-id="228cb-111">The receive location is associated with an adapter and a receive pipeline.</span></span> <span data-ttu-id="228cb-112">您可以設定配接器和管線元件，對已預先決定通訊協定的訊息執行特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="228cb-112">You can configure both the adapter and the pipeline components to perform certain logic on messages of a predetermined protocol.</span></span>  
  
2. <span data-ttu-id="228cb-113">接收位置收到訊息後，便會將訊息傳送至配接器，再由配接器建立新的 BizTalk 訊息，將資料流附加到訊息 (通常在訊息的內文部分)，新增與接收資料的結束點相關的任何中繼資料，然後將該訊息提交至傳訊引擎。</span><span class="sxs-lookup"><span data-stu-id="228cb-113">After the message is received by the receive location, the message is sent to the adapter, which creates a new BizTalk message, attaches the data stream to the message (typically in the body part of the message), adds any metadata pertaining to the endpoint over which the data was received, and then submits that message into the Messaging Engine.</span></span>  
  
3. <span data-ttu-id="228cb-114">傳訊引擎將訊息傳送到接收管線，讓資料在此轉換成 XML，並在此驗證訊息傳送者、解密訊息及驗證 XML。</span><span class="sxs-lookup"><span data-stu-id="228cb-114">The Messaging Engine sends the message to the receive pipeline where the data is transformed into XML, the message sender is authenticated, the message is decrypted, and the XML is validated.</span></span>  
  
4. <span data-ttu-id="228cb-115">傳訊引擎將訊息發佈至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="228cb-115">The Messaging Engine publishes the message to the MessageBox database.</span></span> <span data-ttu-id="228cb-116">MessageBox 是 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料表，其中包含要處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="228cb-116">The MessageBox is a Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] table containing messages to be processed.</span></span> <span data-ttu-id="228cb-117">協調流程和傳送埠兩者都可以訂閱 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="228cb-117">Both orchestrations and send ports can subscribe to the MessageBox.</span></span>  
  
5. <span data-ttu-id="228cb-118">傳訊引擎根據符合訂閱者在篩選條件中設定之規格的訊息內容屬性，將訊息傳送到協調流程或傳送埠訂閱者。</span><span class="sxs-lookup"><span data-stu-id="228cb-118">The Messaging Engine sends the message to either an orchestration or a send port subscriber based upon the message context properties matching the specifications set in the filter on the subscriber.</span></span>  
  
6. <span data-ttu-id="228cb-119">若協調流程為訂閱者，協調流程會處理訊息並透過傳送埠將訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="228cb-119">If an orchestration is the subscriber, it processes the message and sends it out through a send port.</span></span> <span data-ttu-id="228cb-120">如果訂閱者是傳送管線，則在傳輸之前，訊息會先通過傳送管線進入傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="228cb-120">If the subscriber is a send the message passes through the send pipeline into a send adapter before being transmitted.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="228cb-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="228cb-121">In This Section</span></span>  
  
-   [<span data-ttu-id="228cb-122">使用配接器架構工具</span><span class="sxs-lookup"><span data-stu-id="228cb-122">Using the Adapter Framework Tools</span></span>](../core/using-the-adapter-framework-tools.md)  
  
-   [<span data-ttu-id="228cb-123">配接器訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="228cb-123">Adapter Message Exchange Patterns</span></span>](../core/adapter-message-exchange-patterns.md)  
  
-   [<span data-ttu-id="228cb-124">配接器架構元件</span><span class="sxs-lookup"><span data-stu-id="228cb-124">Adapter Framework Components</span></span>](../core/adapter-framework-components.md)  
  
-   [<span data-ttu-id="228cb-125">配接器裝載模型</span><span class="sxs-lookup"><span data-stu-id="228cb-125">Adapter Hosting Model</span></span>](../core/adapter-hosting-model.md)  
  
-   [<span data-ttu-id="228cb-126">配接器元件</span><span class="sxs-lookup"><span data-stu-id="228cb-126">Adapter Components</span></span>](../core/adapter-components.md)