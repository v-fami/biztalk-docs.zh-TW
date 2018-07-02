---
title: 插入、 更新、 刪除或選取 使用 WCF 服務模型的 Oracle 資料庫中的 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, Delete operation
- WCF service model, Select operation
- WCF service model, Insert operation
- WCF service model, Update operation
ms.assetid: d1a9f44f-ea0b-4dd6-9489-fa0d963848c4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91fa9b1828a8519dcbf7e1efba1db99ba84f1d0d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982447"
---
# <a name="insert-update-delete-or-select-operations-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="d1a10-102">插入、 更新、 刪除或選取 使用 WCF 服務模型的 Oracle 資料庫中的 作業</span><span class="sxs-lookup"><span data-stu-id="d1a10-102">Insert, update, delete, or select operations in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="d1a10-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現一組基本 Insert、 Update、 Delete 和 Oracle 資料庫資料表和檢視表的 Select 作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces a set of basic Insert, Update, Delete, and Select operations on Oracle database tables and views.</span></span> <span data-ttu-id="d1a10-104">藉由使用這些作業，您可以執行簡單的 SQL INSERT、 UPDATE、 SELECT、 和 DELETE 陳述式 WHERE 子句的目標資料表或檢視上所限定。</span><span class="sxs-lookup"><span data-stu-id="d1a10-104">By using these operations, you can perform simple SQL INSERT, UPDATE, SELECT, and DELETE statements qualified by a WHERE clause on a target table or view.</span></span> <span data-ttu-id="d1a10-105">若要執行更複雜的作業，例如 SQL SELECT 查詢，會使用 JOIN 運算子，您可以使用 SQLEXECUTE 作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-105">To perform more complex operations, for example a SQL SELECT query that uses the JOIN operator, you can use the SQLEXECUTE operation.</span></span> <span data-ttu-id="d1a10-106">如需有關 LEXECUTE 作業的詳細資訊，請參閱[Oracle Database 中的 WCF 服務模型執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-106">For more information about the SQLEXECUTE operation, see [Performing a SQLEXECUTE Operation in Oracle Database Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="d1a10-107">下表摘要說明基本的 SQL 作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表和檢視表的介面。</span><span class="sxs-lookup"><span data-stu-id="d1a10-107">The following table summarizes the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces on tables and views.</span></span> <span data-ttu-id="d1a10-108">如需這些作業的完整說明，請參閱[基本 Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-108">For a complete description of these operations, see [Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span></span>  
  
|<span data-ttu-id="d1a10-109">作業</span><span class="sxs-lookup"><span data-stu-id="d1a10-109">Operation</span></span>|<span data-ttu-id="d1a10-110">描述</span><span class="sxs-lookup"><span data-stu-id="d1a10-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1a10-111">Insert</span><span class="sxs-lookup"><span data-stu-id="d1a10-111">Insert</span></span>|<span data-ttu-id="d1a10-112">插入作業支援多個記錄或大量插入到目標資料表或檢視表：</span><span class="sxs-lookup"><span data-stu-id="d1a10-112">The Insert operation supports multiple record or bulk inserts into the target table or view:</span></span><br /><br /> <span data-ttu-id="d1a10-113">-多個記錄插入作業會將資料列插入資料表或檢視，根據提供的記錄集。</span><span class="sxs-lookup"><span data-stu-id="d1a10-113">-   A multiple record Insert operation inserts rows into a table or view based on a supplied record set.</span></span><br /><span data-ttu-id="d1a10-114">-在大量插入作業會將資料列插入資料表或檢視，以提供 SQL SELECT 查詢和資料行的清單。</span><span class="sxs-lookup"><span data-stu-id="d1a10-114">-   A bulk Insert operation inserts rows into a table or view based on a supplied SQL SELECT query and column list.</span></span> <span data-ttu-id="d1a10-115">查詢所傳回的記錄插入目標資料表資料行清單為基礎。</span><span class="sxs-lookup"><span data-stu-id="d1a10-115">The records that the query returns are inserted into the target table based on the column list.</span></span>|  
|<span data-ttu-id="d1a10-116">Select</span><span class="sxs-lookup"><span data-stu-id="d1a10-116">Select</span></span>|<span data-ttu-id="d1a10-117">根據提供的清單之資料行名稱和篩選條件字串，指定 SQL WHERE 子句的目標資料表上執行 SQL SELECT 查詢。</span><span class="sxs-lookup"><span data-stu-id="d1a10-117">Performs a SQL SELECT query on the target table based on a supplied list of column names and a filter string that specifies a SQL WHERE clause.</span></span>|  
|<span data-ttu-id="d1a10-118">Update</span><span class="sxs-lookup"><span data-stu-id="d1a10-118">Update</span></span>|<span data-ttu-id="d1a10-119">目標資料表上執行更新。</span><span class="sxs-lookup"><span data-stu-id="d1a10-119">Performs an UPDATE on the target table.</span></span> <span data-ttu-id="d1a10-120">所指定 SQL WHERE 子句的篩選字串指定要更新的記錄。</span><span class="sxs-lookup"><span data-stu-id="d1a10-120">The records to be updated are specified by a filter string that specifies a SQL WHERE clause.</span></span> <span data-ttu-id="d1a10-121">在範本的記錄中指定的更新值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-121">The values for the update are specified in a template record.</span></span>|  
|<span data-ttu-id="d1a10-122">DELETE</span><span class="sxs-lookup"><span data-stu-id="d1a10-122">Delete</span></span>|<span data-ttu-id="d1a10-123">根據 SQL WHERE 子句的篩選條件字串中指定的目標資料表上執行刪除。</span><span class="sxs-lookup"><span data-stu-id="d1a10-123">Performs a DELETE on the target table based on a SQL WHERE clause that is specified in a filter string.</span></span>|  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="d1a10-124">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="d1a10-124">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="d1a10-125">本主題中的範例使用 /SCOTT/ACCOUNTACTIVITY 資料表。</span><span class="sxs-lookup"><span data-stu-id="d1a10-125">The examples in this topic use the /SCOTT/ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="d1a10-126">指令碼來產生此資料表會提供 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="d1a10-126">A script to generate this table is supplied with the SDK samples.</span></span> <span data-ttu-id="d1a10-127">如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-127">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="d1a10-128">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="d1a10-128">The WCF Client Class</span></span>  
 <span data-ttu-id="d1a10-129">WCF 用戶端的基本的 SQL 作業產生的名稱，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面為基礎的資料表或檢視，如同下表的名稱。</span><span class="sxs-lookup"><span data-stu-id="d1a10-129">The name of the WCF client generated for the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces is based on the name of the table or view, as in the following table.</span></span>  
  
