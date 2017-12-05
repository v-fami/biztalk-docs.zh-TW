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
ms.openlocfilehash: 5198335cfa1a7d2036ca05759edc7d04e28cc20b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="syntax-for-an-execquery-statement-in-sap"></a><span data-ttu-id="763ed-102">SAP 中 EXECQUERY 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="763ed-102">Syntax for an EXECQUERY Statement in SAP</span></span>
<span data-ttu-id="763ed-103">您可以使用 SAP GUI 來建立查詢，以圖形方式來選取您想要查詢之資料行和排序的次序，您想要包含在結果集，等資料表。[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可讓使用者從 ADO.NET 應用程式中執行這類的查詢，藉由提供使用者可用來執行查詢，在 SAP 系統中定義的 EXECQUERY 作業。</span><span class="sxs-lookup"><span data-stu-id="763ed-103">You can use the SAP GUI to create queries by graphically selecting the tables you want to query, the columns and sort order you want included in the result set, etc. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] enables users to execute such queries from an ADO.NET application by providing an EXECQUERY operation that users can use to execute a query defined in the SAP system.</span></span>  
  
 <span data-ttu-id="763ed-104">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用自訂的 RFC Z_EXECUTE_SAP_QUERY SAP 系統中執行的預先定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="763ed-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC Z_EXECUTE_SAP_QUERY to execute the pre-defined queries in the SAP system.</span></span> <span data-ttu-id="763ed-105">自訂 RFC 依次執行 RSAQ_REMOTE_QUERY_CALL，這是 SAP 系統中定義的 RFC 的標準。</span><span class="sxs-lookup"><span data-stu-id="763ed-105">The custom RFC in turn executes the RSAQ_REMOTE_QUERY_CALL, which is a standard RFC defined in the SAP system.</span></span> <span data-ttu-id="763ed-106">因此，您可以使用 EXECQUERY 作業之前，您必須安裝自訂 RFC SAP 系統，您會執行針對查詢中。</span><span class="sxs-lookup"><span data-stu-id="763ed-106">Hence, before you can use the EXECQUERY operation, you must install the custom RFC in the SAP system you will be running your queries against.</span></span> <span data-ttu-id="763ed-107">如需有關如何安裝自訂 RFC 的指示，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="763ed-107">For instructions on how to install the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
 <span data-ttu-id="763ed-108">本主題提供的語法 EXECQUERY 作業，以及其他有用資訊 EXECQUERY 與作業有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="763ed-108">This topic provides information on the syntax of the EXECQUERY operation, and other useful information related to the EXECQUERY operation.</span></span>  
  
