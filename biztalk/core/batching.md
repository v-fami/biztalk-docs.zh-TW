---
title: 批次處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching
- Messaging Engine, batching
- batching, batch size
- batching, about batching
- batching, configuring
- batching, Messaging Engine
ms.assetid: eadc177a-d395-4f99-8dab-aa706fd8ea00
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca31344e60daa88a37c21d0f90b6cf2d2a8aa5a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230886"
---
# <a name="batching"></a><span data-ttu-id="9a13d-102">批次處理</span><span class="sxs-lookup"><span data-stu-id="9a13d-102">Batching</span></span>
<span data-ttu-id="9a13d-103">*批次處理*是序列化的一組允許進行最佳化，關於資料庫往返的訊息處理。</span><span class="sxs-lookup"><span data-stu-id="9a13d-103">*Batching* is a serialized processing of a set of messages that allows for optimizations with respect to database round trips.</span></span> <span data-ttu-id="9a13d-104">批次是不可部分完成的工作單位，也就是說，批次不是完全成功就是完全失敗。</span><span class="sxs-lookup"><span data-stu-id="9a13d-104">A batch is a unit of work that is atomic; that is, it either all succeeds or all fails.</span></span> <span data-ttu-id="9a13d-105">若批次中一個作業成功而另一個失敗，則組成批次的所有作業都是無效的，且必須重複執行。</span><span class="sxs-lookup"><span data-stu-id="9a13d-105">If one operation in a batch succeeds but another operation fails, all the operations that make up the batch are invalidated and must be repeated.</span></span>  
  
 <span data-ttu-id="9a13d-106">BizTalk Server 會使用批次處理來進行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9a13d-106">BizTalk Server uses batching to:</span></span>  
  
-   <span data-ttu-id="9a13d-107">攤銷許多訊息的交易成本。</span><span class="sxs-lookup"><span data-stu-id="9a13d-107">Amortize the cost of the transaction across many messages.</span></span>  
  
-   <span data-ttu-id="9a13d-108">藉由減少資料庫往返內部數目來提高速度。</span><span class="sxs-lookup"><span data-stu-id="9a13d-108">Increase speed by reducing the internal number of database round trips.</span></span>  
  
-   <span data-ttu-id="9a13d-109">使用 BizTalk Server 非同步 API，以便更有效地利用 BizTalk Server 執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="9a13d-109">Make more efficient use of the BizTalk Server thread pool by using the BizTalk Server Asynchronous API.</span></span>  
  
## <a name="applying-batching"></a><span data-ttu-id="9a13d-110">套用批次處理</span><span class="sxs-lookup"><span data-stu-id="9a13d-110">Applying Batching</span></span>  
 <span data-ttu-id="9a13d-111">批次處理是在接收位置的進階屬性中設定，並會在傳送埠端自動啟用。</span><span class="sxs-lookup"><span data-stu-id="9a13d-111">Batching is configured in the advanced properties for a receive location and is enabled automatically on the send port side.</span></span>  
  
## <a name="lowering-the-batch-size"></a><span data-ttu-id="9a13d-112">減少批次大小</span><span class="sxs-lookup"><span data-stu-id="9a13d-112">Lowering the Batch Size</span></span>  
 <span data-ttu-id="9a13d-113">若在下列情況下，您應該降低批次大小：</span><span class="sxs-lookup"><span data-stu-id="9a13d-113">You should lower the batch size if in the following instances:</span></span>  
  
-   <span data-ttu-id="9a13d-114">處理大型訊息時</span><span class="sxs-lookup"><span data-stu-id="9a13d-114">When processing large messages</span></span>  
  
-   <span data-ttu-id="9a13d-115">當資料庫往返不是您的瓶頸</span><span class="sxs-lookup"><span data-stu-id="9a13d-115">When database round trips are not your bottleneck</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a13d-116">變更時要小心**LargeMessageThreshold**設定。</span><span class="sxs-lookup"><span data-stu-id="9a13d-116">Be careful when changing the **LargeMessageThreshold** setting.</span></span> <span data-ttu-id="9a13d-117">批次大小乘以平均訊息大小應該小於**LargeMessageThreshold**設定，除非批次大小為 1。</span><span class="sxs-lookup"><span data-stu-id="9a13d-117">The batch size multiplied by the average message size should be less than the **LargeMessageThreshold** setting unless the batch size is 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a13d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a13d-118">See Also</span></span>  
 <span data-ttu-id="9a13d-119">[傳訊引擎](../core/the-messaging-engine.md) </span><span class="sxs-lookup"><span data-stu-id="9a13d-119">[The Messaging Engine](../core/the-messaging-engine.md) </span></span>  
 <span data-ttu-id="9a13d-120">[批次處理接收訊息處理](../core/batching-messages-for-receive-processing.md) </span><span class="sxs-lookup"><span data-stu-id="9a13d-120">[Batching Messages for Receive Processing](../core/batching-messages-for-receive-processing.md) </span></span>  
 [<span data-ttu-id="9a13d-121">傳送處理的批次訊息</span><span class="sxs-lookup"><span data-stu-id="9a13d-121">Batching Messages for Send Processing</span></span>](../core/batching-messages-for-send-processing.md)