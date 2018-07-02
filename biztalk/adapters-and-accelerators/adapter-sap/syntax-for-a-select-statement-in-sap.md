---
title: 在 SAP 中的 SELECT 陳述式的語法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SELECT statement, syntax for
ms.assetid: 47120d74-bf41-4622-a6bc-7b8ddc959305
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92b3cb47df9b151de741b0e64f21041a60b9c90d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970711"
---
# <a name="syntax-for-a-select-statement-in-sap"></a>在 SAP 中的 SELECT 陳述式的語法
下列章節描述文法規格實作針對 SELECT 查詢[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。 請注意，在許多情況下，語法稍有不同的基底的 TRANSACT-SQL 語法。  
  
```  
SELECT {TOP <const> }[0,1] <select_list>  {INTO FILE [‘file_name’ | “file_name”]   
{DELIMITED}[0,1]}[0,1]  FROM table_name  {AS alias_name }[0,1]    
{INNER JOIN table_name {AS alias_name}[0,1] ON  <Join_Condition>}[0,1]  
{ WHERE <predicate> } [0,1] {;}[0,1]   
[OPTION 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'  
```  
  
 其中：  
  
- **<select_list>** = `[ {table_name.}[0,1]column_name { AS alias_name } [0,1] } [ 1, …n ]`  
  
- **<Join_Condition>** = `[Alias_name.|table_name.]column_name <expr> [Alias_name.|table_name.]column_name`  
  
- **\<predicate\>** = `[ predicate [AND|OR] predicate [between|not between] predicate |  NOT predicate |  ‘(‘ predicate ‘)’ | condition ]`  
  
  支援的條件和運算式如下：  
  
- **\<條件\>** = `[ expr | expr [NOT | ] BETWEEN const AND const | expr [NOT | ] LIKE const ]`  
  
- **\<expr\>** = `[ const | column_name [= | ! = | > | > = | ! > | < | < = | ! < ] const | column_name | - const  | const | column_name ]`  
  
  何處 **\<const\>** = `integer | real | string | ? | NULL | xml_element`。  
  
  **OPTION 關鍵字的值**  
  
  您可以指定為選項`OPTION '<option>'`，其中 `<option> = 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'`  
  
- **No_conversion**選項：  
  
  -   如果**no_conversion**選項使用，則資料表中的欄位會公開使用對等的.NET 型別。 SAP 資料類型的.NET 對等的相關資訊，請參閱[基本 SAP 資料型別](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)。  
  
  -   如果**no_conversion**未使用選項，而且如果欄位沒有轉換結束定義，則資料表中的這些欄位會公開使用對等的.NET 型別。 SAP 資料類型的.NET 對等的相關資訊，請參閱[基本 SAP 資料型別](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)。  
  
  -   當**no_conversion**選項未在使用中，如果欄位有轉換並結束定義，則資料表中的這些欄位會公開為.NET 字串。  
  
- 當設定為**batchsize\<大小\>**，SELECT 陳述式的執行會導致多個呼叫進行至 SAP 系統，並在每個呼叫中，只有\<大小\>的記錄數目擷取。 例如，如果您指定 ' batchsize 100'，SELECT 查詢會擷取 100 筆記錄只能在 SAP 系統的每一個呼叫中。 如果**batchsize\<大小\>** 未指定，10000 的預設值會假設批次大小。 請注意，您應該指定批次大小，根據 SAP 系統中的電腦和資料列數目的實體記憶體最佳值。 指定批次大小的最佳值可能會導致記憶體不足例外狀況。  
  
- 當設定為**disabledatavalidation**，則[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不會驗證 DATS、 TIMS 和 NUMC 資料行中存在的值，但改為將其公開成字串。  
  
   這是適用於 ADO.NET 用戶端會從 SAP 資料表在 DATS、 TIMS 和 NUMC 資料行中包含無效的資料擷取資料失敗的情況。 因為 SAP 允許無效的資料會出現在 DATS、 TIMS 和 NUMC 資料行，所以嘗試讀取資料的 ADO.NET 用戶端將無法剖析無效的資料，並將會擲回例外狀況。 如果**disabledatavalidation**上的 SELECT 查詢，設定選項[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不會剖析無效的資料，但它們擷取為字串。  
  
> [!IMPORTANT]
>  您必須永遠提供的值選項關鍵字在單引號中，例如，'*disabledatavalidation*'。  
  
 例如陳述式，請參閱 < [SELECT 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md)。  
  
## <a name="predicates-syntax"></a>述詞的語法  
 下列指定 SELECT 陳述式中使用述詞的文法：  
  
 `Predicate`：  
  
```  
Predicates [AND | OR] Predicates [between|not between] Predicates | [NOT] Predicates | '(' Predicates ')' | Condition  
```  
  
 `Condition`：  
  
```  
Expr | LExpr [NOT] BETWEEN RExpr AND RExpr | LExpr [NOT] LIKE Const  
```  
  
 `Expr`：  
  
```  
LExpr [=|!=|>|>=|!>|<|<=|!<] RExpr>  
```  
  
 `LExpr`：  
  
```  
ColumnName  
```  
  
 `RExpr`：  
  
```  
Const | PlaceHolder  
```  
  
 `ColumnName`：  
  
```  
Column | TableName.Column | '['Column']'  
```  
  
 `Tablename`：  
  
```  
Table | '['Table']'  
```  
  
## <a name="considerations-when-calling-a-select-statement"></a>呼叫 SELECT 陳述式時的考量  
 此區段會列出使用 SELECT 陳述式時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
- 當參數或查詢中指定日期時間值，提供的值做為字串。 提供 SAP 日期時間格式的日期時間字串。  
  
  - `SAP date format`: YYYYMMDD  
  
     例如，日期 2004 年 11 月 10 SAP 查詢中是表示 '20041110'。  
  
     2004 年 11 月 10 SAPParameter p1 中為日期字串 p1。值 = '20041110'。  
  
  - `SAP time format`: HHMMSS  
  
     例如，時間 10:34:32 SAP 查詢中是表示 '103432'。  
  
     時間 10:34:32 SAPParameter p2 中是字串 p2。值 = '103432'。  
  
    SELECT 陳述式，如[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會傳回`DATE`欄位值為.NET`System.DateTime`物件，並傳回`TIME`欄位值為`System.TimeSpan`物件。 如果將 sap 值`DATE`物件是否小於最小的可允許 SQL Server 值 (`1/1/1753`)，則[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會傳回此最小的值， `1/1/1753`。  
  
- 中的 TOP 子句的 SELECT 查詢，當使用特殊字元"#"、"^"，"&"和"%"之前或之後的整數，特殊字元會被忽略，雖然沒有任何錯誤訊息，就會引發。 例如，下列會忽略 TOP 子句的 SELECT 查詢中：  
  
   \#5，5 ^，%5%或和 5  
  
   不過，使用整數，與 5 之間的這些字元 $5，並會擲回錯誤。  
  
- 因為所有大寫字元，會傳回資料表的結構描述中傳回的資料行名稱。 例如，查詢結果集的欄位`Last Name`傳回的資料行標題`LAST NAME`。 若要避免唯一性建議使用全部大寫的 SELECT 陳述式中的衝突。  
  
- LIKE 子句的 SELECT 查詢，在只有百分比符號、"%"（適用於任何零或多個字元字串） 和底線 **"_"** （適用於任何單一字元），是允許的特殊字元。 所有其他特殊字元會被視為字串值，而且會忽略。  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用 Z_EXTRACT_DATA_OO RFC，SAP 系統上執行 SELECT 查詢。 RFC 支援滿足下列條件的資料表中讀取資料：  
  
  - 資料表的 TabClass 是 TRANSP、 叢集或集區。  
  
  - TabClass 檢視而 ViewClass D 或 p。  
  
    請確定 SELECT 陳述式會從滿足這些條件的資料表讀取資料。  
  
- 可能需要超過 255 個字元，例如字串、 RAWSTRING、 LRAW、 VARC 和 LCHAR 的資料類型的值不能在選取的查詢。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會使用隨附的自訂 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，Z_EXTRACT_DATA_OO，SAP 系統上執行 SELECT 查詢。 這個自訂 RFC 不支援任何可能需要超過 255 個字元的資料類型。  
  
- 支援在 SELECT 陳述式中的欄位或資料行的最大數目是 1000年。  
  
- 支援在 WHERE 子句中的述詞的最大數目為 100。  
  
- 不支援選取的相同欄位的設定，多次相同的 SELECT 陳述式中。 自訂 RFC (Z_EXTRACT_DATA_OO) 使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]之前執行的陳述式中移除重複的欄位。 例如，此陳述式：  
  
   `SELECT BUKRS, BUKRS, BUKRS from T001`  
  
   如同寫此陳述式執行：  
  
   `SELECT BUKRS from T001`  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] SELECT 陳述式中不支援重複的別名名稱。 因此，下列 SELECT 陳述式會擲回錯誤：  
  
  ```  
  SELECT KUNNR AS [MYKNA1], JMJAH AS MYKNA1 from KNA1 where KUNNR LIKE 'T-S62A08' AND JMJAH=1995  
  ```  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] 不支援重複的資料行名稱的 SELECT 陳述式。 因此，下列 SELECT 陳述式會擲回錯誤：  
  
  ```  
  SELECT KUNNR AS [MYKNA1], KUNNR AS MYKNA2 from KNA1 where MYKNA2='T-S62A08'  
  ```  
  
- SAP 不會儲存在資料表中的 NULL 值。 如此一來，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援 SELECT 陳述式中的"IS NULL"的值。 因此，下列 SELECT 陳述式會擲回錯誤：  
  
  ```  
  SELECT NAME1, PSTLZ  from KNA1 where CITY IS NULL AND NAME1 LIKE '%MODE%'  
  ```  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] 不支援 ORDER BY 子句的 SELECT 陳述式。 因此，下列 SELECT 陳述式會擲回錯誤：  
  
  ```  
  SELECT NAME1  AS [MYNAME],  LAND1, KUNNR  from KNA1 where NAME1 LIKE '%MODE%'  ORDER BY NAME1  ASC  
  ```  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] 不支援指定星號 （*） 來選取 SAP 資料表中的所有欄位。 因此，下列 SELECT 陳述式會擲回錯誤：  
  
  ```  
  SELECT spfli.* from spfli inner join sflight on spfli.carrid = sflight.carrid  
  ```  
  
   若要選取的所有欄位，您必須個別指定的欄位名稱。  
  
