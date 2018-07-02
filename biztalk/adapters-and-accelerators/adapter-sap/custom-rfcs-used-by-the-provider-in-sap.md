---
title: 在 SAP 中的提供者所使用的自訂 Rfc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Z_EXTRACT_DATA_OO, limitations related to
- RFC, Z_EXTRACT_DATA_OO
- Z_EXTRACT_DATA_OO
- Z_EXTRACT_DATA_OO, best practice
- Z_EXTRACT_DATA_OO, security issue
ms.assetid: 95661f4c-0431-40ca-8a53-3fbe359b8afd
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36b359fc893b8616fd4fb7339e9efbc42d7d3e13
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992719"
---
# <a name="custom-rfcs-used-by-the-provider-in-sap"></a><span data-ttu-id="5e85b-102">在 SAP 中的提供者所使用的自訂 Rfc</span><span class="sxs-lookup"><span data-stu-id="5e85b-102">Custom RFCs Used by the Provider in SAP</span></span>
<span data-ttu-id="5e85b-103">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]提供下列自訂 Rfc，在內部用來執行 SAP 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="5e85b-103">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] provides the following custom RFCs that it internally uses to perform operations on the SAP system.</span></span>  
  
- <span data-ttu-id="5e85b-104">**Z_EXTRACT_DATA_OO RFC**。</span><span class="sxs-lookup"><span data-stu-id="5e85b-104">**Z_EXTRACT_DATA_OO RFC**.</span></span> <span data-ttu-id="5e85b-105">資料擷取 RFC，Z_EXTRACT_DATA_OO，會從資料表擷取資料或檢視中的 SAP R/3 系統、 將轉換的資料，並傳回同步中的 SQL Server 資料表的資料或傾印到一般檔案資料。</span><span class="sxs-lookup"><span data-stu-id="5e85b-105">The data extraction RFC, Z_EXTRACT_DATA_OO, extracts data from tables or views in the SAP R/3 system, converts the data, and either returns the data synchronously in a SQL Server table or dumps data to a flat file.</span></span> <span data-ttu-id="5e85b-106">Z_EXTRACT_DATA_OO 用來執行與 WHERE 子句的 SELECT 作業。</span><span class="sxs-lookup"><span data-stu-id="5e85b-106">The Z_EXTRACT_DATA_OO is used to perform SELECT operation with WHERE clauses.</span></span> <span data-ttu-id="5e85b-107">這個 RFC 的效能是您 SAP 系統的硬體而定。</span><span class="sxs-lookup"><span data-stu-id="5e85b-107">The performance of this RFC is dependent on your SAP system hardware.</span></span>  
  
   <span data-ttu-id="5e85b-108">如需如何將.NET 和 SAP 資料型別對應的 Z_EXTRACT_DATA_OO RFC 資訊，請參閱[Data Type Mapping for 自訂 Rfc](../../adapters-and-accelerators/adapter-sap/data-type-mapping-for-custom-rfcs.md)。</span><span class="sxs-lookup"><span data-stu-id="5e85b-108">For information on how the .NET and SAP data types are mapped for Z_EXTRACT_DATA_OO RFC, see [Data Type Mapping for Custom RFCs](../../adapters-and-accelerators/adapter-sap/data-type-mapping-for-custom-rfcs.md).</span></span>  
  
- <span data-ttu-id="5e85b-109">**Z_EXECUTE_SAP_QUERY RFC**。</span><span class="sxs-lookup"><span data-stu-id="5e85b-109">**Z_EXECUTE_SAP_QUERY RFC**.</span></span> <span data-ttu-id="5e85b-110">使用這個 RFC[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]來執行 SAP 系統中已定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="5e85b-110">This RFC is used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] to execute queries that are already defined in the SAP system.</span></span> <span data-ttu-id="5e85b-111">這個 RFC 會在內部執行的 SAP RFC，RSAQ_REMOTE_QUERY_CALL。</span><span class="sxs-lookup"><span data-stu-id="5e85b-111">This RFC internally executes the SAP RFC, RSAQ_REMOTE_QUERY_CALL.</span></span> <span data-ttu-id="5e85b-112">SAP 查詢是以圖形方式建立所選取資料表、 資料行、 輸入的參數，結果集等的排序順序中使用 SAP GUI 的查詢。使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]您現在可以執行這類 SAP 查詢從 ADO.NET 用戶端。</span><span class="sxs-lookup"><span data-stu-id="5e85b-112">SAP queries are queries that are graphically created using the SAP GUI by selecting the tables, columns, input parameters, sort order of the result set, etc. Using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] you can now execute such SAP queries from an ADO.NET client.</span></span>  
  
   <span data-ttu-id="5e85b-113">EXECQUERY 作業所傳回的所有值都都屬於字串類型。</span><span class="sxs-lookup"><span data-stu-id="5e85b-113">All values returned by the EXECQUERY operation are of string type.</span></span>  
  
