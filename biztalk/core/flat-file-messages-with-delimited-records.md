---
title: 具有分隔記錄的一般檔案訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ad7119b-4e39-43df-9dba-a04382eb6db2
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5dc9eb0253e2bfe8824f6395e1c619c23f0e551
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="flat-file-messages-with-delimited-records"></a>具有分隔記錄的一般檔案訊息
在一般檔案執行個體訊息中的分隔記錄包含由預先定義的字元或字元集分隔的巢狀記錄和/或個別欄位 (資料項目)。 系統根據這些個別的分隔符號來剖析欄位。 例如，請考慮一般檔案執行個體訊息中的下列分隔記錄，其中包含一個假設性的訂單中的兩個產品項目：  
  
```  
  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Electric-120vac,ITEM926-AA|Baby Monitor|1|39.98|Electric-4AA|2004-01-21  
  
```  
  
 此記錄中的一般檔案結構描述的合理定義描述如下︰  
  
-   具有子分隔符號 (,)、子順序前置詞以及標記 ITEMS 之分隔記錄命名的項目。  
  
    -   分隔，名為項目具有子分隔符號 &#124;的重複記錄;、 子順序中置以及標記項目。  
  
    -   名為 "partNum" 的屬性。  
  
    -   名為 "productName" 的項目。  
  
    -   名為 "quantity" 的項目。  
  
    -   名為 "USPrice" 的項目。  
  
    -   名為 "powerSource" 的項目。  
  
-   名為 "shipDate" 的選擇性項目。  
  
 指定這些記錄和欄位定義之後，一般檔案解譯器會產生等同於這些記錄的下列 XML。  
  
```  
  
<items>  
    <item partNum="872-AA">  
        <productName>Lawnmower</productName>  
        <quantity>1</quantity>  
        <USPrice>148.95</USPrice>  
        <powerSource>Electric-120vac</powerSource>  
    </item>  
    <item partNum="926-AA">  
        <productName>Baby Monitor</productName>  
        <quantity>1</quantity>  
        <USPrice>39.98</USPrice>  
        <powerSource>Electric-4AA</powerSource>  
        <shipDate>2004-01-21</shipDate>  
    </item>  
</items>  
  
```  
  
 有一些與分隔記錄相關的考量，會影響接收記錄後剖析記錄的方式，以及傳送記錄後建構記錄的方式，這些考量包括：  
  
-   用來覆寫分隔符號解譯以便將它們做為資料之一部分的一或多個字元。 如需詳細資訊，請參閱[方式解譯特殊字元做為欄位值的一部分](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)。  
  
-   在記錄開頭的一個選擇性標記，用來區別記錄與其他相似的記錄。 如需詳細資訊，請參閱[在分隔記錄中處理標記](../core/tag-handling-in-delimited-records.md)。  
  
-   在有最小長度限制的欄位中資料的對齊方式與其填補字元有關。 如需詳細資訊，請參閱[欄位填補](../core/field-padding.md)，[欄位左右對齊](../core/field-justification.md)，和[最小欄位長度內分隔記錄](../core/minimum-field-lengths-within-delimited-records.md)。  
  
-   在其他分隔記錄中的巢狀位置記錄。 如需詳細資訊，請參閱[巢狀位置記錄與分隔記錄](../core/nested-positional-and-delimited-records.md)。  
  
-   在固定長度的欄位中資料的對齊方式與其填補字元有關。 如需詳細資訊，請參閱[欄位左右對齊](../core/field-justification.md)。  
  
-   與分隔符號所分隔之資料相關的位置考量。 如需詳細資訊，請參閱[子順序考量](../core/child-order-considerations.md)。  
  
-   在接收或傳送一般檔案訊息時保留和隱藏分隔符號。 如需詳細資訊，請參閱[保留和隱藏分隔符號](../core/delimiter-preservation-and-suppression.md)。  
  
 若要協助您深入了解如何使用分隔的一般檔案，請參閱位於的 FlatFileReceive 和 FlatFileSend 資料夾中的範例[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Pipelines\AssemblerDisassembler\\。  
  
> [!NOTE]
>  如果您的一般檔案包含分隔和位置記錄，您必須設定 **結構** 根節點屬性 **分隔** 和 **結構** 為附屬記錄節點屬性 **分隔** 或 **Positional** 視情況。  
  
> [!NOTE]
>  一般檔案中的分隔欄位長度限制為 50000000 個字元。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md)   
 [如何建立一般檔案訊息的結構描述](../core/how-to-create-schemas-for-flat-file-messages.md)   
 [移轉一般檔案記錄](../core/migrating-flat-file-records.md)