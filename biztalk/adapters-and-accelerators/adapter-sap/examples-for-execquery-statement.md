---
title: "EXECQUERY 陳述式的範例 mySAP 配接器在 BizTalk 中 |Microsoft 文件"
description: "EXECQUERY 範例和範例使用 mySAP 配接器在 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4139af16-7c38-4ea2-b3e5-5acf8fc1f3c4
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77c5d5877ff502b8fdca620d8b92e4427d3b73b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="examples-for-execquery-statement"></a>EXECQUERY 陳述式的範例
本主題提供範例 EXECQUERY 陳述式。  


## <a name="sample-statements"></a>範例陳述式
-   要執行的查詢，會採用兩個參數 P1 和 P2 命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
-   若要執行可採用參數 P1 的值範圍的查詢命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   命令來執行查詢，會使用在特定範圍的參數 P1 的值。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   要執行的查詢，可以採用參數 P1 的兩個值的其中一個命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262', @P1 = '0000003263'  
    ```  
  
-   要執行的查詢，無法取得參數的特定值的命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 = '0000003262', NOT @P2 = '0000003263'  
    ```  
  
     在此範例中，P1 可以有 '0000003262' 以外的任何值。 同樣地，P2 可以有 '0000003263' 以外的任何值。  
  
-   要執行具有變體在 SAP 系統中定義的查詢命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant = ‘variant1’  
    ```  
  
     變數是指一組儲存執行 SAP 查詢時，您可以指定的選取準則。 例如，您可以使用變數來指定查詢的預設值。 對於已定義的所有參數的變異的查詢，您不需要命令文字中指定的參數。  
  
-   要執行的查詢，不需要參數的命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'some_dummy_value'  
    ```  
  
     不接受參數的查詢，您必須指定參數使用空值。  
  
-   執行查詢，其中包含參數，必須是日期值的命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '20080606'  
    ```  
  
     對於使用參數必須是日期值的查詢，您必須指定日期為 YYYYMMDD。  
  
-   藉由指定參數的 null 值上執行查詢命令。  
  
     針對這類的查詢，您無法指定為查詢：  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'null'  
    ```  
  
     相反地，如果您不想指定的值，您不應該指定 P1 完全。  
  
-   要執行包含參數值必須是大於特定數目的查詢命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 > '0000003262'  
    ```  
  
-   命令執行查詢，其中包含應為值參數小於特定數目。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 < '0000003262'  
    ```  
  
-   執行查詢，其中包含參數，應為的值大於或等於特定數目的命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 >= '0000003262'  
    ```  
  
-   執行查詢，其中包含參數，應為的值小於或等於特定數目的命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 <= '0000003262'  
    ```  
  
-   執行查詢，其中包含參數，應為的值不等於特定數目的命令。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 != '0000003262'  
    ```  
  