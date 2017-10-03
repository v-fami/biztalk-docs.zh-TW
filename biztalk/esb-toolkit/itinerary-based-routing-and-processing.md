---
title: "路由和處理行程基礎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8354538-e45c-487d-a380-59f497ea060f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5405e1e37834071bb4a1295b5e99bde3bf6ec846
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="itinerary-based-routing-and-processing"></a><span data-ttu-id="62301-102">行程為基礎的路由和處理</span><span class="sxs-lookup"><span data-stu-id="62301-102">Itinerary-Based Routing and Processing</span></span>
<span data-ttu-id="62301-103">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]實作路由名單模式，透過使用自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="62301-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implements a routing slip pattern through the use of custom pipeline components.</span></span> <span data-ttu-id="62301-104">訊息中繼資料和其他因素，可用來判斷適當的路由名單，也稱為路線，要用於每個訊息。</span><span class="sxs-lookup"><span data-stu-id="62301-104">Message metadata and other factors are used to determine the appropriate routing slip, also known as an itinerary, to be used for each message.</span></span> <span data-ttu-id="62301-105">此路由 slip 執行訊息轉換、 叫用協調流程服務，以及定義訊息路由步驟[!INCLUDE[prague](../includes/prague-md.md)]將會執行，有效地減少從核心 BizTalk Server 引擎的訊息處理指示。</span><span class="sxs-lookup"><span data-stu-id="62301-105">This routing slip can perform message transformation, invoke orchestration services, and define message routing steps that [!INCLUDE[prague](../includes/prague-md.md)] will execute, effectively decoupling message processing instructions from the core BizTalk Server engine.</span></span>  
  
 <span data-ttu-id="62301-106">如需有關行程的處理方式的詳細資訊，請參閱[重要案例及開發工作](../esb-toolkit/key-scenarios-and-development-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="62301-106">For more information on how itineraries are processed, see [Key Scenarios and Development Tasks](../esb-toolkit/key-scenarios-and-development-tasks.md).</span></span>