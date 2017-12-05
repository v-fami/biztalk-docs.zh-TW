---
title: "SAP 的 EXEC 陳述式的語法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: EXEC statement, syntax for
ms.assetid: 406b1100-39a0-4321-89c9-ec1b8a3cfdc6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 362aa1f81158c9d9f1135c9bff25c64d7d745953
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="syntax-for-an-exec-statement-in-sap"></a>SAP 的 EXEC 陳述式的語法
下節說明實作 EXEC 陳述式的文法規格[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。 請注意，在數個情況下，語法與 TRANSACT-SQL 語法稍有不同。  
  
```  
EXEC rfc_name {<argument_element>} [ , …n ]  {;}[0,1] [ OPTION <disabledatavalidation>, <firstresultset> ]  
```  
  
 其中：  
  
-   **rfc_name**指定執行的函式呼叫的名稱。  
  
-   **< argument_element >** :: = @param_name = [0，1] \<const\> {[輸入 &#124;輸出]} [0，1]  
  
    -   **param_name**指定函式的介面中定義的參數名稱。  
  
    -   **\<const\>**  :: = 整數 &#124; 真實 &#124; 字串 &#124; 嗎？ &#124;NULL &#124;xml_element  
  
-   **選項**提供您想要如何呈現資料的選項。 可用的選項如下：  
  
    -   **disabledatavalidation**選項集**EnableSafeTyping**繫結屬性在基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 當已啟用 「 安全輸入 DATS、 TIMS 和 NUMC 資料型別會表示為字串。 如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
    -   **firstresultset**指定所傳回的第一個結果集[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。 在 ADO 提供者來源上執行的任何陳述式時，只有第一個傳回的結果集使用。 RFC EXEC 案例中，通常有多個資料表參數會傳回但只有第一個結果集供用戶端程式，這可能不是使用。 藉由指定"firstresultset 「 關鍵字做為 OPTION 子句的一部分，用戶端可以指定他們想要傳回的提供者的第一個資料表參數。 例如：  
  
        ```  
        EXEC Z_TEST_ALL_TYPES @P_IN='TestInput' OPTION 'disabledatavalidation', firstresultset TAB_ALLTYPES'  
        ```  
  
         在此範例中，在 EXEC 陳述式會指定傳回的第一個資料表參數應該 TAB_ALLTYPES。  
  
    > [!IMPORTANT]
    >  您必須一律提供的值選項關鍵字在單引號中，例如，'*disabledatavalidation*'。  
  
 在上述語法中，xml_element 可用來提供輸入的複雜型別。 Xml 項目結構會結構與資料表的不同。 結構 xml_element 如下所示：  
  
```  
<PARAM_NAME>  
    <FIELDNAME_1 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_1>  
    <FIELDNAME_2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_2>  
    ...  
    ...  
</ PARAM_NAME>  
```  
  
 資料表 xml_element 如下所示：  
  
```  
<PARAM_NAME>  
    <STRUCT_NAME  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
        <FIELDNAME_1>value</FIELDNAME_1>  
    <STRUCT_NAME/>  
    <STRUCT_NAME  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
        <FIELDNAME_1>value</FIELDNAME_1>  
    <STRUCT_NAME/>  
    ...  
    ...  
</ PARAM_NAME>  
```  
  
 例如，結構類型的 XML 項目如下所示：  
  
```  
<INOUT_STRUCT>  
       <ACCPFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006</ACCPFIELD>  
       <CHARFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">John</CHARFIELD>                 
</INOUT_STRUCT>  
```  
  
 同樣地，資料表類型的 XML 項目如下所示：  
  
```  
<TAB_ALLTYPES>   
<ZZSTRUCTALLTYPES_RFC xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
       <ACCPFIELD>2006</ACCPFIELD>  
       <CHARFIELD>John</CHARFIELD>                          
</ZZSTRUCTALLTYPES_RFC>  
<ZZSTRUCTALLTYPES_RFC xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
       <ACCPFIELD>2007</ACCPFIELD>  
       <CHARFIELD>James</CHARFIELD>                          
</ZZSTRUCTALLTYPES_RFC>  
</TAB_ALLTYPES>  
```  
  
 如需範例陳述式，請參閱[EXEC 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md)。  
  
## <a name="handling-named-parameters"></a>處理具名參數  
 指定具名參數在 EXEC 查詢中的指導方針如下：  
  
-   您必須指定參數加以命名 (例如， @param_name= 值)。  
  
    > [!NOTE]
    >  不支援未命名的參數  
  
-   使用預設值來定義參數時，您可以執行程序，但未指定參數。  
  
-   EXEC 查詢不支援使用參數具有下列屬性：  
  
    -   巢狀的結構 （包含結構做為其欄位的結構）。  
  
    -   巢狀的資料表。  
  
    -   包含結構的資料表。  
  
    -   包含資料表的結構。  
  
    -   結構或資料表包含複合字串類型的欄位，例如`SSTRING`或`RAWSTRING`。  
  
     執行 RFC 時下, 表列出之間 RFC 參數型別和參數方向的邏輯對應。  
  
    |RFC 參數類型|查詢關鍵字|參數方向|  
    |--------------------|-------------------|-------------------------|  
    |匯入參數|執行任何動作|Paramdirection.Input|  
    |匯出參數|輸出|Paramdirection.Output|  
    |資料表參數|輸出/Nothing|輸入輸出|  
  
 以下是處理參數的一般指導方針：  
  
-   您可以指定參數值為常數或使用查詢中的預留位置。  
  
-   當在查詢中使用的預留位置，您必須建立`SAPParameter`物件，並將它加入至對應的命令物件。 然後將預留位置名稱傳遞給建構函式。方向和值取決於內容。  
  
    -   如`Input`參數，未指定在查詢中的參數方向的關鍵字。 `value`必須設定參數物件的欄位，或提供者將會擲回例外狀況。 您必須明確地設定`direction`欄位的參數物件，因為提供者預設為`Input`。  
  
    -   其他參數，使用表單`@paramname=@placeholder`並指定`Output`在查詢中明確的關鍵字。 然後您必須加入`SAPParameter`對應於預留位置，而且明確設定的參數方向為`ParamDirection.Output`或`ParamDirection.InputOutput`，視使用的參數類型。  
  
-   參數名稱和預留位置名稱不區分大小寫。  
  
-   在查詢中不重複的參數名稱，除非他們擁有不同的方向。  
  
-   預留位置名稱不能在查詢中重複。  
  
## <a name="considerations-when-calling-an-exec-statement"></a>呼叫 EXEC 陳述式時的考量  
 此區段會列出使用 EXEC 陳述式使用時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
-   EXEC 陳述式[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]傳回`TIMS`欄位值為.NET`System.DateTime`物件。  
  
    > [!NOTE]
    >  SELECT 陳述式，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]傳回`TIMS`欄位值為.NET`System.TimeSpan`物件。 如需 SELECT 陳述式的詳細資訊，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。  
  
## <a name="see-also"></a>請參閱  
 [關於 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)