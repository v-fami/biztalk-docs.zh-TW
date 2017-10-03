---
title: "重新判斷提示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Assert function [Business Rules Engine]
ms.assetid: 9cd640a2-bfeb-4c7a-b737-1c92cc122a9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22fcc8be7760d85a12cb05c53137177703c0fa73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="reassert"></a><span data-ttu-id="e89f8-102">重新判斷提示</span><span class="sxs-lookup"><span data-stu-id="e89f8-102">Reassert</span></span>
<span data-ttu-id="e89f8-103">若要*重新判斷提示*表示呼叫**Assert**函式在引擎中的物件上的工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="e89f8-103">To *reassert* means to call the **Assert** function on an object that is already in the engine's working memory.</span></span> <span data-ttu-id="e89f8-104">重新判斷提示命令相當於對物件發出撤回命令，之後跟隨判斷指示命令。</span><span class="sxs-lookup"><span data-stu-id="e89f8-104">A reassert command is equivalent to issuing a retract command for the object, followed by an assert command.</span></span>  
  
## <a name="net-objects"></a><span data-ttu-id="e89f8-105">.NET 物件</span><span class="sxs-lookup"><span data-stu-id="e89f8-105">.NET Objects</span></span>  
 <span data-ttu-id="e89f8-106">此物件是第一個被撤回的物件，而且使用此物件 (在述詞或動作中) 的規則議程上的任何動作都會被移除。</span><span class="sxs-lookup"><span data-stu-id="e89f8-106">The object is first retracted and any actions on the agenda for rules that use the object (in a predicate or action) are removed.</span></span> <span data-ttu-id="e89f8-107">然後該物件會判斷提示回工作記憶體中，並評估為新判斷提示的任何物件。</span><span class="sxs-lookup"><span data-stu-id="e89f8-107">The object is then asserted back into working memory and evaluated as any object that is newly asserted.</span></span> <span data-ttu-id="e89f8-108">這表示在述詞中使用此物件的任何規則都會重新評估，而且會依適當的情況將其動作新增到議程中。</span><span class="sxs-lookup"><span data-stu-id="e89f8-108">This means that any rules that use the object in a predicate are re-evaluated and their actions are added to the agenda as appropriate.</span></span> <span data-ttu-id="e89f8-109">之前評估為任何規則**true**並使用其動作中的物件會將其重新加入到議程的動作。</span><span class="sxs-lookup"><span data-stu-id="e89f8-109">Any rules that previously evaluated to **true** and only use the object in their actions will have their actions re-added to the agenda.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="e89f8-110">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="e89f8-110">TypedXmlDocument</span></span>  
 <span data-ttu-id="e89f8-111">當最上層**TypedXmlDocument** (**TXD**) 重新判斷提示，子**TXD**之時，會建立最上層**TXD**一開始判斷提示具有不同的行為，根據的子狀態**TXD**s。</span><span class="sxs-lookup"><span data-stu-id="e89f8-111">When a top level **TypedXmlDocument** (**TXD**) is reasserted, the child **TXD**s that are created when the top level **TXD** is initially asserted have different behaviors depending on the state of the child **TXD**s.</span></span> <span data-ttu-id="e89f8-112">在新的子節點或子節點已變更，這表示到至少其中一個欄位已變更的原則中使用 規則動作，判斷提示，或重新判斷提示動作上執行的子節點。</span><span class="sxs-lookup"><span data-stu-id="e89f8-112">In the case of a new child node or a child node that is dirty, meaning that at least one of its fields has been changed in the policy by using a rule action, an assert, or reassert action is performed on the child node.</span></span> <span data-ttu-id="e89f8-113">未變更的現有子節點仍存在工作記憶體中。</span><span class="sxs-lookup"><span data-stu-id="e89f8-113">Any existing child node that is not dirty remains in the working memory.</span></span> <span data-ttu-id="e89f8-114">以下範例是一個簡化的實例，描述在重新判斷提示子節點的父節點時其子節點的行為。</span><span class="sxs-lookup"><span data-stu-id="e89f8-114">The following example is a simplified scenario that describes the behaviors of the child nodes when their parent node is reasserted.</span></span>  
  
 <span data-ttu-id="e89f8-115">假設有三個**TXD**目前在工作記憶體中的 s: **P**， **C**1， **C**2，和**C**3。</span><span class="sxs-lookup"><span data-stu-id="e89f8-115">Assume there are three **TXD**s currently in the working memory: **P**, **C**1, **C**2, and **C**3.</span></span> <span data-ttu-id="e89f8-116">**P**是最上層**TXD**，父節點; 每個子節點都包含欄位**x**。</span><span class="sxs-lookup"><span data-stu-id="e89f8-116">**P** is the top level **TXD**, the parent node; each child node contains a field **x**.</span></span>  
  
 <span data-ttu-id="e89f8-117">**P**</span><span class="sxs-lookup"><span data-stu-id="e89f8-117">**P**</span></span>  
  
 <span data-ttu-id="e89f8-118">**C**1 (**C**1。**x** = 1)</span><span class="sxs-lookup"><span data-stu-id="e89f8-118">**C**1 (**C**1.**x** = 1)</span></span>  
  
 <span data-ttu-id="e89f8-119">**C**2 (**C**2。**x** = 1)</span><span class="sxs-lookup"><span data-stu-id="e89f8-119">**C**2 (**C**2.**x** = 1)</span></span>  
  
 <span data-ttu-id="e89f8-120">**C**3 (**C**3。**x** = 1)</span><span class="sxs-lookup"><span data-stu-id="e89f8-120">**C**3 (**C**3.**x** = 1)</span></span>  
  
 <span data-ttu-id="e89f8-121">接著，假設下列作業已做為規則動作的結果執行：</span><span class="sxs-lookup"><span data-stu-id="e89f8-121">Next, assume the following operations have been performed as a result of rule action:</span></span>  
  
