---
title: 在結構描述中建立自訂資料型別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2.X schemas, creating Z data types [Z objects]
- data types, creating [Z objects]
- Z objects, creating Z data types
ms.assetid: e545c849-d414-4d5d-bb56-d3f9d5238c70
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea38eb106b3554b72885355aaa9aef4928f4fda2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "25960676"
---
# <a name="creating-custom-data-types-in-schemas"></a>在結構描述中建立自訂資料型別
您可以建立自訂資料類型中 datatypes_\<*版本*\>.xsd 通用的結構描述。 您可以根據自訂資料類型，現有的資料類型，基底資料型別或列舉型別資料表中定義。  
  
### <a name="to-create-a-z-data-type"></a>若要建立 Z 資料類型  
  
1.  在 Visual Studio 的方案總管，開啟 常見的資料類型結構描述檔案 (**datatypes_\<*版本*\>.xsd**)，然後按一下 **開啟**.  
  
2.  在 BizTalk 編輯器 中，以滑鼠右鍵按一下**HL7DefinedDataTypes**，指向 **插入結構描述節點**，然後按一下 **子記錄**建立元件的資料類型，或按一下**子項目**建立簡單的資料類型。  
  
3.  三個字元標記開頭為"Z"的已命名的資料類型。  
  
4.  在 [屬性] 窗格中，鍵入您想要的數值**基底資料型別**，**資料型別**，和其他屬性，視需要。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [在結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [擴充列舉型別](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [處理未宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)