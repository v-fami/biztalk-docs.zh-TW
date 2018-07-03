---
title: 使用 MSMQ 配接器的交易處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, transaction handling
- transactions, MSMQ adapters
ms.assetid: 2e5dd0da-3852-48bf-9372-b019ecab23be
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e55494175029fd8edda1a457298af1d829be3087
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980919"
---
# <a name="transaction-handling-with-the-msmq-adapter"></a><span data-ttu-id="af34f-102">使用 MSMQ 配接器的交易處理</span><span class="sxs-lookup"><span data-stu-id="af34f-102">Transaction Handling with the MSMQ Adapter</span></span>
<span data-ttu-id="af34f-103">本節將討論交易如何接收和傳送。</span><span class="sxs-lookup"><span data-stu-id="af34f-103">This section discusses how transactions work in receiving and sending.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af34f-104">若是 MSMQ 配接器，即使您使用的是遠端佇列，交易還是會從 BizTalk MessageBox 資料庫擴充到本機「訊息佇列」佇列。</span><span class="sxs-lookup"><span data-stu-id="af34f-104">For the MSMQ adapter, a transaction extends from the BizTalk MessageBox database to the local Message Queuing queue even if you are using a remote queue.</span></span>  
  
 <span data-ttu-id="af34f-105">您可以透過 MSMQ 配接器，在傳送和接收中使用交易。</span><span class="sxs-lookup"><span data-stu-id="af34f-105">You can use transactions on both send and receive with the MSMQ adapter.</span></span> <span data-ttu-id="af34f-106">在交易傳送上，配接器會累計訊息，直到有完整批次為止。</span><span class="sxs-lookup"><span data-stu-id="af34f-106">On transacted sends, the adapter accumulates messages until it has a complete batch.</span></span> <span data-ttu-id="af34f-107">然後配接器會將批次提交給本機「訊息佇列」服務，以做為單一交易。</span><span class="sxs-lookup"><span data-stu-id="af34f-107">The adapter then submits the batch to the local Message Queuing service as a single transaction.</span></span> <span data-ttu-id="af34f-108">若提交失敗，則配接器會嘗試重新提交批次。</span><span class="sxs-lookup"><span data-stu-id="af34f-108">If the submission fails, the adapter tries to resubmit the batch.</span></span> <span data-ttu-id="af34f-109">若重新提交失敗，配接器會移動到次要傳輸。</span><span class="sxs-lookup"><span data-stu-id="af34f-109">If the resubmission fails, the adapter moves to the secondary transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af34f-110">配接器支援 Message Queuing 4.0 或更新版本與遠端佇列的交易式讀取。</span><span class="sxs-lookup"><span data-stu-id="af34f-110">The adapter supports transactional reads of remote queues with Message Queuing 4.0 or later only.</span></span> <span data-ttu-id="af34f-111">在此案例中 BizTalk Server 和遠端的訊息佇列伺服器必須執行 Message Queuing 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="af34f-111">In this scenario both the BizTalk Server and the remote Message Queuing server must be running Message Queuing 4.0 or later.</span></span>  
  
 <span data-ttu-id="af34f-112">在交易接收上，配接器會擱置失敗的訊息，因此它不會遺失任何訊息。</span><span class="sxs-lookup"><span data-stu-id="af34f-112">On transacted receives, the adapter suspends failed messages so that it does not lose any one of the messages.</span></span> <span data-ttu-id="af34f-113">在交易接收期間，配接器會將訊息新增到批次，直到批次完成。</span><span class="sxs-lookup"><span data-stu-id="af34f-113">During a transacted receive the adapter adds messages to a batch until the batch is complete.</span></span> <span data-ttu-id="af34f-114">然後提交批次：</span><span class="sxs-lookup"><span data-stu-id="af34f-114">It then submits the batch:</span></span>  
  
- <span data-ttu-id="af34f-115">若沒有問題，且伺服器接收到訊息，則配接器會認同交易。</span><span class="sxs-lookup"><span data-stu-id="af34f-115">If there are no problems and the server receives the messages, the adapter commits the transaction.</span></span>  
  
