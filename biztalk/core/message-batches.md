---
title: "訊息批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f893d16-2670-4463-9a89-6f5be912a045
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25866ac076d77eae13d2ab5378a7582f584b6670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-batches"></a><span data-ttu-id="9e287-102">訊息批次</span><span class="sxs-lookup"><span data-stu-id="9e287-102">Message Batches</span></span>
<span data-ttu-id="9e287-103">需要同時處理配接器的訊息群組時，您應該批次處理這些訊息，以最佳化效能。</span><span class="sxs-lookup"><span data-stu-id="9e287-103">When your adapter has a group of messages that need to be processed at one time, you should batch these messages to optimize performance.</span></span> <span data-ttu-id="9e287-104">就程式設計來說，訊息批次是具有關聯作業的訊息集合。</span><span class="sxs-lookup"><span data-stu-id="9e287-104">Programmatically, message batches are collections of messages with an associated operation.</span></span> <span data-ttu-id="9e287-105">將批次中的訊息分組，而不個別提交每個訊息，您可以最佳化使用資源和處理工作。</span><span class="sxs-lookup"><span data-stu-id="9e287-105">By grouping messages in a batch rather than submitting each message individually, you optimize the use of resources and processing tasks.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9e287-106">使用批次處理，以：</span><span class="sxs-lookup"><span data-stu-id="9e287-106"> uses batching to:</span></span>  
  
-   <span data-ttu-id="9e287-107">攤銷許多訊息的交易成本。</span><span class="sxs-lookup"><span data-stu-id="9e287-107">Amortize the cost of the transaction across many messages.</span></span>  
  
-   <span data-ttu-id="9e287-108">藉由減少資料庫往返內部數目來提高速度。</span><span class="sxs-lookup"><span data-stu-id="9e287-108">Increase speed by reducing the internal number of database round trips.</span></span>  
  
-   <span data-ttu-id="9e287-109">以非同步方式處理訊息，以便更有效地使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="9e287-109">Make more efficient use of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] thread pool by processing the messages asynchronously.</span></span>  
  
 <span data-ttu-id="9e287-110">批次是不可部分完成的工作單位。</span><span class="sxs-lookup"><span data-stu-id="9e287-110">A batch is a unit of work that is atomic.</span></span> <span data-ttu-id="9e287-111">也就是說，其中的所有作業不是全部成功就是全部失敗。</span><span class="sxs-lookup"><span data-stu-id="9e287-111">That is, either all operations in it succeed or all operations in it fail.</span></span> <span data-ttu-id="9e287-112">如果批次內其中一個作業成功而另一個失敗，則組成批次的所有作業都是無效的，而且必須重新提交這些訊息。</span><span class="sxs-lookup"><span data-stu-id="9e287-112">If one operation in a batch succeeds but another operation fails, all the operations that make up the batch are invalidated and the messages must be resubmitted.</span></span> <span data-ttu-id="9e287-113">這表示，為了回應失敗的批次，配接器必須執行三項作業：</span><span class="sxs-lookup"><span data-stu-id="9e287-113">This means that an adapter must do three things in response to a failed batch:</span></span>  
  
-   <span data-ttu-id="9e287-114">判斷哪些訊息失敗。</span><span class="sxs-lookup"><span data-stu-id="9e287-114">Determine which messages failed.</span></span>  
  
-   <span data-ttu-id="9e287-115">決定失敗訊息的處理方式。</span><span class="sxs-lookup"><span data-stu-id="9e287-115">Decide what to do with the failed messages.</span></span>  
  
-   <span data-ttu-id="9e287-116">重新提交未失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="9e287-116">Resubmit the messages that did not fail.</span></span>