- SELECT 陳述式的一部分，您可以指定 SELECT 陳述式的輸出會寫入至其中的檔案。 不過，如果輸出檔位於網路共用，請確定 SAP 服務執行的 SAP 服務帳戶具有網路共用的寫入權限。 例如：  
  
  ```  
  SELECT * into file '\\share\output.txt' from spfli inner join sflight on spfli.carrid = sflight.carrid  
  ```  
  
   在上述範例中，SAP 服務帳戶必須具有寫入權限的網路共用名稱"share"。  
  
- SELECT 陳述式，使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]SELECT 查詢中支援的引數值的參數名稱。 不過，請確定您遵循這些規則對於參數名稱：  
  
  -   在選取查詢中，「\@"符號必須在參數名稱前面。  
  
  -   「\@"符號後面必須接著字母字元 （A-Z 或 a-z）。  
  
  -   參數名稱可以包含英數字元 (A-Z、 a-z 或 0-9) 和特殊字元。 可以包含在參數名稱的唯一特殊字元是底線"_"及"#"的雜湊。  
  
- 當您在檢視上執行 SELECT 查詢時，請確定基底資料表的所有主索引鍵資料行也會出現在檢視中。 此外，做法是，您必須將標記資料行在檢視中的主索引鍵資料行也。  
  
   如果在檢視中沒有主索引鍵資料行，在檢視上的 SELECT 查詢將會導致例外狀況。  
  
