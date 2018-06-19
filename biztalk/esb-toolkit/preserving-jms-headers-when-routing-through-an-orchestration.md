---
title: 透過協調流程路由時保留 JMS 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9a59ff3-0cbf-499f-92b2-cf5b808d8b3f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 362f41919a050b08bdba9c70c7771698ab71ce33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294670"
---
# <a name="preserving-jms-headers-when-routing-through-an-orchestration"></a><span data-ttu-id="328ff-102">保留 JMS 標頭時透過協調流程路由</span><span class="sxs-lookup"><span data-stu-id="328ff-102">Preserving JMS Headers When Routing Through an Orchestration</span></span>
<span data-ttu-id="328ff-103">在此使用情況下，元件隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]從內送訊息中擷取 Java 訊息服務 (JMS) 標頭，並再重新加以建構外寄訊息中。</span><span class="sxs-lookup"><span data-stu-id="328ff-103">In this use case, components provided with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extract Java Message Service (JMS) headers from an incoming message and then reconstructs them in the outgoing message.</span></span> <span data-ttu-id="328ff-104">這示範了 JMS 訊息標頭的保留和存取中的標頭內容，在協調流程，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="328ff-104">This demonstrates JMS message header preservation and access to header context from inside an orchestration, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="328ff-105">![保留 JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3 PreservingJMS")</span><span class="sxs-lookup"><span data-stu-id="328ff-105">![Preserving JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3-PreservingJMS")</span></span>  
  
 <span data-ttu-id="328ff-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="328ff-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="328ff-107">**保留 JMS ESB 協調流程和處理整個的標頭資訊**</span><span class="sxs-lookup"><span data-stu-id="328ff-107">**Preserving JMS header information throughout an ESB orchestration and processing**</span></span>  
  
 <span data-ttu-id="328ff-108">隨附的 「 JMS MQRFH2 元件 」 範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例，並包含下列三個部分：</span><span class="sxs-lookup"><span data-stu-id="328ff-108">The JMS MQRFH2 Component sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case and consists of the following three parts:</span></span>  
  
-   <span data-ttu-id="328ff-109">第 1 部分示範失真標頭的保留，因為訊息是從 IBM WebSphere MQ，透過 ESB 和 BizTalk Server，然後再回到 IBM WebSphere MQ。</span><span class="sxs-lookup"><span data-stu-id="328ff-109">Part 1 demonstrates full-fidelity header preservation as a message travels from IBM WebSphere MQ, through ESB and BizTalk Server, and back to IBM WebSphere MQ.</span></span>  
  
-   <span data-ttu-id="328ff-110">第 2 部分會示範如何在 ESB 協調流程中的程式碼可以存取 MQRFH2 標頭屬性。</span><span class="sxs-lookup"><span data-stu-id="328ff-110">Part 2 demonstrates how code in an ESB orchestration can access MQRFH2 header properties.</span></span> <span data-ttu-id="328ff-111">在此情況下，指令碼會修改 JMS 標頭屬性，以指定的目的地佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="328ff-111">In this case, the code modifies a JMS header property to specify the destination queue name.</span></span>  
  
-   <span data-ttu-id="328ff-112">第 3 部分示範大量載入的佇列訊息，並顯示如何應用程式將訊息路由傳送至訊息內容中指定的目的地佇列。</span><span class="sxs-lookup"><span data-stu-id="328ff-112">Part 3 demonstrates bulk loading a queue with messages and shows how the application routes messages to the destination queues specified as part of the message content.</span></span>  
  
 <span data-ttu-id="328ff-113">如需詳細資訊，請參閱[安裝和執行 JMS MQRFH2 元件範例](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="328ff-113">For more information, see [Installing and Running the JMS MQRFH2 Component Sample](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md).</span></span>