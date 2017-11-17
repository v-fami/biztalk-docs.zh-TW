---
title: "表格迴圈運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Looping functoids
- Table Looping functoids, about Table Looping functoids
ms.assetid: 6189a789-afe7-4e72-a778-2b0374db8f69
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c5e5f2967fb48bfe896c26246db1630266812f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="table-looping-functoid"></a><span data-ttu-id="00353-102">表格迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="00353-102">Table Looping Functoid</span></span>
<span data-ttu-id="00353-103">**表格迴圈**運算質可讓您建立用來建立輸出執行個體訊息的輸出值的資料表。</span><span class="sxs-lookup"><span data-stu-id="00353-103">The **Table Looping** functoid enables you to create a table of output values to use in creating the output instance message.</span></span> <span data-ttu-id="00353-104">表格中的資料可包含連結和常數。</span><span class="sxs-lookup"><span data-stu-id="00353-104">The data in the table can consist of links and constants.</span></span> <span data-ttu-id="00353-105">第一個輸入的參數**表格迴圈**運算質設定範圍，或多少次記錄迴圈。</span><span class="sxs-lookup"><span data-stu-id="00353-105">The first input parameter to the **Table Looping** functoid configures the scope, or how many times the records will loop.</span></span> <span data-ttu-id="00353-106">第二個輸入參數**表格迴圈**運算質決定有多少資料行在資料表中，而其餘輸入不依特定順序定義資料表，可能的資料格的值。</span><span class="sxs-lookup"><span data-stu-id="00353-106">The second input parameter for the **Table Looping** functoid determines how many columns are in the table, and the remaining inputs define possible cell values for the table, in no particular order.</span></span> <span data-ttu-id="00353-107">如需有關使用這些屬性的詳細資訊，請參閱[Table-Driven 迴圈組態](../core/table-driven-looping-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="00353-107">For more information about working with these properties, see [Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md).</span></span> <span data-ttu-id="00353-108">另請參閱[Table-Driven 迴圈範例](../core/table-driven-looping-example.md)。</span><span class="sxs-lookup"><span data-stu-id="00353-108">Also see [Table-Driven Looping Example](../core/table-driven-looping-example.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00353-109">**表格迴圈**運算質會重複它連接至迴圈記錄。</span><span class="sxs-lookup"><span data-stu-id="00353-109">The **Table Looping** functoid repeats with the looping record it is connected to.</span></span> <span data-ttu-id="00353-110">在每個重複項目中，它會在表格迴圈格線中為每一列迴圈一次，以產生多個輸出迴圈。</span><span class="sxs-lookup"><span data-stu-id="00353-110">Within each iteration, it loops once per row in the table looping grid, producing multiple output loops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00353-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00353-111">See Also</span></span>  
 <span data-ttu-id="00353-112">[表格抽選程式運算質](../core/table-extractor-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="00353-112">[Table Extractor Functoid](../core/table-extractor-functoid.md) </span></span>  
 <span data-ttu-id="00353-113">[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="00353-113">[How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="00353-114">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="00353-114">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="00353-115">[索引運算質](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="00353-115">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="00353-116">[反覆項目運算質](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="00353-116">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="00353-117">[迴圈運算質](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="00353-117">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="00353-118">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="00353-118">Record Count Functoid</span></span>](../core/record-count-functoid.md)