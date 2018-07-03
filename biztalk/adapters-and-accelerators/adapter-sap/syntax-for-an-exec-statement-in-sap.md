---
title: 在 SAP 中 EXEC 陳述式的語法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EXEC statement, syntax for
ms.assetid: 406b1100-39a0-4321-89c9-ec1b8a3cfdc6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7da9395ec244f6877dc7902e0feae22f6d81b391
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020073"
---
# <a name="syntax-for-an-exec-statement-in-sap"></a>在 SAP 中 EXEC 陳述式的語法
下列章節會說明實作 EXEC 陳述式的文法規格[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。 請注意，在許多情況下，語法的 TRANSACT-SQL 語法稍有不同。  
  
```  
EXEC rfc_name {<argument_element>} [ , …n ]  {;}[0,1] [ OPTION <disabledatavalidation>, <firstresultset> ]  
```  
  
 其中：  
  
- **rfc_name**指定執行的函式呼叫的名稱。  
  
- **< argument_element >** :: = @param_name = [0，1] \<const\> {[輸入&#124;輸出]} [0，1]  
  
  -   **param_name**指定函式的介面中定義的參數名稱。  
  
  -   **\<const\>**  :: = 整數&#124;real&#124;字串&#124;？ &#124;NULL &#124; xml_element  
  
- **選項**提供選項，在您要將資料呈現的方式。 可用的選項如下：  
  
  - **disabledatavalidation**選項組**EnableSafeTyping**繫結屬性，在基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 啟用 「 安全輸入時 DATS、 TIMS 和 NUMC 資料型別會表示為字串。 如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
  - **firstresultset**指定所傳回的第一個結果集[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。 在 ADO 提供者來源上執行的任何陳述式時，只有第一個傳回的結果集使用。 RFC EXEC 的情況下，通常是多個資料表參數會傳回但只有第一個結果集可供用戶端程式，可能無法使用的程式。 藉由指定"firstresultset 」 關鍵字的 OPTION 子句的一部分，用戶端可以指定他們想要傳回的提供者的第一個資料表參數。 例如：  
  
    ```  
    EXEC Z_TEST_ALL_TYPES @P_IN='TestInput' OPTION 'disabledatavalidation', firstresultset TAB_ALLTYPES'  
    ```  
  
     在此範例中，在 EXEC 陳述式會指定傳回的第一個資料表參數應該 TAB_ALLTYPES。  
  
  > [!IMPORTANT]
  >  您必須永遠提供的值選項關鍵字在單引號中，例如，'*disabledatavalidation*'。  
  
  在上述語法中，xml_element 可用來提供輸入的複雜型別。 Xml 項目結構會有不同結構和資料表。 結構 xml_element 如下所示：  
  
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
  
 同樣地，針對資料表類型的 XML 項目如下所示：  
  
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
  
 例如陳述式，請參閱 < [EXEC 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md)。  
  
## <a name="handling-named-parameters"></a>具名參數的處理  
 指定的具名參數執行查詢的指導方針如下：  
  
- 您必須指定參數，透過命名 (例如@param_name= value)。  
  
  > [!NOTE]
  >  不支援未命名的參數  
  
- 使用預設值來定義參數時，您可以執行程序，而不指定參數。  
  
- EXEC 查詢不支援使用參數具有下列屬性：  
  
  - 巢狀的結構 （包含結構做為其欄位的結構）。  
  
  - 巢狀的資料表。  
  
  - 包含結構的資料表。  
  
  - 包含資料表的結構。  
  
  - 結構或具有具有複合字串類型的欄位，例如資料表`SSTRING`或`RAWSTRING`。  
  
    執行 RFC 時下, 表將列出 RFC 參數類型與參數方向之間的邏輯對應。  
  
  |RFC 參數類型|查詢關鍵字|參數方向|  
  |--------------------|-------------------|-------------------------|  
  |匯入參數|執行任何動作|Paramdirection.Input|  
  |匯出參數|輸出|Paramdirection.Output|  
  |資料表參數|輸出/無|InputOutput|  
  
  以下是一般的指導方針處理參數：  
  
- 您可以指定參數值，為常數，或是在查詢中使用的預留位置。  
  
- 當在查詢中使用的預留位置，您必須建立`SAPParameter`物件，並將它新增至對應的命令物件。 然後將預留位置名稱傳遞給建構函式方向和值取決於內容。  
  
  -   針對`Input`參數，未指定查詢中的參數方向的關鍵字。 `value`必須設定參數物件的欄位，或提供者將會擲回例外狀況。 您必須明確設定`direction`欄位的參數物件，因為提供者預設為`Input`。  
  
  -   其他參數，使用表單`@paramname=@placeholder`並指定`Output`查詢中明確的關鍵字。 然後您必須加入`SAPParameter`相對應的預留位置，明確地將參數方向設定為`ParamDirection.Output`或`ParamDirection.InputOutput`，取決於參數類型。  
  
- 參數名稱和預留位置名稱不區分大小寫。  
  
- 在查詢中不重複參數名稱，除非它們有不同的方向。  
  
- 預留位置名稱不能在查詢中重複。  
  
## <a name="considerations-when-calling-an-exec-statement"></a>呼叫 EXEC 陳述式時的考量  
 此區段會列出使用 EXEC 陳述式時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。  
  
- EXEC 陳述式[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會傳回`TIMS`欄位值為.NET`System.DateTime`物件。  
  
  > [!NOTE]
  >  SELECT 陳述式，如[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會傳回`TIMS`欄位值為.NET`System.TimeSpan`物件。 如需 SELECT 陳述式的詳細資訊，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關於 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)