-   <span data-ttu-id="e89f8-122">欄位 (**x**) 值**C**2 更新。</span><span class="sxs-lookup"><span data-stu-id="e89f8-122">The field (**x**) value for **C**2 is updated.</span></span>  
  
-   <span data-ttu-id="e89f8-123">**C**3 會刪除使用使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="e89f8-123">**C**3 is deleted by using user code.</span></span>  
  
-   <span data-ttu-id="e89f8-124">如果是其他子節點， **D**，加入至**P**使用使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="e89f8-124">An additional child node, **D**, is added to **P** by using user code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e89f8-125">作業的「商務規則引擎」不會將節點標示為已變更，因為引擎不處理這些動作。</span><span class="sxs-lookup"><span data-stu-id="e89f8-125">A node will not be marked dirty by the Business Rule Engine from operations, of which the engine is not aware.</span></span> <span data-ttu-id="e89f8-126">例如，在外部應用程式中以程式設計方式新增、刪除或修改節點。</span><span class="sxs-lookup"><span data-stu-id="e89f8-126">For example, adding, deleting, or modifying a node programmatically in an external application.</span></span>  
  
 <span data-ttu-id="e89f8-127">工作記憶體中新的物件表示法如下：</span><span class="sxs-lookup"><span data-stu-id="e89f8-127">The new representation of the objects in working memory is as follows.</span></span>  
  
 <span data-ttu-id="e89f8-128">**P**</span><span class="sxs-lookup"><span data-stu-id="e89f8-128">**P**</span></span>  
  
 <span data-ttu-id="e89f8-129">**C**1 (**C**1。**x** = 1)</span><span class="sxs-lookup"><span data-stu-id="e89f8-129">**C**1 (**C**1.**x** = 1)</span></span>  
  
 <span data-ttu-id="e89f8-130">**C**2 (**C**2。**x** = *0*)</span><span class="sxs-lookup"><span data-stu-id="e89f8-130">**C**2 (**C**2.**x** = *0*)</span></span>  
  
 <span data-ttu-id="e89f8-131">**D**</span><span class="sxs-lookup"><span data-stu-id="e89f8-131">**D**</span></span>  
  
 <span data-ttu-id="e89f8-132">現在，重新判斷提示**P**。下列幾點摘要說明子節點的行為：</span><span class="sxs-lookup"><span data-stu-id="e89f8-132">Now, reassert **P**. The following points summarize the behaviors of the child nodes:</span></span>  
  
-   <span data-ttu-id="e89f8-133">節點**C**2 已重新判斷提示，因為它已經變更正在更新其欄位之後。</span><span class="sxs-lookup"><span data-stu-id="e89f8-133">Node **C**2 is reasserted, because it has become dirty after its field being updated.</span></span>  
  
-   <span data-ttu-id="e89f8-134">節點**C**3 會從工作記憶體撤回。</span><span class="sxs-lookup"><span data-stu-id="e89f8-134">Node **C**3 is retracted from the working memory.</span></span>  
  
-   <span data-ttu-id="e89f8-135">節點**D**判斷提示至工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="e89f8-135">Node **D** is asserted into the working memory.</span></span>  
  
-   <span data-ttu-id="e89f8-136">節點**C**1 中維持不變的工作記憶體，因為它未更新之前**P**重新判斷提示。</span><span class="sxs-lookup"><span data-stu-id="e89f8-136">Node **C**1 remains unchanged in the working memory, because it was not updated before **P** was reasserted.</span></span>  
  
## <a name="typeddatatable"></a><span data-ttu-id="e89f8-137">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="e89f8-137">TypedDataTable</span></span>  
 <span data-ttu-id="e89f8-138">如果**重新判斷提示**上發出**TypedDataRow**，該資料列會先撤回，然後再重新判斷提示至工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="e89f8-138">If **Reassert** is issued on a **TypedDataRow**, that row is retracted and then asserted into working memory.</span></span> <span data-ttu-id="e89f8-139">如果**重新判斷提示**上發出**TypedDataTable**，所有關聯**TypedDataRow**都會撤回，然進行判斷提示。</span><span class="sxs-lookup"><span data-stu-id="e89f8-139">If **Reassert** is issued on the **TypedDataTable**, all associated **TypedDataRow**s are retracted and then asserted.</span></span>  
  
## <a name="dataconnection"></a><span data-ttu-id="e89f8-140">DataConnection</span><span class="sxs-lookup"><span data-stu-id="e89f8-140">DataConnection</span></span>  
 <span data-ttu-id="e89f8-141">所有**TypedDataRow**擷取透過**DataConnection**不當所致。</span><span class="sxs-lookup"><span data-stu-id="e89f8-141">All **TypedDataRow**s retrieved through the **DataConnection** are retracted.</span></span> <span data-ttu-id="e89f8-142">使用的所有述詞**DataConnection**然後重新評估，造成**DataConnection**來重新建立相關查詢**TypedDataRow**s。</span><span class="sxs-lookup"><span data-stu-id="e89f8-142">All predicates that use the **DataConnection** are then re-evaluated, causing the **DataConnection** to be requeried to create the relevant **TypedDataRow**s.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89f8-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e89f8-143">See Also</span></span>  
 [<span data-ttu-id="e89f8-144">引擎控制函式</span><span class="sxs-lookup"><span data-stu-id="e89f8-144">Engine Control Functions</span></span>](../core/engine-control-functions.md)