---
title: "解決資料庫錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases
- errors, databases
ms.assetid: d7b1cc9f-3f3e-464a-8249-1fd03b2b4d76
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47a22877cf06f03f875138208281420e56963da9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="resolving-database-errors"></a><span data-ttu-id="af259-102">解決資料庫錯誤</span><span class="sxs-lookup"><span data-stu-id="af259-102">Resolving Database Errors</span></span>
<span data-ttu-id="af259-103">在 HL7 組織發行 HL7 Access 資料庫 Dataitem 和 TableValues 是 table_id 和 hl7_version 所連結的兩個資料表。</span><span class="sxs-lookup"><span data-stu-id="af259-103">In the HL7 Access database that the HL7 organization publishes, DataItems and TableValues are two tables linked by table_id and hl7_version.</span></span> <span data-ttu-id="af259-104">下列某些資料項目參照 table_id，列在資料表中沒有值的資料庫跨查詢顯示：</span><span class="sxs-lookup"><span data-stu-id="af259-104">The following database cross-query shows that some data items refer to a table_id, which has no values listed in the table:</span></span>  
  
```  
select distinct d.table_id, d.hl7_version, t.table_item from DataElements as d left join TableValues as t on   
   d.table_id = t.table_id and d.hl7_version = t.hl7_version where d.table_id <>0 order by d.table_id  
```  
  
 <span data-ttu-id="af259-105">如果 HL7 Access 資料庫有遺失的列舉值，您必須跨檢查此值手動與 HL7 規格和結構描述中使用這些值。</span><span class="sxs-lookup"><span data-stu-id="af259-105">If the HL7 Access database has missing enumeration values, you must cross check the values manually with the HL7 specifications and use those values in your schema.</span></span> <span data-ttu-id="af259-106">將列舉清單加入至結構描述是一種方式處理此情況。</span><span class="sxs-lookup"><span data-stu-id="af259-106">One way to deal with this situation is to add an enumeration list to the schema.</span></span> <span data-ttu-id="af259-107">若要這樣做，請參閱[擴充列舉](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="af259-107">To do so, see [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af259-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af259-108">See Also</span></span>  
 <span data-ttu-id="af259-109">[使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="af259-109">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 [<span data-ttu-id="af259-110">擴充 HL7 2.X Z 物件結構描述</span><span class="sxs-lookup"><span data-stu-id="af259-110">Extending HL7 2.X Schemas with Z Objects</span></span>](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)