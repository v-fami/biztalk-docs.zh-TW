---
title: 使用 MATH_NUMERIC 類型 1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards EnterpriseOne adapters], currency
- JD Edwards EnterpriseOne adapters, exponents
- adapters [JD Edwards EnterpriseOne adapters], exponents
- MATH_NUMERIC type
- currency, values [JD Edwards EnterpriseOne adapters]
- JD Edwards EnterpriseOne adapters, currency
- exponents, values [JD Edwards EnterpriseOne adapters]
ms.assetid: 2a302216-f0a6-4afb-8f7d-bb1475ea1c57
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec4a5df2d15f489d52c8e3d6dfc575f9e644c646
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288510"
---
# <a name="using-the-mathnumeric-type"></a>使用 MATH_NUMERIC 類型
本主題說明 MATH_NUMERIC 型別及其指數處理方式、最大位數與最大小數位數等相關細節， 其中亦包含下列討論：  
  
-   指數  
  
-   無效值  
  
-   運算精確度  
  
-   貨幣  
  
 MATH_NUMERIC 型別是數值字串型別。 若要使用，請輸入下列格式的參數值：  
  
```  
<OptionalSign><IntegerAndFractionalPart><OptionalExponentPart>  
  
```  
  
 位置  
  
 `<OptionalSign>`可以是`+`或`-`。 `+`預設值。  
  
 `<IntegerAndFractionalPart>` 最多可有 32 個有效位數，不計入小數點符號。 小數點符號是地區設定特定的 JD Edwards EnterpriseOne 安裝 — 通常是句號 （.） 或逗號 （，）。 數字可以是全部整數、全部小數或是部分整數部分小數，但是不得超過 32 個位數。  
  
 `<OptionalExponentPart>` 等於：  
  
```  
'e' <OptionalSign><ExponentDigits>  
```  
  
 位置  
  
 `<OptionalSign>`可以是`+`或`-`。 `+`預設值。  
  
 `<ExponentDigits>` 最多可有兩位數。 您可以使用 63 到 -63 之間的值 (0 除外)。  
  
## <a name="valid-values"></a>有效的值  
 範例**有效**MATH_NUMERIC 值：  
  
-   123.045  
  
-   4089 (請注意，千位處沒有逗號)  
  
-   -9084  
  
-   -230.75  
  
-   0.010503  
  
-   1.023e-10，這等於 0.0000000001023  
  
-   0.097e5 或 0.097e+5，這等於 9700  
  
-   1.0e-32，這等於 0.00000000000000000000000000000001 (這是有效值，因為在此例中會忽略整數 '0'，有效的小數點後數字位數為 32 個)  
  
## <a name="invalid-values"></a>無效值  
 無效值需視值的種類而定。 太小的小數將視為零 (將喪失全部有效位數)。 整數包含太多有效位數會造成無法預期的後果。 在此情況下，JD Edwards EnterpriseOne 不一定會引發錯誤狀況。 指數若是太大或太小，也會傳回為無效值。  
  
 範例**無效**MATH_NUMERIC 值：  
  
-   1034.00000000000000000000000000001023 - 有效位數過多  
  
-   1.023e-64 - 指數太小  
  
-   0.00317e64 - 指數太大  
  
 除正負號與小數符號外的所有其他非數值字元都會造成無效值。  
  
## <a name="exponents"></a>指數  
 JD Edwards EnterpriseOne MATH_NUMERIC 提供的指數是為了方便用來輸入值。 不過，大多數的傳回值不會包含指數 (32 個有效位數全部顯示出來)。  
  
## <a name="precision-for-operations"></a>運算精確度  
 如果運算會導致失去精確度，則會自動四捨五入。 例如：  
  
 1.9e-31 / 10.0 = 0.00000000000000000000000000000002。  
  
 1.9e-31 / 100.0 = 0.00000000000000000000000000000000  
  
 在其他情況中，當非常大的正值乘以另一個正值時會出現無法預期的後果。 1.01e32 * 2.053e32 不會產生可靠的結果，並不會引發錯誤。 大多數的商務案例都不會超過這些範圍。  
  
## <a name="currency"></a>貨幣  
 當 JD Edwards EnterpriseOne 商務功能需要貨幣值時，商務功能永遠會有一個參數用於四字元貨幣代碼。 除非您要使用和 JD Edwards EnterpriseOne 系統設定的預設值不同的貨幣，否則並不需要傳遞此代碼。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 b： 資料類型](../core/appendix-b-data-types.md)