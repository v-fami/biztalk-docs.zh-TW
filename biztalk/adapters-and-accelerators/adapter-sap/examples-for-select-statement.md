---
title: "SELECT 陳述式的範例 mySAP 配接器在 BizTalk 中 |Microsoft 文件"
description: "選取範例和範例使用 mySAP 配接器在 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54a5a4ac-a994-4706-9735-a5a1a82b893b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 140e895bf8ec2fb65a848c8752dc8e141530bd85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="examples-for-select-statement"></a>SELECT 陳述式的範例
本主題說明各種不同的 SELECT 陳述式的範例語法。

## <a name="sample-statements"></a>範例陳述式 
  
-   若要列出名為 SPFLI 表所列的班機的相關詳細資料，請使用下列語法：  
  
    ```  
    Select * from SPFLI  
    ```  
  
-   若要擷取的資料儲存到名為在 flight.txt 檔案\\\SAPServer\Extracts，使用下列語法：  
  
    ```  
    Select * Into file '\\SAPServer\Extracts\flight.txt' from SPFLI  
    ```  
  
-   若要列出所有班機從 New York 抵 San Francisco 的詳細資料，使用下列語法：  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and cityto='SAN FRANCISCO'  
    ```  
  
-   若要列出的所有詳細資料 flights 從 New York 其`connid`欄位的值為 1000年到 5000 之間，請使用下列語法：  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and (connid>1000 and connid<5000)  
    ```  
  
-   若要列出所有班機從 New York 使用者指定的所在城市的詳細資料，使用下列語法：  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and cityto=@variable  
    ```  
  
     在本例中，建立名為的 SAP 參數`@variable`、 指定值，並將它加入至對應的命令物件。  
  
-   在 LIKE 子句的 SELECT 查詢中，只有百分比符號，"%"（適用於任何零或多個字元字串） 和底線"_"（適用於任何單一字元），是允許的特殊字元。 其他所有項目會被視為字串值，而且會被忽略。  
  
    -   示範如何使用百分比"%"的範例  
  
        ```  
        SELECT NAME1, PSTLZ  from KNA1 where (MANDT between 596 AND 999) AND NAME1 LIKE '%MODE%'  
        ```  
  
         在這裡，%模式會擷取所有記錄 Name1 其中包含字串 「 模式 」。  
  
    -   範例示範如何使用底線"_"  
  
        ```  
        SELECT NAME1  AS [MYANME],  LAND1, KUNNR  from KNA1 where (NAME1 LIKE 'D_' )  
        ```  
  
         在這裡，"D_"提取其中 Name1 以"D"開頭，且包含兩個字元的所有記錄。  
  
-   範例，示範"between"的述詞子句  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where (MANDT between 596 AND 999) AND NAME1 LIKE '%MODE%'  
    ```  
  
-   範例，示範 「 不之間"述詞子句  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where (MANDT not between 596 AND 599) AND NAME1 LIKE '%MODE%'  
    ```  
  
-   使用聯結和 TOP 子句的 SELECT 陳述式的範例  
  
    ```  
    SELECT TOP 1 * FROM spfli INNER JOIN sflight ON spfli.mandt = sflight.mandt  
    ```  
  
-   使用 OPTION 子句的 SELECT 陳述式的範例  
  
    ```  
    SELECT top 50000 * from bseg option 'batchsize 20000'  
    ```  