## <a name="limitations-related-to-the-zextractdataoo-rfc"></a><span data-ttu-id="5e85b-114">有關 Z_EXTRACT_DATA_OO RFC 的限制</span><span class="sxs-lookup"><span data-stu-id="5e85b-114">Limitations Related to the Z_EXTRACT_DATA_OO RFC</span></span>  
  
-   <span data-ttu-id="5e85b-115">Z_EXTRACT_DATA_OO RFC 支援滿足下列條件的資料表中讀取資料：</span><span class="sxs-lookup"><span data-stu-id="5e85b-115">The Z_EXTRACT_DATA_OO RFC supports reading data from tables that satisfy the following conditions:</span></span>  
  
    -   <span data-ttu-id="5e85b-116">資料表的 TabClass 是 TRANSP、 叢集或集區。</span><span class="sxs-lookup"><span data-stu-id="5e85b-116">TabClass for the table is TRANSP, CUSTER, or POOL.</span></span>  
  
    -   <span data-ttu-id="5e85b-117">TabClass 檢視而 ViewClass D 或 p。</span><span class="sxs-lookup"><span data-stu-id="5e85b-117">TabClass is VIEW and ViewClass is either D or P.</span></span>  
  
-   <span data-ttu-id="5e85b-118">Z_EXTRACT_DATA_OO 不支援 HR 叢集資料表，例如 PCL1、 PCL2、 PCL3、 PCL4、 PCL5。</span><span class="sxs-lookup"><span data-stu-id="5e85b-118">Z_EXTRACT_DATA_OO does not support HR cluster tables, for example PCL1, PCL2, PCL3, PCL4, PCL5.</span></span>  
  
-   <span data-ttu-id="5e85b-119">可以由 Z_EXTRACT_DATA_OO 擷取的資料列數目取決於 SAP 伺服器上的硬體資源。</span><span class="sxs-lookup"><span data-stu-id="5e85b-119">The number of rows that can be extracted by Z_EXTRACT_DATA_OO depends on the hardware resources on the SAP server.</span></span>  
  
-   <span data-ttu-id="5e85b-120">主索引鍵的順序，會傳回所有擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="5e85b-120">All extracted data is returned in order of the primary keys.</span></span>  
  
-   <span data-ttu-id="5e85b-121">不支援資料表或檢視表包含字串、 SSTRING 和 RAWSTRING 可變長度資料類型。</span><span class="sxs-lookup"><span data-stu-id="5e85b-121">Tables or views containing the variable-length data types STRING, SSTRING and RAWSTRING are not supported.</span></span> <span data-ttu-id="5e85b-122">無法擷取資料表或檢視表包含這些資料類型。</span><span class="sxs-lookup"><span data-stu-id="5e85b-122">Tables or views containing these data types cannot be extracted.</span></span>  
  
-   <span data-ttu-id="5e85b-123">Z_EXTRACT_DATA_OO 執行轉換結束已指派給他們的轉換結束的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="5e85b-123">Z_EXTRACT_DATA_OO runs conversion exits on all fields that have conversion exits assigned to them.</span></span> <span data-ttu-id="5e85b-124">在 SELECT 陳述式的 WHERE 子句中，就必須輸入產生的轉換的值。</span><span class="sxs-lookup"><span data-stu-id="5e85b-124">The resulting converted values must be entered in the WHERE clause of a SELECT statement.</span></span> <span data-ttu-id="5e85b-125">也會傳回已轉換的值。</span><span class="sxs-lookup"><span data-stu-id="5e85b-125">Converted values are also returned.</span></span> <span data-ttu-id="5e85b-126">這可能會造成 Z_EXTRACT_DATA_OO 所傳回的結果中的 SAP 資料瀏覽器 (SE16) 傳回的結果之間的不一致。</span><span class="sxs-lookup"><span data-stu-id="5e85b-126">This might cause inconsistencies between the results returned by Z_EXTRACT_DATA_OO and the results returned in the SAP data browser (SE16).</span></span>  
  
