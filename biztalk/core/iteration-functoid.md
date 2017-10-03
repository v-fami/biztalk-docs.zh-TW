---
title: "反覆項目運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Iteration functoids
- Greater Than or Equal To functoids
- And functoids
- Less Than or Equal To functoids
ms.assetid: 24d8911d-2282-4b07-910c-eb2e846dc1f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a491b8829f23296e77ba5a89d12985e8ccd32783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="iteration-functoid"></a><span data-ttu-id="be66d-102">重複項目運算質</span><span class="sxs-lookup"><span data-stu-id="be66d-102">Iteration Functoid</span></span>
<span data-ttu-id="be66d-103">**反覆項目**運算質的輸出中迴圈的目前記錄的索引結構，在第一筆記錄，而第二個資料錄，2 的 1 開始等等。</span><span class="sxs-lookup"><span data-stu-id="be66d-103">The **Iteration** functoid outputs the index of the current record in a looping structure, beginning at 1 for the first record, 2 for the second record, and so on.</span></span>  
  
 <span data-ttu-id="be66d-104">下圖顯示**反覆項目**運算質結合**Greater Than 或 Equal To**運算質，**小於或等於**運算質和**和**建立的對等運算質**如**迴圈。</span><span class="sxs-lookup"><span data-stu-id="be66d-104">The following figure shows an **Iteration** functoid combined with a **Greater Than or Equal To** functoid, a **Less Than or Equal To** functoid, and an **And** functoid to create the equivalent of a **For** loop.</span></span>  
  
 <span data-ttu-id="be66d-105">![反覆項目運算質用法的對應](../core/media/iterationfunctoid.gif "iterationfunctoid")</span><span class="sxs-lookup"><span data-stu-id="be66d-105">![Map illustrating the use of the iteration functoid](../core/media/iterationfunctoid.gif "iterationfunctoid")</span></span>  
<span data-ttu-id="be66d-106">重複項目運算質對應</span><span class="sxs-lookup"><span data-stu-id="be66d-106">Iteration Functoid Map</span></span>  
  
 <span data-ttu-id="be66d-107">假設**Greater Than 或 Equal To**運算質會測試的值大於或等於 2，而**小於或等於**運算質會測試的值小於或等於 4。</span><span class="sxs-lookup"><span data-stu-id="be66d-107">Assume that the **Greater Than or Equal To** functoid tests for values greater than or equal to 2, and the **Less Than or Equal To** functoid tests for values less than or equal to 4.</span></span> <span data-ttu-id="be66d-108">在此情況下，**和**運算質會傳回**true**只針對記錄 2、 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="be66d-108">In that case, the **And** functoid will return **true** only for records 2, 3, and 4.</span></span> <span data-ttu-id="be66d-109">因此，輸出執行個體將會包含兩個、 三和四個輸入執行個體訊息的記錄。</span><span class="sxs-lookup"><span data-stu-id="be66d-109">Thus, the output instance will contain records two, three, and four of the input instance message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be66d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be66d-110">See Also</span></span>  
 <span data-ttu-id="be66d-111">[如何新增反覆項目運算質至對應](../core/how-to-add-iteration-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="be66d-111">[How to Add Iteration Functoids to a Map](../core/how-to-add-iteration-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="be66d-112">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="be66d-112">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="be66d-113">[索引運算質](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="be66d-113">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="be66d-114">[迴圈運算質](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="be66d-114">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="be66d-115">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="be66d-115">Record Count Functoid</span></span>](../core/record-count-functoid.md)