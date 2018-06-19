---
title: 欄位左右對齊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04380208-9bfd-43cf-a279-104daea2b978
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da9209040e64380b3a7a167dd013a15232543a75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246078"
---
# <a name="field-justification"></a>欄位左右對齊

## <a name="overview"></a>概觀
欄位左右對齊關係著欄位中的資料字元是在附加填補字元的前面 (靠左對齊) 或後面 (靠右對齊)。  
  
 有時欄位中所包含的資料字元在該欄位中不需要所有的空格。 這是最常在位置記錄，其中固定的位元組數或欄位的字元，則為 true，由**Positional Length**和**Positional Offset**屬性。 這在資料項目小於欄位長度的實例中是很常見的，會在欄位未使用的部分填入填補字元。  
  
 分隔記錄中，這類填補也會發生時的值**Minimum Length with Pad Character**屬性超過儲存相關資料項目所需的空間。  
  
 在這兩個這類情況下，值**理由**屬性 (**左**或**右邊**) 之相關**欄位項目**或**欄位屬性**節點判斷是否填補字元會遵循 （靠左對齊） 的資料字元或填補字元會在前面 （靠右對齊） 的資料字元。  
  
 當一般檔案解譯器將一般檔案執行個體訊息轉換為相等的 XML 執行個體訊息，**理由**屬性可在剖析對應的欄位。 當一般檔案組合器將 XML 執行個體訊息轉換為相等的一般檔案執行個體訊息中，**理由**屬性用來判斷當填補字元相關聯的特定欄位中，如果有的話，應加入至資料流： 之前或之後的對應資料字元。  
  
## <a name="see-also"></a>另請參閱  
- [欄位考量](../core/field-considerations.md)   
- 下列屬性的詳細資訊[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    - 對齊方式 （一般檔案結構描述中的節點屬性）  
    - Positional Offset （一般檔案結構描述中的節點屬性）  
    - Positional Length （一般檔案結構描述中的節點屬性）