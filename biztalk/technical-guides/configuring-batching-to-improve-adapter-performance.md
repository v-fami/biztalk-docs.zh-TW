---
title: 設定批次處理來改善配接器效能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65589925-af94-45f1-b501-37c21618b2cf
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dbee8e5b238af0a6dc7f15d54b85d85e0c4b26c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300382"
---
# <a name="configuring-batching-to-improve-adapter-performance"></a><span data-ttu-id="d325c-102">設定批次處理來改善配接器效能</span><span class="sxs-lookup"><span data-stu-id="d325c-102">Configuring Batching to Improve Adapter Performance</span></span>
<span data-ttu-id="d325c-103">配接器處理批次的方式可能大幅影響效能。</span><span class="sxs-lookup"><span data-stu-id="d325c-103">The way an adapter processes a batch can have a significant effect on performance.</span></span> <span data-ttu-id="d325c-104">因為每一個交易都有關聯的固定延遲，所以您應該嘗試將一個以上的作業結合成單一批次，讓交易的數目減至最少。</span><span class="sxs-lookup"><span data-stu-id="d325c-104">Because there is a fixed delay associated with each transaction, you should try to minimize the number of transactions by combining more than one operation into a single batch.</span></span>  
  
 <span data-ttu-id="d325c-105">如果您提交訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]批次，不會限制只會根據訊息計數的批次大小。</span><span class="sxs-lookup"><span data-stu-id="d325c-105">If you are submitting messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in batches, do not limit the batch size based only on the message count.</span></span> <span data-ttu-id="d325c-106">比方說，如果批次大小為二，而配接器取得四個訊息的大小 4 KB、 8 KB、 1 MB 和 5 MB，將會第一個批次大小的 12 KB 和第二個批次將是 6 MB 的大小。</span><span class="sxs-lookup"><span data-stu-id="d325c-106">For example, if the batch size is two and the adapter gets four messages of size 4 KB, 8 KB, 1 MB, and 5 MB respectively, the first batch will be of size 12 KB, and the second batch will be of size 6 MB.</span></span> <span data-ttu-id="d325c-107">由於 BizTalk 傳訊引擎會循序處理單一批次中的所有訊息，所以此範例中第二個批次的處理速度要比第一個批次緩慢許多，</span><span class="sxs-lookup"><span data-stu-id="d325c-107">Because the BizTalk Messaging Engine processes all messages in a single batch sequentially, the second batch in this example will be processed much more slowly than the first batch.</span></span> <span data-ttu-id="d325c-108">這項的影響是降低的輸送量。</span><span class="sxs-lookup"><span data-stu-id="d325c-108">The effect of this is reduced throughput.</span></span>  
  
 <span data-ttu-id="d325c-109">若要處理這個問題，我們建議您要批次處理為基礎的訊息計數和批次 （也就是以位元組為單位的批次大小） 中的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="d325c-109">To handle this problem, we recommend that you batch based on both the message count and the total number of bytes in the batch (that is, batch size in bytes).</span></span> <span data-ttu-id="d325c-110">沒有任何最佳數目的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="d325c-110">There is no optimal number for total bytes.</span></span> <span data-ttu-id="d325c-111">不過，在正常處理案例中，如果批次大小超過 1 MB，將會啟動遇到不佳的並行處理和輸送量。</span><span class="sxs-lookup"><span data-stu-id="d325c-111">However, in a normal processing scenario, if the batch size exceeds 1 MB, you will start encountering poor concurrency and throughput.</span></span>  
  
 <span data-ttu-id="d325c-112">配接器通常會處理在生產環境中的各種大小的訊息。</span><span class="sxs-lookup"><span data-stu-id="d325c-112">Adapters generally process messages of varying size in the production environment.</span></span> <span data-ttu-id="d325c-113">內送訊息的大小有可能會大大地改變。</span><span class="sxs-lookup"><span data-stu-id="d325c-113">The sizes of incoming messages are likely to vary significantly.</span></span> <span data-ttu-id="d325c-114">如此一來，永遠使用訊息計數和總位元組數來建立批次。</span><span class="sxs-lookup"><span data-stu-id="d325c-114">As a result, always use message count and total bytes to build the batch.</span></span>