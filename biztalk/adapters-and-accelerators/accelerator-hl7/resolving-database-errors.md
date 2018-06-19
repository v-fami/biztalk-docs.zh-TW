---
title: 解決資料庫錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases
- errors, databases
ms.assetid: d7b1cc9f-3f3e-464a-8249-1fd03b2b4d76
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47a22877cf06f03f875138208281420e56963da9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206006"
---
# <a name="resolving-database-errors"></a>解決資料庫錯誤
在 HL7 組織發行 HL7 Access 資料庫 Dataitem 和 TableValues 是 table_id 和 hl7_version 所連結的兩個資料表。 下列某些資料項目參照 table_id，列在資料表中沒有值的資料庫跨查詢顯示：  
  
```  
select distinct d.table_id, d.hl7_version, t.table_item from DataElements as d left join TableValues as t on   
   d.table_id = t.table_id and d.hl7_version = t.hl7_version where d.table_id <>0 order by d.table_id  
```  
  
 如果 HL7 Access 資料庫有遺失的列舉值，您必須跨檢查此值手動與 HL7 規格和結構描述中使用這些值。 將列舉清單加入至結構描述是一種方式處理此情況。 若要這樣做，請參閱[擴充列舉](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)