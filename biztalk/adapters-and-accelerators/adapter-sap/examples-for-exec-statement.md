---
title: EXEC 陳述式 mySAP 配接器在 BizTalk 中的範例 |Microsoft Docs
description: EXEC 範例和範例使用 mySAP 配接器在 「 BizTalk 配接器組件 」 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad2691f4-34bb-423c-9b3e-4abe2d55ddac
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59bdabcba48d00bdf1d6c884ae1f2b469d858626
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992591"
---
# <a name="examples-for-exec-statement"></a>EXEC 陳述式的範例
本主題說明各種 EXEC 陳述式的範例語法。

## <a name="sample-statements"></a>範例陳述式 
  
-   若要執行不接受任何輸入的參數的 BAPI，請使用下列語法;資料透過傳回**DataReader**物件：  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST  
    ```  
  
-   若要執行會使用輸入的參數的 RFC，請使用下列語法：  
  
    ```  
    EXEC RFC_CUSTOMER_GET @NAME1='Contoso'  
    ```  
  
-   若要執行會為變數指定的輸入的參數的 RFC，請使用下列語法：  
  
    ```  
    EXEC RFC_CUSTOMER_GET @var=@var  
    ```  
  
     在此範例中，您必須建立名為`@var`並將值明確 （例如，若要為 1001)，因為 RFC_CUSTOMER_GET 的第一個參數對應至 KUNNR (Customer Number)  
  
-   若要執行 RFC 使用輸入的參數名稱的變數，請使用下列語法：  
  
    ```  
    EXEC RFC_CUSTOMER_GET @KUNNR=@var1, @NAME1='Contoso'  
    ```  
  
     您必須建立名為`@var1`，指定的值，然後將它繫結至對應的命令物件。 新建立的參數物件的預設方向是`input`。  
  
-   若要執行 BAPI 和傳回的資料表做為參數，使用下列語法：  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST @COMPANYCODE_LIST=@var1 OUTPUT  
    ```  
  
     您必須建立名為`@var1`、 指定的值，並將它繫結至對應的命令物件。 新建立的參數物件的方向應該`InputOutput`或`Output`。  
  
-   下列 EXEC 範例會使用資料表的複雜型別參數。 在範例中，@fields資料表參數。  
  
    ```  
    exec rfc_read_table @query_table='BNKA', @fields='<FIELDS xmlns='http://Microsoft.LobServices.Sap/2007/03/Rfc/'>  
                <RFC_DB_FLD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                  <FIELDNAME>BANKL</FIELDNAME>  
                </RFC_DB_FLD>  
                <RFC_DB_FLD  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                    <FIELDNAME>BANKS</FIELDNAME>  
                </RFC_DB_FLD>  
              </FIELDS>', @fields=@flds output  
    ```  
  
-   下列 EXEC 範例會使用結構複雜型別。 在範例中，@equimaster結構參數。  
  
    ```  
    exec BAPI_EQMT_MODIFY @equipment='000000000000000637', @equimaster='<EQUIMASTER>           
                <EQUIPMENT xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">equip</EQUIPMENT>  
                <EQUICATGRY xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">E</EQUICATGRY>  
                <MATERIAL xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">mat</MATERIAL>  
              </EQUIMASTER >', @equimaster=@em output  
    ```  
  
## <a name="support-for-complex-parameter-types"></a>複雜的參數類型的支援  
 有兩種方式來支援複雜的 RFC 參數 （資料表和結構） 當您使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:  
  
- 提供內嵌的 XML 值的複雜型別。 此範例示範如何將 XML 傳遞到複雜的參數型別*欄位*。 在下列範例中， <em>@fields</em>資料表參數。  
  
  ```  
  exec rfc_read_table @query_table='BNKA', @fields='<FIELDS xmlns='http://Microsoft.LobServices.Sap/2007/03/Rfc/'>  
              <RFC_DB_FLD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                <FIELDNAME>BANKL</FIELDNAME>  
              </RFC_DB_FLD>  
              <RFC_DB_FLD  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                  <FIELDNAME>BANKS</FIELDNAME>  
              </RFC_DB_FLD>  
            </FIELDS>', @fields=@flds output  
  ```  
  
- 建立**DataTable**複雜型別和 SAP 參數值的集合中的欄位的資料行的參數**DataTable**。 此範例示範如何設定@fields使用的複雜型別**DataTable**。  
  
  ```  
  cmd.CommandText = "exec rfc_read_table @query_table='BNKA', @fields = @p_fields";  
  DataTable dt = new DataTable();  
  dt.Columns.Add("FIELDNAME");  
  SAPParameter p = new SAPParameter("@p_fields");  
  p.Value = dt;  
  ```  
  
## <a name="limitations"></a>限制  
 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]具有下列限制的複雜型別。  
  
- 傳遞時，複雜型別參數中使用**DataTable**，您必須包含所有欄位 （資料行） 中的複雜型別**DataTable**。  
  
- [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] Nepodporuje **DbNull**。 您無法設定**DbNull**做為參數的值。  
  
