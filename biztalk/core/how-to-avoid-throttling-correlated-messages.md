---
title: "如何避免節流相關訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfe47747-01e7-4e2f-bbd5-d5055cea001a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10cfcf0009cac5a72d71190c1b974ca6d01a2e1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-avoid-throttling-correlated-messages"></a><span data-ttu-id="e6beb-102">如何避免節流相關訊息</span><span class="sxs-lookup"><span data-stu-id="e6beb-102">How to Avoid Throttling Correlated Messages</span></span>
<span data-ttu-id="e6beb-103">排入 BizTalk Server 中佇列的訊息 (例如透過接收位置或協調流程) 可以使用下列其中一種方式加以處理：</span><span class="sxs-lookup"><span data-stu-id="e6beb-103">Messages that are en-queued into BizTalk Server, for example through a receive location or by orchestrations, can be processed in one of the following ways:</span></span>  
  
-   <span data-ttu-id="e6beb-104">這些訊息可以啟動訂閱者 (即協調流程或傳送埠) 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6beb-104">They can activate new instances of subscribers (that is, orchestrations or send ports)</span></span>  
  
-   <span data-ttu-id="e6beb-105">這些訊息可以透過相互關聯傳遞到現有的訂閱者執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6beb-105">They can be routed to an existing subscriber instance via correlation.</span></span> <span data-ttu-id="e6beb-106">如需有關相互關聯的詳細資訊，請參閱[使用協調流程中的相互關聯](../core/using-correlations-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="e6beb-106">For more information about correlation, see [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md).</span></span>  
  
 <span data-ttu-id="e6beb-107">許多開發人員都會考慮使用接收位置當做解決方案，因為這樣可以透過同一個連接埠同時接收解決方案的啟動和相關訊息。</span><span class="sxs-lookup"><span data-stu-id="e6beb-107">A lot of developers think about the receive locations for a solution as receiving both activation and correlated messages for the solution through the same port.</span></span> <span data-ttu-id="e6beb-108">這是很自然的想法，因為這種方法可以減少訊息傳送者所需追蹤的位址數目。</span><span class="sxs-lookup"><span data-stu-id="e6beb-108">This is natural as it minimizes the number of addresses that message senders need to keep track of.</span></span> <span data-ttu-id="e6beb-109">不過，由於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中已有節流功能，因此在處理節流時，若能設法將啟動訊息資料流及相關訊息資料流分開處理，可能會比較好。</span><span class="sxs-lookup"><span data-stu-id="e6beb-109">However, with throttling in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there can be advantages to thinking about the stream of activation messages and the stream of correlated messages separately when it comes to throttling.</span></span>  
  
 <span data-ttu-id="e6beb-110">當啟動和相互關聯訊息透過同一個接收位置送達時，這些訊息都受相同的節流狀態所控制，因為節流是在主控件層級上套用。</span><span class="sxs-lookup"><span data-stu-id="e6beb-110">When both activation and correlation messages arrive through the same receive location, they are subject to the same throttling state because throttling is applied at the host level.</span></span> <span data-ttu-id="e6beb-111">因此，送達主控件接收位置的所有訊息都會以一個單位同時進行節流。</span><span class="sxs-lookup"><span data-stu-id="e6beb-111">As a result, all messages arriving at receive locations in the host will be throttled as a unit.</span></span> <span data-ttu-id="e6beb-112">在許多情況下，這並不會造成問題，但是在某些節流與啟動相互關聯的情況中，可能會產生某種系統鎖死情況。</span><span class="sxs-lookup"><span data-stu-id="e6beb-112">This is not an issue for many scenarios, but there are cases where throttling correlations with activations can result in a type of system deadlock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6beb-113">範例</span><span class="sxs-lookup"><span data-stu-id="e6beb-113">Example</span></span>  
 <span data-ttu-id="e6beb-114">例如，假設您有一個包含協調流程的案例，而此協調流程會接收一項啟動，並使用這項啟動來初始化相互關聯集合，然後接收相互關聯集合後面的 10 則額外訊息的群組。</span><span class="sxs-lookup"><span data-stu-id="e6beb-114">For example, let's assume you have a scenario containing an orchestration that receives one activation, uses it to initialize a correlation set, then receives a convoy of 10 additional messages that follow the correlation set.</span></span> <span data-ttu-id="e6beb-115">另外，假設在負載過低的情況下，多工緩衝處理中的積存累積為啟動及相互關聯訊息到達之混合，而導致系統必須以節流方式調整可以接收的訊息數量。</span><span class="sxs-lookup"><span data-stu-id="e6beb-115">In addition, assume that, under load, a backlog builds up in the spool as the mix of activation and correlation messages arrive that results in throttling the amount of messages that can be received.</span></span> <span data-ttu-id="e6beb-116">但是很不巧，相互關聯訊息與啟動一起進行節流調整，而使協調流程完成的速度變慢，從而形成更多積存以及其他節流調整。</span><span class="sxs-lookup"><span data-stu-id="e6beb-116">Unfortunately, the correlation messages are throttled along with the activations, which slows down the completion of orchestrations, causing further backlog and additional throttling.</span></span> <span data-ttu-id="e6beb-117">若系統允許繼續作業，這種情況可能會導致系統輸送量因為節流而降到幾近零的程度。</span><span class="sxs-lookup"><span data-stu-id="e6beb-117">Allowed to continue, this would result in throttling the system down to near zero throughput.</span></span>  
  
 <span data-ttu-id="e6beb-118">將單一接收位置分割成兩個 (一個用於啟動、一個用於相互關聯)，並在個別主控件上設定這些位置，即可讓啟動的資料庫大小節流閾值低於相互關聯的資料庫大小節流閾值，進而減少積存總量，並讓訊息持續傳送。</span><span class="sxs-lookup"><span data-stu-id="e6beb-118">By splitting the single receive location into two -- one for activations and one for correlations -- and configuring the locations in separate hosts, the database size throttling threshold for the activations can be kept lower than that for correlations, which will result in reduced backlog overall, and keep the messages flowing.</span></span>  
  
 <span data-ttu-id="e6beb-119">因此，您可能會問: 「 為什麼無法我只引發資料庫大小閾值單一接收位置，以修正問題？ 」</span><span class="sxs-lookup"><span data-stu-id="e6beb-119">So, you might be asking: "why can’t I just raise the database size threshold for my single receive location to fix the problem?"</span></span> <span data-ttu-id="e6beb-120">您可以這樣做，但這種方法並不是每次都能產生預期的結果。</span><span class="sxs-lookup"><span data-stu-id="e6beb-120">The answer is, you can, but it won’t always result in the desired behavior.</span></span> <span data-ttu-id="e6beb-121">使用節流的主要目的是為了避免系統超過負載。</span><span class="sxs-lookup"><span data-stu-id="e6beb-121">Throttling is there primarily to protect the system from becoming overloaded.</span></span> <span data-ttu-id="e6beb-122">如果您將閾值提高到足夠的程度，或是將它們全部關閉，就可以解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="e6beb-122">If you raise the thresholds high enough, or turn them off altogether, you will eliminate this protection.</span></span>  
  
