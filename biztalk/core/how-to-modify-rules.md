---
title: 如何修改規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, activating
- deactivating business rules
- business rules, priorities
- activating business rules
- business rules, deactivating
- modifying, business rules
- business rules, modifying
ms.assetid: 661b2637-b5d6-4bde-9c42-24cd9e9d241c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce3fb78ce67b6c82f2301dfcb4cb2175aee0dde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254230"
---
# <a name="how-to-modify-rules"></a><span data-ttu-id="5c625-102">如何修改規則</span><span class="sxs-lookup"><span data-stu-id="5c625-102">How to Modify Rules</span></span>
<span data-ttu-id="5c625-103">變更規則的能力是商務規則範例的重要部分。</span><span class="sxs-lookup"><span data-stu-id="5c625-103">The ability to change rules is an important part of the business rules paradigm.</span></span> <span data-ttu-id="5c625-104">您可以使用兩種方式來修改原則中的規則：建立原則的新版本或是直接修改未發佈的原則版本。</span><span class="sxs-lookup"><span data-stu-id="5c625-104">You can modify rules within a policy in two ways: either by creating a new version of the policy, or by directly modifying an unpublished version of the policy.</span></span>  
  
 <span data-ttu-id="5c625-105">您可以個別修改規則、新增規則或刪除現有的規則。</span><span class="sxs-lookup"><span data-stu-id="5c625-105">You can modify rules individually, add new rules, or delete existing rules.</span></span> <span data-ttu-id="5c625-106">您可以從規則條件刪除述詞和邏輯運算子、刪除動作、在顯示中往上和往下移動動作，或是在條件中移動述詞和邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="5c625-106">You can delete predicates and logical operators from a rule condition, delete actions, move actions up and down in the display, or move predicates and logical operators within a condition.</span></span> <span data-ttu-id="5c625-107">不過，請記住述詞和邏輯運算子的顯示順序並不會決定評估的順序。</span><span class="sxs-lookup"><span data-stu-id="5c625-107">Keep in mind, however, the order in which the predicates and logical operators are displayed does not determine the order of evaluation.</span></span>  
  
 <span data-ttu-id="5c625-108">您可以將規則設定為非作用中，這樣在執行原則時就不會執行規則，或者您可以重新啟動已經停用的規則。</span><span class="sxs-lookup"><span data-stu-id="5c625-108">You can set a rule to be inactive, so that the rule is not executed when the policy is executed, or you can reactivate a rule that has been deactivated.</span></span>  
  
 <span data-ttu-id="5c625-109">您可以在規則上設定優先順序，這樣就會在不同優先順序的任何規則的動作之前或之後執行其動作。</span><span class="sxs-lookup"><span data-stu-id="5c625-109">You can set the priority on a rule so that its actions will be executed before or after the actions of any rule of different priority.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5c625-110">若您需要停止 SQL Server 電腦，請務必儲存任何未儲存的詞彙版本或詞彙定義，並關閉「商務規則編輯器」，這樣就不會遺失任何變更。</span><span class="sxs-lookup"><span data-stu-id="5c625-110">If you need to stop your SQL Server computer, be sure to save any unsaved vocabulary versions or vocabulary definitions, and close the Business Rule Composer so that no changes are lost.</span></span>  
  
 <span data-ttu-id="5c625-111">本主題包含下列工作的程序：</span><span class="sxs-lookup"><span data-stu-id="5c625-111">This topic contains procedures for the following tasks:</span></span>  
  
-   <span data-ttu-id="5c625-112">變更條件或動作中的引數</span><span class="sxs-lookup"><span data-stu-id="5c625-112">To change an argument in a condition or action</span></span>  
  
-   <span data-ttu-id="5c625-113">移動條件中的述詞</span><span class="sxs-lookup"><span data-stu-id="5c625-113">To move a predicate within a condition</span></span>  
  
-   <span data-ttu-id="5c625-114">移動條件中的邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="5c625-114">To move a logical operator within a condition</span></span>  
  
-   <span data-ttu-id="5c625-115">變更規則中的動作順序</span><span class="sxs-lookup"><span data-stu-id="5c625-115">To change the order of actions within a rule</span></span>  
  
-   <span data-ttu-id="5c625-116">刪除述詞、邏輯運算子或動作</span><span class="sxs-lookup"><span data-stu-id="5c625-116">To delete a predicate, logical operator, or action</span></span>  
  
-   <span data-ttu-id="5c625-117">啟動或停用規則</span><span class="sxs-lookup"><span data-stu-id="5c625-117">To activate or deactivate a rule</span></span>  
  
-   <span data-ttu-id="5c625-118">在規則上設定優先順序</span><span class="sxs-lookup"><span data-stu-id="5c625-118">To set a priority on a rule</span></span>  
  
