---
title: "在運算式中使用運算子 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, operators
- XLANG/s, operators
- orchestrations, XLANG/s
ms.assetid: f0948ce2-c508-48aa-af79-d207f577b22f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 155aad11ecddd021b8e16892b5a5294087fedd4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-operators-in-expressions"></a>在運算式中使用運算子
在協調流程運算式中也可以使用下列的 XLANG/s 運算子。 這些運算子幾乎完全符合 C# 中對應的運算子的功能。  
  
|運算子|Description|範例|  
|--------------|-----------------|-------------|  
|checked()|在算術溢位時引發錯誤|checked(x = y * 1000)|  
|unchecked()|忽略算術溢位|unchecked(x = y * 1000)|  
|new|建立類別的執行個體|myObject = new MyClass;|  
|typeof|類型擷取|myMapType = typeof(myMap)|  
|succeeded()|測試交易式範圍或協調流程是否順利完成|成功 (\<目前範圍或服務的子交易的交易識別碼 >)|  
|exists|測試訊息內容屬性是否存在|BTS.RetryCount exists Message_In|  
|+|一元加號|+(int x)|  
|-|一元減號|-(int x)|  
|!|邏輯否定|!myBool|  
|~|位元補數|x = ~y|  
|()|強制轉型|(bool) myInt|  
|*|times|Weight = MyMsg.numOrders * 20|  
|/|除以|x / y|  
|+|加|x + y|  
|-|減|x - y|  
|<<|左移|x <\< 2|  
|>>|右移|x >> 2|  
|<|小於|如果 (MyMsg.numOrders \< 10)...|  
|>|大於|如果 (MyMsg.numOrders > 10)...|  
|<=|小於或等於|如果 (MyMsg.numOrders \<= 10)...|  
|>=|大於或等於|如果 (MyMsg.numOrders > = 10)...|  
|==|等於|If (MyMsg.numOrders == 10)...|  
|!=|不等於|If (MyMsg.numOrders != 10)...|  
|&|和|If (myByte & 255)...|  
|^|排除式 or|If (myByte ^ 1)...|  
|&#124;|或|如果 (myByte &#124; 1)...|  
|&&|條件式 and|If (MyMsg.numOrders > 10) && (MyMsg.numOrders < 100)|  
|&#124;&#124;|條件式 or|如果 (MyMsg.numOrders \< 10) &#124; &#124;(MyMsg.numOrders > 100)|  
|//|註解|//這是註解|  
  
> [!NOTE]
>  規則的差異一般運算式和篩選運算式會搭配**接收**圖形。  
  
## <a name="see-also"></a>另請參閱  
 [使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md)