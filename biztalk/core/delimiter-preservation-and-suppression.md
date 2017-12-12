---
title: "保留和隱藏分隔符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30985b94-625e-411a-8137-1c129bc197bf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0b5a5c60d42892479feacc93aedb3802b11308c
ms.sourcegitcommit: d572ae5c887898adedcb3dfc5f83841beedd3434
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="delimiter-preservation-and-suppression"></a>保留和隱藏分隔符號

## <a name="overview"></a>概觀
適用於分隔記錄的兩個屬性：**保留空白資料的分隔符號**和**隱藏尾端分隔符號**。 您可以使用這些屬性來控制一般檔案組合器如何處理不存在的資料與尾端分隔符號與相關聯的分隔符號。 當您將**保留空白資料的分隔符號**屬性**是**（此為預設值），分隔符號會包含在轉譯的一般檔案訊息：  
  
-   沒有資料的欄位。  
  
-   沒有資料也沒有關聯標記的直接附屬記錄。  
  
 當您將**保留空白資料的分隔符號**屬性**否**，分隔符號不會包含在轉譯的一般檔案的記錄和欄位，但不含資料。 進一步，不論設定為何**保留空白資料的分隔符號**屬性的直接附屬記錄沒有定義了標記資料轉譯的一般檔案訊息中將不包含分隔符號。  
  
 當您將**隱藏尾端分隔符號**屬性**否**（此為預設值），轉譯的一般檔案訊息中可能包含一或多個尾端分隔符號。 當您將**隱藏尾端分隔符號**屬性**是**、 尾端分隔符號不會包含在轉譯的一般檔案訊息中。  

## <a name="special-scenarios"></a>特殊案例  
 有某些特殊情況下，設定所造成的行為**保留空白資料的分隔符號**和**隱藏尾端分隔符號**屬性可能會發生衝突。 在這種情況下，第二個屬性，與關聯的行為**隱藏尾端分隔符號**，更高的優先順序。 此外，在某些特殊情況下，若您為這兩個屬性所選擇的設定可能互相衝突時，則會提出警告。  
  
 例如，請考慮**記錄**定義具有下列屬性值的節點：  
  
-   節點名稱為 MyRec  
  
-   標記識別項為 Rec  
  
-   子分隔符號為 ,  
  
-   子系順序為 Infix  
  
 定義包含五個和**欄位項目**具有以下名稱的節點 (它們也可能是**欄位屬性**節點或附屬**記錄**節點):  
  
-   FieldElem1  
  
-   FieldElem2  
  
-   FieldElem3  
  
-   FieldElem4  
  
-   FieldElem5  
  
 接下來，假設，下列主要的空 XML 片段，這代表**記錄** 節點，會傳遞至一般檔案組合器。  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <FieldElem4 />  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 下表顯示產生的輸出和相關聯的其他屬性，設定相關的結構描述節點，根據不同的設定需求**保留空白資料的分隔符號**(PDFED) 和**隱藏尾端分隔符號**(STD) 屬性。  
  
|PDFED 設定|STD 設定|輸出|其他節點需求|  
|---|---|---|---|  
|是|否|Rec,,,Val,,|無。|  
|否|是|Rec,Val|所有**欄位項目**必須設定為選擇性節點。|  
|是|是|Rec,,,Val|節點名稱為**FieldElem4**和**[fieldelem5]**必須設定為選擇性。|  
|否|否|Rec,Val,,|所有**欄位項目**必須設定為選擇性節點。|  
  
 當這些屬性設定指定分隔符號不能保留或應該隱藏時，會在下列兩種情況下發出訊息，警告可能無法使用相同的結構描述剖析序列化的一般檔案資料：  
  
-   當**記錄**節點**保留空白資料的分隔符號**屬性設定為**否**及/或**隱藏尾端分隔符號**屬性設定為**是**，分別包含次級**欄位項目**節點**欄位屬性**節點，或**記錄**沒有標記已指定的節點。  
  
-   當次級**欄位項目**節點**欄位屬性**節點，和**記錄**沒有標記已指定的節點不會設定為選擇性 (藉由設定**Min Occurs**屬性設定為零) 在結構描述中。 當**隱藏尾端分隔符號**屬性設定為**是**，只有最後一個這類附屬節點都必須設定為選擇性。 當**保留空白資料的分隔符號**屬性設定為**否**，所有尾端附屬節點都必須設定為選擇性。  
  
> [!NOTE]
>  XML 項目相關聯 （假定可省略） 時，一律會保留分隔符號**記錄**，**欄位項目**，或**欄位屬性**節點會完全遺失從商務文件，除了當後面接著 「 記錄遺失的選擇性欄位的 XML 表示法。 也就是說，當資料和括住它的 XML 標記都遺失時，對應的分隔符號永遠都會包含在商務文件的一般檔案表示法中。  
  
 現在請變更結構描述，以兩個欄位項目 (緊接在遺失的欄位項目之後) 包含子記錄。 子記錄項目設定為使用 &#124;（管線） 字元做為分隔符號。  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <!-- <FieldElem4 /> -->  
    <ChildRec>  
        <InnerFieldElement1>Inner1</InnerFieldElement1>   
        <InnerFieldElement2>Inner2</InnerFieldElement1>  
    </ChildRec>  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 如果此記錄被傳遞給一般檔案解譯器，將不會保留 FieldElem4 的分隔符號，但是會如預期地分隔後續的記錄。  
  
```  
,,Val,,Inner1,Inner2,,  
```  
  
## <a name="see-also"></a>請參閱  
-  [分隔記錄考量](../core/delimited-record-considerations.md)   
-  **保留空白資料 （一般檔案結構描述中的節點屬性） 的分隔符號**和**隱藏尾端分隔符號 （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
