---
title: "SAP 中 EXECQUERY 陳述式語法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bd7fbb-64f2-4327-a8ae-ccb574e56150
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f1eb41d07ef6a6ac3577bf0ef6d3f5bffb874f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="syntax-for-an-execquery-statement-in-sap"></a>SAP 中 EXECQUERY 陳述式語法
您可以使用 SAP GUI 來建立查詢，以圖形方式來選取您想要查詢之資料行和排序的次序，您想要包含在結果集，等資料表。[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可讓使用者從 ADO.NET 應用程式中執行這類的查詢，藉由提供使用者可用來執行查詢，在 SAP 系統中定義的 EXECQUERY 作業。  
  
 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用自訂的 RFC Z_EXECUTE_SAP_QUERY SAP 系統中執行的預先定義的查詢。 自訂 RFC 依次執行 RSAQ_REMOTE_QUERY_CALL，這是 SAP 系統中定義的 RFC 的標準。 因此，您可以使用 EXECQUERY 作業之前，您必須安裝自訂 RFC SAP 系統，您會執行針對查詢中。 如需有關如何安裝自訂 RFC 的指示，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。  
  
 本主題提供的語法 EXECQUERY 作業，以及其他有用資訊 EXECQUERY 與作業有關的資訊。  
  
## <a name="syntax-for-an-execquery-statement"></a>EXECQUERY 陳述式語法  
 下節描述的文法規格，使用針對 EXECQUERY 作業[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
```  
EXECQUERY <QueryName> @USERGROUP='usergroup' [, @WORKSPACE='X'] [, @VARIANT='variant']   
[, @P1='\<value 1>’] [, @P2='\<value 2>'] ... [, @Pn = '<value n>'] [, @P1!='\<value 3>'] [, @P1 > '\<value 4>'] [, @P1 <= '\<value 2>']   
[, NOT @P1 = '\<value 2>'] [, NOT @P1 != '\<value 2>'] [, NOT @P1 > '\<value 2>']   
[, @P1 BETWEEN '\<value 1>' AND '\<value 2>'] [, NOT @P1 BETWEEN '\<value 1>' AND '<value2>’]  
[OPTION 'USEORIGINALCOLUMNNAMES']  
  
```  
  
 其中：  
  
-   **\<QueryName >** SAP 系統中所定義之查詢的名稱。  
  
-   **USERGROUP**指的是用來定義查詢的使用者群組。 這是強制參數。  
  
-   **工作區**指的是用來定義查詢的工作區。 SAP 中有兩個工作區，Standard 和全域。 提供的空白處來指定 [標準] 工作區。 提供`X`指定 [全域] 工作區。 預設值是空的空間。  
  
-   **VARIANT**指的是一組儲存執行 SAP 查詢時，您可以指定的選取準則。 例如，您可以使用變數來指定查詢的預設值。  
  
-   **@Pn**n 是指<sup>th</sup> SAP 查詢定義中的選取項目欄位。  
  
-   **USEORIGINALCOLUMNNAMES**指定提供者是否使用原始的資料行名稱，在資料集中，它們在 SAP 系統中存在。 根據預設，提供者會使用 SAP 查詢中所定義的易記名稱。 不過，如果查詢中的易記名稱不是唯一的 ADO.NET 用戶端將會擲回錯誤時從資料集讀取資料。 在這種情況下，您必須指定 USEORIGINALCOLUMNNAMES 選項，指出提供者會使用原始的資料行名稱，資料集內。  
  
    > [!IMPORTANT]
    >  您必須一律提供值選項關鍵字在單引號中，例如，'*USEORIGINALCOLUMNNAMES*'。  
  
> [!NOTE]
>  SAP 查詢的參數如何轉譯成 EXECQUERY 語法的相關資訊，請參閱[轉譯 SAP 查詢參數為 EXECQUERY 命令](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md)。  
  
### <a name="framing-an-execquery-syntax"></a>框架 EXECQUERY 語法  
 框架 EXECQUERY 作業，以執行 SAP 查詢的語法，取決於查詢中的 SAP 系統，包括在 SAP 中定義的每個參數值的定義方式。 如需如何框架 EXECQUERY 執行 SAP 查詢的語法資訊，請參閱[轉譯 SAP 查詢參數為 EXECQUERY 命令](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md)。  
  
### <a name="additional-considerations-while-using-the-execquery-operation"></a>其他考量而使用 EXECQUERY 作業  
 此區段會列出使用 EXECQUERY 陳述式使用時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
-   USERGROUP、 工作區中，以及變數所指定的值做為傳遞的標準 SAP RFC RSAQ_REMOTE_QUERY_CALL 是。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不會驗證指定這些參數的值。  
  
-   EXECQUERY 作業所傳回的所有值都都是字串型別。  
  
-   查詢名稱、 使用者群組、 工作區中，而且變異的關鍵字不區分大小寫。 不過，參數名稱中都必須上方 caseP 例如@P1，@P2等等。例如：  
  
    ```  
    EXECQUERY xyz USERGROUP=’mygrp’, NOT @P1= 'somevalue'  
    ```  
  
     等同於  
  
    ```  
    EXECQUERY xyz uSERgROUP=’mygrp’, NOT @P1= 'somevalue'  
    ```  
  
-   EXECQUERY 所支援的運算子為 >， \<，> =、 < =、 ！ =、 NOT、 BETWEEN 和。  
  
-   EXECQUERY 作業不支援萬用字元。 例如，下列陳述式的預期的輸出如下：  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
     不過，相同的查詢執行時未使用萬用字元會顯示錯誤。 請注意，萬用字元來使用 **@P2** 。  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = '*&*'  
    ```  
  
     在此範例中，您可能會收到錯誤，指出已找到任何資料。 這是因為查詢會搜尋**'\*&\*'**做為字串，並不考慮星號 （*） 做為萬用字元。  
  
-   您永遠必須指定日期值格式為 YYYYMMDD。  
  
-   如果您執行的具有 variant SAP 系統中定義的查詢，您可以指定之變數的名稱做為命令的一部分。 例如：  
  
    ```  
    EXECQUERY myquery @usergroup='mygroup',@variant = 'variant1'  
    ```  
  
    > [!NOTE]
    >  您不需要指定變數的名稱，如果預設 variant SAP 系統中定義的查詢。  
  
## <a name="see-also"></a>另請參閱  
 [使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)