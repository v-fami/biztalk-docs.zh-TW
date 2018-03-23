---
title: 插入、 更新、 刪除或選取 SQL 使用 WCF 服務模型中的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340048ad-ce28-4acf-ae4e-f18bdb3b6f47
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2bc522a1b0b60a9ba0b8407228dd1db65c4e6f0
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="insert-update-delete-or-select-operations-in-sql-using-the-wcf-service-model"></a><span data-ttu-id="97b0c-102">插入、 更新、 刪除或 SQL 使用 WCF 服務模型中選取作業</span><span class="sxs-lookup"><span data-stu-id="97b0c-102">Insert, update, delete, or select operations in SQL using the WCF service model</span></span>
<span data-ttu-id="97b0c-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]會探索 SQL Server 資料庫資料表和檢視表的基本 Insert、 Select、 Update 和 Delete 作業的一組。</span><span class="sxs-lookup"><span data-stu-id="97b0c-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] discovers a set of basic Insert, Select, Update, and Delete operations on SQL Server database tables and views.</span></span> <span data-ttu-id="97b0c-104">藉由使用這些作業，您可以執行簡單的 SQL Insert、 Select、 Update 和 Delete 陳述式 Where 所限定的目標資料表或檢視上的子句。</span><span class="sxs-lookup"><span data-stu-id="97b0c-104">By using these operations, you can perform simple SQL Insert, Select, Update, and Delete statements qualified by a Where clause on a target table or view.</span></span> <span data-ttu-id="97b0c-105">本主題提供有關如何執行這些作業使用 WCF 服務模型的指示。</span><span class="sxs-lookup"><span data-stu-id="97b0c-105">This topic provides instructions on how to perform these operations using the WCF service model.</span></span>  
  
 <span data-ttu-id="97b0c-106">如需有關配接器如何支援這些作業的詳細資訊，請參閱[Insert、 Update、 Delete 和選取資料表和檢視表與 SQL 配接器的作業](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="97b0c-106">For more information on how the adapter supports these operations, see [Insert, Update, Delete, and Select Operations on Tables and Views with the SQL adapter](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97b0c-107">如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視表使用 SQL 配接器的使用者定義類型的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發應用程式之前。</span><span class="sxs-lookup"><span data-stu-id="97b0c-107">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) before you start developing your application.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="97b0c-108">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="97b0c-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="97b0c-109">本主題中的範例上執行作業的員工資料表。</span><span class="sxs-lookup"><span data-stu-id="97b0c-109">The example in this topic performs operations on the Employee table.</span></span> <span data-ttu-id="97b0c-110">Employee 資料表會建立執行範例所提供的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="97b0c-110">The Employee table is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="97b0c-111">如需有關範例的詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="97b0c-111">For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="97b0c-112">範例中， **EmployeeBasicOps**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="97b0c-112">A sample, **EmployeeBasicOps**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="97b0c-113">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="97b0c-113">The WCF Client Class</span></span>  
 <span data-ttu-id="97b0c-114">為基本的 SQL 作業產生 WCF 用戶端的名稱，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會探索下表列出根據資料表或檢視表的名稱。</span><span class="sxs-lookup"><span data-stu-id="97b0c-114">The name of the WCF client generated for the basic SQL operations that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers is based on the name of the table or view, as listed in the following table.</span></span>  
  
|<span data-ttu-id="97b0c-115">SQL Server 資料庫成品</span><span class="sxs-lookup"><span data-stu-id="97b0c-115">SQL Server Database Artifact</span></span>|<span data-ttu-id="97b0c-116">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="97b0c-116">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="97b0c-117">Table</span><span class="sxs-lookup"><span data-stu-id="97b0c-117">Table</span></span>|<span data-ttu-id="97b0c-118">TableOp_[Schema]_[TABLE_NAME]Client</span><span class="sxs-lookup"><span data-stu-id="97b0c-118">TableOp_[Schema]_[TABLE_NAME]Client</span></span>|  
|<span data-ttu-id="97b0c-119">檢視</span><span class="sxs-lookup"><span data-stu-id="97b0c-119">View</span></span>|<span data-ttu-id="97b0c-120">ViewOp_[Schema]_[VIEW_NAME]Client</span><span class="sxs-lookup"><span data-stu-id="97b0c-120">ViewOp_[Schema]_[VIEW_NAME]Client</span></span>|  
  
 <span data-ttu-id="97b0c-121">[SCHEMA] = 集合 SQL Server 成品。例如，dbo。</span><span class="sxs-lookup"><span data-stu-id="97b0c-121">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
 <span data-ttu-id="97b0c-122">[TABLE_NAME] = 表格的名稱例如，員工。</span><span class="sxs-lookup"><span data-stu-id="97b0c-122">[TABLE_NAME] = The name of the table; for example, Employee.</span></span>  
  
 <span data-ttu-id="97b0c-123">[VIEW_NAME] = 檢視; 的名稱例如，Employee_View。</span><span class="sxs-lookup"><span data-stu-id="97b0c-123">[VIEW_NAME] = The name of the view; for example, Employee_View.</span></span>  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a><span data-ttu-id="97b0c-124">叫用資料表上的作業的方法簽章</span><span class="sxs-lookup"><span data-stu-id="97b0c-124">Method Signature for Invoking Operations on Tables</span></span>  
 <span data-ttu-id="97b0c-125">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="97b0c-125">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="97b0c-126">簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。</span><span class="sxs-lookup"><span data-stu-id="97b0c-126">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="97b0c-127">運算</span><span class="sxs-lookup"><span data-stu-id="97b0c-127">Operation</span></span>|<span data-ttu-id="97b0c-128">方法簽章</span><span class="sxs-lookup"><span data-stu-id="97b0c-128">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="97b0c-129">Insert</span><span class="sxs-lookup"><span data-stu-id="97b0c-129">Insert</span></span>|<span data-ttu-id="97b0c-130">long[] Insert([TABLE_NS].[TABLE_NAME][] Rows);</span><span class="sxs-lookup"><span data-stu-id="97b0c-130">long[] Insert([TABLE_NS].[TABLE_NAME][] Rows);</span></span>|  
|<span data-ttu-id="97b0c-131">Select</span><span class="sxs-lookup"><span data-stu-id="97b0c-131">Select</span></span>|<span data-ttu-id="97b0c-132">[TABLE_NS].[TABLE_NAME][] Select(string COLUMNS, string QUERY);</span><span class="sxs-lookup"><span data-stu-id="97b0c-132">[TABLE_NS].[TABLE_NAME][] Select(string COLUMNS, string QUERY);</span></span>|  
|<span data-ttu-id="97b0c-133">Update</span><span class="sxs-lookup"><span data-stu-id="97b0c-133">Update</span></span>|<span data-ttu-id="97b0c-134">int Update([TABLE_NS].[TABLE_NAME].RowPair[] Rows);</span><span class="sxs-lookup"><span data-stu-id="97b0c-134">int Update([TABLE_NS].[TABLE_NAME].RowPair[] Rows);</span></span>|  
|<span data-ttu-id="97b0c-135">Delete</span><span class="sxs-lookup"><span data-stu-id="97b0c-135">Delete</span></span>|<span data-ttu-id="97b0c-136">int Delete([TABLE_NS].[TABLE_NAME][] Rows);</span><span class="sxs-lookup"><span data-stu-id="97b0c-136">int Delete([TABLE_NS].[TABLE_NAME][] Rows);</span></span>|  
  
 <span data-ttu-id="97b0c-137">[TABLE_NS] = 名稱的資料表命名空間中。例如，schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee。</span><span class="sxs-lookup"><span data-stu-id="97b0c-137">[TABLE_NS] = The name of the table namespace; for example, schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee.</span></span>  
  
 <span data-ttu-id="97b0c-138">[TABLE_NAME] = 表格的名稱例如，員工。</span><span class="sxs-lookup"><span data-stu-id="97b0c-138">[TABLE_NAME] = The name of the table; for example, Employee.</span></span>  
  
 <span data-ttu-id="97b0c-139">例如，下列程式碼會示範預設"dbo"結構描述在員工資料表上的 Delete、 Insert、 Select 和 Update 作業所產生 WCF 用戶端類別的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="97b0c-139">As an example, the following code shows the method signatures for a WCF client class generated for the Delete, Insert, Select and Update operations on the Employee table under the default “dbo” schema.</span></span>  
  
```  
public partial class TableOp_dbo_EmployeeClient : System.ServiceModel.ClientBase<TableOp_dbo_Employee>, TableOp_dbo_Employee {      
    public int Delete(schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Rows);  
  
    public long[] Insert(schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Rows);  
  
    public schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Select(string Columns, string Query);  
  
    public int Update(schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[] Rows);  
}  
```  
  
 <span data-ttu-id="97b0c-140">在此程式碼片段，TableOp_dbo_EmployeeClient 是 WCF 中類別的名稱所產生的 SqlAdapterBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="97b0c-140">In this snippet, TableOp_dbo_EmployeeClient is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-table-operations"></a><span data-ttu-id="97b0c-141">資料表作業的參數</span><span class="sxs-lookup"><span data-stu-id="97b0c-141">Parameters for Table Operations</span></span>  
 <span data-ttu-id="97b0c-142">本節提供每個資料表作業所需的參數</span><span class="sxs-lookup"><span data-stu-id="97b0c-142">This section provides the parameters required by each table operation</span></span>  
  
 <span data-ttu-id="97b0c-143">**插入作業**</span><span class="sxs-lookup"><span data-stu-id="97b0c-143">**Insert Operation**</span></span>  
  
|<span data-ttu-id="97b0c-144">插入作業類型</span><span class="sxs-lookup"><span data-stu-id="97b0c-144">Insert operation type</span></span>|<span data-ttu-id="97b0c-145">資料錄集</span><span class="sxs-lookup"><span data-stu-id="97b0c-145">RECORDSET</span></span>|  
|---------------------------|---------------|  
|<span data-ttu-id="97b0c-146">多個記錄</span><span class="sxs-lookup"><span data-stu-id="97b0c-146">Multiple record</span></span>|<span data-ttu-id="97b0c-147">應插入至資料表的 INSERTRECORDS 的集合。</span><span class="sxs-lookup"><span data-stu-id="97b0c-147">A collection of INSERTRECORDS that should be inserted into the table.</span></span>|  
  
 <span data-ttu-id="97b0c-148">插入作業會傳回長整數資料類型的陣列，並將插入的資料列的識別值，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="97b0c-148">The insert operation returns an array of Long data type and stores the identity values of the inserted rows, if any.</span></span> <span data-ttu-id="97b0c-149">如果資料表沒有識別資料行，傳回值會是 NULL。</span><span class="sxs-lookup"><span data-stu-id="97b0c-149">If there is no identity column in a table, the return value is NULL.</span></span>  
  
 <span data-ttu-id="97b0c-150">**選取作業**</span><span class="sxs-lookup"><span data-stu-id="97b0c-150">**Select Operation**</span></span>  
  
|<span data-ttu-id="97b0c-151">COLUMN_NAMES</span><span class="sxs-lookup"><span data-stu-id="97b0c-151">COLUMN_NAMES</span></span>|<span data-ttu-id="97b0c-152">QUERY</span><span class="sxs-lookup"><span data-stu-id="97b0c-152">QUERY</span></span>|  
|-------------------|-----------|  
|<span data-ttu-id="97b0c-153">目標; 中的資料行名稱以逗號分隔清單例如，"Employee_ID，指定"。</span><span class="sxs-lookup"><span data-stu-id="97b0c-153">A comma-delimited list of column names in the target; for example, "Employee_ID, Designation".</span></span> <span data-ttu-id="97b0c-154">資料行清單中指定的目標所應傳回結果集中的資料行。</span><span class="sxs-lookup"><span data-stu-id="97b0c-154">The column list specifies the columns of the target that should be returned in the result set.</span></span> <span data-ttu-id="97b0c-155">未指定資料行清單中的資料行會設定為其傳回的記錄組中的.NET 預設值。</span><span class="sxs-lookup"><span data-stu-id="97b0c-155">Columns not specified in the column list will be set to their .NET default values in the returned record set.</span></span> <span data-ttu-id="97b0c-156">Nillable 資料行，這個值是**null**。</span><span class="sxs-lookup"><span data-stu-id="97b0c-156">For nillable columns, this value is **null**.</span></span>|<span data-ttu-id="97b0c-157">SQL WHERE 子句會指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。</span><span class="sxs-lookup"><span data-stu-id="97b0c-157">The contents of a SQL WHERE clause that specifies the target rows of the query; for example, "Designation = 'Manager'".</span></span> <span data-ttu-id="97b0c-158">您可以將此參數設定為**null**傳回目標的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="97b0c-158">You can set this parameter to **null** to return all rows of the target.</span></span>|  
  
 <span data-ttu-id="97b0c-159">選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列從目標資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="97b0c-159">The return value of the Select operation is a strongly-typed result set that contains the specified columns and rows from the target table or view.</span></span>  
  
 <span data-ttu-id="97b0c-160">**更新作業**</span><span class="sxs-lookup"><span data-stu-id="97b0c-160">**Update Operation**</span></span>  
  
|<span data-ttu-id="97b0c-161">該配對的第一個資料列</span><span class="sxs-lookup"><span data-stu-id="97b0c-161">First row of the pair</span></span>|<span data-ttu-id="97b0c-162">該配對的第二個資料列</span><span class="sxs-lookup"><span data-stu-id="97b0c-162">Second row of the pair</span></span>|  
|---------------------------|----------------------------|  
|<span data-ttu-id="97b0c-163">第一項記錄的記錄組對應到新的值需要更新，亦即，它對應到 UPDATE 陳述式的 SET 子句。</span><span class="sxs-lookup"><span data-stu-id="97b0c-163">The first record of the record pair corresponds to new values that need to be updated, that is, it corresponds to the SET clause of the UPDATE statement.</span></span> <span data-ttu-id="97b0c-164">這可以設定使用`RowPair.After`。</span><span class="sxs-lookup"><span data-stu-id="97b0c-164">This can be set using `RowPair.After`.</span></span>|<span data-ttu-id="97b0c-165">第二個記錄的記錄組對應的資料列的舊值，也就是它對應到 UPDATE 陳述式的 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="97b0c-165">The second record of the record pair corresponds to the old values of the rows, that is, it corresponds to the WHERE clause of the UPDATE statement.</span></span> <span data-ttu-id="97b0c-166">這可以設定使用`RowPair.Before`。</span><span class="sxs-lookup"><span data-stu-id="97b0c-166">This can be set using `RowPair.Before`.</span></span>|  
  
 <span data-ttu-id="97b0c-167">更新作業的傳回值的 Int32 資料型別，並代表更新的資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="97b0c-167">The return value of the Update operation is of Int32 data type, and denotes the number of rows updated.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="97b0c-168">指定必須更新的記錄，同時您必須提供值給所有資料行，即使未正確更新所有的值。</span><span class="sxs-lookup"><span data-stu-id="97b0c-168">While specifying the record that has to be updated, you must provide values for all the columns, even if all values are not being updated.</span></span> <span data-ttu-id="97b0c-169">例如，如果資料列都有五個資料行，並更新作業更新只有 2 個資料行，做為 RowPair.Before 的一部分，您必須傳遞所有 5 個資料行值。</span><span class="sxs-lookup"><span data-stu-id="97b0c-169">For example, if a row has five columns and the Update operation updates only 2 columns, as part of RowPair.Before, you must pass all the 5 column values.</span></span> <span data-ttu-id="97b0c-170">不過，如 RowPair.After，您可以指定將更新的資料行。</span><span class="sxs-lookup"><span data-stu-id="97b0c-170">However, for RowPair.After, you can specify only the columns that will be updated.</span></span>  
  
 <span data-ttu-id="97b0c-171">**刪除作業**</span><span class="sxs-lookup"><span data-stu-id="97b0c-171">**Delete Operation**</span></span>  
  
 <span data-ttu-id="97b0c-172">刪除作業會為強類型的輸入陣列的記錄。</span><span class="sxs-lookup"><span data-stu-id="97b0c-172">The Delete operation takes as input a strongly-typed array of records.</span></span> <span data-ttu-id="97b0c-173">刪除作業的傳回值的 Int32 資料型別，並代表刪除資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="97b0c-173">The return value of the Delete operation is of Int32 data type, and denotes the number of rows deleted.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-and-views"></a><span data-ttu-id="97b0c-174">建立 WCF 用戶端來叫用資料表和檢視表上的作業</span><span class="sxs-lookup"><span data-stu-id="97b0c-174">Creating a WCF Client to Invoke Operations on Tables and Views</span></span>  
 <span data-ttu-id="97b0c-175">使用 WCF 用戶端的 SQL Server 上執行作業所需的動作的泛型集合包含一組工作中所述[SQL 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="97b0c-175">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="97b0c-176">本章節描述如何建立 WCF 用戶端來叫用基本 Insert、 Select、 Update 資料表上的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="97b0c-176">This section describes how to create a WCF client to invoke basic Insert, Select, Update, Delete operations on a table.</span></span>  
  
#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a><span data-ttu-id="97b0c-177">若要建立 WCF 用戶端在資料表上執行作業</span><span class="sxs-lookup"><span data-stu-id="97b0c-177">To create a WCF client to perform operations on tables</span></span>  
  
1.  <span data-ttu-id="97b0c-178">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="97b0c-178">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="97b0c-179">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="97b0c-179">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="97b0c-180">產生 WCF 用戶端類別的 Insert、 Select、 Update 和刪除操作的 Employee 資料表。</span><span class="sxs-lookup"><span data-stu-id="97b0c-180">Generate the WCF client class for the Insert, Select, Update, and Delete operation on the Employee table.</span></span> <span data-ttu-id="97b0c-181">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="97b0c-181">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="97b0c-182">在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。</span><span class="sxs-lookup"><span data-stu-id="97b0c-182">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="97b0c-183">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。</span><span class="sxs-lookup"><span data-stu-id="97b0c-183">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="97b0c-184">開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="97b0c-184">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="97b0c-185">在此程式碼片段， `TableOp_dbo_EmployeeClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="97b0c-185">In this snippet, `TableOp_dbo_EmployeeClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="97b0c-186">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="97b0c-186">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="97b0c-187">`SqlAdapterBinding_TableOp_dbo_Employee` 用戶端端點組態的名稱，而定義在 app.config 中。這個檔案也會產生由[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="97b0c-187">`SqlAdapterBinding_TableOp_dbo_Employee` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="97b0c-188">在此片段中，您從組態檔使用的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="97b0c-188">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="97b0c-189">您可以同時也可以明確指定這些值，在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="97b0c-189">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="97b0c-190">如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="97b0c-190">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="97b0c-191">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="97b0c-191">Open the client as described in the snippet below:</span></span>  
  
    ```  
    try  
    {  
       Console.WriteLine("Opening Client...");  
       client.Open();  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    ```  
  
6.  <span data-ttu-id="97b0c-192">叫用的 Employee 資料表的 Insert 作業。</span><span class="sxs-lookup"><span data-stu-id="97b0c-192">Invoke the Insert operation on the Employee table.</span></span>  
  
    ```  
    long[] recordsInserted;  
  
    schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] insertRecord =  
    new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[1];  
  
    insertRecord[0] = new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee();  
    insertRecord[0].Name = "John Smith";  
    insertRecord[0].Designation = "Manager";  
    insertRecord[0].Salary = 500000;  
  
    try  
    {  
       Console.WriteLine("Inserting new table entry...");  
       recordsInserted = client.Insert(insertRecord);  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
  
    Console.WriteLine("Record inserted");  
    Console.WriteLine("Press any key to continue ...");  
    Console.ReadLine();  
    ```  
  
     <span data-ttu-id="97b0c-193">您可以取代上述程式碼片段來執行 Select、 Update 或 Delete 作業，以及。</span><span class="sxs-lookup"><span data-stu-id="97b0c-193">You can replace the preceding code snippet to perform Select, Update, or Delete operations as well.</span></span> <span data-ttu-id="97b0c-194">您也可以附加到單一應用程式的所有執行的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="97b0c-194">You can also append the code snippets to perform all operation in a single application.</span></span> <span data-ttu-id="97b0c-195">如需如何執行這些作業程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="97b0c-195">For code snippets on how to perform these operations.</span></span>  
  
7.  <span data-ttu-id="97b0c-196">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="97b0c-196">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="97b0c-197">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="97b0c-197">Build the project and then run it.</span></span> <span data-ttu-id="97b0c-198">應用程式中的 Employee 資料表中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="97b0c-198">The application inserts a record in the Employee table.</span></span>  
  
###   <a name="select-operation"></a><span data-ttu-id="97b0c-199">選取作業</span><span class="sxs-lookup"><span data-stu-id="97b0c-199">Select Operation</span></span>  
 <span data-ttu-id="97b0c-200">下列程式碼會顯示為目標的 Employee 資料表的選取作業。</span><span class="sxs-lookup"><span data-stu-id="97b0c-200">The following code shows a Select operation that targets the Employee table.</span></span> <span data-ttu-id="97b0c-201">選取的作業選取插入至資料表的最後一個記錄。</span><span class="sxs-lookup"><span data-stu-id="97b0c-201">The Select operation selects the last record inserted into the table.</span></span> <span data-ttu-id="97b0c-202">傳回的記錄會寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="97b0c-202">The returned records are written to the console.</span></span>  
  
```  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] selectRecords;  
  
try  
{  
   Console.WriteLine("Selecting Row...");  
   selectRecords = client.Select("*", "where [Employee_ID] = (select IDENT_CURRENT('Employee'))");  
}  
  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("The details of the newly added employee are:");  
Console.WriteLine("********************************************");  
for (int i = 0; i < selectRecords.Length; i++)  
{  
   Console.WriteLine("Employee ID        : " + selectRecords[i].Employee_ID);  
   Console.WriteLine("Employee Name      : " + selectRecords[i].Name);  
   Console.WriteLine("Employee Desigation: " + selectRecords[i].Designation);  
   Console.WriteLine();  
}  
Console.WriteLine("********************************************");  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###   <a name="update-operation"></a><span data-ttu-id="97b0c-203">更新作業</span><span class="sxs-lookup"><span data-stu-id="97b0c-203">Update Operation</span></span>  
 <span data-ttu-id="97b0c-204">下列程式碼會示範 Employee 資料表為目標的更新作業。</span><span class="sxs-lookup"><span data-stu-id="97b0c-204">The following code shows an Update operation that targets the Employee table.</span></span>  
  
```  
int result;  
  
schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair updateRecordPair =  
   new schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair();  
  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee updateRecord =   
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee();  
  
schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[] updateArray =  
   new schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[1];  
  
updateRecord = insertRecord[0];  
updateRecord.Name = "Jeff Smith";  
  
updateRecordPair.After = updateRecord;  
updateRecordPair.Before = selectRecords[0];  
  
updateArray[0] = updateRecordPair;  
  
try  
{  
   Console.WriteLine("Updating the database...");  
   result = client.Update(updateArray);  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("Updated Record for {0}", updateRecordPair.Before.Name);  
Console.WriteLine("The new name for the employee is {0}", updateRecordPair.After.Name);  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###   <a name="delete-operation"></a><span data-ttu-id="97b0c-205">刪除動作</span><span class="sxs-lookup"><span data-stu-id="97b0c-205">Delete Operation</span></span>  
 <span data-ttu-id="97b0c-206">下列程式碼會顯示為目標的 Employee 資料表的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="97b0c-206">The following code shows a Delete operation that targets the Employee table.</span></span>  
  
```  
int deleteSuccess;  
  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] deleteRecords =  
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[1];  
  
deleteRecords = client.Select("*", "where [Employee_ID] = (select IDENT_CURRENT('Employee'))");  
  
Console.WriteLine("Following employees will be deleted from the database:");  
for (int i = 0; i < deleteRecords.Length; i++)  
{  
   Console.WriteLine("Name: {0}", deleteRecords[i].Name);  
}  
Console.WriteLine("Press any key to begin deletion...");  
Console.ReadLine();  
  
try  
{  
   Console.WriteLine("Deleting employee record...");  
   deleteSuccess = client.Delete(deleteRecords);  
}  
  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="97b0c-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97b0c-207">See Also</span></span>  
[<span data-ttu-id="97b0c-208">使用 WCF 服務模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="97b0c-208">Develop applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)