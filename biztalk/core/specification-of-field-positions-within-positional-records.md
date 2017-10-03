---
title: "在位置記錄中欄位位置的規格 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33c2eee3-ec30-46c5-a143-a3d2e2f265a6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91a253c76e8f3394897514716978e1902cf2e3d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="specification-of-field-positions-within-positional-records"></a>在位置記錄中欄位位置的規格
若要定義序數記錄，您必須提供該記錄中欄位的位置和長度之相關資訊。 若記錄包含子記錄，則子記錄中欄位的位置和長度會納入包含記錄之相關資訊。  
  
 您為指定的值的總和**Positional Offset**和**Positional Length**特定屬性**欄位項目**或**欄位屬性**節點決定對應欄位專屬的字元數目。 在記錄及其任何子記錄中所有欄位的這些總和決定記錄中欄位的界限。  
  
> [!NOTE]
>  當**Count Positions In Bytes**屬性**結構描述**節點設定為**是**、 **Positional Length**和**位置位移**屬性指定的位元組，而不是字元。  

這些屬性查看詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="positional-offset-property"></a>Positional Offset 屬性  
 當一般檔案解譯器將一般檔案執行個體訊息轉換為相等的 XML 執行個體訊息時，您指定值的**Positional Offset**屬性定義所忽略的幾個字元 （或位元組）並透過該位置執行個體訊息中略過。 換句話說，在該開始位置和長度發生的任何資訊 (所指定的第二個**Positional Offset**屬性) 在 一般檔案執行個體訊息將不會複製到訊息的 XML 版本。  
  
 當一般檔案組合器將 XML 執行個體訊息轉換為相等的一般檔案執行個體訊息時，您指定值的**Positional Offset**屬性會定義填滿的數字字元 （或位元組）正在建立一般檔案執行個體訊息中該開始位置的空格字元。 空白字元永遠用來填滿位移位置，使用的字元無法設定。  
  
 **Positional Offset**屬性提供彈性為解譯序數記錄的內容。 本質上，這個屬性可讓您忽略在設為非零值欄位前的任何固定長度資料。 該固定長度資料可能是一或多個整個欄位資料或某個類型的常數資料，像是與欄位關聯的標記，不需要包含在一般檔案執行個體訊息對等的 XML 中。 如需詳細資訊，請參閱下列範例。  
  
## <a name="positional-length-property"></a>Positional Length 屬性  
 當一般檔案解譯器將一般檔案執行個體訊息轉換為相等的 XML 執行個體訊息時，您指定值的**Positional Length**屬性定義的字元 （或位元組） 的數目執行個體訊息中該位置欄位相關聯。 發生的開始位置和長度，一般檔案執行個體訊息中構成在欄位中，受限於提供由相關聯的其他資訊的資料的資訊**理由**和**填補字元**屬性。 如需有關左右對齊和欄位填補的概念性資訊，請參閱[欄位左右對齊](../core/field-justification.md)和[欄位填補](../core/field-padding.md)。  
  
 當一般檔案組合器將 XML 執行個體訊息轉換為相等的一般檔案執行個體訊息時，您指定值的**Positional Length**屬性定義幾個字元 （或位元組） 適用於撰寫與該欄位相關聯的資料。 若資料字元少於指定的欄位長度，則使用相關的填補字元填滿差距。 如果有資料字元多於指定欄位長度，開頭或結尾的資料會截斷為基礎的設定**理由**屬性，不包含在一般檔案執行個體訊息正在建構。  
  
> [!NOTE]
>  靠左對齊資料的尾端部分會被截斷並捨棄。 靠右對齊資料的開頭部分會被截斷並捨棄。  
  
## <a name="example"></a>範例  
 考量下列的記錄欄位定義。  
  
|欄位節點名稱|Offset|長度|填補字元|理由|  
|---------------------|------------|------------|-------------------|-------------------|  
|Field1|0|6|預設 (空格)|Left|  
|Field2|0|4|*|Right|  
|Field3|2|6|*|Left|  
|Field4|4|6|預設 (空格)|Right|  
  
 具備這些欄位定義之記錄的開始點發生下列字元資料流 (第一行用於計算字元位置)。  
  
```  
123456789012345678901234567890123456789012345678901234567890  
abc   **12345678**skip  here  
```  
  
 當這些欄位定義套用到此範例記錄資料時，一般檔案解譯器會產生以下對等 XML (其資料以粗體字顯示)。  
  
```  
<Field1>abc</Field1>  
<Field2>12</Field2>  
<Field3>5678</Field3>  
<Field4>here</Field4>  
```  
  
 下列觀察與此資料的剖析方式有關：  
  
-   Field1 與相關聯的字元 （長度為 6，沒有位移） 是 「`abc` "，但不包含空格 XML 中因為空白字元是 Field1 的 （預設） 填補字元，而 Field1 定義為靠左對齊。  
  
-   與 Field2 (長度為 4，沒有位移) 關聯的字元為 "`**12`"，但 XML 中不包含星號，因為星號字元已定義為 Field2 的填補字元，而 Field2 定義為靠右對齊。  
  
-   與 Field3 (長度為 6，位移為 2) 關聯的字元為 "`345678**`"，但由於位移的緣故，所以 XML 中不包含 3 和 4。 XML 中也不包含星號，因為星號字元已定義為 Field2 的填補字元，而 Field2 定義為靠左對齊。  
  
-   與 Field4 (長度為 6，位移為 4) 關聯的字元為 "`skip  here`"，但由於位移的緣故，所以 XML 中不包含字元順序 "`skip`"。 XML 中也不包含兩個空白字元，因為空白字元是 Field4 的 (預設) 填補字元，而 Field4 定義為靠右對齊。  
  
 若此範例中由一般檔案解譯器產生的 XML 使用相同的欄位定義傳遞給一般檔案組合器，則會產生相同的一般檔案資料，但有兩個例外：捨棄的位移順序 34 和跳過會以空白字元填滿 (在緊接著資料的行中以 `^` 字元表示)。  
  
```  
123456789012345678901234567890123456789012345678901234567890  
abc   **12  5678**      here  
          ^^      ^^^^  
  
```  
  
## <a name="see-also"></a>另請參閱  
-  [欄位考量](../core/field-considerations.md)    
-  [欄位左右對齊](../core/field-justification.md)   
-  [欄位填補](../core/field-padding.md)   
- 下列屬性的詳細資訊[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    - 計算位置，以位元組為單位 （一般檔案結構描述中的節點屬性）  
    - 對齊方式 （一般檔案結構描述中的節點屬性）  
    - Pad Character （一般檔案結構描述中的節點屬性） 
    - Positional Offset （一般檔案結構描述中的節點屬性）
    - Positional Length （一般檔案結構描述中的節點屬性）