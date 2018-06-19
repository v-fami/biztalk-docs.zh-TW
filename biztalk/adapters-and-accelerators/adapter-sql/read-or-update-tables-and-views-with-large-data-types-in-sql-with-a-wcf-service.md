---
title: 使用 SQL 使用 WCF 服務模型中的大型資料類型執行資料表和檢視表上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d33e17c-e09e-4a57-9acc-43095e67ed8c
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1da0def828c1dbfa8511dc61b529fa02cb53ca5a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967124"
---
# <a name="run-operations-on-tables-and-views-with-large-data-types-in-sql-using-the-wcf-service-model"></a><span data-ttu-id="13ba2-102">使用 SQL 使用 WCF 服務模型中的大型資料類型執行資料表和檢視表上的作業</span><span class="sxs-lookup"><span data-stu-id="13ba2-102">Run Operations on Tables and Views with Large Data Types in SQL using the WCF Service Model</span></span>
<span data-ttu-id="13ba2-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓讀取及更新大型資料類型的資料行中的資料，也就是配接器用戶端、 varchar （max）、 nvarchar （max） 或 varbinary （max）。</span><span class="sxs-lookup"><span data-stu-id="13ba2-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to read and update data in columns of large data types, that is, varchar(max), nvarchar(max), or varbinary(max).</span></span> <span data-ttu-id="13ba2-104">若要從這類資料行讀取資料，配接器用戶端可以使用選取的作業。</span><span class="sxs-lookup"><span data-stu-id="13ba2-104">To read data from such columns, adapter clients can use the Select operation.</span></span> <span data-ttu-id="13ba2-105">若要插入或更新到這類資料行的資料，配接器會公開一組\<*column_name* \>作業，其中\< *column_name* \>名稱類型 varchar （max）、 nvarchar （max） 或 varbinary （max） 資料行。</span><span class="sxs-lookup"><span data-stu-id="13ba2-105">To insert or update data into such columns, the adapter exposes a Set\<*column_name*\> operation, where \<*column_name*\> is the name of the column of type varchar(max), nvarchar(max), or varbinary(max).</span></span>  
  
 <span data-ttu-id="13ba2-106">此外，在 SQL Server 中，您可以儲存非結構化的資料，例如文字文件和影像 varbinay(max) 資料行。</span><span class="sxs-lookup"><span data-stu-id="13ba2-106">Additionally, in SQL Server, you can have the varbinay(max) column store unstructured data such as text documents and images.</span></span> <span data-ttu-id="13ba2-107">這類非結構化的資料稱為 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="13ba2-107">Such unstructured data is called FILESTREAM data.</span></span> <span data-ttu-id="13ba2-108">FILESTREAM 資料可以儲存為檔案系統上的檔案。</span><span class="sxs-lookup"><span data-stu-id="13ba2-108">FILESTREAM data can be stored as files on the file system.</span></span> <span data-ttu-id="13ba2-109">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓用戶端若要將輸入資料行類型 varbinary （max） FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="13ba2-109">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables the client to enter FILESTREAM data into columns of type varbinary(max).</span></span> <span data-ttu-id="13ba2-110">[FILESTREAM 儲存體](https://docs.microsoft.com/sql/relational-databases/blob/filestream-sql-server)更多詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="13ba2-110">[FILESTREAM storage](https://docs.microsoft.com/sql/relational-databases/blob/filestream-sql-server) has more information.</span></span> 
  
 <span data-ttu-id="13ba2-111">本主題提供您必須執行某些工作的相關資訊的電腦上執行 SQL Server 的電腦及執行配接器用戶端能夠插入或更新 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="13ba2-111">This topic provides information about certain tasks you must perform on the computer running SQL Server and the computer running the adapter client to be able to insert or update FILESTREAM data.</span></span> <span data-ttu-id="13ba2-112">本主題也提供指示執行 Set\<*column_name* \>插入 FILESTREAM 資料的作業。</span><span class="sxs-lookup"><span data-stu-id="13ba2-112">This topic also provides instructions on performing Set\<*column_name*\> operations to insert FILESTREAM data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13ba2-113">如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視表使用 SQL 配接器的使用者定義類型的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-113">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="13ba2-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="13ba2-114">Prerequisites</span></span>  
 <span data-ttu-id="13ba2-115">您必須執行 SQL Server 的電腦和執行配接器用戶端電腦上執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="13ba2-115">You must perform the following tasks on the computer running SQL Server and the computer running the adapter client.</span></span>  
  
-   <span data-ttu-id="13ba2-116">**執行 SQL Server 的電腦上**</span><span class="sxs-lookup"><span data-stu-id="13ba2-116">**On the computer running SQL Server**</span></span>  
  
    -   <span data-ttu-id="13ba2-117">您必須在 SQL Server 執行個體上啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="13ba2-117">You must enable FILESTREAM on the SQL Server instance.</span></span> <span data-ttu-id="13ba2-118">請參閱[啟用及設定 FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/enable-and-configure-filestream)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-118">See [Enable and Configure FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/enable-and-configure-filestream).</span></span>
  
    -   <span data-ttu-id="13ba2-119">您必須建立啟用 FILESTREAM 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="13ba2-119">You must create a FILESTREAM-enabled database.</span></span> <span data-ttu-id="13ba2-120">請參閱[建立啟用 FILESTREAM 的資料庫](https://docs.microsoft.com/sql/relational-databases/blob/create-a-filestream-enabled-database)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-120">See [Create a FILESTREAM-Enabled Database](https://docs.microsoft.com/sql/relational-databases/blob/create-a-filestream-enabled-database).</span></span>
  
    -   <span data-ttu-id="13ba2-121">您必須具有儲存 FILESTREAM 資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="13ba2-121">You must have a table for storing FILESTREAM data.</span></span> <span data-ttu-id="13ba2-122">請參閱[建立儲存 FILESTREAM 資料的資料表](https://docs.microsoft.com/sql/relational-databases/blob/create-a-table-for-storing-filestream-data)，</span><span class="sxs-lookup"><span data-stu-id="13ba2-122">See [Create a Table for Storing FILESTREAM Data](https://docs.microsoft.com/sql/relational-databases/blob/create-a-table-for-storing-filestream-data),</span></span>
  
-   <span data-ttu-id="13ba2-123">**執行配接器用戶端的電腦上**</span><span class="sxs-lookup"><span data-stu-id="13ba2-123">**On the computer running the adapter client**</span></span>  
  
    -   <span data-ttu-id="13ba2-124">您必須安裝 SQL 用戶端連接性 SDK。</span><span class="sxs-lookup"><span data-stu-id="13ba2-124">You must have the SQL Client Connectivity SDK installed.</span></span> <span data-ttu-id="13ba2-125">您可以在執行 SQL Server 安裝程式並選取安裝 SQL 用戶端連接性 SDK **SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="13ba2-125">You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard.</span></span> <span data-ttu-id="13ba2-126">配接器使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。</span><span class="sxs-lookup"><span data-stu-id="13ba2-126">The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.</span></span>  
  
 <span data-ttu-id="13ba2-127">您已完成這些工作之後，您已設定完畢插入或更新 SQL Server 資料庫資料表中的 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="13ba2-127">After you have completed these tasks, you are all set to insert or update FILESTREAM data in SQL Server database tables.</span></span>  
  
## <a name="how-this-topic-demonstrates-operations-on-large-data-types"></a><span data-ttu-id="13ba2-128">本主題將大型資料類型上的作業的示範</span><span class="sxs-lookup"><span data-stu-id="13ba2-128">How This Topic Demonstrates Operations on Large Data Types</span></span>  
 <span data-ttu-id="13ba2-129">若要示範如何執行資料集\<*column_name* \>作業在資料表上的使用大型資料類型，而需要資料表，**記錄**，具有資料行**識別碼**和**文件**:</span><span class="sxs-lookup"><span data-stu-id="13ba2-129">To demonstrate how to perform Set\<*column_name*\> operations on tables with large data types, take a table, **Records**, that has columns **Id** and **Document**:</span></span>  
  
-   <span data-ttu-id="13ba2-130">**記錄**資料表，且所有資料，由執行 SQL 指令碼提供範例。</span><span class="sxs-lookup"><span data-stu-id="13ba2-130">The **Records** table, with all the data, is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="13ba2-131">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-131">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
-   <span data-ttu-id="13ba2-132">**識別碼**類型 uniqueidentifier 的資料行，並採用 GUID。</span><span class="sxs-lookup"><span data-stu-id="13ba2-132">The **Id** column is of type uniqueidentifier and takes a GUID.</span></span> <span data-ttu-id="13ba2-133">假設**識別碼**資料行已經有一個 GUID '`438B7B4C-5491-409F-BCC1-78817C399EC3`'。</span><span class="sxs-lookup"><span data-stu-id="13ba2-133">Assume that the **Id** column already has a GUID ‘`438B7B4C-5491-409F-BCC1-78817C399EC3`’.</span></span>  
  
-   <span data-ttu-id="13ba2-134">**文件**資料行是 varbinary （max） 類型。</span><span class="sxs-lookup"><span data-stu-id="13ba2-134">The **Document** column is of type VARBINARY(MAX).</span></span> <span data-ttu-id="13ba2-135">若要更新**文件**資料行中，配接器會公開**SetDocument**作業。</span><span class="sxs-lookup"><span data-stu-id="13ba2-135">To update the **Document** column, the adapter exposes the **SetDocument** operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13ba2-136">SQL Server，以示範 FILESTREAM 作業，假設**文件**資料行可儲存 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="13ba2-136">For SQL Server, to demonstrate FILESTREAM operations, assume that the **Document** column can store FILESTREAM data.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="13ba2-137">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="13ba2-137">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="13ba2-138">本主題中的範例上執行作業**記錄**資料表。</span><span class="sxs-lookup"><span data-stu-id="13ba2-138">The example in this topic performs operations on the **Records** table.</span></span> <span data-ttu-id="13ba2-139">**記錄**執行範例所提供的 SQL 指令碼來建立資料表。</span><span class="sxs-lookup"><span data-stu-id="13ba2-139">The **Records** table is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="13ba2-140">如需有關範例的詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-140">For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="13ba2-141">範例中， **Records_FILESTREAM_Op**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="13ba2-141">A sample, **Records_FILESTREAM_Op**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="13ba2-142">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="13ba2-142">The WCF Client Class</span></span>  
 <span data-ttu-id="13ba2-143">WCF 用戶端產生大型資料上作業的名稱類型[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]探索，如下所列於下表根據資料表或檢視表的名稱。</span><span class="sxs-lookup"><span data-stu-id="13ba2-143">The name of the WCF client generated for the operations on large data types that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers, is based on the name of the table or view, as listed in the following table.</span></span>  
  
|<span data-ttu-id="13ba2-144">SQL Server 資料庫成品</span><span class="sxs-lookup"><span data-stu-id="13ba2-144">SQL Server Database Artifact</span></span>|<span data-ttu-id="13ba2-145">WCF 用戶端名稱</span><span class="sxs-lookup"><span data-stu-id="13ba2-145">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="13ba2-146">Table</span><span class="sxs-lookup"><span data-stu-id="13ba2-146">Table</span></span>|<span data-ttu-id="13ba2-147">TableOp_ [Schema] _ [TABLE_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="13ba2-147">TableOp_[Schema]_[TABLE_NAME]Client</span></span>|  
|<span data-ttu-id="13ba2-148">檢視</span><span class="sxs-lookup"><span data-stu-id="13ba2-148">View</span></span>|<span data-ttu-id="13ba2-149">ViewOp_ [Schema] _ [VIEW_NAME] 用戶端</span><span class="sxs-lookup"><span data-stu-id="13ba2-149">ViewOp_[Schema]_[VIEW_NAME]Client</span></span>|  
  
 <span data-ttu-id="13ba2-150">[SCHEMA] = 集合 SQL Server 成品。例如，dbo。</span><span class="sxs-lookup"><span data-stu-id="13ba2-150">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
### <a name="method-signature-for-invoking-operations-on-columns-of-large-data-types"></a><span data-ttu-id="13ba2-151">叫用的大型資料類型的資料行上作業的方法簽章</span><span class="sxs-lookup"><span data-stu-id="13ba2-151">Method Signature for Invoking Operations on Columns of Large Data Types</span></span>  
 <span data-ttu-id="13ba2-152">下表顯示在資料表上的基本作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="13ba2-152">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="13ba2-153">簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。</span><span class="sxs-lookup"><span data-stu-id="13ba2-153">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="13ba2-154">作業</span><span class="sxs-lookup"><span data-stu-id="13ba2-154">Operation</span></span>|<span data-ttu-id="13ba2-155">方法簽章</span><span class="sxs-lookup"><span data-stu-id="13ba2-155">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="13ba2-156">設定\<*column_name*\></span><span class="sxs-lookup"><span data-stu-id="13ba2-156">Set\<*column_name*\></span></span>|<span data-ttu-id="13ba2-157">public void Set\<*column_name*\>（字串篩選條件，byte [] 的資料;）</span><span class="sxs-lookup"><span data-stu-id="13ba2-157">public void Set\<*column_name*\>(string Filter, byte[] Data);</span></span>|  
  
 <span data-ttu-id="13ba2-158">\<*column_name* \> = 大型資料類型的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="13ba2-158">\<*column_name*\> = Name of the column of large data type.</span></span>  
  
 <span data-ttu-id="13ba2-159">例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**SetDocument**作業**記錄**預設"dbo"結構描述底下的資料表。</span><span class="sxs-lookup"><span data-stu-id="13ba2-159">As an example, the following code shows the method signatures for a WCF client class generated for the **SetDocument** operation on the **Records** table under the default “dbo” schema.</span></span>  
  
```  
public partial class TableOp_dbo_RecordsClient : System.ServiceModel.ClientBase<TableOp_dbo_Records>, TableOp_dbo_Records {      
    public void SetDocument (string Filter, byte[] Data);  
}  
```  
  
 <span data-ttu-id="13ba2-160">在此程式碼片段， **TableOp_dbo_RecordsClient**是 WCF 中的類別所產生的 SqlAdapterBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="13ba2-160">In this snippet, **TableOp_dbo_RecordsClient** is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-operations-on-columns-of-large-data-types"></a><span data-ttu-id="13ba2-161">針對大型資料類型的資料行上的作業參數</span><span class="sxs-lookup"><span data-stu-id="13ba2-161">Parameters for Operations on Columns of Large Data Types</span></span>  
 <span data-ttu-id="13ba2-162">本節提供設定所需的參數\<*column_name* \>作業。</span><span class="sxs-lookup"><span data-stu-id="13ba2-162">This section provides the parameters required by the Set\<*column_name*\> operation.</span></span>  
  
|<span data-ttu-id="13ba2-163">參數名稱</span><span class="sxs-lookup"><span data-stu-id="13ba2-163">Parameter name</span></span>|<span data-ttu-id="13ba2-164">Description</span><span class="sxs-lookup"><span data-stu-id="13ba2-164">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="13ba2-165">字串篩選條件</span><span class="sxs-lookup"><span data-stu-id="13ba2-165">string Filter</span></span>|<span data-ttu-id="13ba2-166">指定 WHERE 子句基礎的介面卡更新大型資料類型的資料行的記錄。</span><span class="sxs-lookup"><span data-stu-id="13ba2-166">Specifies the WHERE clause based on which the adapter updates the record for the column of large data type.</span></span>|  
|<span data-ttu-id="13ba2-167">byte [] 的資料</span><span class="sxs-lookup"><span data-stu-id="13ba2-167">byte[] Data</span></span>|<span data-ttu-id="13ba2-168">指定必須更新大型資料類型的資料行的值。</span><span class="sxs-lookup"><span data-stu-id="13ba2-168">Specifies the value that must be updated for the column of large data type.</span></span>|  
  
 <span data-ttu-id="13ba2-169">集合\<*column_name* \>作業不會傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="13ba2-169">The Set\<*column_name*\> operation does not return any values.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-columns-of-large-data-types"></a><span data-ttu-id="13ba2-170">建立 WCF 用戶端來叫用的大型資料類型資料行上的作業</span><span class="sxs-lookup"><span data-stu-id="13ba2-170">Creating a WCF Client to Invoke Operations on Columns of Large Data Types</span></span>  
 <span data-ttu-id="13ba2-171">使用 WCF 用戶端的 SQL Server 上執行作業所需的動作的泛型集合包含一組工作中所述[SQL 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-171">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="13ba2-172">本章節描述如何建立 WCF 用戶端來叫用**SetDocument**作業**記錄**資料表。</span><span class="sxs-lookup"><span data-stu-id="13ba2-172">This section describes how to create a WCF client to invoke the **SetDocument** operation on the **Records** table.</span></span> <span data-ttu-id="13ba2-173">配接器會公開**SetDocument**作業，以便更新大型資料類型的資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="13ba2-173">The adapter exposes the **SetDocument** operation to update data in columns of large data types.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="13ba2-174">若要建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="13ba2-174">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="13ba2-175">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="13ba2-175">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="13ba2-176">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="13ba2-176">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="13ba2-177">產生 WCF 用戶端類別**SetDocument**作業**記錄**資料表。</span><span class="sxs-lookup"><span data-stu-id="13ba2-177">Generate the WCF client class for the **SetDocument** operation on the **Records** table.</span></span> <span data-ttu-id="13ba2-178">如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-178">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
3.  <span data-ttu-id="13ba2-179">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`， `Microsoft.ServiceModel.Channels`，和`System.Transactions`。</span><span class="sxs-lookup"><span data-stu-id="13ba2-179">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, and `System.Transactions`.</span></span>  
  
4.  <span data-ttu-id="13ba2-180">開啟 Program.cs 檔案並加入`System.Transactions`命名空間。</span><span class="sxs-lookup"><span data-stu-id="13ba2-180">Open the Program.cs file and add the `System.Transactions` namespace.</span></span>  
  
5.  <span data-ttu-id="13ba2-181">在 Program.cs 中，建立用戶端，如以下程式碼片段中所述。</span><span class="sxs-lookup"><span data-stu-id="13ba2-181">In the Program.cs, create a client as described in the snippet below.</span></span>  
  
    ```  
  
              TableOp_dbo_RecordsClient client = new TableOp_dbo_RecordsClient("SqlAdapterBinding_TableOp_dbo_Records");  
    client.ClientCredentials.UserName.UserName = "";  
    client.ClientCredentials.UserName.Password = "";  
  
    ```  
  
     <span data-ttu-id="13ba2-182">在此程式碼片段， `TableOp_dbo_RecordsClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="13ba2-182">In this snippet, `TableOp_dbo_RecordsClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="13ba2-183">這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="13ba2-183">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="13ba2-184">`SqlAdapterBinding_TableOp_dbo_Records`用戶端端點組態的名稱，而定義在 app.config 中。這個檔案也會產生由[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="13ba2-184">`SqlAdapterBinding_TableOp_dbo_Records` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="13ba2-185">若要執行 FILESTREAM 資料上的作業，您永遠必須連接到 SQL Server 使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="13ba2-185">To perform operations on FILESTREAM data, you must always connect to SQL Server using Windows authentication.</span></span> <span data-ttu-id="13ba2-186">若要使用 Windows 驗證進行連接，您必須提供空的使用者名稱和密碼，如先前的程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="13ba2-186">To connect using Windows authentication, you must provide empty username and password, as shown in the preceding snippet.</span></span> <span data-ttu-id="13ba2-187">此外，然後再使用 Windows 驗證來連接到 SQL Server，您必須執行中所述的步驟[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-187">Also, before using Windows authentication to connect to SQL Server, you must have performed the steps mentioned in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13ba2-188">在此片段中，您從組態檔使用的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="13ba2-188">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="13ba2-189">您可以同時也可以明確指定這些值，在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="13ba2-189">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="13ba2-190">如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="13ba2-190">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
6.  <span data-ttu-id="13ba2-191">以下程式碼片段中所述，請開啟用戶端：</span><span class="sxs-lookup"><span data-stu-id="13ba2-191">Open the client as described in the snippet below:</span></span>  
  
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
  
7.  <span data-ttu-id="13ba2-192">叫用**SetDocument**作業**記錄**資料表。</span><span class="sxs-lookup"><span data-stu-id="13ba2-192">Invoke the **SetDocument** operation on the **Records** table.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="13ba2-193">集合 *< column_name >* 一律必須在交易中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="13ba2-193">The Set *<column_name>* operations must always be performed in a transaction.</span></span> <span data-ttu-id="13ba2-194">若要，確保組 *< column_name >* 必須在交易範圍內叫用作業和**UseAmbientTransaction**繫結屬性必須設定為**true**在 app.config 中。</span><span class="sxs-lookup"><span data-stu-id="13ba2-194">To ensure this, the Set *<column_name>* operation must be invoked within a transaction scope and the **UseAmbientTransaction** binding property must be set to **true** in the app.config.</span></span>  
  
    ```  
    using (TransactionScope tx = new TransactionScope())  
    {  
        string filter = "WHERE Id='438B7B4C-5491-409F-BCC1-78817C399EC3'";  
        byte[] data = ASCIIEncoding.ASCII.GetBytes("Sample data");  
        client.SetDocument(filter, data);  
        tx.Complete();  
    }  
    ```  
  
     <span data-ttu-id="13ba2-195">應用程式，將 「 範例資料 」 的字串轉換成 base64 編碼的字串，並更新符合篩選準則的記錄中。</span><span class="sxs-lookup"><span data-stu-id="13ba2-195">Here, the application converts the string “Sample data” into a base64 encoded string, and updates it in the record that satisfies the filter criteria.</span></span>  
  
8.  <span data-ttu-id="13ba2-196">以下程式碼片段中所述，請關閉用戶端：</span><span class="sxs-lookup"><span data-stu-id="13ba2-196">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
9. <span data-ttu-id="13ba2-197">建置專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="13ba2-197">Build the project and then run it.</span></span> <span data-ttu-id="13ba2-198">應用程式更新**文件**中的資料行**記錄**資料表。</span><span class="sxs-lookup"><span data-stu-id="13ba2-198">The application updates the **Document** column in the **Records** table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ba2-199">請參閱</span><span class="sxs-lookup"><span data-stu-id="13ba2-199">See Also</span></span>  
[<span data-ttu-id="13ba2-200">使用 WCF 服務模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="13ba2-200">Develop applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)