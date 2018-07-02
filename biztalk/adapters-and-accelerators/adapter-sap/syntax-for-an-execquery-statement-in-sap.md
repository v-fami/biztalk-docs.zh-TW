---
title: 在 SAP 中 EXECQUERY 陳述式的語法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99bd7fbb-64f2-4327-a8ae-ccb574e56150
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccf479438a5b0960a66b35ef7946df63d088284b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982015"
---
# <a name="syntax-for-an-execquery-statement-in-sap"></a><span data-ttu-id="77719-102">在 SAP 中 EXECQUERY 陳述式的語法</span><span class="sxs-lookup"><span data-stu-id="77719-102">Syntax for an EXECQUERY Statement in SAP</span></span>
<span data-ttu-id="77719-103">您可以使用 SAP GUI 來建立查詢，以圖形方式選取您想要查詢之資料行和排序的次序，您想要包含在結果集等資料表。[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可讓使用者從 ADO.NET 應用程式中執行這類查詢，藉由提供使用者可用來執行 SAP 系統中定義的查詢 EXECQUERY 作業。</span><span class="sxs-lookup"><span data-stu-id="77719-103">You can use the SAP GUI to create queries by graphically selecting the tables you want to query, the columns and sort order you want included in the result set, etc. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] enables users to execute such queries from an ADO.NET application by providing an EXECQUERY operation that users can use to execute a query defined in the SAP system.</span></span>  
  
 <span data-ttu-id="77719-104">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用自訂的 RFC Z_EXECUTE_SAP_QUERY SAP 系統中執行的預先定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="77719-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC Z_EXECUTE_SAP_QUERY to execute the pre-defined queries in the SAP system.</span></span> <span data-ttu-id="77719-105">自訂 RFC 依次執行 RSAQ_REMOTE_QUERY_CALL，這是 SAP 系統中定義的 RFC 的標準。</span><span class="sxs-lookup"><span data-stu-id="77719-105">The custom RFC in turn executes the RSAQ_REMOTE_QUERY_CALL, which is a standard RFC defined in the SAP system.</span></span> <span data-ttu-id="77719-106">因此，您可以使用 EXECQUERY 作業之前，您必須安裝自訂 RFC 的 SAP 系統，您將執行針對查詢中。</span><span class="sxs-lookup"><span data-stu-id="77719-106">Hence, before you can use the EXECQUERY operation, you must install the custom RFC in the SAP system you will be running your queries against.</span></span> <span data-ttu-id="77719-107">如需有關如何安裝自訂 RFC 的指示，請參閱 <<c0> [ 安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="77719-107">For instructions on how to install the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
 <span data-ttu-id="77719-108">本主題提供 EXECQUERY 作業和其他有用的資訊與 EXECQUERY 作業相關的語法資訊。</span><span class="sxs-lookup"><span data-stu-id="77719-108">This topic provides information on the syntax of the EXECQUERY operation, and other useful information related to the EXECQUERY operation.</span></span>  
  
