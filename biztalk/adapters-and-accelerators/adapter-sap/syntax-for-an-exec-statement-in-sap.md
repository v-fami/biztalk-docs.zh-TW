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
# <a name="syntax-for-an-exec-statement-in-sap"></a><span data-ttu-id="2b749-102">在 SAP 中 EXEC 陳述式的語法</span><span class="sxs-lookup"><span data-stu-id="2b749-102">Syntax for an EXEC Statement in SAP</span></span>
<span data-ttu-id="2b749-103">下列章節會說明實作 EXEC 陳述式的文法規格[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b749-103">The following section describes grammar specifications for implementing EXEC statements against the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span> <span data-ttu-id="2b749-104">請注意，在許多情況下，語法的 TRANSACT-SQL 語法稍有不同。</span><span class="sxs-lookup"><span data-stu-id="2b749-104">Notice that in several cases, the syntax is somewhat different from Transact-SQL syntax.</span></span>  
  
```  
EXEC rfc_name {<argument_element>} [ , …n ]  {;}[0,1] [ OPTION <disabledatavalidation>, <firstresultset> ]  
```  
  
 <span data-ttu-id="2b749-105">其中：</span><span class="sxs-lookup"><span data-stu-id="2b749-105">where:</span></span>  
  
- <span data-ttu-id="2b749-106">**rfc_name**指定執行的函式呼叫的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b749-106">**rfc_name** specifies the name of the function call to execute.</span></span>  
  
- <span data-ttu-id="2b749-107">**< argument_element >** :: = @param_name = [0，1] \<const\> {[輸入&#124;輸出]} [0，1]</span><span class="sxs-lookup"><span data-stu-id="2b749-107">**<argument_element>** ::= @param_name = [0,1] \<const\> {[ INPUT &#124; OUTPUT ]}[0,1]</span></span>  
  
  -   <span data-ttu-id="2b749-108">**param_name**指定函式的介面中定義的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="2b749-108">**param_name** specifies the parameter name defined in the function interface.</span></span>  
  
  -   <span data-ttu-id="2b749-109">**\<const\>**  :: = 整數&#124;real&#124;字串&#124;？</span><span class="sxs-lookup"><span data-stu-id="2b749-109">**\<const\>** ::= integer &#124; real &#124; string &#124; ?</span></span> <span data-ttu-id="2b749-110">&#124;NULL &#124; xml_element</span><span class="sxs-lookup"><span data-stu-id="2b749-110">&#124; NULL &#124; xml_element</span></span>  
  
- <span data-ttu-id="2b749-111">**選項**提供選項，在您要將資料呈現的方式。</span><span class="sxs-lookup"><span data-stu-id="2b749-111">**OPTION**  provides option on how you want to present the data.</span></span> <span data-ttu-id="2b749-112">可用的選項如下：</span><span class="sxs-lookup"><span data-stu-id="2b749-112">The available options are:</span></span>  
  
  - <span data-ttu-id="2b749-113">**disabledatavalidation**選項組**EnableSafeTyping**繫結屬性，在基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b749-113">**disabledatavalidation** option sets the **EnableSafeTyping** binding property in the underlying [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="2b749-114">啟用 「 安全輸入時 DATS、 TIMS 和 NUMC 資料型別會表示為字串。</span><span class="sxs-lookup"><span data-stu-id="2b749-114">When safe typing is enabled the DATS, TIMS, and NUMC data types are represented as strings.</span></span> <span data-ttu-id="2b749-115">如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2b749-115">For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
  - <span data-ttu-id="2b749-116">**firstresultset**指定所傳回的第一個結果集[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b749-116">**firstresultset** specifies the first result set that is returned by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="2b749-117">在 ADO 提供者來源上執行的任何陳述式時，只有第一個傳回的結果集使用。</span><span class="sxs-lookup"><span data-stu-id="2b749-117">When any statement is executed on an ADO Provider source, only the first result set returned is available.</span></span> <span data-ttu-id="2b749-118">RFC EXEC 的情況下，通常是多個資料表參數會傳回但只有第一個結果集可供用戶端程式，可能無法使用的程式。</span><span class="sxs-lookup"><span data-stu-id="2b749-118">For RFC EXEC scenarios, usually multiple table parameters are returned but if only the first result set is available for the client program, which might not be of use.</span></span> <span data-ttu-id="2b749-119">藉由指定"firstresultset 」 關鍵字的 OPTION 子句的一部分，用戶端可以指定他們想要傳回的提供者的第一個資料表參數。</span><span class="sxs-lookup"><span data-stu-id="2b749-119">By specifying the “firstresultset” keyword as part of the OPTION clause, clients can specify the first table parameter that they want the Provider to return.</span></span> <span data-ttu-id="2b749-120">例如：</span><span class="sxs-lookup"><span data-stu-id="2b749-120">For example:</span></span>  
  
    ```  
    EXEC Z_TEST_ALL_TYPES @P_IN='TestInput' OPTION 'disabledatavalidation', firstresultset TAB_ALLTYPES'  
    ```  
  
     <span data-ttu-id="2b749-121">在此範例中，在 EXEC 陳述式會指定傳回的第一個資料表參數應該 TAB_ALLTYPES。</span><span class="sxs-lookup"><span data-stu-id="2b749-121">In this example, the EXEC statement specifies that the first table parameter returned should be TAB_ALLTYPES.</span></span>  
  
  > [!IMPORTANT]
  >  <span data-ttu-id="2b749-122">您必須永遠提供的值選項關鍵字在單引號中，例如，'*disabledatavalidation*'。</span><span class="sxs-lookup"><span data-stu-id="2b749-122">You must always provide the values for the OPTION keyword within single quotes, for example, '*disabledatavalidation*'.</span></span>  
  
  <span data-ttu-id="2b749-123">在上述語法中，xml_element 可用來提供輸入的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="2b749-123">In the preceding syntax, xml_element can be used to provide input for complex types.</span></span> <span data-ttu-id="2b749-124">Xml 項目結構會有不同結構和資料表。</span><span class="sxs-lookup"><span data-stu-id="2b749-124">The xml element structure will be different for structures and tables.</span></span> <span data-ttu-id="2b749-125">結構 xml_element 如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b749-125">The xml_element for structure resembles the following:</span></span>  
  
```  
<PARAM_NAME>  
    <FIELDNAME_1 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_1>  
    <FIELDNAME_2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_2>  
    ...  
    ...  
</ PARAM_NAME>  
```  
  
 <span data-ttu-id="2b749-126">資料表 xml_element 如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b749-126">The xml_element for table resembles the following:</span></span>  
  
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
  
 <span data-ttu-id="2b749-127">例如，結構類型的 XML 項目如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b749-127">For example, the XML element for a structure type resembles the following:</span></span>  
  
```  
<INOUT_STRUCT>  
       <ACCPFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006</ACCPFIELD>  
       <CHARFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">John</CHARFIELD>                 
</INOUT_STRUCT>  
```  
  
 <span data-ttu-id="2b749-128">同樣地，針對資料表類型的 XML 項目如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b749-128">Similarly, the XML element for a table type resembles the following:</span></span>  
  
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
  
 <span data-ttu-id="2b749-129">例如陳述式，請參閱 < [EXEC 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="2b749-129">For example statements, see [Examples for EXEC Statement](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).</span></span>  
  
## <a name="handling-named-parameters"></a><span data-ttu-id="2b749-130">具名參數的處理</span><span class="sxs-lookup"><span data-stu-id="2b749-130">Handling Named Parameters</span></span>  
 <span data-ttu-id="2b749-131">指定的具名參數執行查詢的指導方針如下：</span><span class="sxs-lookup"><span data-stu-id="2b749-131">The following are guidelines for specifying named parameters in EXEC queries:</span></span>  
  
- <span data-ttu-id="2b749-132">您必須指定參數，透過命名 (例如@param_name= value)。</span><span class="sxs-lookup"><span data-stu-id="2b749-132">You must specify parameters by naming them (for example, @param_name=value).</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="2b749-133">不支援未命名的參數</span><span class="sxs-lookup"><span data-stu-id="2b749-133">Unnamed parameters are not supported</span></span>  
  
- <span data-ttu-id="2b749-134">使用預設值來定義參數時，您可以執行程序，而不指定參數。</span><span class="sxs-lookup"><span data-stu-id="2b749-134">When a parameter is defined using a default value, you can execute the procedure without specifying a parameter.</span></span>  
  
- <span data-ttu-id="2b749-135">EXEC 查詢不支援使用參數具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="2b749-135">EXEC queries do not support using parameters with the following properties:</span></span>  
  
  - <span data-ttu-id="2b749-136">巢狀的結構 （包含結構做為其欄位的結構）。</span><span class="sxs-lookup"><span data-stu-id="2b749-136">Nested structures (structures that contain structures as their fields).</span></span>  
  
  - <span data-ttu-id="2b749-137">巢狀的資料表。</span><span class="sxs-lookup"><span data-stu-id="2b749-137">Nested tables.</span></span>  
  
  - <span data-ttu-id="2b749-138">包含結構的資料表。</span><span class="sxs-lookup"><span data-stu-id="2b749-138">A table containing a structure.</span></span>  
  
  - <span data-ttu-id="2b749-139">包含資料表的結構。</span><span class="sxs-lookup"><span data-stu-id="2b749-139">A structure containing a table.</span></span>  
  
  - <span data-ttu-id="2b749-140">結構或具有具有複合字串類型的欄位，例如資料表`SSTRING`或`RAWSTRING`。</span><span class="sxs-lookup"><span data-stu-id="2b749-140">A structure or table that has fields with composite string types, for example `SSTRING` or `RAWSTRING`.</span></span>  
  
    <span data-ttu-id="2b749-141">執行 RFC 時下, 表將列出 RFC 參數類型與參數方向之間的邏輯對應。</span><span class="sxs-lookup"><span data-stu-id="2b749-141">The following table lists logical mappings between RFC parameter types and parameter directions when executing an RFC.</span></span>  
  
  |<span data-ttu-id="2b749-142">RFC 參數類型</span><span class="sxs-lookup"><span data-stu-id="2b749-142">RFC Param Type</span></span>|<span data-ttu-id="2b749-143">查詢關鍵字</span><span class="sxs-lookup"><span data-stu-id="2b749-143">Query Keyword</span></span>|<span data-ttu-id="2b749-144">參數方向</span><span class="sxs-lookup"><span data-stu-id="2b749-144">Parameter Direction</span></span>|  
  |--------------------|-------------------|-------------------------|  
  |<span data-ttu-id="2b749-145">匯入參數</span><span class="sxs-lookup"><span data-stu-id="2b749-145">Import parameters</span></span>|<span data-ttu-id="2b749-146">執行任何動作</span><span class="sxs-lookup"><span data-stu-id="2b749-146">Nothing</span></span>|<span data-ttu-id="2b749-147">Paramdirection.Input</span><span class="sxs-lookup"><span data-stu-id="2b749-147">Paramdirection.Input</span></span>|  
  |<span data-ttu-id="2b749-148">匯出參數</span><span class="sxs-lookup"><span data-stu-id="2b749-148">Export parameters</span></span>|<span data-ttu-id="2b749-149">輸出</span><span class="sxs-lookup"><span data-stu-id="2b749-149">Output</span></span>|<span data-ttu-id="2b749-150">Paramdirection.Output</span><span class="sxs-lookup"><span data-stu-id="2b749-150">Paramdirection.Output</span></span>|  
  |<span data-ttu-id="2b749-151">資料表參數</span><span class="sxs-lookup"><span data-stu-id="2b749-151">Table parameters</span></span>|<span data-ttu-id="2b749-152">輸出/無</span><span class="sxs-lookup"><span data-stu-id="2b749-152">Output/Nothing</span></span>|<span data-ttu-id="2b749-153">InputOutput</span><span class="sxs-lookup"><span data-stu-id="2b749-153">InputOutput</span></span>|  
  
  <span data-ttu-id="2b749-154">以下是一般的指導方針處理參數：</span><span class="sxs-lookup"><span data-stu-id="2b749-154">The following are general guidelines for handling parameters:</span></span>  
  
- <span data-ttu-id="2b749-155">您可以指定參數值，為常數，或是在查詢中使用的預留位置。</span><span class="sxs-lookup"><span data-stu-id="2b749-155">You can specify parameter values either as constants or by using placeholders in the query.</span></span>  
  
- <span data-ttu-id="2b749-156">當在查詢中使用的預留位置，您必須建立`SAPParameter`物件，並將它新增至對應的命令物件。</span><span class="sxs-lookup"><span data-stu-id="2b749-156">When using placeholders in the query, you must create a `SAPParameter` object and add it to the corresponding command object.</span></span> <span data-ttu-id="2b749-157">然後將預留位置名稱傳遞給建構函式方向和值取決於內容。</span><span class="sxs-lookup"><span data-stu-id="2b749-157">You then pass the placeholder name to the constructor; the direction and value depend on the context.</span></span>  
  
  -   <span data-ttu-id="2b749-158">針對`Input`參數，未指定查詢中的參數方向的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2b749-158">For `Input` parameters, do not specify in the query a keyword for the parameter direction.</span></span> <span data-ttu-id="2b749-159">`value`必須設定參數物件的欄位，或提供者將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2b749-159">The `value` field of the parameter object must be set, or the provider will throw an exception.</span></span> <span data-ttu-id="2b749-160">您必須明確設定`direction`欄位的參數物件，因為提供者預設為`Input`。</span><span class="sxs-lookup"><span data-stu-id="2b749-160">You must not explicitly set the `direction` field of the parameter object, because the provider defaults to `Input`.</span></span>  
  
  -   <span data-ttu-id="2b749-161">其他參數，使用表單`@paramname=@placeholder`並指定`Output`查詢中明確的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2b749-161">For other parameters, use the form `@paramname=@placeholder` and specify the `Output` keyword explicitly in the query.</span></span> <span data-ttu-id="2b749-162">然後您必須加入`SAPParameter`相對應的預留位置，明確地將參數方向設定為`ParamDirection.Output`或`ParamDirection.InputOutput`，取決於參數類型。</span><span class="sxs-lookup"><span data-stu-id="2b749-162">You must then add a `SAPParameter` that corresponds with the placeholder and explicitly set the parameter direction to either `ParamDirection.Output` or `ParamDirection.InputOutput`, depending on the parameter type.</span></span>  
  
- <span data-ttu-id="2b749-163">參數名稱和預留位置名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2b749-163">Parameter names and placeholder names are not case-sensitive.</span></span>  
  
- <span data-ttu-id="2b749-164">在查詢中不重複參數名稱，除非它們有不同的方向。</span><span class="sxs-lookup"><span data-stu-id="2b749-164">Parameter names cannot be repeated in a query unless they have different directions.</span></span>  
  
- <span data-ttu-id="2b749-165">預留位置名稱不能在查詢中重複。</span><span class="sxs-lookup"><span data-stu-id="2b749-165">Placeholder names cannot be repeated in a query.</span></span>  
  
## <a name="considerations-when-calling-an-exec-statement"></a><span data-ttu-id="2b749-166">呼叫 EXEC 陳述式時的考量</span><span class="sxs-lookup"><span data-stu-id="2b749-166">Considerations When Calling an EXEC Statement</span></span>  
 <span data-ttu-id="2b749-167">此區段會列出使用 EXEC 陳述式時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b749-167">This section lists the points that you must keep in mind when using the EXEC statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
- <span data-ttu-id="2b749-168">EXEC 陳述式[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會傳回`TIMS`欄位值為.NET`System.DateTime`物件。</span><span class="sxs-lookup"><span data-stu-id="2b749-168">For an EXEC statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `TIMS` field values as .NET `System.DateTime` objects.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="2b749-169">SELECT 陳述式，如[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會傳回`TIMS`欄位值為.NET`System.TimeSpan`物件。</span><span class="sxs-lookup"><span data-stu-id="2b749-169">For a SELECT statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `TIMS` field values as .NET `System.TimeSpan` objects.</span></span> <span data-ttu-id="2b749-170">如需 SELECT 陳述式的詳細資訊，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="2b749-170">For more information about the SELECT statement, see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b749-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b749-171">See Also</span></span>  
 [<span data-ttu-id="2b749-172">關於 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="2b749-172">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)