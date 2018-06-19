---
title: 如何在協調流程上設定交易屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- atomic transactions
- orchestrations, transactions
- transactions, long-running
- orchestrations, configuring
- transactions, atomic
ms.assetid: 8eec6019-4d96-4ed6-8a90-9403738d8af4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9164a9f5670a996a62450a19d802c97b89d8e242
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248814"
---
# <a name="how-to-configure-transactional-properties-on-an-orchestration"></a><span data-ttu-id="53944-102">如何在協調流程上設定交易屬性</span><span class="sxs-lookup"><span data-stu-id="53944-102">How to Configure Transactional Properties on an Orchestration</span></span>
<span data-ttu-id="53944-103">協調流程可視為不可部分完成的交易、長時間執行的交易，或兩者皆非。</span><span class="sxs-lookup"><span data-stu-id="53944-103">An orchestration can be treated as an atomic transaction, a long-running transaction, or neither.</span></span>  
  
### <a name="to-make-your-orchestration-an-atomic-transaction"></a><span data-ttu-id="53944-104">讓協調流程變成不可部分完成的交易</span><span class="sxs-lookup"><span data-stu-id="53944-104">To make your orchestration an atomic transaction</span></span>  
  
1.  <span data-ttu-id="53944-105">在 [協調流程檢視] 視窗中，選取**協調流程屬性**。</span><span class="sxs-lookup"><span data-stu-id="53944-105">In the Orchestration View window, select **Orchestration Properties**.</span></span>  
  
2.  <span data-ttu-id="53944-106">在 [屬性] 視窗中，選取**不可部分完成**的下拉式清單中**交易類型**屬性。</span><span class="sxs-lookup"><span data-stu-id="53944-106">In the Properties window, select **Atomic** in the drop-down for the **Transaction Type** property.</span></span>  
  
     <span data-ttu-id="53944-107">**批次**，**補償**，**隔離等級**，**重試**，**逾時**，和**交易識別項**就如同任何範圍，會顯示為 [屬性] 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="53944-107">**Batch**, **Compensation**, **Isolation Level**, **Retry**, **Timeout**, and **Transaction Identifier** appear as properties in the Properties window, just as they do for any scope.</span></span> <span data-ttu-id="53944-108">如需有關這些屬性的詳細資訊，請參閱[如何設定 「 範圍 」 圖形](../core/how-to-configure-the-scope-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="53944-108">For more information on these properties, see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).</span></span>  
  
### <a name="to-make-your-orchestration-a-long-running-transaction"></a><span data-ttu-id="53944-109">讓協調流程變成長時間執行的交易</span><span class="sxs-lookup"><span data-stu-id="53944-109">To make your orchestration a long-running transaction</span></span>  
  
1.  <span data-ttu-id="53944-110">在 [協調流程檢視] 視窗中，選取**協調流程屬性**。</span><span class="sxs-lookup"><span data-stu-id="53944-110">In the Orchestration View window, select **Orchestration Properties**.</span></span>  
  
2.  <span data-ttu-id="53944-111">在 [屬性] 視窗中，選取**長時間執行**的下拉式清單中**交易類型**屬性。</span><span class="sxs-lookup"><span data-stu-id="53944-111">In the Properties window, select **Long Running** in the drop-down for the **Transaction Type** property.</span></span>  
  
     <span data-ttu-id="53944-112">**補償**，**逾時**，和**交易識別項**會顯示為 [屬性] 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="53944-112">**Compensation**, **Timeout**, and **Transaction Identifier** appear as properties in the Properties window.</span></span> <span data-ttu-id="53944-113">就像是任何範圍的屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="53944-113">For more information on these properties, just as they do for any scope.</span></span> <span data-ttu-id="53944-114">如需有關這些屬性的詳細資訊，請參閱[如何設定 「 範圍 」 圖形](../core/how-to-configure-the-scope-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="53944-114">For more information on these properties, see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53944-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53944-115">See Also</span></span>  
 [<span data-ttu-id="53944-116">建立交易式協調流程</span><span class="sxs-lookup"><span data-stu-id="53944-116">Making Orchestrations Transactional</span></span>](../core/making-orchestrations-transactional.md)