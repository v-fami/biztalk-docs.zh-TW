---
title: 議程與優先順序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, executing
- Business Rules Engine, agendas
- Business Rules Engine, priorities
- business rules, priorities
- business rules, examples
- Business Rules Engine, examples
- examples, Business Rules Engine
- Business Rules Engine, rules
ms.assetid: ca54f750-4f2d-4734-8e6e-7af1b4967e6a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4529753251c2bf7934616b91662bde836c8339e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230206"
---
# <a name="agenda-and-priority"></a><span data-ttu-id="2f99e-102">議程與優先順序</span><span class="sxs-lookup"><span data-stu-id="2f99e-102">Agenda and Priority</span></span>
<span data-ttu-id="2f99e-103">若要了解商務規則引擎如何評估規則與執行動作，您必須了解的概念*議程*和*優先順序*。</span><span class="sxs-lookup"><span data-stu-id="2f99e-103">To understand how the Business Rule engine evaluates rules and executes actions, you need to understand the concepts of *agenda* and *priority*.</span></span>  
  
## <a name="agenda"></a><span data-ttu-id="2f99e-104">議程</span><span class="sxs-lookup"><span data-stu-id="2f99e-104">Agenda</span></span>  
 <span data-ttu-id="2f99e-105">議程是引擎用來佇列要執行的規則之排程。</span><span class="sxs-lookup"><span data-stu-id="2f99e-105">The agenda is a schedule used by the engine to queue rules for execution.</span></span> <span data-ttu-id="2f99e-106">引擎執行個體具有議程，並做為單一原則，而不是一系列的原則。</span><span class="sxs-lookup"><span data-stu-id="2f99e-106">The agenda exists for an engine instance, and acts on a single policy, not on a series of policies.</span></span> <span data-ttu-id="2f99e-107">當事實判斷提示至工作記憶體，且符合指定規則的條件時，規則就會放置在議程中，並根據優先順序執行。</span><span class="sxs-lookup"><span data-stu-id="2f99e-107">When a fact is asserted into working memory and the conditions of a given rule are satisfied, the rule is placed on the agenda and executed according to priority.</span></span> <span data-ttu-id="2f99e-108">規則的動作會依照由上至下的順序來執行，接著再執行議程中下一個規則的動作。</span><span class="sxs-lookup"><span data-stu-id="2f99e-108">A rule's actions are executed in order from top to bottom, and then the actions of the next rule on the agenda are executed.</span></span>  
  
 <span data-ttu-id="2f99e-109">屬於一個規則的動作會被視為一個區塊，如此可以在移到下一個規則之前先執行所有動作。</span><span class="sxs-lookup"><span data-stu-id="2f99e-109">The actions belonging to a rule are treated as a block, so that all actions are executed before moving on to the next rule.</span></span> <span data-ttu-id="2f99e-110">不論區塊中的其他動做為何，規則區塊中的所有動作都會執行。</span><span class="sxs-lookup"><span data-stu-id="2f99e-110">All actions in a rule block will execute regardless of other actions in the block.</span></span> <span data-ttu-id="2f99e-111">如需判斷提示的詳細資訊，請參閱[引擎控制函式](../core/engine-control-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="2f99e-111">For more information about assertion, see [Engine Control Functions](../core/engine-control-functions.md).</span></span>  
  
 <span data-ttu-id="2f99e-112">下列範例示範議程的運作方式。</span><span class="sxs-lookup"><span data-stu-id="2f99e-112">The following example demonstrates how the agenda works.</span></span>  
  
 <span data-ttu-id="2f99e-113">**規則 1**</span><span class="sxs-lookup"><span data-stu-id="2f99e-113">**Rule1**</span></span>  
  
```  
IF  
Fact1 == 1  
THEN  
Action1  
Action2  
```  
  
 <span data-ttu-id="2f99e-114">**Rule2**</span><span class="sxs-lookup"><span data-stu-id="2f99e-114">**Rule2**</span></span>  
  
```  
IF  
Fact1 > 0  
THEN  
Action3  
Action4  
```  
  
 <span data-ttu-id="2f99e-115">將事實 Fact1 (其值為 1) 判斷提示至引擎。</span><span class="sxs-lookup"><span data-stu-id="2f99e-115">We assert the fact Fact1, which has a value of 1, into the engine.</span></span> <span data-ttu-id="2f99e-116">因為同時符合 Rule1 與 Rule2 的條件，所以這兩個規則都會移到議程中以執行其動作。</span><span class="sxs-lookup"><span data-stu-id="2f99e-116">Because the conditions of both Rule 1 and Rule 2 are satisfied, both rules are moved to the agenda for execution of their actions.</span></span>  
  
|<span data-ttu-id="2f99e-117">工作記憶體</span><span class="sxs-lookup"><span data-stu-id="2f99e-117">Working memory</span></span>|<span data-ttu-id="2f99e-118">議程</span><span class="sxs-lookup"><span data-stu-id="2f99e-118">Agenda</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="2f99e-119">Fact1 (value=1)</span><span class="sxs-lookup"><span data-stu-id="2f99e-119">Fact1 (value=1)</span></span>|<span data-ttu-id="2f99e-120">**規則 1**</span><span class="sxs-lookup"><span data-stu-id="2f99e-120">**Rule1**</span></span><br /><br /> <span data-ttu-id="2f99e-121">-Action1</span><span class="sxs-lookup"><span data-stu-id="2f99e-121">-   Action1</span></span><br /><span data-ttu-id="2f99e-122">-Action2</span><span class="sxs-lookup"><span data-stu-id="2f99e-122">-   Action2</span></span><br /><br /> <span data-ttu-id="2f99e-123">**Rule2**</span><span class="sxs-lookup"><span data-stu-id="2f99e-123">**Rule2**</span></span><br /><br /> <span data-ttu-id="2f99e-124">-Action3</span><span class="sxs-lookup"><span data-stu-id="2f99e-124">-   Action3</span></span><br /><span data-ttu-id="2f99e-125">-Action4</span><span class="sxs-lookup"><span data-stu-id="2f99e-125">-   Action4</span></span>|  
  
## <a name="priority"></a><span data-ttu-id="2f99e-126">優先權</span><span class="sxs-lookup"><span data-stu-id="2f99e-126">Priority</span></span>  
 <span data-ttu-id="2f99e-127">要執行的優先順序會設定在每個個別規則上，而所有規則的預設優先順序均為 0。</span><span class="sxs-lookup"><span data-stu-id="2f99e-127">Priority for execution is set on each individual rule, with a default priority of 0 for all rules.</span></span> <span data-ttu-id="2f99e-128">優先順序的範圍可從 0 的任一邊開始，數目愈大則優先順序愈高。</span><span class="sxs-lookup"><span data-stu-id="2f99e-128">The priority can range on either side of 0, with larger numbers having higher priority.</span></span> <span data-ttu-id="2f99e-129">會依照最高優先順序到最低優先順序的順序來執行動作。</span><span class="sxs-lookup"><span data-stu-id="2f99e-129">Actions are executed in order from highest priority to lowest priority.</span></span>  
  
 <span data-ttu-id="2f99e-130">下列範例顯示優先順序如何影響規則執行的順序。</span><span class="sxs-lookup"><span data-stu-id="2f99e-130">The following example shows how priority affects the order of execution for the rules.</span></span>  
  
 <span data-ttu-id="2f99e-131">**Rule1 (優先順序 = 0)**</span><span class="sxs-lookup"><span data-stu-id="2f99e-131">**Rule1 (priority = 0)**</span></span>  
  
```  
IF  
Fact1 == 1  
THEN  
Discount = 10%  
```  
  
 <span data-ttu-id="2f99e-132">**Rule2 (優先順序 = 10)**</span><span class="sxs-lookup"><span data-stu-id="2f99e-132">**Rule2 (priority = 10)**</span></span>  
  
```  
IF  
Fact1 > 0  
THEN  
Discount = 15%  
```  
  
 <span data-ttu-id="2f99e-133">已同時符合兩個規則的條件，但是會先執行 Rule2，因為它的優先順序比較高。</span><span class="sxs-lookup"><span data-stu-id="2f99e-133">The conditions for both rules have been met, but Rule2 is executed first because it has higher priority.</span></span> <span data-ttu-id="2f99e-134">最終的折扣是 10%，因為它是為 Rule1 執行的動作之結果，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="2f99e-134">The final discount is 10 percent, because it is the result of the action executed for Rule1, as shown in the following table.</span></span>  
  
|<span data-ttu-id="2f99e-135">工作記憶體</span><span class="sxs-lookup"><span data-stu-id="2f99e-135">Working memory</span></span>|<span data-ttu-id="2f99e-136">議程</span><span class="sxs-lookup"><span data-stu-id="2f99e-136">Agenda</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="2f99e-137">Fact1 (value=1)</span><span class="sxs-lookup"><span data-stu-id="2f99e-137">Fact1 (value=1)</span></span>|<span data-ttu-id="2f99e-138">**Rule2**</span><span class="sxs-lookup"><span data-stu-id="2f99e-138">**Rule2**</span></span><br /><br /> <span data-ttu-id="2f99e-139">折扣 = 15%</span><span class="sxs-lookup"><span data-stu-id="2f99e-139">Discount = 15%</span></span><br /><br /> <span data-ttu-id="2f99e-140">**規則 1**</span><span class="sxs-lookup"><span data-stu-id="2f99e-140">**Rule1**</span></span><br /><br /> <span data-ttu-id="2f99e-141">Discount = 10%</span><span class="sxs-lookup"><span data-stu-id="2f99e-141">Discount = 10%</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f99e-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f99e-142">See Also</span></span>  
 [<span data-ttu-id="2f99e-143">規則引擎</span><span class="sxs-lookup"><span data-stu-id="2f99e-143">Rule Engine</span></span>](../core/rule-engine.md)