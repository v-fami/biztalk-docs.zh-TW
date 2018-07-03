---
title: 使用 MATH_NUMERIC 類型 2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exponents, JD Edwards OneWorld adapters
- currency, JD Edwards OneWorld adapters
- MATH_NUMERIC type
- adapters [JD Edwards OneWorld adapters], currency
ms.assetid: 14d04576-0028-4af4-84bd-92c4ca492126
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13de687f158bc18f4fa6a036ab239a25774d02ba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998903"
---
# <a name="using-the-mathnumeric-type"></a>使用 MATH_NUMERIC 類型
本主題說明 MATH_NUMERIC 型別及其指數處理方式、最大位數與最大小數位數等相關細節， 並包含下列內容的討論：  
  
- 指數  
  
- 無效值  
  
- 運算精確度  
  
- CURRENCY  
  
  MATH_NUMERIC 型別是數值字串型別。 若要使用，請輸入下列格式的參數值：  
  
```  
<OptionalSign><IntegerAndFractionalPart><OptionalExponentPart>  
```  
  
 位置  
  
- `<OptionalSign>` 可以是`+`或`-`。 `+` 預設值。  
  
- `<IntegerAndFractionalPart>` 最多可有 32 個有效位數，不計入小數點符號。 JD Edwards OneWorld 安裝中的小數點符號需依據地區設定而定，一般是使用句點 (.) 或逗點 (,)。 數字可以是全部整數、全部小數或是部分整數部分小數，但是不得超過 32 個位數。  
  
- `<OptionalExponentPart>` 等於：  
  
  ```  
  'e' <OptionalSign><ExponentDigits>  
  ```  
  
  位置  
  
- `<OptionalSign>` 可以是`+`或-。 `+` 預設值。  
  
- `<ExponentDigits>` 最多可有兩位數。 您可以使用 63 到 -63 之間的值 (0 除外)。  
  
## <a name="valid-values"></a>有效的值  
 有效的 MATH_NUMERIC 值範例：  
  
-   123.045  
  
-   4089 (請注意，千位處沒有逗號)  
  
-   -9084  
  
-   -230.75  
  
-   0.010503  
  
-   1.023e-10，這等於 0.0000000001023  
  
-   0.097e5 或 0.097e+5，這等於 9700  
  
-   1.0e-32，等於 0.00000000000000000000000000000001  
  
     (此值有效，因為此處忽略整數 "0" 後，總共有 32 個有效的小數位數。)  
  
## <a name="invalid-values"></a>無效值  
 無效值需視值的種類而定。 太小的小數將視為零 (將喪失全部有效位數)。 整數包含太多有效位數會造成無法預期的後果。 在此情況下，JD Edwards OneWorld 不一定每次都會報告錯誤狀況。  
  
 太大或太小的指數會傳回無效值。  
  
 無效的 MATH_NUMERIC 值範例：  
  
- 1034.00000000000000000000000000001023 - 有效位數過多  
  
- 1.023e-64 - 指數太小  
  
- 0.00317e64 - 指數太大  
  
  除正負號與小數符號外的所有其他非數值字元都會造成無效值。  
  
## <a name="exponents"></a>指數  
 為方便輸入值，JD Edwards OneWorld MATH_NUMERIC 特地提供指數功能。 不過，大多數的傳回值不會包含指數 (32 個有效位數全部顯示出來)。  
  
## <a name="precision-for-operations"></a>運算精確度  
 如果運算會導致失去精確度，則會自動四捨五入。 例如：  
  
 1.9e-31 / 10.0 = 0.00000000000000000000000000000002  
  
 1.9e-31 / 100.0 = 0.00000000000000000000000000000000  
  
 在其他情況中，當非常大的正值乘以另一個正值時會出現無法預期的後果。  
  
 1.01e32 * 2.053e32 不會產生可靠的結果，並不會引發錯誤。  
  
 大多數的商務案例都不會超過這些範圍。  
  
## <a name="currency"></a>CURRENCY  
 當某個 JD Edwards OneWorld 商務功能預期收到貨幣值時，該商務功能一律會另外使用一個參數來代表四個字元的貨幣代碼。 除非您使用的貨幣與 JD Edwards OneWorld 系統預設的不同，否則通常不需要傳入此代碼。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 A：資料類型](../core/appendix-a-data-types.md)