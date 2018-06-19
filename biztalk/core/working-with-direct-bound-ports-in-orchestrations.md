---
title: 使用 協調流程中的直接繫結連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03a37ac0-5131-4d37-b60b-56763c460463
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e7b2b59ccdaa23271ee0707f19f4fd2cddc0508
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289270"
---
# <a name="working-with-direct-bound-ports-in-orchestrations"></a><span data-ttu-id="f6419-102">在協調流程中使用直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="f6419-102">Working with Direct Bound Ports in Orchestrations</span></span>
<span data-ttu-id="f6419-103">有三種類型的直接繫結連接埠： MessageBox、 自我相互關聯和夥伴協調流程。</span><span class="sxs-lookup"><span data-stu-id="f6419-103">There are three types of direct bound ports: MessageBox, self-correlating, and partner orchestration.</span></span>  
  
 <span data-ttu-id="f6419-104">MessageBox 直接繫結連接埠適用於發行-訂閱設計模式。</span><span class="sxs-lookup"><span data-stu-id="f6419-104">MessageBox direct bound ports allow for publish-subscribe design patterns.</span></span> <span data-ttu-id="f6419-105">在 MessageBox 直接繫結連接埠上傳送的訊息會發行至 MessageBox 資料庫，訊息收件者則在此根據訂閱收取訊息。</span><span class="sxs-lookup"><span data-stu-id="f6419-105">Messages sent on a MessageBox direct bound port are published to the MessageBox database, where message recipients pick them up based on subscriptions.</span></span> <span data-ttu-id="f6419-106">設定為 MessageBox 直接繫結連接埠的邏輯接收埠會直接從 MessageBox 資料庫取得訊息。</span><span class="sxs-lookup"><span data-stu-id="f6419-106">Logical receive ports configured as MessageBox direct bound ports get messages directly from the MessageBox database.</span></span> <span data-ttu-id="f6419-107">對於啟動**接收**圖形，MessageBox 直接繫結接收埠 get 透過訂閱訊息類型和篩選條件運算式的訊息。</span><span class="sxs-lookup"><span data-stu-id="f6419-107">For activating **Receive** shapes, the MessageBox direct bound receive ports get the messages through subscriptions to the message type and the filter expression.</span></span> <span data-ttu-id="f6419-108">對於非啟動**接收**圖形，MessageBox 直接繫結接收埠 get 透過訂閱訊息類型和相互關聯集的訊息。</span><span class="sxs-lookup"><span data-stu-id="f6419-108">For non-activating **Receive** shapes, the MessageBox direct bound receive ports get the messages through subscriptions to the message type and the correlation set.</span></span>  
  
 <span data-ttu-id="f6419-109">自我相互關聯的直接繫結連接埠可以協助您設計非同步協調流程之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="f6419-109">Self-correlating direct bound ports assist you in designing asynchronous inter-orchestration communication.</span></span> <span data-ttu-id="f6419-110">傳送至自我相互關聯直接繫結連接埠的訊息，會路由傳送至已建立自我相互關聯直接繫結連接埠接收端的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="f6419-110">Messages sent to a self-correlating direct bound port are routed to the instance of the orchestration that created the receiving end of the self-correlated direct bound port.</span></span>  
  
 <span data-ttu-id="f6419-111">夥伴協調流程直接繫結連接埠可以提供協調流程之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="f6419-111">Partner orchestration direct bound ports provide for inter-orchestration communication.</span></span> <span data-ttu-id="f6419-112">在夥伴協調流程直接繫結連接埠上傳送的訊息可以傳送到預定的收件者協調流程，而在夥伴協調流程直接繫結連接埠上接收的訊息則可以從預定的傳送者協調流程中收到。</span><span class="sxs-lookup"><span data-stu-id="f6419-112">Messages sent on a partner orchestration direct bound port can be sent to an intended recipient orchestration, and messages received on a partner orchestration direct bound port can be received from an intended sender orchestration.</span></span>  
  
 <span data-ttu-id="f6419-113">雖然在直接繫結的情況下，訊息似乎是從一個協調流程直接移至另一個，但是透過任何類型的邏輯連接埠傳送的任何訊息，實際上都必定會行經 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f6419-113">Although with direct binding, the message appears to go directly from one orchestration to another, in fact any message sent through any type of logical port always travels through the MessageBox database.</span></span> <span data-ttu-id="f6419-114">此外，直接繫結的連接埠不過是邏輯連接埠，因此直接繫結也只是一項設計階段設定功能。</span><span class="sxs-lookup"><span data-stu-id="f6419-114">Moreover, direct bound ports are only logical ports and therefore direct binding is only a design-time configuration feature.</span></span> <span data-ttu-id="f6419-115">直接繫結的連接埠無法繫結到實體連接埠，而且您只能在設計階段變更直接繫結設定。</span><span class="sxs-lookup"><span data-stu-id="f6419-115">A direct bound port cannot be bound to a physical port, and you can only change the direct binding configuration at design time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6419-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="f6419-116">In This Section</span></span>  
  
-   [<span data-ttu-id="f6419-117">如何使用 MessageBox 直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="f6419-117">How to Use MessageBox Direct Bound Ports</span></span>](../core/how-to-use-messagebox-direct-bound-ports.md)  
  
-   [<span data-ttu-id="f6419-118">如何使用自我相互關聯直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="f6419-118">How to Use Self-Correlating Direct Bound Ports</span></span>](../core/how-to-use-self-correlating-direct-bound-ports.md)  
  
-   [<span data-ttu-id="f6419-119">如何使用夥伴協調流程直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="f6419-119">How to Use Partner Orchestration Direct Bound Ports</span></span>](../core/how-to-use-partner-orchestration-direct-bound-ports.md)  
  
## <a name="see-also"></a><span data-ttu-id="f6419-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6419-120">See Also</span></span>  
 [<span data-ttu-id="f6419-121">連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="f6419-121">Port Bindings</span></span>](../core/port-bindings.md)