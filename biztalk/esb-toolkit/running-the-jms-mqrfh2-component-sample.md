---
title: 執行 JMS MQRFH2 元件範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44f4b48c-398a-4ec1-a033-1fc4a76a305c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fcea4bca324f73ee37b63e78673140eae250692
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294262"
---
# <a name="running-the-jms-mqrfh2-component-sample"></a><span data-ttu-id="2b285-102">執行 JMS MQRFH2 元件範例</span><span class="sxs-lookup"><span data-stu-id="2b285-102">Running the JMS MQRFH2 Component Sample</span></span>
<span data-ttu-id="2b285-103">JMS MQRFH2 元件 」 範例包含三個部分：</span><span class="sxs-lookup"><span data-stu-id="2b285-103">The JMS MQRFH2 Component sample consists of three parts:</span></span>  
  
-   <span data-ttu-id="2b285-104">[執行 JMS MQRFH2 標頭保留範例](../esb-toolkit/running-the-jms-mqrfh2-header-preservation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="2b285-104">[Running the JMS MQRFH2 Header Preservation Sample](../esb-toolkit/running-the-jms-mqrfh2-header-preservation-sample.md).</span></span> <span data-ttu-id="2b285-105">因為訊息是從 IBM WebSphere MQ，透過 ESB 和 Microsoft BizTalk Server，然後再回到 IBM WebSphere MQ 這個部分會示範失真標頭的保留。</span><span class="sxs-lookup"><span data-stu-id="2b285-105">This part demonstrates full-fidelity header preservation as a message travels from IBM WebSphere MQ, through ESB and Microsoft BizTalk Server, and back to IBM WebSphere MQ.</span></span>  
  
-   <span data-ttu-id="2b285-106">[從協調流程 」 範例執行標頭屬性存取](../esb-toolkit/running-the-header-property-access-from-an-orchestration-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="2b285-106">[Running the Header Property Access from an Orchestration Sample](../esb-toolkit/running-the-header-property-access-from-an-orchestration-sample.md).</span></span> <span data-ttu-id="2b285-107">此組件會示範如何 ESB 協調流程內的程式碼可以存取 MQRFH2 標頭屬性。</span><span class="sxs-lookup"><span data-stu-id="2b285-107">This part demonstrates how code within an ESB orchestration can access MQRFH2 header properties.</span></span> <span data-ttu-id="2b285-108">在此情況下，程式碼會使用標頭屬性來指定目的地佇列名稱。</span><span class="sxs-lookup"><span data-stu-id="2b285-108">In this case, the code uses a header property to specify the destination queue name.</span></span>  
  
-   <span data-ttu-id="2b285-109">[執行大量載入以內容為基礎的路由範例](../esb-toolkit/running-the-bulk-load-content-based-routing-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="2b285-109">[Running the Bulk Load Content-Based Routing Sample](../esb-toolkit/running-the-bulk-load-content-based-routing-sample.md).</span></span> <span data-ttu-id="2b285-110">此部分示範如何在大量載入的佇列訊息，並顯示如何應用程式將訊息路由傳送至訊息內容中指定的目的地佇列。</span><span class="sxs-lookup"><span data-stu-id="2b285-110">This part demonstrates bulk loading a queue with messages, and it shows how the application routes messages to the destination queues specified as part of the message content.</span></span>