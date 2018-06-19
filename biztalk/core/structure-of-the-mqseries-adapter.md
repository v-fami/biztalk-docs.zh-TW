---
title: MQSeries 配接器的結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, MQSeries adapters
- MQSeries adapters, architecture
ms.assetid: d25caf6a-3f93-4164-9c92-489b919a624d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6239b78f0b9bd2c44a314b7ba0ba6ace8f3b78e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278494"
---
# <a name="structure-of-the-mqseries-adapter"></a><span data-ttu-id="42213-102">MQSeries 配接器的結構</span><span class="sxs-lookup"><span data-stu-id="42213-102">Structure of the MQSeries Adapter</span></span>
<span data-ttu-id="42213-103">MQSeries 配接器有兩個部分： 執行配接器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 COM + 應用程式，MQSAgent、 下執行 MQSeries Server for Windows。</span><span class="sxs-lookup"><span data-stu-id="42213-103">The MQSeries adapter has two parts: the adapter running under [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and a COM+ application, MQSAgent, running under MQSeries Server for Windows.</span></span> <span data-ttu-id="42213-104">下圖顯示此關係。</span><span class="sxs-lookup"><span data-stu-id="42213-104">The following figure shows this relationship.</span></span>  
  
 <span data-ttu-id="42213-105">![MQSeries 配接器元件](../core/media/bts-dev-mqoverallstructure.gif "BTS_Dev_MQOverallStructure")</span><span class="sxs-lookup"><span data-stu-id="42213-105">![MQSeries Adapter components](../core/media/bts-dev-mqoverallstructure.gif "BTS_Dev_MQOverallStructure")</span></span>  
  
 <span data-ttu-id="42213-106">配接器與 MQSAgent 應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="42213-106">The adapter communicates with the MQSAgent application.</span></span> <span data-ttu-id="42213-107">然後 MQSAgent 應用程式與 MQSeries Server for Windows 通訊。</span><span class="sxs-lookup"><span data-stu-id="42213-107">The MQSAgent application, in turn, communicates with MQSeries Server for Windows.</span></span> <span data-ttu-id="42213-108">若您將 MQSeries Server for Windows 安裝在電腦上，可以將代理程式安裝在與配接器相同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="42213-108">You can install the agent on the same computer as the adapter if you install MQSeries Server for Windows on the computer.</span></span>  
  
 <span data-ttu-id="42213-109">配接器的傳送埠將訊息傳送至 MQSAgent。</span><span class="sxs-lookup"><span data-stu-id="42213-109">The send part of the adapter sends the message to the MQSAgent.</span></span> <span data-ttu-id="42213-110">MQSAgent 然後使用**MQPut**，將訊息傳送至 MQSeries 佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="42213-110">MQSAgent then, using **MQPut**, sends the message to the MQSeries Queue Manager.</span></span>  
  
 <span data-ttu-id="42213-111">配接器的接收部分輪詢 MQSAgent，以查看是否有訊息。</span><span class="sxs-lookup"><span data-stu-id="42213-111">The receive part of the adapter polls the MQSAgent to see if there are messages.</span></span> <span data-ttu-id="42213-112">訊息時，MQSAgent 會執行**MQGet**擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="42213-112">When there is a message, the MQSAgent performs an **MQGet** to retrieve the message.</span></span> <span data-ttu-id="42213-113">MQSAgent 從「佇列管理員」擷取訊息時，包含內定 3 秒的等待間隔。</span><span class="sxs-lookup"><span data-stu-id="42213-113">MQSAgent includes a hard-coded three-second wait for retrieving the message from the Queue Manager.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42213-114">您可以設定配接器的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="42213-114">You can set the polling interval of the adapter.</span></span> <span data-ttu-id="42213-115">當您將輪詢間隔設定為少於三秒時，等待間隔會設為輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="42213-115">When you set the polling interval to less than three seconds, the wait interval is set to the polling interval.</span></span>  
  
 <span data-ttu-id="42213-116">傳送和接收訊息動作都可能在交易中發生。</span><span class="sxs-lookup"><span data-stu-id="42213-116">Both the send and receive message actions may occur in transactions.</span></span> <span data-ttu-id="42213-117">這讓配接器能夠回復資訊，也可能重試傳送或接收作業。</span><span class="sxs-lookup"><span data-stu-id="42213-117">This enables the adapter to roll back the message and, possibly, to retry the send or receive operations.</span></span> <span data-ttu-id="42213-118">如需有關交易的詳細資訊，請參閱[MQSeries 配接器批次和交易處理](../core/mqseries-adapter-batching-and-transaction-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="42213-118">For more information about transactions, see [MQSeries Adapter Batching and Transaction Handling](../core/mqseries-adapter-batching-and-transaction-handling.md).</span></span>  
  
 <span data-ttu-id="42213-119">因為配接器是在一部以上的電腦運作，所以可能發生安全性問題。</span><span class="sxs-lookup"><span data-stu-id="42213-119">Because the adapter works across more than one computer, there is a possible security problem.</span></span> <span data-ttu-id="42213-120">有害的程式可能會模擬代理程式並擷取資料。</span><span class="sxs-lookup"><span data-stu-id="42213-120">A hostile program could impersonate the agent and capture data.</span></span> <span data-ttu-id="42213-121">如需有關增強的保護代理程式與配接器的詳細資訊，請參閱[MQSeries 配接器安全性](../core/mqseries-adapter-security.md)。</span><span class="sxs-lookup"><span data-stu-id="42213-121">For more information about enhanced protection for the adapter and agent, see [MQSeries Adapter Security](../core/mqseries-adapter-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42213-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42213-122">See Also</span></span>  
 <span data-ttu-id="42213-123">[MQSeries 配接器架構](../core/mqseries-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="42213-123">[MQSeries Adapter Architecture](../core/mqseries-adapter-architecture.md) </span></span>  
 [<span data-ttu-id="42213-124">何謂 MQSeries 配接器？</span><span class="sxs-lookup"><span data-stu-id="42213-124">What Is the MQSeries Adapter?</span></span>](../core/what-is-the-mqseries-adapter.md)