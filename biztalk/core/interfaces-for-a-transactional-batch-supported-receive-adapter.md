---
title: 交易式批次支援接收配接器介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5289e8b8-4447-4196-9f7c-5e60c6598d8d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27b51a67f63f3088ce64c9db35c368289ce156d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257574"
---
# <a name="interfaces-for-a-transactional-batch-supported-receive-adapter"></a><span data-ttu-id="452bd-102">支援交易式批次的接收配接器介面</span><span class="sxs-lookup"><span data-stu-id="452bd-102">Interfaces for a Transactional Batch-Supported Receive Adapter</span></span>
<span data-ttu-id="452bd-103">接收配接器可以在需要交易式的訊息提交時建立及控制交易。</span><span class="sxs-lookup"><span data-stu-id="452bd-103">A receive adapter creates and controls transactions when the transactional submission of messages is required.</span></span>  
  
 <span data-ttu-id="452bd-104">交易式接收配接器建立，並將指標傳遞至 Microsoft Distributed Transaction Coordinator (MSDTC) 交易，**完成**方法**IBTTransportBatch**介面。</span><span class="sxs-lookup"><span data-stu-id="452bd-104">A transactional receive adapter creates and passes a pointer to a Microsoft Distributed Transaction Coordinator (MSDTC) transaction on the **Done** method of the **IBTTransportBatch** interface.</span></span> <span data-ttu-id="452bd-105">這樣可確保所有的批次作業都在特定交易物件的範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="452bd-105">This ensures that all batch operations are performed in the scope of that specific transaction object.</span></span> <span data-ttu-id="452bd-106">當批次提交完成時，配接器回呼方法便會認可或復原交易。</span><span class="sxs-lookup"><span data-stu-id="452bd-106">When the batch submission completes, the adapter callback method commits or rolls back the transaction.</span></span> <span data-ttu-id="452bd-107">配接器所採取的動作取決於從傳輸 Proxy 傳回的狀態，並可能由配接器所進行的其他交易相關工作 (傳輸 Proxy 看不到) 決定。</span><span class="sxs-lookup"><span data-stu-id="452bd-107">Which action it takes depends upon the status returned from the transport proxy, and possibly upon other transaction-related work that the adapter does that is not visible to the transport proxy.</span></span> <span data-ttu-id="452bd-108">配接器會決定交易為失敗或成功。</span><span class="sxs-lookup"><span data-stu-id="452bd-108">The adapter determines whether the transaction failed or succeeded.</span></span> <span data-ttu-id="452bd-109">配接器報告交易 （commit 或 rollback） 的結果傳回給傳輸 proxy 使用**DTCCommitConfirm**方法**IBTDTCCommitConfirm**介面。</span><span class="sxs-lookup"><span data-stu-id="452bd-109">The adapter reports the result of the transaction (commit or rollback) back to the transport proxy by using the **DTCCommitConfirm** method of the**IBTDTCCommitConfirm** interface.</span></span> <span data-ttu-id="452bd-110">配接器會對成功的交易傳入 `true`，或是對失敗傳入 `false`。</span><span class="sxs-lookup"><span data-stu-id="452bd-110">It passes in `true` for a successful transaction or `false` for a failure.</span></span>  
  
 <span data-ttu-id="452bd-111">下圖顯示在建立支援交易式批次的接收配接器時所牽涉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="452bd-111">The following figure shows the object interactions involved in creating a transactional batch-supported receive adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter2.gif "ebiz_sdk_devadapter2")  
<span data-ttu-id="452bd-112">使用 DCT 交易之接收配接器提交訊息批次的工作流程</span><span class="sxs-lookup"><span data-stu-id="452bd-112">Workflow for a receive adapter submitting a batch of messages using DTC transactions</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="452bd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="452bd-113">See Also</span></span>  
 <span data-ttu-id="452bd-114">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="452bd-114">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="452bd-115">[開發接收配接器](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="452bd-115">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="452bd-116">[具現化，並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="452bd-116">[Instantiating and Initializing a Receive Adapter](../core/instantiating-and-initializing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="452bd-117">[介面的內含式接收配接器](../core/interfaces-for-an-in-process-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="452bd-117">[Interfaces for an In-Process Receive Adapter](../core/interfaces-for-an-in-process-receive-adapter.md) </span></span>  
 <span data-ttu-id="452bd-118">[介面的外掛式接收配接器](../core/interfaces-for-an-isolated-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="452bd-118">[Interfaces for an Isolated Receive Adapter](../core/interfaces-for-an-isolated-receive-adapter.md) </span></span>  
 <span data-ttu-id="452bd-119">[接收配接器批次支援的介面](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="452bd-119">[Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span></span>  
 [<span data-ttu-id="452bd-120">接收配接器同步要求-回應的介面</span><span class="sxs-lookup"><span data-stu-id="452bd-120">Interfaces for a Synchronous Request-Response Receive Adapter</span></span>](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)