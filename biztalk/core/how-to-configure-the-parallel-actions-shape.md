---
title: 如何設定平行動作圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Parallel Actions shape [Orchestration Designer], Terminate shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer], synchronizing data access
- Parallel Actions shape [Orchestration Designer]
- configuring [Orchestration Designer], Parallel Actions shapes
- Parallel Actions shape [Orchestration Designer], branching
- Parallel Actions shape [Orchestration Designer], about Parallel Actions shape
- Terminate shape [Orchestration Designer], Parallel Actions shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer], configuring
ms.assetid: 396d6182-f5dd-4aab-9edc-92efe236fd3e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 125d479a09eefb6771a884d2cddbfa98f34aeb36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247798"
---
# <a name="how-to-configure-the-parallel-actions-shape"></a><span data-ttu-id="43be4-102">如何設定平行動作圖形</span><span class="sxs-lookup"><span data-stu-id="43be4-102">How to Configure the Parallel Actions Shape</span></span>
![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")  
<span data-ttu-id="43be4-103">平行動作圖形</span><span class="sxs-lookup"><span data-stu-id="43be4-103">Parallel Actions shape</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="43be4-104">如果您將放入**Terminate**圖形放**平行動作**圖形，並包含分支**終止**執行時，在執行個體完成立即不論其他分支是否完成執行。</span><span class="sxs-lookup"><span data-stu-id="43be4-104">If you place a **Terminate** shape inside a **Parallel Actions** shape, and the branch with the **Terminate** on it is run, the instance completes immediately, regardless of whether other branches have finished running.</span></span> <span data-ttu-id="43be4-105">取決於您的設計，在此情況下的結果可能會無法預料。</span><span class="sxs-lookup"><span data-stu-id="43be4-105">Depending on your design, results might be unpredictable in this case.</span></span>  
  
## <a name="synchronization-of-data-access"></a><span data-ttu-id="43be4-106">資料存取的同步處理</span><span class="sxs-lookup"><span data-stu-id="43be4-106">Synchronization of data access</span></span>  
 <span data-ttu-id="43be4-107">可能的多個分支**平行動作**圖形會嘗試存取相同的資料。</span><span class="sxs-lookup"><span data-stu-id="43be4-107">It is possible that more than one branch of a **Parallel Actions** shape will attempt to access the same data.</span></span> <span data-ttu-id="43be4-108">為了避免錯誤，請將存取資料的任何圖形都放置在同步的範圍內。</span><span class="sxs-lookup"><span data-stu-id="43be4-108">To avoid errors, place any shapes that access the data inside synchronized scopes.</span></span> <span data-ttu-id="43be4-109">您可以指定的屬性中**範圍**圖形是同步或非同步。</span><span class="sxs-lookup"><span data-stu-id="43be4-109">You can specify in the properties of a **Scope** shape that it is synchronized or not synchronized.</span></span> <span data-ttu-id="43be4-110">如需詳細資訊，請參閱[範圍](../core/scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="43be4-110">For more information, see [Scopes](../core/scopes.md).</span></span>  
  
#### <a name="to-add-a-branch-to-a-parallel-actions-shape"></a><span data-ttu-id="43be4-111">若要將分支新增到平行動作圖形</span><span class="sxs-lookup"><span data-stu-id="43be4-111">To add a branch to a Parallel Actions shape</span></span>  
  
1.  <span data-ttu-id="43be4-112">以滑鼠右鍵按一下**平行動作**圖形，，然後按一下**新平行分支**。</span><span class="sxs-lookup"><span data-stu-id="43be4-112">Right-click the **Parallel Actions** shape, and then click **New Parallel Branch**.</span></span>  
  
     <span data-ttu-id="43be4-113">-或者-</span><span class="sxs-lookup"><span data-stu-id="43be4-113">—Or—</span></span>  
  
2.  <span data-ttu-id="43be4-114">在兩個現有的分支之間拖曳新的圖形。</span><span class="sxs-lookup"><span data-stu-id="43be4-114">Drag a new shape between two existing branches.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43be4-115">若要移除的分支**平行動作**圖形中，以滑鼠右鍵按一下您想要移除，然後按一下的分支**刪除**。</span><span class="sxs-lookup"><span data-stu-id="43be4-115">To remove a branch from a **Parallel Actions** shape, right-click the branch you want to remove, and then click **Delete**.</span></span>