|<span data-ttu-id="d1a10-130">Oracle 資料庫成品</span><span class="sxs-lookup"><span data-stu-id="d1a10-130">Oracle Database Artifact</span></span>|<span data-ttu-id="d1a10-131">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="d1a10-131">WCF Client Name</span></span>|  
|------------------------------|---------------------|  
|<span data-ttu-id="d1a10-132">Table</span><span class="sxs-lookup"><span data-stu-id="d1a10-132">Table</span></span>|<span data-ttu-id="d1a10-133">[結構描述]表格 [TABLE_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="d1a10-133">[SCHEMA]Table[TABLE_NAME]Client</span></span>|  
|<span data-ttu-id="d1a10-134">檢視</span><span class="sxs-lookup"><span data-stu-id="d1a10-134">View</span></span>|<span data-ttu-id="d1a10-135">[結構描述]檢視 [VIEW_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="d1a10-135">[SCHEMA]View[VIEW_NAME]Client</span></span>|  
  
 <span data-ttu-id="d1a10-136">[SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="d1a10-136">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="d1a10-137">[TABLE_NAME] = 資料表的名稱比方說，ACCOUNTACTIVITY。</span><span class="sxs-lookup"><span data-stu-id="d1a10-137">[TABLE_NAME] = The name of the table; for example, ACCOUNTACTIVITY.</span></span>  
  
 <span data-ttu-id="d1a10-138">[VIEW_NAME] = [] 檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="d1a10-138">[VIEW_NAME] = The name of the view.</span></span>  
  
 <span data-ttu-id="d1a10-139">下表顯示在資料表上的基本 SQL 作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="d1a10-139">The following table shows the method signatures for the basic SQL operations on a table.</span></span> <span data-ttu-id="d1a10-140">簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。</span><span class="sxs-lookup"><span data-stu-id="d1a10-140">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="d1a10-141">作業</span><span class="sxs-lookup"><span data-stu-id="d1a10-141">Operation</span></span>|<span data-ttu-id="d1a10-142">方法簽章</span><span class="sxs-lookup"><span data-stu-id="d1a10-142">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="d1a10-143">Insert</span><span class="sxs-lookup"><span data-stu-id="d1a10-143">Insert</span></span>|<span data-ttu-id="d1a10-144">長時間插入 ([TABLE_NS]。 [TABLE_NAME] RECORDINSERT [資料錄集，字串 COLUMN_NAMES，查詢字串);</span><span class="sxs-lookup"><span data-stu-id="d1a10-144">long Insert([TABLE_NS].[TABLE_NAME]RECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);</span></span>|  
|<span data-ttu-id="d1a10-145">Select</span><span class="sxs-lookup"><span data-stu-id="d1a10-145">Select</span></span>|<span data-ttu-id="d1a10-146">[TABLE_NS]。[名稱]RECORDSELECT [] 選取 （字串 COLUMN_NAMES，篩選條件的字串）;</span><span class="sxs-lookup"><span data-stu-id="d1a10-146">[TABLE_NS].[TABLE_NAME]RECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);</span></span>|  
|<span data-ttu-id="d1a10-147">Update</span><span class="sxs-lookup"><span data-stu-id="d1a10-147">Update</span></span>|<span data-ttu-id="d1a10-148">長時間更新 ([TABLE_NS]。 [TABLE_NAME] RECORDUPDATE 資料錄集，篩選條件的字串）;</span><span class="sxs-lookup"><span data-stu-id="d1a10-148">long Update([TABLE_NS].[TABLE_NAME]RECORDUPDATE RECORDSET, string FILTER);</span></span>|  
|<span data-ttu-id="d1a10-149">DELETE</span><span class="sxs-lookup"><span data-stu-id="d1a10-149">Delete</span></span>|<span data-ttu-id="d1a10-150">長時間刪除 （字串篩選條件）;</span><span class="sxs-lookup"><span data-stu-id="d1a10-150">Long Delete(string FILTER);</span></span>|  
  
 <span data-ttu-id="d1a10-151">[TABLE_NS] = 資料表的命名空間的名稱比方說，microsoft.lobservices.oracledb._2007._03.SCOTT。Table.ACCOUNTACTIVITY。</span><span class="sxs-lookup"><span data-stu-id="d1a10-151">[TABLE_NS] = The name of the table namespace; for example, microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.</span></span>  
  
 <span data-ttu-id="d1a10-152">[TABLE_NAME] = 資料表的名稱比方說，ACCOUNTACTIVITY。</span><span class="sxs-lookup"><span data-stu-id="d1a10-152">[TABLE_NAME] = The name of the table; for example, ACCOUNTACTIVITY.</span></span>  
  
 <span data-ttu-id="d1a10-153">Insert、 Update 和 Select 作業所使用的記錄類型都定義在資料表或檢視的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d1a10-153">The record types used by the Insert, Update, and Select operations are all defined in the table or view namespace.</span></span>  
  
 <span data-ttu-id="d1a10-154">下列程式碼示範 WCF 用戶端類別的方法簽章為 Delete、 Insert、 Select 和 Update 產生/SCOTT/ACCOUNTACTIVITY 資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-154">The following code shows the method signatures for a WCF client class generated for the Delete, Insert, Select and Update operations on the /SCOTT/ACCOUNTACTIVITY table.</span></span>  
  
```  
public partial class SCOTTTableACCOUNTACTIVITYClient : System.ServiceModel.ClientBase<SCOTTTableACCOUNTACTIVITY>, SCOTTTableACCOUNTACTIVITY {  
  
    public long Delete(string FILTER);  
  
    public long Insert(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);  
  
    public long Update(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE RECORDSET, string FILTER);  
}  
```  
  
## <a name="invoking-the-basic-sql-operations"></a><span data-ttu-id="d1a10-155">叫用基本的 SQL 作業</span><span class="sxs-lookup"><span data-stu-id="d1a10-155">Invoking the Basic SQL Operations</span></span>  
 <span data-ttu-id="d1a10-156">若要使用的 WCF 用戶端叫用資料表或檢視表的基本 SQL 作業，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="d1a10-156">To invoke the basic SQL operations on a table or view by using a WCF client, perform the following steps.</span></span>  
  
1. <span data-ttu-id="d1a10-157">產生 WCF 用戶端類別，針對目標資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="d1a10-157">Generate a WCF client class for the target table or view.</span></span> <span data-ttu-id="d1a10-158">這個類別應該包含您將會在目標成品叫用作業的方法。</span><span class="sxs-lookup"><span data-stu-id="d1a10-158">This class should contain methods for the operations that you will invoke on the target artifact.</span></span>  
  
2. <span data-ttu-id="d1a10-159">建立 WCF 用戶端類別的執行個體，並叫用其方法來執行資料表或檢視表上的作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-159">Create an instance of the WCF client class and invoke its methods to perform operations on the table or view.</span></span>  
  
   <span data-ttu-id="d1a10-160">如需詳細資訊，有關如何建立 WCF 用戶端類別，並在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 的 Oracle 資料庫配接器使用 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-160">For more detailed information about how to create a WCF client class and invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Overview of the WCF Service Model with the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span></span>  
  
   <span data-ttu-id="d1a10-161">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的 Oracle 資料庫上執行每個作業在交易內。</span><span class="sxs-lookup"><span data-stu-id="d1a10-161">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes each operation inside of a transaction on the Oracle database.</span></span> <span data-ttu-id="d1a10-162">您可以設定來控制此交易的隔離等級**TransactionIsolationLevel**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d1a10-162">You can control the isolation level of this transaction by setting the **TransactionIsolationLevel** binding property.</span></span> <span data-ttu-id="d1a10-163">如需詳細資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，請參閱[使用 BizTalk Adapter for Oracle 資料庫繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-163">For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Working with BizTalk Adapter for Oracle Database Binding Properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span>  
  
   <span data-ttu-id="d1a10-164">下列各節提供有關如何叫用每個基本的 SQL 作業，在您的程式碼的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d1a10-164">The following sections provide details about how to invoke each basic SQL operation in your code.</span></span>  
  
###  <a name="BKMK_InsertOperation"></a> <span data-ttu-id="d1a10-165">插入作業</span><span class="sxs-lookup"><span data-stu-id="d1a10-165">Insert Operation</span></span>  
 <span data-ttu-id="d1a10-166">下表顯示如何設定多個記錄插入的參數和大量插入作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-166">The following table shows how to set parameters for multiple record Insert and bulk Insert operations.</span></span>  
  
|<span data-ttu-id="d1a10-167">插入作業類型</span><span class="sxs-lookup"><span data-stu-id="d1a10-167">Insert operation type</span></span>|<span data-ttu-id="d1a10-168">資料錄集</span><span class="sxs-lookup"><span data-stu-id="d1a10-168">RECORDSET</span></span>|<span data-ttu-id="d1a10-169">COLUMN_NAMES</span><span class="sxs-lookup"><span data-stu-id="d1a10-169">COLUMN_NAMES</span></span>|<span data-ttu-id="d1a10-170">QUERY</span><span class="sxs-lookup"><span data-stu-id="d1a10-170">QUERY</span></span>|  
|---------------------------|---------------|-------------------|-----------|  
|<span data-ttu-id="d1a10-171">多個記錄</span><span class="sxs-lookup"><span data-stu-id="d1a10-171">Multiple record</span></span>|<span data-ttu-id="d1a10-172">應插入至目標的 INSERTRECORDS 的集合。</span><span class="sxs-lookup"><span data-stu-id="d1a10-172">A collection of INSERTRECORDS that should be inserted into the target.</span></span>|<span data-ttu-id="d1a10-173">null</span><span class="sxs-lookup"><span data-stu-id="d1a10-173">null</span></span>|<span data-ttu-id="d1a10-174">null</span><span class="sxs-lookup"><span data-stu-id="d1a10-174">null</span></span>|  
|<span data-ttu-id="d1a10-175">大量</span><span class="sxs-lookup"><span data-stu-id="d1a10-175">Bulk</span></span>|<span data-ttu-id="d1a10-176">null</span><span class="sxs-lookup"><span data-stu-id="d1a10-176">null</span></span>|<span data-ttu-id="d1a10-177">目標; 中的資料行名稱的逗號分隔清單例如，"TID，帳戶 」。</span><span class="sxs-lookup"><span data-stu-id="d1a10-177">A comma-delimited list of column names in the target; for example, "TID, ACCOUNT".</span></span> <span data-ttu-id="d1a10-178">資料行清單中指定查詢結果應該會放置在每個插入的資料列中的資料行。</span><span class="sxs-lookup"><span data-stu-id="d1a10-178">The column list specifies the columns into which the query results should be placed in each inserted row.</span></span> <span data-ttu-id="d1a10-179">查詢必須傳回符合指定的數目和類型的資料行清單中的資料行的結果集。</span><span class="sxs-lookup"><span data-stu-id="d1a10-179">The query must return a result set that matches the columns specified in the column list in both number and type.</span></span>|<span data-ttu-id="d1a10-180">在資料庫資料表或檢視傳回的結果集要插入至目標; 上的 SQL SELECT 查詢比方說，「 從 NEW_TRANSACTIONS WHERE 帳戶選取 （帳戶中的 TID） = 100001"。</span><span class="sxs-lookup"><span data-stu-id="d1a10-180">A SQL SELECT query on a database table or view that returns a result set to insert into the target; for example, "SELECT (TID, ACCOUNT) FROM NEW_TRANSACTIONS WHERE ACCOUNT = 100001".</span></span> <span data-ttu-id="d1a10-181">結果集必須符合在數目和類型的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="d1a10-181">The result set must match the column list in both number and type.</span></span>|  
  
 <span data-ttu-id="d1a10-182">插入作業傳回記錄插入至目標的數目。</span><span class="sxs-lookup"><span data-stu-id="d1a10-182">The Insert operation returns the number of records inserted into the target.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1a10-183">在 WCF 服務模型中，用於插入作業的記錄集是強型別。</span><span class="sxs-lookup"><span data-stu-id="d1a10-183">In the WCF service model, the record set used in the Insert operation is strongly-typed.</span></span> <span data-ttu-id="d1a10-184">您可以設定要 nillable 資料行的值**null**排除該資料行插入作業; 從記錄中不過，您無法設定的值非 nill 的資料行**null**。</span><span class="sxs-lookup"><span data-stu-id="d1a10-184">You can set the value of a nillable column to **null** in a record to exclude that column from the Insert operation; however, you cannot set the value of a non-nillable column to **null**.</span></span> <span data-ttu-id="d1a10-185">這表示，在多個記錄插入作業中，您必須提供每個記錄中的所有非 nill 的資料行值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-185">This means that in a multiple record Insert operation, you must supply values for all non-nillable columns in each record.</span></span> <span data-ttu-id="d1a10-186">此外，沒有資料流支援基本的 SQL 作業時使用 WCF 服務模型。</span><span class="sxs-lookup"><span data-stu-id="d1a10-186">In addition, there is no streaming support for the basic SQL operations when you use the WCF service model.</span></span> <span data-ttu-id="d1a10-187">如果您的多個記錄插入作業牽涉到大型的記錄集，這可能是很重要的考量。</span><span class="sxs-lookup"><span data-stu-id="d1a10-187">If your multiple record Insert operation involves a large record set, this may be an important consideration.</span></span> <span data-ttu-id="d1a10-188">如需詳細資訊，請參閱 <<c0> [ 叫用使用 WCF 服務模型的基本的 SQL 作業的限制](#BKMK_LimitationsInvoking)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-188">For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).</span></span>  
  
 <span data-ttu-id="d1a10-189">下列程式碼顯示的多個記錄插入作業 （兩筆記錄） 為目標的 ACCOUNTACTIVITY 資料表。</span><span class="sxs-lookup"><span data-stu-id="d1a10-189">The following code shows a multiple record Insert operation (two records) that targets the ACCOUNTACTIVITY table.</span></span>  
  
```  
// Insert records  
                using (SCOTTTableACCOUNTACTIVITYClient aaTableClient =   
                    new SCOTTTableACCOUNTACTIVITYClient("OracleDBBinding_SCOTT.Table.ACCOUNTACTIVITY"))  
                {  
                    long recsInserted;  
  
                    aaTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
                    aaTableClient.ClientCredentials.UserName.Password = "TIGER";  
  
                    try  
                    {  
                        aaTableClient.Open();  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    // Do a multiple record Insert of 2 records for account 100001  
  
                    microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] insertRecs =  
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[2];  
  
                                  TID__COMPLEX_TYPE tid = new TID__COMPLEX_TYPE();  
                                  tid.InlineValue = "tidSequence.NextVal()";  
  
                                  ACCOUNT__COMPLEX_TYPE account = new ACCOUNT__COMPLEX_TYPE();  
                                  account.Value = 100001;  
  
                    AMOUNT__COMPLEX_TYPE amount = new AMOUNT__COMPLEX_TYPE();  
                    amount.Value = 400;  
  
                    TRANSDATE__COMPLEX_TYPE transdate = new TRANSDATE__COMPLEX_TYPE();  
                    transdate.Value = DateTime.Now.Date;  
  
                    PROCESSED__COMPLEX_TYPE processed = new PROCESSED__COMPLEX_TYPE();  
                    processed.Value = "n";  
  
                    DESCRIPTION__COMPLEX_TYPE description1 = new DESCRIPTION__COMPLEX_TYPE();  
                    description1.Value = "Inserted Record #1";  
  
                    DESCRIPTION__COMPLEX_TYPE description2 = new DESCRIPTION__COMPLEX_TYPE();  
                    description2.Value = "Inserted Record #2";  
  
                    insertRecs[0] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[0].TID = tid;  
                    insertRecs[0].ACCOUNT = account;  
                    insertRecs[0].AMOUNT = amount;  
                    insertRecs[0].TRANSDATE = transdate;  
                    insertRecs[0].DESCRIPTION = description1;  
                    insertRecs[0].PROCESSED = processed;  
  
                    insertRecs[1] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[1].TID = tid;  
                    insertRecs[1].ACCOUNT = account;  
                    insertRecs[1].AMOUNT = amount;  
                    insertRecs[1].TRANSDATE = transdate;  
                    insertRecs[1].DESCRIPTION = description2;  
                    insertRecs[1].PROCESSED = processed;  
  
                    try  
                    {  
                        recsInserted = aaTableClient.Insert(insertRecs, null, null);  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    Console.WriteLine("Insert Done: {0} records inserted", recsInserted);  
```  
  
### <a name="select-operation"></a><span data-ttu-id="d1a10-190">選取作業</span><span class="sxs-lookup"><span data-stu-id="d1a10-190">Select Operation</span></span>  
 <span data-ttu-id="d1a10-191">下表顯示所選取的作業參數。</span><span class="sxs-lookup"><span data-stu-id="d1a10-191">The following table shows the parameters for the Select operation.</span></span>  
  
|<span data-ttu-id="d1a10-192">COLUMN_NAMES</span><span class="sxs-lookup"><span data-stu-id="d1a10-192">COLUMN_NAMES</span></span>|<span data-ttu-id="d1a10-193">FILTER</span><span class="sxs-lookup"><span data-stu-id="d1a10-193">FILTER</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="d1a10-194">目標; 中的資料行名稱的逗號分隔清單例如，"TID，帳戶 」。</span><span class="sxs-lookup"><span data-stu-id="d1a10-194">A comma-delimited list of column names in the target; for example, "TID, ACCOUNT".</span></span> <span data-ttu-id="d1a10-195">資料行清單中指定目標應該在結果集中傳回之資料的行。</span><span class="sxs-lookup"><span data-stu-id="d1a10-195">The column list specifies the columns of the target that should be returned in the result set.</span></span> <span data-ttu-id="d1a10-196">未指定資料行清單中的資料行，將設為.NET 預設值在傳回的記錄集內。</span><span class="sxs-lookup"><span data-stu-id="d1a10-196">Columns not specified in the column list will be set to their .NET default values in the returned record set.</span></span> <span data-ttu-id="d1a10-197">Nillable 的資料行，這個值是**null**。</span><span class="sxs-lookup"><span data-stu-id="d1a10-197">For nillable columns, this value is **null**.</span></span>|<span data-ttu-id="d1a10-198">SQL WHERE 子句，指定查詢; 的目標資料列的內容例如，"描述 = '插入記錄 #1' 」。</span><span class="sxs-lookup"><span data-stu-id="d1a10-198">The contents of a SQL WHERE clause that specifies the target rows of the query; for example, "DESCRIPTION = 'Insert Record #1'".</span></span> <span data-ttu-id="d1a10-199">您可以將此參數設定為**null**傳回目標的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="d1a10-199">You can set this parameter to **null** to return all rows of the target.</span></span>|  
  
 <span data-ttu-id="d1a10-200">選取的作業會傳回強型別記錄集的目標資料列型別為基礎。</span><span class="sxs-lookup"><span data-stu-id="d1a10-200">The Select operation returns a strongly-typed record set based on the row type of the target.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1a10-201">當您使用 WCF 服務模型時，沒有資料流支援基本的 SQL 作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-201">There is no streaming support for the basic SQL operations when you use the WCF service model.</span></span> <span data-ttu-id="d1a10-202">如果您的查詢傳回大量的記錄集，您可以使用 WCF 通道模型來改善效能。</span><span class="sxs-lookup"><span data-stu-id="d1a10-202">If your query returns a large record set, you might be able to improve performance by using the WCF channel model.</span></span> <span data-ttu-id="d1a10-203">如需詳細資訊，請參閱 <<c0> [ 叫用使用 WCF 服務模型的基本的 SQL 作業的限制](#BKMK_LimitationsInvoking)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-203">For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).</span></span>  
  
 <span data-ttu-id="d1a10-204">下列程式碼會顯示目標 ACCOUNTACTIVITY 資料表的選取作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-204">The following code shows a Select operation that targets the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="d1a10-205">傳回的記錄會寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1a10-205">The returned records are written to the console.</span></span>  
  
```  
// Declare a variable to hold the result set  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
  
// Select all records and write them to the console  
try  
{  
    selectRecords = aaTableClient.Select("*", null);  
}  
catch (Exception ex)  
{  
    // handle exception  
}  
  
Console.WriteLine("ACCOUNTACTIVITY before any operations");  
for (int i = 0; i \< selectRecords.Length; i++)  
{  
    Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", selectRecords[i].TID,  
    selectRecords[i].ACCOUNT,  
    selectRecords[i].AMOUNT,  
    selectRecords[i].TRANSDATE,  
    selectRecords[i].DESCRIPTION);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="d1a10-206">此程式碼省略了建立、 設定及開啟 WCF 用戶端執行個體的步驟。</span><span class="sxs-lookup"><span data-stu-id="d1a10-206">This code omits steps to create, configure, and open the WCF client instance.</span></span> <span data-ttu-id="d1a10-207">如需包含下列步驟的範例，請參閱 < [Insert 作業](#BKMK_InsertOperation)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-207">For an example that includes these steps, see [Insert Operation](#BKMK_InsertOperation).</span></span>  
  
### <a name="update-operation"></a><span data-ttu-id="d1a10-208">更新作業</span><span class="sxs-lookup"><span data-stu-id="d1a10-208">Update Operation</span></span>  
 <span data-ttu-id="d1a10-209">下表顯示更新作業的參數。</span><span class="sxs-lookup"><span data-stu-id="d1a10-209">The following table shows the parameters for the Update operation.</span></span>  
  
|<span data-ttu-id="d1a10-210">資料錄集</span><span class="sxs-lookup"><span data-stu-id="d1a10-210">RECORDSET</span></span>|<span data-ttu-id="d1a10-211">FILTER</span><span class="sxs-lookup"><span data-stu-id="d1a10-211">FILTER</span></span>|  
|---------------|------------|  
|<span data-ttu-id="d1a10-212">強型別範本記錄，根據目標的資料列型別。</span><span class="sxs-lookup"><span data-stu-id="d1a10-212">A strongly-typed template record based on the row type of the target.</span></span> <span data-ttu-id="d1a10-213">範本記錄指定的目標資料列的更新值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-213">The template record specifies the update values for the target rows.</span></span> <span data-ttu-id="d1a10-214">Nillable 的資料列的資料行，您可以指定 null 值，指出資料行不會更新目標資料列中。</span><span class="sxs-lookup"><span data-stu-id="d1a10-214">For nillable row columns, you can specify a null value to indicate that the column should not be updated in the target rows.</span></span>|<span data-ttu-id="d1a10-215">SQL WHERE 子句，指定要更新的資料列在目標中的內容。</span><span class="sxs-lookup"><span data-stu-id="d1a10-215">The contents of a SQL WHERE clause that specifies the rows to be updated in the target.</span></span> <span data-ttu-id="d1a10-216">例如，"描述 = 'Inserted Record #1' 」。</span><span class="sxs-lookup"><span data-stu-id="d1a10-216">For example, "DESCRIPTION= 'Inserted Record #1'".</span></span>|  
  
 <span data-ttu-id="d1a10-217">更新作業會傳回從目標刪除的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d1a10-217">The Update operation returns the number of rows deleted from the target.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1a10-218">在 WCF 服務模型中，更新作業所使用的範本記錄會是強型別。</span><span class="sxs-lookup"><span data-stu-id="d1a10-218">In the WCF service model, the template record used in the Update operation is strongly-typed.</span></span> <span data-ttu-id="d1a10-219">如果 nillable 資料行，您可以省略更新作業的資料行，其值設定為**null**在範本記錄中; 不過，如果資料行不為 nillable，然後您必須設定其範本記錄中的值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-219">If a column is nillable, you can omit the column from the Update operation by setting its value to **null** in the template record; however, if a column is not nillable, then you must set its value in the template record.</span></span> <span data-ttu-id="d1a10-220">比方說，如果資料行是主索引鍵，它必須包含值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-220">For example, if a column is a primary key, it must contain a value.</span></span> <span data-ttu-id="d1a10-221">如需詳細資訊，請參閱 <<c0> [ 叫用使用 WCF 服務模型的基本的 SQL 作業的限制](#BKMK_LimitationsInvoking)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-221">For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).</span></span>  
  
 <span data-ttu-id="d1a10-222">下列程式碼會顯示目標 ACCOUNTACTIVITY 資料表的更新作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-222">The following code shows an Update operation that targets the ACCOUNTACTIVITY table.</span></span>  
  
```  
long recsUpdated;  
  
...  
  
// Create updated template. The TID, TIME, AMOUNT, and DESCRIPTION fields will be updated  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE updateRecord =  
    new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE();  
        updateRecord.TID = tidSequence.NextVal();  
        updateRecord.ACCOUNT = null;  
        updateRecord.AMOUNT = 300;  
        updateRecord.TRANSDATE = DateTime.Now.Date;  
        updateRecord.DESCRIPTION = "Updated Record #2";  
        updateRecord.PROCESSED = null;  
  
// Set filter string to specify the target record by using the DESCRIPTION field  
string filter = "DESCRIPTION = 'Inserted Record #2'";  
  
try  
{  
    recsUpdated = aaTableClient.Update(updateRecord, filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
    ...  
}  
  
Console.WriteLine("{0} records updated", recsUpdated);  
```  
  
> [!NOTE]
>  <span data-ttu-id="d1a10-223">此程式碼省略了建立、 設定及開啟 WCF 用戶端執行個體的步驟。</span><span class="sxs-lookup"><span data-stu-id="d1a10-223">This code omits steps to create, configure, and open the WCF client instance.</span></span> <span data-ttu-id="d1a10-224">如需包含下列步驟的範例，請參閱 < [Insert 作業](#BKMK_InsertOperation)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-224">For an example that includes these steps, see [Insert Operation](#BKMK_InsertOperation).</span></span>  
  
### <a name="delete-operation"></a><span data-ttu-id="d1a10-225">刪除動作</span><span class="sxs-lookup"><span data-stu-id="d1a10-225">Delete Operation</span></span>  
 <span data-ttu-id="d1a10-226">下表顯示刪除作業的參數。</span><span class="sxs-lookup"><span data-stu-id="d1a10-226">The following table shows the parameters for the Delete operation.</span></span>  
  
|<span data-ttu-id="d1a10-227">FILTER</span><span class="sxs-lookup"><span data-stu-id="d1a10-227">FILTER</span></span>|  
|------------|  
|<span data-ttu-id="d1a10-228">SQL WHERE 子句，指定要從目標刪除的資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="d1a10-228">The contents of a SQL WHERE clause that specifies the rows to be deleted from the target.</span></span> <span data-ttu-id="d1a10-229">例如，"描述 = 'Inserted Record #1' 」。</span><span class="sxs-lookup"><span data-stu-id="d1a10-229">For example, "DESCRIPTION= 'Inserted Record #1'".</span></span>|  
  
 <span data-ttu-id="d1a10-230">刪除作業會傳回從目標刪除的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d1a10-230">The Delete operation returns the number of rows deleted from the target.</span></span> <span data-ttu-id="d1a10-231">下列程式碼顯示目標 ACCOUNTACTIVITY 資料表的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-231">The following code shows a Delete operation that targets the ACCOUNTACTIVITY table.</span></span>  
  
```  
// Set filter string equal to the DESCRIPTION field of the target record  
string filter = "DESCRIPTION = 'Inserted Record #1'";  
  
try  
{  
    recsDeleted = aaTableClient.Delete(filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
  
    ...  
}  
Console.WriteLine("{0} records deleted", recsDeleted);  
```  
  
> [!NOTE]
>  <span data-ttu-id="d1a10-232">此程式碼省略了建立、 設定及開啟 WCF 用戶端執行個體的步驟。</span><span class="sxs-lookup"><span data-stu-id="d1a10-232">This code omits steps to create, configure, and open the WCF client instance.</span></span> <span data-ttu-id="d1a10-233">如需包含下列步驟的範例，請參閱 < [Insert 作業](#BKMK_InsertOperation)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-233">For an example that includes these steps, see the [Insert Operation](#BKMK_InsertOperation).</span></span>  
  
##  <a name="BKMK_LimitationsInvoking"></a> <span data-ttu-id="d1a10-234">使用 WCF 服務模型叫用的基本 SQL 作業的限制</span><span class="sxs-lookup"><span data-stu-id="d1a10-234">Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model</span></span>  
 <span data-ttu-id="d1a10-235">當您使用 WCF 用戶端叫用的基本的 SQL 作業時，就會有下列限制：</span><span class="sxs-lookup"><span data-stu-id="d1a10-235">The following limitations exist when you invoke the basic SQL operations by using a WCF client:</span></span>  
  
- <span data-ttu-id="d1a10-236">**插入作業。**</span><span class="sxs-lookup"><span data-stu-id="d1a10-236">**Insert operation.**</span></span> <span data-ttu-id="d1a10-237">多個記錄插入作業所用的記錄集是強型別，並因此包括所有的資料列資料行。</span><span class="sxs-lookup"><span data-stu-id="d1a10-237">The record set used in a multiple record Insert operation is strongly-typed and therefore includes all row columns.</span></span> <span data-ttu-id="d1a10-238">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解譯為 null 的值來表示記錄中，資料行應該排除插入作業; 不過，非 nill 的資料行無法排除，因為您不能設為 null 的值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-238">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a null value in a record to mean that the column should be excluded from the Insert operation; however, non-nillable columns cannot be excluded because you cannot set them to a null value.</span></span> <span data-ttu-id="d1a10-239">因此，您必須指定非 nill 的資料行的值，當您執行多個記錄插入作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-239">Therefore, you must specify values for non-nillable columns when you perform a multiple record Insert operation.</span></span>  
  
- <span data-ttu-id="d1a10-240">**插入作業。**</span><span class="sxs-lookup"><span data-stu-id="d1a10-240">**Insert operation.**</span></span> <span data-ttu-id="d1a10-241">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解譯**DbNull** nillable 的資料行來表示應該從多個記錄插入作業中排除資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-241">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a **DbNull** value in a nillable data column to mean that the column should be excluded from a multiple record Insert operation.</span></span> <span data-ttu-id="d1a10-242">這表示您無法將 nillable 的資料行設定為**DbNull** Oracle 資料庫中的多個記錄插入作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-242">This means that you cannot set a nillable column to **DbNull** on the Oracle database in a multiple record Insert operation.</span></span>  
  
- <span data-ttu-id="d1a10-243">**插入作業。**</span><span class="sxs-lookup"><span data-stu-id="d1a10-243">**Insert operation.**</span></span> <span data-ttu-id="d1a10-244">沒有資料流支援多個記錄插入作業牽涉到大型的記錄集。</span><span class="sxs-lookup"><span data-stu-id="d1a10-244">There is no streaming support for multiple record insert operations that involve a large record set.</span></span>  
  
- <span data-ttu-id="d1a10-245">**更新作業。**</span><span class="sxs-lookup"><span data-stu-id="d1a10-245">**Update operation.**</span></span> <span data-ttu-id="d1a10-246">在更新作業中使用的範本記錄為強型別，並因此包括所有的資料列資料行。</span><span class="sxs-lookup"><span data-stu-id="d1a10-246">The template record used in an Update operation is strongly-typed and therefore includes all row columns.</span></span> <span data-ttu-id="d1a10-247">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解譯來表示此記錄中的 null 值，應該從更新作業中排除資料行; 不過，非 nill 的資料行無法排除，因為無法為 null 值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-247">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a null value in this record to mean that the column should be excluded from the Update operation; however, non-nillable columns cannot be excluded because you cannot them to a null value.</span></span> <span data-ttu-id="d1a10-248">因此，您必須指定非 nill 的資料行的值，當您執行更新作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-248">Therefore, you must specify values for non-nillable columns when you perform an Update operation.</span></span>  
  
- <span data-ttu-id="d1a10-249">**更新作業。**</span><span class="sxs-lookup"><span data-stu-id="d1a10-249">**Update operation.**</span></span> <span data-ttu-id="d1a10-250">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解譯**DbNull** nillable 資料資料行中的範本記錄来表示應該從作業中排除資料行的值。</span><span class="sxs-lookup"><span data-stu-id="d1a10-250">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a **DbNull** value in a nillable data column in the template record to mean that the column should be excluded from the operation.</span></span> <span data-ttu-id="d1a10-251">這表示您無法將 nillable 的資料行設定為**DbNull**使用更新作業的 Oracle 資料庫上。</span><span class="sxs-lookup"><span data-stu-id="d1a10-251">This means that you cannot set a nillable column to **DbNull** on the Oracle database by using the Update operation.</span></span>  
  
- <span data-ttu-id="d1a10-252">**選取作業。**</span><span class="sxs-lookup"><span data-stu-id="d1a10-252">**Select operation.**</span></span> <span data-ttu-id="d1a10-253">沒有資料流支援傳回大型的記錄集的 SELECT 查詢。</span><span class="sxs-lookup"><span data-stu-id="d1a10-253">There is no streaming support for SELECT queries that return a large record set.</span></span>  
  
  <span data-ttu-id="d1a10-254">這些限制其中呈現挑戰的情況下，您可以使用 WCF 通道模型，因為叫用作業：</span><span class="sxs-lookup"><span data-stu-id="d1a10-254">For scenarios where these limitations present challenges, you can invoke the operation by using the WCF channel model because:</span></span>  
  
- <span data-ttu-id="d1a10-255">藉由使用 WCF 通道模型，您可以排除特定的資料行 Update 和 Insert 作業。</span><span class="sxs-lookup"><span data-stu-id="d1a10-255">By using the WCF channel model, you can exclude specific data columns from Update and Insert operations.</span></span>  
  
- <span data-ttu-id="d1a10-256">WCF 通道模型提供節點層級的資料流支援基本的 SQL 作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-256">The WCF channel model provides node-level streaming support for the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes.</span></span>  
  
  <span data-ttu-id="d1a10-257">如需有關使用使用的 WCF 通道模型[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d1a10-257">For more information about using the WCF channel model with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Develop Oracle Database Applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a10-258">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1a10-258">See Also</span></span>  
 [<span data-ttu-id="d1a10-259">開發使用 WCF 通道模型的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="d1a10-259">Develop Oracle Database Applications Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)