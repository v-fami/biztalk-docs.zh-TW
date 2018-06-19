---
title: 使用 MSMQ 配接器的可信賴傳訊屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, properties
- queues, MSMQ adapters
- MSMQ adapters, dead letters
- queues, failures [MSMQ adapters]
- MSMQ adapters, impersonation
- MSMQ adapters, remote queues
- queues
- reliability, MSMQ adapters
- impersonation, MSMQ adapters
- MSMQ adapters, queue failures
- clustering, MSMQ adapters
- queues, remote
- MSMQ adapters, reliability
- MSMQ adapters, clustering
ms.assetid: 34bfe028-b2aa-4816-a437-3679d19dffb2
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49aebf12c86ae72d5dcb224d078c62afefcb8f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268846"
---
# <a name="properties-for-reliable-messaging-with-the-msmq-adapter"></a><span data-ttu-id="7e47e-102">使用 MSMQ 配接器的可信賴傳訊屬性</span><span class="sxs-lookup"><span data-stu-id="7e47e-102">Properties for Reliable Messaging with the MSMQ Adapter</span></span>
<span data-ttu-id="7e47e-103">您可以藉由設定 MSMQ 配接器的方式來改善以 MSMQ 配接器傳送和接收訊息的可靠性。</span><span class="sxs-lookup"><span data-stu-id="7e47e-103">You can improve the reliability of sending and receiving messages with the MSMQ adapter by the way you configure the MSMQ adapter.</span></span> <span data-ttu-id="7e47e-104">本主題討論使用幾個組態屬性以進行可靠傳訊。</span><span class="sxs-lookup"><span data-stu-id="7e47e-104">This topic discusses using several configuration properties for reliable messaging.</span></span>  
  
## <a name="running-msmq-adapter-handlers-within-a-clustered-biztalk-host"></a><span data-ttu-id="7e47e-105">在叢集 BizTalk 主控件中執行 MSMQ 配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="7e47e-105">Running MSMQ Adapter Handlers Within a Clustered BizTalk Host</span></span>  
 <span data-ttu-id="7e47e-106">達成高可用性的一個方法是在不同的 BizTalk Server 之多個主控件執行個體中，同時執行配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="7e47e-106">One approach to high availability is to run adapter handlers in multiple host instances on different BizTalk servers simultaneously.</span></span> <span data-ttu-id="7e47e-107">不建議將此方法用於 MSMQ 配接器處理常式，因為 MSMQ 不支援遠端交易讀取，且因為 MSMQ 傳送處理常式會在本機執行的 MSMQ 服務執行個體上維持相依性。</span><span class="sxs-lookup"><span data-stu-id="7e47e-107">This approach is not recommended for the MSMQ adapter handlers, because MSMQ does not support remote transacted reads and because the MSMQ send handler maintains a dependency on the locally running instance of the MSMQ service.</span></span> <span data-ttu-id="7e47e-108">若要提供 MSMQ 傳送和接收處理常式的高可用性，建議您在 BizTalk 主控件的叢集執行個體中執行 MSMQ 配接器。</span><span class="sxs-lookup"><span data-stu-id="7e47e-108">To provide high availability for the MSMQ send and receive handlers it is recommended that you run the MSMQ adapter handlers in a clustered instance of a BizTalk Host.</span></span> <span data-ttu-id="7e47e-109">如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。</span><span class="sxs-lookup"><span data-stu-id="7e47e-109">For more information, see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span></span>  
  