-   <span data-ttu-id="5e85b-127">選取的資料表不能包含是 ABAP （例如，連線） 中的保留的名稱的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="5e85b-127">Selected tables cannot contain field names that are reserved names in ABAP (for example, CONNECTION).</span></span>  
  
-   <span data-ttu-id="5e85b-128">由於 SAP R/3 4.6c，版本型別的整數欄位的值中的查詢處理器中的限制 INT4 必須大於或等於-999999999 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="5e85b-128">Due to a limitation in the query processor in SAP R/3 version 4.6C, values for integer fields of type INT4 must be greater than or equal to -999999999 in the WHERE clause.</span></span> <span data-ttu-id="5e85b-129">不論是否選取這個欄位包含值，將不會擷取 INT4 值小於-999999999 的資料列。</span><span class="sxs-lookup"><span data-stu-id="5e85b-129">Rows with INT4 values less than -999999999 will not be extracted regardless of whether the field containing the value is selected.</span></span>  
  
-   <span data-ttu-id="5e85b-130">SAP 系統 4.7 版或更新版本; 上執行時，會限制為 256 個字元的 WHERE 子句中的值的所有資料型別限制為在版本 4.6 c 的 70 個字元。</span><span class="sxs-lookup"><span data-stu-id="5e85b-130">Values for all data types in a WHERE clause are limited to 256 characters when executing on SAP system version 4.7 or greater; the limit is 70 characters in version 4.6c.</span></span> <span data-ttu-id="5e85b-131">未經處理的資料類型值，這些限制會變成一半 128 到 35 個字元，以分別。</span><span class="sxs-lookup"><span data-stu-id="5e85b-131">For RAW data type values, these limits are halved to 128 and 35 characters, respectively.</span></span> <span data-ttu-id="5e85b-132">如此一來傳回時在 RAW 和 LCHR 資料類型長度上沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="5e85b-132">There is no limit on RAW and LCHR data type length when they are returned as a result.</span></span>  
  
-   <span data-ttu-id="5e85b-133">在 SAP R/3 4.6c，版本欄位的 where 子句限於 70 個字元。</span><span class="sxs-lookup"><span data-stu-id="5e85b-133">In SAP R/3 version 4.6C, fields in the WHERE clause are limited to 70 characters.</span></span>  
  
-   <span data-ttu-id="5e85b-134">在 SAP R/3 4.6c 版本，無法擷取任何輸出長度大於 70 個字元的主索引鍵欄位的資料表。</span><span class="sxs-lookup"><span data-stu-id="5e85b-134">In SAP R/3 version 4.6C, any table with a primary key field that has an output length greater than 70 characters cannot be extracted.</span></span>  
  
-   <span data-ttu-id="5e85b-135">在 SAP R/3，版本 4.6 c，資料表和檢視表，包含可變長度資料類型 (`VARC`) 不支援，以及資料表和檢視包含不能從使用 Z_EXTRACT_DATA_OO 函式呼叫的資料來源中擷取這些資料類型。</span><span class="sxs-lookup"><span data-stu-id="5e85b-135">In SAP R/3, version 4.6c, tables and views that contain variable length data types (`VARC`) are not supported, and tables and views containing these data types cannot be extracted from the data source using the Z_EXTRACT_DATA_OO function call.</span></span>  
  
