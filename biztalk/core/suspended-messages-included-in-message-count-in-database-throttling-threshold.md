---
title: 擱置的訊息會包含在訊息中的計數資料庫節流閾值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9eb708bb-6d6d-4494-8b8d-67aa44800a20
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f8ea0643ccf2d6206ba86bc56b5dd54c0d51115
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278126"
---
# <a name="suspended-messages-are-included-in-the-message-count-in-database-throttling-threshold"></a><span data-ttu-id="79578-102">資料庫節流閾值中的訊息計數有包含擱置的訊息</span><span class="sxs-lookup"><span data-stu-id="79578-102">Suspended Messages are Included in the Message Count in Database Throttling Threshold</span></span>
<span data-ttu-id="79578-103">根據預設，主控件**訊息 DB 中的計數**節流閾值會設為 50000，將會觸發節流狀況，在下列情況下的值：</span><span class="sxs-lookup"><span data-stu-id="79578-103">By default the host **Message count in DB** throttling threshold is set to a value of 50,000, which will trigger a throttling condition under the following circumstances:</span></span>  
  
-   <span data-ttu-id="79578-104">主控件執行個體發佈到訂閱之主控件的工作、狀態和擱置佇列的訊息總數超過 50,000。</span><span class="sxs-lookup"><span data-stu-id="79578-104">The total number of messages published by the host instance to the work, state, and suspended queues of the subscribing hosts exceeds 50,000.</span></span>  
  
-   <span data-ttu-id="79578-105">多工緩衝處理表格或追蹤表格中的訊息數目超過 50,000 個訊息。</span><span class="sxs-lookup"><span data-stu-id="79578-105">The number of messages in the spool table or the tracking tables exceeds 500,000 messages.</span></span>  
  
 <span data-ttu-id="79578-106">因為已擱置的訊息會包含在**訊息 DB 中的計數**計算，可以進行訊息發佈即使 BizTalk server 很低或完全無負載的節流。</span><span class="sxs-lookup"><span data-stu-id="79578-106">Since suspended messages are included in the **Message count in DB** calculation, throttling of message publishing can occur even if the BizTalk server is experiencing low or no load.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="79578-107">建議</span><span class="sxs-lookup"><span data-stu-id="79578-107">Recommendations</span></span>  
  
-   <span data-ttu-id="79578-108">如果您預期，您可能會有大量擱置的訊息，請考慮增加的預設值為**訊息 DB 中的計數**包含 SQL server 的空間需求納入考量的臨界值BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="79578-108">If you anticipate that you may have a large number of suspended messages, consider increasing the default value for the **Message count in DB** threshold taking into consideration the space requirements of the SQL server that contains the BizTalk databases.</span></span> <span data-ttu-id="79578-109">也請考慮增加**多工緩衝處理乘數**和**追蹤資料乘數**值，以便讓多工緩衝處理資料表中的其他待處理項目。</span><span class="sxs-lookup"><span data-stu-id="79578-109">Also consider increasing the **Spool multiplier** and **Tracking data multiplier** values to allow additional backlog in the Spool table.</span></span>  
  
     <span data-ttu-id="79578-110">如需有關這些值的詳細資訊，請參閱[如何修改資源基礎節流設定](../core/how-to-modify-resource-based-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="79578-110">For more information about these values, see [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md).</span></span>  
  
-   <span data-ttu-id="79578-111">使用**訊息發佈節流狀態**與相關聯的效能監視器計數器**biztalk: Messageagent**效能物件類別，來測量目前的節流狀態。</span><span class="sxs-lookup"><span data-stu-id="79578-111">Use the **Message publishing throttling state** Performance Monitor counter associated with **BizTalk:MessageAgent** performance object category to measure the current throttling state.</span></span> <span data-ttu-id="79578-112">如果這個計數器傳回 6 的值，則會檢查是否有擱置的執行個體，並視需要終止擱置的執行個體，或讓它繼續。</span><span class="sxs-lookup"><span data-stu-id="79578-112">If this counter returns a value of 6, then check for suspended instances and terminate or resume suspended instances as needed.</span></span>  
  
     <span data-ttu-id="79578-113">如需主控件節流效能計數器的詳細資訊，請參閱[主控件節流效能計數器](../core/host-throttling-performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="79578-113">For more information about the host throttling performance counters, see [Host Throttling Performance Counters](../core/host-throttling-performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79578-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79578-114">See Also</span></span>  
 [<span data-ttu-id="79578-115">節流設計建議</span><span class="sxs-lookup"><span data-stu-id="79578-115">Throttling Design Recommendations</span></span>](../core/throttling-design-recommendations.md)