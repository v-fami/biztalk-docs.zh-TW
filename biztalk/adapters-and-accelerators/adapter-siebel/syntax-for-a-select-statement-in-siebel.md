---
title: "Siebel 中的 SELECT 陳述式的語法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, searching and sorting data using
- Data Provider for Siebel, SELECT statement
- SELECT statement, syntax for
ms.assetid: 8528b115-d6f3-420d-8617-0e56dc8922bf
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3eeb0a6d4a1fceebe7e16b3f71566f848e4a20f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="syntax-for-a-select-statement-in-siebel"></a>Siebel 中的 SELECT 陳述式的語法
使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，ADO.NET 用戶端可以藉由指定 WHERE 子句，表示有效的 Siebel 搜尋規格在 Siebel 商務元件中執行 SELECT 查詢。 SELECT 陳述式的語法為：  
  
```  
SELECT  
<column name 1> AS <column alias 1>,  
<column name 2> AS <column alias 2>,  
…  
FROM  
<Business object name>.<Business component name> AS <table alias>  
WHERE  
<filter condition>  
OPTION  
'ViewMode <value>'  
```  
  
 在上述語法 ViewMode 選項對應到 Siebel 系統的檢視模式，這是篩選的機制，來限制一組符合查詢的記錄。 允許的值組，請參閱 Siebel 文件。  
  
> [!NOTE]
>  如果在 WHERE 子句中的欄位名稱包含特殊字元或空格，請確定您一律將括在方括弧內的欄位名稱。  
  
> [!NOTE]
>  在 SELECT 查詢，其中包含含有特殊字元的別名名稱，請確定您包含方括號中的別名名稱。  
  
> [!NOTE]
>  [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援別名的資料表名稱在 SELECT 子句中，但不是在 WHERE 子句。  
  
## <a name="searching-and-sorting-data-using-the-data-provider-for-siebel"></a>搜尋和排序的資料提供者使用 siebel 資料  
 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] Siebel 系統所支援的搜尋規格為基礎的 SQL 陳述式中支援篩選條件。  
  
 搜尋規格的規則如下：  
  
-   一般比較運算子必須用來比較常數、 欄位或欄位至另一個欄位。 這些包括 =、 ！ =、 >、 <>、 =、 和 < =。  
  
    ```  
    Example: [Revenue] > 5000  
    ```  
  
-   字串常數必須括在雙引號內，並將字串值必須是區分大小寫。  
  
    ```  
    Example: [Type] != "COST LIST"  
    ```  
  
-   邏輯運算子 AND、 OR 和必須要變換正負號或運算式結合使用。 這些運算子; 會忽略區分大小寫例如，"和"等同於"AND"。  
  
    ```  
    Example: [Competitor] IS NOT NULL and [Competitor] != "N"  
    ```  
  
-   在搜尋規格中的欄位名稱必須括在方括號中。  
  
    ```  
    Example: [Conflict Id] = 0  
    ```  
  
-   LIKE 運算子可用來建立欄位會與常數比較運算式的文字字串或另一個欄位和相符項目僅前幾個字元的欄位是必要。 萬用字元"*"和"？" 必須用於分別指出任何數目的字元，以及單一字元。  
  
-   ADO.NET 用戶端可以指定原始 Siebel 商務物件、 商務元件和商務元件欄位名稱。 這些名稱必須括在方括號中，不含任何特殊字元或空白字元。 支援的查詢的範例包括：  
  
    ```  
    SELECT [Name], [Postal Code] FROM Account.Account where [Postal Code] != '11065'  
    SELECT [Name], [Postal Code], Id From Account.Account where [Postal Code] != '60626' Order BY Id ASC, Name DESC  
    SELECT * FROM [Admin Price List].[Price Book Items]  
    ```  
  
 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]支援排序依據排序規格排序 Siebel 所支援的 SQL 陳述式中的規格。 排序規格的規則如下：  
  
-   使用逗號來分隔排序規格排序; 中的欄位名稱例如，名稱、 位置  
  
-   若要表示以遞減順序排序清單中的欄位，包括 (DESC) 在欄位名稱後面，如同 「 開始日期 (DESC)。 」 如果未不指定任何排序順序，則會使用遞增的順序。 若要明確地指定遞增順序，請使用關鍵字 (ASC)。  
  
-   排序規格運算式必須是 255 個字元或更少。  
  
## <a name="see-also"></a>請參閱  
 [使用 .NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)