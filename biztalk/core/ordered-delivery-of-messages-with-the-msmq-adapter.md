---
title: "依序傳遞訊息，與 MSMQ 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, ordered delivery
- MSMQ adapters, ordered delivery
ms.assetid: e8dafc76-e894-4120-9cea-d014d635850e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac842fcd1e9b386fa885844f3a797504ed7c4c3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ordered-delivery-of-messages-with-the-msmq-adapter"></a><span data-ttu-id="cf08f-102">依序傳遞訊息，與 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="cf08f-102">Ordered Delivery of Messages with the MSMQ Adapter</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cf08f-103">提供**排序的傳遞**選項用於靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="cf08f-103"> provides an **Ordered Delivery** option for static send ports.</span></span> <span data-ttu-id="cf08f-104">設定**排序的傳遞**至傳送埠上的選項**True**可確保 BizTalk Server 將訊息傳遞至傳送埠，它們會發佈到 MessageBox 資料庫的順序相同。</span><span class="sxs-lookup"><span data-stu-id="cf08f-104">Setting the **Ordered Delivery** option on a send port to **True** ensures that BizTalk Server delivers messages to the send port in the same order that they are published to the MessageBox database.</span></span> <span data-ttu-id="cf08f-105">若要提供端對端排序的傳遞，必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="cf08f-105">To provide end-to-end ordered delivery the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="cf08f-106">必須以保留提交訊息給 BizTalk Server 的訊息順序之配接器接收訊息。</span><span class="sxs-lookup"><span data-stu-id="cf08f-106">Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server.</span></span>  
  
-   <span data-ttu-id="cf08f-107">您必須訂閱這些訊息的傳送埠**排序的傳遞**選項設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="cf08f-107">You must subscribe to these messages with a send port that has the **Ordered Delivery** option to **True**.</span></span>  
  
-   <span data-ttu-id="cf08f-108">如果應使用的訊息，協調流程中的單一執行個體的程序來協調流程，協調流程應該設定為使用循序群組，而**排序的傳遞**屬性協調流程的接收埠應該設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="cf08f-108">If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to **True**.</span></span>  
  
## <a name="using-the-msmq-adapter-for-ordered-delivery-of-messages"></a><span data-ttu-id="cf08f-109">使用 MSMQ 配接器進行依序傳遞訊息</span><span class="sxs-lookup"><span data-stu-id="cf08f-109">Using the MSMQ Adapter for Ordered Delivery of Messages</span></span>  
 <span data-ttu-id="cf08f-110">MSMQ 接收配接器必須支援保留提交訊息至 BizTalk Server 的訊息順序。</span><span class="sxs-lookup"><span data-stu-id="cf08f-110">The MSMQ receive adapter provides support for preserving the order of messages when submitting them to BizTalk Server.</span></span> <span data-ttu-id="cf08f-111">端對端排序的傳遞訊息透過 BizTalk Server 接收訊息與 MSMQ 配接器，如果透過已設定的傳送埠來處理訊息時可達到**排序的傳遞**選項設為**True**。</span><span class="sxs-lookup"><span data-stu-id="cf08f-111">End-to-end ordered delivery of messages through BizTalk Server can be achieved when receiving messages with the MSMQ adapter if the messages are processed by a send port that is configured with the **Ordered Delivery** option set to **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf08f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf08f-112">See Also</span></span>  
 <span data-ttu-id="cf08f-113">[依序傳遞訊息](../core/ordered-delivery-of-messages.md) </span><span class="sxs-lookup"><span data-stu-id="cf08f-113">[Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md) </span></span>  
 [<span data-ttu-id="cf08f-114">如何設定 MSMQ 接收位置</span><span class="sxs-lookup"><span data-stu-id="cf08f-114">How to Configure an MSMQ Receive Location</span></span>](../core/how-to-configure-an-msmq-receive-location.md)