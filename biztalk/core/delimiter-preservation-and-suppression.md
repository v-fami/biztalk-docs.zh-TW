---
title: 保留和隱藏分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30985b94-625e-411a-8137-1c129bc197bf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bb92d9784fb9e12494757407898388d6f52725e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975471"
---
# <a name="delimiter-preservation-and-suppression"></a>保留和隱藏分隔符號

## <a name="overview"></a>概觀
有兩個適用於分隔記錄的屬性：**保留空白資料的分隔符號**並**隱藏尾端分隔符號**。 使用這些屬性來控制一般檔案組合器如何處理不存在的資料和尾端分隔符號與相關聯的分隔符號。 當您設定**保留空白資料的分隔符號**屬性設**是**（此為預設設定，） 分隔符號會包含在轉譯的一般檔案訊息：  
  
- 沒有資料的欄位。  
  
- 沒有資料也沒有關聯標記的直接附屬記錄。  
  
  當您設定**保留空白資料的分隔符號**屬性設**No**，分隔符號不會包含在轉譯的一般檔案的記錄和欄位，但不含資料。 此外，不論設定為何**保留空白資料的分隔符號**屬性，分隔符號不會納入的直接附屬記錄，但不含定義標記資料轉譯的一般檔案訊息。  
  
  當您設定**隱藏尾端分隔符號**屬性設**No** （這是預設值），轉譯的一般檔案訊息中可能包含一或多個尾端分隔符號。 當您設定**隱藏尾端分隔符號**屬性設**是**、 尾端分隔符號不會包含在轉譯的一般檔案訊息中。  

## <a name="special-scenarios"></a>特殊案例  
 有一些特殊的情況下，設定所造成的行為**保留空白資料的分隔符號**並**隱藏尾端分隔符號**屬性可能會發生衝突。 在此情況下，後者的屬性，與關聯的行為**隱藏尾端分隔符號**，將會優先。 此外，在某些特殊情況下，若您為這兩個屬性所選擇的設定可能互相衝突時，則會提出警告。  
  
 例如，請考慮**記錄**節點定義下列屬性值：  
  
- 節點名稱為 MyRec  
  
- 標記識別項為 Rec  
  
- 子分隔符號為 ,  
  
- 子系順序為 Infix  
  
  並定義包含五個**欄位項目**具有下列名稱的節點 (也可以是**Field 屬性**節點或附屬**記錄**節點):  
  
- FieldElem1  
  
- FieldElem2  
  
- FieldElem3  
  
- FieldElem4  
  
- FieldElem5  
  
  接下來，假設，下列主要的空 XML 片段，表示這個**記錄** 節點，會傳遞至一般檔案組合器。  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <FieldElem4 />  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 下表顯示所產生的輸出和相關聯的其他屬性，設定相關的結構描述節點，根據不同的設定需求**保留空白資料的分隔符號**(PDFED) 和**隱藏尾端分隔符號**(STD) 屬性。  
  
|PDFED 設定|STD 設定|輸出|其他節點需求|  
|---|---|---|---|  
|是|否|Rec,,,Val,,|無。|  
|否|是|Rec,Val|所有**欄位項目**節點必須設定為選擇性。|  
|是|是|Rec,,,Val|名為的節點**FieldElem4**並 **[fieldelem5]** 必須設定為選擇性。|  
|否|否|Rec,Val,,|所有**欄位項目**節點必須設定為選擇性。|  
  
 當這些屬性設定指定分隔符號不能保留或應該隱藏時，會在下列兩種情況下發出訊息，警告可能無法使用相同的結構描述剖析序列化的一般檔案資料：  
  
-   當**記錄**節點**保留空白資料的分隔符號**屬性設定為**No**和/或**隱藏尾端分隔符號**屬性設定為 **[是]** 分別包含附屬於**欄位項目**節點**欄位屬性**節點，或**記錄**不指定任何標記的節點。  
  
-   當下層**欄位項目**節點，**欄位屬性**節點，和**記錄**不指定任何標記的節點未設定為 optional (藉由設定**Min Occurs**屬性設定為零) 結構描述中。 當**隱藏尾端分隔符號**屬性設定為**是**，只有最後一個這類附屬節點都必須設定為選擇性。 當**保留空白資料的分隔符號**屬性設定為**No**，所有尾端附屬節點都必須設定為選擇性。  
  
> [!NOTE]
>  XML 項目相關聯 （大概是選擇項） 時，一律會保留分隔符號**記錄**，**欄位項目**，或**欄位屬性**節點會完全遺失從商務文件，除了當後面接著 「 記錄遺失的選擇性欄位的 XML 表示法。 也就是說，當資料和括住它的 XML 標記都遺失時，對應的分隔符號永遠都會包含在商務文件的一般檔案表示法中。  
  
 現在請變更結構描述，以兩個欄位項目 (緊接在遺失的欄位項目之後) 包含子記錄。 子記錄項目設定為使用&#124;（管線） 字元做為分隔符號。  
  
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
  
## <a name="see-also"></a>另請參閱  
- [分隔記錄考量](../core/delimited-record-considerations.md)   
- **保留空白資料 （一般檔案結構描述中的節點屬性） 的分隔符號**和**隱藏尾端分隔符號 （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
