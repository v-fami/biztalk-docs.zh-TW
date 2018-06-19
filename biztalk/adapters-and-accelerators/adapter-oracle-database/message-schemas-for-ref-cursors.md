---
title: REF CURSOR 的訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- REF CURSORS, message schemas for
- IN REF CURSOR
- OUT REF CURSOR
- IN OUT REF CURSOR
ms.assetid: b62e7a9f-278c-41b3-90f0-2f621a34327b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bddfde0b0897c7d8c21a20126d2fa1d2f0f8c78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214758"
---
# <a name="message-schemas-for-ref-cursors"></a>REF CURSOR 的訊息結構描述
REF CURSOR 是 Oracle 的 PL/SQL 資料類型，表示結果集的 Oracle 資料庫中的指標。 REF CURSOR 類型啟用輸入和輸出資料的資料流，適合用來傳輸大量資料的 PL/SQL 程式碼區塊。 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]提供傳遞強型別和弱型別 REF CURSOR 參數的 PL/SQL 程序和函式中，逾時及在 OUT 參數的支援。  
  
 在 Oracle 資料庫中，REF CURSOR 類型可以是強型別或弱型別：  
  
-   RETURN 子句中宣告強類型的 REF CURSOR `TYPE StrongCurType IS REF CURSOR RETURN emp%ROWTYPE;`。 強型別 REF 資料指標變數只能表示結果集，其中包含符合的型別與宣告其 REF 資料指標類型的資料。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]傳回強型別結果集是強型別 REF 資料指標。  
  
-   弱型別 REF 資料指標宣告時沒有做為中的 RETURN 子句`TYPE WeakCurType IS REF CURSOR;`。 Oracle 也提供一種特殊的 REF CURSOR 類型呼叫可以用來宣告弱型別 REF 資料指標變數的 SYS_REFCURSOR。 弱型別 REF 資料指標變數可以表示結果集包含任何種類的資料列資料。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]弱式類型的 REF CURSOR 傳回弱式類型的結果集的一般記錄。  
  
## <a name="in-ref-cursor-parameters"></a>中的 REF CURSOR 參數  
 沒有任何 ODP.NET API，來建立 REF CURSOR 在 Oracle 伺服器上，所以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]無法提供建立和維護 REF 資料指標變數的用戶端程式的功能。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ，不過，讓用戶端中 REF CURSOR 參數傳遞給函式或預存程序，藉由指定傳回 REF CURSOR 的 PL/SQL 程式碼區塊。 配接器會使用此程式碼以建立並開啟 Oracle 伺服器上的 REF CURSOR 變數然後，它會呼叫函式或預存程序中使用這個變數做為 IN 參數。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]以包含 PL/SQL 程式碼區塊的字串表示中 REF CURSOR 參數。 在這個區塊中使用問號 （？） 指定 REF CURSOR 的位置。 PL/SQL 程式碼區塊可以包含開啟 FOR 陳述式，其中包含 SQL 查詢。或者也可以包含函數或程序呼叫中，開啟的 REF CURSOR 傳回 OUT 參數中。  
  
 以下顯示如何藉由呼叫預存程序或函式來開啟 REF CURSOR 指定中 REF CURSOR。  
  
```  
<[IN_REF_CURSOR_PARAM_NAME]>begin [SP_NAME]([SP_PARAMS...], ?, [SP_PARAMS...]); end;</[IN_REF_CURSOR_PARAM_NAME]>  
  
Example:  
<EMP_RC>begin GETEMP(1, ?); end; </EMP_RC>  
```  
  
 以下顯示如何使用選取的查詢開啟 REF CURSOR 指定中 REF CURSOR。  
  
```  
<IN_REF_CURSOR_PARAM_NAME>begin open ? for select [FIELD_NAMES] from [TABLE_NAME]; end;</IN_REF_CURSOR_PARAM_NAME>  
  
Example:  
<EMP_RC>begin open ? for select * from EMP; end;</EMP_RC>  
```  
  
## <a name="out-ref-cursor-parameters"></a>OUT REF CURSOR 參數  
 OUT REF CURSOR 參數會傳回做為強型別或弱式類型的結果集。 傳回的結果集的類型取決於是否 REF CURSOR 參數宣告強型別或弱式類型的 REF CURSOR，在預存程序或函式定義為 Oracle 伺服器上。 強類型傳回結果集是強型別 REF CURSOR 參數的和弱型別會傳回結果集的弱式類型的 REF CURSOR 參數 （例如，參數宣告的 SYS_REFCURSOR）。  
  
 下圖顯示的強型別出 REF CURSOR 參數的 XML。  
  
```  
<[PARAM_NAME]>  
 <[PARAM_NAME]RECORD>  
  <[COL1_NAME]>value1</[COL1_NAME]>  
  <[COL2_NAME]>value2</[COL2_NAME]>  
  ...  
 </[PARAM_NAME]RECORD>  
</[PARAM_NAME]>  
  
[PARAM_NAME] = OUT REF CURSOR parameter name; for example, EMP_REFCURSOR  
[COL_NAME] = Name of a column in the REF CURSOR type; for example, Name.  
```  
  
 下圖顯示弱型別出 REF CURSOR 參數的 XML。  
  
```  
<[PARAM_NAME]>  
 <GenRecordRow xmlns="oracledb">  
  <GenRecordColumn>  
   <ColumnName>COL_NAME</ColumnName>  
   <ColumnValue>COL_VALUE</ColumnValue>  
   <ColumnType>COL_TYPE</ColumnType>  
  </GenRecordColumn>  
  …  
 </GenRecordRow>  
 …  
</[PARAM_NAME]>  
  
[COL_NAME] = Name of column; for example, Name  
[COL_VALUE] = Column value; for example, Scott  
[COL_TYPE] = Column data type; for example, System.String  
```  
  
## <a name="in-out-ref-cursor-parameters"></a>IN，OUT REF CURSOR 參數  
 因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]模型中 REF CURSOR 參數做為字串和複雜類型的 REF CURSOR OUT 參數，它不能支援單一類型 IN OUT REF CURSOR 參數。 基於這個理由，它會將 IN OUT REF CURSOR 參數視為兩個不同的參數： 在要求訊息和回應訊息中的 OUT 參數，為 IN 參數。  
  
 若要避免名稱衝突，在服務模型程式設計中，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]將字串"_IN"附加至 IN 參數，要求訊息中，以便針對給定的參數，名為 [PARAM_NAME]，建立兩個參數：  
  
-   [PARAM_NAME] _IN 是中 REF CURSOR 參數的預存程序或函式要求訊息中。 它包含的 PL/SQL 陳述式 （select 查詢或預存程序或函式呼叫） 傳回 REF CURSOR。  
  
-   [PARAM_NAME] 是出 REF CURSOR 參數的預存程序或函式的回應訊息中。 它包含 OUT REF CURSOR 做為強型別或弱式類型的結果集。  
  
> [!IMPORTANT]
>  配接器不支援的程序或函數，其中包含名為 [PARAM_NAME] _IN 和 IN OUT REF CURSOR 參數名為 [PARAM_NAME] 為 IN 參數。 這是因為配接器必須要有一個名為 [PARAM_NAME] _IN 代表 REF CURSOR 參數的輸入參數，而且您無法在要求訊息中指定這兩個參數。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)