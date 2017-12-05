---
title: "XLANG-s 至 BPEL4WS 型別轉換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XLANG/s
- XLANG/s, warning
- XLANG/s, BPEL4WS
- XLANG/s, converting
ms.assetid: a35d4dba-9344-43c8-86e6-a373a4452579
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02412b86b8649b73cadb4715793f085682a1de74
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="xlang-s-to-bpel4ws-type-conversions"></a>XLANG-s 至 BPEL4WS 型別轉換
下表詳述各種 XLANG/s 建構和 BPEL4WS 建構之間的轉換。  
  
> [!CAUTION]
>  XPath 1.1 不支援指數或雙精度浮點數格式的數字。 XLANG/s 協調流程中這些格式的常值數值會使用 %f 格式匯出到 BPEL4WS，而可能會喪失一些精確度。  
  
## <a name="literals-if-the-literal-is-part-of-an-expression"></a>常值 (如果此常值是運算式的一部分)  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|字串、字元|XPath 字串|  
|整數，真實|XPath 數字|  
|布林值 "true"、"false"|XPath true()、false() 函式|  
  
## <a name="literals-standalone-assignment"></a>常值 (獨立指派)  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|常值常數|XSD 同等項目|  
  
## <a name="variables"></a>變數  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|變數參考|bpws:getContainerData(%varName%,  part, %locationPath%)|  
|訊息參考 (.NET 類型)|bpws:getContainerData(%msgName%, part, %locationPath%)|  
|訊息部分參考|bpws:getContainerData(%msgName%, %locationPath%)|  
|辨別欄位參考|bpws:getContainerData(%msgName%, %partName%, %locationPath%)|  
|訊息資料屬性參考|bpws:getContainerProperty(%msgName%, %propertyQName%)|  
  
## <a name="operators"></a>操作員  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|一元 +|忽略|  
|一元 -|XPath 一元 -|  
|一元 !|XPath not() 函式|  
|二進位 & &、 &#124; &#124;|XPath 'and'、'or' 運算子|  
|二進位 ==、!=、<=、<、>=、>|XPath '='、'! ='，' < ='，' <'、 '> ='、' >' 運算子|  
|二進位 +、-、*、% (含兩個整數運算元)|XPath '+'、'-'、'*'、'mod' 運算子|  
  
## <a name="xlangs-constructs-that-are-disallowed-in-bpel4ws"></a>BPEL4WS 中不允許的 XLANG/s 建構  
  
-   訊息內容屬性參考  
  
-   服務屬性參考  
  
-   連接埠屬性參考  
  
-   服務連結屬性參考  
  
-   一元 -- 非整數類型  
  
-   一元 ~  
  
-   轉換運算子  
  
-   二進位 / 含整數運算元  
  
-   二進位 +、-、*、%、/ (含非整數運算元)  
  
-   二進位 <=、<、>=、> (含非字串運算元)  
  
-   位元運算子 &、 ^、 &#124;  
  
-   移位運算子 <<、>>  
  
-   已檢查的運算式  
  
-   內建運算式  
  
-   遞增和遞減前後 ++、--  
  
-   物件引動過程 (含或不含 and/or 參考參數)  
  
-   'new' 運算子