- <span data-ttu-id="af34f-116">若有問題，配接器會建立新的批次，以做為目前交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="af34f-116">If there are problems, the adapter creates a new batch as part of the current transaction.</span></span> <span data-ttu-id="af34f-117">然後將任何有問題的訊息移動到新的批次。</span><span class="sxs-lookup"><span data-stu-id="af34f-117">It then moves any problem messages into the new batch.</span></span> <span data-ttu-id="af34f-118">接著重新提交第一個批次，並將新的批次以擱置的訊息提交。</span><span class="sxs-lookup"><span data-stu-id="af34f-118">It then resubmits the first batch and submits the new batch as suspended messages.</span></span> <span data-ttu-id="af34f-119">若在此重新提交期間沒有任何問題，則配接器會認同交易。</span><span class="sxs-lookup"><span data-stu-id="af34f-119">The adapter commits the transaction if there are no problems during this resubmission.</span></span>  
  
  <span data-ttu-id="af34f-120">若您在叢集式 BizTalk 主控件執行個體中執行 MSMQ 配接器傳送處理常式，應該要將相同叢集群組中的 MSMQ 服務叢集起來，以確保交易一致性。</span><span class="sxs-lookup"><span data-stu-id="af34f-120">If you are running an MSMQ adapter send handler in a clustered BizTalk Host instance, you should cluster the MSMQ service in the same cluster group to ensure transactional consistency.</span></span>  
  
  <span data-ttu-id="af34f-121">如果 「 網路 DTC 存取 」 已停用 DCOMCNFG 公用程式中，MSMQ 的交易式遠端接收作業會失敗並難以理解的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="af34f-121">If "Network DTC Access" is disabled in the DCOMCNFG utility, a MSMQ transactional remote receive operation will fail with a cryptic error message.</span></span>  <span data-ttu-id="af34f-122">若要執行交易式遠端接收與 MSMQ 配接器，必須啟用 「 網路 DTC 存取 」。</span><span class="sxs-lookup"><span data-stu-id="af34f-122">To do a transactional remote receive with the MSMQ adapter, "Network DTC Access" must be enabled.</span></span> <span data-ttu-id="af34f-123">詳細資訊位於[ http://go.microsoft.com/fwlink/?LinkId=124623 ](http://go.microsoft.com/fwlink/?LinkId=124623)。</span><span class="sxs-lookup"><span data-stu-id="af34f-123">More information can be found at [http://go.microsoft.com/fwlink/?LinkId=124623](http://go.microsoft.com/fwlink/?LinkId=124623).</span></span>  
  
  <span data-ttu-id="af34f-124">若您在叢集式 BizTalk 主控件執行個體中執行 MSMQ 配接器接收處理常式，則應該將相同叢集群組中的 MSMQ 服務叢集起來，以支援本機交易讀取，因為 MSMQ 不支援遠端交易讀取。</span><span class="sxs-lookup"><span data-stu-id="af34f-124">If you are running an MSMQ adapter receive handler in a clustered BizTalk Host instance, you should cluster the MSMQ service in the same cluster group to support local transacted reads because MSMQ does not support remote transactional reads.</span></span> <span data-ttu-id="af34f-125">如需在叢集 BizTalk 主控件執行個體中執行 MSMQ 配接器處理常式的詳細資訊，請參閱[在叢集主控件執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。</span><span class="sxs-lookup"><span data-stu-id="af34f-125">For more information about running MSMQ adapter handlers in a clustered instance of a BizTalk Host, see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af34f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af34f-126">See Also</span></span>  
 [<span data-ttu-id="af34f-127">使用 MSMQ 配接器的可靠傳訊</span><span class="sxs-lookup"><span data-stu-id="af34f-127">Reliable Messaging with the MSMQ Adapter</span></span>](../core/reliable-messaging-with-the-msmq-adapter.md)