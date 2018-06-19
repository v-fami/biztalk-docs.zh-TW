---
title: 如何設定例外狀況圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Throw Exception shape [Orchestration Designer]
- orchestrations, errors
- Orchestration Designer, errors
ms.assetid: d3190f1b-db5e-4988-bff6-f7a276760ece
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07d156572484ba4fbe71533252ce4fe956136699
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248078"
---
# <a name="how-to-configure-the-throw-exception-shape"></a><span data-ttu-id="91000-102">如何設定例外狀況圖形</span><span class="sxs-lookup"><span data-stu-id="91000-102">How to Configure the Throw Exception Shape</span></span>
<span data-ttu-id="91000-103">您可以明確擲回例外狀況的協調流程中使用**擲回的例外狀況**圖形。</span><span class="sxs-lookup"><span data-stu-id="91000-103">You can explicitly throw exceptions in an orchestration by using the **Throw Exception** shape.</span></span> <span data-ttu-id="91000-104">執行擲回動作時，執行階段引擎會搜尋最接近且可以處理擲回之例外狀況類型的例外處理常式。</span><span class="sxs-lookup"><span data-stu-id="91000-104">When the throw is performed, the runtime engine will search for the nearest exception handler that can handle the type of exception being thrown.</span></span>  
  
 <span data-ttu-id="91000-105">首先，執行階段引擎會先在目前的協調流程中搜尋封閉式範圍，再循序考慮此範圍中相關的例外處理常式，以針對擲回的例外狀況類型，找出適當的處理常式。</span><span class="sxs-lookup"><span data-stu-id="91000-105">First, the current orchestration is searched for an enclosing scope, and the associated exception handlers of the scope are considered in order to locate the appropriate handler for the type of exception that has been thrown.</span></span>  
  
 <span data-ttu-id="91000-106">如果找不到適當的例外處理常式，便會在呼叫目前協調流程的協調流程中，搜尋含括目前協調流程之呼叫點的範圍。</span><span class="sxs-lookup"><span data-stu-id="91000-106">If no appropriate exception handler is found, the orchestration that called the current orchestration is searched for a scope that encloses the point of the call to the current orchestration.</span></span> <span data-ttu-id="91000-107">這項搜尋作業會繼續進行，直到找到可以處理目前例外狀況的例外處理常式為止。</span><span class="sxs-lookup"><span data-stu-id="91000-107">This search continues until an exception handler is found that can handle the current exception.</span></span>  
  
 <span data-ttu-id="91000-108">與例外狀況完全相符的例外狀況類別，屬於與擲回之例外狀況執行階段型別相同的類別，或是其基底類別。</span><span class="sxs-lookup"><span data-stu-id="91000-108">An exact match for the exception is an exception class that is of the same class as, or a base class of, the run-time type of the exception being thrown.</span></span>  
  
 <span data-ttu-id="91000-109">找到相符的例外處理常式之後，控制權便會轉移到例外處理常式的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="91000-109">After a matching exception handler is found, control is transferred to the first statement of the exception handler.</span></span>  
  
 <span data-ttu-id="91000-110">若相符例外處理常式的搜尋失敗，協調流程便會中止。</span><span class="sxs-lookup"><span data-stu-id="91000-110">If the search for matching exception handlers fails, the orchestration halts.</span></span> <span data-ttu-id="91000-111">交易可以幫助您降低這種狀況的影響。</span><span class="sxs-lookup"><span data-stu-id="91000-111">Transactions can help you minimize the impact of such an occurrence.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="91000-112">程序</span><span class="sxs-lookup"><span data-stu-id="91000-112">Procedure</span></span>  
  
#### <a name="to-configure-a-throw-exception-shape"></a><span data-ttu-id="91000-113">若要設定例外狀況圖形</span><span class="sxs-lookup"><span data-stu-id="91000-113">To configure a Throw Exception shape</span></span>  
  
-   <span data-ttu-id="91000-114">在 屬性 視窗中，選取 可用的物件類型，以從擲回**例外狀況物件**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="91000-114">In the Properties window, select an available object type to throw from the **Exception Object** drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="91000-115">選取 一般例外狀況中**擲回的例外狀況**圖形才**擲回的例外狀況**圖形位於例外狀況處理常式，而且您想要重新擲回目前例外狀況處理常式中攔截到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="91000-115">Select General Exception in the **Throw Exception** shape only if the **Throw Exception** shape is within an exception handler and you want to rethrow the exception caught in the current exception handler.</span></span> <span data-ttu-id="91000-116">如果您使用的一般例外狀況，您會在編譯期間收到錯誤**擲回的例外狀況**圖形中其他任何內容。</span><span class="sxs-lookup"><span data-stu-id="91000-116">You will receive an error during the compile if you use General Exception for a **Throw Exception** shape in any other context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91000-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91000-117">See Also</span></span>  
 [<span data-ttu-id="91000-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="91000-118">Exceptions</span></span>](../core/exceptions.md)