---
title: 開發商務程序管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developing, process management solution tutorial
- process management solution tutorial, developing
ms.assetid: 3b590533-2b18-4e78-b9e5-88f4a680532f
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60632efe6cfc8d48d395d20949012354874c7e46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239638"
---
# <a name="developing-a-business-process-management-solution"></a><span data-ttu-id="c6d88-102">開發商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="c6d88-102">Developing a Business Process Management Solution</span></span>
<span data-ttu-id="c6d88-103">本節描述與設計解決方案相關的基本模式，以及這些模式如何轉譯為 BizTalk 元件與結構。</span><span class="sxs-lookup"><span data-stu-id="c6d88-103">This section describes the basic patterns involved in the design of the solution and how those patterns translate into BizTalk components and structures.</span></span> <span data-ttu-id="c6d88-104">本節也會在解決方案中逐步處理訂單訊息、提供其他實作詳細資料、讓您瞭解如何規劃解決方案，並提供訊息與檔案參考。</span><span class="sxs-lookup"><span data-stu-id="c6d88-104">It also follows an order message through processing in the solution, provides additional implementation details, tells you how to version and scale the solution, and provides message and file references.</span></span> <span data-ttu-id="c6d88-105">如需解決方案與其設計背後的商務需求的詳細資訊，請參閱 < 商務需求 > 中[了解商務程序管理解決方案](../core/understanding-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d88-105">For more information about the solution and the business requirements behind its design, see "Business Requirements" in [Understanding the Business Process Management Solution](../core/understanding-the-business-process-management-solution.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6d88-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="c6d88-106">In This Section</span></span>  
  
-   [<span data-ttu-id="c6d88-107">商務程序管理解決方案中的模式</span><span class="sxs-lookup"><span data-stu-id="c6d88-107">Patterns in the Business Process Management Solution</span></span>](../core/patterns-in-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="c6d88-108">商務程序管理解決方案的元件</span><span class="sxs-lookup"><span data-stu-id="c6d88-108">Components of the Business Process Management Solution</span></span>](../core/components-of-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="c6d88-109">商務程序管理解決方案中的處理</span><span class="sxs-lookup"><span data-stu-id="c6d88-109">Processing in the Business Process Management Solution</span></span>](../core/processing-in-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="c6d88-110">商務程序管理解決方案的實作重點</span><span class="sxs-lookup"><span data-stu-id="c6d88-110">Implementation Highlights of the Business Process Management Solution</span></span>](../core/implementation-highlights-of-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="c6d88-111">監視與 BAM 商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="c6d88-111">Monitoring the Business Process Management Solution with BAM</span></span>](../core/monitoring-the-business-process-management-solution-with-bam.md)  
  
-   [<span data-ttu-id="c6d88-112">版本控制商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="c6d88-112">Versioning the Business Process Management Solution</span></span>](../core/versioning-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="c6d88-113">商務程序管理解決方案參考</span><span class="sxs-lookup"><span data-stu-id="c6d88-113">Business Process Management Solution Reference</span></span>](../core/business-process-management-solution-reference.md)