## <a name="syntax-for-an-execquery-statement"></a><span data-ttu-id="77719-109">EXECQUERY 陳述式的語法</span><span class="sxs-lookup"><span data-stu-id="77719-109">Syntax for an EXECQUERY Statement</span></span>  
 <span data-ttu-id="77719-110">下節描述的文法規格使用 EXECQUERY 作業[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77719-110">The following section describes the grammar specifications for using the EXECQUERY operation against the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
```  
EXECQUERY <QueryName> @USERGROUP='usergroup' [, @WORKSPACE='X'] [, @VARIANT='variant']   
[, @P1='<value 1>’] [, @P2='<value 2>'] ... [, @Pn = '<value n>'] [, @P1!='<value 3>'] [, @P1 > '<value 4>'] [, @P1 <= '<value 2>']   
[, NOT @P1 = '<value 2>'] [, NOT @P1 != '<value 2>'] [, NOT @P1 > '<value 2>']   
[, @P1 BETWEEN '<value 1>' AND '<value 2>'] [, NOT @P1 BETWEEN '<value 1>' AND '<value2>’]  
[OPTION 'USEORIGINALCOLUMNNAMES']  
  
```  
  
 <span data-ttu-id="77719-111">其中：</span><span class="sxs-lookup"><span data-stu-id="77719-111">where:</span></span>  
  
- <span data-ttu-id="77719-112">**\<QueryName\>** 是 SAP 系統中定義的查詢名稱。</span><span class="sxs-lookup"><span data-stu-id="77719-112">**\<QueryName\>** is the name of the query defined in the SAP system.</span></span>  
  
- <span data-ttu-id="77719-113">**USERGROUP**指的是在其中定義查詢的使用者群組。</span><span class="sxs-lookup"><span data-stu-id="77719-113">**USERGROUP** refers to the user group in which the query is defined.</span></span> <span data-ttu-id="77719-114">這是強制參數。</span><span class="sxs-lookup"><span data-stu-id="77719-114">This is a mandatory parameter.</span></span>  
  
- <span data-ttu-id="77719-115">**工作區**指的是在其中定義查詢的工作區。</span><span class="sxs-lookup"><span data-stu-id="77719-115">**WORKSPACE** refers to the workspace in which the query is defined.</span></span> <span data-ttu-id="77719-116">在 SAP 中，有兩個工作區，標準和全域。</span><span class="sxs-lookup"><span data-stu-id="77719-116">In SAP, there are two workspaces—Standard and Global.</span></span> <span data-ttu-id="77719-117">提供空白空間，以指定的標準工作區。</span><span class="sxs-lookup"><span data-stu-id="77719-117">Provide an empty space to specify the Standard workspace.</span></span> <span data-ttu-id="77719-118">提供`X`指定通用的工作區。</span><span class="sxs-lookup"><span data-stu-id="77719-118">Provide `X` to specify the Global workspace.</span></span> <span data-ttu-id="77719-119">預設值是空的空間。</span><span class="sxs-lookup"><span data-stu-id="77719-119">Default is empty space.</span></span>  
  
- <span data-ttu-id="77719-120">**VARIANT**指的是一組儲存執行 SAP 查詢時，您可以指定的選取準則。</span><span class="sxs-lookup"><span data-stu-id="77719-120">**VARIANT** refers to a saved set of selection criteria that you can specify while executing an SAP query.</span></span> <span data-ttu-id="77719-121">比方說，您可以使用變數來指定查詢的預設值。</span><span class="sxs-lookup"><span data-stu-id="77719-121">For example, you can use variants to specify default values for queries.</span></span>  
  
- <span data-ttu-id="77719-122"><strong>@Pn</strong> n 是指<sup>th</sup> SAP 查詢定義中的選取項目欄位。</span><span class="sxs-lookup"><span data-stu-id="77719-122"><strong>@Pn</strong> refers to the n<sup>th</sup> selection field in the SAP query definition.</span></span>  
  
- <span data-ttu-id="77719-123">**USEORIGINALCOLUMNNAMES**指定提供者是否會使用原始的資料行名稱，在資料集中，因為它們存在於 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="77719-123">**USEORIGINALCOLUMNNAMES** specifies whether the provider uses the original column names in the DataSet, as they exist in the SAP system.</span></span> <span data-ttu-id="77719-124">根據預設，提供者會使用 SAP 查詢中所定義的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="77719-124">By default, the provider uses the friendly names defined in the SAP query.</span></span> <span data-ttu-id="77719-125">不過，如果在查詢中的易記名稱不是唯一的 ADO.NET 用戶端會擲回錯誤時讀取資料集的資料。</span><span class="sxs-lookup"><span data-stu-id="77719-125">However, if the friendly names within the query are not unique, the ADO.NET client will throw an error while reading the data from the DataSet.</span></span> <span data-ttu-id="77719-126">在此情況下，您必須指定 USEORIGINALCOLUMNNAMES 選項，表示提供者會在資料集中使用的原始資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="77719-126">In such scenarios, you must specify the USEORIGINALCOLUMNNAMES option, indicating that the provider uses the original column names in the DataSet.</span></span>  
  
  > [!IMPORTANT]
  >  <span data-ttu-id="77719-127">您必須永遠提供值選項關鍵字在單引號中，例如，'*USEORIGINALCOLUMNNAMES*'。</span><span class="sxs-lookup"><span data-stu-id="77719-127">You must always provide the value for the OPTION keyword within single quotes, for example, '*USEORIGINALCOLUMNNAMES*'.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77719-128">如需如何將 SAP 查詢的參數轉譯為 EXECQUERY 語法資訊，請參閱[轉譯 SAP 查詢參數為 EXECQUERY 命令](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md)。</span><span class="sxs-lookup"><span data-stu-id="77719-128">For information about how the parameters of an SAP Query translate into an EXECQUERY syntax, see [Translate SAP query parameters into EXECQUERY command](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).</span></span>  
  
### <a name="framing-an-execquery-syntax"></a><span data-ttu-id="77719-129">框架 EXECQUERY 語法</span><span class="sxs-lookup"><span data-stu-id="77719-129">Framing an EXECQUERY Syntax</span></span>  
 <span data-ttu-id="77719-130">框架 EXECQUERY 作業來執行 SAP 查詢的語法，取決於 SAP 系統，包括在 SAP 中定義每個參數值中定義查詢的方式。</span><span class="sxs-lookup"><span data-stu-id="77719-130">Framing syntax for an EXECQUERY operation to execute an SAP query depends on how the query is defined in the SAP system, including each parameter value defined in SAP.</span></span> <span data-ttu-id="77719-131">如需如何執行 SAP 查詢的 EXECQUERY 語法資訊，請參閱[轉譯 SAP 查詢參數為 EXECQUERY 命令](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md)。</span><span class="sxs-lookup"><span data-stu-id="77719-131">For information about how to frame EXECQUERY syntax to execute an SAP query, see [Translate SAP query parameters into EXECQUERY command](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).</span></span>  
  
### <a name="additional-considerations-while-using-the-execquery-operation"></a><span data-ttu-id="77719-132">其他考量而使用 EXECQUERY 作業</span><span class="sxs-lookup"><span data-stu-id="77719-132">Additional Considerations While Using the EXECQUERY operation</span></span>  
 <span data-ttu-id="77719-133">此區段會列出使用 EXECQUERY 陳述式時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77719-133">This section lists the points that you must keep in mind when using the EXECQUERY statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
- <span data-ttu-id="77719-134">指定使用者群組、 工作區中和 VARIANT 的值會傳遞做為標準 SAP RFC RSAQ_REMOTE_QUERY_CALL 是。</span><span class="sxs-lookup"><span data-stu-id="77719-134">The values specified for USERGROUP, WORKSPACE, and VARIANT are passed on as-is to the standard SAP RFC, RSAQ_REMOTE_QUERY_CALL.</span></span> <span data-ttu-id="77719-135">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不會驗證指定這些參數的值。</span><span class="sxs-lookup"><span data-stu-id="77719-135">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not validate the values specified for these parameters.</span></span>  
  
- <span data-ttu-id="77719-136">EXECQUERY 作業所傳回的所有值都都屬於字串類型。</span><span class="sxs-lookup"><span data-stu-id="77719-136">All values returned by the EXECQUERY operation are of string type.</span></span>  
  
- <span data-ttu-id="77719-137">查詢名稱、 使用者群組、 工作區中和變化的關鍵字不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="77719-137">Keywords for query names, user group, workspace, and variants are not case sensitive.</span></span> <span data-ttu-id="77719-138">不過，參數名稱必須一律位於上方 caseP 這類@P1，@P2等等。例如：</span><span class="sxs-lookup"><span data-stu-id="77719-138">However, the parameter names must always be in upper caseP such as @P1, @P2, etc. For example:</span></span>  
  
  ```  
  EXECQUERY xyz USERGROUP=’mygrp’, NOT @P1= 'somevalue'  
  ```  
  
   <span data-ttu-id="77719-139">等同於</span><span class="sxs-lookup"><span data-stu-id="77719-139">is the same as</span></span>  
  
  ```  
  EXECQUERY xyz uSERgROUP=’mygrp’, NOT @P1= 'somevalue'  
  ```  
  
- <span data-ttu-id="77719-140">EXECQUERY 所支援的運算子為 >，<>、 =、 < =、 ！ =、 NOT、 BETWEEN 和。</span><span class="sxs-lookup"><span data-stu-id="77719-140">The operators supported by the EXECQUERY are >, <, >=, <=, !=, NOT, and BETWEEN.</span></span>  
  
- <span data-ttu-id="77719-141">EXECQUERY 作業不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="77719-141">Wildcard characters are not supported by the EXECQUERY operation.</span></span> <span data-ttu-id="77719-142">例如，下列陳述式會提供預期的輸出：</span><span class="sxs-lookup"><span data-stu-id="77719-142">For example, the following statement gives the expected output:</span></span>  
  
  ```  
  EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
  ```  
  
   <span data-ttu-id="77719-143">不過，相同的查詢執行時未使用萬用字元會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="77719-143">However, the same query when executed with a wildcard character gives an error.</span></span> <span data-ttu-id="77719-144">請注意，使用萬用字元<strong>@P2</strong>。</span><span class="sxs-lookup"><span data-stu-id="77719-144">Notice the use of wildcard characters for <strong>@P2</strong>.</span></span>  
  
  ```  
  EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = '*&*'  
  ```  
  
   <span data-ttu-id="77719-145">在此範例中，您可能會收到錯誤訊息指出找不資料。</span><span class="sxs-lookup"><span data-stu-id="77719-145">In this example, you might get an error stating that no data was found.</span></span> <span data-ttu-id="77719-146">這是因為查詢會搜尋 **'\*&\*'** 做為字串並不會視為星號 （\*） 做為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="77719-146">This is because the query searches for **'\*&\*'** as a string and does not consider asterisk (\*) as a wildcard character.</span></span>  
  
- <span data-ttu-id="77719-147">您一律必須指定日期值格式為 YYYYMMDD。</span><span class="sxs-lookup"><span data-stu-id="77719-147">You must always specify a date values in YYYYMMDD format.</span></span>  
  
- <span data-ttu-id="77719-148">如果您執行的具有 variant，SAP 系統中定義的查詢，您可以指定之變數的名稱做為命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="77719-148">If you are executing a query that has a variant defined in the SAP system, you can specify the name of the variant as part of the command.</span></span> <span data-ttu-id="77719-149">例如：</span><span class="sxs-lookup"><span data-stu-id="77719-149">For example:</span></span>  
  
  ```  
  EXECQUERY myquery @usergroup='mygroup',@variant = 'variant1'  
  ```  
  
  > [!NOTE]
  >  <span data-ttu-id="77719-150">您不需要指定變數的名稱，如果預設變數，會在 SAP 系統中定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="77719-150">You do not need to specify a variant name if a default variant is defined for the query in the SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77719-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77719-151">See Also</span></span>  
 [<span data-ttu-id="77719-152">使用 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="77719-152">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)