---
title: "建立自訂的資料表結構描述中 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, Z tables [Z objects]
- Z objects, creating Z tables
- 2.X schemas, creating Z tables
ms.assetid: d6ab8ac9-a835-4ec0-9ddd-76ff267a3cbd
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7c3ce69e60517f90af4031bf76691a551afcbe2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-custom-tables-in-schemas"></a>在結構描述中建立自訂的資料表
您可以建立自訂的資料表中 tablevalues_\<*版本*>.xsd 通用的結構描述。 您可以根據自訂資料表或資料表中定義的列舉型別上現有的資料類型，基底資料型別。  
  
### <a name="to-create-a-z-table"></a>若要建立 Z 資料表  
  
1.  在 [方案總管] 中，開啟通用的資料類型結構描述檔案 **tablevalues_\<*版本*>.xsd * *，然後按一下**開啟**。  
  
2.  在 BizTalk 編輯器 中，以滑鼠右鍵按一下**HL7DefinedTables**，指向 **插入結構描述節點**，然後按一下 **子欄位項目**。  
  
3.  開頭為字母"Z"標記的已命名資料表。  
  
4.  視需要請在 [屬性] 窗格中，輸入您想要用於特定屬性的值。  
  
5.  列舉型別與表格中的 屬性 窗格中，設定**Derived By**至**限制**，按一下 **列舉**，按一下省略符號 （...） 按鈕，如**列舉型別**，然後輸入您想要包含在 列舉編輯器 中列舉的值。 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [擴充列舉型別](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [處理未宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)