-   <span data-ttu-id="5e85b-136">在檔案模式中，Z_EXTRACT_DATA_OO 函式呼叫不會檢查是否為目的地檔案已經開啟時，本身或其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e85b-136">In file mode, the Z_EXTRACT_DATA_OO function call does not check whether a destination file is already opened, either by itself or by another application.</span></span> <span data-ttu-id="5e85b-137">因此，函式可以不正確地寫入開啟檔案時同時將資料附加到相同的檔案。</span><span class="sxs-lookup"><span data-stu-id="5e85b-137">Therefore, the function can incorrectly write to an open file while simultaneously appending data to the same file.</span></span> <span data-ttu-id="5e85b-138">不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="5e85b-138">No error is raised.</span></span>  
  
-   <span data-ttu-id="5e85b-139">在檔案模式中，Z_EXTRACT_DATA_OO 函式呼叫可覆寫現有檔案。</span><span class="sxs-lookup"><span data-stu-id="5e85b-139">In file mode, the Z_EXTRACT_DATA_OO function call can overwrite existing files.</span></span> <span data-ttu-id="5e85b-140">請確定使用 Z_EXTRACT_DATA_OO 的 SAP 使用者有限 S_DATASET 透過檔案系統存取。</span><span class="sxs-lookup"><span data-stu-id="5e85b-140">Ensure that SAP users who use Z_EXTRACT_DATA_OO have restricted file-system access by way of S_DATASET.</span></span>  
  
## <a name="security-considerations-with-the-custom-rfc"></a><span data-ttu-id="5e85b-141">自訂 rfc 的安全性考量</span><span class="sxs-lookup"><span data-stu-id="5e85b-141">Security Considerations with the Custom RFC</span></span>  
  
-   <span data-ttu-id="5e85b-142">`Security Issue`： 沒有可能公開 （expose） 如果您無法協助保護這些檔案會寫入至一般檔案的資料。</span><span class="sxs-lookup"><span data-stu-id="5e85b-142">`Security Issue`: There is potential to expose data that is written to flat files if you do not help protect those files.</span></span>  
  
     <span data-ttu-id="5e85b-143">`Best practice`： 改進 Z_EXTRACT_DATA_OO 函式呼叫，在一般的檔案模式中的任何資料會寫入至其中的檔案共用的安全性。</span><span class="sxs-lookup"><span data-stu-id="5e85b-143">`Best practice`: Improve the security of the file share to which any data is written by the Z_EXTRACT_DATA_OO function call in flat file mode.</span></span>  
  
-   <span data-ttu-id="5e85b-144">`Security Issue`： 沒有可能會覆寫任何會寫入至檔案模式中使用 Z_EXTRACT_DATA_OO 函式呼叫的共用上的檔案。</span><span class="sxs-lookup"><span data-stu-id="5e85b-144">`Security Issue`: There is the potential to overwrite files on any share that is written to using the Z_EXTRACT_DATA_OO function call in file mode.</span></span> <span data-ttu-id="5e85b-145">這可能會發生任何 SAP 網域帳戶有權存取的共用上的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="5e85b-145">This can occur to any file on any share to which the SAP domain account has access.</span></span>  
  
     <span data-ttu-id="5e85b-146">`Best practice`： 致力於保護 SAP 網域帳戶有權存取的所有共用。</span><span class="sxs-lookup"><span data-stu-id="5e85b-146">`Best practice`: Strive to protect all shares to which the SAP domain account has access.</span></span>  
  
-   <span data-ttu-id="5e85b-147">`Security Issue`： 使用者能夠檢查 （或 「 探查 」） 資料從 SAP 應用程式伺服器到其目標檔案共用的傳輸期間在目標為不同的實體機器上時的情況下。</span><span class="sxs-lookup"><span data-stu-id="5e85b-147">`Security Issue`: Users have the ability to inspect (or "sniff") data during transmission from an SAP application server to its target file share, in cases when the target is on a different physical machine.</span></span>  
  
     <span data-ttu-id="5e85b-148">`Best practice`： 使用 IPsec 或另一個適當的方法來協助讓通訊更加安全 SAP 伺服器與目標之間。</span><span class="sxs-lookup"><span data-stu-id="5e85b-148">`Best practice`: Use IPsec or another appropriate method to help make communication more secure between the SAP server and its targets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e85b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e85b-149">See Also</span></span>  
 [<span data-ttu-id="5e85b-150">關於 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="5e85b-150">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)