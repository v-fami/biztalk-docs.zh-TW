---
title: "MSMQ 配接器架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, MSMQ adapters
- MSMQ adapters, architecture
ms.assetid: acecc2a4-0670-487e-be39-28a24c8c3f16
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd314b6f835568b6336121478268b84381a288ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="msmq-adapter-architecture"></a><span data-ttu-id="8a7ab-102">MSMQ 配接器架構</span><span class="sxs-lookup"><span data-stu-id="8a7ab-102">MSMQ Adapter Architecture</span></span>
<span data-ttu-id="8a7ab-103">MSMQ 配接器讓您可以利用 Microsoft Message Queuing (也稱為 MSMQ) 功能，該功能在 BizTalk Server 中是無法使用的。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-103">The MSMQ adapter lets you take advantage of Microsoft Message Queuing (also known as MSMQ) features that are otherwise unavailable in BizTalk Server.</span></span>  
  
## <a name="adapter-structure"></a><span data-ttu-id="8a7ab-104">配接器結構</span><span class="sxs-lookup"><span data-stu-id="8a7ab-104">Adapter Structure</span></span>  
 <span data-ttu-id="8a7ab-105">MSMQ 配接器和其他 BizTalk 配接器的結構相同，並且使用「配接器架構」。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-105">The MSMQ adapter has the same structure as other BizTalk adapters and uses the Adapter Framework.</span></span> <span data-ttu-id="8a7ab-106">它是由設計階段元件與執行階段元件所組成。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-106">It is made up of a design-time component and a run-time component.</span></span> <span data-ttu-id="8a7ab-107">執行階段元件依序包含實作訊息傳輸的項目。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-107">The run-time component, in turn, contains the elements that implement the message transport.</span></span>  
  
 <span data-ttu-id="8a7ab-108">設計階段元件讓您設定傳送和接收的配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-108">The design-time component lets you configure the adapter properties for sending and receiving.</span></span>  
  
 <span data-ttu-id="8a7ab-109">執行階段元件可以將訊息傳送到設計階段定義的佇列，或從指定的佇列接收訊息。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-109">The run-time component can send messages to a queue defined at design time or receive messages from a designated queue.</span></span> <span data-ttu-id="8a7ab-110">配接器執行階段與 BizTalk Server 應用程式在相同的程序中執行，而且不會在外掛式主控件中執行。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-110">The adapter runtime runs in the same process as the BizTalk Server application and does not run in an isolated host.</span></span>  
  
 <span data-ttu-id="8a7ab-111">所有訊息處理都依靠本機「訊息佇列」服務，即使遠端佇列也一樣。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-111">All message handling relies on the local Message Queuing service, even for remote queues.</span></span> <span data-ttu-id="8a7ab-112">對於遠端佇列，配接器會將訊息送交本機「訊息佇列」服務。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-112">For remote queues, the adapter hands messages off to the local Message Queuing service.</span></span> <span data-ttu-id="8a7ab-113">接著，它會將訊息傳送到遠端佇列。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-113">It, in turn, sends the messages to the remote queue.</span></span>  
  
 <span data-ttu-id="8a7ab-114">如需完整清單的傳送和接收組態屬性，請參閱[如何設定 MSMQ 傳送埠](../core/how-to-configure-an-msmq-send-port.md)和[如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-114">For a complete list of send and receive configuration properties, see [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md) and [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md).</span></span>  
  
 <span data-ttu-id="8a7ab-115">如需有關訊息佇列的詳細資訊，請參閱 Microsoft TechNet 文件庫中可用的下列主題：</span><span class="sxs-lookup"><span data-stu-id="8a7ab-115">For more information about Message Queuing, see the following topics available in the Microsoft TechNet Library:</span></span>  
  
-   <span data-ttu-id="8a7ab-116">**訊息佇列設計指南**在[http://go.microsoft.com/fwlink/?LinkId=137080](http://go.microsoft.com/fwlink/?LinkId=137080)。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-116">**Message Queuing Design Guide** at [http://go.microsoft.com/fwlink/?LinkId=137080](http://go.microsoft.com/fwlink/?LinkId=137080).</span></span>  
  
-   <span data-ttu-id="8a7ab-117">**訊息佇列操作指南**在[http://go.microsoft.com/fwlink/?LinkId=137079](http://go.microsoft.com/fwlink/?LinkId=137079)。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-117">**Message Queuing Operations Guide** at [http://go.microsoft.com/fwlink/?LinkId=137079](http://go.microsoft.com/fwlink/?LinkId=137079).</span></span>  
  
-   <span data-ttu-id="8a7ab-118">**訊息佇列疑難排解指南**在[http://go.microsoft.com/fwlink/?LinkId=137081](http://go.microsoft.com/fwlink/?LinkId=137081)。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-118">**Message Queuing Troubleshooting Guide** at [http://go.microsoft.com/fwlink/?LinkId=137081](http://go.microsoft.com/fwlink/?LinkId=137081).</span></span>  
  
-   <span data-ttu-id="8a7ab-119">**訊息佇列技術參考**在[http://go.microsoft.com/fwlink/?LinkId=137082](http://go.microsoft.com/fwlink/?LinkId=137082)。</span><span class="sxs-lookup"><span data-stu-id="8a7ab-119">**Message Queuing Technical Reference** at [http://go.microsoft.com/fwlink/?LinkId=137082](http://go.microsoft.com/fwlink/?LinkId=137082).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7ab-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a7ab-120">See Also</span></span>  
 [<span data-ttu-id="8a7ab-121">什麼是 MSMQ 配接器？</span><span class="sxs-lookup"><span data-stu-id="8a7ab-121">What Is the MSMQ Adapter?</span></span>](../core/what-is-the-msmq-adapter.md)