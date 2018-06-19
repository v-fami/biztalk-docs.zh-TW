---
title: 基本 Types1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, data types
- JD Edwards OneWorld adapters, business functions
- .NET Framework, mapping [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], data types
- adapters [JD Edwards OneWorld adapters], .NET Framework
- JD Edwards OneWorld adapters, .NET Framework
- adapters [JD Edwards OneWorld adapters], business functions
ms.assetid: d306ea1b-fb74-4fa3-9681-405252928df1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e90cda6259567adf5236d0c28e576900d8b25271
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231854"
---
# <a name="basic-types"></a>基本類型
Microsoft BizTalk Adapter for JD Edwards OneWorld 僅提供對 JD Edwards OneWorld 商務功能的存取。 商務功能中繼資料是透過商務功能介面來讀取，並可用以尋找商務功能與相關資料結構的清單。 不論什麼情況，所有商務功能方法都會使用強型別的中繼資料。  
  
 所有商務功能方法都具有相同的呼叫慣例： 由系統衍生，三個參數和資料結構的指標。 下表列出商務功能資料型別的呈現方式。  
  
 **商務功能資料型別的**  
  
|JD Edwards OneWorld 資料型別|Description|WDSL 轉換|  
|-----------------------------------|-----------------|---------------------|  
|char|字元字串。|xsd:string 1|  
|int|短整數。|xsd:short|  
|long|長整數。|xsd:short|  
|字串|請參閱[處理字串值](../core/handling-string-values1.md)。|xsd:string|  
|JDEDATE|日期的特殊實作。|xsd:date|  
|MATH_NUMERIC|浮點值的特殊實作，包括貨幣值。|xsd: string 為 32|  
|Byte|不帶正負號的單一字元。|xsd:string 1|  
  
 下表包含 JD Edwards OneWorld 中的基本型別清單，及其對應至 Microsoft .NET Framework 的情形。  
  
 **基本類型，以及它們如何對應至 Microsoft.NET Framework**  
  
|JD Edwards OneWorld XE|.NET Framework|  
|----------------------------|--------------------|  
|char|字串|  
|int|Short|  
|long|Short|  
|字串|字串|  
|JDEDATE|System.DateTime|  
|MATH_NUMERIC|字串|  
|Byte|字串|  
  
> [!NOTE]
>  如果只有一個引數，且傳回引數為 void，則預留位置會取代為類別，外部部分則會變成傳回值。 例如：  
  
```  
org.apache.axis.holders.DateHolder becomes a java.util.Date.   
```  
  
 以下是方法簽章的範例：  
  
```  
void testDate1(org.apache.axis.holders.DateHolder date1  
        org.apache.axis.holders.DateHolder date2);  
  
java.util.Date testDate2(java.util.Date date);  
```  
  
## <a name="character-limited-strings"></a>有限字元的字串  
 在 JD Edwards OneWorld 中，有些字串有字元限制。 任何額外的字元都會導致錯誤。 若要檢視字串中的字元限制，您可以使用 Microsoft 配接器精靈。  
  
## <a name="see-also"></a>另請參閱  
 [使用 MATH_NUMERIC 類型](../core/using-the-math-numeric-type2.md)   
 [處理字串值](../core/handling-string-values1.md)   
 [附錄 a： 資料類型](../core/appendix-a-data-types.md)