## <a name="queue-failure-and-the-dead-letter-queue"></a><span data-ttu-id="7e47e-110">佇列失敗與無法寄出的信件佇列</span><span class="sxs-lookup"><span data-stu-id="7e47e-110">Queue Failure and the Dead Letter Queue</span></span>  
 <span data-ttu-id="7e47e-111">在成功傳送訊息之後，若停用或刪除接收佇列，則不會為後續訊息提示錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e47e-111">After successfully sending a message, there is no error for subsequent messages if the receiving queue is disabled or deleted.</span></span> <span data-ttu-id="7e47e-112">此狀況可能造成訊息遺失。</span><span class="sxs-lookup"><span data-stu-id="7e47e-112">This situation could cause loss of messages.</span></span>  
  
 <span data-ttu-id="7e47e-113">設定**使用寄不出信件佇列**組態屬性**True**可避免您遺失訊息。</span><span class="sxs-lookup"><span data-stu-id="7e47e-113">Setting the **Use Dead Letter Queue** configuration property to **True** prevents you from losing messages.</span></span> <span data-ttu-id="7e47e-114">當這個屬性為 `True` (預設) 時，佇列未接收的訊息會進入無法寄出的信件佇列中。</span><span class="sxs-lookup"><span data-stu-id="7e47e-114">When the property is `True` (the default), messages that the queue does not receive go into the dead letter queue.</span></span>  
  
## <a name="impersonation-and-remote-queues"></a><span data-ttu-id="7e47e-115">模擬與遠端佇列</span><span class="sxs-lookup"><span data-stu-id="7e47e-115">Impersonation and Remote Queues</span></span>  
 <span data-ttu-id="7e47e-116">您也必須設定**使用寄不出信件佇列**組態屬性**True**當您使用遠端佇列。</span><span class="sxs-lookup"><span data-stu-id="7e47e-116">You also have to set the **Use Dead Letter Queue** configuration property to **True** when you use remote queues.</span></span> <span data-ttu-id="7e47e-117">若 MSMQ 配接器模擬沒有使用遠端佇列的權限之使用者，則訊息可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="7e47e-117">If the adapter for MSMQ impersonates a user without permission to use the remote queue, the message could be lost.</span></span>  
  
 <span data-ttu-id="7e47e-118">若屬性是**True**模擬的使用者沒有使用遠端佇列的權限，本機或遠端電腦上的訊息會移至寄不出信件佇列。</span><span class="sxs-lookup"><span data-stu-id="7e47e-118">When the property is **True** and the impersonated user does not have permission to use the remote queue, the message goes to the dead letter queue on either the local or remote computer.</span></span> <span data-ttu-id="7e47e-119">在交易式傳送中，訊息會進入本機電腦之無法寄出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="7e47e-119">In a transactional send, the message goes to the dead letter queue on the local computer.</span></span> <span data-ttu-id="7e47e-120">在非交易式傳送中，訊息會進入遠端電腦之無法寄出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="7e47e-120">In a non-transactional send, the message goes to the dead letter queue on the remote computer.</span></span>  
  
## <a name="recoverable-and-use-journal-queue-properties"></a><span data-ttu-id="7e47e-121">[可復原] 和 [使用日誌佇列] 屬性</span><span class="sxs-lookup"><span data-stu-id="7e47e-121">Recoverable and Use Journal Queue Properties</span></span>  
 <span data-ttu-id="7e47e-122">這兩個**可修復**和**使用日誌佇列**屬性都會儲存傳送訊息的複本。</span><span class="sxs-lookup"><span data-stu-id="7e47e-122">Both the **Recoverable** and **Use Journal Queue** properties save copies of sent messages.</span></span> <span data-ttu-id="7e47e-123">如需有關這些屬性的詳細資訊，請參閱[如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)和[如何設定 MSMQ 傳送埠](../core/how-to-configure-an-msmq-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="7e47e-123">For more information about these properties, see [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md) and [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e47e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e47e-124">See Also</span></span>  
 <span data-ttu-id="7e47e-125">[使用 MSMQ 配接器的可信賴傳訊](../core/reliable-messaging-with-the-msmq-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="7e47e-125">[Reliable Messaging with the MSMQ Adapter](../core/reliable-messaging-with-the-msmq-adapter.md) </span></span>  
 [<span data-ttu-id="7e47e-126">執行叢集主控件中的配接器處理常式的考量</span><span class="sxs-lookup"><span data-stu-id="7e47e-126">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)