### <a name="to-change-an-argument-in-a-condition-or-action"></a><span data-ttu-id="5c625-119">變更條件或動作中的引數</span><span class="sxs-lookup"><span data-stu-id="5c625-119">To change an argument in a condition or action</span></span>  
  
1.  <span data-ttu-id="5c625-120">在 [事實和定義] 視窗中，按一下適當的索引標籤，巡覽至您要作為引數的詞彙。</span><span class="sxs-lookup"><span data-stu-id="5c625-120">In the Facts and Definitions window, click the appropriate tab, and navigate to the term you want to use as an argument.</span></span> <span data-ttu-id="5c625-121">該詞彙必須是述詞或函式所預期的類型。</span><span class="sxs-lookup"><span data-stu-id="5c625-121">The term must be of a type expected by the predicate or function.</span></span>  
  
2.  <span data-ttu-id="5c625-122">按一下詞彙並將它拖曳至條件中的述詞引數或是動作中的函式引數。</span><span class="sxs-lookup"><span data-stu-id="5c625-122">Click the term and drag it onto a predicate argument in a condition or a function argument in an action.</span></span>  
  
### <a name="to-move-a-predicate-within-a-condition"></a><span data-ttu-id="5c625-123">移動條件中的述詞</span><span class="sxs-lookup"><span data-stu-id="5c625-123">To move a predicate within a condition</span></span>  
  
-   <span data-ttu-id="5c625-124">按一下述詞，並將它拖曳至另一個邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="5c625-124">Click the predicate, and drag it to another logical operator.</span></span>  
  
### <a name="to-move-a-logical-operator-within-a-condition"></a><span data-ttu-id="5c625-125">移動條件中的邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="5c625-125">To move a logical operator within a condition</span></span>  
  
-   <span data-ttu-id="5c625-126">按一下邏輯運算子，並將它拖曳至另一個邏輯運算子或**條件**。</span><span class="sxs-lookup"><span data-stu-id="5c625-126">Click the logical operator, and drag it onto another logical operator or onto **Conditions**.</span></span>  
  
### <a name="to-change-the-order-of-actions-within-a-rule"></a><span data-ttu-id="5c625-127">變更規則中的動作順序</span><span class="sxs-lookup"><span data-stu-id="5c625-127">To change the order of actions within a rule</span></span>  
  
-   <span data-ttu-id="5c625-128">按一下動作，然後按一下 **往上移動動作**或**往下移動動作**。</span><span class="sxs-lookup"><span data-stu-id="5c625-128">Click the action and then click **Move action up** or **Move action down**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c625-129">規則的動作將會依照引擎控制函式例外狀況所指定的順序執行，這些引擎控制函式將會在其他動作之後執行。</span><span class="sxs-lookup"><span data-stu-id="5c625-129">The actions of a rule will be executed in the order specified with the exception of engine control functions which are executed after the other actions.</span></span>  
  
### <a name="to-delete-a-predicate-logical-operator-or-action"></a><span data-ttu-id="5c625-130">刪除述詞、邏輯運算子或動作</span><span class="sxs-lookup"><span data-stu-id="5c625-130">To delete a predicate, logical operator, or action</span></span>  
  
-   <span data-ttu-id="5c625-131">按一下述詞、 邏輯運算子或動作，然後再按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="5c625-131">Click the predicate, logical operator, or action, and then click **Delete**.</span></span>  
  
### <a name="to-activate-or-deactivate-a-rule"></a><span data-ttu-id="5c625-132">啟動或停用規則</span><span class="sxs-lookup"><span data-stu-id="5c625-132">To activate or deactivate a rule</span></span>  
  
-   <span data-ttu-id="5c625-133">按一下 [規則]，然後在 [屬性] 視窗中設定**Active**為**True**或**False**。</span><span class="sxs-lookup"><span data-stu-id="5c625-133">Click the rule, and then in the Properties window, set **Active** to either **True** or **False**.</span></span>  
  
### <a name="to-set-a-priority-on-a-rule"></a><span data-ttu-id="5c625-134">在規則上設定優先順序</span><span class="sxs-lookup"><span data-stu-id="5c625-134">To set a priority on a rule</span></span>  
  
-   <span data-ttu-id="5c625-135">按一下 [規則]，然後在 [屬性] 視窗中設定**優先順序**為整數值。</span><span class="sxs-lookup"><span data-stu-id="5c625-135">Click the rule, and then in the Properties window, set **Priority** to an integer value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c625-136">優先順序是相對的，而且某個指定優先順序的規則其所有動作都將在具有較低優先順序值的規則動作之前執行。</span><span class="sxs-lookup"><span data-stu-id="5c625-136">Priorities are relative, and all of the actions of a rule of a given priority will be executed in order before any of the actions of a rule with a lower value for priority.</span></span> <span data-ttu-id="5c625-137">優先順序值預設為零，不過它可以是正數或負數。</span><span class="sxs-lookup"><span data-stu-id="5c625-137">The priority value defaults to zero, but it can be positive or negative.</span></span>