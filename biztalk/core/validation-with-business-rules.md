---
title: "使用商務規則驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, process management solutions
- process management solution tutorial, validating
- business rules, validating
- process management solution tutorial, business rules
ms.assetid: a67f3781-629a-4157-9a27-3b73d7a5a3a8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8926cf8bd95c2b90c7d16151b47f8893120b812e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="validation-with-business-rules"></a><span data-ttu-id="43f6b-102">使用商務規則驗證</span><span class="sxs-lookup"><span data-stu-id="43f6b-102">Validation with Business Rules</span></span>
<span data-ttu-id="43f6b-103">進行驗證的一個常用方法是使用商務規則架構來建構一組商務規則。</span><span class="sxs-lookup"><span data-stu-id="43f6b-103">A common way to do validation is to construct a set of business rules using the Business Rules Framework.</span></span> <span data-ttu-id="43f6b-104">然後在您要執行驗證的協調流程中使用「呼叫規則」圖形。</span><span class="sxs-lookup"><span data-stu-id="43f6b-104">Then you use the Call Rules shape in the orchestration where you want to perform validation.</span></span>  
  
 <span data-ttu-id="43f6b-105">在商務程序管理應用程式，**驗證**協調流程會使用商務規則來測試訂單是否有效。</span><span class="sxs-lookup"><span data-stu-id="43f6b-105">In the business process management application, the **Validation** orchestration uses business rules to test the validity of the order.</span></span>  
  
 <span data-ttu-id="43f6b-106">使用 「 商務規則架構可讓您變更的規則，而不需要重新編譯和重新部署**驗證**協調流程。</span><span class="sxs-lookup"><span data-stu-id="43f6b-106">Using the Business Rules Framework enables you to change the rules without recompiling and redeploying the **Validation** orchestration.</span></span> <span data-ttu-id="43f6b-107">代價是，對於簡單的規則集，您可能無法節省處理時間，由協調流程中的邏輯撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="43f6b-107">The trade-off is that for simple sets of rules, you may be able to save processing time by coding the logic in the orchestration.</span></span>  
  
 <span data-ttu-id="43f6b-108">如需有關使用 「 商務規則架構的詳細資訊，請參閱[建立和使用商務規則](../core/creating-and-using-business-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="43f6b-108">For more information about using the Business Rules Framework, see [Creating and Using Business Rules](../core/creating-and-using-business-rules.md).</span></span> <span data-ttu-id="43f6b-109">如需 「 呼叫規則 」 圖形的詳細資訊，請參閱[如何使用 [呼叫規則] 圖形](../core/how-to-use-the-call-rules-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="43f6b-109">For more information about the Call Rules shape, see [How to Use the Call Rules Shape](../core/how-to-use-the-call-rules-shape.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f6b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43f6b-110">See Also</span></span>  
 <span data-ttu-id="43f6b-111">[商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="43f6b-111">[Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="43f6b-112">程序管理員邏輯</span><span class="sxs-lookup"><span data-stu-id="43f6b-112">Process Manager Logic</span></span>](../core/process-manager-logic.md)