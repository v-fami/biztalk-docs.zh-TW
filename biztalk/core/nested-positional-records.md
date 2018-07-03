---
title: 巢狀位置記錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e205e9d-f740-4177-b45a-5e1baadae99a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 618d5475842a9e5844f289a7ca77e4d9a725b130
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990215"
---
# <a name="nested-positional-records"></a><span data-ttu-id="eb52d-102">巢狀序數記錄</span><span class="sxs-lookup"><span data-stu-id="eb52d-102">Nested Positional Records</span></span>
<span data-ttu-id="eb52d-103">如果允許巢狀序數記錄**Max Occurs**子記錄的屬性設定為正整數。</span><span class="sxs-lookup"><span data-stu-id="eb52d-103">Nested positional records are allowed if the **Max Occurs** property of child records is set to a positive integer.</span></span> <span data-ttu-id="eb52d-104">欄位自動計算應該能夠處理新的深度。</span><span class="sxs-lookup"><span data-stu-id="eb52d-104">Field autocalculation should be able to handle the new depth.</span></span> <span data-ttu-id="eb52d-105">不過，此行為的方式有些修改。</span><span class="sxs-lookup"><span data-stu-id="eb52d-105">However, there is a modification to the way this behaves.</span></span> <span data-ttu-id="eb52d-106">特別是因為可能有空值分隔符號，所以只會在符合下列其中一個條件時，欄位位置的自動計算才會運作：</span><span class="sxs-lookup"><span data-stu-id="eb52d-106">Specifically, because of the possibility for null delimiters, autocalculation of field positions will function only if one of the following conditions is met:</span></span>  
  
- <span data-ttu-id="eb52d-107">選取的節點有中置分隔的父系。</span><span class="sxs-lookup"><span data-stu-id="eb52d-107">The selected node has a parent that is infix delimited.</span></span>  
  
- <span data-ttu-id="eb52d-108">選取的節點有指定的開始位置。</span><span class="sxs-lookup"><span data-stu-id="eb52d-108">The selected node has a specified starting position.</span></span>  
  
  <span data-ttu-id="eb52d-109">請注意，巢狀序數記錄和父系為分隔的容器 (分隔符號為空值) 之序數記錄有所不同。</span><span class="sxs-lookup"><span data-stu-id="eb52d-109">Note that there is a distinction between nested positional records and positional records whose parent is a delimited container where the delimiter is null.</span></span> <span data-ttu-id="eb52d-110">對於真正巢狀位置的結構而言，在決定深度時不能有任何模稜兩可之處。</span><span class="sxs-lookup"><span data-stu-id="eb52d-110">For structures to be truly nested positionally, there must not be any ambiguity in determining their length.</span></span> <span data-ttu-id="eb52d-111">例如，分隔的迴圈節點可以包含一個重複的序數記錄，出現 0 至 N 次。</span><span class="sxs-lookup"><span data-stu-id="eb52d-111">For example, a delimited loop node can contain a repeating positional record that occurs 0 to N times.</span></span> <span data-ttu-id="eb52d-112">不過，因為該迴圈節點本身由位置決定，而且也可能包含對等於重複序數記錄的欄位，所以必須確定重複序數記錄的出現次數 (正整數)。</span><span class="sxs-lookup"><span data-stu-id="eb52d-112">However, for that loop node itself to be positional, and possibly also contain fields as peers to the repeating positional record, the occurrence of the repeating positional record must be deterministic (a positive integer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb52d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb52d-113">See Also</span></span>  
 [<span data-ttu-id="eb52d-114">位置記錄考量</span><span class="sxs-lookup"><span data-stu-id="eb52d-114">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)