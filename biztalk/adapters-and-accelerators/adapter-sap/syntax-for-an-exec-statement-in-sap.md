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
ms.openlocfilehash: e9b2299407986ef2fca53304b536c5ce89625941
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="syntax-for-an-exec-statement-in-sap"></a><span data-ttu-id="c4ec3-102">SAP 的 EXEC 陳述式的語法</span><span class="sxs-lookup"><span data-stu-id="c4ec3-102">Syntax for an EXEC Statement in SAP</span></span>
<span data-ttu-id="c4ec3-103">下節說明實作 EXEC 陳述式的文法規格[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-103">The following section describes grammar specifications for implementing EXEC statements against the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span> <span data-ttu-id="c4ec3-104">請注意，在數個情況下，語法與 TRANSACT-SQL 語法稍有不同。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-104">Notice that in several cases, the syntax is somewhat different from Transact-SQL syntax.</span></span>  
  
```  
EXEC rfc_name {<argument_element>} [ , …n ]  {;}[0,1] [ OPTION <disabledatavalidation>, <firstresultset> ]  
```  
  
 <span data-ttu-id="c4ec3-105">其中：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-105">where:</span></span>  
  
-   <span data-ttu-id="c4ec3-106">**rfc_name**指定執行的函式呼叫的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-106">**rfc_name** specifies the name of the function call to execute.</span></span>  
  
-   <span data-ttu-id="c4ec3-107">**< argument_element >** :: = @param_name = [0，1] \<const > {[輸入 &#124;輸出]} [0，1]</span><span class="sxs-lookup"><span data-stu-id="c4ec3-107">**<argument_element>** ::= @param_name = [0,1] \<const> {[ INPUT &#124; OUTPUT ]}[0,1]</span></span>  
  
    -   <span data-ttu-id="c4ec3-108">**param_name**指定函式的介面中定義的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-108">**param_name** specifies the parameter name defined in the function interface.</span></span>  
  
    -   <span data-ttu-id="c4ec3-109">**\<const >** :: = 整數 &#124; 真實 &#124; 字串 &#124; 嗎？</span><span class="sxs-lookup"><span data-stu-id="c4ec3-109">**\<const>** ::= integer &#124; real &#124; string &#124; ?</span></span> <span data-ttu-id="c4ec3-110">&#124;NULL &#124;xml_element</span><span class="sxs-lookup"><span data-stu-id="c4ec3-110">&#124; NULL &#124; xml_element</span></span>  
  
-   <span data-ttu-id="c4ec3-111">**選項**提供您想要如何呈現資料的選項。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-111">**OPTION**  provides option on how you want to present the data.</span></span> <span data-ttu-id="c4ec3-112">可用的選項如下：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-112">The available options are:</span></span>  
  
    -   <span data-ttu-id="c4ec3-113">**disabledatavalidation**選項集**EnableSafeTyping**繫結屬性在基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-113">**disabledatavalidation** option sets the **EnableSafeTyping** binding property in the underlying [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="c4ec3-114">當已啟用 「 安全輸入 DATS、 TIMS 和 NUMC 資料型別會表示為字串。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-114">When safe typing is enabled the DATS, TIMS, and NUMC data types are represented as strings.</span></span> <span data-ttu-id="c4ec3-115">如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-115">For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    -   <span data-ttu-id="c4ec3-116">**firstresultset**指定所傳回的第一個結果集[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-116">**firstresultset** specifies the first result set that is returned by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="c4ec3-117">在 ADO 提供者來源上執行的任何陳述式時，只有第一個傳回的結果集使用。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-117">When any statement is executed on an ADO Provider source, only the first result set returned is available.</span></span> <span data-ttu-id="c4ec3-118">RFC EXEC 案例中，通常有多個資料表參數會傳回但只有第一個結果集供用戶端程式，這可能不是使用。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-118">For RFC EXEC scenarios, usually multiple table parameters are returned but if only the first result set is available for the client program, which might not be of use.</span></span> <span data-ttu-id="c4ec3-119">藉由指定"firstresultset 「 關鍵字做為 OPTION 子句的一部分，用戶端可以指定他們想要傳回的提供者的第一個資料表參數。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-119">By specifying the “firstresultset” keyword as part of the OPTION clause, clients can specify the first table parameter that they want the Provider to return.</span></span> <span data-ttu-id="c4ec3-120">例如：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-120">For example:</span></span>  
  
        ```  
        EXEC Z_TEST_ALL_TYPES @P_IN='TestInput' OPTION 'disabledatavalidation', firstresultset TAB_ALLTYPES'  
        ```  
  
         <span data-ttu-id="c4ec3-121">在此範例中，在 EXEC 陳述式會指定傳回的第一個資料表參數應該 TAB_ALLTYPES。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-121">In this example, the EXEC statement specifies that the first table parameter returned should be TAB_ALLTYPES.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c4ec3-122">您必須一律提供的值選項關鍵字在單引號中，例如，'*disabledatavalidation*'。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-122">You must always provide the values for the OPTION keyword within single quotes, for example, '*disabledatavalidation*'.</span></span>  
  
 <span data-ttu-id="c4ec3-123">在上述語法中，xml_element 可用來提供輸入的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-123">In the preceding syntax, xml_element can be used to provide input for complex types.</span></span> <span data-ttu-id="c4ec3-124">Xml 項目結構會結構與資料表的不同。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-124">The xml element structure will be different for structures and tables.</span></span> <span data-ttu-id="c4ec3-125">結構 xml_element 如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-125">The xml_element for structure resembles the following:</span></span>  
  
```  
<PARAM_NAME>  
    <FIELDNAME_1 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_1>  
    <FIELDNAME_2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_2>  
    ...  
    ...  
\</ PARAM_NAME>  
```  
  
 <span data-ttu-id="c4ec3-126">資料表 xml_element 如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-126">The xml_element for table resembles the following:</span></span>  
  
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
\</ PARAM_NAME>  
```  
  
 <span data-ttu-id="c4ec3-127">例如，結構類型的 XML 項目如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-127">For example, the XML element for a structure type resembles the following:</span></span>  
  
```  
<INOUT_STRUCT>  
       <ACCPFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006</ACCPFIELD>  
       <CHARFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">John</CHARFIELD>                 
</INOUT_STRUCT>  
```  
  
 <span data-ttu-id="c4ec3-128">同樣地，資料表類型的 XML 項目如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-128">Similarly, the XML element for a table type resembles the following:</span></span>  
  
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
  
 <span data-ttu-id="c4ec3-129">如需範例陳述式，請參閱[EXEC 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-129">For example statements, see [Examples for EXEC Statement](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).</span></span>  
  
## <a name="handling-named-parameters"></a><span data-ttu-id="c4ec3-130">處理具名參數</span><span class="sxs-lookup"><span data-stu-id="c4ec3-130">Handling Named Parameters</span></span>  
 <span data-ttu-id="c4ec3-131">指定具名參數在 EXEC 查詢中的指導方針如下：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-131">The following are guidelines for specifying named parameters in EXEC queries:</span></span>  
  
-   <span data-ttu-id="c4ec3-132">您必須指定參數加以命名 (例如， @param_name= 值)。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-132">You must specify parameters by naming them (for example, @param_name=value).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4ec3-133">不支援未命名的參數</span><span class="sxs-lookup"><span data-stu-id="c4ec3-133">Unnamed parameters are not supported</span></span>  
  
-   <span data-ttu-id="c4ec3-134">使用預設值來定義參數時，您可以執行程序，但未指定參數。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-134">When a parameter is defined using a default value, you can execute the procedure without specifying a parameter.</span></span>  
  
-   <span data-ttu-id="c4ec3-135">EXEC 查詢不支援使用參數具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-135">EXEC queries do not support using parameters with the following properties:</span></span>  
  
    -   <span data-ttu-id="c4ec3-136">巢狀的結構 （包含結構做為其欄位的結構）。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-136">Nested structures (structures that contain structures as their fields).</span></span>  
  
    -   <span data-ttu-id="c4ec3-137">巢狀的資料表。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-137">Nested tables.</span></span>  
  
    -   <span data-ttu-id="c4ec3-138">包含結構的資料表。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-138">A table containing a structure.</span></span>  
  
    -   <span data-ttu-id="c4ec3-139">包含資料表的結構。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-139">A structure containing a table.</span></span>  
  
    -   <span data-ttu-id="c4ec3-140">結構或資料表包含複合字串類型的欄位，例如`SSTRING`或`RAWSTRING`。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-140">A structure or table that has fields with composite string types, for example `SSTRING` or `RAWSTRING`.</span></span>  
  
     <span data-ttu-id="c4ec3-141">執行 RFC 時下, 表列出之間 RFC 參數型別和參數方向的邏輯對應。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-141">The following table lists logical mappings between RFC parameter types and parameter directions when executing an RFC.</span></span>  
  
    |<span data-ttu-id="c4ec3-142">RFC 參數類型</span><span class="sxs-lookup"><span data-stu-id="c4ec3-142">RFC Param Type</span></span>|<span data-ttu-id="c4ec3-143">查詢關鍵字</span><span class="sxs-lookup"><span data-stu-id="c4ec3-143">Query Keyword</span></span>|<span data-ttu-id="c4ec3-144">參數方向</span><span class="sxs-lookup"><span data-stu-id="c4ec3-144">Parameter Direction</span></span>|  
    |--------------------|-------------------|-------------------------|  
    |<span data-ttu-id="c4ec3-145">匯入參數</span><span class="sxs-lookup"><span data-stu-id="c4ec3-145">Import parameters</span></span>|<span data-ttu-id="c4ec3-146">執行任何動作</span><span class="sxs-lookup"><span data-stu-id="c4ec3-146">Nothing</span></span>|<span data-ttu-id="c4ec3-147">Paramdirection.Input</span><span class="sxs-lookup"><span data-stu-id="c4ec3-147">Paramdirection.Input</span></span>|  
    |<span data-ttu-id="c4ec3-148">匯出參數</span><span class="sxs-lookup"><span data-stu-id="c4ec3-148">Export parameters</span></span>|<span data-ttu-id="c4ec3-149">輸出</span><span class="sxs-lookup"><span data-stu-id="c4ec3-149">Output</span></span>|<span data-ttu-id="c4ec3-150">Paramdirection.Output</span><span class="sxs-lookup"><span data-stu-id="c4ec3-150">Paramdirection.Output</span></span>|  
    |<span data-ttu-id="c4ec3-151">資料表參數</span><span class="sxs-lookup"><span data-stu-id="c4ec3-151">Table parameters</span></span>|<span data-ttu-id="c4ec3-152">輸出/Nothing</span><span class="sxs-lookup"><span data-stu-id="c4ec3-152">Output/Nothing</span></span>|<span data-ttu-id="c4ec3-153">輸入輸出</span><span class="sxs-lookup"><span data-stu-id="c4ec3-153">InputOutput</span></span>|  
  
 <span data-ttu-id="c4ec3-154">以下是處理參數的一般指導方針：</span><span class="sxs-lookup"><span data-stu-id="c4ec3-154">The following are general guidelines for handling parameters:</span></span>  
  
-   <span data-ttu-id="c4ec3-155">您可以指定參數值為常數或使用查詢中的預留位置。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-155">You can specify parameter values either as constants or by using placeholders in the query.</span></span>  
  
-   <span data-ttu-id="c4ec3-156">當在查詢中使用的預留位置，您必須建立`SAPParameter`物件，並將它加入至對應的命令物件。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-156">When using placeholders in the query, you must create a `SAPParameter` object and add it to the corresponding command object.</span></span> <span data-ttu-id="c4ec3-157">然後將預留位置名稱傳遞給建構函式。方向和值取決於內容。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-157">You then pass the placeholder name to the constructor; the direction and value depend on the context.</span></span>  
  
    -   <span data-ttu-id="c4ec3-158">如`Input`參數，未指定在查詢中的參數方向的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-158">For `Input` parameters, do not specify in the query a keyword for the parameter direction.</span></span> <span data-ttu-id="c4ec3-159">`value`必須設定參數物件的欄位，或提供者將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-159">The `value` field of the parameter object must be set, or the provider will throw an exception.</span></span> <span data-ttu-id="c4ec3-160">您必須明確地設定`direction`欄位的參數物件，因為提供者預設為`Input`。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-160">You must not explicitly set the `direction` field of the parameter object, because the provider defaults to `Input`.</span></span>  
  
    -   <span data-ttu-id="c4ec3-161">其他參數，使用表單`@paramname=@placeholder`並指定`Output`在查詢中明確的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-161">For other parameters, use the form `@paramname=@placeholder` and specify the `Output` keyword explicitly in the query.</span></span> <span data-ttu-id="c4ec3-162">然後您必須加入`SAPParameter`對應於預留位置，而且明確設定的參數方向為`ParamDirection.Output`或`ParamDirection.InputOutput`，視使用的參數類型。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-162">You must then add a `SAPParameter` that corresponds with the placeholder and explicitly set the parameter direction to either `ParamDirection.Output` or `ParamDirection.InputOutput`, depending on the parameter type.</span></span>  
  
-   <span data-ttu-id="c4ec3-163">參數名稱和預留位置名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-163">Parameter names and placeholder names are not case-sensitive.</span></span>  
  
-   <span data-ttu-id="c4ec3-164">在查詢中不重複的參數名稱，除非他們擁有不同的方向。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-164">Parameter names cannot be repeated in a query unless they have different directions.</span></span>  
  
-   <span data-ttu-id="c4ec3-165">預留位置名稱不能在查詢中重複。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-165">Placeholder names cannot be repeated in a query.</span></span>  
  
## <a name="considerations-when-calling-an-exec-statement"></a><span data-ttu-id="c4ec3-166">呼叫 EXEC 陳述式時的考量</span><span class="sxs-lookup"><span data-stu-id="c4ec3-166">Considerations When Calling an EXEC Statement</span></span>  
 <span data-ttu-id="c4ec3-167">此區段會列出使用 EXEC 陳述式使用時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-167">This section lists the points that you must keep in mind when using the EXEC statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
-   <span data-ttu-id="c4ec3-168">EXEC 陳述式[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]傳回`TIMS`欄位值為.NET`System.DateTime`物件。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-168">For an EXEC statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `TIMS` field values as .NET `System.DateTime` objects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4ec3-169">SELECT 陳述式，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]傳回`TIMS`欄位值為.NET`System.TimeSpan`物件。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-169">For a SELECT statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `TIMS` field values as .NET `System.TimeSpan` objects.</span></span> <span data-ttu-id="c4ec3-170">如需 SELECT 陳述式的詳細資訊，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ec3-170">For more information about the SELECT statement, see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ec3-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4ec3-171">See Also</span></span>  
 [<span data-ttu-id="c4ec3-172">關於.NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="c4ec3-172">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)