- 當您選取欄位的型別 LRAW 資料表上執行 SELECT 查詢時，請確定您選取的相對應的 PREC 欄位。 此外，PREC 欄位必須立即 LRAW 欄位之前 SELECT 子句中出現。  
  
   資料表中的每個 LRAW 欄位有相對應的 PREC 欄位 LRAW 欄位中儲存資料的長度。 指定只 LRAW 欄位 PREC 欄位沒有 SELECT 子句中，可能會導致不正確所擷取的資料。  
  
- 在 SAP 系統中，字元的比較會區分大小寫。 因此，下列兩個查詢可能傳回不同的結果。  
  
  ```  
  SELECT * FROM KNA1 WHERE LAND1 LIKE 'D%'  
  ```  
  
   And  
  
  ```  
  SELECT * FROM KNA1 WHERE LAND1 LIKE 'd%'  
  ```  
  
   請確定您使用正確的情況下，當框架的 select 查詢。 此外，在 SAP 系統中，並非所有資料行可包含大寫或小寫字元。 您可以使用 SAP GUI 來找出資料表中的資料行是否會儲存大寫或小寫字元。 如需有關使用 SAP GUI 的指示，請參閱[決定是否資料行存放小寫或大寫值](../../adapters-and-accelerators/adapter-sap/determining-whether-a-column-stores-lowercase-or-uppercase-values.md)。  
  
- WHERE 條件僅支援與某個資料值的欄位值的比較並*不*與其他資料表欄位值。 因為[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援只有一個資料表 SELECT 查詢，在 聯結條件中的資料表欄位查詢應該使用的聯結條件，以支援相同。  
  
- 聯結條件必須包含資料表名稱。  
  
   以下是正確的 SELECT 陳述式  
  
  ```  
  select A.x, B.y from A inner join B on A.m = B.n  
  ```  
  
   以下是不正確的 SELECT 陳述式  
  
  ```  
  select A.x, B.y from A inner join B on m = n  
  ```  
  
- 聯結條件，聯結條件中的左方的資料表應該位於左側的條件，並聯結條件的右方資料表應指定聯結條件右邊。  
  
   以下是正確的方式來指定聯結條件：  
  
  ```  
  select A.x, B.y from A inner join B on A.m = B.n  
  ```  
  
   以下是不正確的方式來指定聯結條件：  
  
  ```  
  select A.x, B.y from A inner join B on B.n = A.m  
  ```  
  
- SELECT 陳述式只可包含在 JOIN 子句中的 「 等於 」 條件。 例如：  
  
  ```  
  select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
  ```  
  
- SELECT 陳述式不會從 SAP 系統擷取資料行型別為 STRING。  
  
- SELECT 陳述式必須包含單一聯結。 例如：  
  
  ```  
  select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
  ```  
  
## <a name="see-also"></a>另請參閱  
 [關於 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)
