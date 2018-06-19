---
title: 處理未宣告的 Z 區段 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Z segments, 2.X schemas
- 2.X schemas, undeclared Z segments
- segments, undeclared [Z objects]
- Z objects, undeclared segments
ms.assetid: 8878bc93-1833-4bfc-b80e-305e4144739e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ff982aedee39ed60820a9f03db11d7e4d051a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204670"
---
# <a name="handling-undeclared-z-segments"></a>處理未宣告的 Z 區段
有兩種類型的 Z 區段： 宣告 Z 線段，而未宣告的 Z 線段。 時，您可以使用這些本機進行，它們很相似，它們是在您使用的方式大不相同。  
  
 您在訊息結構描述中包含宣告 Z 線段的定義和[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用它來處理訊息，就像 HL7 標準所定義的結構描述。 沒有結構描述定義了未宣告的 Z 區段。 包含未宣告的 Z 區段結尾的訊息，和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通過，而不需處理針對結構描述。 剖析器和序列化程式不會驗證它。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會將它視為二進位大型物件 (BLOB)。 僅檢查[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]沒有上未宣告的 Z 區段會驗證 BLOB 不包含任何現有的三個字元的結構描述標記。  
  
 您包含未宣告的 Z 區段，做為第三個部分或 Z 部分多部分訊息。 此訊息包含的標頭、 內文和 Z 組件。 Z 部分具有開頭為字母"Z"的區段識別碼。  
  
> [!NOTE]
>  Zpart 必須永遠包含資料。 指定在錯誤狀況的資料流結果為 null。 如果沒有資料包含在 Zpart [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Zpart 中插入 「 空白 」 這個字。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]使用內容屬性**ZPartPresent**來判斷是否要序列化的 Z 部分。  
  
> [!CAUTION]
>  [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]過測試 Zsegments ANSI 字元集，ANSI 字元的 Zsegment 行為是可預測的結果。 不過，使用其他字元集 Zsegments 中可能會導致無法預期的行為。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [在結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)