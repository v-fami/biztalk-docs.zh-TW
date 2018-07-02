---
title: 透過協調流程路由時保留 JMS 標頭 |Microsoft Docs
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
ms.openlocfilehash: 142bd0d2e5ff86362fe3c3ffa7ef8ec256202708
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979711"
---
# <a name="preserving-jms-headers-when-routing-through-an-orchestration"></a><span data-ttu-id="d6d7f-102">透過協調流程路由時保留 JMS 標頭</span><span class="sxs-lookup"><span data-stu-id="d6d7f-102">Preserving JMS Headers When Routing Through an Orchestration</span></span>
<span data-ttu-id="d6d7f-103">在此使用案例中，元件隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擷取內送訊息的 Java 訊息服務 (JMS) 標頭，然後重新加以建構外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="d6d7f-103">In this use case, components provided with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extract Java Message Service (JMS) headers from an incoming message and then reconstructs them in the outgoing message.</span></span> <span data-ttu-id="d6d7f-104">這示範 JMS 訊息標頭保留及從協調流程內的標頭內容的存取 圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="d6d7f-104">This demonstrates JMS message header preservation and access to header context from inside an orchestration, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="d6d7f-105">![保留 JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3 PreservingJMS")</span><span class="sxs-lookup"><span data-stu-id="d6d7f-105">![Preserving JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3-PreservingJMS")</span></span>  
  
 <span data-ttu-id="d6d7f-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="d6d7f-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="d6d7f-107">**保留 JMS 標頭資訊，在 ESB 協調流程和處理**</span><span class="sxs-lookup"><span data-stu-id="d6d7f-107">**Preserving JMS header information throughout an ESB orchestration and processing**</span></span>  
  
 <span data-ttu-id="d6d7f-108">JMS MQRFH2 元件範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例，並包含下列三個部分：</span><span class="sxs-lookup"><span data-stu-id="d6d7f-108">The JMS MQRFH2 Component sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case and consists of the following three parts:</span></span>  
  
- <span data-ttu-id="d6d7f-109">第 1 部分示範失真標頭保留從 IBM WebSphere MQ，透過 ESB 和 BizTalk Server，再回到 IBM WebSphere MQ 會傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="d6d7f-109">Part 1 demonstrates full-fidelity header preservation as a message travels from IBM WebSphere MQ, through ESB and BizTalk Server, and back to IBM WebSphere MQ.</span></span>  
  
- <span data-ttu-id="d6d7f-110">第 2 部分示範如何在 ESB 協調流程中的程式碼可以存取 MQRFH2 標頭屬性。</span><span class="sxs-lookup"><span data-stu-id="d6d7f-110">Part 2 demonstrates how code in an ESB orchestration can access MQRFH2 header properties.</span></span> <span data-ttu-id="d6d7f-111">在此情況下，指令碼會修改 JMS 標頭屬性，以指定目的地佇列名稱。</span><span class="sxs-lookup"><span data-stu-id="d6d7f-111">In this case, the code modifies a JMS header property to specify the destination queue name.</span></span>  
  
- <span data-ttu-id="d6d7f-112">第 3 部分示範大量載入的佇列訊息，並顯示應用程式將訊息路由至訊息內容中指定的目的地佇列的方式。</span><span class="sxs-lookup"><span data-stu-id="d6d7f-112">Part 3 demonstrates bulk loading a queue with messages and shows how the application routes messages to the destination queues specified as part of the message content.</span></span>  
  
  <span data-ttu-id="d6d7f-113">如需詳細資訊，請參閱 <<c0> [ 安裝和執行 JMS MQRFH2 元件範例](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="d6d7f-113">For more information, see [Installing and Running the JMS MQRFH2 Component Sample](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md).</span></span>