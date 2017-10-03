---
title: "表格抽選程式運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Extractor functoids
- Table Extractor functoids, about Table Extractor functoids
ms.assetid: cb5f6f15-f4e1-46d3-846e-6e2664699b62
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 837762dcf1bd0814494f05712eb7d616cdfa7180
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="table-extractor-functoid"></a><span data-ttu-id="6a04b-102">表格擷取程式運算質</span><span class="sxs-lookup"><span data-stu-id="6a04b-102">Table Extractor Functoid</span></span>
<span data-ttu-id="6a04b-103">**表格抽選程式**運算質可判定要從迴圈格線的每個資料列擷取哪些資料**表格迴圈**運算質代表列。</span><span class="sxs-lookup"><span data-stu-id="6a04b-103">The **Table Extractor** functoid determines which data to extract from each row of the looping grid as the **Table Looping** functoid presents the rows.</span></span> <span data-ttu-id="6a04b-104">您需要一個**表格抽選程式**運算質的輸出中的每個欄位。</span><span class="sxs-lookup"><span data-stu-id="6a04b-104">You need one **Table Extractor** functoid for each output field.</span></span> <span data-ttu-id="6a04b-105">例如，假設您的輸入執行個體訊息有單一格式的位址，但是您的輸出執行個體訊息需要兩個格式的位址，而且每個格式是已標記的。</span><span class="sxs-lookup"><span data-stu-id="6a04b-105">For example, suppose your input instance message had an address in a single format, but your output instance message needed the address in two formats with each format tagged.</span></span> <span data-ttu-id="6a04b-106">然後您就必須**表格抽選程式**運算質標記與位址的每個項目。</span><span class="sxs-lookup"><span data-stu-id="6a04b-106">Then you would need a **Table Extractor** functoid for the tag and for each element of the address.</span></span> <span data-ttu-id="6a04b-107">如需有關設定**表格抽選程式**運算質，請參閱[Table-Driven 迴圈組態](../core/table-driven-looping-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="6a04b-107">For more information about configuring the **Table Extractor** functoid, see [Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md).</span></span> <span data-ttu-id="6a04b-108">另請參閱[Table-Driven 迴圈範例](../core/table-driven-looping-example.md)。</span><span class="sxs-lookup"><span data-stu-id="6a04b-108">Also see [Table-Driven Looping Example](../core/table-driven-looping-example.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a04b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a04b-109">See Also</span></span>  
 <span data-ttu-id="6a04b-110">[表格迴圈運算質](../core/table-looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="6a04b-110">[Table Looping Functoid](../core/table-looping-functoid.md) </span></span>  
 <span data-ttu-id="6a04b-111">[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="6a04b-111">[How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="6a04b-112">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="6a04b-112">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="6a04b-113">[索引運算質](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="6a04b-113">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="6a04b-114">[反覆項目運算質](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="6a04b-114">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="6a04b-115">[迴圈運算質](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="6a04b-115">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="6a04b-116">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="6a04b-116">Record Count Functoid</span></span>](../core/record-count-functoid.md)