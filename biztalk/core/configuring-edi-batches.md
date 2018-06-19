---
title: 設定 EDI 批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8be06e5c-603a-4f93-b018-105314666157
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765dfe5d687c55a763dfd3ff8945606fd32d3239
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232798"
---
# <a name="configuring-edi-batches"></a><span data-ttu-id="78080-102">設定 EDI 批次</span><span class="sxs-lookup"><span data-stu-id="78080-102">Configuring EDI Batches</span></span>
<span data-ttu-id="78080-103">此章節的主題描述如何接收分割或保留批次的交換，如何透過 XML 管線，傳送保留的交換以及如何實作外部批次的釋放機制。</span><span class="sxs-lookup"><span data-stu-id="78080-103">The topics in this section describe how to receive a split or preserved batched interchange, how to send a preserved interchange over an XML pipeline, and how to implement an external batch release mechanism.</span></span>  
  
 <span data-ttu-id="78080-104">本節中的主題不會包含有關如何在批次中傳送的交換。</span><span class="sxs-lookup"><span data-stu-id="78080-104">The topics in this section do not contain information on how to send interchanges in batches.</span></span> <span data-ttu-id="78080-105">如需有關如何批次處理外寄交換的詳細資訊，請參閱[設定批次處理 (X12)](../core/configuring-batching-x12.md) （對於 X12 編碼訊息） 或[設定批次處理 (EDIFACT)](../core/configuring-batching-edifact.md) （對於 EDIFACT 編碼的訊息）。</span><span class="sxs-lookup"><span data-stu-id="78080-105">For more information on how to batch outgoing interchanges, see [Configuring Batching (X12)](../core/configuring-batching-x12.md) (for X12 encoded messages) or [Configuring Batching (EDIFACT)](../core/configuring-batching-edifact.md) (for EDIFACT encoded messages).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78080-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="78080-106">In This Section</span></span>  
  
-   [<span data-ttu-id="78080-107">分割批次的交換</span><span class="sxs-lookup"><span data-stu-id="78080-107">Splitting a Batched Interchange</span></span>](../core/splitting-a-batched-interchange.md)  
  
-   [<span data-ttu-id="78080-108">保留的批次的交換</span><span class="sxs-lookup"><span data-stu-id="78080-108">Preserving a Batched Interchange</span></span>](../core/preserving-a-batched-interchange.md)  
  
-   [<span data-ttu-id="78080-109">傳送保留批次透過 XML 傳送管線</span><span class="sxs-lookup"><span data-stu-id="78080-109">Sending a Preserved Batch with an XML Send Pipeline</span></span>](../core/sending-a-preserved-batch-with-an-xml-send-pipeline.md)  
  
-   [<span data-ttu-id="78080-110">實作外部批次的釋放機制</span><span class="sxs-lookup"><span data-stu-id="78080-110">Implementing an External Batch Release Mechanism</span></span>](../core/implementing-an-external-batch-release-mechanism.md)  
  
-   [<span data-ttu-id="78080-111">內送的交易集與外寄批次相互關聯</span><span class="sxs-lookup"><span data-stu-id="78080-111">Correlating an Incoming Transaction Set with an Outgoing Batch</span></span>](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md)  
  
## <a name="see-also"></a><span data-ttu-id="78080-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78080-112">See Also</span></span>  
 [<span data-ttu-id="78080-113">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="78080-113">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)