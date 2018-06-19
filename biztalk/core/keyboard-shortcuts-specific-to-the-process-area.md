---
title: 鍵盤快速鍵特有的 「 處理區域 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- keyboard shortcuts, Orchestration Designer
- Orchestration Designer, keyboard shortcuts
ms.assetid: d993d341-99f2-4788-b1f3-6a8b911e5278
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba60b23c6c8719789e8de6903dbb538fa5088b08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262062"
---
# <a name="keyboard-shortcuts-specific-to-the-process-area"></a><span data-ttu-id="129dc-102">「 處理區域的專用鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="129dc-102">Keyboard Shortcuts Specific to the Process Area</span></span>
<span data-ttu-id="129dc-103">下表描述 [處理區域] 中可用的鍵盤巡覽方式，[處理區域] 是設計介面的中央區域，用來定義協調流程的處理流程。</span><span class="sxs-lookup"><span data-stu-id="129dc-103">The following table describes the keyboard navigation available in the Process Area, the central area of the design surface used to define the process flow of the orchestration.</span></span>  
  
|<span data-ttu-id="129dc-104">索引鍵</span><span class="sxs-lookup"><span data-stu-id="129dc-104">Key</span></span>|<span data-ttu-id="129dc-105">效果</span><span class="sxs-lookup"><span data-stu-id="129dc-105">Effect</span></span>|  
|---------|------------|  
|<span data-ttu-id="129dc-106">DOWN ARROW</span><span class="sxs-lookup"><span data-stu-id="129dc-106">DOWN ARROW</span></span>|<span data-ttu-id="129dc-107">將選取範圍移至下一個連接線或下面的圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-107">Moves the selection to the next connecting line or shape below.</span></span> <span data-ttu-id="129dc-108">若圖形連接至下面的數個分支 (如同在 [決定] 圖形的情況)，則選取範圍會移至最左邊分支的第一個圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-108">If the shape is connected to several branches below (as in the case of a Decide shape), the selection moves to the first shape in the leftmost branch.</span></span><br /><br /> <span data-ttu-id="129dc-109">若選取範圍在協調流程的 [結束] 圖形上，則按下此按鍵會沒有作用，因為其下方已經沒有其他圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-109">If selection is on the End shape for the orchestration, pressing this key has no effect, because there are no more shapes below it.</span></span>|  
|<span data-ttu-id="129dc-110">向上鍵</span><span class="sxs-lookup"><span data-stu-id="129dc-110">UP ARROW</span></span>|<span data-ttu-id="129dc-111">將選取範圍移至下一個連接線或上面的圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-111">Moves the selection to the next connecting line or shape above.</span></span> <span data-ttu-id="129dc-112">若圖形連接至上面的數個分支，則選取範圍會移至最左邊分支的最後一個圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-112">If the shape is connected to several branches above, selection moves to the last shape on the leftmost branch.</span></span><br /><br /> <span data-ttu-id="129dc-113">按下此按鍵會沒有任何作用**啟動**選取圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-113">Pressing this key has no effect when the **Start** shape is selected.</span></span>|  
|<span data-ttu-id="129dc-114">向左鍵</span><span class="sxs-lookup"><span data-stu-id="129dc-114">LEFT ARROW</span></span>|<span data-ttu-id="129dc-115">若選取範圍是在 [傳送] 或 [接收] 圖形，且圖形連接至某個連接埠：</span><span class="sxs-lookup"><span data-stu-id="129dc-115">If the selection is on a Send or Receive shape and the shape is connected to a port:</span></span><br /><br /> <span data-ttu-id="129dc-116">-若圖形具有連至 [左連接埠介面] 中連接埠連接器，焦點和選取範圍會轉移至圖形的連接埠連接器。</span><span class="sxs-lookup"><span data-stu-id="129dc-116">-   If the shape has a port connector leading to a port in the Left Port Surface, focus and selection shift to the port connector of the shape.</span></span><br /><span data-ttu-id="129dc-117">-若圖形具有連至 [右連接埠介面] 中，按下此按鍵會沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="129dc-117">-   If the shape has a port connector leading to a port in the Right Port Surface, pressing this key has no effect.</span></span><br /><span data-ttu-id="129dc-118">-如果圖形有沒有連接埠連接器，巡覽作業和任何其他圖形一樣。</span><span class="sxs-lookup"><span data-stu-id="129dc-118">-   If the shape has no port connector, navigation is the same as with any other shape.</span></span><br /><br /> <span data-ttu-id="129dc-119">對於其他圖形 (或未連接至連接埠的 [傳送] 或 [接收] 圖形)：</span><span class="sxs-lookup"><span data-stu-id="129dc-119">For other shapes (or Send or Receive shapes not connected to a port):</span></span><br /><br /> <span data-ttu-id="129dc-120">-如果選取範圍位於分支中，且含有圖形的最新分支中，左邊分支左邊分支上將選取範圍移至最接近的圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-120">-   If the selection is in a branch, and a branch exists with shapes on it to the left of the current branch, the selection moves to the nearest shape on the branch to the left.</span></span><br /><span data-ttu-id="129dc-121">-索引鍵有協調流程中其他位置沒有作用。</span><span class="sxs-lookup"><span data-stu-id="129dc-121">-   The key has no effect anywhere else in the orchestration.</span></span>|  
|<span data-ttu-id="129dc-122">向右鍵</span><span class="sxs-lookup"><span data-stu-id="129dc-122">RIGHT ARROW</span></span>|<span data-ttu-id="129dc-123">與向左鍵相同，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="129dc-123">Same as the LEFT ARROW key, but in the opposite direction.</span></span>|  
|<span data-ttu-id="129dc-124">HOME</span><span class="sxs-lookup"><span data-stu-id="129dc-124">HOME</span></span>|<span data-ttu-id="129dc-125">將選取範圍變更至從協調流程之 [開始] 圖形連過來的連接器。</span><span class="sxs-lookup"><span data-stu-id="129dc-125">Selection changes to the connector that leads from the Start shape of the orchestration.</span></span>|  
|<span data-ttu-id="129dc-126">END</span><span class="sxs-lookup"><span data-stu-id="129dc-126">END</span></span>|<span data-ttu-id="129dc-127">將選取範圍變更至連至協調流程之 [結束] 圖形的連接器。</span><span class="sxs-lookup"><span data-stu-id="129dc-127">Selection changes to the connector that leads into the End shape of the orchestration.</span></span>|  
|<span data-ttu-id="129dc-128">NUM LOCK + -</span><span class="sxs-lookup"><span data-stu-id="129dc-128">NUM LOCK + -</span></span>|<span data-ttu-id="129dc-129">摺疊選取的複雜圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-129">Collapses the selected complex shape.</span></span>|  
|<span data-ttu-id="129dc-130">NUM LOCK + +</span><span class="sxs-lookup"><span data-stu-id="129dc-130">NUM LOCK + +</span></span>|<span data-ttu-id="129dc-131">展開選取的複雜圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-131">Expands the selected complex shape.</span></span>|  
|<span data-ttu-id="129dc-132">NUM LOCK + \*</span><span class="sxs-lookup"><span data-stu-id="129dc-132">NUM LOCK + \*</span></span>|<span data-ttu-id="129dc-133">展開選取的複雜圖形，及其擁有的任何子複雜圖形。</span><span class="sxs-lookup"><span data-stu-id="129dc-133">Expands the selected complex shape, plus any child complex shapes it may have.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="129dc-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="129dc-134">See Also</span></span>  
 [<span data-ttu-id="129dc-135">協調流程設計工具鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="129dc-135">Orchestration Designer Keyboard Shortcuts</span></span>](../core/orchestration-designer-keyboard-shortcuts.md)