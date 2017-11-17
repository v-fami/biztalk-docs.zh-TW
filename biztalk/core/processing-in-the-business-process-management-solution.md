---
title: "商務程序管理解決方案中的處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, process management solutions
ms.assetid: 0b26447e-d8f1-4084-aa34-6e7f8ffccea5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 145dd8e616048f1caaa1a59ec41d099e93e47880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="processing-in-the-business-process-management-solution"></a><span data-ttu-id="1f75c-102">商務程序管理解決方案中的處理</span><span class="sxs-lookup"><span data-stu-id="1f75c-102">Processing in the Business Process Management Solution</span></span>
<span data-ttu-id="1f75c-103">本節描述商務程序管理解決方案的運作方式： 如何處理訂單，它會使用插斷，以及如何處理例外狀況，該動作的方式可重試。</span><span class="sxs-lookup"><span data-stu-id="1f75c-103">This section describes how the Business Process Management Solution works: how it processes orders, how it makes use of interrupts, and how it handles exceptions so that actions can be retried.</span></span>  
  
 <span data-ttu-id="1f75c-104">訂單處理依賴兩個主要的協調流程， **OrderBroker**和**OrderManager**。</span><span class="sxs-lookup"><span data-stu-id="1f75c-104">Order processing relies on two main orchestrations, **OrderBroker** and **OrderManager**.</span></span> <span data-ttu-id="1f75c-105">**OrderBroker**協調流程的撰寫方式可以有多個訂單管理員協調流程，其中的每一種順序。</span><span class="sxs-lookup"><span data-stu-id="1f75c-105">The **OrderBroker** orchestration is written so that there can be multiple order manager orchestrations, one for each kind of order.</span></span> <span data-ttu-id="1f75c-106">解決方案僅包括一個**OrderManager**。</span><span class="sxs-lookup"><span data-stu-id="1f75c-106">The solution includes only one **OrderManager**.</span></span> <span data-ttu-id="1f75c-107">它的撰寫方式也是相當一般的，使其可適用於其他類型的訂單。</span><span class="sxs-lookup"><span data-stu-id="1f75c-107">It, too, is relatively generic so that it can be adapted to other types of orders.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f75c-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="1f75c-108">In This Section</span></span>  
  
-   [<span data-ttu-id="1f75c-109">OrderBroker 協調流程中處理</span><span class="sxs-lookup"><span data-stu-id="1f75c-109">Processing in the OrderBroker Orchestration</span></span>](../core/processing-in-the-orderbroker-orchestration.md)  
  
-   [<span data-ttu-id="1f75c-110">程序管理員邏輯</span><span class="sxs-lookup"><span data-stu-id="1f75c-110">Process Manager Logic</span></span>](../core/process-manager-logic.md)  
  
-   [<span data-ttu-id="1f75c-111">訂單處理階段中的處理</span><span class="sxs-lookup"><span data-stu-id="1f75c-111">Processing in the Order Processing Stages</span></span>](../core/processing-in-the-order-processing-stages.md)  
  
-   [<span data-ttu-id="1f75c-112">中斷商務程序管理解決方案中的處理</span><span class="sxs-lookup"><span data-stu-id="1f75c-112">Interrupt Handling in the Business Process Management Solution</span></span>](../core/interrupt-handling-in-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="1f75c-113">在商務程序管理解決方案中處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="1f75c-113">Exception Handling in the Business Process Management Solution</span></span>](../core/exception-handling-in-the-business-process-management-solution.md)