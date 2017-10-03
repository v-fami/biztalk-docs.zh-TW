---
title: "使用多重訂單項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, multiple calls
- JD Edwards OneWorld adapters, multi-order numbers
- multiple edit line calls [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], multi-order numbers
- multi-order numbers [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], multiple calls
ms.assetid: 207ea92c-03f7-4117-8414-eb174e659d26
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 389e73ede2d1062c9907bd8640f38ce74ad6f316
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-multi-order-items"></a><span data-ttu-id="e28a1-102">使用多重訂單項目</span><span class="sxs-lookup"><span data-stu-id="e28a1-102">Using Multi-Order Items</span></span>
<span data-ttu-id="e28a1-103">由於 JD Edwards OneWorld API 的結構，如果您想要搭配 BizTalk Server 使用多重訂單編號，您必須在協調流程中執行多個編輯明細項目呼叫，以將那些明細項目新增至協調流程中。</span><span class="sxs-lookup"><span data-stu-id="e28a1-103">Due to the structure of the JD Edwards OneWorld API, if you want to use multi-order numbers with BizTalk Server, you must make multiple edit line calls in your orchestration to add those line items in an orchestration.</span></span> <span data-ttu-id="e28a1-104">例如，多重訂單項目在標頭處可能包含單一訂單編號，而詳細資料則包含數個項目訂單 (例如，玩具 1EA、手套 2EA)。</span><span class="sxs-lookup"><span data-stu-id="e28a1-104">For example, a multi-order item might contain a header with a single order number, and detail that includes several items orders (like Toy 1EA, Gloves 2EA).</span></span>  
  
 <span data-ttu-id="e28a1-105">若要使用多重編輯明細項目呼叫，則要由 BizTalk Server 開發人員負責建構。</span><span class="sxs-lookup"><span data-stu-id="e28a1-105">To use multiple edit line calls, it is the responsibility of the BizTalk Server developer to structure them.</span></span> <span data-ttu-id="e28a1-106">開發人員應在協調流程中建立內部迴圈，來執行那些呼叫。</span><span class="sxs-lookup"><span data-stu-id="e28a1-106">The developer should create an internal loop in the orchestration to make those calls.</span></span>  
  
 <span data-ttu-id="e28a1-107">JD Edwards OneWorld 系統支援多重編輯明細項目呼叫，但 API 則否。</span><span class="sxs-lookup"><span data-stu-id="e28a1-107">The JD Edwards OneWorld system supports multiple edit line calls, but the API does not.</span></span> <span data-ttu-id="e28a1-108">請查看「編輯明細項目」方法的結構，您便可看出其為簡維結構而且並非連續編號。</span><span class="sxs-lookup"><span data-stu-id="e28a1-108">If you look at the structure of the Edit Line method, it is a flat structure and not a sequence.</span></span> <span data-ttu-id="e28a1-109">因此，每當您想要插入明細項目時，就必須呼叫該函式。</span><span class="sxs-lookup"><span data-stu-id="e28a1-109">Therefore, you must call the function every time you want to insert a line item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28a1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e28a1-110">See Also</span></span>  
 [<span data-ttu-id="e28a1-111">規劃與架構</span><span class="sxs-lookup"><span data-stu-id="e28a1-111">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)