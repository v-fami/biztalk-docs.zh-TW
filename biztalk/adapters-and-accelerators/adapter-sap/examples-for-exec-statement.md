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
# <a name="examples-for-exec-statement"></a><span data-ttu-id="a5490-103">EXEC 陳述式的範例</span><span class="sxs-lookup"><span data-stu-id="a5490-103">Examples for EXEC Statement</span></span>
<span data-ttu-id="a5490-104">本主題說明各種 EXEC 陳述式的範例語法。</span><span class="sxs-lookup"><span data-stu-id="a5490-104">This topic shows example syntax for various EXEC statements.</span></span>

## <a name="sample-statements"></a><span data-ttu-id="a5490-105">範例陳述式</span><span class="sxs-lookup"><span data-stu-id="a5490-105">Sample statements</span></span> 
  
-   <span data-ttu-id="a5490-106">若要執行不接受任何輸入的參數的 BAPI，請使用下列語法;資料透過傳回**DataReader**物件：</span><span class="sxs-lookup"><span data-stu-id="a5490-106">To execute a BAPI that takes no input parameters, use the following syntax; data is returned through a **DataReader** object:</span></span>  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST  
    ```  
  
-   <span data-ttu-id="a5490-107">若要執行會使用輸入的參數的 RFC，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a5490-107">To execute an RFC that takes input parameters, use the following syntax:</span></span>  
  
    ```  
    EXEC RFC_CUSTOMER_GET @NAME1='Contoso'  
    ```  
  
-   <span data-ttu-id="a5490-108">若要執行會為變數指定的輸入的參數的 RFC，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a5490-108">To execute an RFC that takes input parameters specified as a variable, use the following syntax:</span></span>  
  
    ```  
    EXEC RFC_CUSTOMER_GET @var=@var  
    ```  
  
     <span data-ttu-id="a5490-109">在此範例中，您必須建立名為`@var`並將值明確 （例如，若要為 1001)，因為 RFC_CUSTOMER_GET 的第一個參數對應至 KUNNR (Customer Number)</span><span class="sxs-lookup"><span data-stu-id="a5490-109">In this example, you must create a parameter named `@var` and set the value explicitly (for example, to 1001), because the first parameter for RFC_CUSTOMER_GET corresponds to KUNNR (Customer Number)</span></span>  
  
-   <span data-ttu-id="a5490-110">若要執行 RFC 使用輸入的參數名稱的變數，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a5490-110">To execute an RFC that uses a variable for the input parameter name, use the following syntax:</span></span>  
  
    ```  
    EXEC RFC_CUSTOMER_GET @KUNNR=@var1, @NAME1='Contoso'  
    ```  
  
     <span data-ttu-id="a5490-111">您必須建立名為`@var1`，指定的值，然後將它繫結至對應的命令物件。</span><span class="sxs-lookup"><span data-stu-id="a5490-111">You must create a parameter named `@var1`, specify the value, and then bind it to the corresponding command object.</span></span> <span data-ttu-id="a5490-112">新建立的參數物件的預設方向是`input`。</span><span class="sxs-lookup"><span data-stu-id="a5490-112">The default direction of the newly created parameter object is `input`.</span></span>  
  
-   <span data-ttu-id="a5490-113">若要執行 BAPI 和傳回的資料表做為參數，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a5490-113">To execute a BAPI and return tables as a parameter, use the following syntax:</span></span>  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST @COMPANYCODE_LIST=@var1 OUTPUT  
    ```  
  
     <span data-ttu-id="a5490-114">您必須建立名為`@var1`、 指定的值，並將它繫結至對應的命令物件。</span><span class="sxs-lookup"><span data-stu-id="a5490-114">You must create a parameter named `@var1`, specify the value, and bind it to the corresponding command object.</span></span> <span data-ttu-id="a5490-115">新建立的參數物件的方向應該`InputOutput`或`Output`。</span><span class="sxs-lookup"><span data-stu-id="a5490-115">The direction of the newly created parameter object should be `InputOutput` or `Output`.</span></span>  
  
