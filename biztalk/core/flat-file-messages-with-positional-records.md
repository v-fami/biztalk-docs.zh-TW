---
title: 具有位置記錄的一般檔案訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72c17c25-3847-458e-a43e-0dbdc42db749
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42ad36873c5b252afb185f5e341de923942dea73
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005591"
---
# <a name="flat-file-messages-with-positional-records"></a>具有位置記錄的一般檔案訊息
在一般檔案執行個體訊息中的位置記錄包含每個均有預先定義長度的個別欄位 (資料項目)。 會根據這些長度來剖析欄位。 例如，請考慮下列一般檔案執行個體訊息的位置記錄，其中包含送貨地址 (第一行顯示為每個欄位保留的字元數目)。  
  
```  
123456789012345678901234567890123456789012345678901234567890123456789012345  
US        Alice Smith         123 Maple Street    Mill Valley    CA 90952  
```  
  
 在一般檔案結構描述中對此記錄的合理定義可描述為位置記錄 (稱之為 shipTo)，其中包含下列欄位：  
  
-   名稱為 [國家/地區] 的屬性，該屬性靠左對齊，長度為 10 個字元，包含零個字元位移。  
  
-   名稱為 [名稱] 的項目，該項目靠左對齊，長度為 20 個字元，包含零個字元位移。  
  
-   名稱為 [街道] 的項目，該項目靠左對齊，長度為 20 個字元，包含零個字元位移。  
  
-   名稱為 [縣市] 的項目，該項目靠左對齊，長度為 15 個字元，包含零個字元位移。  
  
-   名稱為 [省市] 的項目，該項目靠左對齊，長度為 2 個字元，包含零個字元位移。  
  
-   名稱為 [郵遞區號] 的項目，該項目靠左對齊，長度為 5 個字元，包含一個字元位移。  
  
 指定這些記錄和欄位定義之後，一般檔案解譯器會產生等同於此記錄的下列 XML。  
  
```  
<shipTo country/region="US">  
    <name>Alice Smith</name>  
    <street>123 Maple Street</street>  
    <city>Mill Valley</city>  
    <state>CA</state>  
    <zip>90952</zip>  
</shipTo>  
  
```  
  
 有一些與位置記錄相關的考量，會影響接收記錄後剖析記錄的方式，以及傳送記錄後建構記錄的方式，這些考量包括：  
  
-   用來填入每個欄位未使用部分的字元，稱為填補字元。 如需詳細資訊，請參閱[欄位填補](../core/field-padding.md)。  
  
-   記錄中的一個選擇性標記，用來區別記錄與其他相似的記錄。 標記通常出現在記錄的開頭，不過，它可以出現在記錄中的任何位置。 如需詳細資訊，請參閱[在位置記錄中處理標記](../core/tag-handling-in-positional-records.md)。 位置記錄可以定義為有標記或沒有標記，但是，一旦定義之後，會根據定義決定標記是否必須存在。  
  
-   在固定長度的欄位中資料的對齊方式與其填補字元有關。 如需詳細資訊，請參閱[欄位左右對齊](../core/field-justification.md)。  
  
-   在其他位置或分隔記錄中的巢狀位置記錄。 如需詳細資訊，請參閱[巢狀位置記錄](../core/nested-positional-records.md)。  
  
-   位置記錄中指定的欄位長度為特定的位元組數目，而不是特定的字元數目。 如需詳細資訊，請參閱[以位元組為單位計算位置](../core/position-counting-in-bytes.md)。  
  
 若要協助您深入了解如何使用位置一般檔案，請參閱位於 \Program Files\Microsoft BizTalk Server\SDK\Samples\Pipelines\AssemblerDisassembler 的 FlatFileReceive 和 FlatFileSend 資料夾中的範例\\。  
  
> [!NOTE]
>  如果您的一般檔案包含分隔和位置記錄，您必須設定**結構**根節點屬性**分隔**和**結構**屬性附屬記錄節點設為 **分隔**或**Positional**依適當情況。  
  
> [!NOTE]
>  位置記錄中的欄位長度限制為 50000000 個字元。  
  
## <a name="see-also"></a>請參閱  
 [一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md)   
 [如何建立一般檔案訊息的結構描述](../core/how-to-create-schemas-for-flat-file-messages.md)