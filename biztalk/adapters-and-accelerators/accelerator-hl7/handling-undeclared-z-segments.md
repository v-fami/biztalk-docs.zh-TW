---
title: 處理未宣告的 Z 區段 |Microsoft Docs
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
ms.openlocfilehash: 633c1d338a87bef7c0fe53ff5df7f53438eac843
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990015"
---
# <a name="handling-undeclared-z-segments"></a>處理未宣告的 Z 區段
有兩種類型的 Z 區段： 宣告的 Z 區段和未宣告的 Z 區段。 雖然它們的相似處，在於您用於本機的用途，它們是在您使用的方式非常不同。  
  
 您納入宣告的 Z 區段的定義訊息結構描述] 和 [Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會使用它來處理訊息時，就像 HL7 標準所定義的結構描述。 沒有結構描述定義的未宣告的 Z 區段。 您包含結尾的訊息時，未宣告的 Z 區段和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通過，而不需處理針對結構描述。 剖析器和序列化程式不會驗證它。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 會將其視為二進位大型物件 (BLOB)。 只檢查[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]未上未宣告的 Z 區段會驗證 BLOB 不包含任何現有的三個字元的結構描述標記。  
  
 您包含未宣告的 Z 區段，為第三個部分或 Z 部分的多部分訊息。 此訊息包含標頭、 內文和 Z 組件。 Z 組件會有開頭為字母"Z"的區段識別碼。  
  
> [!NOTE]
>  Zpart 一律必須包含資料。 指定在錯誤狀況的資料流結果為 null。 如果沒有資料包含在 Zpart， [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Zpart 中插入 「 空白 」 這個字。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 使用內容屬性**ZPartPresent**來判斷是否要序列化的 Z 部分。  
> 
> [!CAUTION]
>  Microsoft 已經測試 Zsegments ANSI 字元集，以 ANSI 字元的 Zsegment 行為是可預測的結果。 不過，使用其他字元集 Zsegments 中可能會導致無法預期的行為。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [結構描述中建立自訂資料類型](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [在結構描述中建立自訂資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)