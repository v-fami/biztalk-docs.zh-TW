---
title: "XLANG 的變數和運算子 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02512789-2cb9-4ba9-aa78-e59b248e6b24
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c1773b7af3ec029026ee884e6c1161e27a3c330
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="xlang-s-variables-and-operators"></a>XLANG 的變數和運算子
本節討論 XLANG/s 語言中使用的變數和運算子。  
  
## <a name="xlangs-variables"></a>XLANG/s 變數  
 變數代表儲存位置。 每個變數都具有型別，決定該變數可以儲存什麼樣的值。 XLANG/s 屬於型別安全的語言，其編譯器保證變數中儲存的值一定會有適當的型別。 XLANG/s 支援下列變數型別：  
  
-   訊息  
  
-   相互關聯集合  
  
-   服務連結  
  
-   連接埠  
  
-   辨別內建實值型別：**布林**，**位元組**， **Char**，**十進位**， **Double**， **Int16**， **Int32**， **Int64**， **SByte**，**單一**，**字串**，**UInt16**， **UInt32**，和**UInt64**  
  
-   物件  
  
-   列舉型別  
  
 XLANG/s 為上述每一個型別提供初始化語意。 這類初始化可以視為對該型別變數的指派。 在 XLANG/s 中，必須明確指派變數，才能取得或使用其值。  
  
## <a name="xlangs-operators"></a>XLANG/s 運算子  
 XLANG/s 支援下列運算子。 這些運算子幾乎完全符合 C# 中對應的運算子的功能。  
  
|運算子|Description|範例|  
|--------------|-----------------|-------------|  
|已選取|在算術溢位時引發錯誤|checked(x = y * 1000)|  
|取消選取|忽略算術溢位|unchecked(x = y * 1000)|  
|new|建立類別的執行個體|myObject = new MyClass;|  
|typeof|擷取型別|myMapType = typeof(myMap)|  
|succeeded|測試交易式範圍或協調流程是否順利完成|成功 (\<目前範圍或服務的子交易的交易識別碼\>)|  
|exists|測試訊息內容屬性是否存在|BTS.RetryCount exists Message_In|  
|+|一元加號運算子|+(int x)|  
|-|一元減號運算子|-(int x)|  
|!|邏輯否定|!myBool|  
|~|位元補數|x = ~y|  
|()|轉換|(bool) myInt|  
|*|乘|Weight = MyMsg.numOrders * 20|  
|/|除|x / y|  
|+|加|x + y|  
|-|減|x - y|  
|<<|左移|x << 2|  
|>>|右移|x >> 2|  
|<|小於|If (MyMsg.numOrders < 10)...|  
|>|大於|如果 (MyMsg.numOrders > 10)...|  
|<=|小於或等於|If (MyMsg.numOrders <= 10)...|  
|>=|大於或等於|如果 (MyMsg.numOrders > = 10)...|  
|==|等於|If (MyMsg.numOrders == 10)...|  
|!=|不等於|If (MyMsg.numOrders != 10)...|  
  
## <a name="see-also"></a>請參閱  
 [XLANG 的資料型別](../core/xlang-s-data-types.md)   
 [XLANG s 陳述式](../core/xlang-s-statements.md)   
 [XLANG 的運算式](../core/xlang-s-expressions.md)   
 [XLANG s 保留字](../core/xlang-s-reserved-words.md)   
 [XLANG-s 至 BPEL4WS 類型轉換](../core/xlang-s-to-bpel4ws-type-conversions.md)