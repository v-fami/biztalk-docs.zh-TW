---
title: 基本 Types2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, data types
- adapters [JD Edwards EnterpriseOne adapters], data types
- data types, JD Edwards EnterpriseOne adapters
ms.assetid: 96a70f0d-f7f8-4e3b-9511-59b330910ead
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7e5c47d8760e9743ec11a62598581d9d20b3e53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230918"
---
# <a name="basic-types"></a>基本類型
Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 僅提供對 JD Edwards EnterpriseOne 商務功能的存取。 商務功能中繼資料是透過商務功能介面來讀取，並可用以尋找商務功能與相關資料結構的清單。 不論什麼情況，所有商務功能方法都會使用強型別的中繼資料。  
  
 所有商務功能方法都具有相同的呼叫慣例： 由系統衍生，三個參數和資料結構的指標。 下表顯示商務功能資料型別的呈現方式。  
  
|JD Edwards EnterpriseOne 資料型別|Description|WDSL 轉換|  
|----------------------------------------|-----------------|---------------------|  
|char|字元字串。|xsd:string 1|  
|int|短整數。|xsd:short|  
|long|長整數。|xsd:short|  
|字串|請參閱[處理字串值](../core/handling-string-values2.md)。|xsd:string|  
|JDEDATE|日期的特殊實作。|xsd:date|  
|MATH_NUMERIC|浮點值的特殊實作，包括貨幣值。|xsd: string 為 32|  
|Byte|不帶正負號的單一字元。|xsd:string 1|  
|JDEUTIME|同時包括日期和時間元件。<br /><br /> 資料類型會儲存所有日期/時間，以及依國際標準時間 (Coordinated Universal Time，UTC) 執行所有日期/時間計算。|xsd:dateTime|  
  
## <a name="see-also"></a>另請參閱  
 [使用 MATH_NUMERIC 類型](../core/using-the-math-numeric-type1.md)   
 [處理字串值](../core/handling-string-values2.md)   
 [附錄 b： 資料類型](../core/appendix-b-data-types.md)