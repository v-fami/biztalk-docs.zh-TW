---
title: "串聯運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Cascading
- Cascading functoids
ms.assetid: 03c46e7b-be1c-475e-b68b-f9d1d7732fce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d5e9cfcad2432eb83c8a251147bac76b20db0bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="cascading-functoids"></a><span data-ttu-id="97e01-102">串聯運算質</span><span class="sxs-lookup"><span data-stu-id="97e01-102">Cascading Functoids</span></span>
<span data-ttu-id="97e01-103">當一個運算質在連結到目的結構描述中的記錄或欄位之前，先連結到另一個運算質時，稱為串連運算質。</span><span class="sxs-lookup"><span data-stu-id="97e01-103">Functoids are said to be cascaded when one functoid is linked to another functoid before it is linked to a record or field in the destination schema.</span></span> <span data-ttu-id="97e01-104">例如，您可以建立串連運算質，其中兩個串連的字串會產生要傳送至目的結構描述的欄位中的第三個字串。</span><span class="sxs-lookup"><span data-stu-id="97e01-104">For example, you can create cascading functoids in which two concatenated strings produce a third string fed into a field in the destination schema.</span></span>  
  
 <span data-ttu-id="97e01-105">當您串連運算質時，可以在格線頁中建立多個連續的轉換。</span><span class="sxs-lookup"><span data-stu-id="97e01-105">When you cascade functoids, you can create multiple, consecutive transformations in the grid page.</span></span> <span data-ttu-id="97e01-106">雖然在一頁中可串連的運算質數目沒有限制，但請謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="97e01-106">While there is no limit to the number of functoids that you can cascade in a page, use cascading wisely.</span></span> <span data-ttu-id="97e01-107">複雜的串連會增加轉換輸入執行個體訊息為輸出執行個體訊息的時間，這會嚴重降低執行階段效能。</span><span class="sxs-lookup"><span data-stu-id="97e01-107">Complex cascading can increase the time to transform an input instance message into an output instance message, significantly reducing run time performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e01-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97e01-108">See Also</span></span>  
 <span data-ttu-id="97e01-109">[在對應中的運算質](../core/functoids-in-maps.md) </span><span class="sxs-lookup"><span data-stu-id="97e01-109">[Functoids in Maps](../core/functoids-in-maps.md) </span></span>  
 [<span data-ttu-id="97e01-110">使用運算質建立更複雜的對應</span><span class="sxs-lookup"><span data-stu-id="97e01-110">Using Functoids to Create More Complex Mappings</span></span>](../core/using-functoids-to-create-more-complex-mappings.md)