-   <span data-ttu-id="a5490-116">下列 EXEC 範例會使用資料表的複雜型別參數。</span><span class="sxs-lookup"><span data-stu-id="a5490-116">The following EXEC example uses a table complex type parameter.</span></span> <span data-ttu-id="a5490-117">在範例中，@fields資料表參數。</span><span class="sxs-lookup"><span data-stu-id="a5490-117">In the example, @fields is a TABLE parameter.</span></span>  
  
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
  
-   <span data-ttu-id="a5490-118">下列 EXEC 範例會使用結構複雜型別。</span><span class="sxs-lookup"><span data-stu-id="a5490-118">The following EXEC example uses a STRUCT complex type.</span></span> <span data-ttu-id="a5490-119">在範例中，@equimaster結構參數。</span><span class="sxs-lookup"><span data-stu-id="a5490-119">In the example, @equimaster is a STRUCT parameter.</span></span>  
  
    ```  
    exec BAPI_EQMT_MODIFY @equipment='000000000000000637', @equimaster='<EQUIMASTER>           
                <EQUIPMENT xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">equip</EQUIPMENT>  
                <EQUICATGRY xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">E</EQUICATGRY>  
                <MATERIAL xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">mat</MATERIAL>  
              </EQUIMASTER >', @equimaster=@em output  
    ```  
  
## <a name="support-for-complex-parameter-types"></a><span data-ttu-id="a5490-120">複雜的參數類型的支援</span><span class="sxs-lookup"><span data-stu-id="a5490-120">Support for Complex Parameter Types</span></span>  
 <span data-ttu-id="a5490-121">有兩種方式來支援複雜的 RFC 參數 （資料表和結構） 當您使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a5490-121">There are two ways to support complex RFC parameters (tables and structures) when you use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:</span></span>  
  
- <span data-ttu-id="a5490-122">提供內嵌的 XML 值的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="a5490-122">Provide an inline XML value for the complex type.</span></span> <span data-ttu-id="a5490-123">此範例示範如何將 XML 傳遞到複雜的參數型別*欄位*。</span><span class="sxs-lookup"><span data-stu-id="a5490-123">This example shows how to pass XML to the complex parameter type *fields*.</span></span> <span data-ttu-id="a5490-124">在下列範例中， <em>@fields</em>資料表參數。</span><span class="sxs-lookup"><span data-stu-id="a5490-124">In the following example, <em>@fields</em> is a table parameter.</span></span>  
  
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
  
- <span data-ttu-id="a5490-125">建立**DataTable**複雜型別和 SAP 參數值的集合中的欄位的資料行的參數**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="a5490-125">Create a **DataTable** parameter with columns for the fields in the complex type and set the SAP parameter value to **DataTable**.</span></span> <span data-ttu-id="a5490-126">此範例示範如何設定@fields使用的複雜型別**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="a5490-126">This example shows how to set the @fields complex type by using a **DataTable**.</span></span>  
  
  ```  
  cmd.CommandText = "exec rfc_read_table @query_table='BNKA', @fields = @p_fields";  
  DataTable dt = new DataTable();  
  dt.Columns.Add("FIELDNAME");  
  SAPParameter p = new SAPParameter("@p_fields");  
  p.Value = dt;  
  ```  
  
## <a name="limitations"></a><span data-ttu-id="a5490-127">限制</span><span class="sxs-lookup"><span data-stu-id="a5490-127">Limitations</span></span>  
 <span data-ttu-id="a5490-128">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]具有下列限制的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="a5490-128">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] has the following limitations for complex types.</span></span>  
  
- <span data-ttu-id="a5490-129">傳遞時，複雜型別參數中使用**DataTable**，您必須包含所有欄位 （資料行） 中的複雜型別**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="a5490-129">When you pass a complex type in a parameter by using a **DataTable**, you must include all fields (columns) of the complex type in the **DataTable**.</span></span>  
  
- <span data-ttu-id="a5490-130">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] Nepodporuje **DbNull**。</span><span class="sxs-lookup"><span data-stu-id="a5490-130">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] does not support **DbNull**.</span></span> <span data-ttu-id="a5490-131">您無法設定**DbNull**做為參數的值。</span><span class="sxs-lookup"><span data-stu-id="a5490-131">You cannot set **DbNull** as a value for parameters.</span></span>  
  