## <a name="recommendation"></a><span data-ttu-id="e6beb-123">建議</span><span class="sxs-lookup"><span data-stu-id="e6beb-123">Recommendation</span></span>  
 <span data-ttu-id="e6beb-124">在上述涉及節流相互關聯訊息的類似案例中，最好的作法是將接收位置分隔成可以獨立節流的個別主控件。</span><span class="sxs-lookup"><span data-stu-id="e6beb-124">The best practice for scenarios such as the one described above that are sensitive to throttling correlation messages, is to separate the receive locations into separate hosts which can be throttled independently.</span></span>  
  
 <span data-ttu-id="e6beb-125">設定接收位置的個別主控件時，請將接收位置使用之主控件的資料庫大小節流閾值，設定成小於協調流程或相互關聯使用之主控件的資料庫大小節流閾值。</span><span class="sxs-lookup"><span data-stu-id="e6beb-125">When separate hosts are configured for receive locations, set the database size throttling threshold for the host used by the receive locations to a lower value than the database size throttling threshold for hosts used by orchestrations or correlations.</span></span>  
  
 <span data-ttu-id="e6beb-126">如果您確定負載絕對不會高於系統的最大持續輸送量 (MST)，或是可在兩個尖峰事件之間復原輸送量尖峰值，則提高節流閾值也可以解決問題，但是可能無法維持如同針對啟動和相互關聯使用個別主控件一樣高的輸送量。</span><span class="sxs-lookup"><span data-stu-id="e6beb-126">If you know that your load will never be higher than the maximum sustainable throughput (MST) for the system, or that throughput peaks are recoverable between peak events, then raising the throttling thresholds will also work, but may not sustain as high a throughput as using separate hosts for activations and correlations.</span></span>