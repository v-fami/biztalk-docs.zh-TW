---
title: "依序傳遞訊息與 MQSeries 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, ordered delivery
- MQSeries adapters, ordered delivery
ms.assetid: 517ff2a4-7315-43b5-8d4b-7494adf141e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f8b602adf93152f6af1e5dbbc576180d570a4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ordered-delivery-of-messages-with-the-mqseries-adapter"></a><span data-ttu-id="07096-102">使用 MQSeries 配接器依序傳遞訊息</span><span class="sxs-lookup"><span data-stu-id="07096-102">Ordered Delivery of Messages with the MQSeries Adapter</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="07096-103">提供**排序的傳遞**選項用於靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="07096-103"> provides an **Ordered Delivery** option for static send ports.</span></span> <span data-ttu-id="07096-104">設定**排序的傳遞**至傳送埠上的選項**True**可確保 BizTalk Server 將訊息傳遞至傳送埠，它們會發佈到 BizTalk MessageBox 資料庫的順序相同。</span><span class="sxs-lookup"><span data-stu-id="07096-104">Setting the **Ordered Delivery** option on a send port to **True** ensures that BizTalk Server delivers messages to the send port in the same order that they are published to the BizTalk MessageBox database.</span></span> <span data-ttu-id="07096-105">若要提供端對端排序的傳遞，必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="07096-105">To provide end-to-end ordered delivery the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="07096-106">必須以保留提交訊息給 BizTalk Server 的訊息順序之配接器接收訊息。</span><span class="sxs-lookup"><span data-stu-id="07096-106">Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server.</span></span> <span data-ttu-id="07096-107">例如，接收訊息時使用 MQSeries 接收配接器，接收位置應該設定的選項**含有停止的順序**或**含有擱置的順序**。</span><span class="sxs-lookup"><span data-stu-id="07096-107">For example, when receiving messages with the MQSeries receive adapter, the receive location should be configured with the option **Order with Stop** or **Order with Suspend**.</span></span>  
  
-   <span data-ttu-id="07096-108">您必須訂閱這些訊息的傳送埠**排序的傳遞**選項設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="07096-108">You must subscribe to these messages with a send port that has the **Ordered Delivery** option to **True**.</span></span>  
  
-   <span data-ttu-id="07096-109">如果應使用的訊息，協調流程中的單一執行個體的程序來協調流程，協調流程應該設定為使用循序群組，而**排序的傳遞**屬性協調流程的接收埠應該設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="07096-109">If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to **True**.</span></span>  
  
## <a name="using-the-mqseries-adapter-for-ordered-delivery-of-messages"></a><span data-ttu-id="07096-110">使用 MQSeries 配接器依序傳遞訊息</span><span class="sxs-lookup"><span data-stu-id="07096-110">Using the MQSeries Adapter for Ordered Delivery of Messages</span></span>  
 <span data-ttu-id="07096-111">MQSeries 接收配接器支援保留訊息提交到 BizTalk Server 時的順序。</span><span class="sxs-lookup"><span data-stu-id="07096-111">The MQSeries receive adapter provides support for preserving the order of messages when submitting them to BizTalk Server.</span></span> <span data-ttu-id="07096-112">端對端排序的傳遞訊息透過 BizTalk Server 接收訊息與 MQSeries 配接器，如果透過已設定的傳送埠來處理訊息時可達到**排序的傳遞**選項設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="07096-112">End-to-end ordered delivery of messages through BizTalk Server can be achieved when receiving messages with the MQSeries adapter if the messages are processed by a send port that is configured with the **Ordered Delivery** option set to **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07096-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07096-113">See Also</span></span>  
 <span data-ttu-id="07096-114">[依序傳遞訊息](../core/ordered-delivery-of-messages.md) </span><span class="sxs-lookup"><span data-stu-id="07096-114">[Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md) </span></span>  
 [<span data-ttu-id="07096-115">如何設定 MQSeries 配接器接收位置和傳送埠</span><span class="sxs-lookup"><span data-stu-id="07096-115">How to Configure MQSeries Adapter Receive Locations and Send Ports</span></span>](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)