## <a name="syntax-for-an-execquery-statement"></a><span data-ttu-id="763ed-109">EXECQUERY 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="763ed-109">Syntax for an EXECQUERY Statement</span></span>  
 <span data-ttu-id="763ed-110">下節描述的文法規格，使用針對 EXECQUERY 作業[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="763ed-110">The following section describes the grammar specifications for using the EXECQUERY operation against the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
```  
EXECQUERY <QueryName> @USERGROUP='usergroup' [, @WORKSPACE='X'] [, @VARIANT='variant']   
[, @P1='<value 1>’] [, @P2='<value 2>'] ... [, @Pn = '<value n>'] [, @P1!='<value 3>'] [, @P1 > '<value 4>'] [, @P1 <= '<value 2>']   
[, NOT @P1 = '<value 2>'] [, NOT @P1 != '<value 2>'] [, NOT @P1 > '<value 2>']   
[, @P1 BETWEEN '<value 1>' AND '<value 2>'] [, NOT @P1 BETWEEN '<value 1>' AND '<value2>’]  
[OPTION 'USEORIGINALCOLUMNNAMES']  
  
```  
  
 <span data-ttu-id="763ed-111">其中：</span><span class="sxs-lookup"><span data-stu-id="763ed-111">where:</span></span>  
  
-   <span data-ttu-id="763ed-112">**\<QueryName\>**  SAP 系統中所定義之查詢的名稱。</span><span class="sxs-lookup"><span data-stu-id="763ed-112">**\<QueryName\>** is the name of the query defined in the SAP system.</span></span>  
  
-   <span data-ttu-id="763ed-113">**USERGROUP**指的是用來定義查詢的使用者群組。</span><span class="sxs-lookup"><span data-stu-id="763ed-113">**USERGROUP** refers to the user group in which the query is defined.</span></span> <span data-ttu-id="763ed-114">這是強制參數。</span><span class="sxs-lookup"><span data-stu-id="763ed-114">This is a mandatory parameter.</span></span>  
  
-   <span data-ttu-id="763ed-115">**工作區**指的是用來定義查詢的工作區。</span><span class="sxs-lookup"><span data-stu-id="763ed-115">**WORKSPACE** refers to the workspace in which the query is defined.</span></span> <span data-ttu-id="763ed-116">SAP 中有兩個工作區，Standard 和全域。</span><span class="sxs-lookup"><span data-stu-id="763ed-116">In SAP, there are two workspaces—Standard and Global.</span></span> <span data-ttu-id="763ed-117">提供的空白處來指定 [標準] 工作區。</span><span class="sxs-lookup"><span data-stu-id="763ed-117">Provide an empty space to specify the Standard workspace.</span></span> <span data-ttu-id="763ed-118">提供`X`指定 [全域] 工作區。</span><span class="sxs-lookup"><span data-stu-id="763ed-118">Provide `X` to specify the Global workspace.</span></span> <span data-ttu-id="763ed-119">預設值是空的空間。</span><span class="sxs-lookup"><span data-stu-id="763ed-119">Default is empty space.</span></span>  
  
-   <span data-ttu-id="763ed-120">**VARIANT**指的是一組儲存執行 SAP 查詢時，您可以指定的選取準則。</span><span class="sxs-lookup"><span data-stu-id="763ed-120">**VARIANT** refers to a saved set of selection criteria that you can specify while executing an SAP query.</span></span> <span data-ttu-id="763ed-121">例如，您可以使用變數來指定查詢的預設值。</span><span class="sxs-lookup"><span data-stu-id="763ed-121">For example, you can use variants to specify default values for queries.</span></span>  
  
-   <span data-ttu-id="763ed-122">**@Pn**n 是指<sup>th</sup> SAP 查詢定義中的選取項目欄位。</span><span class="sxs-lookup"><span data-stu-id="763ed-122">**@Pn** refers to the n<sup>th</sup> selection field in the SAP query definition.</span></span>  
  
-   <span data-ttu-id="763ed-123">**USEORIGINALCOLUMNNAMES**指定提供者是否使用原始的資料行名稱，在資料集中，它們在 SAP 系統中存在。</span><span class="sxs-lookup"><span data-stu-id="763ed-123">**USEORIGINALCOLUMNNAMES** specifies whether the provider uses the original column names in the DataSet, as they exist in the SAP system.</span></span> <span data-ttu-id="763ed-124">根據預設，提供者會使用 SAP 查詢中所定義的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="763ed-124">By default, the provider uses the friendly names defined in the SAP query.</span></span> <span data-ttu-id="763ed-125">不過，如果查詢中的易記名稱不是唯一的 ADO.NET 用戶端將會擲回錯誤時從資料集讀取資料。</span><span class="sxs-lookup"><span data-stu-id="763ed-125">However, if the friendly names within the query are not unique, the ADO.NET client will throw an error while reading the data from the DataSet.</span></span> <span data-ttu-id="763ed-126">在這種情況下，您必須指定 USEORIGINALCOLUMNNAMES 選項，指出提供者會使用原始的資料行名稱，資料集內。</span><span class="sxs-lookup"><span data-stu-id="763ed-126">In such scenarios, you must specify the USEORIGINALCOLUMNNAMES option, indicating that the provider uses the original column names in the DataSet.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="763ed-127">您必須一律提供值選項關鍵字在單引號中，例如，'*USEORIGINALCOLUMNNAMES*'。</span><span class="sxs-lookup"><span data-stu-id="763ed-127">You must always provide the value for the OPTION keyword within single quotes, for example, '*USEORIGINALCOLUMNNAMES*'.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="763ed-128">SAP 查詢的參數如何轉譯成 EXECQUERY 語法的相關資訊，請參閱[轉譯 SAP 查詢參數為 EXECQUERY 命令](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md)。</span><span class="sxs-lookup"><span data-stu-id="763ed-128">For information about how the parameters of an SAP Query translate into an EXECQUERY syntax, see [Translate SAP query parameters into EXECQUERY command](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).</span></span>  
  
### <a name="framing-an-execquery-syntax"></a><span data-ttu-id="763ed-129">框架 EXECQUERY 語法</span><span class="sxs-lookup"><span data-stu-id="763ed-129">Framing an EXECQUERY Syntax</span></span>  
 <span data-ttu-id="763ed-130">框架 EXECQUERY 作業，以執行 SAP 查詢的語法，取決於查詢中的 SAP 系統，包括在 SAP 中定義的每個參數值的定義方式。</span><span class="sxs-lookup"><span data-stu-id="763ed-130">Framing syntax for an EXECQUERY operation to execute an SAP query depends on how the query is defined in the SAP system, including each parameter value defined in SAP.</span></span> <span data-ttu-id="763ed-131">如需如何框架 EXECQUERY 執行 SAP 查詢的語法資訊，請參閱[轉譯 SAP 查詢參數為 EXECQUERY 命令](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md)。</span><span class="sxs-lookup"><span data-stu-id="763ed-131">For information about how to frame EXECQUERY syntax to execute an SAP query, see [Translate SAP query parameters into EXECQUERY command](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).</span></span>  
  
### <a name="additional-considerations-while-using-the-execquery-operation"></a><span data-ttu-id="763ed-132">其他考量而使用 EXECQUERY 作業</span><span class="sxs-lookup"><span data-stu-id="763ed-132">Additional Considerations While Using the EXECQUERY operation</span></span>  
 <span data-ttu-id="763ed-133">此區段會列出使用 EXECQUERY 陳述式使用時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="763ed-133">This section lists the points that you must keep in mind when using the EXECQUERY statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
-   <span data-ttu-id="763ed-134">USERGROUP、 工作區中，以及變數所指定的值做為傳遞的標準 SAP RFC RSAQ_REMOTE_QUERY_CALL 是。</span><span class="sxs-lookup"><span data-stu-id="763ed-134">The values specified for USERGROUP, WORKSPACE, and VARIANT are passed on as-is to the standard SAP RFC, RSAQ_REMOTE_QUERY_CALL.</span></span> <span data-ttu-id="763ed-135">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不會驗證指定這些參數的值。</span><span class="sxs-lookup"><span data-stu-id="763ed-135">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not validate the values specified for these parameters.</span></span>  
  
-   <span data-ttu-id="763ed-136">EXECQUERY 作業所傳回的所有值都都是字串型別。</span><span class="sxs-lookup"><span data-stu-id="763ed-136">All values returned by the EXECQUERY operation are of string type.</span></span>  
  
-   <span data-ttu-id="763ed-137">查詢名稱、 使用者群組、 工作區中，而且變異的關鍵字不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="763ed-137">Keywords for query names, user group, workspace, and variants are not case sensitive.</span></span> <span data-ttu-id="763ed-138">不過，參數名稱中都必須上方 caseP 例如@P1，@P2等等。例如：</span><span class="sxs-lookup"><span data-stu-id="763ed-138">However, the parameter names must always be in upper caseP such as @P1, @P2, etc. For example:</span></span>  
  
    ```  
    EXECQUERY xyz USERGROUP=’mygrp’, NOT @P1= 'somevalue'  
    ```  
  
     <span data-ttu-id="763ed-139">等同於</span><span class="sxs-lookup"><span data-stu-id="763ed-139">is the same as</span></span>  
  
    ```  
    EXECQUERY xyz uSERgROUP=’mygrp’, NOT @P1= 'somevalue'  
    ```  
  
-   <span data-ttu-id="763ed-140">EXECQUERY 所支援的運算子為 >，<>、 =、 < =、 ！ =、 NOT、 BETWEEN 和。</span><span class="sxs-lookup"><span data-stu-id="763ed-140">The operators supported by the EXECQUERY are >, <, >=, <=, !=, NOT, and BETWEEN.</span></span>  
  
-   <span data-ttu-id="763ed-141">EXECQUERY 作業不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="763ed-141">Wildcard characters are not supported by the EXECQUERY operation.</span></span> <span data-ttu-id="763ed-142">例如，下列陳述式的預期的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="763ed-142">For example, the following statement gives the expected output:</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
     <span data-ttu-id="763ed-143">不過，相同的查詢執行時未使用萬用字元會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="763ed-143">However, the same query when executed with a wildcard character gives an error.</span></span> <span data-ttu-id="763ed-144">請注意，萬用字元來使用 **@P2** 。</span><span class="sxs-lookup"><span data-stu-id="763ed-144">Notice the use of wildcard characters for **@P2**.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = '*&*'  
    ```  
  
     <span data-ttu-id="763ed-145">在此範例中，您可能會收到錯誤，指出已找到任何資料。</span><span class="sxs-lookup"><span data-stu-id="763ed-145">In this example, you might get an error stating that no data was found.</span></span> <span data-ttu-id="763ed-146">這是因為查詢會搜尋**'\*&\*'**做為字串，並不考慮星號 （*） 做為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="763ed-146">This is because the query searches for **'\*&\*'** as a string and does not consider asterisk (*) as a wildcard character.</span></span>  
  
-   <span data-ttu-id="763ed-147">您永遠必須指定日期值格式為 YYYYMMDD。</span><span class="sxs-lookup"><span data-stu-id="763ed-147">You must always specify a date values in YYYYMMDD format.</span></span>  
  
-   <span data-ttu-id="763ed-148">如果您執行的具有 variant SAP 系統中定義的查詢，您可以指定之變數的名稱做為命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="763ed-148">If you are executing a query that has a variant defined in the SAP system, you can specify the name of the variant as part of the command.</span></span> <span data-ttu-id="763ed-149">例如：</span><span class="sxs-lookup"><span data-stu-id="763ed-149">For example:</span></span>  
  
    ```  
    EXECQUERY myquery @usergroup='mygroup',@variant = 'variant1'  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="763ed-150">您不需要指定變數的名稱，如果預設 variant SAP 系統中定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="763ed-150">You do not need to specify a variant name if a default variant is defined for the query in the SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763ed-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="763ed-151">See Also</span></span>  
 [<span data-ttu-id="763ed-152">使用 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="763ed-152">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)